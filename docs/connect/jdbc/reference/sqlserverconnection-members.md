---
title: "SQLServerConnection のメンバー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3115a533-756b-4c78-aee9-4ba7253c85e0
caps.latest.revision: "25"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ac235e229d5156895c45d3e0ec705d0c2b84ca06
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="sqlserverconnection-members"></a>SQLServerConnection のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表に、によって公開されるメンバー、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)クラスです。  
  
## <a name="constructors"></a>コンス トラクター  
 [なし] :  
  
## <a name="fields"></a>フィールド  
  
|名前|Description|  
|----------|-----------------|  
|[TRANSACTION_SNAPSHOT](../../../connect/jdbc/reference/transaction-snapshot-field-sqlserverconnection.md)|スナップショット トランザクションの分離レベルを指定する場合に使用します。|  
  
## <a name="inherited-fields"></a>継承されたフィールド  
  
|継承元のクラス|Description|  
|---------------------------|-----------------|  
|java.sql.Connection|TRANSACTION_NONE、TRANSACTION_READ_COMMITTED、TRANSACTION_READ_UNCOMMITTED、TRANSACTION_REPEATABLE_READ、TRANSACTION_SERIALIZABLE|  
  
## <a name="methods"></a>メソッド  
  
|名前|Description|  
|----------|-----------------|  
|[clearWarnings](../../../connect/jdbc/reference/clearwarnings-method-sqlserverconnection.md)|この報告されたすべての警告をクリア[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。|  
|[閉じる](../../../connect/jdbc/reference/close-method-sqlserverconnection.md)|このデータベースを解放[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトと JDBC リソースを待たずにすぐに自動的に解放します。|  
|[コミット](../../../connect/jdbc/reference/commit-method-sqlserverconnection.md)|前回のコミットまたはロールバック以降を恒久的に、すべての変更が行われ、これによって現在保持されているデータベース ロックは解放[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。|  
|[createBlob](../../../connect/jdbc/reference/createblob-method-sqlserverconnection.md)|作成、 **java.sql.Blob**データを含まないオブジェクト。|  
|[createClob](../../../connect/jdbc/reference/createclob-method-sqlserverconnection.md)|作成、 **java.sql.Clob**データを含まないオブジェクト。|  
|[createNClob](../../../connect/jdbc/reference/createnclob-method-sqlserverconnection.md)|作成、 **java.sql.NClob**データを含まないオブジェクト。|  
|[createStatement](../../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md)|作成、 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)データベースに SQL ステートメントを送信するためのオブジェクト。|  
|[createSQLXML](../../../connect/jdbc/reference/createsqlxml-method-sqlserverconnection.md)|作成、 **java.sql.SQLXML**データを含まないオブジェクト。|  
|[getAutoCommit](../../../connect/jdbc/reference/getautocommit-method-sqlserverconnection.md)|この現在の自動コミット モードを取得[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。|  
|[getCatalog](../../../connect/jdbc/reference/getcatalog-method-sqlserverconnection.md)|この現在のカタログ名を取得する[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。|  
|[getClientConnectionID メソッド &#40;です。SQLServerConnection &#41;](../../../connect/jdbc/reference/getclientconnectionid-method-sqlserverconnection.md)|接続に成功したか失敗したかにかかわらず、直近に試行された接続の ID を取得します。|  
|[getClientInfo](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)|JDBC ドライバーでサポートされているクライアント情報のプロパティに関する情報を取得します。|  
|[getHoldability](../../../connect/jdbc/reference/getholdability-method-sqlserverconnection.md)|現在の保持機能を取得[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)これを使用して作成されるオブジェクト[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。|  
|[getMetaData](../../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md)|取得、 [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)先であるデータベースについてのメタデータを格納しているオブジェクト[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトが接続を表します。|  
|[getTransactionIsolation](../../../connect/jdbc/reference/gettransactionisolation-method-sqlserverconnection.md)|この現在のトランザクション分離レベルを取得[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。|  
|[getTypeMap](../../../connect/jdbc/reference/gettypemap-method-sqlserverconnection.md)|これに関連付けられているマップ オブジェクトを取得します[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。|  
|[getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md)|この呼び出しによって報告された最初の警告取得[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。|  
|[isClosed](../../../connect/jdbc/reference/isclosed-method-sqlserverconnection.md)|示すかどうかこの[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトが閉じられました。|  
|[isReadOnly](../../../connect/jdbc/reference/isreadonly-method-sqlserverconnection.md)|示すかどうかこの[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトは読み取り専用モードにします。|  
|[isValid](../../../connect/jdbc/reference/isvalid-method-sqlserverconnection.md)|示すかどうかこの[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトが閉じられていないは現在も有効です。|  
|[nativeSQL](../../../connect/jdbc/reference/nativesql-method-sqlserverconnection.md)|渡された SQL ステートメントを、データベース サーバーのネイティブな SQL 文法に変換します。|  
|[prepareCall](../../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md)|作成、 [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)データベースのストアド プロシージャを呼び出すためのオブジェクト。|  
|[prepareStatement](../../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md)|作成、 [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)化されたデータベースに SQL ステートメントを送信するためのオブジェクト。|  
|[releaseSavepoint](../../../connect/jdbc/reference/releasesavepoint-method-sqlserverconnection.md)|指定された削除[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)現在のトランザクションからのオブジェクト。|  
|[ロールバック](../../../connect/jdbc/reference/rollback-method-sqlserverconnection.md)|現在のトランザクションで行われたすべての変更が取り消され、これによって現在保持されているデータベース ロックは解放[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。|  
|[setAutoCommit](../../../connect/jdbc/reference/setautocommit-method-sqlserverconnection.md)|自動コミット モードを設定[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトを特定の状態にします。|  
|[setCatalog](../../../connect/jdbc/reference/setcatalog-method-sqlserverconnection.md)|このサブ空間を選択する指定したカタログ名を設定[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトのデータベースの作業を行う。|  
|[setClientInfo](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)|クライアント情報のプロパティの値を設定します。|  
|[setHoldability](../../../connect/jdbc/reference/setholdability-method-sqlserverconnection.md)|変更の保持機能[SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)これを使用して作成されるオブジェクト[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)指定の保持機能するオブジェクト。|  
|[setReadOnly](../../../connect/jdbc/reference/setreadonly-method-sqlserverconnection.md)|これは、 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクトをデータベースの最適化を有効にするには、JDBC driver にヒントとしての読み取り専用モードにします。|  
|[setSavepoint](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)|現在のトランザクションで、名前のないセーブポイントを作成し、新しい返します[SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md)を表すオブジェクト。|  
|[setTransactionIsolation](../../../connect/jdbc/reference/settransactionisolation-method-sqlserverconnection.md)|このトランザクションの分離レベルを変更しようとしています。 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)に指定されたオブジェクト。|  
|[setTypeMap](../../../connect/jdbc/reference/settypemap-method-sqlserverconnection.md)|この型マップとして指定された TypeMap オブジェクトをインストール[SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
|java.lang.Wrapper|isWrapperFor、unwrap|  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
