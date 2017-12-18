---
title: "Server Memory Change イベント クラス | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: event-classes
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Server Memory Change event class
ms.assetid: c9836484-39c5-4a89-b080-3567783b6fff
caps.latest.revision: "29"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7d37287080b33f3e3ff1398e60006e204d20b12
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="server-memory-change-event-class"></a>Server Memory Change イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)] **Server Memory Change** イベント クラスは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のメモリ使用率が 1 MB または最大サーバー メモリ容量の 5 % のどちらか大きい方を超えて増加または減少したときに発生します。  
  
## <a name="server-memory-change-event-class-data-columns"></a>Server Memory Change イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|可|  
|----------------------|---------------|-----------------|---------------|---------|  
|**EventClass**|**int**|イベントの種類 = 81。|27|いいえ|  
|**EventSequence**|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|**EventSubClass**|**int**|イベント サブクラスの種類。<br /><br /> 1 = メモリ増加<br /><br /> 2 = メモリ減少|21|可|  
|**IntegerData**|**int**|メガバイト (MB) 単位の新しいメモリ サイズ。|25|可|  
|**IsSystem**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|可|  
|**RequestID**|**int**|ステートメントが含まれている要求の ID。|49|可|  
|**ServerName**|**nvarchar**|トレースされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|はい|  
|**SPID**|**int**|イベントが発生したセッションの ID。|12|はい|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|はい|  
|**TransactionID**|**bigint**|システムによって割り当てられたトランザクション ID。|4|はい|  
|**XactSequence**|**bigint**|現在のトランザクションを説明するトークン。|50|はい|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [サーバー メモリに関するサーバー構成オプション](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  
