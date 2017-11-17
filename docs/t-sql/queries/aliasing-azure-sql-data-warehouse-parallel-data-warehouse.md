---
title: "エイリアス (Azure SQL Data Warehouse、並列データ ウェアハウス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
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
ms.assetid: 7b3a5c74-05cf-4385-8ee6-6176d003cb8a
caps.latest.revision: 11
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: edc81ce4377f490b482d920871ad361c98f961c5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="aliasing-azure-sql-data-warehouse-parallel-data-warehouse"></a>エイリアス (Azure SQL Data Warehouse、並列データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  エイリアスがあることでテーブルまたは列名の代わりに、短期的および覚えやすい文字列の一時的な置換[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)][!INCLUDE[DWsql](../../includes/dwsql-md.md)]クエリ。 テーブルの別名は、結合の構文は、列を参照するときに、完全修飾オブジェクト名を必要とするために多くの場合、結合クエリで使用されます。  
  
 エイリアスは、オブジェクトの名前付け規則に準拠している 1 つの単語である必要があります。 詳細については、「オブジェクトの名前付け規則」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。 エイリアスは、空白文字を含めることはできず、単一引用符または二重引用符で囲むことはできません。  
  
## <a name="syntax"></a>構文  
  
```  
object_source [ AS ] alias  
```  
  
## <a name="arguments"></a>引数  
 *object_source*  
 ソース テーブルまたは列の名前。  
  
 AS  
 省略可能なエイリアス置くの場合。 範囲変数のエイリアスを使用する場合は、AS キーワードが禁止されています。  
  
 *エイリアス*  
 テーブルまたは列の目的の一時的な参照名。 任意の有効なオブジェクト名を使用できます。 詳細については、「オブジェクトの名前付け規則」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例は、複数の結合のクエリを示しています。 この例では、テーブルと列の両方のエイリアスが示されています。  
  
-   列の別名: 両方の列と、選択リスト内の列を含む式は、この例で別名を指定します。 `SalesTerritoryRegion AS SalesTR`単純な列の別名を示しています。 `Sum(SalesAmountQuota) AS TotalSales`示します  
  
-   テーブル別名:`dbo.DimSalesTerritory AS st`の作成を示しています、`st`のエイリアス、`dbo.DimSalesTerritory`テーブル。  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) AS TotalSales, SalesTerritoryRegion AS SalesTR,  
    RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) AS RankResult  
FROM dbo.DimEmployee AS e  
INNER JOIN dbo.FactSalesQuota AS sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory AS st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
  
```  
  
 AS キーワードは、次のように、除外することが読みやすくするために含まれる多くの場合。  
  
```  
-- Uses AdventureWorks  
  
SELECT LastName, SUM(SalesAmountQuota) TotalSales, SalesTerritoryRegion SalesTR,  
RANK() OVER (PARTITION BY SalesTerritoryRegion ORDER BY SUM(SalesAmountQuota) DESC ) RankResult  
FROM dbo.DimEmployee e  
INNER JOIN dbo.FactSalesQuota sq ON e.EmployeeKey = sq.EmployeeKey  
INNER JOIN dbo.DimSalesTerritory st ON e.SalesTerritoryKey = st.SalesTerritoryKey  
WHERE SalesPersonFlag = 1 AND SalesTerritoryRegion != N'NA'  
GROUP BY LastName, SalesTerritoryRegion;  
```  
  
## <a name="see-also"></a>参照  
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [UPDATE &#40;Transact-SQL&#41;](../../t-sql/queries/update-transact-sql.md)  
  
  

