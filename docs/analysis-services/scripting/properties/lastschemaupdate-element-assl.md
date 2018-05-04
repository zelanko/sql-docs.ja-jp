---
title: LastSchemaUpdate 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- LastSchemaUpdate Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- LastSchemaUpdate
helpviewer_keywords:
- LastSchemaUpdate element
ms.assetid: 0634c105-91cc-4882-87be-97ca29a251a6
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 83ea6689a40438b8a36ea6a1ed69522a5d64e469
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="lastschemaupdate-element-assl"></a>LastSchemaUpdate 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  親要素の読み取り専用のメタデータ更新タイムスタンプを格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Assembly> <!-- or one of the elements that are listed in the Element Relationships table -->  
   ...  
   <LastSchemaUpdate>...</LastSchemaUpdate>  
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
|親要素|[アセンブリ](../../../analysis-services/scripting/objects/assembly-element-assl.md)、[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、[データベース](../../../analysis-services/scripting/objects/database-element-assl.md)、[データソース](../../../analysis-services/scripting/objects/datasource-element-assl.md)、 [DataSourceView](../../../analysis-services/scripting/objects/datasourceview-element-assl.md)、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)、 [MdxScript](../../../analysis-services/scripting/objects/mdxscript-element-assl.md)、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)、 [MiningModel](../../../analysis-services/scripting/objects/miningmodel-element-assl.md)、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)、[権限](../../../analysis-services/scripting/data-type/permission-data-type-assl.md)、[パースペクティブ](../../../analysis-services/scripting/objects/perspective-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **LastSchemaUpdate**要素を含む読み取り専用**DateTime**の特定のインスタンスでオブジェクトのメタデータが変更された日時を表す値[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].  
  
 親に対応する要素**LastSchemaUpdate**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.Assembly>、 <xref:Microsoft.AnalysisServices.Cube>、 <xref:Microsoft.AnalysisServices.Database>、 <xref:Microsoft.AnalysisServices.DataSource>、 <xref:Microsoft.AnalysisServices.DataSourceView>、 <xref:Microsoft.AnalysisServices.Dimension>、 <xref:Microsoft.AnalysisServices.MdxScript>、 <xref:Microsoft.AnalysisServices.MeasureGroup>、 <xref:Microsoft.AnalysisServices.MiningModel>、 <xref:Microsoft.AnalysisServices.MiningStructure>、 <xref:Microsoft.AnalysisServices.Partition>、 <xref:Microsoft.AnalysisServices.Permission>、および<xref:Microsoft.AnalysisServices.Perspective>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL & #41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
