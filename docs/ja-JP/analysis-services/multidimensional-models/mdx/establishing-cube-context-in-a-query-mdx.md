---
title: クエリ (MDX) 内のキューブ コンテキストを確立 |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b2439072216ca037254758c5d43161aec8d25835
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="establishing-cube-context-in-a-query-mdx"></a>クエリ内のキューブ コンテキストの確立 (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [MDX クエリの基礎と #40 です。Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
