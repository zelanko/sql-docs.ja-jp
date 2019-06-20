---
title: DefaultMember (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3a0c11acadcbdcadfd9398baff09db9292c87eb2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248127"
---
# <a name="defaultmember-mdx"></a>DefaultMember (MDX)


  階層の既定のメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Hierarchy_Expression.DefaultMember  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式。  
  
## <a name="remarks"></a>コメント  
 属性がクエリに含まれていない場合は、属性上の既定のメンバーが式の評価に使用されます。  
  
## <a name="example"></a>例  
 次の例では、 **DefaultMember**と組み合わせて、関数、**名前**を Adventure Works キューブ内の Destination Currency ディメンションの既定のメンバーを返す関数。 例では、返す**米ドル**します。 **名前**関数を使用して、これは、メジャーの既定のプロパティではなく、メジャーの名前を返す**値**します。  
  
```  
WITH MEMBER Measures.x AS   
   [Destination Currency].[Destination Currency].DefaultMember.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [既定のメンバーの定義](../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
