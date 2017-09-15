---
title: "JDBC ドライバー API リファレンス |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4e1ae9d-18a6-41db-8bd2-9cf0eee4cccb
caps.latest.revision: 46
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c19740d1247fa1fd7fe8036fa2aa557e01e74c82
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="jdbc-driver-api-reference"></a>JDBC Driver API リファレンス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] API を提供する Java 内で使用できるプログラミング コードへの接続し、対話する、 [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データベース。  
  
> [!NOTE]  
>  JDBC ドライバーの使用に関する概念については、次を参照してください。 [JDBC ドライバーの概要](../../../connect/jdbc/overview-of-the-jdbc-driver.md)です。  
  
> [!IMPORTANT]  
>  JDBC 4.1 と 4.2 のコンプライアンス サポートは、Microsoft JDBC Driver 4.2 (またはそれ以降) を使用して SQL Server 用です。 以前の Microsoft JDBC ドライバーの 4.1 リリースと 4.0 リリースの場合、JDBC 4.1 や 4.2 で導入された新しいメソッドに対応していません。  
>   
>  JDBC 4.1 コンプライアンスの API 詳細についてはこのセクションでは扱いません。 参照してください[JDBC 4.1 準拠、JDBC driver](../../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md)です。  
>   
>  JDBC 4.2 コンプライアンスの API 詳細についてはこのセクションでは扱いません。 参照してください[JDBC 4.2 準拠、JDBC driver](../../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md)です。  
>   
>  Microsoft JDBC Driver 4.2 for SQL Server から利用できるように、一括コピーの API 詳細については、このセクションの内容が見つかりません。 参照してください[JDBC ドライバーで一括コピーを使用して](../../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md)です。  
>   
>  Always Encrypted を使用できる Microsoft JDBC Driver 6.0 for SQL Server 以降の API 詳細については、このセクションの内容が見つかりません。 参照してください[Always Encrypted の JDBC ドライバー API リファレンス](../../../connect/jdbc/always-encrypted-api-reference-for-the-jdbc-driver.md)  
>   
>  Microsoft JDBC Driver 6.0 for SQL Server 以降使用可能な Using Table-Valued パラメーターの API 詳細については、このセクションの内容が見つかりません。 参照してください[テーブル値パラメーターの使用](../../../connect/jdbc/using-table-valued-parameters.md)  
>   
>  Microsoft JDBC Drivers 6.0 と JDK 5.0、6.0、7.0、8.0 によるコンパイルに 4.2 対応します。  
>   
>  Microsoft JDBC ドライバー 4.1 は JDK 5.0、6.0、7.0 によるコンパイルに対応しています。  
>   
>  Microsoft JDBC ドライバー 4.0 は JDK 5.0 と 6.0 によるコンパイルに対応しています。  
  
## <a name="interfaces"></a>インターフェイス  
  
|インターフェイス名|Description|  
|--------------------|-----------------|  
|[ISQLServerCallableStatement インターフェイス](../../../connect/jdbc/reference/isqlservercallablestatement-interface.md)|入力パラメーターおよび出力パラメーターと共に、呼び出すストアド プロシージャの名前を指定できます。|  
|[ISQLServerConnection インターフェイス](../../../connect/jdbc/reference/isqlserverconnection-interface.md)|JDBC の接続を表し、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データベース。|  
|[SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)|接続に固有のプロパティの一覧を表す、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データベースを使用して、 [ISQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。|  
|[ISQLServerPreparedStatement](../../../connect/jdbc/reference/isqlserverpreparedstatement-interface.md)|JDBC の準備されたステートメント機能の基本的な実装を表します。|  
|[ISQLServerResultSet](../../../connect/jdbc/reference/isqlserverresultset-interface.md)|JDBC 結果セットを表します。|  
|[ISQLServerStatement](../../../connect/jdbc/reference/isqlserverstatement-interface.md)|JDBC ステートメント機能の基本的な実装を表します。|  
  
## <a name="classes"></a>クラス  
  
|クラス名|Description|  
|----------------|-----------------|  
|[DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)|microsoft.sql.DateTimeOffset 型のオブジェクトを表します。|  
|[SQLServerBlob](../../../connect/jdbc/reference/sqlserverblob-class.md)|BLOB (binary large object) を表します。|  
|[SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)|ISQLServerCallableStatement を実装します。|  
|[SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-class.md)|CLOB (character large binary object) を表します。|  
|[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)|ISQLServerConnectopn を実装します。|  
|[SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)|接続プール マネージャーの物理データベース接続を表します。|  
|[SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)|データベースのメタデータを表します。|  
|[SQLServerDataSource](../../../connect/jdbc/reference/isqlserverdatasource-interface.md)|接続に固有のプロパティの一覧を表す、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データベースを使用して、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。|  
|[SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-class.md)|JNDI (Java Naming and Directory Interface) からのデータ ソースを生成するオブジェクト ファクトリを表します。|  
|[SQLServerDriver](../../../connect/jdbc/reference/sqlserverdriver-class.md)|JDBC ドライバーを表します。 このクラスに接続するためのメソッドが含まれています、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]データベース、および JDBC ドライバーに関する情報を取得するためです。|  
|[SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)|SQL ステートメントの実行に失敗したこと、または実行が完了しなかったことを表します。|  
|[SQLServerNClob クラス](../../../connect/jdbc/reference/sqlservernclob-class.md)|Character large binary object National Character Set を使用してを表します。|  
|[SQLServerParameterMetaData](../../../connect/jdbc/reference/sqlserverparametermetadata-class.md)|準備されたステートメントのパラメーターのメタデータを表します。|  
|[SQLServerPooledConnection](../../../connect/jdbc/reference/sqlserverpooledconnection-class.md)|接続プール内の物理データベース接続を表します。|  
|[SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)|ISQLServerPreparedStatement を実装します。|  
|[SQLServerResource](../../../connect/jdbc/reference/sqlserverresource-class.md)|ローカライズされたエラー文字列リソースを表します。 このクラスは内部でのみ使用されます。|  
|[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)|ISQLServerResultSet を実装します。|  
|[SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)|結果セットに含まれる列のメタデータを表します。|  
|[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)|トランザクションのロールバックが可能なチェックポイントを表します。|  
|[SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)|ISQLServerStatement を実装します。|  
|[SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)|分散 (XA) トランザクションに参加できる JDBC 接続を表します。|  
|[SQLServerXADataSource](../../../connect/jdbc/reference/sqlserverxadatasource-class.md)|ファクトリを表します[SQLServerXAConnection](../../../connect/jdbc/reference/sqlserverxaconnection-class.md)内部的に使用されるオブジェクト。|  
|[SQLServerXAResource](../../../connect/jdbc/reference/sqlserverxaresource-class.md)|XA の XAResource を表しますは分散トランザクション管理です。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
