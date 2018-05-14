---
title: RelationshipEndVisualizationProperties データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd044aa7e40fb54852e3f8c95b383f45a9ab8d26
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="relationshipendvisualizationproperties-data-type-assl"></a>RelationshipEndVisualizationProperties データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  リレーションシップのリレーションシップ End を表すプリミティブ データ型を定義します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<RelationshipEnd>  
   <FolderPosition>...</FolderPosition>  
   <ContextualNameRule>...</ContextualNameRule>  
   <DefaultDetailsPosition>...</DefaultDetailsPosition>  
   <DisplayKeyPosition>...</DisplayKeyPosition>  
   <CommonIdentifierPosition>...</CommonIdentifierPosition>  
   <IsDefaultMeasure>...</IsDefaultMeasure>  
   <IsDefaultImage>...</IsDefaultImage>  
   <SortPropertiesPosition>...</SortPropertiesPosition>  
</RelationshipEnd>  
```  
  
## <a name="data-type-characteristics"></a>データ型の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|基本データ型|なし|  
|派生データ型|なし|  
  
## <a name="data-type-relationships"></a>データ型のリレーションシップ  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[RelationshipEnd](../../../analysis-services/scripting/data-type/relationshipend-data-type-assl.md)|  
|子要素|[FolderPosition](../../../analysis-services/xmla/xml-elements-properties/folderposition-element-xml.md)、 [ContextualNameRule](../../../analysis-services/xmla/xml-elements-properties/contextualnamerule-element-xml.md)、 [DefaultDetailsPosition](../../../analysis-services/xmla/xml-elements-properties/defaultdetailsposition-element-xml.md)、 [DisplayKeyPosition](../../../analysis-services/xmla/xml-elements-properties/displaykeyposition-element-xml.md)、 [CommonIdentifierPosition](../../../analysis-services/xmla/xml-elements-properties/commonidentifierposition-element-xml.md)、 [IsDefaultMeasure](../../../analysis-services/xmla/xml-elements-properties/isdefaultmeasure-element-xml.md)、 [IsDefaultImage](../../../analysis-services/xmla/xml-elements-properties/isdefaultimage-element-xml.md)、 [SortPropertiesPosition](../../../analysis-services/xmla/xml-elements-properties/sortpropertiesposition-element-xml.md)|  
|派生要素||  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.RelationshipEnd>します。  
  
  
