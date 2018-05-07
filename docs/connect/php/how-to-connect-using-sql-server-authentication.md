---
title: '方法: SQL Server 認証を使用して接続 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- connecting to the server, SQL Server Authentication
ms.assetid: 8d298830-3186-47e7-aef6-586b457901c1
caps.latest.revision: 34
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6991014daf7c1ac11aee177b9d81f489d5b1bf6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-connect-using-sql-server-authentication"></a>方法: SQL Server 認証を使用して接続する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] は、SQL Server への接続時に SQL Server 認証をサポートしています。  
  
SQL Server 認証は、Windows 認証が使用できない場合にのみ使用します。 Windows 認証を使用した接続の詳細については、「 [How to: Connect Using Windows Authentication](../../connect/php/how-to-connect-using-windows-authentication.md)」を参照してください。  
  
SQL Server 認証を使用して SQL Server に接続する場合は、次の点を考慮する必要があります。  
  
-   サーバーで SQL Server の混合モード認証を有効にする必要があります。  
  
-   ユーザー ID とパスワード (*UID*と*PWD* SQLSRV ドライバーで接続属性) の接続を確立するときに設定する必要があります。 ユーザー ID とパスワードは、有効な SQL Server ユーザー名とパスワードにマップする必要があります。  
  
> [!NOTE]  
> 右中かっこ (}) を含むパスワードは、2 つ目の右中かっこでエスケープする必要があります。 たとえば、SQL Server のパスワードが "pass}word" の場合、 *PWD* 接続属性の値を "pass}}word" に設定する必要があります。  
  
SQL Server 認証を使用して SQL Server に接続する場合は、次の予防措置を実行する必要があります。  
  
-   ネットワーク経由で Web サーバーからデータベースに渡された資格情報を保護 (暗号化) します。 SQL Server 2005 以降では、資格情報は既定で暗号化されます。 セキュリティ強化のために、暗号化接続属性を「オン」に設定し、サーバーに送信されるすべてのデータを暗号化します。  
  
> [!NOTE]  
> 暗号化接続属性を「オン」に設定すると、データの暗号化によってコンピューターに負荷がかかるため、パフォーマンスが低下する場合があります。  
  
-   PHP スクリプトのプレーン テキストには、接続属性 *UID* と *PWD* の値を含めないでください。 これらの値は、適切な制限されたアクセス許可を持つアプリケーション固有のディレクトリに格納する必要があります。  
  
-   *sa* アカウントは使用しないでください。 必要な特権を持つデータベース ユーザーにアプリケーションをマップし、強力なパスワードを使用します。  
  
> [!NOTE]  
> 接続を確立するときに、ユーザー ID とパスワードに加え、接続属性を設定できます。 サポートされている接続属性の一覧については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。  
  
## <a name="example"></a>例  
次の例では、SQL Server 認証で SQLSRV ドライバーを使用して、SQL Server のローカル インスタンスに接続します。 必須の値は、 *UID*と*PWD*接続属性は、アプリケーション固有のテキスト ファイルから取得*uid.txt*と*pwd.txt*で、 *C:\AppData*ディレクトリ。 接続が確立されると、ユーザーのログインを確認するためにサーバーが照会されます。  
  
例では、SQL Server および[AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works)データベースがローカル コンピューターにインストールされています。 ブラウザーからこの例を実行すると、すべての出力はブラウザーに書き込まれます。  
  
```  
<?php  
/* Specify the server and connection string attributes. */  
$serverName = "(local)";  
  
/* Get UID and PWD from application-specific files.  */  
$uid = file_get_contents("C:\AppData\uid.txt");  
$pwd = file_get_contents("C:\AppData\pwd.txt");  
$connectionInfo = array( "UID"=>$uid,  
                         "PWD"=>$pwd,  
                         "Database"=>"AdventureWorks");  
  
/* Connect using SQL Server Authentication. */  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Unable to connect.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Query SQL Server for the login of the user accessing the  
database. */  
$tsql = "SELECT CONVERT(varchar(32), SUSER_SNAME())";  
$stmt = sqlsrv_query( $conn, $tsql);  
if( $stmt === false )  
{  
     echo "Error in executing query.</br>";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Retrieve and display the results of the query. */  
$row = sqlsrv_fetch_array($stmt);  
echo "User login: ".$row[0]."</br>";  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>例  
このサンプルでは、PDO_SQLSRV ドライバーを使用して、SQL Server 認証で接続する方法を示します。  
  
```  
<?php  
   $serverName = "(local)";   
   $database = "AdventureWorks";  
  
   // Get UID and PWD from application-specific files.   
   $uid = file_get_contents("C:\AppData\uid.txt");  
   $pwd = file_get_contents("C:\AppData\pwd.txt");  
  
   try {  
      $conn = new PDO( "sqlsrv:server=$serverName;Database = $database", $uid, $pwd);   
      $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );   
   }  
  
   catch( PDOException $e ) {  
      die( "Error connecting to SQL Server" );   
   }  
  
   echo "Connected to SQL Server\n";  
  
   $query = 'select * from Person.ContactType';   
   $stmt = $conn->query( $query );   
   while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){   
      print_r( $row );   
   }  
  
   // Free statement and connection resources.   
   $stmt = null;   
   $conn = null;   
?>  
```  
  
## <a name="see-also"></a>参照  
[方法: SQL Server 認証を使用して接続する](../../connect/php/how-to-connect-using-sql-server-authentication.md)

[For PHP for SQL Server の Microsoft drivers ガイドのプログラミング](../../connect/php/programming-guide-for-php-sql-driver.md)

[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)

[SUSER_SNAME (TRANSACT-SQL)](../../t-sql/functions/suser-sname-transact-sql.md)

[方法: SQL Server ログインの作成](../../relational-databases/security/authentication-access/create-a-login.md)

[方法: データベース ユーザーの作成](../../relational-databases/security/authentication-access/create-a-database-user.md)

[ユーザー、ロール、およびログインの管理](../../relational-databases/server-management-objects-smo/tasks/managing-users-roles-and-logins.md)

[ユーザーとスキーマの分離](../../relational-databases/server-management-objects-smo/tasks/managing-users-roles-and-logins.md)

[オブジェクト アクセス許可 (TRANSACT-SQL)](../../t-sql/statements/grant-object-permissions-transact-sql.md)  
  
