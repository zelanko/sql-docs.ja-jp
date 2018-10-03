---
title: sp_helpremotelogin (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpremotelogin_TSQL
- sp_helpremotelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpremotelogin
ms.assetid: 93f50869-2627-4642-899f-8f626f8833f4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 1181ab030078b0f7ba61a72448991ed677e22d76
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47704806"
---
# <a name="sphelpremotelogin-transact-sql"></a>sp_helpremotelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ローカル サーバーで定義されている、特定のリモート サーバーまたはすべてのリモート サーバーのリモート ログインに関する情報をレポートします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)]代わりに、リンク サーバーとリンク サーバー ストアド プロシージャを使用してください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpremotelogin [ [ @remoteserver = ] 'remoteserver' ]   
     [ , [ @remotename = ] 'remote_name' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @remoteserver **=** ] **'***remoteserver***'**  
 リモート ログイン情報を返すリモート サーバーを指定します。 *remoteserver*は**sysname**、既定値は NULL です。 場合*remoteserver*が指定されていない場合、ローカル サーバーで定義されたすべてのリモート サーバーに関する情報が返されます。  
  
 [ @remotename **=** ] **'***remote_name***'**  
 リモート サーバー上の特定のリモート ログインを指定します。 *remote_name*は**sysname**、既定値は NULL です。 場合*remote_name*が指定されていないのすべてのリモート ユーザーに関する情報が定義されている*remoteserver*が返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|server|**sysname**|ローカル サーバーで定義されているリモート サーバーの名前。|  
|local_user_name|**sysname**|サーバーのリモート ログインがマップされているローカル サーバー上のログイン。|  
|remote_user_name|**sysname**|Local_user_name にマップされるリモート サーバーにログインします。|  
|options|**sysname**|Trusted = リモート サーバーからローカル サーバーに接続するとき、リモート ログインはパスワードを指定する必要はありません。<br /><br /> Untrusted (または空) = リモート サーバーからローカル サーバーに接続するとき、リモート ログインはパスワードを指定する必要があります。|  
  
## <a name="remarks"></a>コメント  
 Sp_helpserver を使用して、ローカル サーバーで定義されたリモート サーバーの名前を一覧表示します。  
  
## <a name="permissions"></a>アクセス許可  
 権限は確認されません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-reporting-help-on-a-single-server"></a>A. 特定のサーバーに関するヘルプをレポートする  
 次の例では、すべてのリモート ユーザーに関する情報を表示、リモート サーバーで`Accounts`します。  
  
```  
EXEC sp_helpremotelogin 'Accounts';  
```  
  
### <a name="b-reporting-help-on-all-remote-users"></a>B. すべてのリモート ユーザーに関するヘルプをレポートする  
 次の例では、ローカル サーバーで認識されているすべてのリモート サーバー上のリモート ユーザーに関する情報を表示します。  
  
```  
EXEC sp_helpremotelogin;  
```  
  
## <a name="see-also"></a>参照  
 [sp_addremotelogin &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql.md)   
 [sp_dropremotelogin &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropremotelogin-transact-sql.md)   
 [sp_helpserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpserver-transact-sql.md)   
 [sp_remoteoption &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-remoteoption-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
