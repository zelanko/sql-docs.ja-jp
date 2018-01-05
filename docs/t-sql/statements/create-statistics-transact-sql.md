---
title: "統計情報 (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/04/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- STATISTICS
- STATISTICS_TSQL
- CREATE STATISTICS
- CREATE_STATISTICS_TSQL
dev_langs: TSQL
helpviewer_keywords:
- query optimization statistics [SQL Server], creating
- indexed views [SQL Server], statistics
- FULLSCAN option
- CREATE STATISTICS statement
- filtered statistics [SQL Server]
- creating statistics [SQL Server]
- NORECOMPUTE clause
ms.assetid: b23e2f6b-076c-4e6d-9281-764bdb616ad2
caps.latest.revision: "105"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 088b79e73be6258afc5c664aaf14ba3cad9d2f5f
ms.sourcegitcommit: 4aeedbb88c60a4b035a49754eff48128714ad290
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/05/2018
---
# <a name="create-statistics-transact-sql"></a>CREATE STATISTICS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  テーブル、インデックス付きビュー、または、外部テーブルの 1 つまたは複数の列には、クエリの最適化に関する統計を作成します。 ほとんどのクエリでは、高品質のクエリ プランに必要な統計がクエリ オプティマイザーによって既に生成されていますが、クエリのパフォーマンスを向上させるために CREATE STATISTICS で追加の統計を作成したりクエリのデザインを変更したりする必要がある場合もあります。  
  
 詳細については、次を参照してください。[統計](../../relational-databases/statistics/statistics.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Create statistics on an external table  
CREATE STATISTICS statistics_name   
ON { table_or_indexed_view_name } ( column [ ,...n ] )   
    [ WITH FULLSCAN ] ;  
  
-- Create statistics on a regular table or indexed view  
CREATE STATISTICS statistics_name   
ON { table_or_indexed_view_name } ( column [ ,...n ] )   
    [ WHERE <filter_predicate> ]  
    [ WITH   
        [ [ FULLSCAN   
            [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
          | SAMPLE number { PERCENT | ROWS }   
            [ [ , ] PERSIST_SAMPLE_PERCENT = { ON | OFF } ]    
          | <update_stats_stream_option> [ ,...n ]    
        [ [ , ] NORECOMPUTE ]   
        [ [ , ] INCREMENTAL = { ON | OFF } ] 
        [ [ , ] MAXDOP = max_degree_of_parallelism ]
    ] ;  
  
<filter_predicate> ::=   
    <conjunct> [AND <conjunct>]  
  
<conjunct> ::=  
    <disjunct> | <comparison>  
  
<disjunct> ::=  
        column_name IN (constant ,…)  
  
<comparison> ::=  
        column_name <comparison_op> constant  
  
<comparison_op> ::=  
    IS | IS NOT | = | <> | != | > | >= | !> | < | <= | !<  
    
<update_stats_stream_option> ::=  
    [ STATS_STREAM = stats_stream ]  
    [ ROWCOUNT = numeric_constant ]  
    [ PAGECOUNT = numeric_contant ] 
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
CREATE STATISTICS statistics_name   
    ON [ database_name . [schema_name ] . | schema_name. ] table_name   
    ( column_name  [ ,...n ] )   
    [ WHERE <filter_predicate> ]  
    [ WITH {  
           FULLSCAN   
           | SAMPLE number PERCENT   
      }  
    ]  
[;]  
  
<filter_predicate> ::=   
    <conjunct> [AND <conjunct>]  
  
<conjunct> ::=  
    <disjunct> | <comparison>  
  
<disjunct> ::=  
        column_name IN (constant ,…)  
  
<comparison> ::=  
        column_name <comparison_op> constant  
  
<comparison_op> ::=  
    IS | IS NOT | = | <> | != | > | >= | !> | < | <= | !<  
```  
  
## <a name="arguments"></a>引数  
 *statistics_name*  
 作成する統計の名前です。  
  
 *table_or_indexed_view_name*  
 テーブル、インデックス付きビュー、または外部テーブルには、統計を作成するための名前です。 を別のデータベースで統計を作成するには、修飾テーブル名を指定します。  
  
 *列 [,... n]*  
 統計情報に含まれる 1 つまたは複数の列。 列は、左から右への優先順位にする必要があります。 ヒストグラムを作成する最初の列のみが使用されます。 すべての列では、密度と呼ばれる列間の相関関係の統計が使用されます。  
  
 インデックス キー列として指定できる任意の列を指定できますが、次の例外があります。  
  
-   **Xml**フルテキスト、FILESTREAM 列を指定することはできません。  
  
-   計算列は、データベース設定の ARITHABORT と QUOTED_IDENTIFIER が ON に設定されている場合にのみ指定できます。  
  
-   CLR ユーザー定義型の列は、データ型でバイナリ順がサポートされている場合に指定できます。 ユーザー定義型列のメソッド呼び出しとして定義されている計算列は、メソッドが決定的とマークされている場合に指定できます。  
  
 ここで\<filter_predicate > 統計オブジェクトを作成するときに含める行のサブセットを選択するための式を指定します。 フィルター述語を使用して作成された統計は、フィルター選択された統計情報と呼ばれます。 フィルター述語は単純な比較ロジックを使用し、計算列、UDT 列、空間データ型の列は参照できませんまたは**hierarchyID**データ型の列です。 比較演算子では、NULL リテラルを使用する比較を実行できません。 代わりに、IS NULL 演算子と IS NOT NULL 演算子を使用します。  
  
 次に、Production.BillOfMaterials テーブルのフィルター述語の例をいくつか示します。  
  
 * `WHERE StartDate > '20000101' AND EndDate <= '20000630'`  
  
 * `WHERE ComponentID IN (533, 324, 753)`  
  
 * `WHERE StartDate IN ('20000404', '20000905') AND EndDate IS NOT NULL`  
  
 フィルター述語の詳細については、次を参照してください。 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)です。  
  
 FULLSCAN  
 すべての行をスキャンして統計を計算します。 FULLSCAN と SAMPLE 100 PERCENT は同じ結果になります。 FULLSCAN では SAMPLE オプションは使用できません。  
  
 SQL Server がサンプリングを使用して、統計を作成して、高品質のクエリ プランを作成するために必要なサンプル サイズを決定します。 省略すると、  
  
 サンプル*数*{%|行}  
 テーブルやインデックス付きビューに含まれている行について、クエリ オプティマイザーで統計を作成する際に使用するおおよその割合または数を指定します。 %、*数*は、0 100 からと、行から*数*行の合計数を 0 から指定できます。 クエリ オプティマイザーによってサンプリングされる行の実際の割合や行数が、指定した割合や行数と一致しない場合もあります。 たとえば、データ ページではすべての行がスキャンされます。  
  
 サンプルは、これで、既定のサンプリングに基づくクエリ プランが最適でない特殊な場合に便利です。 ほとんどの場合は、高品質のクエリ プランを作成するために必要なように、クエリ オプティマイザーは、既にサンプリングを使用して、既定では、統計的に有意なサンプル サイズを決定するためにサンプルを指定する必要はありません。  
  
 SAMPLE では FULLSCAN オプションは使用できません。 SAMPLE も FULLSCAN も指定しない場合、既定ではクエリ オプティマイザーはサンプリングしたデータを使用してサンプル サイズを計算します。  
  
 0 PERCENT や 0 ROWS を指定することはお勧めしません。 0 PERCENT または 0 ROWS を指定した場合、統計オブジェクトは作成されますが、統計データは含まれません。  
 
 PERSIST_SAMPLE_PERCENT = {ON |オフ}  
 ときに**ON**、統計サンプリング比率が明示的に指定されていない後続の更新プログラムの作成のサンプリングの割合が保持されます。 ときに**OFF**、統計サンプリング率はサンプリング比率が明示的に指定されていない後続の更新で既定のサンプリングをリセットします。 既定値は**OFF**です。 
 
 **適用されます**: [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] (以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1 CU4) を通じて [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] (以降で [!INCLUDE[ssSQL17](../../includes/sssql17-md.md)] CU1)。    
  
 STATS_STREAM  **=**  *stats_stream*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 NORECOMPUTE  
 自動統計の AUTO_STATISTICS_UPDATE オプションの更新を無効に*statistics_name*です。 このオプションを指定すると、クエリ オプティマイザーが完了の進行中に必要な更新プログラムすべて*statistics_name*および今後の更新を無効にします。  
  
 統計の更新プログラムを再度有効にして、統計情報を削除[DROP STATISTICS](../../t-sql/statements/drop-statistics-transact-sql.md)し、NORECOMPUTE オプションを指定せずに CREATE STATISTICS を実行します。  
  
> [!WARNING]  
>  このオプションを使用すると、最適ではないクエリ プランが作成されることがあります。 このオプションは慎重に使用してください。特に、資格のあるシステム管理者だけが使用することをお勧めします。  
  
 AUTO_STATISTICS_UPDATE オプションの詳細については、次を参照してください。 [ALTER DATABASE SET Options &#40;です。TRANSACT-SQL と #41 です](../../t-sql/statements/alter-database-transact-sql-set-options.md)。 無効にして、統計の更新プログラムを再有効化の詳細については、次を参照してください。[統計](../../relational-databases/statistics/statistics.md)です。  
  
 INCREMENTAL = { ON | OFF }  
 ときに**ON**、作成される統計は、パーティションごとの統計はします。 ときに**OFF**、すべてのパーティションの統計が結合されます。 既定値は**OFF**です。  
  
 パーティションごとの統計がサポートされていない場合は、エラーが生成されます。 次の種類の統計では、増分統計がサポートされていません。  
  
-   ベース テーブルにパーティションで固定されていないインデックスを使用して作成された統計。  
-   Always On の読み取り可能なセカンダリ データベースに対して作成された統計。  
-   読み取り専用のデータベースに対して作成された統計。  
-   フィルター選択されたインデックスに対して作成された統計。  
-   ビューに対して作成された統計。  
-   内部テーブルに対して作成された統計。  
-   空間インデックスまたは XML インデックスを使用して作成された統計。  
  
**適用対象**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
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

## <a name="permissions"></a>アクセス許可  
 これらのアクセス許可のいずれかが必要です。  
  
-   ALTER TABLE  
-   ユーザーがテーブルの所有者  
-   メンバーシップ、 **db_ddladmin**固定データベース ロール  
  
## <a name="general-remarks"></a>全般的な解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]統計を構築する前に、サンプリングされた行を並べ替えるには、tempdb を使用できます。  
  
### <a name="statistics-for-external-tables"></a>外部テーブルの統計  
 外部テーブルの統計を作成するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]外部テーブルに一時的なインポート[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]テーブル、および統計を作成します。 サンプルの統計のサンプリングされた行のみがインポートされます。 場合は、大きな外部テーブルがある場合は、フル スキャンのオプションの代わりに、既定のサンプリングを使用する方が速くなります。  
  
### <a name="statistics-with-a-filtered-condition"></a>条件がフィルター選択された統計情報  
 適切に定義されたデータのサブセットから選択するクエリでは、フィルター選択された統計情報を使用するとクエリのパフォーマンスを向上させることができます。 フィルター選択された統計情報では、統計情報に含まれるデータのサブセットを選択するために WHERE 句でフィルター述語を使用します。  
  
### <a name="when-to-use-create-statistics"></a>CREATE STATISTICS を使用する場合  
 CREATE STATISTICS を使用する場合の詳細については、次を参照してください。[統計](../../relational-databases/statistics/statistics.md)です。  
  
### <a name="referencing-dependencies-for-filtered-statistics"></a>フィルター選択された統計情報の参照による依存関係  
 [Sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)カタログ ビューは、参照元の依存関係としてフィルター選択された統計情報の述語内の各列を追跡します。 フィルター選択された統計情報の述語で定義されているテーブル列の定義を削除、名前変更、または変更することはできないので、フィルター選択された統計情報を作成する前に、テーブル列で実行する操作を検討してください。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
* テーブルの外部では、統計を更新することはできません。 外部テーブルの統計を更新するには、削除し、統計を再作成します。  
* 統計オブジェクトごとの最大 64 個の列を一覧表示できます。
* MAXDOP オプションは、STATS_STREAM、ROWCOUNT および PAGECOUNT オプションと互換性がありません。
  
## <a name="examples"></a>使用例  

### <a name="examples-use-the-adventureworks-database"></a>例では、AdventureWorks データベースを使用します。  

### <a name="a-using-create-statistics-with-sample-number-percent"></a>A. CREATE STATISTICS を SAMPLE number PERCENT と共に使用する  
 次の例を作成、`ContactMail1`の 5% のランダムなサンプルを使用して、統計、`BusinessEntityID`と`EmailPromotion`の列、`Contact`のテーブル、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```sql  
CREATE STATISTICS ContactMail1  
    ON Person.Person (BusinessEntityID, EmailPromotion)  
    WITH SAMPLE 5 PERCENT;  
```  
  
### <a name="b-using-create-statistics-with-fullscan-and-norecompute"></a>B. CREATE STATISTICS を FULLSCAN および NORECOMPUTE と共に使用する  
 次の例では、`ContactMail2` テーブルの `BusinessEntityID` 列と `EmailPromotion` 列のすべての行を対象に、`Contact` 統計情報を作成し、統計の自動再計算を無効にします。  
  
```sql  
CREATE STATISTICS NamePurchase  
    ON AdventureWorks2012.Person.Person (BusinessEntityID, EmailPromotion)  
    WITH FULLSCAN, NORECOMPUTE;  
```  
  
### <a name="c-using-create-statistics-to-create-filtered-statistics"></a>C. CREATE STATISTICS を使用してフィルター選択された統計情報を作成する  
 次の例では、フィルター選択された統計情報 `ContactPromotion1` を作成します。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 50% のデータをサンプリングしを持つ行を選択し、 `EmailPromotion` 2 に等しい。  
  
```sql  
CREATE STATISTICS ContactPromotion1  
    ON Person.Person (BusinessEntityID, LastName, EmailPromotion)  
WHERE EmailPromotion = 2  
WITH SAMPLE 50 PERCENT;  
GO  
```  
  
### <a name="d-create-statistics-on-an-external-table"></a>D. 統計、外部テーブルを作成します。  
 列の一覧を提供するだけでなく、外部テーブルの統計を作成するときにする必要がある唯一の意思決定は、行をサンプリングすることによって、またはすべての行をスキャンして統計を作成するかどうかです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フル スキャンのオプション、統計を作成する一時テーブルに外部テーブルからデータをインポートがかなり長くかかります。 大きなテーブルの場合は、既定のサンプリング方法通常で十分です。  
  
```sql  
--Create statistics on an external table and use default sampling.  
CREATE STATISTICS CustomerStats1 ON DimCustomer (CustomerKey, EmailAddress);  
  
--Create statistics on an external table and scan all the rows  
CREATE STATISTICS CustomerStats1 ON DimCustomer (CustomerKey, EmailAddress) WITH FULLSCAN;  
```  

### <a name="e-using-create-statistics-with-fullscan-and-persistsamplepercent"></a>E. CREATE STATISTICS を FULLSCAN および PERSIST_SAMPLE_PERCENT で使用します。  
 次の例を作成、`ContactMail2`のすべての行の統計情報、`BusinessEntityID`と`EmailPromotion`の列、`Contact`テーブルし、明示的に必要ないのは後続のすべての更新プログラムを指定、サンプリングの 100% のサンプリング比率を設定割合です。  
  
```sql  
CREATE STATISTICS NamePurchase  
    ON AdventureWorks2012.Person.Person (BusinessEntityID, EmailPromotion)  
    WITH FULLSCAN, PERSIST_SAMPLE_PERCENT = ON;  
```  
  
### <a name="examples-using-adventureworksdw-database"></a>AdventureWorksDW データベースを使用する例。 
  
### <a name="f-create-statistics-on-two-columns"></a>F. 2 つの列に統計を作成します。  
 次の例を作成、`CustomerStats1`に基づいて統計、`CustomerKey`と`EmailAddress`の列、`DimCustomer`テーブル。 内の行の統計的に有意なサンプルに基づいて統計が作成、`Customer`テーブル。  
  
```sql  
CREATE STATISTICS CustomerStats1 ON DimCustomer (CustomerKey, EmailAddress);  
```  
  
### <a name="g-create-statistics-by-using-a-full-scan"></a>G. フル スキャンを使用して統計を作成します。  
 次の例を作成、`CustomerStatsFullScan`内の行をすべてスキャンに基づいて、統計、`DimCustomer`テーブル。  
  
```sql  
CREATE STATISTICS CustomerStatsFullScan 
ON DimCustomer (CustomerKey, EmailAddress) WITH FULLSCAN;  
```  
  
### <a name="h-create-statistics-by-specifying-the-sample-percentage"></a>H. サンプルの割合を指定して統計を作成します。  
 次の例を作成、`CustomerStatsSampleScan`内の行の 50% のスキャンに基づく、統計情報、`DimCustomer`テーブル。  
  
```sql  
CREATE STATISTICS CustomerStatsSampleScan 
ON DimCustomer (CustomerKey, EmailAddress) WITH SAMPLE 50 PERCENT;  
```  
  
## <a name="see-also"></a>参照  
 [統計情報](../../relational-databases/statistics/statistics.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)   
 [sp_updatestats &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updatestats-transact-sql.md)   
 [DBCC SHOW_STATISTICS &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-show-statistics-transact-sql.md)   
 [DROP STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/drop-statistics-transact-sql.md)   
 [sys.stats &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-stats-transact-sql.md)   
 [sys.stats_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-stats-columns-transact-sql.md)  
  
  

