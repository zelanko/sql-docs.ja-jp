---
title: "sp_xp_cmdshell_proxy_account (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_xp_cmdshell_proxy_account
- sp_xp_cmdshell_proxy_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xp_cmdshell_proxy_account
- xp_cmdshell
ms.assetid: f807c373-7fbc-4108-a2bd-73b48a236003
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: f2aa36f38df0fdf1f36e5cfddc48044222d9509c
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spxpcmdshellproxyaccount-transact-sql"></a>sp_xp_cmdshell_proxy_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  プロキシ資格情報を作成**xp_cmdshell**です。  
  
> [!NOTE]  
>  **xp_cmdshell**は既定で無効になります。 有効にする**xp_cmdshell**を参照してください[xp_cmdshell サーバー構成オプション](../../database-engine/configure-windows/xp-cmdshell-server-configuration-option.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_xp_cmdshell_proxy_account [ NULL | { 'account_name' , 'password' } ]  
```  
  
## <a name="arguments"></a>引数  
 NULL  
 プロキシ資格情報を削除します。  
  
 *account_name*  
 プロキシとなる Windows ログインを指定します。  
  
 *パスワード*  
 Windows アカウントのパスワードを指定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 プロキシ資格情報が呼び出される**##xp_cmdshell_proxy_account##**です。  
  
 NULL オプションを使用してを実行すると**sp_xp_cmdshell_proxy_account**プロキシ資格情報を削除します。  
  
## <a name="permissions"></a>Permissions  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-the-proxy-credential"></a>A. プロキシ資格情報を作成する  
 次の例では、パスワード `ADVWKS\Max04` が設定されている Windows アカウント `ds35efg##65` 用にプロキシ資格情報を作成します。  
  
```  
EXEC sp_xp_cmdshell_proxy_account 'ADVWKS\Max04', 'ds35efg##65';  
GO  
```  
  
### <a name="b-dropping-the-proxy-credential"></a>B. プロキシ資格情報を削除する  
 次の例では、資格情報ストアからプロキシ資格情報を削除します。  
  
```  
EXEC sp_xp_cmdshell_proxy_account NULL;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [xp_cmdshell &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/xp-cmdshell-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)  
  
  
