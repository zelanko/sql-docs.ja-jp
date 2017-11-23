---
title: "sys.dm_os_dispatcher_pools (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/18/2017
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
- dm_os_dispatcher_pools_TSQL
- dm_os_dispatcher_pools
- sys.dm_os_dispatcher_pools
- sys.dm_os_dispatcher_pools_TSQL
dev_langs: TSQL
helpviewer_keywords:
- extended events [SQL Server], views
- sys.dm_os_dispatcher_pools DMV
ms.assetid: b9edbc83-c6bc-4753-9bb5-a454cfe7d6bf
caps.latest.revision: "25"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 479e97ce3202d33fdf125f0c5978e2c1899ee0cd
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmosdispatcherpools-transact-sql"></a>sys.dm_os_dispatcher_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セッション ディスパッチャー プールに関する情報を返します。 ディスパッチャー プールは、システム コンポーネントがバックグラウンド処理を実行するために使用するスレッド プールです。  
  
> [!NOTE]  
>  これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_dispatcher_pools**です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|dispatcher_pool_address|**varbinary (8)**|ディスパッチャー プールのアドレス。 dispatcher_pool_address は一意です。 NULL 値は許可されません。|  
|型|**nvarchar (256)**|ディスパッチャー プールの種類。 NULL 値は許可されません。 ディスパッチャー プールには、次の 2 種類があります。<br /><br /> DISP_POOL_XE_ENGINE<br /><br /> DISP_POOL_XE_SESSION<br /><br /> 完全な一覧について、DMV のクエリ|  
|name|**nvarchar (256)**|ディスパッチャー プールの名前。 NULL 値は許可されません。|  
|dispatcher_count|**int**|アクティブなディスパッチャー スレッドの数。 NULL 値は許可されません。|  
|dispatcher_ideal_count|**int**|ディスパッチャー プールに追加して使用できるディスパッチャー スレッドの数。 NULL 値は許可されません。|  
|dispatcher_timeout_ms|**int**|ディスパッチャーが終了する前に新しい処理を待つ時間 (ミリ秒単位)。 NULL 値は許可されません。|  
|dispatcher_waiting_count|**int**|アイドル状態のディスパッチャー スレッドの数。 NULL 値は許可されません。|  
|queue_length|**int**|ディスパッチャー プールによる処理を待っている作業項目の数。 NULL 値は許可されません。|  
|pdw_node_id|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>Permissions  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。   
  
## <a name="see-also"></a>参照  
  
  


