---
title: "sp_enum_login_for_proxy (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_enum_login_for_proxy_TSQL
- sp_enum_login_for_proxy
dev_langs: TSQL
helpviewer_keywords: sp_enum_login_for_proxy
ms.assetid: 62a75019-248a-44c8-a5cc-c79f55ea3acf
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: efb661e0ad7f711654840392425a0ae78f936c3b
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="spenumloginforproxy-transact-sql"></a>sp_enum_login_for_proxy (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  セキュリティ プリンシパルとプロキシとの関連付けを一覧表示します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_enum_login_for_proxy  
    [ @name = ] 'name'  
    [ @proxy_id = ] id,  
    [ @proxy_name = ] 'proxy_name'  
```  
  
## <a name="arguments"></a>引数  
 [  **@name** =] '*名前*'  
 名前、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プリンシパル、ログイン、サーバー ロール、または**msdb**プロキシを一覧表示するデータベース ロール。 名前は**nvarchar (256)**、既定値は NULL です。  
  
 [  **@proxy_id** =] *id*  
 情報を一覧表示するプロキシのプロキシ識別番号を指定します。 *Proxy_id*は**int**、既定値は NULL です。 いずれか、 *id*または*proxy_name*指定することがあります。  
  
 [  **@proxy_name** =] **'***proxy_name***'**  
 情報を一覧表示するプロキシの名前を指定します。 *Proxy_name*は**sysname**、既定値は NULL です。 いずれか、 *id*または*proxy_name*指定することがあります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**proxy_id**|**int**|プロキシの識別番号|  
|**proxy_name**|**sysname**|プロキシの名前|  
|**name**|**sysname**|関連付けを表示するセキュリティ プリンシパルの名前|  
|**フラグ**|**int**|セキュリティ プリンシパルの種類<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン<br /><br /> **1** = 固定システム ロール<br /><br /> **2**のデータベース ロールを = **msdb**|  
  
## <a name="remarks"></a>解説  
 パラメーターが指定されていないときに**sp_enum_login_for_proxy**各プロキシのインスタンス内のすべてのログインに関する情報を一覧表示します。  
  
 プロキシ id またはプロキシ名を指定した場合、 **sp_enum_login_for_proxy**をプロキシへのアクセスを持つログインを一覧表示します。 ログイン名を指定すると、 **sp_enum_login_for_proxy**へのアクセスをログインのあるプロキシを一覧表示します。  
  
 プロキシ情報とログイン名の両方を指定した場合、結果セットでは、指定のログインが指定のプロキシにアクセスできる場合に 1 行のデータが返されます。  
  
 このストアド プロシージャにある**msdb**です。  
  
## <a name="permissions"></a>Permissions  
 メンバーにこのプロシージャの既定の実行のアクセス許可、 **sysadmin**固定サーバー ロール。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-all-associations"></a>A. すべての関連付けを一覧表示する  
 次の例では、現在のインスタンスに対し、ログインとプロキシの間に確立されているすべての権限を一覧表示します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_login_for_proxy ;  
GO  
```  
  
### <a name="b-listing-proxies-for-a-specific-login"></a>B. 指定したログインに対するプロキシを一覧表示する  
 次の例では、ログイン `terrid` がアクセスできるプロキシを一覧表示します。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_enum_login_for_proxy  
    @name = 'terrid' ;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sp_help_proxy &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-help-proxy-transact-sql.md)   
 [sp_grant_login_to_proxy &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-grant-login-to-proxy-transact-sql.md)   
 [sp_revoke_login_from_proxy &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-revoke-login-from-proxy-transact-sql.md)  
  
  
