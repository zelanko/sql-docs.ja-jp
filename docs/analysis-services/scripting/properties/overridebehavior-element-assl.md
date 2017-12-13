---
title: "OverrideBehavior 要素 (ASSL) |Microsoft ドキュメント"
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
apiname: OverrideBehavior Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: OverrideBehavior element
ms.assetid: 6a5b361a-6061-4b73-b1a7-1237fb77606c
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 4f917a5ee24e47cf3989bd2b65d6e968774db637
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="overridebehavior-element-assl"></a>OverrideBehavior 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]記述されるリレーションシップのオーバーライド動作を示す、 [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <OverrideBehavior>...</OverrideBehavior>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*厳密な*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 **OverrideBehavior**要素は、関連する属性の位置付けのしくみ、属性の位置付けを決定します。  
  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*厳密な*|AttributeRelationship 要素で記述されるリレーションシップの上書き動作を示します。 一方の属性での配置がもう一方の配置にどのように影響するかを指定します。|  
|*なし*|影響しません。|  
  
 許可される値に対応する列挙**OverrideBehavior**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.OverrideBehavior>します。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [プロパティ &#40;です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  
