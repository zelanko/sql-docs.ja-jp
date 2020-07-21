---
title: ドリルダウンレベル (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: ef2f94eb843b3ffbfbb67eb6ca01f2114522e024
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68049221"
---
# <a name="drilluplevel-mdx"></a>ドリルダウンレベル (MDX)


  セットのメンバーのうち、指定されたレベルの下位に属するメンバーをドリル アップします。  
  
## <a name="syntax"></a>構文  
  
```  
  
DrillupLevel(Set_Expression [ , Level_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>Remarks  
 **ドリルダウンレベル**関数は、指定されたセットに含まれるメンバーに基づいて階層的に編成されたメンバーのセットを返します。 指定されたセット内のメンバーの間に順序が保持されます。  
  
 レベル式が指定されている場合、**ドリル**ダウンレベル関数は、指定されたレベルを超えるメンバーだけを取得してセットを構築します。 レベル式が指定されていて、指定されたレベルのメンバーが指定されたセットで表されていない場合、指定されたセットが返されます。  
  
 レベル式が指定されていない場合、指定されたセット内で参照されている最初のディメンションの最下位レベルより 1 つ上のレベルにあるメンバーだけを取得してセットを構築します。  
  
## <a name="example"></a>例  
 次の例は、最初のセットから Subcategory レベルより上位にあるメンバーのセットを返します。  
  
```  
SELECT DrillUpLevel   
  ({[Product].[Product Categories].[All Products]  
    ,[Product].[Product Categories].[Subcategory].&[32],  
    [Product].[Product Categories].[Product].&[215]},  
  [Product].[Product Categories].[Subcategory]  
    )  
  ON 0  
  FROM [Adventure Works]  
  WHERE [Measures].[Internet Order Quantity]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
