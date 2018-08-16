---
title: JDBC Driver のシステム要件 |Microsoft Docs
ms.custom: ''
ms.date: 07/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 447792bb-f39b-49b4-9fd0-1ef4154c74ab
caps.latest.revision: 73
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e5363b1135cb7e5d04201b2005bda9caf8ff8811
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/08/2018
ms.locfileid: "39662284"
---
# <a name="system-requirements-for-the-jdbc-driver"></a>JDBC Driver のシステム要件
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] または [!INCLUDE[ssAzure](../../includes/ssazure_md.md)] のデータにアクセスするには、次のコンポーネントをコンピューターにインストールする必要があります。

- [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] ([ダウンロード](download-microsoft-jdbc-driver-for-sql-server.md))
- Java ランタイム環境

## <a name="java-runtime-environment-requirements"></a>Java ランタイム環境の要件  
 Microsoft JDBC Driver 7.0 for SQL Server 以降で、Sun Java SE Development Kit (JDK) 10.0 と Java Runtime Environment (JRE) 10.0 がサポートされています。

 Microsoft JDBC Driver 6.4 for SQL Server 以降で、Sun Java SE Development Kit (JDK) 9.0 と Java Runtime Environment (JRE) 9.0 がサポートされています。

 Microsoft JDBC Driver 4.2 for SQL Server 以降で、Sun Java SE Development Kit (JDK) 8.0 と Java Runtime Environment (JRE) 8.0 がサポートされています。 Java Database Connectivity (JDBC) Spec API のサポートが拡張され、JDBC 4.1 と 4.2 API が対象になりました。  
  
 Microsoft JDBC Driver 4.1 for SQL Server 以降で、Sun Java SE Development Kit (JDK) 7.0 と Java Runtime Environment (JRE) 7.0 がサポートされています。  
  
 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] 以降では、JDBC 4.0 API を包含する形で Java Database Connectivity (JDBC) Spec API に対する JDBC ドライバー サポートが拡張されています。 JDBC 4.0 API は、Sun Java SE Development Kit (JDK) 6.0 および Java ランタイム環境 (JRE) 6.0 の一部として導入されました。 JDBC 4.0 は、JDBC 3.0 API のスーパーセットです。  
  
 Windows と UNIX オペレーティング システムで [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] を展開する場合、インストール パッケージである *sqljdbc_\<version>_enu.exe* と *sqljdbc_\<version>_enu.tar.gz* をそれぞれ使用する必要があります。 JDBC Driver を展開する方法の詳細については、次を参照してください。 [JDBC Driver の展開](../../connect/jdbc/deploying-the-jdbc-driver.md)トピック。  
  
**Microsoft JDBC Driver 7.0 for SQL Server:**  

  JDBC ドライバーの 7.0 には、各インストール パッケージの 2 つの JAR クラス ライブラリが含まれています: **mssql-jdbc-7.0.0.jre8.jar**、および**mssql-jdbc-7.0.0.jre10.jar**します。

  JDBC Driver 7.0 は、Sun と同等のすべての主要な Java 仮想マシンで操作とサポートができるよう設計されていますが、テストが実行されるのは Sun JRE 8.0 と 10.0 上のみです。
  
  Microsoft JDBC Driver 7.0 for SQL Server に含まれている 2 つの JAR ファイルによって提供されるサポートの概要を以下に示します。  
  
  |JAR|JDBC バージョン準拠|Java バージョンをお勧めします。|[説明]|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-7.0.0.jre8.jar|4.2|8|Java Runtime Environment (JRE) 8.0 が必要です。 JRE 7.0 または低いがスローされます、例外を使用します。<br /><br /> 7.0 の新機能が含まれます JDK 10 のサポート、JDBC 4.2 仕様、空間データ型のサポート、cancelQueryTimeout 接続プロパティ、メソッドの境界の要求、useBulkCopyForBatchInsert 接続プロパティ、データ更新の既定のコンプライアンス レベル。検出と分類の情報、utf-8 の拡張機能、および CityHash サポートします。 |    
|mssql-jdbc-7.0.0.jre10.jar|4.3|10|Java Runtime Environment (JRE) 10.0 が必要です。 JRE 9.0 または低いがスローされます、例外を使用します。<br /><br /> 7.0 の新機能が含まれます JDK 10 のサポート、JDBC 4.2 仕様、空間データ型のサポート、cancelQueryTimeout 接続プロパティ、メソッドの境界の要求、useBulkCopyForBatchInsert 接続プロパティ、データ更新の既定のコンプライアンス レベル。検出と分類の情報、utf-8 の拡張機能、および CityHash サポートします。 |    


  JDBC ドライバーの 7.0 では、Maven Central Repository の使用もし、POM で次のコードを追加することで、Maven プロジェクトに追加できます。XML:  
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
</dependency>
```      
  
**Microsoft JDBC Driver 6.4 for SQL Server:**  

  JDBC Driver 6.4、には 3 つの JAR クラス ライブラリには、各インストール パッケージが含まれています: **mssql-jdbc-6.4.0.jre7.jar**、 **mssql-jdbc-6.4.0.jre8.jar**と**mssql-jdbc-6.4.0.jre9.jar**.

  JDBC Driver 6.4 は、Sun と同等のすべての主要な Java 仮想マシンで操作とサポートができるよう設計されていますが、Sun JRE 7.0、8.0、9.0 のみでテストされます。
  
  Microsoft JDBC Driver 6.4 for SQL Server に含まれている 3 つの JAR ファイルによって提供されるサポートの概要を以下に示します。  
  
  |JAR|JDBC バージョン準拠|Java バージョンをお勧めします。|[説明]|  
|---------|-----------------------------|----------------------|-----------------|   
|mssql-jdbc-6.4.0.jre7.jar|4.1|7|Java Runtime Environment (JRE) 7.0 が必要です。 JRE 6.0 または下のスローを例外を使用します。<br /><br /> 6.4 で新しい機能が含まれます: Linux、Kerberos、クロス ドメイン認証、Kerberos 制約付き委任、クエリのタイムアウト、ソケットのタイムアウトのための SPN の REALM の自動検出のプリンシパル/パスワード メソッド用の Azure AD の認証および準備されました。ステートメント ハンドルを再利用します。 |  
|mssql-jdbc-6.4.0.jre8.jar|4.2|8|Java Runtime Environment (JRE) 8.0 が必要です。 JRE 7.0 または低いがスローされます、例外を使用します。<br /><br /> 6.4 で新しい機能が含まれます: Linux、Kerberos、クロス ドメイン認証、Kerberos 制約付き委任、クエリのタイムアウト、ソケットのタイムアウトのための SPN の REALM の自動検出のプリンシパル/パスワード メソッド用の Azure AD の認証および準備されました。ステートメント ハンドルを再利用します。 |    
|mssql-jdbc-6.4.0.jre9.jar|4.3|9|Java Runtime Environment (JRE) 9.0 が必要です。 JRE 8.0 または低いがスローされます、例外を使用します。<br /><br /> 6.4 で新しい機能が含まれます: Linux、Kerberos、クロス ドメイン認証、Kerberos 制約付き委任、クエリのタイムアウト、ソケットのタイムアウトのための SPN の REALM の自動検出のプリンシパル/パスワード メソッド用の Azure AD の認証および準備されました。ステートメント ハンドルを再利用します。 |

JDBC Driver 6.4 は、Maven Central Repository の使用もし、POM で次のコードを追加することで、Maven プロジェクトに追加できます。XML 

 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.4.0.jre9</version>
</dependency>
```

**Microsoft JDBC Driver 6.2 for SQL Server:**  
  
  JDBC Driver 6.2 の各インストール パッケージには、2 つの JAR クラス ライブラリ (**mssql-jdbc-6.2.2.jre7.jar** および **mssql-jdbc-6.2.2.jre8.jar**) が含まれています。 
  
 JDBC Driver 6.2 は、Sun と同等のすべての主要な Java 仮想マシンで操作とサポートができるよう設計されていますが、Sun JRE 5.0、6.0、7.0、8.0 のみでテストされます。
  
 Microsoft JDBC Driver 6.0 for SQL Server および Microsoft JDBC Driver 4.2 for SQL Server に含まれている 2 つの JAR ファイルによって提供されるサポートの概要を以下に示します。  
  
|JAR|JDBC バージョン準拠|Java バージョンをお勧めします。|[説明]|  
|---------|-----------------------------|----------------------|-----------------|
|mssql-jdbc-6.2.2.jre7.jar|4.1|7|Java Runtime Environment (JRE) 7.0 が必要です。 JRE 6.0 または下のスローを例外を使用します。<br /><br /> 6.2 の新機能が含まれます: Linux、Kerberos、クロス ドメイン認証、Kerberos 制約付き委任、クエリのタイムアウト、ソケットのタイムアウトのための SPN の REALM の自動検出のプリンシパル/パスワード メソッド用の Azure AD の認証および準備されました。ステートメント ハンドルを再利用します。 |  
|mssql-jdbc-6.2.3.jre8.jar|4.2|8|Java Runtime Environment (JRE) 8.0 が必要です。 JRE 7.0 または低いがスローされます、例外を使用します。<br /><br /> 6.2 の新機能が含まれます: Linux、Kerberos、クロス ドメイン認証、Kerberos 制約付き委任、クエリのタイムアウト、ソケットのタイムアウトのための SPN の REALM の自動検出のプリンシパル/パスワード メソッド用の Azure AD の認証および準備されました。ステートメント ハンドルの再利用|    

  JDBC Driver 6.2 では、Maven Central Repository では使用可能なもあり、POM で次のコードを追加することで、Maven プロジェクトに追加できます。XML 
  
 ```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.2.2.jre8</version>
</dependency>
```    

 **Microsoft JDBC Driver 6.0 for SQL Server および Microsoft JDBC Driver 4.2 for SQL Server:**  
  
  JDBC ドライバー 6.0 と 4.2 は、各インストール パッケージに 2 つの JAR クラス ライブラリを含める: **sqljdbc41.jar**、および**sqljdbc42.jar**します。 
  
 JDBC Driver 6.0 および 4.2 は、Sun と同等のすべての主要な Java 仮想マシンで操作とサポートができるよう設計されていますが、Sun JRE 5.0、6.0、7.0、8.0 のみでテストされます。 
  
 Microsoft JDBC Driver 6.0 for SQL Server および Microsoft JDBC Driver 4.2 for SQL Server に含まれている 2 つの JAR ファイルによって提供されるサポートの概要を以下に示します。  
  
|JAR|JDBC バージョン準拠|Java バージョンをお勧めします。|[説明]|  
|---------|-----------------------------|----------------------|-----------------|   
|sqljdbc41.jar|4.1|7|Java Runtime Environment (JRE) 7.0 が必要です。 JRE 6.0 または下のスローを例外を使用します。<br /><br /> 6.0 と 4.2 のパッケージの新機能には、JDBC 4.1 準拠と一括コピーが含まれています。<br /><br /> さらに、6.0 のパッケージのみの新機能が含まれます Always Encrypted により、テーブル値パラメーターの場合は、Azure Active Directory 認証、Always On 可用性グループでのパラメーター メタデータの取得での改善に透過的な接続の準備。クエリと国際化ドメイン名 (IDN)|  
|sqljdbc42.jar|4.2|8|Java Runtime Environment (JRE) 8.0 が必要です。 JRE 7.0 または低いがスローされます、例外を使用します。<br /><br /> 6.0 と 4.2 のパッケージの新機能には、JDBC 4.1 準拠、JDBC 4.2 準拠、一括コピーが含まれています。<br /><br /> さらに、6.0 のパッケージのみの新機能が含まれます Always Encrypted により、テーブル値パラメーターの場合は、Azure Active Directory 認証、Always On 可用性グループでのパラメーター メタデータの取得での改善に透過的な接続の準備。クエリと国際化ドメイン名 (IDN)|  
  
 **Microsoft JDBC Driver 4.1 for SQL Server:**  
  
 JDBC Driver 4.1 には各インストール パッケージで 1 つの JAR クラス ライブラリが含まれています: **sqljdbc41.jar**します。  
    
|JAR|[説明]|  
|---------|-----------------|  
|sqljdbc41.jar|**sqljdbc41.jar** クラス ライブラリでは、JDBC 4.0 API のサポートが提供されます。 JDBC 4.0 ドライバーのすべての機能と JDBC 4.0 API メソッドを備えています。 JDBC 4.1 はサポートされていません ("SQLFeatureNotSupportedException" の例外がスローされます)。<br /><br /> **sqljdbc41.jar** クラス ライブラリを使用するには、Java Runtime Environment (JRE) 7.0 が必要です。 使用して**sqljdbc41.jar** JRE 6.0 と 5.0 では、例外をスローします。<br /><br /> 
  
 この JDBC ドライバーは、Sun の Java 仮想マシンと同等の主要な仮想マシンをすべてサポートし、適切に動作するように設計されていますが、テストは Sun JRE 5.0、6.0、および 7.0 で行われています。  
  
 Microsoft JDBC Driver 4.1 for SQL Server に含まれている JAR ファイルによって提供されるサポートの概要を以下に示します。  
  
|JAR|JDBC のバージョン|JRE (実行可能)|JDK (コンパイル可能)|  
|---------|------------------|---------------------|-------------------------|   
|sqljdbc41.jar|4|7|7 6 5|  
  
## <a name="sql-server-requirements"></a>SQL Server の要件  
 JDBC ドライバーは、Azure SQL Database と SQL Server への接続をサポートします。 Microsoft JDBC Driver 4.2 for SQL Server と Microsoft JDBC Driver 4.1 for SQL Server では、SQL Server 2008 以降をサポートします。
  
## <a name="operating-system-requirements"></a>必要なオペレーティング システム  
 JDBC ドライバーは、Java 仮想マシン (JVM) の使用をサポートするすべてのオペレーティング システムで機能するように設計されています。 ただし、公式にテストされているのは、Sun Solaris、SUSE Linux、および Windows オペレーティング システムだけです。  
  
## <a name="supported-languages"></a>サポートされる言語  
 JDBC ドライバーは、すべての [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 列の照合順序をサポートしています。 JDBC ドライバーでサポートされる照合順序の詳細については、次を参照してください。 [JDBC Driver の国際対応](../../connect/jdbc/international-features-of-the-jdbc-driver.md)します。  
  
 照合順序の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] オンライン ブックの「照合順序の使用」を参照してください。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
