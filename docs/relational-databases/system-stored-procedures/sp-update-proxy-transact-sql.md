---
title: sp_update_proxy (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_update_proxy
- sp_update_proxy_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER PROXY statement
- sp_update_proxy
ms.assetid: 864fd0e6-9d61-4f07-92ef-145318d2f881
caps.latest.revision: 30
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 402bdaa7ad89675cfaefec39cc8e36312e78d359
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spupdateproxy-transact-sql"></a>sp_update_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のプロキシのプロパティを変更します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_update_proxy   
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name',  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @new_name = ] 'new_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description'  
```  
  
## <a name="arguments"></a>引数  
 [ **@proxy_id**=] *id*  
 変更するプロキシのプロキシ識別番号を指定します。 *Proxy_id*は**int**、既定値は NULL です。  
  
 [ **@proxy_name**= ] **'***proxy_name***'**  
 変更するプロキシの名前を指定します。 *Proxy_name*は**sysname**、既定値は NULL です。  
  
 [ **@credential_name** =] **'***credential_name***'**  
 プロキシの新しい資格情報の名前を指定します。 *Credential_name*は**sysname**、既定値は NULL です。 いずれか*credential_name*または*credential_id*指定することがあります。  
  
 [ **@credential_id** =] *credential_id*  
 プロキシの新しい資格情報の識別番号を指定します。 *Credential_id*は**int**、既定値は NULL です。 いずれか*credential_name*または*credential_id*指定することがあります。  
  
 [ **@new_name**=] **'***new_name***'**  
 プロキシの新しい名前を指定します。 *New_name*は**sysname**、既定値は NULL です。 プロシージャが変更するプロキシの名前で指定した場合、 *new_name*です。 この引数が NULL の場合、プロキシの名前は変更されません。  
  
 [ **@enabled** =] *is_enabled*  
 プロキシが有効になっているかどうかです。 *Is_enabled*フラグは**tinyint**、既定値は NULL です。 ときに*is_enabled*は**0**プロキシが有効でないと、ジョブ ステップで使用することはできません。 この引数が NULL の場合、プロキシの状態は変更されません。  
  
 [ **@description**=] **'***説明***'**  
 プロキシの新しい説明を指定します。 *説明*は**nvarchar (512)**、既定値は NULL です。 この引数が NULL の場合、プロキシの説明は変更されません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 いずれか**@proxy_name**または**@proxy_id**指定する必要があります。 両方の引数を指定する場合は、両方とも同じプロキシを参照する必要があります。異なるプロキシを参照する場合、ストアド プロシージャは失敗します。  
  
 いずれか**@credential_name**または**@credential_id**プロキシの資格情報を変更するを指定する必要があります。 両方の引数を指定する場合は、両方とも同じ資格情報を参照する必要があります。異なる資格情報を参照する場合、ストアド プロシージャは失敗します。  
  
 このプロシージャでプロキシが変更されますが、プロキシへのアクセスは変更されません。 プロキシへのアクセスを変更するには、使用**sp_grant_login_to_proxy**と**sp_revoke_login_from_proxy**です。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定セキュリティ ロールは、この手順を実行できます。  
  
## <a name="examples"></a>使用例  
 次の例では、プロキシ `Catalog application proxy` の enabled の値を `0` に設定します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 0;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェント ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [SQL Server エージェントのセキュリティを実装します。](http://msdn.microsoft.com/library/d770d35c-c8de-4e00-9a85-7d03f45a0f0d)   
 [sp_add_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-proxy-transact-sql.md)   
 [sp_delete_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-delete-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
