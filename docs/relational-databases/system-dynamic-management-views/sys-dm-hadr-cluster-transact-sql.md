---
title: "sys.dm_hadr_cluster (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_cluster
- dm_hadr_cluster_HADR
- sys.dm_hadr_cluster_TSQL
- dm_hadr_cluster
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- sys.dm_hadr_cluster catalog view
- Availability Groups [SQL Server], WSFC clusters
ms.assetid: 13ce70e4-9d43-4a80-a826-099e6213bf85
caps.latest.revision: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 545712f1469d46c2d82dc2f36bd0084ceaf94daf
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysdmhadrcluster-transact-sql"></a>sys.dm_hadr_cluster (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  かどうか、Windows Server フェールオーバー クラスタ リング (WSFC) ノード インスタンスをホストするの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]対応した[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]に WSFC クォーラムがある**sys.dm_hadr_cluster**クラスター名と情報を公開する行を返しますクォーラムについて。 WSFC ノードがクォーラムを持たない場合、行は返されません。  
 > [!TIP]
 > 以降で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、この動的管理ビューは、Always On フェールオーバー クラスター インスタンスだけでなく Always On 可用性グループをサポートしています。

|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**cluster_name**|**nvarchar(128)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に対応した [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] のインスタンスをホストする WSFC クラスターの名前。|  
|**quorum_type**|**tinyint**|この WSFC クラスターで使用されているクォーラムの種類。次のいずれかになります。<br /><br /> 0 = ノード マジョリティ。 このクォーラム構成では、クラスター内の半数のノード (切り上げ) より 1 つ少ない数のノードの障害に耐えることができます。 たとえば、7 つのノードから成るクラスターの場合、このクォーラム構成では 3 つのノードの障害に対する耐性があります。<br /><br /> 1 = ノードおよびディスク マジョリティ。 ディスク監視がオンラインのままの場合、このクォーラム構成では、クラスター内の半数のノード (切り上げ) の障害に耐えることができます。 たとえば、6 つのノードから成るクラスターの場合、ディスク監視がオンラインのときは 3 つのノードの障害に対する耐性があります。 ディスク監視がオフラインになった場合、またはディスク監視で障害が発生している場合、半数のノード (切り上げ) より 1 つ少ない数のノードの障害に耐えることができます。 たとえば、6 つのノードから成るクラスターの場合、ディスク監視で障害が発生しているときは 2 つのノード (3-1=2) の障害に対する耐性があります。<br /><br /> 2 = ノードおよびファイル共有マジョリティ。 このクォーラム構成は "ノードおよびディスク マジョリティ" と同じように動作しますが、ディスク監視の代わりにファイル共有監視を使用します。<br /><br /> 3 = マジョリティなし: ディスクのみ。 クォーラム ディスクがオンラインの場合、このクォーラム構成では、1 つを除くすべてのノードの障害に耐えることができます。|  
|**quorum_type_desc**|**varchar (50)**|説明**quorum_type**,、1 つの。<br /><br /> NODE_MAJORITY<br /><br /> NODE_AND_DISK_MAJORITY<br /><br /> NODE_AND_FILE_SHARE_MAJORITY<br /><br /> NO_MAJORITY:_DISK_ONLY|  
|**quorum_state**|**tinyint**|WSFC クォーラムの状態。次のいずれかになります。<br /><br /> 0 = クォーラム状態不明<br /><br /> 1 = 通常のクォーラム<br /><br /> 2 = 強制クォーラム|  
|**quorum_state_desc**|**varchar (50)**|説明**quorum_state**,、1 つの。<br /><br /> UNKNOWN_QUORUM_STATE<br /><br /> NORMAL_QUORUM<br /><br /> FORCED_QUORUM|  
  
## <a name="permissions"></a>権限  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [AlwaysOn 可用性グループのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [可用性グループの監視と &#40; です。Transact SQL と &#41; です。](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [sys.dm_hadr_cluster_members &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql.md)  
  
  
