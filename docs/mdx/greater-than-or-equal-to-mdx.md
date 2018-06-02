---
title: '&gt;= (より大きいか等しい) (MDX) |Microsoft ドキュメント'
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: db81285593b04a2b82c5eed87c3747a1f9450e42
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34579124"
---
# <a name="gt-greater-than-or-equal-to-mdx"></a>&gt;= (より大きいか等しい) (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  1 つの多次元式 (MDX) 式の値が、別の MDX 式の値以上であるかどうかを判別する比較演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
MDX_Expression >= MDX_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *MDX_Expression*  
 有効な MDX 式です。  
  
## <a name="return-value"></a>戻り値  
 以下の条件に基づくブール値です。  
  
-   **true**かどうか、最初のパラメーターに、2 番目のパラメーターの値以上である値。  
  
-   **false**最初のパラメーター値が 2 番目のパラメーターの値よりも小さい値です。  
  
-   **true**両方のパラメーターが null の場合、または 1 つのパラメーターが null と、その他のパラメーターが 0 です。  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を以下に示します。  
  
```  
-- This query returns the gross profit margin (GPM)  
-- for Australia where the GPM is greater than or equal to 50%.  
With Member [Measures].[HighGPM] as  
  IIF(  
      [Measures].[Gross Profit Margin] >= .5,  
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
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
