---
title: sys.availability_groups (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.availability_groups_TSQL
- availability_groups_TSQL
- sys.availability_groups
- availability_groups
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.availability_groups catalog view
ms.assetid: da7fa55f-c008-45d9-bcfc-3513b02d9e71
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b6992cceb19d0fe39c1e53e36535949a94907295
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67942653"
---
# <a name="sysavailabilitygroups-transact-sql"></a>sys.availability_groups (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  SQL Server のローカル インスタンスが可用性レプリカをホストしている各可用性グループの行を返します。 各行には、可用性グループ メタデータのキャッシュされたコピーが含まれます。  
   
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|可用性グループの一意の識別子 (GUID)。|  
|**name**|**sysname**|可用性グループの名前。 これはユーザー指定の名前であり、Windows Server フェールオーバー クラスター (WSFC) 内で一意であることが必要です。|  
|**resource_id**|**nvarchar(40)**|WSFC クラスター リソースのリソース ID。|  
|**resource_group_id**|**nvarchar(40)**|可用性グループの WSFC クラスター リソース グループのリソース グループ ID。|  
|**failure_condition_level**|**int**|ユーザー定義のエラー条件レベルを自動フェールオーバーをトリガーすることは、この表のすぐ下の表に示す整数値のいずれかです。<br /><br /> エラー状態レベルの範囲は 1 ～ 5 で、レベル 1 が最も制限が緩く、レベル 5 が最も制限の厳しい指定です。 任意の状態レベルは、それより制限が緩いすべてのレベルを含みます。 したがって、最も厳しい状態レベル 5 にはそれより制限が緩い状態レベル (1 から 4) が含まれ、レベル 4 にはレベル 1 から 3 が含まれます。以下同様です。<br /><br /> この値を変更するには、FAILURE_CONDITION_LEVEL オプションを使用して、 [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント。|  
|**health_check_timeout**|**int**|待機時間 (ミリ秒単位)、 [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md)システム ストアド プロシージャをサーバーの状態の情報が返されるサーバー インスタンスが速度低下またはハングがあると見なされます。 既定値は 30000 ミリ秒 (30 秒) です。<br /><br /> この値を変更するには、HEALTH_CHECK_TIMEOUT オプションを使用して、 [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント。|  
|**automated_backup_preference**|**tinyint**|この可用性グループ内の可用性データベースのバックアップを実行する推奨される場所。 使用可能な値とその説明を次に示します。<br /><br /> <br /><br /> 0:プライマリにします。 常のプライマリ レプリカでは、バックアップが実行する必要があります。<br /><br /> 1:セカンダリでのみ使用します。 セカンダリ レプリカでバックアップを実行することをお勧めします。<br /><br /> 2:セカンダリを優先します。 プライマリ レプリカでセカンダリ レプリカのことをお勧めが実行するバックアップのバックアップを実行することは許容されるは、バックアップ操作に使用できるセカンダリ レプリカがない場合です。 これは既定の動作です。<br /><br /> 3:任意のレプリカ。 プライマリ レプリカまたはセカンダリ レプリカでバックアップを実行するかどうかについての基本設定がありません。<br /><br /> <br /><br /> 詳細については、「[アクティブなセカンダリ:セカンダリ レプリカでのバックアップ &#40;Always On 可用性グループ&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)」を参照してください。|  
|**automated_backup_preference_desc**|**nvarchar(60)**|説明**automated_backup_preference**、1 つの。<br /><br /> PRIMARY<br /><br /> SECONDARY_ONLY<br /><br /> SECONDARY<br /><br /> なし|  
|**version**|**smallint**|Windows フェールオーバー クラスターに格納されている可用性グループ メタデータのバージョン。 新機能が追加されたときに、このバージョン番号はインクリメントされます。|  
|**basic_features**|**bit**|これは、基本的な可用性グループであるかどうかを指定します。 詳細については、「[基本的な可用性グループ &#40;AlwaysOn 可用性グループ&#41;](../../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md)」を参照してください。|  
|**dtc_support**|**bit**|この可用性グループの DTC サポートが有効になっているかどうかを指定します。 **DTC_SUPPORT**オプションの**CREATE AVAILABILITY GROUP**この設定を制御します。|  
|**db_failover**|**bit**|可用性グループのフェールオーバー データベース正常性の状態をサポートするかどうかを指定します。 **DB_FAILOVER**オプションの**CREATE AVAILABILITY GROUP**この設定を制御します。|  
|**is_distributed**|**bit**|これは、分散型可用性グループであるかどうかを指定します。 詳細については、「[Distributed Availability Groups &#40;Always On Availability Groups&#41; (分散型可用性グループ (Always On 可用性グループ))](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)」を参照してください。|  
  
## <a name="failure-condition-level--values"></a>エラー条件レベルの値  
 次の表の可能性のあるエラー条件レベル、 **failure_condition_level**列。  
  
|値|エラー状態|  
|-----------|-----------------------|  
|1|次のいずれかが発生した場合に自動フェールオーバーを開始する必要があることを指定します。<br /><br /> <br /><br /> -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービスが停止します。<br /><br /> WSFC フェールオーバー クラスターに接続するため、可用性グループのリースでは、サーバー インスタンスから ACK を受信しないため、有効期限が切れます。 詳細については、「[How It Works:SQL Server Always On Lease Timeout (動作方法: SQL Server AlwaysOn のリース タイムアウト)](https://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx)」を参照してください。|  
|2|次のいずれかが発生した場合に自動フェールオーバーを開始する必要があることを指定します。<br /><br /> <br /><br /> -インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クラスター、およびユーザー指定に接続していない**health_check_timeout**可用性グループのしきい値を超えました。<br /><br /> -可用性レプリカは障害が発生した状態です。|  
|3|孤立したスピンロック、重大な書き込みアクセス違反、ダンプが多すぎるなどの重大な [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部エラーが発生した場合に自動フェールオーバーを開始する必要があることを指定します。<br /><br /> これは既定値です。|  
|4|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部リソース プールに永続的なメモリ不足の状態があるなど、中程度の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内部エラーが発生した場合に自動フェールオーバーを開始する必要があることを指定します。|  
|5|以下のような任意の修飾エラー状態に対して自動フェールオーバーを開始する必要があることを指定します。<br /><br /> <br /><br /> -SQL エンジンのワーカー スレッドの枯渇します。<br /><br /> -、解決不可能なデッドロックを検出します。|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 サーバー インスタンスに対する VIEW ANY DEFINITION 権限が必要です。  
  
## <a name="see-also"></a>関連項目  
 [sys.availability_replicas &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [可用性グループの監視 &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [可用性グループの監視 &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
