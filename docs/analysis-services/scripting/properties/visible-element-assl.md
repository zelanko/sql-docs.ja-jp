---
title: Visible 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- Visible Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- Visible
helpviewer_keywords:
- Visible element
ms.assetid: 3e9baf1b-351f-4ebf-b57d-13d561f72d6f
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d47e6f1d64fb1868fc0e06cb9f806c49e17d3ba8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="visible-element-assl"></a>Visible 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  親要素の表示を決定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CalculationProperty> <!-- or one of the elements listed below in the Element Relationships table -->  
  
   <Visible >...</Visible >  
  
</CalculationProperty>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|True|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CalculationProperty](../../../analysis-services/scripting/objects/calculationproperty-element-assl.md)、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、 [CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)、 [CubeHierarchy](../../../analysis-services/scripting/data-type/cubehierarchy-data-type-assl.md)、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)、[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)、 [MemberProperty](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **Visible**要素は、ユーザー インターフェイス コンポーネントが、親要素を表示するかどうかを指定します。  
  
 親に対応する要素**Visible**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.CalculationProperty>、 <xref:Microsoft.AnalysisServices.Cube>、 <xref:Microsoft.AnalysisServices.CubeDimension>、 <xref:Microsoft.AnalysisServices.CubeHierarchy>、 <xref:Microsoft.AnalysisServices.Database>、および<xref:Microsoft.AnalysisServices.Measure>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
