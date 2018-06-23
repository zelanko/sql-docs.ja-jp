---
title: ErrorConfiguration 要素 (ASSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- ErrorConfiguration Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- ErrorConfiguration
helpviewer_keywords:
- ErrorConfiguration element
ms.assetid: e8363ec2-fbbf-48f6-a55d-01793afa759c
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c509fa16348e6f91da1587f5879e651f2362678c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070551"
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
|親要素|[キューブ](cube-element-assl.md)、[ディメンション](dimension-element-assl.md)、 [MeasureGroup](group-element-assl.md)、 [MiningStructure](miningstructure-element-assl.md)、[パーティション](partition-element-assl.md)|  
|子要素|[KeyDuplicate](../properties/keyduplicate-element-assl.md)、 [KeyErrorAction](action-element-assl.md)、 [KeyErrorLimit](../properties/keyerrorlimit-element-assl.md)、 [KeyErrorLimitAction](../properties/keyerrorlimitaction-element-assl.md)、 [KeyErrorLogFile](file-element-assl.md)、 [KeyNotFound](../properties/keynotfound-element-assl.md)、 [NullKeyConvertedToUnknown](../properties/nullkeyconvertedtounknown-element-assl.md)、 [NullKeyNotAllowed](../properties/nullkeynotallowed-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 分析管理オブジェクト (AMO) オブジェクト モデルで対応する要素は<xref:Microsoft.AnalysisServices.ErrorConfiguration>します。  
  
## <a name="see-also"></a>参照  
 [オブジェクト&#40;ASSL&#41;](objects-assl.md)  
  
  