---
title: コメント (MDX) |Microsoft ドキュメント
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
- '*/'
- /*
dev_langs:
- kbMDX
helpviewer_keywords:
- commenting characters
- /*...*/ (comment)
ms.assetid: 64434ae4-80ce-4634-86b8-4125dfaa7f61
caps.latest.revision: 40
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 4a4c9aa5bfbb27fd208b6f418e18b1c224451f27
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="comment-mdx"></a>コメント (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  ユーザーが指定したコメントのテキストを示します。  
  
## <a name="syntax"></a>構文  
  
```  
  
/* Comment_Text */      
```  
  
#### <a name="parameters"></a>パラメーター  
 *Comment_Text*  
 コメントのテキストを含む文字列です。  
  
## <a name="remarks"></a>解説  
 サーバーが、コメント文字の間のテキストを評価できません/* と\*/です。 コメントは、別個の行に挿入することも、多次元式 (MDX) ステートメントの中に指定することも可能です。 によって複数行のコメントを示す必要があります/\*と\*/です。  
  
 コメントの長さには制限がありません。 `/* Test /*Comment*/ Text*/` のようにコメントを入れ子にすることもできます。  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を以下に示します。  
  
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
 [--& #40 です。コメント & #41;& #40 です。MDX と #41 です。](../mdx/comment-mdx-operator-reference.md)   
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
