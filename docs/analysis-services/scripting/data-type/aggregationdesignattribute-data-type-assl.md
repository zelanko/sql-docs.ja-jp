---
title: AggregationDesignAttribute データ型 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 686d8efedaa95d6349d52d3ffbf5231111b930eb
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="aggregationdesignattribute-data-type-assl"></a>AggregationDesignAttribute データ型 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
 [AggregationDesignDimension データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/aggregationdesigndimension-data-type-assl.md)   
 [Analysis Services スクリプト言語の XML データ型 & #40 です。ASSL & #41;](../../../analysis-services/scripting/data-type/analysis-services-scripting-language-xml-data-types-assl.md)  
  
  
