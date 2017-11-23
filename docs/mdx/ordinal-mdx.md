---
title: "序数 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Ordinal
dev_langs: kbMDX
helpviewer_keywords: Ordinal function
ms.assetid: 9d416c39-da4a-4f0d-8d85-a76af5df0a87
caps.latest.revision: "28"
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: d3251af290976850888e755287a47cf01bf72172
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="ordinal-mdx"></a>Ordinal (MDX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レベルに関連付けられた 0 から始まる序数値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Level_Expression.Ordinal   
```  
  
## <a name="arguments"></a>引数  
 *Level_Expression*  
 レベルを返す有効な多次元式 (MDX) 式です。  
  
## <a name="remarks"></a>解説  
 **序数**と共にで頻繁に使用される関数、 **IIF**と**CurrentMember**クエリ結果内の特定の各セルの序数位置に基づいて、条件付きで別の階層レベルで異なる値を表示する関数。 たとえば、使用することができます、**序数**関数を特定のレベルで計算を実行し、その他のレベルで、既定値は"N/A"を表示します。  
  
## <a name="example"></a>例  
 次の例では、Calendar 階層内の Calendar Quarter レベルの序数が返されます。  
  
```  
WITH MEMBER Measures.x AS [Date].[Calendar].[Calendar Quarter].Ordinal  
SELECT Measures.x on 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>参照  
 [MDX 関数リファレンス &#40;です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  
