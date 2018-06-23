---
title: MiningStructure 要素 (ASSL) |Microsoft ドキュメント
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
- MiningStructure Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- MiningStructure
helpviewer_keywords:
- MiningStructure element
ms.assetid: b943cd92-0ed8-4bd8-8fbc-7dab0534aede
caps.latest.revision: 48
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 5298c78f1902ee9a8fb1ed12ecf066092a02d938
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177180"
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
|親要素|[MiningStructures](../collections/miningstructures-element-assl.md)|  
|子要素|[注釈](../collections/annotations-element-assl.md)、 [CacheMode](../properties/cachemode-element-assl.md)、[照合](../properties/collation-element-assl.md)、[列](../collections/columns-element-assl.md)、 [CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、[の説明](../properties/description-element-assl.md)、 [ErrorConfiguration](errorconfiguration-element-assl.md)、<br /><br /> [HoldoutActualSize](../properties/holdoutactualsize-element.md)、<br /><br /> [HoldoutMaxCases](../properties/holdoutmaxcases-element.md)、<br /><br /> [HoldoutMaxPercent](../properties/holdoutmaxpercent-element.md)、<br /><br /> [HoldoutSeed](../properties/holdoutseed-element.md)、<br /><br /> [ID](../properties/id-element-assl.md)、[言語](../properties/language-element-assl.md)、 [LastProcessed](../properties/lastprocessed-element-assl.md)、 [LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、 [MiningModels](../collections/miningmodels-element-assl.md)、 [MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md)、[名前](../properties/name-element-assl.md)、[ソース](../properties/source-element-binding-assl.md)、[状態](../properties/state-element-assl.md)、[翻訳](../collections/translations-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 マイニング構造は列およびバインドを定義します。 マイニング構造を定義すると、その構造を使用して多数のマイニング モデルを定義できます。 マイニング構造とその構造に格納されている各マイニング モデルは個別に処理できます。  
  
> [!NOTE]  
>  提示されたプロパティの `HoldoutMaxCases`、`HoldoutMaxPercent`、`HoldoutSeed`、および `HoldoutActualSize` は、[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] で導入されました。 これらのプロパティを使用すると、マイニング構造で、その構造に関連するすべてのマイニング モデルのテスト セットとして機能するパーティションを定義できます。 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] では、これらのプロパティはサポートされません。 したがって、これらのプロパティを [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] のインスタンスで使用すると、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] でエラーが返されます。  
  
## <a name="drillthrough-to-structure-columns"></a>構造列へのドリルスルー  
 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]に新しい権限要素が追加されて、 [MiningStructurePermissions 要素&#40;ASSL&#41; ](../collections/miningstructurepermissions-element-assl.md)コレクション。 追加する場合`AllowDrillthrough`両方へのアクセス許可、 [MiningStructurePermissions](../collections/miningstructurepermissions-element-assl.md)と[MiningModelPermission](miningmodelpermission-element-assl.md)ように、構造にマイニング モデルからコレクション、ドリルスルーが有効になっています。持つロールのメンバーが`AllowDrillthrough`モデルに対するアクセス許可が、データ マイニング モデルをクエリおよびモデルに含まれていない構造列を返すことができます。  
  
 したがって、機密データまたは個人情報を保護するため、機密情報をマスクするデータ ソース ビューを構築し、マイニング構造に対する `AllowDrillthrough` 権限は必要な場合にのみ許可する必要があります。 詳細については、次を参照してください。 [AllowDrillThrough 要素&#40;ASSL&#41;](../properties/allowdrillthrough-element-assl.md)です。  
  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.MiningStructure>します。  
  
## <a name="see-also"></a>参照  
 [MiningModel 要素&#40;ASSL&#41;](miningmodel-element-assl.md)   
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)   
 [選択&AMP;#40;DMX&AMP;#41;](/sql/dmx/select-dmx)  
  
  
