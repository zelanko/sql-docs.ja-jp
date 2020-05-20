---
title: dm_hadr_availability_replica_cluster_states (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_availability_replica_cluster_states_TSQL
- dm_hadr_availability_replica_cluster_states
- sys.dm_hadr_availability_replica_cluster_states
- dm_hadr_availability_replica_cluster_states_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_availability_replica_cluster_states dynamic management view
ms.assetid: 2e0dd780-6a71-4f4b-b7f7-6e063bec71d6
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: cdc5edf1c752478c96cd0f7e4cb3eef441bd078c
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82811908"
---
# <a name="sysdm_hadr_availability_replica_cluster_states-transact-sql"></a>dm_hadr_availability_replica_cluster_states (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Windows Server フェールオーバー クラスタリング (WSFC) クラスター内のすべての AlwaysOn 可用性グループ (レプリカの場所を問いません) の AlwaysOn 可用性レプリカ (結合状態を問いません) ごとに 1 行のデータを返します。  
  
##  <a name="connected_state"></a>  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**replica_id**|**uniqueidentifier**|可用性レプリカの一意識別子。|  
|**replica_server_name**|**nvarchar(256)**|レプリカをホストするのインスタンスの名前 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。|  
|**group_id**|**uniqueidentifier**|可用性グループの一意識別子。|  
|**join_state**|**tinyint**|0 = 未結合<br /><br /> 1 = 結合済み、スタンドアロン<br /><br /> 2 = 参加済み、フェールオーバークラスターインスタンス|  
|**join_state_desc**|**nvarchar(60)**|NOT_JOINED<br /><br /> JOINED_STANDALONE<br /><br /> JOINED_FAILOVER_CLUSTER_INSTANCE|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [可用性グループの監視 &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)  
  
  
