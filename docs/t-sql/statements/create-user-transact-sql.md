---
title: "ユーザー (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/28/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- WITHOUT_LOGIN_TSQL
- CREATE_USER_TSQL
- SQL13.SWB.DATABASEUSER.OWNEDSCHEMAS.F1
- WITHOUT LOGIN
- CREATE USER
- ALLOW_ENCRYPTED_VALUE_MODIFICATIONS
- ALLOW_ENCRYPTED_VALUE_MODIFICATIONS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- adding users
- WITHOUT LOGIN [SQL Server]
- CREATE USER statement
- database user additions [SQL Server]
- USER WITHOUT LOGIN [SQL Server]
- users [SQL Server], adding
- users [SQL Server]
ms.assetid: 01de7476-4b25-4d58-85b7-1118fe64aa80
caps.latest.revision: 111
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 47004dfe9ec810fec68a63849755021690f98fdb
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-user-transact-sql"></a>CREATE USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースにユーザーを追加します。 11 個の種類のユーザーは、最も基本的な構文のサンプルを次に示します。  
  
**Master 内のログインに基づくユーザー**これは、最も一般的なユーザーの種類。  
  
-   Windows Active Directory アカウントに基づくログインに基づくユーザー。 `CREATE USER [Contoso\Fritz];`     
-   Windows グループに基づくログインに基づくユーザー。 `CREATE USER [Contoso\Sales];`   
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用したログインに基づくユーザー。 `CREATE USER Mary;`  
  
**データベースで認証されるユーザー**データベースの移植性を高めるためにはお勧めします。  
 常に許可[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]です。 包含データベースでのみ許可[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]です。  
  
-   ログインのない Windows ユーザーに基づくユーザー。 `CREATE USER [Contoso\Fritz];`    
-   ログインのない Windows グループに基づくユーザー。 `CREATE USER [Contoso\Sales];`  
-   内のユーザー[!INCLUDE[ssSDS](../../includes/sssds-md.md)]または[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]Azure Active Directory ユーザーに基づきます。 `CREATE USER [Contoso\Fritz] FROM EXTERNAL PROVIDER;`     

-   パスワードを持つ包含データベース ユーザー。 (で利用できない[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)])。`CREATE USER Mary WITH PASSWORD = '********';`   
  
**Windows グループ ログインを介して接続する Windows プリンシパルに基づくユーザー**  
  
-   ログインのない Windows ユーザーに基づくユーザーでありながら、Windows グループのメンバーシップを介して[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続できるユーザー。 `CREATE USER [Contoso\Fritz];`  
  
-   ログインのない Windows グループに基づくユーザーでありながら、別の Windows グループのメンバーシップを介して[!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続できるユーザー。 `CREATE USER [Contoso\Fritz];`  
  
**認証できないユーザー**にこれらのユーザーがログインできない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]または[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
-   ログインのないユーザー。 ログインできませんが、権限の付与対象となります。 `CREATE USER CustomApp WITHOUT LOGIN;`    
-   証明書に基づくユーザー。 ログインできませんが、権限の付与対象となり、モジュールに署名できます。 `CREATE USER TestProcess FOR CERTIFICATE CarnationProduction50;`  
-   非対称キーに基づくユーザー。 ログインできませんが、権限の付与対象となり、モジュールに署名できます。 `CREATE User TestProcess FROM ASYMMETRIC KEY PacificSales09;`   
 
![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
-- Syntax Users based on logins in master  
CREATE USER user_name   
    [   
        { FOR | FROM } LOGIN login_name   
    ]  
    [ WITH <limited_options_list> [ ,... ] ]   
[ ; ]  
  
--Users that authenticate at the database  
CREATE USER   
    {  
      windows_principal [ WITH <options_list> [ ,... ] ]  
  
    | user_name WITH PASSWORD = 'password' [ , <options_list> [ ,... ]   
    | Azure_Active_Directory_principal FROM EXTERNAL PROVIDER   
    }  
  
 [ ; ]  
  
--Users based on Windows principals that connect through Windows group logins  
CREATE USER   
    {   
          windows_principal [ { FOR | FROM } LOGIN windows_principal ]  
        | user_name { FOR | FROM } LOGIN windows_principal  
}  
    [ WITH <limited_options_list> [ ,... ] ]   
[ ; ]  
  
--Users that cannot authenticate   
CREATE USER user_name   
    {  
         WITHOUT LOGIN [ WITH <limited_options_list> [ ,... ] ]  
       | { FOR | FROM } CERTIFICATE cert_name   
       | { FOR | FROM } ASYMMETRIC KEY asym_key_name   
    }  
 [ ; ]  
  
<options_list> ::=  
      DEFAULT_SCHEMA = schema_name  
    | DEFAULT_LANGUAGE = { NONE | lcid | language name | language alias }  
    | SID = sid   
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ] ]  
  
<limited_options_list> ::=  
      DEFAULT_SCHEMA = schema_name ]   
    | ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ ON | OFF ] ]  
  
-- SQL Database syntax when connected to a federation member  
CREATE USER user_name  
[;]  
```  

```  
-- Syntax for Azure SQL Data Warehouse  
  
CREATE USER user_name   
    [ { { FOR | FROM } { LOGIN login_name }   
      | WITHOUT LOGIN  
    ]   
    [ WITH DEFAULT_SCHEMA = schema_name ]  
[;]

CREATE USER Azure_Active_Directory_principal FROM EXTERNAL PROVIDER  
    [ WITH DEFAULT_SCHEMA = schema_name ]  
[;]
``` 
  
```  
-- Syntax for Parallel Data Warehouse  
  
CREATE USER user_name   
    [ { { FOR | FROM }  
      {   
        LOGIN login_name   
      }   
      | WITHOUT LOGIN  
    ]   
    [ WITH DEFAULT_SCHEMA = schema_name ]  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *user_name*  
 データベース内でユーザーを識別する名前を指定します。 *user_name*は、 **sysname**です。 半角 128 文字まで指定できます。 Windows プリンシパルに基づいてユーザーを作成する場合、別のユーザー名を指定しないと、Windows プリンシパル名がユーザー名になります。  
  
 ログイン*login_name*  
 作成するデータベース ユーザーのログインを指定します。 *login_name*サーバーで有効なログインをする必要があります。 Windows プリンシパルに基づくログイン (ユーザーまたはグループ) か、または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証を使用したログインを指定できます。 この [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインをデータベースに対して入力すると、データベースでは、作成されるデータベース ユーザーの名前と ID が取得されます。 Windows プリンシパルからマップされたログインを作成する場合は、形式を使用して**[***\<domainName >*  **\\**   *\<loginName >***]**です。 例については、次を参照してください。[構文の概要](#SyntaxSummary)です。  
  
 CREATE USER ステートメントが SQL のバッチ内の唯一のステートメントである場合、Windows Azure SQL データベースでは WITH LOGIN 句がサポートされます。 CREATE USER ステートメントが SQL のバッチ内の唯一のステートメントではない場合、または動的 SQL で実行されていない場合、WITH LOGIN 句はサポートされません。  
  
 DEFAULT_SCHEMA = *schema_name*  
 このデータベース ユーザー用のオブジェクトの名前を解決するときに、サーバーで最初に検索されるスキーマを指定します。  
  
 '*windows_principal*'  
 データベース ユーザーを作成する Windows プリンシパルを指定します。 *Windows_principal* Windows ユーザーまたは Windows グループを指定できます。 ユーザーが作成される場合でも、 *windows_principal*ログインは存在しません。 接続するときに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合、 *windows_principal*ログイン、Windows プリンシパルを認証するのには存在しません、[!INCLUDE[ssDE](../../includes/ssde-md.md)]ログインを持っている Windows グループのメンバーシップを通じて、または接続文字列にする必要があります初期カタログとして、包含データベースを指定します。 を、Windows プリンシパルからユーザーを作成する場合は、形式を使用して**[***\<domainName >*  **\\**   *\<loginName >***]**です。 例については、次を参照してください。[構文の概要](#SyntaxSummary)です。 Active Directory ユーザーに基づくユーザーより小さい 21 文字の名前に制限されます。    
  
 '*Azure_Active_Directory_principal*'  
 **適用されます**: [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]、[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]です。  
  
 データベース ユーザーが作成される Azure Active Directory のプリンシパルを指定します。 *Azure_Active_Directory_principal* Azure Active Directory ユーザー、または Azure Active Directory グループを指定できます。 (Azure Active Directory ユーザー Windows 認証ログインを持つことはできません[!INCLUDE[ssSDS](../../includes/sssds-md.md)]; のみのデータベース ユーザーです)。接続文字列には、初期カタログとして、包含データベースを指定する必要があります。 

 ユーザーの場合は、プリンシパルのドメインの完全なエイリアスを使用します。   
 
-   `CREATE USER [bob@contoso.com] FROM EXTERNAL PROVIDER;`  
  
-   `CREATE USER [alice@fabrikam.onmicrosoft.com] FROM EXTERNAL PROVIDER;`

 使用するセキュリティ グループの場合、*表示名*セキュリティ グループのです。 *看護師*セキュリティ グループを使用します。  
  
-   `CREATE USER [Nurses] FROM EXTERNAL PROVIDER;`  
  
 詳細については、「 [Azure Active Directory 認証を使用して SQL Database に接続する](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication)」を参照してください。  
  
パスワード = '*パスワード*'  
 **適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 包含データベースでのみ使用できます。 作成するユーザーのパスワードを指定します。 以降で[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]保存されたパスワード情報はソルト化パスワードの sha-512 を使用して計算されます。  
  
WITHOUT LOGIN  
 ユーザーを既存のログインにマップしません。  
  
証明書*cert_name*  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 作成するデータベース ユーザーの証明書を指定します。  
  
非対称キー *asym_key_name*  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 作成するデータベース ユーザーの非対称キーを指定します。  
  
DEFAULT_LANGUAGE = *{NONE |\<lcid > |\<言語名 > |\<言語の別名 >}*  
 **適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 新しいユーザーの既定の言語を指定します。 ユーザーに対して既定の言語を指定した場合、データベースの既定の言語を後で変更しても、ユーザーの既定の言語は指定した言語のままになります。 既定の言語を指定しない場合、データベースの既定の言語がユーザーの既定の言語として使用されます。 ユーザーに対して既定の言語を指定しない場合、データベースの既定の言語を後で変更すると、ユーザーの既定の言語はデータベースの新しい既定の言語に変更されます。  
  
> [!IMPORTANT]  
>  *DEFAULT_LANGUAGE*は包含データベース ユーザーにのみ使用します。  
  
SID = *sid*  
 **適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 包含データベースにパスワード ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 認証) を持つユーザーに対してのみ適用されます。 新しいデータベース ユーザーの SID を指定します。 このオプションを選択しない場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって SID が自動的に割り当てられます。 複数のデータベースで同じ ID (SID) を持つユーザーを作成するには SID パラメーターを使用します。 これは、機能は、Always On フェールオーバーの準備をする複数のデータベース内のユーザーを作成するときに便利です。 ユーザーの SID を特定するのには、sys.database_principals をクエリします。  
  
ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = [ON |**OFF** ]  
 **適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
 一括コピー操作で、サーバーに対する暗号化メタデータ チェックを抑制します。 これにより、データの暗号化を解除せずにテーブルまたはデータベース間でデータを一括コピーを暗号化するユーザー。 既定値は OFF です。  
  
> [!WARNING]  
>  このオプションを不適切に使用すると、データが破損する場合があります。 詳細については、次を参照してください。[機密性の高いデータで保護された移行 Always Encrypted](../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md)です。  
  
## <a name="remarks"></a>解説  
 FOR LOGIN を省略した場合、新しいデータベース ユーザーは同じユーザー名を持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにマップされます。  
  
 既定のスキーマは、このデータベース ユーザー用のオブジェクトの名前を解決するときに、サーバーで最初に検索されるスキーマになります。 特に指定しない限り、このデータベース ユーザーによって作成されたオブジェクトの所有者になるのは、既定のスキーマです。  
  
 ユーザーに既定のスキーマが設定されている場合は、その既定のスキーマが使用されます。 ユーザーに既定のスキーマが指定されておらず、そのユーザーが所属しているグループに既定のスキーマが指定されている場合は、グループの既定のスキーマが使用されます。 ユーザーに既定のスキーマが指定されておらず、そのユーザーが複数のグループに所属している場合、ユーザーの既定のスキーマは、最も小さい principle_id と明示的に設定された既定のスキーマを持つ Windows グループのスキーマになります。 利用可能な既定のスキーマのいずれかを、使用するスキーマとして明示的に選択することはできません。で、ユーザーの既定のスキーマを特定できない場合、 **dbo**スキーマが使用されます。  
  
 DEFAULT_SCHEMA は、このオプションが指すスキーマが作成されていなくても設定できます。  
  
 DEFAULT_SCHEMA は、証明書または非対称キーにマップされるユーザーを作成する場合には指定できません。  
  
 ユーザーが固定サーバー ロール sysadmin のメンバーである場合、DEFAULT_SCHEMA の値は無視されます。 固定サーバー ロール sysadmin のすべてのメンバーには、`dbo` の既定のスキーマが割り当てられます。  
  
 WITHOUT LOGIN 句でユーザーを作成する場合、ユーザーは SQL Server ログインにマップされず、 他のデータベースには guest として接続できます。 ログインのないこのユーザーには権限を割り当てることができます。セキュリティ コンテキストがログインのないユーザーに変更されると、元のユーザーはログインのないユーザーの権限を受け取ります。 例を参照して[D. 作成とログインのないユーザーを使用して](#withoutLogin)です。  
  
 Windows プリンシパルに割り当てられているユーザーは、円記号を含めることができますのみ (**\\**)。  
  
 guest ユーザーは各データベース内に既に存在しているため、CREATE USER を使用して guest ユーザーを作成することはできません。 guest ユーザーは、次のように CONNECT 権限を与えることで有効にできます。  
  
```  
GRANT CONNECT TO guest;  
GO  
```  
  
 データベース ユーザーに関する情報は、 [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)カタログ ビューです。  
  
##  <a name="SyntaxSummary"></a>構文の概要  
 **Master 内のログインに基づくユーザー**  
  
 ログインに基づくユーザーに関して使用できる構文を次に示します。 既定のスキーマ オプションは除外しています。  
  
-   `CREATE USER [Domain1\WindowsUserBarry]`  
-   `CREATE USER [Domain1\WindowsUserBarry] FOR LOGIN Domain1\WindowsUserBarry`  
-   `CREATE USER [Domain1\WindowsUserBarry] FROM LOGIN Domain1\WindowsUserBarry`  
-   `CREATE USER [Domain1\WindowsGroupManagers]`  
-   `CREATE USER [Domain1\WindowsGroupManagers] FOR LOGIN [Domain1\WindowsGroupManagers]`  
-   `CREATE USER [Domain1\WindowsGroupManagers] FROM LOGIN [Domain1\WindowsGroupManagers]`  
-   `CREATE USER SQLAUTHLOGIN`  
-   `CREATE USER SQLAUTHLOGIN FOR LOGIN SQLAUTHLOGIN`  
-   `CREATE USER SQLAUTHLOGIN FROM LOGIN SQLAUTHLOGIN`  
  
**データベースで認証されるユーザー**  
  
 包含データベースでのみ使用できるユーザーに関して使用できる構文を次に示します。 作成されたユーザーはのどのログインに関連付けられていない、**マスター**データベース。 既定のスキーマおよび言語オプションは除外しています。  
  
> [!IMPORTANT]  
>  この構文では、データベースへのアクセス許可と[!INCLUDE[ssDE](../../includes/ssde-md.md)]への新しいアクセス許可がユーザーに与えられます。  
  
-   `CREATE USER [Domain1\WindowsUserBarry]`  
-   `CREATE USER [Domain1\WindowsGroupManagers]`  
-   `CREATE USER Barry WITH PASSWORD = 'sdjklalie8rew8337!$d'`  
  
**Master 内のログインのない Windows プリンシパルに基づくユーザー**  
  
 次の一覧へのアクセスを持つユーザーに関して使用できる構文を示しています、[!INCLUDE[ssDE](../../includes/ssde-md.md)]によって、Windows グループしますが、ないログイン**マスター**です。 この構文は、あらゆる種類のデータベースで使用できます。 既定のスキーマおよび言語オプションは除外しています。  
  
 この構文は master 内のログインに基づくユーザーの構文と似ていますが、このカテゴリのユーザーは master 内にログインを持ちません。 ユーザーは、Windows グループ ログインを介して[!INCLUDE[ssDE](../../includes/ssde-md.md)]にアクセスする許可が与えられている必要があります。  
  
 この構文は Windows プリンシパルに基づく包含データベース ユーザーの構文に似ていますが、このカテゴリのユーザーには[!INCLUDE[ssDE](../../includes/ssde-md.md)]への新しいアクセス許可は与えられません。  
  
-   `CREATE USER [Domain1\WindowsUserBarry]`  
-   `CREATE USER [Domain1\WindowsUserBarry] FOR LOGIN Domain1\WindowsUserBarry`  
-   `CREATE USER [Domain1\WindowsUserBarry] FROM LOGIN Domain1\WindowsUserBarry`  
-   `CREATE USER [Domain1\WindowsGroupManagers]`  
-   `CREATE USER [Domain1\WindowsGroupManagers] FOR LOGIN [Domain1\WindowsGroupManagers]`  
-   `CREATE USER [Domain1\WindowsGroupManagers] FROM LOGIN [Domain1\WindowsGroupManagers]`  
  
**認証できないユーザー**  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にログインできないユーザーに関して使用できる構文を次に示します。  
  
-   `CREATE USER RIGHTSHOLDER WITHOUT LOGIN`  
-   `CREATE USER CERTUSER FOR CERTIFICATE SpecialCert`  
-   `CREATE USER CERTUSER FROM CERTIFICATE SpecialCert`  
-   `CREATE USER KEYUSER FOR ASYMMETRIC KEY SecureKey`  
-   `CREATE USER KEYUSER FROM ASYMMETRIC KEY SecureKey`  
  
## <a name="security"></a>セキュリティ  
 ユーザーを作成するとデータベースへのアクセス許可が与えられますが、データベース内のオブジェクトに対するアクセス許可は自動的には与えられません。 ユーザーを作成した後の一般的な操作として、データベース オブジェクトに対する権限を持つデータベース ロールにユーザーを追加するか、またはオブジェクト権限をユーザーに付与します。 権限システムの設計の詳細については、「 [データベース エンジンの権限の概要](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)」を参照してください。  
  
### <a name="special-considerations-for-contained-databases"></a>包含データベースに関する注意事項  
 ユーザーが、ログインを持っていない場合、包含データベースに接続するとき、**マスター**データベース、接続文字列は、初期カタログとして、包含データベース名を含める必要があります。 初期カタログ パラメーターは、パスワードを持つ包含データベース ユーザーに対して常に必要になります。  
  
 包含データベースでは、ユーザーを作成することにより、データベースと[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスとを分離して、データベースを [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の別のインスタンスに簡単に移動できるようになります。 詳細については、次を参照してください。 [Contained Databases](../../relational-databases/databases/contained-databases.md)と[包含データベース ユーザー - ポータブルなデータベース](../../relational-databases/security/contained-database-users-making-your-database-portable.md)です。 基づくユーザーから、データベース ユーザーを変更する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パスワードを持つ包含データベース ユーザーを認証ログインを参照してください[sp_migrate_user_to_contained (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-migrate-user-to-contained-transact-sql.md).  
  
 包含データベースでユーザーする必要はありませんログインを持つ、**マスター**データベース。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 管理者は、包含データベースに対するアクセス許可を [!INCLUDE[ssDE](../../includes/ssde-md.md)] レベルではなくデータベース レベルで付与できることを理解する必要があります。 詳しくは、「 [Security Best Practices with Contained Databases](../../relational-databases/databases/security-best-practices-with-contained-databases.md)」をご覧ください。  
  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] で包含データベース ユーザーを使用する場合、サーバー レベルのファイアウォール ルールではなく、データベース レベルのファイアウォール ルールを使用してアクセスを構成します。 詳細については、次を参照してください。 [sp_set_database_firewall_rule & #40 です。Azure SQL データベース &#41;](../../relational-databases/system-stored-procedures/sp-set-database-firewall-rule-azure-sql-database.md).
 
[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]と[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)]包含データベース ユーザー、SSMS は、多要素認証をサポートできます。 詳細については、「 [SQL Database と SQL Data Warehouse での Azure AD MFA のための SSMS のサポート](https://azure.microsoft.com/documentation/articles/sql-database-ssms-mfa-authentication/)」をご覧ください。  
  
### <a name="permissions"></a>Permissions  
 データベースに対する ALTER ANY USER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-database-user-based-on-a-sql-server-login"></a>A. SQL Server ログインに基づくデータベース ユーザーを作成する  
 次の例では、最初に `AbolrousHazem` という [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを作成し、次に対応するデータベース ユーザー `AbolrousHazem` を `AdventureWorks2012` に作成します。  
  
```  
CREATE LOGIN AbolrousHazem   
    WITH PASSWORD = '340$Uuxwp7Mcxo7Khy';  
```   
ユーザー データベースを変更します。 たとえば、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を使用して、`USE AdventureWorks2012`ステートメントです。 [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]、ユーザー データベースへの新しい接続を行う必要があります。

```   
CREATE USER AbolrousHazem FOR LOGIN AbolrousHazem;  
GO   
```  
  
### <a name="b-creating-a-database-user-with-a-default-schema"></a>B. 既定のスキーマでデータベース ユーザーを作成する  
 次の例では、まず `WanidaBenshoof` というサーバー ログインをパスワード付きで作成し、次に対応するデータベース ユーザー `Wanida` を既定のスキーマ `Marketing` で作成します。  
  
```  
CREATE LOGIN WanidaBenshoof   
    WITH PASSWORD = '8fdKJl3$nlNv3049jsKK';  
USE AdventureWorks2012;  
CREATE USER Wanida FOR LOGIN WanidaBenshoof   
    WITH DEFAULT_SCHEMA = Marketing;  
GO  
```  
  
### <a name="c-creating-a-database-user-from-a-certificate"></a>C. 証明書からデータベース ユーザーを作成する  
 次の例では、証明書 `JinghaoLiu` からデータベース ユーザー `CarnationProduction50` を作成します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
USE AdventureWorks2012;  
CREATE CERTIFICATE CarnationProduction50  
    WITH SUBJECT = 'Carnation Production Facility Supervisors',  
    EXPIRY_DATE = '11/11/2011';  
GO  
CREATE USER JinghaoLiu FOR CERTIFICATE CarnationProduction50;  
GO   
```  
  
###  <a name="withoutLogin"></a> D. ログインのないユーザーを作成して使用する  
 次の例では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインにマップされないデータベース ユーザー `CustomApp` を作成します。 その後、ユーザー `adventure-works\tengiz0` に、`CustomApp` ユーザーの権限を借用する権限を許可します。  
  
```  
USE AdventureWorks2012 ;  
CREATE USER CustomApp WITHOUT LOGIN ;  
GRANT IMPERSONATE ON USER::CustomApp TO [adventure-works\tengiz0] ;  
GO   
```  
  
 ユーザー `CustomApp` が `adventure-works\tengiz0` の資格情報を使用するには、次のステートメントを実行します。  
  
```  
EXECUTE AS USER = 'CustomApp' ;  
GO  
```  
  
 `adventure-works\tengiz0` の資格情報に戻すには、次のステートメントを実行します。  
  
```  
REVERT ;  
GO  
```  
  
### <a name="e-creating-a-contained-database-user-with-password"></a>E. パスワードを持つ包含データベース ユーザーを作成する  
 次の例では、パスワードを持つ包含データベース ユーザーを作成します。 この例は、包含データベースでのみ実行できます。  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] この例は DEFAULT_LANGUAGE が削除された場合に [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] で機能します。  
  
```  
USE AdventureWorks2012 ;  
GO  
CREATE USER Carlo  
WITH PASSWORD='RN92piTCh%$!~3K9844 Bl*'  
    , DEFAULT_LANGUAGE=[Brazilian]  
    , DEFAULT_SCHEMA=[dbo]  
GO   
```  
  
### <a name="f-creating-a-contained-database-user-for-a-domain-login"></a>F. ドメイン ログインのための包含データベース ユーザーを作成する  
 次の例では、Contoso という名前のドメインの Fritz という名前のログインに対する包含データベース ユーザーを作成します。 この例は、包含データベースでのみ実行できます。  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
USE AdventureWorks2012 ;  
GO  
CREATE USER [Contoso\Fritz] ;  
GO   
```  
  
### <a name="g-creating-a-contained-database-user-with-a-specific-sid"></a>G. 特定の SID を持つ包含データベース ユーザーを作成する  
 次の例では、CarmenW という名前の、SQL Server 認証を使用する包含データベース ユーザーを作成します。 この例は、包含データベースでのみ実行できます。  
  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
USE AdventureWorks2012 ;  
GO  
CREATE USER CarmenW WITH PASSWORD = 'a8ea v*(Rd##+'  
, SID = 0x01050000000000090300000063FF0451A9E7664BA705B10E37DDC4B7;  
  
```  
  
### <a name="h-creating-a-user-to-copy-encrypted-data"></a>H. 暗号化されたデータをコピーするユーザーを作成します。  
 次の例では、(同じまたは別のデータベースの) で暗号化された列を含むテーブルの別のセットに、暗号化された列を含む、テーブルの 1 つのセットから Always Encrypted 機能によって保護されているデータをコピーできるユーザーを作成します。  詳細については、次を参照してください。[機密性の高いデータで保護された移行 Always Encrypted](../../relational-databases/security/encryption/migrate-sensitive-data-protected-by-always-encrypted.md)です。  
  
**適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。  
  
```  
CREATE USER [Chin]   
WITH   
      DEFAULT_SCHEMA = dbo  
    , ALLOW_ENCRYPTED_VALUE_MODIFICATIONS = ON ;  
```  
  

## <a name="next-steps"></a>次の手順  
ユーザーが作成した後を使用してデータベース ロールにユーザーを追加することを検討してください、 [ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md)ステートメントです。  
することも[GRANT Object Permissions](../../t-sql/statements/grant-object-permissions-transact-sql.md)ロール テーブルにアクセスできるようにします。 SQL Server セキュリティ モデルの概要については、次を参照してください。[権限](../../relational-databases/security/permissions-database-engine.md)です。   
  
## <a name="see-also"></a>参照  
 [データベース ユーザーを作成します。](../../relational-databases/security/authentication-access/create-a-database-user.md)   
 [sys.database_principals &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [ALTER USER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-user-transact-sql.md)   
 [DROP USER &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-user-transact-sql.md)   
 [CREATE LOGIN &#40;Transact-SQL&#41;](../../t-sql/statements/create-login-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [包含データベース](../../relational-databases/databases/contained-databases.md)   
 [Azure Active Directory 認証を使用して SQL データベースに接続します。](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication)   
 [データベース エンジンの権限の概要](../../relational-databases/security/authentication-access/getting-started-with-database-engine-permissions.md)  
  
  



