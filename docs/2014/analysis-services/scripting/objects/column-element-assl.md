---
title: Column 要素 (ASSL) |Microsoft ドキュメント
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
- Column Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Column
helpviewer_keywords:
- Column element
ms.assetid: 10dc6d5e-c690-4415-adbb-eaeebaa29cb4
caps.latest.revision: 27
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 54fbcc7c236752d29a30ec89dafe4e7f5dfa491b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178551"
---
# <a name="column-element-assl"></a>Column 要素 (ASSL)
  親要素に関連付けられた列コレクション内の列を記述します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Columns>  
   <Column xsi:type="MeasureBinding">...</Column> <!-- parent of collection: DrillThroughAction -->  
   <!-- or -->  
   <Column xsi:type="CubeAttributeBinding">...</Column> <!-- parent of collection: DrillThroughAction -->  
   <!-- or -->  
   <Column xsi:type="EventColumn">...</Column> <!-- parent of collection: Event -->  
   <!-- or -->  
   <Column xsi:type="MiningModelColumn">...</Column> <!-- parent of collection: MiningModel or MiningModelColumn -->  
   <!-- or -->  
   <Column xsi:type="MiningStructureColumn">...</Column> <!-- parent of collection: MiningStructure or TableMiningStructureColumn -->  
</Columns>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ||  
|既定値|なし|  
|Cardinality||  
  
|先祖または親|データ型|  
|------------------------|---------------|  
|[DrillThroughAction](../data-type/binding-data-type-assl.md)、 [CubeAttributeBinding](../data-type/attributebinding-data-type-assl.md)|  
|[イベント](../data-type/eventcolumn-data-type-assl.md)|  
|[MiningModel](miningmodel-element-assl.md)、 [MiningModelColumn](../data-type/miningmodelcolumn-data-type-assl.md)|  
|[MiningStructure](miningstructure-element-assl.md)、 [TableMiningStructureColumn](../data-type/miningstructurecolumn-data-type-assl.md)|  
  
|先祖または親|Cardinality|  
|------------------------|-----------------|  
|[イベント](event-element-assl.md)|1-n : 必須要素で、複数回の出現が可能です|  
|他のすべて|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[[列]](../collections/columns-element-assl.md)|  
|子要素|なし|  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  