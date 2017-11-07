---
title: "AggregationDesignAttribute データ型 (ASSL) |Microsoft ドキュメント"
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
- AggregationDesignAttribute Data Type
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- AggregationDesignAttribute
helpviewer_keywords:
- AggregationDesignAttribute data type
ms.assetid: 03d29d76-e4bd-4035-92cc-35149d83fbf9
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 98e6e6fa25ece247ab5ec1a84fc7ca0f61871d34
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="aggregationdesignattribute-data-type-assl"></a>AggregationDesignAttribute データ型 (ASSL)
  属性の間の関連付けを表すプリミティブ データ型を定義し、 [AggregationDesignDimension](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AggregationDesignAttribute>  
   <AttributeID>...</AttributeID>  
      <EstimatedCount>...</EstimatedCount>  
</AggregationDesignAttribute>  
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
|子要素|[AttributeID](../../../analysis-services/scripting/properties/attributeid-element-assl.md)、 [EstimatedCount](../../../analysis-services/scripting/properties/estimatedcount-element-assl.md)|  
|派生要素|[属性](../../../analysis-services/scripting/objects/attribute-element-assl.md)([属性](../../../analysis-services/scripting/collections/attributes-element-assl.md)のコレクション[AggregationDesignDimension](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md))|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.AggregationDesignAttribute>します。  
  
## <a name="see-also"></a>参照  
 [AggregationDesignDimension データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL &#41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  

