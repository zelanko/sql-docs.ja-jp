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
ms.openlocfilehash: 4d5f2316e3af5ce3c925ef71e1da5baf5bab868d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68036851"
---
# <a name="-string-concatenation-mdx"></a>+ (文字列連結) (MDX)


  2 つ以上の文字列、組、または文字列と組の組み合わせを連結する文字列演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
String_Expression + String_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *String_Expression*  
 文字列値を返す有効な多次元式 (MDX) 式です。  
  
## <a name="return-value"></a>戻り値  
 優先順位の高いパラメーターのデータ型を持つ値。  
  
## <a name="remarks"></a>Remarks  
 両方の式は、同じデータ型でなければなりません。または、一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。 1 つの式が NULL 値に評価される場合、この演算子は、もう一方の式の結果を返します。  
  
## <a name="see-also"></a>参照  
 [Mdx 演算子リファレンス &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
