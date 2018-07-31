---
title: Kerberos 統合認証による SQL Server への接続 | Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5c36df2b7cc6feda976a3edfdadbac68e9b96dd3
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279044"
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>Kerberos 統合認証による SQL Server への接続」を参照してください。
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] 以降、アプリケーションは、**authenticationScheme** 接続プロパティを使用して、タイプ 4 の Kerberos 統合認証を使用してデータベースに接続することを示すことができます。 参照してください[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)接続のプロパティの詳細についてはします。 Kerberos の詳細については、次を参照してください。 [Microsoft Kerberos](http://go.microsoft.com/fwlink/?LinkID=100758)します。  
  
 Java **Krb5LoginModule** で統合認証を使用する場合、[Krb5LoginModule クラス](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html)を使用してモジュールを構成できます。  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] では、IBM Java VM 用に次のプロパティが設定されます。  
  
-   **useDefaultCcache = true**  
  
-   **moduleBanner = false**  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] では、他のすべての Java VM 用に次のプロパティが設定されます。  
  
-   **useTicketCache = true**  
  
-   **doNotPrompt = true**  
  
## <a name="remarks"></a>Remarks  
 前のバージョン[!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]、アプリケーションは、統合認証 (Kerberos または NTLM を使用して、によって提供される) を指定できますを使用して、 **integratedSecurity**接続プロパティおよび参照することによって**sqljdbc_auth.dll**」の説明に従って、[接続 URL の構築](../../connect/jdbc/building-the-connection-url.md)します。  
  
 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] 以降、アプリケーションは、**authenticationScheme** 接続プロパティを使用して、ピュア Java Kerberos 実装を使用した Kerberos 統合認証を使用してデータベースに接続することを示すことができます。  
  
-   統合認証を使用する場合**Krb5LoginModule**を指定する必要があります、 **integratedSecurity = true**接続プロパティです。 指定し、 **authenticationScheme = java Kerberos**接続プロパティです。  
  
-   による統合認証を使用し続ける**sqljdbc_auth.dll**を指定するだけ**integratedSecurity = true**接続プロパティ (および必要に応じて**authenticationScheme =NativeAuthentication**)。  
  
-   指定した場合**authenticationScheme = java Kerberos**も指定しないで**integratedSecurity = true**、ドライバーは無視されます、 **authenticationScheme**接続プロパティが、接続文字列にユーザー名とパスワードの資格情報を検索する期待します。  
  
 データソースを使用して接続を作成する場合、setAuthenticationScheme を使用して認証スキームをプログラムで設定できます。また、必要に応じて、**setServerSpn** を使用して Kerberos 接続用の SPN を設定できます。  
  
 Kerberos 認証をサポートするために、新しいロガー com.microsoft.sqlserver.jdbc.internals.KerbAuthentication が追加されました。 詳しくは、「[ドライバー操作のトレース](../../connect/jdbc/tracing-driver-operation.md)」をご覧ください。  
  
 Kerberos を構成する場合は、次のガイドラインに従ってください。  
  
1.  設定**AllowTgtSessionKey** Windows 用のレジストリ内の 1 にします。 詳しくは、「[Kerberos protocol registry entries and KDC configuration keys in Windows Server 2003](http://support.microsoft.com/kb/837361)」(Windows Server 2003 における Kerberos プロトコルのレジストリ エントリおよび KDC 構成キー) をご覧ください。  
  
2.  Kerberos 構成 (UNIX 環境の krb5.conf) で環境の適切な領域および KDC が指定されていることを確認します。  
  
3.  kinit を使用するかまたはドメインにログインして、TGT キャッシュを初期化します。  
  
4.  **authenticationScheme=JavaKerberos** を使用するアプリケーションを Windows Vista または Windows 7 オペレーティング システムで実行する場合は、標準ユーザー アカウントを使用する必要があります。 ただし、管理者のアカウントでアプリケーションを実行する場合は、アプリケーションを管理者権限で実行する必要があります。  
  
> [!NOTE]  
>  serverSpn 接続属性は、Microsoft JDBC Driver 4.2 以降でのみサポートされています。  
  
## <a name="service-principal-names"></a>サービス プリンシパル名  
 サービス プリンシパル名 (SPN) は、クライアントがサービスのインスタンスを一意に識別するための名前です。  
  
 **serverSpn** 接続プロパティを使用して SPN を指定できますが、ドライバーで自動的に作成することもできます (既定)。  このプロパティの形式は "MSSQLSvc/fqdn:port\@REALM" です。ここで、fqdn は完全修飾ドメイン名、port はポート番号、REALM は大文字で表記された SQL Server の Kerberos 領域です。  Kerberos 構成の既定の領域が、サーバーと同じ領域であり、既定で含まれていない場合には、このプロパティの領域部分は省略可能です。  ここで、Kerberos 構成で既定の領域がサーバーの領域とは異なる領域であり、その領域間の認証のシナリオをサポートする場合には、serverSpn プロパティを使用して SPN を設定する必要があります。  
  
 たとえば、SPN のようになります。:"MSSQLSvc/some-server.zzz.corp.contoso.com:1433\@ZZZZ します。CORP.CONTOSO.COM"  
  
 サービス プリンシパル名 (SPN) の詳細については、以下を参照してください。  
  
-   [SQL Server で Kerberos 認証を使用する方法](http://support.microsoft.com/kb/319723)  
  
-   [SQL Server での Kerberos の使用](http://go.microsoft.com/fwlink/?LinkId=207814)  

> [!NOTE]  
> 6.2.0 を領域 Kerberos の間の適切な使用を JDBC ドライバーのリリース前に、明示的に設定する必要があります、 **serverSpn**します。
>
> 6.2.0 時点でリリースでは、ドライバーを構築することになります、 **serverSpn**交差領域の Kerberos を使用する場合でも、既定でします。 1 つを使用できますが**serverSpn**明示的にすぎます。 
  
## <a name="creating-a-login-module-configuration-file"></a>ログイン モジュール構成ファイルの作成  
 オプションで Kerberos 構成ファイルを指定できます。 構成ファイルを指定しない場合、次の設定が有効になります。  
  
 Sun JVM  
 com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;  
  
 IBM JVM  
 com.ibm.security.auth.module.Krb5LoginModule required useDefaultCcache = true;  
  
 ログイン モジュール構成ファイルを作成する場合は、次の形式に従ってファイルを作成する必要があります。  
  
```  
<name> {  
    <LoginModule> <flag> <LoginModule options>;  
    <optional_additional_LoginModules, flags_and_options>;  
};  
```  
  
 ログイン構成ファイルは、特定の 1 つまたは複数のアプリケーションに使用する基底の認証テクノロジを指定する 1 つ以上のエントリから構成されます。 例を次に示します。  
  
```java
SQLJDBCDriver {  
   com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;  
};  
```  
  
 このように、それぞれのログイン モジュール構成ファイル エントリは、名前と、それに続く、(それぞれがセミコロンで終了し、グループ全体が中かっこで囲まれた) 1 つまたは複数のログイン モジュール固有のエントリから構成されます。 それぞれの構成ファイル エントリはセミコロンで終了します。  
  
 ドライバーは、ログイン モジュール構成ファイルに指定された設定を使用して Kerberos 資格情報を取得できることに加え、既存の資格情報を使用できます。 この機能は、アプリケーションでユーザーの資格情報を複数使用して接続を作成する必要がある場合に便利です。  
  
 ドライバーは、指定されたログイン モジュールを使用してログインを試行する前に、既存の資格情報を使用できる場合はそれを使用します。 したがって、特定のコンテキストで Subject.doAs メソッドを使用してコードを実行した場合、Subject.doAs 呼び出しに渡された資格情報を使用して接続が作成されます。  
  
 詳しくは、「[JAAS Login Configuration File](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html)」(JAAS ログイン構成ファイル) および「[Class Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html)」(Krb5LoginModule クラス) をご覧ください。  

 Microsoft JDBC Driver 6.2 以降は接続プロパティ jaasConfigurationName を使用してログイン モジュール構成ファイルの名前を渡されることができます必要に応じて、これにより、独自のログインの構成を持つ各接続。
 
## <a name="creating-a-kerberos-configuration-file"></a>Kerberos 構成ファイルの作成  
 Kerberos の構成ファイルについて詳しくは、「[Kerberos Requirements](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html)」(Kerberos の要件) をご覧ください。  
  
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
 ドメイン構成ファイルを有効にするには、-Djava.security.krb5.conf を使用します。 ログイン モジュール構成ファイルを有効にすることができます **-Djava.security.auth.login.config**します。  
  
 たとえば、アプリケーションを起動するときに、次のコマンド ラインを使用できます。  
  
```  
Java.exe -Djava.security.auth.login.config=SQLJDBCDriver.conf -Djava.security.krb5.conf=krb5.ini <APPLICATION_NAME>  
  
```  
  
## <a name="verifying-that-sql-server-can-be-accessed-via-kerberos"></a>Kerberos を介して SQL Server にアクセスできるかどうかの確認  
 SQL Server Management Studio で次のクエリを実行します。  
  
 **sys.dm_exec_connections から auth_scheme を選択して、session_id =\@\@spid**  
  
 このクエリを実行するために必要な権限があることを確認してください。  

## <a name="constrained-delegation"></a>制約付き委任
Microsoft JDBC Driver 6.2 以降は、ドライバーは Kerberos の制約付き委任をサポートします。 Org.ietf.jgss.GSSCredential オブジェクトとしての委任された資格情報を渡すことが、これらの資格情報は、ドライバーで接続を確立するために使用されます。 

```java
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>プリンシパル名とパスワードを使用して Kerberos 接続
Microsoft JDBC Driver 6.2 以降は、ドライバーは接続文字列で Kerberos プリンシパル名とパスワードを使用して接続が渡されるを確立できます。 
```java
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```
Krb5.conf ファイルで設定 default_realm にユーザーが属している場合、username プロパティによる領域は不要です。 ときに`userName`と`password`と共に設定されている`integratedSecurity=true;`と`authenticationScheme=JavaKerberos;`プロパティ、接続を確立するにはユーザー名の値を持つに沿って Kerberos プリンシパルとして指定されたパスワードを使用しています。
 
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる SQL Server への接続](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
