---
title: "UPDATE STATISTICS (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/04/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATE STATISTICS
- UPDATE_STATISTICS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- updating statistics
- query optimization statistics [SQL Server], updating
- UPDATE STATISTICS statement
- statistical information [SQL Server], updating
ms.assetid: 919158f2-38d0-4f68-82ab-e1633bd0d308
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7c69949773ff1dae533c98d087780a2f4b436b62
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="update-statistics-transact-sql"></a>UPDATE STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  テーブルまたはインデックス付きビューで、クエリ最適化に関する統計を更新します。 既定では、クエリ オプティマイザー既に統計を更新、クエリ プランを向上させるために必要に応じて場合によっては、UPDATE STATISTICS またはストアド プロシージャを使用してクエリのパフォーマンスを向上できます[sp_updatestats](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md)を既定の更新より頻繁に統計を更新します。  
  
 統計を更新すると、クエリが最新の統計を使用してコンパイルされるようになります。 ただし、統計の更新によりクエリが再コンパイルされます。 パフォーマンスの向上を目的とする場合、クエリ プランの改善とクエリの再コンパイルに要する時間の間にはトレードオフの関係があるため、あまり頻繁に統計を更新しないようにすることをお勧めします。 実際のトレードオフはアプリケーションによって異なります。 統計の更新では、tempdb を使用して、統計を作成するための行のサンプルを並べ替えます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
UPDATE STATISTICS table_or_indexed_view_name   
    [   
        {   
            { index_or_statistics__name }  
          | ( { index_or_statistics_name } [ ,...n ] )   
                }  
    ]   
    [    WITH   
        [  
            FULLSCAN   
              [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
            | SAMPLE number { PERCENT | ROWS }   
              [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
            | RESAMPLE   
              [ ON PARTITIONS ( { <partition_number> | <range> } [, …n] ) ]  
            | <update_stats_stream_option> [ ,...n ]  
        ]   
        [ [ , ] [ ALL | COLUMNS | INDEX ]   
        [ [ , ] NORECOMPUTE ]   
        [ [ , ] INCREMENTAL = { ON | OFF } ] 
        [ [ , ] MAXDOP = max_degree_of_parallelism ] 
    ] ;  
  
<update_stats_stream_option> ::=  
    [ STATS_STREAM = stats_stream ]  
    [ ROWCOUNT = numeric_constant ]  
    [ PAGECOUNT = numeric_contant ]  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
UPDATE STATISTICS schema_name . ] table_name   
    [ ( { statistics_name | index_name } ) ]  
    [ WITH   
       {  
              FULLSCAN   
            | SAMPLE number PERCENT   
            | RESAMPLE   
        }  
    ]  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *table_or_indexed_view_name*  
 テーブルまたはインデックス付きビューを含む、統計オブジェクトの名前です。  
  
 *index_or_statistics_name*  
 統計の更新対象のインデックスの名前、または更新する統計の名前を指定します。 場合*index_or_statistics_name*が指定されていない、クエリ オプティマイザーがテーブルまたはインデックス付きビューのすべての統計を更新します。 これには、CREATE STATISTICS ステートメントを使用して作成した統計、AUTO_CREATE_STATISTICS がオンの場合に作成される 1 列ずつの統計、およびインデックスに対して作成された統計が含まれます。  
  
 AUTO_CREATE_STATISTICS の詳細については、次を参照してください。 [ALTER DATABASE SET Options &#40;です。TRANSACT-SQL と #41 です](../../t-sql/statements/alter-database-transact-sql-set-options.md)。 使用してテーブルまたはビューのすべてのインデックスを表示するには、 [sp_helpindex](../../relational-databases/system-stored-procedures/sp-helpindex-transact-sql.md)です。  
  
 FULLSCAN  
 テーブルまたはインデックス付きビュー内のすべての行をスキャンして統計を計算します。 FULLSCAN と SAMPLE 100 PERCENT は同じ結果になります。 FULLSCAN では SAMPLE オプションは使用できません。  
  
 サンプル*数*{%|行}  
 テーブルやインデックス付きビューに含まれている行について、クエリ オプティマイザーで統計を更新する際に使用するおおよその割合または数を指定します。 %、*数*は、0 100 からと、行から*数*行の合計数を 0 から指定できます。 クエリ オプティマイザーによってサンプリングされる行の実際の割合や行数が、指定した割合や行数と一致しない場合もあります。 たとえば、データ ページではすべての行がスキャンされます。  
  
 サンプルは、これで、既定のサンプリングに基づくクエリ プランが最適でない特殊な場合に便利です。 既定ではクエリ オプティマイザーはサンプリングを使用して統計的に有意なサンプル サイズを決定するため、SAMPLE を指定する必要はほとんどありませんが、高品質のクエリ プランを作成する場合は、SAMPLE が必要になります。 
 
以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]、互換性レベルが 130 を使用して、統計コレクションのパフォーマンスを向上する場合は、統計を作成するデータのサンプリングを並列で実行します。 テーブルのサイズが一定のしきい値を超えたときに、クエリ オプティマイザーは parallel のサンプルの統計情報を使用します。 
   
 SAMPLE では FULLSCAN オプションは使用できません。 SAMPLE も FULLSCAN も指定しない場合、既定ではクエリ オプティマイザーはサンプリングしたデータを使用してサンプル サイズを計算します。  
  
 0 PERCENT や 0 ROWS を指定することはお勧めしません。 0 PERCENT または 0 ROWS を指定した場合、統計オブジェクトは更新されますが、統計データは含まれません。  
  
 ほとんどのワークロードのフル スキャンが必要でないと既定のサンプリングが適切です。  
ただしは多様なデータ分布に影響する特定のワークロードは、増加したサンプル サイズ、または完全なスキャンでも必要があります。  
詳細については、次を参照してください。、 [CSS SQL エスカレーション Services ブログ](http://blogs.msdn.com/b/psssql/archive/2010/07/09/sampling-can-produce-less-accurate-statistics-if-the-data-is-not-evenly-distributed.aspx)です。  
  
 RESAMPLE  
 最新のサンプル レートを使用して各統計を更新します。  
  
 RESAMPLE を使用すると、フル テーブル スキャンが実行される場合があります。 たとえば、インデックスの統計では、サンプル レートを取得するためにフル テーブル スキャンが使用されます。 サンプル オプション (SAMPLE、FULLSCAN、RESAMPLE) がいずれも指定されていなければ、既定ではクエリ オプティマイザーはデータをサンプリングしてサンプル サイズを計算します。  

PERSIST_SAMPLE_PERCENT = {ON |オフ}  
ときに**ON**統計のサンプリング比率が明示的に指定されていない後続の更新プログラム セット サンプリングの割合が保持されます。 ときに**OFF**、統計サンプリング率はサンプリング比率が明示的に指定されていない後続の更新で既定のサンプリングをリセットします。 既定値は**OFF**です。 
 
 > [!NOTE]
 > AUTO_UPDATE_STATISTICS が実行された場合は、使用可能な場合は、永続化されたサンプリング率を使用してまたは以外の場合は、既定のサンプリング比率を使用します。
 > RESAMPLE は、このオプションの動作は影響しません。
 
 > [!TIP] 
 > [DBCC SHOW_STATISTICS](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)と[sys.dm_db_stats_properties](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md)選択された統計情報の永続化されたサンプルの割合の値を公開します。
 
 **適用されます**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (以降で [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] SP1 CU4) を通じて [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (以降で [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU1)。  
 
 パーティションで ({ \<partition_number > |\<範囲 >}[、... n])を再計算、および全体の統計を作成するマージし、ON PARTITIONS 句で指定されたパーティションをカバーするリーフ レベルの統計を強制します。 異なるサンプル レートで構築されたパーティションの統計はマージできないため、WITH RESAMPLE が必要になります。  
  
**適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 ALL | COLUMNS | INDEX  
 すべての既存の統計、1 つ以上の列で作成された統計、またはインデックスに対して作成された統計を更新します。 何も指定しない場合は、テーブルまたはインデックス付きビューのすべての統計が更新されます。  
  
 NORECOMPUTE  
 指定した統計の自動統計更新オプション (AUTO_UPDATE_STATISTICS) を無効にします。 このオプションを指定すると、現在の更新は実行され、その後の更新が無効になります。  
  
 AUTO_UPDATE_STATISTICS オプションの動作を再度有効にする、NORECOMPUTE オプションを指定せずに UPDATE STATISTICS を再実行、または実行**sp_autostats**です。  
  
> [!WARNING]  
>  このオプションを使用すると、最適ではないクエリ プランが作成されることがあります。 このオプションは慎重に使用してください。特に、資格のあるシステム管理者だけが使用することをお勧めします。  
  
 AUTO_STATISTICS_UPDATE オプションの詳細については、次を参照してください。 [ALTER DATABASE SET Options &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql-set-options.md)  
  
 INCREMENTAL = { ON | OFF }  
 ときに**ON**パーティションの統計情報に従って、統計を再作成します。 ときに**OFF**、統計ツリーが削除されると[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]統計が再計算します。 既定値は**OFF**です。  
  
 パーティションごとの統計がサポートされていない場合は、エラーが生成されます。 次の種類の統計では、増分統計がサポートされていません。  
  
-   ベース テーブルにパーティションで固定されていないインデックスを使用して作成された統計。  
-   Always On の読み取り可能なセカンダリ データベースに対して作成された統計。  
-   読み取り専用のデータベースに対して作成された統計。  
-   フィルター選択されたインデックスに対して作成された統計。  
-   ビューに対して作成された統計。  
-   内部テーブルに対して作成された統計。  
-   空間インデックスまたは XML インデックスを使用して作成された統計。  
  
**適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]

MAXDOP = *max_degree_of_parallelism*  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL17](../../includes/sssql17-md.md)]CU3)。  
  
 上書き、**並列処理の次数の最大**統計操作の実行中の構成オプション。 詳細については、「 [max degree of parallelism サーバー構成オプションの構成](../../database-engine/configure-windows/configure-the-max-degree-of-parallelism-server-configuration-option.md)」を参照してください。 並列プランの実行で使用されるプロセッサ数を制限するには、MAXDOP を使用します。 最大数は 64 プロセッサです。  
  
 *max_degree_of_parallelism*を指定できます。  
  
 @shouldalert  
 並列プラン生成を抑制します。  
  
 \>1  
 指定した数以内の現在のシステム ワークロードに基づいて並列統計操作で使用されるプロセッサの最大数を制限します。  
  
 0 (既定値)  
 現在のシステム ワークロードに基づいて、実際の数以下のプロセッサを使用します。  
  
 \<update_stats_stream_option >[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  

## <a name="remarks"></a>解説  
  
## <a name="when-to-use-update-statistics"></a>UPDATE STATISTICS を使用する場合  
 詳細について UPDATE STATISTICS を使用する場合は、次を参照してください。[統計](../../relational-databases/statistics/statistics.md)です。  

## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
* テーブルの外部では、統計を更新することはできません。 外部テーブルの統計を更新するには、削除し、統計を再作成します。  
* MAXDOP オプションは、STATS_STREAM、ROWCOUNT および PAGECOUNT オプションと互換性がありません。

## <a name="updating-all-statistics-with-spupdatestats"></a>sp_updatestats によるすべての統計の更新  
 データベース内のすべてのユーザー定義および内部テーブルの統計を更新する方法については、ストアド プロシージャ [sp_updatestats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md) の説明を参照してください。 たとえば次のコマンドは、sp_updatestats を呼び出してデータベースのすべての統計を更新します。  
  
```sql  
EXEC sp_updatestats;  
```  
  
## <a name="determining-the-last-statistics-update"></a>統計の最終更新日の特定  
 統計の最終更新日を調べるには、 [STATS_DATE](../../t-sql/functions/stats-date-transact-sql.md) 関数を使用します。  
  
## <a name="pdw--sql-data-warehouse"></a>PDW SQL データ ウェアハウス/  
 PDW では、次の構文はサポートされていない SQL データ ウェアハウス/  
  
```sql  
update statistics t1 (a,b);   
```  
  
```sql  
update statistics t1 (a) with sample 10 rows;  
```  
  
```sql  
update statistics t1 (a) with NORECOMPUTE;  
```  
  
```sql  
update statistics t1 (a) with INCREMENTAL=ON;  
```  
  
```sql  
update statistics t1 (a) with stats_stream = 0x01;  
```  
  
## <a name="permissions"></a>アクセス許可  
 テーブルまたはビューに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-update-all-statistics-on-a-table"></a>A. テーブルのすべての統計を更新する  
 次の例は、上のすべてのインデックスの統計を更新、`SalesOrderDetail`テーブル。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE STATISTICS Sales.SalesOrderDetail;  
GO  
```  
  
### <a name="b-update-the-statistics-for-an-index"></a>B. 1 つのインデックスの統計を更新する  
 次の例の統計を更新する、`AK_SalesOrderDetail_rowguid`のインデックス、`SalesOrderDetail`テーブル。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE STATISTICS Sales.SalesOrderDetail AK_SalesOrderDetail_rowguid;  
GO  
```  
  
### <a name="c-update-statistics-by-using-50-percent-sampling"></a>C. 50% サンプリングで統計を更新する  
 次の例を作成しの統計を更新し、`Name`と`ProductNumber`内の列、`Product`テーブル。  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE STATISTICS Products  
    ON Production.Product ([Name], ProductNumber)  
    WITH SAMPLE 50 PERCENT  
-- Time passes. The UPDATE STATISTICS statement is then executed.  
UPDATE STATISTICS Production.Product(Products)   
    WITH SAMPLE 50 PERCENT;  
```  
  
### <a name="d-update-statistics-by-using-fullscan-and-norecompute"></a>D. FULLSCAN および NORECOMPUTE を使用して統計を更新する  
 次の例の更新プログラム、`Products`内の統計、`Product`テーブルで、すべての行でフル スキャンの強制、`Product`テーブル、および自動の統計をオフに、`Products`統計。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE STATISTICS Production.Product(Products)  
    WITH FULLSCAN, NORECOMPUTE;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-update-statistics-on-a-table"></a>E. テーブルで統計を更新します。  
 次の例の更新プログラム、`CustomerStats1`に関する統計情報、`Customer`テーブル。  
  
```sql  
UPDATE STATISTICS Customer ( CustomerStats1 );  
```  
  
### <a name="f-update-statistics-by-using-a-full-scan"></a>F. フル スキャンを使用して、統計の更新  
 次の例の更新プログラム、`CustomerStats1`内の行をすべてスキャンに基づいて、統計、`Customer`テーブル。  
  
```sql  
UPDATE STATISTICS Customer (CustomerStats1) WITH FULLSCAN;  
```  
  
### <a name="g-update-all-statistics-on-a-table"></a>G. テーブルのすべての統計を更新する  
 次の例は、すべての統計を更新、`Customer`テーブル。  
  
```sql  
UPDATE STATISTICS Customer;  
```  
  
## <a name="see-also"></a>参照  
 [統計情報](../../relational-databases/statistics/statistics.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [CREATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/create-statistics-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sp_autostats &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-autostats-transact-sql.md)   
 [sp_updatestats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md)   
 [STATS_DATE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/stats-date-transact-sql.md)  
 [sys.dm_db_stats_properties (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-properties-transact-sql.md) [sys.dm_db_stats_histogram (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-stats-histogram-transact-sql.md) 
  



