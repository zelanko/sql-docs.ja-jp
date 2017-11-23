---
title: "sys.dm_exec_connections (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/16/2017
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
- dm_exec_connections_TSQL
- sys.dm_exec_connections_TSQL
- sys.dm_exec_connections
- dm_exec_connections
dev_langs: TSQL
helpviewer_keywords: sys.dm_exec_connections dynamic management view
ms.assetid: 6bd46fe1-417d-452d-a9e6-5375ee8690d8
caps.latest.revision: "50"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 02fcbfb195c913396d6013f62a76853045ac3b9b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmexecconnections-transact-sql"></a>sys.dm_exec_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  このインスタンスの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] との間に確立された接続に関する情報と各接続の詳細を返します。 SQL Server のサーバー全体の接続情報を返します。 SQL データベースの現在のデータベース接続情報を返します。  
  
> [!NOTE]
> これから[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]または[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]を使用して[sys.dm_pdw_exec_connections &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-exec-connections-transact-sql.md).  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|session_id|**int**|この接続に関連付けられたセッションの識別子。 NULL 値が許可されます。|  
|most_recent_session_id|**int**|この接続に関連付けられた最新の要求のセッション ID。 SOAP 接続は別のセッションで再利用できます。NULL 値が許可されます。|  
|connect_time|**datetime**|接続が確立されたタイムスタンプ。 NULL 値は許可されません。|  
|net_transport|**nvarchar (40)**|常に返します**セッション**接続で複数のアクティブな結果セット (MARS) は有効にします。<br /><br /> **注:**この接続で使用される物理的な転送プロトコルについて説明します。 NULL 値は許可されません。|  
|protocol_type|**nvarchar (40)**|ペイロードのプロトコルの種類。 現在、TDS (TSQL) と SOAP が区別されます。 NULL 値が許可されます。|  
|protocol_version|**int**|この接続に関連付けられたデータ アクセス プロトコルのバージョン。 NULL 値が許可されます。|  
|endpoint_id|**int**|この接続の種類を表す識別子。 この endpoint_id は sys.endpoints ビューのクエリに使用できます。 NULL 値が許可されます。|  
|encrypt_option|**nvarchar (40)**|この接続で暗号化が有効かどうかを表すブール値。 NULL 値は許可されません。|  
|auth_scheme|**nvarchar (40)**|指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Windows 認証スキームがこの接続で使用します。 NULL 値は許可されません。|  
|node_affinity|**smallint**|この接続が関係しているメモリ ノード。 NULL 値は許可されません。|  
|num_reads|**int**|この接続で発生したバイトの読み取りの数。 NULL 値が許可されます。|  
|num_writes|**int**|この接続で発生したバイトの書き込みの数。 NULL 値が許可されます。|  
|last_read|**datetime**|この接続で最後に発生した読み取りのタイムスタンプ。 NULL 値が許可されます。|  
|last_write|**datetime**|この接続で最後に発生した書き込みのタイムスタンプ。 Null 値はありません。|  
|net_packet_size|**int**|情報とデータの転送に使用されたネットワーク パケット サイズ。 NULL 値が許可されます。|  
|client_net_address|**varchar(48)**|このサーバーに接続するクライアントのホスト アドレス。 NULL 値が許可されます。<br /><br /> V12 する前に[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、この列は常に NULL を返します。|  
|client_tcp_port|**int**|この接続に関連付けられたクライアント コンピューターのポート番号。 NULL 値が許可されます。<br /><br /> [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、この列は常に NULL を返します。|  
|local_net_address|**varchar(48)**|この接続の対象となったサーバーの IP アドレス。 TCP トランスポート プロバイダーを使用する接続の場合にのみ該当します。 NULL 値が許可されます。<br /><br /> [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、この列は常に NULL を返します。|  
|local_tcp_port|**int**|接続で TCP トランスポートを使用した場合に、この接続の対象となったサーバー TCP ポート。 NULL 値が許可されます。<br /><br /> [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、この列は常に NULL を返します。|  
|connection_id|**uniqueidentifier**|各接続の一意識別子。 NULL 値は許可されません。|  
|parent_connection_id|**uniqueidentifier**|MARS セッションが使用しているプライマリ接続の識別子。 NULL 値が許可されます。|  
|most_recent_sql_handle|**varbinary (64)**|この接続で実行された最新の要求の SQL ハンドル。 most_recent_sql_handle 列は、常に most_recent_session_id 列と同期されます。 NULL 値が許可されます。|  
|pdw_node_id|**int**|**適用されます**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> この分布はでは、ノードの識別子。|  
  
## <a name="permissions"></a>Permissions  
[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]が必要です`VIEW SERVER STATE`権限です。   
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 階層が必要です、`VIEW DATABASE STATE`データベースの権限です。 [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Standard および Basic 階層は、必要があります、**サーバー管理者**または**Azure Active Directory 管理者**アカウント。
  
## <a name="physical-joins"></a>物理結合  
 ![Sys.dm_exec_connections の結合](../../relational-databases/system-dynamic-management-views/media/join-dm-exec-connections-1.gif "sys.dm_exec_connections の結合")  
  
## <a name="relationship-cardinalities"></a>リレーションシップの基数  
  
||||  
|-|-|-|  
|dm_exec_sessions.session_id|dm_exec_connections.session_id|一対一|  
|dm_exec_requests.connection_id|dm_exec_connections.connection_id|多対一|  
|dm_broker_connections.connection_id|dm_exec_connections.connection_id|一対一|  
  
## <a name="examples"></a>使用例  
 クエリ専用接続についての情報を収集する典型的なクエリ。  
  
```t-sql  
SELECT   
    c.session_id, c.net_transport, c.encrypt_option,   
    c.auth_scheme, s.host_name, s.program_name,   
    s.client_interface_name, s.login_name, s.nt_domain,   
    s.nt_user_name, s.original_login_name, c.connect_time,   
    s.login_time   
FROM sys.dm_exec_connections AS c  
JOIN sys.dm_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = @@SPID;  
```  
  
## <a name="see-also"></a>参照  

 [実行関連の動的管理ビューおよび関数 &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/execution-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  


