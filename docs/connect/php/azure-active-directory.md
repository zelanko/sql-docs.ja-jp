---
title: Azure Active Directory |Microsoft Docs
ms.date: 02/25/2019
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- azure active directory, authentication, access token
author: david-puglielli
ms.author: v-dapugl
manager: mbarwin
ms.openlocfilehash: 30423cd7c15a920d99fad4c0ea08e074beaece0b
ms.sourcegitcommit: 8664c2452a650e1ce572651afeece2a4ab7ca4ca
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2019
ms.locfileid: "56828052"
---
# <a name="connect-using-azure-active-directory-authentication"></a>Azure Active Directory 認証を使用して接続する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) は、サーバーの全体のユーザー ID 管理テクノロジの代替として動作する[SQL Server 認証](../../connect/php/how-to-connect-using-sql-server-authentication.md)します。 Azure AD は、ユーザー名とパスワード、Windows 統合認証、または Azure AD アクセス トークンを使用して Azure AD でフェデレーション id を持つ Microsoft Azure SQL Database と SQL Data Warehouse への接続を許可します。 SQL Server 用 PHP ドライバーでは、これらの機能の部分的なサポートを提供します。

Azure AD を使用する、**認証**または**AccessToken**キーワード (相互に排他的は)、次の表に示すようにします。 技術的な詳細についてを参照してください[を使用して Azure Active Directory と ODBC ドライバー](../../connect/odbc/using-azure-active-directory.md)します。

|Keyword|値|[説明]|
|-|-|-|
|**AccessToken**|(既定) の設定します。|認証モードがその他のキーワードによって決定されます。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。 |
||バイトの文字列|Azure AD アクセス トークンを OAuth JSON 応答から抽出します。 ユーザー ID、パスワード、または認証キーワードが、接続文字列に含まれていない必要があります (ODBC Driver 17 が必要です以降では、Linux または macOS)。 |
|**[認証]**|(既定) の設定します。|認証モードがその他のキーワードによって決定されます。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。 |
||`SqlPassword`|(これは、Azure インスタンスである可能性があります)、SQL Server インスタンスへの直接認証ユーザー名とパスワードを使用します。 ユーザー名とパスワードを使用して、接続文字列に渡す必要がある、 **UID**と**PWD**キーワード。 |
||`ActiveDirectoryPassword`|ユーザー名とパスワードを使用して id を Azure Active Directory で認証します。 ユーザー名とパスワードを使用して、接続文字列に渡す必要がある、 **UID**と**PWD**キーワード。 |
||`ActiveDirectoryMsi`|システムによって割り当てられた管理対象 id またはユーザー割り当て管理対象 id のいずれかを使用して認証 (ODBC ドライバー バージョン 17.3.1.1 必要がありますまたはそれ以降)。 概要とチュートリアルを参照してください[Azure リソースの管理対象の id とは何ですか?](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview)します。|

**認証**キーワードが接続のセキュリティ設定に影響します。 既定ではその後、接続文字列に設定されている場合、 **Encrypt**キーワードは、クライアントの暗号化を要求することを意味する true に設定します。 さらに、サーバー証明書が暗号化の設定に関係なく検証する場合を除き、 **TrustServerCertificate**設定を true に (**false**既定)。 この機能は、暗号化は、接続文字列で明確に要求された場合にのみのサーバー証明書を検証、セキュリティで保護されたログイン メソッドより、古いと区別されます。

Windows 上の SQL Server 用 PHP ドライバーと共に Azure AD を使用している場合が求められることをインストールする、 [Microsoft Online Services サインイン アシスタント](https://www.microsoft.com/download/details.aspx?id=41950)(ODBC 17 + は必要ありません)。

#### <a name="limitations"></a>制限事項

、Windows では、基になる ODBC ドライバーは、1 つ以上の値をサポートしています、**認証**キーワード、 **ActiveDirectoryIntegrated**、が PHP ドライバーが任意のプラットフォームでこの値をサポートしません。

## <a name="example---connect-using-sqlpassword-and-activedirectorypassword"></a>例 - SqlPassword ActiveDirectoryPassword を使用して接続

```php
<?php
// First connect to a local SQL Server instance by setting Authentication to SqlPassword
$serverName = "myserver.mydomain";

$connectionInfo = array("UID"=>$myusername, "PWD"=>$mypassword, "Authentication"=>'SqlPassword');

$conn = sqlsrv_connect($serverName, $connectionInfo);
if ($conn === false) {
    echo "Could not connect with Authentication=SqlPassword.\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Authentication=SqlPassword.\n";
    sqlsrv_close($conn);
}

// Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
$azureServer = "myazureserver.database.windows.net";
$azureDatabase = "myazuredatabase";
$azureUsername = "myuid";
$azurePassword = "mypassword";
$connectionInfo = array("Database"=>$azureDatabase,
                        "UID"=>$azureUsername,
                        "PWD"=>$azurePassword,
                        "Authentication"=>'ActiveDirectoryPassword');

$conn = sqlsrv_connect($azureServer, $connectionInfo);
if ($conn === false) {
    echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
    sqlsrv_close($conn);
}

?>
```

## <a name="example---connect-using-the-pdosqlsrv-driver"></a>例 - PDO_SQLSRV ドライバーを使用して接続

```php
<?php
// First connect to a local SQL Server instance by setting Authentication to SqlPassword
$serverName = "myserver.mydomain";

$connectionInfo = "Database = $databaseName; Authentication = SqlPassword;";

try {
    $conn = new PDO("sqlsrv:server = $serverName ; $connectionInfo", $myusername, $mypassword);
    echo "Connected successfully with Authentication=SqlPassword.\n";
    $conn = null;
} catch (PDOException $e) {
    echo "Could not connect with Authentication=SqlPassword.\n";
    print_r($e->getMessage());
    echo "\n";
}

// Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
$azureServer = "myazureserver.database.windows.net";
$azureDatabase = "myazuredatabase";
$azureUsername = "myuid";
$azurePassword = "mypassword";
$connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryPassword;";

try {
    $conn = new PDO("sqlsrv:server = $azureServer ; $connectionInfo", $azureUsername, $azurePassword);
    echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
    unset($conn);
} catch (PDOException $e) {
    echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
    print_r($e->getMessage());
    echo "\n";
}
?>
```

## <a name="example---connect-using-azure-ad-access-token"></a>例 - Azure AD アクセス トークンを使用して接続

### <a name="sqlsrv-driver"></a>SQLSRV ドライバー

```php
<?php
// Using an access token to connect: do not use UID or PWD connection options
// Assume $accToken is the valid byte string extracted from an OAuth JSON response
$connectionInfo = array("Database"=>$azureAdDatabase, "AccessToken"=>$accToken);
$conn = sqlsrv_connect($azureAdServer, $connectionInfo);
if ($conn === false) {
    echo "Could not connect with Azure AD Access Token.\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Azure AD Access Token.\n";
    sqlsrv_close($conn);
}
?>
```

### <a name="pdosqlsrv-driver"></a>PDO_SQLSRV ドライバー

```php
<?php
try {
    // Using an access token to connect: do not pass in $uid or $pwd
    // Assume $accToken is the valid byte string extracted from an OAuth JSON response
    $connectionInfo = "Database = $azureAdDatabase; AccessToken = $accToken;";
    $conn = new PDO("sqlsrv:server = $azureAdServer; $connectionInfo");
    echo "Connected successfully with Azure AD Access Token\n";
    unset($conn);
} catch (PDOException $e) {
    echo "Could not connect with Azure AD Access Token.\n";
    print_r($e->getMessage());
    echo "\n";
}
?>
```

## <a name="example---connect-using-managed-identities-for-azure-resources"></a>例 - Azure リソースの管理対象 id を使用して接続

### <a name="using-the-system-assigned-managed-identity-with-sqlsrv-driver"></a>SQLSRV ドライバーを使用したシステムによって割り当てられた管理対象 id を使用します。

システムによって割り当てられたを使用して接続する管理対象 id、ときに、UID、PWD またはオプションを使わないでください。

```php
<?php

$azureServer = 'myazureserver.database.windows.net';
$azureDatabase = 'myazuredatabase';
$connectionInfo = array('Database'=>$azureDatabase,
                        'Authentication'=>'ActiveDirectoryMsi');
$conn = sqlsrv_connect($azureServer, $connectionInfo);

if ($conn === false) {
    echo "Could not connect with Authentication=ActiveDirectoryMsi (system-assigned).\n";
    print_r(sqlsrv_errors());
} else {
    echo "Connected successfully with Authentication=ActiveDirectoryMsi (system-assigned).\n";
    
    $tsql = "SELECT @@Version AS SQL_VERSION";
    $stmt = sqlsrv_query($conn, $tsql);
    if ($stmt === false) {
        echo "Failed to run the simple query (system-assigned).\n";
        print_r(sqlsrv_errors());
    } else {
        while ($row = sqlsrv_fetch_array($stmt, SQLSRV_FETCH_ASSOC)) {
            echo $row['SQL_VERSION'] . PHP_EOL;
        }

        sqlsrv_free_stmt($stmt);
    }
    
    sqlsrv_close($conn);
}
?>
```

### <a name="using-the-user-assigned-managed-identity-with-pdosqlsrv-driver"></a>PDO_SQLSRV ドライバーでユーザー割り当て管理対象 id を使用

ユーザー割り当て管理対象 id は、スタンドアロン Azure リソースとして作成されます。 Azure では、使用中のサブスクリプションによって信頼されている Azure AD テナントで id を作成します。 Id が作成されると、id は、1 つまたは複数の Azure サービスのインスタンスに割り当てることができます。 コピー、`Object ID`この id とセットの接続文字列で名前をユーザーとして。 

そのため、ユーザー割り当てを使用して接続する管理対象 id、ユーザー名とオブジェクト ID を提供が、パスワードを省略します。

```php
<?php

$azureServer = 'myazureserver.database.windows.net';
$azureDatabase = 'myazuredatabase';
$azureUser = '2d68f56e-9547-4dae-aee8-f3g28ab9674x';    // Object ID of the identity
$connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryMsi;";

try {
    $conn = new PDO("sqlsrv:server = $azureServer; $connectionInfo", $azureUser);
    echo "Connected successfully with Authentication=ActiveDirectoryMsi (user-assigned).\n";
    
    $tsql = "SELECT @@Version AS SQL_VERSION";
    
    try {
        $stmt = $conn->query($tsql);
        $result = $stmt->fetchall(PDO::FETCH_ASSOC);
        print_r($result);

        unset($stmt);
    } catch (PDOException $e) {
        echo "Failed to run the simple query (user-assigned).\n";
    }
    unset($conn);
} catch (PDOException $e) {
    echo "Could not connect with Authentication=ActiveDirectoryMsi (user-assigned).\n";
    print_r($e->getMessage());
    echo "\n";
}
?>
```

## <a name="see-also"></a>参照
[ODBC ドライバーでの Azure Active Directory の使用](https://docs.microsoft.com/sql/connect/odbc/using-azure-active-directory)

[Azure リソースの管理対象の id とは何ですか。](https://docs.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview)
