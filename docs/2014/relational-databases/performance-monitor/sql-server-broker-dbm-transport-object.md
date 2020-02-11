---
title: SQL Server、Broker、DBM トランスポートオブジェクト |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Broker / DBM Transport object
- SQLServer:Broker/DBM Transport
ms.assetid: eddb60b6-20a9-416c-adf3-4bc1687944fa
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b0347c7f7e19ae5500f8c5be100ef2d0dc663784
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63250729"
---
# <a name="sql-server-broker-and-dbm-transport-object"></a>SQL Server の Broker および DBM Transport オブジェクト
  **Broker / DBM Transport** パフォーマンス オブジェクトには、Service Broker とデータベース ミラーリングに関するネットワーク情報を報告するパフォーマンス カウンターが含まれています。 次の表は、このオブジェクトに含まれているカウンターを示します。  
  
|SQL Server: Broker / DBM Transport カウンター|[説明]|  
|------------------------------------------------|-----------------|  
|**Current Bytes for Recv I/O**|現在実行中のトランスポート受信操作で読み取るバイト数を報告します。|  
|**Current Bytes for Send I/O**|ネットワーク経由で送信処理中のメッセージ フラグメントに含まれるバイト数を報告します。|  
|**Current Msg Frags for Send I/O**|ネットワーク経由で送信処理中のメッセージ フラグメントの総数を報告します。|  
|**Message Fragment P1 Sends/sec**|ネットワーク経由で 1 秒あたりに送信された優先度 1 のメッセージ フラグメント数を報告します。|  
|**Message Fragment P2 Sends/sec**|ネットワーク経由で 1 秒あたりに送信された優先度 2 のメッセージ フラグメント数を報告します。|  
|**Message Fragment P3 Sends/sec**|ネットワーク経由で 1 秒あたりに送信された優先度 3 のメッセージ フラグメント数を報告します。|  
|**Message Fragment P4 Sends/sec**|ネットワーク経由で 1 秒あたりに送信された優先度 4 のメッセージ フラグメント数を報告します。|  
|**Message Fragment P5 Sends/sec**|ネットワーク経由で 1 秒あたりに送信された優先度 5 のメッセージ フラグメント数を報告します。|  
|**Message Fragment P6 Sends/sec**|ネットワーク経由で 1 秒あたりに送信された優先度 6 のメッセージ フラグメント数を報告します。|  
|**Message Fragment P7 Sends/sec**|ネットワーク経由で 1 秒あたりに送信された優先度 7 のメッセージ フラグメント数を報告します。|  
|**Message Fragment P8 Sends/sec**|ネットワーク経由で 1 秒あたりに送信された優先度 8 のメッセージ フラグメント数を報告します。|  
|**Message Fragment P9 Sends/sec**|ネットワーク経由で 1 秒あたりに送信された優先度 9 のメッセージ フラグメント数を報告します。|  
|**Message Fragment P10 Sends/sec**|ネットワーク経由で 1 秒あたりに送信された優先度 10 のメッセージ フラグメント数を報告します。|  
|**Message Fragment Send Size Avg**|ネットワーク経由で送信されたメッセージ フラグメントの平均サイズを報告します。|  
|**Message Fragment Sends/sec**|ネットワーク経由で 1 秒あたりに送信されたすべての優先度のメッセージ フラグメント数を報告します。|  
|**Msg Fragment Receives/sec**|ネットワーク経由で 1 秒あたりに受信したメッセージ フラグメント数を報告します。|  
|**メッセージフラグメントの受信サイズの平均**|ネットワーク経由で受信したメッセージ フラグメントの平均サイズを報告します。|  
|**接続数を開く**|Service Broker が現在開いているネットワーク接続の数を報告します。|  
|**受信 i/o の保留中バイト数**|ネットワークからの受信後、まだキューへの配置も破棄も行われていないメッセージ フラグメントに含まれるバイト数を報告します。|  
|**保留中の送信 i/o のバイト数**|ネットワーク経由での送信準備が整ったメッセージ フラグメント内の合計バイト数を報告します。|  
|**Pending Msg Frags for Recv i/o**|ネットワークからの受信後、まだキューへの配置も破棄も行われていないメッセージ フラグメントの数を報告します。|  
|**Pending Msg Frags for Send i/o**|ネットワーク経由での送信準備が整ったメッセージ フラグメントの総数を報告します。|  
|**Receive i/o Bytes Total**|Service Broker のエンドポイントとデータベース ミラーリングのエンドポイントで、ネットワーク経由で受信した合計バイト数を報告します。|  
|**Receive i/o bytes/sec**|Service Broker のエンドポイントとデータベース ミラーリングのエンドポイントで、ネットワーク経由で 1 秒あたりに受信したバイト数を報告します。|  
|**Receive i/o Len Avg**|トランスポート受信操作の平均バイト数を報告します。|  
|**Receive I/Os/second**|Service Broker / DBM トランスポート層が 1 秒あたりに完了したトランスポート受信 I/O 操作の数を報告します。 1 つのトランスポート受信操作には、複数のメッセージ フラグメントが含まれている可能性があることに注意してください。|  
|**Send i/o Bytes Total**|Service Broker のエンドポイントとデータベース ミラーリングのエンドポイントで、ネットワーク経由で送信した合計バイト数を報告します。|  
|**Send i/o bytes/sec**|Service Broker のエンドポイントとデータベース ミラーリングのエンドポイントで、ネットワーク経由で 1 秒あたりに送信したバイト数を報告します。|  
|**Send i/o Len Avg**|各トランスポート送信操作の平均サイズをバイト単位で報告します。 1 つのトランスポート送信操作には、複数のメッセージ フラグメントが含まれている可能性があることに注意してください。|  
|**Send I/Os/sec**|1 秒あたりに完了したトランスポート送信 I/O 操作の数を報告します。 1 つのトランスポート送信操作には、複数のメッセージ フラグメントが含まれている可能性があることに注意してください。|  
  
## <a name="see-also"></a>参照  
 [dm_broker_forwarded_messages &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-broker-forwarded-messages-transact-sql)   
 [SQL Server Service Broker](../../database-engine/configure-windows/sql-server-service-broker.md)   
 [リソース使用状況の監視 &#40;システムモニタ&#41;](monitor-resource-usage-system-monitor.md)  
  
  
