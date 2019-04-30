---
title: SetToStr (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 57e74eb1c7db4aebdd01fde8fc48a425d7affa55
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149283"
---
# <a name="settostr-mdx"></a>SetToStr (MDX)


  指定されたセットに対応する MDX 形式の文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SetToStr(Set_Expression)  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="remarks"></a>コメント  
 この関数は、解析用にセットの文字列表記を外部関数に転送する場合に使用します。 返される文字列は中かっこで囲まれた{}コンマで区切られたセット内の各項目にします。  
  
## <a name="example"></a>例  
 次の例では、Geography.Country 属性階層のメンバーのすべてを含む文字列を返します。  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
