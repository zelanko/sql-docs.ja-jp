---
title: "(TRANSACT-SQL) で |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/29/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IN_TSQL
- IN
dev_langs: TSQL
helpviewer_keywords:
- values [SQL Server], matching
- NOT IN keyword
- 8623 (Database Engine error)
- matching values in subquery or list [SQL Server]
- IN keyword
- 8632 (Database Engine error)
ms.assetid: 4419de73-96b1-4dfe-8500-f4507915db04
caps.latest.revision: "37"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 610c374bb6d935495779362d8dd7f1e0a53931d8
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="in-transact-sql"></a>IN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定された値が、サブクエリまたは一覧内の値と一致するかどうかを判断します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
test_expression [ NOT ] IN   
    ( subquery | expression [ ,...n ]  
    )   
```  
  
## <a name="arguments"></a>引数  
 *test_expression*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。  
  
 *subquery*  
 1 列の結果セットを返すサブクエリです。 この列と同じデータ型を持つ必要があります*な任意*です。  
  
 *expression*[ **,**... *n* ]  
 一致するかどうかのテストに使用する式のリストです。 すべての式と同じ型でなければなりません*な任意*です。  
  
## <a name="result-types"></a>戻り値の型  
 **ブール値**  
  
## <a name="result-value"></a>結果の値  
 場合の値*な任意*がによって返される任意の値に等しい*サブクエリ*と等しいか、または*式*コンマ区切りの一覧から、結果の値は TRUE です。それ以外の場合、結果の値は FALSE です。  
  
 否定 NOT IN を使用して、*サブクエリ*値または*式*です。  
  
> [!CAUTION]  
>  Null 値によって返される*サブクエリ*または*式*へと比較される*な任意*IN を使用するかではなく UNKNOWN が返されます。 IN または NOT IN と共に NULL 値を使用すると、予期しない結果が生じる可能性があります。  
  
## <a name="remarks"></a>解説  
 IN 句に、かっこで囲まれた明示的に非常に多数の値 (何千ものコンマで区切られた値) を含む、リソースを消費し、エラー 8623 または 8632 が返されることができます。 この問題を回避するには、テーブルのボックスの一覧で項目を格納し、IN 句の中で SELECT サブクエリを使用します。  
  
 エラー 8623:  
  
 `The query processor ran out of internal resources and could not produce a query plan. This is a rare event and only expected for extremely complex queries or queries that reference a very large number of tables or partitions. Please simplify the query. If you believe you have received this message in error, contact Customer Support Services for more information.`  
  
 エラー 8632:  
  
 `Internal error: An expression services limit has been reached. Please look for potentially complex expressions in your query, and try to simplify them.`  
  
## <a name="examples"></a>使用例  
  
### <a name="a-comparing-or-and-in"></a>A. OR と IN を比較する  
 次の例では、デザイン エンジニア、ツール デザイナー、またはマーケティング アシスタントのいずれかである従業員の名前の一覧を選択します。  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, e.JobTitle  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e  
    ON p.BusinessEntityID = e.BusinessEntityID  
WHERE e.JobTitle = 'Design Engineer'   
   OR e.JobTitle = 'Tool Designer'   
   OR e.JobTitle = 'Marketing Assistant';  
GO  
```  
  
 IN を使用しても同じ結果が得られます。  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName, e.JobTitle  
FROM Person.Person AS p  
JOIN HumanResources.Employee AS e  
    ON p.BusinessEntityID = e.BusinessEntityID  
WHERE e.JobTitle IN ('Design Engineer', 'Tool Designer', 'Marketing Assistant');  
GO  
```  
  
 いずれかのクエリからの結果セットを次に示します。  
  
```  
FirstName   LastName      Title  
---------   ---------   ---------------------  
Sharon      Salavaria   Design Engineer                                     
Gail        Erickson    Design Engineer                                     
Jossef      Goldberg    Design Engineer                                     
Janice      Galvin      Tool Designer                                       
Thierry     D'Hers      Tool Designer                                       
Wanida      Benshoof    Marketing Assistant                                 
Kevin       Brown       Marketing Assistant                                 
Mary        Dempsey     Marketing Assistant                                 
  
(8 row(s) affected)  
```  
  
### <a name="b-using-in-with-a-subquery"></a>B. IN とサブクエリを使用する  
 次の例は、販売員のすべての Id を検索、`SalesPerson`年度の 250,000 ドルの販売ノルマがありからを選択し、従業員のテーブル、`Employee`テーブルのすべての従業員名、`EmployeeID`と一致する、結果、`SELECT`サブクエリ。  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName  
FROM Person.Person AS p  
    JOIN Sales.SalesPerson AS sp  
    ON p.BusinessEntityID = sp.BusinessEntityID  
WHERE p.BusinessEntityID IN  
   (SELECT BusinessEntityID  
   FROM Sales.SalesPerson  
   WHERE SalesQuota > 250000);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
FirstName   LastName                                             
---------   --------   
Tsvi         Reiter                                              
Michael      Blythe                                              
Tete         Mensa-Annan                                         
  
(3 row(s) affected)  
```  
  
### <a name="c-using-not-in-with-a-subquery"></a>C. NOT IN とサブクエリを使用する  
 次の例では、販売ノルマが 250,000 ドル以下の販売員が検索されます。 `NOT IN` は、値の一覧に一致する項目がない販売員を検索します。  
  
```  
-- Uses AdventureWorks  
  
SELECT p.FirstName, p.LastName  
FROM Person.Person AS p  
    JOIN Sales.SalesPerson AS sp  
    ON p.BusinessEntityID = sp.BusinessEntityID  
WHERE p.BusinessEntityID NOT IN  
   (SELECT BusinessEntityID  
   FROM Sales.SalesPerson  
   WHERE SalesQuota > 250000);  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-in-and-not-in"></a>D. ではなくを使用します。  
 次の例は、すべてのエントリを検索、`FactInternetSales`テーブルと一致する`SalesReasonKey`の値が、`DimSalesReason`テーブル。  
  
```  
-- Uses AdventureWorks  
  
SELECT * FROM FactInternetSalesReason   
WHERE SalesReasonKey   
IN (SELECT SalesReasonKey FROM DimSalesReason);   
```  
  
 次の例は、すべてのエントリを検索、`FactInternetSalesReason`テーブルと一致しない`SalesReasonKey`の値が、`DimSalesReason`テーブル。  
  
```  
-- Uses AdventureWorks  
  
SELECT * FROM FactInternetSalesReason   
WHERE SalesReasonKey   
NOT IN (SELECT SalesReasonKey FROM DimSalesReason);  
```  
  
### <a name="e-using-in-with-an-expression-list"></a>E. 式のリストで使用します。  
 次の例は、販売員のすべての Id を検索、`DimEmployee`最初を持つ従業員名のいずれかのテーブル`Mike`または`Michael`です。  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName  
FROM DimEmployee  
WHERE FirstName IN ('Mike', 'Michael');  
```  
  
## <a name="see-also"></a>参照  
 [場合 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/case-transact-sql.md)   
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)   
 [ALL と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/all-transact-sql.md)   
 [一部 &#124;です。いずれかと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/some-any-transact-sql.md)  
  
  



