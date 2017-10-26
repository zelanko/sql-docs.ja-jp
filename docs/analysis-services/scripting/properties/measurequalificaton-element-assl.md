---
title: "MeasureQualificaton 要素 (ASSL) |Microsoft ドキュメント"
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
- MeasureQualificaton Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- MeasureQualification element
ms.assetid: 754a037c-f20b-4717-a6e8-12f495e8e3b4
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 01bb9fa9dab28eafbe0cd833028c7eef451d9c3f
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="measurequalificaton-element-assl"></a>MeasureQualificaton 要素 (ASSL)
  内のメジャーにプレフィックスが適用されるかどうかを決定、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)です。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroup>  
   ...  
   <MeasureQualification>...</MeasureQualification>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*なし*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メジャー グループ](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*なし*|このメジャー グループ内のメジャーにプレフィックスは適用されません。|  
|*PrefixMeasureGroup*|このメジャーグループの各メジャーの一意の名前およびキャプションに、プレフィックスとしてメジャー グループの名前と 1 つのスペースが付加されます。|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**MeasureQualification**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MeasureGroup>します。  
  
## <a name="see-also"></a>参照  
 [Cube 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/cube-element-assl.md)   
 [Dimension 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/dimension-element-assl.md)   
 [MeasureGroup 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

