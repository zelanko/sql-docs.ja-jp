---
title: BeginSession 要素 (XMLA) |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3f369a963c287fd2bf1c2dc82a51bb285088c8b1
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="beginsession-element-xmla"></a>BeginSession 要素 (XMLA)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../../includes/ssas-appliesto-sqlas-aas.md)]
  インスタンスで新しいセッションを開始する SOAP 要求メッセージの SOAP ヘッダーを使用して[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]です。  
  
 **Namespace** urn: スキーマ-microsoft-{urn:schemas-microsoft-com:xml-sql} の分析  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <BeginSession  
         xmlns="urn:schemas-microsoft-com:xml-analysis" />  
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
  
## <a name="remarks"></a>解説  
 **BeginSession**ヘッダー要素に送信される SOAP 要求の一部である、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス、および明示的にインスタンスで新しいセッションを開始します。 SOAP 応答によって返される SOAP ヘッダーが含まれています、[セッション](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)新しいセッションを識別する要素。 この新しいセッション識別子は保存されを使用して後続の SOAP 要求で送信された、**セッション**ヘッダー要素。  
  
 場合、 **BeginSession**ヘッダー要素は送信されず、セッションが明示的に開始されていません。 セッションが明示的に開始されない場合、そのセッション上のトランザクションを管理することはできません。 つまり、Analysis (XMLA) コマンドを次の XML を使用することはできません: [BeginTransaction](../../../analysis-services/xmla/xml-elements-commands/begintransaction-element-xmla.md)、 [CommitTransaction](../../../analysis-services/xmla/xml-elements-commands/committransaction-element-xmla.md)、および[RollbackTransaction](../../../analysis-services/xmla/xml-elements-commands/rollbacktransaction-element-xmla.md)です。 暗黙的に開始されたセッションで実行されるすべての XMLA メソッドおよびコマンドは、アトミックなトランザクションと見なされます。  
  
## <a name="see-also"></a>参照  
 [EndSession 要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/endsession-element-xmla.md)   
 [Session 要素 & #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/session-element-xmla.md)   
 [管理接続およびセッション (&) #40 です。XMLA & #41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [ヘッダーと #40 です。XMLA & #41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  
