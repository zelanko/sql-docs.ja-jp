---
title: "いくつか |任意 (TRANSACT-SQL) |Microsoft ドキュメント"
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
- SOME
- SOME_TSQL
dev_langs: TSQL
helpviewer_keywords:
- scalar values
- comparing scalar with single-column set
- ANY operator
- SOME | ANY keyword
- single-column set of values [SQL Server]
ms.assetid: 1f717ad6-f67b-4980-9397-577ecb0e5789
caps.latest.revision: "41"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 0f99a9d507b74dfd12bbdaf273683f857ceec881
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="some--any-transact-sql"></a>SOME | ANY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  スカラー値を単一列で構成される値のセットと比較します。 SOME と ANY は等価です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
scalar_expression { = | < > | ! = | > | > = | ! > | < | < = | ! < }   
     { SOME | ANY } ( subquery )   
```  
  
## <a name="arguments"></a>引数  
 *scalar_expression*  
 有効な[式](../../t-sql/language-elements/expressions-transact-sql.md)です。  
  
 { = | <> | != | > | >= | !> | < | <= | !< }  
 有効な比較演算子です。  
  
 SOME | ANY  
 比較を行うことを指定します。  
  
 *subquery*  
 1 列の結果セットを返すサブクエリです。 返される列のデータ型が同じデータ型にする必要があります*scalar_expression*です。  
  
## <a name="result-types"></a>戻り値の型  
 **ブール値**  
  
## <a name="result-value"></a>結果の値  
 SOME または ANY を返します**TRUE**指定された比較が TRUE の場合、ペアに対して (*scalar_expression***、***x*) 場所*x*内の値は、単一列セットです。返しますそれ以外の場合、 **FALSE**です。  
  
## <a name="remarks"></a>解説  
 いくつかが必要、 *scalar_expression*サブクエリによって返されるには、少なくとも 1 つの値に対し肯定的な比較をします。 ステートメントを必要とする、 *scalar_expression* 、サブクエリによって返されるすべての値に対し肯定的な比較を参照してください。 [ALL と #40 です。TRANSACT-SQL と #41 です](../../t-sql/language-elements/all-transact-sql.md)。 たとえば、サブクエリは 2 および 3 の値を返す場合は、 *scalar_expression* = SOME (subquery) は TRUE と評価、 *scalar_express* 2 のです。 サブクエリは 2 および 3 の値を返す場合*scalar_expression* = ALL (subquery) はサブクエリ (値 3) の値の一部は、式の条件を満たさないために、FALSE と評価します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-running-a-simple-example"></a>A. 簡単な例を実行する  
 次のステートメントでは、簡単なテーブルを作成し、`1` 列に値 `2`、`3`、`4`、`ID` を追加します。  
  
```  
CREATE TABLE T1  
(ID int) ;  
GO  
INSERT T1 VALUES (1) ;  
INSERT T1 VALUES (2) ;  
INSERT T1 VALUES (3) ;  
INSERT T1 VALUES (4) ;  
```  
  
 次のクエリを返します`TRUE`ため`3`がいくつかのテーブル内の値より小さい。  
  
```  
IF 3 < SOME (SELECT ID FROM T1)  
PRINT 'TRUE'   
ELSE  
PRINT 'FALSE' ;  
```  
  
 `FALSE` はテーブル内の値の中で最も小さい値ではないため、次のクエリは `3` を返します。  
  
```  
IF 3 < ALL (SELECT ID FROM T1)  
PRINT 'TRUE'   
ELSE  
PRINT 'FALSE' ;  
```  
  
### <a name="b-running-a-practical-example"></a>B. 実用的な例を実行する  
 次の例を決定するストアド プロシージャを作成するかどうか、指定のすべてのコンポーネント`SalesOrderID`で、`AdventureWorks2012`データベースは、指定した日数で製造できます。 この例の数の一覧を作成するサブクエリを使用して`DaysToManufacture`、特定のすべてのコンポーネントの値`SalesOrderID`、かどうか、サブクエリによっては指定の日数よりも大きい返される値のいずれかをテストし、そのします。 場合の各値`DaysToManufacture`提供された場合、条件が TRUE と最初のメッセージが出力した数より小さいですが返されます。  
  
```  
-- Uses AdventureWorks  
  
CREATE PROCEDURE ManyDaysToComplete @OrderID int, @NumberOfDays int  
AS  
IF   
@NumberOfDays < SOME  
   (  
    SELECT DaysToManufacture  
    FROM Sales.SalesOrderDetail  
    JOIN Production.Product   
    ON Sales.SalesOrderDetail.ProductID = Production.Product.ProductID   
    WHERE SalesOrderID = @OrderID  
   )  
PRINT 'At least one item for this order cannot be manufactured in specified number of days.'  
ELSE   
PRINT 'All items for this order can be manufactured in the specified number of days or less.' ;  
  
```  
  
 プロシージャをテストするを使用してプロシージャを実行、`SalesOrderID``49080`を必要とする 1 つのコンポーネントを持つ`2`曜日と 0 日を必要とする 2 つのコンポーネントです。 最初のステートメントは条件を満たしますが、 2 番目のクエリは条件を満たしません。  
  
```  
EXECUTE ManyDaysToComplete 49080, 2 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `All items for this order can be manufactured in the specified number of days or less.`  
  
```  
EXECUTE ManyDaysToComplete 49080, 1 ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `At least one item for this order cannot be manufactured in specified number of days.`  
  
## <a name="see-also"></a>参照  
 [ALL と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/all-transact-sql.md)   
 [場合 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/case-transact-sql.md)   
 [組み込み関数 &#40;Transact-SQL&#41;](~/t-sql/functions/functions.md)   
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [ここで &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/where-transact-sql.md)   
 [IN &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/in-transact-sql.md)  
  
  
