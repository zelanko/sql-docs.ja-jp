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
ms.openlocfilehash: 2c6c0fcffae318e13025d63c7a244f44de8689f4
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85724671"
---
# <a name="sysevents-transact-sql"></a>sys. events (Transact-sql)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  トリガーまたはイベント通知が発生するイベントごとに1行の値を格納します。 これらのイベントは、 [CREATE trigger](../../t-sql/statements/create-trigger-transact-sql.md)または[create event notification](../../t-sql/statements/create-event-notification-transact-sql.md)を使用してトリガーまたはイベント通知が作成されるときに指定されるイベントの種類を表します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**object_id**|**int**|トリガーまたはイベント通知の ID。 この値は、**型**と共に、行を一意に識別します。|  
|**type**|**int**|トリガーを起動させるイベントです。|  
|**type_desc**|**nvarchar(60)**|トリガーを起動するイベントの説明。|  
|**is_trigger_event**|**bit**|1 = トリガーイベント。<br /><br /> 0 = 通知イベント。|  
|**event_group_type**|**int**|トリガーまたはイベント通知が作成されるイベントグループ。イベントグループに作成されていない場合は null。|  
|**event_group_type_desc**|**nvarchar(60)**|トリガーまたはイベント通知を作成する対象のイベント グループの説明です。イベント グループが作成対象でない場合は NULL になります。|  
  
## <a name="see-also"></a>関連項目  
 [オブジェクトカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
