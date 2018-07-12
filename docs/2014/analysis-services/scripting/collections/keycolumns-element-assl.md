---
title: KeyColumns 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- KeyColumns Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- KeyColumns
helpviewer_keywords:
- KeyColumns element
ms.assetid: 03f3ad21-25cb-4afd-9287-cbf942ac1ad9
caps.latest.revision: 32
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 88df5fa8590bf3f049632abb8137e62e959a67fe
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37151613"
---
# <a name="keycolumns-element-assl"></a>KeyColumns 要素 (ASSL)
  コレクションを格納[KeyColumn](../objects/column-element-assl.md)親オブジェクトの要素の定義。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DimensionAttribute> <!-- or AggregationInstanceAttribute, AggregationInstanceCubeDimension, MeasureGroupAttribute, ScalarMiningStructureColumn -->  
   ...  
   <KeyColumns>  
      <KeyColumn xsi:type="DataItem"...</KeyColumn>  
   </KeyColumns>  
   ...  
</Dimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-n : 必須要素で、複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AggregationInstanceAttribute](../data-type/aggregationinstanceattribute-data-type-assl.md)、 [AggregationInstanceCubeDimension](../data-type/dimension-data-type-assl.md)、 [DimensionAttribute](../data-type/dimensionattribute-data-type-assl.md)、 [MeasureGroupAttribute](../data-type/measuregroupattribute-data-type-assl.md)、 [ScalarMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
|子要素|[KeyColumn](../objects/column-element-assl.md)型の[DataItem](../data-type/dataitem-data-type-assl.md)|  
  
## <a name="remarks"></a>コメント  
 `KeyColumns` コレクションには、属性またはマイニング構造列の複数の要素で構成されるキーを表す、複数の `KeyColumn` 要素を格納できます。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
