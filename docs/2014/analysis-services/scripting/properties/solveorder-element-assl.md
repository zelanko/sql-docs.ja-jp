---
title: SolveOrder 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- SolveOrder Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- SolveOrder
helpviewer_keywords:
- SolveOrder element
ms.assetid: ec43e055-97dd-4f2a-9a7c-2df2e1119e56
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: ed5092f93494162179dc2ee142a6769eddd5d6da
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36176703"
---
# <a name="solveorder-element-assl"></a>SolveOrder 要素 (ASSL)
  解決順序を示す、 [CalculationProperty](../objects/calculationproperty-element-assl.md)要素は、計算されるメンバーまたは計算されるセル定義に適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperty>  
   ...  
   <SolveOrder>...</SolveOrder>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|Integer|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CalculationProperty](../objects/calculationproperty-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `SolveOrder`プロパティに適用されます`CalculationProperty`要素を[CalculationType](calculationtype-element-assl.md)の*メンバー*または*セル*です。  
  
 親に対応する要素`SolveOrder`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CalculationProperty>します。  
  
## <a name="see-also"></a>参照  
 [CalculationProperties 要素&#40;ASSL&#41;](../collections/calculationproperties-element-assl.md)   
 [MdxScript 要素&#40;ASSL&#41;](../objects/mdxscript-element-assl.md)   
 [MdxScripts 要素&#40;ASSL&#41;](../collections/mdxscripts-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  