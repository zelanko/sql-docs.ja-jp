---
title: sys.dm_geo_replication_link_status (Azure SQL データベース) |Microsoft ドキュメント
ms.custom: ''
ms.date: 10/13/2016
ms.prod: ''
ms.prod_service: sql-database
ms.reviewer: ''
ms.service: sql-database
ms.component: dmv's
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- dm_geo_replication_link_status
- dm_geo_replication_link_status_TSQL
- sys.dm_geo_replication_link_status
- sys.dm_geo_replication_link_status_TSQL
helpviewer_keywords:
- dm_geo_replication_link_status dynamic management view
- sys.dm_geo_replication_link_status dynamic management view
ms.assetid: d763d679-470a-4c21-86ab-dfe98d37e9fd
caps.latest.revision: 15
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 60a6bf3758e947539d0d9afcd008555e75a1473b
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="sysdmgeoreplicationlinkstatus-azure-sql-database"></a>sys.dm_geo_replication_link_status (Azure SQL データベース)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  地理的レプリケーション パートナーでのプライマリおよびセカンダリ データベース間でのレプリケーション リンクごとに 1 行が含まれています。 これには、プライマリとセカンダリの両方のデータベースが含まれます。 特定のプライマリ データベースの 1 つ以上の連続レプリケーション リンクが存在する場合、次の表は、各リレーションシップの行を格納します。 ビューは、論理マスターを含む、すべてのデータベースに作成されます。 ただし、論理マスターでこのビューに対してクエリを実行すると、空のセットが返されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|link_guid|**uniqueidentifier**|レプリケーション リンクの一意の ID。|  
|partner_server|**sysname**|リンクされたデータベースを含む論理サーバーの名前です。|  
|partner_database|**sysname**|リンクの論理サーバー上のリンクされたデータベースの名前です。|  
|last_replication|**datetimeoffset**|プライマリ データベースのクロックに基づいて、セカンダリで最後のトランザクションの受信確認のタイムスタンプ。 この値は、プライマリ データベースでのみで使用できます。|  
|replication_lag_sec|**int**|Last_replication 値と、プライマリ データベースのクロックに基づくプライマリ上でそのトランザクションのコミットのタイムスタンプ間時間差 (秒)。  この値は、プライマリ データベースでのみで使用できます。|  
|replication_state|**tinyint**|このデータベースには、いずれかの地理的レプリケーションの状態: です。<br /><br /> 1 = シード処理中です。 地理的レプリケーションの対象がシード中は、2 つのデータベースがまだ同期されていません。 シードが完了するまでは、セカンダリ データベースに接続することはできません。 プライマリからセカンダリ データベースを削除すると、シード操作がキャンセルされます。<br /><br /> 2 = キャッチアップです。 セカンダリ データベースはトランザクション全体で一貫性のある状態でありが常に、プライマリ データベースと同期されています。<br /><br /> 4 = 保留します。 これはアクティブな連続コピー リレーションシップではありません。 通常、この状態は、インターリンクに利用できる帯域幅がプライマリ データベース上のトランザクション アクティビティのレベルに対して不十分であることを示します。 ただし、連続コピー リレーションシップはそのまま保持されます。|  
|replication_state_desc|**nvarchar (256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|ロール (role)|**tinyint**|いずれかの地理的レプリケーション ロール:<br /><br /> 0 = プライマリです。 Database_id は、地理的レプリケーション パートナーシップのプライマリ データベースを参照します。<br /><br /> 1 = セカンダリです。  Database_id は、地理的レプリケーション パートナーシップのプライマリ データベースを参照します。|  
|role_desc|**nvarchar (256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|いずれかのセカンダリ型。<br /><br /> 0 = ダイレクトではありません、セカンダリ データベースに対する接続は許可し、データベースは読み取りアクセスで使用できません。<br /><br /> 2 = all セカンダリ repl; 内のデータベースに接続が許可されている読み取り専用アクセスの ication します。|  
|secondary_allow_connections_desc|**nvarchar (256)**|いいえ<br /><br /> すべて|  
|last_commit|**datetimeoffset**|データベースにコミットされた最後のトランザクションの時刻。 プライマリ データベースで取得された場合は、プライマリ データベースで最後のコミット時間を示します。 セカンダリ データベースで取得された場合は、セカンダリ データベースで最後のコミット時間を示します。 取得された場合は、セカンダリ データベースで、レプリケーション リンクのプライマリがダウンした場合は、どの時点で、セカンダリが解消されるまでことを示します。|
  
> [!NOTE]  
>  セカンダリ データベース (セクション 4.2) データベースに行を削除することで、レプリケーション関係が終了したかどうか、 **sys.dm_geo_replication_link_status**ビューは表示されなくなります。  
  
## <a name="permissions"></a>権限  
 View_database_state のアクセス許可を持つアカウントを照会できます**sys.dm_geo_replication_link_status**です。  
  
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
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Azure SQL データベース&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [sys.geo_replication_links &#40;Azure SQL データベース&#41;](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [sys.dm_operation_status &#40;Azure SQL データベース&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)  
  
  
