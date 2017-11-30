---
title: "sp_addlogin (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_addlogin
- sp_addlogin_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_addlogin
ms.assetid: 030f19c3-a5e3-4b53-bfc4-de4bfca0fddc
caps.latest.revision: "25"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 09a8425f9c3d773af00a0418ff4430839c221d87
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spaddlogin-transact-sql"></a>sp_addlogin (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  新たに作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスに接続するユーザーを許可するログイン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用して[CREATE LOGIN](../../t-sql/statements/create-login-transact-sql.md)代わりにします。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteWinAuthentication](../../includes/ssnotewinauthentication-md.md)]  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addlogin [ @loginame = ] 'login'   
    [ , [ @passwd = ] 'password' ]   
    [ , [ @defdb = ] 'database' ]   
    [ , [ @deflanguage = ] 'language' ]   
    [ , [ @sid = ] sid ]   
    [ , [ @encryptopt = ] 'encryption_option' ]   
[;]  
```  
  
## <a name="arguments"></a>引数  
 [ @loginame=] '*ログイン*'  
 ログインの名前を指定します。 *ログイン*は**sysname**、既定値はありません。  
  
 [ @passwd=] '*パスワード*'  
 ログイン パスワードを指定します。 *パスワード*は**sysname**、既定値は NULL です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteStrongPass](../../includes/ssnotestrongpass-md.md)]  
  
 [ @defdb=] '*データベース*'  
 ログインの既定のデータベースを指定します (そのログインがログインした後に最初に接続されるデータベース)。 *データベース*は**sysname**、既定値は**マスター**です。  
  
 [ @deflanguage=] '*言語*'  
 ログインの既定の言語を指定します。 *言語*は**sysname**、既定値は NULL です。 場合*言語*が指定されていない、既定値*言語*新しいログインに設定されているサーバーの現在の既定の言語です。  
  
 [ @sid=] '*sid*'  
 セキュリティ ID 番号 (SID) を指定します。 *sid*は**varbinary (16)**、既定値は NULL です。 場合*sid*が NULL の場合、システムには、新しいログインの SID が生成されます。 使用に関係なく、 **varbinary**データ型、NULL 以外の値は 16 バイトの長さにする必要があり、既に存在する必要があります。 指定する*sid*役に立ちます、たとえば、スクリプトをまたは移動するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を別の 1 つのサーバーからログインする別のサーバーに同じ SID をログインします。  
  
 [ @encryptopt=] '*encryption_option*'  
 パスワードを、クリア テキストとして渡すか、またはクリア テキスト パスワードのハッシュとして渡すかを指定します。 暗号化は行われないことに注意してください。 ここでは、"暗号化" という用語を旧バージョンとの互換性のために使用しています。 クリア テキスト パスワードが渡される場合、そのパスワードはハッシュされます。 ハッシュは保存されます。 *encryption_option*は**varchar (20)**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|NULL|パスワードがクリア テキストで渡されます。 これは既定値です。|  
|**skip_encryption**|パスワードは既にハッシュされています。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]再ハッシュせず、値を格納する必要があります。|  
|**skip_encryption_old**|指定されたパスワードは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の以前のバージョンでハッシュされています。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]再ハッシュせず、値を格納する必要があります。 このオプションはアップグレードのために提供されています。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの長さは 1 ～ 128 文字で、英字、記号、および数字を含めることができます。 ログインは、円記号を含めることはできません (\\) 以外の場合は sa や public などの予約済みログイン名を指定または既に存在; か、NULL または空の文字列にする (`''`)。  
  
 既定のデータベース名を把握していれば、USE ステートメントを実行しなくても指定されたデータベースに接続できます。 アクセスを付与するデータベースにデータベース所有者がまで既定のデータベースを使用することはできませんただし、(を使用して[sp_adduser](../../relational-databases/system-stored-procedures/sp-adduser-transact-sql.md)または[sp_addrolemember](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)) または[sp_addrole](../../relational-databases/system-stored-procedures/sp-addrole-transact-sql.md).  
  
 SID 番号は、サーバーでログインを一意に識別する GUID です。  
  
 サーバーの既定の言語を変更しても、既存のログインに関する既定の言語は変更されません。 サーバーの既定の言語を変更するには、使用[sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)です。  
  
 使用して**skip_encryption**を抑制する状況パスワード ハッシュは場合に便利にログインが追加されると、パスワードは既にハッシュされて[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 以前のバージョンので、パスワードがハッシュされてかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して**skip_encryption_old**です。  
  
 ユーザー定義のトランザクション内では、sp_addlogin を実行できません。  
  
 次の表は、sp_addlogin と共に使用されるストアド プロシージャを示しています。  
  
|ストアド プロシージャ|Description|  
|----------------------|-----------------|  
|[sp_grantlogin](../../relational-databases/system-stored-procedures/sp-grantlogin-transact-sql.md)|Windows のユーザーまたはグループを追加します。|  
|[sp_password](../../relational-databases/system-stored-procedures/sp-password-transact-sql.md)|ユーザーのパスワードを変更します。|  
|[sp_defaultdb](../../relational-databases/system-stored-procedures/sp-defaultdb-transact-sql.md)|ユーザーの既定のデータベースを変更します。|  
|[sp_defaultlanguage](../../relational-databases/system-stored-procedures/sp-defaultlanguage-transact-sql.md)|ユーザーの既定の言語を変更します。|  
  
## <a name="permissions"></a>Permissions  
 ALTER ANY LOGIN 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-sql-server-login"></a>A. SQL Server ログインを作成する  
 次の例を作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザーのログイン`Victoria`、パスワードを使用して`B1r12-36`既定のデータベースを指定せずします。  
  
```  
EXEC sp_addlogin 'Victoria', 'B1r12-36';  
GO  
```  
  
### <a name="b-creating-a-sql-server-login-that-has-a-default-database"></a>B. 既定のデータベースを持つ SQL Server ログインを作成する  
 次の例を作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザーのログイン`Albert`、パスワードを使用して`B5432-3M6`と、既定のデータベース`corporate`です。  
  
```  
EXEC sp_addlogin 'Albert', 'B5432-3M6', 'corporate';  
GO  
```  
  
### <a name="c-creating-a-sql-server-login-that-has-a-different-default-language"></a>C. 既定の言語が異なる SQL Server ログインを作成する  
 次の例では、パスワード `TzTodorov`、既定のデータベース `709hLKH7chjfwv`、および既定の言語 `AdventureWorks2012` を指定して、ユーザー `Bulgarian` の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを作成します。  
  
```  
EXEC sp_addlogin 'TzTodorov', '709hLKH7chjfwv', 'AdventureWorks2012', N'български'  
```  
  
### <a name="d-creating-a-sql-server-login-that-has-a-specific-sid"></a>D. 特定の SID を持つ SQL Server ログインを作成する  
 次の例では、パスワード `Michael`、既定のデータベース `B548bmM%f6`、既定の言語 `AdventureWorks2012`、および SID `us_english` を指定して、ユーザー `0x0123456789ABCDEF0123456789ABCDEF` の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを作成します。  
  
```  
EXEC sp_addlogin 'Michael', 'B548bmM%f6', 'AdventureWorks2012', 'us_english', 0x0123456789ABCDEF0123456789ABCDEF  
```  
  
## <a name="see-also"></a>参照  
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [sp_droplogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droplogin-transact-sql.md)   
 [sp_helpuser &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [sp_revokelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-revokelogin-transact-sql.md)   
 [xp_logininfo &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/xp-logininfo-transact-sql.md)  
  
  
