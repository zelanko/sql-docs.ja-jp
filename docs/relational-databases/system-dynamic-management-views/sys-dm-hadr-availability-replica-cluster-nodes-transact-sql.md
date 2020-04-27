---
title: dm_hadr_availability_replica_cluster_nodes (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_hadr_availability_replica_cluster_nodes
- sys.dm_hadr_availability_replica_cluster_nodes_TSQL
- dm_hadr_availability_replica_cluster_nodes_TSQL
- sys.dm_hadr_availability_replica_cluster_nodes
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_availability_replica_cluster_nodes dynamic management view
ms.assetid: dbd7e416-badd-4332-a45c-438aa0145a99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a5e33207fd6fd14fe4fe2f8bcc732b2f762f3723
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "67900623"
---
# <a name="sysdm_hadr_availability_replica_cluster_nodes-transact-sql"></a>sys.dm_hadr_availability_replica_cluster_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Windows Server フェールオーバー クラスタリング (WSFC) クラスター内の AlwaysOn 可用性グループの可用性レプリカ (結合状態に関係なく) ごとに 1 行のデータを返します。  

 ##  <a name="connected_state"></a>  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**group_name**|**nvarchar(256)**|可用性グループの名前。|  
|**replica_server_name**|**nvarchar(256)**|レプリカをホストするの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスの名前。|  
|**node_name**|**nvarchar(256)**|クラスターノードの名前。|  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;可用性グループの監視](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
