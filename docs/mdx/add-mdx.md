---
title: + (追加)(MDX) |Microsoft ドキュメント
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 59031a14dd4c844aa8b0540d640e683c9d2f0894
ms.sourcegitcommit: 97bef3f248abce57422f15530c1685f91392b494
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34739711"
---
# <a name="-add-mdx"></a>+ (加算) (MDX)


  2 つの数を加算する算術演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Numeric_Expression + Numeric_Expression  
```  
  
#### <a name="parameters"></a>パラメーター  
 *数値式*  
 数値を返す有効な多次元式 (MDX) 式です。  
  
## <a name="return-value"></a>戻り値  
 パラメーターのデータ型のうち、優先順位が高い方のデータ型を持つ値です。  
  
## <a name="remarks"></a>コメント  
 両方の式は、同じデータ型でなければなりません。または、一方の式をもう一方の式のデータ型に暗黙的に変換できる必要があります。 1 つの式が NULL 値に評価される場合、この演算子は、もう一方の式の結果を返します。  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
