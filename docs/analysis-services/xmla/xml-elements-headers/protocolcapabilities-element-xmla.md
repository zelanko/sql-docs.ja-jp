---
title: "ProtocolCapabilities 要素 (XMLA) |Microsoft ドキュメント"
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
- ProtocolCapabilities Element
apilocation:
- http://schemas.microsoft.com/analysisservices/2003/engine
apitype: Schema
applies_to:
- SQL Server 2016 Preview
f1_keywords:
- microsoft.xml.analysis.protocolcapabilities
- http://schemas.microsoft.com/analysisservices/2003/engine#ProtocolCapabilities
- urn:schemas-microsoft-com:xml-analysis#ProtocolCapabilities
helpviewer_keywords:
- ProtocolCapabilities element
ms.assetid: f923896a-3f32-46a3-9543-388c30b3465d
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5d2ff72b1fdc3a3e3a4b09a046933d3ead88fc78
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# ProtocolCapabilities 要素 (XMLA)
  インスタンス間のプロトコル機能を識別する、SOAP 要求メッセージの SOAP ヘッダーを使用[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]とクライアント アプリケーション。  
  
 **Namespace**`http://schemas.microsoft.com/analysisservices/2003/engine`  
  
## 構文  
  
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
  
## 要素の特性  
  
|特性|説明|  
|--------------------|-----------------|  
|データ型と長さ|なし|  
|既定値|なし|  
|Cardinality|0-1 : 省略可能な要素で、出現する場合は 1 回だけの出現が可能です|  
  
## 要素の関係  
  
|リレーションシップ|要素|  
|------------------|-------------|  
|親要素|なし|  
|子要素|[機能](../../../analysis-services/xmla/xml-elements-properties/capability-element-xmla.md)|  
  
## 解説  
 **ProtocolCapabilities**要素により、クライアント アプリケーションでバイナリ XML や圧縮サポートなどのプロトコル機能をネゴシエートする、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]いつでもインスタンス。 プロトコルのネゴシエーションは以下の手順で行われます。  
  
1.  クライアント アプリケーションは、SOAP ヘッダー内に **ProtocolCapabilities** 要素を含む SOAP 要求を送信することにより、自らのプロトコル機能を示します。  
  
2.  [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] は SOAP 要求を受信して処理します。  
  
3.  場合、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスに要求されたものと同じプロトコル機能は、インスタンスが同じを含む SOAP 応答を送信**ProtocolCapabilities**要素が SOAP 要求で送信し、プロトコル、されました正常にネゴシエートします。 そうでない場合、プロトコル機能は正常にネゴシエートされず、インスタンスは SOAP エラーを返します。  
  
 プロトコル機能をどのくらいの時間のクライアント アプリケーションを正常にネゴシエートされた後、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスを使用する特定のプロトコルは、セッションが明示的か暗黙かどうかによって異なります。  
  
-   使用して作成されるものは、明示的なセッション、 [BeginSession](../../../analysis-services/xmla/xml-elements-headers/beginsession-element-xmla.md)ヘッダー要素。 明示的セッションの場合、ネゴシエートされたプロトコルは、クライアント アプリケーションが新しい **ProtocolCapabilities** 要素を送るまで、またはセッションが終了するまで使用されます。  
  
-   暗黙のセッションとは [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] インスタンスによって作成されるセッションで、SOAP 要求の送信時にクライアント アプリケーションによって明示的に指定されるものではありません。 暗黙のセッションの場合、ネゴシエートされたプロトコルは、SOAP 要求が完了するまでの期間だけ使用されます。  
  
 プロトコル機能を明示的にネゴシエートする必要はありません。 つまり、クライアント アプリケーションで **ProtocolCapabilities** 要素を SOAP 要求に含める必要はありません。 SOAP 要求が含まれていない場合、 **ProtocolCapabilities**要素、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]インスタンスは SOAP 要求と同じ形式を使用して応答を行います。  
  
## 参照  
 [管理接続およびセッション (&) #40 です。XMLA &#41;](../../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)   
 [ヘッダーと #40 です。XMLA &#41;](../../../analysis-services/xmla/xml-elements-headers/xml-elements-headers.md)  
  
  

