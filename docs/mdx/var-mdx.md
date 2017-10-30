---
title: "Var (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- VAR
dev_langs:
- kbMDX
helpviewer_keywords:
- Var function [MDX]
ms.assetid: 5575b68e-ebc1-4eaf-9547-1321d495ea62
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 62031626198e41bd798f27ac9c94137b3438ffe8
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="var-mdx"></a>Var (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  バイアスをかけない母集団の公式を使用して、セットに対して評価される数値式のサンプル分散を返します (除算 *n* )。  
  
## <a name="syntax"></a>構文  
  
```  
  
Var(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **Var**関数、指定されたセットに対して評価される指定数値式のバイアスをかけない分散を返します。  
  
 **Var**関数は、バイアスをかけない母集団数式を使用し、 [VarP](../mdx/varp-mdx.md)関数は、バイアスをかけた母集団の公式を使用します。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

