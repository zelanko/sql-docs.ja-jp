---
title: sys.database_event_session_fields (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.component: system-catalog-views
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
ms.assetid: 9b5c94d6-612c-4e0f-976d-ac6ba55da3ac
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 0a7c7ee610ae5eb3a56a46c5b8c7ba1645b64532
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdatabaseeventsessionfields-azure-sql-database"></a>sys.database_event_session_fields (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  イベントおよびターゲットに明示的に設定されたカスタマイズ可能な列ごとに 1 行のデータを返します。  
  
||  
|-|  
|**適用されます**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 およびそれ以降のバージョン。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|イベント セッションの ID。 NULL 値は許可されません。|  
|object_id|**int**|このフィールドに関連付けられているオブジェクトの ID。 NULL 値は許可されません。|  
|name|**sysname**|フィールドの名前です。 NULL 値は許可されません。|  
|value|**sql_variant**|フィールドの値です。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="remarks"></a>解説  
 このビューは、次に示すリレーションシップの基数を持ちます。  
  
||||  
|-|-|-|  
|From|変換先|リレーションシップ|  
|sys.database_event_session_actions.event_session_id|sys.database_event_sessions.event_session_id|多対一|  
|sys.database_event_session_actions.event_id<br /><br /> sys.database_event_session_actions.object_id<br /><br /> sys.database_event_session_actions.event_session_id|sys.database_event_session_events.event_session_id<br /><br /> sys.database_event_session_events.event_id|多対一|  
|sys.database_event_session_actions.event_session_id<br /><br /> sys.database_event_session_actions.object_id|sys.database_event_session_targets.event_session_id<br /><br /> sys.database_event_session_targets.target_id|多対一|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  
