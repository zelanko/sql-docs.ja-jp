---
title: Visible 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Visible Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Visible
helpviewer_keywords:
- Visible element
ms.assetid: 3e9baf1b-351f-4ebf-b57d-13d561f72d6f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a28fa446eb1753ce85458a19b849729f57c67a7a
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48166662"
---
# <a name="visible-element-assl"></a>Visible 要素 (ASSL)
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
|親要素|[CalculationProperty](../objects/calculationproperty-element-assl.md)、[キューブ](../objects/cube-element-assl.md)、 [CubeDimension](../data-type/dimension-data-type-assl.md)、 [CubeHierarchy](../data-type/hierarchy-data-type-assl.md)、[データベース](../objects/database-element-assl.md)、[メジャー](../objects/measure-element-assl.md)、 [MemberProperty](../objects/attributerelationship-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Visible` 要素は、親要素をユーザー インターフェイス コンポーネントに表示する必要があるかどうかを決定します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで `Visible` の親に対応する要素は、<xref:Microsoft.AnalysisServices.CalculationProperty>、<xref:Microsoft.AnalysisServices.Cube>、<xref:Microsoft.AnalysisServices.CubeDimension>、<xref:Microsoft.AnalysisServices.CubeHierarchy>、<xref:Microsoft.AnalysisServices.Database>、および <xref:Microsoft.AnalysisServices.Measure> です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
