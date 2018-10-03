---
title: StopTime 要素 (ASSL) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- StopTime Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- StopTime
helpviewer_keywords:
- StopTime element
ms.assetid: 6f863d53-033b-46e0-9837-e891e739b4b0
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 0970bae601d7012b01966163b84f084df4edcdfb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48108892"
---
# <a name="stoptime-element-assl"></a>StopTime 要素 (ASSL)
  日付と時刻を指定します、[トレース](../objects/trace-element-assl.md)要素が停止する必要があります。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Trace>  
   ...  
   <StopTime>...</StopTime>  
   ...  
</Trace>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|DateTime|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[トレース](../objects/trace-element-assl.md)|  
|子要素|なし|  
  
 親に対応する要素`StopTime`分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Trace>します。  
  
## <a name="see-also"></a>参照  
 [要素をトレース&#40;ASSL&#41;](../collections/traces-element-assl.md)   
 [プロパティ&#40;ASSL&#41;](properties-assl.md)  
  
  
