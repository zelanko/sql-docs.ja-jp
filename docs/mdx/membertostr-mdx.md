---
title: MemberToStr (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- MEMBERTOSTR
dev_langs:
- kbMDX
helpviewer_keywords:
- MemberToStr function
ms.assetid: 2076b24a-603a-4d74-91bd-a3d347739bcd
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: fc72fc2373c763d64ed3b44b6b0264aaab0b4545
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="membertostr-mdx"></a>MemberToStr (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたメンバーに対応する多次元式 (MDX) 形式の文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
MemberToStr(Member_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 この関数は、メンバーの一意の名前を表す文字列を返します。 通常、メンバーの一意の名前を外部関数に渡すために使用されます。  
  
## <a name="example"></a>例  
 次の例は、文字列 [Geography].[Geography].[Country].&[United States] を返します。  
  
 `WITH MEMBER Measures.x AS MemberToStr`  
  
 `([Geography].[Geography].[Country].[United States])`  
  
 `SELECT Measures.x ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
