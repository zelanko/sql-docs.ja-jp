---
title: "マージ (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: dd8ecb3609dd70516023afe84125252c708ad1ad
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="merge-transact-sql"></a>MERGE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  ソース テーブルとの結合結果に基づき、挿入、更新、削除のいずれかの操作を対象テーブルに対して実行します。 たとえば、他のテーブルとの違いに基づいて、あるテーブル内の行を挿入、更新、または削除することにより、2 つのテーブルを同期できます。  
  
 **パフォーマンス ヒント:** MERGE ステートメントでは 2 つのテーブルがある複雑に絡み合った特性に一致する場合に最適に説明されている条件付き動作します。 たとえば、存在しない場合は行を挿入し、一致しない場合は行を更新します。 別のテーブルの行に基づいて 1 つのテーブルを更新するだけで、基本的な INSERT、UPDATE、および DELETE ステートメントのパフォーマンスとスケーラビリティが向上します。 例:  
  
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
 \<Common_table_expression >  
 MERGE ステートメントのスコープ内で定義された、一時的な名前付き結果セットまたはビュー (共通テーブル式とも呼ばれる) を指定します。 結果セットは単純なクエリから派生し、MERGE ステートメントで参照されます。 詳細については、次を参照してください。[で common_table_expression と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/with-common-table-expression-transact-sql.md).  
  
 上部 (*式*) [PERCENT]  
 影響を受ける行の数またはパーセンテージを指定します。 *式*行数または行の割合を指定できます。 TOP 式で参照される行は順序付けされません。 詳細については、次を参照してください。 [TOP &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/top-transact-sql.md).  
  
 TOP 句は、ソース テーブル全体と対象テーブル全体が結合され、挿入、更新、または削除操作の対象とならない結合された行が削除された後に適用されます。 TOP 句を使用すると、結合された行の数が指定の値まで減少し、挿入、更新、または削除操作が残りの結合された行に順序付けなしで適用されます。 つまり、WHEN 句で定義された各操作に行を割り当てる順序に決まりはありません。 たとえば、TOP (10) と指定すると 10 行に影響しますが、そのうち 7 行が更新されて 3 行が挿入される場合も、1 行が削除、5 行が更新され、4 行が挿入される場合もあります。  
  
 MERGE ステートメントはソース テーブルと対象テーブルの両方のフル テーブル スキャンを実行するので、TOP 句を使用し、複数のバッチを作成して大きなテーブルを変更すると、I/O パフォーマンスが影響を受ける場合があります。 この場合は、一連のすべてのバッチが新しい行を対象としていることを確認してください。  
  
 *database_name*  
 対象となるデータベースの名前を指定*対象テーブル*が配置されています。  
  
 *schema_name*  
 スキーマの名前を指定*対象テーブル*が属しています。  
  
 *対象テーブル*  
 テーブルまたはビューからデータ行を対象となる\<table_source > に基づいてが一致する\<clause_search_condition >。 *対象テーブル*insert、update、または MERGE ステートメントの WHEN 句で指定された削除操作の対象となっています。  
  
 場合*対象テーブル*ビューは、これに対するアクションはビューの更新条件を満たす必要があります。 詳細については、次を参照してください。[変更データ ビューを経由した](../../relational-databases/views/modify-data-through-a-view.md)です。  
  
 *対象テーブル*リモート テーブルを指定することはできません。 *対象テーブル*すべてに対してルールを定義することはできません。  
  
 [と]*table_alias*  
 テーブルを参照するために使用する代替名です。  
  
 使用して\<table_source >  
 内のデータ行と一致するデータ ソースを指定*対象テーブル*に基づいて\<merge_search condition >。 この照合結果によって、MERGE ステートメントの WHEN 句で実行される操作が決まります。 \<table_source > リモート テーブルまたはリモート テーブルにアクセスする派生テーブルを指定できます。 
  
 \<table_source > を使用する派生テーブルを指定することができます、 [!INCLUDE[tsql](../../includes/tsql-md.md)] [テーブル値コンス トラクター](../../t-sql/queries/table-value-constructor-transact-sql.md)に複数の行を指定することによって、テーブルを作成します。  
  
 この句の引数と構文に関する詳細については、次を参照してください。 [FROM &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/from-transact-sql.md).  
  
 ON \<merge_search_condition >  
 対象の条件を指定\<table_source > に参加している*対象テーブル*を一致箇所を判断します。 
  
> [!CAUTION]  
>  照合目的で使用する対象テーブルの列だけを指定することが重要です。 つまり、対象テーブルのうち、ソース テーブル内の対応する列と比較する列を指定します。 `AND NOT target_table.column_x = value` と指定するなど、ON 句で対象テーブル内の行にフィルターを適用することによって、クエリ パフォーマンスを向上させようとしないでください。 この場合、予期しない無効な結果が返されることがあります。  
  
 MATCHED THEN とき\<merge_matched >  
 指定するすべての行の*対象テーブル*によって返される行に一致する\<table_source > ON \<merge_search_condition >、および追加の検索条件を満たすは更新または削除よると、 \<merge_matched > 句。  
  
 MERGE ステートメントには、最大 2 つの WHEN MATCHED 句を指定できます。 2 つの句を指定したかどうかは、最初の句は AND と共に必要があります\<search_condition > 句。 任意の行に対し、最初の WHEN MATCHED 句が適用されなかった場合にのみ、2 番目の WHEN MATCHED 句が適用されます。 WHEN MATCHED 句が 2 つある場合は、一方で UPDATE 操作を、もう一方で DELETE 操作を指定する必要があります。 更新プログラムがで指定されている場合、 \<merge_matched > 句、および 1 つ以上の行の\<table_source > の行と一致する*対象テーブル*に基づいて\<merge_search_condition >、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]はエラーを返します。 MERGE ステートメントで、同じ行を複数回更新することや、同じ行の更新と削除を行うことはできません。  
  
 NOT MATCHED [BY TARGET] THEN とき\<merge_not_matched >  
 行を挿入することを示す*対象テーブル*によって返される行ごとに\<table_source > ON \<merge_search_condition > 内の行と一致しません*対象テーブル*が存在する場合、追加の検索条件を満たしてがします。 挿入する値がで指定された、 \<merge_not_matched > 句。 MERGE ステートメントに指定できる WHEN NOT MATCHED 句は 1 つだけです。  
  
 ときに NOT MATCHED BY SOURCE し\<merge_matched >  
 指定のすべての行*対象テーブル*によって返される行は一致しない\<table_source > ON \<merge_search_condition >、更新するかは任意の追加の検索条件に一致します。に従って削除されたか、 \<merge_matched > 句。  
  
 MERGE ステートメントには、最大 2 つの WHEN NOT MATCHED BY SOURCE 句を指定できます。 2 つの句を指定したかどうかは、最初の句は AND と共に必要があります\<clause_search_condition > 句。 任意の行に対し、最初の WHEN NOT MATCHED BY SOURCE 句が適用されなかった場合にのみ、2 番目の WHEN NOT MATCHED BY SOURCE 句が適用されます。 WHEN NOT MATCHED BY SOURCE 句が 2 つある場合は、一方で UPDATE 操作を、もう一方で DELETE 操作を指定する必要があります。 対象のテーブルから列のみを参照できる\<clause_search_condition >。  
  
 ときに行が返されないによって\<table_source >、ソース テーブルの列にアクセスすることはできません。 Update または delete 操作で指定される場合、 \<merge_matched > 句がソース テーブルの列を参照、エラー 207 (無効な列名) が返されます。 たとえば、ソース テーブルの `WHEN NOT MATCHED BY SOURCE THEN UPDATE SET TargetTable.Col1 = SourceTable.Col1` にアクセスできないために、`Col1` 句によってステートメントが失敗することがあります。  
  
 および\<clause_search_condition >  
 任意の有効な検索条件を指定します。 詳細については、次を参照してください。[検索条件 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/search-condition-transact-sql.md).  
  
 \<table_hint_limited >  
 MERGE ステートメントによって実行される挿入、更新、削除の各操作に対し、対象テーブルに適用される 1 つ以上のテーブル ヒントを指定します。 キーワード WITH とかっこが必要です。  
  
 NOLOCK および READUNCOMMITTED は指定できません。 テーブル ヒントの詳細については、次を参照してください。[テーブル ヒント &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/hints-transact-sql-table.md).  
  
 INSERT ステートメントの対象であるテーブルに対して TABLOCK ヒントを指定すると、TABLOCKX ヒントを指定した場合と同じ効果を得られます。 テーブルに対して、排他ロックが取得されます。 FORCESEEK を指定すると、対象テーブルとソース テーブルが結合された暗黙のインスタンスに対して適用されます。  
  
> [!CAUTION]  
>  WHEN NOT MATCHED [ BY TARGET ] THEN INSERT に READPAST を指定すると、UNIQUE 制約に違反する INSERT 操作が発生する場合があります。  
  
 INDEX ( index_val [ ,...n ] )  
 ソース テーブルとの暗黙の結合を実行するため、対象テーブルの 1 つ以上のインデックスの名前または ID を指定します。 詳細については、「[テーブル ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)」を参照してください。  
  
 \<output_clause >  
 行のすべての行を返します*対象テーブル*が更新、挿入、または任意の順序で、削除します。 **$action** output 句で指定することができます。 **$action**型の列は、 **nvarchar (10)**行ごとに 3 つの値のいずれかを返します: 'INSERT'、'UPDATE'、または 'DELETE'、その行に対して実行されたアクションに従ってします。 この句の引数の詳細については、次を参照してください。 [OUTPUT 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/output-clause-transact-sql.md).  
  
 オプション ( \<query_hint > [、.. .n])  
 オプティマイザー ヒントを使用して、データベース エンジンがステートメントを処理する方法をカスタマイズすることを指定します。 詳細については、「[クエリ ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)」を参照してください。  
  
 \<merge_matched >  
 更新プログラムを指定またはのすべての行に適用されるアクションを削除*対象テーブル*によって返される行は一致しない\<table_source > ON \<merge_search_condition >、いずれかに一致します。追加の検索条件。  
  
 UPDATE SET \<set_clause >  
 対象テーブル内で更新する列名または変数名の一覧と、それらの更新に使用する値を指定します。  
  
 この句の引数の詳細については、次を参照してください。[更新 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/update-transact-sql.md). 列と同じ値を変数に設定することはできません。  
  
 DELETE  
 内の行に一致する行を指定します*対象テーブル*は削除されます。  
  
 \<merge_not_matched >  
 対象テーブルに挿入する値を指定します。  
  
 (*column_list*)  
 データを挿入する、対象テーブルの 1 つ以上の列で構成されるリストを指定します。 列は 1 部構成の名前で指定する必要があります。そうしないと MERGE ステートメントが失敗します。 *column_list*をかっこで囲むしてコンマで区切る必要があります。  
  
 値 ( *values_list*)  
 対象テーブルに挿入する値を返す定数、変数、または式を、コンマ区切りのリストで指定します。 式には、EXECUTE ステートメントを含めることはできません。  
  
 DEFAULT VALUES  
 挿入される行が、各列に対して定義されている既定値で構成されることを指定します。  
  
 この句の詳細については、次を参照してください。 [INSERT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/insert-transact-sql.md).  
  
 \<検索条件 >  
 指定するために使用する検索条件を指定\<merge_search_condition > または\<clause_search_condition >。 この句の引数の詳細については、次を参照してください。[検索条件 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/search-condition-transact-sql.md).  
  
## <a name="remarks"></a>解説  
 3 つの MATCHED 句のうち、少なくとも 1 つは指定する必要があります。これらの句は、任意の順序で指定できます。 1 つの MATCHED 句で 1 つの変数を複数回更新することはできません。  
  
 MERGE ステートメントによって対象テーブルに指定された挿入、更新、削除の各操作は、連鎖参照整合性制約など、定義されている制約の制限を受けます。 対象テーブルの一意インデックスで IGNORE_DUP_KEY が ON に設定されていると、MERGE ではこの設定が無視されます。  
  
 MERGE ステートメントでは、ステートメントのターミネータとしてセミコロン (;) が必要です。 MERGE ステートメントにターミネータを付けずに実行すると、エラー 10713 が生成されます。  
  
 MERGE の後に使用すると[@@ROWCOUNT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/rowcount-transact-sql.md)挿入、更新、およびクライアントに削除された行の合計数を返します。  
  
 データベースの互換性レベルが 100 以上に設定されている場合、MERGE は完全に予約されたキーワードです。 MERGE ステートメントはデータベースの互換性レベルが 90 と 100 の両方で使用できますが、データベースの互換性レベルが 90 に設定されている場合、MERGE キーワードは完全には予約されていません。  
  
 **マージ**更新中のレプリケーションを使用してキューに置かれたときに、ステートメントは使用できません。 **マージ**とキュー更新トリガーは互換性がありません。 置換、**マージ**insert または update ステートメントのステートメント。  
  
## <a name="trigger-implementation"></a>トリガーの実装  
 すべての挿入、更新、または MERGE ステートメントで指定されたアクションの削除[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]対応する、対象のテーブルで定義された AFTER トリガーを起動するが、最初と最後のトリガーを起動するには、どのアクションには保証されません。 同じアクションに対して定義された複数のトリガーは、指定した順序に従います。 トリガー起動順序の設定の詳細については、次を参照してください。[指定最初と最後のトリガー](../../relational-databases/triggers/specify-first-and-last-triggers.md)です。  
  
 MERGE ステートメントによって実行される挿入、更新、削除のいずれかの操作に対して、有効な INSTEAD OF トリガーが対象テーブルに定義されている場合、MERGE ステートメントに指定されたすべての操作に有効な INSTEAD OF トリガーを定義する必要があります。  
  
 INSTEAD OF UPDATE がまたはで INSTEAD OF DELETE トリガーが定義されている場合は*対象テーブル*、update または delete 操作は実行されません。 代わりに、トリガーが起動され、**挿入**と**削除**テーブルはそれに従って作成されます。  
  
 ないで定義されている挿入トリガーではなく*対象テーブル*、挿入操作は実行されません。 代わりに、トリガーが起動され、**挿入**テーブルはそれに従って作成されます。  
  
## <a name="permissions"></a>Permissions  
 ソース テーブルに対する SELECT 権限と、対象テーブルに対する INSERT、UPDATE、または DELETE 権限が必要です。 詳細については、アクセス許可」セクションを参照してください、[選択](../../t-sql/queries/select-transact-sql.md)、[挿入](../../t-sql/statements/insert-transact-sql.md)、[更新](../../t-sql/queries/update-transact-sql.md)、および[削除](../../t-sql/statements/delete-transact-sql.md)トピックです。  
  
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
 次の例では、MERGE を使用して、`ProductInventory` テーブルで処理される注文に基づいて、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] サンプル データベース内の `SalesOrderDetail` テーブルを毎日更新します。 `Quantity` テーブルで各製品のその日の注文数を差し引くことで、`ProductInventory` テーブルの `SalesOrderDetail` 列を更新します。 製品の注文の数は、0 に、製品のレベルが以下に、インベントリを削除からその製品の行が削除、`ProductInventory`テーブル。  
  
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
 次の例でマージを使用して変更する、`SalesReason`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]を更新または行を挿入するデータベース。 ときの値`NewName`テーブル ソース内の値に一致する、 `Name` 、対象のテーブルの列 (`SalesReason`) では、`ReasonType`ターゲット テーブルの列を更新します。 `NewName` の値が一致しない場合は、ソース行が対象テーブルに挿入されます。 ソース テーブルが使用する派生テーブル、[!INCLUDE[tsql](../../includes/tsql-md.md)]ソース テーブルの複数の行を指定するテーブル値コンス トラクターです。 詳細については、派生テーブルでテーブル値コンス トラクターを使用して、次を参照してください。[テーブル値コンス トラクターと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/table-value-constructor-transact-sql.md). この例では、OUTPUT 句の結果をテーブル変数に格納し、挿入された行数と更新された行数を返す単純な選択操作を実行することで MERGE ステートメントの結果をまとめる方法も示しています。  
  
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
 [OUTPUT 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/output-clause-transact-sql.md)   
 [Integration services パッケージをマージします。](../../integration-services/control-flow/merge-in-integration-services-packages.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [テーブル値コンス トラクターと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/table-value-constructor-transact-sql.md)  
  
  

