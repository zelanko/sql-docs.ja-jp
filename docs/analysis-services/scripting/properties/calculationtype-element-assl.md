---
title: "CalculationType 要素 (ASSL) |Microsoft ドキュメント"
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
- CalculationType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- CalculationType
helpviewer_keywords:
- CalculationType element
ms.assetid: b974b3d3-fbf7-4d77-8f6e-4e05a258fe84
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 35ef2ca152038a71474a62d2ae7a5b23678f1997
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="calculationtype-element-assl"></a>CalculationType 要素 (ASSL)
  関連付けられたで定義されている計算の種類を表します[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperty>  
   ...  
   <CalculationType>...</CalculationType>  
   ...  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|Description|  
|-----------|-----------------|  
|*メンバー*|計算プロパティは計算されるメンバーの定義に適用されます。|  
|*設定*|計算プロパティは名前付きセットの定義に適用されます。|  
|*セル*|計算プロパティは計算されるセルの定義に適用されます。|  
  
 許可される値に対応する列挙**CalculationType**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CalculationType>します。  
  
## <a name="see-also"></a>参照  
 [CalculationProperties 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/calculationproperties-element-assl.md)   
 [MdxScript 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)   
 [MdxScripts 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/mdxscripts-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

