---
title: Trace 要素 (ASSL) |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: assl
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 420150dbdf4910683fc78c8c364d2cf0976adfc3
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="trace-element-assl"></a>Trace 要素 (ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  クエリできるトレースを定義します。  
  
## <a name="syntax"></a>構文  
  
```  
  
      Profiler syntax  
<Traces>  
   <Trace>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate>  
      <LogFileName>...</LogFileName>  
      <LogFileAppend>...</LogFileAppend>  
      <LogFileSize>...</LogFileSize>  
      <Audit>...</Audit>  
      <LogFileRollover>...</LogFileRollover>  
      <AutoRestart>...</AutoRestart>  
      <StopTime>...</StopTime>  
      <Filter>...</Filter>  
      <Events>...</Events>  
      <Annotations>...</Annotations>  
   </Trace>  
</Traces>  
```  
  
```  
  
      Extended Events syntax  
<Traces>  
   <Trace>  
      <Name>...</Name>  
      <ID>...</ID>  
      <Description>...</Description>  
      <CreatedTimestamp>...</CreatedTimestamp>  
      <LastSchemaUpdate>...</LastSchemaUpdate> 
      <AutoRestart>...</AutoRestart>
      <XEvent>...</XEvent>  
      <Annotations>...</Annotations>  
   </Trace>  
</Traces>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-n : 省略可能な要素で、出現する場合は複数回の出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[トレース](../../../analysis-services/scripting/collections/traces-element-assl.md)|  
|子要素|[注釈](../../../analysis-services/scripting/collections/annotations-element-assl.md)、[監査](../../../analysis-services/scripting/properties/audit-element-assl.md)、 [AutoRestart](../../../analysis-services/scripting/properties/autorestart-element-assl.md)、 [CreatedTimestamp](../../../analysis-services/scripting/properties/createdtimestamp-element-assl.md)、[説明](../../../analysis-services/scripting/properties/description-element-assl.md)、[イベント](../../../analysis-services/scripting/collections/events-element-assl.md)、[フィルター](../../../analysis-services/scripting/properties/filter-element-trace-assl.md)、 [ID](../../../analysis-services/scripting/properties/id-element-assl.md)、 [LastSchemaUpdate](../../../analysis-services/scripting/properties/lastschemaupdate-element-assl.md)、 [LogFileAppend](../../../analysis-services/scripting/properties/logfileappend-element-assl.md)、 [LogFileName](../../../analysis-services/scripting/properties/logfilename-element-assl.md)、 [LogFileRollover](../../../analysis-services/scripting/properties/logfilerollover-element-assl.md)、 [LogFileSize](../../../analysis-services/scripting/properties/logfilesize-element-assl.md)、[名前](../../../analysis-services/scripting/properties/name-element-assl.md)、 [StopTime](../../../analysis-services/scripting/properties/stoptime-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.Trace>します。  
  
## <a name="see-also"></a>参照  
 [Server 要素 & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/server-element-assl.md)   
 [オブジェクト & #40 です。ASSL & #41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  
