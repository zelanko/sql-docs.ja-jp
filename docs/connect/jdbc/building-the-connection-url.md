---
title: "接続 URL の構築 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44996746-d373-4f59-9863-a8a20bb8024a
caps.latest.revision: 53
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b5707221b51bff301aa5e9214497ba9090750aae
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="building-the-connection-url"></a>接続 URL の構築
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  接続 URL の一般的な書式は次のとおりです。  
  
 `jdbc:sqlserver://[serverName[\instanceName][:portNumber]][;property=value[;property=value]]`  
  
 それぞれの文字の説明は次のとおりです。  
  
-   **jdbc:sqlserver://** (必須) は、サブプロトコルあり定数です。  
  
-   **serverName** (省略可能) に接続するサーバーのアドレス。 接続先のサーバーのアドレスには DNS または IP アドレスを指定するか、またはローカル コンピューターを表す localhost あるいは 127.0.0.1 を指定できます。 接続 URL で指定されていない場合、プロパティのコレクションでサーバー名を指定する必要があります。  
  
-   **instanceName** (省略可能) は、serverName 上に接続するインスタンス。 指定しない場合、既定のインスタンスへの接続が行われます。  
  
-   **portNumber** (省略可能) は、serverName 上に接続するポート。 既定では 1433 です。 既定のポートを使用する場合は、URL でポートおよびその前の ':' を指定する必要はありません。  
  
    > [!NOTE]  
    >  最適な接続パフォーマンスのために、名前付きインスタンスに接続するときは portNumber を設定します。 こうすることにより、ポート番号を決定するためのサーバーへのラウンド トリップが回避されます。 portNumber および instanceName の両方が使用されている場合、portNumber が優先され、instanceName は無視されます。  
  
-   **プロパティ**(省略可能) は 1 つまたは複数の接続プロパティ オプション。 詳細については、次を参照してください。[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。 リストに含まれる任意のプロパティを指定できます。 プロパティを区切るには必ずセミコロン (';') を使用します。またプロパティを重複して指定することはできません。  
  
> [!CAUTION]  
>  セキュリティ上の理由から、ユーザー入力に基づく接続 URL の作成は避ける必要があります。 URL では、サーバー名とドライバーだけを指定するようにします。 ユーザー名とパスワードの値には、接続プロパティのコレクションを使用します。 JDBC アプリケーションにおけるセキュリティの詳細については、次を参照してください。 [JDBC ドライバー アプリケーションのセキュリティで保護する](../../connect/jdbc/securing-jdbc-driver-applications.md)です。  
  
## <a name="connection-examples"></a>接続の例  
 ユーザー名とパスワードを使用して、ローカル コンピューター上の既定のデータベースに接続します。  
  
 `jdbc:sqlserver://localhost;user=MyUserName;password=*****;`  
  
> [!NOTE]  
>  前の例では接続文字列でユーザー名とパスワードを使用していますが、より安全な統合セキュリティを使用する必要があります。 詳細については、次を参照してください。、[統合認証を使用した接続](#Connectingintegrated)このトピックで後述します。  
  
 次の接続文字列に接続する方法の例を示しています、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースでサポートされている任意のオペレーティング システムで実行されているアプリケーションから統合認証および Kerberos を使用して、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]:  
  
```  
jdbc:sqlserver://;servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos  
```  
  
 統合認証を使用して、ローカル コンピューター上の既定のデータベースに接続します。  
  
 `jdbc:sqlserver://localhost;integratedSecurity=true;`  
  
 リモート サーバー上の名前付きデータベースに接続します。  
  
 `jdbc:sqlserver://localhost;databaseName=AdventureWorks;integratedSecurity=true;`  
  
 既定のポートでリモート サーバーに接続します。  
  
 `jdbc:sqlserver://localhost:1433;databaseName=AdventureWorks;integratedSecurity=true;`  
  
 カスタマイズされたアプリケーション名を指定して接続します。  
  
 `jdbc:sqlserver://localhost;databaseName=AdventureWorks;integratedSecurity=true;applicationName=MyApp;`  
  
## <a name="named-and-multiple-sql-server-instances"></a>名前付きおよび複数の SQL Server インスタンス  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]サーバーごとの複数のデータベース インスタンスをインストールをできます。 各インスタンスは個別の名前によって識別されます。 名前付きインスタンスに接続する[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)](推奨)、名前付きインスタンスのポート番号を指定することができますか、またはインスタンス名を JDBC URL プロパティとして指定することができます、または**データソース**プロパティです。 インスタンス名またはポート番号のプロパティを指定しない場合は、既定のインスタンスへの接続が作成されます。 次の例を参照してください。  
  
 ポート番号を使用するには、次のように指定します。  
  
 `jdbc:sqlserver://localhost:1433;integratedSecurity=true;<more properties as required>;`  
  
 JDBC URL プロパティを使用するには、次のように指定します。  
  
 `jdbc:sqlserver://localhost;instanceName=instance1;integratedSecurity=true;<more properties as required>;`  
  
## <a name="escaping-values-in-the-connection-url"></a>接続 URL での値のエスケープ  
 スペース、セミコロン、引用符などの特殊文字を挿入するため、接続 URL の値の特定部分のエスケープが必要になる場合があります。 JDBC ドライバーでは、エスケープする文字を中かっこで囲みます。 たとえば、{;} とするとセミコロンがエスケープされます。  
  
 エスケープする値には特殊文字 (特に '='、';'、'[]'、およびスペース) を含めることができますが、中かっこはエスケープできません。 エスケープが必要な値に中かっこが含まれる場合は、プロパティのコレクションに加える必要があります。  
  
> [!NOTE]  
>  中かっこ内の空白はリテラルでありトリミングされません。  
  
##  <a name="Connectingintegrated"></a>Windows 統合認証を使用した接続  
 JDBC ドライバーでは、integratedSecurity 接続文字列プロパティを通じて、Windows オペレーティング システム上でのタイプ 2 の統合認証の使用がサポートされています。 統合認証を使用するには、JDBC ドライバーがインストールされているコンピューターの Windows システム パス上のディレクトリに sqljdbc_auth.dll ファイルをコピーします。  
  
 sqljdbc_auth.dll ファイルは次の場所にインストールされています。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \auth\  
  
 サポートされている任意のオペレーティング システムについて、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]を参照してください[を使用して Kerberos 統合認証を SQL Server への接続](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)で追加された機能の詳細については[!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]アプリケーションに接続することができます、データベースはタイプ 4 の Kerberos 統合認証を使用します。  
  
> [!NOTE]  
>  32 ビットの Java 仮想マシン (JVM) を実行している場合は、オペレーティング システムのバージョンが x64 であっても、x86 フォルダーの sqljdbc_auth.dll ファイルを使用してください。 64 ビットの JVM を x64 プロセッサ上で実行している場合は、x64 フォルダーの sqljdbc_auth.dll ファイルを使用してください。  
  
 または、java.libary.path システム プロパティを設定して sqljdbc_auth.dll のディレクトリを指定することもできます。 たとえば、JDBC ドライバーが既定のディレクトリにインストールされている場合、Java アプリケーションの起動時に次の仮想マシン (VM) 引数を使用することで、DLL の場所を指定できます。  
  
 `-Djava.library.path=C:\Microsoft JDBC Driver 4.0 for SQL Server\sqljdbc_<version>\enu\auth\x86`  
  
## <a name="connecting-with-ipv6-addresses"></a>IPv6 アドレスによる接続  
 JDBC ドライバーでは、接続プロパティのコレクション、および serverName 接続文字列プロパティと合わせて IPv6 アドレスを使用できます。 Jdbc など、serverName の初期値:*sqlserver*://*serverName*、接続文字列内の IPv6 アドレスはサポートされていません。 名前を使用して*serverName*生 IPv6 ではなくアドレスは、接続ですべてのケースで機能します。 詳細を次の例に示します。  
  
 **ServerName プロパティを使用するには**  
  
 `jdbc:sqlserver://;serverName=3ffe:8311:eeee:f70f:0:5eae:10.203.31.9\\instance1;integratedSecurity=true;`  
  
 **プロパティのコレクションを使用するには**  
  
 `Properties pro = new Properties();`  
  
 `pro.setProperty("serverName", "serverName=3ffe:8311:eeee:f70f:0:5eae:10.203.31.9\\instance1");`  
  
 `Connection con = DriverManager.getConnection("jdbc:sqlserver://;integratedSecurity=true;", pro);`  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーで SQL Server に接続します。](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
