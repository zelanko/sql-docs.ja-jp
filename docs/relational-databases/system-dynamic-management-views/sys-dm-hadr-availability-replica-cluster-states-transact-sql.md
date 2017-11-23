---
title: "sys.dm_hadr_availability_replica_cluster_states (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_availability_replica_cluster_states_TSQL
- dm_hadr_availability_replica_cluster_states
- sys.dm_hadr_availability_replica_cluster_states
- dm_hadr_availability_replica_cluster_states_TSQL
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_availability_replica_cluster_states dynamic management view
ms.assetid: 2e0dd780-6a71-4f4b-b7f7-6e063bec71d6
caps.latest.revision: "12"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d7c173b034bd54bd187a78508d3d29b65b194406
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmhadravailabilityreplicaclusterstates-transact-sql"></a>sys.dm_hadr_availability_replica_cluster_states (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Windows Server フェールオーバー クラスタ リング (WSFC) クラスター内の各 Always On 可用性レプリカ (結合状態) に関係なくすべての Always On 可用性グループ (レプリカの場所) に関係なくの行を返します。  
  
##  <a name="connected_state"></a>  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|可用性レプリカの一意識別子。|  
|**replica_server_name**|**nvarchar (256)**|インスタンスの名前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリカをホストします。|  
|**group_id**|**uniqueidentifier**|可用性グループの一意識別子。|  
|**join_state**|**tinyint**|0 = 未結合<br /><br /> 1 = 結合済み、スタンドアロン インスタンス<br /><br /> 2 = 結合済み、フェールオーバー クラスター インスタンス|  
|**join_state_desc**|**nvarchar (60)**|NOT_JOINED<br /><br /> JOINED_STANDALONE_INSTANCE<br /><br /> JOINED_FAILOVER_CLUSTER_INSTANCE|  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [可用性グループの監視 &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
