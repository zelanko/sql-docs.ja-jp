---
title: CreatedTimestamp 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- CreatedTimestamp Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- CreatedTimestamp
helpviewer_keywords:
- CreatedTimestamp element
ms.assetid: 35f5dd33-ea82-4be3-a117-69136aa9d1a4
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: e13b032b34ee63a7c7a939d7ad17b8ceb1786739
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48191022"
---
# <a name="createdtimestamp-element-assl"></a>CreatedTimestamp 要素 (ASSL)
  親要素の読み取り専用の作成タイムスタンプを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Assembly> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <CreatedTimestamp>...</CreatedTimestamp>  
   ...  
</Assembly>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|DateTime|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[アセンブリ](../objects/assembly-element-assl.md)、[キューブ](../objects/cube-element-assl.md)、[データベース](../objects/database-element-assl.md)、 [DataSource](../objects/datasource-element-assl.md)、 [DataSourceView](../objects/datasourceview-element-assl.md)、[ディメンション](../objects/dimension-element-assl.md)、 [MdxScript](../objects/mdxscript-element-assl.md)、 [MeasureGroup](../objects/group-element-assl.md)、 [MiningModel](../objects/miningmodel-element-assl.md)、 [MiningStructure](../objects/miningstructure-element-assl.md)、[パーティション](../objects/partition-element-assl.md)、[権限](../data-type/permission-data-type-assl.md)、[パースペクティブ](../objects/perspective-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>Remarks  
 `CreatedTimestamp` 要素には、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] の特定のインスタンスでオブジェクトが作成された日時を表す、読み取り専用の `DateTime` 値が含まれています。 この要素の値を空にすることはできません。  
  
 親に対応する要素`CreatedTimestamp`分析管理オブジェクト (AMO) オブジェクト モデルは、 <xref:Microsoft.AnalysisServices.Assembly>、 <xref:Microsoft.AnalysisServices.Cube>、 <xref:Microsoft.AnalysisServices.Database>、 <xref:Microsoft.AnalysisServices.DataSource>、 <xref:Microsoft.AnalysisServices.DataSourceView>、 <xref:Microsoft.AnalysisServices.Dimension>、 <xref:Microsoft.AnalysisServices.MdxScript>、 <xref:Microsoft.AnalysisServices.MeasureGroup>、 <xref:Microsoft.AnalysisServices.MiningModel>、 <xref:Microsoft.AnalysisServices.MiningStructure>、 <xref:Microsoft.AnalysisServices.Partition>、 <xref:Microsoft.AnalysisServices.Permission>、および<xref:Microsoft.AnalysisServices.Perspective>します。  
  
## <a name="see-also"></a>関連項目  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
