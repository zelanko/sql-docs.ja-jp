---
title: Stdev (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- STDEV
dev_langs:
- kbMDX
helpviewer_keywords:
- Stdev function [MDX]
ms.assetid: c3e31763-18ca-4a2b-bc03-3ee777970c68
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 8210c22fb7ae3ee1c989ceb4fd68582c494b9dcb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="stdev-mdx"></a>Stdev (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  バイアスをかけない母集団の公式 (n-1 で除算) を使用して、セットに対して評価した数値式のサンプル標準偏差を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Stdev(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **Stdev**関数は、バイアスをかけない母集団を使用しているときに、数式、 [StdevP](../mdx/stdevp-mdx.md)関数は、バイアスをかけた母集団の公式を使用します。  
  
## <a name="example"></a>例  
 次の例では、バイアスをかけない母集団の公式を使用して、2003 年度の最初の 3 か月に対して評価した、Internet Order Quantity の標準偏差を返します。  
  
```  
WITH MEMBER Measures.x AS   
   Stdev   
   ( { [Date].[Calendar].[Month].[January 2003],  
       [Date].[Calendar].[Month].[February 2003],  
       [Date].[Calendar].[Month].[March 2003]},  
    [Measures].[Internet Order Quantity])  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
