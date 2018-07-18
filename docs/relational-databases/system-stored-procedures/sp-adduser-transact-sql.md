---
title: sp_adduser (TRANSACT-SQL) |Microsoft Docs
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
- sp_adduser
- sp_adduser_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_adduser
ms.assetid: 61a40eb4-573f-460c-9164-bd1bbfaf8b25
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: d4f7afe6646fd22ff24aa6aee4e5dcde416420e9
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38036100"
---
# <a name="spadduser-transact-sql"></a>sp_adduser (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースに新しいユーザーを追加します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[CREATE USER](../../t-sql/statements/create-user-transact-sql.md)代わりにします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_adduser [ @loginame = ] 'login'   
    [ , [ @name_in_db = ] 'user' ]   
    [ , [ @grpname = ] 'role' ]   
```  
  
## <a name="arguments"></a>引数  
 [ **@loginame =** ] **'***login***'**  
 名前を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたは Windows ログインします。 *ログイン*は、 **sysname**、既定値はありません。 *ログイン*既存する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたは Windows ログインします。  
  
 [  **@name_in_db =** ] **'***ユーザー***'**  
 新しいデータベース ユーザーの名前です。 *ユーザー*は、 **sysname**、既定値は NULL です。 場合*ユーザー*が指定されていない、既定で、新しいデータベース ユーザーの名前、*ログイン*名。 指定する*ユーザー*サーバー レベルのログイン名と異なるデータベースの名前を新しいユーザーに与えます。  
  
 [  **@grpname =** ] **'***ロール***'**  
 新しいユーザーがメンバーになるデータベース ロールを指定します。 *ロール*は**sysname**、既定値は NULL です。 *ロール*現在のデータベースで有効なデータベース ロールである必要があります。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_adduser**もユーザーの名前を持つスキーマが作成されます。  
  
 ユーザーを追加した後、GRANT、DENY、および REVOKE ステートメントを使用して、ユーザーが実行する操作を制御する権限を定義します。  
  
 使用**sys.server_principals**有効なログイン名の一覧を表示します。  
  
 使用**sp_helprole**有効なロール名の一覧を表示します。 ロールを指定すると、そのロールに対して定義されている権限が自動的にユーザーに与えられます。 ロールが指定されていない場合、ユーザーは、既定値に付与されるアクセス許可を取得**パブリック**ロール。 値、ロールにユーザーを追加する、*ユーザー名*指定する必要があります。 (*username*と同じであることができます*login_id*)。  
  
 ユーザー**ゲスト**すべてのデータベースに既に存在します。 ユーザーの追加**ゲスト**無効だった場合、このユーザーが有効になります。 既定では、ユーザー**ゲスト**新しいデータベースでは無効です。  
  
 **sp_adduser**ユーザー定義のトランザクション内で実行することはできません。  
  
 追加することはできません、**ゲスト**ユーザーのため、**ゲスト**ユーザーが各データベース内に既に存在します。 有効にする、**ゲスト**ユーザー、grant**ゲスト**に示すように CONNECT 権限。  
  
```  
GRANT CONNECT TO guest;  
GO  
```  
  
## <a name="permissions"></a>アクセス許可  
 データベースの所有権が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-adding-a-database-user"></a>A. データベース ユーザーを追加する  
 次の例は、データベース ユーザーを追加します。`Vidur`既存`Recruiting`既存を使用して、現在のデータベース内のロール[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`Vidur`します。  
  
```  
EXEC sp_adduser 'Vidur', 'Vidur', 'Recruiting';  
```  
  
### <a name="b-adding-a-database-user-with-the-same-login-id"></a>B. ログイン ID と同じデータベース ユーザーを追加する  
 次の例では、ユーザー `Arvind` を、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のログイン `Arvind` として現在のデータベースに追加します。 既定値をこのユーザーが属している**パブリック**ロール。  
  
```  
EXEC sp_adduser 'Arvind';  
```  
  
### <a name="c-adding-a-database-user-with-a-different-name-than-its-server-level-login"></a>C. サーバーレベル ログインとは異なる名前のデータベース ユーザーを追加する  
 次の例では、追加[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン`BjornR`のユーザー名を持つ現在のデータベースに`Bjorn`、データベース ユーザーを追加および`Bjorn`を`Production`データベース ロール。  
  
```  
EXEC sp_adduser 'BjornR', 'Bjorn', 'Production';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sys.server_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-principals-transact-sql.md)   
 [sp_addrole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md)   
 [CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)   
 [sp_dropuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropuser-transact-sql.md)   
 [sp_grantdbaccess &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantdbaccess-transact-sql.md)   
 [sp_grantlogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
