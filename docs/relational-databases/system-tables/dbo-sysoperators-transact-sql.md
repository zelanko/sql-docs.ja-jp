---
title: dbo.sysoperators (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3796714cbdfb55900447bf23904136ac5abefa9c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47678920"
---
# <a name="dbosysoperators-transact-sql"></a>dbo.sysoperators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ごとに 1 つの行を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェントのオペレーターです。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|オペレーターの ID。|  
|**name**|**sysname**|オペレーターの名前。|  
|**enabled**|**tinyint**|警告通知の状態 (ブール値)。 場合**1**アラートが発生した場合、このオペレーターが通知を受信できます。|  
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
  
  
