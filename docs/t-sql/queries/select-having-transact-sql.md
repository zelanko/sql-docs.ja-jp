---
title: "(TRANSACT-SQL) を持つ |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/28/2017
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
- HAVING
- HAVING_TSQL
dev_langs: TSQL
helpviewer_keywords:
- restricting conditions for result set
- search conditions [SQL Server], HAVING clause
- HAVING clause
- HAVING clause, about HAVING clause
ms.assetid: 55650709-001e-42f4-902f-ead09a3c34af
caps.latest.revision: "27"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: cf99ee7aece979c973d2d162062ac2bae7aac296
ms.sourcegitcommit: 721ad1cbc10e8147c087ae36b36296d72cbb0de8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/07/2017
---
# <a name="select---having-transact-sql"></a>選択 - こと (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  グループまたは集計の検索条件を指定します。 HAVING は、SELECT ステートメントと共にのみ使用できます。 通常、HAVING は GROUP BY 句と共に使用します。 GROUP BY を使用しない場合は、暗黙的な集計された、1 つのグループです。   
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
[ HAVING <search condition> ]  
```  
  
## <a name="arguments"></a>引数  
\<search_condition > を満たすには、グループまたは集計の 1 つまたは複数の述語を指定します。 検索条件および述語の詳細については、次を参照してください。[検索条件 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/search-condition-transact-sql.md)  
  
 **テキスト**、**イメージ**、および**ntext**データ型は HAVING 句では使用できません。  
  
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
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例で、`HAVING`句の合計を取得する`SalesAmount`から、`FactInternetSales`時にテーブル、`OrderDateKey`年 2004 以降に。  
  
```  
-- Uses AdventureWorks  
  
SELECT OrderDateKey, SUM(SalesAmount) AS TotalSales   
FROM FactInternetSales  
GROUP BY OrderDateKey   
HAVING SUM(SalesAmount) > 80000  
ORDER BY OrderDateKey;  
```  
  
## <a name="see-also"></a>参照  
 [GROUP BY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/select-group-by-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)  
  
  

