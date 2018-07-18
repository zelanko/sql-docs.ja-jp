---
title: Relationships 要素 (ASSL) |Microsoft Docs
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
ms.assetid: e78882c9-b14e-4044-848e-ea7fddd3b75d
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2071ae26b20ee39b47115e4ada1695878631fc84
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37316952"
---
# <a name="relationships-element-assl"></a>Relationships 要素 (ASSL)
  関連付けられているディメンションのリレーションシップのコレクションを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimension> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <Attributes>  
      <Attribute>...</Attribute>  
  </Attributes>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeDimension](../data-type/dimension-data-type-assl.md)、[ディメンション](../objects/dimension-element-assl.md)、 [PerspectiveDimension](../data-type/perspectivedimension-data-type-assl.md)、 [RegularMeasureGroupDimension](../data-type/measuregroupdimension-data-type-assl.md)|  
|子要素|[リレーションシップ](../data-type/relationship-data-type-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデル内の対応する要素が<xref:Microsoft.AnalysisServices.RelationshipCollection>します。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  
