---
title: Azure Active Directory 認証を使用して接続する |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2018
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.technology:
- drivers
ms.topic: article
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: ef69bb70de8af6b6dc56df66e652f7f4dae7529c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="connecting-using-azure-active-directory-authentication"></a>Azure Active Directory 認証を使用して接続します。

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

この記事では、SQL Server 用 Microsoft JDBC Driver 6.0 (またはそれ以上) は、Azure Active Directory の認証の機能を使用する Java アプリケーションを開発する方法について説明します。

Azure Active Directory (AAD) の認証は、Azure SQL Database v12 への接続機構を使用する Azure Active Directory で id を使用します。 SQL Server 認証の代わりとしてのデータベース ユーザーの id を一元的に管理するのにには、Azure Active Directory 認証を使用します。 JDBC ドライバーでは、Azure SQL DB に接続する JDBC 接続文字列で、Azure Active Directory の資格情報を指定することができます。 Azure Active Directory 認証を構成する方法については、次を参照してください。[認証して SQL Database を使用して Azure Active Directory に接続する](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)です。 

Azure Active Directory 認証をサポートするために、2 つの新しい接続プロパティが追加されました。
*   **認証**: このプロパティを使用して、接続に使用する SQL 認証方法を指定します。 指定できる値は: **ActiveDirectoryIntegrated**、 **ActiveDirectoryPassword**、 **SqlPassword**と既定**NotSpecified**.
    * 使用して ' 認証 ActiveDirectoryIntegrated を =' 統合 Windows 認証を使用して SQL データベースに接続します。 この認証モードを使用するには、内部設置型 Active Directory フェデレーション サービス (ADFS) を Azure AD とクラウド内のフェデレーションを実行する必要があります。 これが設定されたら、Kerberos チケットだけでなく、ドメインに参加しているコンピューターにログインしているときに資格情報の入力を求められず Azure SQL DB にアクセスできます。 
    * 使用して ' 認証 ActiveDirectoryPassword を =' Azure AD のプリンシパル名とパスワードを使用して SQL データベースに接続します。
    * 使用して ' 認証 SqlPassword を =' ユーザー名/ユーザー名とパスワードのプロパティを使用して SQL Server に接続します。
    * 使用して ' 認証 NotSpecified を =' のままに既定値としてこれらのどの認証方法が必要な場合またはします。

*   **accessToken**: このプロパティを使用してアクセス トークンを使用して SQL データベースに接続します。 accessToken は、パラメーターを使用して、プロパティ、getConnection() メソッドの DriverManager クラスでのみ設定できます。 接続 URL で使用することはできません。  

詳細情報の認証プロパティを参照してください、[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)ページ。  


## <a name="client-setup-requirements"></a>クライアントのセットアップ要件
次のコンポーネントが、クライアント コンピューターにインストールされていることを確認してください。
* Java 7 以上
*   Microsoft JDBC Driver 6.0 (またはそれ以降) for SQL Server
*   アクセス トークン ベースの認証モードを使用している場合は済みます[azure active directory-ライブラリ-用の java](https://github.com/AzureAD/azure-activedirectory-library-for-java)とその依存関係からを実行する例では、この記事の内容。 詳細については、次を参照してください。**アクセス トークンを使用した接続**セクションです。
*   ActiveDirectoryPassword 認証モードを使用している場合は済みます[azure active directory-ライブラリ-用の java](https://github.com/AzureAD/azure-activedirectory-library-for-java)とその依存関係。 詳細については、次を参照してください。 **ActiveDirectoryPassword 認証モードを使用して接続する**セクションです。
*   ActiveDirectoryIntegrated モードを使用している場合は、azure active directory-ライブラリ-用の java とその依存関係を必要です。 詳細については、次を参照してください。 **ActiveDirectoryIntegrated 認証モードを使用して接続する**セクションです。
    
## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>ActiveDirectoryIntegrated 認証モードを使用して接続します。
 バージョン 6.4 では、Microsoft JDBC Driver は、複数のプラットフォーム (Windows または Linux、Mac) で Kerberos チケットを使用して ActiveDirectoryIntegrated 認証のサポートを追加します。
参照してください[Windows、Linux、Mac 上の設定の Kerberos チケット](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac)詳細についてはします。 また、Windows では、sqljdbc_auth.dll こともできます JDBC ドライバーで ActiveDirectoryIntegrated 認証します。

> [!NOTE]
>  古いバージョンのドライバーを使用している場合はこれをチェック[リンク](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)この認証モードを使用するために必要なそれぞれの依存関係。 

次の例は、使用する方法を示しています。 ' authentication = ActiveDirectoryIntegrated' モードです。 Azure Active Directory とフェデレーションすると、ドメインに参加しているマシンでは、この例を実行します。 Azure AD のプリンシパル、またはグループのいずれかを表す包含データベース ユーザーに属している、データベース内に存在する必要がありますして CONNECT 権限を持つ必要があります。 

ビルドとクライアント コンピューター上の例を実行する前に (を例を実行する)、ダウンロード、 [azure active directory-ライブラリ-用の java ライブラリ](https://github.com/AzureAD/azure-activedirectory-library-for-java)とその依存関係 Java ビルド パスに含めます

サーバー/データベース名を例を実行する前に次の行で、サーバー/データベース名に置き換えます。

```
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
```

この例では、ActiveDirectoryIntegrated 認証モードを使用します。
```
import java.sql.Connection;
import java.sql.ResultSet;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class IntegratedExample {

    public static void main(String[] args) throws Exception {
        SQLServerDataSource ds = new SQLServerDataSource();

        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database name
        ds.setAuthentication("ActiveDirectoryIntegrated");
        ds.setHostNameInCertificate("*.database.windows.net");

        Connection connection = ds.getConnection();

        ResultSet rs = connection.createStatement().executeQuery("SELECT SUSER_SNAME()");
        if(rs.next()){
            System.out.println("You have successfully logged on as: " + rs.getString(1));
        }
    }
}
```
Kerberos チケットを使用して自動的にクライアント コンピューターでこの例を実行して、パスワードは必要ありません。 接続が確立されると、次のメッセージが表示されます。
```
You have successfully logged on as: <your domain user name>
```

### <a name="set-kerberos-ticket-on-windows-linux-and-mac"></a>Windows、Linux、Mac 上の Kerberos チケットを設定します。

Kerberos チケットが、現在のユーザーを Windows ドメイン アカウントにリンクを設定する必要があります。 主要な手順の概要は、以下に示します。

#### <a name="windows"></a>Windows
JDK が付属して`kinit`が Azure Active Directory と統合されているマシンを参加を KDC (キー配布センター) からドメインに、TGT を取得することができます。

##### <a name="step-1-ticket-granting-ticket-retrieval"></a>手順 1: チケット保証チケットの取得
- **上で実行**: Windows
- **アクション**:
  - コマンドを使用して`kinit username@DOMAIN.COMPANY.COM`KDC から TGT を取得し、ように求められますドメイン パスワードです。
  - 使用して`klist`に利用可能なチケットを参照してください。 Kinit、成功した場合、krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM からチケットが表示されます。

> [!NOTE]
>  指定する必要があります、`.ini`ファイルと`-Djava.security.krb5.conf`KDC を検索するアプリケーション。

#### <a name="linux-and-mac"></a>Linux と Mac

##### <a name="requirements"></a>必要条件
Kerberos ドメイン コント ローラーを照会するのには Windows ドメインに参加しているコンピューターへのアクセス

##### <a name="step-1-find-kerberos-kdc"></a>手順 1: Kerberos KDC を検索します。
- **上で実行**: Windows コマンドライン
- **アクション**: `nltest /dsgetdc:DOMAIN.COMPANY.COM` (ここで"DOMAIN.COMPANY.COM"にマップするようにドメインの名前)
- **サンプル出力**
  ```
  DC: \\co1-red-dc-33.domain.company.com
  Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
  ...
  The command completed successfully
  ```
- **情報を抽出する**DC 名ここでは、 `co1-red-dc-33.domain.company.com`

##### <a name="step-2-configuring-kdc-in-krb5conf"></a>手順 2: krb5.conf の KDC を構成します。
- **上で実行**: Linux または Mac
- **アクション**: 任意のエディターで/etc/krb5.conf を編集します。 次のキーを構成します。
  ```
  [libdefaults]
    default_realm = DOMAIN.COMPANY.COM
   
  [realms]
  DOMAIN.COMPANY.COM = {
     kdc = co1-red-dc-28.domain.company.com
  }
  ```
  Krb5.conf ファイルと終了を保存し、

> [!NOTE]
>  ドメインは、すべて大文字でなければなりません。

##### <a name="step-3-testing-the-ticket-granting-ticket-retrieval"></a>手順 3: テストのチケット保証チケットの取得
- **上で実行**: Linux または Mac
- **アクション**:
  - コマンドを使用して`kinit username@DOMAIN.COMPANY.COM`KDC から TGT を取得し、ように求められますドメイン パスワードです。
  - 使用して`klist`に利用可能なチケットを参照してください。 Kinit、成功した場合、krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM からチケットが表示されます。

## <a name="connecting-using-activedirectorypassword-authentication-mode"></a>ActiveDirectoryPassword 認証モードを使用して接続します。
次の例は、使用する方法を示しています。 ' authentication = ActiveDirectoryPassword' モードです。

構築し、例を実行する: 前に
1.  クライアント コンピューターで、(を例を実行する)、ダウンロード、 [azure active directory-ライブラリ-用の java ライブラリ](https://github.com/AzureAD/azure-activedirectory-library-for-java)とその依存関係、Java ビルド パスに含めます
2.  次のコード行を検索し、サーバー/データベース名をサーバー/データベース名に置き換えます。
    ```
    ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
    ds.setDatabaseName("demo"); // replace with your database name
    ```
3.  次のコード行を検索し、ユーザー名として接続する Azure AD ユーザーの名前に置き換えます。
    ```
    ds.setUser("bob@cqclinic.onmicrosoft.com"); // replace with your user name
    ds.setPassword("password");     // replace with your password
    ```

この例では、ActiveDirectoryPassword 認証モードを使用します。
```
import java.sql.Connection;
import java.sql.ResultSet;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class UserPasswordExample {
    
    public static void main(String[] args) throws Exception{
        SQLServerDataSource ds = new SQLServerDataSource();
        
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database
        ds.setUser("bob@cqclinic.onmicrosoft.com"); // Replace with your user name
        ds.setPassword("password"); // Replace with your password
        ds.setAuthentication("ActiveDirectoryPassword");
        ds.setHostNameInCertificate("*.database.windows.net");
        
        Connection connection = ds.getConnection();
        
        ResultSet rs = connection.createStatement().executeQuery("SELECT SUSER_SNAME()");
        if(rs.next()){
            System.out.println("You have successfully logged on as: " + rs.getString(1));
        }
    }
}
```
接続が確立された場合、出力として、次のメッセージが表示されます。
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> 包含ユーザー データベースが存在する必要がありますと包含データベース ユーザーを表す、指定した Azure AD のユーザーまたはグループを指定された Azure のいずれかの AD ユーザーに属している、データベース内に存在する必要があります、(Azure Active Directory を除く、CONNECT 権限が必要サーバー管理者またはグループ)


## <a name="connecting-using-access-token"></a>アクセス トークンを使用した接続
アプリケーション/サービスでは、Azure Active Directory からアクセス トークンを取得でき、SQL Azure データベースへの接続に使用することができます。 DriverManager クラスで、プロパティ、メソッドのパラメーター getConnection() を使用してその accessToken を設定することができますのみに注意してください。 これは、接続文字列で使用できません。
 
次の例には、アクセス トークン ベース認証を使用して Azure SQL データベースに接続する簡単な Java アプリケーションが含まれています。 構築と、例を実行する、前に、次の手順を実行します。
1.  Azure Active Directory で、サービスのアプリケーション アカウントを作成します。
    1. Azure 管理ポータルにサインインするには
    2. Azure Active Directory での左側にあるナビゲーション ウィンドウでをクリックします。
    3. 「アプリの登録」タブをクリックします。
    4. ドロアーには、「新しいアプリケーションの登録」をクリックします。
    5. アプリケーションのフレンドリ名として mytokentest を入力して、"Web アプリ/API"を選択します。
    6. サインオン URL は不要です。 だけのものを指定して:"http://mytokentest"です。
    7. 下部にある [作成] をクリックします。
    9. Azure ポータルで、アプリケーションの [設定] タブをクリックし、[プロパティ] タブを開きます。
    10. "アプリケーション ID"(別名クライアント ID) の値を検索し、コピー別に、この後で場合に必要 (たとえば、1846943b-ad04-4808-aa13-4702d908b5c1) アプリケーションを構成します。 次のスナップショットを参照してください。
    11. "アプリ ID URL"の値を検索し、コピー別に、これは、STS の URL。
    12. [「キー」] セクションでは、[名前] フィールドに情報を入力、キーの期間を選択し、(値フィールドを空のままにして) の構成を保存して、キーを作成します。 値フィールドにする必要があります、保存した後に生成された値をコピーする、自動的に入力します。 これは、クライアント シークレットです。

    ![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)  
2. Azure Active Directory 管理者と、アプリケーションのプリンシパルの T-SQL コマンド プロビジョニング、包含データベース ユーザーを使用して Azure SQL Server のユーザー データベースにログオンします。 参照してください、 [SQL データベースまたは SQL データ ウェアハウス認証を使用して Azure Active Directory に接続する](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)を Azure Active Directory 管理者と包含データベース ユーザーを作成する方法の詳細についてはします。

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  クライアント コンピューターで、(を例を実行する)、ダウンロード、 [azure active directory-ライブラリ-用の java](https://github.com/AzureAD/azure-activedirectory-library-for-java)ライブラリとその依存関係 Java ビルド パスに含めます。 このライブラリから Azure AD からアクセス トークンを取得する Api を使用するように、この特定の例を実行する、azure active directory-ライブラリ-用の java が必要なだけことに注意してください。 アクセス トークンがある場合は、この手順を省略できます。 アクセス トークンの取得の例では、セクションを削除する必要がありますに注意してください。

次の例では、実際の値に、STS の URL、クライアント ID、クライアント シークレット、サーバーとデータベース名を置き換えます。

```
import java.sql.Connection;
import java.sql.ResultSet;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

// The azure-activedirectory-library-for-java is needed to retrieve the access token from the AD. 
import com.microsoft.aad.adal4j.AuthenticationContext;
import com.microsoft.aad.adal4j.AuthenticationResult;
import com.microsoft.aad.adal4j.ClientCredential;


public class TokenBasedExample {

    public static void main(String[] args) throws Exception{

        // Retrieve the access token from the AD.
        String spn = "https://database.windows.net/";
        String stsurl = "https://microsoft.onmicrosoft.com/..."; // Replace with your STS URL.
        String clientId = "1846943b-ad04-4808-aa13-4702d908b5c1"; // Replace with your client ID.
        String clientSecret = "..."; // Replace with your client secret.

        AuthenticationContext context = new AuthenticationContext(stsurl, false, Executors.newFixedThreadPool(1));
        ClientCredential cred = new ClientCredential(clientId, clientSecret);

        Future<AuthenticationResult> future = context.acquireToken(spn, cred, null);
        String accessToken = future.get().getAccessToken();

        System.out.println("Access Token: " + accessToken);     
        
        // Connect with the access token.
        SQLServerDataSource ds = new SQLServerDataSource();

        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name.
        ds.setDatabaseName("demo"); // Replace with your database name.
        ds.setAccessToken(accessToken);
        ds.setHostNameInCertificate("*.database.windows.net");

        Connection connection = ds.getConnection();

        ResultSet rs = connection.createStatement().executeQuery("SELECT SUSER_SNAME()");
        if(rs.next()){
            System.out.println("You have successfully logged on as: " + rs.getString(1));
        }
    }
}
``` 

接続が成功した場合、出力として、次のメッセージが表示されます。
```
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 
