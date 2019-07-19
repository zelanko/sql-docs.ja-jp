---
title: sys.dm_geo_replication_link_status (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- dm_geo_replication_link_status
- dm_geo_replication_link_status_TSQL
- sys.dm_geo_replication_link_status
- sys.dm_geo_replication_link_status_TSQL
helpviewer_keywords:
- dm_geo_replication_link_status dynamic management view
- sys.dm_geo_replication_link_status dynamic management view
ms.assetid: d763d679-470a-4c21-86ab-dfe98d37e9fd
author: mashamsft
ms.author: mathoma
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 8302de76b45ca09e86c87c29ab99c30898168de5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67900884"
---
# <a name="sysdmgeoreplicationlinkstatus-azure-sql-database"></a>sys.dm_geo_replication_link_status (Azure SQL Database)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Geo レプリケーション パートナーシップのプライマリとセカンダリ データベース間のレプリケーション リンクごとに 1 行が含まれています。 これには、プライマリとセカンダリの両方のデータベースが含まれます。 特定のプライマリ データベースの 1 つ以上の連続レプリケーション リンクが存在する場合、このテーブルは、各リレーションシップの行を含みます。 ビューは、論理マスターを含む、すべてのデータベースに作成されます。 ただし、論理マスターでこのビューをクエリには、空のセットが返されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|link_guid|**uniqueidentifier**|レプリケーション リンクの一意の ID。|  
|partner_server|**sysname**|リンクされたデータベースを含む SQL データベース サーバーの名前。|  
|partner_database|**sysname**|リンクされた SQL データベース サーバー上にあるリンクされたデータベースの名前。|  
|last_replication|**datetimeoffset**|プライマリ データベースのクロックに基づいて、セカンダリで最後のトランザクションの受信確認のタイムスタンプ。 この値は、プライマリ データベースのみでご確認いただけます。|  
|replication_lag_sec|**int**|Last_replication 値と、プライマリ データベースのクロックに基づくプライマリでトランザクションのコミットのタイムスタンプの時間差 (秒)。  この値は、プライマリ データベースのみでご確認いただけます。|  
|replication_state|**tinyint**|このデータベースは、いずれかの geo レプリケーションの状態: です。<br /><br /> 1 = シード処理します。 Geo レプリケーションの対象がシード中は、2 つのデータベースがまだ同期されていません。 シードが完了するまでセカンダリ データベースに接続することはできません。 プライマリからセカンダリ データベースを削除すると、シード処理操作が取り消されます。<br /><br /> 2 = キャッチアップします。 セカンダリ データベースでは、状態の一貫性があり、常に、プライマリ データベースと同期中します。<br /><br /> 4 = Suspended。 これは、アクティブな連続コピー リレーションシップではありません。 通常、この状態は、インターリンクに利用できる帯域幅がプライマリ データベース上のトランザクション アクティビティのレベルに対して不十分であることを示します。 ただし、連続コピー リレーションシップはそのままです。|  
|replication_state_desc|**nvarchar (256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|ロール (role)|**tinyint**|1 つの Geo レプリケーション ロール:<br /><br /> 0 = プライマリです。 Database_id は、geo レプリケーション パートナーシップのプライマリ データベースを指します。<br /><br /> 1 = セカンダリ。  Database_id は、geo レプリケーション パートナーシップのプライマリ データベースを指します。|  
|role_desc|**nvarchar (256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|1 つのセカンダリ型。<br /><br /> 0 = ダイレクトではありません、セカンダリ データベースへの接続を許可し、データベースは読み取りアクセスのために使用できません。<br /><br /> 2 = すべてセカンダリ repl; で、データベースへの接続を許可 ication の読み取り専用アクセス。|  
|secondary_allow_connections_desc|**nvarchar (256)**|いいえ<br /><br /> All|  
|last_commit|**datetimeoffset**|最後に、データベースにコミットされたトランザクションの時刻。 場合は、プライマリ データベースで取得される、プライマリ データベースで最後のコミット時間を示します。 場合は、セカンダリ データベースで取得される、セカンダリ データベースで最後のコミット時間を示します。 レプリケーション リンクのプライマリがダウンした場合、セカンダリ データベースを取得する場合は、どの時点で、セカンダリが解消されるまでことを示します。|
  
> [!NOTE]  
>  セカンダリ データベース (セクション 4.2) では、そのデータベースの行を削除することでレプリケーション リレーションシップが終了したかどうか、 **sys.dm_geo_replication_link_status**ビューは表示されなくなります。  
  
## <a name="permissions"></a>アクセス許可  
 View_database_state のアクセス許可を持つアカウントを照会できます**sys.dm_geo_replication_link_status**します。  
  
## <a name="example"></a>例  
 レプリケーションに遅れると、セカンダリ データベースの最後のレプリケーションの時刻を表示します。  
  
```  
SELECT   
     link_guid  
   , partner_server  
   , last_replication  
   , replication_lag_sec   
FROM sys.dm_geo_replication_link_status;  
```  
  
## <a name="see-also"></a>関連項目  
 [ALTER DATABASE &#40;Azure SQL Database&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [sys.geo_replication_links &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [sys.dm_operation_status &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
  
  
