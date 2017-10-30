---
title: "ディメンション、階層、およびレベル関数を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
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
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 10996fe3bec61356308a59ef78e52ecfeacca95a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="using-dimension-hierarchy-and-level-functions"></a>ディメンション関数、階層関数、およびレベル関数の使用
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

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
 [ディメンションと #40 です。MDX と #41 です。](../mdx/dimension-mdx.md)   
 [関数と #40 です。MDX 構文 &#41;](../mdx/functions-mdx-syntax.md)   
 [階層 & #40 です。MDX と #41 です。](../mdx/hierarchy-mdx.md)   
 [レベル & #40 です。MDX と #41 です。](../mdx/level-mdx.md)  
  
  

