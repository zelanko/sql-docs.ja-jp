---
title: "sp_grant_proxy_to_subsystem (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
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
- sp_grant_login_to_subsystem_TSQL
- sp_grant_login_to_subsystem
dev_langs: TSQL
helpviewer_keywords: sp_grant_proxy_to_subsystem
ms.assetid: 866aaa27-a1e0-453a-9b1b-af39431ad9c2
caps.latest.revision: "37"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: aad59561938886f4fbb1e64dd45e425662c7f4d4
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="spgrantproxytosubsystem-transact-sql"></a>sp_grant_proxy_to_subsystem (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブシステムに対するアクセス権をプロキシに与えます。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_grant_proxy_to_subsystem  
     { [ @proxy_id = ] proxy_id | [ @proxy_name = ] 'proxy_name' },  
     { [ @subsystem_id = ] subsystem_id | [ @subsystem_name = ] 'subsystem_name' }  
```  
  
## <a name="arguments"></a>引数  
 [  **@proxy_id =** ] *id*  
 アクセス権を与えるプロキシのプロキシ識別番号を指定します。 *Proxy_id*は**int**、既定値は NULL です。 いずれか*proxy_id*または*proxy_name*指定する必要がありますが、両方を指定することはできません。  
  
 [  **@proxy_name =** ] **'***proxy_name***'**  
 アクセス権の対象となるプロキシの名前を指定します。 *Proxy_name*は**sysname**、既定値は NULL です。 いずれか*proxy_id*または*proxy_name*指定する必要がありますが、両方を指定することはできません。  
  
 [  **@subsystem_id =** ] *id*  
 アクセス権の対象となるサブシステムの識別番号を指定します。 *Subsystem_id*は**int**、既定値は NULL です。 いずれか*subsystem_id*または*subsystem_name*指定する必要がありますが、両方を指定することはできません。 次の表は、各サブシステムの ID に指定できる値の一覧です。  
  
|値|説明|  
|-----------|-----------------|  
|**2**|[!INCLUDE[msCoName](../../includes/msconame-md.md)] ActiveX スクリプト<br /><br /> **\*\* 重要な \*\*** ActiveX スクリプティング サブシステムはから削除する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の将来のバージョンのエージェント[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新規の開発作業ではこの機能を使用しないようにし、現在この機能を使用しているアプリケーションは修正することを検討してください。|  
|**3**|オペレーティング システム (**CmdExec**)|  
|**4**|レプリケーション スナップショット エージェント|  
|**5**|レプリケーション ログ リーダー エージェント|  
|**6**|レプリケーション ディストリビューション エージェント|  
|**7**|レプリケーション マージ エージェント|  
|**8**|レプリケーション キュー リーダー エージェント|  
|**9**|Analysis Services クエリ|  
|"**10**"|Analysis Services コマンド|  
|**11**|[!INCLUDE[ssIS](../../includes/ssis-md.md)] パッケージ実行|  
|**12**|PowerShell スクリプト|  
  
 [  **@subsystem_name =** ] **'***subsystem_name***'**  
 アクセス権の対象となるサブシステムの名前を指定します。 **Subsystem_name**は**sysname**、既定値は NULL です。 いずれか*subsystem_id*または*subsystem_name*指定する必要がありますが、両方を指定することはできません。 次の表は、各サブシステムの ID に指定できる値の一覧です。  
  
|値|Description|  
|-----------|-----------------|  
|**ActiveScripting**|ActiveX スクリプト|  
|**CmdExec**|オペレーティング システム (**CmdExec**)|  
|**スナップショット**|レプリケーション スナップショット エージェント|  
|**LogReader**|レプリケーション ログ リーダー エージェント|  
|**Distribution**|レプリケーション ディストリビューション エージェント|  
|**Merge**|レプリケーション マージ エージェント|  
|**QueueReader**|レプリケーション キュー リーダー エージェント|  
|**ANALYSISQUERY**|Analysis Services クエリ|  
|**ANALYSISCOMMAND**|Analysis Services コマンド|  
|**Dts**|SSIS パッケージ実行|  
|**PowerShell**|PowerShell スクリプト|  
  
## <a name="remarks"></a>解説  
 サブシステムへのアクセス権をプロキシに与えても、プロキシで指定されているプリンシパルに対する権限は変更されません。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_grant_proxy_to_subsystem**です。  
  
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
 [SQL Server エージェントのセキュリティを実装します。](http://msdn.microsoft.com/library/d770d35c-c8de-4e00-9a85-7d03f45a0f0d)   
 [sp_revoke_proxy_from_subsystem &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-revoke-proxy-from-subsystem-transact-sql.md)   
 [sp_add_proxy &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_update_proxy &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-update-proxy-transact-sql.md)  
  
  
