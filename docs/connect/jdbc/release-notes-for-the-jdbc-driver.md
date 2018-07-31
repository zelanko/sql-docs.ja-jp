---
title: JDBC ドライバーのリリース ノート |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
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
ms.openlocfilehash: 1ec71defcba0a6f122d3c3ff9a098e163f07079c
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38021128"
---
# <a name="release-notes-for-the-jdbc-driver"></a>JDBC Driver のリリース ノート
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-64-for-sql-server"></a>Microsoft JDBC Driver 6.4 for SQL Server の更新された機能
SQL Server 用 Microsoft JDBC Driver 6.4 は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 6.4 パッケージに含まれる jar が Java のバージョンの互換性の名前です。 たとえば、Java 8 で使用する 6.4 パッケージから mssql-jdbc-6.4.0.jre8.jar ファイルがお勧めします。 

**JDK 9 のサポート**  
  
Java Development Kit (JDK) バージョン 8.0 および 7.0 だけでなく、JDK 9.0 もサポートするようになりました。
  
**JDBC 4.3 コンプライアンス**  
  
Java Database Connectivity API 4.1 および 4.2 だけでなく、4.3 の仕様もサポートするようになりました。 JDBC 4.3 API メソッドは追加が、まだ実装されていません。 詳細を参照してください[JDBC Driver の JDBC 4.3 準拠](../../connect/jdbc/jdbc-4-3-compliance-for-the-jdbc-driver.md)します。
 
**新しい接続プロパティの追加: sslProtocol**

ユーザーが TLS プロトコルのキーワードを指定できるようにする新しい接続プロパティを追加します。 値:"TLS"、"TLSv1"、"TLSv1.1"、"TLSv1.2"。 参照してください[SSLProtocol](https://github.com/Microsoft/mssql-jdbc/wiki/SSLProtocol)詳細についてはします。

**接続プロパティを非推奨とされます: fipsProvider**

接続のプロパティ"fipsProvider"は、受け入れられた接続プロパティの一覧から削除されます。 詳細を参照してください。[ここ](https://github.com/Microsoft/mssql-jdbc/pull/460)します。

**カスタムの TrustManager を指定する追加の接続プロパティ**

接続プロパティ "trustManagerClass" と "trustManagerConstructorArg" の追加により、ドライバーでカスタムの TrustManager を指定できるようになりました。 'trustManagerConstructorArg' が使用されます。これにより、JVM 環境のグローバル設定を変更することがなく、接続ごとに信頼されている証明書の一連の動的な指定。

**テーブル値パラメーター (TVP) での datetime または smalldatetime 型のサポートが追加されました**

テーブル値パラメーター (TVP) を使用するときに、ドライバーでデータ型 DATETIME と SMALLDATETIME がサポートされるようになりました。

**Sql_variant データ型のサポートが追加されました**

JDBC Driver は、SQL Server で使用される sql_variant データ型をサポートします。 Sql_variant は制限事項の下で BulkCopy テーブル値パラメーター (TVP) などの機能でもサポートされています。

1. 日付の値: TVP を使用して値を入れるテーブルで datetime/smalldatetime/date の値が sql_variant 列に格納されているときは、getDateTime()/getSmallDateTime()/getDate() メソッドを結果セットに対して呼び出しても機能せず、次の例外が返されます。
    ```
    java.lang.String cannot be cast to java.sql.Timestamp
    ```
    回避策: "getString()" メソッドまたは "getObject()" メソッドを代わりに使用します。

2. TVP を null 値の SQL VARIANT とともに使用する

TVP を使用してテーブルに値を入れるときに NULL 値を sql_variant 型の列に送ると、例外が発生します。TVP で NULL 値を sql_variant 型の列に挿入することは現時点ではサポートされていないためです。

TVP で NULL 値を sql_variant 型の列に挿入することは現時点ではサポートされていないためです。**準備されたステートメントが実装されているメタデータのキャッシュ**

JDBC Driver は、実装ステートメント メタデータ キャッシュの準備パフォーマンスが向上します。 プリペアド ステートメントのメタデータをドライバー内でキャッシュできるようになりました。これには接続プロパティ "disableStatementPooling" と "statementPoolingCacheSize" が使用されます。 この機能は、既定では無効化されています。 詳細は[こちら](../../connect/jdbc/prepared-statement-metadata-caching-for-the-jdbc-driver.md)をご覧ください。

**Linux または Mac で AAD 統合認証のサポートが追加されました**

JDBC ドライバーで Azure Active Directory 統合認証も、サポート対象のすべてのオペレーティング システム (Windows/Linux/Mac) で Kerberos とともにサポートされるようになりました。 Kerberos とともにサポートされるようになりました。または、Windows オペレーティング システムでは、ユーザーを認証できます sqljdbc_auth.dll の。

**更新された ADAL4J バージョン 1.4.0**

JDBC ドライバーがバージョン 1.4.0 に azure active directory-ライブラリ-の-java (ADAL4J) 時に、maven の依存関係を更新します。 依存関係の詳細についてを参照してください[ここ](../../connect/jdbc/feature-dependencies-of-microsoft-jdbc-driver-for-sql-server.md)

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>Microsoft JDBC Driver 6.2 for SQL Server の更新された機能
Microsoft JDBC Driver 6.2 for SQL Server は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 6.0 パッケージに含まれる jar が Java のバージョンの互換性の名前です。 たとえば、Java 8 で使用する 6.2 パッケージから mssql-jdbc-6.2.1.jre8.jar ファイルがお勧めします。 

> [!NOTE]  
>  2017 年 6 月 29 日にリリースされた JDBC 6.2 RTW でのメタデータ キャッシュの改善により、問題が見つかりました。 改善がロールバックされ、新しい jar (バージョン 6.2.1) は、上、2017 年 7 月 17 日にリリースされた、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/?linkid=852460)、 [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1)、および[Maven Central](http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22)します。 6.2.1 を使用するプロジェクトを更新してください jar をリリースします。 参照してください[リリース ノート](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1)の詳細。

**Linux 用 azure Active Directory (AAD) のサポート**

ユーザー名/パスワードおよびそのアクセス トークンの方法を使用して AAD 認証を使用して Azure SQL Database に、Linux アプリケーションを接続します。

**連邦情報処理規格 (FIPS) には、Jvm が有効になっています。**

JDBC Driver は、Jvm 連邦標準およびコンプライアンスを満たすために FIPS 140 準拠モードで実行されているで今すぐ使用できます。 

**Kerberos 認証の機能強化** 

JDBC ドライバーでは、サポートできるようになりました。 
* プリンシパル/パスワード メソッド アプリケーションの Kerberos の構成が変更または新しいトークンまたは keytab を取得できませんにすることはできません。 このメソッドは、Kerberos 認証のみを許可する SQL Server への認証に使用できます。 
* 領域間のサーバーの SPN を明示的に設定しなくても Kerberos 統合認証を使用して認証します。 ドライバー今すぐ自動的に計算されますレルム指定されていない場合でもです。
* そのまま使用して Kerberos の制約付き委任は、データ ソースを使用して、GSS 資格情報オブジェクトとしてユーザーの資格情報を偽装します。 この権限を借用した資格情報を使用し、Kerberos の接続を確立します。 

**追加のタイムアウト**

JDBC ドライバーでは、次構成可能なタイムアウトを変更することができます、アプリケーションのニーズに基づいてできるようになりました。 
* タイムアウトするまで待機する秒数を制御するクエリのタイムアウトは、クエリを実行するときに発生します。 
* ソケットのタイムアウトが発生する前に待機するミリ秒数を指定するソケットのタイムアウトは、読み取りまたはそのまま使用します。 

## <a name="updates-in-microsoft-jdbc-driver-61-for-sql-server"></a>Microsoft JDBC Driver 6.1 for SQL Server の更新された機能

SQL Server 用 Microsoft JDBC Driver 6.1 が 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 これは、JDBC ドライバーのオープン ソースの初期リリースであり、Java のバージョンの互換性に対応する mssql-jdbc-6.1.0.jre8.jar mssql-jdbc-6.1.0.jre7.jar ファイルが含まれます。 

## <a name="updates-in-microsoft-jdbc-driver-60-for-sql-server"></a>Microsoft JDBC Driver 6.0 for SQL Server の更新された機能

Microsoft JDBC Driver 6.0 for SQL Server は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 6.0 パッケージに含まれる jar 名前は自らのコンプライアンスを JDBC API バージョンです。 たとえば、6.0 パッケージから sqljdbc42.jar ファイルは、JDBC API 4.2 に準拠してが。 同様に、sqljdbc41.jar ファイルは、JDBC API 4.1 準拠です。

適切な sqljdbc42.jar または sqljdbc41.jar をしたことを確認するには、次のコード行を実行します。 出力する場合は"ドライバーのバージョン: 6.0.7507.100"、JDBC Driver 6.0 パッケージがあります。
```
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```  
 **Always Encrypted**  
  
 SQL Server 2016 で最近リリースされた Always Encrypted 機能をサポートします。これは、SQL Server インスタンスで機密データがプレーンテキストで絶対に表示されないようにする新たなセキュリティ機能です。 Always Encrypted は透過的な機能で、アプリケーション内のデータの暗号化を行います。SQL Server は暗号化データのみを扱い、プレーンテキスト値は処理しません。 SQL インスタンスまたはホスト コンピューターが侵害された場合であっても、すべての攻撃者が取得できるのは機密データの暗号化テキストになります。 詳細については、「[JDBC ドライバーでの Always Encrypted の使用](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)」を参照してください。  
  
 **国際化ドメイン名 (IDN)**  
  
 サーバー名に関する国際化ドメイン名 (IDN) をサポートします。 詳細情報を使用した国際化ドメイン名を参照してください、 [JDBC Driver の国際対応](../../connect/jdbc/international-features-of-the-jdbc-driver.md)ページ。  
  
 **パラメーター化クエリ**  
  
 サブクエリや結合などの複雑なクエリで、準備されたステートメントを使用したパラメーター メタデータの取得をサポートできるようになりました。 なお、この機能強化を利用できるのは、SQL Server 2012 以降のバージョンを使用する場合に限られます。  
  
 **Azure Active Directory (AAD)**  
  
 AAD 認証は、Azure SQL Database v12 に接続するメカニズムでは、AAD の id を使用します。 AAD 認証は、データベース ユーザーの ID を一元管理するという目的で使用でき、SQL Server 認証に代わる方法となります。 JDBC Driver 6.0 では、AAD の資格情報を JDBC 接続文字列の中で指定して Azure SQL DB に接続することができます。  詳細情報を認証プロパティを参照してください、[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)ページ。  
  
 **テーブル値パラメーター**  
  
 テーブル値パラメーターは、複数行のデータをクライアント アプリケーションから SQL Server に簡単にマーシャリングするための手段です。複数のラウンド トリップや、データ処理用の特別なサーバー側ロジックは必要ありません。 テーブル値パラメーターを使用すると、クライアント アプリケーションで複数行のデータをカプセル化してサーバーに送信する処理を 1 つのパラメーター化コマンドで実行できます。 パラメーター化コマンドで実行できます。受信データ行は、TRANSACT-SQL を使用してで操作できるテーブル変数に格納されます。 詳細を参照してください[Using Table-Valued パラメーター](../../connect/jdbc/using-table-valued-parameters.md)します。  
  
 **AlwaysOn 可用性グループ (AG)**  
  
 ドライバーは、AlwaysOn 可用性グループへの透過的な接続をサポートします。 ドライバーがサーバー インフラストラクチャの現在の AlwaysOn トポロジをすばやく検出して、現在アクティブなサーバーに透過的に接続します。  
  
## <a name="updates-in-microsoft-jdbc-driver-42-for-sql-server-and-later"></a>Microsoft JDBC Driver 4.2 for SQL Server 以降の更新された機能  
Microsoft JDBC Driver 4.2 for SQL Server は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 4.2 のパッケージに含まれる jar は、JDBC API バージョンの準拠の名前です。 たとえば、4.2 のパッケージから sqljdbc42.jar ファイルは、JDBC API 4.2 に準拠してが。 同様に、sqljdbc41.jar ファイルは、JDBC API 4.1 準拠です。

適切な sqljdbc42.jar または sqljdbc41.jar をしたことを確認するには、次のコード行を実行します。 出力する場合は"ドライバーのバージョン: 4.2.6420.100"、JDBC Driver 4.2 のパッケージがあります。
```
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```
 **JDK 8 のサポート**  
  
 Java Development Kit (JDK) バージョン 5.0、6.0、および 7.0 だけでなく、JDK 8.0 もサポートするようになりました。  
  
 **JDBC 4.1 および 4.2 への準拠**  
  
 Java Database Connectivity API 4.0 だけでなく、4.1、および 4.2 の仕様もサポートするようになりました。 詳細を参照してください[JDBC Driver の JDBC 4.1 準拠](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md)と[JDBC Driver の JDBC 4.2 準拠](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md)します。  
  
 **一括コピー**  
  
 一括コピー機能を使用すると、SQL Server データベースのテーブルまたはビューに大量のデータを迅速にコピーできます。 詳細を参照してください[JDBC ドライバーで一括コピーを使用して](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md)します。  
  
 **XA トランザクション ロールバック オプション**  
  
 準備解除されたトランザクションを自動的にロールバックする既存のオプションに、新しいタイムアウト オプションが追加されました。 詳細についてを参照してください。 [XA トランザクションの概要](../../connect/jdbc/understanding-xa-transactions.md)します。  
  
 **新しい Kerberos プリンシパル接続プロパティ**  
  
 Kerberos 接続に、柔軟な処理を行うための新しい接続プロパティが追加されました。 詳細については、「[Kerberos 統合認証による SQL Server への接続](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)」を参照してください。  
  
## <a name="updates-in-microsoft-jdbc-driver-41-for-sql-server-and-later"></a>Microsoft JDBC Driver 4.1 for SQL Server 以降の更新された機能  
 **JDK 7 のサポート**  
  
 Java Development Kit (JDK) バージョン 5.0 および 6.0 だけでなく、JDK 7.0 もサポートするようになりました。  
  
## <a name="itanium-not-supported-for-jdbc-driver-64-60-42-and-41-applications"></a>Itanium では JDBC Driver 6.4、6.0、4.2、4.1 アプリケーションがサポートされない  
  
 Microsoft JDBC Drivers 6.4、6.0、4.2、4.1 for SQL Server アプリケーションは、Itanium コンピューター上での実行がサポートされていません。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

