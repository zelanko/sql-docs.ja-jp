---
title: "NonEmptyCrossjoin (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: NONEMPTYCROSSJOIN
dev_langs: kbMDX
helpviewer_keywords: NonEmptyCrossjoin function
ms.assetid: 3dc9522d-9126-4f7a-b587-216fa7a06c62
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: ffa983a749245022d0815906fe8e17850f9aabdf
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="nonemptycrossjoin-mdx"></a>NonEmptyCrossjoin (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  1 つ以上のセットのクロス積を含むセットを返します。ただし、空の組と、ファクト テーブル データに関連付けられていない組は含まれません。  
  
## <a name="syntax"></a>構文  
  
```  
  
NonEmptyCrossjoin(Set_Expression1 [ ,Set_Expression2,...] [,Count ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression1*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Set_Expression2*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *カウント*  
 返すセットの数を指定する有効な数値式です。  
  
## <a name="remarks"></a>解説  
 **NonEmptyCrossjoin**関数は、データを基になるファクト テーブルによって提供されることがなく、空の組または組を除外して、セットとして 2 つ以上のセットのクロス積を返します。 によって**NonEmptyCrossjoin**関数の動作、すべての計算メンバーは自動的に除外します。  
  
 場合*カウント*が指定されていない、クロス関数は、指定したすべてのセットを結合し、結果セットから空のメンバーを除外します。 セットの数を指定した場合は、指定した最初のセットを先頭として、指定数のセットがクロス結合されます。 **NonEmptyCrossjoin**関数は、後続の指定したセットに指定されているがされていないクロスのどのメンバーは、結果として得られるクロス結合されたセットに空でないと見なされますの決定に参加している残りのセットを使用します。 **NonEmptyCrossjoin**関数は、 **NON_EMPTY_BEHAVIOR**計算されるメジャーの設定。  
  
> [!IMPORTANT]  
>  この関数は旧バージョンとの互換性を維持するために用意されており、使用は推奨されていません。 代わりに、使用する必要があります、 [Exists (MDX)](../mdx/exists-mdx.md)メジャー グループ名の引数を持つ関数または[NonEmpty (MDX)](../mdx/nonempty-mdx.md)関数。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
