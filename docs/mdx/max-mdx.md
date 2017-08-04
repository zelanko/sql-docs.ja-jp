---
title: "Max (MDX) |Microsoft ドキュメント"
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
- MAX
dev_langs:
- kbMDX
helpviewer_keywords:
- Max function [MDX]
ms.assetid: 745c2b3e-022b-471a-ac16-e39ecb3297ea
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dd3151c2fec5a7fecee1a3ff0b1c2b988f9e08bc
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="max-mdx"></a>Max (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セットに対して評価される数値式の最大値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Max( Set_Expression [ , Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 数値式を指定した場合、この数値式がセットに対して評価されてから、その評価で得られる最大値が返されます。 数値式を指定しなかった場合、指定したセットがそのセットのメンバーの現在のコンテキストで評価されてから、その評価で得られる最大値が返されます。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] では、数値セットの最大値が計算される際、NULL 値は無視されます。  
  
## <a name="example"></a>例  
 次の例では、Adventure Works キューブ内の四半期、サブカテゴリ、および国ごとに毎月の売上高の最大値を返します。  
  
```  
WITH MEMBER Measures.x AS Max   
   ([Date].[Calendar].CurrentMember.Children  
      , [Measures].[Reseller Order Quantity]  
   )  
SELECT Measures.x ON 0  
,NON EMPTY [Date].[Calendar].[Calendar Quarter]*   
   [Product].[Product Categories].[Subcategory].members *  
   [Geography].[Geography].[Country].Members  
ON 1  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

