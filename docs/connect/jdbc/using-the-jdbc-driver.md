---
title: JDBC ドライバーの使用 |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 6faaf05b-8b70-4ed2-9b44-eee5897f1cd0
caps.latest.revision: 54
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1ece23b74de9265f28468ae11702c07cdca1cecc
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786107"
---
# <a name="using-the-jdbc-driver"></a>JDBC ドライバーの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

このセクションでは、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースへのシンプルな接続を作成する方法について簡単に説明します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに接続する前に、まず [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をローカル コンピューターまたはサーバーのどちらかにインストールし、JDBC ドライバーをローカル コンピューターにインストールする必要があります。  
  
## <a name="choosing-the-right-jar-file"></a>最適な JAR ファイルの選択

Microsoft JDBC Driver は、下にな Java ランタイム環境 (JRE) 設定、通信で使用されるさまざまな Jar を提供します。

SQL Server 用 Microsoft JDBC ドライバー 7.0 では、 **mssql-jdbc-7.0.0.jre8.jar**、および**mssql-jdbc-7.0.0.jre10.jar**クラス ライブラリ ファイル。

SQL Server 用 Microsoft JDBC Driver 6.4 の提供**mssql-jdbc-6.4.0.jre7.jar**、 **mssql-jdbc-6.4.0.jre8.jar**、および**mssql-jdbc-6.4.0.jre9.jar**クラス ライブラリファイル。

Microsoft JDBC Driver 6.2 for SQL Server は、 **mssql-jdbc-6.2.2.jre7.jar**、および**mssql-jdbc-6.2.2.jre8.jar**クラス ライブラリ ファイル。
  
Microsoft JDBC Drivers 6.0 と 4.2 for SQL Server 提供**sqljdbc41.jar**、および**sqljdbc42.jar**クラス ライブラリ ファイル。
  
Microsoft JDBC Driver 4.1 for SQL Server の提供、 **sqljdbc41.jar**クラス ライブラリ ファイル。

また、選択した JAR ファイルによって、使用可能な機能が決定します。 選択する JAR ファイルの詳細については、次を参照してください。 [JDBC Driver のシステム要件](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)します。  
  
## <a name="setting-the-classpath"></a>クラスパスの設定

Microsoft JDBC driver jar が Java SDK の一部ではないと、ユーザー アプリケーションの Classpath に含める必要があります。

JDBC Driver 4.1 または 4.2 を使用して、クラスパスの設定が含まれている場合**sqljdbc41.jar**または**sqljdbc42.jar**それぞれのドライバーのダウンロードからファイル。

JDBC Driver 6.2 を使用して、クラスパスの設定が含まれている場合、 **mssql-jdbc-6.2.2.jre7.jar**または**mssql-jdbc-6.2.2.jre8.jar**します。

JDBC Driver 6.4 を使用して設定されて、クラスパスに含める場合、 **mssql-jdbc-6.4.0.jre7.jar**、* * mssql jdbc-6.4.0.jre8.jar または**mssql-jdbc-6.4.0.jre9.jar**します。

JDBC ドライバーの 7.0 を使用して設定されて、クラスパスに含める場合、 **mssql-jdbc-7.0.0.jre8.jar**または**mssql-jdbc-7.0.0.jre10.jar**します。

アプリケーションが、一般的なをスローする場合は、クラスパスには、適切な Jar ファイルのエントリがない、`Class not found`例外。  
  
### <a name="for-microsoft-jdbc-driver-70"></a>Microsoft JDBC driver 7.0

**Mssql-jdbc-7.0.0.jre8.jar**または**mssql-jdbc-7.0.0.jre10.jar**ファイルは、次の場所にインストールされます。

```bash
\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-7.0.0.jre8.jar

\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-7.0.0.jre10.jar
```

次のスニペットは、Windows アプリケーションで使用される CLASSPATH ステートメントの例です。  

`CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 7.0 for SQL Server\sqljdbc_7.0\enu\mssql-jdbc-7.0.0.jre10.jar`  
  
次のスニペットは、Unix/Linux アプリケーションで使用される CLASSPATH ステートメントの例です。  
  
`CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_7.0/enu/mssql-jdbc-7.0.0.jre10.jar`  
  
CLASSPATH ステートメントに、1 つだけ含まれているかどうかを確認[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]、いずれかなど**mssql-jdbc-7.0.0.jre8.jar**または**mssql-jdbc-7.0.0.jre10.jar**します。

### <a name="for-microsoft-jdbc-driver-64"></a>Microsoft JDBC driver 6.4

**Mssql-jdbc-6.4.0.jre7.jar**、* * mssql jdbc-6.4.0.jre8.jar または**mssql-jdbc-6.4.0.jre9.jar**ファイルは次の場所にインストールされます。  

```bash  
\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-6.4.0.jre7.jar
  
\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-6.4.0.jre8.jar

\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-6.4.0.jre9.jar
```

次のスニペットは、Windows アプリケーションで使用される CLASSPATH ステートメントの例です。  
  
`CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.4 for SQL Server\sqljdbc_6.4\enu\mssql-jdbc-6.4.0.jre9.jar`  
  
次のスニペットは、Unix/Linux アプリケーションで使用される CLASSPATH ステートメントの例です。  
  
`CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_6.4/enu/mssql-jdbc-6.4.0.jre9.jar`  
  
CLASSPATH ステートメントに、1 つだけ含まれているかどうかを確認[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]、いずれかなど**mssql-jdbc-6.4.0.jre7.jar**、* * mssql jdbc-6.4.0.jre8.jar または**mssql-jdbc-6.4.0.jre9.jar**します。

### <a name="for-microsoft-jdbc-driver-62"></a>Microsoft JDBC driver 6.2

**Mssql-jdbc-6.2.2.jre7.jar**または**mssql-jdbc-6.2.2.jre8.jar**ファイルは、次の場所にインストールされます。

```bash
\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-6.2.2.jre7.jar
  
\<installation directory>\sqljdbc_<version>\<language>\mssql-jdbc-6.2.2.jre8.jar
```

次のスニペットは、Windows アプリケーションで使用される CLASSPATH ステートメントの例です。  
  
`CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.2 for SQL Server\sqljdbc_6.2\enu\mssql-jdbc-6.2.2.jre8.jar`  
  
次のスニペットは、Unix/Linux アプリケーションで使用される CLASSPATH ステートメントの例です。  
  
`CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_6.2/enu/mssql-jdbc-6.2.2.jre8.jar`  
  
CLASSPATH ステートメントに、1 つだけ含まれているかどうかを確認[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]mssql の jdbc-6.2.2.jre7.jar mssql-jdbc-6.2.2.jre8.jar など。  

### <a name="for-microsoft-jdbc-driver-41-42-and-60"></a>Microsoft JDBC driver 4.1、4.2、および 6.0

sqljdbc.jar ファイル、sqljdbc4.jar ファイル、sqljdbc41.jar ファイル、または sqljdbc42.jar ファイルは次の場所にインストールします。  

```bash
\<installation directory>\sqljdbc_<version>\<language>\sqljdbc.jar  
  
\<installation directory>\sqljdbc_<version>\<language>\sqljdbc4.jar  
  
\<installation directory>\sqljdbc_<version>\<language>\sqljdbc41.jar  
  
\<installation directory>\sqljdbc_<version>\<language>\sqljdbc42.jar  
```

次のスニペットは、Windows アプリケーションで使用される CLASSPATH ステートメントの例です。  
  
`CLASSPATH =.;C:\Program Files\Microsoft JDBC Driver 6.0 for SQL Server\sqljdbc_4.2\enu\sqljdbc42.jar`  
  
次のスニペットは、Unix/Linux アプリケーションで使用される CLASSPATH ステートメントの例です。  

`CLASSPATH =.:/home/usr1/mssqlserverjdbc/Driver/sqljdbc_4.2/enu/sqljdbc42.jar`  
  
CLASSPATH ステートメントに含まれている [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] が、sqljdbc.jar、sqljdbc4.jar、sqljdbc41.jar、または sqljdbc42.jar のいずれか 1 つであることを確認してください。  
  
> [!NOTE]  
> Windows システムでは、ディレクトリ名が 8.3 ファイル名規則より長い場合、またはフォルダー名にスペースが含まれている場合、クラスパスに問題が生じることがあります。 この種の問題が疑われる場合、sqljdbc.jar ファイル、sqljdbc4.jar ファイル、または sqljdbc41.jar ファイルを一時的に `C:\Temp` のようなシンプルな名前のディレクトリへ移動し、クラスパスを変更して問題が解決するかどうかを判断する必要があります。  
  
### <a name="applications-that-are-run-directly-at-the-command-prompt"></a>コマンド プロンプトで直接実行されるアプリケーション

クラスパスは、オペレーティング システムにおいて構成されます。 sqljdbc.jar、sqljdbc4.jar、または sqljdbc41.jar をシステムのクラスパスに追加します。 または、`java -classpath` オプションを使用して、アプリケーションを実行するクラスパスを Java コマンド ラインで指定することもできます。  
  
### <a name="applications-that-run-in-an-ide"></a>IDE で実行されるアプリケーション  

各 IDE ベンダーでは、クラスパスを自社の IDE に設定するためのさまざまな方法を用意しています。 クラスパスをオペレーティング システムで設定するだけでは動作しません。 sqljdbc.jar、sqljdbc4.jar、または sqljdbc41.jar を IDE クラスパスに追加する必要があります。  
  
### <a name="servlets-and-jsps"></a>サーブレットおよび JSP  

サーブレットや JSP は、Tomcat のようなサーブレット/JSP エンジンで実行されます。 クラスパスは、サーブレット/JSP エンジンのドキュメントに従って設定する必要があります。 クラスパスをオペレーティング システムで設定するだけでは動作しません。 一部のサーブレット/JSP エンジンでは、エンジンのクラスパスを設定するために使用できるセットアップ画面が用意されています。 この場合、正しい JDBC ドライバー用 JAR ファイルを既存のエンジン クラスパスに追加し、エンジンを再起動する必要があります。 この他の場合は、エンジンをインストールするときに lib のような特定のディレクトリに sqljdbc.jar、sqljdbc4.jar、または sqljdbc41.jar をコピーしてドライバーを配置することができます。 エンジン ドライバーのクラスパスは、エンジン固有の構成ファイルで指定することもできます。  
  
### <a name="enterprise-java-beans"></a>Enterprise Java Beans  

Enterprise Java Beans (EJB) は、EJB コンテナーで実行されます。 EJB コンテナーは、さまざまなベンダーから供給されています。 Java アプレットはブラウザー上で動作しますが、Web サーバーからダウンロードされます。 sqljdbc.jar、sqljdbc4.jar、または sqljdbc41.jar を Web サーバーのルートにコピーし、アプレットの [HTML archive] タブで JAR ファイル名を指定します。たとえば、`<applet ... archive=mssql-jdbc-***.jar>` のようになります。  
  
## <a name="making-a-simple-connection-to-a-database"></a>データベースへの単純な接続を行う

sqljdbc.jar クラス ライブラリを使用するアプリケーションでは、まず次のようにしてドライバーを登録する必要があります。  
  
`Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");`  

ドライバーが読み込まれるときに、接続 URL および DriverManager クラスの getConnection メソッドを使用して接続を確立することができます。

```java
String connectionUrl = "jdbc:sqlserver://localhost:1433;" +  
   "databaseName=AdventureWorks;user=MyUserName;password=*****;";  
Connection con = DriverManager.getConnection(connectionUrl);  
```

JDBC API 4.0 以降、JDBC ドライバーが自動的に読み込まれるように、`DriverManager.getConnection()` メソッドが改良されました。 したがって、ドライバーの Jar ライブラリを使用する場合は、アプリケーションから `Class.forName` メソッドを呼び出してドライバーの登録や読み込みを行う必要はありません。  
  
DriverManager クラスの getConnection メソッドが呼び出されたときに、一連の登録済みの JDBC ドライバーから適切なドライバーがあります。 sqljdbc4.jar、sqljdbc41.jar、または sqljdbc42.jar ファイルには含む"META-INF/services/java.sql.Driver"ファイルが含まれています、 **com.microsoft.sqlserver.jdbc.SQLServerDriver**登録済みのドライバーとして。 現在 Class.forName メソッドを使用してドライバーを読み込む仕様になっている既存のアプリケーションも正常に動作します。特に修正の必要はありません。  
  
> [!NOTE]  
> sqljdbc4.jar、sqljdbc41.jar、または sqljdbc42.jar のクラス ライブラリは、以前のバージョンの Java Runtime Environment (JRE) では使用できません。 参照してください[JDBC Driver のシステム要件](../../connect/jdbc/system-requirements-for-the-jdbc-driver.md)によってサポートされる JRE バージョンの一覧については、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]します。  

データ ソースに接続して、接続 URL を使用する方法の詳細については、次を参照してください。[接続 URL の構築](../../connect/jdbc/building-the-connection-url.md)と[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)します。  
  
## <a name="see-also"></a>参照  

[JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
