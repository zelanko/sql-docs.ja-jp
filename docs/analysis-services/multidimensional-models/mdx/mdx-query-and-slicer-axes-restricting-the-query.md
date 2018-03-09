---
title: "クエリとスライサー軸 (MDX) クエリを制限する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/13/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: b0efaa9f791e125cb6a2b9b139a318a120f969c9
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/15/2018
---
# <a name="mdx-query-and-slicer-axes---restricting-the-query"></a>MDX クエリ軸とスライサー軸のクエリを制限します。
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
多次元式 (MDX) の SELECT ステートメントを作成する場合、アプリケーションでは通常、キューブを調べ、階層のセットを以下の 2 つのサブセットに分けます。  
  
-   **クエリ軸**。これは、複数のメンバーに関してデータを取得するための階層のセットです。 クエリ軸の詳細については、「[クエリ軸の内容の指定 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)」を参照してください。  
  
-   **スライサー軸**。これは、1 つのメンバーに関してデータを取得するための階層のセットです。 スライサー軸の詳細については、「[スライサー軸の内容の指定 &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)」を参照してください。  
  
 クエリ軸とスライサー軸は、クエリの実行対象であるキューブの複数の階層で構成できるため、これらの用語によって、クエリの実行対象であるキューブで使用される階層と、MDX クエリで返されたキューブで作成される階層とを区別しています。  
  
 クエリ軸のスライサー軸を使用する単純な例については、「[Using Query and Slicer Axes in a Simple Example &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md)」(クエリ軸とスライサー軸を使用する簡単な例) を参照してください。  
  
## <a name="see-also"></a>参照  
 [メンバー、組、およびセット &#40; の操作MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [MDX クエリの基礎と #40 です。Analysis Services &#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  
