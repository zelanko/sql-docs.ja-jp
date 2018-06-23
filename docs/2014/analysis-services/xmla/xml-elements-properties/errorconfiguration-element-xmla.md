---
title: ErrorConfiguration 要素 (XMLA) |Microsoft ドキュメント
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
- http://schemas.microsoft.com/analysisservices/2003/engine#ErrorConfiguration
- urn:schemas-microsoft-com:xml-analysis#ErrorConfiguration
- microsoft.xml.analysis.errorconfiguration
helpviewer_keywords:
- ErrorConfiguration element
ms.assetid: 5e350f5f-3a14-49b4-80c0-208c61f336d5
caps.latest.revision: 13
author: mgblythe
ms.author: mblythe
manager: mblythe
ms.openlocfilehash: 1ce9cf2dc862f187c1a9f9cb9e3403e01ade0cfa
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084392"
---
# <a name="errorconfiguration-element-xmla"></a>ErrorConfiguration 要素 (XMLA)
  中に発生したエラーの処理の設定を指定、[バッチ](../xml-elements-commands/batch-element-xmla.md)または[プロセス](../xml-elements-commands/process-element-xmla.md)操作します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Batch> <!-- or Process -->  
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
</Batch>  
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
|親要素|[バッチ](../xml-elements-commands/batch-element-xmla.md)、[プロセス](../xml-elements-commands/process-element-xmla.md)|  
|子要素|[KeyDuplicate](../../scripting/properties/keyduplicate-element-assl.md)、 [KeyErrorAction](../../scripting/objects/action-element-assl.md)、 [KeyErrorLimit](../../scripting/properties/keyerrorlimit-element-assl.md)、 [KeyErrorLimitAction](../../scripting/properties/keyerrorlimitaction-element-assl.md)、 [KeyErrorLogFile](../../scripting/objects/file-element-assl.md)、 [KeyNotFound](../../scripting/properties/keynotfound-element-assl.md)、 [NullKeyConvertedToUnknown](../../scripting/properties/nullkeyconvertedtounknown-element-assl.md)、 [NullKeyNotAllowed](../../scripting/properties/nullkeynotallowed-element-assl.md)|  
  
## <a name="remarks"></a>コメント  
 この要素の構造は、Analysis Services Scripting Language (ASSL) の `ErrorConfiguration` 要素の構造と同じです。 詳細については、`ErrorConfiguration`要素を参照してください[ErrorConfiguration 要素&#40;ASSL&#41;](../../scripting/objects/errorconfiguration-element-assl.md)です。  
  
## <a name="see-also"></a>参照  
 [プロパティ&#40;XMLA&#41;](xml-elements-properties.md)  
  
  