---
description: 論理関数の使用
title: 論理関数の使用 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2a13f9fa95878277b164b37bb71e3d9af646d89f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340998"
---
# <a name="using-logical-functions"></a>論理関数の使用


  論理関数は、オブジェクトおよび式に対して論理演算または比較を実行し、ブール値を返します。 論理関数は、メンバーの位置を決定するために、多次元式 (MDX) において不可欠です。  
  
 最もよく使用される論理関数は、 **IsEmpty** 関数です。 **IsEmpty**関数の使用方法の詳細については、「[空の値の操作](../mdx/working-with-empty-values.md)」を参照してください。  
  
 次のクエリは、 **Isleaf** 関数と **isleaf** 関数の使用方法を示しています。  
  
 `WITH`  
  
 `//Returns true if the CurrentMember on Calendar is a leaf member, ie it has no children`  
  
 `MEMBER MEASURES.[IsLeafDemo] AS IsLeaf([Date].[Calendar].CurrentMember)`  
  
 `//Returns true if the CurrentMember on Calendar is an Ancestor of July 1st 2001`  
  
 `MEMBER MEASURES.[IsAncestorDemo] AS IsAncestor([Date].[Calendar].CurrentMember, [Date].[Calendar].[Date].&[1])`  
  
 `SELECT{MEASURES.[IsLeafDemo],MEASURES.[IsAncestorDemo] } ON 0,`  
  
 `[Date].[Calendar].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [関数 &#40;MDX 構文&#41;](../mdx/functions-mdx-syntax.md)  
  
  
