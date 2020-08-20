---
description: 連結演算子
title: 連結演算子 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 54e935e3491156c04e1a4b9e704b655a7151fdb3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88466494"
---
# <a name="concatenation-operators"></a>連結演算子


  連結演算子はプラス記号 (+) です。 複数の文字列を1つの文字列に結合したり、連結したりすることができます。 バイナリ文字列も連結できます。  
  
 製品名と製品の一意の名前を組み合わせる連結演算子の例を次のコードに示します。  
  
```  
WITH MEMBER Measures.ProductName AS   
   Product.Product.CurrentMember.Name + " (" + Product.Product.CurrentMember.UniqueName + ")"  
SELECT   
   {Measures.ProductName} ON COLUMNS,  
   Product.Product.Members ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="language-considerations"></a>言語に関する注意点  
 連結対象の複数の文字列の照合順序が同じである場合、連結結果の文字列は、入力と同じ照合順序になります。 連結で使用される文字列の照合順序が異なる場合、照合順序の優先順位の規則によって、結果として得られる文字列の照合順序が決まります。 詳細については、「[言語および照合順序 &#40;Analysis Services&#41;](https://docs.microsoft.com/analysis-services/languages-and-collations-analysis-services)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Mdx 演算子リファレンス &#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [MDX 構文 &#40;の演算子&#41;](../mdx/operators-mdx-syntax.md)  
  
  
