---
title: "MiningStructure 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- MiningStructure Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- MiningStructure
helpviewer_keywords:
- MiningStructure element
ms.assetid: b943cd92-0ed8-4bd8-8fbc-7dab0534aede
caps.latest.revision: 48
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 0f0ce9ca930e54c1cf8ac989330e00f298a06a28
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="miningstructure-element-assl"></a>MiningStructure 要素 (ASSL)
  マイニング モデルのセットの構造を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MiningStructures>  
   <MiningStructure>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</<Description>  
      <Source>...</Source>  
      <CreatedTimestamp>...</<CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LastProcessed>...</LastProcessed>  
      <Translations>...</Translations>  
      <Language>...</Language>  
            <Collation>...</Collation>  
      <ErrorConfiguration>...</ErrorConfiguration>  
      <CacheMode>...</CacheMode>  
            <Columns>...</Columns>  
      <State>...</State>  
      <HoldoutActualSize>...</HoldoutActualSize>  
      <HoldoutMaxCases>...</HoldoutMaxCases>  
      <HoldoutMaxPercent>...</HoldoutMaxPercent>  
      <HoldoutSeed>...</HoldoutSeed>        
            <MiningStructurePermissions>...</<MiningStructurePermissions>  
            <MiningModels>...</MiningModels>  
            <Annotations>...</Annotations>  
   </MiningStructure>  
</MiningStructures>  
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
|親要素|[MiningStructures](../../../analysis-services/scripting/collections/miningstructures-element-assl.md)|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [CacheMode](../../../analysis-services/scripting/properties/cachemode-element-assl.md)、[照合](../../../analysis-services/scripting/properties/collation-element-assl.md)、[列](../../../analysis-services/scripting/collections/columns-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、 [説明](../../../analysis-services/scripting/properties/description-element-assl.md)、 [ErrorConfiguration](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)、<br /><br /> [HoldoutActualSize](../../../analysis-services/scripting/properties/holdoutactualsize-element.md)、<br /><br /> [HoldoutMaxCases](../../../analysis-services/scripting/properties/holdoutmaxcases-element.md)、<br /><br /> [HoldoutMaxPercent](../../../analysis-services/scripting/properties/holdoutmaxpercent-element.md)、<br /><br /> [HoldoutSeed](../../../analysis-services/scripting/properties/holdoutseed-element.md)、<br /><br /> [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、[言語](../../../analysis-services/scripting/properties/language-element-assl.md)、 [LastProcessed](../../../analysis-services/scripting/properties/lastprocessed-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、 [MiningModels](../../../analysis-services/scripting/collections/miningmodels-element-assl.md)、 [MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)、[状態](../../../analysis-services/scripting/properties/state-element-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 マイニング構造は列およびバインドを定義します。 マイニング構造を定義すると、その構造を使用して多数のマイニング モデルを定義できます。 マイニング構造とその構造に格納されている各マイニング モデルは個別に処理できます。  
  
> [!NOTE]  
>  提示のプロパティ、 **HoldoutMaxCases**、 **HoldoutMaxPercent**、 **HoldoutSeed**、および**HoldoutActualSize**で導入されました。[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]. これらのプロパティを使用すると、マイニング構造で、その構造に関連するすべてのマイニング モデルのテスト セットとして機能するパーティションを定義できます。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では、これらのプロパティはサポートされません。 したがって、これらのプロパティを [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] のインスタンスで使用すると、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でエラーが返されます。  
  
## <a name="drillthrough-to-structure-columns"></a>構造列へのドリルスルー  
 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]に新しい権限要素が追加されて、 [MiningStructurePermissions 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md)コレクション。 追加する場合**AllowDrillthrough**両方へのアクセス許可、 [MiningStructurePermissions](../../../analysis-services/scripting/collections/miningstructurepermissions-element-assl.md)と[MiningModelPermission](../../../analysis-services/scripting/objects/miningmodelpermission-element-assl.md)コレクション、ドリルスルーが有効になっているから、マイニング モデル、構造には、このような方法を持つロールのメンバーが**AllowDrillthrough**モデルに対するアクセス許可が、データ マイニング モデルをクエリおよびモデルに含まれていない構造列を返すことができます。  
  
 したがって、機密データまたは個人情報を保護する必要がありますを構築、機密情報をマスクし、付与、するデータ ソース ビュー **AllowDrillthrough**必要な場合にのみ、マイニング構造に対する権限。 詳細については、次を参照してください。 [AllowDrillThrough 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/allowdrillthrough-element-assl.md).  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.MiningStructure>します。  
  
## <a name="see-also"></a>参照  
 [MiningModel 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)   
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)   
 [選択 (&) #40";"DMX"&"#41;](../../../dmx/select-dmx.md)  
  
  

