---
title: "JDBC ドライバーのリリース ノート |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 074f211e-984a-4b76-bb15-ee36f5946f12
caps.latest.revision: 206
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bd65725237fd625c40f8755e636bb4f6fa2c55ea
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="release-notes-for-the-jdbc-driver"></a>JDBC ドライバーのリリース ノート
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

## <a name="updates-in-microsoft-jdbc-driver-62-for-sql-server"></a>SQL Server 用 Microsoft JDBC Driver 6.2 で更新プログラム
SQL Server 用 Microsoft JDBC Driver 6.2 は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 Java バージョンの互換性に応じて 6.0 のパッケージに含まれる jar と呼びます。 たとえば、Java 8 で使用する 6.2 パッケージから mssql jdbc-6.2.1.jre8.jar ファイルをお勧めします。 

**注:** 2017 年 6 月 29 日にリリースされた JDBC 6.2 RTW でメタデータの向上をキャッシュに問題が見つかりました。 改善されたロールバックされ、新しい jar ファイル (バージョン 6.2.1) は、2017 年 7 月 17 日にリリースされた、 [Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/?linkid=852460)、 [GitHub](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1)、および[Maven 中央](http://search.maven.org/#search%7Cgav%7C1%7Cg%3A%22com.microsoft.sqlserver%22%20AND%20a%3A%22mssql-jdbc%22)します。 6.2.1 を使用するプロジェクトを更新してください jar ファイルを解放します。 参照してください[リリース ノート](https://github.com/Microsoft/mssql-jdbc/releases/tag/v6.2.1)詳細についてはします。

**Linux 用 azure Active Directory (AAD) のサポート**

ユーザー名/パスワードおよびそのアクセス トークンの方法を使用して AAD 認証を使用して Azure SQL データベースに、Linux アプリケーションに接続します。

**連邦情報処理規格 (FIPS) には、Jvm が有効になっています。**

JDBC ドライバーは、Jvm を連邦政府の規格とコンプライアンスを満たすために FIPS 140 準拠モードで実行されているで現在使用できます。 

**Kerberos 認証の機能強化** 

JDBC ドライバーでは、サポートできるようになりました。 
* プリンシパル/パスワード メソッドのアプリケーションの Kerberos 構成が変更済み、または新しいトークンまたは keytab を取得できません。 をすることはできません。 このメソッドは、Kerberos 認証のみを許可する SQL Server への認証に使用できます。 
* 領域間のサーバーの SPN を明示的に設定しなくても Kerberos 統合認証を使用して認証します。 ドライバーここで自動的に計算されますレルム指定されていない場合でもです。
* そのまま使用して Kerberos 制約付き委任は、データ ソースを介して GSS の資格情報オブジェクトとしてユーザーの資格情報を偽装します。 この権限を借用した資格情報は Kerberos 接続を確立するために使用されます。 

**追加のタイムアウト**

JDBC ドライバーでは、次構成可能なタイムアウトを変更することができます、アプリケーションのニーズに基づいてできるようになりました。 
* タイムアウトするまで待機する秒数を制御するクエリのタイムアウトは、クエリを実行するときに発生します。 
* ソケットのタイムアウトが発生する前に待機するミリ秒数を指定するソケットのタイムアウトは、読み取るか、受け入れます。 

## <a name="updates-in-microsoft-jdbc-driver-61-for-sql-server"></a>Microsoft JDBC Driver 6.1 for SQL Server での更新

SQL Server 用 Microsoft JDBC Driver 6.1 が 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 これは、JDBC ドライバーのオープン ソースの初期リリースであり、Java バージョンの互換性に対応する mssql jdbc-6.1.0.jre8.jar mssql jdbc-6.1.0.jre7.jar ファイルが含まれます。 

## <a name="updates-in-microsoft-jdbc-driver-60-for-sql-server"></a>Microsoft JDBC Driver 6.0 for SQL Server での更新

Microsoft JDBC Driver 6.0 for SQL Server は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 6.0 のパッケージに含まれている jar ファイルは、JDBC API のバージョンに準拠してに従って付けられます。 たとえば、6.0 のパッケージから sqljdbc42.jar ファイルは、JDBC API 4.2 準拠が。 同様に、sqljdbc41.jar ファイルは、JDBC API 4.1 に準拠しています。

右 sqljdbc42.jar または sqljdbc41.jar をしたことを確認するには、するには、次のコード行を実行します。 出力は次の場合"ドライバーのバージョン: 6.0.7507.100"、JDBC Driver 6.0 パッケージがあります。
```
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```  
 **Always Encrypted**  
  
 SQL Server 2016 で確実に機密性の高いデータは、SQL Server インスタンスにプレーン テキストで表示されることは、新しいセキュリティ機能で最近リリースされた Always Encrypted 機能のサポート。 Always Encrypted は透過的な機能で、アプリケーション内のデータの暗号化を行います。SQL Server は暗号化データのみを扱い、プレーンテキスト値は処理しません。 SQL インスタンスまたはホスト コンピューターが侵害された場合でも、攻撃者が取得できるは機微なデータの暗号文です。 詳細をご覧ください[JDBC ドライバーで Always Encrypted を使用して](../../connect/jdbc/using-always-encrypted-with-the-jdbc-driver.md)です。  
  
 **国際化ドメイン名 (IDN)**  
  
 サーバー名に関する国際化ドメイン名 (IDN) をサポートします。 詳細情報に関する国際ドメイン名の使用を参照してください、 [JDBC ドライバーの国際対応機能](../../connect/jdbc/international-features-of-the-jdbc-driver.md)ページ。  
  
 **パラメーター化クエリ**  
  
 サブクエリや結合などの複雑なクエリで、準備されたステートメントを使用したパラメーター メタデータの取得をサポートできるようになりました。 なお、この機能強化を利用できるのは、SQL Server 2012 以降のバージョンを使用する場合に限られます。  
  
 **Azure Active Directory (AAD)**  
  
 AAD 認証は、Azure SQL Database v12 への接続のメカニズム AAD の id を使用します。 SQL Server 認証の代わりとしてのデータベース ユーザーの id を一元的に管理するのにには、AAD 認証を使用します。 JDBC Driver 6.0 では、Azure SQL DB に接続する JDBC 接続文字列に AAD 資格情報を指定することができます。  詳細情報の認証プロパティを参照してください、[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)ページ。  
  
 **テーブル値パラメーター**  
  
 テーブル値パラメーターは、データを処理する複数のラウンド トリップや特別なサーバー側ロジックを必要とせず複数行の SQL Server へのクライアント アプリケーションからデータをマーシャ リングする簡単な方法を提供します。 テーブル値パラメーターを使用して、クライアント アプリケーション内のデータの行をカプセル化し、1 つのパラメーター化コマンド内のサーバーにデータを送信することができます。 受信データ行は、処理できる Transact SQL を使用してテーブル変数に格納されます。 詳細をご覧ください[Using Table-Valued パラメーター](../../connect/jdbc/using-table-valued-parameters.md)です。  
  
 **AlwaysOn 可用性グループ (AG)**  
  
 ドライバーでは、AlwaysOn 可用性グループへの透過的な接続できるようになりました。 ドライバーはすぐに、サーバー インフラストラクチャの現在の AlwaysOn トポロジを検出し、透過的には、現在アクティブなサーバーに接続します。  
  
## <a name="updates-in-microsoft-jdbc-driver-42-for-sql-server-and-later"></a>Microsoft JDBC Driver 4.2 for SQL Server 以降の更新された機能  
Microsoft JDBC Driver 4.2 for SQL Server は 4.1 と 4.2 の JDBC 仕様に完全に準拠します。 4.2 のパッケージに含まれる jar ファイルは、JDBC API のバージョンに準拠してに従って付けられます。 たとえば、4.2 のパッケージから sqljdbc42.jar ファイルは、JDBC API 4.2 準拠が。 同様に、sqljdbc41.jar ファイルは、JDBC API 4.1 に準拠しています。

右 sqljdbc42.jar または sqljdbc41.jar をしたことを確認するには、するには、次のコード行を実行します。 出力は次の場合"ドライバーのバージョン: 4.2.6420.100"、JDBC Driver 4.2 のパッケージがあります。
```
Connection conn = DriverManager.getConnection("jdbc:sqlserver://<server>;user=<user>;password=<password>;");
System.out.println("Driver version: " + conn.getMetaData().getDriverVersion());
```
 **JDK 8 のサポート**  
  
 Java Development Kit (JDK) 8.0 に加えて JDK 7.0、6.0、および 5.0 バージョン用のサポート。  
  
 **JDBC 4.1 と 4.2 のコンプライアンス**  
  
 Java Database Connectivity API 4.0 だけでなく、4.1、および 4.2 の仕様もサポートするようになりました。 詳細をご覧ください[JDBC Driver の JDBC 4.1 準拠](../../connect/jdbc/jdbc-4-1-compliance-for-the-jdbc-driver.md)と[JDBC Driver の JDBC 4.2 準拠](../../connect/jdbc/jdbc-4-2-compliance-for-the-jdbc-driver.md)です。  
  
 **一括コピー**  
  
 一括コピー機能を使用すると、SQL Server データベースのテーブルまたはビューに大量のデータを迅速にコピーできます。 詳細をご覧ください[JDBC ドライバーで一括コピーを使用して](../../connect/jdbc/using-bulk-copy-with-the-jdbc-driver.md)です。  
  
 **XA トランザクション ロールバック オプション**  
  
 準備解除されたトランザクションを自動的にロールバックする既存のオプションに、新しいタイムアウト オプションが追加されました。 詳細についてを参照してください。 [XA トランザクションについて](../../connect/jdbc/understanding-xa-transactions.md)です。  
  
 **新しい Kerberos プリンシパル接続プロパティ**  
  
 Kerberos 接続に、柔軟な処理を行うための新しい接続プロパティが追加されました。 詳細についてを参照してください。[を使用して Kerberos 統合認証を SQL Server への接続](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)です。  
  
## <a name="updates-in-microsoft-jdbc-driver-41-for-sql-server-and-later"></a>Microsoft JDBC Driver 4.1 for SQL Server 以降の更新された機能  
 **JDK 7 のサポート**  
  
 Java Development Kit (JDK) バージョン 5.0 および 6.0 だけでなく、JDK 7.0 もサポートするようになりました。  
  
## <a name="updates-in-microsoft-jdbc-driver-40-for-sql-server-and-later"></a>Microsoft JDBC Driver 4.0 for SQL Server 以降の更新された機能  
 **Azure SQL Database への接続に関する情報**  
  
 Azure SQL Database への接続に関するトピックが追加されました。 参照してください[Azure SQL database への接続](../../connect/jdbc/connecting-to-an-azure-sql-database.md)詳細についてはします。  
  
 **高可用性、災害復旧のサポート**  
  
 高可用性、障害復旧接続での AlwaysOn 可用性グループのサポート[!INCLUDE[ssSQL11](../../includes/sssql11_md.md)]です。 参照してください[High Availability, Disaster Recovery の JDBC ドライバー サポート](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)詳細についてはします。  
  
 **Kerberos 統合認証を使用して SQL Server に接続**  
  
 接続するアプリケーションのタイプ 4 の Kerberos 統合認証のサポート[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 詳細については、次を参照してください。[を使用して Kerberos 統合認証を SQL Server への接続](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)です。 (タイプ 2 の Kerberos 統合認証で使用できる[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]4.0 より前のバージョンです)。  
  
 **拡張イベント ログの診断情報にアクセスします。**  
  
 サーバーの拡張イベント ログにアクセスして、接続エラーに関する情報を得ることができます。 詳細については、次を参照してください。[へのアクセス ログの診断情報、拡張イベント](../../connect/jdbc/accessing-diagnostic-information-in-the-extended-events-log.md)です。  
  
 **スパース列の追加のサポート**  
  
 スパース列が使用されているテーブル内のデータに既にアクセスしているアプリケーションでは、パフォーマンスが向上します。 列 (スパース列の情報を含む) に関する情報を取得できる[getColumns メソッド & #40 です。SQLServerDatabaseMetaData &#41;](../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md). 詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]、スパース列を参照してください[スパース列の使用](http://go.microsoft.com/fwlink/?LinkId=224244)です。  
  
 **Xid.getFormatId**  
  
 以降で[!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]、JDBC ドライバーは、アプリケーションをデータベース サーバーから形式識別子を渡します。 このように動作を更新するには、サーバー上の sqljdbc_xa.dll が更新されていることをご確認ください。 更新のバージョンの sqljdbc_xa.dll をサーバーにコピーする方法の詳細については、次を参照してください。 [XA トランザクションについて](../../connect/jdbc/understanding-xa-transactions.md)です。  
  
## <a name="itanium-not-supported-for-jdbc-driver-60-42-41-and-40-applications"></a>Itanium JDBC Driver 6.0、4.2、4.1、4.0 アプリケーションがサポートされません。  
  
 Microsoft JDBC Drivers 6.0、4.2、4.1、および 4.0 for SQL Server アプリケーションは、Itanium コンピューター上で実行するサポートされていません。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

