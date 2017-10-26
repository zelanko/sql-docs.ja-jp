---
title: "Session 要素 (XMLA) |Microsoft ドキュメント"
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
- Session Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.session
- http://schemas.microsoft.com/analysisservices/2003/engine#Session
- urn:schemas-microsoft-com:xml-analysis#Session
helpviewer_keywords:
- Session element
ms.assetid: 884ed090-968e-41d3-97e5-6d12787467da
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: aa1f136ee02b73ab792dae7ee7730a3917dace66
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="session-element-xmla"></a>Session 要素 (XMLA)
  インスタンス上の既存の明示的なセッションを識別する、SOAP 要求メッセージの SOAP ヘッダーを使用して[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql} の分析  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <Session  
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
  
|属性|Description|  
|---------------|-----------------|  
|SessionId|必要な**文字列**を使用するセッションを識別する属性。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はグローバル一意識別子 (GUID) を使用してセッションを識別します。|  
  
## <a name="remarks"></a>解説  
 **セッション**ヘッダー要素で明示的に開始された既存のセッションを識別する、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス。 **セッション**要素は、次の種類のメッセージの SOAP ヘッダーの一部。  
  
-   含む SOAP 応答、 [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md) SOAP ヘッダー要素。  
  
-   実行する対象のセッションを識別する SOAP 要求、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)または[Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。  
  
 セッション識別子は、そのセッションが引き続き有効であることを保証するものではありません。 指定されたセッション、**セッション**要素が切れることができます。 たとえば、セッションがタイムアウトになるか、セッションに関連した接続が切断された場合には、セッションが有効期限切れになることがあります。 セッションが有効期限切れになり、有効でなくなった場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はそのセッションを終了して、現在処理中のすべてのトランザクションをロールバックします。 無効なセッション識別子を使用して送信された SOAP メッセージは失敗し、指定されたセッションが見つからないことを示す SOAP エラーが報告されます。  
  
 場合、**セッション**要素が SOAP 要求の一部として送信されない、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスの実行中のセッションを暗黙的に開始する、 **Discover**または**Execute**メソッドを呼び出すと、メソッドの呼び出しが完了したら、そのセッションを終了します。  
  
## <a name="see-also"></a>参照  
 [EndSession 要素 & #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [管理接続およびセッション (&) #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [ヘッダーと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  

