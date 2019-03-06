---
title: DSN と接続文字列キーワードの ODBC ドライバー - SQL Server |Microsoft Docs
ms.custom: ''
ms.date: 02/04/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
ms.reviewer: MightyPen
ms.author: v-jizho2
author: karinazhou
manager: craigg
ms.openlocfilehash: e2db3b8df9ea63c16e0e96af9df42b7c22adaf80
ms.sourcegitcommit: b3d84abfa4e2922951430772c9f86dce450e4ed1
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/22/2019
ms.locfileid: "56662876"
---
# <a name="dsn-and-connection-string-keywords-and-attributes"></a>DSN と接続文字列のキーワードと属性

このページは、接続文字列と、Dsn キーワード、SQLSetConnectAttr と SQLGetConnectAttr、ODBC Driver for SQL Server で使用可能な接続属性を一覧表示します。

## <a name="supported-dsnconnection-string-keywords-and-connection-attributes"></a>DSN または接続文字列のキーワードと接続属性をサポート

次の表は、使用可能なキーワードと各プラットフォーム (l: Linux での属性M: Mac。W: Windows の場合)。 キーワードの詳細属性をクリックします。

| DSN / 接続文字列のキーワード | 接続属性 | プラットフォーム |
|-|-|-|
| [Addr](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [Address](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [AnsiNPW](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_ANSI_NPW](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssansinpw) | LMW |
| [APP](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [ApplicationIntent](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_APPLICATION_INTENT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssapplicationintent) | LMW |
| [AttachDBFileName](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_ATTACHDBFILENAME](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssattachdbfilename) | LMW |
| [[認証]](../../connect/odbc/dsn-connection-string-attribute.md#authentication---sqlcoptssauthentication) | [SQL_COPT_SS_AUTHENTICATION](../../connect/odbc/dsn-connection-string-attribute.md#authentication---sqlcoptssauthentication) | LMW |
| [AutoTranslate](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_TRANSLATE](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsstranslate) | LMW |
| [ColumnEncryption](../../connect/odbc/dsn-connection-string-attribute.md#columnencryption---sqlcoptsscolumnencryption) | [SQL_COPT_SS_COLUMN_ENCRYPTION](../../connect/odbc/dsn-connection-string-attribute.md#columnencryption---sqlcoptsscolumnencryption) | LMW |
| [ConnectRetryCount](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) | [SQL_COPT_SS_CONNECT_RETRY_COUNT](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) | W |
| [ConnectRetryInterval](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) | [SQL_COPT_SS_CONNECT_RETRY_INTERVAL](../../connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver.md) | W |
| [[データベース]](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_ATTR_CURRENT_CATALOG](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | LMW |
| [[説明]](../../connect/odbc/dsn-connection-string-attribute.md#description) | | LMW |
| [[ドライバー]](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [DSN](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [Encrypt](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_ENCRYPT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssencrypt) | LMW |
| [Failover_Partner](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_FAILOVER_PARTNER](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssfailoverpartner) | W |
| [FailoverPartnerSPN](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_FAILOVER_PARTNER_SPN](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | W |
| [FileDSN](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [KeystoreAuthentication](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#connection-string-keywords) | | LMW |
| [KeystorePrincipalId](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#connection-string-keywords) | | LMW |
| [KeystoreSecret](../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md#connection-string-keywords) | | LMW |
| [言語](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [MARS_Connection](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_MARS_ENABLED](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssmarsenabled) | LMW |
| [MultiSubnetFailover](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_MULTISUBNET_FAILOVER](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssmultisubnetfailover) | LMW |
| [Net](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [Network](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [PWD](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [QueryLog_On](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_QUERY](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfquery) | W |
| [QueryLogFile](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_QUERY_LOG](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfquerylog) | W |
| [QueryLogTIme](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_QUERY_INTERVAL](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfqueryinterval) | W |
| [QuotedId](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_QUOTED_IDENT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssquotedident) | LMW |
| [Regional](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [SaveFile](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [[サーバー]](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [ServerSPN](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_SERVER_SPN](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | LMW |
| [StatsLog_On](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_DATA](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfdata) | W |
| [StatsLogFile](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_PERF_DATA_LOG](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfdatalog) | W |
| [TransparentNetworkIPResolution](../../connect/odbc/dsn-connection-string-attribute.md#transparentnetworkipresolution---sqlcoptsstnir) | [SQL_COPT_SS_TNIR](../../connect/odbc/dsn-connection-string-attribute.md#transparentnetworkipresolution---sqlcoptsstnir) | LMW |
| [Trusted_Connection](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_INTEGRATED_SECURITY](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssintegratedsecurity) | LMW |
| [TrustServerCertificate](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | [SQL_COPT_SS_TRUST_SERVER_CERTIFICATE](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsstrustservercertificate) | LMW |
| [UID](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| [UseFMTONLY](../../connect/odbc/dsn-connection-string-attribute.md#usefmtonly) | | LMW |
| [WSID](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md) | | LMW |
| | [SQL_ATTR_ACCESS_MODE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_ACCESS_MODE) | LMW |
| | [SQL_ATTR_ASYNC_DBC_EVENT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_ASYNC_DBC_PCALLBACK](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_ASYNC_DBC_PCONTEXT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_ASYNC_ENABLE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | W |
| | [SQL_ATTR_AUTO_IPD](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | LMW |
| | [SQL_ATTR_AUTOCOMMIT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_AUTOCOMMIT) | LMW |
| | [SQL_ATTR_CONNECTION_DEAD](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | LMW |
| | [SQL_ATTR_CONNECTION_TIMEOUT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | LMW |
| | [SQL_ATTR_DBC_INFO_TOKEN](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | LMW |
| | [SQL_ATTR_LOGIN_TIMEOUT](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_LOGIN_TIMEOUT) | LMW |
| | [SQL_ATTR_METADATA_ID](../../odbc/reference/syntax/sqlsetconnectattr-function.md) | LMW |
| | [SQL_ATTR_ODBC_CURSORS](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_ODBC_CURSORS) | LMW |
| | [SQL_ATTR_PACKET_SIZE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_PACKET_SIZE) | LMW |
| | [SQL_ATTR_QUIET_MODE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_QUIET_MODE) | LMW |
| | [SQL_ATTR_RESET_CONNECTION](../../odbc/reference/develop-driver/upgrading-a-3-5-driver-to-a-3-8-driver.md#connection-pooling) <br> (SQL_COPT_SS_RESET_CONNECTION) | LMW |  
| | [SQL_ATTR_TRACE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_OPT_TRACE) | LMW |
| | [SQL_ATTR_TRACEFILE](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_OPT_TRACEFILE) | LMW |
| | [SQL_ATTR_TRANSLATE_LIB](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_TRANSLATE_DLL) | LMW |
| | [SQL_ATTR_TRANSLATE_OPTION](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_TRANSLATE_OPTION) | LMW |
| | [SQL_ATTR_TXN_ISOLATION](../../odbc/reference/syntax/sqlsetconnectattr-function.md) <br> (SQL_TXN_ISOLATION) | LMW |
| | [SQL_COPT_SS_ACCESS_TOKEN](dsn-connection-string-attribute.md#sqlcoptssaccesstoken) | LMW |
| | [SQL_COPT_SS_ANSI_OEM](dsn-connection-string-attribute.md#sqlcoptssansioem)| W |
| | [SQL_COPT_SS_BCP](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssbcp) | LMW |
| | [SQL_COPT_SS_BROWSE_CACHE_DATA](../../relational-databases/native-client-odbc-api/sqlbrowseconnect.md) | LMW |
| | [SQL_COPT_SS_BROWSE_CONNECT](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssbrowseconnect) | LMW |
| | [SQL_COPT_SS_BROWSE_SERVER](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssbrowseserver) | LMW |
| | [SQL_COPT_SS_CEKEYSTOREDATA](dsn-connection-string-attribute.md#sqlcoptsscekeystoredata) | LMW |
| | [SQL_COPT_SS_CEKEYSTOREPROVIDER](dsn-connection-string-attribute.md#sqlcoptsscekeystoreprovider) | LMW |
| | [SQL_COPT_SS_CLIENT_CONNECTION_ID](../../relational-databases/native-client-odbc-api/sqlgetconnectattr.md) | LMW |
| | [SQL_COPT_SS_CONCAT_NULL](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssconcatnull) | LMW |
| | [SQL_COPT_SS_CONNECTION_DEAD](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssconnectiondead) | LMW |
| | [SQL_COPT_SS_ENLIST_IN_DTC](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssenlistindtc) | W |
| | [SQL_COPT_SS_ENLIST_IN_XA](dsn-connection-string-attribute.md#sql_copt_ss_enlist_in_xa) | LMW |
| | [SQL_COPT_SS_FALLBACK_CONNECT](dsn-connection-string-attribute.md#sqlcoptssfallbackconnect) | LMW |
| | [SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | LMW |
| | [SQL_COPT_SS_MUTUALLY_AUTHENTICATED](../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md) | LMW |
| | [SQL_COPT_SS_OLDPWD](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssoldpwd) | LMW |
| | [SQL_COPT_SS_PERF_DATA_LOG_NOW](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssperfdatalognow) | W |
| | [SQL_COPT_SS_PRESERVE_CURSORS](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsspreservecursors) | LMW |
| | [SQL_COPT_SS_TXN_ISOLATION](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsstxnisolation) | LMW |
| | [SQL_COPT_SS_USER_DATA](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptssuserdata) | LMW |
| | [SQL_COPT_SS_WARN_ON_CP_ERROR](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md#sqlcoptsswarnoncperror) | LMW |


ここではいくつかの接続文字列キーワードとに記載されていない接続属性[使用した Connection String Keywords with SQL Server Native Client を使用して](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)、 [SQLSetConnectAttr](../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md)と[SQLSetConnectAttr 関数](../../odbc/reference/syntax/sqlsetconnectattr-function.md)します。

### <a name="description"></a>[説明]

データ ソースの記述に使用されます。

### <a name="sqlcoptssansioem"></a>SQL_COPT_SS_ANSI_OEM

データの変換を OEM に ANSI を制御します。 

| 属性値 | [説明] |
|-|-|
| SQL_AO_OFF | (既定値)変換は行われません。 |
| SQL_AO_ON | 変換が実行されます。 |

### <a name="sqlcoptssfallbackconnect"></a>SQL_COPT_SS_FALLBACK_CONNECT

SQL Server のフォールバック接続の使用を制御します。 この 1 つがサポートされていません。

| 属性値 | [説明] |
|-|-|
| SQL_FB_OFF | (既定値)フォールバックの接続が無効です。 |
| SQL_FB_ON | フォールバックの接続を有効にします。 |



## <a name="new-connection-string-keywords-and-connection-attributes"></a>新しい接続文字列のキーワードと接続属性

###  <a name="authentication---sqlcoptssauthentication"></a>認証 - SQL_COPT_SS_AUTHENTICATION

SQL Server に接続するときに使用する認証モードを設定します。 参照してください[を使用して Azure の Active Directory](using-azure-active-directory.md)詳細についてはします。

| キーワードの値 | 属性値 | [説明] |
|-|-|-|
| |SQL_AU_NONE|(既定値)設定されていません。 その他の属性の組み合わせでは、認証モードによって決まります。|
|SqlPassword|SQL_AU_PASSWORD|ユーザー名とパスワードを使用する SQL Server 認証。|
|ActiveDirectoryIntegrated|SQL_AU_AD_INTEGRATED|Azure Active Directory 統合認証。|
|ActiveDirectoryPassword|SQL_AU_AD_PASSWORD|Azure Active Directory パスワード認証。|
|ActiveDirectoryInteractive|SQL_AU_AD_INTERACTIVE|Azure Active Directory 対話型認証。|
|ActiveDirectoryMsi|SQL_AU_AD_MSI|Azure Active Directory 管理対象サービス Id 認証します。 ユーザー割り当て id、UID は、ユーザー id のオブジェクト ID に設定されます。 |
| |SQL_AU_RESET|未設定。 任意の DSN または接続文字列の設定をオーバーライドします。|

> [!NOTE]
> 使用する場合`Authentication`キーワードまたは属性を明示的に指定`Encrypt`接続文字列では、目的の値を設定/DSN/接続属性。 参照してください[使用した Connection String Keywords with SQL Server Native Client を使用して](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)詳細についてはします。

### <a name="columnencryption---sqlcoptsscolumnencryption"></a>ColumnEncryption - SQL_COPT_SS_COLUMN_ENCRYPTION

透過的な列の暗号化 (Always Encrypted) を制御します。 参照してください[を使用して Always Encrypted (ODBC)](using-always-encrypted-with-the-odbc-driver.md)詳細についてはします。

| キーワードの値 | 属性値 | [説明] |
|-|-|-|
|有効|SQL_CE_ENABLED|Always Encrypted を有効にします。|
|Disabled|SQL_CE_DISABLED|(既定値)Always Encrypted を無効にします。|
| |SQL_CE_RESULTSETONLY|解読のみ (結果と戻り値) を有効にします。|

### <a name="transparentnetworkipresolution---sqlcoptsstnir"></a>TransparentNetworkIPResolution - SQL_COPT_SS_TNIR

コントロールを短時間で再接続を許可する MultiSubnetFailover を使用した透過的なネットワーク IP 解決機能にしようとします。 参照してください[透過的なネットワーク IP 解決を使用して](using-transparent-network-ip-resolution.md)詳細についてはします。

| キーワードの値 | 属性値| [説明] |
|-|-|-|
|可|SQL_IS_ON|(既定値) 透過的なネットワーク IP の解決を有効にします。|
|いいえ|SQL_IS_OFF|透過的なネットワーク IP の解決を無効にします。|

### <a name="usefmtonly"></a>UseFMTONLY

SQL Server 2012 への接続と新しい場合は、メタデータに SET FMTONLY の使用を制御します。

| キーワードの値 | [説明] |
|-|-|
|いいえ|(既定値)使用可能な場合は、メタデータの sp_describe_first_result_set を使用します。 |
|可| メタデータに SET FMTONLY を使用します。 |

### <a name="sqlcoptssaccesstoken"></a>SQL_COPT_SS_ACCESS_TOKEN

認証のための Azure Active Directory のアクセス トークンの使用を許可します。 参照してください[を使用して Azure の Active Directory](using-azure-active-directory.md)詳細についてはします。

| 属性値 | [説明] |
|-|-|
| NULL | (既定値)アクセス トークンが提供されていません。 |
| ACCESSTOKEN* | アクセス トークンへのポインター。 |

### <a name="sqlcoptsscekeystoredata"></a>SQL_COPT_SS_CEKEYSTOREDATA

読み込まれたキーストア プロバイダー ライブラリと通信します。 コントロールの透過的な列暗号化 (Always Encrypted) を参照してください。 この属性には、既定値はありません。 参照してください[カスタム キーストア プロバイダー](custom-keystore-providers.md)詳細についてはします。

| 属性値 | [説明] |
|-|-|
| CEKEYSTOREDATA * | キーストア プロバイダー ライブラリの通信データの構造 |

### <a name="sqlcoptsscekeystoreprovider"></a>SQL_COPT_SS_CEKEYSTOREPROVIDER

キーストア プロバイダー ライブラリを読み込み、Always encrypted または読み込まれたキーストア プロバイダー ライブラリの名前を取得します。 参照してください[カスタム キーストア プロバイダー](custom-keystore-providers.md)詳細についてはします。 この属性には、既定値はありません。

| 属性値 | [説明] |
|-|-|
| char * | キーストア プロバイダー ライブラリへのパス |

### <a name="sqlcoptssenlistinxa"></a>SQL_COPT_SS_ENLIST_IN_XA

XA トランザクション XA 準拠のトランザクション プロセッサ (TP) を有効にする、アプリケーションを呼び出す必要がある**SQLSetConnectAttr** SQL_COPT_SS_ENLIST_IN_XA とへのポインター、`XACALLPARAM`オブジェクト。 このオプションは、Windows、Linux の (17.3 以降) およびファルダにサポートされます。
```
SQLSetConnectAttr(hdbc, SQL_COPT_SS_ENLIST_IN_XA, param, SQL_IS_POINTER);  // XACALLPARAM *param
``` 
 関連付ける、XA トランザクションと ODBC 接続のみ、TRUE または FALSE SQL_COPT_SS_ENLIST_IN_XA にポインターではなく呼び出し時に指定**SQLSetConnectAttr**します。 これは Windows では有効なだけであり、クライアント アプリケーションを通じて XA 操作を指定するのには使用できません。 
 ```
SQLSetConnectAttr(hdbc, SQL_COPT_SS_ENLIST_IN_XA, (SQLPOINTER)TRUE, 0);
``` 

|[値]|[説明]|プラットフォーム|  
|-----------|-----------------|-----------------|  
|XACALLPARAM オブジェクト *|ポインター`XACALLPARAM`オブジェクト。|Windows、Linux および Mac|
|TRUE|XA トランザクションを ODBC 接続に関連付けます。 関連するすべてのデータベース アクティビティは、XA トランザクションの保護下で実行されます。|Windows|  
|FALSE|ODBC 接続を使用してトランザクションの関連付けを解除します。|Windows|

 参照してください[XA トランザクションを使用して](../../connect/odbc/use-xa-with-dtc.md)XA トランザクションについての詳細。
