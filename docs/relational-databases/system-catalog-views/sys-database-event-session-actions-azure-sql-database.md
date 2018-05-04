---
title: sys.database_event_session_actions (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.service: ''
ms.component: system-catalog-views
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- Azure SQL Database
ms.assetid: 32494df1-7ab7-4b88-a858-6b1021d67433
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: d1cd4e1ecedc444949ab2e886b6902017add44a4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdatabaseeventsessionactions-azure-sql-database"></a>sys.database_event_session_actions (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  イベント セッションの各イベントのアクションごとに 1 行のデータを返します。  
  
||  
|-|  
|**適用されます**: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 およびそれ以降のバージョン。|  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|イベント セッションの ID。 NULL 値は許可されません。|  
|event_id|**int**|イベントの ID。 この ID は、イベント セッション オブジェクト内で一意です。 NULL 値は許可されません。|  
|name|**sysname**|アクションの名前です。 NULL 値が許可されます。|  
|パッケージ (package)|**sysname**|イベントを含むイベント パッケージの名前。 NULL 値が許可されます。|  
|モジュール (module)|**sysname**|イベントを含むモジュールの名前。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="remarks"></a>解説  
 このビューは、次に示すリレーションシップの基数を持ちます。  
  
||||  
|-|-|-|  
|From|変換先|リレーションシップ|  
|sys.database_event_session_actions.event_session_id|sys.sys.database_event_sessions.event_session_id|多対一|  
|sys.database_event_session_actions.event_id<br /><br /> sys.database_event_session_actions.event_session_id|sys.database_event_session_events.event_session_id<br /><br /> sys.database_event_session_events.event_id|多対一|  
  
  
