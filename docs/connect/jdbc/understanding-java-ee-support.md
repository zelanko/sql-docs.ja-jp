---
title: Java EE のサポートについて |Microsoft Docs
ms.custom: ''
ms.date: 02/06/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a9448b80-b7a3-49cf-8bb4-322c73676005
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ae55a5bc677c70d2a1f998e235031ac9bafd5aba
ms.sourcegitcommit: c61c7b598aa61faa34cd802697adf3a224aa7dc4
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56154617"
---
# <a name="understanding-java-ee-support"></a>Java EE のサポートについて

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

以下のセクションでは、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] が Java Platform, Enterprise Edition (Java EE) および JDBC 3.0 のオプションの API 機能をサポートするしくみについて説明します。 このヘルプ システムで提供されるソース コード例は、これらの機能を使用するための優れた参考資料となります。  
  
まず、使用している Java 環境 (JDK、JRE) に javax.sql パッケージが含まれていることを確認してください。 このパッケージは、オプションの API を使用するすべての JDBC アプリケーションに必須です。 JDK 1.5 以降のバージョンには、このパッケージが既に含まれているので、別途インストールする必要はありません。  
  
## <a name="driver-name"></a>ドライバー名

このドライバーのクラス名は、**com.microsoft.sqlserver.jdbc.SQLServerDriver** です。 JDBC Driver 4.1、4.2、6.0 の場合、このドライバーは **sqljdbc.jar**、**sqljdbc4.jar**、**sqljdbc41.jar**、または **sqljdbc42.jar** ファイルに含まれています。

JDBC Driver 6.2、ドライバーが含まれている**mssql-jdbc-6.2.2.jre7.jar**または**mssql-jdbc-6.2.2.jre8.jar**します。

JDBC Driver 6.4 では、ドライバーが含まれている**mssql-jdbc-6.4.0.jre7.jar**、 **mssql-jdbc-6.4.0.jre8.jar**、または**mssql-jdbc-6.4.0.jre9.jar**します。

JDBC ドライバーの 7.0 のドライバーが含まれている**mssql-jdbc-7.0.0.jre8.jar**、または**mssql-jdbc-7.0.0.jre10.jar**します。

JDBC ドライバーの 7.2 のドライバーが含まれている**mssql-jdbc-7.2.1.jre8.jar**、または**mssql-jdbc-7.2.1.jre11.jar**します。
  
このクラス名は、JDBC DriverManager クラスを使用してドライバーを読み込むたびに使用されます。 また、ドライバー構成でドライバーのクラス名を指定する必要があるときにも使用されます。 たとえば、Java EE アプリケーション サーバー内でデータ ソースを構成するには、ドライバーのクラス名を入力する必要が生じる場合があります。  
  
## <a name="data-sources"></a>ソリューション エクスプローラー

この JDBC ドライバーは、Java EE または JDBC 3.0 データ ソースをサポートします。 JDBC driver [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md)によってクラスが実装されている`com.microsoft.sqlserver.jdbc.SQLServerXADataSource`します。  
  
### <a name="datasource-names"></a>データ ソース名

データ ソースを使用して、データベース接続を確立できます。 次の表は、JDBC ドライバーで使用できるデータ ソースを示しています。  
  
|データ ソースの種類|クラスの名前と説明|  
|---------------|--------------------------|  
|DataSource|`com.microsoft.sqlserver.jdbc.SQLServerDataSource` <br/> <br/> 非プーリング データ ソース。|  
|ConnectionPoolDataSource|`com.microsoft.sqlserver.jdbc.SQLServerConnectionPoolDataSource` <br/> <br/> JAVA EE アプリケーション サーバー接続プールを構成するデータ ソース。 通常は、アプリケーションが JAVA EE アプリケーション サーバー内で実行される場合に使用されます。|  
|XADataSource|`com.microsoft.sqlserver.jdbc.SQLServerXADataSource` <br/> <br/> JAVA EE XA データ ソースを構成するデータ ソース。 通常は、アプリケーションが JAVA EE アプリケーション サーバーおよび XA トランザクション マネージャー内で実行される場合に使用されます。|  
  
### <a name="data-source-properties"></a>データ ソースのプロパティ

すべてのデータ ソースは、基になるドライバーのプロパティ セットに関連付けられているプロパティを設定または取得する機能をサポートします。  
  
例 :  
  
`setServerName("localhost");`  
`setDatabaseName("AdventureWorks");`  
  
以下は、アプリケーションがデータ ソースを使用して接続するしくみを示しています。  

```java
//initialize JNDI ..  
Context ctx = new InitialContext(System.getProperties());
...
DataSource ds = (DataSource) ctx.lookup("MyDataSource");
Connection c = ds.getConnection("user", "pwd");  
```

データ ソースのプロパティの詳細については、次を参照してください。[データ ソースのプロパティを設定](../../connect/jdbc/setting-the-data-source-properties.md)します。  
  
## <a name="see-also"></a>参照

[JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
