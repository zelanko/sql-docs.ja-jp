---
title: "Azure Active Directory |Microsoft ドキュメント"
ms.date: 07/13/2017
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.topic: article
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 01d921ebee152924b905fa7a9de8c6d46f41ca64
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connect-using-azure-active-directory-authentication"></a>Azure Active Directory 認証を使用して接続します。
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-whatis) (Azure AD) は、代替手段として動作する中央のユーザー ID 管理テクノロジ[SQL Server 認証](../../connect/php/how-to-connect-using-sql-server-authentication.md)です。 Azure AD によりフェデレーション id を持つ Microsoft Azure SQL Database と SQL データ ウェアハウスへの接続では、Azure AD を使用して、ユーザー名とパスワード、Windows 統合認証、または Azure AD アクセス トークンです。SQL Server 用 PHP ドライバーでは、これらの機能の部分的なサポートを提供します。

Azure AD を使用する、**認証**キーワード。 値を**認証**かかる場合に、次の表で説明します。

|Keyword|値|Description|
|-|-|-|
|**[認証]**|(既定) の設定します。|認証モードがその他のキーワードによって決定されます。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。 |
||`SqlPassword`|(Azure のインスタンスがあります) を SQL Server インスタンスへの直接認証ユーザー名とパスワードを使用します。 ユーザー名とパスワードを使用する接続文字列に渡す必要があります、 **UID**と**PWD**キーワード。 |
||`ActiveDirectoryPassword`|ユーザー名とパスワードを使用して Azure Active Directory id を認証します。 ユーザー名とパスワードを使用する接続文字列に渡す必要があります、 **UID**と**PWD**キーワード。 |

**認証**キーワードが接続のセキュリティ設定に影響します。 既定では、接続文字列に設定されている場合、**暗号化**キーワードが true に設定は、クライアントは暗号化を要求するようにします。 さらに、サーバー証明書は、暗号化設定に関係なく、検証する場合を除き、 **TrustServerCertificate**設定が true に設定します。 これには、古いと、セキュリティで保護された、ログイン メソッドを暗号化は接続文字列で個別に要求しない限り、サーバー証明書は検証されません低は区別されます。

SQL Server on Windows 用 PHP ドライバーで Azure AD を使用して、前にインストールしてあることを確認してください、 [Microsoft Online Services サインイン アシスタント](https://www.microsoft.com/download/details.aspx?id=41950)(Linux と MacOS は必要ありません)。

#### <a name="limitations"></a>制限事項

基になる ODBC ドライバーを Windows では、1 つ以上の値をサポートしている、**認証**キーワード、 **ActiveDirectoryIntegrated**、PHP ドライバーでは、任意のプラットフォームでは、この値はできませんが、つまりもAzure AD トークン ベースの認証をサポートしていません。

## <a name="example"></a>例

次の例を使用して接続する方法を示しています。 **SqlPassword**と**ActiveDirectoryPassword**です。

```php
    <?php
    // First connect to a local SQL Server instance by setting Authentication to SqlPassword
    $serverName = "myserver.mydomain";

    $connectionInfo = array( "UID"=>$myusername, "PWD"=>$mypassword, "Authentication"=>'SqlPassword' );

    $conn = sqlsrv_connect( $serverName, $connectionInfo );
    if( $conn === false )
    {
        echo "Could not connect with Authentication=SqlPassword.\n";
        print_r( sqlsrv_errors() );
    }
    else
    {
        echo "Connected successfully with Authentication=SqlPassword.\n";
        sqlsrv_close( $conn );
    }

    // Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
    $azureServer = "myazureserver.database.windows.net";
    $azureDatabase = "myazuredatabase";
    $azureUsername = "myuid";
    $azurePassword = "mypassword";
    $connectionInfo = array( "Database"=>$azureDatabase, "UID"=>$azureUsername, "PWD"=>$azurePassword,
                             "Authentication"=>'ActiveDirectoryPassword' );

    $conn = sqlsrv_connect( $azureServer, $connectionInfo );
    if( $conn === false )
    {
        echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
        print_r( sqlsrv_errors() );
    }
    else
    {
        echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
        sqlsrv_close( $conn );
    }

    ?>
```

次の例では、上記と同じ PDO_SQLSRV ドライバーで。

```php
    <?php
    // First connect to a local SQL Server instance by setting Authentication to SqlPassword
    $serverName = "myserver.mydomain";

    $connectionInfo = "Database = $databaseName; Authentication = SqlPassword;";

    try
    {
        $conn = new PDO( "sqlsrv:server = $serverName ; $connectionInfo", $myusername, $mypassword );
        echo "Connected successfully with Authentication=SqlPassword.\n";
        $conn = null;
    }
    catch( PDOException $e )
    {
        echo "Could not connect with Authentication=SqlPassword.\n";
        print_r( $e->getMessage() );
        echo "\n";
    }

    // Now connect to an Azure SQL database by setting Authentication to ActiveDirectoryPassword
    $azureServer = "myazureserver.database.windows.net";
    $azureDatabase = "myazuredatabase";
    $azureUsername = "myuid";
    $azurePassword = "mypassword";
    $connectionInfo = "Database = $azureDatabase; Authentication = ActiveDirectoryPassword;";

    try
    {
        $conn = new PDO( "sqlsrv:server = $azureServer ; $connectionInfo", $azureUsername, $azurePassword );
        echo "Connected successfully with Authentication=ActiveDirectoryPassword.\n";
        $conn = null;
    }
    catch( PDOException $e )
    {
        echo "Could not connect with Authentication=ActiveDirectoryPassword.\n";
        print_r( $e->getMessage() );
        echo "\n";
    }

    ?>
```
## <a name="see-also"></a>参照  
[ODBC ドライバーで Azure Active Directory の使用](https://docs.microsoft.com/en-us/sql/connect/odbc/using-azure-active-directory)

