---
title: JDBC ドライバー API リファレンス |Microsoft Docs
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e4e1ae9d-18a6-41db-8bd2-9cf0eee4cccb
caps.latest.revision: 46
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a6949c49dc019e1dc7b9d875fb3ee7f38363a46
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785805"
---
# <a name="jdbc-driver-api-reference"></a>JDBC Driver API リファレンス

[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] が提供する API は Java プログラミング内で使用し、[!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに接続し、やりとりできます。



### <a name="javadocio-website-is-primary"></a>JavaDoc.io web サイトがプライマリ

JavaDoc.io web サイトに、表示する場合、Microsoft JDBC API のリファレンス ドキュメントがホストされています。 JavaDoc.io は JDBC リファレンス ドキュメントについては、プライマリ web サイトではようになりました。 JavaDoc.io で JDBC リファレンスのドキュメントは次の直接リンクでご利用いただけます。

- [https://javadoc.io/doc/com.microsoft.sqlserver/mssql-jdbc/](https://javadoc.io/doc/com.microsoft.sqlserver/mssql-jdbc/)

JavaDoc.io がバージョン 6.0 以降の JDBC リファレンス ドキュメントです。

#### <a name="only-legacy-jdbc-documentation-is-here-on-docs"></a>Docs でレガシ JDBC ドキュメントのみがここでは

JDBC API のリファレンス ドキュメントの記事では、ここ**https://docs.microsoft.com/sql/connect/jdbc/reference/** JDBC クラスの新しいリリースの更新時に不要になった更新中です。 ただし、こちらの記事は、JDBC バージョン 4.1 と 4.2 のすべての参照を含めることが操作を行います。

JDBC バージョン 6.0、およびいくつかの以降のバージョンのドキュメントがここではもします。 6.0 以降のバージョン、JavaDoc.io web サイトを使用します。



### <a name="important-notes"></a>重要な注意点

> [!NOTE]  
>  JDBC ドライバーを使用して概念については、次を参照してください。 [JDBC ドライバーの概要](../../../connect/jdbc/overview-of-the-jdbc-driver.md)します。  
  
> [!IMPORTANT]  
>  JDBC 4.1 と 4.2 のコンプライアンス サポートについては、Microsoft JDBC Driver 4.2 for SQL Server (以降) を使用します。 以前の Microsoft JDBC ドライバーの 4.1 リリースと 4.0 リリースの場合、JDBC 4.1 や 4.2 で導入された新しいメソッドに対応していません。  
>   
>  JDBC 4.1 コンプライアンスの API 詳細についてはこのセクションでは扱いません。 「[JDBC Driver の JDBC 4.1 への準拠](../../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md)」を参照してください。  
>   
>  JDBC 4.2 コンプライアンスの API 詳細についてはこのセクションでは扱いません。 「[JDBC Driver の JDBC 4.2 への準拠](../../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md)」を参照してください。  
>   
>  Microsoft JDBC Driver 4.2 for SQL Server より利用できる一括コピーの API 詳細についてはこのセクションでは扱いません。 「[JDBC ドライバーでの一括コピーの使用](../../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md)」を参照してください。  
>   
>  Microsoft JDBC Driver 6.0 for SQL Server より利用できる Always Encrypted の API 詳細についてはこのセクションでは扱いません。 「[JDBC ドライバーの Always Encrypted API のリファレンス](../../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)」を参照してください。  
>   
>  このセクションでは、SQL Server 用 Microsoft JDBC Driver 6.0 以降使用可能な Using Table-Valued パラメーターの API 詳細については見つかりませんでした。 「[テーブル値パラメーターの使用](../../../connect/jdbc/using-table-valued-parameters.md)」を参照してください。  
>   
>  Microsoft JDBC ドライバー 6.4 は JDK 7.0、8.0、および 9.0 によるコンパイルに対応しています。  
>   
>  Microsoft JDBC ドライバー 6.2 は JDK 7.0 と 8.0 によるコンパイルに対応しています。  
>   
>  Microsoft JDBC ドライバー 6.0 と 4.2 は JDK 5.0、6.0、7.0、および 8.0 によるコンパイルに対応しています。  
>   
>  Microsoft JDBC ドライバー 4.1 は JDK 5.0、6.0、7.0 によるコンパイルに対応しています。  



## <a name="interfaces"></a>インターフェイス  
  
|インターフェイス名|[説明]|  
|--------------------|-----------------|  
|[ISQLServerCallableStatement インターフェイス](../../../connect/jdbc/reference/isqlservercallablestatement-interface.md)|入力パラメーターおよび出力パラメーターと共に、呼び出すストアド プロシージャの名前を指定できます。|  
|[ISQLServerConnection インターフェイス](../../../connect/jdbc/reference/isqlserverconnection-interface.md)|[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースへの JDBC 接続を表します。|  
|[SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)|[ISQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) オブジェクトを利用した [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースへの接続に固有のプロパティの一覧を表します。|  
|[ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)|JDBC の準備されたステートメント機能の基本的な実装を表します。|  
|[ISQLServerResultSet](../../../connect/jdbc/reference/isqlserverresultset-interface.md)|JDBC 結果セットを表します。|  
|[ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)|JDBC ステートメント機能の基本的な実装を表します。|
| &nbsp; | &nbsp; |


  
## <a name="classes"></a>クラス  
  
|クラス名|[説明]|  
|----------------|-----------------|  
|[DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)|microsoft.sql.DateTimeOffset 型のオブジェクトを表します。|  
|[SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)|BLOB (binary large object) を表します。|  
|[SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)|ISQLServerCallableStatement を実装します。|  
|[SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)|CLOB (character large binary object) を表します。|  
|[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)|ISQLServerConnectopn を実装します。|  
|[SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)|接続プール マネージャーの物理データベース接続を表します。|  
|[SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)|データベースのメタデータを表します。|  
|[SQLServerDataSource](../../../connect/jdbc/reference/isqlserverdatasource-interface.md)|[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) オブジェクトを利用した [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースへの接続に固有のプロパティの一覧を表します。|  
|[SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)|JNDI (Java Naming and Directory Interface) からのデータ ソースを生成するオブジェクト ファクトリを表します。|  
|[SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)|JDBC ドライバーを表します。 このクラスには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースに接続し、JDBC ドライバーに関する情報を取得するためのメソッドが含まれます。|  
|[SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)|SQL ステートメントの実行に失敗したこと、または実行が完了しなかったことを表します。|  
|[SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)|National Character Set を使用する文字ラージ バイナリ オブジェクトを表します。|  
|[SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)|準備されたステートメントのパラメーターのメタデータを表します。|  
|[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)|接続プール内の物理データベース接続を表します。|  
|[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)|ISQLServerPreparedStatement を実装します。|  
|[SQLServerResource](../../../connect/jdbc/reference/sqlserverresource-class.md)|ローカライズされたエラー文字列リソースを表します。 このクラスは内部でのみ使用されます。|  
|[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)|ISQLServerResultSet を実装します。|  
|[SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)|結果セットに含まれる列のメタデータを表します。|  
|[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)|トランザクションのロールバックが可能なチェックポイントを表します。|  
|[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)|ISQLServerStatement を実装します。|  
|[SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)|分散 (XA) トランザクションに参加できる JDBC 接続を表します。|  
|[SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)|内部で使用されている [SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md) オブジェクトのファクトリを表します。|  
|[SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)|XA 分散トランザクション管理用の XAResource を表します。|
| &nbsp; | &nbsp; |



## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../../connect/jdbc/overview-of-the-jdbc-driver.md)

