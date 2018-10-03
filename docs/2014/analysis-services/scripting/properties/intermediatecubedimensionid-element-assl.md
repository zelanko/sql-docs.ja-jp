---
title: IntermediateCubeDimensionID 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- IntermediateCubeDimensionID Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- IntermediateCubeDimensionID
helpviewer_keywords:
- IntermediateCubeDimensionID element
ms.assetid: 305c0a91-7bc2-4268-ba94-8f19d8c22ca3
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b95216c83858e343341217a3efa34ab01fa87f70
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48059922"
---
# <a name="intermediatecubedimensionid-element-assl"></a>IntermediateCubeDimensionID 要素 (ASSL)
  参照ディメンションをメジャー グループに関連付けるディメンションの識別子 (ID) を格納します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ReferenceMeasureGroupDimension>  
   ...  
   <IntermediateCubeDimensionID>...</IntermediateCubeDimensionID>  
   ...  
</ReferenceMeasureGroupDimension>  
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
|親要素|[ReferenceMeasureGroupDimension](../data-type/dimension-data-type-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>Remarks  
 親に対応する要素`IntermediateCubeDimensionID`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.ReferenceMeasureGroupDimension>します。  
  
## <a name="see-also"></a>関連項目  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
