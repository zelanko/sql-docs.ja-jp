---
title: "ScalarMiningStructureColumn データ型 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: ScalarMiningStructureColumn Data Type
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: ScalarMiningStructureColumn
helpviewer_keywords: ScalarMiningStructureColumn data type
ms.assetid: 8f4afc15-601c-4189-bc45-f5a216aed879
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 78a0a879953a45ed9246a744df19c6e9820f56ca
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="scalarminingstructurecolumn-data-type-assl"></a>ScalarMiningStructureColumn データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]表す派生データ型を定義、 [MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)要素に関連付けられている入れ子になったテーブルではなく、スカラー値を含む、 [TableMiningStructureColumn](../../../analysis-services/scripting/data-type/tableminingstructurecolumn-data-type-assl.md)要素入れ子になったテーブルが含まれています。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ScalarMiningStructureColumn>  
   <!-- The following elements extend MiningStructureColumn -->  
   <IsKey>...</IsKey>  
   <Source>...</Source>  
   <Distribution>...</Distribution>  
   <ModelingFlags>...</ModelingFlags>  
   <Content>...</Content>  
   <ClassifiedColumnID>...</<ClassifiedColumnI  
   <DiscretizationMethod>...</DiscretizationMethod>  
   <DiscretizationBucketCount>...</DiscretizationBucketCount>  
   <KeyColumns>...</KeyColumns>  
   <NameColumn>...</NameColumn>  
   <Translations>...</Translations>  
</ScalarMiningStructureColumn>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|Description|  
|--------------------|-----------------|  
|基本データ型|[MiningStructureColumn](../../../analysis-services/scripting/data-type/miningstructurecolumn-data-type-assl.md)|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[ClassifiedColumnID](../../../analysis-services/scripting/properties/classifiedcolumnid-element-assl.md)、[コンテンツ](../../../analysis-services/scripting/properties/content-element-assl.md)、 [DiscretizationBucketCount](../../../analysis-services/scripting/properties/discretizationbucketcount-element-assl.md)、 [DiscretizationMethod](../../../analysis-services/scripting/properties/discretizationmethod-element-assl.md)、[配布](../../../analysis-services/scripting/properties/distribution-element-assl.md)、 [IsKey](../../../analysis-services/scripting/properties/iskey-element-assl.md)、 [KeyColumns](../../../analysis-services/scripting/collections/keycolumns-element-assl.md)、 [ModelingFlags](../../../analysis-services/scripting/collections/modelingflags-element-assl.md)、 [NameColumn](../../../analysis-services/scripting/objects/namecolumn-element-assl.md)、[ソース](../../../analysis-services/scripting/properties/source-element-binding-assl.md)、[翻訳](../../../analysis-services/scripting/collections/translations-element-assl.md)|  
|派生要素|[列](../../../analysis-services/scripting/objects/column-element-assl.md)([列](../../../analysis-services/scripting/collections/columns-element-assl.md)のコレクション[MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md))|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ScalarMiningStructureColumn>します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services スクリプト言語の XML データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
