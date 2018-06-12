---
title: スカラー関数の使用 |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a80933b1a9845ec2676fba470ed39e06ee7f4ad8
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34743901"
---
# <a name="using-scalar-expressions"></a>スカラー関数の使用


  多次元式 (MDX) では、スカラー関数は MDX 構文の要素であり、評価されるときに評価のコンテキスト内で 1 つの値を返します。  
  
 スカラー式には、MDX 形式の文字列式、数値式、および日付式が含まれます。  
  
 計算されるメンバーがスカラー値を返す必要があるため、通常、計算されるメンバーの定義ではスカラー式が使用されます。 次のクエリでは、さまざまな種類のスカラー式を使用する、メジャー ディメンションの計算されるメンバーの例を示します。  
  
 `WITH`  
  
 `MEMBER MEASURES.NumericValue AS 10`  
  
 `MEMBER MEASURES.NumericExpression AS 10 + 10`  
  
 `MEMBER MEASURES.NumericExpressionBasedOnMeasure AS [Measures].[Internet Sales Amount] + 10`  
  
 `MEMBER MEASURES.StringValue AS "10"`  
  
 `MEMBER MEASURES.ConcatenatedString AS "10" + "10"`  
  
 `MEMBER MEASURES.StringFunction AS MEASURES.CURRENTMEMBER.NAME`  
  
 `MEMBER MEASURES.TodaysDate AS NOW()`  
  
 `SELECT`  
  
 `{MEASURES.NumericValue,MEASURES.NumericExpression,MEASURES.NumericExpressionBasedOnMeasure,`  
  
 `MEASURES.StringValue, MEASURES.ConcatenatedString, MEASURES.StringFunction, MEASURES.TodaysDate}`  
  
 `ON COLUMNS`  
  
 `FROM [Adventure Works]`  
  
 計算されるメジャーかどうかを問わず、メジャーで返すことのできるデータ型は OLE Variant 型だけです。 したがって、場合によっては、メジャー値を特定の型にキャストして、予測される動作を受け入れることも必要になります。 次のクエリでは、この例を示します。  
  
```  
WITH  
//Two calculated measures that return strings  
MEMBER MEASURES.NumericString1 AS "10"  
MEMBER MEASURES.NumericString2 AS "10"  
//In this case, the + operator acts to concatenate the strings  
MEMBER MEASURES.Concatenation AS MEASURES.NumericString1 + MEASURES.NumericString2  
//Casting one value to an integer with the CINT function causes the second measure  
//to be treated as an integer too, so that the + operator now acts to add the values  
MEMBER MEASURES.Addition AS CINT(MEASURES.NumericString1) + MEASURES.NumericString2  
SELECT  
{MEASURES.NumericString1,MEASURES.NumericString2,MEASURES.Concatenation,MEASURES.Addition }  
ON COLUMNS  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [式&#40;MDX&#41;](../mdx/expressions-mdx.md)  
  
  
