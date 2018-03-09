---
title: "SetToArray (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: SETTOARRAY
dev_langs: kbMDX
helpviewer_keywords: SetToArray function
ms.assetid: e408c626-3a2a-4ce9-aeb4-247301334893
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 7cf8bdfdb22175a59207f14792abcf7f27aede0a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="settoarray-mdx"></a>SetToArray (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  ユーザー定義関数で使用するために、1 つ以上のセットを配列に変換します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SetToArray(Set_Expression1 [ ,Set_Expression2,...n ][ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression1*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Set_Expression2*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **SetToArray**関数が 1 つまたは複数のセットをユーザー定義関数で使用する配列に変換します。 結果の配列内のディメンションの数は、指定されたセットの数と同一になります。  
  
 オプションの数値式で、配列のセルに値を指定することもできます。 数値式を指定しなかった場合は、現在のコンテキストでセットのクロス結合が評価されます。  
  
 この結果作成される配列では、セルの座標がセットの並び順に対応します。 たとえば、`SA`、`SB`、`SC` という 3 つのセットがあるとします。 それぞれのセットには 2 つの要素があります。 MDX ステートメント`SetToArray(SA, SB, SC)`、次の 3 次元の配列を作成します。  
  
```  
(SA1, SB1, SC1) (SA2, SB1, SC1) (SA1, SB2, SC1) (SA2, SB2, SC1)   
(SA1, SB1, SC2) (SA2, SB1, SC2) (SA1, SB2, SC2) (SA2, SB2, SC2)   
```  
  
> [!NOTE]  
>  戻り値の型、 **SetToArray**関数は、バリアント型の VT_ARRAY です。 したがって、出力の**SetToArray**関数は、ユーザー定義関数への入力としてのみ使用する必要があります。  
  
## <a name="example"></a>例  
 次の例では、配列が 1 つ返されます。  
  
```  
SetToArray([Geography].[Geography].Members, [Measures].[Internet Sales Amount])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
