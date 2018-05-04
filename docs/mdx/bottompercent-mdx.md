---
title: BottomPercent (MDX) |Microsoft ドキュメント
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
- BOTTOMPERCENT
dev_langs:
- kbMDX
helpviewer_keywords:
- BottomPercent function
ms.assetid: c04866e6-e6dd-4ed1-ae79-c718c194930c
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: b309a60979d0f43605a4499803d61a8b76dd5d40
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="bottompercent-mdx"></a>BottomPercent (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットを昇順で並べ替え、累積合計が指定された割合以上になるように、値の小さい方から組のセットを作成して返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
BottomPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *[パーセント]*  
 返す組の割合を指定する有効な数値式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **BottomPercent**関数セットを昇順で並べ替え、指定されたセットに対して評価される指定数値式の合計を計算します。 次に、その合計値の累積割合が指定されている割合以上になるように、最も値の小さい方から要素を返します。 この関数は、累積合計が指定された割合以上になるセットの最小サブセットを返します。 要素は大きい方から順に返されます。  
  
> [!IMPORTANT]  
>  **BottomPercent**関数は、like、 [TopPercent](../mdx/toppercent-mdx.md)関数を常に階層を解除します。 詳細については、Order 関数に関するトピックを参照してください。  
  
## <a name="example"></a>例  
 次の例では、Bike カテゴリについて、Reseller Sales Amount メジャーを使用した累積合計が全体の 15% 以上になるような、2003 会計年度の Geography ディメンションの Geography 階層にある City レベルの最小のメンバーのセットを返します (最も売り上げが少ないメンバーを 1 番目に返します)。  
  
```  
SELECT  
[Product].[Product Categories].Bikes ON 0,  
BottomPercent  
   ({[Geography].[Geography].[City].Members}  
   , 15  
   , ([Measures].[Reseller Sales Amount],[Product].[Product Categories].Bikes)  
   ) ON 1  
FROM [Adventure Works]  
WHERE ([Measures].[Reseller Sales Amount],[Date].[Fiscal].[Fiscal Year].[FY 2003])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
