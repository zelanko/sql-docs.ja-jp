---
title: FT:Crawl Stopped イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Crawl Stopped event class
ms.assetid: dbc91bf7-687c-4083-9694-02f3e102c175
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: bc26a028a353bd122659a15666afe20f9815c92d
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43073115"
---
# <a name="ftcrawl-stopped-event-class"></a>FT:Crawl Stopped イベント クラス
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **:Crawl Stopped** イベント クラスは、フルテキスト クロール (作成) が停止されたことを示します。 クロールは、正常に完了するか、致命的なエラーが発生したときに、停止される可能性があります。  
  
## <a name="ftcrawl-stopped-event-class-data-columns"></a>FT:Crawl Stopped イベント クラスのデータ列  
  
|データ列名|データ型|[説明]|列 ID|フィルターの適用|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|フルテキスト クロールが停止したデータベースの ID。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|[ユーザー アカウント制御]|  
|**EventClass**|**int**|イベントの種類 = 156。|27|いいえ|  
|**EventSequence**|**int**|要求内の特定のイベントのシーケンス。|51|いいえ|  
|**IsSystem**|**int**|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。 1 はシステム、0 はユーザーです。|60|[ユーザー アカウント制御]|  
|**Exchange Spill**|**int**|システムによって割り当てられたオブジェクト ID。 このオブジェクトのフルテキスト インデックスでフルテキスト クロールが停止しました。|22|[ユーザー アカウント制御]|  
|**SessionLoginName**|**nvarchar**|セッションを開始したユーザーのログイン名。 たとえば、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、 **SessionLoginName** には Login1 が表示され、 **LoginName** には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ログインの両方が表示されます。|64|[ユーザー アカウント制御]|  
|**SPID**|**int**|イベントが発生したセッションの ID。|12|[ユーザー アカウント制御]|  
|**StartTime**|**datetime**|イベントの開始時刻 (取得できた場合)。|14|[ユーザー アカウント制御]|  
|**TransactionID**|**bigint**|システムによって割り当てられたトランザクション ID。|4|[ユーザー アカウント制御]|  
  
## <a name="see-also"></a>参照  
 [sp_trace_setevent &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
