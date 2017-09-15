---
title: "よく寄せられる質問 (FAQ) JDBC ドライバーの |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cbc0e397-ecf2-4494-87b2-a492609bceae
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 508f8526ed13af3f7f92aa500b182e077f5bb23d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="frequently-asked-questions-faq-for-jdbc-driver"></a>よく寄せられる質問 (FAQ) JDBC driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  この記事では、Microsoft SQL Server 用 JDBC Driver についてよく寄せられる質問に対する回答をご紹介します。  
  
## <a name="frequently-asked-questions"></a>よく寄せられる質問  
**JDBC ドライバーの向上を支援する方法は?**  
JDBC ドライバーはオープン ソースと、ソース コードにある  [GitHub](https://github.com/microsoft/mssql-jdbc)です。 問題をファイリングによって、コード ベースに貢献しているドライバーを強化することができます。

**ドライバーはどのバージョンの SQL Server と Java をサポートしますか。**  
 参照してください、 [Microsoft JDBC Driver for SQL Server のサポート マトリックス](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md)詳細ページ。  
  
 **どのような知っておくべきドライバーをアップグレードするときにしますか。**  
 Microsoft JDBC Driver 6.2 では、JDBC 4.0、4.1、および 4.2 仕様をサポートしており、次のように、インストール パッケージに 2 つの JAR クラス ライブラリが含まれています。  
  
|JAR|JDBC の仕様|JDK のバージョン|  
|-|-|-|  
|mssql jdbc-6.2.1.jre8.jar|JDBC 4.2、4.1、4.0|JDK 8.0|  
|mssql jdbc-6.2.1.jre7.jar|JDBC 4.1、4.0|JDK 7.0|  
 
 Microsoft JDBC Drivers 6.0 と 4.2 for SQL Server JDBC 4.0、4.1、および 4.2 の仕様をサポートし、次のように、インストール パッケージに 2 つの JAR クラス ライブラリを含めます。  
  
|JAR|JDBC の仕様|JDK のバージョン|   
|-|-|-|  
|sqljdbc42.jar|JDBC 4.2、4.1、4.0|JDK 8.0|  
|sqljdbc41.jar|JDBC 4.1、4.0|JDK 7.0|  
  
 Microsoft JDBC Driver 4.1 for SQL Server では、JDBC 4.0 仕様をサポートしており、次のように、インストール パッケージに 1 つの JAR クラス ライブラリが含まれています。  
  
|JAR|JDBC の仕様|JDK のバージョン|    
|-|-|-|  
|sqljdbc41.jar|JDBC 4.0|JDK 7.0 および 6.0|
  
 Microsoft SQL Server 用 JDBC Driver 4.0 では、JDBC 3.0 と JDBC 4.0 の両方の仕様をサポートしており、各仕様のインストール パッケージに 2 つの JAR クラス ライブラリ (sqljdbc.jarおよび sqljdbc4.ja) を含んでいます。  
  
|JAR|JDBC の仕様|JDK のバージョン|   
|-|-|-|  
|sqljdbc4.jar|JDBC 4.0|JDK 6.0、5.0|  
|sqljdbc.jar|JDBC 3.0|JDK 6.0、5.0|  
  
 **既存の SQL Server のバージョンで最新のドライバーを使用するアプリケーションでコード変更を加える必要がありますか。**  
 通常、ドライバーは下位互換性を持つよう設計されているため、ドライバーをアップグレードする際に既存のアプリケーションを変更する必要はありません。 イベントで新しいドライバーのバージョンに重大な変更が導入されています、 [JDBC ドライバーのリリース ノート](../../connect/jdbc/release-notes-for-the-jdbc-driver.md)セクションはクリアについて詳しく変更と既存のアプリケーションに影響します。 さらに、そのリリースと既知の問題で修正されたバグの一覧については、ドライバーに付属のリリース ノートをご覧ください。  
  
 **ドライバーの料金はいくらですか。**  
 Microsoft SQL Server 用 JDBC Driver は、追加料金なしでご利用いただけます。  
  
 **ドライバーを再配布できますか。** JDBC ドライバー 4.1、4.2、6.0、6.2 は再頒布可能パッケージです。 ライセンス契約で、「再頒布可能コード」句を確認してください。
 
 JDBC Driver 4.0 は、登録が必要な個別の再配布ライセンスの下で自由に再頒布可能です。 登録または詳細については、次を参照してください。 この[Microsoft JDBC Driver の再配布](../../connect/jdbc/redistributing-the-microsoft-jdbc-driver.md)です。 
 
   
 **ドライバーを使用して Linux コンピューターから Microsoft SQL Server にアクセスできますか。** はい。 ドライバーを使用して、Linux、Unix、他の Windows 以外のプラットフォームから SQL Server にアクセスできます。 参照してください、 [Microsoft JDBC Driver for SQL Server のサポート マトリックス](../../connect/jdbc/microsoft-jdbc-driver-for-sql-server-support-matrix.md)詳細についてはします。  
  
 **ドライバーは Secure Sockets Layer (SSL) 暗号化をサポートしますか。** バージョン 1.2 以降のドライバーは、Secure Sockets Layer (SSL) 暗号化をサポートしています。 詳細については、次を参照してください。 [SSL 暗号化を使用して](../../connect/jdbc/using-ssl-encryption.md)です。  
  
 **どのような認証は、SQL Server 用 Microsoft JDBC Driver でサポートされてですか。**  
 次の表は、使用可能な認証オプションを示しています。 4.0 リリース以降のドライバーでは、ピュア Java Kerberos 認証が使用可能です。  
  
|||  
|-|-|  
|プラットフォーム|[認証]|  
|Windows 以外|ピュア Java Kerberos|  
|Windows 以外|SQL Server|  
|Windows|ピュア Java Kerberos|  
|Windows|SQL Server|  
|Windows|Kerberos と NTLM バックアップ|  
|Windows|NTLM|  
  
**ドライバーはサポートしてインターネット プロトコル バージョン 6 (IPv6) アドレスですか?**  
 はい。このドライバーは、接続プロパティのコレクションと serverName 接続文字列プロパティと合わせて IPv6 アドレスの使用をサポートしています。 詳細については、次を参照してください。[接続 URL の構築](../../connect/jdbc/building-the-connection-url.md)です。  
  
**アダプティブ バッファリングとは**  
 アダプティブ バッファリングは、Microsoft SQL Server 2005 JDBC Driver 1.2 以降に導入されており、サーバー カーソルのオーバーヘッドを発生させることなく、あらゆる種類の大きな値のデータを取得できるように設計されています。 Microsoft SQL Server JDBC Driver のアダプティブ バッファリング機能には接続文字列プロパティ responseBuffering があり、これを "adaptive" または "full" に設定できます。 JDBC Driver 2.0 以降では、ドライバーの既定の動作は "adaptive" です。 つまり、アプリケーションから明示的に要求しなくても、アダプティブ バッファリングの動作が適用されます。 ただし、バージョン 1.2 リリースでは、"full" が既定のバッファリング モードであるため、アプリケーションから明示的にアダプティブ バッファリング モードを要求する必要があります。 詳細については、次を参照してください。[アダプティブ バッファリングを使用して](../../connect/jdbc/using-adaptive-buffering.md)トピックとブログ[新機能は adaptiveresponse バッファー化および使用する理由に?](http://go.microsoft.com/fwlink/?LinkId=111575)です。  
  
**ドライバーの接続プールをサポートしますか。**  
 ドライバーは、Java Platform, Enterprise Edition 5 (Java EE 5) の接続プールをサポートしています。 ドライバーは、ミドルウェア アプリケーション サーバー ベンダーが提供するあらゆる接続プールの実装に参加できるように、JDBC 3.0 に必要なインターフェイスを実装しています。 このドライバーは、これらの環境でプールされた接続に参加します。 詳細については、次を参照してください。[接続プールを使用して](../../connect/jdbc/using-connection-pooling.md)です。 ドライバーは独自のプール実装を提供せず、むしろサードパーティの Java アプリケーション サーバーに依存しています。  
  
**ドライバーのサポートがあるか。**  
 さまざまなサポート オプションをご利用いただけます。 質問を投稿するか、発行、 [GitHub リポジトリ](https://github.com/microsoft/mssql-jdbc)これは Microsoft によって監視します。 [フォーラム](http://go.microsoft.com/fwlink/?LinkID=246673)Microsoft、MVP、コミュニティで監視します。 マイクロソフト カスタマー サポートにお問い合わせいただくこともできます。 サードパーティのアプリケーション サーバーの外部で問題の再現をお客様にお願いする場合があります。 ホストしている Java コンテナー環境の外部で問題を再現できない場合は、マイクロソフトが引き続きお客様を支援できるよう、関連するサードパーティを介入させる必要があります。 また、マイクロソフトが最大限の支援を行えるよう、Windows などのオペレーティング システムで問題の再現をお客様にお願いする場合もあります。  
  
**ドライバーは、サード パーティのアプリケーション サーバーで使用する用に認定されていますか。**
ドライバーは、IBM WebSphere、SAP NetWeaver などのさまざまなアプリケーション サーバーに対してテスト済みです。  
  
**トレースを有効にする方法は?**  
 ドライバーはトレース (またはログ記録) の使用をサポートしているため、アプリケーションで使用するときに JDBC Driver で発生した問題の解決に役立てることができます。 クライアント側の JAR のトレースの使用を有効にするため、JDBC Driver は java.util.logging でログ記録 API を使用しています。 詳細については、次を参照してください。[ドライバー操作のトレース](../../connect/jdbc/tracing-driver-operation.md)です。 サーバー側の XA のトレースについては、「 [Data Access Tracing in SQL Server (SQL Server でのデータ アクセスのトレース)](http://go.microsoft.com/fwlink/?LinkId=248705)」をご覧ください。  
  
**古いバージョンの SQL Server 2000 JDBC ドライバー、2005年ドライバーなどのドライバーをダウンロードする場所 1.0、1.1、または 1.2 ドライバーですか?**  
 これらのバージョンのドライバーはサポートされていないため、ダウンロードできません。 マイクロソフトは Java 接続のサポートの向上を継続的に進めています。 そのため、最新バージョンの JDBC ドライバーを使用することを強くおすすめします。  
  
 **JRE 1.4 を使用しています。JRE 1.4 と互換性のあるドライバー** SAP 製品を使用していて JRE 1.4 のサポートを必要とお客様のご連絡[SAPService Marketplace](http://service.sap.com/) 1.2 Microsoft JDBC ドライバーを入手します。  
  
**ドライバー通信できる FIPS 検証アルゴリズムを使用しますか。** Microsoft JDBC Driver には暗号化アルゴリズムが含まれていません。 お客様が、Federal Information Processing Standards (FIPS) に準拠していると見なされるオペレーティング システム、アプリケーション、JVM アルゴリズムを活用して、これらのアルゴリズムを使用するドライバーを構成する場合、ドライバーは指定されたアルゴリズムのみを通信に使用します。  
  
  

