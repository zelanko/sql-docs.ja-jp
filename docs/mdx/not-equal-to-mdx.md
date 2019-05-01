---
title: '&lt;&gt; (等しくない)(MDX) |Microsoft Docs'
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ac3241e7d6acd8ba883cdd59f9410f4a0fd9187d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63277516"
---
# <a name="ltgt-not-equal-to-mdx"></a>&lt;&gt; (等しくない)(MDX)


  1 つの多次元式 (MDX) 式の値が別の MDX 式の値と等しくないかどうかを決定する比較演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
MDX_Expression <> MDX_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *MDX_Expression*  
 有効な MDX 式です。  
  
## <a name="return-value"></a>戻り値  
 次の条件に基づくブール値。  
  
-   **true**両方のパラメーターが null 以外の場合と、最初のパラメーターが 2 番目のパラメーターと等しくないかどうか。  
  
-   **false**両方のパラメーターが null 以外の場合と、最初のパラメーターが 2 番目のパラメーターと等しいかどうか。  
  
-   いずれか一方または両方のパラメーターが NULL 値に評価される場合は、NULL です。  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
