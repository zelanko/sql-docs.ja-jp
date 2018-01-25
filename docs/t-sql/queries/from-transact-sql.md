---
title: "(TRANSACT-SQL) から |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- JOIN
- FROM_TSQL
- FROM
- JOIN_TSQL
- CROSS_TSQL
- CROSS_APPLY_TSQL
- APPLY_TSQL
- CROSS_JOIN_TSQL
dev_langs: TSQL
helpviewer_keywords:
- OUTER APPLY operator
- hints [SQL Server], FROM clause
- SELECT statement [SQL Server], FROM clause
- ISO syntax
- DELETE statement [SQL Server], FROM clause
- CROSS APPLY operator
- FROM clause
- APPLY operator
- joins [SQL Server], FROM clause
- UPDATE statement [SQL Server], FROM clause
- derived tables
ms.assetid: 36b19e68-94f6-4539-aeb1-79f5312e4263
caps.latest.revision: "97"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 9ddc3ee291d4e3b498dd6dfd9bbb49ca4299bea6
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="from-transact-sql"></a>FROM (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  テーブル、ビュー、派生テーブル、および内のステートメントを DELETE、SELECT、および UPDATE の結合テーブルの使用を示す[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。 SELECT ステートメントでは、選択リストに定数、変数、および数式のみが含まれて列名が含まれていない場合を除き、FROM 句を指定する必要があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
[ FROM { <table_source> } [ ,...n ] ]   
<table_source> ::=   
{  
    table_or_view_name [ [ AS ] table_alias ]   
        [ <tablesample_clause> ]   
        [ WITH ( < table_hint > [ [ , ]...n ] ) ]   
    | rowset_function [ [ AS ] table_alias ]   
        [ ( bulk_column_alias [ ,...n ] ) ]   
    | user_defined_function [ [ AS ] table_alias ]  
    | OPENXML <openxml_clause>   
    | derived_table [ [ AS ] table_alias ] [ ( column_alias [ ,...n ] ) ]   
    | <joined_table>   
    | <pivoted_table>   
    | <unpivoted_table>  
    | @variable [ [ AS ] table_alias ]  
    | @variable.function_call ( expression [ ,...n ] )   
        [ [ AS ] table_alias ] [ (column_alias [ ,...n ] ) ]  
    | FOR SYSTEM_TIME <system_time>   
}  
<tablesample_clause> ::=  
    TABLESAMPLE [SYSTEM] ( sample_number [ PERCENT | ROWS ] )   
        [ REPEATABLE ( repeat_seed ) ]   
  
<joined_table> ::=   
{  
    <table_source> <join_type> <table_source> ON <search_condition>   
    | <table_source> CROSS JOIN <table_source>   
    | left_table_source { CROSS | OUTER } APPLY right_table_source   
    | [ ( ] <joined_table> [ ) ]   
}  
<join_type> ::=   
    [ { INNER | { { LEFT | RIGHT | FULL } [ OUTER ] } } [ <join_hint> ] ]  
    JOIN  
  
<pivoted_table> ::=  
    table_source PIVOT <pivot_clause> [ [ AS ] table_alias ]  
  
<pivot_clause> ::=  
        ( aggregate_function ( value_column [ [ , ]...n ])   
        FOR pivot_column   
        IN ( <column_list> )   
    )   
  
<unpivoted_table> ::=  
    table_source UNPIVOT <unpivot_clause> [ [ AS ] table_alias ]  
  
<unpivot_clause> ::=  
    ( value_column FOR pivot_column IN ( <column_list> ) )   
  
<column_list> ::=  
    column_name [ ,...n ]   
  
<system_time> ::=  
{  
       AS OF <date_time>  
    |  FROM <start_date_time> TO <end_date_time>  
    |  BETWEEN <start_date_time> AND <end_date_time>  
    |  CONTAINED IN (<start_date_time> , <end_date_time>)   
    |  ALL  
}  
  
    <date_time>::=  
        <date_time_literal> | @date_time_variable  
  
    <start_date_time>::=  
        <date_time_literal> | @date_time_variable  
  
    <end_date_time>::=  
        <date_time_literal> | @date_time_variable  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
FROM { <table_source> [ ,...n ] }  
  
<table_source> ::=   
{  
    [ database_name . [ schema_name ] . | schema_name . ] table_or_view_name [ AS ] table_or_view_alias  
    | derived_table [ AS ] table_alias [ ( column_alias [ ,...n ] ) ]  
    | <joined_table>  
}  
  
<joined_table> ::=   
{  
    <table_source> <join_type> <table_source> ON search_condition   
    | <table_source> CROSS JOIN <table_source> 
    | left_table_source { CROSS | OUTER } APPLY right_table_source   
    | [ ( ] <joined_table> [ ) ]   
}  
  
<join_type> ::=   
    [ INNER ] [ <join hint> ] JOIN  
    | LEFT  [ OUTER ] JOIN  
    | RIGHT [ OUTER ] JOIN  
    | FULL  [ OUTER ] JOIN  
  
<join_hint> ::=   
    REDUCE  
    | REPLICATE  
    | REDISTRIBUTE  
```  
  
## <a name="arguments"></a>引数  
\<table_source>  
 使用する別名の有無は、テーブル、ビュー、テーブル変数、または派生テーブル ソースを指定します、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 1 つのステートメント内で 256 個までのテーブル ソースを使用できますが、この上限値は、使用可能なメモリとクエリ内の他の式の複雑さに応じて変化します。 個別のクエリは、256 個までのテーブル ソースをサポートできません。  
  
> [!NOTE]  
>  クエリのパフォーマンスは、クエリで参照される多くのテーブルによって低下する可能性があります。 コンパイルと最適化にかかる時間も、追加の要素によって影響を受けます。 インデックスおよびインデックス付きビューごとに存在するが含まれます\<table_source > のサイズ、 \<select_list > の SELECT ステートメントにします。  
  
 FROM キーワードの後のテーブル ソースの順序は、返される結果セットには影響しません。 FROM 句内に重複した名前を指定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] はエラーを返します。  
  
 *table_or_view_name*  
 テーブルまたはビューの名前です。  
  
 テーブルまたはビューが別のデータベースの同じインスタンスに存在するかどうかは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、形式で完全修飾名を使用して*データベース*.*スキーマ*.*object_name*です。  
  
 インスタンスの外部にテーブルまたはビューが存在するかどうかは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]l、4 部構成の名前を使用して、フォームで*linked_server*.*カタログ*.*スキーマ*.*オブジェクト*です。 詳細については、「 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)からデータにアクセスする方法について説明します。 使用して作成されますが、4 部構成の名前、 [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md)関数のように、名前のサーバー部分は、リモート テーブル ソースを指定するも使用できます。 OPENDATASOURCE を指定すると、 *database_name*と*schema_name*がすべてのデータ ソースに適用し、は、リモート オブジェクトにアクセスする OLE DB プロバイダーの機能の対象になります。  
  
 [AS] *table_alias*  
 エイリアス*table_source*利便性のために、またはテーブルまたはビューで、自己結合を区別またはサブクエリを使用できます。 別名にはテーブル名を短縮したものが指定されることが多く、結合されたテーブルの特定の列を参照するために使用されます。 同じ列名が、結合の 1 つ以上のテーブルに存在する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]列名は、テーブル名、ビューの名前または別名で修飾する必要があります。 別名が定義されている場合、テーブル名は使用できません。  
  
 派生テーブル、行セットまたはテーブル値関数または演算子句 (PIVOT や UNPIVOT) を使用する場合、必要な*table_alias*句の末尾には、グループ化列を含むすべての列に関連付けられているテーブル名返されます。  
  
 WITH (\<table_hint> )  
 クエリ オプティマイザーが、このテーブルを使用して、このステートメントに対し最適化またはロックを使用することを指定します。 詳細については、「[テーブル ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)」を参照してください。  
  
 *rowset_function*  

**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  

  
 OPENROWSET など、テーブル参照の代わりに使用できるオブジェクトを返す行セット関数のいずれかを指定します。 行セット関数の一覧の詳細については、次を参照してください。[行セット関数 &#40;です。TRANSACT-SQL と #41 です](../../t-sql/functions/rowset-functions-transact-sql.md)。  
  
 OPENROWSET 関数および OPENQUERY 関数を使用したリモート オブジェクトの指定は、そのオブジェクトにアクセスする OLE DB プロバイダーの機能に依存します。  
  
 *bulk_column_alias*  

**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  

  
 結果セット内の列名に対する別名です。このパラメーターは省略可能です。 列の別名は、BULK オプションが指定された OPENROWSET 関数を使用する SELECT ステートメント内でのみ使用できます。 使用すると*bulk_column_alias*ファイル内の列と同じ順序で各テーブル列の別名を指定します。  
  
> [!NOTE]  
>  この別名は、XML 形式のファイルの COLUMN 要素内に NAME 属性が存在する場合は、それを上書きします。  
  
 *user_defined_function*  
 テーブル値関数を指定します。  
  
 OPENXML \<openxml_clause>  

**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  

  
 XML ドキュメントに対して行セット ビューを提供します。 詳細については、次を参照してください。 [OPENXML &#40;です。TRANSACT-SQL と #41 です](../../t-sql/functions/openxml-transact-sql.md)。  
  
 *derived_table*  
 データベースから行を取得するサブクエリです。 *derived_table*外側のクエリに入力として使用されます。  
  
 *派生* *_table*使用できる、[!INCLUDE[tsql](../../includes/tsql-md.md)]テーブル値コンス トラクター機能を複数の行を指定します。 たとえば、 `SELECT * FROM (VALUES (1, 2), (3, 4), (5, 6), (7, 8), (9, 10) ) AS MyTable(a, b);`のようにします。 詳細については、次を参照してください。[テーブル値コンス トラクターと #40 です。TRANSACT-SQL と #41 です](../../t-sql/queries/table-value-constructor-transact-sql.md)。  
  
 *column_alias*  
 派生テーブルの結果セット内の列名に対する別名です。このパラメーターは省略可能です。 選択リストの各列の別名を 1 つずつ含みます。列の別名リスト全体をかっこで囲みます。  
  
 *table_or_view_name* FOR SYSTEM_TIME \<system_time >  

**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  

  
 データの特定のバージョンが、指定された時間的なテーブルとそのシステムのバージョン情報のリンクの履歴テーブルから返されることを指定します。  
  
\<tablesample_clause>  
 テーブルからのデータのサンプルが返されることを指定します。 サンプルは、概数になる可能性があります。 この句は、SELECT、UPDATE、または DELETE ステートメント内の主テーブルまたは結合テーブルで使用できます。 TABLESAMPLE はビューを使用して指定できません。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にアップグレードされたデータベースに対して TABLESAMPLE を使用するときは、データベースの互換性レベルは 110 以上に設定され、再帰共通テーブル式 (CTE) クエリでは PIVOT は許可されません。 詳細については、「[ALTER DATABASE 互換性レベル &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)」を参照してください。  
  
 SYSTEM  
 ISO 標準で指定された、実装に依存するサンプリング方法です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、これは、唯一のサンプリング方法と、既定で適用されます。 SYSTEM は、サンプルとしてテーブルからページがランダムに選択され、それらのページのすべての行がサンプル サブセットとして返される、ページ ベースのサンプリング方法を適用します。  
  
 *sample_number*  
 行数または行数に対応する割合を表す真数または概数値の定数値式です。 PERCENT を指定したときに*sample_number*暗黙的に変換されます、 **float**値。 それ以外の場合、これはに変換**bigint**です。 PERCENT は既定値です。  
  
 PERCENT  
 指定する、 *sample_number*テーブルの行の割合は、テーブルから取得する必要があります。 PERCENT が指定されている場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は指定された割合の概数を返します。 PERCENT が指定されている場合、 *sample_number*式は、0 ~ 100 の値に評価する必要があります。  
  
 ROWS  
 つまり約を指定します*sample_number*の行が取得されます。 行を指定すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]指定数の行の概数を返します。 行を指定すると、 *sample_number*式は、0 より大きい整数値に評価される必要があります。  
  
 REPEATABLE  
 選択されたサンプルを再度返すことができることを示します。 指定すると、同じ*repeat_seed*値、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は、テーブル内の行に変更が加えされていない限り、同じ行のサブセットを返します。 指定すると、別*repeat_seed*値、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]返す可能性がありますをいくつかの異なるテーブル内の行のサンプルはします。 テーブルに対する挿入、更新、削除、インデックスの再構築またはデフラグ、およびデータベースの復元またはアタッチは、変更と見なされます。  
  
 *repeat_seed*  
 によって使用される整数の定数式は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]乱数を生成します。 *repeat_seed*は**bigint**です。 場合*repeat_seed*が指定されていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]値をランダムに割り当てます。 特定の*repeat_seed*値、サンプルの結果は常に同じテーブルに変更が適用されていない場合。 *Repeat_seed*式は、0 より大きい整数に評価される必要があります。  
  
 \<joined_table>  
 2 つ以上のテーブルが組み合わされた結果セットです。 複数の結合については、かっこを使って結合の順序を変更できます。  
  
\<join_type>  
 結合操作の種類を指定します。  
  
 **内部**  
 一致するすべての行をペアで返すことを指定します。 両方のテーブルで一致しない行は廃棄します。 結合の種類が指定されていない場合は、これが既定値になります。  
  
 FULL [ OUTER ]  
 結合条件に合わない左側または右側のテーブルの行も結果セットに含まれ、他方のテーブルに対応する出力列は NULL に設定されることを指定します。 この処理は、INNER JOIN によって通常返される行も含めて、すべての行を返します。  
  
 LEFT [ OUTER ]  
 内部結合によって返されるすべての行に加えて、結合条件に合わない左側のテーブルのすべての行も結果セットに含まれます。右側のテーブルからの出力列は NULL に設定されることを指定します。  
  
 RIGHT [OUTER]  
 内部結合によって返されるすべての行に加えて、結合条件に合わない右側のテーブルのすべての行も結果セットに含まれます。左側のテーブルからの出力列は NULL に設定されることを指定します。  
  
\<join_hint>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と[!INCLUDE[ssSDS](../../includes/sssds-md.md)]、ことを指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クエリ オプティマイザーがクエリの FROM 句で指定される結合ごと、1 つの結合ヒントまたは実行アルゴリズムを使用します。 詳細については、次を参照してください。[結合ヒント &#40;です。TRANSACT-SQL と #41 です](../../t-sql/queries/hints-transact-sql-join.md)。  
  
 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、2 つのディストリビューションの互換性のない列上の内部結合にこれらの結合ヒントを適用します。 クエリの処理中に発生するデータの移動量を制限することでクエリのパフォーマンスを向上することができます。 許容される結合のヒント:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]とおりです。  
  
 削減  
 互換性のある 2 つのディストリビューションの互換性のないテーブルを作成するために、テーブルの結合の右側に移動する行の数を減らします。 REDUCE ヒントは、半結合のヒントとも呼ばれます。  
  
 REPLICATE  
 値を結合する列のすべてのノードにレプリケートされる結合の左側にあるテーブルからさせます。 右側のテーブルは、これらの列のレプリケートされたバージョンに参加しています。  
  
 再配布します。  
 JOIN 句で指定された列に配布するフォースの 2 つのデータ ソース。 分散テーブル[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]シャッフル移動を実行します。 レプリケートされたテーブルの[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]トリムの移動を実行します。 これらの移動の種類を理解するには、「についてのクエリ プラン」のトピックで「DMS クエリ操作を計画する」セクションを参照してください。、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。 このヒントは、クエリ プランは、ディストリビューションの互換性のない結合を解決するのには、ブロードキャストの移動を使用している場合、パフォーマンスを向上させることができます。  
  
 JOIN  
 指定されたテーブル ソースまたはビューの間で、指定された結合操作が行われることを指定します。  
  
 ON \<search_condition>  
 結合するときの条件を指定します。 列と比較演算子はよく使用されますが、条件で任意の結合述語を指定できます。たとえば、次のようになります。  
  
```sql
SELECT p.ProductID, v.BusinessEntityID  
FROM Production.Product AS p   
JOIN Purchasing.ProductVendor AS v  
ON (p.ProductID = v.ProductID);  
  
```  
  
 列に結合条件を指定する場合、使用される列は、同じ列名、同じデータ型である必要はありません。ただし、データ型が異なる場合は、互換性のあるデータ型であるか、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が暗黙的に変換できるデータ型である必要があります。 データ型が暗黙的に変換されない場合は、CONVERT 関数を使用して明示的に変換する必要があります。  
  
 ON 句に、結合されるテーブルのいずれかだけを指定している述語がある場合があります。 このような述語は、クエリの WHERE 句にもある場合があります。 このように述語を指定した場合、INNER 結合に対しては同じ結果になりますが、OUTER 結合が関係するときは結果が異なることがあります。 ON 句内の述語は結合の前にテーブルに適用されるのに対し、WHERE 句は意味的に結合結果に適用されるためです。  
  
 検索条件および述語の詳細については、次を参照してください。[検索条件 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/search-condition-transact-sql.md)  
  
 CROSS JOIN  
 2 つのテーブルの結合を指定します。 SQL-92 形式でない旧形式の結合で WHERE 句が指定されていない場合と同じ行が返されます。  
  
 *left_table_source* { CROSS | OUTER } APPLY *right_table_source*  
 指定する、 *right_table_source*適用の演算子がすべての行に対して評価されます、 *left_table_source*です。 この機能が便利な場合に、 *right_table_source*から列の値を受け取るテーブル値関数を含む、 *left_table_source*引数の 1 つとしてです。  
  
 CROSS または OUTER は、APPLY を使用して指定する必要があります。 行は生成されません CROSS を指定したときに、 *right_table_source*の指定された行に対して評価される、 *left_table_source*し、空の結果セットを返します。  
  
 行ごとに 1 つの行が生成される OUTER を指定すると、 *left_table_source*場合でも、 *right_table_source*その行に対して評価し、空の結果セットを返します。  
  
 詳細については、「解説」を参照してください。  
  
 *left_table_source*  
 前の引数で定義されたテーブル ソースです。 詳細については、「解説」を参照してください。  
  
 *right_table_source*  
 前の引数で定義されたテーブル ソースです。 詳細については、「解説」を参照してください。  
  
 *table_source* PIVOT \<pivot_clause>  
 指定する、 *table_source*に基づいてピボットされる、 *pivot_column*です。 *table_source*はテーブルまたはテーブル式。 出力は次のすべての列を含むテーブル、 *table_source*を除く、 *pivot_column*と*value_column*です。 列、 *table_source*、を除き、 *pivot_column*と*value_column*、pivot 演算子のグループ化列と呼ばれます。 PIVOT および UNPIVOT の詳細については、次を参照してください。[を使用して PIVOT および UNPIVOT](../../t-sql/queries/from-using-pivot-and-unpivot.md)です。  
  
 PIVOT は、グループ化列に関する入力テーブルに対してグループ化の操作を実行し、各グループごとに 1 行のデータを返します。 さらに、出力がで指定された値ごとに 1 つの列を含む、 *column_list*に表示される、 *pivot_column*の*input_table*です。  
  
 詳細については、後の「解説」を参照してください。  
  
 *aggregate_function*  
 システムまたはユーザー定義の集計関数で、1 つ以上の入力を受け取ります。 集計関数は、NULL 値に固定されます。 NULL 値に固定された集計関数は、集計値を評価する際に、グループ内の NULL 値を考慮しません。  
  
 COUNT(*) システム集計関数は使用できません。  
  
 *value_column*  
 PIVOT 演算子の値列です。 UNPIVOT を使用すると*value_column*入力内の既存の列の名前にすることはできません*table_source*です。  
  
 FOR *pivot_column*  
 PIVOT 演算子のピボット列です。 *pivot_column*暗黙的または明示的に変換できる型にする必要があります**nvarchar()**です。 この列にすることはできません**イメージ**または**rowversion**です。  
  
 UNPIVOT が使用されるときに*pivot_column*から絞り込まれる出力列の名前を指定します、 *table_source*です。 既存の列が存在することはできません*table_source*その名前を持つ。  
  
 IN (*column_list* )  
 PIVOT 句内の値の一覧、 *pivot_column*出力テーブルの列名になります。 一覧は、入力で既に存在する任意の列名を指定することはできません*table_source*をピボット処理されています。  
  
 UNPIVOT 句で列が一覧表示*table_source*を 1 つに絞り込まれる*pivot_column*です。  
  
 *table_alias*  
 出力テーブルの別名です。 *pivot_table_alias*指定する必要があります。  
  
 UNPIVOT \< unpivot_clause >  
 入力テーブルが複数の列から絞り込まれることを示す*column_list*と呼ばれる 1 つの列に*pivot_column*です。 PIVOT および UNPIVOT の詳細については、次を参照してください。[を使用して PIVOT および UNPIVOT](../../t-sql/queries/from-using-pivot-and-unpivot.md)です。  
  
 AS OF \<date_time>  

**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  

  
 これまでの時間内には、指定位置で行ごとに実際の値を含む (現在) の 1 つのレコードを含むテーブルを返します。 内部的には、共用体は、テンポラル テーブルとその履歴テーブルの間で実行し、結果はフィルター処理が有効であった時点で指定された時間内の行に値を返しますが、 *\<日付 _ 時刻 >*パラメーター。 行の値が有効と見なされます場合、 *system_start_time_column_name*値より小さいかと等しい、 *\<日付 _ 時刻 >*パラメーター値、および*system_end_time_column_name*値がより大きい、 *\<日付 _ 時刻 >*パラメーターの値。   
  
 FROM \<start_date_time> TO \<end_date_time>

**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。

  
 前にアクティブなを起動するかどうかに関係なく、指定した時間範囲内でアクティブだったすべてのレコードのバージョンの値を持つテーブルを返します、  *\<start_date_time >*からのパラメーター値引数または後にアクティブながされているが中断されること、  *\<end_date_time >*パラメーターに引数の値。 内部的には、共用体が一時的なテーブルとその履歴テーブルの間実行され、結果をフィルター処理すると、指定した時間範囲の中にいつでもにアクティブだったすべての行のバージョンの値を返します。 FROM エンドポイントによって定義されている下限の境界で正確にアクティブになった行のサイズが含まれ、宛先エンドポイントによって定義された境界の上限で正確にアクティブになった行は含まれません。  
  
 間\<start_date_time > AND \<end_date_time >  

**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 上と同じで、 **FROM \<start_date_time > TO \<end_date_time >**説明、によって定義された上限の境界上でアクティブになった行が含まれています点を除いて、 \<end_date_time >エンドポイント。  
  
 含まれる IN (\<start_date_time >、 \<end_date_time >)  

**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  

  
 開き、含まれている IN 引数の 2 つの datetime 値で定義されている指定された時間範囲内で終了したすべてのレコードのバージョンの値を持つテーブルを返します。 行が下位の境界に正確に有効になったまたは上限の境界上だけでアクティブにされているが中断されることでは、含まれています。  
  
 ALL  
 現在のテーブルと、履歴テーブルの両方からのすべての行から値を持つテーブルを返します。  
  
## <a name="remarks"></a>解説  
 FROM 句は、結合テーブルと派生テーブルに対して SQL-92-SQL 構文がサポートされています。 SQL-92 構文には、INNER、LEFT OUTER、RIGHT OUTER、FULL OUTER、および CROSS 結合演算子が用意されています。  
  
 FROM 句内での UNION と JOIN は、ビュー内で、および派生テーブルやサブクエリ内でサポートされています。  
  
 自己結合は、そのテーブル自体に対して結合されるテーブルです。 自己結合に基づいた挿入または更新の操作は、FROM 句の順序に従います。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は列の分布統計を提供するリンク サーバーからの分布統計および基数統計を検討するので、REMOTE 結合ヒントを使用して結合をリモートから評価する必要はありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] クエリ プロセッサはリモートの統計量を検討し、リモート結合の方法が適切かどうかを決定します。 REMOTE 結合ヒントは、列の分布統計を提供しないプロバイダーに対しては便利です。  
  
## <a name="using-apply"></a>APPLY の使用  
 APPLY 演算子の左右両方のオペランドはテーブル式です。 これらのオペランドの主な違いは、 *right_table_source*から列を取得するテーブル値関数を使用することができます、 *left_table_source*関数の引数の 1 つとしてです。 *Left_table_source*テーブル値関数を含めることができますからの列である引数を含めることはできません、 *right_table_source*です。  
  
 APPLY 演算子は、FROM 句のテーブル ソースを作成するために、次の方法で動作します。  
  
1.  評価*right_table_source*の各行に対して、 *left_table_source*行セットを作成します。  
  
     内の値、 *right_table_source*依存*left_table_source*です。 *right_table_source*ほとんどこの方法を表すことができます:`TVF(left_table_source.row)`ここで、`TVF`テーブル値関数です。  
  
2.  評価の各行に対して生成されると、結果セットを結合*right_table_source*で、 *left_table_source* UNION ALL 操作を実行しています。  
  
     APPLY 演算子の結果によって生成される列の一覧から列のセットは、 *left_table_source*をから列の一覧と組み合わせて使用する、 *right_table_source*です。  
  
## <a name="using-pivot-and-unpivot"></a>PIVOT および UNPIVOT の使用  
 *Pivot_column*と*value_column* PIVOT 演算子によって使用されている列をグループ化されます。 PIVOT は、次のプロセスに従って出力結果セットを取得します。  
  
1.  グループ化を実行、 *input_table*グループ化列と生成 1 つの出力行に対するグループごとにします。  
  
     出力行のグループ化列でそのグループに対応する列の値を取得する、 *input_table*です。  
  
2.  次の処理を実行して、各出力行の列の一覧内の列に対して値を生成します。  
  
    1.  さらに、GROUP BY に対して前の手順で生成された行をグループ化、 *pivot_column*です。  
  
         場合は、各出力列に対して、 *column_list*条件を満たすサブグループを選択します。  
  
         `pivot_column = CONVERT(<data type of pivot_column>, 'output_column')`  
  
    2.  *aggregate_function*に対して評価される、 *value_column*このサブグループされ、その結果が対応する値として返されます*output_column*です。 サブグループが空の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の null 値を生成*output_column*です。 集計関数が COUNT であり、サブグループが空である場合は、0 が返されます。  

> [!NOTE]
> 内の列識別子、`UNPIVOT`句がカタログ照合順序に従います。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]、照合順序は常に`SQL_Latin1_General_CP1_CI_AS`です。 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]部分的包含データベースの照合順序は常に`Latin1_General_100_CI_AS_KS_WS_SC`です。 他の列では、collate 句に列を組み合わせた場合 (`COLLATE DATABASE_DEFAULT`) 競合を回避するために必要なです。   
  
 PIVOT および UNPIVOT の例を含む詳細については、次を参照してください。[を使用して PIVOT および UNPIVOT](../../t-sql/queries/from-using-pivot-and-unpivot.md)です。  
  
## <a name="permissions"></a>権限  
 DELETE、SELECT、または UPDATE ステートメントに対する権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-a-simple-from-clause"></a>A. 単純な FROM 句を使用する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] サンプル データベース内の `TerritoryID` テーブルから `Name` および `SalesTerritory` 列を取得します。  
  
```sql    
SELECT TerritoryID, Name  
FROM Sales.SalesTerritory  
ORDER BY TerritoryID ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
TerritoryID Name                            
----------- ------------------------------  
1           Northwest                       
2           Northeast                       
3           Central                         
4           Southwest                       
5           Southeast                       
6           Canada                          
7           France                          
8           Germany                         
9           Australia                       
10          United Kingdom                  
(10 row(s) affected)  
```  
  
### <a name="b-using-the-tablock-and-holdlock-optimizer-hints"></a>B. TABLOCK および HOLDLOCK オプティマイザー ヒントを使用する  
 次の部分的なトランザクションでは、明示的な共有テーブル ロックを `Employee` に設定する方法と、インデックスを読み取る方法を示します。 ロックはトランザクション全体をとおして保持されます。  
  
```sql    
BEGIN TRAN  
SELECT COUNT(*)   
FROM HumanResources.Employee WITH (TABLOCK, HOLDLOCK) ;  
```  
  
### <a name="c-using-the-sql-92-cross-join-syntax"></a>C. SQL-92 CROSS JOIN 構文を使用する  
 次の例は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内の 2 つのテーブル `Employee` と `Department` がクロスした結果を返します。 すべての組み合わせの一覧`BusinessEntityID`行とすべて`Department`名前の行が返されます。  
  
```wql    
SELECT e.BusinessEntityID, d.Name AS Department  
FROM HumanResources.Employee AS e  
CROSS JOIN HumanResources.Department AS d  
ORDER BY e.BusinessEntityID, d.Name ;  
```  
  
### <a name="d-using-the-sql-92-full-outer-join-syntax"></a>D. SQL-92 FULL OUTER JOIN 構文を使用する  
 次の例は、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内の `SalesOrderDetail` テーブル内の製品名、および対応する販売注文を返します。 また、製品記載がない販売注文を返します、`Product`テーブル、およびすべての製品に表示されている別の販売注文、`Product`テーブル。  
  
```sql  
-- The OUTER keyword following the FULL keyword is optional.  
SELECT p.Name, sod.SalesOrderID  
FROM Production.Product AS p  
FULL OUTER JOIN Sales.SalesOrderDetail AS sod  
ON p.ProductID = sod.ProductID  
ORDER BY p.Name ;  
```  
  
### <a name="e-using-the-sql-92-left-outer-join-syntax"></a>E. SQL-92 LEFT OUTER JOIN 構文を使用する  
 次の例では、2 つのテーブルを結合に`ProductID`し、左テーブルから一致しない行を保持します。 `Product` テーブルは、各テーブル内の `SalesOrderDetail` 列について `ProductID` テーブルと照合されます。 注文されたかどうかにかかわらず、すべての製品が結果セットに表示されます。  
  
```sql    
SELECT p.Name, sod.SalesOrderID  
FROM Production.Product AS p  
LEFT OUTER JOIN Sales.SalesOrderDetail AS sod  
ON p.ProductID = sod.ProductID  
ORDER BY p.Name ;  
```  
  
### <a name="f-using-the-sql-92-inner-join-syntax"></a>F. SQL-92 INNER JOIN 構文を使用する  
 次の例では、すべての製品名と販売注文 ID を返します。  
  
```sql    
-- By default, SQL Server performs an INNER JOIN if only the JOIN   
-- keyword is specified.  
SELECT p.Name, sod.SalesOrderID  
FROM Production.Product AS p  
INNER JOIN Sales.SalesOrderDetail AS sod  
ON p.ProductID = sod.ProductID  
ORDER BY p.Name ;  
```  
  
### <a name="g-using-the-sql-92-right-outer-join-syntax"></a>G. SQL-92 RIGHT OUTER JOIN 構文を使用する  
 次の例では、`TerritoryID` の 2 つのテーブルを結合し、右側のテーブルから一致しない行を取り出します。 `SalesTerritory`テーブルと対応している、`SalesPerson`テーブルに対して、`TerritoryID`各テーブル内の列です。 販売区域に割り当てられているかどうかに関係なく、すべての販売員は結果セットに表示されます。  
  
```sql    
SELECT st.Name AS Territory, sp.BusinessEntityID  
FROM Sales.SalesTerritory AS st   
RIGHT OUTER JOIN Sales.SalesPerson AS sp  
ON st.TerritoryID = sp.TerritoryID ;  
```  
  
### <a name="h-using-hash-and-merge-join-hints"></a>H. HASH および MERGE 結合ヒントを使用する  
 次の例の間で 3 つのテーブル結合を実行する、 `Product`、 `ProductVendor`、および`Vendor`製品とそのベンダーの一覧を生成するためにテーブルです。 クエリ オプティマイザーは、MERGE 結合を使用して `Product` と `ProductVendor` (`p` と `pv`) を結合します。 次に、`Product` と `ProductVendor` の MERGE 結合の結果が (`p` と `pv`)、`Vendor` テーブルに対して HASH 結合され、(`p` と `pv`) と `v` が作成されます。  
  
> [!IMPORTANT]  
>  結合ヒントを指定すると、INNER キーワードを省略することはできません。INNER JOIN を明示的に指定して、実行する必要があります。  
  
```sql    
SELECT p.Name AS ProductName, v.Name AS VendorName  
FROM Production.Product AS p   
INNER MERGE JOIN Purchasing.ProductVendor AS pv   
ON p.ProductID = pv.ProductID  
INNER HASH JOIN Purchasing.Vendor AS v  
ON pv.BusinessEntityID = v.BusinessEntityID  
ORDER BY p.Name, v.Name ;  
```  
  
### <a name="i-using-a-derived-table"></a>I. 派生テーブルを使用する  
 次の例では、派生テーブル、つまり `SELECT` 句の後に `FROM` ステートメントを使用することで、すべての従業員の姓と名、およびそれぞれの住所のある都市を返します。  
  
```sql    
SELECT RTRIM(p.FirstName) + ' ' + LTRIM(p.LastName) AS Name, d.City  
FROM Person.Person AS p  
INNER JOIN HumanResources.Employee e ON p.BusinessEntityID = e.BusinessEntityID   
INNER JOIN  
   (SELECT bea.BusinessEntityID, a.City   
    FROM Person.Address AS a  
    INNER JOIN Person.BusinessEntityAddress AS bea  
    ON a.AddressID = bea.AddressID) AS d  
ON p.BusinessEntityID = d.BusinessEntityID  
ORDER BY p.LastName, p.FirstName;  
```  
  
### <a name="j-using-tablesample-to-read-data-from-a-sample-of-rows-in-a-table"></a>J. TABLESAMPLE を使用してテーブル内のサンプル行からデータを読み取る  
 次の例では、`TABLESAMPLE` 句内で `FROM` を使用して、`10` テーブル内にあるすべての行の約 `Customer`% を返します。  
  
```sql    
SELECT *  
FROM Sales.Customer TABLESAMPLE SYSTEM (10 PERCENT) ;  
```  
  
### <a name="k-using-apply"></a>K. APPLY の使用  
 次の例では、次のスキーマを使用した次のテーブルがデータベース内に存在することを前提としています。  
  
-   `Departments`: `DeptID`, `DivisionID`, `DeptName`, `DeptMgrID`  
  
-   `EmpMgr`: `MgrID`, `EmpID`  
  
-   `Employees`: `EmpID`, `EmpLastName`, `EmpFirstName`, `EmpSalary`  
  
 テーブル値関数は、`GetReports(MgrID)`すべての従業員の一覧を返す (`EmpID`、 `EmpLastName`、 `EmpSalary`) を指定された直接または間接の部下を`MgrID`です。  
  
 この例では`APPLY`をその部門ですべての部門およびすべての従業員を返します。 特定の部門に従業員が存在しない場合は、その部門には行が返されません。  
  
```sql
SELECT DeptID, DeptName, DeptMgrID, EmpID, EmpLastName, EmpSalary  
FROM Departments d CROSS APPLY dbo.GetReports(d.DeptMgrID) ;  
```  
  
 `EmpID`、`EmpLastName`、および `EmpSalary` 列に対して NULL 値を作成する、従業員が存在しない部門に対してもクエリによって行を作成する場合は、代わりに `OUTER APPLY` を使用します。  
  
```sql
SELECT DeptID, DeptName, DeptMgrID, EmpID, EmpLastName, EmpSalary  
FROM Departments d OUTER APPLY dbo.GetReports(d.DeptMgrID) ;  
```  
  
### <a name="l-using-cross-apply"></a>L. CROSS APPLY を使用する  
 次の例では、`sys.dm_exec_cached_plans` 動的管理ビューに対してクエリを実行し、キャッシュにあるすべてのクエリ プランのプラン ハンドルを取得することによって、プラン キャッシュにあるすべてのクエリ プランのスナップショットを取得します。 続いて、`CROSS APPLY`へのハンドルを渡す、計画、演算子が指定されて`sys.dm_exec_query_plan`です。 XML プラン表示の出力は、現在プラン キャッシュにある各プランは、`query_plan`返されるテーブルの列です。  
  
```sql
USE master;  
GO  
SELECT dbid, object_id, query_plan   
FROM sys.dm_exec_cached_plans AS cp   
CROSS APPLY sys.dm_exec_query_plan(cp.plan_handle);   
GO  
```  
  
### <a name="m-using-for-systemtime"></a>M. FOR SYSTEM_TIME を使用します。  
  
**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 次の例では、SYSTEM_TIME の date_time_literal_or_variable 引数を使用して、2014 年 1 月 1 日の時点で実際の (現在) をされたテーブル行を返します。  
  
```sql
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME AS OF '2014-01-01'  
WHERE ManagerID = 5;
```  
  
 次の例では、date_time_literal_or_variable 引数に FOR SYSTEM_TIME FROM date_time_literal_or_variable を使用して、2013 年 1 月 1 日に開始すると、2014 年 1 月 1 日で終わる定義されている期間中にアクティブだったすべての行を返します上限の境界の排他。  
  
```sql
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME FROM '2013-01-01' TO '2014-01-01'  
WHERE ManagerID = 5;
```  
  
 次の例では、SYSTEM_TIME 間で date_time_literal_or_variable と date_time_literal_or_variable 引数のすべての行を返すには、2013 年 1 月 1 日に始まり、2014 年 1 月 1 日で終わる定義されている期間中にアクティブだった上限の境界の包括的です。  
  
```sql
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME BETWEEN '2013-01-01' AND '2014-01-01'  
WHERE ManagerID = 5;
```  
  
 次の例は、FOR SYSTEM_TIME CONTAINED IN (date_time_literal_or_variable、date_time_literal_or_variable) 引数を開きで、2013 年 1 月 1 日に開始および終了として定義されている期間中に終了されたすべての行を返す2014 年 1 月 1 日です。  
  
```sql
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME CONTAINED IN ( '2013-01-01', '2014-01-01' )  
WHERE ManagerID = 5;
```  
  
 次の例では、リテラルではなく、変数を使用して、クエリの日付の境界値を指定します。  
  
```sql
DECLARE @AsOfFrom datetime2 = dateadd(month,-12, sysutcdatetime());
DECLARE @AsOfTo datetime2 = dateadd(month,-6, sysutcdatetime());
  
SELECT DepartmentNumber,   
    DepartmentName,   
    ManagerID,   
    ParentDepartmentNumber   
FROM DEPARTMENT  
FOR SYSTEM_TIME FROM @AsOfFrom TO @AsOfTo  
WHERE ManagerID = 5;
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="n-using-the-inner-join-syntax"></a>N. INNER JOIN 構文を使用します。  
 次の例を返します、 `SalesOrderNumber`、 `ProductKey`、および`EnglishProductName`からの列、`FactInternetSales`と`DimProduct`テーブルの結合キー `ProductKey`、両方のテーブルに一致します。 `SalesOrderNumber`と`EnglishProductName`各列に存在テーブルのみのいずれかが示すように、これらの列を持つテーブルの別名を指定する必要はありません。 これらのエイリアスは読みやすくするために含まれます。 単語**AS**エイリアスの前に名前は必要ありませんが、ANSI 標準に準拠して読みやすくするためにはお勧めします。  
  
```sql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM FactInternetSales AS fis 
INNER JOIN DimProduct AS dp  
    ON dp.ProductKey = fis.ProductKey;  
```  
  
 以降、`INNER`キーワードは、内部結合に必要なは、このクエリのように記述します。  
  
```sql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM FactInternetSales AS fis 
JOIN DimProduct AS dp  
ON dp.ProductKey = fis.ProductKey;  
```  
  
 A`WHERE`句こともできますこのクエリに結果を制限します。 次の例は、結果を制限`SalesOrderNumber`'SO5000' よりも大きい値。  
  
```sql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM FactInternetSales AS fis 
JOIN DimProduct AS dp  
    ON dp.ProductKey = fis.ProductKey  
WHERE fis.SalesOrderNumber > 'SO50000'  
ORDER BY fis.SalesOrderNumber;  
```  
  
### <a name="o-using-the-left-outer-join-and-right-outer-join-syntax"></a>O.  LEFT OUTER JOIN、RIGHT OUTER JOIN 構文を使用します。  
 次の例の結合、`FactInternetSales`と`DimProduct`でテーブル、`ProductKey`列です。 左外部結合の構文が左から一致しない行を保持 (`FactInternetSales`) テーブルです。 以降、`FactInternetSales`テーブル含まない`ProductKey`値と一致しない、`DimProduct`テーブルでは、このクエリは、最初の内部結合例と同じ行を返します。  
  
```sql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM FactInternetSales AS fis 
LEFT OUTER JOIN DimProduct AS dp  
    ON dp.ProductKey = fis.ProductKey;  
```  
  
 このクエリは、せずも記述できます、`OUTER`キーワード。  
  
 右外部結合、右テーブルから一致しない行が保持されます。 次の例では、上記の左外部結合の例と同じ行を返します。  
  
```sql
-- Uses AdventureWorks  
  
SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
FROM DimProduct AS dp 
RIGHT OUTER JOIN FactInternetSales AS fis  
    ON dp.ProductKey = fis.ProductKey;  
```  
  
 次のクエリは、`DimSalesTerritory`左外部結合の左側のテーブルとしてテーブル。 取得、`SalesOrderNumber`値から、`FactInternetSales`テーブル。 特定の注文が存在しない場合`SalesTerritoryKey`、NULL が返されます、`SalesOrderNumber`その行に対してです。 このクエリが並べ、`SalesOrderNumber`列はこの列のいずれかが null に設定できるように、結果の上部に表示されます。  
  
```sql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, dst.SalesTerritoryRegion, fis.SalesOrderNumber  
FROM DimSalesTerritory AS dst 
LEFT OUTER JOIN FactInternetSales AS fis  
    ON dst.SalesTerritoryKey = fis.SalesTerritoryKey  
ORDER BY fis.SalesOrderNumber;  
```  
  
 このクエリは、同じ結果を取得する右外部結合で書き直すことができます。  
  
```sql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, dst.SalesTerritoryRegion, fis.SalesOrderNumber  
FROM FactInternetSales AS fis 
RIGHT OUTER JOIN DimSalesTerritory AS dst  
    ON fis.SalesTerritoryKey = dst.SalesTerritoryKey  
ORDER BY fis.SalesOrderNumber;  
```  
  
### <a name="p-using-the-full-outer-join-syntax"></a>P. FULL OUTER JOIN 構文を使用します。  
 次の例では、両方の結合テーブルからすべての行を返しますが、別のテーブルと一致しない値は NULL を返しますが、完全外部結合を示します。  
  
```sql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, dst.SalesTerritoryRegion, fis.SalesOrderNumber  
FROM DimSalesTerritory AS dst 
FULL OUTER JOIN FactInternetSales AS fis  
    ON dst.SalesTerritoryKey = fis.SalesTerritoryKey  
ORDER BY fis.SalesOrderNumber;  
```  
  
 このクエリは、せずも記述できます、`OUTER`キーワード。  
  
```sql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, dst.SalesTerritoryRegion, fis.SalesOrderNumber  
FROM DimSalesTerritory AS dst 
FULL JOIN FactInternetSales AS fis  
    ON dst.SalesTerritoryKey = fis.SalesTerritoryKey  
ORDER BY fis.SalesOrderNumber;  
```  
  
### <a name="q-using-the-cross-join-syntax"></a>Q.  CROSS JOIN 構文を使用します。  
 次の例のクロス積を返します、`FactInternetSales`と`DimSalesTerritory`テーブル。 すべての組み合わせの一覧`SalesOrderNumber`と`SalesTerritoryKey`が返されます。 ない場合に注意してください、`ON`クロス結合クエリ内の句。  
  
```sql
-- Uses AdventureWorks  
  
SELECT dst.SalesTerritoryKey, fis.SalesOrderNumber  
FROM DimSalesTerritory AS dst 
CROSS JOIN FactInternetSales AS fis  
ORDER BY fis.SalesOrderNumber;  
```  
  
### <a name="r-using-a-derived-table"></a>R.  派生テーブルを使用する  
 次の例では、派生テーブル (、`SELECT`後のステートメント、`FROM`句) を返す、`CustomerKey`と`LastName`内の顧客すべての列、`DimCustomer`を持つテーブル`BirthDate`1 月 1 日より後の値1970、姓と名 'Smith' です。  
  
```sql
-- Uses AdventureWorks  
  
SELECT CustomerKey, LastName  
FROM  
   (SELECT * FROM DimCustomer  
    WHERE BirthDate > '01/01/1970') AS DimCustomerDerivedTable  
WHERE LastName = 'Smith'  
ORDER BY LastName;  
```  
  
### <a name="s-reduce-join-hint-example"></a>S.  結合ヒントの例を減らす  
 次の例では、`REDUCE`結合ヒントをクエリ内で派生テーブルの処理を変更します。 使用する場合、`REDUCE`このクエリで結合ヒント、`fis.ProductKey`は射影、レプリケートされ、個別にし、参加していると`DimProduct`のランダム再生中に`DimProduct`で`ProductKey`です。 結果として得られる派生テーブルに分散させて`fis.ProductKey`です。  
  
```sql
-- Uses AdventureWorks  
  
EXPLAIN SELECT SalesOrderNumber  
FROM  
   (SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
    FROM DimProduct AS dp   
      INNER REDUCE JOIN FactInternetSales AS fis   
          ON dp.ProductKey = fis.ProductKey  
   ) AS dTable  
ORDER BY SalesOrderNumber;  
```  
  
### <a name="t-replicate-join-hint-example"></a>T.  レプリケート結合ヒントの例  
 次の例は、という点以外、前の例と同じクエリを示しています、`REPLICATE`の代わりに結合ヒントを使用、`REDUCE`結合ヒント。 使用、`REPLICATE`ヒント内の値の原因、 `ProductKey` (参加) の列から、`FactInternetSales`すべてのノードにレプリケートされるテーブル。 `DimProduct`テーブルは、それらの値のレプリケートされたバージョンに結合します。  
  
```sql
-- Uses AdventureWorks  
  
EXPLAIN SELECT SalesOrderNumber  
FROM  
   (SELECT fis.SalesOrderNumber, dp.ProductKey, dp.EnglishProductName  
    FROM DimProduct AS dp   
      INNER REPLICATE JOIN FactInternetSales AS fis  
          ON dp.ProductKey = fis.ProductKey  
   ) AS dTable  
ORDER BY SalesOrderNumber;  
```  
  
### <a name="u-using-the-redistribute-hint-to-guarantee-a-shuffle-move-for-a-distribution-incompatible-join"></a>U.  ディストリビューションの互換性のない結合のため、ランダム再生の移動を保証するために REDISTRIBUTE ヒントを使用します。  
 次のクエリは、ディストリビューションの互換性のない結合に再配布のクエリ ヒントを使用します。 これにより、クエリ オプティマイザーはクエリ プランで、ランダム再生の移動を使用します。 これは、クエリ プランは分散テーブルは、レプリケートされたテーブルに移動するブロードキャスト move を使用しないも保証されます。  
  
 次の例では REDISTRIBUTE ヒント強制的 ProductKey は DimProduct の配布] 列であり、FactInternetSales のディストリビューション列ではないため、FactInternetSales テーブルで、[ランダム再生の移動にします。  
  
```sql
-- Uses AdventureWorks  
  
EXPLAIN  
SELECT dp.ProductKey, fis.SalesOrderNumber, fis.TotalProductCost  
FROM DimProduct AS dp 
INNER REDISTRIBUTE JOIN FactInternetSales AS fis  
    ON dp.ProductKey = fis.ProductKey;  
```  
  
## <a name="see-also"></a>参照  
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [挿入 &#40; です。Transact SQL と &#41; です。](../../t-sql/statements/insert-transact-sql.md)   
 [OPENQUERY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/openquery-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)  
