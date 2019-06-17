---
title: -(コメント) (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dc8bf49f6d25c4e00c2d5693ff6a9cf48d5450ee
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208753"
---
# <a name="comment---mdx-operator-reference"></a>コメントの MDX 演算子リファレンス


  コメントのテキストは、ユーザーによって提供されることを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>コメント  
 コメントは、個別の行に挿入された、多次元式 (MDX) スクリプトの行の末尾で入れ子にまたは MDX ステートメント内で入れ子になったことができます。 サーバーはコメントを評価しません。  
  
 1 行のコメントまたは入れ子にしたコメントには、この演算子を使用します。 -- によって挿入するコメントは、改行文字で区切ります。  
  
 コメントの長さには制限がありません。  
  
## <a name="examples"></a>使用例  
 次の例では、この演算子の使用を示します。  
  
```  
-- This member returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM -- Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>参照  
 [コメント &#40;MDX&#41;](../mdx/comment-mdx.md)   
 [&#40;コメント&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md)   
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
