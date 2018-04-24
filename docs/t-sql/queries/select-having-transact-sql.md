---
title: HAVING (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 11/28/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: t-sql|queries
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- HAVING
- HAVING_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- restricting conditions for result set
- search conditions [SQL Server], HAVING clause
- HAVING clause
- HAVING clause, about HAVING clause
ms.assetid: 55650709-001e-42f4-902f-ead09a3c34af
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7975851cc55a0d59472c93b4cd4753d7b6c408c1
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="select---having-transact-sql"></a>SELECT - HAVING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  グループまたは集計の検索条件を指定します。 HAVING は、SELECT ステートメントと共にのみ使用できます。 通常、HAVING は GROUP BY 句と共に使用されます。 GROUP BY を使用しない場合は、暗黙的な 1 つの集計グループがあります。   
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
[ HAVING <search condition> ]  
```  
  
## <a name="arguments"></a>引数  
\<search_condition> は、条件を満たすグループまたは集計の 1 つまたは複数の述語を指定します。 検索条件および述語の詳細については、「[検索条件 &#40;Transact-SQL&#41;](../../t-sql/queries/search-condition-transact-sql.md)」を参照してください。  
  
 **text**、**image**、および **ntext** 型は HAVING 句では使用できません。  
  
## <a name="examples"></a>使用例  
 次の例では、`HAVING` テーブルから `SalesOrderID` を超える `SalesOrderDetail` ごとの合計を取得する単純な `$100000.00` 句を使用しています。  
  
```  
USE AdventureWorks2012 ;  
GO  
SELECT SalesOrderID, SUM(LineTotal) AS SubTotal  
FROM Sales.SalesOrderDetail  
GROUP BY SalesOrderID  
HAVING SUM(LineTotal) > 100000.00  
ORDER BY SalesOrderID ;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、`HAVING` 句を使用して、`FactInternetSales` テーブルから `OrderDateKey` が 2004 年以降の各 `SalesAmount` の合計を取得します。  
  
```  
-- Uses AdventureWorks  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSales  
GROUP BY OrderDateKey   
HAVING SUM(SalesAmount) > 80000  
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>参照  
 [GROUP BY &#40;Transact-SQL&#41;](../../t-sql/queries/select-group-by-transact-sql.md)   
 [WHERE &#40;Transact-SQL&#41;](../../t-sql/queries/where-transact-sql.md)  
  
  

