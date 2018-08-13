---
title: JDBC ドライバーのリリース ノート |Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
caps.latest.revision: 206
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 10f14eedb1a74f74cb1ee055a247a96671224ce0
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662464"
---
# <a name="release-notes-for-the-jdbc-driver"></a>JDBC Driver のリリース ノート

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-70-for-sql-server"></a>Microsoft JDBC Driver 7.0 for SQL Server の更新された機能

SQL Server 用 Microsoft JDBC Driver 7.0 は、JDBC API 仕様 4.2 に完全に準拠します。 7.0 のパッケージ内の jar が Java のバージョンの互換性の名前です。 たとえば、7.0 パッケージから mssql-jdbc-7.0.0.jre10.jar ファイルを使用して、Java 10 でください。

### <a name="support-for-jdk-10"></a>JDK 10 のサポート

SQL Server 用 Microsoft JDBC Driver 7.0 は、Java Development Kit (JDK) バージョン 10.0 に加えて JDK 1.8 と互換性のあるようになりました。 この更新プログラム、ドライバーの ' 自動-Module-Name' としても公開します`com.microsoft.sqlserver.jdbc`のマニフェスト ファイルを使用します。

### <a name="support-for-spatial-datatypes"></a>空間データ型のサポート

SQL Server 用 Microsoft JDBC Driver 7.0 は、今すぐ SQL Server 空間データ型 'Geography' と 'ジオメトリ' のサポートを提供します。 空間データ型の Api とその使用方法の詳細については、次を参照してください。[ここ](../../connect/jdbc/use-spatial-datatypes.md)します。

### <a name="implementation-for-jdbc-43-introduced-javasqlconnection-apis-beginrequest-and-endrequest"></a>JDBC 4.3 の実装で、java.sql.Connection の API beginRequest() と endRequest() が導入されました。

SQL Server の現在の実装用の Microsoft JDBC Driver 7.0`beginRequest()`と`endRequest()`Api から`java.sql.Connection`クラス。 これらの Api は、JDBC 4.3 仕様と JDK 9 で導入されました。 これらの Api のドライバーの実装の詳細については、次を参照してください。[ここ](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md)します。

### <a name="support-for-sql-data-discovery-and-classification"></a>"SQL データの検出と分類" のサポート

SQL Server 用 Microsoft JDBC Driver 7.0 では、この機能をサポートする任意のターゲット データベースの 'SQL データの検出と分類' の機能をサポートします。 ドライバーを今すぐ公開`SQLServerResultSet.getSensitivityClassification()`Api フェッチされた結果セットからこの情報を抽出します。

JDBC ドライバーでこの機能を使用する方法の詳細については、サンプルを参照してください。[ここ](../../connect/jdbc/data-discovery-classification-sample.md)します。

### <a name="added-new-connection-property-usebulkcopyforbatchinsert"></a>新しい接続プロパティの追加: useBulkCopyForBatchInsert

SQL Server 用 Microsoft JDBC Driver 7.0 には、次のように新しい接続プロパティ 'useBulkCopyForBatchInsert' にのみサポートされているが導入されています**Data Warehouse**します。

このプロパティは**無効になっている**によって既定および Azure Data Warehouse にデータを金額大規模なプッシュ時に、ユーザー アプリケーションのパフォーマンスを向上させるために有効にできます。 このプロパティを有効にするユーザー指定のデータを一括コピー操作に切り替えるバッチ挿入操作の動作を変更します。 このプロパティと制限事項の詳細については、参照[ここ](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md)します。

### <a name="added-new-connection-property-cancelquerytimeout"></a>新しい接続プロパティの追加: cancelQueryTimeout

SQL Server 用 Microsoft JDBC Driver 7.0 には新しい接続のプロパティが導入されています`cancelQueryTimeout`をキャンセルするには、`queryTimeout`で`java.sql.Connection`と`java.sql.Statement`オブジェクト。

### <a name="added-azure-key-vault-provider-constructors"></a>追加の Azure Key Vault プロバイダーのコンス トラクター

SQL Server 用 Microsoft JDBC Driver 7.0 以前に削除したコンス トラクターを再導入の`SQLServerColumnEncryptionAzureKeyVaultProvider`、経由で実装するカスタム メソッドを使用して、許可されている認証`SQLServerKeyVaultAuthenticationCallback`をアクセス トークンをフェッチします。

新しいコンス トラクターが、定義の下。

```java
/* This constructor is added to provide backwards compatibility with 6.0
* version of the driver. It is marked deprecated for removal in next
* stable release.
*/
@Deprecated
public SQLServerColumnEncryptionAzureKeyVaultProvider(
        SQLServerKeyVaultAuthenticationCallback authenticationCallback,
        ExecutorService executorService) throws SQLServerException;

/*New Constructor to replace the above constructor*/
public SQLServerColumnEncryptionAzureKeyVaultProvider(
            SQLServerKeyVaultAuthenticationCallback authenticationCallback) throws SQLServerException;
```

### <a name="updated-adal4j-version-to-160"></a>更新されたように ADAL4J をバージョン 1.6.0 を

SQL Server 用 Microsoft JDBC Driver 7.0 がバージョン 1.6.0 に azure active directory-ライブラリ-の-java (ADAL4J) 時に、maven の依存関係を更新します。 依存関係について詳しくは、[こちら](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)をご覧ください。

## <a name="updates-in-microsoft-jdbc-driver-64-for-sql-server"></a>Microsoft JDBC Driver 6.4 for SQL Server の更新された機能

SQL Server 用 Microsoft JDBC Driver 6.4 は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 6.4 パッケージ内の jar が Java のバージョンの互換性の名前です。 たとえば、6.4 パッケージから mssql-jdbc-6.4.0.jre8.jar ファイルは、Java 8 で使用する必要があります。

### <a name="support-for-jdk-9"></a>JDK 9 のサポート

Java Development Kit (JDK) バージョン 8.0 および 7.0 だけでなく、JDK 9.0 もサポートするようになりました。

### <a name="jdbc-43-compliance"></a>JDBC 4.3 コンプライアンス

Java Database Connectivity API 4.1 および 4.2 だけでなく、4.3 の仕様もサポートするようになりました。 JDBC 4.3 API メソッドは追加が、まだ実装されていません。 詳細については、「[JDBC Driver の JDBC 4.3 への準拠](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md)」をご覧ください。

### <a name="added-new-connection-property-sslprotocol"></a>新しい接続プロパティの追加: sslProtocol

ユーザーが TLS プロトコルのキーワードを指定できるようにする新しい接続プロパティを追加します。 値:"TLS"、"TLSv1"、"TLSv1.1"、"TLSv1.2"。 参照してください[SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol)詳細についてはします。

### <a name="deprecated-connection-property-fipsprovider"></a>接続プロパティを非推奨とされます: fipsProvider

接続のプロパティ"fipsProvider"は、受け入れられた接続プロパティの一覧から削除されます。 詳細を参照してください。[ここ](https://github.com/Microsoft/mssql-jdbc/pull/460)します。

### <a name="added-connection-properties-for-specifying-custom-trustmanager"></a>カスタムの TrustManager を指定する追加の接続プロパティ

接続プロパティ "trustManagerClass" と "trustManagerConstructorArg" の追加により、ドライバーでカスタムの TrustManager を指定できるようになりました。 これにより、JVM 環境のグローバル設定を変更することがなく、接続ごとに信頼されている証明書の一連の動的な指定。

### <a name="added-support-for-datetimesmalldatetime-in-table-valued-parameters-tvp"></a>テーブル値パラメーター (TVP) での datetime または smalldatetime 型のサポートが追加されました

テーブル値パラメーター (TVP) を使用するときに、ドライバーでデータ型 DATETIME と SMALLDATETIME がサポートされるようになりました。

### <a name="added-support-for-sqlvariant-datatype"></a>Sql_variant データ型のサポートが追加されました

JDBC Driver は、SQL Server で使用される sql_variant データ型をサポートします。 Sql_variant は制限事項の下で BulkCopy テーブル値パラメーター (TVP) などの機能でもサポートされています。

1. 日付の値: TVP を使用して値を入れるテーブルで datetime/smalldatetime/date の値が sql_variant 列に格納されているときは、getDateTime()/getSmallDateTime()/getDate() メソッドを結果セットに対して呼び出しても機能せず、次の例外が返されます。`java java.lang.String cannot be cast to java.sql.Timestamp` 回避策: "getString()" メソッドまたは "getObject()" メソッドを代わりに使用します。

2. TVP を null 値の SQL VARIANT とともに使用する

TVP を使用してテーブルに値を入れるときに NULL 値を sql_variant 型の列に送ると、例外が発生します。TVP で NULL 値を sql_variant 型の列に挿入することは現時点ではサポートされていないためです。

### <a name="implemented-prepared-statement-metadata-caching"></a>準備されたステートメントが実装されているメタデータのキャッシュ

JDBC Driver は、実装ステートメント メタデータ キャッシュの準備パフォーマンスが向上します。 プリペアド ステートメントのメタデータをドライバー内でキャッシュできるようになりました。これには接続プロパティ "disableStatementPooling" と "statementPoolingCacheSize" が使用されます。 この機能は、既定では無効化されています。 詳細は[こちら](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)をご覧ください。

### <a name="added-support-for-aad-integrated-authentication-on-linuxmac"></a>Linux または Mac で AAD 統合認証のサポートが追加されました

JDBC ドライバーで Azure Active Directory 統合認証も、サポート対象のすべてのオペレーティング システム (Windows/Linux/Mac) で Kerberos とともにサポートされるようになりました。 または、Windows オペレーティング システムでは、ユーザーを認証できます sqljdbc_auth.dll の。

### <a name="updated-adal4j-version-to-140"></a>更新された ADAL4J バージョン 1.4.0

JDBC ドライバーがバージョン 1.4.0 に azure active directory-ライブラリ-の-java (ADAL4J) 時に、maven の依存関係を更新します。 依存関係について詳しくは、[こちら](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)をご覧ください。

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>Microsoft JDBC Driver 6.2 for SQL Server の更新された機能

Microsoft JDBC Driver 6.2 for SQL Server は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 6.2 パッケージ内の jar が Java のバージョンの互換性の名前です。 たとえば、Java 8 で使用する 6.2 パッケージから mssql-jdbc-6.2.2.jre8.jar ファイルがお勧めします。

> [!NOTE]  
> 2017 年 6 月 29 日にリリースされた JDBC 6.2 RTW でのメタデータ キャッシュの改善により、問題が見つかりました。 改善がロールバックされ、新しい jar (バージョン 6.2.1) は、2017 年 7 月 17 日にリリースされました。 
>
> Azure Key Vault の依存するライブラリのバージョンを 1.0.0 にアップグレードする機能の強化が行われ、新しい jar (版 6.2.2) は、2017 年 10 月 19 日にリリースされました。
>
> JDBC Driver 6.2 で最新の更新プログラムをダウンロード[Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/?linkid=852460)、 [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2)、および[Maven Central](http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22)します。 6.2.2 を使用するプロジェクトを更新してください jar をリリースします。 リリース ノートを参照してください[v6.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1)と[v6.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2)の詳細。

### <a name="azure-active-directory-aad-support-for-linux"></a>Linux 用 azure Active Directory (AAD) のサポート

ユーザー名/パスワードおよびそのアクセス トークンの方法を使用して AAD 認証を使用して Azure SQL Database に、Linux アプリケーションを接続します。

### <a name="federal-information-processing-standard-fips-enabled-jvms"></a>連邦情報処理規格 (FIPS) には、Jvm が有効になっています。

JDBC Driver は、Jvm 連邦標準およびコンプライアンスを満たすために FIPS 140 準拠モードで実行されているで今すぐ使用できます。

### <a name="kerberos-authentication-improvements"></a>Kerberos 認証の機能強化

JDBC ドライバーでは、サポートできるようになりました。

- プリンシパル/パスワード メソッド アプリケーションの Kerberos の構成が変更または新しいトークンまたは keytab を取得できませんにすることはできません。 このメソッドは、Kerberos 認証のみを許可する SQL Server への認証に使用できます。
- 領域間のサーバーの SPN を明示的に設定しなくても Kerberos 統合認証を使用して認証します。 ドライバー今すぐ自動的に計算されます、領域が提供されている場合でもです。
- そのまま使用して Kerberos の制約付き委任は、データ ソースを使用して、GSS 資格情報オブジェクトとしてユーザーの資格情報を偽装します。 この権限を借用した資格情報を使用し、Kerberos の接続を確立します。

### <a name="added-timeouts"></a>追加のタイムアウト

JDBC ドライバーでは、次構成可能なタイムアウトを変更することができます、アプリケーションのニーズに基づいてできるようになりました。

- タイムアウトするまで待機する秒数を制御するクエリのタイムアウトは、クエリを実行するときに発生します。
- ソケットのタイムアウトが発生する前に待機するミリ秒数を指定するソケットのタイムアウトは、読み取りまたはそのまま使用します。

## <a name="updates-in-microsoft-jdbc-driver-61-for-sql-server"></a>Microsoft JDBC Driver 6.1 for SQL Server の更新された機能

SQL Server 用 Microsoft JDBC Driver 6.1 が 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 これは、JDBC ドライバーの最初のオープン ソース リリースであり、Java のバージョンの互換性に対応する mssql-jdbc-6.1.0.jre8.jar mssql-jdbc-6.1.0.jre7.jar ファイルが含まれます。

## <a name="updates-in-microsoft-jdbc-driver-60-for-sql-server"></a>Microsoft JDBC Driver 6.0 for SQL Server の更新された機能

Microsoft JDBC Driver 6.0 for SQL Server は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 Jar を 6.0 のパッケージの名前は、JDBC API のバージョンに準拠してです。 たとえば、6.0 パッケージから sqljdbc42.jar ファイルは、JDBC API 4.2 に準拠してが。 同様に、sqljdbc41.jar ファイルは、JDBC API 4.1 準拠です。

適切な sqljdbc42.jar または sqljdbc41.jar をしたことを確認するには、次のコード行を実行します。 出力する場合は"ドライバーのバージョン: 6.0.7507.100"、JDBC Driver 6.0 パッケージがあります。

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="always-encrypted"></a>Always Encrypted

SQL Server 2016 で最近リリースされた Always Encrypted 機能をサポートします。これは、SQL Server インスタンスで機密データがプレーンテキストで絶対に表示されないようにする新たなセキュリティ機能です。 Always Encrypted は透過的な機能で、アプリケーション内のデータの暗号化を行います。SQL Server は暗号化データのみを扱い、プレーンテキスト値は処理しません。 SQL インスタンスまたはホスト コンピューターが侵害された場合であっても、すべての攻撃者が取得できるのは機密データの暗号化テキストになります。 詳細については、「[JDBC ドライバーでの Always Encrypted の使用](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)」をご覧ください。

### <a name="internationalized-domain-name-idn"></a>国際化ドメイン名 (IDN)

サーバー名に関する国際化ドメイン名 (IDN) をサポートします。 詳細情報を使用した国際化ドメイン名を参照してください、 [JDBC Driver の国際対応](../../connect/jdbc/international-features-of-the-jdbc-driver.md)ページ。

### <a name="parameterized-query"></a>パラメーター化クエリ

サブクエリや結合などの複雑なクエリで、準備されたステートメントを使用したパラメーター メタデータの取得をサポートできるようになりました。 なお、この機能強化を利用できるのは、SQL Server 2012 以降のバージョンを使用する場合に限られます。

### <a name="azure-active-directory-aad"></a>Azure Active Directory (AAD)

AAD 認証は、Azure SQL Database v12 に接続するメカニズムでは、AAD の id を使用します。 AAD 認証は、データベース ユーザーの ID を一元管理するという目的で使用でき、SQL Server 認証に代わる方法となります。 JDBC Driver 6.0 では、AAD の資格情報を JDBC 接続文字列の中で指定して Azure SQL DB に接続することができます。 詳細情報を認証プロパティを参照してください、[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)ページ。

### <a name="table-valued-parameters"></a>テーブル値パラメーター

テーブル値パラメーターは、複数行のデータをクライアント アプリケーションから SQL Server に簡単にマーシャリングするための手段です。複数のラウンド トリップや、データ処理用の特別なサーバー側ロジックは必要ありません。 テーブル値パラメーターを使用すると、クライアント アプリケーションで複数行のデータをカプセル化してサーバーに送信する処理を 1 つのパラメーター化コマンドで実行できます。 受信データ行は、TRANSACT-SQL を使用してで操作できるテーブル変数に格納されます。 詳細については、次を参照してください。 [Using Table-Valued パラメーター](../../connect/jdbc/using-table-valued-parameters.md)します。

### <a name="alwayson-availability-groups-ag"></a>AlwaysOn 可用性グループ (AG)

ドライバーは、AlwaysOn 可用性グループへの透過的な接続をサポートします。 ドライバーがサーバー インフラストラクチャの現在の AlwaysOn トポロジをすばやく検出して、現在アクティブなサーバーに透過的に接続します。

## <a name="updates-in-microsoft-jdbc-driver-42-for-sql-server-and-later"></a>Microsoft JDBC Driver 4.2 for SQL Server 以降の更新された機能

Microsoft JDBC Driver 4.2 for SQL Server は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 Jar を 4.2 のパッケージの名前は、JDBC API のバージョンに準拠してです。 たとえば、4.2 のパッケージから sqljdbc42.jar ファイルは、JDBC API 4.2 に準拠してが。 同様に、sqljdbc41.jar ファイルは、JDBC API 4.1 準拠です。

適切な sqljdbc42.jar または sqljdbc41.jar をしたことを確認するには、次のコード行を実行します。 出力する場合は"ドライバーのバージョン: 4.2.6420.100"、JDBC Driver 4.2 のパッケージがあります。

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="support-for-jdk-8"></a>JDK 8 のサポート

Java Development Kit (JDK) バージョン 5.0、6.0、および 7.0 だけでなく、JDK 8.0 もサポートするようになりました。

### <a name="jdbc-41-and-42-compliance"></a>JDBC 4.1 および 4.2 への準拠

Java Database Connectivity API 4.0 だけでなく、4.1、および 4.2 の仕様もサポートするようになりました。 詳細については、次を参照してください。 [JDBC Driver の JDBC 4.1 準拠](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md)と[JDBC Driver の JDBC 4.2 準拠](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md)します。

### <a name="bulk-copy"></a>一括コピー

一括コピー機能を使用すると、SQL Server データベースのテーブルまたはビューに大量のデータを迅速にコピーできます。 詳細については、「[JDBC ドライバーでの一括コピーの使用](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md)」をご覧ください。

### <a name="xa-transaction-rollback-option"></a>XA トランザクション ロールバック オプション

準備解除されたトランザクションを自動的にロールバックする既存のオプションに、新しいタイムアウト オプションが追加されました。 詳細については、次を参照してください。 [XA トランザクションの概要](../../connect/jdbc/understanding-xa-transactions.md)します。

### <a name="new-kerberos-principal-connection-property"></a>新しい Kerberos プリンシパル接続プロパティ

Kerberos 接続に、柔軟な処理を行うための新しい接続プロパティが追加されました。 詳細については、「[Kerberos 統合認証による SQL Server への接続](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)」をご覧ください。

## <a name="updates-in-microsoft-jdbc-driver-41-for-sql-server-and-later"></a>Microsoft JDBC Driver 4.1 for SQL Server 以降の更新された機能

### <a name="support-for-jdk-7"></a>JDK 7 のサポート

Java Development Kit (JDK) バージョン 5.0 および 6.0 だけでなく、JDK 7.0 もサポートするようになりました。

## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Itanium では JDBC Driver 6.4、6.0、4.2、4.1 アプリケーションがサポートされない

Microsoft JDBC Drivers 6.4、6.0、4.2、4.1 for SQL Server アプリケーションは、Itanium コンピューター上での実行がサポートされていません。

## <a name="see-also"></a>参照

[JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)
