---
title: Members (String) (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 05df2d0a846af30d46e702c1d5489945d57c9115
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68001491"
---
# <a name="members-string-mdx"></a>Members (String) (MDX)


  文字列式で指定されたメンバーを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Members(Member_Name)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Name*  
 メンバー名を指定する有効な文字列式です。  
  
## <a name="remarks"></a>Remarks  
 **Members (String)** 関数は、名前が指定された1つのメンバーを返します。 通常、members **(** string) 関数を外部関数と共に使用し、 **members (string)** 関数にメンバーを識別する文字列を指定します。また、 **members (string)** 関数は、この指定されたメンバーの値を返します。  
  
## <a name="example"></a>例  
 次の例では、 **Members (string)** 関数を使用して、指定した文字列を有効なメンバーに変換し、文字列で指定されたメンバーの既定のメジャーを返します。 指定された文字列は単一引用符で囲まれています。 既定のメジャーは、再販業者の Sales Amount メジャーです。  
  
```  
SELECT Members ('[Geography].[Geography].[Country].&[United States] ') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
