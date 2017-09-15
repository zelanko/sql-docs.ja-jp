---
title: "SQLServerDataSource のメンバー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e749bc5-d765-4864-be2b-7822d4c20c09
caps.latest.revision: 43
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: eb9919441a3e20fdb02753258e134ba7bedb0ce0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverdatasource-members"></a>SQLServerDataSource のメンバー
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  次の表に、によって公開されるメンバー、 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)クラスです。  
  
## <a name="constructors"></a>コンス トラクター  
  
|名前|Description|  
|----------|-----------------|  
|[SQLServerDataSource)](../../../connect/jdbc/reference/sqlserverdatasource-constructor.md)|新しいインスタンスを初期化、 [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)クラスです。|  
  
## <a name="fields"></a>フィールド  
 [なし] :  
  
## <a name="inherited-fields"></a>継承されたフィールド  
 [なし] :  
  
## <a name="methods"></a>メソッド  
  
|名前|Description|  
|----------|-----------------|  
|[getApplicationIntent](../../../connect/jdbc/reference/getapplicationintent-method-sqlserverdatasource.md)|値を返します、 **applicationIntent**接続プロパティです。|  
|[getApplicationName](../../../connect/jdbc/reference/getapplicationname-method-sqlserverdatasource.md)|アプリケーション名を返します。|  
|[getConnection](../../../connect/jdbc/reference/getconnection-method-sqlserverdatasource.md)|このソースのデータとの接続を確立するために試行[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクトを表します。|  
|[getDatabaseName](../../../connect/jdbc/reference/getdatabasename-method-sqlserverdatasource.md)|データベース名を返します。|  
|[getEncrypt](../../../connect/jdbc/reference/getencrypt-method-sqlserverdatasource.md)|返します、**ブール**encrypt プロパティが有効になっているかどうかを示す値。|  
|[getDescription](../../../connect/jdbc/reference/getdescription-method-sqlserverdatasource.md)|データ ソースの記述を返します。|  
|[getFailoverPartner](../../../connect/jdbc/reference/getfailoverpartner-method-sqlserverdatasource.md)|データベース ミラーリング構成で使用されるフェールオーバー サーバーの名前を返します。|  
|[getHostNameInCertificate](../../../connect/jdbc/reference/gethostnameincertificate-method-sqlserverdatasource.md)|SQL Server の SSL (Secure Sockets Layer) 証明書の検証に使用されるホスト名を返します。|  
|[getInstanceName](../../../connect/jdbc/reference/getinstancename-method-sqlserverdatasource.md)|返します、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]インスタンス名。|  
|[getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md)|返します、**ブール**lastUpdateCount プロパティが有効になっているかどうかを示す値。|  
|[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md)|返します、 **int**データベースがロック タイムアウトを報告する前に待機するミリ秒数を示す値。|  
|[getLoginTimeout](../../../connect/jdbc/reference/getlogintimeout-method-sqlserverdatasource.md)|この秒数を返します[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクトが接続を確立中に待機します。|  
|[getLogWriter](../../../connect/jdbc/reference/getlogwriter-method-sqlserverdatasource.md)|すべてのログ メッセージとトレース メッセージで使用される文字出力ストリームを返します。|  
|[getMultiSubnetFailover](../../../connect/jdbc/reference/getmultisubnetfailover-method-sqlserverdatasource.md)|値を返します、 **multiSubnetFailover**接続プロパティです。|  
|[getPacketSize](../../../connect/jdbc/reference/getpacketsize-method-sqlserverdatasource.md)|通信するために使用される現在のネットワーク パケット サイズを返します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]、バイト単位で指定します。|  
|[getPortNumber](../../../connect/jdbc/reference/getportnumber-method-sqlserverdatasource.md)|通信するために使用される現在のポート番号を返します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。|  
|[getReference](../../../connect/jdbc/reference/getreference-method-sqlserverdatasource.md)|この参照を返します[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクト。|  
|[getResponseBuffering](../../../connect/jdbc/reference/getresponsebuffering-method-sqlserverdatasource.md)|このモードをバッファリング応答を返します[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクト。|  
|[getSelectMethod](../../../connect/jdbc/reference/getselectmethod-method-sqlserverdatasource.md)|これを使用して作成されたすべての結果セットを使用する既定のカーソルの種類を返します[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクト。|  
|[getSendStringParametersAsUnicode](../../../connect/jdbc/reference/getsendstringparametersasunicode-method-sqlserverdatasource.md)|返します、**ブール**文字列パラメーターを UNICODE 形式でサーバーに送信が有効になっているかどうかを示す値。|  
|[getSendTimeAsDatetime](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|設定値を返します、 **SendTimeAsDatetime**接続プロパティです。|  
|[getServerName](../../../connect/jdbc/reference/getservername-method-sqlserverdatasource.md)|実行するコンピューターの名前を返します[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。|  
|[getTrustServerCertificate](../../../connect/jdbc/reference/gettrustservercertificate-method-sqlserverdatasource.md)|返します、**ブール**trustServerCertificate プロパティが有効になっているかどうかを示す値。|  
|[getTrustStore](../../../connect/jdbc/reference/gettruststore-method-sqlserverdatasource.md)|証明書の trustStore ファイルへのパス (ファイル名を含む) を返します。|  
|[getURL](../../../connect/jdbc/reference/geturl-method-sqlserverdatasource.md)|データ ソースへの接続に使用される URL を返します。|  
|[getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md)|データ ソースに接続するために使用するユーザー名を返します。|  
|[getUseSQLServerBaseDate](../../../connect/jdbc/reference/getsendtimeasdatetime-method-sqlserverdatasource.md)|useSQLServerBaseDate 接続プロパティの設定を返します。|  
|[getWorkstationID](../../../connect/jdbc/reference/getworkstationid-method-sqlserverdatasource.md)|データ ソースに接続するため、クライアント コンピューターの名前を返します。|  
|[getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md)|返します、**ブール**XOPEN 互換の状態を SQL 状態の変換が有効になっているかどうかを示す値。|  
|[isWrapperFor](../../../connect/jdbc/reference/iswrapperfor-method-sqlserverdatasource.md)|データ ソース オブジェクトが指定されたインターフェイスのラッパーであるかどうかを示します。|  
|[setApplicationIntent](../../../connect/jdbc/reference/setapplicationintent-method-sqlserverdatasource.md)|値を設定、 **applicationIntent**接続プロパティです。|  
|[setApplicationName](../../../connect/jdbc/reference/setapplicationname-method-sqlserverdatasource.md)|アプリケーション名を設定します。|  
|[setAuthenticationScheme](../../../connect/jdbc/reference/setauthenticationscheme-sqlserverdatasource.md)|アプリケーションで使用する統合セキュリティの種類を示します。|  
|[setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md)|接続するデータベース名を設定します。|  
|[setDescription](../../../connect/jdbc/reference/setdescription-method-sqlserverdatasource.md)|データ ソースの記述を設定します。|  
|[setEncrypt](../../../connect/jdbc/reference/setencrypt-method-sqlserverdatasource.md)|セット、**ブール**encrypt プロパティが有効になっているかどうかを示す値。|  
|[setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md)|データベース ミラーリング構成で使用されるフェールオーバー サーバーの名前を設定します。|  
|[setHostNameInCertificate](../../../connect/jdbc/reference/sethostnameincertificate-method-sqlserverdatasource.md)|SQL Server の SSL (Secure Sockets Layer) 証明書の検証に使用されるホスト名を設定します。|  
|[setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md)|セット、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]インスタンス名。|  
|[setIntegratedSecurity](../../../connect/jdbc/reference/setintegratedsecurity-method-sqlserverdatasource.md)|セット、**ブール**integratedSecurity プロパティが有効になっているかどうかを示す値。|  
|[setLastUpdateCount](../../../connect/jdbc/reference/setlastupdatecount-method-sqlserverdatasource.md)|セット、**ブール**lastUpdateCount プロパティが有効になっているかどうかを示す値。|  
|[setLockTimeout](../../../connect/jdbc/reference/setlocktimeout-method-sqlserverdatasource.md)|セット、 **int**データベースがロック タイムアウトを報告する前に待機するミリ秒数を示す値。|  
|[setLoginTimeout](../../../connect/jdbc/reference/setlogintimeout-method-sqlserverdatasource.md)|秒数を設定この[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクトが接続を確立中に待機します。|  
|[setLogWriter](../../../connect/jdbc/reference/setlogwriter-method-sqlserverdatasource.md)|すべてのログ メッセージとトレース メッセージで文字出力ストリームが使用されるように設定します。|  
|[setMultiSubnetFailover](../../../connect/jdbc/reference/setmultisubnetfailover-method-sqlserverdatasource.md)|値を設定、 **multiSubnetFailover**接続プロパティです。|  
|[setPacketSize](../../../connect/jdbc/reference/setpacketsize-method-sqlserverdatasource.md)|通信するために使用される現在のネットワーク パケット サイズを設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]、バイト単位で指定します。|  
|[setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md)|接続に使用するパスワードを設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。|  
|[setPortNumber](../../../connect/jdbc/reference/setportnumber-method-sqlserverdatasource.md)|通信するために使用するポート番号を設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。|  
|[setResponseBuffering](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverdatasource.md)|応答バッファリングこれを使用して作成された接続のモードを設定[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクト。|  
|[setSelectMethod](../../../connect/jdbc/reference/setselectmethod-method-sqlserverdatasource.md)|これを使用して作成されたすべての結果セットを使用する既定のカーソルの種類を設定[SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)オブジェクト。|  
|[setSendStringParametersAsUnicode](../../../connect/jdbc/reference/setsendstringparametersasunicode-method-sqlserverdatasource.md)|セット、**ブール**文字列パラメーターを UNICODE 形式でサーバーに送信が有効になっているかどうかを示す値。|  
|[setSendTimeAsDatetime](../../../connect/jdbc/reference/setsendtimeasdatetime-method-sqlserverdatasource.md)|java.sql.Time 値をサーバーに送信する方法を指定します。|  
|[setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md)|実行するコンピューターの名前を設定[!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]です。|  
|[setTrustServerCertificate](../../../connect/jdbc/reference/settrustservercertificate-method-sqlserverdatasource.md)|セット、**ブール**trustServerCertificate プロパティが有効になっているかどうかを示す値。|  
|[setTrustStore](../../../connect/jdbc/reference/settruststore-method-sqlserverdatasource.md)|証明書の trustStore ファイルへのパス (ファイル名を含む) を設定します。|  
|[setTrustStorePassword](../../../connect/jdbc/reference/settruststorepassword-method-sqlserverdatasource.md)|trustStore データの整合性を確認するために使用するパスワードを設定します。|  
|[setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md)|データ ソースへの接続に使用される URL を設定します。|  
|[setUser](../../../connect/jdbc/reference/setuser-method-sqlserverdatasource.md)|データ ソースに接続するために使用するユーザー名を設定します。|  
|[setWorkstationID](../../../connect/jdbc/reference/setworkstationid-method-sqlserverdatasource.md)|データ ソースへの接続に使用されるクライアント コンピューターの名前を設定します。|  
|[setXopenStates](../../../connect/jdbc/reference/setxopenstates-method-sqlserverdatasource.md)|セット、**ブール**XOPEN 互換の状態を SQL 状態の変換が有効になっているかどうかを示す値。|  
|[unwrap](../../../connect/jdbc/reference/unwrap-method-sqlserverdatasource.md)|アクセス許可を指定したインターフェイスを実装するオブジェクトを返します、 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]-特定のメソッドです。|  
  
## <a name="inherited-methods"></a>継承されたメソッド  
  
|継承元のクラス|メソッド|  
|---------------------------|-------------|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
|java.sql.Wrapper|isWrapperFor、unwrap|  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
