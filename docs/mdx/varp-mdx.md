---
title: VarP (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dc1e6276de9a03af9800b9e242d54130c4241732
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63251477"
---
# <a name="varp-mdx"></a>VarP (MDX)


  バイアスをかけた母集団の公式を使用し、セットに対して評価される数値式の母分散を返します (除算*n*-1)。  
  
## <a name="syntax"></a>構文  
  
```  
  
VarP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression*  
 有効な数値式は、通常、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>コメント  
 **VarP**関数は、指定されたセットに対して評価される指定数値式のバイアスをかけた分散を返します。  
  
 **VarP**関数は、バイアスをかけた母集団を使用しているときに、数式、 [Var](../mdx/var-mdx.md)関数は、バイアスをかけない母集団の公式を使用します。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
