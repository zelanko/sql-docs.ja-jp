---
title: Goal 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Goal Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- Goal
helpviewer_keywords:
- Goal element
ms.assetid: 75fa5b57-418e-43ad-8704-764e4f0a40cf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fe7ff6a2623db0c0f6b1cb5a3d1c09010a984e72
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48117602"
---
# <a name="goal-element-assl"></a>Goal 要素 (ASSL)
  目標を識別、 [Kpi](../objects/kpi-element-assl.md)要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Kpi>  
   ...  
   <Goal>...</Goal>  
   ...  
</Kpi>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|String|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[Kpi](../objects/kpi-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>コメント  
 `Goal` 要素には多次元式 (MDX) が含まれています。  
  
 親に対応する要素`Goal`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Kpi>します。  
  
## <a name="see-also"></a>参照  
 [Status 要素&#40;ASSL&#41;](status-element-assl.md)   
 [要素の傾向&#40;ASSL&#41;](trend-element-assl.md)   
 [要素の値&#40;ASSL&#41;](value-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
