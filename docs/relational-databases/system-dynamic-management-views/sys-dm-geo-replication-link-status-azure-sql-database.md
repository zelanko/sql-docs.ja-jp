---
title: sys.dm_geo_replication_link_status
titleSuffix: Azure SQL Database
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
ms.custom: seo-dt-2019
ms.openlocfilehash: 8bdf74e6ee774d9a0cc8e3d9128c659b75287511
ms.sourcegitcommit: d1f6da6f0f5e9630261cf733c64958938a3eb859
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79198229"
---
# <a name="sysdm_geo_replication_link_status-azure-sql-database"></a>sys.dm_geo_replication_link_status (Azure SQL Database)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  geo レプリケーション パートナーシップのプライマリ データベースとセカンダリ データベース間のレプリケーション リンクごとに 1 行の行が含まれます。 これには、プライマリ データベースとセカンダリ データベースの両方が含まれます。 特定のプライマリ データベースについて複数の連続レプリケーション リンクが存在する場合、このテーブルには、各リレーションシップについて 1 行が含まれます。 このビューは、すべてのデータベース (論理 master データベースを含む) で作成されます。 ただし、論理 master データベースでこのビューにクエリを実行しても、空のセットが返されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|link_guid|**Uniqueidentifier**|レプリケーション リンクの一意の ID。|  
|partner_server|**Sysname**|リンクされたデータベースを含む SQL データベース サーバーの名前。|  
|partner_database|**Sysname**|リンクされた SQL データベース サーバー上にあるリンクされたデータベースの名前。|  
|last_replication|**Datetimeoffset**|プライマリ データベース クロックに基づくセカンダリによる最後のトランザクションの確認応答のタイムスタンプ。 この値は、プライマリ データベースでのみ使用できます。|  
|replication_lag_sec|**Int**|プライマリ データベース クロックに基づいて、プライマリでのlast_replication値とトランザクションのコミットのタイムスタンプの間の時間差 (秒単位)。  この値は、プライマリ データベースでのみ使用できます。|  
|replication_state|**tinyint**|このデータベースの geo レプリケーションの状態。:<br /><br /> 1 = シード処理。 geo レプリケーション ターゲットはシードされますが、2 つのデータベースはまだ同期されていません。 シード処理が完了するまで、セカンダリ データベースに接続できません。 プライマリからセカンダリ データベースを削除すると、シード処理操作がキャンセルされます。<br /><br /> 2 = キャッチアップ。 セカンダリ データベースはトランザクションで一貫性のある状態にあり、プライマリ データベースと常に同期されています。<br /><br /> 4 = 中断。 これは、アクティブな連続コピー関係ではありません。 通常、この状態は、インターリンクに利用できる帯域幅がプライマリ データベース上のトランザクション アクティビティのレベルに対して不十分であることを示します。 ただし、連続コピーリレーションシップはそのまま残ります。|  
|replication_state_desc|**nvarchar(256)**|PENDING<br /><br /> SEEDING<br /><br /> CATCH_UP|  
|role|**tinyint**|geo レプリケーションロール(以下のいずれか):<br /><br /> 0 = プライマリ。 database_idは、geo レプリケーション パートナーシップのプライマリ データベースを参照します。<br /><br /> 1 = セカンダリ。  database_idは、geo レプリケーション パートナーシップのプライマリ データベースを参照します。|  
|role_desc|**nvarchar(256)**|PRIMARY<br /><br /> SECONDARY|  
|secondary_allow_connections|**tinyint**|セカンダリタイプ(以下のいずれか):<br /><br /> 0 = セカンダリ データベースへの直接接続は許可されず、データベースは読み取りアクセスに使用できません。<br /><br /> 2 = すべての接続は、読み取り専用アクセスの場合は、セカンダリ repl;ication 内のデータベースに許可されます。|  
|secondary_allow_connections_desc|**nvarchar(256)**|いいえ<br /><br /> All|  
|last_commit|**Datetimeoffset**|データベースにコミットされた最後のトランザクションの時刻。 プライマリ データベースで取得された場合、プライマリ データベースの最後のコミット時間を示します。 セカンダリ データベースで取得された場合、セカンダリ データベースの最後のコミット時間を示します。 レプリケーション リンクのプライマリがダウンしているときにセカンダリ データベースで取得した場合、セカンダリ がどの時点で追いついたかを示します。|
  
> [!NOTE]  
>  セカンダリ データベース (セクション 4.2) を削除してレプリケーション リレーションシップを終了すると **、sys.dm_geo_replication_link_status**ビューでそのデータベースの行が削除されます。  
  
## <a name="permissions"></a>アクセス許可  
 view_database_state権限を持つアカウントは **、sys.dm_geo_replication_link_status**を照会できます。  
  
## <a name="example"></a>例  
 セカンダリ データベースのレプリケーションの遅延と最後のレプリケーション時間を表示します。  
  
```  
SELECT   
     link_guid  
   , partner_server  
   , last_replication  
   , replication_lag_sec   
FROM sys.dm_geo_replication_link_status;  
```  
  
## <a name="see-also"></a>関連項目  
 [データベースの変更&#40;Azure SQL データベース&#41;](../../t-sql/statements/alter-database-azure-sql-database.md)   
 [azure SQL データベース&#41;&#40;sys.geo_replication_links](../../relational-databases/system-dynamic-management-views/sys-geo-replication-links-azure-sql-database.md)   
 [azure SQL データベース&#41;&#40;sys.dm_operation_status](../../relational-databases/system-dynamic-management-views/sys-dm-operation-status-azure-sql-database.md)   
 [sp_wait_for_database_copy_sync](../system-stored-procedures/active-geo-replication-sp-wait-for-database-copy-sync.md)
  
