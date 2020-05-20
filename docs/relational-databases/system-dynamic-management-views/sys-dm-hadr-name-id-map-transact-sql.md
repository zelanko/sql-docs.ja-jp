---
title: dm_hadr_name_id_map (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_name_id_map
- sys.dm_hadr_name_id_map_TSQL
- dm_hadr_name_id_map
- dm_hadr_name_id_map_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_name_id_map dynamic management view
ms.assetid: e07bb8a9-37de-4a39-a257-950d7c3ae8fb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ef571a14c0d4679930f04ed0353231ba5a0c44aa
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82827941"
---
# <a name="sysdm_hadr_name_id_map-transact-sql"></a>dm_hadr_name_id_map (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  の現在のインスタンスが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可用性グループ id、wsfc リソース id、および Wsfc グループ id という3つの一意の id に結合した Always On 可用性グループのマッピングを示します。 このマッピングの目的は、WSFC リソースまたは WSFC グループの名前が変更されるシナリオを処理することです。  
   
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**ag_name**|**nvarchar(256)**|可用性グループの名前。 これは、Windows Server フェールオーバークラスター (WSFC) クラスター内で一意である必要があるユーザー指定の名前です。|  
|**ag_id**|**uniqueidentifier**|可用性グループの一意識別子 (GUID)。|  
|**ag_resource_id**|**nvarchar(256)**|WSFC クラスターのリソースとしての可用性グループの一意な ID。|  
|**ag_group_id**|**nvarchar(256)**|可用性グループの一意の WSFC グループ ID。|  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [Always On 可用性グループの動的管理ビューおよび関数 &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [Always On 可用性グループのカタログビュー &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [Transact-sql&#41;&#40;可用性グループの監視](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
