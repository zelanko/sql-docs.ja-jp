---
title: sys.availability_groups_cluster (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
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
caps.latest.revision: 16
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 6ffcb675b106536741a9edd298296485773a3ac1
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33182108"
---
# <a name="sysavailabilitygroupscluster-transact-sql"></a>sys.availability_groups_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Always On 可用性グループごとの行で、Windows Server フェールオーバー クラスタ リング (WSFC) を返します。 各行には、WSFC クラスターからの可用性グループ メタデータが含まれます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|可用性グループの一意識別子 (GUID)。|  
|**name**|**sysname**|可用性グループの名前。 これはユーザー指定の名前であり、Windows Server フェールオーバー クラスター (WSFC) 内で一意であることが必要です。|  
|**resource_id**|**nvarchar(40)**|WSFC クラスター リソースのリソース ID。|  
|**resource_group_id**|**nvarchar(40)**|可用性グループの WSFC クラスター リソース グループのリソース グループ ID。|  
|**failure_condition_level**|**int**|自動フェールオーバーをトリガーする必要のあるユーザー定義のエラー状態レベル。次のいずれかの整数値です。<br /><br /> 1: 自動フェールオーバーを開始することを指定します、次のいずれかが発生したとき。 <br />-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービスが停止します。<br />-WSFC フェールオーバー クラスターに接続するための可用性グループのリースは、サーバー インスタンスから ACK を受信しないために期限が切れます。 詳細については、「 [動作方法: SQL Server Always On のリース タイムアウト](http://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx)」を参照してください。<br /><br /> 2: 自動フェールオーバーを開始することを指定します、次のいずれかが発生したとき。  <br />-インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クラスター、およびユーザー指定に接続していない**health_check_timeout**可用性グループのしきい値を超えた。 <br />可用性レプリカがエラー状態です。 <br />3: 重要なので、自動フェールオーバーを開始することを指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]孤立したスピンロック、深刻な書き込みアクセス違反、ダンプが多すぎるなどの内部エラーが発生します。 これが既定値です。 <br />4: 度が中程度、自動フェールオーバーを開始することを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で永続的なメモリ不足の状態などの内部エラーが発生、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内部リソース プールです。<br />5: を含む任意の限定されたエラー条件に対して自動フェールオーバーを開始することを指定します。<br />-SQL エンジンのワーカー スレッドの枯渇しています。 <br />解決不可能なデッドロックの検出。<br /><br /> エラー状態レベルの範囲は 1 ～ 5 で、レベル 1 が最も制限が緩く、レベル 5 が最も制限の厳しい指定です。 任意の状態レベルは、それより制限が緩いすべてのレベルを含みます。 したがって、最も厳しい状態レベル 5 にはそれより制限が緩い状態レベル (1 ～ 4) が含まれ、レベル 4 にはレベル 1 ～ 3 が含まれます。以下同様です。<br /><br /> この値を変更するには、FAILURE_CONDITION_LEVEL オプションを使用して、 [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。|  
|**health_check_timeout**|**int**|待機時間 (ミリ秒単位)、 [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md)システム ストアド プロシージャによってサーバーの状態の情報を返す、前に、サーバー インスタンスが速度低下またはハングがあると見なされます。 既定値は 30000 ミリ秒 (30 秒) です。<br /><br /> この値を変更するには、HEALTH_CHECK_TIMEOUT オプションを使用して[ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。|  
|**automated_backup_preference**|**tinyint**|この可用性グループの可用性データベースでバックアップを実行する場合の優先される場所。 次の値のいずれかになります。<br /><br /> 0: プライマリです。 バックアップを常にプライマリ レプリカで実行する必要があります。<br />1: セカンダリのみです。 セカンダリ レプリカでのバックアップの実行が優先されます。<br />2: セカンダリを優先します。 セカンダリ レプリカでのバックアップの実行が優先されますが、バックアップ操作に使用できるセカンダリ レプリカがない場合は、プライマリ レプリカでバックアップを実行してもかまいません。 これは既定の動作です。<br />3: 任意のレプリカです。 バックアップをプライマリ レプリカとセカンダリ レプリカのどちらで実行するかについての優先指定はありません。<br /><br /> 詳細については、「 [アクティブなセカンダリ: セカンダリ レプリカでのバックアップ &#40;Always On 可用性グループ&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)」を参照してください。|  
|**automated_backup_preference_desc**|**nvarchar(60)**|説明**automated_backup_preference**,、1 つの。<br /><br /> PRIMARY<br /><br /> SECONDARY_ONLY<br /><br /> SECONDARY<br /><br /> なし|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 サーバー インスタンスに対する VIEW ANY DEFINITION 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [sys.availability_replicas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [可用性グループの監視と &#40; です。Transact SQL と &#41; です。](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [可用性グループの監視と &#40; です。Transact SQL と &#41; です。](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
