---
title: コメント (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6469921572b8a1809e228fff0d25061475399ae7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181571"
---
# <a name="comment-mdx"></a>コメント (MDX)


  コメントのテキストは、ユーザーによって提供されることを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
/* Comment_Text */      
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>コメント  
 コメント文字の間のテキストを評価しませんサーバー/* と\*/。 または、多次元式 (MDX) ステートメント内で別々 の行にコメントを挿入できます。 によって複数行のコメントを示す必要があります/\*と\*/。  
  
 コメントの長さには制限がありません。 `/* Test /*Comment*/ Text*/` のようにコメントを入れ子にすることもできます。  
  
## <a name="examples"></a>使用例  
 次の例では、この演算子の使用を示します。  
  
```  
/* This member returns the gross profit margin for product types  
  and reseller types crossjoined by year. */  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM /* Select from the Adventure Works cube. */  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>関連項目  
 [&#40;コメント&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md)   
 [-- &#40;コメント&#41; &#40;MDX&#41;](../mdx/comment-mdx-operator-reference.md)   
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
