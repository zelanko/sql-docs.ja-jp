---
title: "Database Mirroring State Change イベント クラス | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- event notifications [SQL Server], database mirroring
- database mirroring [SQL Server], event notifications
- Database Mirroring State Change event class
ms.assetid: f936a99e-2a81-4768-8177-5c969bbe2e04
caps.latest.revision: 31
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c17b166b850dbd10020927efb4398a91d6db81df
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="database-mirroring-state-change-event-class"></a>Database Mirroring State Change イベント クラス
  **Database Mirroring State Change** イベント クラスは、ミラー化されたデータベースの状態が変更された時点を示します。 このイベント クラスは、ミラー化されたデータベースの状態を監視するトレースに含めます。  
  
 **Database Mirroring State Change** イベント クラスをトレースに含めても、相対的なオーバーヘッドは低くなります。 ミラー化されたデータベースの状態が増加すると、オーバーヘッドがより大きくなることがあります。  
  
## <a name="data-database-mirroring-state-change-event-class-data-columns"></a>Data Database Mirroring State Change イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database* ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、 **ServerName** データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|はい|  
|**DatabaseName**|**nvarchar**|ミラー化されたデータベースの名前。|35|はい|  
|**EventClass**|**int**|イベントの種類 = 167。|27|いいえ|  
|**EventSequence**|**int**|バッチ内のイベント クラスのシーケンス。|51|いいえ|  
|**IntegerData**|**int**|優先状態 ID。|25|可|  
|**IsSystem**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|可|  
|**LoginSid**|**image**|ログイン ユーザーのセキュリティ ID 番号 (SID)。 この情報は、 **sys.server_principals** カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|可|  
|**RequestID**|**int**|ステートメントが含まれている要求の ID。|49|はい|  
|**ServerName**|**nvarchar**|トレースされている [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|はい|  
|**SPID**|**int**|イベントが発生したセッションの ID。|12|はい|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|可|  
|**状態**|**int**|新しいミラーリング状態 ID。<br /><br /> 0 = NULL 通知<br /><br /> 1 = ミラーリング監視サーバー付きの同期されたプリンシパル<br /><br /> 2 = ミラーリング監視サーバーなしの同期されたプリンシパル<br /><br /> 3 = ミラーリング監視サーバー付きの同期されたミラー<br /><br /> 4 = ミラーリング監視サーバーなしの同期されたミラー<br /><br /> 5 = プリンシパルとの接続の喪失<br /><br /> 6 = ミラーとの接続の喪失<br /><br /> 7 = 手動フェールオーバー<br /><br /> 8 = 自動フェールオーバー<br /><br /> 9 = ミラーリングの中断<br /><br /> 10 = クォーラムなし<br /><br /> 11 = ミラーの同期中<br /><br /> 12 = プリンシパルの不安定状態での実行中|30|可|  
|**TextData**|**ntext**|状態変化の説明。|1|可|  
|**TransactionID**|**bigint**|システムによって割り当てられたトランザクション ID。|4|はい|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)   
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
