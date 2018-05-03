---
title: ドライバー操作のトレース |Microsoft ドキュメント
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
ms.assetid: 723aeae7-6504-4585-ba8b-3525115bea8b
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1df1fbf986714ad81c5879673213b84f8f6be8ce
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="tracing-driver-operation"></a>ドライバー操作のトレース」を参照してください。
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]アプリケーションで使用されているときに、JDBC ドライバーでの問題やエラーを解決するために、トレース (またはログ) の使用をサポートします。 トレースの使用を有効にするのには、JDBC ドライバーは、Logger と LogRecord オブジェクトを作成するための一連のクラスを提供する java.util.logging でログ記録 Api を使用します。  
  
> [!NOTE]  
>  JDBC Driver に含まれているネイティブのコンポーネント sqljdbc_xa.dll については、Built-In Diagnostics (BID) フレームワークを使用してトレースを有効にしています。 BID の詳細については、次を参照してください。 [SQL Server では、データ アクセスのトレース](http://go.microsoft.com/fwlink/?LinkId=70042)です。  
  
 アプリケーションを開発するときに、順番に渡されてハンドラー オブジェクトの処理、LogRecord オブジェクトを作成するロガー オブジェクトへの呼び出しを行うことができます。 オブジェクトによってログ記録レベルを両方使用されるロガーとハンドラーとをどの LogRecords を制御するためのログ記録フィルターの処理オプションでします。 ログ記録操作が完了したら、ハンドラー オブジェクトがログ情報を公開するのにフォーマッタ オブジェクトを使用できます必要に応じて。  
  
 既定では、java.util.logging フレームワークは出力をファイルに書き込みます。 この出力ログ ファイルは、JDBC Driver が動作しているコンテキストについて書き込みアクセス許可を持つ必要があります。  
  
> [!NOTE]  
>  プログラムをトレースするためのさまざまなログ記録オブジェクトの使用の詳細については、Sun Microsystems の Web サイトで Java ログ記録 API についてのドキュメント (英語ページの可能性があります) を参照してください。  
  
 次のセクションでは、ログ記録のレベルおよびログ記録可能なカテゴリについて説明し、アプリケーションでトレースを有効にする方法についての情報を提供します。  
  
## <a name="logging-levels"></a>ログ記録のレベル  
 作成されるすべてのログ メッセージは、ログ記録のレベルと関連付けられています。 ログ記録レベルで定義されているログ メッセージの重要度を決定する、**レベル**java.util.logging クラスです。 あるレベルでログ記録を有効にすると、それより上のすべてのレベルでログ記録が有効になります。 このセクションでは、ログ記録のパブリックなカテゴリと内部的なカテゴリの両方を対象に、ログ記録のレベルについて説明します。 ログ記録カテゴリの詳細については、このトピックの「ログ記録のカテゴリ」を参照してください。  
  
 次の表では、パブリックなログ記録のカテゴリで利用可能なログ記録の各レベルについて説明します。  
  
|名前|Description|  
|----------|-----------------|  
|SEVERE|重大なエラーを示す、最高レベルのログ記録です。 JDBC Driver では、このレベルはエラーや例外の報告に使用されます。|  
|WARNING|問題が発生する可能性があることを示します。|  
|INFO|情報としてのメッセージを提供します。|  
|CONFIG|構成に関するメッセージを提供します。 ただし、現時点では JDBC Driver から構成メッセージは一切提供されません。|  
|FINE|パブリック メソッドによってスローされるすべての例外を含め、基本的なトレース情報を提供します。|  
|FINER|パブリック メソッドのすべての開始ポイントと終了ポイント、関連するパラメーターのデータ型、パブリック クラスのすべてのパブリック プロパティなど、詳細なトレース情報を提供します。 さらに、入力パラメーター、出力パラメーター、およびメソッドの戻り値を除き、CLOB、BLOB、NCLOB、Reader、\<ストリーム > 値の型を返します。|  
|FINEST|より詳細なトレース情報を提供します。 これは最低レベルのログ記録です。|  
|OFF|ログ記録をオフにします。|  
|ALL|すべてのメッセージのログ記録を有効にします。|  
  
 次の表では、内部的なログ記録のカテゴリで利用可能なログ記録の各レベルについて説明します。  
  
|名前|Description|  
|----------|-----------------|  
|SEVERE|重大なエラーを示す、最高レベルのログ記録です。 JDBC Driver では、このレベルはエラーや例外の報告に使用されます。|  
|WARNING|問題が発生する可能性があることを示します。|  
|INFO|情報としてのメッセージを提供します。|  
|FINE|基本的なオブジェクトの作成と破棄など、各種のトレース情報を提供します。 パブリック メソッドによってスローされるすべての例外も含まれます。|  
|FINER|パブリック メソッドのすべての開始ポイントと終了ポイント、関連するパラメーターのデータ型、パブリック クラスのすべてのパブリック プロパティなど、詳細なトレース情報を提供します。 さらに、入力パラメーター、出力パラメーター、およびメソッドの戻り値を除き、CLOB、BLOB、NCLOB、Reader、\<ストリーム > 値の型を返します。<br /><br /> 次のログ記録のカテゴリがバージョン 1.2 の JDBC driver が存在し、問題のログ記録レベルを必要がある: [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)、XA、および[SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md). これらは、バージョン 2.0 リリース以降で FINER レベルにアップグレードされています。|  
|FINEST|より詳細なトレース情報を提供します。 これは最低レベルのログ記録です。<br /><br /> バージョン 1.2 の JDBC Driver には、TDS.DATA および TDS.TOKEN というログ記録カテゴリが存在し、いずれも FINEST のログ記録レベルが割り当てられていました。 バージョン 2.0 リリース以降でも、ログ記録レベルは FINEST から変更されていません。|  
|OFF|ログ記録をオフにします。|  
|ALL|すべてのメッセージのログ記録を有効にします。|  
  
## <a name="logging-categories"></a>ログ記録のカテゴリ  
 ロガー オブジェクトを作成するときは、どの名前付きエンティティまたはカテゴリからログ情報を取得しているオブジェクトを指定する必要があります。 JDBC Driver は、パブリックなログ記録のカテゴリとして、次のカテゴリをサポートします。いずれも com.microsoft.sqlserver.jdbc ドライバー パッケージで定義されています。  
  
|名前|Description|  
|----------|-----------------|  
|接続|メッセージを記録、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINER として設定できます。|  
|ステートメントから削除してください。|メッセージを記録、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINER として設定できます。|  
|DataSource|メッセージを記録、 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE として設定できます。|  
|ResultSet|メッセージを記録、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINER として設定できます。|  
|Driver|メッセージを記録、 [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINER として設定できます。|  
  
 Microsoft JDBC Driver Version 2.0 以降では、さらに com.microsoft.sqlserver.jdbc.internals パッケージが用意されており、内部的なログ記録のカテゴリとして、次のカテゴリがサポートされています。  
  
|名前|Description|  
|----------|-----------------|  
|AuthenticationJNI|Windows に関連するログ メッセージは統合認証の問題 (ときに、 **authenticationScheme**接続プロパティが暗黙的または明示的に設定**NativeAuthentication**)。<br /><br /> アプリケーションは、ログ記録レベルを FINEST および FINE として設定できます。|  
|SQLServerConnection|メッセージを記録、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE および FINER として設定できます。|  
|SQLServerDataSource|メッセージを記録、 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)、 [SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)、および[SQLServerPooledConnection](../../connect/jdbc/reference/sqlserverpooledconnection-class.md)クラスです。<br /><br /> アプリケーションは、ログ記録レベルを FINER として設定できます。|  
|InputStream|java.io.InputStream、java.io.Reader のほか、max 指定子を持つデータ型 (varchar、nvarchar、varbinary など) に関するメッセージを記録します。<br /><br /> アプリケーションは、ログ記録レベルを FINER として設定できます。|  
|SQLServerException|メッセージを記録、 [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE として設定できます。|  
|SQLServerResultSet|メッセージを記録、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE、FINER、および FINEST として設定できます。|  
|SQLServerStatement|メッセージを記録、 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE、FINER、および FINEST として設定できます。|  
|XA|すべての XA トランザクションについてメッセージを記録、 [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE および FINER として設定できます。|  
|KerbAuthentication|タイプ 4 Kerberos 認証に関するメッセージをログに記録 (ときに、 **authenticationScheme**接続プロパティに設定**java Kerberos**)。 アプリケーションは、ログ記録レベルを FINE または FINER として設定できます。|  
|TDS.DATA|ドライバーと SQL Server の間で交わされる TDS プロトコル レベルのメッセージ交換を含んだメッセージを記録します。 送受信される各 TDS パケットの詳細な内容が ASCII および 16 進形式で記録されます。 ログイン資格情報 (ユーザー名とパスワード) は記録されません。 それ以外のすべてのデータが記録されます。<br /><br /> このカテゴリは非常に冗長で詳細なメッセージを作成します。ログ記録のレベルを FINEST に設定したときにのみ有効になります。|  
|TDS.Channel|SQL Server との TCP 通信チャネルのアクションをトレースします。 記録されるメッセージには、読み取りや書き込みのほか、ソケットの開閉が含まれます。 SQL Server との SSL (Secure Sockets Layer) 接続の確立に関連したメッセージもトレースされます。<br /><br /> このカテゴリは、ログ記録レベルを FINE、FINER、または FINEST に設定したときにのみ有効になります。|  
|TDS.Writer|TDS チャネルへの書き込みをトレースします。 トレースされるのは書き込みの長さのみです。書き込みの内容がトレースされるわけではありません。 このカテゴリでは、アテンション シグナルがサーバーに送信され、ステートメントの実行がキャンセルされた場合にも、問題がトレースされます。<br /><br /> このカテゴリは、ログ記録レベルを FINEST に設定したときにのみ有効になります。|  
|TDS.Reader|TDS チャネルからの特定の読み取り操作を FINEST レベルでトレースします。 FINEST レベルのトレースは、非常に冗長になる場合があります。 WARNING レベルや SEVERE レベルでは、ドライバーが接続を閉じる前に SQL Server から無効な TDS プロトコルを受信した場合にトレースが行われます。<br /><br /> このカテゴリは、ログ記録レベルを FINER または FINEST に設定したときにのみ有効になります。|  
|TDS.Command|このカテゴリは、低レベルの状態遷移やなど、TDS コマンドの実行に関連付けられているその他の情報をトレース[!INCLUDE[tsql](../../includes/tsql_md.md)]ステートメントの実行、ResultSet カーソルのフェッチ、コミット、およびなどです。<br /><br /> このカテゴリは、ログ記録レベルを FINEST に設定したときにのみ有効になります。|  
|TDS.TOKEN|このカテゴリは、TDS パケット内のトークンのみを記録しますが、TDS.DATA カテゴリほど冗長ではありません。 ログ記録レベルを FINEST に設定したときにのみ有効になります。<br /><br /> FINEST レベルでは、応答で処理される TDS トークンがトレースされます。 SEVERE レベルでは、無効な TDS トークンが検出された場合にトレースが実行されます。|  
|SQLServerDatabaseMetaData|メッセージを記録、 [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE として設定できます。|  
|SQLServerResultSetMetaData|メッセージを記録、 [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE として設定できます。|  
|SQLServerParameterMetaData|メッセージを記録、 [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE として設定できます。|  
|SQLServerBlob|メッセージを記録、 [SQLServerBlob](../../connect/jdbc/reference/sqlserverblob-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE として設定できます。|  
|SQLServerClob|メッセージを記録、 [SQLServerClob](../../connect/jdbc/reference/sqlserverclob-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE として設定できます。|  
|SQLServerSQLXML|内部 SQLServerSQLXML クラスでは、メッセージを記録します。 アプリケーションは、ログ記録レベルを FINE として設定できます。|  
|SQLServerDriver|メッセージを記録、 [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE として設定できます。|  
|SQLServerNClob|メッセージを記録、 [SQLServerNClob](../../connect/jdbc/reference/sqlservernclob-class.md)クラスです。 アプリケーションは、ログ記録レベルを FINE として設定できます。|  
  
## <a name="enabling-tracing-programmatically"></a>プログラムによるトレースの有効化  
 トレースを有効にするプログラムでロガー オブジェクトを作成し、カテゴリを示すログに記録します。 たとえば、次のコードは SQL ステートメントのログ記録を有効にする方法を示しています。  
  
```  
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc.Statement");  
logger.setLevel(Level.FINER);  
```  
  
 コードの中でログ記録を無効にするには、次のようにします。  
  
```  
logger.setLevel(Level.OFF);  
```  
  
 利用可能なすべてのカテゴリをログ記録するには、次のようにします。  
  
```  
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc");  
logger.setLevel(Level.FINE);  
```  
  
 特定のカテゴリのログ記録を無効にするには、次のようにします。  
  
```  
Logger logger = Logger.getLogger("com.microsoft.sqlserver.jdbc.Statement");  
logger.setLevel(Level.OFF);  
```  
  
## <a name="enabling-tracing-by-using-the-loggingproperties-file"></a>Logging.Properties ファイルを使用してトレースを有効にする  
 使用してトレースを有効にすることもできます、`logging.properties`は含まれているファイル、`lib`の Java ランタイム環境 (JRE) のインストールのディレクトリ。 このファイルを使用すると、トレースが有効になったときに使用されるロガーやハンドラーに既定値を設定することができます。  
  
 次の例に示しますで行うことができます、設定、`logging.properties`ファイル。  
  
```  
# Specify the handler, the handlers will be installed during VM startup.  
handlers= java.util.logging.FileHandler  
  
# Default global logging level.  
.level= OFF  
  
# default file output is in user's home directory.  
java.util.logging.FileHandler.pattern = %h/java%u.log  
java.util.logging.FileHandler.limit = 5000000  
java.util.logging.FileHandler.count = 20  
java.util.logging.FileHandler.formatter = java.util.logging.SimpleFormatter  
java.util.logging.FileHandler.level = FINEST  
  
# Facility specific properties.  
com.microsoft.sqlserver.jdbc.level=FINEST  
  
```  
  
> [!NOTE]  
>  プロパティを設定することができます、 `logging.properties` java.util.logging に含まれている LogManager オブジェクトを使用してファイル。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーで発生した問題の診断](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  
