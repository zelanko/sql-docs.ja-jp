---
title: ネットワーク プロパティ |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 70e1ea429d7c60f3d9ba7806d6e6a6a25998b4f5
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="network-properties"></a>ネットワーク プロパティ
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] では、次の表に示すサーバー プロパティがサポートされています。 その他のサーバー プロパティとその設定方法の詳細については、「 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)」を参照してください。  
  
 **適用対象:** 多次元サーバー モードおよびテーブル サーバー モード  
  
## <a name="general"></a>全般  
 **ListenOnlyOnLocalConnections**  
 localhost などのローカル接続のみリッスンするかどうかを識別する、ブール型プロパティです。  
  
## <a name="listener"></a>リスナー  
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
  
## <a name="requests"></a>要求  
 **EnableBinaryXML**  
 サーバーがバイナリ XML 形式の要求を認識するかどうかを指定する、ブール型プロパティです。  
  
 **EnableCompression**  
 要求の圧縮を有効にするかどうかを指定する、ブール型プロパティです。  
  
## <a name="responses"></a>応答  
 **CompressionLevel**  
 詳細プロパティです。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] サポートの指示がない限り、変更しないでください。  
  
 **EnableBinaryXML**  
 サーバーでバイナリ XML 応答を有効にするかどうかを指定する、ブール型プロパティです。  
  
 **EnableCompression**  
 クライアント要求に対する応答の圧縮を有効にするかどうかを指定する、ブール型プロパティです。  
  
## <a name="tcp"></a>TCP  
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
  
## <a name="see-also"></a>参照  
 [Analysis Services のサーバー プロパティ](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [Analysis Services インスタンスのサーバー モードの決定](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
