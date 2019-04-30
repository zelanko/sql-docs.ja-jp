---
title: Members (セット) (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3bd4fe92c064f4665a4b397e47a45ae5bde50f39
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63048451"
---
# <a name="members-set-mdx"></a>Members (セット) (MDX)


  ディメンション、レベル、または階層でメンバーのセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Hierarchy expression syntax  
Hierarchy_Expression.Members  
  
Level expression Syntax  
Level_Expression.Members  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式。  
  
## <a name="remarks"></a>コメント  
 階層式が指定されている場合、 **Members (セット)** 関数は、計算されるメンバーを含まない、指定された階層内のすべてのメンバーのセットを返します。 すべてのメンバー、計算のセットを取得またはそれ以外の場合、階層を使用して、 [AllMembers &#40;MDX&#41; ](../mdx/allmembers-mdx.md)関数  
  
 レベル式が指定されている場合、 **Members (セット)** 関数は、指定されたレベル内のすべてのメンバーのセットを返します。  
  
> [!IMPORTANT]  
>  ディメンションに表示されている 1 つの階層のみが含まれている場合、階層を構成できますディメンション名または階層の名前をこのシナリオでは、ディメンション名はそののみ表示される階層に解決されるためです。 たとえば、Measures.Members は、Measures ディメンション内の唯一の階層に解決されるため、有効な MDX 式です。  
  
## <a name="examples"></a>使用例  
 次の例では、Adventure Works キューブの Calendar Year 階層のすべてのメンバーのセットを返しています。  
  
```  
SELECT   
   [Date].[Calendar].[Calendar Year].Members ON 0  
FROM  
   [Adventure Works]  
  
```  
  
 次の例では、`[Product].[Products].[Product Line]` レベルの各メンバーについて 2003 年の注文数量を返します。 **メンバー**関数を表すすべてのレベルにメンバー セットを返します。  
  
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
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
