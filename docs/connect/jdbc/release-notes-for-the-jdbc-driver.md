---
title: JDBC ドライバーのリリース ノート |Microsoft Docs
ms.custom: ''
ms.date: 01/29/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4b7f863c7534421fa6e091e793297b4be3f73542
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2019
ms.locfileid: "55737063"
---
# <a name="release-notes-for-the-jdbc-driver"></a>JDBC ドライバーのリリース ノート

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-72-for-sql-server"></a>Microsoft JDBC Driver 7.2 for SQL Server の更新された機能

SQL Server 用 Microsoft JDBC Driver 7.2 は、JDBC API 仕様 4.2 に完全に準拠します。 7.2 パッケージ内の jar が Java のバージョンの互換性の名前です。 たとえば、7.2 パッケージから mssql-jdbc-7.2.0.jre11.jar ファイルを使用して、Java 11 でください。

### <a name="support-for-jdk-11"></a>JDK 11 のサポート

SQL Server 用 Microsoft JDBC Driver 7.2 は、Java Development Kit (JDK) バージョン 11.0 に加えて JDK 1.8 と互換性のあるようになりました。

### <a name="support-for-active-directory-managed-service-identity-msi-authentication"></a>Active Directory 管理対象サービス Id (MSI) 認証のサポート

SQL Server 用 Microsoft JDBC Driver 7.2 は、Active Directory 管理対象サービス Id (MSI) 認証モードをサポートします。 この認証モードでは、"Identity"機能を有効に対応の Azure リソースに適用できます。 取得をドライバーによって管理対象システムの Id (MSI) の両方の種類がサポートされている**accessToken**セキュリティで保護された接続を確立するためです。

詳細については、この認証モードを使用するサンプル アプリケーションはこちら。[Azure Active Directory 認証を利用した接続](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md)

### <a name="osgi-support"></a>OSGi サポート

SQL Server 用 Microsoft JDBC Driver 7.2 は、以下の実装を追加して、ドライバーに OSGi サポートを導入`org.osgi.service.jdbc.DataSourceFactory`と`org.osgi.framework.BundleActivator`:

- `com.microsoft.sqlserver.jdbc.osgi.SQLServerDataSourceFactory`
- `com.microsoft.sqlserver.jdbc.osgi.Activator`

### <a name="sqlservererror-apis"></a>SQLServerError Api

SQL Server 用 Microsoft JDBC Driver 7.2 紹介`SQLServerException.getSQLServerError()`と`SQLServerError`getter、サーバーから生成されたエラーに関する追加情報を取得する Api。 詳細については、「[Handling Errors](../../connect/jdbc/handling-errors.md)」 (エラーの処理) を参照してください。

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-163"></a>"Microsoft Azure Active Directory Authentication Library (ADAL4J) for Java" バージョン: 1.6.3 に更新

SQL Server 用 Microsoft JDBC Driver 7.2 が Maven の依存関係としても"Java クライアント ランタイムの AutoRest"導入されていますが「Microsoft Azure Active Directory 認証ライブラリ (ADAL4J) Java の」バージョン 1.6.3 への Maven 依存性を更新 (バージョン。1.6.5) として実装されています。 依存関係の詳細については、次を参照してください。 [for SQL Server、Microsoft JDBC Driver の依存関係をフィーチャー](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)します。

### <a name="updated-microsoft-azure-key-vault-sdk-for-java-version-120"></a>"Microsoft Azure Key Vault SDK の Java"の更新バージョン:1.2.0) として実装されています。

SQL Server 用 Microsoft JDBC Driver 7.2 は Maven への依存性"Microsoft Azure Key Vault SDK の Java"バージョン 1.2.0 にも"Microsoft Azure SDK の Key Vault WebKey"Maven の依存関係として導入されていますが、更新 (バージョン。1.2.0) として実装されています。 依存関係の詳細については、次を参照してください。 [for SQL Server、Microsoft JDBC Driver の依存関係をフィーチャー](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)します。

### <a name="known-issues"></a>既知の問題

SQL Server 用 Microsoft JDBC Driver 7.2 で特定のパラメーター化クエリでの既知の問題が存在します。 この問題に対処 7.2 バージョン (v7.2.1) の更新プログラムが間もなくリリースされます。


## <a name="updates-in-microsoft-jdbc-driver-70-for-sql-server"></a>Microsoft JDBC Driver 7.0 for SQL Server の更新された機能

SQL Server 用 Microsoft JDBC Driver 7.0 は、JDBC API 仕様 4.2 に完全に準拠します。 7.0 のパッケージ内の jar が Java のバージョンの互換性の名前です。 たとえば、7.0 パッケージから mssql-jdbc-7.0.0.jre10.jar ファイルを使用して、Java 10 でください。

### <a name="support-for-jdk-10"></a>JDK 10 のサポート

SQL Server 用 Microsoft JDBC Driver 7.0 は、Java Development Kit (JDK) バージョン 10.0 に加えて JDK 1.8 と互換性のあるようになりました。 また、この更新プログラムを公開、ドライバーの`Automatic-Module-Name`として`com.microsoft.sqlserver.jdbc`のマニフェスト ファイルを使用します。

### <a name="support-for-spatial-datatypes"></a>空間データ型のサポート

これで、SQL Server 用 Microsoft JDBC Driver 7.0 は、Geography および Geometry 空間型を SQL Server のサポートをします。 空間データ型の Api とその使用方法の詳細については、次を参照してください。[空間データ型を使用して](../../connect/jdbc/use-spatial-datatypes.md)します。

### <a name="implementation-for-jdbc-43-introduced-javasqlconnection-apis-beginrequest-and-endrequest"></a>JDBC 4.3 の実装で、java.sql.Connection の API beginRequest() と endRequest() が導入されました。

SQL Server の現在の実装用の Microsoft JDBC Driver 7.0`beginRequest()`と`endRequest()`から Api、`java.sql.Connection`クラス。 これらの Api は、JDBC 4.3 仕様と JDK 9 で導入されました。 これらの Api のドライバーの実装の詳細については、次を参照してください。 [JDBC Driver の JDBC 4.3 コンプライアンス](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md)します。

### <a name="support-for-sql-data-discovery-and-classification"></a>SQL データの検出と分類のサポート

SQL Server 用 Microsoft JDBC Driver 7.0 では、SQL データの検出と分類では、この機能をサポートする任意のターゲット データベースのサポートを提供します。 ドライバーを今すぐ公開`SQLServerResultSet.getSensitivityClassification()`にフェッチされたからこの情報を抽出するための Api`ResultSet`します。

JDBC ドライバーでこの機能を使用する方法の詳細については、サンプルを参照してください。 [SQL データの検出と分類](../../connect/jdbc/data-discovery-classification-sample.md)します。

### <a name="added-connection-property-usebulkcopyforbatchinsert"></a>接続プロパティの追加: useBulkCopyForBatchInsert

SQL Server 用 Microsoft JDBC Driver 7.0 には、新しい接続プロパティが導入されています`useBulkCopyForBatchInsert`します。 このプロパティは、Azure SQL Data Warehouse に対してのみサポートします。

このプロパティは、既定で無効です。 Azure SQL Data Warehouse に大量のデータをプッシュしているときに、ユーザー アプリケーションのパフォーマンスを向上させることが有効にできます。 このプロパティを有効にすると、ユーザー指定のデータを一括コピー操作に切り替えるバッチ挿入操作の動作を変更します。 このプロパティと制限事項の詳細については、次を参照してください。[バッチの一括コピー API を使用して挿入操作](../../connect/jdbc/use-bulk-copy-api-batch-insert-operation.md)します。

### <a name="added-connection-property-cancelquerytimeout"></a>接続プロパティの追加: cancelQueryTimeout

SQL Server 用 Microsoft JDBC Driver 7.0 には、新しい接続プロパティが導入されています`cancelQueryTimeout`をキャンセルするには、`queryTimeout`で`java.sql.Connection`と`java.sql.Statement`オブジェクト。

### <a name="added-azure-key-vault-provider-constructors"></a>追加された Azure Key Vault Provider コンス トラクター

SQL Server 用 Microsoft JDBC Driver 7.0 以前に削除したコンス トラクターを再導入の`SQLServerColumnEncryptionAzureKeyVaultProvider`します。 経由で実装するカスタム メソッドを通じて認証が許可される`SQLServerKeyVaultAuthenticationCallback`をアクセス トークンをフェッチします。

新しいコンス トラクターは、次の定義を含めます。

```java
/* This constructor is added to provide backward compatibility with 6.0
* version of the driver. It is marked deprecated for removal in the next
* stable release.
*/
@Deprecated
public SQLServerColumnEncryptionAzureKeyVaultProvider(
        SQLServerKeyVaultAuthenticationCallback authenticationCallback,
        ExecutorService executorService) throws SQLServerException;

/*New constructor to replace the above constructor*/
public SQLServerColumnEncryptionAzureKeyVaultProvider(
            SQLServerKeyVaultAuthenticationCallback authenticationCallback) throws SQLServerException;
```

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-160"></a>"Microsoft Azure Active Directory Authentication Library (ADAL4J) for Java" バージョン: 1.6.0 に更新

SQL Server 用 Microsoft JDBC Driver 7.0 がバージョン 1.6.0 に「Microsoft Azure Active Directory 認証ライブラリ (ADAL4J) Java の」で、Maven の依存関係を更新します。 依存関係の詳細については、次を参照してください。 [for SQL Server、Microsoft JDBC Driver の依存関係をフィーチャー](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)します。

## <a name="updates-in-microsoft-jdbc-driver-64-for-sql-server"></a>Microsoft JDBC Driver 6.4 for SQL Server の更新された機能

SQL Server 用 Microsoft JDBC Driver 6.4 は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 6.4 パッケージ内の jar が Java のバージョンの互換性の名前です。 たとえば、6.4 パッケージから mssql-jdbc-6.4.0.jre8.jar ファイルは、Java 8 で使用する必要があります。

### <a name="support-for-jdk-9"></a>JDK 9 のサポート

ドライバーには、JDK バージョン 9.0 に加えて、JDK 8.0、および 7.0 がサポートしています。

### <a name="jdbc-43-compliance"></a>JDBC 4.3 コンプライアンス

ドライバーでは、Java Database Connectivity API 4.1 および 4.2 に加えて、4.3 の仕様もサポートされます。 JDBC 4.3 API メソッドは追加が、まだ実装されていません。 詳細については、「[JDBC Driver の JDBC 4.3 への準拠](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md)」をご覧ください。

### <a name="added-connection-property-sslprotocol"></a>接続プロパティの追加: sslProtocol

新しい接続プロパティを使用して、TLS プロトコルのキーワードを指定できます。 有効な値は次のとおりです。"TLS"、"TLSv1"、"TLSv1.1"および"TLSv1.2"。 詳細については、次を参照してください。 [SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol)します。

### <a name="deprecated-connection-property-fipsprovider"></a>接続プロパティを非推奨とされます: fipsProvider

接続プロパティ`fipsProvider`受け入れられた接続プロパティの一覧から削除されます。 詳細については、関連する [GitHub pull request](https://github.com/Microsoft/mssql-jdbc/pull/460) を参照してください。

### <a name="added-connection-properties-for-specifying-a-custom-trustmanager"></a>カスタムの TrustManager を指定する追加の接続プロパティ

サポートとカスタム TrustManager を指定する追加のドライバー`trustManagerClass`と`trustManagerConstructorArg`接続のプロパティ。 Java 仮想マシン (JVM) 環境のグローバル設定を変更することがなく接続ごとに、一連の信頼されている証明書を動的に指定できます。

### <a name="added-support-for-datetimesmalldatetime-in-table-valued-parameters"></a>テーブル値パラメーターで datetime または smalldatetime 型のサポートが追加されました

ドライバーでは、データ型をサポート`datetime`と`smallDatetime`テーブル値パラメーター (Tvp) を使用している場合。

### <a name="added-support-for-the-sqlvariant-datatype"></a>Sql_variant データ型のサポートが追加されました

JDBC ドライバーになりました`sql_variant`SQL Server で使用するデータ型。 `sql_variant`データ型は Tvp と、次の制限を使用した一括コピーなどの機能もサポートされます。

* **日付の値の場合**: 

  含むテーブルを作成するを TVP を使用しているときに`datetime`、 `smalldatetime`、または`date`に格納された値、`sql_variant`列、呼び出し元、 `getDateTime()`、 `getSmallDateTime()`、または`getDate()`結果セットに対してメソッドが機能しないと次の例外がスローされます。

  `java java.lang.String cannot be cast to java.sql.Timestamp`
    
  この問題を回避するには、使用、`getString()`または`getObject()`メソッド代わりにします。

* **null 値に対して TVP を sql_variant と共に使用する**:
  
  TVP を使用して、テーブルを作成して、NULL 値を送信する場合、`sql_variant`列の種類、例外が発生します。 列の型と NULL 値を挿入する`sql_variant`TVP は現在サポートされていません。

### <a name="implemented-prepared-statement-metadata-caching"></a>準備されたステートメント メタデータ キャッシュの実装

JDBC ドライバーでは、パフォーマンスを向上させるための準備されたステートメント メタデータ キャッシュを実装しました。 ドライバーがドライバーで準備されたステートメント メタデータをキャッシュをサポートして今すぐ`disableStatementPooling`と`statementPoolingCacheSize`接続のプロパティ。 この機能は、既定では無効化されています。 詳細については、次を参照してください。 [JDBC Driver のステートメント メタデータ キャッシュを準備](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)します。

### <a name="added-support-for-azure-ad-integrated-authentication-on-linuxmac"></a>Linux または Mac での Azure AD 統合認証のサポートが追加されました

JDBC ドライバーでは、サポート対象のすべてのオペレーティング システム (Windows、Linux、Mac) 上で Kerberos を使った Azure Active Directory (Azure AD) 統合認証がサポートされるようになりました。 または、Windows オペレーティング システムでは、ユーザーは sqljdbc_auth.dll で認証できます。

### <a name="updated-microsoft-azure-active-directory-authentication-library-adal4j-for-java-version-140"></a>"Microsoft Azure Active Directory Authentication Library (ADAL4J) for Java" バージョン: 1.4.0 に更新

JDBC Driver がバージョン 1.4.0 に「Microsoft Azure Active Directory 認証ライブラリ (ADAL4J) Java の」で、Maven の依存関係を更新します。 依存関係の詳細については、次を参照してください。 [for SQL Server、Microsoft JDBC Driver の依存関係をフィーチャー](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)します。

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>Microsoft JDBC Driver 6.2 for SQL Server の更新された機能

Microsoft JDBC Driver 6.2 for SQL Server は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 6.2 パッケージ内の jar が Java のバージョンの互換性の名前です。 たとえば、6.2 のパッケージから mssql-jdbc-6.2.2.jre8.jar ファイルは Java 8 で使用するためお勧めします。

> [!NOTE]  
> 2017 年 6 月 29 日にリリースされた JDBC 6.2 RTW でのメタデータ キャッシュの改善により、問題が見つかりました。 改善がロールバックされ、新しい jar (バージョン 6.2.1) は、2017 年 7 月 17 日にリリースされました。 
>
> 機能の強化、1.0.0 に Azure Key Vault の依存するライブラリのバージョンをアップグレードして、新しい jar (版 6.2.2) は、2017 年 10 月 19 日にリリースされました。
>
> 最新の更新プログラムのダウンロードから JDBC Driver 6.2 for [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/?linkid=852460)、 [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2)と[Maven Central](https://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22)します。 6.2.2 を使用するプロジェクトを更新してください jar をリリースします。 詳細については、表示のリリース ノート[6.2.1](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1)と[6.2.2](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.2)します。

### <a name="azure-ad-support-for-linux"></a>Linux 用 azure AD のサポート

ユーザー名/パスワードおよびそのアクセス トークンの方法を使用して Azure AD 認証を使用して Azure SQL Database に、Linux アプリケーションを接続します。

### <a name="fips-enabled-jvms"></a>FIPS 対応 Jvm

JDBC Driver は、Jvm の準拠状態に関する連邦政府の基準を満たしての連邦情報処理規格 (FIPS) 140 準拠モードで実行されているで今すぐ使用できます。

### <a name="kerberos-authentication-improvements"></a>Kerberos 認証の機能強化

JDBC ドライバーでは、サポートできるようになりました。

- プリンシパル/パスワード メソッド アプリケーションまたは Kerberos の構成が変更することはできません、新しいトークンまたは keytab を取得できません。 このメソッドは、Kerberos 認証のみを許可する SQL Server インスタンスへの認証に使用できます。
- サーバーの SPN を明示的に設定しなくても Kerberos 統合認証を使用して領域間の認証。 ドライバー今すぐ自動的に計算されます、領域が提供されていない場合でもです。
- そのまま使用して Kerberos の制約付き委任は、データ ソースを使用して、GSS 資格情報オブジェクトとしてユーザーの資格情報を偽装します。 この権限を借用した資格情報を使用し、Kerberos の接続を確立します。

### <a name="added-timeouts"></a>追加のタイムアウト

JDBC Driver は、次の構成可能なタイムアウトをサポートします。 アプリケーションのニーズに基づいてそれらを変更できます。

- タイムアウトするまで待機する秒数を制御するクエリのタイムアウトは、クエリを実行しているときに発生します。
- ソケットのタイムアウトが発生する前に待機するミリ秒数を指定するソケットのタイムアウトは、読み取りまたはそのまま使用します。

## <a name="updates-in-microsoft-jdbc-driver-61-for-sql-server"></a>Microsoft JDBC Driver 6.1 for SQL Server の更新された機能

SQL Server 用 Microsoft JDBC Driver 6.1 が 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 これは、JDBC ドライバーの最初のオープン ソース リリースです。 Java のバージョンの互換性に対応する mssql-jdbc-6.1.0.jre8.jar と mssql-jdbc-6.1.0.jre7.jar ファイルが含まれています。

## <a name="updates-in-microsoft-jdbc-driver-60-for-sql-server"></a>Microsoft JDBC Driver 6.0 for SQL Server の更新された機能

Microsoft JDBC Driver 6.0 for SQL Server は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 Jar を 6.0 のパッケージの名前は、JDBC API のバージョンに準拠してです。 たとえば、6.0 パッケージから sqljdbc42.jar ファイルは、JDBC API 4.2 に準拠してが。 同様に、sqljdbc41.jar ファイルは、JDBC API 4.1 準拠です。

適切な sqljdbc42.jar または sqljdbc41.jar ファイルがあることを確認するには、次のコード行を実行します。 出力する場合は"ドライバーのバージョン。6.0.7507.100"、JDBC Driver 6.0 パッケージがあります。

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="always-encrypted"></a>Always Encrypted

ドライバーでは、SQL Server 2016 では、Always Encrypted 機能をサポートしています。 この機能により機密データを SQL Server インスタンスにプレーン テキストで見たようになります。 Always Encrypted はアプリケーション内のデータを透過的に暗号化することによって動作します。そのため、SQL Server では暗号化データのみが処理され、プレーンテキスト値は処理されません。 SQL Server のインスタンスまたはホスト コンピューターが侵害されたとしても、攻撃者が取得できるものは機密データの暗号化テキストだけになります。 詳細については、「[JDBC ドライバーでの Always Encrypted の使用](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)」をご覧ください。

### <a name="internationalized-domain-names"></a>国際化ドメイン名

ドライバーは、サーバー名の国際化ドメイン名 (Idn) をサポートします。 詳細については、「を使用した国際化ドメイン名」を参照してください、 [JDBC Driver の国際化機能](../../connect/jdbc/international-features-of-the-jdbc-driver.md)記事。

### <a name="parameterized-queries"></a>パラメーター化クエリ

ドライバーで、サブクエリや結合など、複雑なクエリのために準備されたステートメントを使ったパラメーター メタデータの取得がサポートされました。 この機能強化を使用できるのは、SQL Server 2012 以降のバージョンを使用している場合のみであることに注意してください。

### <a name="azure-active-directory"></a>Azure Active Directory

Azure AD 認証は、Azure ad の id を使用して Azure SQL Database v12 に接続するメカニズムです。 Azure AD 認証は、データベース ユーザーの ID を一元管理するために、SQL Server 認証の代替として使用します。 

JDBC Driver 6.0 を使用して、Azure SQL Database に接続するための JDBC 接続文字列で、Azure AD 資格情報を指定することができます。 詳細については、認証プロパティを参照してください、[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)記事。

### <a name="table-valued-parameters"></a>テーブル値パラメーター

TVP は、複数行のデータをクライアント アプリケーションから SQL Server に簡単にマーシャリングするための手段です。複数のラウンド トリップや、データ処理用の特別なサーバー側ロジックは必要ありません。 TVP を使用すると、1 つのパラメーター化コマンドで、クライアント アプリケーションで複数行のデータをカプセル化し、そのデータをサーバーに送信できます。 受信データ行は、TRANSACT-SQL を使用してでを操作できるテーブル変数に格納されます。 詳細については、次を参照してください。[テーブル値パラメーターを使用して](../../connect/jdbc/using-table-valued-parameters.md)します。

### <a name="always-on-availability-groups"></a>Always On 可用性グループ

ドライバーは、Always On 可用性グループへの透過的な接続をサポートします。 ドライバーによってサーバー インフラストラクチャの現在の Always On トポロジがすばやく検出され、現在アクティブなサーバーに透過的に接続されます。

## <a name="updates-in-microsoft-jdbc-driver-42-for-sql-server-and-later"></a>Microsoft JDBC Driver 4.2 for SQL Server 以降の更新された機能

Microsoft JDBC Driver 4.2 for SQL Server は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 Jar を 4.2 のパッケージの名前は、JDBC API のバージョンに準拠してです。 たとえば、4.2 のパッケージから sqljdbc42.jar ファイルは、JDBC API 4.2 に準拠してが。 同様に、sqljdbc41.jar ファイルは、JDBC API 4.1 準拠です。

確認するには、適切な sqljdbc42.jar または sqljdbc41.jar ファイルを次のコード行を実行があります。 出力する場合は"ドライバーのバージョン。4.2.6420.100"、JDBC Driver 4.2 のパッケージがあります。

```java
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```

### <a name="support-for-jdk-8"></a>JDK 8 のサポート

ドライバーは、JDK 8.0 JDK 7.0 だけでなく、6.0、および 5.0 バージョンをサポートします。

### <a name="jdbc-41-and-42-compliance"></a>JDBC 4.1 および 4.2 への準拠

ドライバーで、Java Database Connectivity API 4.0 だけでなく、4.1 と 4.2 の仕様もサポートされるようになりました。 詳細については、次を参照してください。 [JDBC Driver の JDBC 4.1 準拠](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md)と[JDBC Driver の JDBC 4.2 コンプライアンス](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md)します。

### <a name="bulk-copy"></a>一括コピー

一括コピー機能を使うと、SQL Server データベースのテーブルまたはビューに大量のデータを簡単にコピーできます。 詳細については、「[JDBC ドライバーでの一括コピーの使用](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md)」をご覧ください。

### <a name="xa-transaction-rollback-option"></a>XA トランザクション ロールバック オプション

既存の準備解除されたトランザクションの自動ロールバックに向けた、新しいタイムアウト オプションがドライバーに追加されました。 詳細については、次を参照してください。[理解 XA トランザクション](../../connect/jdbc/understanding-xa-transactions.md)です。

### <a name="new-kerberos-principal-connection-property"></a>新しい Kerberos プリンシパル接続プロパティ

Kerberos 接続での柔軟性を強化するために、ドライバーで新しい接続プロパティが使用されます。 詳細については、「[Kerberos 統合認証による SQL Server への接続](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)」をご覧ください。

## <a name="updates-in-microsoft-jdbc-driver-41-for-sql-server-and-later"></a>Microsoft JDBC Driver 4.1 for SQL Server 以降の更新された機能

### <a name="support-for-jdk-7"></a>JDK 7 のサポート

ドライバーは、JDK バージョン 7.0 も JDK 6.0、5.0 をサポートします。

## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Itanium では JDBC Driver 6.4、6.0、4.2、4.1 アプリケーションがサポートされない

Microsoft JDBC Drivers 6.4、6.0、4.2、4.1 for SQL Server アプリケーションは、Itanium コンピューター上での実行がサポートされていません。

## <a name="see-also"></a>参照

[JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)
