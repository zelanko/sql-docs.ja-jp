---
title: tcp_endpoints (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.tcp_endpoints
- sys.tcp_endpoints_TSQL
- tcp_endpoints
- tcp_endpoints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.tcp_endpoints catalog view
ms.assetid: 43cc3afa-cced-4463-8e97-fbfdaf2e4fa8
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 493bf17904f65b265656e03299fe13f9ea3f6441
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82821676"
---
# <a name="systcp_endpoints-transact-sql"></a>sys.tcp_endpoints (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  システム内の TCP エンドポイントごとに1行のレコードを格納します。 Tcp_endpoints によって記述されるエンドポイントは、接続特権を許可および取り消すためのオブジェクトを提供し**ます**。 ポートと IP アドレスについて表示される情報は、プロトコルの構成には使用されず、実際のプロトコル構成と一致しない場合があります。 プロトコルを表示および構成するには、Configuration Manager を使用し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**< 継承された列>**||は、列を継承し[ます。](../../relational-databases/system-catalog-views/sys-endpoints-transact-sql.md)|  
|**port**|INT|エンドポイントがリッスンするポート番号です。 NULL 値は許可されません。|  
|**is_dynamic_port**|bit|1 = ポート番号は動的に割り当てられました。<br /><br /> NULL 値は許可されません。|  
|**ip_address**|**nvarchar (45)**|LISTENER_IP 句によって指定されたリスナーの IP アドレス。 NULL 値が許可されます。|  
  
## <a name="remarks"></a>解説  
 次のクエリを実行して、エンドポイントと接続に関する情報を収集します。 現在の接続を使用していないエンドポイント、または TCP 接続がないエンドポイントは、NULL 値で表示されます。 **WHERE** `WHERE des.session_id = @@SPID` 現在の接続に関する情報を返す where 句を追加します。  
  
```  
SELECT des.login_name, des.host_name, program_name,  dec.net_transport, des.login_time,   
e.name AS endpoint_name, e.protocol_desc, e.state_desc, e.is_admin_endpoint,   
t.port, t.is_dynamic_port, dec.local_net_address, dec.local_tcp_port   
FROM sys.endpoints AS e  
LEFT JOIN sys.tcp_endpoints AS t  
   ON e.endpoint_id = t.endpoint_id  
LEFT JOIN sys.dm_exec_sessions AS des  
   ON e.endpoint_id = des.endpoint_id  
LEFT JOIN sys.dm_exec_connections AS dec  
   ON des.session_id = dec.session_id;  
```  
  
## <a name="permissions"></a>アクセス許可  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;カタログビュー](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [エンドポイントのカタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/endpoints-catalog-views-transact-sql.md)  
  
  
