---
title: "サブクエリ (Azure SQL Data Warehouse、並列データ ウェアハウス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e8ebd60-1936-48c9-b2b9-e099c8269fcf
caps.latest.revision: 
author: barbkess
ms.author: barbkess
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5b30ff820d9a9003a1832c8b4226adf20072fceb
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="subqueries-azure-sql-data-warehouse-parallel-data-warehouse"></a>サブクエリ (Azure SQL Data Warehouse、並列データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  このトピックでは内のサブクエリを使用する例[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。  
  
 SELECT ステートメントで、次を参照してください[SELECT &#40;。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-transact-sql.md)  
  
## <a name="contents"></a>目次  
  
-   [基本](#Basics)  
  
-   [例: SQL データ ウェアハウスと並列データ ウェアハウス](#Examples)  
  
##  <a name="Basics"></a>基本  
 サブクエリ  
 サブクエリとは、SELECT、INSERT、UPDATE、または DELETE の各ステートメントの内部、または別のサブクエリの内部で入れ子になっているクエリです。 これは、内部クエリや内部選択にも呼び出されます。  
  
 外側のクエリ  
 このステートメントは、サブクエリが含まれています。 これは外側の select とも呼ばれます。  
  
 相関サブクエリ  
 外側のクエリでテーブルを参照するサブクエリ。  
  
##  <a name="Examples"></a>例:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 このセクションでサポートされるサブクエリの例を示します[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。  
  
### <a name="a-top-and-order-by-in-a-subquery"></a>A. TOP と ORDER BY をサブクエリに  
  
```  
SELECT * FROM tblA  
WHERE col1 IN  
    (SELECT TOP 100 col1 FROM tblB ORDER BY col1);  
  
```  
  
### <a name="b-having-clause-with-a-correlated-subquery"></a>B. HAVING 句と相関サブクエリ  
  
```  
SELECT dm.EmployeeKey, dm.FirstName, dm.LastName   
FROM DimEmployee AS dm   
GROUP BY dm.EmployeeKey, dm.FirstName, dm.LastName  
HAVING 5000 <=   
(SELECT sum(OrderQuantity)  
FROM FactResellerSales AS frs  
WHERE dm.EmployeeKey = frs.EmployeeKey)  
ORDER BY EmployeeKey;  
  
```  
  
### <a name="c-correlated-subqueries-with-analytics"></a>C. 分析を使った相関サブクエリ  
  
```  
SELECT * FROM ReplA AS A   
WHERE A.ID IN   
    (SELECT sum(B.ID2) OVER() FROM ReplB AS B WHERE A.ID2 = B.ID);  
```  
  
### <a name="d-correlated-union-statements-in-a-subquery"></a>D. 相関サブクエリで union ステートメント  
  
```  
SELECT * FROM RA   
WHERE EXISTS   
    (SELECT 1 FROM RB WHERE RB.b1 = RA.a1   
     UNION ALL SELECT 1 FROM RC);  
```  
  
### <a name="e-join-predicates-in-a-subquery"></a>E. サブクエリで述語を参加させる  
  
```  
SELECT * FROM RA INNER JOIN RB   
    ON RA.a1 = (SELECT COUNT(*) FROM RC);  
```  
  
### <a name="f-correlated-join-predicates-in-a-subquery"></a>F. サブクエリ相関結合述語  
  
```  
SELECT * FROM RA   
    WHERE RA.a2 IN   
    (SELECT 1 FROM RB INNER JOIN RC ON RA.a1=RB.b1+RC.c1);  
```  
  
### <a name="g-correlated-subselects-as-data-sources"></a>G. データ ソースとして相関サブセレクト  
  
```  
SELECT * FROM RA   
    WHERE 3 = (SELECT COUNT(*)   
        FROM (SELECT b1 FROM RB WHERE RB.b1 = RA.a1) X);  
```  
  
### <a name="h-correlated-subqueries-in-the-data-values--used-with-aggregates"></a>H. 集計関数と共に使用するデータ値の相関サブクエリ  
  
```  
SELECT Rb.b1, (SELECT RA.a1 FROM RA WHERE RB.b1 = RA.a1) FROM RB GROUP BY RB.b1;  
```  
  
### <a name="i-using-in-with-a-correlated-subquery"></a>I. 相関サブクエリを使用します。  
 次の例では、相関または繰り返しサブクエリ内で `IN` を使用しています。 これは、外側のクエリによって値が決まるクエリです。 内側のクエリを繰り返し実行は、行ごとに 1 回を選択できます外側のクエリでします。 このクエリは、1 つのインスタンスを取得、`EmployeeKey`と対象の各従業員の姓と名、`OrderQuantity`で、`FactResellerSales`テーブルが`5`一致で従業員の識別番号、`DimEmployee`と`FactResellerSales`テーブル。  
  
```  
SELECT DISTINCT dm.EmployeeKey, dm.FirstName, dm.LastName   
FROM DimEmployee AS dm   
WHERE 5 IN   
    (SELECT OrderQuantity  
    FROM FactResellerSales AS frs  
    WHERE dm.EmployeeKey = frs.EmployeeKey)  
ORDER BY EmployeeKey;  
```  
  
### <a name="j-using-exists-versus-in-with-a-subquery"></a>J. EXISTS in とサブクエリを使用します。  
 次の例では意味的に等しい使用方法の相違を説明するためにクエリ、`EXISTS`キーワードおよび`IN`キーワード。 これらの製品サブカテゴリの各製品名の 1 つのインスタンスを取得するサブクエリの例は`Road Bikes`します。 `ProductSubcategoryKey`間で一致する、`DimProduct`と`DimProductSubcategory`テーブル。  
  
```  
SELECT DISTINCT EnglishProductName  
FROM DimProduct AS dp   
WHERE EXISTS  
    (SELECT *  
     FROM DimProductSubcategory AS dps   
     WHERE dp.ProductSubcategoryKey = dps.ProductSubcategoryKey  
           AND dps.EnglishProductSubcategoryName = 'Road Bikes')  
ORDER BY EnglishProductName;  
```  
  
 または  
  
```  
SELECT DISTINCT EnglishProductName  
FROM DimProduct AS dp   
WHERE dp.ProductSubcategoryKey IN  
    (SELECT ProductSubcategoryKey  
     FROM DimProductSubcategory   
     WHERE EnglishProductSubcategoryName = 'Road Bikes')  
ORDER BY EnglishProductName;  
```  
  
### <a name="k-using-multiple-correlated-subqueries"></a>K. 複数の相関サブクエリを使用します。  
 この例では、2 つの相関サブクエリを使って、特定の製品を販売した従業員の名前を検索します。  
  
```  
SELECT DISTINCT LastName, FirstName, e.EmployeeKey  
FROM DimEmployee e JOIN FactResellerSales s ON e.EmployeeKey = s.EmployeeKey  
WHERE ProductKey IN  
(SELECT ProductKey FROM DimProduct WHERE ProductSubcategoryKey IN  
(SELECT ProductSubcategoryKey FROM DimProductSubcategory   
 WHERE EnglishProductSubcategoryName LIKE '%Bikes'))  
ORDER BY LastName  
;  
  
```  
  
  
