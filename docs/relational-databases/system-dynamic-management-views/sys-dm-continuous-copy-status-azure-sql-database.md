---
title: sys.dm_continuous_copy_status (Azure SQL データベース) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_continuous_copy_status_TSQL
- dm_continuous_copy_status_TSQL
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
dev_langs:
- TSQL
helpviewer_keywords:
- dm_continuous_copy_status
- sys.dm_continuous_copy_status
ms.assetid: 411b2e71-4421-4ef5-900d-5af068750899
author: stevestein
ms.author: sstein
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: cace39108f3f99d5c165f42b4337e837e1fb7c5c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68121025"
---
# <a name="sysdmcontinuouscopystatus-azure-sql-database"></a>sys.dm_continuous_copy_status (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  各ユーザー データベース (V11) は現在、Geo レプリケーションの連続コピー リレーションシップに関与している行を返します。 1 つ以上の連続コピー リレーションシップが特定のプライマリ データベースに対して開始された場合、このテーブルには、アクティブなセカンダリ データベースごとに 1 つの行が含まれています。  
  
使用する必要がある SQL Database V12 を使用している場合[sys.dm_geo_replication_link_status](../../relational-databases/system-dynamic-management-views/sys-dm-geo-replication-link-status-azure-sql-database.md) (ため*sys.dm_continuous_copy_status* V11 にのみ適用されます)。

  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**copy_guid**|**uniqueidentifier**|レプリカ データベースの一意の ID。|  
|**partner_server**|**sysname**|リンクされた SQL データベース サーバーの名前。|  
|**partner_database**|**sysname**|リンクされた SQL データベース サーバー上にあるリンクされたデータベースの名前。|  
|**last_replication**|**datetimeoffset**|最後のタイムスタンプは、レプリケートされたトランザクションを適用します。|  
|**replication_lag_sec**|**int**|秒で、現在の時刻とアクティブ セカンダリ データベースによって確認されていない、プライマリ データベースで最後に正常にコミットされたトランザクションのタイムスタンプの差を時間。|  
|**replication_state**|**tinyint**|このデータベースの連続コピー レプリケーションの状態。 使用可能な値とその説明を次に示します。<br /><br /> 1:シード処理します。 レプリケーションの対象がシード中と、トランザクション一貫性のない状態にあります。 シードが完了するまで、アクティブなセカンダリ データベースに接続できません。 <br />2:遅れを取り戻しています。 アクティブなセカンダリ データベースが遅れを取り戻して現在プライマリ データベースにし、トランザクション上一貫性のある状態にあります。<br />3:再シード処理します。 アクティブなセカンダリ データベースは復旧不可能なレプリケーションの失敗によって自動的に再シードされています。<br />4:一時中断。 これは、アクティブな連続コピー リレーションシップではありません。 通常、この状態は、インターリンクに利用できる帯域幅がプライマリ データベース上のトランザクション アクティビティのレベルに対して不十分であることを示します。 ただし、連続コピー リレーションシップはそのままです。|  
|**replication_state_desc**|**nvarchar (256)**|Replication_state のいずれかの説明です。<br /><br /> SEEDING<br /><br /> CATCH_UP<br /><br /> RE_SEEDING<br /><br /> SUSPENDED|  
|**is_rpo_limit_reached**|**bit**|これは常に 0 に設定します。|  
|**is_target_role**|**bit**|0 = コピー リレーションシップのソース<br /><br /> 1 = コピー リレーションシップのターゲット|  
|**is_interlink_connected**|**bit**|1 = インターリンクは接続されています。<br /><br /> 0 = インター リンクが切断されています。|  
  
## <a name="permissions"></a>アクセス許可  
 データを取得するメンバーシップが必要です、 **db_owner**データベース ロール。 メンバー、dbo ユーザー、 **dbmanager**データベース ロール、および、sa ログインはすべてのクエリも、このビュー。  
  
## <a name="remarks"></a>コメント  
 **Sys.dm_continuous_copy_status**にビューが作成、**リソース**データベースし、は、論理マスターを含む、すべてのデータベースに表示されます。 ただし、論理マスターでこのビューをクエリには、空のセットが返されます。  
  
 データベース、そのデータベース内の行の連続コピー リレーションシップが終了した場合、 **sys.dm_continuous_copy_status**ビューは表示されなくなります。  
  
 ように、 **sys.dm_database_copies**ビュー、 **sys.dm_continuous_copy_status**をデータベースがプライマリまたはアクティブなのセカンダリ データベースの連続コピー リレーションシップの状態を反映. 異なり**sys.dm_database_copies**、 **sys.dm_continuous_copy_status**操作やパフォーマンスに関する詳細を提供する複数の列が含まれています。 これらの列を含める**last_replication**、および**replication_lag_sec**.  
  
## <a name="see-also"></a>関連項目  
 [sys.dm_database_copies &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-database-copies-azure-sql-database.md)   
 [アクティブ Geo レプリケーションのストアド プロシージャ&#40;TRANSACT-SQL&#41;](https://msdn.microsoft.com/library/81658ee4-4422-4d73-bf7a-86a07422cb0d)  
  
  
