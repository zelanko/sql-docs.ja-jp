---
title: "sys.events (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.events_TSQL
- sys.events
- events_TSQL
- events
dev_langs: TSQL
helpviewer_keywords: sys.events catalog view
ms.assetid: f245a97a-80fc-43fb-a6e4-139420c9a47a
caps.latest.revision: "38"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b975acfb9ee4134eb768055bd9a012678681dc4b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sysevents-transact-sql"></a>sys.events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  トリガーまたはイベント通知を起動するイベントごとに 1 行のデータを格納します。 これらのイベントを使用して、トリガーまたはイベント通知が作成されるときに指定されているイベントの種類を表す[CREATE TRIGGER](../../t-sql/statements/create-trigger-transact-sql.md)または[CREATE EVENT NOTIFICATION](../../t-sql/statements/create-event-notification-transact-sql.md)です。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|トリガーまたはイベント通知の ID。 この値と連携して**型**、一意に行を識別します。|  
|**型**|**int**|トリガーを起動するイベント。|  
|**type_desc**|**nvarchar (60)**|トリガーを起動するイベントの説明。|  
|**is_trigger_event**|**bit**|1 = トリガー イベント。<br /><br /> 0 = 通知イベント。|  
|**event_group_type**|**int**|トリガーまたはイベント通知を作成する対象のイベント グループです。イベント グループが作成対象でない場合は NULL になります。|  
|**event_group_type**|**nvarchar (60)**|トリガーまたはイベント通知を作成する対象のイベント グループの説明です。イベント グループが作成対象でない場合は NULL になります。|  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
