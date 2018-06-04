---
title: ディメンション、階層、およびレベル関数を使用して |Microsoft ドキュメント
ms.date: 05/30/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 96315c01133f3a25e5853ba076d2b28e5ba81a35
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2018
ms.locfileid: "34581494"
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>ディメンション関数、階層関数、およびレベル関数の使用
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  ディメンション関数、階層関数、およびレベル関数は、Analysis Services で検出された多次元階層をスキャンする際に役立ちます。 通常は、ディメンション、階層、またはレベルのメンバーに関する情報を得るために、これらの関数を他の関数と共に使用します。  
  
 次の例を使用する方法を示しています、 **[.Dimension](../mdx/dimension-mdx.md)** 、 **[.Hierarchy](../mdx/hierarchy-mdx.md)** 、および **[.Level](../mdx/level-mdx.md)** 関数。  
  
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
 [Dimension&#40;MDX&#41;](../mdx/dimension-mdx.md)   
 [関数&#40;MDX 構文&#41;](../mdx/functions-mdx-syntax.md)   
 [Hierarchy&#40;MDX&#41;](../mdx/hierarchy-mdx.md)   
 [Lavel&#40;MDX&#41;](../mdx/level-mdx.md)  
  
  
