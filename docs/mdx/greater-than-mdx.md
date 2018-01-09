---
title: "&gt;(より大きい)(MDX) |Microsoft ドキュメント"
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
f1_keywords: '>'
dev_langs: kbMDX
helpviewer_keywords:
- greater than operator (>)
- '> (greater than operator)'
ms.assetid: 36ba6462-5517-43be-8e7d-a38b7343c5d3
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: f60f464114d9ff0c2bf51257d03ec9e0952a7a7f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="gt-greater-than-mdx"></a>&gt;(より大きい)(MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  1 つの多次元式 (MDX) 式の値が、別の MDX 式の値よりも大きいかどうかを判別する比較演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
MDX_Expression > MDX_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *MDX_Expression*  
 有効な MDX 式です。  
  
## <a name="return-value"></a>戻り値  
 以下の条件に基づくブール値です。  
  
-   **true**かどうかは、両方のパラメーターが null 以外の場合、および最初のパラメーターが 2 番目のパラメーターの値より大きい値が含まれています。  
  
-   **false**かどうかは、両方のパラメーターが null 以外の場合、および最初のパラメーターにはと等しいか、2 番目のパラメーターの値よりも小さい値が含まれています。  
  
-   いずれか一方または両方のパラメーターが NULL 値に評価される場合は、NULL です。  
  
## <a name="examples"></a>使用例  
 次のクエリでは、この演算子の使用例を示します。  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for Australia where the GPM is more than 50%.  
With Member [Measures].[HighGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] > .5,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT   
NON EMPTY [Sales Territory].[Sales Territory Country].[Australia] ON 0,  
    NON EMPTY [Product].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[HighGPM])  
  
```  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-operator-reference-mdx.md)  
  
  
