---
title: 階層 (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Hierarchy
dev_langs:
- kbMDX
helpviewer_keywords:
- Hierarchy function
ms.assetid: 5ddf354f-8cae-4e3a-8803-0055fa86bad1
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 19ee9504682303372450100e2e5ab78abc271bbf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="hierarchy-mdx"></a>Hierarchy (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指定されたメンバーまたはレベルを含む階層を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member expression syntax  
Member_Expression.Hierarchy  
  
Level expression syntax  
Level_Expression.Hierarchy  
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
### <a name="examples"></a>使用例  
 次の例では、AdventureWorks キューブで Date ディメンションの Calendar 階層の名前を返します。  
  
 `WITH`  
  
 `MEMBER Measures.HierarchyName as`  
  
 `[Date].[Calendar].Currentmember.Hierarchy.Name`  
  
 `SELECT {Measures.HierarchyName}  ON 0,`  
  
 `{[Date].[Calendar].[All Periods]} ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
