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
ms.openlocfilehash: 3965c3cc8ea2a2f2de292ca0c75e49c957e04f02
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68036971"
---
# <a name="settostr-mdx"></a>SetToStr (MDX)


  指定されたセットに対応する多次元式 (MDX) 形式の文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SetToStr(Set_Expression)  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>Remarks  
 この関数は、解析用にセットの文字列表記を外部関数に転送する場合に使用します。 返される文字列は中かっこ{}で囲まれ、セット内の各項目はコンマで区切られます。  
  
## <a name="example"></a>例  
 次の例では、Geography 属性階層のすべてのメンバーを含む文字列を返します。  
  
```  
WITH MEMBER Measures.x AS SetToStr (Geography.Geography.Children)  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
