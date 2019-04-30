---
title: Var (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 14caf6e96b41fdf2e7f8b4d20f16852e890bd166
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63251508"
---
# <a name="var-mdx"></a>Var (MDX)


  バイアスをかけない母集団の公式を使用して、セットに対して評価される数値式のサンプル分散を返します (除算*n*)。  
  
## <a name="syntax"></a>構文  
  
```  
  
Var(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression*  
 有効な数値式は、通常、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **Var**関数は、指定されたセットに対して評価される指定数値式のバイアスをかけない分散を返します。  
  
 **Var**関数は、バイアスをかけない母集団数式を使用して、 [VarP](../mdx/varp-mdx.md)関数は、バイアスをかけた母集団の公式を使用します。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
