---
title: "列ストア インデックス - 最適化 | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 01/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3efda1a-7bdb-47f5-80bf-f075329edee5
caps.latest.revision: 17
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: eea1da9c6a3c9dd30b89c72488570ae98737eaa5
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="columnstore-indexes---defragmentation"></a>列ストア インデックス - 最適化
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  列ストア インデックスを最適化するタスク。  
  
## <a name="use-alter-index-reorganize-to-defragment-a-columnstore-index-online"></a>ALTER INDEX REORGANIZE を使用して、列ストア インデックスをオンラインで最適化する  
 適用対象: SQL Server (2016 以降)、Azure SQL Database  
  
  何らかの種類の読み込みを実行した後、デルタストアに複数の小さな行グループが含まれることがあります。 ALTER INDEX REORGANIZE を使用して、すべての行グループを列ストアに強制的に移動し、これらの行グループを、より行数の多い少数の行グループへと結合することができます。  再構成操作では、列ストアから削除された行も削除されます。  
  
 詳細については、SQL データベース エンジン チームのブログにある Sunil Agarwal のブログ投稿を参照してください。  
  
-   [Minimizing index fragmentation in columnstore indexes (列ストア インデックスでインデックスの断片化を最小限に抑える)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/07/columnstore-index-defragmentation-using-reorganize-command/)  
  
-   [Columnstore indexes and the merge policy for rowgroups (列ストア インデックスと、行グループのマージ ポリシー)](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/03/08/columnstore-index-merge-policy-for-reorganize/)  
  
### <a name="recommendations-for-reorganizing"></a>再構成に関する推奨事項  
 クエリのパフォーマンスの利点をできるだけ早く得るために、1 つ以上のデータが読み込まれた後に列ストア インデックスを再編成します。 再構成ではデータを圧縮するために最初に追加の CPU リソースが必要とされ、システムの全体的なパフォーマンスが遅くなる場合があります。 しかし、データが圧縮されるとすぐにクエリ パフォーマンスが改善します。  
  
 「[sys.dm_db_column_store_row_group_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md)」の例を使用して、断片化を計算します。 これにより、REORGANIZE 操作を実行する意義があるかどうかを判断できます。  
  
### <a name="example-how-reorganizing-works"></a>例: 再編成のしくみ  
 この例では、ALTER INDEX REORGANIZE がすべてのデルタストア行グループを列ストアに強制的に移動し、行グループを結合する方法を示します。  
  
1.  この Transact-SQL を実行して、300,000 行を含むステージング テーブルを作成します。 これを使用して、行を列ストア インデックスに一括読み込みします。  
  
    ```  
    USE master;  
    GO  
  
    IF EXISTS (SELECT name FROM sys.databases  
        WHERE name = N'[columnstore]')  
        DROP DATABASE [columnstore];  
    GO  
  
    CREATE DATABASE [columnstore];  
    GO  
  
    IF EXISTS (SELECT name FROM sys.tables  
        WHERE name = N'staging'  
        AND object_id = OBJECT_ID (N'staging'))  
    DROP TABLE dbo.staging;  
    GO  
  
    CREATE TABLE [staging] (  
         AccountKey int NOT NULL,  
         AccountDescription nvarchar (50),  
         AccountType nvarchar(50),  
         AccountCodeAlternateKey int  
    );  
    GO  
  
    -- Load data  
    DECLARE @loop int;  
    DECLARE @AccountDescription varchar(50);  
    DECLARE @AccountKey int;  
    DECLARE @AccountType varchar(50);  
    DECLARE @AccountCode int;  
  
    SELECT @loop = 0;  
    BEGIN TRAN  
        WHILE (@loop < 300000)   
          BEGIN  
            SELECT @AccountKey = CAST (RAND()*10000000 AS int);  
            SELECT @AccountDescription = 'accountdesc ' + CONVERT(varchar(20), @AccountKey);  
            SELECT @AccountType = 'AccountType ' + CONVERT(varchar(20), @AccountKey);  
            SELECT @AccountCode =  CAST (RAND()*10000000 AS int);  
  
            INSERT INTO staging VALUES (  
               @AccountKey,   
               @AccountDescription,   
               @AccountType,   
               @AccountCode  
            );  
  
            SELECT @loop = @loop + 1;  
          END  
    COMMIT  
  
    ```  
  
2.  列ストア インデックスとして格納されるテーブルを作成します。  
  
    ```  
    IF EXISTS (SELECT name FROM sys.tables  
        WHERE name = N'cci_target'  
        AND object_id = OBJECT_ID (N'cci_target'))  
    DROP TABLE dbo.cci_target;  
    GO  
  
    -- Create a table with a clustered columnstore index  
    -- and the same columns as the rowstore staging table.  
    CREATE TABLE cci_target (  
         AccountKey int NOT NULL,  
         AccountDescription nvarchar (50),  
         AccountType nvarchar(50),  
         AccountCodeAlternateKey int,  
         INDEX idx_cci_target CLUSTERED COLUMNSTORE  
    )  
    GO  
  
    ```  
  
3.  ステージング テーブルの行を列ストア テーブルに一括挿入します。 INSERT INTO ... SELECT は一括挿入を実行します。   TABLOCK は並列挿入を実行します。  
  
    ```  
    -- Insert rows in parallel  
    INSERT INTO cci_target WITH (TABLOCK)  
    SELECT TOP (300000) * FROM staging;  
    GO  
  
    ```  
  
4.  sys.dm_db_column_store_row_group_physical_stats 動的管理ビュー (DMV) を使用して、行グループを表示します。  
  
    ```  
    -- Run this dynamic management view (DMV) to see the OPEN rowgroups.   
    -- The number of rowgroups depends on the degree of parallelism.   
    -- You will see multiple OPEN rowgroups depending on the degree of parallelism.   
    -- This is because insert operation can run in parallel in SQL server 2016.  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
  
    ```  
  
     この例の結果は、それぞれ 37,500 行を含む 8 つの OPEN 行グループを示しています。 OPEN 行グループの番号は、max_degree_of_parallelism 設定によって決まります。  
  
     ![OPEN 行グループ](../../relational-databases/indexes/media/cci-openrowgroups.png "OPEN rowgroups")  
  
5.  ALTER INDEX REORGANIZE とともに COMPRESS_ALL_ROW_GROUPS オプションを使用して、すべての行グループを列ストアに強制的に圧縮します。  
  
    ```  
    -- This command will force all CLOSED and OPEN rowgroups into the columnstore.  
    ALTER INDEX idx_cci_target ON cci_target   
    REORGANIZE WITH (COMPRESS_ALL_ROW_GROUPS = ON);  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
  
    ```  
  
     この結果は、8 つの COMPRESSED 行グループと 8 つの TOMBSTONE 行グループを示しています。 各行グループは、そのサイズに関係なく列ストアに圧縮されます。 TOMBSTONE 行グループは、システムによって削除されます。  
  
     ![TOMBSTONE と COMPRESSED 行グループ](../../relational-databases/indexes/media/cci-tombstone-compressed-rowgroups.png "TOMBSTONE and COMPRESSED rowgroups")  
  
6.  クエリ パフォーマンスのためには、小さな行グループを結合する方がはるかに効果的です。  ALTER INDEX REORGANIZE は、COMPRESSED 行グループを結合します。 これで、デルタ行グループが列ストアに圧縮されたので、ALTER INDEX REORGANIZE を再度実行して、小さな COMPRESSED 行グループを結合します。 ここでは、COMPRESS_ALL_ROW_GROUPS オプションは不要です。  
  
    ```  
    -- Run this again and you will see that smaller rowgroups   
    -- combined into one compressed rowgroup with 300,000 rows  
    ALTER INDEX idx_cci_target ON cci_target REORGANIZE;  
  
    SELECT *   
    FROM sys.dm_db_column_store_row_group_physical_stats   
    WHERE object_id  = object_id('cci_target')  
    ORDER BY row_group_id;  
    ```  
  
     この結果は、8 つの COMPRESSED 行グループが 1 つの COMPRESSED 行グループに結合されたことを示しています。  
  
     ![結合行グループ](../../relational-databases/indexes/media/cci-compressed-rowgroups.png "Combined rowgroups")  
  
##  <a name="rebuild"></a> ALTER INDEX REBUILD を使用して、列ストア インデックスをオフラインで最適化する  
 SQL Server 2016 以降では、通常、列ストア インデックスの再構築は必要ありません。これは、REORGANIZE がオンサイン操作としてバック グラウンドで再構築の基本事項を実行するためです。  
  
 列ストア インデックスを再構築すると、断片化が解消され、すべての行が列ストアに移動されます。 [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-columnstore-index-transact-sql.md) または [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md) を使用して、既存のクラスター化列ストア インデックスの完全な再構築を行います。 また、ALTER INDEX …  REBUILD を使用して特定のパーティションを再構築できます。  
  
### <a name="rebuild-process"></a>再構築プロセス  
 列ストア インデックスを再構築する際、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は以下のように動作します。  
  
1.  再構築が行われている間、テーブルまたはパーティションを排他的にロックします。  データは、NOLOCK、RCSI または SI を使用する場合でも、「オフライン」であり、再構築中に使用できません。  
  
2.  すべてのデータを列ストアに再圧縮します。 再構築が行われている間、列ストア インデックスのコピーが 2 つ存在します。 再構築が完了したら、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] により、元の列ストア インデックスが削除されます。  
  
### <a name="recommendations-for-rebuilding-a-columnstore-index"></a>列ストア インデックスの再構築に関する推奨事項  
 列ストア インデックスを再構築すると、断片化を解消する場合、およびすべての行を列ストアに移動する場合に便利です。 次の推奨事項が用意されています。  
  
1.  テーブル全体ではなくパーティションを再構築します。  
  
    -   インデックスが大きいとテーブル全体の再構築には時間がかかり、再構築中にインデックスの追加コピーを格納するために十分なディスク領域が必要です。 通常は、最近使用されたパーティションを再構築するだけで済みます。  
  
    -   パーティション テーブルでは、columnstore インデックス全体を再構築する必要はありません。断片化は最近変更されたパーティションのみで起きる可能性が高いためです。 ファクト テーブルや大きなディメンション テーブルは通常、テーブルのチャンク上でバックアップおよび管理を行うためにパーティション分割されます。  
  
2.  負荷の高い DML 操作後にパーティションを再構築します。  
  
    -   パーティションを再構築すると、パーティションの断片化を解消し、ディスク ストレージが減少します。 再構築すると、削除のマークが付けられた列ストアからすべての行が削除され、すべての行グループがデルタストアから列ストアに移動されます。 デルタストアには、それぞれ 100 万未満の行を含む複数の行グループがある場合があります。  
  
3.  データを読み込んだ後に、パーティションを再構築します。  
  
    -   これにより、すべてデータが columnstore に格納されます。 同時実行のプロセスでそれぞれ 100,000 未満の行が同じパーティションに同時に読み込まれた場合、パーティションに複数のデルタストアが含まれることがあります。 再構築すると、すべてのデルタストア行が columnstore に移動されます。  
  
## <a name="see-also"></a>参照        
[列ストア インデックス - 新機能](../../relational-databases/indexes/columnstore-indexes-what-s-new.md)

[列ストア インデックス - クエリ パフォーマンス](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
[列ストアを使用したリアルタイム運用分析の概要](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 [列ストア インデックス - データ ウェアハウス](../../relational-databases/indexes/columnstore-indexes-data-warehouse.md)   
   
  
  

