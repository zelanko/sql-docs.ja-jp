---
title: "ExecuteResponse 要素 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- ExecuteResponse Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- urn:schemas-microsoft-com:xml-analysis#ExecuteResponse
- http://schemas.microsoft.com/analysisservices/2003/engine#ExecuteResponse
- microsoft.xml.analysis.executeresponse
helpviewer_keywords:
- ExecuteResponse element
ms.assetid: 6edb1b82-da4c-4cd9-9385-bea04032f0eb
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d90ec4cac02bf3429603d095cb91c3bef77cc00d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="xml-elements---objects---executeresponse"></a>XML 要素のオブジェクトの ExecuteResponse
  インスタンスによって返される情報を含む[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]への応答、 [Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドの呼び出しです。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql} の分析  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<ExecuteResponse>  
   <return>  
</ExecuteResponse>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|1-1 : 必須要素で、1 回だけ出現可能です|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[戻り値](../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)|  
  
## <a name="remarks"></a>解説  
 **ExecuteResponse**要素は最上位の要素の SOAP 応答の本体、 **Execute**メソッドです。  
  
## <a name="see-also"></a>参照  
 [DiscoverResponse 要素 & #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-objects-discoverresponse.md)   
 [オブジェクト & #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-objects.md)  
  
  
