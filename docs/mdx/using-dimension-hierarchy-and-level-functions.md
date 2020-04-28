---
title: ディメンション、階層、およびレベル関数の使用 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 8fa374ef93f56f8cddaed81bc9e3872d1eb206c7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68097184"
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>ディメンション関数、階層関数、およびレベル関数の使用


  ディメンション、階層、およびレベル関数は、Analysis Services で見つかった多次元構造を走査するのに役立ちます。 通常、このような関数を他の関数と組み合わせて使用して、ディメンション、階層、またはレベルのメンバーに関する情報を取得します。  
  
 を使用する方法を次の例に示し**ます。Dimension**、 **。階層**、および **。レベル**関数:  
  
 `WITH`  
  
 `MEMBER MEASURES.DIMENSIONNAME AS [Date].[Calendar].CURRENTMEMBER.DIMENSION.NAME`  
  
 `MEMBER MEASURES.HIERARCHYNAME AS [Date].[Calendar].CURRENTMEMBER.HIERARCHY.NAME`  
  
 `MEMBER MEASURES.LEVELNAME AS [Date].[Calendar].LEVEL.NAME`  
  
 `SELECT`  
  
 `{MEASURES.DIMENSIONNAME, MEASURES.HIERARCHYNAME, MEASURES.LEVELNAME}`  
  
 `ON Columns,`  
  
 `[Date].[Calendar].MEMBERS`  
  
 `ON Rows`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>参照  
 [ディメンション &#40;MDX&#41;](../mdx/dimension-mdx.md)   
 [関数 &#40;MDX 構文&#41;](../mdx/functions-mdx-syntax.md)   
 [階層 &#40;MDX&#41;](../mdx/hierarchy-mdx.md)   
 [MDX&#41;&#40;レベル](../mdx/level-mdx.md)  
  
  
