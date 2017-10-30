---
title: "Count (階層レベル) (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- COUNT
dev_langs:
- kbMDX
helpviewer_keywords:
- Count function [MDX]
ms.assetid: 3de6a824-2ff3-47ac-9ceb-e3369a04f35d
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: d3e031210ea5b19628bc11a044b5c3977c465b9a
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="count-hierarchy-levels-mdx"></a>Count (階層レベル) (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  階層内のレベル数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Hierarchy_Expression.Levels.Count  
```  
  
## <a name="arguments"></a>引数  
 *Hierarchy_Expression*  
 階層を返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 階層内のレベル数を返します。`[All]` レベルがある場合はこれも含みます。  
  
> [!IMPORTANT]  
>  表示可能な階層がディメンション内に 1 つしかない場合は、ディメンション名がその 1 つしかない階層に解決されるため、その階層はディメンション名でも階層名でも参照できます。 たとえば、`Measures.Levels.Count`有効な MDX 式は、Measures ディメンション内の唯一の階層に解決されるためです。  
  
## <a name="example"></a>例  
 次の例は、Adventure Works キューブ内のユーザー定義階層 Product Categories 内のレベル数を返します。  
  
```  
WITH MEMBER measures.X AS  
   [Product].[Product Categories].Levels.Count   
Select Measures.X ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [カウント (&) #40";"ディメンション"&"#41;& #40 です。MDX と #41 です。](../mdx/count-dimension-mdx.md)   
 [カウント & #40 です。組と #41 です。& #40 です。MDX と #41 です。](../mdx/count-tuple-mdx.md)   
 [カウント & #40 です。セット &#41;& #40 です。MDX と #41 です。](../mdx/count-set-mdx.md)   
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

