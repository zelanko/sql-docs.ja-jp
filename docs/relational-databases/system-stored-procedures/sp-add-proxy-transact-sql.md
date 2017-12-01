---
title: "sp_add_proxy (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_add_proxy
- sp_add_proxy_TSQL
dev_langs: TSQL
helpviewer_keywords:
- CREATE PROXY statement
- sp_add_proxy
ms.assetid: cb59df37-f103-439b-bec1-2871fb669a8b
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e7cf6fb206ab8500ce334b11e9e78ddb9e5d1cee
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spaddproxy-transact-sql"></a>sp_add_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定した追加[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エージェント プロキシ。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_proxy  
    [ @proxy_name = ] 'proxy_name' ,  
    [ @enabled = ] is_enabled ,  
    [ @description = ] 'description' ,  
    [ @credential_name = ] 'credential_name' ,  
    [ @credential_id = ] credential_id ,  
    [ @proxy_id = ] id OUTPUT   
```  
  
## <a name="arguments"></a>引数  
 [  **@proxy_name** =] **'***proxy_name***'**  
 作成するプロキシの名前を指定します。 *Proxy_name*は**sysname**、既定値は NULL です。 ときに、 *proxy_name*が NULL または空の文字列、プロキシは既定の名前、 *user_name*指定します。  
  
 [  **@enabled**  =] *is_enabled*  
 プロキシが有効かどうかを指定します。 *Is_enabled*フラグは**tinyint**、既定値は 1 です。 ときに*is_enabled*は**0**プロキシが有効でないと、ジョブ ステップで使用することはできません。  
  
 [  **@description** =] **'***説明***'**  
 プロキシの説明を指定します。 説明は**nvarchar (512)**、既定値は NULL です。 この説明はプロキシを記述する場合の参照情報として利用できますが、それ以外の目的では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによってこの説明が使用されることはありません。 したがって、この引数は省略可能です。  
  
 [  **@credential_name**  =] **'***credential_name***'**  
 プロキシの資格情報の名前を指定します。 *Credential_name*は**sysname**、既定値は NULL です。 いずれか*credential_name*または*credential_id*指定する必要があります。  
  
 [  **@credential_id**  =] *credential_id*  
 プロキシの資格情報の識別番号を指定します。 *Credential_id*は**int**、既定値は NULL です。 いずれか*credential_name*または*credential_id*指定する必要があります。  
  
 [  **@proxy_id** =] *id*出力  
 プロキシの作成が成功したときにプロキシに割り当てられる、プロキシ識別番号です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="remarks"></a>解説  
 このストアド プロシージャを実行する必要があります、 **msdb**データベース。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント プロキシは、[!INCLUDE[tsql](../../includes/tsql-md.md)] サブシステム以外のサブシステムが含まれるジョブ ステップのセキュリティを管理します。 各プロキシには対応するセキュリティ資格情報が 1 つあります。 プロキシは、任意の数のサブシステムにアクセスする可能性があります。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定セキュリティ ロールは、この手順を実行できます。  
  
 メンバー、 **sysadmin**固定セキュリティ ロールは、任意のプロキシを使用するジョブ ステップを作成できます。 ストアド プロシージャを使用して[sp_grant_login_to_proxy (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)をプロキシに他のログイン アクセスを付与します。  
  
## <a name="examples"></a>使用例  
 この例は、資格情報のプロキシを作成`CatalogApplicationCredential`です。 このコードは、資格情報が既に存在していることを前提としています。 資格情報の詳細については、次を参照してください。 [CREATE CREDENTIAL &#40;です。TRANSACT-SQL と #41 です;](../../t-sql/statements/create-credential-transact-sql.md)。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_add_proxy  
    @proxy_name = 'Catalog application proxy',  
    @enabled = 1,  
    @description = 'Maintenance tasks on catalog application.',  
    @credential_name = 'CatalogApplicationCredential' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
