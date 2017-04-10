---
title: "SQL Server vNext の新機能 (データベース エンジン) | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-vnext"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42f45b23-6509-45e8-8ee7-76a78f99a920
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 13
---
# SQL Server vNext の新機能 (データベース エンジン)
[!INCLUDE[tsql-appliesto-ssvNxt-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssvnxt-xxxx-xxxx-xxx.md)]

**注:** SQL Server vNext には、SQL Server 2016 サービス パックに追加された機能も含まれています。 それらの項目については、「[SQL Server 2016 (データベース エンジン) の新機能](../../database-engine/configure-windows/what-s-new-in-sql-server-2016-database-engine.md)」を参照してください。

## <a name="sql-server-database-engine-ctp-13"></a>SQL Server データベース エンジン (CTP 1.3)
- 間接チェックポイントのパフォーマンスが強化されました。
- クラスターレス可用性グループのサポートが追加されました。
- ミニマム レプリカ コミット可用性グループの設定が追加されました。
- Windows と Linux 間で可用性グループが利用できるようになり、OS 間での移行とテストができるようになりました。
- テンポラル表の保持ポリシーのサポートが追加されました。
- DMV SYS.DM_DB_STATS_HISTOGRAM が新しくなりました。
- 非クラスター化列ストア インデックスのオンライン ビルドおよびリビルドのサポートが追加されました。
- Linux プロセスの情報を返す動的管理ビューが&5; つ追加されました。 詳細については、[Linux のサービスの動的管理ビュー](../../relational-databases/system-dynamic-management-views/linux-process-dynamic-management-views-transact-sql.md)に関する記事を参照してください。   
- 統計情報を確認するための [sys.dm_db_stats_histogram (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) が追加されました。

## <a name="sql-server-database-engine-ctp-12"></a>SQL Server データベース エンジン (CTP 1.2)

- SQL Server Management Studio バージョン 16.4 とともにリリースされた データベース チューニング アドバイザー (DTA) には、SQL Server 2016 以降を分析する際の追加のオプションがあります。    
   - 向上したパフォーマンス。 詳細については、「[Performance Improvements using Database Engine Tuning Advisor (DTA) recommendations (データベース エンジン チューニング アドバイザー (DTA) の推奨事項を使用したパフォーマンスの強化)](../../relational-databases/performance/performance-improvements-using-dta-recommendations.md)」を参照してください。
   - 列ストア インデックスの推奨事項を許可する `-fc` オプション。 詳細については、「[dta ユーティリティ](../../tools/dta/dta-utility.md)」、および「[Columnstore index recommendations in Database Engine Tuning Advisor (DTA) (データベース エンジン チューニング アドバイザー (DTA) での列ストア インデックス推奨事項)](../../relational-databases/performance/columnstore-index-recommendations-in-database-engine-tuning-advisor-dta.md)」を参照してください。  
   - DTA を許可してクエリ ストアのワークロードをレビューする `-iq` オプション。 詳細については、「[Tuning Database Using Workload from Query Store (クエリ ストアのワークロードを使用してデータベースをチューニングする)](../../relational-databases/performance/tuning-database-using-workload-from-query-store.md)」を参照してください。
   

## <a name="sql-server-database-engine-ctp-11"></a>SQL Server データベース エンジン (CTP 1.1)

<a name="InMemoryBulletsCtp11"/>
- インメモリ機能用に、メモリ最適化テーブルおよびネイティブにコンパイルされた関数の追加の機能強化が次に示されています。また、コード サンプルは[後続のテキスト](#InMemory_CodeSamples)で利用可能です。
    - 計算列のインデックスなど、メモリ最適化テーブルの計算列のサポート。
    - ネイティブ コンパイル モジュールと CHECK 制約の JSON 関数の完全サポート。
    - ネイティブ コンパイル モジュールの `CROSS APPLY` 演算子。   
- 新しい文字列関数 [CONCAT_WS](../../t-sql/functions/concat-ws-transact-sql.md)、[TRANSLATE](../../t-sql/functions/translate-transact-sql.md)、および[TRIM](../../t-sql/functions/trim-transact-sql.md) が追加されました。   
- [STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md) 関数で `WITHIN GROUP` 句がサポートされました。
- 2 つの新しい日本語の照合順序ファミリ (Japanese_Bushu_Kakusu_140 and Japanese_XJIS_140) が追加されました。また、日本語の照合順序用に、照合順序オプション Variation-selector-sensitive (_VSS) が追加されました。 詳細については、「[照合順序と Unicode のサポート](../../relational-databases/collations/collation-and-unicode-support.md)」を参照してください。   
- 新しい一括アクセス オプション ([BULK INSERT](../../t-sql/statements/bulk-insert-transact-sql.md) と [OPENROWSET(BULK...)](../../t-sql/functions/openrowset-transact-sql.md)) を使用すると、[EXTERNAL DATA SOURCE](../../t-sql/statements/create-external-data-source-transact-sql.md) の新しい `BLOB_STORAGE` オプションで、CSV 形式で指定したファイルまたは Azure BLOB 記憶域に格納されているファイルから直接データにアクセスできます。


## <a name="sql-server-database-engine-ctp-10"></a>SQL Server データベース エンジン (CTP 1.0)

- データベース **COMPATIBILITY_LEVEL** 140 が追加されました。   このレベルで実行しているお客様には、最新の言語機能とクエリ オプティマイザー動作が与えられます。 これには、Microsoft 製品の各リリース前バージョンの変更が含まれています。
- 増分統計更新の方法が改善、しきい値が計算されます (140 互換モード必須)。
- [sys.dm_exec_query_statistics_xml](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-statistics-xml-transact-sql.md) が追加されます。
- インメモリ テーブルにパフォーマンスと言語のさまざま拡張機能が追加されました。
    - インメモリ テーブルで `sp_spaceused` がサポートされるようになりました。
    - ネイティブ モジュールで `sp_rename` がサポートされるようになりました。
    - ネイティブ モジュールで `CASE` ステートメントがサポートされるようになりました。
    - インメモリ テーブルで 8 個のインデックス制限がなくなりました。
    - ネイティブ モジュールで `TOP (N) WITH TIES` がサポートされるようになりました。
    - 一部のケースで、インメモリ テーブルに対する `ALTER TABLE` が大幅に速くなりました。
    - インメモリ テーブルのやり直しトランザクションが並列で行われるようになりました。 それにより、フェールオーバーや (一部のケースで) 再起動にかかる時間が大幅に短縮されます。
    - インメモリ チェックポイント ファイルを Azure Storage に保存できるようになりました。 これで LDF ファイルと同等の機能が MDF に与えられます。
- クラスター化された列ストア インデックスが LOB 列 (nvarchar(max)、varchar(max)、varbinary(max)) 対応になりました。
- [STRING_AGG](../../t-sql/functions/string-agg-transact-sql.md) 集計関数が追加されました。  
- 新しい権限: `DATABASE SCOPED CREDENTIAL` クラスがセキュリティ保護可能となり、`CONTROL`、`ALTER`、`REFERENCES`、`TAKE OWNERSHIP`、および `VIEW DEFINITION` の各権限がサポートされるようになりました。 SQL Database に限られていた `ADMINISTER DATABASE BULK OPERATIONS` が `sys.fn_builtin_permissions` で表示されるようになりました。   
- [sys.dm_os_host_info](../../relational-databases/system-dynamic-management-views/sys-dm-os-host-info-transact-sql.md) DMV が追加され、Windows と Linux の両方のオペレーティング システム情報を提供します。   
- データベース ロールが R サービスで作成され、パッケージに関連付けられているアクセス許可を管理します。 詳細については、[SQL Server の R パッケージ管理](../../advanced-analytics/r-services/r-package-management-for-sql-server-r-services.md)に関するページを参照してください。
 
<a name="InMemory_CodeSamples"/> 
## <a name="code-samples-for-new-in-memory-enhancements"></a>新しいインメモリ機能強化のコード サンプル

次のサブセクションでは Transact-SQL コード サンプルを提供します。これは、この記事の前出のテキストで箇条書きされている、新しいインメモリ機能を表すものです。

インメモリの CTP 1.1 箇条書きリストは[こちら](#InMemoryBulletsCtp11)にあります。

#### <a name="computed-column-in-a-memory-optimized-table"></a>メモリ最適化テーブルの計算列

この CREATE TABLE ステートメントは、前出の CTP 1.1 に関するテキストで言及された、次の機能を表しています。

- 列の JSON CHECK 制約。
- 新しい計算列。
- 計算列のインデックス。

```tsql
CREATE TABLE Product(
    ProductID  int            PRIMARY KEY NONCLUSTERED,
    Name       nvarchar(400)  NOT NULL,
    Price      float,

    Data      nvarchar(4000)  CONSTRAINT [Data contains JSON]  CHECK (ISJSON(Data)=1),

    MadeIn  AS CAST(JSON_VALUE(Data, '$.MadeIn')            as NVARCHAR(50)) PERSISTED,
    Cost    AS CAST(JSON_VALUE(Data, '$.ManufacturingCost') as float       ),

    INDEX [idx_Product_MadeIn] NONCLUSTERED (MadeIn)
)
        WITH (MEMORY_OPTIMIZED=ON);
```

#### <a name="cross-apply-and-json-functions"></a>CROSS APPLY、JSON 関数

ネイティブにコンパイルされたストアド プロシージャ用のこの CREATE PROCEDURE ステートメントは、前出の CTP 1.1 に関するテキストで言及された、次の機能を表しています。

- CROSS APPLY 演算子。
- JSON 関数。

```tsql
CREATE OR ALTER PROCEDURE ProductList()
    WITH SCHEMABINDING, NATIVE_COMPILATION
as begin
    atomic with (transaction isolation level = snapshot,  language = N'English')

    SELECT
            ProductID, Name, Price, Tags,
            Data,
            JSON_VALUE(Data,'$.MadeIn') AS MadeIn,
            value
        FROM Product
        CROSS APPLY OPENJSON(Data, '$.SalesReasons')
        FOR JSON PATH
end;
```
