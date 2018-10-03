---
title: RelationshipType 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- RelationshipType Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- RelationshipType
helpviewer_keywords:
- RelationshipType element
ms.assetid: 72e1ab0e-a95d-4ebe-857d-21de1bf9fe03
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 3cc0ca0577b63e655c42c9b8bdcb19b1a67cb538
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096712"
---
# <a name="relationshiptype-element-assl"></a>RelationshipType 要素 (ASSL)
  示すかどうかのメンバー リレーションシップを[AttributeRelationship](../objects/attributerelationship-element-assl.md)変更できます。  
  
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
|親要素|[AttributeRelationship](../objects/attributerelationship-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表の一覧に示す文字列のいずれかに限定されています。  
  
|値|説明|  
|-----------|-----------------|  
|*柔軟性に欠ける*|属性と関連属性の間のメンバー リレーションシップは変更できません。|  
|*柔軟です*|属性と関連属性の間のメンバー リレーションシップは変更できます。|  
  
 たとえば場合、`ZipCode`から 1 つを変更することはできません`City`間のリレーションシップを`ZipCode`に`City`としてマークされて*固定*します。  
  
 許容された値に対応する列挙体`RelationshipType`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.RelationshipType>します。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
