---
title: "Azure Active Directory 認証を使用して接続する |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.topic: article
ms.assetid: 9c9d97be-de1d-412f-901d-5d9860c3df8c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 83d5ad3bae131b58dd344c3f5f9bfc7f5d0c4f5a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-using-azure-active-directory-authentication"></a>Azure Active Directory 認証を使用して接続します。
この記事では、SQL Server 用 Microsoft JDBC Driver 6.0 (またはそれ以上) は、Azure Active Directory の認証の機能を使用する Java アプリケーションを開発する方法について説明します。

Microsoft JDBC Driver 6.0 for SQL Server 以降、Azure SQL Database v12 への接続機構である Azure Active Direcoty (AAD) 認証を使用することが Azure Active Directory で id を使用します。 SQL Server 認証の代わりとしてのデータベース ユーザーの id を一元的に管理するのにには、Azure Active Directory 認証を使用します。 JDBC Driver 6.0 (以降) では、Azure SQL DB に接続する JDBC 接続文字列で、Azure Active Directory の資格情報を指定することができます。 Azure Active Directory 認証を構成する方法については、次を参照してください。[認証して SQL Database を使用して Azure Active Directory に接続する](https://azure.microsoft.com/documentation/articles/sql-database-aad-authentication/)です。 

Azure Active Directory 認証をサポートするために、2 つの新しい接続プロパティが追加されました。
*   **認証**: このプロパティを使用して、接続に使用する SQL 認証方法を指定します。 指定できる値は: **ActiveDirectoryIntegrated**、 **ActiveDirectoryPassword**、 **SqlPassword**と既定**NotSpecified**.
    * 使用して ' 認証 ActiveDirectoryIntegrated を =' 統合 Windows 認証を使用して SQL データベースに接続します。 この認証モードを使用するには、内部設置型 Active Directory フェデレーション サービス (ADFS) を Azure AD とクラウド内のフェデレーションを実行する必要があります。 セットアップは、いったん ceredentials ドメインに参加しているコンピューターにログインしているときに入力することがなく Azure SQL DB にアクセスできます。 
    * 使用して ' 認証 ActiveDirectoryPassword を =' Azure AD のプリンシパル名とパスワードを使用して SQL データベースに接続します。
    * 使用して ' 認証 SqlPassword を =' ユーザー名/ユーザー名とパスワードのプロパティを使用して SQL Server に接続します。
    * 使用して ' 認証 NotSpecified を =' のままに既定値としてこれらのどの認証方法が必要な場合またはします。

*   **accessToken**: このプロパティを使用してアクセス トークンを使用して SQL データベースに接続します。 accessToken は、パラメーターを使用して、プロパティ、getConnection() メソッドの DriverManager クラスでのみ設定できます。 接続 URL で使用することはできません。  

詳細情報の認証プロパティを参照してください、[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)ページ。  


## <a name="client-setup-requirements"></a>クライアントのセットアップ要件
次のコンポーネントが、クライアント コンピューターにインストールされていることを確認してください。
* Java 7 以上
*   6.2 (またはそれ以降) の Microsoft JDBC Driver for SQL Server
*   アクセス トークンに基づく認証モードを使用している場合は必要[azure active directory-ライブラリ-用の java](https://github.com/AzureAD/azure-activedirectory-library-for-java)とその依存関係からを実行する例では、この記事の内容。 参照してください**アクセス トークンを使用した接続**詳細についてはします。
*   ActiveDirectoryPassword 認証モードを使用している場合は必要[azure active directory-ライブラリ-用の java](https://github.com/AzureAD/azure-activedirectory-library-for-java)とその依存関係。 参照してください**ActiveDirectoryPassword 認証モードを使用して接続する**詳細についてはします。
*   ActiveDirectoryIntegrated モードを使用している場合は、for SQL Server (ADALSQL Active Directory 認証ライブラリをインストールする必要があります.DLL) および sqljdbc_auth.dll です。
    * ADALSQL です。DLL は、Azure Active Directory を使用して Microsoft Azure SQL データベースへの認証にアプリケーションを使用できます。 DLL をダウンロード[Microsoft SQL Server 用 Microsoft Active Directory 認証ライブラリ](http://www.microsoft.com/en-us/download/details.aspx?id=48742)
    * ADALSQL します。DLL 2 つバイナリ バージョン X86 および X64 をダウンロードします。 間違ったのバイナリのバージョンがインストールされているか、ドライバーで、次のエラーを発生させる、DLL が見つからない場合、:"adalsql.dll をロードできません (Authentication =...')。 エラー コード: 0x2。"です。 このような場合、ADALSQL の適切なバージョンをダウンロードします。DLL です。 
    * sqljdbc_auth.dll は、ドライバー パッケージで使用できます。 JDBC ドライバーがインストールされているコンピューター上の Windows システム パス上のディレクトリに sqljdbc_auth.dll ファイルをコピーします。 または、java.libary.path システム プロパティを設定して sqljdbc_auth.dll のディレクトリを指定することもできます。 
    * 64 ビットの JVM を x64 プロセッサ上で実行している場合は、x64 フォルダーの sqljdbc_auth.dll ファイルを使用してください。 
    * 32 ビットの Java 仮想マシン (JVM) を実行している場合は、オペレーティング システムのバージョンが x64 であっても、x86 フォルダーの sqljdbc_auth.dll ファイルを使用してください。 
    * たとえば、32 ビットの JVM を使用している既定のディレクトリに、JDBC ドライバーがインストールされている場合は、Java アプリケーションの起動時に次の仮想マシン (VM) 引数を使用して、DLL の場所を指定できます。  
        ```
        -Djava.library.path=C:\Microsoft JDBC Driver <version> for SQL Server\sqljdbc_<version>\enu\auth\x86
        ```
    
## <a name="connecting-using-activedirectoryintegrated-authentication-mode"></a>ActiveDirectoryIntegrated 認証モードを使用して接続します。
次の例は、使用する方法を示しています。 ' authentication = ActiveDirectoryIntegrated' モードです。 Azure Active Directory とフェデレーションすると、ドメインに参加しているマシンでは、この例を実行します。 Azure AD のプリンシパル、またはグループのいずれかを表す包含データベース ユーザーに属している、データベース内に存在する必要がありますして CONNECT 権限を持つ必要があります。 
    
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
Azure Active Directory とフェデレーションすると、ドメインに参加しているコンピューターでこの例を実行すると、Windows の資格情報が自動的に使用し、パスワードは必要ありません。 接続が確立されると、次のメッセージが表示されます。
```
You have successfully logged on as: <your domain user name>
```

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
> 包含ユーザー データベースが存在する必要がありますと包含データベース ユーザーを表す、指定した Azure AD のユーザーまたはグループを指定された Azure のいずれかの AD ユーザーに属しているデータベースに存在する必要があります、(Azure Active Directory を除く、CONNECT 権限が必要サーバー管理者またはグループ)


## <a name="connecting-using-access-token"></a>アクセス トークンを使用した接続
アプリケーション/サービスでは、Azure Active Directory からアクセス トークンを取得でき、SQL Azure データベースへの接続に使用することができます。 DriverManager クラスで、プロパティ、メソッドのパラメーター getConnection() を使用してその accessToken を設定することができますのみに注意してください。 これは、接続文字列で使用できません。
 
次の例には、アクセス トークンに基づく認証を使用して Azure SQL データベースに接続する簡単な Java アプリケーションが含まれています。 構築と、例を実行する、前に、次の手順を実行します。
1.  Azure Active Directory で、サービスのアプリケーション アカウントを作成します。
    1. Azure 管理ポータルにサインインするには
    2. Azure Active Directory での左側にあるナビゲーション ウィンドウでをクリックします。
    3. サンプル アプリケーションを登録したいディレクトリ テナントをクリックします。 これは、データベース (データベースをホストするサーバー) に関連付けられている同じディレクトリでなければなりません。
    4. [アプリケーション] タブをクリックします。
    5. ドロアーには、[追加] をクリックします。
    6. 「自分の所属組織で開発中のアプリケーションを追加する」をクリックします。
    7. アプリケーションのフレンドリ名として mytokentest を入力して、"Web Application and/or Web API"を選択し、[次へ] をクリックします。
    8. このアプリケーションは、デーモン/サービスと web アプリケーションではないと仮定すると、必要はありません、サインイン URL またはアプリ ID URI。 これら 2 つのフィールドを http://mytokentest」と入力します。
    9. Azure ポータルで、アプリケーションの構成 タブをクリックします。
    10. クライアント ID 値を検索し、コピー別に、必要になる後で (つまり、アプリケーションを構成するときに a4bbfe26-dbaa-4fec-8ef5-223d229f647d)。 以下のスクリーン ショットを参照してください。
    11. 「キー」セクションで、キーの期間を選択、構成を保存および後で使用できるキーをコピーします。 これは、クライアント シークレットです。
    12. 下部で、「エンドポイントの表示」をクリックし、後で使用できる「OAUTH 2.0 承認エンドポイント」の下の URL をコピーします。 これは、STS の URL です。


![JDBC_AAD_Token](../../connect/jdbc/media/jdbc_aad_token.png)


2. Azure Active Directory 管理者とアプリケーションのプリンシパルの T-SQL コマンド プロビジョニング、包含データベース ユーザーを使用して Azure SQL Server のユーザー データベースにログオンします。 参照してください、 [SQL データベースまたは SQL データ ウェアハウス認証を使用して Azure Active Directory に接続する](https://azure.microsoft.com/en-us/documentation/articles/sql-database-aad-authentication/)を Azure Active Directory 管理者と包含データベース ユーザーを作成する方法の詳細についてはします。

    ```
    CREATE USER [mytokentest] FROM EXTERNAL PROVIDER
    ```

3.  クライアント コンピューターで、(を例を実行する)、ダウンロード、 [azure active directory-ライブラリ-用の java](https://github.com/AzureAD/azure-activedirectory-library-for-java)ライブラリとその依存関係 Java ビルド パスに含めます。 このライブラリから Azure AD からアクセス トークンを取得する Api を使用するように、この特定の例を実行する、azure active directory-ライブラリ-用の java が必要なだけことに注意してください。 アクセス トークンがある場合は、この手順を省略できます。 アクセス トークンの取得の例では、セクションを削除する必要がありますを注意してください。

次の例では、STS の URL、クライアント ID、クライアント シークレット、サーバーおよびデータベース名、値を持つを置き換えます。

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
        String stsurl = "https://login.microsoftonline.com/..."; // Replace with your STS URL.
        String clientId = "a4bbfe26-dbaa-4fec-8ef5-223d229f647d"; // Replace with your client ID.
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

