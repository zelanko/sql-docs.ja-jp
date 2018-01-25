---
title: "検索条件 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/15/2018
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
- search
- Search Condition
- condition
dev_langs: TSQL
helpviewer_keywords:
- OR operator [Transact-SQL]
- CONTAINS predicate (Transact-SQL)
- ESCAPE keyword
- operators [Transact-SQL], search condition
- search conditions [SQL Server]
- WHERE clause, search conditions
- ALL keyword
- FREETEXT predicate (Transact-SQL)
- EXISTS keyword
- search conditions [SQL Server], about search conditions
- NOT operator [Transact-SQL]
- BETWEEN operator
- SOME | ANY keyword
- predicates [full-text search]
- AND, about search conditions
- logical operators [SQL Server], about search conditions
- precedence [SQL Server], logical operators
- logical operators [SQL Server], precedence
- LIKE comparisons
ms.assetid: 09974469-c5d2-4be8-bc5a-78e404660b2c
caps.latest.revision: "43"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e507b4e7e14c68f629708255a1cfd6ab06cadb5f
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="search-condition-transact-sql"></a>検索条件 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  論理演算子 AND、OR、および NOT を使用した、1 つ以上の述語の組み合わせです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
<search_condition> ::=   
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
  ( { column | * } , '<contains_search_condition>' )   
    | FREETEXT ( { column | * } , 'freetext_string' )   
    | expression [ NOT ] IN ( subquery | expression [ ,...n ] )   
    | expression { = | < > | ! = | > | > = | ! > | < | < = | ! < }   
  { ALL | SOME | ANY} ( subquery )   
    | EXISTS ( subquery )     }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
< search_condition > ::=   
    { [ NOT ] <predicate> | ( <search_condition> ) }   
    [ { AND | OR } [ NOT ] { <predicate> | ( <search_condition> ) } ]   
[ ,...n ]   
  
<predicate> ::=   
    { expression { = | < > | ! = | > | > = | < | < = } expression   
    | string_expression [ NOT ] LIKE string_expression   
    | expression [ NOT ] BETWEEN expression AND expression   
    | expression IS [ NOT ] NULL   
    | expression [ NOT ] IN (subquery | expression [ ,...n ] )   
    | expression [ NOT ] EXISTS (subquery)     }   
```  
  
## <a name="arguments"></a>引数  
 \<search_condition>  
 SELECT ステートメント、クエリ式、またはサブクエリの場合、結果セットに返す行の条件を指定します。 UPDATE ステートメントの場合、更新する行を指定します。 DELETE ステートメントの場合、削除する行を指定します。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの検索条件に含まれる述語の数に制限はありません。  
  
 [NOT]  
 述語によって指定されたブール式を否定します。 詳細については、次を参照してください。[いない &#40;です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/not-transact-sql.md)。  
  
 [AND]  
 2 つの条件を結合し、両方の条件が真の場合に TRUE と評価します。 詳細については、次を参照してください。 [AND &#40;です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/and-transact-sql.md)。  
  
 または  
 2 つの条件を結合し、少なくとも片方の条件が真の場合に TRUE と評価します。 詳細については、次を参照してください。[または &#40;です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/or-transact-sql.md)。  
  
 \<述語 >  
 TRUE、FALSE、または UNKNOWN を返す式です。  
  
 *式 (expression)*  
 列名、定数、関数、変数、スカラー サブクエリ、または 1 つ以上の演算子やサブクエリで接続された列名、定数、および関数の組み合わせです。 expression には CASE 式が含まれる場合もあります。  
  
> [!NOTE]  
>  非 Unicode 文字列定数と変数は、データベースの既定の照合順序に対応するコード ページを使用します。 コード ページ変換が発生の非 Unicode 文字のデータのみを使用する場合と非 Unicode 文字データ型を参照する**char**、 **varchar**、および**テキスト**です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]参照先の列の照合順序に対応するか、そのコード ページが、データベースの既定の照合順序に対応するコード ページと異なる場合、COLLATE を使用するを指定するコード ページには、非 Unicode 文字列定数と変数を変換します。 新しいコード ページに存在しない任意の文字の場合は、類似した文字に変換されます、[最適マッピング](http://www.unicode.org/Public/MAPPINGS/VENDORS/MICSFT/WindowsBestFit/)の既定の置換文字に変換されるか、または見つからない"?"。  
>  
> 複数のコード ページを使用するときに文字定数の先頭に大文字の ' N '、および Unicode コード ページ変換を避けるために、変数を使用できます。  
  
 =  
 2 つの式が等しいことを調べるのに使用する演算子です。  
  
 <>  
 2 つの式が互いに等しくないという条件を調べるのに使用する演算子です。  
  
 !=  
 2 つの式が互いに等しくないという条件を調べるのに使用する演算子です。  
  
 \>  
 一方の式がもう一方の式より大きいという条件を調べるのに使用する演算子です。  
  
 \>=  
 一方の式がもう一方の式以上であるという条件を調べるのに使用する演算子です。  
  
 !>  
 一方の式がもう一方の式より大きくないという条件を調べるのに使用する演算子です。  
  
 <  
 一方の式がもう一方の式より小さいという条件を調べるのに使用する演算子です。  
  
 <=  
 一方の式がもう一方の式以下であるという条件を調べるのに使用する演算子です。  
  
 !<  
 一方の式がもう一方の式より小さくないという条件を調べるのに使用する演算子です。  
  
 *string_expression*  
 文字列とワイルドカード文字から成る文字列です。  
  
 [ NOT ] LIKE  
 後続の文字列が、パターン照合で使用されます。 詳細については、次を参照してください。[のような &#40;です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/like-transact-sql.md)。  
  
 ESCAPE **'***escape_ character***'**  
 ワイルドカードとして機能するのではなく、ワイルドカード文字そのものを文字列内で検索できます。 *escape_character*この特別な用途を示すために、ワイルドカード文字の前に配置されている文字です。  
  
 [ NOT ] BETWEEN  
 両端を含む値の範囲を指定します。 最初と最後の値を除外するには、AND を使用します。 詳細については、次を参照してください。 [BETWEEN &#40;です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/between-transact-sql.md)。  
  
 IS [NOT] NULL  
 指定のキーワードに応じて、NULL 値または NULL 値以外の値の検索を指定します。 ビットごとの演算子や算術演算子を使う式は、オペランドの少なくとも 1 つが NULL であれば、NULL と評価されます。  
  
 CONTAINS  
 検索またはあいまいの文字ベースのデータを含む列 (*あいまい*) 1 つの単語または語句、特定の範囲内で 1 つの別、および重み付き検索語の近接度に一致します。 このオプションは、SELECT ステートメントでのみ使用できます。 詳細については、次を参照してください。 [CONTAINS &#40;です。TRANSACT-SQL と #41 です](../../t-sql/queries/contains-transact-sql.md)。  
  
 FREETEXT  
 文字ベースのデータを含む列で、述語内の文字の並びと正確に一致しなくても意味が合っている値を検索するための、単純形式の自然言語クエリを指定します。 このオプションは、SELECT ステートメントでのみ使用できます。 詳細については、次を参照してください。 [FREETEXT &#40;です。TRANSACT-SQL と #41 です](../../t-sql/queries/freetext-transact-sql.md)。  
  
 [ NOT ] IN  
 式がリストに含まれているかどうかに基づいて、式の検索を指定します。 検索式には定数または列名を指定できます。またリストには、一般的にはサブクエリが指定されますが、一連の定数も指定できます。 値のリストはかっこで囲んでください。 詳細については、「[IN &#40;Transact-SQL&#41;](../../t-sql/language-elements/in-transact-sql.md)」を参照してください。  
  
 *subquery*  
 制限された SELECT ステートメントと見なされます。 と似ています\<query_expresssion > SELECT ステートメントでします。 ORDER BY 句および INTO キーワードは使用できません。 詳細については、次を参照してください[SELECT &#40;。TRANSACT-SQL と #41 です](../../t-sql/queries/select-transact-sql.md)。  
  
 ALL  
 比較演算子およびサブクエリと共に使用します。 に対して TRUE を返します\<述語 > ときに、サブクエリから取得したすべての値を満たす、比較操作またはすべての値の場合は FALSE 比較要件を満たしてとき、サブクエリ行を返しません外側のステートメントにします。 詳細については、次を参照してください。 [ALL と #40 です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/all-transact-sql.md)。  
  
 { SOME | ANY }  
 比較演算子およびサブクエリと共に使用します。 に対して TRUE を返します\<述語 > サブクエリを満たす、比較操作またはサブクエリで値を持たない場合は FALSE 比較要件を満たしてとき、サブクエリ行を返しません外側のステートメントに対してに任意の値を取得するときにします。 それ以外の場合には、式は UNKNOWN と評価されます。 詳細については、次を参照してください。[一部 &#124;です。いずれかと #40 です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/some-any-transact-sql.md)。  
  
 EXISTS  
 サブクエリと共に使用され、サブクエリによって返される行が存在するかどうかを調べます。 詳細については、次を参照してください。 [EXISTS と #40 です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/exists-transact-sql.md)。  
  
## <a name="remarks"></a>解説  
 論理演算子の優先順位は、高い方から NOT、AND、OR です。 かっこを使用することによって、検索条件におけるこれらの優先順位を変更することができます。 論理演算子の評価順序は、クエリ オプティマイザーが行う選択によって異なる場合があります。 論理値の論理演算子の動作方法の詳細については、次を参照してください。 [AND &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/and-transact-sql.md)、[または &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/or-transact-sql.md)、および[いない &#40;です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/not-transact-sql.md)。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-where-with-like-and-escape-syntax"></a>A. WHERE を LIKE および ESCAPE 構文と共に使用する  
 次の例である行の検索、`LargePhotoFileName`列が文字`green_`を使用して、 `ESCAPE` _ ワイルドカード文字は、オプションを指定します。 指定せず、`ESCAPE`オプション、説明の値、単語を含むクエリで検索が`green`_ 文字以外の任意の 1 文字が続きます。  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT *   
FROM Production.ProductPhoto  
WHERE LargePhotoFileName LIKE '%greena_%' ESCAPE 'a' ;  
```  
  
### <a name="b-using-where-and-like-syntax-with-unicode-data"></a>B. WHERE および LIKE 構文を UNICODE データと共に使用する  
 次の例では、`WHERE`米国外にあるすべての会社の住所を取得する句 (`US`) で始まる名前を持つ都市で`Pa`です。  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT AddressLine1, AddressLine2, City, PostalCode, CountryRegionCode    
FROM Person.Address AS a  
JOIN Person.StateProvince AS s ON a.StateProvinceID = s.StateProvinceID  
WHERE CountryRegionCode NOT IN ('US')  
AND City LIKE N'Pa%' ;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-where-with-like"></a>C. WHERE を like を使用してください。  
 次の例である行の検索、`LastName`列が文字`and`です。  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName LIKE '%and%';  
```  
  
### <a name="d-using-where-and-like-syntax-with-unicode-data"></a>D. WHERE および LIKE 構文を UNICODE データと共に使用する  
 次の例では、`WHERE`句で Unicode 検索を実行する、`LastName`列です。  
  
```  
-- Uses AdventureWorks  
  
SELECT EmployeeKey, LastName  
FROM DimEmployee  
WHERE LastName LIKE N'%and%';  
```  
  
## <a name="see-also"></a>参照  
 [集計関数と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/aggregate-functions-transact-sql.md)   
 [場合 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/case-transact-sql.md)   
 [CONTAINSTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [カーソル &#40;Transact-SQL&#41;](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [FREETEXTTABLE &#40;Transact-SQL&#41;](../../relational-databases/system-functions/freetexttable-transact-sql.md)   
 [FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
  
  

