---
title: Relationships 要素 (ASSL) |Microsoft ドキュメント
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
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 987b35a09670908e5604693c2b42b4a014d5eda6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36173551"
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
 分析管理オブジェクト (AMO) オブジェクト モデル内の対応する要素が<xref:Microsoft.AnalysisServices.RelationshipCollection>です。  
  
## <a name="see-also"></a>参照  
 [コレクション&#40;ASSL&#41;](collections-assl.md)  
  
  