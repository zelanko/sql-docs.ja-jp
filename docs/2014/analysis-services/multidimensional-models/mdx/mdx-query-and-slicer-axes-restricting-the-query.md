---
title: クエリ軸とスライサー軸 (MDX) によるクエリの制限 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Multidimensional Expressions [Analysis Services], axes
- queries [MDX], axes
- axes [MDX]
- MDX [Analysis Services], axes
ms.assetid: a64b8172-cd73-42f9-8847-52e967b9697a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b2a7d69055d3d60f8805a7cf7e8b9f1a98b9c01e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048184"
---
# <a name="restricting-the-query-with-query-and-slicer-axes-mdx"></a>クエリ軸とスライサー軸によるクエリの制限 (MDX)
  多次元式 (MDX) の SELECT ステートメントを作成する場合、アプリケーションでは通常、キューブを調べ、階層のセットを以下の 2 つのサブセットに分けます。  
  
-   **クエリ軸**。これは、複数のメンバーに関してデータを取得するための階層のセットです。 クエリ軸の詳細については、「[クエリ軸の内容の指定 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-query-axis.md)」を参照してください。  
  
-   **スライサー軸**。これは、1 つのメンバーに関してデータを取得するための階層のセットです。 スライサー軸の詳細については、「[スライサー軸の内容の指定 &#40;MDX&#41;](mdx-query-and-slicer-axes-specify-the-contents-of-a-slicer-axis.md)」を参照してください。  
  
 クエリ軸とスライサー軸は、クエリの実行対象であるキューブの複数の階層で構成できるため、これらの用語によって、クエリの実行対象であるキューブで使用される階層と、MDX クエリで返されたキューブで作成される階層とを区別しています。  
  
 クエリ軸のスライサー軸を使用する単純な例については、「[Using Query and Slicer Axes in a Simple Example &#40;MDX&#41;](mdx-query-and-slicer-axes-using-axes-in-a-simple-example.md)」(クエリ軸とスライサー軸を使用する簡単な例) を参照してください。  
  
## <a name="see-also"></a>参照  
 [メンバー、組、およびセットの操作&#40;MDX&#41;](working-with-members-tuples-and-sets-mdx.md)   
 [MDX クエリの基礎&#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
