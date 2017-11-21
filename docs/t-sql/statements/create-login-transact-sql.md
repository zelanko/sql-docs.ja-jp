---
title: "ログイン (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/15/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE_LOGIN_TSQL
- CREATE LOGIN
- LOGIN_TSQL
- LOGIN
dev_langs:
- TSQL
helpviewer_keywords:
- passwords [SQL Server], logins
- mapping logins [SQL Server]
- logins [SQL Server], creating
- CREATE LOGIN statement
- permissions [SQL Server], logins
- Windows domain accounts [SQL Server]
- re-hashing passwords
- certificates [SQL Server], logins
ms.assetid: eb737149-7c92-4552-946b-91085d8b1b01
caps.latest.revision: 101
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: e0b84743a9c3c578954560613c69f2863af8aa01
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

---
# <a name="create-login-transact-sql"></a>CREATE LOGIN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  [!INCLUDE[ssDE](../../includes/ssde-md.md)] および [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] ログインを作成します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
CREATE LOGIN login_name { WITH <option_list1> | FROM <sources> }  
  
<option_list1> ::=   
    PASSWORD = { 'password' | hashed_password HASHED } [ MUST_CHANGE ]  
    [ , <option_list2> [ ,... ] ]  
  
<option_list2> ::=    
    SID = sid  
    | DEFAULT_DATABASE = database      
    | DEFAULT_LANGUAGE = language  
    | CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
    | CREDENTIAL = credential_name   
  
<sources> ::=  
    WINDOWS [ WITH <windows_options>[ ,... ] ]  
    | CERTIFICATE certname  
    | ASYMMETRIC KEY asym_key_name  
  
<windows_options> ::=        
    DEFAULT_DATABASE = database  
    | DEFAULT_LANGUAGE = language  
```  
  
```  
-- Syntax for Azure SQL Database and Azure SQL Data Warehouse  
  
CREATE LOGIN login_name  
 { WITH <option_list3> }  
  
<option_list3> ::=   
    PASSWORD = { 'password' }  
    [ SID = sid ]  
```  
  
```  
-- Syntax for Parallel Data Warehouse  
  
CREATE LOGIN loginName { WITH <option_list1> | FROM WINDOWS }  
  
<option_list1> ::=   
    PASSWORD = { 'password' } [ MUST_CHANGE ]  
    [ , <option_list2> [ ,... ] ]  
  
<option_list2> ::=    
      CHECK_EXPIRATION = { ON | OFF}  
    | CHECK_POLICY = { ON | OFF}  
```  
  
## <a name="arguments"></a>引数  
 *login_name*  
 作成するログインの名前を指定します。 ログインには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログイン、Windows ログイン、証明書マッピング ログイン、非対称キー マッピング ログインの 4 種類があります。 Windows ドメイン アカウントからマップされるログインを作成するときの形式で windows 2000 より前のユーザー ログオン名を使用する必要があります [\<domainName >\\< login_name >] です。 形式の UPN を使用することはできませんlogin_name@DomainNameです。 例については、後の例 D を参照してください。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証ログインの種類**sysname**の規則に従っている必要があります[識別子](http://msdn.microsoft.com/library/ms175874.aspx)含めることはできません、'**\\**' です。 Windows ログインを含めることができます、'**\\**' です。 Active Directory ユーザーに基づくログインより小さい 21 文字の名前に制限されます。  
  
 パスワード**='***パスワード***'**  
 適用されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインのみです。 作成するログインのパスワードを指定します。 強力なパスワードを使用する必要があります。 詳細については、次を参照してください。[強力なパスワードの](../../relational-databases/security/strong-passwords.md)と[パスワード ポリシー](../../relational-databases/security/password-policy.md)です。 以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]保存されたパスワード情報はソルト化パスワードの sha-512 を使用して計算されます。  
  
 パスワードでは大文字と小文字が区別されます。 パスワードの長さは 8 文字以上 128 文字以下である必要があります。  パスワードには、a ～ z、A ～ Z、0 ～ 9 およびほとんどの英数字以外の文字を含めることができます。 パスワードは、単一引用符を含めることはできませんまたは*login_name*です。  
  
 パスワード **=**  *hashed_password*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 HASHED キーワードにのみ適用されます。 作成するログインのパスワードのハッシュ値を指定します。  
  
 HASHED   
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 適用されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインのみです。 PASSWORD 引数の後に入力されたパスワードが、ハッシュ済みであることを示します。 このオプションを選択しなかった場合、パスワードとして入力した文字列は、ハッシュされてからデータベースに格納されます。 このオプションは、あるサーバーから別のサーバーにデータベースを移行する場合にのみ使用してください。 新しいログインを作成する場合は HASHED オプションを使用しないでください。 作成されたハッシュでは、HASHED オプションを使用できません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]7 以降  
  
 MUST_CHANGE   
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 適用されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインのみです。 このオプションが含まれている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]最初に、新しいログインを使用するとき、ユーザーに新しいパスワードを求められます。  
  
 資格情報 **=**  *credential_name*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 新しいにマップする資格情報の名前[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。 この資格情報はサーバー内に存在する必要があります。 現在このオプションは、資格情報をログインに関連付けるだけです。 資格情報は、システム管理者 (sa) ログインにマップすることはできません。  
  
 SID = *sid*  
 ログインを再作成に使用されます。 適用されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証ログインの場合のみ、Windows 認証ログインではありません。 新しい SID を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証ログインです。 このオプションを使用しない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SID を自動的に割り当てられます。 SID 構造に依存、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バージョン。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログイン SID: 16 バイト (**binary (16)**) リテラル値は GUID に基づいています。 たとえば、 `SID = 0x14585E90117152449347750164BA00A7`があります。  
  
-   [!INCLUDE[ssSDS](../../includes/sssds-md.md)]ログイン SID。 SID 構造体の有効な[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]します。 通常、これは 32 バイト (**binary (32)**) から成るリテラル`0x01060000000000640000000000000000`16 バイトの GUID を表すとします。 たとえば、 `SID = 0x0106000000000064000000000000000014585E90117152449347750164BA00A7`があります。  
  
DEFAULT_DATABASE  **=** *データベース*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ログインに割り当てられる既定のデータベースを指定します。 このオプションを指定しない場合は、既定のデータベースが master に設定されます。  
  
DEFAULT_LANGUAGE  **=** *言語*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ログインに割り当てられる既定の言語を指定します。 このオプションを指定しない場合は、サーバーの現在の既定の言語が既定の言語になります。 サーバーの既定の言語が将来変更されても、ログインの既定の言語は変更されません。  
  
CHECK_EXPIRATION  **=**  {ON |**OFF** }  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 適用されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインのみです。 このログインに、パスワードの有効期限ポリシーを適用するかどうかを指定します。 既定値は OFF です。  
  
CHECK_POLICY  **=**  { **ON** |オフ}  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 適用されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインのみです。 指定するコンピューターの Windows パスワード ポリシー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が実行中は、このログインに適用する必要があります。 既定値は ON です。  
  
 Windows のポリシーで強力なパスワードが求められる場合は、次の 4 つの特性のうちの少なくとも 3 つをパスワードに含める必要があります。  
  
-   大文字 (A ～ Z)。  
-   小文字 (a ～ z)。  
-   数字 (0 ～ 9)。  
-   スペース、_、@、*、^、%、!、$、#、& などの英数字以外の文字。  
  
WINDOWS  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ログインを Windows ログインにマップするよう指定します。  
  
証明書*証明書名*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ログインに関連付ける証明書の名前を指定します。 この証明書は、master データベース内に既に存在する必要があります。  
  
非対称キー *asym_key_name*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ログインに関連付ける非対称キーの名前を指定します。 このキーは、master データベース内に既に存在する必要があります。  
  
## <a name="remarks"></a>解説  
 パスワードでは大文字と小文字が区別されます。  
  
 パスワードのハッシュは作成する場合にのみサポート[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインします。  
  
 MUST_CHANGE が指定された場合、CHECK_EXPIRATION および CHECK_POLICY は ON に設定されなければなりません。 ON に設定しない場合、ステートメントは失敗します。  
  
 CHECK_POLICY = OFF と CHECK_EXPIRATION = ON の組み合わせはサポートされていません。  
  
 CHECK_POLICY を OFF に設定したときに*lockout_time*はリセット CHECK_EXPIRATION が OFF に設定されているとします。  
  
> [!IMPORTANT]  
>  CHECK_EXPIRATION および CHECK_POLICY のみに適用されます[!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)]およびそれ以降。 詳細については、「 [Password Policy](../../relational-databases/security/password-policy.md)」をご参照ください。  
  
 証明書または非対称キーから作成されたログインはコード署名用にのみ使用されます。 接続には使用できません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 証明書または非対称キーからログインを作成できるのは、その証明書または非対称キーが master に存在している場合のみです。  
  
 ログインを転送するスクリプトを次を参照してください。 [SQL Server 2005 のインスタンスと SQL Server 2008 の間で、ログインおよびパスワードを転送する方法](http://support.microsoft.com/kb/918992)です。  
  
 ログインを自動的に作成する、新しいログインを有効にし、ログイン、サーバー レベルの付与**CONNECT SQL**権限です。  
  
 権限システムの設計の詳細については、「 [データベース エンジンの権限の概要](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)」を参照してください。  
  
## <a name="includesssdsfullincludessssdsfull-mdmd-and-includesssdwincludessssdw-mdmd-logins"></a>[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]および[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]ログイン  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、 **CREATE LOGIN**ステートメントはバッチ内の唯一のステートメントである必要があります。  
  
 接続のいくつかの方法で[!INCLUDE[ssSDS](../../includes/sssds-md.md)]など**sqlcmd**、追加する必要があります、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバー名を使用して接続文字列内のログイン名を*\<ログイン >*@ *\<サーバー >*表記します。 たとえば、ログインが`login1`との完全修飾名、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバーが`servername.database.windows.net`、*ユーザー名*接続文字列のパラメーターでなければなりません`login1@servername`です。 の合計の長さ、 *username*パラメーターは、128 文字まで*login_name*はサーバー名の長さマイナス 127 文字に制限されます。 例では、`login_name`ためにできるだけ 117 文字まで`servername`10 文字です。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]と[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]にログインを作成する master データベースに接続する必要がある必要があります。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]作成することがルール、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]形式の認証ログイン\<loginname > @\<サーバー名 >。 場合、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]サーバーが**myazureserver** 、ログインが **myemail@live.com** 、としてログインを指定する必要があります **myemail@live.com @myazureserver** .  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)]接続の認証に必要なログイン データ、およびサーバー レベルのファイアウォール ルールは、各データベースでは一時的にキャッシュします。 このキャッシュは定期的に更新されます。 認証キャッシュの更新を強制し、データベースのログインの表に、最新バージョンがあることを確認、実行[DBCC FLUSHAUTHCACHE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-flushauthcache-transact-sql.md).  
  
 詳細については[!INCLUDE[ssSDS](../../includes/sssds-md.md)]ログインを参照してください[Windows Azure SQL データベースにおけるデータベースの管理とログイン](http://msdn.microsoft.com/library/ee336235.aspx)です。  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]が必要です**ALTER ANY LOGIN**メンバーシップまたはサーバーに対する権限、 **securityadmin**固定サーバー ロール。  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] では、(準備プロセスによって作成される) サーバーレベルのプリンシパルのログインまたは master データベースの `loginmanager` データベース ロールのメンバーだけが新しいログインを作成できます。  
  
 場合、**資格情報**オプションを使うと、必要もあります**ALTER ANY CREDENTIAL**サーバーに対する権限。  
  
## <a name="next-steps"></a>次の手順  
 ログインを作成するには、ログインに接続できる、[!INCLUDE[ssDE](../../includes/ssde-md.md)]または[!INCLUDE[ssSDS](../../includes/sssds-md.md)]のみに許可する権限を持つ、**パブリック**ロール。 次の操作のいくつかを実行することを検討してください。  
  
-   データベースに接続するには、ログイン用のデータベース ユーザーを作成する必要があります。 詳細については、「[CREATE USER &#40;Transact-SQL&#41;](../../t-sql/statements/create-user-transact-sql.md)」を参照してください。  
  
-   使用して、ユーザー定義サーバー ロールを作成[CREATE SERVER ROLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-role-transact-sql.md). 使用して**サーバーの役割が ALTER**しています. **メンバーの追加**ユーザー定義サーバー ロールに、新しいログインを追加します。 詳細については、次を参照してください。 [CREATE SERVER ROLE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-server-role-transact-sql.md)と[ALTER SERVER ROLE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-server-role-transact-sql.md).  
  
-   使用して**sp_addsrvrolemember**固定サーバー ロールにログインを追加します。 詳細については、次を参照してください。[サーバー レベルのロール](../../relational-databases/security/authentication-access/server-level-roles.md)と[sp_addsrvrolemember (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addsrvrolemember-transact-sql.md).  
  
-   使用して、 **GRANT**ステートメントでは、新しいログインまたはログインを含むロールにサーバー レベルのアクセス許可を付与します。 詳細については、「[GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-login-with-a-password"></a>A. パスワード付きのログインを作成する  
 次の例では、特定のユーザーのログインを作成し、パスワードを割り当てます。  
  
```  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>';  
GO  
```  
  
### <a name="b-creating-a-login-with-a-password"></a>B. パスワード付きのログインを作成する  
 次の例では、特定のユーザーのログインを作成し、パスワードを割り当てます。 `MUST_CHANGE` オプションが指定されているため、ユーザーは、最初にサーバーに接続するときにこのパスワードを変更する必要があります。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>' MUST_CHANGE;  
GO  
```  
  
### <a name="c-creating-a-login-mapped-to-a-credential"></a>C. 資格情報にマップされるログインを作成する  
 次の例では、ユーザーを使用して、特定のユーザーのログインを作成します。 このログインは資格情報にマップされます。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
CREATE LOGIN <login_name> WITH PASSWORD = '<enterStrongPasswordHere>',   
    CREDENTIAL = <credentialName>;  
GO  
```  
  
### <a name="d-creating-a-login-from-a-certificate"></a>D. 証明書からログインを作成する  
 次の例では、master データベースでの証明書から特定のユーザーのログインを作成します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
USE MASTER;  
CREATE CERTIFICATE <certificateName>  
    WITH SUBJECT = '<login_name> certificate in master database',  
    EXPIRY_DATE = '12/05/2025';  
GO  
CREATE LOGIN <login_name> FROM CERTIFICATE <certificateName>;  
GO  
```  
  
### <a name="e-creating-a-login-from-a-windows-domain-account"></a>E. Windows ドメイン アカウントからログインを作成する  
 次の例では、Windows ドメイン アカウントからログインを作成します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
CREATE LOGIN [<domainName>\<login_name>] FROM WINDOWS;  
GO  
```  
  
### <a name="f-creating-a-login-from-a-sid"></a>F. SID からログインを作成します。  
 次の例の最初の作成、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証ログインし、ログインの SID を決定します。  
  
```  
CREATE LOGIN TestLogin WITH PASSWORD = 'SuperSecret52&&';  
  
SELECT name, sid FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
 クエリでは、SID として 0x241C11948AEEB749B0D22646DB1A19F2 を返します。 クエリでは、別の値を返します。 次のステートメントは、ログインを削除し、ログインを作成し直します。 前のクエリから SID を使用します。  
  
```  
DROP LOGIN TestLogin;  
GO  
  
CREATE LOGIN TestLogin   
WITH PASSWORD = 'SuperSecret52&&', SID = 0x241C11948AEEB749B0D22646DB1A19F2;  
  
SELECT * FROM sys.sql_logins WHERE name = 'TestLogin';  
GO  
```  
  
## <a name="examples-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="g-creating-a-sql-server-authentication-login-with-a-password"></a>G. パスワードで SQL Server 認証ログインを作成します。  
 次の例は、ログインを作成`Mary7`パスワードを持つ`A2c3456`します。  
  
```tsql  
CREATE LOGIN Mary7 WITH PASSWORD = 'A2c3456$#' ;  
```  
  
### <a name="h-using-options"></a>H. オプションを使用します。  
 次の例は、ログインを作成`Mary8`パスワードといくつかの省略可能な引数を使用します。  
  
```  
CREATE LOGIN Mary8 WITH PASSWORD = 'A2c3456$#' MUST_CHANGE,  
CHECK_EXPIRATION = ON,  
CHECK_POLICY = ON;  
```  
  
### <a name="i-creating-a-login-from-a-windows-domain-account"></a>I. Windows ドメイン アカウントからログインを作成する  
 次の例は、という名前の Windows ドメイン アカウントからログインを作成`Mary`で、`Contoso`ドメイン。  
  
```  
CREATE LOGIN [Contoso\Mary] FROM WINDOWS;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンの権限の概要](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)   
 [プリンシパル &#40;データベース エンジン&#41;](../../relational-databases/security/authentication-access/principals-database-engine.md)   
 [パスワード ポリシー](../../relational-databases/security/password-policy.md)   
 [ALTER LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/alter-login-transact-sql.md)   
 [DROP LOGIN &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-login-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [ログインの作成](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  

