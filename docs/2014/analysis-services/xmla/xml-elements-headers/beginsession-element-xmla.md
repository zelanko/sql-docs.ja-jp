---
title: BeginSession 要素 (XMLA) |Microsoft Docs
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
- BeginSession Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- http://schemas.microsoft.com/analysisservices/2003/engine#BeginSession
- urn:schemas-microsoft-com:xml-analysis#BeginSession
- microsoft.xml.analysis.beginsession
helpviewer_keywords:
- BeginSession element
ms.assetid: 49873a97-58d7-42a9-ab7f-e045e2856737
caps.latest.revision: 16
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: cf272ae8221b66f7ac8390fab900d22d6b8aaf87
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37285828"
---
# <a name="beginsession-element-xmla"></a>BeginSession 要素 (XMLA)
  インスタンスで新しいセッションを開始する、SOAP 要求メッセージの SOAP ヘッダーを使用して[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]します。  
  
 **Namespace** urn: スキーマ-microsoft-'http://www.w3.org/2001/xmlschema'-分析  
  
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
  
## <a name="remarks"></a>コメント  
 `BeginSession` ヘッダー要素は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスに送信される SOAP 要求の一部分で、インスタンス上で新しいセッションを明示的に開始します。 SOAP 応答によって返される SOAP ヘッダーが含まれています、[セッション](session-element-xmla.md)新しいセッションを識別する要素。 この新しいセッション識別子は保存され、後続の SOAP 要求内で `Session` ヘッダー要素を使用して送信されます。  
  
 `BeginSession` ヘッダー要素が送信されない場合、セッションは明示的に開始されません。 セッションが明示的に開始されない場合、そのセッション上のトランザクションを管理することはできません。 つまり、for Analysis (XMLA) コマンドを次の XML を使用することはできません: [BeginTransaction](../xml-elements-commands/begintransaction-element-xmla.md)、 [CommitTransaction](../xml-elements-commands/committransaction-element-xmla.md)、および[RollbackTransaction](../xml-elements-commands/rollbacktransaction-element-xmla.md)します。 暗黙的に開始されたセッションで実行されるすべての XMLA メソッドおよびコマンドは、アトミックなトランザクションと見なされます。  
  
## <a name="see-also"></a>参照  
 [EndSession 要素&#40;XMLA&#41;](endsession-element-xmla.md)   
 [Session 要素&#40;XMLA&#41;](session-element-xmla.md)   
 [接続およびセッション管理&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [ヘッダー &#40;XMLA&#41;](xml-elements-headers.md)  
  
  
