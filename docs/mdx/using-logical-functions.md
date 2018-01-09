---
title: "論理関数の使用 |Microsoft ドキュメント"
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
dev_langs: kbMDX
helpviewer_keywords: logical functions [MDX]
ms.assetid: 0cb34d53-9146-4924-9c9b-607afcb7a2be
caps.latest.revision: "25"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: 5ef44399a37c1b404e4ec9693baedb3a97d413f6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="using-logical-functions"></a>論理関数の使用
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  論理関数は、オブジェクトや式に対して論理操作または比較を実行し、ブール値を返します。 論理関数は、メンバーの位置を判別するために、多次元式 (MDX) において不可欠なものです。  
  
 最もよく使用される論理関数は、 **IsEmpty**関数。 使用する方法の詳細について、 **IsEmpty**関数を参照してください[空の値を操作](../mdx/working-with-empty-values.md)です。  
  
 次のクエリを使用する方法を示しています、 **IsLeaf**と**IsAncestor**関数。  
  
 `WITH`  
  
 `//Returns true if the CurrentMember on Calendar is a leaf member, ie it has no children`  
  
 `MEMBER MEASURES.[IsLeafDemo] AS IsLeaf([Date].[Calendar].CurrentMember)`  
  
 `//Returns true if the CurrentMember on Calendar is an Ancestor of July 1st 2001`  
  
 `MEMBER MEASURES.[IsAncestorDemo] AS IsAncestor([Date].[Calendar].CurrentMember, [Date].[Calendar].[Date].&[1])`  
  
 `SELECT{MEASURES.[IsLeafDemo],MEASURES.[IsAncestorDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [関数と #40 です。MDX 構文 &#41;](../mdx/functions-mdx-syntax.md)  
  
  
