---
title: 論理関数の使用 |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6bd427ebfca1fbf2f546603853b2352d6dcf4c90
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34582464"
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
 [関数&#40;MDX 構文&#41;](../mdx/functions-mdx-syntax.md)  
  
  
