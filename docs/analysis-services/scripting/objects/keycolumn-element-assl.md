---
title: "KeyColumn 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- KeyColumn Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- KeyColumn
helpviewer_keywords:
- KeyColumn element
ms.assetid: 7b03eeb3-d478-4c38-822e-8cdfcc485039
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 58cb42e1d57ed2b18e05aad50bf6ab04403f5ad3
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="keycolumn-element-assl"></a>KeyColumn 要素 (ASSL)
  属性のキーまたはその一部である、列の定義を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<KeyColumns>  
   <KeyColumn xsi:type="DataItem">...</KeyColumn>  
<KeyColumns>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|1-n : 必須要素で、複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[Keycolumns]](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 詳細については、 **DataItem**の Analysis Services スクリプト言語 (ASSL) オブジェクトおよびプロパティのテーブルを含む、型、 **DataItem**を入力しを参照してください[DataItem データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 親に対応する要素、 **KeyColumns**分析管理オブジェクト (AMO) オブジェクト モデルのコレクションは<xref:Microsoft.AnalysisServices.AggregationInstanceAttribute>、 <xref:Microsoft.AnalysisServices.DimensionAttribute>、 <xref:Microsoft.AnalysisServices.MeasureGroupAttribute>、および<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>です。  
  
## <a name="see-also"></a>参照  
 [AggregationInstanceAttribute データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationinstanceattribute-data-type-assl.md)   
 [AggregationInstanceCubeDimension データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationinstancecubedimension-data-type-assl.md)   
 [DimensionAttribute データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/dimensionattribute-data-type-assl.md)   
 [MeasureGroupAttribute データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/measuregroupattribute-data-type-assl.md)   
 [ScalarMiningStructureColumn データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/scalarminingstructurecolumn-data-type-assl.md)   
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
