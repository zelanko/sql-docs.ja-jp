---
title: RelationshipEndVisualizationProperties データ型 (ASSL) |Microsoft Docs
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
ms.assetid: 11f9a10f-d36c-4faf-b595-3fe969d1935e
caps.latest.revision: 5
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 58348251e9ea00c4f6eebc5fcec067683e49a3a2
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37161273"
---
# <a name="relationshipendvisualizationproperties-data-type-assl"></a>RelationshipEndVisualizationProperties データ型 (ASSL)
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
|親要素|[RelationshipEnd](relationshipend-data-type-assl.md)|  
|子要素|[FolderPosition](../../xmla/xml-elements-properties/folderposition-element-xml.md)、 [ContextualNameRule](../../xmla/xml-elements-properties/contextualnamerule-element-xml.md)、 [DefaultDetailsPosition](../../xmla/xml-elements-properties/defaultdetailsposition-element-xml.md)、 [DisplayKeyPosition](../../xmla/xml-elements-properties/displaykeyposition-element-xml.md)、 [CommonIdentifierPosition](../../xmla/xml-elements-properties/commonidentifierposition-element-xml.md)、 [IsDefaultMeasure](../../xmla/xml-elements-properties/isdefaultmeasure-element-xml.md)、 [IsDefaultImage](../../xmla/xml-elements-properties/isdefaultimage-element-xml.md)、 [SortPropertiesPosition](../../xmla/xml-elements-properties/sortpropertiesposition-element-xml.md)|  
|派生要素||  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.RelationshipEnd>します。  
  
  
