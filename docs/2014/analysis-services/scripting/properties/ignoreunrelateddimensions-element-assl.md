---
title: IgnoreUnrelatedDimensions 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- IgnoreUnrelatedDimensions Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- IgnoreUnrelatedDimensions
helpviewer_keywords:
- IgnoreUnrelatedDimensions element
ms.assetid: c7d7a1cd-a8e0-4ae7-9464-a1d2a55a86ab
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 400a1ef9f55d5696e2bbaeabbdd4a109c7a13587
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48099342"
---
# <a name="ignoreunrelateddimensions-element-assl"></a>IgnoreUnrelatedDimensions 要素 (ASSL)
  メジャー グループに関連付けられていないディメンションのメンバーがクエリに含まれているときに、関連付けられていないディメンションをトップ レベルに強制するかどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<MeasureGroup>  
   ...  
   <IgnoreUnrelatedDimensions>...</IgnoreUnrelatedDimensions>  
   ...  
</MeasureGroup>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|ブール値|  
|既定値|True|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[メジャー グループ](../objects/group-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>Remarks  
 `IgnoreUnrelatedDimensions` が `true` である場合、関連付けられていないディメンションはトップ レベルに強制されます。値が `false` である場合、関連付けられていないディメンションはトップ レベルに強制されません。 このプロパティは、多次元式 (MDX) に似ています[ValidMeasure](/sql/mdx/validmeasure-mdx)関数。  
  
 親に対応する要素`IgnoreUnrelatedDimensions`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.MeasureGroup>します。  
  
## <a name="see-also"></a>関連項目  
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
