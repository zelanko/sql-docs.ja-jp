---
title: Kerberos を使用して統合 SQL Server への接続に認証 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d9023c31e0d7b985e17991a080a7c9afc077ff6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Kerberos 統合認証による SQL Server への接続」を参照してください。
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  以降で[!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]、アプリケーションで使用できます、 **authenticationScheme**タイプ 4 Kerberos 統合認証を使用してデータベースに接続したいことを示すために、接続プロパティです。 参照してください[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)接続のプロパティについての詳細。 Kerberos の詳細については、次を参照してください。 [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkID=100758)です。  
  
 Java で統合認証を使用する場合**Krb5LoginModule**を使用して、モジュールを構成する[クラス Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html)です。  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] IBM Java Vm 用に、次のプロパティを設定します。  
  
-   **useDefaultCcache = true**  
  
-   **moduleBanner = false**  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]他のすべての Java Vm 用に、次のプロパティを設定します。  
  
-   **useTicketCache = true**  
  
-   **doNotPrompt = true**  
  
## <a name="remarks"></a>解説  
 前のバージョン[!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]、アプリケーションが統合認証 (Kerberos または NTLM を使用して、使用可能なに合わせて) を指定できますを使用して、 **integratedSecurity**接続プロパティおよび参照することによって**sqljdbc_auth.dll**」の説明に従って、[接続 URL の構築](../../connect/jdbc/building-the-connection-url.md)です。  
  
 以降で[!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]、アプリケーションで使用できます、 **authenticationScheme** Kerberos を使用してデータベースに接続したいことを示すために、接続プロパティは、ピュア Java Kerberos を使用して認証を統合実装:  
  
-   統合認証を使用する場合**Krb5LoginModule**を指定する必要があります、 **integratedSecurity = true**接続プロパティです。 指定します、 **authenticationScheme = java Kerberos**接続プロパティです。  
  
-   による統合認証を使用し続ける**sqljdbc_auth.dll**を指定するだけ**integratedSecurity = true**接続プロパティ (および必要に応じて**authenticationScheme =NativeAuthentication**)。  
  
-   指定した場合**authenticationScheme = java Kerberos**もを指定しないで**integratedSecurity = true**、ドライバーは無視されます、 **authenticationScheme**接続プロパティと、接続文字列でユーザー名とパスワードの資格情報を検索していると見なします。  
  
 データ ソースを使用して、接続を作成する、setAuthenticationScheme を使用して認証スキームをプログラムで設定して (必要に応じて) を使用して Kerberos 接続用の SPN を設定**setServerSpn**です。  
  
 Kerberos 認証をサポートするために、新しいロガー com.microsoft.sqlserver.jdbc.internals.KerbAuthentication が追加されました。 詳細については、次を参照してください。[ドライバー操作のトレース](../../connect/jdbc/tracing-driver-operation.md)です。  
  
 Kerberos を構成する場合は、次のガイドラインに従ってください。  
  
1.  設定**AllowTgtSessionKey** Windows のレジストリで 1 にします。 詳細については、次を参照してください。 [Kerberos プロトコルのレジストリ エントリおよび KDC 構成キー Windows Server 2003 で](http://support.microsoft.com/kb/837361)です。  
  
2.  Kerberos 構成 (UNIX 環境の krb5.conf) で環境の適切な領域および KDC が指定されていることを確認します。  
  
3.  kinit を使用するかまたはドメインにログインして、TGT キャッシュを初期化します。  
  
4.  ときに使用するアプリケーションを**authenticationScheme = java Kerberos**オペレーティング システムを Windows Vista または Windows 7 が実行され、標準ユーザー アカウントを使用する必要があります。 ただし、管理者のアカウントでアプリケーションを実行する場合は、アプリケーションを管理者権限で実行する必要があります。  
  
> [!NOTE]  
>  ServerSpn 接続属性には、Microsoft JDBC Drivers 4.2 によって以降のみサポートされます。  
  
## <a name="service-principal-names"></a>サービス プリンシパル名  
 サービス プリンシパル名 (SPN) は、クライアントがサービスのインスタンスを一意に識別するための名前です。  
  
 使用して、SPN を指定することができます、 **serverSpn**接続プロパティ、または単に、ドライバー (既定値) をビルドします。  このプロパティは、の形式で:"MSSQLSvc/fqdn:port@REALM"fqdn は完全修飾ドメイン名、port はポート番号、および領域とは大文字で SQL Server の Kerberos 領域をここでします。  Kerberos 構成の既定の領域が、サーバーと同じ領域であり、既定で含まれていない場合には、このプロパティの領域部分は省略可能です。  ここで、Kerberos 構成で既定の領域がサーバーの領域とは異なる領域であり、その領域間の認証のシナリオをサポートする場合には、serverSpn プロパティを使用して SPN を設定する必要があります。  
  
 たとえば、SPN のようになります:"MSSQLSvc/some-server.zzz.corp.contoso.com:1433@ZZZZ.CORP.CONTOSO.COM"。  
  
 サービス プリンシパル名 (SPN) の詳細については、以下を参照してください。  
  
-   [SQL Server で Kerberos 認証を使用する方法](http://support.microsoft.com/kb/319723)  
  
-   [SQL Server で Kerberos を使用](http://go.microsoft.com/fwlink/?LinkId=207814)  

> [!NOTE]  
> 6.2.0 がレルム Kerberos の間の適切な使用の JDBC ドライバーの解放前に、明示的に設定する必要がありますが、 **serverSpn**です。
>
> 6.2.0 時点でリリースでは、ドライバーを構築できる、 **serverSpn**既定では、クロス レルム Kerberos を使用する場合でもです。 1 つを使用できますが**serverSpn**明示的にすぎます。 
  
## <a name="creating-a-login-module-configuration-file"></a>ログイン モジュール構成ファイルの作成  
 オプションで Kerberos 構成ファイルを指定できます。 構成ファイルを指定しない場合、次の設定が有効になります。  
  
 Sun JVM  
 com.sun.security.auth.module.Krb5LoginModule 必要 useTicketCache = true  
  
 IBM JVM  
 com.ibm.security.auth.module.Krb5LoginModule 必要 useDefaultCcache = true  
  
 ログイン モジュール構成ファイルを作成する場合は、次の形式に従ってファイルを作成する必要があります。  
  
```  
<name> {  
    <LoginModule> <flag> <LoginModule options>;  
    <optional_additional_LoginModules, flags_and_options>;  
};  
```  
  
 ログイン構成ファイルは、特定の 1 つまたは複数のアプリケーションに使用する基底の認証テクノロジを指定する 1 つ以上のエントリから構成されます。 例を次に示します。  
  
```  
SQLJDBCDriver {  
   com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;  
};  
```  
  
 このように、それぞれのログイン モジュール構成ファイル エントリは、名前と、それに続く、(それぞれがセミコロンで終了し、グループ全体が中かっこで囲まれた) 1 つまたは複数のログイン モジュール固有のエントリから構成されます。 それぞれの構成ファイル エントリはセミコロンで終了します。  
  
 ドライバーは、ログイン モジュール構成ファイルに指定された設定を使用して Kerberos 資格情報を取得できることに加え、既存の資格情報を使用できます。 この機能は、アプリケーションでユーザーの資格情報を複数使用して接続を作成する必要がある場合に便利です。  
  
 ドライバーは、指定されたログイン モジュールを使用してログインを試行する前に、既存の資格情報を使用できる場合はそれを使用します。 したがって、特定のコンテキストで Subject.doAs メソッドを使用してコードを実行した場合、Subject.doAs 呼び出しに渡された資格情報を使用して接続が作成されます。  
  
 詳細については、次を参照してください。 [JAAS ログイン構成ファイル](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html)と[クラス Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html)です。  

 Microsoft JDBC Driver 6.2 以降は、接続プロパティ jaasConfigurationName を使用してログイン モジュール構成ファイルの名前を渡されることができます必要に応じて、これにより、独自のログイン構成を持つ各接続
 
## <a name="creating-a-kerberos-configuration-file"></a>Kerberos 構成ファイルの作成  
 Kerberos 構成ファイルの詳細については、次を参照してください。 [Kerberos の要件](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html)です。  
  
 サンプル ドメイン構成ファイルの例を次に示します。ここで、YYYY および ZZZZ は、サイトのドメイン名です。  
  
```  
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  
  
[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  
  
[realms]  
        YYYY.CORP.CONTOSO.COM = {  
  kdc = krbtgt/YYYY.CORP. CONTOSO.COM @ YYYY.CORP. CONTOSO.COM  
  default_domain = YYYY.CORP. CONTOSO.COM  
}  
  
        ZZZZ.CORP. CONTOSO.COM = {  
  kdc = krbtgt/ZZZZ.CORP. CONTOSO.COM @ ZZZZ.CORP. CONTOSO.COM  
  default_domain = ZZZZ.CORP. CONTOSO.COM  
}  
  
```  
  
## <a name="enabling-the-domain-configuration-file-and-the-login-module-configuration-file"></a>ドメイン構成ファイルおよびログイン モジュール構成ファイルの有効化  
 ドメイン構成ファイルを有効にするには、-Djava.security.krb5.conf を使用します。 ログイン モジュール構成ファイルを有効にすることができます **-Djava.security.auth.login.config**です。  
  
 たとえば、アプリケーションを起動するときに、次のコマンド ラインを使用できます。  
  
```  
Java.exe -Djava.security.auth.login.config=SQLJDBCDriver.conf -Djava.security.krb5.conf=krb5.ini <APPLICATION_NAME>  
  
```  
  
## <a name="verifying-that-sql-server-can-be-accessed-via-kerberos"></a>Kerberos を介して SQL Server にアクセスできるかどうかの確認  
 SQL Server Management Studio で次のクエリを実行します。  
  
 **sys.dm_exec_connections から auth_scheme を選択している session_id = @@spid**  
  
 このクエリを実行するために必要な権限があることを確認してください。  

## <a name="constrained-delegation"></a>制約付き委任
Microsoft JDBC Driver 6.2 以降は、ドライバーは、Kerberos 制約付き委任をサポートします。 Org.ietf.jgss.GSSCredential オブジェクトとしてで委任された資格情報を渡すことが、これらの資格情報は、ドライバーで接続を確立するために使用されます。 

```
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>プリンシパル名とパスワードを使用して Kerberos 接続
Microsoft JDBC Driver 6.2 以降は、ドライバーは接続文字列に Kerberos プリンシパル名とパスワードを使用して接続を渡すを確立できます。 
```
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```
Krb5.conf ファイルで設定 default_realm にユーザーが属している場合、ユーザー名プロパティによる領域は不要です。 ときに`userName`と`password`と共に設定されている`integratedSecurity=true;`と`authenticationScheme=JavaKerberos;`プロパティ、接続が確立されるユーザー名の値を持つに沿って Kerberos プリンシパルとして指定されたパスワードを使用します。
 
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる SQL Server への接続](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
