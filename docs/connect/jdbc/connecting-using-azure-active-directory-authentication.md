---
title: Azure Active Directory 認証を利用した接続 | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8f699c97aee04bfe2c6f29789be6f34b673408e7
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2018
ms.locfileid: "52401155"
---
# <a name="connecting-using-azure-active-directory-authentication"></a>Azure Active Directory 認証を利用した接続

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

この記事では、SQL Server 用 Microsoft JDBC Driver 6.0 (またはそれ以上) は、Azure Active Directory 認証の機能を使用する Java アプリケーションを開発する方法について説明します。

Azure SQL Database v12 に接続するメカニズムである Azure Active Directory (AAD) 認証を使用する Azure Active Directory id を使用します。 Azure Active Directory 認証は、データベース ユーザーの ID を一元管理するという目的で使用でき、SQL Server 認証に代わる方法となります。 JDBC ドライバーでは、Azure SQL DB への接続に JDBC 接続文字列で、Azure Active Directory の資格情報を指定できます。 Azure Active Directory 認証を構成する方法については、次を参照してください。 [SQL データベースを Azure Active Directory 認証を使用する接続](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)します。 

Azure Active Directory 認証をサポートするために、2 つの新しい接続プロパティが追加されました。
*   **認証**: このプロパティを使用して、接続に使用する SQL 認証方法を指定します。 指定できる値は: **ActiveDirectoryIntegrated**、 **ActiveDirectoryPassword**、 **SqlPassword**と既定**NotSpecified**.
    * 'authentication=ActiveDirectoryIntegrated' を使用して、統合 Windows 認証を使用している SQL Database に接続します。 この認証モードを使用するには、オンプレミス Active Directory フェデレーション サービス (ADFS)、クラウドでの AAD でのフェデレーションを実行する必要があります。 これは、Kerberos チケットを取得および設定は後、は、ドメイン参加済みコンピューターにログインしているときに資格情報を表示せず Azure SQL DB を利用できます。 
    * 'authentication=ActiveDirectoryPassword' を使用して、Azure AD のプリンシパル名とパスワードを使用している SQL Database に接続します。
    * 使用して ' authentication = SqlPassword'/ユーザー名とパスワードのプロパティを使用して SQL Server に接続します。
    * 使用して '認証 = notspecified です' またはその既定値のまま上記のどの認証方法が必要な場合。

*   **accessToken**: このプロパティを使用してアクセス トークンを使用して SQL database に接続します。 accessToken は、ドライバー マネージャー クラスで getConnection() メソッドのプロパティのパラメーターを使用してのみ設定できます。 これは、接続 URL で使用できません。  

詳細についてでの認証プロパティを参照してください、[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)ページ。  


## <a name="client-setup-requirements"></a>クライアントのセットアップ要件
クライアント コンピューターで、次のコンポーネントがインストールされていることを確認してください。
* Java 7 以降
*   Microsoft JDBC Driver 6.0 (またはそれ以降) for SQL Server
*   必要な場合は、アクセス トークン ベースの認証モードを使用している[azure active directory-ライブラリ-の-java](https://github.com/AzureAD/azure-activedirectory-library-for-java)とその依存関係、この記事からの例を実行します。 詳細については、次を参照してください。**アクセス トークンを使用して接続**セクション。
*   ActiveDirectoryPassword 認証モードを使用している必要[azure active directory-ライブラリ-の-java](https://github.com/AzureAD/azure-activedirectory-library-for-java)とその依存関係。 詳細については、次を参照してください。 **ActiveDirectoryPassword 認証モードを使用して接続**セクション。
*   ActiveDirectoryIntegrated モードを使用している場合、有効な azure active directory-ライブラリ-の-java とその依存関係する必要があります。 詳細については、次を参照してください。 **ActiveDirectoryIntegrated 認証モードを使用して接続**セクション。
    
## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>ActiveDirectoryIntegrated 認証モードを使用して接続します。
 バージョン 6.4 では、Microsoft JDBC Driver は、Kerberos チケットを使用して、複数のプラットフォーム (Windows または Linux と Mac) で ActiveDirectoryIntegrated 認証のサポートを追加します。
詳細については、次を参照してください。 [Windows、Linux と Mac での設定の Kerberos チケット](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac)の詳細。 または、Windows で sqljdbc_auth.dll こともできます JDBC ドライバーで ActiveDirectoryIntegrated 認証。

> [!NOTE]
>  以前のバージョンのドライバーを使用している場合はこれをチェック[リンク](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)この認証モードを使用するために必要なそれぞれの依存関係。 

次の例を使用する方法を示しています。 ' authentication = ActiveDirectoryIntegrated' モード。 Azure Active Directory とフェデレーションされているドメイン参加しているコンピューターには、この例を実行します。 Azure AD プリンシパルまたはグループのいずれかを表す包含データベース ユーザーにするに属している、データベース内に存在する必要があります、CONNECT 権限が必要です。 

ビルドとクライアント コンピューター上の例を実行する前に (を例を実行する)、ダウンロード、 [azure active directory-ライブラリ-用の java ライブラリ](https://github.com/AzureAD/azure-activedirectory-library-for-java)とその依存関係を Java ビルド パスに含めます

サーバー/データベース名を例を実行する前に、次の行で、サーバー/データベース名に置き換えます。

```java
ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
ds.setDatabaseName("demo"); // replace with your database name
```

ActiveDirectoryIntegrated 認証モードを使用する例を示します。
```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AADIntegrated {
    public static void main(String[] args) throws Exception {

        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database name
        ds.setAuthentication("ActiveDirectoryIntegrated");
        ds.setHostNameInCertificate("*.database.windows.net");

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();) {
            
            ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()");
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```
Kerberos チケットを使用して自動的にクライアント コンピューターでこの例を実行していると、パスワードは必要ありません。 接続が確立されている場合は、次のメッセージが表示されます。
```
You have successfully logged on as: <your domain user name>
```

### <a name="set-kerberos-ticket-on-windows-linux-and-mac"></a>Windows、Linux と Mac での Kerberos チケットを設定します。

Kerberos チケットが、現在のユーザーを Windows ドメイン アカウントにリンクを設定する必要があります。 主要な手順の概要は、以下に示します。

#### <a name="windows"></a>Windows
JDK が付属して`kinit`、Azure Active Directory とフェデレーションされているマシンを参加させるドメイン TGT をキー配布センター (KDC) から取得するために使用できます。

##### <a name="step-1-ticket-granting-ticket-retrieval"></a>手順 1: チケット保証チケットの取得
- **上で実行**: Windows
- **アクション**:
  - コマンドを使用して`kinit username@DOMAIN.COMPANY.COM`を KDC から TGT を取得し、ように求められます。 ドメイン パスワード。
  - 使用`klist`に利用可能なチケットを参照してください。 Kinit に成功した場合は、krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM からチケットが表示されます。

> [!NOTE]
>  指定する必要があります、`.ini`ファイルと`-Djava.security.krb5.conf`KDC を検索するアプリケーション。

#### <a name="linux-and-mac"></a>Linux と Mac

##### <a name="requirements"></a>必要条件
Kerberos ドメイン コント ローラーのクエリを実行する Windows ドメインに参加しているコンピューターへのアクセス。

##### <a name="step-1-find-kerberos-kdc"></a>手順 1: Kerberos KDC を検索します。
- **上で実行**: Windows コマンドライン
- **アクション**: `nltest /dsgetdc:DOMAIN.COMPANY.COM` ("DOMAIN.COMPANY.COM"は、ドメインの名前にマップ)
- **サンプル出力**
  ```
  DC: \\co1-red-dc-33.domain.company.com
  Address: \\2111:4444:2111:33:1111:ecff:ffff:3333
  ...
  The command completed successfully
  ```
- **情報を抽出する**DC 名、ここで `co1-red-dc-33.domain.company.com`

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
>  ドメインは、すべて大文字である必要があります。

##### <a name="step-3-testing-the-ticket-granting-ticket-retrieval"></a>手順 3: テストのチケット保証チケットの取得
- **上で実行**: Linux または Mac
- **アクション**:
  - コマンドを使用して`kinit username@DOMAIN.COMPANY.COM`を KDC から TGT を取得し、ように求められます。 ドメイン パスワード。
  - 使用`klist`に利用可能なチケットを参照してください。 Kinit に成功した場合は、krbtgt/DOMAIN.COMPANY.COM@ DOMAIN.COMPANY.COM からチケットが表示されます。

## <a name="connecting-using-activedirectorypassword-authentication-mode"></a>ActiveDirectoryPassword 認証モードを使用して接続します。
次の例を使用する方法を示しています。 ' authentication = ActiveDirectoryPassword' モード。

前のビルドと実行の例。
1.  クライアント コンピューターで (を例を実行する)、ダウンロード、 [azure active directory-ライブラリ-用の java ライブラリ](https://github.com/AzureAD/azure-activedirectory-library-for-java)とその依存関係を Java ビルド パスに含めます
2.  次のコード行を検索し、サーバー/データベース名をサーバー/データベース名に置き換えます。
    ```java
    ds.setServerName("aad-managed-demo.database.windows.net"); // replace 'aad-managed-demo' with your server name
    ds.setDatabaseName("demo"); // replace with your database name
    ```
3.  次のコード行を検索し、ユーザーの名として接続する、AAD ユーザーの名前に置き換えます。
    ```java
    ds.setUser("bob@cqclinic.onmicrosoft.com"); // replace with your user name
    ds.setPassword("password");     // replace with your password
    ```

ActiveDirectoryPassword 認証モードを使用する例を示します。
```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;

import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

public class AADUserPassword {
    
    public static void main(String[] args) throws Exception{
        
        SQLServerDataSource ds = new SQLServerDataSource();
        ds.setServerName("aad-managed-demo.database.windows.net"); // Replace with your server name
        ds.setDatabaseName("demo"); // Replace with your database
        ds.setUser("bob@cqclinic.onmicrosoft.com"); // Replace with your user name
        ds.setPassword("password"); // Replace with your password
        ds.setAuthentication("ActiveDirectoryPassword");
        ds.setHostNameInCertificate("*.database.windows.net");
        
        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();) {
            
            ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()");
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
```
接続が確立されている場合、次のメッセージを出力として表示されます。
```
You have successfully logged on as: <your user name>
```

> [!NOTE]  
> 包含ユーザーのデータベースが存在する必要がありますと、包含データベース ユーザーを表す、指定した Azure AD ユーザーまたはグループを指定された Azure AD ユーザーに属している、データベース内に存在する必要があります、(を除く Azure Active Directory CONNECT アクセス許可が必要サーバー管理者またはグループ)

## <a name="connecting-using-access-token"></a>アクセス トークンを使用した接続
アプリケーション/サービスでは、Azure Active Directory からアクセス トークンを取得でき、SQL Azure データベースへの接続に使用することができます。

> [!NOTE] 
> **accessToken** DriverManager クラスで getConnection() メソッドのプロパティのパラメーターを使用してのみ設定できます。 これは、接続文字列で使用できません。

次の例には、アクセス トークン ベース認証を使用して Azure SQL Database に接続する単純な Java アプリケーションが含まれています。 ビルドと、例を実行する前に、次の手順に従います。
1.  Azure Active Directory で、サービスのアプリケーション アカウントを作成します。
    1. Azure portal にサインインします。
    2. 左側のナビゲーションで、Azure Active Directory をクリックします。
    3. [アプリの登録] タブをクリックします。
    4. ドロワーでは、"新しいアプリケーションの登録 をクリックします。
    5. [Web アプリ/API] を選択して、アプリケーションのフレンドリ名として mytokentest を入力します。
    6. サインオン URL は不要です。 何も指定します。 "https://mytokentest" 。
    7. 下部にある [作成] をクリックします。
    9. Azure portal で、アプリケーションの [設定] タブをクリックし、[プロパティ] タブを開きます。
    10. "アプリケーション ID"(クライアント ID とも呼ばれます) の値を見つけてコピーして、この後で必要 (たとえば、1846943b-ad04-4808-aa13-4702d908b5c1) アプリケーションを構成するときにします。 次のスナップショットを参照してください。
    11. [「キー」] セクションで、[名前] フィールドに入力し、キーの期間を選択して、構成 (値フィールドを空のままに) 保存キーを作成します。 保存後は、値フィールドにする必要があります、生成された値をコピーして、自動的に入力します。 これがクライアント シークレットです。
    12. 左側のパネルで、Azure Active Directory をクリックします。 [アプリの登録] の下には、「エンドポイント」タブを検索します。これは、STS の URL を「OATH 2.0 トークン エンドポイント」の下の URL をコピーします。
    
    ![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)  
2. Azure Active Directory 管理者と、アプリケーションのプリンシパルの T-SQL コマンドのプロビジョニングの包含データベース ユーザーを使用して Azure SQL Server のユーザー データベースにサインインします。 詳細については、次を参照してください。、[への SQL Database または SQL データ ウェアハウスを使用して Azure Active Directory 認証して](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)Azure Active Directory 管理者と包含データベース ユーザーを作成する方法の詳細についてはします。

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  クライアント コンピューターで (を例を実行する)、ダウンロード、 [azure active directory-ライブラリ-の-java](https://github.com/AzureAD/azure-activedirectory-library-for-java)ライブラリとその依存関係を Java ビルド パスに含めます。 この特定の例を実行する、azure active directory-ライブラリ-の-java がのみ必要なことに注意してください。 例では、このライブラリから Api を使用して Azure AAD からアクセス トークンを取得します。 アクセス トークンは、既にある場合は、この手順をスキップすることができます。 アクセス トークンの取得の例では、セクションを削除する必要があることに注意してください。

次の例では、STS の URL、クライアント ID、クライアント シークレット、サーバーおよびデータベースの名前に、値を置き換えます。

```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import com.microsoft.sqlserver.jdbc.SQLServerDataSource;

// The azure-activedirectory-library-for-java is needed to retrieve the access token from the AD.
import com.microsoft.aad.adal4j.AuthenticationContext;
import com.microsoft.aad.adal4j.AuthenticationResult;
import com.microsoft.aad.adal4j.ClientCredential;

public class AADTokenBased {

    public static void main(String[] args) throws Exception {

        // Retrieve the access token from the AD.
        String spn = "https://database.windows.net/";
        String stsurl = "https://login.microsoftonline.com/..."; // Replace with your STS URL.
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

        try (Connection connection = ds.getConnection(); 
                Statement stmt = connection.createStatement();) {

            ResultSet rs = stmt.executeQuery("SELECT SUSER_SNAME()");
            if (rs.next()) {
                System.out.println("You have successfully logged on as: " + rs.getString(1));
            }
        }
    }
}
``` 

接続が成功した場合、次のメッセージを出力として表示されます。
```java
Access Token: <your access token>
You have successfully logged on as: <your client ID>    
``` 
