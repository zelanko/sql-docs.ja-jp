---
title: sys.availability_groups_cluster (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.availability_groups_cluster
- availability_groups_cluster
- availability_groups_cluster_TSQL
- sys.availability_groups_cluster_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_groups_cluster catalog view
- Availability Groups [SQL Server], WSFC clusters
ms.assetid: d0f4683f-cdf0-4227-8b68-720ffe58f158
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 1173764b8726aebc2e53cef103f341b95e8c82fa
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52511086"
---
# <a name="sysavailabilitygroupscluster-transact-sql"></a>sys.availability_groups_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Always On 可用性グループごとの行で、Windows Server フェールオーバー クラスタ リング (WSFC) を返します。 各行には、WSFC クラスターからの可用性グループ メタデータが含まれます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|可用性グループの一意識別子 (GUID)。|  
|**name**|**sysname**|可用性グループの名前。 これはユーザー指定の名前であり、Windows Server フェールオーバー クラスター (WSFC) 内で一意であることが必要です。|  
|**resource_id**|**nvarchar(40)**|WSFC クラスター リソースのリソース ID。|  
|**resource_group_id**|**nvarchar(40)**|可用性グループの WSFC クラスター リソース グループのリソース グループ ID。|  
|**failure_condition_level**|**int**|自動フェールオーバーをトリガーする必要のあるユーザー定義のエラー状態レベル。次のいずれかの整数値です。<br /><br /> 1:次のいずれかが発生した場合に自動フェールオーバーを開始する必要があることを指定します。 <br />-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービスが停止します。<br />WSFC フェールオーバー クラスターに接続するため、可用性グループのリースでは、サーバー インスタンスから ACK を受信しないため、有効期限が切れます。 詳細については、次を参照してください。[動作方法。SQL Server Always On のリース タイムアウト](https://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx)します。<br /><br /> 2:次のいずれかが発生した場合に自動フェールオーバーを開始する必要があることを指定します。  <br />-インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クラスター、およびユーザー指定に接続していない**health_check_timeout**可用性グループのしきい値を超えました。 <br />-可用性レプリカは障害が発生した状態です。 <br />3:孤立したスピンロック、重大な書き込みアクセス違反、ダンプが多すぎるなどの重大な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部エラーが発生した場合に自動フェールオーバーを開始する必要があることを指定します。 これが既定値です。 <br />4:[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部リソース プールに永続的なメモリ不足の状態があるなど、中程度の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部エラーが発生した場合に自動フェールオーバーを開始する必要があることを指定します。<br />5:以下のような任意の修飾エラー状態に対して自動フェールオーバーを開始する必要があることを指定します。<br />-SQL エンジンのワーカー スレッドの枯渇します。 <br />-、解決不可能なデッドロックを検出します。<br /><br /> エラー状態レベルの範囲は 1 ～ 5 で、レベル 1 が最も制限が緩く、レベル 5 が最も制限の厳しい指定です。 任意の状態レベルは、それより制限が緩いすべてのレベルを含みます。 したがって、最も厳しい状態レベル 5 にはそれより制限が緩い状態レベル (1 ～ 4) が含まれ、レベル 4 にはレベル 1 ～ 3 が含まれます。以下同様です。<br /><br /> この値を変更するには、FAILURE_CONDITION_LEVEL オプションを使用して、 [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント。|  
|**health_check_timeout**|**int**|待機時間 (ミリ秒単位)、 [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md)システム ストアド プロシージャをサーバーの状態の情報が返されるサーバー インスタンスが速度低下またはハングがあると見なされます。 既定値は 30000 ミリ秒 (30 秒) です。<br /><br /> この値を変更するには、HEALTH_CHECK_TIMEOUT オプションを使用して[ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント。|  
|**automated_backup_preference**|**tinyint**|この可用性グループの可用性データベースでバックアップを実行する場合の優先される場所。 次のいずれかの値です。<br /><br /> 0:[プライマリ]。 バックアップを常にプライマリ レプリカで実行する必要があります。<br />1:[セカンダリのみ]。 セカンダリ レプリカでのバックアップの実行が優先されます。<br />2:[セカンダリを優先]。 セカンダリ レプリカでのバックアップの実行が優先されますが、バックアップ操作に使用できるセカンダリ レプリカがない場合は、プライマリ レプリカでバックアップを実行してもかまいません。 これは既定の動作です。<br />3:[任意のレプリカ]。 バックアップをプライマリ レプリカとセカンダリ レプリカのどちらで実行するかについての優先指定はありません。<br /><br /> 詳細については、次を参照してください。[アクティブなセカンダリ。セカンダリ レプリカでバックアップ&#40;Always On 可用性グループ&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)します。|  
|**automated_backup_preference_desc**|**nvarchar(60)**|説明**automated_backup_preference**、1 つの。<br /><br /> PRIMARY<br /><br /> SECONDARY_ONLY<br /><br /> SECONDARY<br /><br /> なし|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 サーバー インスタンスに対する VIEW ANY DEFINITION 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sys.availability_replicas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [可用性グループの監視 &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [可用性グループの監視 &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
