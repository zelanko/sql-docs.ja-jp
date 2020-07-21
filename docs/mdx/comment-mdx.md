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
ms.openlocfilehash: f0aa1455ffd9f52fd917f68d2bb0bb80e3f25a94
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68006276"
---
# <a name="comment-mdx"></a>コメント (MDX)


  ユーザーによって指定されたコメントテキストを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
/* Comment_Text */      
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>Remarks  
 サーバーでは、コメント文字 (/* と\*/) の間のテキストは評価されません。 コメントは、別の行に挿入することも、多次元式 (MDX) ステートメント内に挿入することもできます。 複数行のコメントは、/\*および\*/で示す必要があります。  
  
 コメントの長さには制限がありません。 `/* Test /*Comment*/ Text*/` のようにコメントを入れ子にすることもできます。  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を次に示します。  
  
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
  
## <a name="see-also"></a>参照  
 [&#40;コメント&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md)   
 [--&#40;コメント&#41; &#40;MDX&#41;](../mdx/comment-mdx-operator-reference.md)   
 [Mdx 演算子リファレンス &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
