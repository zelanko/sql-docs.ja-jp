---
title: HierarchyUniqueNameStyle 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- HierarchyUniqueNameStyle Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
helpviewer_keywords:
- HierarchyUniqueNameStyle element
ms.assetid: 2ac57825-e9e5-4ec4-9856-fa2326d2c43f
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 04776eb3c9f20e0fa8c870621020c466ba625826
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196872"
---
# <a name="hierarchyuniquenamestyle-element-assl"></a>HierarchyUniqueNameStyle 要素 (ASSL)
  一意の名前が決定内に含まれる階層に対して生成される、 [CubeDimension](../data-type/dimension-data-type-assl.md)します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<CubeDimension>  
   ...  
   <HierarchyUniqueNameStyle>...</HierarchyUniqueNameStyle>  
   ...  
</CubeDimension>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String (列挙型)|  
|既定値|*IncludeDimensionName*|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeDimension](../data-type/dimension-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 この要素の値は、次の表のいずれかの文字列に制限されます。  
  
|値|説明|  
|-----------|-----------------|  
|*IncludeDimensionName*|ディメンションの名前が、階層の名前の一部として含まれます。|  
|*ExcludeDimensionName*|ディメンションの名前が、階層の名前の一部として含まれません。|  
  
 親に対応する要素`HierarchyUniqueNameStyle`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.CubeDimension>します。  
  
## <a name="see-also"></a>参照  
 [キューブ要素&#40;ASSL&#41;](../objects/cube-element-assl.md)   
 [ディメンション要素&#40;ASSL&#41;](../objects/dimension-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
