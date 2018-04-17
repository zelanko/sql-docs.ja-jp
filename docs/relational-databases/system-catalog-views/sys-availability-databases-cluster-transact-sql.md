---
title: sys.availability_databases_cluster (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.availability_databases_cluster_TSQL
- sys.availability_databases_cluster
- availability_databases_cluster_TSQL
- availability_databases_cluster
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.availability_databases_cluster catalog view
- Availability Groups [SQL Server], databases
ms.assetid: 8d9c57e5-7f39-4315-b466-92748231140a
caps.latest.revision: 14
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c781a3e8d09596096244e95855aa7ce0c71074e7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sysavailabilitydatabasescluster-transact-sql"></a>sys.availability_databases_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  インスタンスで可用性データベースごとに 1 つの行を含む[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Always On 可用性グループ、ローカル データベースにコピーするかどうかに関係なく、Windows Server フェールオーバー クラスタ リング (WSFC) クラスター内の可用性レプリカをホストしています。参加している可用性グループにまだです。  
  
> [!NOTE]  
>  データベースを可用性グループに追加すると、プライマリ データベースは自動的にそのグループに参加します。 セカンダリ データベースを可用性グループに参加させるには、各セカンダリ レプリカでそのデータベースを準備する必要があります。   
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**group_id**|**uniqueidentifier**|データベースが参加している可用性グループ (存在する場合) の一意の識別子。<br /><br /> NULL = データベースは可用性グループの可用性レプリカの一部ではありません。|  
|**group_database_id**|**uniqueidentifier**|データベースが参加している可用性グループ (存在する場合) 内のデータベースの一意の識別子。 **group_database_id**をデータベースが参加している可用性グループにすべてのセカンダリ レプリカとプライマリ レプリカでは、このデータベースに対して同じです。<br /><br /> NULL = データベースは、どの可用性グループの可用性レプリカの一部でもありません。|  
|**database_name**|**sysname**|可用性グループに追加されたデータベースの名前。|  
  
## <a name="permissions"></a>権限  
 場合、呼び出し元の**sys.availability_databases_cluster**データベース、ALTER ANY DATABASE、対応する行を確認するために必要な最低限の権限または VIEW ANY DATABASE のサーバー レベルの権限、または作成の所有者ではありませんDATABASE の権限、**マスター**データベース。  
  
## <a name="see-also"></a>参照  
 [sys.availability_groups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.dm_hadr_database_replica_states &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-states-transact-sql.md)   
 [sys.dm_hadr_database_replica_cluster_states &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-database-replica-cluster-states-transact-sql.md)   
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
