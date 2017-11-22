---
title: "選択 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/24/2017
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
- SELECT_TSQL
- SELECT
dev_langs: TSQL
helpviewer_keywords:
- retrieving rows
- SELECT statement [SQL Server]
- SELECT statement [SQL Server], about SELECT statement
- row retrieval [SQL Server], SELECT statement
- DML [SQL Server], SELECT statement
- data manipulation language [SQL Server], SELECT statement
- row retrieval [SQL Server]
- queries [SQL Server], results
ms.assetid: dc85caea-54d1-49af-b166-f3aa2f3a93d0
caps.latest.revision: "51"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 012853c97e01250bf5aee62d95ae7971549f5094
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="select-transact-sql"></a>SELECT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  データベースから行が取得され、1 つ以上のテーブルからの行または列の 1 つまたは複数を選択できるように[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 SELECT ステートメントの完全な構文は複雑ですが、主な句は次のとおりです。  
  
[で {[XMLNAMESPACES] [ \<common_table_expression >]}]
  
 選択*select_list* [INTO *new_table* ]  
  
 [から*table_source* ] [場所*search_condition* ]  
  
 [GROUP BY *group_by_expression* ]  
  
 [持つ*search_condition* ]  
  
 [ORDER BY *order_expression* [ASC |DESC]  
  
 UNION、EXCEPT、INTERSECT 演算子はクエリを結合または比較の結果の 1 つの結果セットの間で使用できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
<SELECT statement> ::=    
    [ WITH { [ XMLNAMESPACES ,] [ <common_table_expression> [,...n] ] } ]  
    <query_expression>   
    [ ORDER BY { order_by_expression | column_position [ ASC | DESC ] }   
  [ ,...n ] ]   
    [ <FOR Clause>]   
    [ OPTION ( <query_hint> [ ,...n ] ) ]   
<query_expression> ::=   
    { <query_specification> | ( <query_expression> ) }   
    [  { UNION [ ALL ] | EXCEPT | INTERSECT }  
        <query_specification> | ( <query_expression> ) [...n ] ]   
<query_specification> ::=   
SELECT [ ALL | DISTINCT ]   
    [TOP ( expression ) [PERCENT] [ WITH TIES ] ]   
    < select_list >   
    [ INTO new_table ]   
    [ FROM { <table_source> } [ ,...n ] ]   
    [ WHERE <search_condition> ]   
    [ <GROUP BY> ]   
    [ HAVING < search_condition > ]   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
[ WITH <common_table_expression> [ ,...n ] ]  
SELECT <select_criteria>  
[;]  
  
<select_criteria> ::=  
    [ TOP ( top_expression ) ]   
    [ ALL | DISTINCT ]   
    { * | column_name | expression } [ ,...n ]   
    [ FROM { table_source } [ ,...n ] ]  
    [ WHERE <search_condition> ]   
    [ GROUP BY <group_by_clause> ]   
    [ HAVING <search_condition> ]   
    [ ORDER BY <order_by_expression> ]  
    [ OPTION ( <query_option> [ ,...n ] ) ]  
  
```  
  
## <a name="remarks"></a>解説  
 SELECT ステートメントは非常に複雑であるため、構文の構成要素と引数の詳細を句ごとに説明します。  
  
|||  
|-|-|  
|[WITH XMLNAMESPACES](../../t-sql/xml/with-xmlnamespaces.md)<br /><br /> [WITH common_table_expression](../../t-sql/queries/with-common-table-expression-transact-sql.md)|[持つ](../../t-sql/queries/select-having-transact-sql.md)|  
|[SELECT 句](../../t-sql/queries/select-clause-transact-sql.md)|[共用体](../../t-sql/language-elements/set-operators-union-transact-sql.md)|  
|[INTO 句](../../t-sql/queries/select-into-clause-transact-sql.md)|[EXCEPT および INTERSECT](../../t-sql/language-elements/set-operators-except-and-intersect-transact-sql.md)|  
|[FROM](../../t-sql/queries/from-transact-sql.md)|[ORDER BY](../../t-sql/queries/select-order-by-clause-transact-sql.md)|  
|[WHERE](../../t-sql/queries/where-transact-sql.md)|[FOR 句](../../t-sql/queries/select-for-clause-transact-sql.md)|  
|[グループ化](../../t-sql/queries/select-group-by-transact-sql.md)|[OPTION 句](../../t-sql/queries/option-clause-transact-sql.md)|  
  
 SELECT ステートメント内の句の順序は重要です。 オプションの句は省略できます。ただし、オプションの句を使用する場合は、適切な順序で指定する必要があります。  
  
 ユーザー定義関数に SELECT ステートメントを指定できるのは、関数にとってローカルな変数に値を代入する式がステートメントの選択リストに含まれる場合だけです。  
  
 サーバー名の部分として OPENDATASOURCE 関数で構築された 4 部構成の名前は、テーブル名は、SELECT ステートメントで指定できるテーブル ソースとして使用できます。 4 部構成の名前を指定することはできません[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 リモート テーブルに関係する SELECT ステートメントには、構文の制約がいくつか適用されます。  
  
## <a name="logical-processing-order-of-the-select-statement"></a>SELECT ステートメントの論理的な処理順序  
 以下のステップは、SELECT ステートメントの論理的な処理順序 (バインド順序) を示しています。 この順序によって、1 つのステップで定義されたオブジェクトが、以降のステップにおける句でいつ利用可能になるかが決まります。 たとえば、クエリ プロセッサが FROM 句で定義されているテーブルまたはビューにバインド (アクセス) できる場合、これらのオブジェクトとその列は、以降のすべてのステップで利用できます。 逆に、SELECT 句はステップ 8 にあるので、この句で定義されているすべての列の別名と派生列は、それより前の句では参照できません。 ただし、ORDER BY 句などの後続の句で参照されていることができます。 ステートメントの実際の物理的な実行は、クエリ プロセッサによって決定され、この一覧から、順序が異なる場合があります。  
  
1.  FROM  
2.  ON  
3.  JOIN  
4.  WHERE  
5.  GROUP BY  
6.  WITH CUBE または WITH ROLLUP  
7.  HAVING  
8.  SELECT  
9. DISTINCT  
10. ORDER BY  
11. 先頭に戻る  

> [!WARNING]
> 上記の順序は、通常は true です。 ただしは一般的でない場合は、シーケンスが異なる場合があります。
>
> たとえば、ビューがいくつかのテーブル行を除外およびビューの SELECT 列リストから、データ型を変更する変換を使用して、ビューにクラスター化インデックスがある*varchar*に*整数*です。 このような状況では、変換は、WHERE 句を実行する前に実行できます。 珍しいことで実際にします。 多くの場合、方法がある場合で問題になる場合は、別のシーケンスを避けるためにビューを変更します。 

## <a name="permissions"></a>Permissions  
 データの選択にはテーブルまたはビューに対する **SELECT** 権限が必要です。この権限は、スキーマに対する **SELECT** 権限やテーブルに対する **CONTROL** 権限など上位スコープから継承されます。 メンバーシップが必要か、 **db_datareader**または**db_owner**固定データベース ロール、または**sysadmin**固定サーバー ロール。 使用して新しいテーブルを作成する**SELECTINTO**両方も必要、 **CREATETABLE**権限、および**ALTERSCHEMA**新しいテーブルを所有するスキーマに対する権限。  
  
## <a name="examples"></a>例 :   
次の例では、[!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)] データベースを使用します。
  
### <a name="a-using-select-to-retrieve-rows-and-columns"></a>A. SELECT を使用して行および列を取得する  
 このセクションでは、次の 3 つのコード例を示します。 この最初のコード例には、(WHERE 句が指定されていない) すべての行とすべての列が返されます (を使用して、 `*`) から、`DimEmployee`テーブル。  
  
```sql  
SELECT *  
FROM DimEmployee  
ORDER BY LastName;  
```  
  
 テーブル別名を使用して、同じ結果を達成する次の例です。  
  
```sql  
SELECT e.*  
FROM DimEmployee AS e  
ORDER BY LastName;  
```  
  
 この例は、(WHERE 句が指定されていない) すべての行と列のサブセットを返します (`FirstName`、 `LastName`、 `StartDate`) から、`DimEmployee`テーブルに、`AdventureWorksPDW2012`データベース。 3 番目の列見出しの名前を変更する`FirstDay`です。  
  
```sql  
SELECT FirstName, LastName, StartDate AS FirstDay  
FROM DimEmployee   
ORDER BY LastName;  
```  
  
 この例の行のみを返します`DimEmployee`がある、`EndDate`が NULL でないと、`MaritalStatus`の AM' (結婚)。  
  
```sql  
SELECT FirstName, LastName, StartDate AS FirstDay  
FROM DimEmployee   
WHERE EndDate IS NOT NULL   
AND MaritalStatus = 'M'  
ORDER BY LastName;  
```  
  
### <a name="b-using-select-with-column-headings-and-calculations"></a>B. 列ヘッダーおよび計算処理と共に SELECT を使用する  
 次の例は、すべての行を返します、`DimEmployee`テーブル、およびに基づいて各従業員の支給総額が計算されます、`BaseRate`と 40 時間稼働します。  
  
```sql  
SELECT FirstName, LastName, BaseRate, BaseRate * 40 AS GrossPay  
FROM DimEmployee  
ORDER BY LastName;  
```  
  
### <a name="c-using-distinct-with-select"></a>C. DISTINCT を SELECT と共に使用する  
 次の例で`DISTINCT`すべて一意のタイトルの一覧を生成する、`DimEmployee`テーブル。  
  
```sql  
SELECT DISTINCT Title  
FROM DimEmployee  
ORDER BY Title;  
```  
  
### <a name="d-using-group-by"></a>D. GROUP BY を使用する  
 次の例では、各日に、すべての売上の合計金額を検索します。  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey  
ORDER BY OrderDateKey;  
```  
  
 ため、`GROUP BY`句、毎日のすべての売上合計を含む 1 つだけの行が返されます。  
  
### <a name="e-using-group-by-with-multiple-groups"></a>E. GROUP BY を複数のグループと共に使用する  
 次の例は、1 日に、発注日および昇格キーによってグループ化に対して、平均価格とインターネット販売の合計を検索します。  
  
```sql  

SELECT OrderDateKey, PromotionKey, AVG(SalesAmount) AS AvgSales, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey, PromotionKey  
ORDER BY OrderDateKey;   
```  
  
### <a name="f-using-group-by-and-where"></a>F. GROUP BY と WHERE を使用する  
 次の例では、受注日、2002 年 8 月 1 日より後の行のみを取得した後、結果がグループを格納します。  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
WHERE OrderDateKey > '20020801'  
GROUP BY OrderDateKey  
ORDER BY OrderDateKey;  
```  
  
### <a name="g-using-group-by-with-an-expression"></a>G. 1 つの式と共に GROUP BY を使用する  
 次の例では、式によってグループ化します。 式に集計関数が含まれない限り、式によってグループ化することができます。  
  
```sql  
SELECT SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY (OrderDateKey * 10);  
```  
  
### <a name="h-using-group-by-with-order-by"></a>H. ORDER BY と共に GROUP BY を使用する  
 次の例では、1 日で日、および注文あたりの売り上げ高の合計を検索します。  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey  
ORDER BY OrderDateKey;  
```  
  
### <a name="i-using-the-having-clause"></a>I. HAVING 句を使用する  
 このクエリを使用して、`HAVING`結果を制限する句。  
  
```sql  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales  
FROM FactInternetSales  
GROUP BY OrderDateKey  
HAVING OrderDateKey > 20010000  
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>参照  
 [例 &#40; を選択します。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-examples-transact-sql.md)  
 [ヒント &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/hints-transact-sql.md)
  

