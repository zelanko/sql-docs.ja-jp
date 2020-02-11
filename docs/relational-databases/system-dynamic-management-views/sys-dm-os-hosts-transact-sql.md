---
title: dm_os_hosts (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_hosts_TSQL
- dm_os_hosts
- dm_os_hosts_TSQL
- sys.dm_os_hosts
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_hosts dynamic management view
ms.assetid: a313ff3b-1fe9-421e-b94b-cea19c43b0e5
author: stevestein
ms.author: sstein
ms.openlocfilehash: e4ff3e25accf5c499afb5e306a0eec206f6b3f82
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "73982552"
---
# <a name="sysdm_os_hosts-transact-sql"></a>dm_os_hosts (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  のインスタンスに現在登録されているすべて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のホストを返します。 このビューでは、ホストで使用されているリソースも返されます。  
  
> [!NOTE]  
>  またはから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]これを[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]呼び出すには、 **dm_pdw_nodes_os_hosts**という名前を使用します。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**host_address**|**varbinary (8)**|ホスト オブジェクトの内部メモリ アドレス。|  
|**type**|**nvarchar (60)**|ホストされるコンポーネントの種類。 たとえば、次のように入力します。<br /><br /> SOSHOST_CLIENTID_SERVERSNI = SQL Server ネイティブインターフェイス<br /><br /> SOSHOST_CLIENTID_SQLOLEDB = SQL Server Native Client OLE DB プロバイダー<br /><br /> SOSHOST_CLIENTID_MSDART = Microsoft データアクセスの実行時|  
|**name**|**nvarchar (32)**|ホストの名前。|  
|**enqueued_tasks_count**|**int**|ホストによって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のキューに挿入されたタスクの合計数。|  
|**active_tasks_count**|**int**|このホストがキューに配置した現在実行中のタスクの数。|  
|**completed_ios_count**|**int**|このホストで発行され、完了した i/o の合計数。|  
|**completed_ios_in_bytes**|**bigint**|このホストで完了した i/o の合計バイト数。|  
|**active_ios_count**|**int**|現在完了を待機しているこのホストに関連する i/o 要求の合計数。|  
|**default_memory_clerk_address**|**varbinary (8)**|このホストに関連付けられているメモリクラークオブジェクトのメモリアドレス。 詳細については、「 [sys. dm_os_memory_clerks &#40;transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)」を参照してください。|  
|**pdw_node_id**|**int**|**適用対象**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> このディストリビューションが配置されているノードの識別子。|  
  
## <a name="permissions"></a>アクセス許可

で[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]は、 `VIEW SERVER STATE`権限が必要です。   
Premium [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルでは、データベース`VIEW DATABASE STATE`の権限が必要です。 Standard [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]レベルおよび Basic レベルでは、**サーバー管理**者または**Azure Active Directory 管理者**アカウントが必要です。   

## <a name="remarks"></a>解説  
 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の実行可能なコンポーネント以外の OLE DB プロバイダーなどのコンポーネントが、メモリを割り当てたりノンプリエンプティブなスケジュールに参加することが許可されます。 これらのコンポーネントはに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]よってホストされ、これらのコンポーネントによって割り当てられるすべてのリソースが追跡されます。 ホスティングによって、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の外部コンポーネントで使用されるリソースをより正確に把握できます。  
  
## <a name="relationship-cardinalities"></a>リレーションシップ基数  
  
|移行元|To|リレーションシップ|  
|----------|--------|------------------|  
|sys.dm_os_hosts. default_memory_clerk_address|dm_os_memory_clerks。 memory_clerk_address|1対1|  
|sys.dm_os_hosts. host_address|dm_os_memory_clerks。 host_address|1対1|  
  
## <a name="examples"></a>例  
 次の例では、ホストされるコンポーネントによってコミットされたメモリの合計量を確認します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 以降。|  
  
```  
SELECT h.type, SUM(mc.pages_kb) AS commited_memory  
FROM sys.dm_os_memory_clerks AS mc   
INNER JOIN sys.dm_os_hosts AS h   
    ON mc.memory_clerk_address = h.default_memory_clerk_address  
GROUP BY h.type;  
```  
  
## <a name="see-also"></a>参照  

 [dm_os_memory_clerks &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-clerks-transact-sql.md)   
 [SQL Server オペレーティングシステム関連の動的管理ビュー &#40;Transact-sql&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


