---
title: KeyColumn 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- KeyColumn Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyColumn
helpviewer_keywords:
- KeyColumn element
ms.assetid: 7b03eeb3-d478-4c38-822e-8cdfcc485039
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1cc42afde5212befbbd2a16a81340fb7e1f629bb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48090327"
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
|データ型と長さ|[DataItem](../data-type/dataitem-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|1-n : 必須要素で、複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[Keycolumns]](../collections/columns-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 詳細については、`DataItem`の Analysis Services スクリプト言語 (ASSL) オブジェクトおよびプロパティのテーブルを含む、型、`DataItem`入力を参照してください[DataItem データ型&#40;ASSL&#41;](../data-type/dataitem-data-type-assl.md)します。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで `KeyColumns` コレクションの親に対応する要素は、<xref:Microsoft.AnalysisServices.AggregationInstanceAttribute>、<xref:Microsoft.AnalysisServices.DimensionAttribute>、<xref:Microsoft.AnalysisServices.MeasureGroupAttribute>、および <xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn> です。  
  
## <a name="see-also"></a>参照  
 [AggregationInstanceAttribute データ型&#40;ASSL&#41;](../data-type/aggregationinstanceattribute-data-type-assl.md)   
 [AggregationInstanceCubeDimension データ型&#40;ASSL&#41;](../data-type/dimension-data-type-assl.md)   
 [DimensionAttribute データ型&#40;ASSL&#41;](../data-type/dimensionattribute-data-type-assl.md)   
 [MeasureGroupAttribute データ型&#40;ASSL&#41;](../data-type/measuregroupattribute-data-type-assl.md)   
 [ScalarMiningStructureColumn データ型&#40;ASSL&#41;](../data-type/miningstructurecolumn-data-type-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
