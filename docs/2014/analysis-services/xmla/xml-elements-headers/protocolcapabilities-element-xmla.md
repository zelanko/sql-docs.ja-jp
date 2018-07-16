---
title: ProtocolCapabilities 要素 (XMLA) |Microsoft Docs
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
- ProtocolCapabilities Element
api_location:
- http://schemas.microsoft.com/analysisservices/2003/engine
topic_type:
- apiref
f1_keywords:
- microsoft.xml.analysis.protocolcapabilities
- http://schemas.microsoft.com/analysisservices/2003/engine#ProtocolCapabilities
- urn:schemas-microsoft-com:xml-analysis#ProtocolCapabilities
helpviewer_keywords:
- ProtocolCapabilities element
ms.assetid: f923896a-3f32-46a3-9543-388c30b3465d
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c4183d90d07a54cf009daec59ca29ca802f2bf67
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37295432"
---
# <a name="protocolcapabilities-element-xmla"></a>ProtocolCapabilities 要素 (XMLA)
  インスタンス間のプロトコル機能を識別するために、SOAP 要求メッセージの SOAP ヘッダーを使用して[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]とクライアント アプリケーション。  
  
 **Namespace** http://schemas.microsoft.com/analysisservices/2003/engine  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<soap:Envelope xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
   <soap:Header>  
      ...  
      <ProtocolCapabilities xmlns="http://schemas.microsoft.com/analysisservices/2003/engine">  
         <Capability>...</Capability>  
      </ProtocolCapabilities>  
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
|子要素|[機能](../xml-elements-properties/capability-element-xmla.md)|  
  
## <a name="remarks"></a>コメント  
 `ProtocolCapabilities` 要素は、クライアント アプリケーションが [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスとの間でプロトコル機能 (たとえばバイナリ XML や圧縮サポート) を任意の時点でネゴシエートすることを可能にします。 プロトコルのネゴシエーションは以下の手順で行われます。  
  
1.  クライアント アプリケーションを含む SOAP 要求を送信することによってそのプロトコル機能を識別する、 `ProtocolCapabilities` SOAP ヘッダーの一部として要素。  
  
2.  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は SOAP 要求を受信して処理します。  
  
3.  要求されたプロトコル機能と同じものを [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスが保有している場合、インスタンスは SOAP 要求で送られたのと同じ `ProtocolCapabilities` 要素を含む SOAP 応答を送信し、その時点でプロトコルのネゴシエーションが正常に完了します。 そうでない場合、プロトコル機能は正常にネゴシエートされず、インスタンスは SOAP エラーを返します。  
  
 プロトコル機能をどのくらいの時間、クライアント アプリケーションを正常にネゴシエートした後、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンス使用して、特定のプロトコルは、セッションが明示的または暗黙的なのかどうかによって異なります。  
  
-   明示的セッションが 1 つを使用して作成される、 [BeginSession](session-element-xmla.md)ヘッダー要素。 クライアント アプリケーションが新しいまで明示的なセッションでは、ネゴシエートされたプロトコルが使用される`ProtocolCapabilities`要素またはセッションが終了します。  
  
-   暗黙のセッションとは [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスによって作成されるセッションで、SOAP 要求の送信時にクライアント アプリケーションによって明示的に指定されるものではありません。 暗黙のセッションの場合、ネゴシエートされたプロトコルは、SOAP 要求が完了するまでの期間だけ使用されます。  
  
 プロトコル機能を明示的にネゴシエートする必要はありません。 つまり、クライアント アプリケーションに含める必要ありません、 `ProtocolCapabilities` SOAP 要求の一部として要素。 SOAP 要求に `ProtocolCapabilities` 要素が含まれない場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスは SOAP 要求と同じ形式を使用して応答します。  
  
## <a name="see-also"></a>参照  
 [接続およびセッション管理&#40;XMLA&#41;](../../multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [ヘッダー &#40;XMLA&#41;](xml-elements-headers.md)  
  
  
