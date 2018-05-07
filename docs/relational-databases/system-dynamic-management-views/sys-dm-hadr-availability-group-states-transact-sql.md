---
title: sys.dm_hadr_availability_group_states (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_availability_group_states
- sys.dm_hadr_availability_group_states_TSQL
- dm_hadr_availability_group_states_TSQL
- dm_hadr_availability_group_states
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_availability_group_states dynamic management view
ms.assetid: d18019dd-f8dc-4492-b035-b1a639369b65
caps.latest.revision: 43
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fc182f6d184368dee73bb44e11c7f3f8ab99a299
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmhadravailabilitygroupstates-transact-sql"></a>sys.dm_hadr_availability_group_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Always On 可用性グループごとのローカル インスタンス上の可用性レプリカを保持する行を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 各行には、特定の可用性グループの正常性を定義する状態が表示されます。  
  
> [!NOTE]  
>  完全な一覧を取得するクエリ、 [sys.availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)カタログ ビューです。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|可用性グループの一意識別子。|  
|**primary_replica**|**varchar(128)**|現在のプライマリ レプリカをホストしているサーバー インスタンスの名前。<br /><br /> NULL = プライマリ レプリカでないか、WSFC フェールオーバー クラスターと通信できません。|  
|**primary_recovery_health**|**tinyint**|プライマリ レプリカの復旧の正常性状態を示します。次のいずれかになります。<br /><br /> 0 = 実行中<br /><br /> 1 = オンライン<br /><br /> NULL<br /><br /> セカンダリ レプリカで、 **primary_recovery_health**列は NULL です。|  
|**primary_recovery_health_desc**|**nvarchar(60)**|説明**primary_replica_health**,、1 つの。<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**secondary_recovery_health**|**tinyint**|レプリカのセカンダリ レプリカでの 1 つの復旧の正常性を示します。<br /><br /> 0 = 実行中<br /><br /> 1 = オンライン<br /><br /> NULL<br /><br /> プライマリ レプリカの場合、 **secondary_recovery_health**列は NULL です。|  
|**secondary_recovery_health_desc**|**nvarchar(60)**|説明**secondary_recovery_health**,、1 つの。<br /><br /> ONLINE_IN_PROGRESS<br /><br /> ONLINE<br /><br /> NULL|  
|**synchronization_health**|**tinyint**|更新プログラムのロールアップを反映して、 **synchronization_health**すべての可用性レプリカの可用性グループです。 使用可能な値とその説明のとおりです。<br /><br /> 0: 正常ではありません。 正常ながある可用性レプリカがまったく**synchronization_health** (2 = HEALTHY)。<br /><br /> 1: 部分的に正常な状態です。 一部の可用性レプリカの同期状態は正常です。<br /><br /> 2: 正常な状態です。 すべての可用性レプリカの同期状態は正常です。<br /><br /> レプリカの同期状態については、次を参照してください。、 **synchronization_health**内の列[sys.dm_hadr_availability_replica_states &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql.md)です。|  
|**synchronization_health_desc**|**nvarchar(60)**|説明**synchronization_health**,、1 つの。<br /><br /> NOT_HEALTHY<br /><br /> PARTIALLY_HEALTHY<br /><br /> HEALTHY|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [可用性グループの監視と &#40; です。Transact SQL と &#41; です。](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)   
 [Always On 可用性グループの動的管理ビューおよび関数&#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)  
  
  
