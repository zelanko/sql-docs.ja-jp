---
description: sys.database_event_session_targets (Azure SQL Database)
title: sys.database_event_session_targets (Azure SQL Database) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
ms.assetid: 38d775ee-1fe1-4820-88c6-02b2f875a66b
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 2b77a6340fe245884c137fb24fbeac653a8a2ff0
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97458520"
---
# <a name="sysdatabase_event_session_targets-azure-sql-database"></a>sys.database_event_session_targets (Azure SQL Database)

[!INCLUDE [sqlserver2016-asdb-asdbmi](../../includes/applies-to-version/sqlserver2016-asdb-asdbmi.md)]

  イベント セッションのイベント ターゲットごとに 1 行のデータを返します。  
  
||  
|-|  
|**に適用さ** れます: [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V12 およびそれ以降のすべてのバージョン。|  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|event_session_id|**int**|イベントセッションの ID。 NULL 値は許可されません。|  
|target_id|**int**|ターゲットの ID。 ID は、イベントセッションオブジェクト内で一意です。 NULL 値は許可されません。|  
|name|**sysname**|イベントターゲットの名前。 NULL 値は許可されません。|  
|パッケージ|**sysname**|イベントターゲットを含むイベントパッケージの名前。 NULL 値は許可されません。|  
|name|**sysname**|イベント ターゲットを含むモジュールの名前。 NULL 値は許可されません。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW DATABASE STATE 権限が必要です。  
  
## <a name="remarks"></a>解説  
 このビューには、次のリレーションシップ基数があります。  
  
|差出人|終了|リレーションシップ|  
|-|-|-|  
|sys.database_event_session_targets sys.database_event_session_targets.event_session_id|sys.database_event_sessions sys.database_event_sessions.event_session_id|多対一|  
  
## <a name="see-also"></a>参照  
 [拡張イベント](../../relational-databases/extended-events/extended-events.md)  
  
  
