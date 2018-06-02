---
title: DefaultMember (MDX) |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 04c99c0882bd71d1ad56c8d4f42bf3744756c81b
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34580244"
---
# <a name="defaultmember-mdx"></a>DefaultMember (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  階層の既定のメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Hierarchy_Expression.DefaultMember  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 属性がクエリに含まれていない場合は、属性上の既定のメンバーが式の評価に使用されます。  
  
## <a name="example"></a>例  
 次の例では、 **DefaultMember**と組み合わせて、関数、**名前**を Adventure Works キューブ内の Destination Currency ディメンションの既定のメンバーを返す関数。 この例を返します**米国ドル**です。 **名前**関数を使用して、これは、メジャーの既定のプロパティではなく、メジャーの名前を返す**値**です。  
  
```  
WITH MEMBER Measures.x AS   
   [Destination Currency].[Destination Currency].DefaultMember.Name  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス&#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)   
 [既定のメンバーを定義します。](../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
