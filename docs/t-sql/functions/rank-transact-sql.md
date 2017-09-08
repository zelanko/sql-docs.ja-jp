---
title: "順位 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/25/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RANK
- RANK_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- row ranking [SQL Server]
- tied rows [SQL Server]
- ranking rows
- RANK function [Transact-SQL]
ms.assetid: 2d96f6d2-5db7-4b3c-a63e-213c58e4af55
caps.latest.revision: 62
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 304ceaedefe1755c56b27a8f6e64a922a1986bc0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="rank-transact-sql"></a>RANK (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  結果セットのパーティション内の各行の順位を返します。 行の順位は、その行より上にある順位の数に 1 を加えたものです。  

  ROW_NUMBER とランク似ています。 (たとえば 1、2、3、4, 5)、すべて ROW_NUMBER 番号は順番に行です。 ランクは、(たとえば 1、2、2、4, 5) 同順位の数値を提供します。   
  
> [!NOTE]
> ランクは、一時的な値は、クエリの実行時に計算されます。 テーブル内の数字を保持するため、次を参照してください。 [IDENTITY プロパティ](../../t-sql/statements/create-table-transact-sql-identity-property.md)と[シーケンス](../../t-sql/statements/create-sequence-transact-sql.md)です。 
   
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
RANK ( ) OVER ( [ partition_by_clause ] order_by_clause )  
```  
  
## <a name="arguments"></a>引数  
 経由で**(** [ *partition_by_clause* ] *order_by_clause***)**  
 *partition_by_clause*関数を適用するパーティションに FROM 句で生成される結果セットに分割します。 指定しない場合、関数ではクエリ結果セットのすべての行を 1 つのグループとして扱います。 *order_by_clause*関数が適用される前に、データの順序を決定します。 *Order_by_clause*が必要です。 \<行または範囲句 > RANK 関数の over 句を指定することはできません。 詳細については、次を参照してください。 [OVER 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-over-clause-transact-sql.md).  
  
## <a name="return-types"></a>戻り値の型  
 **bigint**  
  
## <a name="remarks"></a>解説  
 複数の行が 1 つの順位を分け合う場合は、それぞれの行に同じ順位が付けられます。 たとえば、上位 2 人の販売員の SalesYTD 値が同じである場合は、両方に順位 1 が付けられます。 SalesYTD が次に高い販売員には、順位 3 が付けられます。順位のより高い行が 2 つあるためです。 そのため、RANK 関数は連続した整数を返すとは限りません。  
  
 クエリ全体に使用される並べ替え順によって、結果セットにおける行の順序が決まります。  
  
 RANK は非決定的です。 詳細については、「 [決定的関数と非決定的関数](../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-ranking-rows-within-a-partition"></a>A. パーティション内の行に順位を付ける  
 次の例では、指定された在庫場所の在庫内の製品を数量に応じて順位付けしています。 結果セットは `LocationID` によってパーティションに分割され、`Quantity` によって論理的に順序付けされます。 494 と 495 の製品が同じ数量であることを確認します。 これらは数量が同じなので、両方とも順位が 1 位になっています。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT i.ProductID, p.Name, i.LocationID, i.Quantity  
    ,RANK() OVER   
    (PARTITION BY i.LocationID ORDER BY i.Quantity DESC) AS Rank  
FROM Production.ProductInventory AS i   
INNER JOIN Production.Product AS p   
    ON i.ProductID = p.ProductID  
WHERE i.LocationID BETWEEN 3 AND 4  
ORDER BY i.LocationID;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
  
ProductID   Name                   LocationID   Quantity Rank  
----------- ---------------------- ------------ -------- ----  
494         Paint - Silver         3            49       1  
495         Paint - Blue           3            49       1  
493         Paint - Red            3            41       3  
496         Paint - Yellow         3            30       4  
492         Paint - Black          3            17       5  
495         Paint - Blue           4            35       1  
496         Paint - Yellow         4            25       2  
493         Paint - Red            4            24       3  
492         Paint - Black          4            14       4  
494         Paint - Silver         4            12       5  
 (10 row(s) affected)  
```  
  
### <a name="b-ranking-all-rows-in-a-result-set"></a>B. 結果セット内のすべての行に順位を付ける  
 次の例では、給与に順位を付け、トップ 10 の従業員を返します。 PARTITION BY 句が指定されていないため、RANK 関数は結果セットのすべての行に適用されます。  
  
```  
USE AdventureWorks2012  
SELECT TOP(10) BusinessEntityID, Rate,   
       RANK() OVER (ORDER BY Rate DESC) AS RankBySalary  
FROM HumanResources.EmployeePayHistory AS eph1  
WHERE RateChangeDate = (SELECT MAX(RateChangeDate)   
                        FROM HumanResources.EmployeePayHistory AS eph2  
                        WHERE eph1.BusinessEntityID = eph2.BusinessEntityID)  
ORDER BY BusinessEntityID;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
BusinessEntityID Rate                  RankBySalary  
---------------- --------------------- --------------------  
1                125.50                1  
2                63.4615               4  
3                43.2692               8  
4                29.8462               19  
5                32.6923               16  
6                32.6923               16  
7                50.4808               6  
8                40.8654               10  
9                40.8654               10  
10               42.4808               9  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-ranking-rows-within-a-partition"></a>C:、パーティション内の行に順位付け  
 次の例では、売上合計に応じて販売区域ごとの販売担当者がランク付けします。 行セットは `SalesTerritoryGroup` によってパーティション分割され、`SalesAmountQuota` によって並べ替えられます。  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) AS TotalSales, SalesTerritoryRegion,  
    RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) AS RankResult  
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory AS st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `LastName          TotalSales     SalesTerritoryGroup  RankResult`  
  
 `----------------  -------------  -------------------  --------`  
  
 `Tsoflias          1687000.0000   Australia            1`  
  
 `Saraiva           7098000.0000   Canada               1`  
  
 `Vargas            4365000.0000   Canada               2`  
  
 `Carson            12198000.0000  Central              1`  
  
 `Varkey Chudukatil 5557000.0000   France               1`  
  
 `Valdez            2287000.0000   Germany              1`  
  
 `Blythe            11162000.0000  Northeast            1`  
  
 `Campbell          4025000.0000   Northwest            1`  
  
 `Ansman-Wolfe      3551000.0000   Northwest            2`  
  
 `Mensa-Annan       2753000.0000   Northwest            3`  
  
 `Reiter            8541000.0000   Southeast            1`  
  
 `Mitchell          11786000.0000  Southwest            1`  
  
 `Ito               7804000.0000   Southwest            2`  
  
 `Pak               10514000.0000  United Kingdom       1`  
  
## <a name="see-also"></a>参照  
 [DENSE_RANK & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/dense-rank-transact-sql.md)   
 [ROW_NUMBER & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/row-number-transact-sql.md)   
 [NTILE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ntile-transact-sql.md)   
 [順位付け関数 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ranking-functions-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)  
  
  




