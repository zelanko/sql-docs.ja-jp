---
title: 連結演算子 |Microsoft ドキュメント
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
dev_langs:
- kbMDX
helpviewer_keywords:
- concatenation operators [MDX]
ms.assetid: 9e4c181a-b71e-41ec-98a1-ec8b5b5103b1
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: d84baf1472265bf6c2f9b5d5354ef4f22bd79858
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="concatenation-operators"></a>連結演算子
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  連結演算子はプラス記号 (+) です。 複数の文字列を 1 つの文字列に結合つまり連結できます。 バイナリ文字列も連結できます。  
  
 以下のコードは、製品名とその製品の一意の名前を結合する連結演算子の例です。  
  
```  
WITH MEMBER Measures.ProductName AS   
   Product.Product.CurrentMember.Name + " (" + Product.Product.CurrentMember.UniqueName + ")"  
SELECT   
   {Measures.ProductName} ON COLUMNS,  
   Product.Product.Members ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="language-considerations"></a>言語に関する注意点  
 連結対象の複数の文字列の照合順序が同じである場合、連結結果の文字列は、入力と同じ照合順序になります。 連結対象の複数の文字列の照合順序が異なる場合、連結結果の文字列の照合順序は、照合優先順位の規則によって決まります。 詳細については、「[言語および照合順序 &#40;Analysis Services&#41;](../analysis-services/languages-and-collations-analysis-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [演算子&#40;MDX 構文&#41;](../mdx/operators-mdx-syntax.md)  
  
  
