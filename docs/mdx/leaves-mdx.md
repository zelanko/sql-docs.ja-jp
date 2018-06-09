---
title: リーフ (MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b18f283dce1ed5d0d3099dbdc26e27e8aff39ffc
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34741251"
---
# <a name="leaves-mdx"></a>Leaves (MDX)


  すべての属性から構成されるセットを返します。必要に応じて特定のディメンションに属している属性のみを返すこともできます。 返すセット内の各属性 x について、x が粒度属性であるか、直接または間接的に粒度属性に関連付けられている属性である場合、粒度はスライスに影響することなく属性 x に対して設定されます。 **まま**関数が SCOPE ステートメント内または代入の左辺で使用するために設計されています。  
  
## <a name="syntax"></a>構文  
  
```  
  
Leaves( [ Dimension_expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Dimension_Expression*  
 ディメンションを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 リーフ メンバーとは、すべての属性階層の最下位レベルのクロス結合によって形成される組です。 計算されるメンバーは除外されます。  
  
-   ディメンション名が指定されている場合、**まま**関数を指定されたディメンションのキー属性のリーフ メンバーを含むセットを返します。  
  
-   ディメンションが複数のメジャー グループに関連付けられている場合、現在のスコープにあるメジャーのディメンションが使用されます。  
  
-   ディメンション名が指定されていない場合は、キューブ全体のリーフ メンバーで構成されるセットを返します。  
  
    > [!NOTE]  
    >  ディメンション式が階層に解決され、その階層の一意名がディメンションの一意名と同じになる場合 (キューブ ディメンション プロパティ HierarchyUniqueNameStyle = ExcludeDimensionName であり、階層名 = ディメンション名の場合) は、ディメンションが使用されます。  
  
    > [!IMPORTANT]  
    >  現在のスコープのメジャー グループに対する粒度が異なる属性が 1 つでもあると、エラーが生成されます。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
