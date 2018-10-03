---
title: sp_revokelogin (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_revokelogin_TSQL
- sp_revokelogin
dev_langs:
- TSQL
helpviewer_keywords:
- sp_revokelogin
ms.assetid: cb1ab102-1ae0-4811-9144-9a8121ef2d7e
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 57c7ef9242b6c974c8043f8f6ab237b0fbe07941
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47706656"
---
# <a name="sprevokelogin-transact-sql"></a>sp_revokelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログイン エントリを削除します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows ユーザーまたはログインの作成を使用して作成したグループの**sp_grantlogin**、または**sp_denylogin**します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_revokelogin [ @loginame= ] 'login'  
```  
  
## <a name="arguments"></a>引数  
 [  **@loginame=**] **'***ログイン***'**  
 Windows ユーザーまたはグループの名前です。 *ログイン*は**sysname**、既定値はありません。 *ログイン*、既存の Windows ユーザー名またはフォーム内のグループを指定することができます*コンピューター名*\\*ユーザーまたはドメイン*\\*ユーザー*します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_revokelogin**で指定されたアカウントを使用して接続を無効になります、*ログイン*パラメーター。 インスタンスへのアクセスが許可されている Windows ユーザーが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Windows のメンバーシップを通じてグループに接続できる、グループ、個々 のアクセスが取り消された後です。 同様に場合、*ログイン*とは別にされているそのグループのメンバーは、のインスタンスへのアクセスを許可パラメーターでは、Windows グループの名前を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は引き続き接続できます。  
  
 たとえば場合、Windows ユーザー **advworks \john** Windows グループのメンバーである**advworks \admins**、および**sp_revokelogin**へのアクセスを取り消します`ADVWORKS\john`:  
  
```  
sp_revokelogin [ADVWORKS\john]  
```  
  
 ユーザー **advworks \john**場合にも接続できます**advworks \admins**のインスタンスへのアクセス権が[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 同様に場合、Windows グループ**advworks \admins**取り消すそのアクセスしますが、 **advworks \john**アクセスが許可**advworks \john**も接続できます。  
  
 使用**sp_denylogin**明示的にユーザーのインスタンスに接続できないようにする[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows グループ メンバーシップに関係なく、します。  
  
 **sp_revokelogin**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>アクセス許可  
 サーバーに対する ALTER ANY LOGIN 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、Windows ユーザー用のログイン エントリを削除する`Corporate\MollyA`します。  
  
```  
EXEC sp_revokelogin 'Corporate\MollyA';  
```  
  
 スイッチまたは  
  
```  
EXEC sp_revokelogin [Corporate\MollyA];  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/drop-login-transact-sql.md)   
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
