---
title: "BottomPercent (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 416c5c68b30b72352ffc95658d0f34cc77f8e9af
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="bottompercent-mdx"></a>BottomPercent (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
  

