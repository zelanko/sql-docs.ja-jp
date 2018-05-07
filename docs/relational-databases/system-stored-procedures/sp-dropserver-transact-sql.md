---
title: sp_dropserver (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_dropserver_TSQL
- sp_dropserver
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropserver
ms.assetid: 0fc83e35-0caa-49a3-a4b6-a1890d4f46ef
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 82f030a0f35a75bb1494035c9db8cd0ae0f002c0
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spdropserver-transact-sql"></a>sp_dropserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdbmi-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスにある、既知のリモート サーバーおよびリンク サーバーの一覧からサーバーを削除します。  
  
[!INCLUDE[ssMIlimitation](../../includes/sql-db-mi-limitation.md)]

 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropserver [ @server = ] 'server'   
     [ , [ @droplogins = ] { 'droplogins' | NULL} ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@server =** ] **'***server***'**  
 削除するサーバーを指定します。 *server* のデータ型は **sysname**で、既定値はありません。 *サーバー*存在する必要があります。  
  
 [  **@droplogins =** ] **'droplogins'** |NULL  
 リモートおよびリンク サーバー ログインに関係していることを示します*サーバー*場合にも削除する必要があります**droplogins**を指定します。 **@droplogins** **char (10)**、既定値は NULL です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 実行する場合**sp_dropserver**リモートおよびリンク サーバーのログイン エントリが関連付けられているサーバーまたはサーバーがレプリケーション パブリッシャーとして構成されている、エラー メッセージが返されます。 サーバーを削除するときに、サーバーのすべてのリモートおよびリンク サーバー ログインを削除するには、使用、 **droplogins**引数。  
  
 **sp_dropserver**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>権限  
 サーバーに対する ALTER ANY LINKED SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、リモート サーバー `ACCOUNTS` とそれに関連するすべてのリモート ログインを、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンスから削除します。  
  
```  
sp_dropserver 'ACCOUNTS', 'droplogins';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addserver &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpremotelogin &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
