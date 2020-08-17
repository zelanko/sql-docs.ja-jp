---
description: Members (Set) (MDX)
title: Members (Set) (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0358f20d0aeba0e4d455fabadb6dc1e4361081e5
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341398"
---
# <a name="members-set-mdx"></a>Members (Set) (MDX)


  ディメンション、レベル、または階層内のメンバーのセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Hierarchy expression syntax  
Hierarchy_Expression.Members  
  
Level expression Syntax  
Level_Expression.Members  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 階層式が指定されている場合、 **members (セット)** 関数は、計算されるメンバーを含まない、指定された階層内のすべてのメンバーのセットを返します。 すべてのメンバーのセットを取得するには、階層で、all メンバー [&#40;MDX&#41;](../mdx/allmembers-mdx.md) 関数を使用します。  
  
 レベル式が指定されている場合、 **members (セット)** 関数は、指定されたレベル内のすべてのメンバーのセットを返します。  
  
> [!IMPORTANT]  
>  ディメンションに表示される階層が1つだけの場合、このシナリオのディメンション名は、表示されている唯一の階層に解決されるので、階層はディメンション名または階層名で参照できます。 たとえば、Measures。 Members は、Measures ディメンション内の唯一の階層に解決されるため、有効な MDX 式です。  
  
## <a name="examples"></a>例  
 次の例では、Adventure Works キューブの Calendar Year 階層のすべてのメンバーのセットを返しています。  
  
```  
SELECT   
   [Date].[Calendar].[Calendar Year].Members ON 0  
FROM  
   [Adventure Works]  
  
```  
  
 次の例では、`[Product].[Products].[Product Line]` レベルの各メンバーについて 2003 年の注文数量を返します。 **Members**関数は、レベル内のすべてのメンバーを表すセットを返します。  
  
```  
SELECT   
   {Measures.[Order Quantity]} ON COLUMNS,  
   [Product].[Product Line].[Product Line].Members ON ROWS  
FROM  
   [Adventure Works]  
WHERE  
   {[Date].[Calendar Year].[Calendar Year].&[2003]}  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
