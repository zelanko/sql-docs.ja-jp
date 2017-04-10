---
title: "ネットワーク プロパティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "LingerTimeout プロパティ"
  - "EnableNagleAlgorithm プロパティ"
  - "MinPendingAcceptExCount プロパティ"
  - "MaxPendingSendCount プロパティ"
  - "EnableBinaryXML プロパティ"
  - "MinPendingReceiveCount プロパティ"
  - "MaxCompletedReceiveCount プロパティ"
  - "DisableNonblockingMode プロパティ"
  - "RequestSizeThreshold プロパティ"
  - "CompressionLevel プロパティ"
  - "ReceiveBufferSize プロパティ"
  - "EnableCompression プロパティ"
  - "ServerSendTimeout プロパティ"
  - "IPV4Support プロパティ"
  - "MaxPendingReceiveCount プロパティ"
  - "MaxPendingAcceptExCount プロパティ"
  - "IPV6Support プロパティ"
  - "MaxAllowedRequestSize プロパティ"
  - "ServerReceiveTimeout プロパティ"
  - "EnableLingerOnClose プロパティ"
  - "InitialConnectTimeout プロパティ"
  - "SendBufferSize プロパティ"
  - "ScatterReceiveMultiplier プロパティ"
  - "ネットワーク プロパティ [Analysis Services]"
ms.assetid: ef4251e2-abe5-4c5b-9868-7549782d0244
caps.latest.revision: 15
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 15
---
# ネットワーク プロパティ
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、次の表に示すサーバー プロパティがサポートされています。 その他のサーバー プロパティとその設定方法の詳細については、「[Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。  
  
 **適用対象:** 多次元サーバー モードおよびテーブル サーバー モード  
  
## 全般  
 **ListenOnlyOnLocalConnections**  
 localhost などのローカル接続のみリッスンするかどうかを識別する、ブール型プロパティです。  
  
## リスナー  
 **IPV4Support**  
 IPv4 プロトコルのサポートを定義する、符号付き 32 ビット整数のプロパティです。 このプロパティは、次の表に示すいずれかの値になります。  
  
|値|説明|  
|-----------|-----------------|  
|*0*|IPv4 は無効です。クライアントは接続できません。|  
|*1*|(既定) IPv4 が必要です。IPv4 をリッスンできない場合、サーバーは起動しません。|  
|*2*|IPv4 はオプションです。サーバーは IPv4 をリッスンしようとしますが、それが不可能でも起動します。|  
  
 **IPV6Support**  
 IPv6 プロトコルのサポートを定義する、符号付き 32 ビット整数のプロパティです。 このプロパティは、次の表に示すいずれかの値になります。  
  
|値|説明|  
|-----------|-----------------|  
|*0*|IPv6 は無効です。クライアントは接続できません。|  
|*1*|(既定) IPv6 が必要です。IPv6 をリッスンできない場合、サーバーは起動しません。|  
|*2*|IPv6 はオプションです。サーバーは IPv6 をリッスンしようとしますが、それが不可能でも起動します。|  
  
 **MaxAllowedRequestSize**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **RequestSizeThreshold**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ServerReceiveTimeout**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ServerSendTimeout**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## 要求  
 **EnableBinaryXML**  
 サーバーがバイナリ XML 形式の要求を認識するかどうかを指定する、ブール型プロパティです。  
  
 **EnableCompression**  
 要求の圧縮を有効にするかどうかを指定する、ブール型プロパティです。  
  
## 応答  
 **CompressionLevel**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **EnableBinaryXML**  
 サーバーでバイナリ XML 応答を有効にするかどうかを指定する、ブール型プロパティです。  
  
 **EnableCompression**  
 クライアント要求に対する応答の圧縮を有効にするかどうかを指定する、ブール型プロパティです。  
  
## TCP  
 **InitialConnectTimeout**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MaxCompletedReceiveCount**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MaxPendingAcceptExCount**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MaxPendingReceiveCount**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MaxPendingSendCount**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MinPendingAcceptExCount**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **MinPendingReceiveCount**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **ScatterReceiveMultiplier**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **SocketOptions\ DisableNonblockingMode**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **SocketOptions\ EnableLingerOnClose**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **SocketOptions\EnableNagleAlgorithm**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **SocketOptions\ LingerTimeout**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **SocketOptions\ ReceiveBufferSize**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **SocketOptions\ SendBufferSize**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
## 参照  
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  