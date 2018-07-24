---
title: Azure Active Directory |Microsoft Docs
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.suite: sql
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.openlocfilehash: 71e6b3b4556621b6bc8a8a4c7996cfdb47a12849
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38979444"
---
# <a name="connect-using-azure-active-directory-authentication"></a>方法: Azure Active Directory 認証を使用して接続する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-whatis) (Azure AD) は、サーバーの全体のユーザー ID 管理テクノロジの代替として動作する[SQL Server 認証](../../connect/php/how-to-connect-using-sql-server-authentication.md)します。 Azure AD はユーザー名とパスワード、Windows 統合認証、または; Azure AD アクセス トークンを使用の Azure AD でフェデレーション id を持つ Microsoft Azure SQL Database と SQL Data Warehouse への接続を許可します。SQL Server 用 PHP ドライバーでは、これらの機能の部分的なサポートを提供します。

Azure AD を使用する、**認証**キーワード。 値を**認証**かかる場合に、次の表で説明します。

|Keyword|値|[説明]|
|-|-|-|
|**[認証]**|(既定) の設定します。|認証モードがその他のキーワードによって決定されます。 詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。 |
||`SqlPassword`|(これは、Azure インスタンスである可能性があります)、SQL Server インスタンスへの直接認証ユーザー名とパスワードを使用します。 ユーザー名とパスワードを使用して、接続文字列に渡す必要がある、 **UID**と**PWD**キーワード。 |
||`ActiveDirectoryPassword`|ユーザー名とパスワードを使用して id を Azure Active Directory で認証します。 ユーザー名とパスワードを使用して、接続文字列に渡す必要がある、 **UID**と**PWD**キーワード。 |

**認証**キーワードが接続のセキュリティ設定に影響します。 既定ではその後、接続文字列に設定されている場合、 **Encrypt**キーワードが true に設定は、クライアントの暗号化を要求するようにします。 さらに、サーバー証明書が暗号化の設定に関係なく検証する場合を除き、 **TrustServerCertificate**設定が true に設定します。 これには、古いと、暗号化は、接続文字列で具体的には要求されない限り、サーバー証明書は検証されません、セキュリティで保護されたの login メソッドは区別されます。

Azure AD を Windows 上の SQL Server の PHP ドライバーと共に使用する前にインストールされていることを確認、 [Microsoft Online Services サインイン アシスタント](https://www.microsoft.com/download/details.aspx?id=41950)(Linux と MacOS は必要ありません)。

#### <a name="limitations"></a>制限事項

、Windows では、基になる ODBC ドライバーは、1 つ以上の値をサポートしています、**認証**キーワード、 **ActiveDirectoryIntegrated**、PHP ドライバーでは、任意のプラットフォームでは、この値はできませんが、ため、またAzure AD トークン ベース認証をサポートしていません。

## <a name="example"></a>例

次の例を使用して接続する方法を示しています。 **SqlPassword**と**ActiveDirectoryPassword**します。

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

次の例では、上記と同じ PDO_SQLSRV ドライバーを使用します。

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
[ODBC ドライバーでの Azure Active Directory の使用](https://docs.microsoft.com/sql/connect/odbc/using-azure-active-directory)
