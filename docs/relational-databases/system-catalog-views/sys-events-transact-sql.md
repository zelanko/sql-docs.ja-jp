---
title: sys.events (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.events_TSQL
- sys.events
- events_TSQL
- events
dev_langs:
- TSQL
helpviewer_keywords:
- sys.events catalog view
ms.assetid: f245a97a-80fc-43fb-a6e4-139420c9a47a
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 7621b5aba9bb67a07421339e1e72b29f06f4c5ff
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39532733"
---
# <a name="sysevents-transact-sql"></a>sys.events (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  トリガーまたはイベント通知を起動するイベントごとに 1 行のデータを格納します。 これらのイベントを使用して、トリガーまたはイベント通知が作成されるときに指定されているイベントの種類を表す[CREATE TRIGGER](../../t-sql/statements/create-trigger-transact-sql.md)または[CREATE EVENT NOTIFICATION](../../t-sql/statements/create-event-notification-transact-sql.md)します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|トリガーまたはイベント通知の ID。 この値は、と共に**型**を一意に、行を識別します。|  
|**type**|**int**|トリガーを起動するイベント。|  
|**type_desc**|**nvarchar(60)**|トリガーを起動するイベントの説明。|  
|**is_trigger_event**|**bit**|1 = トリガー イベント。<br /><br /> 0 = 通知イベント。|  
|**event_group_type**|**int**|トリガーまたはイベント通知を作成する対象のイベント グループです。イベント グループが作成対象でない場合は NULL になります。|  
|**event_group_type**|**nvarchar(60)**|トリガーまたはイベント通知を作成する対象のイベント グループの説明です。イベント グループが作成対象でない場合は NULL になります。|  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
