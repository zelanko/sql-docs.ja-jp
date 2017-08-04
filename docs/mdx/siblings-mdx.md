---
title: "兄弟 (MDX) |Microsoft ドキュメント"
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
- SIBLINGS
dev_langs:
- kbMDX
helpviewer_keywords:
- Siblings function
ms.assetid: 33e63808-f07e-44f7-8dfa-4dd9fd89ec82
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 6b1f462e280c1d5ba289eab2fffccc0c13975ab0
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="siblings-mdx"></a>Siblings (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたメンバー自体を含めて、メンバーの兄弟を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Member_Expression.Siblings   
```  
  
## <a name="arguments"></a>引数  
 *メンバー式*  
 メンバーを 1 つ返す有効な多次元式 (MDX) 式です。  
  
### <a name="example"></a>例  
 次の例では、March 2003 の兄弟 (January 2003 と February 2003、および March 2003 自体も含む) の既定のメジャーが返されます。  
  
```  
SELECT [Date].[Calendar].[Month].[March 2003].Siblings ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

