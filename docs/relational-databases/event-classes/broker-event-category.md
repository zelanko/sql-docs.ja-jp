---
title: "Broker イベント カテゴリ | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "SQL Server イベント クラス, Broker イベント カテゴリ"
  - "Broker イベント カテゴリ [SQL Server]"
  - "イベント クラス [SQL Server], Broker イベント カテゴリ"
ms.assetid: 470dc93c-0dda-4d89-829b-937738d59b31
caps.latest.revision: 17
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 17
---
# Broker イベント カテゴリ
  **Broker** イベント カテゴリには、一般的な Service Broker イベントが含まれます。  
  
## このセクションの内容  
  
|トピック|説明|  
|-----------|-----------------|  
|[Broker:Activation イベント クラス](../../relational-databases/event-classes/broker-activation-event-class.md)|キュー モニターがアクティブ化ストアド プロシージャを開始するときに生成されるイベント。|  
|[Broker:Connection イベント クラス](../../relational-databases/event-classes/broker-connection-event-class.md)|Service Broker によって管理されるトランスポート接続のステータスをレポートするために生成されるイベントです。|  
|[Broker:Conversation イベント クラス](../../relational-databases/event-classes/broker-conversation-event-class.md)|メッセージ交換の進行状況をレポートするために生成されるイベントです。|  
|[Broker:Conversation Group イベント クラス](../../relational-databases/event-classes/broker-conversation-group-event-class.md)|データベースがメッセージ交換グループを作成または削除すると生成されるイベントです。|  
|[Broker:Corrupted Message イベント クラス](../../relational-databases/event-classes/broker-corrupted-message-event-class.md)|データベースが破損メッセージを受信したことを報告するために生成されるイベント。|  
|[Broker:Forwarded Message Dropped イベント クラス](../../relational-databases/event-classes/broker-forwarded-message-dropped-event-class.md)|転送された Service Broker メッセージが SQL Server によって削除されるときに生成されるイベント。|  
|[Broker:Forwarded Message Sent イベント クラス](../../relational-databases/event-classes/broker-forwarded-message-sent-event-class.md)|SQL Server によって Service Broker メッセージが転送されるときに生成されるイベント。|  
|[Broker:Message Classify イベント クラス](../../relational-databases/event-classes/broker-message-classify-event-class.md)|Service Broker がメッセージのルーティングを決定するときに生成されるイベント。|  
|[Broker:Message Drop イベント クラス](../../relational-databases/event-classes/broker-message-drop-event-class.md)|このインスタンスのサービスに配信する必要のある受信メッセージを、Service Broker が保持できないときに生成されるイベント。|  
|[Broker:Remote Message Ack イベント クラス](../../relational-databases/event-classes/broker-remote-message-ack-event-class.md)|Service Broker がメッセージの受信確認を送信または受信したときに生成されるイベント。|  
  
 Service Broker には、2 つのセキュリティ監査イベントも提供されます。 これらのイベントの詳細については、「[Audit Broker Login イベント クラス](../../relational-databases/event-classes/audit-broker-login-event-class.md)」と「[Audit Broker Conversation イベント クラス](../../relational-databases/event-classes/audit-broker-conversation-event-class.md)」を参照してください。  
  
## 参照  
 [セキュリティ監査イベント カテゴリ](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  