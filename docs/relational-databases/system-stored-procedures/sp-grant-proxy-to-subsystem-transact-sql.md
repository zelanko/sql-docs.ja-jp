---
title: sp_grant_proxy_to_subsystem (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_grant_login_to_subsystem_TSQL
- sp_grant_login_to_subsystem
dev_langs:
- TSQL
helpviewer_keywords:
- sp_grant_proxy_to_subsystem
ms.assetid: 866aaa27-a1e0-453a-9b1b-af39431ad9c2
ms.author: vanto
manager: craigg
ms.openlocfilehash: 883496e1a0f31e69b09c8e4f5eeebdb94e006e68
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47732740"
---
# <a name="spgrantproxytosubsystem-transact-sql"></a>sp_grant_proxy_to_subsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブシステムに対するアクセス権をプロキシに与えます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_grant_proxy_to_subsystem  
     { [ @proxy_id = ] proxy_id | [ @proxy_name = ] 'proxy_name' },  
     { [ @subsystem_id = ] subsystem_id | [ @subsystem_name = ] 'subsystem_name' }  
```  
  
## <a name="arguments"></a>引数  
 [ **@proxy_id =** ] *id*  
 アクセス権を与えるプロキシのプロキシ識別番号を指定します。 *Proxy_id*は**int**、既定値は NULL です。 いずれか*proxy_id*または*proxy_name*指定する必要がありますが、両方を指定することはできません。  
  
 [  **@proxy_name =** ] **'***proxy_name***'**  
 アクセス権の対象となるプロキシの名前を指定します。 *Proxy_name*は**sysname**、既定値は NULL です。 いずれか*proxy_id*または*proxy_name*指定する必要がありますが、両方を指定することはできません。  
  
 [ **@subsystem_id =** ] *id*  
 アクセス権の対象となるサブシステムの識別番号を指定します。 *Subsystem_id*は**int**、既定値は NULL です。 いずれか*subsystem_id*または*subsystem_name*指定する必要がありますが、両方を指定することはできません。 次の表は、各サブシステムの ID に指定できる値の一覧です。  
  
|値|説明|  
|-----------|-----------------|  
|**2**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX スクリプト<br /><br /> **\*\* 重要な \*\*** ActiveX スクリプティング サブシステムはから削除する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の将来のバージョンのエージェント[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。|  
|**3**|オペレーティング システム (**CmdExec**)|  
|**4**|レプリケーション スナップショット エージェント|  
|**5**|レプリケーション ログ リーダー エージェント|  
|**6**|レプリケーション ディストリビューション エージェント|  
|**7**|Replication Merge Agent|  
|**8**|Replication Queue Reader Agent|  
|**9**|Analysis Services クエリ|  
|"**10**"|Analysis Services コマンド|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ実行|  
|**12**|PowerShell スクリプト|  
  
 [  **@subsystem_name =** ] **'***subsystem_name***'**  
 アクセス権の対象となるサブシステムの名前を指定します。 **Subsystem_name**は**sysname**、既定値は NULL です。 いずれか*subsystem_id*または*subsystem_name*指定する必要がありますが、両方を指定することはできません。 次の表は、各サブシステムの ID に指定できる値の一覧です。  
  
|値|説明|  
|-----------|-----------------|  
|**ActiveScripting**|ActiveX スクリプト|  
|**CmdExec**|オペレーティング システム (**CmdExec**)|  
|**スナップショット**|レプリケーション スナップショット エージェント|  
|**LogReader**|レプリケーション ログ リーダー エージェント|  
|**Distribution**|レプリケーション ディストリビューション エージェント|  
|**Merge**|Replication Merge Agent|  
|**QueueReader**|Replication Queue Reader Agent|  
|**ANALYSISQUERY**|Analysis Services クエリ|  
|**ANALYSISCOMMAND**|Analysis Services コマンド|  
|**Dts**|SSIS パッケージ実行|  
|**PowerShell**|PowerShell スクリプト|  
  
## <a name="remarks"></a>コメント  
 サブシステムへのアクセス権をプロキシに与えても、プロキシで指定されているプリンシパルに対する権限は変更されません。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_grant_proxy_to_subsystem**します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-granting-access-to-a-subsystem-by-id"></a>A. ID を使用してサブシステムへのアクセス権を与える  
 次の例は、プロキシを許可`Catalog application proxy`ActiveX スクリプティング サブシステムにアクセスします。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = 'Catalog application proxy',  
    @subsystem_id = 2;  
GO  
```  
  
### <a name="b-granting-access-to-a-subsystem-by-name"></a>B. 名前を使用してサブシステムへのアクセス権を与える  
 次の例は、プロキシを許可`Catalog application proxy`SSIS パッケージ実行サブシステムへのアクセス。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_grant_proxy_to_subsystem  
    @proxy_name = N'Catalog application proxy',  
    @subsystem_name = N'Dts' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントのセキュリティを実装します。](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_revoke_proxy_from_subsystem &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-proxy-from-subsystem-transact-sql.md)   
 [sp_add_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_update_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-update-proxy-transact-sql.md)  
  
  
