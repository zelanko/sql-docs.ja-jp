---
title: "sp_revokelogin (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_revokelogin_TSQL
- sp_revokelogin
dev_langs: TSQL
helpviewer_keywords: sp_revokelogin
ms.assetid: cb1ab102-1ae0-4811-9144-9a8121ef2d7e
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c1d5dd00683f92f77e9ef59a64c66a7012deb274
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sprevokelogin-transact-sql"></a>sp_revokelogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ログイン エントリを削除[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows ユーザーまたはログインの作成を使用して作成されたグループの**sp_grantlogin**、または**sp_denylogin**です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[DROP LOGIN](../../t-sql/statements/drop-login-transact-sql.md)代わりにします。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_revokelogin [ @loginame= ] 'login'  
```  
  
## <a name="arguments"></a>引数  
 [  **@loginame=**] **'***ログイン***'**  
 Windows ユーザーまたはグループの名前です。 *ログイン*は**sysname**、既定値はありません。 *ログイン*任意の既存の Windows ユーザー名またはフォーム内のグループを指定できます*コンピューター名*\\*ユーザーまたはドメイン*\\*ユーザー*です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_revokelogin**で指定されたアカウントを使用して接続を無効になります、*ログイン*パラメーター。 インスタンスへのアクセスが許可されている Windows ユーザーが[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows のメンバーシップを通じてグループ接続できますが、グループとして、個々 のアクセスが取り消された後にします。 同様に場合、*ログイン*とは別にされているそのグループのメンバーは、のインスタンスへのアクセスを許可パラメーターでは、Windows グループの名前を指定、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続することができます。  
  
 たとえば場合の Windows ユーザー **advworks \john** Windows グループのメンバーである**advworks \admins**、および**sp_revokelogin**へのアクセスを取り消します`ADVWORKS\john`:  
  
```  
sp_revokelogin [ADVWORKS\john]  
```  
  
 ユーザー **advworks \john**場合にも接続できます**advworks \admins**のインスタンスへのアクセスを与えられた[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 同様に場合の Windows グループ**advworks \admins**がアクセスを取り消すが**advworks \john** 、アクセス権が付与**advworks \john**も接続できます。  
  
 使用して**sp_denylogin**のインスタンスへの接続からユーザーを明示的に防ぐこと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows グループ メンバーシップに関係なく、します。  
  
 **sp_revokelogin**ユーザー定義のトランザクション内で実行することはできません。  
  
## <a name="permissions"></a>Permissions  
 サーバーに対する ALTER ANY LOGIN 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、Windows ユーザー用のログイン エントリを削除する`Corporate\MollyA`です。  
  
```  
EXEC sp_revokelogin 'Corporate\MollyA';  
```  
  
 または  
  
```  
EXEC sp_revokelogin [Corporate\MollyA];  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DROP LOGIN &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-login-transact-sql.md)   
 [sp_denylogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-denylogin-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
