---
title: "sys.dm_os_child_instances (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sys.dm_os_child_instances
- sys.dm_os_child_instances_TSQL
- dm_os_child_instances
- dm_os_child_instances_TSQL
dev_langs: TSQL
helpviewer_keywords:
- server state information [SQL Server]
- sys.dm_os_child_instances dynamic management view
- monitoring server health
ms.assetid: 1bef3074-0ccc-48fa-8f3d-14f3d99df86b
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d13a86c17d95f31d2ffe99fa6675a0e0fe877ecd
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmoschildinstances-transact-sql"></a>sys.dm_os_child_instances (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  親サーバー インスタンスから作成されたユーザー インスタンスごとに 1 行のデータを返します。  
  
> **重要:** [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 返される情報**sys.dm_os_child_instances**各ユーザー インスタンス (heart_beat) の状態を確認し、ユーザーへの接続の作成に使用できるパイプ名 (instance_pipe_name) を取得するために使用できますインスタンスを使用して[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]または SQLCmd します。 ユーザー インスタンスがクライアント アプリケーションなどの外部プロセスによって開始された場合のみ、ユーザー インスタンスに接続できます。 SQL 管理ツールではユーザー インスタンスを開始できません。  
  
> **注:**の機能、ユーザー インスタンスは[!INCLUDE[ssExpressEd11](../../includes/ssexpressed11-md.md)]のみです。  
  
> **注**これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、名前を使用して**sys.dm_pdw_nodes_os_child_instances**です。  
  
|列|データ型|Description|  
|------------|---------------|-----------------|  
|**owning_principal_name**|**nvarchar (256)**|このユーザー インスタンスに対応するユーザーの名前です。|  
|owning_principal_sid|nvarchar (256)|このユーザー インスタンスを所有するプリンシパルの SID (セキュリティ識別子) です。 この値は、Windows SID と一致します。|  
|owning_principal_sid_binary|varbinary (85)|このユーザー インスタンスを所有するユーザーの SID のバイナリ バージョンです。|  
|**instance_name**|**nvarchar (128)**|このユーザー インスタンスの名前です。|  
|**instance_pipe_name**|**nvarchar (260)**|ユーザー インスタンスを作成すると、アプリケーションから接続するための名前付きパイプが作成されます。 この名前を接続文字列中で使用することにより、ユーザー インスタンスに接続できます。|  
|**os_process_id**|**Int**|このユーザー インスタンスに対応する、Windows プロセスのプロセス番号です。|  
|**os_process_creation_date**|**DateTime**|このユーザー インスタンス プロセスの前回の開始日付と時刻です。|  
|**heart_beat**|**nvarchar (5)**|このユーザー インスタンスの現在の状態 (ALIVE または DEAD) です。|  
|**pdw_node_id**|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>Permissions  
 サーバーに対する VIEW SERVER STATE 権限が必要です。  
  
## <a name="remarks"></a>解説  
 動的管理ビューの詳細については、次を参照してください[動的管理ビューおよび関数 &#40;。TRANSACT-SQL と #41 です。](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)で[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オンライン ブックの「します。  
  
## <a name="see-also"></a>参照  
 [管理者以外のユーザー インスタンス](http://msdn.microsoft.com/en-us/85385aae-10fb-4f8b-9eeb-cce2ee7da019)  
  
  



