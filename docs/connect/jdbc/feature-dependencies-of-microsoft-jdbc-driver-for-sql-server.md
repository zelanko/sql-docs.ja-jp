---
title: SQL Server の機能に関する Microsoft JDBC ドライバーの依存関係の |Microsoft ドキュメント
ms.custom: ''
ms.date: 02/28/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
caps.latest.revision: 57
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 052628258ae1d8c1f31430ea132ed594a976be98
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="feature-dependencies-of-microsoft-jdbc-driver-for-sql-server"></a>Microsoft JDBC Driver for SQL Server の機能の依存関係
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

 このページには、Microsoft JDBC Driver for SQL Server が依存するライブラリの一覧が含まれています。 プロジェクトでは、次の条件。
 
 ## <a name="compile-time"></a>コンパイル時
 - `azure-keyvault` : (省略可能) Azure の Key Vault の Always Encrypted 機能 azure キー資格情報コンテナー プロバイダー
 - `adal4j` : Azure の active Directory ライブラリの Java 用 Azure Active Directory 認証機能と Azure Key Vault 機能 (省略可能)

 ##  <a name="test-time"></a>テスト時間
上記の 2 つの機能のいずれかを必要とする特定のプロジェクトは、その pom ファイル内のそれぞれの依存関係を明示的に宣言する必要があります。

***例:*** を使用している場合*Azure Active Directory 認証機能*を再宣言する必要があります*adal4j*プロジェクトの pom ファイル内の依存関係。 次のスニペットを参照してください。 
```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.4.0.jre8</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.4.0</version>
</dependency>
```

***例:*** を使用している場合*Azure Key Vault 機能*を再宣言する必要があります*azure keyvault*依存関係と*adal4j*内の依存関係、プロジェクトの pom ファイルです。 次のスニペットを参照してください。 
```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>6.4.0.jre8</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.4.0</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.0.0</version>
</dependency>
```
 
 ## <a name="dependency-requirements-for-the-jdbc-driver"></a>JDBC ドライバーの依存関係の要件

 ### <a name="azure-keyvault-feature"></a>Azure の Keyvault 機能:
- JDBC Driver バージョン 6.0.0 
    - 依存関係のバージョン: Azure Keyvault (バージョン 0.9.7)、Adal4j (バージョン 1.3.0) とその依存関係 ([サンプル アプリケーション](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))
- JDBC Driver version 6.2.2 以降 (最新 6.4.0 を含む)
    - 依存関係のバージョン: Azure Keyvault (バージョン 1.0.0)、Adal4j (バージョン 1.4.0) とその依存関係 ([サンプル アプリケーション](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))

> [!NOTE]
>   V6.2.2、時点では、バージョン 1.0.0 を azure keyvault java 依存関係が更新されます。 ただし、新しいバージョンを使用して、以前のバージョン (バージョン 0.9.7) と互換性がなく、そのため、ドライバーで既存の実装の区切りです。 ドライバーの新しい実装では、API の変更は、さらに、Azure Key Vault 機能を使用するクライアント プログラムを中断が必要です。

  
 ### <a name="azure-active-directory-authentication"></a>Azure Active Directory 認証:
- JDBC Driver バージョン 6.0.0 
    - 依存関係のバージョン: Adal4j (バージョン 1.3.0) とその依存関係
        - このバージョンのドライバーでは、使用して接続できます*ActiveDirectoryIntegrated*オペレーティング システムと SQL Server (の sqljdbc_auth.dll と Active Directory 認証ライブラリを使用して Windows だけで認証モードADALSQL です。DLL) です。 
- JDBC Driver バージョン 6.4.0
    - 依存関係のバージョン: Adal4j (バージョン 1.4.0) とその依存関係
        - このバージョンのドライバーでは、アプリケーションは必要ありません ADALSQL を使用します。DLL です。 オペレーティング システムに応じています。 **非 Windows オペレーティング システム**ドライバーが ActiveDirectoryIntegrated 認証と連動する Kerberos チケットを必要とします。 参照してください[Windows、Linux、Mac 上の設定の Kerberos チケット](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac)詳細についてはします。 **Windows オペレーティング システム**sqljdbc_auth.dll が読み込まれると、Kerberos チケットのセットアップまたは adal4j の依存関係は必要ないかどうかに既定ではドライバーがチェックされます。 ただし、sqljdbc_auth.dll が読み込まれていない場合ドライバー非 Windows オペレーティング システムと同様に動作し、セットアップで、次の例で説明されている必要がありますこの機能を使用して、サンプル アプリケーションを検出できる[ここ](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md).

 ## <a name="see-also"></a>参照  
 [JDBC ドライバーの GitHub リポジトリ](https://github.com/microsoft/mssql-jdbc)  
 [JDBC ドライバー API リファレンス](../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  