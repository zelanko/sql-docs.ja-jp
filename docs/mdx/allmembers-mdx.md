---
title: AllMembers (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a5720c3e82fdb341635c23d13a9c6bf4346a1cc0
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34577174"
---
# <a name="allmembers-mdx"></a>AllMembers (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  階層式またはレベル式を評価し、指定された階層またはレベルのすべてのメンバー (計算されるメンバーも含む) を格納したセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Hierarchy syntax  
Hierarchy_Expression.AllMembers  
  
Level syntax  
Level_Expression.AllMembers  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **AllMembers**関数を指定された階層またはレベルで、計算されるメンバーを含むすべてのメンバーを含むセットを返します。 **AllMembers**関数が、指定された階層またはレベルが表示できるメンバーに含まれない場合でも、計算されるメンバーを返します。  
  
> [!IMPORTANT]  
>  ディメンションに表示されている 1 つの階層のみが含まれている場合、階層を構成できますディメンション名、または階層名を参照ディメンションの名前がここでは、表示のみの階層に解決されるためです。 たとえば、`Measures.AllMembers`有効な MDX 式は、Measures ディメンション内の唯一の階層に解決されるためです。  
  
> [!NOTE]  
>  **AllMembers**関数に意味が似て、 [AddCalculatedMembers (MDX)](../mdx/addcalculatedmembers-mdx.md)関数。  
  
## <a name="examples"></a>使用例  
 次の例は、すべてのメンバーを返します、[`Date].[Calendar Year]`列軸で属性階層、これが含まれています計算されるメンバー、およびすべての子のセット、`[Product].[Model Name]`属性階層からの行軸、 **Adventure Works**キューブ。  
  
```  
SELECT  
   [Date].[Calendar Year].AllMembers ON COLUMNS,  
   [Product].[Model Name].Children ON ROWS  
FROM  
   [Adventure Works]  
```  
  
 次の例は、すべてのメンバーを返します、**メジャー**ディメンションで列の軸が含まれますすべての計算されるメンバー、およびすべての子のセット、`[Product].[Model Name]`属性階層からの行軸、 **Adventure Works**キューブ。  
  
```  
SELECT  
    Measures.AllMembers ON COLUMNS,  
    [Product].[Model Name].Children ON ROWS  
FROM  
    [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [AddCalculatedMembers &#40;MDX&#41;](../mdx/addcalculatedmembers-mdx.md)   
 [子&#40;MDX&#41;](../mdx/children-mdx.md)   
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
