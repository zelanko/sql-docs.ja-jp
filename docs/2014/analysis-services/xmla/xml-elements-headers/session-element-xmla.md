---
title: Session 要素 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
api_name:
- Session Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.session
- http://schemas.microsoft.com/analysisservices/2003/engine#Session
- urn:schemas-microsoft-com:xml-analysis#Session
helpviewer_keywords:
- Session element
ms.assetid: 884ed090-968e-41d3-97e5-6d12787467da
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: a2f18754a2ef7d44a2a85bb9da78378bc631ecd0
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48080392"
---
# <a name="session-element-xmla"></a>Session 要素 (XMLA)
  インスタンス上の既存の明示的なセッションを識別するために、SOAP 要求メッセージの SOAP ヘッダーを使用して[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
 **Namespace** urn: スキーマ-microsoft-'http://www.w3.org/2001/xmlschema'-分析  
  
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
  
|属性|説明|  
|---------------|-----------------|  
|SessionId|使用されるセッションを識別する、`String` 型の必須の属性。 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はグローバル一意識別子 (GUID) を使用してセッションを識別します。|  
  
## <a name="remarks"></a>コメント  
 `Session` ヘッダー要素は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンス上の、明示的に開始された既存のセッションを識別します。 `Session` 要素は、次の種類のメッセージ内の SOAP ヘッダーに含まれます。  
  
-   含む SOAP 応答を[BeginSession](session-element-xmla.md) SOAP ヘッダー要素。  
  
-   実行するセッションを識別するために SOAP 要求、 [Discover](../xml-elements-methods-discover.md)または[Execute](../xml-elements-methods-execute.md)メソッド。  
  
 セッション識別子は、そのセッションが引き続き有効であることを保証するものではありません。 `Session` 要素で指定されたセッションは有効期限切れになる可能性があります。 たとえば、セッションがタイムアウトになるか、セッションに関連した接続が切断された場合には、セッションが有効期限切れになることがあります。 セッションが有効期限切れになり、有効でなくなった場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] はそのセッションを終了して、現在処理中のすべてのトランザクションをロールバックします。 無効なセッション識別子を使用して送信された SOAP メッセージは失敗し、指定されたセッションが見つからないことを示す SOAP エラーが報告されます。  
  
 `Session` 要素が SOAP 要求の一部分として送信されない場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスは `Discover` または `Execute` メソッド呼び出しの存続期間に対応するセッションを暗黙的に開始し、メソッド呼び出しが完了した時点でそのセッションを終了します。  
  
## <a name="see-also"></a>参照  
 [EndSession 要素&#40;XMLA&#41;](endsession-element-xmla.md)   
 [接続およびセッション管理&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [ヘッダー &#40;XMLA&#41;](xml-elements-headers.md)  
  
  
