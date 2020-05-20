---
title: sys. events (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 17c8ab2013a1ad36d298039c5706bd518765dd3b
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82831958"
---
# <a name="sysevents-transact-sql"></a>sys. events (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  トリガーまたはイベント通知が発生するイベントごとに1行の値を格納します。 これらのイベントは、 [CREATE trigger](../../t-sql/statements/create-trigger-transact-sql.md)または[create event notification](../../t-sql/statements/create-event-notification-transact-sql.md)を使用してトリガーまたはイベント通知が作成されるときに指定されるイベントの種類を表します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|トリガーまたはイベント通知の ID。 この値は、**型**と共に、行を一意に識別します。|  
|**type**|**int**|トリガーを起動させるイベントです。|  
|**type_desc**|**nvarchar(60)**|トリガーを起動するイベントの説明。|  
|**is_trigger_event**|**bit**|1 = トリガーイベント。<br /><br /> 0 = 通知イベント。|  
|**event_group_type**|**int**|トリガーまたはイベント通知が作成されるイベントグループ。イベントグループに作成されていない場合は null。|  
|**event_group_type_desc**|**nvarchar(60)**|トリガーまたはイベント通知を作成する対象のイベント グループの説明です。イベント グループが作成対象でない場合は NULL になります。|  
  
## <a name="see-also"></a>参照  
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
