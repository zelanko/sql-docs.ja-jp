---
title: SQL Server on Linux のパフォーマンス機能の概要 |Microsoft Docs
description: この記事では、Linux ユーザーが SQL Server に新しい SQL Server のパフォーマンス機能の概要を示します。 これらの例の多くは、すべてのプラットフォームで機能が、この記事のコンテキストは Linux です。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 60036d26-4797-4872-9a9e-3552841c61be
ms.openlocfilehash: a340b3b8ded0824947cc242538ad19159b4abb4d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713322"
---
# <a name="walkthrough-for-the-performance-features-of-sql-server-on-linux"></a>SQL Server on Linux のパフォーマンス機能のチュートリアル

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server を初めて利用する Linux ユーザーの場合、次のタスクはパフォーマンス機能の一部についての解説となります。 これらは Linux に固有のものではありませんが、より詳しく調べたい領域を知るのに役立ちます。 各例では、その領域の詳細なドキュメントのリンクが提供されます。

> [!NOTE]
> 次の例では、AdventureWorks サンプル データベースを使用します。 このサンプル データベースを入手し、インストールする方法については、次を参照してください。 [Windows から Linux に SQL Server のデータベースを復元](sql-server-linux-migrate-restore-database.md)。

## <a name="create-a-columnstore-index"></a>列ストア インデックスを作成します。
列ストア インデックスは、列ストアと呼ばれる列指向データ形式で大規模なストアのデータを格納して、クエリを実行するためのテクノロジです。  

1. 次の TRANSACT-SQL コマンドを実行して、SalesOrderDetail テーブルに列ストア インデックスを追加します。

   ```sql
   CREATE NONCLUSTERED COLUMNSTORE INDEX [IX_SalesOrderDetail_ColumnStore]
      ON Sales.SalesOrderDetail
      (UnitPrice, OrderQty, ProductID)
   GO
   ```

2. 列ストア インデックスを使用して、テーブルをスキャンする次のクエリを実行します。

   ```sql
   SELECT ProductID, SUM(UnitPrice) SumUnitPrice, AVG(UnitPrice) AvgUnitPrice,
      SUM(OrderQty) SumOrderQty, AVG(OrderQty) AvgOrderQty
   FROM Sales.SalesOrderDetail
      GROUP BY ProductID
      ORDER BY ProductID
   ```

3. 列ストア インデックスの object_id を参照して SalesOrderDetail テーブルの使用状況の統計に表示されることを確認することにより、列ストア インデックスが使用されたことを確認します。

   ```sql
   SELECT * FROM sys.indexes WHERE name = 'IX_SalesOrderDetail_ColumnStore'
   GO

   SELECT * 
   FROM sys.dm_db_index_usage_stats
      WHERE database_id = DB_ID('AdventureWorks')
      AND object_id = OBJECT_ID('AdventureWorks.Sales.SalesOrderDetail');
   ```
   
## <a name="use-in-memory-oltp"></a>インメモリ OLTP を使用します。
SQL Server では、アプリケーションのシステムのパフォーマンスを大幅に改善できるインメモリ OLTP 機能を提供します。  評価ガイドのこのセクションでは、コンパイルまたは解釈することなくテーブルにアクセスできる、ネイティブ コンパイル ストアド プロシージャと、メモリに格納されているメモリ最適化テーブルを作成する手順を説明します。

### <a name="configure-database-for-in-memory-oltp"></a>インメモリ OLTP でのデータベースを構成します。
1. インメモリ OLTP を使用するには少なくとも 130 の互換性レベルにデータベースを設定することをお勧めします。  AdventureWorks の現在の互換性レベルを確認するには、次のクエリを使用します。  

   ```sql
   USE AdventureWorks
   GO
   SELECT d.compatibility_level
   FROM sys.databases as d
     WHERE d.name = Db_Name();
   GO
   ```
   
   必要に応じて、レベルを 130 に更新します。

   ```sql
   ALTER DATABASE CURRENT
   SET COMPATIBILITY_LEVEL = 130;
   GO
   ```

2. トランザクションは、ディスク ベース テーブルとメモリ最適化テーブルの両方では、ときにきわめて重要トランザクションのメモリ最適化部分が、トランザクション分離レベルで動作するスナップショットの名前。  コンテナーをまたがるトランザクションでメモリ最適化テーブルに対してこのレベルを確実に適用するには、次を実行します。

   ```sql
   ALTER DATABASE CURRENT SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON
   GO
   ```

3. メモリ最適化テーブルを作成する前に、メモリ最適化ファイル グループとデータ ファイルのコンテナーを作成します。

   ```sql
   ALTER DATABASE AdventureWorks ADD FILEGROUP AdventureWorks_mod CONTAINS memory_optimized_data
   GO  
   ALTER DATABASE AdventureWorks ADD FILE (NAME='AdventureWorks_mod', FILENAME='/var/opt/mssql/data/AdventureWorks_mod') TO FILEGROUP AdventureWorks_mod
   GO
   ```

### <a name="create-a-memory-optimized-table"></a>メモリ最適化テーブルを作成します。
メモリ最適化テーブルのプライマリ ストアはメイン メモリであるため、ディスク ベース テーブルとは異なり、ディスクからメモリ バッファーにデータを読み取る必要はありません。  メモリ最適化テーブルを作成するには、MEMORY_OPTIMIZED = ON 句を使用します。

1. メモリ最適化テーブルの dbo.ShoppingCart を作成するために、次のクエリを実行します。  既定では、データは持続性の目的のためディスクに保持されます (注: 持続性は、スキーマのみを保持するよう設定することもできます)。 

   ```sql
   CREATE TABLE dbo.ShoppingCart ( 
   ShoppingCartId INT IDENTITY(1,1) PRIMARY KEY NONCLUSTERED,
   UserId INT NOT NULL INDEX ix_UserId NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000), 
   CreatedDate DATETIME2 NOT NULL, 
   TotalPrice MONEY
   ) WITH (MEMORY_OPTIMIZED=ON) 
   GO
   ```

2. いくつかのレコードをテーブルに挿入します。

   ```sql
   INSERT dbo.ShoppingCart VALUES (8798, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (23, SYSDATETIME(), 45.4) 
   INSERT dbo.ShoppingCart VALUES (80, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (342, SYSDATETIME(), 65.4) 
   ```

### <a name="natively-compiled-stored-procedure"></a>ネイティブ コンパイル ストアド プロシージャ
SQL Server では、メモリ最適化テーブルにアクセスするネイティブ コンパイル ストアド プロシージャがサポートされています。 T-SQL ステートメントは、機械語のコードにコンパイルされ、高速データ アクセスと従来の T-SQL より効率的なクエリ実行が可能になる、ネイティブ DLL として格納されます。   NATIVE_COMPILATION が設定されているストアド プロシージャはネイティブでコンパイルされます。 

1. ShoppingCart テーブルに多数のレコードを挿入するネイティブ コンパイル ストアド プロシージャを作成する次のスクリプトを実行します。


   ```sql
   CREATE PROCEDURE dbo.usp_InsertSampleCarts @InsertCount int 
    WITH NATIVE_COMPILATION, SCHEMABINDING AS 
   BEGIN ATOMIC 
   WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')

   DECLARE @i int = 0

   WHILE @i < @InsertCount 
    BEGIN 
     INSERT INTO dbo.ShoppingCart VALUES (1, SYSDATETIME() , NULL) 
     SET @i += 1 
    END
   END 
   ```
2. 1,000,000 行を挿入します。

   ```sql
   EXEC usp_InsertSampleCarts 1000000 
   ```

3. 行が挿入されたことを確認するには。

   ```sql
   SELECT COUNT(*) FROM dbo.ShoppingCart 
   ```

### <a name="learn-more-about-in-memory-oltp"></a>インメモリ OLTP の詳細
インメモリ OLTP の詳細については、次のトピックを参照してください。

- [クイック スタート 1。TRANSACT-SQL のパフォーマンスを向上させるインメモリ OLTP テクノロジ](../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)
- [インメモリ OLTP への移行](../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)
- [メモリ最適化を使用した一時テーブルとテーブル変数の高速化](../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)
- [メモリ使用量の監視とトラブルシューティング](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)
- [インメモリ OLTP (インメモリ最適化)](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)

## <a name="use-query-store"></a>クエリ ストアを使用
クエリ ストアは、クエリ、実行プラン、およびランタイム統計に関する詳細なパフォーマンス情報を収集します。

クエリ ストアは、既定ではアクティブではありません。ALTER DATABASE で有効にすることができます。

   ```sql
   ALTER DATABASE AdventureWorks SET QUERY_STORE = ON;
   ```

クエリ ストアにクエリとプランに関する情報を返す次のクエリを実行します。 

   ```sql
   SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*
   FROM sys.query_store_plan AS Pl
      JOIN sys.query_store_query AS Qry
         ON Pl.query_id = Qry.query_id
      JOIN sys.query_store_query_text AS Txt
         ON Qry.query_text_id = Txt.query_text_id ;
   ```

## <a name="query-dynamic-management-views"></a>クエリの動的管理ビュー
動的管理ビューは、サーバー インスタンスのヘルスの監視、問題の診断、パフォーマンスのチューニングに使用できる、サーバーの状態の情報を返します。

Dm_os_wait stats の動的管理ビューを照会するには。

   ```sql
   SELECT wait_type, wait_time_ms
   FROM sys.dm_os_wait_stats;
   ```
