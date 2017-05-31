---
title: "列ストア インデックス - データ ウェアハウス | Microsoft Docs"
ms.custom: 
ms.date: 01/27/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21fd153b-116d-47fc-a926-f1528299a391
caps.latest.revision: 15
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: ba866cdea9d6158affc31e74572bb9610ab94489
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="columnstore-indexes---data-warehouse"></a>列ストア インデックス - データ ウェアハウス
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  列ストア インデックスは、パーティション分割と共に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ ウェアハウスの構築に不可欠な機能です。  
  
## <a name="whats-new"></a>新機能  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] では、列ストアのパフォーマンスを向上させるために、次の機能が導入されています。  
  
-   AlwaysOn で、読み取り可能なセカンダリ レプリカで列ストア インデックスのクエリをサポートします。  
  
-   複数のアクティブな結果セット (MARS) で、列ストア インデックスをサポートします。  
  
-   新しい動的管理ビュー [sys.dm_db_column_store_row_group_physical_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-column-store-row-group-physical-stats-transact-sql.md) は、パフォーマンスのトラブルシューティングに関する情報を行グループ レベルで提供します。  
  
-   列ストア インデックスでのシングル スレッド クエリは、バッチ モードで実行できます。 以前は、バッチ モードで実行できるのはマルチ スレッド クエリのみでした。  
  
-   SORT 演算子は、バッチ モードで実行されます。  
  
-   複数の DISTINCT 操作は、バッチ モードで実行されます。  
  
-   ウィンドウ集計がデータベース互換性レベル 130 のバッチ モードで実行されるようになりました。  
  
-   集計を効率的に処理するための集計プッシュ ダウン。 これは、すべてのデータベース互換性レベルでサポートされています。  
  
-   文字列の述語を効率的に処理するための文字列述語プッシュ ダウン。 これは、すべてのデータベース互換性レベルでサポートされています。  
  
-   データベース互換性レベル 130 でのスナップショット分離  
  
## <a name="improve-performance-by-combining-nonclustered-and-columnstore-indexes"></a>非クラスター化インデックスと列ストア インデックスを組み合わせてパフォーマンスを改善する  
 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]以降では、クラスター化列ストア インデックスに非クラスター化インデックスを定義できます。  
  
### <a name="example-improve-efficiency-of-table-seeks-with-a-nonclustered-index"></a>例: 非クラスター化インデックスを使用してテーブルの検索効率を改善する  
 データ ウェアハウスでのテーブルの検索効率を改善するために、テーブルの検索でクエリが最高のパフォーマンスを発揮するように設計された非クラスター化インデックスを作成できます。 たとえば、一致する値を見つけるクエリや、値の小さな範囲を返すクエリは、列ストア インデックスではなく B ツリー インデックスに対して実行したほうが高いパフォーマンスを発揮します。 このようなクエリでは、列ストア インデックスを介したテーブル全体のスキャンは必要ありません。B ツリー インデックスを介したバイナリ検索を実行すると、よりすばやく正しい結果が返されます。  
  
```  
--BASIC EXAMPLE: Create a nonclustered index on a columnstore table.  
  
--Create the table  
CREATE TABLE t_account (  
    AccountKey int NOT NULL,  
    AccountDescription nvarchar (50),  
    AccountType nvarchar(50),  
    UnitSold int  
);  
GO  
  
--Store the table as a columnstore.  
CREATE CLUSTERED COLUMNSTORE INDEX taccount_cci ON t_account;  
GO  
  
--Add a nonclustered index.  
CREATE UNIQUE INDEX taccount_nc1 ON t_account (AccountKey);  
```  
  
### <a name="example-use-a-nonclustered-index-to-enforce-a-primary-key-constraint-on-a-columnstore-table"></a>例: 非クラスター化インデックスを使用して列ストア テーブルに主キー制約を適用する  
 仕様により、列ストア テーブルに主キー制約を設定することはできません。 ただし、列ストア テーブルで非クラスター化インデックスを使用して、主キー制約を適用できるようになりました。 主キーは非 NULL 列での UNIQUE 制約に相当し、SQL Server は UNIQUE 制約を非クラスター化インデックスとして実装します。 これらの事実を組み合わせて、次の例では、非 NULL 列 accountkey に UNIQUE 制約を定義しています。 その結果、非クラスター化インデックスにより、非 NULL 列の UNIQUE 制約として主キー制約が適用されます。  
  
 次に、テーブルはクラスター化列ストア インデックスに変換されます。 変換中は、非クラスター化インデックスが保持されます。 その結果、クラスター化列ストア インデックスに、主キー制約を適用する非クラスター化インデックスが含まれます。 列ストア テーブルでの更新または挿入は非クラスター化インデックスにも影響するため、UNIQUE 制約と非 NULL に違反する操作を行うと、操作全体の失敗につながります。  
  
 その結果、列ストア インデックスに、両方のインデックスに主キー制約を適用する非クラスター化インデックスが含まれます。  
  
```  
--EXAMPLE: Enforce a primary key constraint on a columnstore table.   
  
--Create a rowstore table with a unique constraint.  
--The unique constraint is implemented as a nonclustered index.  
CREATE TABLE t_account (  
    AccountKey int NOT NULL,  
    AccountDescription nvarchar (50),  
    AccountType nvarchar(50),  
    UnitSold int,  
  
    CONSTRAINT uniq_account UNIQUE (AccountKey)  
);  
  
--Store the table as a columnstore.   
--The unique constraint is preserved as a nonclustered index on the columnstore table.  
CREATE CLUSTERED COLUMNSTORE INDEX t_account_cci ON t_account  
  
--By using the previous two steps, every row in the table meets the UNIQUE constraint  
--on a non-NULL column.  
--This has the same end-result as having a primary key constraint  
--All updates and inserts must meet the unique constraint on the nonclustered index or they will fail.  
  
--If desired, add a foreign key constraint on AccountKey.  
  
ALTER TABLE [dbo].[t_account]  
WITH CHECK ADD FOREIGN KEY([AccountKey]) REFERENCES my_dimension(Accountkey)  
;  
  
```  
  
### <a name="improve-performance-by-enabling-row-level-and-row-group-level-locking"></a>行レベルおよび行グループ レベルのロックを有効にしてパフォーマンスを改善する  
 列ストア インデックス機能で非クラスター化インデックスを補完するために、 [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] には、選択、更新、および削除の各操作に対してより細分化されたロック機能が用意されています。 クエリの実行では、非クラスター化インデックスに対するインデックス検索に行レベルのロックを使用できます。また、列ストア インデックスに対するテーブル全体のスキャンに行グループ レベルのロックを使用できます。 行レベルのロックと行グループ レベルのロックを適切に使用すると、読み取り/書き込みの同時実行度を高めることができます。  
  
```  
--Granular locking example  
--Store table t_account as a columnstore table.  
CREATE CLUSTERED COLUMNSTORE INDEX taccount_cci ON t_account  
GO  
  
--Add a nonclustered index for use with this example  
CREATE UNIQUE INDEX taccount_nc1 ON t_account (AccountKey);  
GO  
  
--Look at locking with access through the nonclustered index  
SET TRANSACTION ISOLATION LEVEL repeatable read;  
GO  
  
BEGIN TRAN  
    -- The query plan chooses a seek operation on the nonclustered index  
    -- and takes the row lock  
    SELECT * FROM t_account WHERE AccountKey = 100;  
END TRAN  
  
```  
  
### <a name="snapshot-isolation-and-read-committed-snapshot-isolations"></a>スナップショット分離と Read Committed スナップショット分離  
 列ストア インデックスのクエリに対し、トランザクションの一貫性を保証するにはスナップショット分離 (SI) を使用し、ステートメント レベルの一貫性を保証するには Read Committed スナップショット分離 (RCSI) を使用します。 これにより、データ ライターをブロックすることなくクエリを実行できるようになります。 この非ブロッキング動作によって、複雑なトランザクションがデッドロックする可能性も大幅に減少します。 詳細については、MSDN の「 [SQL Server でのスナップショット分離](http://msdn.microsoft.com/library/tcbchxcb\(v=vs.110\).aspx) 」を参照してください。  
  
## <a name="see-also"></a>参照  
 列ストア インデックス ガイド   
 列ストア インデックス データの読み込み   
 列ストア インデックスのバージョン管理機能の概要   
 [列ストア インデックスのクエリ パフォーマンス](../../relational-databases/indexes/columnstore-indexes-query-performance.md)   
 [列ストアを使用したリアルタイム運用分析の概要](../../relational-databases/indexes/get-started-with-columnstore-for-real-time-operational-analytics.md)   
 [列ストア インデックスの最適化](../../relational-databases/indexes/columnstore-indexes-defragmentation.md)  
  
  

