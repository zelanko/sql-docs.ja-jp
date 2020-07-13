---
title: database_event_session_actions (Azure SQL Database) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 32494df1-7ab7-4b88-a858-6b1021d67433
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: a5e0e31418e2399a8d2fcfb35fde2422636d2469
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.contentlocale: ja-JP
ms.lasthandoff: 07/06/2020
ms.locfileid: "86003050"
---
# <a name="sysdatabase_event_session_actions-azure-sql-database"></a>sys.database_event_session_actions (Azure SQL Database)
[!INCLUDE [sqlserver2016-asdb-asdbmi-asa](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi-asa.md)]

  イベント セッションの各イベントのアクションごとに 1 行のデータを返します。  
  
||  
|-|  
|**に適用さ**れます: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 およびそれ以降のすべてのバージョン。|  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|イベントセッションの ID。 NULL 値は許可されません。|  
|event_id|**int**|イベントの ID。 この ID は、イベントセッションオブジェクト内で一意です。 NULL 値は許可されません。|  
|name|**sysname**|アクションの名前。 NULL 値が許可されます。|  
|package|**sysname**|イベントを含むイベント パッケージの名前。 NULL 値が許可されます。|  
|name|**sysname**|イベントが格納されているモジュールの名前。 NULL 値が許可されます。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="remarks"></a>コメント  
 このビューには、次のリレーションシップ基数があります。  
  
||||  
|-|-|-|  
|From|終了|リレーションシップ|  
|database_event_session_actions。 event_session_id|sys.sys。 database_event_sessions。 event_session_id|多対一|  
|database_event_session_actions。 event_id<br /><br /> database_event_session_actions。 event_session_id|database_event_session_events。 event_session_id<br /><br /> database_event_session_events。 event_id|多対一|  
  
  
