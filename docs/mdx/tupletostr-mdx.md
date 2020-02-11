---
title: TupleToStr (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: d6cde1f60274d1437517d89e48b111e9e7298b9d
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68097371"
---
# <a name="tupletostr-mdx"></a>TupleToStr (MDX)


  指定された組に対応する多次元式 (MDX) 形式の文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
TupleToStr(Tuple_Expression)   
```  
  
## <a name="arguments"></a>引数  
 *Tuple_Expression*  
 組を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 この関数は、解析用に組の文字列表記を外部関数に転送する場合に使用します。 返される文字列は中かっこ{}で囲まれ、各メンバーは組で明示的に定義されている場合はコンマで区切られます。  
  
## <a name="examples"></a>例  
 次の例では、文字列 ([Date]. [暦年]。 & [2001]、[Geography]。[Geography]。[Country] & [米国]):  
  
```  
WITH MEMBER Measures.x AS TupleToStr   
   (   
      ([Date].[Calendar Year].&[2001]  
         , [Geography].[Geography].[Country].&[United States]  
      )  
   )     
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
 次の例も、上の例と同じ文字列を返します。  
  
```  
WITH SET s AS   
   {  
      ([Date].[Calendar Year].&[2001],  
         [Geography].[Geography].[Country].&[United States]  
      )   
   }  
MEMBER Measures.x AS TupleToStr ( s.Item(0) )  
SELECT Measures.x ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [Mdx 関数リファレンス &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
