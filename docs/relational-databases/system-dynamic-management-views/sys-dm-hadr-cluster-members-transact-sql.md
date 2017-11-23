---
title: "sys.dm_hadr_cluster_members (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/23/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sys.dm_hadr_cluster_members_TSQL
- sys.dm_hadr_cluster_members
- dm_hadr_cluster_members_TSQL
- dm_hadr_cluster_members
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], WSFC clusters
- sys.dm_hadr_cluster_members catalog view
ms.assetid: feb20b3a-8835-41d3-9a1c-91d3117bc170
caps.latest.revision: "23"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ea85525a52734a09bc27d55e2e6b2a307be73ae4
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmhadrclustermembers-transact-sql"></a>sys.dm_hadr_cluster_members (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  かどうか、ホストする WSFC ノードのローカル インスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]対応した[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]WSFC クォーラムが存在する、行の各クォーラムとそれぞれの状態を構成するメンバーを返します。 これには、すべてのノードのクラスター内に含まれます (によって CLUSTER_ENUM_NODE 型で返される、 **Clusterenum**関数)、ディスク監視やファイル共有監視、存在する場合。 特定のメンバーに対して返される行には、そのメンバーの状態に関する情報が含まれます。 たとえば、1 つのノードがダウンしている場合のマジョリティ ノードのクォーラムを 5 つのノードのクラスター **sys.dm_hadr_cluster_members** 、あるサーバー インスタンスが有効になってから照会された[!INCLUDE[ssHADR](../../includes/sshadr-md.md)]クォーラムを持つノード上に存在します。**sys.dm_hadr_cluster_members** "node_down"ダウンしているノードの状態を反映します。  
  
 WSFC ノードにクォーラムが存在しない場合、行は返されません。  
  
 この動的管理ビューを使用すると、次のような疑問点を解決できます。  
  
-   WSFC クラスターで現在どのノードが実行されているか。  
  
-   マジョリティ ノードのクォーラムが失われるまでに、WSFC クラスターがあと何回の障害に耐えられるか。  

 > [!TIP]
 > 以降で[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、この動的管理ビューは、Always On フェールオーバー クラスター インスタンスだけでなく Always On 可用性グループをサポートしています。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**member_name**|**nvarchar (128)**|メンバー名。コンピューター名、ドライブ文字、ファイル共有パスのいずれかになります。|  
|**member_type**|**tinyint**|メンバーの種類。次のいずれかになります。<br /><br /> 0 = WSFC ノード<br /><br /> 1 = ディスク監視<br /><br /> 2 = ファイル共有監視|  
|**member_type_desc**|**nvarchar (50)**|説明**member_type**,、1 つの。<br /><br /> CLUSTER_NODE<br /><br /> DISK_WITNESS<br /><br /> FILE_SHARE_WITNESS|  
|**member_state**|**tinyint**|メンバーの状態。次のいずれかになります。<br /><br /> 0 = オフライン<br /><br /> 1 = オンライン|  
|**member_state_desc**|**nvarchar (60)**|説明**member_state**,、1 つの。<br /><br /> UP<br /><br /> ダウン|  
|**number_of_quorum_votes**|**tinyint**|このクォーラム メンバーが保有するクォーラムの投票数。 "マジョリティなし: ディスクのみ" のクォーラムの場合、この値は既定で 0 になります。 その他のクォーラムの種類の場合、この値は既定で 1 になります。|  
  
## <a name="permissions"></a>Permissions  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
## <a name="see-also"></a>参照  
 [AlwaysOn 可用性グループの動的管理ビューおよび関数 &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions.md)   
 [AlwaysOn 可用性グループのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql.md)   
 [可用性グループの監視 &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/monitor-availability-groups-transact-sql.md)   
 [AlwaysOn 可用性グループ &#40;です。SQL Server &#41;](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md)  
  
  
