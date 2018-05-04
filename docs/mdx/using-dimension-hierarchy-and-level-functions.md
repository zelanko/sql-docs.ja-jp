---
title: ディメンション、階層、およびレベル関数を使用して |Microsoft ドキュメント
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
- dimensions [Analysis Services], functions
- level functions [MDX]
- hierarchy functions [MDX]
ms.assetid: e730f65a-1798-4094-9acf-2739e2505d52
caps.latest.revision: 25
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 3dd67eb8c1883eddfab04542456da0b09fdb6f50
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-dimension-hierarchy-and-level-functions"></a>ディメンション関数、階層関数、およびレベル関数の使用
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  ディメンション関数、階層関数、およびレベル関数は、Analysis Services で検出された多次元階層をスキャンする際に役立ちます。 通常は、ディメンション、階層、またはレベルのメンバーに関する情報を得るために、これらの関数を他の関数と共に使用します。  
  
 次の例を使用する方法を示しています、**です。ディメンション**、**です。階層**、および**です。レベル**関数。  
  
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
 [ディメンション&#40;MDX&#41;](../mdx/dimension-mdx.md)   
 [関数&#40;MDX 構文&#41;](../mdx/functions-mdx-syntax.md)   
 [階層&#40;MDX&#41;](../mdx/hierarchy-mdx.md)   
 [レベル&#40;MDX&#41;](../mdx/level-mdx.md)  
  
  
