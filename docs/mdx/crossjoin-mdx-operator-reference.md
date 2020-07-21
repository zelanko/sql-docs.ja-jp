---
title: '* Crossjoin(MDX) |Microsoft Docs'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 2f8377acec8f213c423de5d19d8859c8b3d93a06
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68047141"
---
# <a name="crossjoin----mdx-operator-reference"></a>Crossjoin-MDX 演算子リファレンス


  2つのセットのクロス積を返すセット演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Set_Expression * Set_Expression  
```  
  
## <a name="parameter"></a>パラメーター  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
## <a name="return-value"></a>戻り値  
 指定された両方のパラメーターのクロス積を含むセット。  
  
## <a name="remarks"></a>Remarks  
 (Crossjoin) 演算子は、機能的には[Crossjoin](../mdx/crossjoin-mdx.md)関数と同等です。 ** \* **  
  
## <a name="examples"></a>使用例  
 この演算子の使用例を次に示します。  
  
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
 [Mdx 演算子リファレンス &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
