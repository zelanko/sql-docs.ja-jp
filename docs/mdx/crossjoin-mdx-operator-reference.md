---
title: '* (クロス積)(MDX) |Microsoft Docs'
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
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63249621"
---
# <a name="crossjoin----mdx-operator-reference"></a>Crossjoin - MDX 演算子リファレンス


  2 つのセットのクロス積を返すセット演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set_Expression * Set_Expression  
```  
  
## <a name="parameter"></a>パラメーター  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
## <a name="return-value"></a>戻り値  
 指定したパラメーターを両方のクロス積を含むセット。  
  
## <a name="remarks"></a>コメント  
  **\* (クロス積)** 演算子は機能的に等価、 [Crossjoin](../mdx/crossjoin-mdx.md)関数。  
  
## <a name="examples"></a>使用例  
 次の例では、この演算子の使用を示します。  
  
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
  
  
