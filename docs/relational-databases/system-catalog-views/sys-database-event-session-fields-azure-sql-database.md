---
title: database_event_session_fields (Azure SQL Database) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 9b5c94d6-612c-4e0f-976d-ac6ba55da3ac
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 910c4a6a8ebf40de23069ecbf3c96d8d67533efa
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82823545"
---
# <a name="sysdatabase_event_session_fields-azure-sql-database"></a>sys.database_event_session_fields (Azure SQL Database)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  イベントおよびターゲットに明示的に設定されたカスタマイズ可能な列ごとに 1 行のデータを返します。  
  
||  
|-|  
|**に適用さ**れます: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 およびそれ以降のすべてのバージョン。|  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|イベントセッションの ID。 NULL 値は許可されません。|  
|object_id|**int**|このフィールドに関連付けられているオブジェクトの ID。 NULL 値は許可されません。|  
|name|**sysname**|フィールドの名前。 NULL 値は許可されません。|  
|value|**sql_variant**|フィールドの値。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="remarks"></a>解説  
 このビューには、次のリレーションシップ基数があります。  
  
||||  
|-|-|-|  
|From|終了|リレーションシップ|  
|database_event_session_actions。 event_session_id|database_event_sessions。 event_session_id|多対一|  
|database_event_session_actions。 event_id<br /><br /> database_event_session_actions。 object_id<br /><br /> database_event_session_actions。 event_session_id|database_event_session_events。 event_session_id<br /><br /> database_event_session_events。 event_id|多対一|  
|database_event_session_actions。 event_session_id<br /><br /> database_event_session_actions。 object_id|database_event_session_targets。 event_session_id<br /><br /> database_event_session_targets。 target_id|多対一|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  
