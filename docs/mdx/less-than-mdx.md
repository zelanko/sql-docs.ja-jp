---
title: '&lt; (より小さい)(MDX) |Microsoft ドキュメント'
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: db93fdcba49829decaee14927cf84ec92bce5f80
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34578954"
---
# <a name="lt-less-than-mdx"></a>&lt; (より小さい)(MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  1 つの多次元式 (MDX) 式の値が、別の MDX 式の値よりも小さいかどうかを判別する比較演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
MDX_Expression < MDX_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *MDX_Expression*  
 有効な MDX 式です。  
  
## <a name="return-value"></a>戻り値  
 以下の条件に基づくブール値です。  
  
-   **true**かどうか両方のパラメーターが null 以外の場合と、最初のパラメーターには、2 番目のパラメーターの値よりも小さい値が含まれています。  
  
-   **false**かどうかは、両方のパラメーターが null 以外の場合、および最初のパラメーターにはと等しいか、2 番目のパラメーターの値より大きい値が含まれています。  
  
-   いずれか一方または両方のパラメーターが NULL 値に評価される場合は、NULL です。  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を以下に示します。  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for clothing sales where the GPM is less than 30%.  
With Member [Measures].[LowGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] < .3,  
      [Measures].[Gross Profit Margin],  
      null)  
SELECT NON EMPTY  
    [Sales Territory].[Sales Territory Country].Members ON 0,  
    [Product].[Category].[Clothing] ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[LowGPM])  
```  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
