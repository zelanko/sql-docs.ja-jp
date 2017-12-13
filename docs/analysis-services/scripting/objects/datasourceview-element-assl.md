---
title: "DataSourceView 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: DataSourceView Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: DataSourceView
helpviewer_keywords: DataSourceView element
ms.assetid: cda26126-8af2-4519-8237-f4a57976a284
caps.latest.revision: "35"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: df0a09565f975c44a6abde379faffee168977edf
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="datasourceview-element-assl"></a>DataSourceView 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]によって使用されるデータ ソース ビューの定義、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [データベース](../../../analysis-services/scripting/objects/database-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<DataSourceViews>  
   <DataSourceView>  
      <Name>...</Name>  
      <ID>...</ID>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <Description>...</Description>  
      <Annotations>...</Annotations>  
      <DataSourceID>   </DataSourceID>  
      <Schema>...</Schema>  
   </DataSourceView>  
</DataSourceViews>  
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
|親要素|[DataSourceViews](../../../analysis-services/scripting/collections/datasourceviews-element-assl.md)|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、 [DataSourceID](../../../analysis-services/scripting/properties/datasourceid-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、[スキーマ](../../../analysis-services/scripting/properties/schema-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.DataSourceView>します。  
  
## <a name="see-also"></a>参照  
 [Database 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/database-element-assl.md)   
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
