---
title: EndSession 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- EndSession Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#EndSession
- urn:schemas-microsoft-com:xml-analysis#EndSession
- microsoft.xml.analysis.endsession
helpviewer_keywords:
- EndSession element
ms.assetid: e64f1da4-5c83-40a2-b15e-837f5451bafa
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 806b1dea9aeb9a4598b9516f8e7a953962307e65
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48096902"
---
# <a name="endsession-element-xmla"></a>EndSession 要素 (XMLA)
  インスタンス上の既存のセッションを終了する、SOAP 要求メッセージの SOAP ヘッダーを使用[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
 **Namespace** urn: スキーマ-microsoft-'http://www.w3.org/2001/xmlschema'-分析  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <EndSession  
         xmlns="urn:schemas-microsoft-com:xml-analysis"  
         SessionId="string" />  
      ...  
   </soap:Header>  
   <soap:Body>  
      ...  
   </soap:Body>  
</soap:Envelope>  
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
|親要素|なし|  
|子要素|なし|  
  
## <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|SessionId|終了するセッションを識別する、必須で `String` 型の属性。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はグローバル一意識別子 (GUID) を使用してセッションを識別します。|  
  
## <a name="remarks"></a>コメント  
 `EndSession` ヘッダー要素は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上で明示的に開始された既存のセッションに対して送信される SOAP 要求の一部分です。 送信された `EndSession` ヘッダー要素に含まれるセッション ID が無効になった場合、セッションが見つからないことを示す SOAP エラーが返されます。  
  
## <a name="see-also"></a>参照  
 [BeginSession 要素&#40;XMLA&#41;](session-element-xmla.md)   
 [Session 要素&#40;XMLA&#41;](session-element-xmla.md)   
 [接続およびセッション管理&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [ヘッダー &#40;XMLA&#41;](xml-elements-headers.md)  
  
  
