---
title: "ALTER LOGIN (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_LOGIN_TSQL
- ALTER LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER LOGIN statement
- change password
- mapping logins [SQL Server]
- logins [SQL Server], modifying
- passwords [SQL Server], modifying
- names [SQL Server], logins
- modifying login accounts
ms.assetid: e247b84e-c99e-4af8-8b50-57586e1cb1c5
caps.latest.revision: 68
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9dd47cb63c56dbbfb5f31ea3f7b2c8d4f45e9d73
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-login-transact-sql"></a>ALTER LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  プロパティを変更、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン アカウントです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
ALTER LOGIN login_name   
    {   
    <status_option>   
    | WITH <set_option> [ ,... ]  
    | <cryptographic_credential_option>  
    }   
[;]  
  
<status_option> ::=  
        ENABLE | DISABLE  
  
<set_option> ::=              
    PASSWORD = 'password' | hashed_password HASHED  
    [   
      OLD_PASSWORD = 'oldpassword'  
      | <password_option> [<password_option> ]   
    ]  
    | DEFAULT_DATABASE = database  
    | DEFAULT_LANGUAGE = language  
    | NAME = login_name  
    | CHECK_POLICY = { ON | OFF }  
    | CHECK_EXPIRATION = { ON | OFF }  
    | CREDENTIAL = credential_name  
    | NO CREDENTIAL  
  
<password_option> ::=   
    MUST_CHANGE | UNLOCK  
  
<cryptographic_credentials_option> ::=   
    ADD CREDENTIAL credential_name  
  | DROP CREDENTIAL credential_name  
```  
  
```  
-- Syntax for Azure SQL Database  
  
ALTER LOGIN login_name   
  {   
      <status_option>   
    | WITH <set_option> [ ,.. .n ]   
  }   
[;]  
  
<status_option> ::=  
    ENABLE | DISABLE  
  
<set_option> ::=   
    PASSWORD ='password'   
    [  
      OLD_PASSWORD ='oldpassword'  
    ]   
    | NAME = login_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER LOGIN login_name   
    {   
    <status_option>   
    | WITH <set_option> [ ,... ]  
    }   
  
<status_option> ::=ENABLE | DISABLE  
  
<set_option> ::=              
    PASSWORD ='password'   
    [   
      OLD_PASSWORD ='oldpassword'  
      | <password_option> [<password_option> ]   
    ]  
    | NAME = login_name  
    | CHECK_POLICY = { ON | OFF }  
    | CHECK_EXPIRATION = { ON | OFF }   
      
<password_option> ::=   
    MUST_CHANGE | UNLOCK  
```  
  
## <a name="arguments"></a>引数  
 *login_name*  
 変更する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの名前を指定します。 ドメイン ログインは角かっこで囲み、[domain\user] の形式で表す必要があります。  
  
 ENABLE | DISABLE  
 このログインを有効にするか無効にするかを指定します。 ログインを無効にしても、既に接続されているログインの動作には影響しません。 (を使用して、`KILL`既存の接続を終了するステートメントです)。無効にしたログインの権限を保持したまま、偽装を継続することができます。  
  
 パスワード**='***パスワード***'**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにのみ適用されます。 変更するログインのパスワードを指定します。 パスワードでは大文字と小文字が区別されます。  
  
 SQL データベースに対するアクティブな接続が (データベース エンジンによって実行されます) を再認証を必要と継続的に、少なくとも 10 時間。 データベース エンジンは、最初に送信されたパスワードを使用して再認証を試行して、ユーザー入力は必要ありません。 パフォーマンス上の理由から、SQL データベースで、パスワードがリセットされたとき、接続はできません、再認証場合でも、接続プールのために、接続がリセットします。 これは、内部設置型 SQL Server の動作と異なります。 接続が最初に承認されているために、パスワードは変更されている場合、は、接続を終了する必要があり、新しいパスワードを使用して新しい接続が作成します。 KILL DATABASE CONNECTION 権限を持つユーザーは、KILL コマンドを使用して SQL データベースへの接続を明示的に終了できます。 詳細については、次を参照してください。 [KILL & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/kill-transact-sql.md).  
  
 パスワード **=**  *hashed_password*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 HASHED キーワードにのみ適用されます。 作成するログインのパスワードのハッシュ値を指定します。  
  
> [!IMPORTANT]  
>  ログイン (または包含データベース ユーザー) が接続して認証されると、接続にはログインに関する ID 情報がキャッシュされます。 Windows 認証ログインの場合、これには Windows グループのメンバーシップに関する情報も含まれます。 接続が維持されている限り、ログインの ID が認証された状態は継続します。 パスワードのリセットや Windows グループのメンバーシップの変更など、ID に関する変更を適用するには、認証機関 (Windows または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]) からログオフしてもう一度ログインする必要があります。 **sysadmin** 固定サーバー ロールのメンバーまたは **ALTER ANY CONNECTION** 権限を持つすべてのログインは、 **KILL** コマンドを使用して接続を終了し、ログインの再接続を強制することができます。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] でオブジェクト エクスプ ローラーおよびクエリ エディター ウィンドウに複数の接続を開くときに、接続情報を再利用できます。 再接続を強制するには、すべての接続を閉じます。  
  
 HASHED   
   
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 適用されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインのみです。 PASSWORD 引数の後に入力されたパスワードが、ハッシュ済みであることを示します。 このオプションを選択しなかった場合、パスワードはハッシュされてからデータベースに格納されます。 このオプションは、2 つのサーバー間でログインを同期する場合にのみ使用してください。 パスワードを定期的に変更する場合は HASHED オプションを使用しないでください。  
  
 OLD_PASSWORD **='***oldpassword***'**  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにのみ適用されます。 新しいパスワードを割り当てるログインの、現在のパスワードを指定します。 パスワードでは大文字と小文字が区別されます。  
  
 MUST_CHANGE   
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにのみ適用されます。 このオプションが含まれている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変更後のログインが使用される更新パスワード最初の時刻が求められます。  
  
 DEFAULT_DATABASE  **=** *データベース*  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 既定のデータベースをログインに割り当てます。  
  
 DEFAULT_LANGUAGE  **=** *言語*  
 
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 既定の言語をログインに割り当てます。 すべての SQL データベース ログインの既定の言語では、英語し、変更できません。 既定の言語、`sa`上のログイン[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Linux では、英語は変更できます。  
  
 名前 = *login_name*  
 ログインの名前を変更する場合、新しい名前を指定します。 Windows ログインの場合は、新しい名前に対応する Windows プリンシパルの SID と、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 内のログインに関連付けられている SID が一致する必要があります。 新しい名前、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインは、円記号を含めることはできません (\\)。  
  
 CHECK_EXPIRATION = {ON |**OFF** }  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにのみ適用されます。 このログインに、パスワードの有効期限ポリシーを適用するかどうかを指定します。 既定値は OFF です。  
  
 CHECK_POLICY  **=**  { **ON** |オフ}  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにのみ適用されます。 指定するコンピューターの Windows パスワード ポリシー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行中は、このログインに適用する必要があります。 既定値は ON です。  
  
 資格情報 = *credential_name*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにマップする資格情報の名前を指定します。 この資格情報はサーバー内に存在する必要があります。 詳細については、次を参照してください。[資格情報 (&) #40";"データベース エンジン"&"#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)です。 資格情報は、sa ログインにマップすることはできません。  
  
 NO CREDENTIAL  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ログインからサーバー資格情報へのマッピングがある場合は削除します。 詳細については、次を参照してください。[資格情報 (&) #40";"データベース エンジン"&"#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)です。  
  
 UNLOCK  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにのみ適用されます。 ロックされているログインのロックを解除します。  
  
 ADD CREDENTIAL  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 拡張キー管理 (EKM: Extensible Key Management) プロバイダー資格情報をログインに追加します。 詳細については、次を参照してください。[拡張キー管理 & #40 です。EKM &#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
 DROP CREDENTIAL  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
ログインから拡張キー管理 (EKM) プロバイダー資格情報を削除します。 詳細については、次を参照してください。[拡張キー管理 & #40 です。EKM &#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md).  
  
## <a name="remarks"></a>解説  
 CHECK_POLICY が ON に設定されている場合、HASHED 引数は使用できません。  
  
 CHECK_POLICY を ON に変更した場合、次の動作が発生します。  
  
-   パスワードの履歴が、現在のパスワード ハッシュの値に初期化されます。  
  
 CHECK_POLICY を OFF に変更した場合、次の動作が発生します。  
  
-   CHECK_EXPIRATION も OFF に設定されます。  
  
-   パスワード履歴は消去されます。  
  
-   値*lockout_time*がリセットされます。  
  
MUST_CHANGE が指定された場合、CHECK_EXPIRATION および CHECK_POLICY は ON に設定されなければなりません。 ON に設定しない場合、ステートメントは失敗します。  
  
CHECK_POLICY を OFF に設定した場合、CHECK_EXPIRATION を ON に設定することはできません。 このオプションの組み合わせで ALTER LOGIN ステートメントを実行すると、ステートメントは失敗します。  
  
ALTER_LOGIN を DISABLE 引数と共に使用して Windows グループへのアクセスを拒否することはできません。 たとえば、ALTER_LOGIN [*domain \group*] 無効にするには、次のエラー メッセージが返されます。  
  
 "メッセージ 15151、レベル 16、状態 1、行 1"  
  
 "ログインを変更することはできません '*domain \group*' が存在しないか、権限がないため、します"。  
  
 これは仕様です。  
  
[!INCLUDE[ssSDS](../../includes/sssds-md.md)]接続の認証に必要なログイン データ、およびサーバー レベルのファイアウォール ルールは、各データベースでは一時的にキャッシュします。 このキャッシュは定期的に更新されます。 認証キャッシュの更新を強制し、データベースのログインの表に、最新バージョンがあることを確認、実行[DBCC FLUSHAUTHCACHE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 ALTER ANY LOGIN 権限が必要です。  
  
 CREDENTIAL オプションを使用する場合は、ALTER ANY CREDENTIAL 権限も必要です。  
  
 変更するログインのメンバーであるかどうか、 **sysadmin**固定サーバー ロールまたは CONTROL SERVER 権限の付与対象ユーザーも必要です CONTROL SERVER 権限、次の変更を行うときに。  
  
-   以前のパスワードを指定せずにパスワードをリセットする。  
  
-   MUST_CHANGE、CHECK_POLICY、または CHECK_EXPIRATION を有効にする。  
  
-   ログイン名を変更する。  
  
-   ログインを有効または無効にする。  
  
-   ログインを別の資格情報にマップする。  
  
 プリンシパルは、所有するログインのパスワード、既定の言語、および既定のデータベースを変更できます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-enabling-a-disabled-login"></a>A. 無効なログインを有効にする  
 次の例では、ログイン `Mary5` を有効にします。  
  
```tsql  
ALTER LOGIN Mary5 ENABLE;  
```  
  
### <a name="b-changing-the-password-of-a-login"></a>B. ログインのパスワードを変更する  
 次の例では、ログイン `Mary5` のパスワードを強力なパスワードに変更します。  
  
```tsql  
ALTER LOGIN Mary5 WITH PASSWORD = '<enterStrongPasswordHere>';  
```  
  
### <a name="c-changing-the-name-of-a-login"></a>C. ログインの名前を変更する  
 次の例では、ログイン `Mary5` の名前を `John2` に変更します。  
  
```tsql  
ALTER LOGIN Mary5 WITH NAME = John2;  
```  
  
### <a name="d-mapping-a-login-to-a-credential"></a>D. ログインを資格情報にマップする  
 次の例は、ログインをマップ`John2`資格情報を`Custodian04`です。  
  
```tsql  
ALTER LOGIN John2 WITH CREDENTIAL = Custodian04;  
```  
  
### <a name="e-mapping-a-login-to-an-extensible-key-management-credential"></a>E. ログインを拡張キー管理資格情報にマップする  
 次の例は、ログインをマップ`Mary5`EKM の資格情報を`EKMProvider1`です。  
  
 
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```tsql  
ALTER LOGIN Mary5  
ADD CREDENTIAL EKMProvider1;  
GO  
```  
  
### <a name="f-unlocking-a-login"></a>F. ログインのロックを解除する  
 ロックを解除する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン、次のステートメントを実行置換 * * * 必要なアカウント パスワードを使用します。  
  
  
```tsql  
ALTER LOGIN [Mary5] WITH PASSWORD = '****' UNLOCK ;  

GO  
```  
  
 パスワードを変更しないでログインのロックを解除するには、チェック ポリシーをオフにしてからもう一度オンにします。  
  
```tsql  
ALTER LOGIN [Mary5] WITH CHECK_POLICY = OFF;  
ALTER LOGIN [Mary5] WITH CHECK_POLICY = ON;  
GO  
```  
  
### <a name="g-changing-the-password-of-a-login-using-hashed"></a>G. HASHED を使用してログインのパスワードを変更する  
 次の例のパスワードの変更、`TestUser`を既にハッシュされた値にログインします。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```tsql  
ALTER LOGIN TestUser WITH   
PASSWORD = 0x01000CF35567C60BFB41EBDE4CF700A985A13D773D6B45B90900 HASHED ;  
GO  
```  
  
 
  
## <a name="see-also"></a>参照  
 [資格情報 (&) #40";"データベース エンジン"&"#41;](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [DROP LOGIN &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-login-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)  
  
  



