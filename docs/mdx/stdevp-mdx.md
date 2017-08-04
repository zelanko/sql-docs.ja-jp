---
title: "StdevP (MDX) |Microsoft ドキュメント"
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
- STDEVP
dev_langs:
- kbMDX
helpviewer_keywords:
- StdevP function [MDX]
ms.assetid: cd8ae7c9-3cef-49f0-bb41-8f577c7b6f31
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d72eb148aafccc60aa5097c8c7fed7f8b842a583
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="stdevp-mdx"></a>StdevP (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  バイアスをかけた母集団の公式を使用して、セットに対して評価される数値式の母標準偏差を返します (除算 *n* )。  
  
## <a name="syntax"></a>構文  
  
```  
  
StdevP(Set_Expression [ ,Numeric_Expression ] )  
```  
  
## <a name="arguments"></a>引数  
 *Set_Expression*  
 セットを返す有効な多次元式 (MDX) です。  
  
 *Numeric_Expression*  
 有効な数値式です。通常は、数値を返すセル座標の多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **StdevP**関数は、バイアスをかけた母集団を使用しているときに、数式、 [Stdev](../mdx/stdev-mdx.md)関数は、バイアスをかけない母集団の公式を使用します。  
  
## <a name="example"></a>例  
 次の例では、バイアスをかけた母集団の公式を使用して、2003 年度の最初の 3 か月に対して評価した、Internet Order Quantity の標準偏差を返します。  
  
```  
WITH MEMBER Measures.x AS   
   StdevP   
   ( { [Date].[Calendar].[Month].[January 2003],  
       [Date].[Calendar].[Month].[February 2003],  
       [Date].[Calendar].[Month].[March 2003]},  
    [Measures].[Internet Order Quantity])  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

