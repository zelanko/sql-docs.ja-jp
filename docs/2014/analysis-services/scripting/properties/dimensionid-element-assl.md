---
title: DimensionID 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- DimensionID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- DimensionID
helpviewer_keywords:
- DimensionID element
ms.assetid: 00262781-4216-4a19-8bdc-d46647f42165
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a5d18084f7726c200b999d764bab579c9ab9b66d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48126102"
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
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現します|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[CubeDimension](../data-type/dimension-data-type-assl.md)、 [DimensionBinding](../data-type/binding-data-type-assl.md)、 [DimensionAttributeBinding](../data-type/dimensionattributebinding-data-type-out-of-line-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 親に対応する要素`DimensionID`分析管理オブジェクト (AMO) オブジェクト モデルは、<xref:Microsoft.AnalysisServices.CubeDimension>と<xref:Microsoft.AnalysisServices.DimensionBinding>します。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
