---
title: "sp_help_proxy (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/09/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_help_proxy
- sp_help_proxy_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_help_proxy
ms.assetid: a2fce164-2b64-40c2-8f35-6eeb7844abf1
caps.latest.revision: "38"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: bf5dd28e001919a43d39685e2e50eaeb03e877af
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="sphelpproxy-transact-sql"></a>sp_help_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 つ以上のプロキシに関する情報を一覧表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @subsystem_name = ] 'subsystem_name' ,  
    [ @name = ] 'name'  
```  
  
## <a name="arguments"></a>引数  
 [  **@proxy_id**  =] *id*  
 情報を一覧表示するプロキシのプロキシ識別番号を指定します。 *Proxy_id*は**int**、既定値は NULL です。 いずれか、 *id*または*proxy_name*指定することがあります。  
  
 [  **@proxy_name**  =] **'***proxy_name***'**  
 情報を一覧表示するプロキシの名前を指定します。 *Proxy_name*は**sysname**、既定値は NULL です。 いずれか、 *id*または*proxy_name*指定することがあります。  
  
 [  **@subsystem_name**  =] '*subsystem_name*'  
 プロキシを一覧表示するサブシステムの名前を指定します。 *Subsystem_name*は**sysname**、既定値は NULL です。 ときに*subsystem_name*が指定されている*名前*も指定する必要があります。  
  
 次の表は、各サブシステムの ID に指定できる値の一覧です。  
  
|値|Description|  
|-----------|-----------------|  
|ActiveScripting|ActiveX スクリプト|  
|CmdExec|オペレーティング システム (CmdExec)|  
|スナップショット|レプリケーション スナップショット エージェント|  
|LogReader|レプリケーション ログ リーダー エージェント|  
|Distribution|レプリケーション ディストリビューション エージェント|  
|Merge|レプリケーション マージ エージェント|  
|QueueReader|レプリケーション キュー リーダー エージェント|  
|ANALYSISQUERY|Analysis Services コマンド|  
|ANALYSISCOMMAND|Analysis Services クエリ|  
|Dts|SSIS パッケージ実行|  
|PowerShell|PowerShell スクリプト|  
  
 [  **@name**  =] '*名前*'  
 名前、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロキシを一覧にログインします。 名前は**nvarchar (256)**、既定値は NULL です。 ときに*名前*が指定されている*subsystem_name*も指定する必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|プロキシの識別番号|  
|**name**|**sysname**|プロキシの名前|  
|**credential_identity**|**sysname**|プロキシに関連付けられている資格情報の Microsoft Windows ドメイン名およびユーザー名|  
|**有効になっています。**|**tinyint**|プロキシが有効かどうか  { **0** = 無効、 **1** = 有効}|  
|**説明**|**nvarchar (1024)**|プロキシの説明|  
|**user_sid**|**varbinary (85)**|プロキシに関する Windows ユーザーの Windows セキュリティ ID|  
|**credential_id**|**int**|プロキシに関連付けられている資格情報の識別子|  
|**credential_identity_exists**|**int**|credential_identity が存在するかどうか  {0 = 存在しない、1 = 存在する}|  
  
## <a name="remarks"></a>解説  
 パラメーターが指定されていないときに**sp_help_proxy**インスタンス内のすべてのプロキシに関する情報を一覧表示します。  
  
 指定されたサブシステムに対して使用できますプロキシ ログインを特定するのには、指定*名前*と*subsystem_name*です。 これらの引数が指定された場合、 **sp_help_proxy**がアクセスおよびは使用する、指定したサブシステムのログインが指定されているプロキシを一覧表示します。  
  
## <a name="permissions"></a>Permissions  
 既定では、このストアド プロシージャを実行できるのは、 **sysadmin** 固定サーバー ロールのメンバーです。 それ以外のユーザーには、 **msdb** データベースの **SQLAgentOperatorRole** 固定サーバー ロールを与える必要があります。  
  
 詳細については**SQLAgentOperatorRole**を参照してください[SQL Server エージェント固定データベース ロール](http://msdn.microsoft.com/library/719ce56b-d6b2-414a-88a8-f43b725ebc79)です。  
  
> [!NOTE]  
>  **Credential_identity**と**user_sid**列にのみ返されます場合の結果セットのメンバー **sysadmin**このストアド プロシージャを実行します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-information-for-all-proxies"></a>A. すべてのプロキシに関する情報を一覧表示する  
 次の例では、インスタンスのすべてのプロキシに関する情報を一覧表示します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_proxy ;  
GO  
```  
  
### <a name="b-listing-information-for-a-specific-proxy"></a>B. 特定のプロキシに関する情報を一覧表示する  
 次の例では、という名前のプロキシに関する情報を表示する`Catalog application proxy`です。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_proxy  
    @proxy_name = N'Catalog application proxy' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント ストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [sp_add_proxy &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)  
  
  
