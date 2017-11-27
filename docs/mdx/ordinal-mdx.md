---
title: "序数 (MDX) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Ordinal
dev_langs:
- kbMDX
helpviewer_keywords:
- Ordinal function
ms.assetid: 9d416c39-da4a-4f0d-8d85-a76af5df0a87
caps.latest.revision: 28
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b848698799bc0c620d9592e90f508f01ac279f6f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="ordinal-mdx"></a>Ordinal (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

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
 [MDX 関数リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-function-reference-mdx.md)  
  
  

