---
title: CovarianceN (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- COVARIANCEN
dev_langs:
- kbMDX
helpviewer_keywords:
- Covariancen function
ms.assetid: 1cc621cd-ffa0-40aa-91f0-bc5cb57f692b
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 35bf5e9917545fc7bcc1fac6ae3aae2d289c65fc
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="covariancen-mdx"></a>CovarianceN (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  バイアスをかけない母集団の公式 (X と Y のペアの数で除算) を使用して、セットに対して評価された値の X と Y のペアのサンプル共分散を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
CovarianceN(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression_y*  
 有効な数値式です。通常は、Y 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
 *Numeric_Expression_x*  
 有効な数値式です。通常は、X 軸の値を表す数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **CovarianceN**関数は、y 軸の値を取得する、最初の数値式に対して指定されたセットを評価します。 次に、2 番目の数値式が指定されている場合は、指定されているセットをその式に対して評価し、X 軸の値のセットを取得します。 2 番目の数値式が指定されていない場合は、指定されたセット内のセルの現在のコンテキストを X 軸の値として使用します。  
  
 **CovarianceN**関数は、バイアスをかけない母集団の公式を使用します。 これは、対照的に、[共変性](../mdx/covariance-mdx.md)バイアスをかけた母集団の公式 (x と y のペアの数で除算) を使用する関数。  
  
> [!NOTE]  
>  **CovarianceN**関数は空のセルまたはテキストや論理値を含むセルを無視します。 ただし、0 の値を持つセルは対象になります。  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
