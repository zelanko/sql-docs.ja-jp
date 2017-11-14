---
title: "StopTime 要素 (ASSL) |Microsoft ドキュメント"
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
- StopTime Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- StopTime
helpviewer_keywords:
- StopTime element
ms.assetid: 6f863d53-033b-46e0-9837-e891e739b4b0
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9ccd9202a73cc68a98a43baf29d3b36ecfdc58f5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="stoptime-element-assl"></a>StopTime 要素 (ASSL)
  日付と時刻を指定、[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)要素を停止する必要があります。  
  
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
|親要素|[トレース](../../../analysis-services/scripting/objects/trace-element-assl.md)|  
|子要素|なし|  
  
 親に対応する要素**StopTime**分析管理オブジェクト (AMO) オブジェクト モデルは<xref:Microsoft.AnalysisServices.Trace>します。  
  
## <a name="see-also"></a>参照  
 [Traces 要素 & #40 です。ASSL &#41;](../../../analysis-services/scripting/collections/traces-element-assl.md)   
 [プロパティ & #40 です。ASSL &#41;](../../../analysis-services/scripting/properties/properties-assl.md)  
  
  

