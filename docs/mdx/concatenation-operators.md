---
title: 連結演算子 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8eacfc08fdeb0f92874758d0f95e5cde3e6b295a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181480"
---
# <a name="concatenation-operators"></a>連結演算子


  連結演算子はプラス記号 (+) です。 結合、または 1 つの文字の文字列に 2 つ以上の文字の文字列を連結することができます。 バイナリ文字列も連結できます。  
  
 次のコードでは、製品名、製品の一意の名前とを結合する連結演算子の例を示します。  
  
```  
WITH MEMBER Measures.ProductName AS   
   Product.Product.CurrentMember.Name + " (" + Product.Product.CurrentMember.UniqueName + ")"  
SELECT   
   {Measures.ProductName} ON COLUMNS,  
   Product.Product.Members ON ROWS  
FROM [Adventure Works]  
```  
  
## <a name="language-considerations"></a>言語に関する注意点  
 連結対象の複数の文字列の照合順序が同じである場合、連結結果の文字列は、入力と同じ照合順序になります。 連結したもので使用される文字列の照合順序が異なる場合は、照合順序の優先順位の規則は、連結結果の文字列の照合順序を決定します。 詳細については、「[言語および照合順序 &#40;Analysis Services&#41;](../analysis-services/languages-and-collations-analysis-services.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [MDX 演算子リファレンス&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [演算子&#40;MDX 構文&#41;](../mdx/operators-mdx-syntax.md)  
  
  
