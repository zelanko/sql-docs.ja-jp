---
title: "sp_droplinkedsrvlogin (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_droplinkedsrvlogin_TSQL
- sp_droplinkedsrvlogin
dev_langs: TSQL
helpviewer_keywords: sp_droplinkedsrvlogin
ms.assetid: 75a4a040-72d5-4d29-8304-de0aa481ad4b
caps.latest.revision: "21"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a0d9e2ed37bd70dda7d1cf47f78a7f1c28692a0f
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spdroplinkedsrvlogin-transact-sql"></a>sp_droplinkedsrvlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  実行しているローカル サーバー上のログインの間の既存のマッピングを削除[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]と、リンク サーバーでログインします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_droplinkedsrvlogin [ @rmtsrvname= ] 'rmtsrvname' ,   
   [ @locallogin= ] 'locallogin'  
```  
  
## <a name="arguments"></a>引数  
 [  **@rmtsrvname =** ] **'***rmtsrvname***'**  
 リンク サーバーの名前を指定する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン マッピングを適用します。 *rmtsrvname*は**sysname**、既定値はありません。 *rmtsrvname*既に存在する必要があります。  
  
 [  **@locallogin =** ] **'***locallogin***'**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、リンク サーバーにマップされているローカル サーバー上のログイン*rmtsrvname*です。 *locallogin*は**sysname**、既定値はありません。 マッピングを*locallogin*に*rmtsrvname*既に存在する必要があります。 によって NULL の場合、既定のマッピングが作成された**sp_addlinkedserver**、削除、リンク サーバー上のログインにローカル サーバー上のすべてのログインをマップします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 既存のマッピング、ログインが削除された、ローカル サーバーを使用する場合、既定のマッピングによって作成された**sp_addlinkedserver**接続すると、リンク サーバーにそのログインのためです。 既定のマッピングを変更するには、使用**sp_addlinkedsrvlogin**です。  
  
 場合は、既定のマッピングも削除されると、明示的に与えられて、リンク サーバーへのログイン マッピングを使用してログインのみ**sp_addlinkedsrvlogin**、リンク サーバーにアクセスできます。  
  
 **sp_droplinkedsrvlogin**ユーザー定義のトランザクション内から実行することはできません。  
  
## <a name="permissions"></a>Permissions  
 サーバーに対する ALTER ANY LOGIN 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-removing-the-login-mapping-for-an-existing-user"></a>A. 既存のユーザーのログイン マッピングを削除する  
 次の例では、ログイン `Mary` に関するローカル サーバーとリンク サーバー `Accounts` のマッピングを削除します。 その結果、ログイン `Mary` は既定のログイン マッピングを使用します。  
  
```  
EXEC sp_droplinkedsrvlogin 'Accounts', 'Mary';  
```  
  
### <a name="b-removing-the-default-login-mapping"></a>B. 既定のログイン マッピングを削除する  
 次の例を実行することによって作成された既定のログイン マッピングを削除する`sp_addlinkedserver`、リンク サーバーで`Accounts`です。  
  
```  
EXEC sp_droplinkedsrvlogin 'Accounts', NULL;  
```  
  
## <a name="see-also"></a>参照  
 [sp_addlinkedserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)   
 [sp_addlinkedsrvlogin &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
