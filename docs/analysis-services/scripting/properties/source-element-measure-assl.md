---
title: "Source 要素 (Measure) (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
apiname: Source Element (Measure)
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
f1_keywords: Source
helpviewer_keywords: Source element
ms.assetid: 9bae7ba4-3065-4623-b3e0-d54cebea7503
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1d90b3f474780112dfa8fb67b3597cf64a9c1cf0
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="source-element-measure-assl"></a>Source 要素 (Measure) (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]値を含むソースの詳細を含む、[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Measure>  
      ...  
   <Source xsi:type="DataItem">...</Source>  
      ...  
</Measure>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[DataItem](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メジャー](../../../analysis-services/scripting/objects/measure-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **ソース**の**DataItem**、として機能する、**ソース**の**メジャー**の種類にできる[RowBinding](../../../analysis-services/scripting/data-type/rowbinding-data-type-assl.md)、 [ColumnBinding](../../../analysis-services/scripting/data-type/columnbinding-data-type-assl.md)、 [MeasureBinding](../../../analysis-services/scripting/data-type/measurebinding-data-type-assl.md)、または[CubeDimensionBinding](../../../analysis-services/scripting/data-type/cubedimensionbinding-data-type-assl.md)です。  
  
 詳細については、 **DataItem**の ASSL オブジェクトおよびプロパティのテーブルを含む、型、 **DataItem**を入力しを参照してください[DataItem データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/dataitem-data-type-assl.md).  
  
 親に対応する要素**ソース**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Measure>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
