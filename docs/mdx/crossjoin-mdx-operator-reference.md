---
title: '* (クロス積)(MDX) |Microsoft ドキュメント'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 132b237fd8baa9c50dc254b02d90ed95d7159a0c
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34740601"
---
# <a name="crossjoin----mdx-operator-reference"></a>クロス結合の MDX 演算子リファレンス


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
  
## <a name="remarks"></a>コメント  
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
  
  
