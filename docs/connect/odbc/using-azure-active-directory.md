---
title: ODBC ドライバーで Azure Active Directory の使用 |SQL Server 用の Microsoft ドキュメント
ms.custom: ''
ms.date: 03/21/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 52205f03-ff29-4254-bfa8-07cced155c86
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b78c4e00a640da21079aebf0c4247b68f3237c25
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-azure-active-directory-with-the-odbc-driver"></a>ODBC ドライバーで Azure Active Directory の使用
[!INCLUDE[Driver_ODBC_Download](../../includes/driver_odbc_download.md)]

## <a name="purpose"></a>用途

上と 13.1 のバージョンの SQL Server 用 Microsoft ODBC Driver は、ユーザー名/パスワード、Azure Active Directory アクセス トークン、または Windows Azure Active Directory でのフェデレーション id を使用して SQL Azure のインスタンスに接続する ODBC アプリケーション統合認証 (_Windows ドライバーのみ_)。 ODBC Driver 13.1、トークンの認証は、Azure Active Directory のアクセスのバージョンの_Windows のみ_です。 ODBC ダイバー 17 と 17.1 バージョンは、すべてのプラットフォーム (Windows、Linux、Mac) でこの認証をサポートします。 新しい Azure Active Directory の対話型認証ログイン id とは、Windows 用 ODBC ドライバー バージョン 17.1 で導入されました。 これらすべては、新しい DSN と接続文字列キーワード、および接続属性を使用して行われます。

## <a name="new-andor-modified-dsn-and-connection-string-keywords"></a>新規または変更された DSN と接続文字列キーワード

`Authentication`キーワード DSN または接続文字列で接続するときに認証モードの制御に使用します。 接続文字列に設定された値よりも優先する、DSN に提供される場合。 _属性値が事前_の`Authentication`設定は、接続文字列と DSN の値から計算された値。

|名前|値|既定値|Description|
|-|-|-|-|
|`Authentication`|(設定しません)、(空の文字列)、 `SqlPassword`、 `ActiveDirectoryPassword`、 `ActiveDirectoryIntegrated`、 `ActiveDirectoryInteractive`|(未設定)|認証モードを制御します。<table><tr><th>値<th>Description<tr><td>(未設定)<td>その他のキーワード (既存のレガシ接続オプション) によって決まります認証モード<tr><td>(空の文字列)<td>(接続文字列のみ) です。上書き設定を解除し、 `Authentication` DSN にセットの値します。<tr><td>`SqlPassword`<td>ユーザー名とパスワードを使用して SQL Server インスタンスに直接認証します。<tr><td>`ActiveDirectoryPassword`<td>ユーザー名とパスワードを使用して Azure Active Directory id を認証します。<tr><td>`ActiveDirectoryIntegrated`<td>_Windows のドライバーのみ_です。 統合認証を使用して Azure Active Directory id を認証します。<tr><td>`ActiveDirectoryInteractive`<td>_Windows のドライバーのみ_です。 対話型の認証を使用して Azure Active Directory id を認証します。</table>|
|`Encrypt`|(設定しません)、 `Yes`、 `No`|(説明を参照してください)|接続の暗号化を制御します。 場合は前の属性の値、`Authentication`の設定が_none_、既定値は`Yes`します。 それ以外の場合、既定値は`No`します。 暗号化の前の属性値は`Yes`値が設定されている場合`Yes`DSN または接続文字列にします。|

## <a name="new-andor-modified-connection-attributes"></a>新規または変更済みの接続属性

次の場合、あらかじめ、属性を導入または、Azure Active Directory 認証をサポートするように変更されているいずれかがへの接続を接続します。 接続属性に対応する接続文字列または DSN キーワードと、設定されている場合は、接続属性が優先されます。

|属性|型|値|既定値|Description|
|-|-|-|-|-|
|`SQL_COPT_SS_AUTHENTICATION`|`SQL_IS_INTEGER`|`SQL_AU_NONE`、`SQL_AU_PASSWORD`、`SQL_AU_AD_INTEGRATED`、`SQL_AU_AD_PASSWORD`、`SQL_AU_AD_INTERACTIVE`、`SQL_AU_RESET`|(未設定)|説明を参照してください`Authentication`上記キーワード。 `SQL_AU_NONE` セットを明示的にオーバーライドするために提供される`Authentication`DSN または接続文字列で、値中に`SQL_AU_RESET`設定されている場合、優先する DSN または接続文字列値を許可する属性を解除します。|
|`SQL_COPT_SS_ACCESS_TOKEN`|`SQL_IS_POINTER`|ポインター`ACCESSTOKEN`または NULL|NULL|Null 以外の場合、を使用する azure Ad アクセス トークンを指定します。 アクセス トークンを指定すると、エラーは、さらに`UID`、 `PWD`、 `Trusted_Connection`、または`Authentication`接続文字列キーワードまたはそれらと同等の属性です。 <br> **注:** ODBC Driver 13.1 のバージョンのみをサポートしている_Windows_です。|
|`SQL_COPT_SS_ENCRYPT`|`SQL_IS_INTEGER`|`SQL_EN_OFF`, `SQL_EN_ON`|(説明を参照してください)|接続の暗号化を制御します。 `SQL_EN_OFF` および`SQL_EN_ON`を無効にして、それぞれの暗号化を有効にします。 場合は前の属性の値、`Authentication`の設定が_none_または`SQL_COPT_SS_ACCESS_TOKEN`が設定されていると`Encrypt`既定値は、DSN または接続文字列で指定されていない`SQL_EN_ON`です。 それ以外の場合、既定値は`SQL_EN_OFF`します。 この属性のコントロールの有効な値[接続の暗号化を使用するかどうか。](https://docs.microsoft.com/en-us/sql/relational-databases/native-client/features/using-encryption-without-validation)|
|`SQL_COPT_SS_OLDPWD`|\-|\-|\-|AAD プリンシパルへパスワードの変更は、ODBC 接続を介して実現できないため、Azure Active Directory でサポートされません。 <br><br>SQL Server 認証のパスワードの有効期限は、SQL Server 2005 で導入されました。 `SQL_COPT_SS_OLDPWD`属性は、接続の古いと、新しいパスワードの両方を提供するために使用できるように追加されました。 この属性が設定されている場合、接続文字列には変更された "古いパスワード" が含まれているので、プロバイダーは最初の接続またはそれ以降の接続で接続プールを使用しません。|
|`SQL_COPT_SS_INTEGRATED_SECURITY`|`SQL_IS_INTEGER`|`SQL_IS_OFF`,`SQL_IS_ON`|`SQL_IS_OFF`|_非推奨_; を使用して`SQL_COPT_SS_AUTHENTICATION`'éý'`SQL_AU_AD_INTEGRATED`代わりにします。 <br><br>強制的に実行は、Windows 認証 (Kerberos Linux や macOS 上) のサーバーのログインでアクセスの検証を使用します。 ドライバーがの一部として提供されるユーザー id とパスワードの値を無視する Windows 認証を使用すると、 `SQLConnect`、 `SQLDriverConnect`、または`SQLBrowseConnect`を処理します。|

## <a name="ui-additions-for-azure-active-directory-windows-driver-only"></a>Azure Active Directory (Windows ドライバー) の UI の変更点

DSN のセットアップとドライバーの接続の Ui は、Azure AD で認証を使用するために必要な追加のオプションが強化されています。

### <a name="creating-and-editing-dsns-in-the-ui"></a>作成と UI の Dsn の編集

作成するときに、認証オプションを使用して、新しい Azure AD またはドライバーのセットアップ UI を使用して既存の DSN を編集することは。

`Authentication=ActiveDirectoryIntegrated` SQL Azure に Azure Active Directory 統合認証

![CreateNewDSN_ADIntegrated.png](windows/CreateNewDSN_ADIntegrated.png)

`Authentication=ActiveDirectoryPassword` SQL Azure に Azure Active Directory ユーザー名/パスワード認証

![CreateNewDSN_ADPassword.png](windows/CreateNewDSN_ADPassword.png)

`Authentication=ActiveDirectoryInteractive` SQL Azure に Azure Active Directory 対話型の認証

![CreateNewDSN_ADInteractive.png](windows/CreateNewDSN_ADInteractive.png)

`Authentication=SqlPassword` SQL Server へのユーザー名/パスワード認証 (Azure またはそれ以外の場合)

![CreateNewDSN_SQLServer.png](windows/CreateNewDSN_SQLServer.png)

`Trusted_Connection=Yes` Windows のレガシ SSPI 統合認証

![CreateNewDSN_winSSPI.png](windows/CreateNewDSN_winSSPI.png)

5 つのオプションに対応`Trusted_Connection=Yes`(既存レガシ Windows SSPI 専用の統合認証) と`Authentication=` `ActiveDirectoryIntegrated`、 `SqlPassword`、 `ActiveDirectoryPassword`、および`ActiveDirectoryInteractive`、それぞれします。

### <a name="sqldriverconnect-prompt-windows-driver-only"></a>SQLDriverConnect プロンプト (Windows ドライバー)

SQLDriverConnect によって、接続を完了に必要な情報を要求するときに表示されるプロンプト ダイアログには、Azure AD の認証用の 3 つの新しいオプションが含まれています。

![ServerLogin.png](windows/ServerLogin.png)

これらのオプションは、DSN セットアップ UI 上で同じ 5 つ以内に対応します。

### <a name="example-connection-strings"></a>接続文字列の例
1. SQL Server 認証 – レガシ構文です。 サーバー証明書が検証されていないと、サーバーは、実施する場合にのみ暗号化を使用します。 ユーザー名とパスワードは、接続文字列で渡されます。
`server=Server;database=Database;UID=UserName;PWD=Password;`
2. SQL 認証 – 新しい構文です。 クライアントが暗号化を要求 (既定値の`Encrypt`は`true`) し、サーバー証明書は、暗号化の設定に関係なく、検証を取得します。 (しない限り、`TrustServerCertificate`に設定されている`true`)。 ユーザー名とパスワードは、接続文字列で渡されます。
 `server=Server;database=Database;UID=UserName;PWD=Password;Authentication=SqlPassword;`
3. 統合 Windows 認証 (Kerberos で Linux および macOS) (SQL Server または SQL IaaS) – する SSPI を現在の構文を使用します。 暗号化を使用しない場合、サーバー証明書は検証されません。 
`server=Server;database=Database;Trusted_Connection=yes;`
4. (_Windows ドライバーのみ_)。統合 Windows 認証 (ターゲット データベースが SQL Server または SQL IaaS) の場合は、SSPI – 新しい構文を使用します。 クライアントが暗号化を要求 (既定値の`Encrypt`は`true`) し、サーバー証明書は、暗号化の設定に関係なく、検証を取得します。 (しない限り、`TrustServerCertificate`に設定されている`true`)。 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
5. AAD のユーザー名/パスワード認証 (ターゲット データベースが Azure SQL DB の場合)。 暗号化の設定に関係なく、サーバー証明書が検証を取得 (しない限り、`TrustServerCertificate`に設定されている`true`)。 ユーザー名とパスワードは、接続文字列で渡されます。 
`server=Server;database=Database;UID=UserName;PWD=Password;Authentication=ActiveDirectoryPassword;`
6. (_Windows ドライバーのみ_)。統合 Windows 認証が ADAL を使用して、AAD で発行されたアクセス トークンの Windows アカウントの資格情報の保証を含む、ターゲット データベースが Azure SQL データベースではあるとします。 暗号化の設定に関係なく、サーバー証明書が検証を取得 (しない限り、`TrustServerCertificate`に設定されている`true`)。 
`server=Server;database=Database;Authentication=ActiveDirectoryIntegrated;`
7. (_Windows ドライバーのみ_)。AAD 対話型の認証は、接続を設定する Azure multi-factor Authentication の技術を使用します。 ログイン ID を指定して、このモードで Windows Azure 認証ダイアログがトリガーされ、接続を完了するためのパスワードを入力することができます。 ユーザー名は、接続文字列で渡されます。
`server=Server;database=Database;UID=UserName;Authentication=ActiveDirectoryInteractive;`

![WindowsAzureAuth.png](windows/WindowsAzureAuth.png)

> [!NOTE] 
>- Windows ODBC ドライバーでは、新しい Active Directory オプションを使用して、ときにいることを確認、 [for SQL Server の Active Directory 認証ライブラリ](http://go.microsoft.com/fwlink/?LinkID=513072)がインストールされています。 Linux および macOS ドライバーでは、Azure Active Directory で認証するため追加の依存関係は必要ありません。
>- SQL Server アカウントのユーザー名とパスワードを使用して接続するに使用できるように、新しい`SqlPassword`オプションは、このオプションによりより安全な接続の既定値から場合に、特に SQL Azure の使用することをお勧めします。
>- Azure Active Directory アカウントのユーザー名とパスワードを使用して接続するには、指定`Authentication=ActiveDirectoryPassword`接続文字列で、`UID`と`PWD`キーワードで、ユーザー名とパスワードをそれぞれします。
>- Windows 統合認証または Active Directory 統合 (Windows ドライバー) 認証を使用して接続するには、指定`Authentication=ActiveDirectoryIntegrated`接続文字列にします。 ドライバーは、適切な認証モードを自動的に選択されます。 `UID` および`PWD`を指定できません。
>- Active Directory 対話型 (Windows ドライバー) の認証を使用して接続する`UID`指定する必要があります。

## <a name="authenticating-with-an-access-token"></a>アクセス トークンを使用した認証

`SQL_COPT_SS_ACCESS_TOKEN`接続前の属性がなく、ユーザー名とパスワード、認証用に Azure AD から取得したアクセス トークンの使用を許可しもネゴシエーションと、ドライバーによってアクセス トークンの取得をバイパスします。 アクセス トークンを使用する設定、`SQL_COPT_SS_ACCESS_TOKEN`へのポインターへの接続属性、`ACCESSTOKEN`構造体。

~~~
typedef struct AccessToken
{
    DWORD dataSize;
    BYTE data[];
} ACCESSTOKEN;
~~~

`ACCESSTOKEN` 4 バイトで構成される可変長構造体は、_長さ_続く_長さ_アクセス トークンを形成する非透過的なデータのバイト数。 経由で 1 つ取得したか SQL Server は、アクセス トークンを処理するため、 [OAuth 2.0](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-authentication-scenarios) JSON 応答は、各バイトのパディング バイト、ASCII 文字のみを含む ucs-2 文字列のような 0 が続くように展開する必要がありますただし、トークンが。非透過の値とバイト単位で指定された長さは、null 終端記号を含めないでください。 制約のため、非常に長い長さと形式、認証には、このメソッドはを介してプログラムで使用できるのみ、 `SQL_COPT_SS_ACCESS_TOKEN` coonnection 属性である対応する DSN または接続文字列キーワードがありません。 接続文字列を含めないでください`UID`、 `PWD`、 `Authentication`、または`Trusted_Connection`キーワード。

> [!NOTE]
> ODBC Driver 13.1 のバージョンのみをサポートしているこの認証で_Windows_です。

## <a name="azure-active-directory-authentication-sample-code"></a>Azure Active Directory 認証のサンプル コード

次の例では、接続キーワードと Azure Active Directory を使用して SQL Server への接続に必要なコードを示します。 自体は、アプリケーション コードを変更する必要がないことに注意してください。接続文字列、または DSN を使用する場合は、AAD 認証を使用するために必要な唯一の変更を示します。
~~~
    ...
    SQLCHAR connString[] = "Driver={ODBC Driver 13 for SQL Server};Server={server};UID=myuser;PWD=myPass;Authentication=ActiveDirectoryPassword"
    ...
    SQLDriverConnect(hDbc, NULL, connString, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    ...
~~~
次の例では、アクセス トークンの認証で Azure Active Directory を使用して SQL Server への接続に必要なコードを示します。 この場合、アクセス トークンを処理し、関連付けられている接続属性を設定するアプリケーション コードを変更する必要はします。
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
Azure Active Directory の対話型認証で使用する接続文字列の例を次に示します。 ない PWD フィールドように Windows Azure Authentication 画面を使用して、パスワードを入力するよう注意してください。
~~~
SQLCHAR connString[] = "Driver={ODBC Driver 17 for SQL Server};Server={server};UID=myuser;Authentication=ActiveDirectoryInteractive"
~~~

## <a name="see-also"></a>参照
[Azure AD 認証を使用して Azure SQL DB のトークン ベースの認証のサポート](https://blogs.msdn.microsoft.com/sqlsecurity/2016/02/09/token-based-authentication-support-for-azure-sql-db-using-azure-ad-auth)

