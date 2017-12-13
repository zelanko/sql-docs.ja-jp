---
title: "IncrementalProcessingNotification 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IncrementalProcessingNotification Element
apilocation: http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to: SQL Server 2016 Preview
helpviewer_keywords: IncrementalProcessingNotification element
ms.assetid: bfc9b0a4-4043-4aaf-82d9-67e7f1d1eb81
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 1a766604a7fd9866ff790f03024f7047e23138c4
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="incrementalprocessingnotification-element-assl"></a>IncrementalProcessingNotification 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]情報が含まれています、 [ProactiveCaching](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)増分処理の進行状況を判断するために実行するクエリについて要素。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<IncrementalProcessingNotifications>  
   <IncrementalProcessingNotification xsi:type="IncrementalProcessingNotification">...</IncrementalProcessingNotification>  
</IncrementalProcessingNotifications>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|[IncrementalProcessingNotification](../../../analysis-services/scripting/data-type/incrementalprocessingnotification-data-type-assl.md)|  
|既定値|なし|  
|Cardinality|1-n : 必須要素で、複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[IncrementalProcessingNotifications](../../../analysis-services/scripting/collections/incrementalprocessingnotifications-element-assl.md)|  
|子要素|なし|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.IncrementalProcessingNotification>します。  
  
## <a name="see-also"></a>参照  
 [ProactiveCachingQueryBinding データ型 &#40;です。ASSL &#41;](../../../analysis-services/scripting/data-type/proactivecachingquerybinding-data-type-assl.md)   
 [ProactiveCaching 要素 &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/proactivecaching-element-assl.md)   
 [オブジェクト &#40;です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
