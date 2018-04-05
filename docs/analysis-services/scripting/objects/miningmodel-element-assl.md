---
title: MiningModel 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- MiningModel Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningModel
helpviewer_keywords:
- MiningModel element
ms.assetid: a61d935f-c8f6-457d-ad0c-44f58bb286f5
caps.latest.revision: 38
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 3acf412e4f7e880e6ce1b76799f6990ce32bf905
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="miningmodel-element-assl"></a>MiningModel 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]1 つのデータ マイニング モデルを定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningModels>  
      <MiningModel>  
      <Name>...</Name>  
            <ID>...</ID>  
      <Description>...</<Descrip  
            <Algorithm>...</Algorithm>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastProcessed>...</LastProcessed>  
      <AlgorithmParameters>...</AlgorithmParameters>  
      <AllowDrillThrough>...</AllowDrillThrough>  
      <Translations>...</Translations>  
      <Columns>...</Columns>  
      <State>...</State>  
      <MiningModelPermissions>...</MiningModelPermissions>  
      <Language>...</Language>  
            <Collation>...</Collation>  
            <Annotations>...</Annotations>  
            <ddl100_100:FoldingParameters>   </FoldingParameters>  
   </MiningModel>  
</MiningModels>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|基数|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[MiningModels](../../../analysis-services/scripting/collections/miningmodels-element-assl.md)|  
|子要素|[アルゴリズム](../../../analysis-services/scripting/properties/algorithm-element-assl.md)、 [AlgorithmParameters](../../../analysis-services/scripting/objects/algorithmparameter-element-assl.md)、 [AllowDrillThrough](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md)、[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[照合](../../../analysis-services/scripting/properties/collation-element-assl.md)、 [列](../../../analysis-services/scripting/collections/columns-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、[言語](../../../analysis-services/scripting/properties/language-element-assl.md)、 [LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、 [MiningModelPermissions](../../../analysis-services/scripting/collections/miningmodelpermissions-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[状態](../../../analysis-services/scripting/properties/state-element-assl.md)、 [翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)、<br /><br /> [FoldingParameters](../../../analysis-services/scripting/properties/foldingparameters-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 **FoldingParameters**マイニング モデルの要素は、サーバーによる内部使用と DDL ステートメントで使用することはできません。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.MiningModel>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
