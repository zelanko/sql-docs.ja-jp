---
title: Cardinality 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- Cardinality Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- Cardinality element
ms.assetid: 60ac8a26-7c8b-4011-9b9b-a29863779428
caps.latest.revision: 15
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7446923efc15a2fe05f3e8bf8c86a2e9f429a2c1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37325082"
---
# <a name="cardinality-element-assl"></a>Cardinality 要素 (ASSL)
  記述されるリレーションシップのカーディナリティを示します、 [AttributeRelationship](../objects/attributerelationship-element-assl.md)または[RegularMeasureGroupDimension](../data-type/dimension-data-type-assl.md)します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<AttributeRelationship> <!-- or RegularMeasureGroupDimension -->  
   ...  
   <Cardinality>...</Cardinality>  
   ...  
</AttributeRelationship>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*多く*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[AttributeRelationship](../objects/attributerelationship-element-assl.md)、 [RegularMeasureGroupDimension](../data-type/dimension-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*多く*|多対一のリレーションシップ|  
|*1 つ*|一対一のリレーションシップ|  
  
 許容された値に対応する列挙`Cardinality`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Cardinality>します。  
  
## <a name="see-also"></a>参照  
 [属性と属性階層](../../multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
