---
title: FT:Crawl Stopped イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Crawl Stopped event class
ms.assetid: dbc91bf7-687c-4083-9694-02f3e102c175
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 82935c5d032887afb580c81b9bf376eba5def47e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37199542"
---
# <a name="ftcrawl-stopped-event-class"></a>FT:Crawl Stopped イベント クラス
  **:Crawl Stopped** イベント クラスは、フルテキスト クロール (作成) が停止されたことを示します。 クロールは、正常に完了するか、致命的なエラーが発生したときに、停止される可能性があります。  
  
## <a name="ftcrawl-stopped-event-class-data-columns"></a>FT:Crawl Stopped イベント クラスのデータ列  
  
|データ列名|データ型|説明|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|フルテキスト クロールが停止したデータベースの ID。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|はい|  
|**EventClass**|**int**|イベントの種類 = 156。|27|いいえ|  
|**EventSequence**|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|**IsSystem**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|はい|  
|**Exchange Spill**|**int**|システムによって割り当てられたオブジェクト ID。 このオブジェクトのフルテキスト インデックスでフルテキスト クロールが停止しました。|22|はい|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログインの両方が表示されます。|64|はい|  
|**SPID**|**int**|イベントが発生したセッションの ID。|12|はい|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|はい|  
|**TransactionID**|**bigint**|システムによって割り当てられたトランザクション ID。|4|はい|  
  
## <a name="see-also"></a>参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql)  
  
  
