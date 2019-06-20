---
title: AllMembers (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 92cde0acf07f62d0678da6dd96efa707dedc1a1f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63066250"
---
# <a name="allmembers-mdx"></a>AllMembers (MDX)


  階層またはレベル式のいずれかを評価し、指定された階層またはレベル、階層またはレベルのすべての計算されるメンバーを含むのすべてのメンバーを含むセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.AllMembers  
  
Level syntax  
Level_Expression.AllMembers  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式。  
  
## <a name="remarks"></a>コメント  
 **AllMembers**関数を指定された階層またはレベルで、計算されるメンバーを含むすべてのメンバーを含むセットを返します。 **AllMembers**場合でも、指定された階層またはレベルが含まれていない表示可能なメンバーには関数は計算されるメンバーを返します。  
  
> [!IMPORTANT]  
>  ディメンションに表示されている 1 つの階層のみが含まれている場合、階層を構成できますディメンション名または階層の名前で参照するか、ディメンション名がここではそののみ表示される階層に解決されるためです。 たとえば、`Measures.AllMembers`有効な MDX 式は、Measures ディメンション内の唯一の階層に解決されるためです。  
  
> [!NOTE]  
>  **AllMembers**関数に意味が似て、 [AddCalculatedMembers (MDX)](../mdx/addcalculatedmembers-mdx.md)関数。  
  
## <a name="examples"></a>使用例  
 次の例は、すべてのメンバーを返します、[`Date].[Calendar Year]` 、列軸上の属性階層、これが含まれています計算されるメンバー、およびすべての子のセット、`[Product].[Model Name]`属性階層からの行軸、 **AdventureWorks**キューブ。  
  
```  
SELECT  
   [Date].[Calendar Year].AllMembers ON COLUMNS,  
   [Product].[Model Name].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
 次の例は、すべてのメンバーを返します、**メジャー**ディメンション列軸で、すべての計算されるメンバーとのすべての子のセットを含みます、`[Product].[Model Name]`行軸上の階層の属性、を**Adventure Works**キューブ。  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [AddCalculatedMembers &#40;MDX&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [Children &#40;MDX&#41;](../mdx/children-mdx.md)   
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
