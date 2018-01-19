---
title: "比較演算子 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|language-elements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: TSQL
helpviewer_keywords:
- expressions [SQL Server], testing
- operators [Transact-SQL], comparison
- testing expressions
- Boolean data type
- Boolean expressions
- comparing expressions
- comparison operators [SQL Server]
ms.assetid: b0cc68ef-3029-484c-a917-0c15dcbc230d
caps.latest.revision: "35"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 7c36efad752eb830b44415add3d279a4a3ecf3ab
ms.sourcegitcommit: 6c54e67818ec7b0a2e3c1f6e8aca0fdf65e6625f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="comparison-operators-transact-sql"></a>比較演算子 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  比較演算子は、2 つの式が同じかどうかをテストします。 比較演算子の式を除くすべての式で使用できます、**テキスト**、 **ntext**、または**イメージ**データ型。 次の表、[!INCLUDE[tsql](../../includes/tsql-md.md)]比較演算子です。  
  
|演算子|意味|  
|--------------|-------------|  
|[= (等しい)](../../t-sql/language-elements/equals-transact-sql.md)|等しい|  
|[> (より大きい)](../../t-sql/language-elements/greater-than-transact-sql.md)|より大きい|  
|[< (より小さい)](../../t-sql/language-elements/less-than-transact-sql.md)|より小さい|  
|[>= (以上)](../../t-sql/language-elements/greater-than-or-equal-to-transact-sql.md)|以上|  
|[<= (以下)](../../t-sql/language-elements/less-than-or-equal-to-transact-sql.md)|以下|  
|[<> (等しくない)](../../t-sql/language-elements/not-equal-to-transact-sql-traditional.md)|等しくない|  
|[\!= (等しくない)](../../t-sql/language-elements/not-equal-to-transact-sql-exclamation.md)|等しくない (ISO 標準外)|  
|[\!< (より小さくない)](../../t-sql/language-elements/not-less-than-transact-sql.md)|より小さくない (ISO 標準外)|  
|[\!> (より大きくない)](../../t-sql/language-elements/not-greater-than-transact-sql.md)|より大きくない (ISO 標準外)|  
  
## <a name="boolean-data-type"></a>ブール値型  
 比較演算子の結果は、**ブール**データ型。 有効値には、TRUE、FALSE、UNKNOWN があります。 返す式、**ブール**データ型はブール式と呼ばれます。  
  
 その他のとは異なり[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型、**ブール**データ型がテーブル列または変数のデータ型として指定することはできませんし、結果セットに返されることはできません。  
  
 SET ANSI_NULLS が ON の場合、1 つまたは 2 つの NULL 式が含まれる演算子では UNKNOWN が返されます。 SET ANSI_NULLS が OFF の場合も同じ規則が適用されますが、両方の式が NULL の場合は、等号 (=) 演算子で TRUE が返されます。 たとえば、NULL = NULL は、SET ANSI_NULLS が OFF の場合 TRUE を返します。  
  
 含む式**ブール**データの種類を対象となる、検索条件およびフロー制御言語ステートメントでこのようなまたは IF や WHILE、たとえば、行をフィルター処理する WHERE 句で使用されます。  
  
```  
-- Uses AdventureWorks  
  
DECLARE @MyProduct int;  
SET @MyProduct = 750;  
IF (@MyProduct <> 0)  
   SELECT ProductID, Name, ProductNumber  
   FROM Production.Product  
   WHERE ProductID = @MyProduct;  
```  
  
## <a name="see-also"></a>参照  
 [式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)  
 [演算子 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/operators-transact-sql.md)  
  
  
