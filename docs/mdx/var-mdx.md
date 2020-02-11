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
ms.openlocfilehash: 96bb307607792a3846ee6566027457a05ce3b905
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037927"
---
# <a name="var-mdx"></a>Var (MDX)


  バイアスをかけない母集団の公式 ( *n*で除算) を使用して、セットに対して評価される数値式のサンプル分散を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Var(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) 式です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **Var**関数は、指定されたセットに対して評価される指定された数値式のバイアスをかけない分散を返します。  
  
 **Var**関数は、バイアスをかける母集団の公式を使用し、 [VarP](../mdx/varp-mdx.md)関数はバイアスをかける母集団の公式を使用します。  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
