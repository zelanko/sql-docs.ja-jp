---
title: よく寄せられる質問 (FAQ) JDBC ドライバーの |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: cbc0e397-ecf2-4494-87b2-a492609bceae
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 282f71f49eba5ccece8bc9d50ef690fd0af3cb8c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="frequently-asked-questions-faq-for-jdbc-driver"></a>よく寄せられる質問 (FAQ) JDBC driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  この記事では、Microsoft SQL Server 用 JDBC Driver についてよく寄せられる質問に対する回答をご紹介します。  
  
## <a name="frequently-asked-questions"></a>よく寄せられる質問  
**JDBC ドライバーの向上を支援する方法は?**  
JDBC ドライバーはオープン ソースと、ソース コードにある  [GitHub](https://github.com/microsoft/mssql-jdbc)です。 問題をファイリングによって、コード ベースに貢献しているドライバーを強化することができます。

**SQL Server と Java は、ドライバーのバージョンがサポートされますか。**  
 参照してください、 [Microsoft JDBC Driver for SQL Server のサポート マトリックス](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md)詳細ページ。  
  
 **どのような知っておくべきドライバーをアップグレードするときにしますか。**  
 Microsoft JDBC Driver 6.4 サポート、JDBC 4.1、4.2、および 4.3 (部分的) の仕様と、インストール パッケージに 3 つの JAR クラス ライブラリを次のように含まれています。  
  
|JAR|JDBC の仕様|JDK のバージョン|  
|-|-|-|  
|mssql-jdbc-6.4.0.jre9.jar|JDBC 4.3 (部分的)、4.2、4.1|JDK 9.0|  
|mssql-jdbc-6.4.0.jre8.jar|JDBC 4.2、4.1|JDK 8.0|  
|mssql-jdbc-6.4.0.jre7.jar|JDBC 4.1|JDK 7.0|  

 Microsoft JDBC Driver 6.2 では、JDBC 4.0、4.1、および 4.2 仕様をサポートしており、次のように、インストール パッケージに 2 つの JAR クラス ライブラリが含まれています。  
  
|JAR|JDBC の仕様|JDK のバージョン|  
|-|-|-|  
|mssql-jdbc-6.2.1.jre8.jar|JDBC 4.2、4.1、4.0|JDK 8.0|  
|mssql-jdbc-6.2.1.jre7.jar|JDBC 4.1、4.0|JDK 7.0|  
 
 Microsoft JDBC Drivers 6.0 と 4.2 for SQL Server JDBC 4.0、4.1、および 4.2 の仕様をサポートし、次のように、インストール パッケージに 2 つの JAR クラス ライブラリを含めます。  
  
|JAR|JDBC の仕様|JDK のバージョン|   
|-|-|-|  
|sqljdbc42.jar|JDBC 4.2、4.1、4.0|JDK 8.0|  
|sqljdbc41.jar|JDBC 4.1、4.0|JDK 7.0|  
  
 Microsoft JDBC Driver 4.1 for SQL Server では、JDBC 4.0 仕様をサポートしており、次のように、インストール パッケージに 1 つの JAR クラス ライブラリが含まれています。  
  
|JAR|JDBC の仕様|JDK のバージョン|    
|-|-|-|  
|sqljdbc41.jar|JDBC 4.0|JDK 7.0 および 6.0|
  
 **既存の SQL Server のバージョンで最新のドライバーを使用するアプリケーションでコード変更を加える必要がありますか。**  
 一般に、ドライバーはことで、旧バージョンと互換性のあるドライバーをアップグレードするときに、既存のアプリケーションを変更する必要はありません設計されています。 新しいドライバーのバージョンには、重大な変更が導入されている、 [JDBC ドライバーのリリース ノート](../../connect/jdbc/release-notes-for-the-jdbc-driver.md)セクションは、変更および既存のアプリケーションへの影響に明確の詳細を示します。 さらに、そのリリースと既知の問題で修正されたバグの一覧については、ドライバーに付属のリリース ノートをご覧ください。  
  
 **ドライバーの料金はいくらですか。**  
 Microsoft SQL Server 用 JDBC Driver は、追加料金なしでご利用いただけます。  
  
 **ドライバーを再配布できますか。** JDBC ドライバー 4.1、4.2、6.0、6.2、および 6.4 は再頒布可能パッケージです。 使用許諾契約を「再頒布可能コード」句を確認します。 
   
 **ドライバーを使用して Linux コンピューターから Microsoft SQL Server にアクセスできますか。** はい。 ドライバーを使用して、Linux、Unix、他の Windows 以外のプラットフォームから SQL Server にアクセスできます。 参照してください[Microsoft JDBC Driver for SQL Server のサポート マトリックス](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md)詳細についてはします。  
  
 **ドライバーは Secure Sockets Layer (SSL) 暗号化をサポートしますか。** バージョン 1.2 以降のドライバーは、Secure Sockets Layer (SSL) 暗号化をサポートしています。 詳細については、次を参照してください。 [SSL 暗号化を使用して](../../connect/jdbc/using-ssl-encryption.md)です。  
  
 **どのような認証は、SQL Server 用 Microsoft JDBC Driver でサポートされてですか。**  
 次の表は、使用可能な認証オプションを示しています。 4.0 リリース以降のドライバーでは、ピュア Java Kerberos 認証が使用可能です。  
  
|||  
|-|-|  
|プラットフォーム|[認証]|  
|Windows 以外|ピュア Java Kerberos|  
|Windows 以外|SQL Server|  
|Windows 以外|Azure Active Directory 認証|
|Windows|ピュア Java Kerberos|  
|Windows|SQL Server|
|Windows|Kerberos と NTLM バックアップ|  
|Windows|NTLM|  
|Windows|Azure Active Directory 認証|  
  
**ドライバーはサポートしてインターネット プロトコル バージョン 6 (IPv6) アドレスですか?**  
 はい。このドライバーは、接続プロパティのコレクションと serverName 接続文字列プロパティと合わせて IPv6 アドレスの使用をサポートしています。 詳細については、次を参照してください。[接続 URL の構築](../../connect/jdbc/building-the-connection-url.md)です。  
  
**アダプティブ バッファリングとは**  
 アダプティブ バッファリングは、Microsoft SQL Server 2005 JDBC Driver 1.2 以降に導入されており、サーバー カーソルのオーバーヘッドを発生させることなく、あらゆる種類の大きな値のデータを取得できるように設計されています。 Microsoft SQL Server JDBC Driver のアダプティブ バッファリング機能には接続文字列プロパティ responseBuffering があり、これを "adaptive" または "full" に設定できます。 JDBC Driver 2.0 以降では、ドライバーの既定の動作は "adaptive" です。 つまり、アプリケーションから明示的に要求しなくても、アダプティブ バッファリングの動作が適用されます。 ただし、バージョン 1.2 リリースでは、"full" が既定のバッファリング モードであるため、アプリケーションから明示的にアダプティブ バッファリング モードを要求する必要があります。 詳細については、次を参照してください。[アダプティブ バッファリングを使用して](../../connect/jdbc/using-adaptive-buffering.md)トピックとブログ。 [新機能は adaptiveresponse バッファー化および使用する理由にしますか。](http://go.microsoft.com/fwlink/?LinkId=111575)  
  
**ドライバーの接続プールをサポートしますか。**  
 ドライバーは、Java Platform, Enterprise Edition 5 (Java EE 5) の接続プールをサポートしています。 ドライバーは、ミドルウェア アプリケーション サーバー ベンダーが提供するあらゆる接続プールの実装に参加できるように、JDBC 3.0 に必要なインターフェイスを実装しています。 このドライバーは、これらの環境でプールされた接続に参加します。 詳細については、次を参照してください。[接続プールを使用して](../../connect/jdbc/using-connection-pooling.md)です。 ドライバーは独自のプール実装を提供せず、むしろサードパーティの Java アプリケーション サーバーに依存しています。  
  
**ドライバーのサポートがあるか。**  
 さまざまなサポート オプションをご利用いただけます。 質問を投稿するか、発行、 [GitHub リポジトリ](https://github.com/microsoft/mssql-jdbc)これは Microsoft によって監視します。 [フォーラム](http://go.microsoft.com/fwlink/?LinkID=246673)Microsoft、Mvp、コミュニティで監視します。 マイクロソフト カスタマー サポートにお問い合わせいただくこともできます。 開発チームでは、すべてのサード パーティのアプリケーション サーバーの外部で問題を再現するよう求められます可能性があります。 ホスティングの Java コンテナー環境の外部の問題を再現できない場合は、チームが役立つ継続できるように、関連するサード パーティが参加する必要があります。 チームはため、問題を最適なサポートされる Windows などのオペレーティング システムで問題を再現することも要求可能性があります。  
  
**ドライバーは、サード パーティのアプリケーション サーバーで使用する用に認定されていますか。**
ドライバーは、IBM WebSphere、SAP NetWeaver などのさまざまなアプリケーション サーバーに対してテスト済みです。  
  
**トレースを有効にする方法は?**  
 ドライバーはトレース (またはログ記録) の使用をサポートしているため、アプリケーションで使用するときに JDBC Driver で発生した問題の解決に役立てることができます。 クライアント側の JAR のトレースの使用を有効にするため、JDBC Driver は java.util.logging でログ記録 API を使用しています。 詳細については、次を参照してください。[ドライバー操作のトレース](../../connect/jdbc/tracing-driver-operation.md)です。 サーバー側の XA のトレースについては、「 [Data Access Tracing in SQL Server (SQL Server でのデータ アクセスのトレース)](http://go.microsoft.com/fwlink/?LinkId=248705)」をご覧ください。  
  
**古いバージョンの SQL Server 2000 JDBC ドライバー、2005年ドライバーなどのドライバーをダウンロードする場所 1.0、1.1、または 1.2 ドライバーですか?**  
 これらのバージョンのドライバーはサポートされていないため、ダウンロードできません。 Java 接続のサポート継続的に改良を進めています。 そのため、Microsoft JDBC ドライバーの最新バージョンの使用を強くお勧めします。  
  
**JRE 1.4 を使用しています。どのドライバーは、JRE 1.4 と互換性のあるですか。**  
 SAP 製品を使用していて JRE 1.4 のサポートが必要なお客様は、 [SAPService Marketplace](http://service.sap.com/) にお問い合わせの上、1.2 Microsoft JDBC ドライバーを入手してください。  
  
**ドライバー通信できる FIPS 検証アルゴリズムを使用しますか。**  
 Microsoft JDBC Driver には暗号化アルゴリズムが含まれていません。 場合は、顧客がオペレーティング システム、アプリケーション、およびと思われる許容可能な連邦情報処理規格 (FIPS) によって JVM アルゴリズムを利用し、それらのアルゴリズムを使用するドライバーを構成し、ドライバーを使用しての指定されたアルゴリズムのみ通信します。  
  
 ## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
