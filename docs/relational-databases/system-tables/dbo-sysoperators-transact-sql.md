---
title: dbo.sysoperators (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- sysoperators
- dbo.sysoperators
- dbo.sysoperators_TSQL
- sysoperators_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoperators system table
ms.assetid: c2afa20c-b15f-46ca-ae74-2eb65909409e
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e0653c108d7fb05dc2d7e68e2d29be7dac0f43ce
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="dbosysoperators-transact-sql"></a>dbo.sysoperators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ごとに 1 つの行を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントのオペレーターです。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|オペレーターの ID。|  
|**name**|**sysname**|オペレーターの名前。|  
|**enabled**|**tinyint**|警告通知の状態 (ブール値)。 場合**1**警告が発生したときに、このオペレーターが通知を受信できます。|  
|**email_address**|**nvarchar(100)**|オペレーターの電子メール アドレス。|  
|**last_email_date**|**int**|オペレーターが前回、電子メールによる警告通知を受信した日付。|  
|**last_email_time**|**int**|オペレーターが前回、電子メールによる警告通知を受信した時刻。|  
|**pager_address**|**nvarchar(100)**|オペレーターのポケットベル アドレス。|  
|**last_pager_date**|**int**|オペレーターが前回、ポケットベルによる警告通知を受信した日付。|  
|**last_pager_time**|**int**|オペレーターが前回、ポケットベルによる警告通知を受信した時刻。|  
|**weekday_pager_start_time**|**int**|平日 (月曜から金曜まで)、オペレーターのポケットベルによる警告通知が受信可能になる時刻。|  
|**weekday_pager_end_time**|**int**|平日 (月曜から金曜まで)、オペレーターのポケットベルによる警告通知が受信不能になる時刻。|  
|**saturday_pager_start_time**|**int**|土曜日にオペレーターのポケットベルによる警告通知が受信可能になる時刻。|  
|**saturday_pager_end_time**|**int**|土曜日にオペレーターのポケットベルによる警告通知が受信不能になる時刻。|  
|**sunday_pager_start_time**|**int**|日曜日にオペレーターのポケットベルによる警告通知が受信可能になる時刻。|  
|**sunday_pager_end_time**|**int**|日曜日にオペレーターのポケットベルによる警告通知が受信不能になる時刻。|  
|**pager_days**|**tinyint**|オペレーターのポケットベルによる警告通知が受信可能になる曜日のビットマスク。|  
|**netsend_address**|**nvarchar(100)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**last_netsend_date**|**int**|指定したオペレーター ID に最新のネットワーク メッセージが送信された前回の日付。|  
|**last_netsend_time**|**int**|指定したオペレーター ID に最新のネットワーク メッセージが送信された前回の時刻。|  
|**category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント テーブル&#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
