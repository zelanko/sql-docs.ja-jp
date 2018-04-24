---
title: MERGE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: t-sql|statements
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- MERGE
- MERGE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- updating data [SQL Server]
- modifying data [SQL Server], MERGE statement
- MERGE statement [SQL Server]
- adding data
- DML [SQL Server], MERGE statement
- table modifications [SQL Server], MERGE statement
- data manipulation language [SQL Server], MERGE statement
- inserting data
ms.assetid: c17996d6-56a6-482f-80d8-086a3423eecc
caps.latest.revision: 76
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: ab3800d6cded8d8221d411ac2fdcbb75cba628df
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="merge-transact-sql"></a>MERGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ソース テーブルとの結合結果に基づき、挿入、更新、削除のいずれかの操作を対象テーブルに対して実行します。 たとえば、他のテーブルとの違いに基づいて、あるテーブル内の行を挿入、更新、または削除することにより、2 つのテーブルを同期できます。  
  
 **パフォーマンスのヒント:** 説明した MERGE ステートメントの条件付きの動作は、一致する特性が 2 つのテーブルで複雑に組み合わされている場合に最適です。 たとえば、存在しない場合は行を挿入し、一致しない場合は行を更新します。 別のテーブルの行に基づいて 1 つのテーブルを更新するだけで、基本的な INSERT、UPDATE、および DELETE ステートメントのパフォーマンスとスケーラビリティが向上します。 例 :  
  
```  
INSERT tbl_A (col, col2)  
SELECT col, col2   
FROM tbl_B   
WHERE NOT EXISTS (SELECT col FROM tbl_A A2 WHERE A2.col = tbl_B.col);  
```  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
[ WITH <common_table_expression> [,...n] ]  
MERGE   
    [ TOP ( expression ) [ PERCENT ] ]   
    [ INTO ] <target_table> [ WITH ( <merge_hint> ) ] [ [ AS ] table_alias ]  
    USING <table_source>   
    ON <merge_search_condition>  
    [ WHEN MATCHED [ AND <clause_search_condition> ]  
        THEN <merge_matched> ] [ ...n ]  
    [ WHEN NOT MATCHED [ BY TARGET ] [ AND <clause_search_condition> ]  
        THEN <merge_not_matched> ]  
    [ WHEN NOT MATCHED BY SOURCE [ AND <clause_search_condition> ]  
        THEN <merge_matched> ] [ ...n ]  
    [ <output_clause> ]  
    [ OPTION ( <query_hint> [ ,...n ] ) ]      
;  
  
<target_table> ::=  
{   
    [ database_name . schema_name . | schema_name . ]  
  target_table  
}  
  
<merge_hint>::=  
{  
    { [ <table_hint_limited> [ ,...n ] ]  
    [ [ , ] INDEX ( index_val [ ,...n ] ) ] }  
}  
  
<table_source> ::=   
{  
    table_or_view_name [ [ AS ] table_alias ] [ <tablesample_clause> ]   
        [ WITH ( table_hint [ [ , ]...n ] ) ]   
  | rowset_function [ [ AS ] table_alias ]   
        [ ( bulk_column_alias [ ,...n ] ) ]   
  | user_defined_function [ [ AS ] table_alias ]  
  | OPENXML <openxml_clause>   
  | derived_table [ AS ] table_alias [ ( column_alias [ ,...n ] ) ]   
  | <joined_table>   
  | <pivoted_table>   
  | <unpivoted_table>   
}  
  
<merge_search_condition> ::=  
    <search_condition>  
  
<merge_matched>::=  
    { UPDATE SET <set_clause> | DELETE }  
  
<set_clause>::=  
SET  
  { column_name = { expression | DEFAULT | NULL }  
  | { udt_column_name.{ { property_name = expression  
                        | field_name = expression }  
                        | method_name ( argument [ ,...n ] ) }  
    }  
  | column_name { .WRITE ( expression , @Offset , @Length ) }  
  | @variable = expression  
  | @variable = column = expression  
  | column_name { += | -= | *= | /= | %= | &= | ^= | |= } expression  
  | @variable { += | -= | *= | /= | %= | &= | ^= | |= } expression  
  | @variable = column { += | -= | *= | /= | %= | &= | ^= | |= } expression  
  } [ ,...n ]   
  
<merge_not_matched>::=  
{  
    INSERT [ ( column_list ) ]   
        { VALUES ( values_list )  
        | DEFAULT VALUES }  
}  
  
<clause_search_condition> ::=  
    <search_condition>  
  
<search condition> ::=  
    { [ NOT ] <predicate> | ( <search_condition> ) }   
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]   
[ ,...n ]   
  
<predicate> ::=   
    { expression { = | < > | ! = | > | > = | ! > | < | < = | ! < } expression   
    | string_expression [ NOT ] LIKE string_expression   
  [ ESCAPE 'escape_character' ]   
    | expression [ NOT ] BETWEEN expression AND expression   
    | expression IS [ NOT ] NULL   
    | CONTAINS   
  ( { column | * } , '< contains_search_condition >' )   
    | FREETEXT ( { column | * } , 'freetext_string' )   
    | expression [ NOT ] IN ( subquery | expression [ ,...n ] )   
    | expression { = | < > | ! = | > | > = | ! > | < | < = | ! < }   
  { ALL | SOME | ANY} ( subquery )   
    | EXISTS ( subquery ) }   
  
<output_clause>::=  
{  
    [ OUTPUT <dml_select_list> INTO { @table_variable | output_table }  
        [ (column_list) ] ]  
    [ OUTPUT <dml_select_list> ]  
}  
  
<dml_select_list>::=  
    { <column_name> | scalar_expression }   
        [ [AS] column_alias_identifier ] [ ,...n ]  
  
<column_name> ::=  
    { DELETED | INSERTED | from_table_name } . { * | column_name }  
    | $action  
```  
  
## <a name="arguments"></a>引数  
 WITH \<common_table_expression>  
 MERGE ステートメントのスコープ内で定義された、一時的な名前付き結果セットまたはビュー (共通テーブル式とも呼ばれる) を指定します。 結果セットは単純なクエリから派生し、MERGE ステートメントで参照されます。 詳細については、「[WITH common_table_expression &#40;Transact-SQL&#41;](../../t-sql/queries/with-common-table-expression-transact-sql.md)」を参照してください。  
  
 TOP ( *expression* ) [ PERCENT ]  
 影響を受ける行の数またはパーセンテージを指定します。 *expression* には、行数または行のパーセンテージを指定できます。 TOP 式で参照される行は順序付けされません。 詳細については、「[TOP &#40;Transact-SQL&#41;](../../t-sql/queries/top-transact-sql.md)」を参照してください。  
  
 TOP 句は、ソース テーブル全体と対象テーブル全体が結合され、挿入、更新、または削除操作の対象とならない結合された行が削除された後に適用されます。 TOP 句を使用すると、結合された行の数が指定の値まで減少し、挿入、更新、または削除操作が残りの結合された行に順序付けなしで適用されます。 つまり、WHEN 句で定義された各操作に行を割り当てる順序に決まりはありません。 たとえば、TOP (10) と指定すると 10 行に影響しますが、そのうち 7 行が更新されて 3 行が挿入される場合も、1 行が削除、5 行が更新され、4 行が挿入される場合もあります。  
  
 MERGE ステートメントはソース テーブルと対象テーブルの両方のフル テーブル スキャンを実行するので、TOP 句を使用し、複数のバッチを作成して大きなテーブルを変更すると、I/O パフォーマンスが影響を受ける場合があります。 この場合は、一連のすべてのバッチが新しい行を対象としていることを確認してください。  
  
 *database_name*  
 *target_table* があるデータベースの名前です。  
  
 *schema_name*  
 *target_table* が属しているスキーマの名前です。  
  
 *target_table*  
 \<clause_search_condition> に基づいて \<table_source> のデータ行が照合されるテーブルまたはビューです。 *target_table* は、MERGE ステートメントの WHEN 句で指定された挿入、更新、削除のいずれかの操作の対象です。  
  
 *target_table* がビューの場合、これに対するアクションはビューの更新条件を満たす必要があります。 詳細については、「[ビューを使用したデータ変更](../../relational-databases/views/modify-data-through-a-view.md)」を参照してください。  
  
 *target_table* にリモート テーブルを指定することはできません。 *target_table* に対してルールを定義することはできません。  
  
 [ AS ] *table_alias*  
 テーブルを参照するために使用する代替名です。  
  
 USING \<table_source>  
 \<merge_search condition> に基づいて *target_table* 内のデータ行と照合するデータ ソースを指定します。 この照合結果によって、MERGE ステートメントの WHEN 句で実行される操作が決まります。 \<table_source> には、リモート テーブルを指定することも、リモート テーブルにアクセスする派生テーブルを指定することもできます。 
  
 \<table_source> には派生テーブルを指定できます。このテーブルでは、複数の行を指定してテーブルを作成する [!INCLUDE[tsql](../../includes/tsql-md.md)] [テーブル値コンストラクター](../../t-sql/queries/table-value-constructor-transact-sql.md)を使用します。  
  
 この句の構文および引数の詳細については、「[FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)」を参照してください。  
  
 ON \<merge_search_condition>  
 \<table_source> と *target_table* を結合して一致箇所を特定するための条件を指定します。 
  
> [!CAUTION]  
>  照合目的で使用する対象テーブルの列だけを指定することが重要です。 つまり、対象テーブルのうち、ソース テーブル内の対応する列と比較する列を指定します。 `AND NOT target_table.column_x = value` と指定するなど、ON 句で対象テーブル内の行にフィルターを適用することによって、クエリ パフォーマンスを向上させようとしないでください。 この場合、予期しない無効な結果が返されることがあります。  
  
 WHEN MATCHED THEN \<merge_matched>  
 \<table_source> ON \<merge_search_condition> で返される行に一致し、追加の検索条件を満たす *target_table* のすべての行を、\<merge_matched> 句に従って更新または削除するように指定します。  
  
 MERGE ステートメントには、最大 2 つの WHEN MATCHED 句を指定できます。 句を 2 つ指定する場合、最初の句は AND \<search_condition> 句と共に使用する必要があります。 任意の行に対し、最初の WHEN MATCHED 句が適用されなかった場合にのみ、2 番目の WHEN MATCHED 句が適用されます。 WHEN MATCHED 句が 2 つある場合は、一方で UPDATE 操作を、もう一方で DELETE 操作を指定する必要があります。 \<merge_matched> 句で UPDATE が指定されており、\<merge_search_condition> に基づいて \<table_source> の複数の行が *target_table* の 1 つの行に一致する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] からエラーが返されます。 MERGE ステートメントで、同じ行を複数回更新することや、同じ行の更新と削除を行うことはできません。  
  
 WHEN NOT MATCHED [ BY TARGET ] THEN \<merge_not_matched>  
 \<table_source> ON \<merge_search_condition> で返される行のうち、*target_table* 内の行とは一致しないが、追加の検索条件 (存在する場合) は満たす行ごとに、*target_table*に 1 行を挿入するように指定します。 挿入する値は、\<merge_not_matched> 句で指定します。 MERGE ステートメントに指定できる WHEN NOT MATCHED 句は 1 つだけです。  
  
 WHEN NOT MATCHED BY SOURCE THEN \<merge_matched>  
 \<table_source> ON \<merge_search_condition> で返される行には一致しないが、追加の検索条件は満たす *target_table* のすべての行を、\<merge_matched> 句に従って更新または削除するように指定します。  
  
 MERGE ステートメントには、最大 2 つの WHEN NOT MATCHED BY SOURCE 句を指定できます。 句を 2 つ指定する場合、最初の句は AND \<clause_search_condition> 句と共に使用する必要があります。 任意の行に対し、最初の WHEN NOT MATCHED BY SOURCE 句が適用されなかった場合にのみ、2 番目の WHEN NOT MATCHED BY SOURCE 句が適用されます。 WHEN NOT MATCHED BY SOURCE 句が 2 つある場合は、一方で UPDATE 操作を、もう一方で DELETE 操作を指定する必要があります。 \<clause_search_condition> では対象テーブルの列のみを参照できます。  
  
 \<table_source> から返される行がない場合、ソース テーブルの列にアクセスすることができません。 \<merge_matched> 句に指定した更新操作または削除操作でソース テーブルの列を参照していると、エラー 207 (無効な列名) が返されます。 たとえば、ソース テーブルの `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1` にアクセスできないために、`Col1` 句によってステートメントが失敗することがあります。  
  
 AND \<clause_search_condition>  
 任意の有効な検索条件を指定します。 詳しくは、「[検索条件 &#40;Transact-SQL&#41;](../../t-sql/queries/search-condition-transact-sql.md)」をご覧ください。  
  
 \<table_hint_limited>  
 MERGE ステートメントによって実行される挿入、更新、削除の各操作に対し、対象テーブルに適用される 1 つ以上のテーブル ヒントを指定します。 キーワード WITH とかっこが必要です。  
  
 NOLOCK および READUNCOMMITTED は指定できません。 テーブル ヒントの詳細については、「[テーブル ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)」を参照してください。  
  
 INSERT ステートメントの対象であるテーブルに対して TABLOCK ヒントを指定すると、TABLOCKX ヒントを指定した場合と同じ効果を得られます。 テーブルに対して、排他ロックが取得されます。 FORCESEEK を指定すると、対象テーブルとソース テーブルが結合された暗黙のインスタンスに対して適用されます。  
  
> [!CAUTION]  
>  WHEN NOT MATCHED [ BY TARGET ] THEN INSERT に READPAST を指定すると、UNIQUE 制約に違反する INSERT 操作が発生する場合があります。  
  
 INDEX ( index_val [ ,...n ] )  
 ソース テーブルとの暗黙の結合を実行するため、対象テーブルの 1 つ以上のインデックスの名前または ID を指定します。 詳細については、「[テーブル ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)」を参照してください。  
  
 \<output_clause>  
 *target_table* 内の更新、挿入、または削除される行ごとに 1 行を返します。この場合、特定の順序はありません。 **$action** は、OUTPUT 句に指定することができます。 **$action** は、行に対して実行されたアクションに従って 'INSERT'、'UPDATE'、'DELETE' のいずれかの値をそれぞれの行について返す、**nvarchar(10)** 型の列です。 この句の引数について詳しくは、「[OUTPUT Clause &#40;Transact-SQL&#41;](../../t-sql/queries/output-clause-transact-sql.md)」をご覧ください。  
  
 OPTION ( \<query_hint> [ ,...n ] )  
 オプティマイザー ヒントを使用して、データベース エンジンがステートメントを処理する方法をカスタマイズすることを指定します。 詳細については、「[クエリ ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)」を参照してください。  
  
 \<merge_matched>  
 \<table_source> ON \<merge_search_condition> で返される行には一致しないが、追加の検索条件は満たす *target_table* のすべての行に対し、適用する更新操作または削除操作を指定します。  
  
 UPDATE SET \<set_clause>  
 対象テーブル内で更新する列名または変数名の一覧と、それらの更新に使用する値を指定します。  
  
 この句の引数について詳しくは、「[UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)」をご覧ください。 列と同じ値を変数に設定することはできません。  
  
 Del  
 *target_table* 内の行に一致する行を削除するように指定します。  
  
 \<merge_not_matched>  
 対象テーブルに挿入する値を指定します。  
  
 (*column_list*)  
 データを挿入する、対象テーブルの 1 つ以上の列で構成されるリストを指定します。 列は 1 部構成の名前で指定する必要があります。そうしないと MERGE ステートメントが失敗します。 *column_list* はかっこで囲み、コンマで区切る必要があります。  
  
 VALUES ( *values_list*)  
 対象テーブルに挿入する値を返す定数、変数、または式を、コンマ区切りのリストで指定します。 式には EXECUTE ステートメントを含めることができません。  
  
 DEFAULT VALUES  
 挿入される行が、各列に対して定義されている既定値で構成されることを指定します。  
  
 この句について詳しくは、「[INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)」をご覧ください。  
  
 \<search condition>  
 \<merge_search_condition> または \<clause_search_condition> の指定に使用する検索条件を指定します。 この句の引数について詳しくは、「[検索条件 &#40;Transact-SQL&#41;](../../t-sql/queries/search-condition-transact-sql.md)」をご覧ください。  
  
## <a name="remarks"></a>Remarks  
 3 つの MATCHED 句のうち、少なくとも 1 つは指定する必要があります。これらの句は、任意の順序で指定できます。 1 つの MATCHED 句で 1 つの変数を複数回更新することはできません。  
  
 MERGE ステートメントによって対象テーブルに指定された挿入、更新、削除の各操作は、連鎖参照整合性制約など、定義されている制約の制限を受けます。 対象テーブルの一意インデックスで IGNORE_DUP_KEY が ON に設定されていると、MERGE ではこの設定が無視されます。  
  
 MERGE ステートメントでは、ステートメントのターミネータとしてセミコロン (;) が必要です。 MERGE ステートメントにターミネータを付けずに実行すると、エラー 10713 が生成されます。  
  
 MERGE の後に [@@ROWCOUNT &#40;Transact-SQL&#41;](../../t-sql/functions/rowcount-transact-sql.md) を使用すると、クライアントに対して挿入、更新、および削除された行の合計数が返されます。  
  
 データベースの互換性レベルが 100 以上に設定されている場合、MERGE は完全に予約されたキーワードです。 MERGE ステートメントはデータベースの互換性レベルが 90 と 100 の両方で使用できますが、データベースの互換性レベルが 90 に設定されている場合、MERGE キーワードは完全には予約されていません。  
  
 **MERGE** ステートメントは、キュー更新レプリケーションの使用時には使用しないでください。 **MERGE** とキュー更新トリガーには互換性がありません。 **MERGE** ステートメントは、挿入ステートメントまたは更新ステートメントと置き換えてください。  
  
## <a name="trigger-implementation"></a>トリガーの実装  
 MERGE ステートメントに指定された挿入、更新、削除の各操作に対し、対象テーブルで定義された対応する AFTER トリガーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって起動されますが、どの操作に対するトリガーからどのような順序で起動されるかは決まっていません。 同じアクションに対して定義された複数のトリガーは、指定した順序に従います。 トリガー起動順序の設定の詳細については、「[最初と最後のトリガーの指定](../../relational-databases/triggers/specify-first-and-last-triggers.md)」を参照してください。  
  
 MERGE ステートメントによって実行される挿入、更新、削除のいずれかの操作に対して、有効な INSTEAD OF トリガーが対象テーブルに定義されている場合、MERGE ステートメントに指定されたすべての操作に有効な INSTEAD OF トリガーを定義する必要があります。  
  
 INSTEAD OF UPDATE トリガーや INSTEAD OF DELETE トリガーが *target_table* に定義されている場合、更新操作や削除操作は実行されません。 代わりにトリガーが起動され、**inserted** テーブルと **deleted** テーブルに適切なデータが設定されます。  
  
 INSTEAD OF INSERT トリガーが *target_table* に定義されている場合、挿入操作は実行されません。 代わりにトリガーが起動され、**inserted** テーブルに適切なデータが設定されます。  
  
## <a name="permissions"></a>アクセス許可  
 ソース テーブルに対する SELECT 権限と、対象テーブルに対する INSERT、UPDATE、または DELETE 権限が必要です。 詳しくは、「[SELECT](../../t-sql/queries/select-transact-sql.md)」、「[INSERT](../../t-sql/statements/insert-transact-sql.md)」、「[UPDATE](../../t-sql/queries/update-transact-sql.md)」、「[DELETE](../../t-sql/statements/delete-transact-sql.md)」の各トピックの「権限」をご覧ください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-merge-to-perform-insert-and-update-operations-on-a-table-in-a-single-statement"></a>A. MERGE を使用して、単一のステートメントでテーブルに INSERT 操作と UPDATE 操作を実行する  
 一般的なシナリオは、一致する行が存在する場合はテーブル内の 1 つ以上の列を更新し、一致する行が存在しない場合はデータを新しい行として挿入することです。 通常、この操作を行うには、適切な UPDATE ステートメントと INSERT ステートメントを含むストアド プロシージャにパラメーターを渡します。 MERGE ステートメントを使用すると、単一のステートメントで両方のタスクを実行できます。 次の例は、INSERT ステートメントと UPDATE ステートメントの両方を含む [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースのストアド プロシージャを示しています。 このプロシージャを、単一の MERGE ステートメントで同等の操作を実行するように変更します。  
  
```  
CREATE PROCEDURE dbo.InsertUnitMeasure  
    @UnitMeasureCode nchar(3),  
    @Name nvarchar(25)  
AS   
BEGIN  
    SET NOCOUNT ON;  
-- Update the row if it exists.      
    UPDATE Production.UnitMeasure  
SET Name = @Name  
WHERE UnitMeasureCode = @UnitMeasureCode  
-- Insert the row if the UPDATE statement failed.  
IF (@@ROWCOUNT = 0 )  
BEGIN  
    INSERT INTO Production.UnitMeasure (UnitMeasureCode, Name)  
    VALUES (@UnitMeasureCode, @Name)  
END  
END;  
GO  
-- Test the procedure and return the results.  
EXEC InsertUnitMeasure @UnitMeasureCode = 'ABC', @Name = 'Test Value';  
SELECT UnitMeasureCode, Name FROM Production.UnitMeasure  
WHERE UnitMeasureCode = 'ABC';  
GO  
  
-- Rewrite the procedure to perform the same operations using the 
-- MERGE statement.  
-- Create a temporary table to hold the updated or inserted values 
-- from the OUTPUT clause.  
CREATE TABLE #MyTempTable  
    (ExistingCode nchar(3),  
     ExistingName nvarchar(50),  
     ExistingDate datetime,  
     ActionTaken nvarchar(10),  
     NewCode nchar(3),  
     NewName nvarchar(50),  
     NewDate datetime  
    );  
GO  
ALTER PROCEDURE dbo.InsertUnitMeasure  
    @UnitMeasureCode nchar(3),  
    @Name nvarchar(25)  
AS   
BEGIN  
    SET NOCOUNT ON;  
  
    MERGE Production.UnitMeasure AS target  
    USING (SELECT @UnitMeasureCode, @Name) AS source (UnitMeasureCode, Name)  
    ON (target.UnitMeasureCode = source.UnitMeasureCode)  
    WHEN MATCHED THEN   
        UPDATE SET Name = source.Name  
WHEN NOT MATCHED THEN  
    INSERT (UnitMeasureCode, Name)  
    VALUES (source.UnitMeasureCode, source.Name)  
    OUTPUT deleted.*, $action, inserted.* INTO #MyTempTable;  
END;  
GO  
-- Test the procedure and return the results.  
EXEC InsertUnitMeasure @UnitMeasureCode = 'ABC', @Name = 'New Test Value';  
EXEC InsertUnitMeasure @UnitMeasureCode = 'XYZ', @Name = 'Test Value';  
EXEC InsertUnitMeasure @UnitMeasureCode = 'ABC', @Name = 'Another Test Value';  
  
SELECT * FROM #MyTempTable;  
-- Cleanup   
DELETE FROM Production.UnitMeasure WHERE UnitMeasureCode IN ('ABC','XYZ');  
DROP TABLE #MyTempTable;  
GO  
```  
  
### <a name="b-using-merge-to-perform-update-and-delete-operations-on-a-table-in-a-single-statement"></a>B. MERGE を使用して、単一のステートメントでテーブルに UPDATE 操作と DELETE 操作を実行する  
 次の例では、MERGE を使用して、`ProductInventory` テーブルで処理される注文に基づいて、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] サンプル データベース内の `SalesOrderDetail` テーブルを毎日更新します。 `Quantity` テーブルで各製品のその日の注文数を差し引くことで、`ProductInventory` テーブルの `SalesOrderDetail` 列を更新します。 製品の注文数によって、製品の在庫レベルが 0 以下に低下した場合は、その製品の行が `ProductInventory` テーブルから削除されます。  
  
```  
CREATE PROCEDURE Production.usp_UpdateInventory  
    @OrderDate datetime  
AS  
MERGE Production.ProductInventory AS target  
USING (SELECT ProductID, SUM(OrderQty) FROM Sales.SalesOrderDetail AS sod  
    JOIN Sales.SalesOrderHeader AS soh  
    ON sod.SalesOrderID = soh.SalesOrderID  
    AND soh.OrderDate = @OrderDate  
    GROUP BY ProductID) AS source (ProductID, OrderQty)  
ON (target.ProductID = source.ProductID)  
WHEN MATCHED AND target.Quantity - source.OrderQty <= 0  
    THEN DELETE  
WHEN MATCHED   
    THEN UPDATE SET target.Quantity = target.Quantity - source.OrderQty,   
                    target.ModifiedDate = GETDATE()  
OUTPUT $action, Inserted.ProductID, Inserted.Quantity, 
    Inserted.ModifiedDate, Deleted.ProductID,  
    Deleted.Quantity, Deleted.ModifiedDate;  
GO  
  
EXECUTE Production.usp_UpdateInventory '20030501'  
```  
  
### <a name="c-using-merge-to-perform-update-and-insert-operations-on-a-target-table-by-using-a-derived-source-table"></a>C. MERGE を使用し、派生ソース テーブルを使用して対象テーブルに UPDATE 操作と INSERT 操作を実行する  
 次の例は、MERGE を使用し、行を更新または挿入することで [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内の `SalesReason` テーブルを変更します。 ソース テーブルの `NewName` の値が対象テーブル (`SalesReason`) の `Name` 列の値と一致すると、対象テーブルの `ReasonType` 列が更新されます。 `NewName` の値が一致しない場合は、ソース行が対象テーブルに挿入されます。 ソース テーブルは、[!INCLUDE[tsql](../../includes/tsql-md.md)] テーブル値コンストラクターを使用して複数の行を指定する派生テーブルです。 派生テーブルでテーブル値コンストラクターを使用する方法について詳しくは、「[テーブル値コンストラクター &#40;Transact-SQL&#41;](../../t-sql/queries/table-value-constructor-transact-sql.md)」をご覧ください。 この例では、OUTPUT 句の結果をテーブル変数に格納し、挿入された行数と更新された行数を返す単純な選択操作を実行することで MERGE ステートメントの結果をまとめる方法も示しています。  
  
```  
-- Create a temporary table variable to hold the output actions.  
DECLARE @SummaryOfChanges TABLE(Change VARCHAR(20));  
  
MERGE INTO Sales.SalesReason AS Target  
USING (VALUES ('Recommendation','Other'), ('Review', 'Marketing'), 
              ('Internet', 'Promotion'))  
       AS Source (NewName, NewReasonType)  
ON Target.Name = Source.NewName  
WHEN MATCHED THEN  
UPDATE SET ReasonType = Source.NewReasonType  
WHEN NOT MATCHED BY TARGET THEN  
INSERT (Name, ReasonType) VALUES (NewName, NewReasonType)  
OUTPUT $action INTO @SummaryOfChanges;  
  
-- Query the results of the table variable.  
SELECT Change, COUNT(*) AS CountPerChange  
FROM @SummaryOfChanges  
GROUP BY Change;  
```  
  
### <a name="d-inserting-the-results-of-the-merge-statement-into-another-table"></a>D. MERGE ステートメントの結果を別のテーブルに挿入する  
 次の例では、MERGE ステートメントの OUTPUT 句から返されたデータをキャプチャし、そのデータを別のテーブルに挿入します。 MERGE ステートメントは、`Quantity` テーブル内で処理される注文に基づいて、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベース内の `ProductInventory` テーブルの `SalesOrderDetail` 列を毎日更新します。 この例では、更新された行をキャプチャし、在庫変更の追跡に使用する別のテーブルに挿入します。  
  
```  
CREATE TABLE Production.UpdatedInventory  
    (ProductID INT NOT NULL, LocationID int, NewQty int, PreviousQty int,  
     CONSTRAINT PK_Inventory PRIMARY KEY CLUSTERED (ProductID, LocationID));  
GO  
INSERT INTO Production.UpdatedInventory  
SELECT ProductID, LocationID, NewQty, PreviousQty   
FROM  
(    MERGE Production.ProductInventory AS pi  
     USING (SELECT ProductID, SUM(OrderQty)   
            FROM Sales.SalesOrderDetail AS sod  
            JOIN Sales.SalesOrderHeader AS soh  
            ON sod.SalesOrderID = soh.SalesOrderID  
            AND soh.OrderDate BETWEEN '20030701' AND '20030731'  
            GROUP BY ProductID) AS src (ProductID, OrderQty)  
     ON pi.ProductID = src.ProductID  
    WHEN MATCHED AND pi.Quantity - src.OrderQty >= 0   
        THEN UPDATE SET pi.Quantity = pi.Quantity - src.OrderQty  
    WHEN MATCHED AND pi.Quantity - src.OrderQty <= 0   
        THEN DELETE  
    OUTPUT $action, Inserted.ProductID, Inserted.LocationID, 
        Inserted.Quantity AS NewQty, Deleted.Quantity AS PreviousQty)  
 AS Changes (Action, ProductID, LocationID, NewQty, PreviousQty) 
 WHERE Action = 'UPDATE';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [OUTPUT 句 &#40;Transact-SQL&#41;](../../t-sql/queries/output-clause-transact-sql.md)   
 [Integration Services パッケージで MERGE を実行する](../../integration-services/control-flow/merge-in-integration-services-packages.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [テーブル値コンストラクター &#40;Transact-SQL&#41;](../../t-sql/queries/table-value-constructor-transact-sql.md)  
  
  

