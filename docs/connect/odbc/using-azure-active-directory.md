---
title: ODBC ドライバーを使用した Azure Active Directory を使用して |SQL Server 用 Microsoft Docs
ms.custom: ''
ms.date: 11/08/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 52205f03-ff29-4254-bfa8-07cced155c86
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7273baec814905d86e431c5a6a8f13313b9743e4
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2018
ms.locfileid: "52536649"
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>ODBC ドライバーでの Azure Active Directory の使用
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>用途

Microsoft ODBC Driver for SQL Server バージョン 13.1 以降は、ユーザー名/パスワード、Azure Active Directory アクセス トークン、または Windows Azure Active Directory でフェデレーション id を使用して SQL Azure のインスタンスに接続する ODBC アプリケーション統合認証 (_Windows ドライバーのみ_)。 ODBC ドライバー バージョン 13.1、トークン認証は、Azure Active Directory のアクセスの_Windows のみ_します。 ODBC ドライバー バージョン 17 の上には、すべてのプラットフォーム (Windows、Linux および Mac) でこの認証をサポートしています。 ログイン id と新しい Azure Active Directory 対話型認証は、Windows の ODBC ドライバー バージョン 17.1 の内容で導入されました。 これらすべては、新しい DSN と接続文字列キーワード、および接続属性を使用して行います。

> [!NOTE]
> Linux および macOS 上の ODBC ドライバーは、Active Directory フェデレーション サービスをサポートしていません。 Linux から Azure Active Directory ユーザー名/パスワード認証を使用している、または macOS のクライアントと、Active Directory の構成は、フェデレーション サービスが含まれています、認証が失敗する可能性があります。

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>新規作成または変更された DSN と接続文字列キーワード

`Authentication`キーワード DSN または接続文字列で接続するときに認証モードの制御に使用します。 接続文字列に設定された値よりも優先される DSN に指定されている場合。 _属性値が事前_の`Authentication`設定は、接続文字列と DSN の値から計算された値。

|[オブジェクト名]|値|既定|[説明]|
|-|-|-|-|
|`Authentication`|(設定しません) (空の文字列)、 `SqlPassword`、 `ActiveDirectoryPassword`、 `ActiveDirectoryIntegrated`、 `ActiveDirectoryInteractive`|(未設定)|認証モードを制御します。<table><tr><th>ReplTest1<th>[説明]<tr><td>(未設定)<td>認証モードの他のキーワード (既存のレガシ接続オプション) によって決まります<tr><td>(空の文字列)<td>接続文字列: "{0}"オーバーライド設定を解除し、`Authentication`値、DSN に設定します。<tr><td>`SqlPassword`<td>ユーザー名とパスワードを使用して SQL Server インスタンスに直接認証します。<tr><td>`ActiveDirectoryPassword`<td>ユーザー名とパスワードを使用して id を Azure Active Directory で認証します。<tr><td>`ActiveDirectoryIntegrated`<td>_Windows ドライバーのみ_します。 統合認証を使用して id を Azure Active Directory で認証します。<tr><td>`ActiveDirectoryInteractive`<td>_Windows ドライバーのみ_します。 対話型認証を使用して id を Azure Active Directory で認証します。</table>|
|`Encrypt`|(未設定)、`Yes`、`No`|(説明を参照してください)|接続の暗号化を制御します。 場合の前の属性値、`Authentication`の設定が_none_ 、DSN または接続文字列は、既定値は`Yes`します。 それ以外の場合、既定値は `No` です。 場合、属性`SQL_COPT_SS_AUTHENTICATION`の前の属性値を上書き`Authentication`、明示的に DSN または接続文字列または接続属性での暗号化の値を設定します。 暗号化の前の属性値が`Yes`値が設定されている場合`Yes`DSN または接続文字列にします。|

## <a name="new-andor-modified-connection-attributes"></a>接続の新規作成または変更された属性

次の場合、あらかじめ、属性を導入または、Azure Active Directory 認証をサポートするように変更されているいずれかが接続を接続します。 接続属性に対応する接続文字列または DSN キーワードが設定されている場合は、接続属性が優先されます。

|属性|型|値|既定|[説明]|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`、`SQL_AU_PASSWORD`、`SQL_AU_AD_INTEGRATED`、`SQL_AU_AD_PASSWORD`、`SQL_AU_AD_INTERACTIVE`、`SQL_AU_RESET`|(未設定)|説明を参照してください。`Authentication`上記キーワード。 `SQL_AU_NONE` セットを明示的にオーバーライドするために提供されます`Authentication`DSN または接続文字列の値に`SQL_AU_RESET`DSN または接続文字列の値を優先できるように、設定された場合に、属性と設定解除されます。|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|ポインター`ACCESSTOKEN`または NULL|NULL|Null 以外の場合は、使用する azure Ad アクセス トークンを指定します。 アクセス トークンを指定するエラーとも`UID`、 `PWD`、 `Trusted_Connection`、または`Authentication`接続文字列キーワードまたは同等の属性。 <br> **注:** ODBC ドライバー バージョン 13.1 に対してのみサポートしてこの_Windows_します。|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(説明を参照してください)|接続の暗号化を制御します。 `SQL_EN_OFF` `SQL_EN_ON`を無効にして、それぞれの暗号化を有効にします。 場合の前の属性値、`Authentication`の設定が_none_または`SQL_COPT_SS_ACCESS_TOKEN`が設定されていると`Encrypt`既定値は、DSN または接続文字列で指定されていない`SQL_EN_ON`します。 それ以外の場合、既定値は `SQL_EN_OFF` です。 場合接続属性`SQL_COPT_SS_AUTHENTICATION`に設定されていない_none_に明示的に設定して、`SQL_COPT_SS_ENCRYPT`目的の値を場合`Encrypt`DSN または接続文字列で指定されていません。 この属性のコントロールの有効値[接続の暗号化を使用するかどうか。](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation)|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|AAD のプリンシパルにパスワードの変更は ODBC 接続を実現できないため、Azure Active Directory でサポートされません。 <br><br>SQL Server 2005 では、SQL Server 認証におけるパスワードの期限切れが導入されました。 `SQL_COPT_SS_OLDPWD`クライアントは、接続の古いと新しいパスワードの両方を提供できるようにする属性が追加されます。 この属性が設定されている場合、接続文字列には変更された "古いパスワード" が含まれているので、プロバイダーは最初の接続またはそれ以降の接続で接続プールを使用しません。|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`、`SQL_IS_ON`|`SQL_IS_OFF`|_非推奨とされます_; を使用して、`SQL_COPT_SS_AUTHENTICATION`設定`SQL_AU_AD_INTEGRATED`代わりにします。 <br><br>強制的には、サーバー ログインのアクセスの検証に Windows 認証 (Kerberos では、Linux および macOS) の使用します。 Windows 認証を使用すると、ドライバーがの一部として提供されるユーザー id とパスワードの値を無視`SQLConnect`、 `SQLDriverConnect`、または`SQLBrowseConnect`処理します。|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Azure Active Directory (Windows ドライバー) の UI の変更点

Azure AD で認証を使用するために必要な追加のオプションの DSN セットアップとドライバーの接続の Ui が強化されています。

### <a name="creating-and-editing-dsns-in-the-ui"></a>作成と編集 UI で Dsn

作成するときに、認証オプションを使用して新しい Azure AD またはドライバーのセットアップ UI を使用して既存の DSN を編集することができます。

SQL Azure への Azure Active Directory 統合認証の場合: `Authentication=ActiveDirectoryIntegrated`

![CreateNewDSN_ADIntegrated.png](windows/CreateNewDSN_ADIntegrated.png)

`Authentication=ActiveDirectoryPassword` SQL Azure に Azure Active Directory ユーザー名/パスワード認証

![CreateNewDSN_ADPassword.png](windows/CreateNewDSN_ADPassword.png)

`Authentication=ActiveDirectoryInteractive` SQL Azure に Azure Active Directory 対話型認証

![CreateNewDSN_ADInteractive.png](windows/CreateNewDSN_ADInteractive.png)

`Authentication=SqlPassword` SQL Server へのユーザー名/パスワード認証 (Azure またはそれ以外の場合)

![CreateNewDSN_SQLServer.png](windows/CreateNewDSN_SQLServer.png)

`Trusted_Connection=Yes` Windows のレガシ SSPI 統合認証

![CreateNewDSN_winSSPI.png](windows/CreateNewDSN_winSSPI.png)

5 つのオプションに対応`Trusted_Connection=Yes`(既存レガシ Windows 統合認証の SSPI 専用) と`Authentication=` `ActiveDirectoryIntegrated`、 `SqlPassword`、 `ActiveDirectoryPassword`、および`ActiveDirectoryInteractive`、それぞれします。

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect プロンプト (Windows ドライバー)

接続を完了に必要な情報を要求するときに、SQLDriverConnect によって表示されるプロンプト ダイアログには、Azure AD 認証のための 3 つの新しいオプションが含まれています。

![ServerLogin.png](windows/ServerLogin.png)

これらのオプションは、UI 上の DSN セットアップで使用できる、同じ 5 つに対応します。

### <a name="example-connection-strings"></a>接続文字列の例
1. SQL Server 認証のレガシ構文。 サーバー証明書が検証されていないと、サーバーがそれを適用している場合のみ暗号化を使用します。 ユーザー名/パスワードは、接続文字列で渡されます。
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. SQL 認証の新しい構文です。 クライアントが暗号化を要求 (既定値の`Encrypt`は`true`) し検証済みの暗号化の設定に関係なく、サーバー証明書を取得します (しない限り、`TrustServerCertificate`に設定されている`true`)。 ユーザー名/パスワードは、接続文字列で渡されます。
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. 統合 Windows 認証 (Kerberos では、Linux および macOS) (SQL Server または SQL IaaS) のための SSPI を現在の構文を使用します。 暗号化を使用しない場合、サーバー証明書は検証されません。 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Windows ドライバーのみ_)。統合 Windows 認証 (ターゲット データベースが SQL Server または SQL IaaS) の場合は、SSPI - 新しい構文を使用します。 クライアントが暗号化を要求 (既定値の`Encrypt`は`true`) し検証済みの暗号化の設定に関係なく、サーバー証明書を取得します (しない限り、`TrustServerCertificate`に設定されている`true`)。 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. AAD のユーザー名/パスワード認証 (ターゲット データベースが Azure SQL DB の場合)。 暗号化設定に関係なく、サーバー証明書が検証を取得します (しない限り、`TrustServerCertificate`に設定されている`true`)。 ユーザー名/パスワードは、接続文字列で渡されます。 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Windows ドライバーのみ_)。統合 Windows 認証が ADAL を使用して、Windows アカウントの資格情報を AAD に発行されたアクセス トークンを引き換えを含む、Azure SQL Database が、ターゲット データベースにある場合します。 暗号化設定に関係なく、サーバー証明書が検証を取得します (しない限り、`TrustServerCertificate`に設定されている`true`)。 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (_Windows ドライバーのみ_)。AAD 対話型認証では、Azure multi-factor Authentication のテクノロジを使用して、接続を設定します。 ログイン ID を提供することで、このモードで Windows Azure の認証ダイアログがトリガーされ、接続を完了するためのパスワードを入力できます。 ユーザー名は、接続文字列で渡されます。
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![WindowsAzureAuth.png](windows/WindowsAzureAuth.png)

> [!NOTE] 
>- Windows ODBC ドライバーを使用した Active Directory の新しいオプションを使用している場合ことを確認します。、 [for SQL Server の Active Directory 認証ライブラリ](https://go.microsoft.com/fwlink/?LinkID=513072)がインストールされています。 Linux と macOS のドライバーを使用して、ことを確認します。`libcurl`がインストールされています。 ドライバー バージョン 17.2 以降では、これは明示的な依存関係、その他の認証方法または ODBC の操作に必要ではないためです。
>- を SQL Server アカウントのユーザー名とパスワードを使用して接続を使用できます、新しい`SqlPassword`オプションは、このオプションにより、より安全な接続の既定値から場合に、特に SQL Azure の使用することをお勧めします。
>- を、Azure Active Directory アカウントのユーザー名とパスワードを使用して接続するには指定`Authentication=ActiveDirectoryPassword`接続文字列で、`UID`と`PWD`キーワードで、ユーザー名とパスワードをそれぞれします。
>- を Windows 統合認証または Active Directory 統合 (Windows ドライバー) 認証を使用して接続するには指定`Authentication=ActiveDirectoryIntegrated`接続文字列にします。 ドライバーは、適切な認証モードを自動的に選択します。 `UID` `PWD`指定されていない必要があります。
>- Active Directory Interactive (Windows ドライバー) の認証を使用して接続する`UID`指定する必要があります。

## <a name="authenticating-with-an-access-token"></a>アクセス トークンを使用した認証

`SQL_COPT_SS_ACCESS_TOKEN`接続前の属性の代わりにユーザー名とパスワード、認証の Azure AD から取得したアクセス トークンを使用できるように、ネゴシエーションと、ドライバーによって、アクセス トークンの取得にも実行されません。 アクセス トークンを使用する設定、`SQL_COPT_SS_ACCESS_TOKEN`へのポインターへの接続属性、`ACCESSTOKEN`構造体。

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

`ACCESSTOKEN` 4 バイトで構成される可変長の構造は、_長さ_続けて_長さ_アクセス トークンを形成する非透過的なデータのバイト数。 経由で 1 つ取得したどの SQL Server では、アクセス トークンを処理するため、 [OAuth 2.0](https://docs.microsoft.com/azure/active-directory/develop/active-directory-authentication-scenarios) JSON 応答は、各バイトのパディング バイトの ASCII 文字のみを格納している ucs-2 ではこの文字列のような 0 が続くように展開する必要がありますただし、は、トークン。非透過の値と、バイト単位で指定された長さには、null 終端記号を含めないでください。 制約のため、かなり長さと形式、認証には、このメソッドは使用したプログラムで使用可能なのみ、`SQL_COPT_SS_ACCESS_TOKEN`接続属性です。 対応する DSN または接続文字列キーワードはありません。 接続文字列に含める必要がありますいない`UID`、 `PWD`、 `Authentication`、または`Trusted_Connection`キーワード。

> [!NOTE]
> ODBC ドライバー バージョン 13.1 に対してこの認証のみサポートして_Windows_します。

## <a name="azure-active-directory-authentication-sample-code"></a>Azure Active Directory 認証サンプル コード

次の例では、接続キーワードを持つ Azure Active Directory を使用して SQL Server への接続に必要なコードを示します。 アプリケーション コード自体を変更する必要がないことに注意してください。接続文字列、または DSN を使用する場合は、認証に AAD を使用するために必要な唯一の変更を示します。
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
次の例では、アクセス トークン認証による Azure Active Directory を使用して SQL Server への接続に必要なコードを示します。 この場合、アクセス トークンを処理し、関連付けられている接続属性を設定するアプリケーション コードを変更する必要は。
~~~
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server}"
    SQLCHAR accessToken[] = "eyJ0eXAiOi..."; // In the format extracted from an OAuth JSON response
    ...
    DWORD dataSize = 2 * strlen(accessToken);
    ACCESSTOKEN *pAccToken = malloc(sizeof(ACCESSTOKEN) + dataSize);
    pAccToken->dataSize = dataSize;
    // Expand access token with padding bytes
    for(int i = 0, j = 0; i < dataSize; i += 2, j++) {
        pAccToken->data[i] = accessToken[j];
        pAccToken->data[i+1] = 0;
    }
    ...
    SQLSetConnectAttr(hDbc, SQL_COPT_SS_ACCESS_TOKEN, (SQLPOINTER)pAccToken, SQL_IS_POINTER);
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);      
    ...
    free(pAccToken);
~~~
Azure Active Directory 対話型認証で使用する接続文字列の例は、次のです。 ない PWD フィールド、パスワードを入力するときは、Windows Azure Authentication 画面を使用すると、注意してください。
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~

## <a name="see-also"></a>参照
[Azure AD 認証を使用して Azure SQL DB のトークン ベースの認証のサポート](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

