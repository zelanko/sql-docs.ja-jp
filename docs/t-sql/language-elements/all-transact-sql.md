---
title: "すべて (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- Azure SQL Database
- SQL Server (starting with 2008)
f1_keywords:
- ALL_TSQL
- ALL
dev_langs: TSQL
helpviewer_keywords:
- single-column set of values [SQL Server]
- ALL (Transact-SQL)
ms.assetid: 4b0c002e-1ffd-4425-a980-11fdc1f24af7
caps.latest.revision: "40"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: b6ea6be0d745ca5ce61a540e9a1e299671d8c7fd
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="all-transact-sql"></a>ALL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  スカラー値を単一列で構成される値のセットと比較します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
scalar_expression { = | <> | != | > | >= | !> | < | <= | !< } ALL ( subquery )  
```  
  
## <a name="arguments"></a>引数  
 *scalar_expression*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。  
  
 { = | <> | != | > | >= | !> | < | <= | !< }  
 比較演算子です。  
  
 *サブクエリ*  
 1 つの列の結果を返すサブクエリが設定されています。 返される列のデータ型は、データと同じ型のデータ型である必要があります*scalar_expression*です。  
  
 制限された SELECT ステートメントです。ORDER BY 句および INTO キーワードは使用できません。  
  
## <a name="result-types"></a>戻り値の型  
 **ブール値**  
  
## <a name="result-value"></a>結果の値  
 指定された比較が TRUE の場合は TRUE を返しますのすべてのペアの (*scalar_expression***、***x)*、 *x*内の値は、単一列セットです。それ以外の場合、FALSE を返します。  
  
## <a name="remarks"></a>解説  
 すべてが必要、 *scalar_expression*サブクエリによって返されるすべての値に対し肯定的な比較します。 インスタンスのサブクエリは 2 および 3 の値を返す場合は、 *scalar_expression* < = ALL (subquery) は TRUE と評価、 *scalar_expression* 2 のです。 サブクエリは 2 および 3 の値を返す場合*scalar_expression* = ALL (subquery) はサブクエリ (値 3) の値の一部は、式の条件を満たさないために、FALSE と評価します。  
  
 ステートメントを必要とする、 *scalar_expression* 、サブクエリによって返される 1 つだけの値に対し肯定的な比較を参照してください。[一部 &#124;です。いずれかと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/some-any-transact-sql.md).  
  
 このトピックでは、ALL をサブクエリと共に使用する場合を想定しています。 すべてでも使用できます[共用体](../../t-sql/language-elements/set-operators-union-transact-sql.md)と[選択](../../t-sql/queries/select-transact-sql.md)です。  
  
## <a name="examples"></a>使用例  
 次の例を決定するストアド プロシージャを作成するかどうか、指定のすべてのコンポーネント`SalesOrderID`で、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベースは、指定した日数で製造できます。 例では、数の一覧を作成するサブクエリを使用して`DaysToManufacture`、特定のコンポーネントのすべての値`SalesOrderID`、し確認をすべて、`DaysToManufacture`は日数内で指定します。  
  
```  
-- Uses AdventureWorks  
  
CREATE PROCEDURE DaysToBuild @OrderID int, @NumberOfDays int  
AS  
IF   
@NumberOfDays >= ALL  
   (  
    SELECT DaysToManufacture  
    FROM Sales.SalesOrderDetail  
    JOIN Production.Product   
    ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID   
    WHERE SalesOrderID = @OrderID  
   )  
PRINT 'All items for this order can be manufactured in specified number of days or less.'  
ELSE   
PRINT 'Some items for this order cannot be manufactured in specified number of days or less.' ;  
  
```  
  
 このプロシージャをテストするには、`SalesOrderID 49080` を使用してプロシージャを実行します。この注文内容には、必要な日数が `2` 日の部品が 1 つと 0 日の部品が 2 つが含まれています。 次に示す最初のステートメントは条件を満たしますが、 2 番目のクエリは条件を満たしません。  
  
```  
EXECUTE DaysToBuild 49080, 2 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `All items for this order can be manufactured in specified number of days or less.`  
  
```  
EXECUTE DaysToBuild 49080, 1 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Some items for this order cannot be manufactured in specified number of days or less.`  
  
## <a name="see-also"></a>参照  
 [場合 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/case-transact-sql.md)   
 [式 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/expressions-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [ような &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/like-transact-sql.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)   
 [IN &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/in-transact-sql.md)  
  
  
