---
title: "JDBC Driver のシステム要件 |Microsoft ドキュメント"
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
ms.assetid: 447792bb-f39b-49b4-9fd0-1ef4154c74ab
caps.latest.revision: 73
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: eed93fab6f0ceec655b7b9f6b392abc390b5f0ff
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="system-requirements-for-the-jdbc-driver"></a>JDBC Driver のシステム要件
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  データにアクセスする、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]または[!INCLUDE[ssAzure](../../includes/ssazure_md.md)]を使用して、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]、次のコンポーネントがコンピューターにインストールする必要があります。  
  
-   [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]  
  
     Microsoft JDBC Driver は、以下のリンクで Microsoft ダウンロード センターからダウンロードできます。 
     * [SQL Server 用 Microsoft JDBC Driver 6.2](http://go.microsoft.com/fwlink/?linkid=852460)
     * [Microsoft JDBC Driver 6.0 for SQL Server](http://go.microsoft.com/fwlink/?linkid=841535)
     * [Microsoft JDBC Driver 4.2 for SQL Server](http://go.microsoft.com/fwlink/?linkid=841534) 
     * [Microsoft JDBC Driver 4.1 for SQL Server](http://go.microsoft.com/fwlink/?linkid=841533) 
     * [Microsoft JDBC Driver 4.0 for SQL Server](http://go.microsoft.com/fwlink/?linkid=841532)
  
-   Java ランタイム環境  
  
## <a name="java-runtime-environment-requirements"></a>Java Runtime Environment の要件  
 Microsoft JDBC Driver 4.2 for SQL Server 以降で、Sun Java SE Development Kit (JDK) 8.0 と Java Runtime Environment (JRE) 8.0 がサポートされています。 Java Database Connectivity (JDBC) Spec API のサポートが拡張され、JDBC 4.1 と 4.2 API が対象になりました。  
  
 Microsoft JDBC Driver 4.1 for SQL Server 以降で、Sun Java SE Development Kit (JDK) 7.0 と Java Runtime Environment (JRE) 7.0 がサポートされています。  
  
 以降で、 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]、JDBC 4.0 API を包含する Java Database Connectivity (JDBC) Spec API に対する JDBC ドライバーのサポートが拡張されています。 JDBC 4.0 API は、Sun Java SE Development Kit (JDK) 6.0 および Java ランタイム環境 (JRE) 6.0 の一部として導入されました。 JDBC 4.0 は、JDBC 3.0 API のスーパーセットです。  
  
 展開するときに、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Windows および UNIX のオペレーティング システム インストール パッケージを使用する必要があります*sqljdbc _\<バージョン > _enu.exe*と*sqljdbc _\<バージョン > _enu.tar.gz*、それぞれします。 JDBC Driver を展開する方法の詳細については、次を参照してください。 [JDBC Driver の展開](../../connect/jdbc/deploying-the-jdbc-driver.md)トピックです。  
  
**SQL Server 用 Microsoft JDBC Driver 6.2:**  
  
  JDBC ドライバー 6.2 には、インストール パッケージごとに 2 つの JAR クラス ライブラリが含まれています: **mssql jdbc-6.2.1.jre7.jar**、および**mssql jdbc-6.2.1.jre8.jar**です。 
  
 JDBC ドライバー 6.2 では、使用すると、すべてメジャー Sun と同等、Java 仮想マシンでサポートするよう設計されていますが、Sun JRE 5.0、6.0、7.0、および 8.0 でのみテストされています。 
  
 SQL Server 用 Microsoft JDBC Drivers 6.0 と 4.2 に含まれている 2 つの JAR ファイルによって提供されるサポートを以下に示します。  
  
|JAR|JDBC バージョン準拠|推奨される Java バージョン|Description|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql jdbc-6.2.1.jre7.jar|4.1|7|Java Runtime Environment (JRE) 7.0 が必要です。 使用 JRE 6.0 またはそれ例外がスローされます。<br /><br /> 6.2 で新機能: Linux、Kerberos、クロス ドメインの認証に Kerberos 制約付き委任、クエリのタイムアウト、ソケットのタイムアウト、SPN に領域の自動検出のプリンシパル/パスワード メソッド用の Azure AD の認証および準備されました。ステートメント ハンドルを再利用します。 |  
|mssql jdbc-6.2.1.jre8.jar|4.2|8|Java Runtime Environment (JRE) 8.0 が必要です。 使用 JRE 7.0 またはそれ例外がスローされます。<br /><br /> 6.2 で新機能: Linux、Kerberos、クロス ドメインの認証に Kerberos 制約付き委任、クエリのタイムアウト、ソケットのタイムアウト、SPN に領域の自動検出のプリンシパル/パスワード メソッド用の Azure AD の認証および準備されました。ステートメント ハンドルを再利用|    

  JDBC ドライバー 6.2 はプロジェクトに追加 Maven POM で次のコードを追加することでは、Maven の中央リポジトリもあります。XML 
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.2.1.jre8</version>
</dependency>
```    

 **Microsoft JDBC Driver 6.0 と 4.2 for SQL Server:**  
  
  JDBC ドライバー 6.0 と 4.2 は、各インストール パッケージに 2 つの JAR クラス ライブラリを含める: **sqljdbc41.jar**、および**sqljdbc42.jar**です。 
  
 JDBC ドライバー 6.0 と 4.2 を使用し、すべてメジャー Sun と同等、Java 仮想マシンでサポートされているためが、Sun JRE 5.0、6.0、7.0、および 8.0 のみでテストされます。 
  
 SQL Server 用 Microsoft JDBC Drivers 6.0 と 4.2 に含まれている 2 つの JAR ファイルによって提供されるサポートを以下に示します。  
  
|JAR|JDBC バージョン準拠|推奨される Java バージョン|Description|  
|---------|-----------------------------|----------------------|-----------------|   
|sqljdbc41.jar|4.1|7|Java Runtime Environment (JRE) 7.0 が必要です。 使用 JRE 6.0 またはそれ例外がスローされます。<br /><br /> 6.0 と 4.2 のパッケージの新機能には、JDBC 4.1 準拠と一括コピーが含まれています。<br /><br /> さらに、6.0 のパッケージのみの新機能が含まれます: Always encrypted により、テーブル値パラメーターの場合は、Azure Active Directory 認証、Always On 可用性グループのパラメーター メタデータの取得の改善に透過的な接続の準備クエリと国際化ドメイン名 (IDN)|  
|sqljdbc42.jar|4.2|8|Java Runtime Environment (JRE) 8.0 が必要です。 使用 JRE 7.0 またはそれ例外がスローされます。<br /><br /> 6.0 と 4.2 のパッケージの新機能には、JDBC 4.1 準拠、JDBC 4.2 準拠、一括コピーが含まれています。<br /><br /> さらに、6.0 のパッケージのみの新機能が含まれます: Always encrypted により、テーブル値パラメーターの場合は、Azure Active Directory 認証、Always On 可用性グループのパラメーター メタデータの取得の改善に透過的な接続の準備クエリと国際化ドメイン名 (IDN)|  
  
 **Microsoft JDBC Driver 4.1 for SQL Server:**  
  
 JDBC Driver 4.1 には、インストール パッケージごとに 1 つの JAR クラス ライブラリが含まれています: **sqljdbc41.jar**です。  
    
|JAR|Description|  
|---------|-----------------|  
|sqljdbc41.jar|**sqljdbc41.jar**クラス ライブラリには、JDBC 4.0 API のサポートが用意されています。 すべての JDBC 4.0 API のメソッドと同様に、JDBC 4.0 driver の機能が含まれます。 JDBC 4.1 はサポートされていません (“SQLFeatureNotSupportedException” の例外がスローされます)。<br /><br /> **sqljdbc41.jar**クラス ライブラリには、Java ランタイム環境 (JRE) 7.0 が必要です。 使用して**sqljdbc41.jar** JRE 6.0 と 5.0 で例外がスローされます。<br /><br /> 
  
 この JDBC Driver は、Sun の Java 仮想マシンと同等の主要な仮想マシンをすべてサポートし、適切に動作するように設計されていますが、テストは Sun JRE 5.0、6.0、および 7.0 で行われています。  
  
 次に、Microsoft JDBC Driver 4.1 for SQL Server に付属の JAR ファイルによって提供されるサポートの概要を示します。  
  
|JAR|JDBC のバージョン|JRE (実行可能)|JDK (コンパイル可能)|  
|---------|------------------|---------------------|-------------------------|   
|sqljdbc41.jar|4|7|7 6 5|  
  
 **Microsoft JDBC Driver 4.0 for SQL Server:**  
  
 JDBC ドライバーには旧バージョンとの互換性および可能なアップグレード シナリオをサポートするインストール パッケージごとに 2 つの JAR クラス ライブラリが含まれます: **sqljdbc.jar**と**sqljdbc4.jar**です。  
  
|JAR|Description|  
|---------|-----------------|  
|sqljdbc.jar|**sqljdbc.jar**クラス ライブラリは、JDBC 3.0 をサポートします。<br /><br /> **sqljdbc.jar**クラス ライブラリ バージョン 5.0 の Java ランタイム環境 (JRE) が必要です。 使用して**sqljdbc.jar** JRE 6.0 または JRE 7.0 では例外をスロー、データベースに接続するときにします。<br /><br /> **注:** JDBC ドライバーは JRE 1.4 をサポートしていません。 JDBC Driver を使用する場合は、JRE 1.4 を JRE 5.0、JRE 6.0、または JRE 7.0 にアップグレードする必要があります。 JDK 5.0 API または JDK 6.0 API との互換性がないことも考えられるため、アプリケーションの再コンパイルが必要になる場合があります。 詳細については、Sun Microsystems の Web サイトで、ドキュメントをご覧ください。<br /><br /> [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]JDK 7 はサポートされません。|  
|sqljdbc4.jar|**sqljdbc4.jar**クラス ライブラリには、JDBC 4.0 API のサポートが用意されています。 すべての機能が含まれています、 **sqljdbc.jar**だけでなく、新しい JDBC 4.0 API のメソッドです。<br /><br /> **sqljdbc4.jar**クラス ライブラリ バージョン 6.0 または 7.0 の Java ランタイム環境 (JRE) が必要です。 使用して**sqljdbc4.jar** JRE 5.0 で例外がスローされます。<br /><br /> **注:**使用**sqljdbc4.jar**とする必要がありますでアプリケーションを実行 JRE 6.0 または 7.0 では、アプリケーションは JDBC 4.0 API の機能を使用しない場合でもです。|  
  
 この JDBC Driver は、Sun の Java 仮想マシンと同等の主要な仮想マシンをすべてサポートし、適切に動作するように設計されていますが、テストは Sun JRE 5.0、6.0、および 7.0 で行われています。  
  
## <a name="sql-server-requirements"></a>SQL Server の要件  
 JDBC ドライバーでは、Azure SQL データベースおよび SQL Server への接続をサポートします。 Microsoft JDBC Driver 4.2 for SQL Server と Microsoft JDBC Driver 4.1 for SQL Server では、SQL Server 2008 以降をサポートします。 Microsoft JDBC Driver 4.0 for SQL Server では、SQL Server 2005 以降をサポートします。  
  
## <a name="operating-system-requirements"></a>必要なオペレーティング システム  
 JDBC ドライバーは、Java 仮想マシン (JVM) の使用をサポートするすべてのオペレーティング システムで機能するように設計されています。 ただし、公式にテストされているのは、Sun Solaris、SUSE Linux、および Windows オペレーティング システムだけです。  
  
## <a name="supported-languages"></a>サポートされる言語  
 JDBC ドライバーをすべてサポートしている[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]列の照合順序。 JDBC ドライバーでサポートされる照合順序の詳細については、次を参照してください。 [JDBC ドライバーの国際対応機能](../../connect/jdbc/international-features-of-the-jdbc-driver.md)します。  
  
 照合順序の詳細についてを参照してください「照合順序の使用」[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]オンライン ブック。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

