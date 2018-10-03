---
title: DataSourceID 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DataSourceID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DataSourceID
helpviewer_keywords:
- DataSourceID element
ms.assetid: 2d71ba53-1684-4da0-8da4-fb75033c971b
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 5d7b2bbf4a3acf952e665d9d5c1acde85905e647
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48201562"
---
# <a name="datasourceid-element-assl"></a>DataSourceID 要素 (ASSL)
  識別、 [DataSource](../objects/datasource-element-assl.md)親要素に関連付けられた要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeBinding> <!-- or one of the elements listed below in the Element Relationships table -->  
   ...  
   <DataSourceID>...</DataSourceID>  
   ...  
</CubeBinding>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|コンテキストに応じる|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeBinding](../data-type/cubebinding-data-type-out-of-line-assl.md)、 [CubeDimensionBinding](../data-type/binding-data-type-assl.md)、 [DimensionBinding](../data-type/dimensionbinding-data-type-assl.md)、 [MeasureGroupBinding](../data-type/measuregroupbinding-data-type-assl.md)、 [QueryBinding](../data-type/querybinding-data-type-assl.md)、[DataSourceView](../objects/datasourceview-element-assl.md)、 [TableBinding](../data-type/tablebinding-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>Remarks  
 分析管理オブジェクト (AMO) オブジェクト モデルで `DataSourceID` の親に対応する要素は、<xref:Microsoft.AnalysisServices.CubeDimensionBinding>、<xref:Microsoft.AnalysisServices.DimensionBinding>、<xref:Microsoft.AnalysisServices.MeasureGroupBinding>、<xref:Microsoft.AnalysisServices.QueryBinding>、<xref:Microsoft.AnalysisServices.DataSourceView>、および <xref:Microsoft.AnalysisServices.TableBinding> です。  
  
## <a name="see-also"></a>関連項目  
 [ID 要素&#40;ASSL&#41;](id-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
