---
description: Union-MDX 演算子リファレンス
title: + 組合(MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 84e6bc2b6b8460b90013ade5f0981af7f0ed8432
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88341191"
---
# <a name="union---mdx-operator-reference"></a>Union-MDX 演算子リファレンス


  重複するメンバーを削除して、2つのセットの和集合を返すセット演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set_Expression + Set_Expression      
```  
  
#### <a name="parameters"></a>パラメーター  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
## <a name="return-value"></a>戻り値  
 指定されている両方のセットのメンバーを含むセットです。  
  
## <a name="remarks"></a>解説  
 **+ (Union)** 演算子は、 [Union &#40;MDX&#41;](../mdx/union-mdx.md)関数と機能的には同等です。  
  
## <a name="examples"></a>例  
 この演算子の使用例を次に示します。  
  
```  
-- This member returns the gross profit margin for each year for North American countries.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members ON 0,  
    {[Sales Territory].[Sales Territory].[Country].[United States]} +  
     {[Sales Territory].[Sales Territory].[Country].[Canada]} ON 1  
FROM  
    [Adventure Works]  
WHERE  
    ([Measures].[Gross Profit Margin])  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 演算子リファレンス &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
