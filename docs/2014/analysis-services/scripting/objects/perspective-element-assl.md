---
title: Perspective 要素 (ASSL) |Microsoft Docs
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
- Perspective Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Perspective
helpviewer_keywords:
- Perspective element
ms.assetid: 0442334c-8b00-4451-ad81-02e58c735e8f
caps.latest.revision: 34
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3b006d7d48c072cb98a68e42c04cf75c4aaa9e04
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37297402"
---
# <a name="perspective-element-assl"></a>Perspective 要素 (ASSL)
  パースペクティブの詳細を定義、[キューブ](cube-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Perspectives>  
   <<Perspective>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Translations>...</Translations>  
      <DefaultMeasure>...</DefaultMeasure>  
      <Dimensions>...</Dimensions>  
            <MeasureGroups>...</MeasureGroups>  
      <Calculations>...</Calculations>  
      <Kpis>...</Kpis>  
            <Actions>...</Actions>  
      <Annotations>...</Annotations>  
   </Perspective>  
</Perspectives>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[パースペクティブ](../collections/perspectives-element-assl.md)|  
|子要素|[アクション](../collections/actions-element-assl.md)、[注釈](../collections/annotations-element-assl.md)、[計算](../collections/calculations-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、 [DefaultMeasure](measure-element-assl.md)、 [説明](../properties/description-element-assl.md)、[ディメンション](../collections/dimensions-element-assl.md)、 [ID](../properties/id-element-assl.md)、 [Kpi](../collections/kpis-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、 [MeasureGroups](../collections/groups-element-assl.md)、[名前](../properties/name-element-assl.md)、[翻訳](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 パースペクティブでは、含まれるディメンション、階層、属性、その他の詳細を選択し、含まれるデータのスライスを定義することによって、キューブのサブセットが提供されます。 パースペクティブは 1 つのキューブにより所有されます。 パースペクティブ内のオブジェクトをオーバーライドしたり追加したりすることはできません。すべてのディメンション、階層、その他の詳細は、基になるキューブに存在する必要があります。 オブジェクトを含めたり、非表示としてマークすることもできません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Perspective>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  
