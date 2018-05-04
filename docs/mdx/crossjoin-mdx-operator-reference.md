---
title: '* (クロス積)(MDX) |Microsoft ドキュメント'
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
- '*'
dev_langs:
- kbMDX
helpviewer_keywords:
- '* (crossjoin operator)'
- crossjoin operator (*)
ms.assetid: e00cb260-0189-4c4e-b3d2-088f4421337b
caps.latest.revision: 41
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: a510ca656d7a17bc80878c49bab20fb3254c81e0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="crossjoin----mdx-operator-reference"></a>クロス結合の MDX 演算子リファレンス
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  2 つのセットのクロス積を返すセット演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set_Expression * Set_Expression  
```  
  
## <a name="parameter"></a>パラメーター  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="return-value"></a>戻り値  
 指定されている両方のパラメーターのクロス積を含むセットです。  
  
## <a name="remarks"></a>解説  
 **\* (クロス積)** 演算子は機能的に等価、 [Crossjoin](../mdx/crossjoin-mdx.md)関数。  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を以下に示します。  
  
```  
-- This query returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
    [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
