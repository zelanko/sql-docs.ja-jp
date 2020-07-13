---
title: NameToSet (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 77731495eb058da05f6c61be391591a40725e579
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68088395"
---
# <a name="nametoset-mdx"></a>NameToSet (MDX)


  多次元式 (MDX) 形式の文字列によって指定されたメンバーを含むセットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
NameToSet(Member_Name)   
```  
  
## <a name="arguments"></a>引数  
 *Member_Name*  
 メンバーの名前を表す有効な文字列式です。  
  
## <a name="remarks"></a>Remarks  
 指定されたメンバー名が存在する場合、 **NameToSet**関数はそのメンバーを含むセットを返します。 それ以外の場合、関数は空のセットを返します。  
  
> [!NOTE]  
>  メンバーの名前には、メンバー名のみを指定する必要があります。メンバー式を指定することはできません。 メンバー式を使用するには、「 [StrToSet &#40;MDX&#41;](../mdx/strtoset-mdx.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、指定されたメンバー名の既定のメジャー値を返します。  
  
```  
SELECT NameToSet('[Date].[Calendar].[July 2001]') ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
