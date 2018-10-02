---
title: Microsoft JDBC Driver for SQL Server の機能依存関係 | Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 939a8773-2583-49a4-bf00-6b892fbe39dc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 61c66d192a158fb754563e2d103eba946dee47c6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47830360"
---
# <a name="feature-dependencies-of-microsoft-jdbc-driver-for-sql-server"></a>Microsoft JDBC Driver for SQL Server の機能依存関係

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

このページは、Microsoft JDBC Driver for SQL Server が依存するライブラリを一覧表示されます。 プロジェクトには、次の依存関係が含まれます。

## <a name="compile-time"></a>コンパイル時間

- `azure-keyvault`: (省略可能) 常に暗号化された Azure Key Vault 機能 azure の Key Vault Provider
- `adal4j`: Java 用 Azure Active Directory 認証の機能と Azure Key Vault 機能 (省略可能) azure active Directory ライブラリ

## <a name="test-time"></a>テスト時間

上記の 2 つの機能のいずれかを必要とする特定のプロジェクトは、pom ファイルにそれぞれの依存関係を明示的に宣言する必要があります。

**_例:_** を使用する場合_Azure Active Directory 認証機能_を再宣言する必要があります_adal4j_プロジェクトの pom ファイルに依存関係。 次のスニペットを参照してください。

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.0</version>
</dependency>
```

**_例:_** を使用する場合_Azure Key Vault 機能_を再宣言する必要があります_azure keyvault_依存関係と_adal4j_プロジェクトの pom ファイルに依存します。 次のスニペットを参照してください。

```xml
<dependency>
    <groupId>com.microsoft.sqlserver</groupId>
    <artifactId>mssql-jdbc</artifactId>
    <version>7.0.0.jre10</version>
    <scope>compile</scope>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>adal4j</artifactId>
    <version>1.6.0</version>
</dependency>

<dependency>
    <groupId>com.microsoft.azure</groupId>
    <artifactId>azure-keyvault</artifactId>
    <version>1.0.0</version>
</dependency>
```

## <a name="dependency-requirements-for-the-jdbc-driver"></a>JDBC Driver の依存関係の要件

### <a name="working-with-azure-key-vault-provider"></a>Azure Key Vault プロバイダーの操作:

- JDBC Driver バージョン 7.0.0 - 依存関係のバージョン: Azure-keyvault (バージョン 1.0.0)、Adal4j (バージョン 1.6.0) とその依存関係 ([サンプル アプリケーション](../../connect/jdbc/azure-key-vault-sample-version-7-0-0.md))
- JDBC Driver version 6.4.0 - 依存関係のバージョン: Azure-keyvault (バージョン 1.0.0)、Adal4j (バージョン 1.4.0) とその依存関係 ([サンプル アプリケーション](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- JDBC Driver version 6.2.2 - 依存関係のバージョン: Azure-keyvault (バージョン 1.0.0)、Adal4j (バージョン 1.4.0) とその依存関係 ([サンプル アプリケーション](../../connect/jdbc/azure-key-vault-sample-version-6.2.2.md))
- JDBC Driver version 6.0.0 - 依存関係のバージョン: Azure-keyvault (バージョン 0.9.7)、Adal4j (バージョン 1.3.0) とその依存関係 ([サンプル アプリケーション](../../connect/jdbc/azure-key-vault-sample-version-6.0.0.md))

> [!NOTE]
> V6.2.2 と v6.4.0 ドライバーのバージョンでは、バージョン 1.0.0 に azure key vault-java 依存関係が更新されました。 ただし、新しいバージョンでは、以前のバージョン (バージョン 0.9.7) と互換性がないと、そのため、ドライバーで既存の実装の区切り。 ドライバーの新しい実装には、さらに、Azure Key Vault プロバイダーを使用するクライアント プログラムを中断する API の変更が必要です。

> この問題が解決され、最新のドライバー バージョン v7.0.0 認証コールバック メカニズムを使用して削除されたすべてのコンス トラクターが追加されるために Azure Key Vault プロバイダーの下位互換性です。

### <a name="working-with-azure-active-directory-authentication"></a>Azure Active Directory 認証の操作:

- JDBC Driver バージョン 7.0.0 - 依存関係のバージョン: Ada4j (バージョン 1.6.0) とその依存関係
- JDBC Driver version 6.4.0 - 依存関係のバージョン: Adal4j (バージョン 1.4.0) とその依存関係
- JDBC Driver version 6.2.2 - 依存関係のバージョン: Adal4j (バージョン 1.4.0) とその依存関係
- JDBC Driver version 6.0.0 - 依存関係のバージョン: Adal4j (バージョン 1.3.0)、ドライバーのこのバージョンで、その依存関係を使用して接続できる_ActiveDirectoryIntegrated_ Windows オペレーティング システムにのみ認証モードsqljdbc_auth.dll と Active Directory Authentication Library for SQL Server (ADALSQL 使用する方法。DLL) です。

ドライバー バージョン 6.4.0 の以降、アプリケーションとは限りませんを必要としない ADALSQL を使用します。Windows オペレーティング システムの DLL です。 **非 Windows オペレーティング システム**ドライバーが ActiveDirectoryIntegrated 認証を使用する Kerberos チケットが必要です。 Kerberos を使用して Active Directory に接続する方法の詳細については、次を参照してください。 [Windows、Linux と Mac での設定の Kerberos チケット](https://docs.microsoft.com/sql/connect/jdbc/connecting-using-azure-active-directory-authentication#set-kerberos-ticket-on-windows-linux-and-mac)します。

**Windows オペレーティング システム**ドライバーは、既定で sqljdbc_auth.dll の外観し、Kerberos チケットのセットアップや Azure ライブラリの依存関係は必要ありません。 ただし、sqljdbc_auth.dll を使用できない場合、ドライバーは、他のオペレーティング システムとして Active Directory への認証に Kerberos チケットを検索します。

この機能を使用してサンプル アプリケーションはあります[ここ](../../connect/jdbc/connecting-using-azure-active-directory-authentication.md)します。

## <a name="see-also"></a>参照

[JDBC ドライバーの GitHub リポジトリ](https://github.com/microsoft/mssql-jdbc)  
 [JDBC Driver API リファレンス](../../connect/jdbc/reference/jdbc-driver-api-reference.md)
