---
title: "NonEmptyBehavior 要素 (ASSL) |Microsoft ドキュメント"
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
- NonEmptyBehavior Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- NonEmptyBehavior
helpviewer_keywords:
- NonEmptyBehavior element
ms.assetid: b4c78af4-b049-4189-a35b-206e3938d1db
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: bafd21bcaf9fc7ebfb06f6f37dbf87a0598cf31f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="nonemptybehavior-element-assl"></a>NonEmptyBehavior 要素 (ASSL)
  親に関連付けられている空でない動作を決定、 [CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperty>  
  
   <NonEmptyBehavior>...</NonEmptyBehavior>  
  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **NonEmptyBehavior**プロパティに適用されます**CalculationProperty**要素を[CalculationType](../../../analysis-services/scripting/properties/calculationtype-element-assl.md) 'éý'*メンバー*です。  
  
 親に対応する要素**NonEmptyBehavior**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CalculationProperty>します。  
  
## <a name="see-also"></a>参照  
 [CalculationProperties 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [MdxScript 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScripts 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

