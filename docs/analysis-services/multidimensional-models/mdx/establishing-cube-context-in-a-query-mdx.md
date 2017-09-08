---
title: "クエリ (MDX) 内のキューブ コンテキストを確立 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cubes [Analysis Services], MDX
- MDX [Analysis Services], cube context
- SELECT statement [MDX]
- Multidimensional Expressions [Analysis Services], cube context
- queries [MDX], cube context
ms.assetid: 79d6a1e8-2825-4eb9-97df-5071aecae8f0
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 826945c3b044e76db93204fcd29afbe822c7e8a6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="establishing-cube-context-in-a-query-mdx"></a>クエリ内のキューブ コンテキストの確立 (MDX)
  各 MDX クエリは、指定したキューブ コンテキスト内で実行されます。 このコンテキストは、クエリ内の式によって評価されるメンバーを定義します。  
  
 SELECT ステートメントでは、FROM 句によってキューブ コンテキストを指定します。 このコンテキストは、キューブ全体の場合もあれば、キューブの中にある 1 つのサブキューブの場合もあります。 FROM 句によってキューブ コンテキストを指定してから、追加の関数によってそのコンテキストを拡大したり縮小したりすることも可能です。  
  
> [!NOTE]  
>  SCOPE ステートメントと CALCULATE ステートメントによって、MDX スクリプト内のキューブ コンテキストを管理することもできます。 詳細については、「[MDX スクリプティングの基礎 (Analysis Services)](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)」を参照してください。  
  
## <a name="from-clause-syntax"></a>FROM 句の構文  
 FROM 句の構文は、以下のとおりです。  
  
```  
<SELECT subcube clause> ::=  
   Cube_Identifier |   
   (SELECT [  
      * |   
      ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]   
   FROM <SELECT subcube clause> <SELECT slicer axis clause> )  
```  
  
 この構文では、 `<SELECT subcube clause>` 句によって、SELECT ステートメントの実行対象にするキューブまたはサブキューブを記述します。  
  
 シンプルな例としては、FROM 句で Adventure Works サンプル キューブ全体を対象として指定する例があります。 そのような FROM 句の形式は、以下のとおりです。  
  
```  
FROM [Adventure Works]  
```  
  
 MDX の SELECT ステートメントで使用する FROM 句の詳細については、「[SELECT ステートメント (MDX)](../../../mdx/mdx-data-manipulation-select.md)」を参照してください。  
  
## <a name="refining-the-context"></a>コンテキストの調整  
 FROM 句ではいずれか 1 つのキューブがキューブ コンテキストとなりますが、複数のキューブのデータを同時に操作できないわけではありません。  
  
 キューブ コンテキストの外部のキューブからデータを取得する場合は、MDX の [LookupCube](../../../mdx/lookupcube-mdx.md) 関数を使用できます。 さらに、クエリの評価時にコンテキストを一時的に制限するために、 [Filter](../../../mdx/filter-mdx.md) などの関数も用意されています。  
  
## <a name="see-also"></a>参照  
 [MDX クエリの基礎 &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
