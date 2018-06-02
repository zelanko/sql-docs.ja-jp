---
title: DrillupLevel (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 19d6443857d53d835db4c395ddd43dc4a305ad8c
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579454"
---
# <a name="drilluplevel-mdx"></a>DrillupLevel (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  セットのメンバーのうち、指定されたレベルの下位に属するメンバーをドリル アップします。  
  
## <a name="syntax"></a>構文  
  
```  
  
DrillupLevel(Set_Expression [ , Level_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **DrillupLevel**指定したセットに含まれるメンバーに基づいて階層的に編成されたメンバーのセット関数を返します。 指定されたセット内のメンバーの順序は保持されます。  
  
 レベル式が指定されている場合、 **DrillupLevel**関数は、指定されたレベルより上位にあるメンバーのみを取得してセットを構築します。 レベル式が指定された、指定されたセット内の指定されたレベルのメンバーが存在しない場合は、指定したセットが返されます。  
  
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
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
