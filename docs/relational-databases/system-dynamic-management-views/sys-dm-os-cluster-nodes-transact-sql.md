---
title: sys.dm_os_cluster_nodes (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_os_cluster_nodes_TSQL
- dm_os_cluster_nodes_TSQL
- dm_os_cluster_nodes
- sys.dm_os_cluster_nodes
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_cluster_nodes dynamic management view
ms.assetid: 92fa804e-2d08-42c6-a36f-9791544b1d42
caps.latest.revision: 36
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b612f3fed92d554ad6fcd9a5cf985eeea571de8c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysdmosclusternodes-transact-sql"></a>sys.dm_os_cluster_nodes (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  フェールオーバー クラスター インスタンスの構成には、ノードごとに 1 行を返します。 現在のインスタンスがフェールオーバー クラスター インスタンスの場合は、このフェールオーバー クラスター インスタンス (「仮想サーバー」以前) が定義されているノードの一覧を返します。 現在のサーバー インスタンスがフェールオーバー クラスター インスタンスではない場合は、空の行セットを返します。  
  
> **注:** これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_cluster_nodes**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**NodeName**|**sysname**|内のノードの名前、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フェールオーバー クラスター インスタンス (仮想サーバー) 構成します。|  
|ステータス|**int**|内のノードの状態、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フェールオーバー クラスター インスタンス: 0、1、2、3、-1。 詳細については、次を参照してください。 [GetClusterNodeState 関数](http://go.microsoft.com/fwlink/?LinkId=204794)です。|  
|status_description|**nvarchar(20)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター ノードの状態の説明。<br /><br /> 0 = up<br /><br /> 1 = down<br /><br /> 2 = 一時停止<br /><br /> 3 = joining<br /><br /> -1 = unknown|  
|is_current_owner|bit|1 は、このノードの現在の所有者、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フェールオーバー クラスターのリソース。|  
|pdw_node_id|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="remarks"></a>解説  
 フェールオーバー クラスタリングが有効な場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスター インスタンス (仮想サーバー) 構成の一部として指定されているフェールオーバー クラスター内のどのノードでも実行できます。  
  
> **注:** このビューには、将来のリリースで廃止予定 fn_virtualservernodes 関数が置き換えられます。  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、sys. dm_os_cluster_nodes を使用して、クラスター化されたサーバー インスタンスの割り当てノードを返します。  
  
```  
SELECT NodeName, status, status_description, is_current_owner   
FROM sys.dm_os_cluster_nodes;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
|NodeName|ステータス|status_description|is_current_owner|  
|--------------|------------|-------------------------|------------------------|  
|node1|0|up|1|  
|node2|0|up|0|  
|Node3|1|ダウン (down)|0|  
  
## <a name="see-also"></a>参照  
 [sys.dm_os_cluster_properties &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-cluster-properties-transact-sql.md)   
 [sys.dm_io_cluster_shared_drives &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-shared-drives-transact-sql.md)   
 [sys.fn_virtualservernodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-functions/sys-fn-virtualservernodes-transact-sql.md)   
 [動的管理ビューおよび関数 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  



