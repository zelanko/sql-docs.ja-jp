---
title: "SolveOrder 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- SolveOrder Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- SolveOrder
helpviewer_keywords:
- SolveOrder element
ms.assetid: ec43e055-97dd-4f2a-9a7c-2df2e1119e56
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b16d2ca5c5bbef046b1332a62c7023300ee5f78a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="solveorder-element-assl"></a>SolveOrder 要素 (ASSL)
  解決順序を示す、 [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)要素は、計算されるメンバーまたは計算されるセル定義に適用します。  
  
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
|親要素|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **SolveOrder**プロパティに適用されます**CalculationProperty**要素を[CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md)の*メンバー*または*セル*です。  
  
 親に対応する要素**SolveOrder**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CalculationProperty>します。  
  
## <a name="see-also"></a>参照  
 [CalculationProperties 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [MdxScript 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScripts 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

