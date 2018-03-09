---
title: "(除算)(TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- /
- /_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- / (divide)
- division [SQL Server]
- divide operator (/)
ms.assetid: 1d69893b-e5c3-441d-8dd8-0e5eb872ecfc
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: a327ba041992614b4da0817d4b9f669b1e83b2f6
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="-division-transact-sql"></a>/(除算) (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  1 つの値を別の値で除算します (算術除算演算子)。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
dividend / divisor  
```  
  
## <a name="arguments"></a>引数  
 *dividend*  
 除算される数値式です。 *被除数*任意の有効なことができる[式](../../t-sql/language-elements/expressions-transact-sql.md)、数値のデータ型のいずれかのデータ型に分類を除く、 **datetime**と**smalldatetime**データ型。  
  
 *divisor*  
 被除数を除算する数値式です。 *除数*を除く、数値データ型カテゴリのデータ型のいずれかの有効な式を指定できます、 **datetime**と**smalldatetime**データ型。  
  
## <a name="result-types"></a>戻り値の型  
 優先順位が高い引数のデータ型を返します。 詳細については、「[データ型の優先順位 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-type-precedence-transact-sql.md)」を参照してください。  
  
 場合整数*被除数*が整数で除算された*除数*を持つ小数部の切り捨てられた整数になります。  
  
## <a name="remarks"></a>解説  
 / 演算子で返される実際の値は、1 番目の式を 2 番目の式で除算して得られる商です。  
  
## <a name="examples"></a>使用例  
 次の例では、算術除算演算子を使用して、[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)] の販売員の各月の販売目標を計算しています。  
  
```  
-- Uses AdventureWorks  
  
SELECT s.BusinessEntityID AS SalesPersonID, FirstName, LastName, SalesQuota, SalesQuota/12 AS 'Sales Target Per Month'  
FROM Sales.SalesPerson AS s   
JOIN HumanResources.Employee AS e   
    ON s.BusinessEntityID = e.BusinessEntityID  
JOIN Person.Person AS p   
    ON e.BusinessEntityID = p.BusinessEntityID;  
```  
  
 部分的な結果セットを次に示します。  
  
```  
  
SalesPersonID FirstName    LastName          SalesQuota  Sales Target Per Month  
------------- ------------ ----------------- ----------- ------------------  
274           Stephen      Jiang             NULL        NULL  
275           Michael      Blythe            300000.00   25000.00  
276           Linda        Mitchell          250000.00   20833.3333  
277           Jillian      Carson            250000.00   20833.3333  
  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、算術除算演算子を使用して、病欠時間に各従業員の休暇時間数の単純な比率を計算します。  
  
```  
-- Uses AdventureWorks  
  
SELECT FirstName, LastName, VacationHours/SickLeaveHours AS PersonalTimeRatio  
FROM DimEmployee;  
  
```  
  
## <a name="see-also"></a>参照  
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)   
 [/= (& a) #40; 除算代入 &#41;&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/divide-equals-transact-sql.md)   
 [複合の演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/compound-operators-transact-sql.md)  
  
  


