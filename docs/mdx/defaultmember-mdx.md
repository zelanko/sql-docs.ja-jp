---
title: DefaultMember (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- DefaultMember
dev_langs:
- kbMDX
helpviewer_keywords:
- DefaultMember function
ms.assetid: c1b53b3a-6e73-4c41-a4fe-9f5c96da5463
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 09fa9c7b92fcb6839efc2870b4dad5d6c4a39fa7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
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
  
## <a name="remarks"></a>解説  
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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)   
 [既定のメンバーを定義します。](../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
