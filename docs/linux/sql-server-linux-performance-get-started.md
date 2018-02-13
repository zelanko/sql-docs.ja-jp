---
title: "Linux 上の SQL Server のパフォーマンス機能の概要 |Microsoft ドキュメント"
description: "この記事では、SQL Server に追加された新しい Linux ユーザーの SQL Server のパフォーマンス機能の概要を示します。 すべてのプラットフォームでは、これらの例の多くは機能が Linux にこの記事のコンテキストが存在します。"
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: 
ms.suite: sql
ms.technology: database-engine
ms.assetid: 60036d26-4797-4872-9a9e-3552841c61be
ms.custom: sql-linux
ms.workload: Inactive
ms.openlocfilehash: 73b452cf99016b4b4f38c7debacadf32a270421d
ms.sourcegitcommit: f02598eb8665a9c2dc01991c36f27943701fdd2d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/13/2018
---
# <a name="walkthrough-for-the-performance-features-of-sql-server-on-linux"></a>Linux 上の SQL Server のパフォーマンス機能のチュートリアル

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server に新しい Linux ユーザーの場合は、次のタスクはパフォーマンス機能の一部を説明します。 これらは一意または Linux に固有でないですがさらに詳しく調査するには、領域の概念を付けると便利です。 各例では、リンクは、その領域の深さのドキュメントが提供されます。

> [!NOTE]
> 次の例では、AdventureWorks サンプル データベースを使用します。 手順を取得して、このサンプル データベースをインストールする方法については、次を参照してください。 [Windows から Linux に SQL Server データベースを復元](sql-server-linux-migrate-restore-database.md)です。

## <a name="create-a-columnstore-index"></a>列ストア インデックスを作成します。
列ストア インデックスは、格納して、列ストアと呼ばれる列指向データ形式でデータの大規模なストアのクエリを実行するためのテクノロジです。  

1. 次の TRANSACT-SQL コマンドを実行することによって、salesorderdetail の各テーブルに列ストア インデックスを追加します。

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

3. 列ストア インデックスの object_id を参照して、salesorderdetail の各テーブルの使用状況の統計が表示されることを確認する、列ストア インデックスが使用されたことを確認します。

   ```sql
   SELECT * FROM sys.indexes WHERE name = 'IX_SalesOrderDetail_ColumnStore'
   GO

   SELECT * 
   FROM sys.dm_db_index_usage_stats
      WHERE database_id = DB_ID('AdventureWorks')
      AND object_id = OBJECT_ID('AdventureWorks.Sales.SalesOrderDetail');
   ```
   
## <a name="use-in-memory-oltp"></a>インメモリ OLTP を使用します。
SQL Server では、アプリケーションのシステムのパフォーマンスを大幅に改善できるインメモリ OLTP 機能を提供します。  評価ガイドのこのセクションでは、メモリおよびコンパイルまたは解釈することがなく、テーブルにアクセスできる、ネイティブ コンパイル ストアド プロシージャに格納されているメモリ最適化テーブルを作成する手順を説明します。

### <a name="configure-database-for-in-memory-oltp"></a>インメモリ OLTP でのデータベースを構成します。
1. データベースのインメモリ OLTP を使用するには、少なくとも 130 の互換性レベルを設定することをお勧めします。  AdventureWorks の現在の互換性レベルを確認するのにには、次のクエリを使用します。  

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

2. トランザクションがディスク ベース テーブルとメモリ最適化テーブルの両方に関与の重要なトランザクションのメモリ最適化部分が、トランザクション分離レベルで動作するには、スナップショットがという名前です。  このレベルのコンテナーにまたがるトランザクションでメモリ最適化テーブルを確実に適用するには、次の手順を実行します。

   ```sql
   ALTER DATABASE CURRENT SET MEMORY_OPTIMIZED_ELEVATE_TO_SNAPSHOT=ON
   GO
   ```

3. 作成する前にするには、メモリ最適化テーブルは、メモリ最適化ファイル グループとデータ ファイルのコンテナーを作成します。

   ```sql
   ALTER DATABASE AdventureWorks ADD FILEGROUP AdventureWorks_mod CONTAINS memory_optimized_data
   GO  
   ALTER DATABASE AdventureWorks ADD FILE (NAME='AdventureWorks_mod', FILENAME='/var/opt/mssql/data/AdventureWorks_mod') TO FILEGROUP AdventureWorks_mod
   GO
   ```

### <a name="create-a-memory-optimized-table"></a>メモリ最適化テーブルを作成します。
メモリ最適化テーブルのプライマリ ストアはメイン メモリしているため、ディスク ベース テーブルとは異なりでのメモリ バッファーにディスクから読み取られるデータは必要ありません。  メモリ最適化テーブルを作成するには、使用、MEMORY_OPTIMIZED = ON 句。

1. メモリ最適化テーブルの dbo を作成する次のクエリを実行します。ShoppingCart です。  として既定では、データは持続性の目的 (持続性を設定して、スキーマのみを保持することもできますメモ) 用のディスクで保持されます。 

   ```sql
   CREATE TABLE dbo.ShoppingCart ( 
   ShoppingCartId INT IDENTITY(1,1) PRIMARY KEY NONCLUSTERED,
   UserId INT NOT NULL INDEX ix_UserId NONCLUSTERED HASH WITH (BUCKET_COUNT=1000000), 
   CreatedDate DATETIME2 NOT NULL, 
   TotalPrice MONEY
   ) WITH (MEMORY_OPTIMIZED=ON) 
   GO
   ```

2. 一部のレコードをテーブルに挿入します。

   ```sql
   INSERT dbo.ShoppingCart VALUES (8798, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (23, SYSDATETIME(), 45.4) 
   INSERT dbo.ShoppingCart VALUES (80, SYSDATETIME(), NULL) 
   INSERT dbo.ShoppingCart VALUES (342, SYSDATETIME(), 65.4) 
   ```

### <a name="natively-compiled-stored-procedure"></a>ネイティブ コンパイル ストアド プロシージャ
SQL Server には、メモリ最適化テーブルにアクセスするネイティブ コンパイル ストアド プロシージャがサポートしています。 T-SQL ステートメントでは、マシン語コードにコンパイルされ、高速データ アクセスと従来の T-SQL でより効率的なクエリ実行を有効にすると、ネイティブ Dll として格納されていることができます。   NATIVE_COMPILATION が設定されているストアド プロシージャはネイティブでコンパイルされます。 

1. ShoppingCart テーブルに大量のレコードを挿入するネイティブ コンパイル ストアド プロシージャを作成する次のスクリプトを実行します。


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
2. 行数は 1,000,000 行を挿入します。

   ```sql
   EXEC usp_InsertSampleCarts 1000000 
   ```

3. 挿入された行を確認します。

   ```sql
   SELECT COUNT(*) FROM dbo.ShoppingCart 
   ```

### <a name="learn-more-about-in-memory-oltp"></a>インメモリ OLTP の詳細を表示します
インメモリ OLTP の詳細については、次のトピックを参照してください。

- [クイック スタート 1: Transact-SQL のパフォーマンスを向上させるインメモリ OLTP テクノロジ](../relational-databases/in-memory-oltp/survey-of-initial-areas-in-in-memory-oltp.md)
- [インメモリ OLTP への移行](../relational-databases/in-memory-oltp/migrating-to-in-memory-oltp.md)
- [メモリ最適化を使用した一時テーブルとテーブル変数の高速化](../relational-databases/in-memory-oltp/faster-temp-table-and-table-variable-by-using-memory-optimization.md)
- [メモリ使用量の監視とトラブルシューティング](../relational-databases/in-memory-oltp/monitor-and-troubleshoot-memory-usage.md)
- [インメモリ OLTP (インメモリ最適化)](../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)

## <a name="use-query-store"></a>クエリ ストアを使用
クエリ ストアは、クエリ、実行プランとランタイム統計情報に関する詳細なパフォーマンス情報を収集します。

クエリ ストアは、既定ではアクティブではありませんし、ALTER DATABASE を有効にすることができます。

   ```sql
   ALTER DATABASE AdventureWorks SET QUERY_STORE = ON;
   ```

クエリ ストアのクエリとプランに関する情報を返す次のクエリを実行します。 

   ```sql
   SELECT Txt.query_text_id, Txt.query_sql_text, Pl.plan_id, Qry.*
   FROM sys.query_store_plan AS Pl
      JOIN sys.query_store_query AS Qry
         ON Pl.query_id = Qry.query_id
      JOIN sys.query_store_query_text AS Txt
         ON Qry.query_text_id = Txt.query_text_id ;
   ```

## <a name="query-dynamic-management-views"></a>クエリの動的管理ビュー
動的管理ビューは、サーバー インスタンスのヘルスを監視、問題の診断し、パフォーマンスのチューニングに使用できるサーバーの状態情報を返します。

Dm_os_wait stats 動的管理ビューを照会します。

   ```sql
   SELECT wait_type, wait_time_ms
   FROM sys.dm_os_wait_stats;
   ```
