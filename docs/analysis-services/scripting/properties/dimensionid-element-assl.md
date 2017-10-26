---
title: "DimensionID 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DimensionID Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- DimensionID
helpviewer_keywords:
- DimensionID element
ms.assetid: 00262781-4216-4a19-8bdc-d46647f42165
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9d0171e6ddcbd67e61ea5255656218f9f0c57994
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="dimensionid-element-assl"></a>DimensionID 要素 (ASSL)
  ディメンションの識別子 (ID) を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimension> <!-- or DimensionBinding, DimensionAttributeBinding -- >  
   ...  
   <DimensionID>...</DimensionID>  
      ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|文字列|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeDimension](../../../analysis-services/scripting/data-type/cubedimension-data-type-assl.md)、 [DimensionBinding](../../../analysis-services/scripting/data-type/dimensionbinding-data-type-assl.md)、 [DimensionAttributeBinding](../../../analysis-services/scripting/data-type/dimensionattributebinding-data-type-out-of-line-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 親に対応する要素**DimensionID**分析管理オブジェクト (AMO) オブジェクト モデルには<xref:Microsoft.AnalysisServices.CubeDimension>と<xref:Microsoft.AnalysisServices.DimensionBinding>です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

