---
title: "ISNULL (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ISNULL
- ISNULL_TSQL
- IFNULL_TSQL
dev_langs: TSQL
helpviewer_keywords:
- replacing null values
- null values [SQL Server], ISNULL
- null values [SQL Server], replacement values
- ISNULL function
ms.assetid: 6f3e5802-864b-4e77-9862-657bb5430b68
caps.latest.revision: "42"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: ad067dd6df83e49c3a46fd5955945f79c20d1b96
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="isnull-transact-sql"></a>ISNULL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  NULL 値を、指定された値に置き換えます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
ISNULL ( check_expression , replacement_value )  
```  
  
## <a name="arguments"></a>引数  
 *check_expression*  
 [式](../../t-sql/language-elements/expressions-transact-sql.md)に NULL をチェックします。 *check_expression*任意の型を指定できます。  
  
 *replacement_value*  
 場合に返される式は、 *check_expression*は NULL です。 *replacement_value*の型に暗黙的に変換できる型でなければなりません*check_expresssion*です。  
  
## <a name="return-types"></a>戻り値の型  
 同じ型を返します*check_expression*です。 リテラル NULL が指定されている場合*check_expression*のデータ型を返します、 *replacement_value*です。 リテラル NULL が指定されている場合*check_expression*および no *replacement_value*提供されるを返します、 **int**です。  
  
## <a name="remarks"></a>解説  
 値*check_expression*かどうかは NULL それ以外の場合、返される*replacement_value*はの型に暗黙的に変換した後に返される*check_expression*。型が異なる場合は、します。 *replacement_value*場合に切り捨てられる*replacement_value*よりも長い*check_expression*です。  
  
> [!NOTE]  
>  使用して[COALESCE &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/coalesce-transact-sql.md)を最初の null 以外の値を返します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-isnull-with-avg"></a>A. AVG で ISNULL を使用する  
 次の例では、すべての製品の重量の平均を求めます。 値を置き換える`50`すべて NULL エントリ、`Weight`の列、`Product`テーブル。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT AVG(ISNULL(Weight, 50))  
FROM Production.Product;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 -------------------------- 
59.79  
  
 (1 row(s) affected)
 ```  
  
### <a name="b-using-isnull"></a>B. ISNULL を使用する  
 次の例では、`AdventureWorks2012` のすべての特価品について、説明、値引き率、最小数量、および最大数量を選択します。 ある特価品の最大数量が NULL の場合、結果セットに表示される `MaxQty` は `0.00` です。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Description, DiscountPct, MinQty, ISNULL(MaxQty, 0.00) AS 'Max Quantity'  
FROM Sales.SpecialOffer;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|  Description       |  DiscountPct    |   MinQty    |   最大数量       |
|  ---------------   |  -------------  |   --------  |   ---------------    |
|  No Discount       |  0.00           |   0         |   0                  |
|  Volume Discount   |  0.02           |   11        |   14                 |
|  Volume Discount   |  0.05           |   15        |   4                  |
|  Volume Discount   |  0.10           |   25        |   0                  |
|  Volume Discount   |  0.15           |   41        |   0                  |
|  Volume Discount   |  0.20           |   61        |   0                  |
|  Mountain-100 Cl   |  0.35           |   0         |   0                  |
|  スポーツ Helmet Di   |  0.10           |   0         |   0                  |
|  道路 650 Overst   |  0.30           |   0         |   0                  |
|  Mountain Tire S   |  0.50           |   0         |   0                  |
|  スポーツ Helmet Di   |  0.15           |   0         |   0                  |
|  LL 道路フレーム S   |  0.35           |   0         |   0                  |
|  Touring 3000 Pr   |  0.15           |   0         |   0                  |
|  Touring 1000 Pr   |  0.20           |   0         |   0                  |
|  半価格 Peda   |  0.50           |   0         |   0                  |
|  Mountain-500 Si   |  0.40           |   0         |   0                  |

 `(16 row(s) affected)`  
  
### <a name="c-testing-for-null-in-a-where-clause"></a>C. WHERE 句で NULL をテストする  
 NULL 値の検索に ISNULL を使用しないでください。 代わりに IS NULL を使用します。 次の例では、weight 列が `NULL` の製品をすべて検索しています。 `IS` と `NULL` の間にスペースがあることに注意してください。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT Name, Weight  
FROM Production.Product  
WHERE Weight IS NULL;  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="d-using-isnull-with-avg"></a>D. AVG で ISNULL を使用する  
 次の例では、サンプル テーブル内のすべての製品の重量の平均値を検索します。 値を置き換える`50`すべて NULL エントリ、`Weight`の列、`Product`テーブル。  
  
```  
-- Uses AdventureWorks  
  
SELECT AVG(ISNULL(Weight, 50))  
FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------------------------   
52.88   
```  
  
### <a name="e-using-isnull"></a>E. ISNULL を使用する  
 次の例で ISNULL を使用して、列で NULL 値をテスト`MinPaymentAmount`値を表示および`0.00`これらの行にします。  
  
```  
-- Uses AdventureWorks  
  
SELECT ResellerName,   
       ISNULL(MinPaymentAmount,0) AS MinimumPayment  
FROM dbo.DimReseller  
ORDER BY ResellerName;  
  
```  
  
 部分的な結果セットを次に示します。  
  
|  ResellerName                |  MinimumPayment    |
|  -------------------------   |  --------------    |
|  自転車の関連付け       |     0.0000         |
|  Bike Store                |     0.0000         |
|  サイクル ショップ                |     0.0000         |
|  優れた自転車会社     |     0.0000         |
|  通常のバイク ショップ         |   200.0000         |
|  許容可能な Sales & サービス  |     0.0000         |
  
### <a name="f-using-is-null-to-test-for-null-in-a-where-clause"></a>F. IS NULL を使用して、WHERE 句で NULL をテストするには  
 次の例を持つすべての製品を検索する`NULL`で、`Weight`列です。 `IS` と `NULL` の間にスペースがあることに注意してください。  
  
```  
-- Uses AdventureWorks  
  
SELECT EnglishProductName, Weight  
FROM dbo.DimProduct  
WHERE Weight IS NULL;  
```  
  
## <a name="see-also"></a>参照  
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [NULL と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/is-null-transact-sql.md)   
 [システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)   
 [合体 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/coalesce-transact-sql.md)  
  
  

