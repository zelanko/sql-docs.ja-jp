---
title: "共用体 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/07/2017
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
- UNION
- UNION_TSQL
dev_langs: TSQL
helpviewer_keywords:
- UNION queries
- combining query results
- UNION operator [SQL Server]
ms.assetid: 607c296f-8a6a-49bc-975a-b8d0c0914df7
caps.latest.revision: "34"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 7c71b2eae1c0c3e55d09cdc5af2dfd7740df143f
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="set-operators---union-transact-sql"></a>集合演算子の和集合 (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  複数のクエリの結果を、1 つの結果セットに結合します。すべてのクエリの結果セットに含まれるすべての行は、その共用体に含まれます。 これは、2 つのテーブルの列を結合した結合列とは異なります。  
  
 UNION を使用して 2 つのクエリの結果セットを結合するための基本的な規則を以下に示します。  
  
-   列の数と順番は、すべてのクエリで同じであること  
  
-   データ型に互換性があること  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
    { <query_specification> | ( <query_expression> ) }   
  UNION [ ALL ]   
  <query_specification | ( <query_expression> )   
 [ UNION [ ALL ] <query_specification> | ( <query_expression> )   
    [ ...n ] ]   
```  
  
## <a name="arguments"></a>引数  
\<query_specification> | ( \<query_expression> ) Is a query specification or query expression that returns data to be combined with the data from another query specification or query expression. UNION 操作の一部である列の定義は同じである必要はありませんが、暗黙的な変換により一致させる必要があります。 規則に基づいて、結果のデータ型を決定するデータ型が異なる場合、[データ型の優先順位](../../t-sql/data-types/data-type-precedence-transact-sql.md)です。 型が同じで、有効桁数、小数点以下桁数、長さが異なる場合、結果は式の結合と同じ規則に基づいて決定されます。 詳しくは、「[有効桁数、小数点以下桁数、および長さ &#40;Transact-SQL&#41;](../../t-sql/data-types/precision-scale-and-length-transact-sql.md)」をご覧ください。  
  
 列、 **xml**データ型は、同等である必要があります。 また、すべての列が XML スキーマに従って型指定されているか、型指定されていないかのいずれかでなければなりません。 型指定されている場合は、同じ XML スキーマ コレクションに従って型指定されている必要があります。  
  
 UNION  
 複数の結果セットを結合し、1 つの結果セットとして返すことを指定します。  
  
 ALL  
 すべての行が結果セットに含まれます。 これには、重複した行も含まれます。 指定しない場合、重複する行は削除されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-a-simple-union"></a>A. 単純な UNION を使用する  
 次の例では、結果セットに `ProductModelID` テーブルと `Name` テーブルの `ProductModel` 列と `Gloves` 列の内容が含まれています。  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
-- Here is the simple union.  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves  
ORDER BY Name;  
GO  
```  
  
### <a name="b-using-select-into-with-union"></a>B. UNION と共に SELECT INTO を使用する  
 この例では、2 番目の `INTO` ステートメントの `SELECT` 句で、`ProductResults` および `ProductModel` テーブルの指定された列のユニオンの最終的な結果セットを `Gloves` という名前のテーブルに格納することを指定します。 `Gloves` テーブルは、最初の `SELECT` ステートメントで作成されます。  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.ProductResults', 'U') IS NOT NULL  
DROP TABLE dbo.ProductResults;  
GO  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
INTO dbo.ProductResults  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves;  
GO  
  
SELECT ProductModelID, Name   
FROM dbo.ProductResults;  
  
```  
  
### <a name="c-using-union-of-two-select-statements-with-order-by"></a>C. ORDER BY 句を指定した 2 つの SELECT ステートメントで UNION 句を使用する  
 UNION 句で使用するある種のパラメーターの順序には重要な意味があります。 次の例では、誤った方法と正しい使用`UNION`を 2 つ`SELECT`ステートメントは、列の出力に名前を変更します。  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.Gloves', 'U') IS NOT NULL  
DROP TABLE dbo.Gloves;  
GO  
-- Create Gloves table.  
SELECT ProductModelID, Name  
INTO dbo.Gloves  
FROM Production.ProductModel  
WHERE ProductModelID IN (3, 4);  
GO  
  
/* INCORRECT */  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
ORDER BY Name  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves;  
GO  
  
/* CORRECT */  
-- Uses AdventureWorks  
  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID NOT IN (3, 4)  
UNION  
SELECT ProductModelID, Name  
FROM dbo.Gloves  
ORDER BY Name;  
GO  
  
```  
  
### <a name="d-using-union-of-three-select-statements-to-show-the-effects-of-all-and-parentheses"></a>D. 3 つの SELECT ステートメントで UNION を使用して、ALL とかっこの効果を示す  
 次の例を使用して`UNION`3 つのテーブルが同じ 5 行のデータがあるすべての結果を結合します。 最初の例では、`UNION ALL` を使用して、重複するレコードも含めて 15 行すべてを返します。 2 番目の例では`UNION`せず`ALL`、3 つの結合された結果から重複する行を削除する`SELECT`ステートメント、および 5 行を返します。  
  
 3 番目の例では、最初の `ALL` と共に `UNION` を使用し、`UNION` を使用していない 2 番目の `ALL` をかっこで囲んでいます。 2 番目`UNION`最初に処理されますが、かっこでは、5 行を返すため、`ALL`オプションを使用しないと、重複を削除します。 これらの 5 行は、最初の結果の結合`SELECT`を使用して、`UNION ALL`キーワード。 これによって 2 組の 5 行の間での重複が削除されることはありません。 最終的な結果は 10 行になります。  
  
```  
-- Uses AdventureWorks  
  
IF OBJECT_ID ('dbo.EmployeeOne', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeOne;  
GO  
IF OBJECT_ID ('dbo.EmployeeTwo', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeTwo;  
GO  
IF OBJECT_ID ('dbo.EmployeeThree', 'U') IS NOT NULL  
DROP TABLE dbo.EmployeeThree;  
GO  
  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeOne  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeTwo  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
SELECT pp.LastName, pp.FirstName, e.JobTitle   
INTO dbo.EmployeeThree  
FROM Person.Person AS pp JOIN HumanResources.Employee AS e  
ON e.BusinessEntityID = pp.BusinessEntityID  
WHERE LastName = 'Johnson';  
GO  
-- Union ALL  
SELECT LastName, FirstName, JobTitle  
FROM dbo.EmployeeOne  
UNION ALL  
SELECT LastName, FirstName ,JobTitle  
FROM dbo.EmployeeTwo  
UNION ALL  
SELECT LastName, FirstName,JobTitle   
FROM dbo.EmployeeThree;  
GO  
  
SELECT LastName, FirstName,JobTitle  
FROM dbo.EmployeeOne  
UNION   
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeTwo  
UNION   
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeThree;  
GO  
  
SELECT LastName, FirstName,JobTitle   
FROM dbo.EmployeeOne  
UNION ALL  
(  
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeTwo  
UNION  
SELECT LastName, FirstName, JobTitle   
FROM dbo.EmployeeThree  
);  
GO  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="e-using-a-simple-union"></a>E. 単純な UNION を使用する  
 次の例では、結果セットには内容が含まれています、`CustomerKey`両方の列、`FactInternetSales`と`DimCustomer`テーブル。 ALL キーワードが使用されていないために、重複は結果から除外されます。  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey   
FROM FactInternetSales    
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="f-using-union-of-two-select-statements-with-order-by"></a>F. ORDER BY 句を指定した 2 つの SELECT ステートメントで UNION 句を使用する  
 UNION ステートメント内のすべての SELECT ステートメントには、ORDER BY 句が含まれている場合は、すべての SELECT ステートメントの後にその句を配置する必要があります。 次の例では、誤った方法と正しい使用`UNION`を 2 つ`SELECT`ステートメントの列が ORDER BY で順序付けします。  
  
```  
-- Uses AdventureWorks  
  
-- INCORRECT  
SELECT CustomerKey   
FROM FactInternetSales    
ORDER BY CustomerKey  
UNION   
SELECT CustomerKey   
FROM DimCustomer  
ORDER BY CustomerKey;  
  
-- CORRECT   
USE AdventureWorksPDW2012;  
  
SELECT CustomerKey   
FROM FactInternetSales    
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="g-using-union-of-two-select-statements-with-where-and-order-by"></a>G. 場所を使用しての 2 つの SELECT ステートメントで UNION を使用して、ORDER BY  
 次の例では、誤った方法と正しい使用`UNION`を 2 つ`SELECT`ステートメント パラメーターの説明、ORDER BY が必要です。  
  
```  
-- Uses AdventureWorks  
  
-- INCORRECT   
SELECT CustomerKey   
FROM FactInternetSales   
WHERE CustomerKey >= 11000  
ORDER BY CustomerKey   
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
  
-- CORRECT  
USE AdventureWorksPDW2012;  
  
SELECT CustomerKey   
FROM FactInternetSales   
WHERE CustomerKey >= 11000  
UNION   
SELECT CustomerKey   
FROM DimCustomer   
ORDER BY CustomerKey;  
```  
  
### <a name="h-using-union-of-three-select-statements-to-show-effects-of-all-and-parentheses"></a>H. 3 つの SELECT ステートメントで UNION を使用して、すべての効果とかっこを表示するには  
 次の例を使用して`UNION`の結果を結合する**、同じテーブル**を使用する場合に、かっことすべての効果をデモンストレーションするために`UNION`です。  
  
 最初の例では`UNION ALL`重複するレコードを返す各テーブルの行のソース 3 回です。 2 番目の例では`UNION`せず`ALL`、3 つの結合された結果から重複する行を削除する`SELECT`ステートメントと、ソース テーブルから重複していない行のみを返します。  
  
 3 番目の例では`ALL`最初で`UNION`と 2 番目を囲むかっこ`UNION`を使用していない`ALL`です。 2 番目`UNION`かっこ内になっているために最初に処理されます。 テーブルから重複していない行のみを返しますが、`ALL`オプションを使用しないと、重複は削除されます。 これらの行は、最初の結果の結合`SELECT`を使用して、`UNION ALL`キーワード。 これには、2 つのセット間での重複は削除されません。  
  
```  
-- Uses AdventureWorks  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer;  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer;  
  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION ALL  
(  
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
UNION   
SELECT CustomerKey, FirstName, LastName  
FROM DimCustomer  
);  
```  
  
## <a name="see-also"></a>参照  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [例 &#40; を選択します。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-examples-transact-sql.md)  
  
  

