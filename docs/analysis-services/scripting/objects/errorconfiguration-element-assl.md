---
title: "ErrorConfiguration 要素 (ASSL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ErrorConfiguration Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- ErrorConfiguration
helpviewer_keywords:
- ErrorConfiguration element
ms.assetid: e8363ec2-fbbf-48f6-a55d-01793afa759c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d70307b772b3220752754c63ed2b02afcbd5d126
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="errorconfiguration-element-assl"></a>ErrorConfiguration 要素 (ASSL)
  親要素が処理されるときに発生する可能性があるエラーを処理するための設定を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Cube> <!-- or Dimension, MeasureGroup, MiningStructure, Partition -->  
   ...  
   <ErrorConfiguration>  
      <KeyErrorLimit>...</KeyErrorLimit>  
      <KeyErrorLogFile>...</KeyErrorLogFile>  
      <KeyErrorAction>...</KeyErrorAction>  
      <KeyErrorLimitAction>...</KeyErrorLimitAction>  
      <KeyNotFound>...</KeyNotFound>  
      <KeyDuplicate>...</KeyDuplicate>  
      <NullKeyConvertedToUnknown>...</NullKeyConvertedToUnknown>  
      <NullKeyNotAllowed>...<NullKeyNotAllowed>  
   </ErrorConfiguration>  
   ...  
</Cube >  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|[キューブ](../../../analysis-services/scripting/objects/cube-element-assl.md)、[ディメンション](../../../analysis-services/scripting/objects/dimension-element-assl.md)、 [MeasureGroup](../../../analysis-services/scripting/objects/measuregroup-element-assl.md)、 [MiningStructure](../../../analysis-services/scripting/objects/miningstructure-element-assl.md)、[パーティション](../../../analysis-services/scripting/objects/partition-element-assl.md)|  
|子要素|[KeyDuplicate](../../../analysis-services/scripting/properties/keyduplicate-element-assl.md)、 [KeyErrorAction](../../../analysis-services/scripting/properties/keyerroraction-element-assl.md)、 [KeyErrorLimit](../../../analysis-services/scripting/properties/keyerrorlimit-element-assl.md)、 [KeyErrorLimitAction](../../../analysis-services/scripting/properties/keyerrorlimitaction-element-assl.md)、 [KeyErrorLogFile](../../../analysis-services/scripting/properties/keyerrorlogfile-element-assl.md)、 [KeyNotFound](../../../analysis-services/scripting/properties/keynotfound-element-assl.md)、 [NullKeyConvertedToUnknown](../../../analysis-services/scripting/properties/nullkeyconvertedtounknown-element-assl.md)、 [NullKeyNotAllowed](../../../analysis-services/scripting/properties/nullkeynotallowed-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ErrorConfiguration>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト & #40 です。ASSL &#41;](../../../analysis-services/scripting/objects/objects-assl.md)  
  
  

