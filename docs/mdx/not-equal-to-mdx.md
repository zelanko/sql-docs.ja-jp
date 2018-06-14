---
title: '&lt;&gt; (等しくない)(MDX) |Microsoft ドキュメント'
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
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34742331"
---
# <a name="ltgt-not-equal-to-mdx"></a>&lt;&gt; (等しくない)(MDX)


  1 つの多次元式 (MDX) 式の値が、別の MDX 式の値と等しくないかどうかを判別する比較演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
MDX_Expression <> MDX_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *MDX_Expression*  
 有効な MDX 式です。  
  
## <a name="return-value"></a>戻り値  
 以下の条件に基づくブール値です。  
  
-   **true**両方のパラメーターが null 以外の場合と、最初のパラメーターが 2 番目のパラメーターと等しくないかどうか。  
  
-   **false**両方のパラメーターが null 以外の場合と、最初のパラメーターが 2 番目のパラメーターと等しいかどうかは。  
  
-   いずれか一方または両方のパラメーターが NULL 値に評価される場合は、NULL です。  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
