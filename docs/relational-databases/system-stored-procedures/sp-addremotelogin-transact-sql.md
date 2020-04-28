---
title: sp_addremotelogin (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_addremotelogin_TSQL
- sp_addremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_addremotelogin
ms.assetid: 71b7cd36-a17d-4b12-b102-10aeb0f9268b
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: eb45ce1c3e1786eb5a9a3cd630741dd4df773c40
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68030962"
---
# <a name="sp_addremotelogin-transact-sql"></a>sp_addremotelogin (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ローカルサーバーに新しいリモートログイン ID を追加します。 これにより、リモートサーバーがリモートプロシージャコールに接続して実行できるようになります。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]代わりに、リンク サーバーとリンク サーバー ストアド プロシージャを使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addremotelogin [ @remoteserver = ] 'remoteserver'   
     [ , [ @loginame = ] 'login' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @remoteserver **=** ] **'**_remoteserver_**'**  
 リモートログインが適用されるリモートサーバーの名前を指定します。 *remoteserver*は**sysname**,、既定値はありません。 *Remoteserver*のみを指定した場合、 *remoteserver*上のすべてのユーザーは、ローカルサーバー上の同じ名前の既存のログインにマップされます。 このサーバーは、ローカル サーバーが認識している必要があります。 サーバーは、sp_addserver を使用して追加されます。 *Remoteserver*のユーザーは、リモートストアドプロシージャを実行するため[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]にを実行しているローカルサーバーに接続するときに、 *remoteserver*での自分のログインと一致するローカルログインとして接続します。 *remoteserver*は、リモートプロシージャコールを開始するサーバーです。  
  
 [ @loginame **=** ] **'**_ログイン_**'**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のローカル インスタンス上のユーザーのログイン ID を指定します。 *login* のデータ型は **sysname** で、既定値は NULL です。 *ログイン*は、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ローカルインスタンスに既に存在している必要があります。 *Login*を指定すると、 *remoteserver*のすべてのユーザーがその特定のローカルログインにマップされます。 *Remoteserver*のユーザーがの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ローカルインスタンスに接続してリモートストアドプロシージャを実行すると、*ログイン*として接続されます。  
  
 [ @remotename **=** ] **'**_remote_name_**'**  
 リモートサーバー上のユーザーのログイン ID を示します。 *remote_name*は**sysname**,、既定値は NULL です。 *remote_name*は*remoteserver*に存在する必要があります。 *Remote_name*が指定されている場合、特定のユーザー *remote_name*がローカルサーバーの*ログイン*にマップされます。 *Remoteserver*で*remote_name* 、リモートストアドプロシージャを実行する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ためにのローカルインスタンスに接続すると、*ログイン*として接続されます。 *Remote_name*のログイン id は、リモートサーバーのログイン id ( *login*) とは異なる場合があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>Remarks  
 分散クエリを実行するには、sp_addlinkedsrvlogin を使用します。  
  
 sp_addremotelogin をユーザー定義のトランザクションの内部で使用することはできません。  
  
## <a name="permissions"></a>アクセス許可  
 sp_addremotelogin を実行できるのは、固定サーバー ロール sysadmin および securityadmin のメンバーだけです。  
  
## <a name="examples"></a>例  
  
### <a name="a-mapping-one-to-one"></a>A. 一対一のマッピング  
 次の例では、リモートサーバー `ACCOUNTS`とローカルサーバーのユーザーログインが同じである場合に、リモート名をローカル名にマップします。  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS';  
```  
  
### <a name="b-mapping-many-to-one"></a>B. 多対一のマッピング  
 次の例では、リモート サーバー `ACCOUNTS` のすべてのユーザーを、ローカル ID `Albert` にマップするエントリを作成します。  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'Albert';  
```  
  
### <a name="c-using-explicit-one-to-one-mapping"></a>C. 明示的に一対一でマップする  
 次の例では、リモートサーバー `Chris` `ACCOUNTS`のリモートユーザーからのリモートログインをローカルユーザー `salesmgr`にマップします。  
  
```  
EXEC sp_addremotelogin 'ACCOUNTS', 'salesmgr', 'Chris';  
```  
  
## <a name="see-also"></a>参照  
 [sp_addlinkedsrvlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql.md)   
 [sp_addlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addlogin-transact-sql.md)   
 [sp_addserver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_dropremotelogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [sp_revokelogin &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
