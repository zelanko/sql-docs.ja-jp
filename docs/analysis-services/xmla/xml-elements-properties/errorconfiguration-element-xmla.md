---
title: ErrorConfiguration 要素 (XMLA) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ErrorConfiguration Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#ErrorConfiguration
- urn:schemas-microsoft-com:xml-analysis#ErrorConfiguration
- microsoft.xml.analysis.errorconfiguration
helpviewer_keywords:
- ErrorConfiguration element
ms.assetid: 5e350f5f-3a14-49b4-80c0-208c61f336d5
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 191b33cd011d461b27c431833404560493584f39
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="errorconfiguration-element-xmla"></a>ErrorConfiguration 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  中に発生したエラーの処理の設定を指定、[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)または[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)操作します。  
  
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
|親要素|[バッチ](../../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)、[プロセス](../../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)|  
|子要素|[KeyDuplicate](../../../analysis-services/scripting/properties/keyduplicate-element-assl.md)、 [KeyErrorAction](../../../analysis-services/scripting/properties/keyerroraction-element-assl.md)、 [KeyErrorLimit](../../../analysis-services/scripting/properties/keyerrorlimit-element-assl.md)、 [KeyErrorLimitAction](../../../analysis-services/scripting/properties/keyerrorlimitaction-element-assl.md)、 [KeyErrorLogFile](../../../analysis-services/scripting/properties/keyerrorlogfile-element-assl.md)、 [KeyNotFound](../../../analysis-services/scripting/properties/keynotfound-element-assl.md)、 [NullKeyConvertedToUnknown](../../../analysis-services/scripting/properties/nullkeyconvertedtounknown-element-assl.md)、 [NullKeyNotAllowed](../../../analysis-services/scripting/properties/nullkeynotallowed-element-assl.md)|  
  
## <a name="remarks"></a>解説  
 この要素の構造が同一の構造に、 **ErrorConfiguration** Analysis Services スクリプト言語 (ASSL) 要素です。 詳細については、 **ErrorConfiguration**要素を参照してください[ErrorConfiguration 要素&#40;ASSL&#41;](../../../analysis-services/scripting/objects/errorconfiguration-element-assl.md)です。  
  
## <a name="see-also"></a>参照  
 [プロパティ & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-properties/xml-elements-properties.md)  
  
  
