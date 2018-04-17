---
title: dbo.sysalerts (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dbo.sysalerts
- sysalerts_TSQL
- dbo.sysalerts_TSQL
- sysalerts
dev_langs:
- TSQL
helpviewer_keywords:
- sysalerts system table
ms.assetid: a2c2f50d-61f3-4951-996a-add5ad092cc2
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 271452f516e231e22140664c049dacdaea5257a9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="dbosysalerts-transact-sql"></a>dbo.sysalerts (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  警告 1 件につき 1 行のデータを格納します。 警告は、イベントに応答して送信されるメッセージです。 警告メッセージは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境の外に転送でき、電子メールやポケットベルのメッセージとして送信することもできます。 また、警告でタスクを生成することもできます。  次の表は、 **msdb**データベース。
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|警告 ID。|  
|**name**|**sysname**|警告名。|  
|**event_source**|**nvarchar(100)**|イベントのソース ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)])。|  
|**event_category_id**|**int**|将来の使用のために予約されています。|  
|**event_id**|**int**|将来の使用のために予約されています。|  
|**message_id**|**int**|ユーザー定義メッセージの ID またはへの参照を**sysmessages**はこのアラートをトリガーするメッセージ。|  
|**severity**|**int**|警告の重大度。|  
|**enabled**|**tinyint**|警告の状態。<br /><br /> **0**無効になっています。<br /><br /> **1** = 有効にします。|  
|**delay_between_responses**|**int**|警告の通知間隔 (秒単位)。|  
|**last_occurrence_date**|**int**|前回の警告発生日。|  
|**last_occurrence_time**|**int**|前回の警告発生時刻。|  
|**last_response_date**|**int**|前回の警告通知日。|  
|**last_response_time**|**int**|前回の警告通知時刻。|  
|**notification_message**|**nvarchar(512)**|警告と一緒に送信された追加情報。|  
|**include_event_description**|**tinyint**|イベントの説明は、電子メール、ポケットベル、または Net send によって送信されるかどうかを表すビットマスク。 値の下のグラフを参照してください。|  
|**database_name**|**nvarchar(512)**|警告を発生したと考えられるデータベース。|  
|**event_description_keyword**|**nvarchar(100)**|警告が発生するときのエラー パターン。|  
|**occurrence_count**|**int**|警告の発生回数。|  
|**count_reset_date**|**int**|日 (日) のカウントをリセットする**0**します。|  
|**count_reset_time**|**int**|積算日の時間にリセットする**0**します。|  
|**job_id**|**uniqueidentifier**|警告が発生したときに実行するタスクの ID。|  
|**has_notification**|**int**|警告が発生したときに電子メール通知を受け取るオペレーターの人数。|  
|**flags**|**int**|予約されています。|  
|**performance_condition**|**nvarchar(512)**|予約されています。|  
|**category_id**|**int**|予約されています。|  
  
 ## <a name="remarks"></a>解説

次の表は、include_event_description ビットマスクの値を示します。 10 進数の値が dbo.sysalerts によって返されます。 

|decimal | binary | 意味 |
|------|------|------|
|0 |0000 |メッセージはありません。 |
|1 |0001 |電子メール |
|2 |0010 |ポケットベル (pager) |
|3 |0011 |ポケットベルとメール |
|4 |0100 |[Net Send] |
|5 |0101 |Net send および電子メール |
|6 |0110 |Net send およびポケットベル |
|7 |0111 |Net send、ポケットベル、および電子メール |
  
