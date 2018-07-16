---
title: ディメンションのデータ型 (ASSL) |Microsoft Docs
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
- Dimension Data Type
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Dimension data type
ms.assetid: 3fe6adc2-5206-44c3-a689-a731705f43ca
caps.latest.revision: 17
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b60c51847900fee89f0baee2d5b04d96dc3c9ad5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37289558"
---
# <a name="dimension-data-type-assl"></a>Dimension データ型 (ASSL)
  データベース ディメンションを表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Dimension>  
   <Name>...</Name>  
   <ID>...</ID>  
   <CreatedTimestamp>...</CreatedTimestamp>  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
   <Description>...</Description>  
   <Source>...</Source>  
   <MiningModelID>...</MiningModelID>  
   <Type>...</Type>  
   <UnknownMember>...</UnknownMember>  
   <MdxMissingMemberMode>...</MdxMissingMemberMode>  
   <ErrorConfiguration>...</ErrorConfiguration>  
   <StorageMode>...</StorageMode>  
   <WriteEnabled>...</WriteEnabled>  
   <ProcessingPriority>...</ProcessingPriority>  
   <LastProcessed>...</LastProcessed>  
   <DimensionPermissions>...</DimensionPermissions>  
   <DependsOnDimensionID>...</DependsOnDimensionID>  
   <Language>...</Language>  
   <Collation>...</Collation>  
   <UnknownMemberName>...</UnknownMemberName>  
   <UnknownMemberTranslations>...</UnknownMemberTranslations>  
   <State>...</State>  
   <ProactiveCaching>...</ProactiveCaching>  
   <ProcessingMode>...</ProcessingMode>  
   <CurrentStorageMode>...</CurrentStorageMode>  
   <Translations>...</Translations>  
   <Attributes>...</Attributes>  
   <AttributeAllMemberName>...</AttributeAllMemberName>  
   <AttributeAllMemberTranslations>...</AttributeAllMemberTranslations>  
   <Hierarchies>...</Hierarchies>  
   <Relationships>...</Annotations>  
   <Annotations>...</Annotations>  
</Dimension>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[Annotations](../collections/annotations-element-assl.md)、[AttributeAllMemberName](../properties/name-element-assl.md)、[AttributeAllMemberTranslations](../collections/translations-element-assl.md)、[Attributes](../collections/attributes-element-assl.md)、[Collation](../properties/collation-element-assl.md)、[CreatedTimestamp](../properties/createdtimestamp-element-assl.md)、[CurrentStorageMode](../properties/storagemode-element-assl.md)、[DependsOnDimensionID](../properties/id-element-assl.md)、[Description](../properties/description-element-assl.md)、[DimensionPermissions](../collections/dimensionpermissions-element-assl.md)、[ErrorConfiguration](../objects/errorconfiguration-element-assl.md)、[Hierarchies](../collections/hierarchies-element-assl.md)、[ID](../properties/id-element-assl.md)、[Language](../properties/language-element-assl.md)、[LastProcessed](../properties/lastprocessed-element-assl.md)、[LastSchemaUpdate](../properties/lastschemaupdate-element-assl.md)、[MdxMissingMemberMode](../properties/mdxmissingmembermode-element-assl.md)、[MiningModelID](../properties/miningmodelid-element-assl.md)、[Name](../properties/name-element-assl.md)、[ProactiveCaching](../objects/proactivecaching-element-assl.md)、[ProcessingMode](../properties/processingmode-element-assl.md)、[ProcessingPriority](../properties/processingpriority-element-assl.md)、[Relationships](../collections/relationships-element-assl.md)、[Source](../properties/source-element-binding-assl.md)、[State](../properties/state-element-assl.md)、[StorageMode](../properties/storagemode-element-assl.md)、[Translations](../collections/translations-element-assl.md)、[Type](../properties/type-element-dimension-assl.md)、[UnknownMember](../objects/member-element-assl.md)、[UnknownMemberName](../properties/unknownmembername-element-assl.md)、[UnknownMemberTranslations](../collections/unknownmembertranslations-element-assl.md)、[WriteEnabled](../properties/enabled-element-assl.md)|  
|派生要素|[Dimension](../objects/dimension-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 DeploymentMode の値が 1 (SharePoint) および 2 (Tabular) の場合、このデータ型には次の検証が適用されます。  
  
-   *WriteEnabled*に子要素を設定する必要があります `False`  
  
-   *UnknownMember*に子要素を設定する必要があります `AutomaticNull`  
  
-   一意のすべての属性があります*NullProcessing*に設定する子要素 `Error`  
  
 次の子属性は、DeploymentMode の値 1 (SharePoint) および 2 (Tabular) ではサポートされていません。  
  
-   *DimensionPermissions*  
  
-   *MiningModelID*  
  
-   *ProactiveCaching*  
  
 分析管理オブジェクト (AMO) オブジェクト モデル内の対応する要素が<xref:Microsoft.AnalysisServices.Dimension>、 <xref:Microsoft.AnalysisServices.AggregationDimension>、 <xref:Microsoft.AnalysisServices.AggregationDesignDimension>、 <xref:Microsoft.AnalysisServices.CubeDimension>、 <xref:Microsoft.AnalysisServices.MeasureGroupDimension>、および<xref:Microsoft.AnalysisServices.PerspectiveDimension>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型&#40;ASSL&#41;](analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
