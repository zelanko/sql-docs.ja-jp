---
title: 接続の操作 |Microsoft ドキュメント
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
ms.assetid: cf8ee392-8a10-40a3-ae32-31c7b1efdd04
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 400b4adb2b4812c1eed0397b93b1a1e08d0b5b39
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="working-with-a-connection"></a>接続の操作
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  次のセクションに接続するさまざまな方法の例を提供する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースを使用して、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)のクラス、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]です。  
  
> [!NOTE]  
>  接続に問題がある場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]JDBC ドライバーを使用して、参照してください[接続のトラブルシューティング](../../connect/jdbc/troubleshooting-connectivity.md)その修正方法の推奨事項についてです。  
  
## <a name="creating-a-connection-by-using-the-drivermanager-class"></a>DriverManager クラスを使用した接続の作成  
 接続を作成するための最も簡単な方法、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースは、JDBC ドライバーの読み込みおよび次のように、DriverManager クラスの getConnection メソッドを呼び出します。  
  
```  
Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver");  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = DriverManager.getConnection(connectionUrl);  
```  
  
 この手法では、渡された URL で正常に接続できるドライバーを示す一覧から、最初の使用可能なドライバーを使用して、データベース接続を作成します。  
  
> [!NOTE]  
>  Sqljdbc4.jar クラス ライブラリを使用する場合、アプリケーションでは、明示的に登録または Class.forName メソッドを使用して、ドライバーを読み込みに必要はありません。 DriverManager クラスの getConnection メソッドを呼び出したときに、一連の登録済みの JDBC ドライバーから適切なドライバーがあります。 詳細については、「JDBC ドライバーの使用」を参照してください。  
  
## <a name="creating-a-connection-by-using-the-sqlserverdriver-class"></a>SQLServerDriver クラスを使用した接続の作成  
 使用して、データベース接続を作成するには、ドライバーの一覧で、特定のドライバーをドライバー マネージャーを指定する必要、[接続](../../connect/jdbc/reference/connect-method-sqlserverdriver.md)のメソッド、 [SQLServerDriver](../../connect/jdbc/reference/sqlserverdriver-class.md)クラスは、次のようにします。  
  
```  
Driver d = (Driver) Class.forName("com.microsoft.sqlserver.jdbc.SQLServerDriver").newInstance();  
String connectionUrl = "jdbc:sqlserver://localhost;database=AdventureWorks;integratedSecurity=true;"  
Connection con = d.connect(connectionUrl, new Properties());  
```  
  
## <a name="creating-a-connection-by-using-the-sqlserverdatasource-class"></a>SQLServerDataSource クラスを使用した接続の作成  
 使用して接続を作成する必要がある場合、 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)クラスを呼び出す前に、クラスのさまざまな setter メソッドを使用できます、 [getConnection](../../connect/jdbc/reference/getconnection-method.md)メソッドは、次のようにします。  
  
```  
SQLServerDataSource ds = new SQLServerDataSource();  
ds.setUser("MyUserName");  
ds.setPassword("*****");  
ds.setServerName("localhost");  
ds.setPortNumber(1433);   
ds.setDatabaseName("AdventureWorks");  
Connection con = ds.getConnection();  
```  
  
## <a name="creating-a-connection-that-targets-a-very-specific-data-source"></a>限定されたデータ ソースを対象とした接続の作成  
 限定されたデータ ソースを対象にデータベース接続を作成するには複数の方法があります。 それぞれの方法は、接続 URL を使用して設定するプロパティによって設定されます。  
  
 リモート サーバーの既定のインスタンスに接続するには、次の方法を使用します。  
  
 `String url = "jdbc:sqlserver://MyServer;integratedSecurity=true;"`  
  
 サーバーの特定のポートに接続するには、次の方法を使用します。  
  
 `String url = "jdbc:sqlserver://MyServer:1533;integratedSecurity=true;"`  
  
 サーバーの名前付きインスタンスに接続するには、次の方法を使用します。  
  
 `String url = "jdbc:sqlserver://209.196.43.19;instanceName=INSTANCE1;integratedSecurity=true;"`  
  
 サーバーの特定のデータベースに接続するには、次の方法を使用します。  
  
 `String url = "jdbc:sqlserver://172.31.255.255;database=AdventureWorks;integratedSecurity=true;"`  
  
 複数の接続 URL の例では、次を参照してください。[接続 URL の構築](../../connect/jdbc/building-the-connection-url.md)です。  
  
## <a name="creating-a-connection-with-a-custom-login-time-out"></a>カスタムのログイン タイムアウトを持つ接続の作成  
 サーバーの負荷またはネットワーク トラフィックを調整する必要がある場合は、次のように、特定のログイン タイムアウト値を秒数で指定した接続を作成できます。  
  
 `String url = "jdbc:sqlserver://MyServer;loginTimeout=90;integratedSecurity=true;"`  
  
## <a name="create-a-connection-with-application-level-identity"></a>アプリケーション レベルの ID を持つ接続の作成  
 ログとプロファイリングを使用する必要がある場合は、次のように、接続が特定のアプリケーションからのものであることを識別する必要があります。  
  
 `String url = "jdbc:sqlserver://MyServer;applicationName=MYAPP.EXE;integratedSecurity=true;"`  
  
## <a name="closing-a-connection"></a>接続を閉じる  
 明示的に呼び出すことによって、データベース接続を閉じることができます、[閉じる](../../connect/jdbc/reference/close-method-sqlserverconnection.md)次のように、SQLServerConnection クラスのメソッド。  
  
 `con.close();`  
  
 これは、SQLServerConnection オブジェクトが使用すると、データベース リソースを解放を返したり接続されるシナリオで、接続プールにします。  
  
> [!NOTE]  
>  Close メソッドを呼び出してもロールバックされます保留中のトランザクション。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる SQL Server への接続](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
