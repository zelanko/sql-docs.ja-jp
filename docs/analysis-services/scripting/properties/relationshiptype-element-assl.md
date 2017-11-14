---
title: "RelationshipType 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- RelationshipType Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- RelationshipType
helpviewer_keywords:
- RelationshipType element
ms.assetid: 72e1ab0e-a95d-4ebe-857d-21de1bf9fe03
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2c851069422e2e2f89c9c00decae26a9b872d93d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="relationshiptype-element-assl"></a>RelationshipType 要素 (ASSL)
  示すかどうかのメンバー リレーションシップ、 [AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)変更できます。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeRelationship>  
   ...  
   <RelationshipType>...</RelationshipType>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*柔軟です*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeRelationship](../../../analysis-services/scripting/objects/attributerelationship-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|Description|  
|-----------|-----------------|  
|*固定*|属性と関連属性の間のメンバー リレーションシップは変更できません。|  
|*柔軟です*|属性と関連属性の間のメンバー リレーションシップは変更できます。|  
  
 たとえば場合、 **ZipCode**から 1 つを変更することはできません**市区町村**間のリレーションシップ**郵便番号**に**市区町村**としてマークされて*固定*です。  
  
 許可される値に対応する列挙**RelationshipType**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.RelationshipType>します。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](../../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

