---
title: + (文字列連結)(MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 292d671fb3b971c30b6e261e3b851aba1ead9b36
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63150010"
---
# <a name="-string-concatenation-mdx"></a>+ (文字列連結) (MDX)


  2 つ以上の文字列、組、または文字列と組の組み合わせを連結する文字列演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
String_Expression + String_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *String_Expression*  
 文字列値を返す有効な多次元式 (MDX) 式。  
  
## <a name="return-value"></a>戻り値  
 優先順位の高いパラメーターのデータ型の値。  
  
## <a name="remarks"></a>コメント  
 1 つの式は、その他の式のデータ型に暗黙的に変換できる必要がありますか、同じデータ型の両方の式があります。 1 つの式が NULL 値に評価される場合、この演算子は、もう一方の式の結果を返します。  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
