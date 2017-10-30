---
title: "MemberToStr (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 562f44cac767b5d2d57d6829ef7b6a76c4484c87
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="membertostr-mdx"></a>MemberToStr (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
  
  

