---
title: sys.servers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- servers_TSQL
- sys.servers_TSQL
- servers
- sys.servers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.servers catalog view
ms.assetid: 4e774ed9-4e83-4726-9f1d-8efde8f9feff
caps.latest.revision: 53
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017
ms.openlocfilehash: 314c2f152080f91b2180fe89bc2ef24307cc90a5
ms.sourcegitcommit: 4cd008a77f456b35204989bbdd31db352716bbe6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2018
ms.locfileid: "39548572"
---
# <a name="sysservers-transact-sql"></a>sys.servers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  登録されると、リンクまたはリモート サーバーごとに 1 行と 1 行を持つ、ローカル サーバーのデータを含む**server_id** = 0。  

[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**server_id**|**int**|リンク サーバーのローカル ID です。|  
|**name**|**sysname**|ときに**server_id** = 0 の場合、サーバー名になります。<br /><br /> ときに**server_id** > 0 で、リンク サーバーのローカル名です。|  
|**product**|**sysname**|リンク サーバーの製品名 "SQL Server" の場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスであることを示します。|  
|**provider**|**sysname**|リンク サーバー接続用の OLE DB プロバイダー名です。|  
|**data_source**|**nvarchar (4000)**|OLE DB データ ソース接続プロパティです。|  
|**location**|**nvarchar (4000)**|OLE DB 場所接続プロパティです。 ない場合は NULL です。|  
|**provider_string**|**nvarchar (4000)**|OLE DB プロバイダー文字列接続プロパティです。<br /><br /> 呼び出し側に ALTER ANY LINKED SERVER 権限がなければ NULL になります。|  
|**catalog**|**sysname**|OLEDB カタログ接続プロパティです。 ない場合は NULL です。|  
|**connect_timeout**|**int**|接続のタイムアウト (秒単位) です。ない場合は 0 です。|  
|**query_timeout**|**int**|クエリのタイムアウト (秒単位) です。ない場合は 0 です。|  
|**is_linked**|**bit**|0 = を使用して追加された旧形式のサーバーは、 **sp_addserver**、さまざまな RPC および分散トランザクションの動作。<br /><br /> 1 の場合、標準リンク サーバーです。|  
|**is_remote_login_enabled**|**bit**|このサーバーに対する着信リモート ログインを有効にする RPC オプションが設定されています。|  
|**is_rpc_out_enabled**|**bit**|(このサーバーからの) 発信 RPC が有効です。|  
|**is_data_access_enabled**|**bit**|サーバーは分散クエリが有効です。|  
|**is_collation_compatible**|**bit**|リモート データの照合順序は、照合順序に関する情報がない場合にはローカル データと互換性があると見なされます。|  
|**uses_remote_collation**|**bit**|1 の場合、リモート サーバーによってレポートされる照合順序を使用し、それ以外の場合は、次の列で指定された照合順序を使用します。|  
|**collation_name**|**sysname**|使用する照合順序名です。ローカルを使用するだけの場合は NULL です。|  
|**lazy_schema_validation**|**bit**|1 の場合、スキーマの検証はクエリの開始時にチェックされません。|  
|**is_system**|**bit**|このサーバーには、内部システムからのみアクセスできます。|  
|**is_publisher**|**bit**|サーバーはレプリケーション パブリッシャーです。|  
|**is_subscriber**|**bit**|サーバーはレプリケーション サブスクライバーです。|  
|**is_distributor**|**bit**|サーバーはレプリケーション ディストリビューターです。|  
|**is_nonsql_subscriber**|**bit**|サーバーは SQL Server 以外のレプリケーション サブスクライバーです。|  
|**is_remote_proc_transaction_promotion_enabled**|**bit**|1 の場合、リモート ストアド プロシージャを呼び出すと分散トランザクションが開始され、トランザクションは MS DTC に参加します。 詳細については、「 [sp_serveroption &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)からデータにアクセスする方法について説明します。|  
|**modify_date**|**datetime**|サーバー情報が前回変更された日付です。|  
  
## <a name="permissions"></a>アクセス許可  
 値**provider_string**は呼び出し元は、ALTER ANY LINKED SERVER 権限を持っていない場合に常に NULL です。  
  
 アクセス許可がローカル サーバーを表示する必要はありません (**server_id** = 0)。  
  
 リンクまたはリモート サーバーを作成するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、既定のログイン マッピングを作成、**パブリック**サーバーの役割。 つまり、既定ではすべてのログインが、すべてのリンク サーバーおよびリモート サーバーを表示できます。 これらのサーバーへの可視性を制限するには、実行することによって既定のログイン マッピングを削除[sp_droplinkedsrvlogin](../../relational-databases/system-stored-procedures/sp-droplinkedsrvlogin-transact-sql.md) NULL を指定して、 *locallogin*パラメーター。  
  
 既定のログイン マッピングを削除すると、リンク ログインまたはリモート ログイン ユーザーとして明示的に追加されたユーザーだけが、対象のリンク サーバーやリモート サーバーを表示できるようになります。 既定のログイン マッピングを削除した後、すべてのリンク サーバーおよびリモート サーバーを表示するには、次の権限が必要です。  
  
-   ALTER ANY LINKED SERVER または ALTER ANY LOGIN ON SERVER  
  
-   メンバーシップ、 **setupadmin**または**sysadmin**固定サーバー ロール  
  
## <a name="see-also"></a>参照  
 [カタログ ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [リンク サーバーのカタログ ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/linked-servers-catalog-views-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)  
  
  
