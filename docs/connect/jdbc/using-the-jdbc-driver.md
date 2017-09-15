---
title: "JDBC ドライバーの使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6faaf05b-8b70-4ed2-9b44-eee5897f1cd0
caps.latest.revision: 54
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1a067e98988c59de27e2c6a65775a337d58b23f9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-the-jdbc-driver"></a>「JDBC ドライバーの使用」を参照してください。
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  このセクションで説明する簡単な接続を行うためのクイック スタート手順、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースを使用して、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]です。 接続する前に、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]ローカル コンピューターまたはサーバーのいずれかで最初にインストールされている必要があり、JDBC ドライバーは、ローカル コンピューターにインストールする必要があります。  
  
## <a name="choosing-the-right-jar-file"></a>最適な JAR ファイルの選択  
 SQL Server 用 Microsoft JDBC Driver 6.2 提供**mssql jdbc-6.2.1.jre7.jar**、および**mssql jdbc-6.2.1.jre8.jar**クラス、推奨の Java ランタイムによって使用されるライブラリ ファイル環境 (JRE) 設定します。  
  
  Microsoft JDBC Drivers 6.0 と 4.2 for SQL Server 提供**sqljdbc41.jar**、および**sqljdbc42.jar**クラス ライブラリ ファイル、必要な Java ランタイム環境 (JRE) 設定によって使い分けることができます。  
  
 Microsoft JDBC Driver 4.1 for SQL Server の提供、 **sqljdbc41.jar**クラス ライブラリ ファイル、必要な Java ランタイム環境 (JRE) 設定によって使い分けることができます。  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 4.0 提供**sqljdbc.jar**と**sqljdbc4.jar**クラス ライブラリ ファイル、必要な Java ランタイム環境 (JRE) 設定によって使い分けることができます。  
  
 また、選択した JAR ファイルによって、使用可能な機能が決定します。 選択する JAR ファイルの詳細については、次を参照してください。 [JDBC Driver のシステム要件](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)です。  
  
## <a name="setting-the-classpath"></a>クラスパスの設定  
 JDBC ドライバーは、Java SDK の一部ではありません。 それを使用する場合に含めるクラスパスを設定する必要があります、 **sqljdbc.jar**ファイル、 **sqljdbc4.jar**ファイル、 **sqljdbc41.jar**ファイル、または**sqljdbc42.jar**ファイル。 JDBC ドライバー 6.2 を使用する、クラスパスの設定を含める場合、 **mssql jdbc-6.2.1.jre7.jar**または**mssql jdbc-6.2.1.jre8.jar**です。 クラスパスにエントリがない場合、アプリケーションで "Class not found" という一般的な例外がスローされます。  
  
### <a name="for-microsoft-jdbc-driver-62"></a>Microsoft JDBC driver 6.2
 **Mssql jdbc-6.2.1.jre7.jar**または**mssql jdbc-6.2.1.jre8.jar**ファイルは、次の場所にインストールされます。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \mssql-jdbc-6.2.1.jre7.jar 
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \mssql-jdbc-6.2.1.jre8.jar
  
 Windows アプリケーションで使用される CLASSPATH ステートメントの例を以下に示します。  
  
 `CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.2 for SQL Server\sqljdbc_6.2\enu\mssql-jdbc-6.2.1.jre8.jar`  
  
 Unix/Linux アプリケーションで使用される CLASSPATH ステートメントの例を以下に示します。  
  
 `CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_6.2/enu/mssql-jdbc-6.2.1.jre8.jar`  
  
 CLASSPATH ステートメントに、1 つだけ含まれていることを確認する必要があります[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]、mssql jdbc-6.2.1.jre7.jar mssql jdbc-6.2.1.jre8.jar などです。  

### <a name="for-microsoft-jdbc-driver-40-41-42-and-60"></a>Microsoft JDBC driver 4.0、4.1、4.2、および 6.0
 sqljdbc.jar ファイル、sqljdbc4.jar ファイル、sqljdbc41.jar ファイル、または sqljdbc42.jar ファイルは次の場所にインストールします。  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \sqljdbc.jar  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \sqljdbc4.jar  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \sqljdbc41.jar  
  
 \<*インストール ディレクトリ*> \sqljdbc_\<*バージョン*>\\<*言語*> \sqljdbc42.jar  
  
 Windows アプリケーションで使用される CLASSPATH ステートメントの例を以下に示します。  
  
 `CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.0 for SQL Server\sqljdbc_4.2\enu\sqljdbc42.jar`  
  
 Unix/Linux アプリケーションで使用される CLASSPATH ステートメントの例を以下に示します。  
  
 `CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_4.2/enu/sqljdbc42.jar`  
  
 CLASSPATH ステートメントに、1 つだけ含まれていることを確認する必要があります[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]sqljdbc.jar、sqljdbc4.jar、sqljdbc41.jar、または sqljdbc42.jar などです。  
  
> [!NOTE]  
>  Windows システムでは、ディレクトリ名が 8.3 ファイル名規則より長い場合、またはフォルダー名にスペースが含まれている場合、クラスパスに問題が生じることがあります。 この種の問題が疑われる場合は一時的に移動する、sqljdbc.jar ファイル、sqljdbc4.jar ファイル、または sqljdbc41.jar ファイル単純なディレクトリ名になど`C:\Temp`クラスパスを変更、および問題を解決するかどうか判断します。  
  
### <a name="applications-that-are-run-directly-at-the-command-prompt"></a>コマンド プロンプトで直接実行されるアプリケーション  
 クラスパスは、オペレーティング システムにおいて構成されます。 sqljdbc.jar、sqljdbc4.jar、または sqljdbc41.jar をシステムのクラスパスに追加します。 またを使用してアプリケーションを実行する Java コマンドラインで、クラスパスを指定することができます、`java -classpath`オプション。  
  
### <a name="applications-that-run-in-an-ide"></a>IDE で実行されるアプリケーション  
 各 IDE ベンダーでは、クラスパスを自社の IDE に設定するためのさまざまな方法を用意しています。 クラスパスをオペレーティング システムで設定するだけでは動作しません。 sqljdbc.jar、sqljdbc4.jar、または sqljdbc41.jar を IDE クラスパスに追加する必要があります。  
  
### <a name="servlets-and-jsps"></a>サーブレットおよび JSP  
 サーブレットや JSP は、Tomcat のようなサーブレット/JSP エンジンで実行されます。 クラスパスは、サーブレット/JSP エンジンのドキュメントに従って設定する必要があります。 クラスパスをオペレーティング システムで設定するだけでは動作しません。 一部のサーブレット/JSP エンジンでは、エンジンのクラスパスを設定するために使用できるセットアップ画面が用意されています。 この場合、正しい JDBC ドライバー用 JAR ファイルを既存のエンジン クラスパスに追加し、エンジンを再起動する必要があります。 この他の場合は、エンジンをインストールするときに lib のような特定のディレクトリに sqljdbc.jar、sqljdbc4.jar、または sqljdbc41.jar をコピーしてドライバーを配置することができます。 エンジン ドライバーのクラスパスは、エンジン固有の構成ファイルで指定することもできます。  
  
### <a name="enterprise-java-beans"></a>Enterprise Java Beans  
 Enterprise Java Beans (EJB) は、EJB コンテナーで実行されます。 EJB コンテナーは、さまざまなベンダーから供給されています。 Java アプレットはブラウザー上で動作しますが、Web サーバーからダウンロードされます。 Sqljdbc.jar、sqljdbc4.jar、または sqljdbc41.jar を web サーバーのルートにコピーし、アプレットの [HTML archive] タブで JAR ファイルの名前を指定する場合など、`<applet ... archive=sqljdbc.jar>`です。  
  
## <a name="making-a-simple-connection-to-a-database"></a>データベースへの単純な接続を行う  
 sqljdbc.jar クラス ライブラリを使用するアプリケーションでは、まず次のようにしてドライバーを登録する必要があります。  
  
 `Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");`  
  
 ドライバーが読み込まれるときに、接続 URL および DriverManager クラスの getConnection メソッドを使用して接続を確立することができます。  
  
```  
String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
   "databaseName=AdventureWorks;user=MyUserName;password=*****;";  
Connection con = DriverManager.getConnection(connectionUrl);  
```  
  
 JDBC API 4.0 では、DriverManager.getConnection メソッドは JDBC ドライバーを自動的に読み込まれるように強化されました。 そのため、アプリケーションでは、登録または sqljdbc4.jar、sqljdbc41.jar、または sqljdbc42.jar クラス ライブラリを使用する場合、ドライバーの読み込みに Class.forName メソッドを呼び出す必要はありません。  
  
 DriverManager クラスの getConnection メソッドを呼び出したときに、一連の登録済みの JDBC ドライバーから適切なドライバーがあります。 sqljdbc4.jar、sqljdbc41.jar、または sqljdbc42.jar ファイルが含まれる"META-INF/services/java.sql.Driver"ファイルが含まれています、 **com.microsoft.sqlserver.jdbc.SQLServerDriver**として登録されているドライバーです。 現在 Class.forName メソッドを使用してドライバーを読み込むの既存のアプリケーションは、変更せずに続行されます。  
  
> [!NOTE]  
>  sqljdbc4.jar、sqljdbc41.jar、または sqljdbc42.jar のクラス ライブラリは、以前のバージョンの Java Runtime Environment (JRE) では使用できません。 参照してください[JDBC Driver のシステム要件](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)によってサポートされる JRE バージョンの一覧については、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]です。  
  
 データ ソースに接続し、接続 URL を使用する方法の詳細については、次を参照してください。[接続 URL の構築](../../connect/jdbc/building-the-connection-url.md)と[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

