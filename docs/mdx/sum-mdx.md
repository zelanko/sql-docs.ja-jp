---
title: Sum (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SUM
dev_langs:
- kbMDX
helpviewer_keywords:
- Sum function [MDX]
ms.assetid: 6c3db1e3-2c02-49f2-a0bf-cab0fb78c622
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 4ca31da42f2a8b41ab4c4247ea0b6d33759b6e3d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sum-mdx"></a>Sum (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されているセットに対して評価された数値式の合計を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Sum( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 有効な多次元式 (MDX) セット式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 数値式を指定した場合、この数値式がセットに対して評価されてから、合計が算出されます。 数値式を指定しなかった場合、指定したセットがセットのメンバーの現在のコンテキストで評価されてから、合計が算出されます。 SUM 関数を数値式ではない式に適用した場合、結果は不確定になります。  
  
> [!NOTE]  
>  Analysis Services では、数値セットの合計が計算される際、NULL 値は無視されます。  
  
## <a name="examples"></a>使用例  
 次の例では、2001 年と 2002 年を対象として、Product.Category 属性階層のすべてのメンバーに対する Reseller Sales Amount の合計を返しています。  
  
```  
WITH MEMBER Measures.x AS SUM  
   ( { [Date].[Calendar Year].&[2001]  
         , [Date].[Calendar Year].&[2002] }  
      , [Measures].[Reseller Sales Amount]  
    )  
SELECT Measures.x ON 0  
,[Product].[Category].Members ON 1  
FROM [Adventure Works]  
```  
  
 次の例では、2002 年 7 月のインターネット販売にかかる運賃をその月の 20 日まで合計して返しています。  
  
```  
WITH MEMBER Measures.x AS SUM   
   (  
      MTD([Date].[Calendar].[Date].[July 20, 2002])  
     , [Measures].[Internet Freight Cost]  
     )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 次の例は、WITH MEMBER キーワードおよび**合計**Geography ディメンション内の Country 属性階層の Canada と United States メンバーに対する Reseller Sales Amount メジャーの合計を格納する、メジャー ディメンションの計算されるメンバーを定義する関数。  
  
```  
WITH MEMBER Measures.NorthAmerica AS SUM   
      (  
         {[Geography].[Country].&[Canada]  
            , [Geography].[Country].&[United States]}  
       ,[Measures].[Reseller Sales Amount]  
      )  
SELECT {[Measures].[NorthAmerica]} ON 0,  
[Product].[Category].members ON 1  
FROM [Adventure Works]  
```  
  
 多くの場合、**合計**関数を併用、 **CURRENTMEMBER**関数または関数と同様に**YTD**階層の currentmember に応じて異なるセットを返します。 たとえば、次のクエリは、年度の初めから ROWS 軸に表示されている日付までのすべての日付の Internet Sales Amount メジャーの合計を返します。  
  
 `WITH MEMBER MEASURES.YTDSUM AS`  
  
 `SUM(YTD(), [Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount], MEASURES.YTDSUM} ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
