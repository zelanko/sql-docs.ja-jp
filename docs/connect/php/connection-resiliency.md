---
title: アイドル接続の回復
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.suite: sql
ms.custom: ''
ms.technology:
- drivers
ms.topic: article
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.workload: Inactive
ms.openlocfilehash: a736fc5dafc3c58401c54ab51d1a11d1753f3479
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idle-connection-resiliency"></a>アイドル接続の回復
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[接続の回復](https://msdn.microsoft.com/library/dn632678.aspx)いるアイドル状態の接続を切断された再確立する、特定の制約内での原則がします。 Microsoft SQL Server への接続に失敗した場合は、自動的に接続を再確立しようとするクライアントが、接続の回復できます。 接続の回復は、データ ソースのプロパティ唯一の SQL Server 2014 以降と Azure SQL データベースは、接続の回復をサポートします。

接続の回復は接続文字列に追加できる 2 つの接続キーワードと実装: **ConnectRetryCount**と**ConnectRetryInterval**です。

|Keyword|値|既定値|Description|
|-|-|-|-|
|**ConnectRetryCount**| 0 ~ 255 (包括) の整数|1|渡す前に切断された接続を再確立を試みるの最大数。 既定では、1 回の試行が壊れている場合、接続を再確立しようとするは。 値の 0 の場合は、再接続は試行されません。|
|**ConnectRetryInterval**| 1 ~ 60 (包括) の整数|1| 時間 (秒)、間には、接続が再確立を試みます。 アプリケーションで、途切れた接続を検出するとすぐに再接続を試みますあり待機し、 **ConnectRetryInterval**してから再試行するまでの秒。 場合、このキーワードは無視されます**ConnectRetryCount**が 0 です。

場合、製品の**ConnectRetryCount**を掛けた**ConnectRetryInterval**よりも大きい**LoginTimeout**クライアントは、1 回の接続を試行しなくなりますし、 **LoginTimeout**に達するまで再接続しようとしています。 引き続きそれ以外の場合、その**ConnectRetryCount**に達した。

#### <a name="remarks"></a>解説

接続の回復は、接続がアイドル状態のときに適用されます。 たとえば、トランザクションを実行する – の再接続試行をトリガーしません中に発生するエラーが失敗が予想とします。 不可能のセッションの状態と呼ばれる、次の状況では、再接続の試行はトリガーされません。

* 一時テーブル
* グローバル カーソルとローカル カーソル
* トランザクションのコンテキストおよびセッション レベル トランザクションのロック
* アプリケーション ロック
* EXECUTE AS のセキュリティ コンテキストを元に戻す/
* OLE オートメーション ハンドル
* 準備済みの XML ハンドル
* トレース フラグ

## <a name="example"></a>例

次のコードでは、データベースに接続し、クエリを実行します。 セッションを強制終了して、接続が中断され、切断された接続を使用して、新しいクエリを試行します。 この例では、 [AdventureWorks](https://msdn.microsoft.com/library/ms124501%28v=sql.100%29.aspx)サンプル データベース。

この例では、接続を解除する前に、バッファー内のカーソルを指定します。 場合は、バッファー内のカーソルは指定しないと、接続が再確立できないこと、アクティブなサーバー側カーソルがあるし、そのため、接続はありませんが壊れているアイドル状態であるためです。 ただし、その場合は sqlsrv_free_stmt() シンプロビジョニング、カーソル位置への接続を解除する前に呼び出すことが、接続が正常に再確立します。

```php
<?php
// This function breaks the connection by determining its session ID and killing it.
// A separate connection is used to break the main connection because a session
// cannot kill itself. The sleep() function ensures enough time has passed for KILL
// to finish ending the session.
function BreakConnection( $conn, $conn_break )
{
    $stmt1 = sqlsrv_query( $conn, "SELECT @@SPID" );
    if ( sqlsrv_fetch( $stmt1 ) )
    {
        $spid=sqlsrv_get_field( $stmt1, 0 );
    }

    $stmt2 = sqlsrv_prepare( $conn_break, "KILL ".$spid );
    sqlsrv_execute( $stmt2 );
    sleep(1);
}

// Connect to the local server using Windows authentication and specify
// AdventureWorks as the database in use. Specify values for
// ConnectRetryCount and ConnectRetryInterval as well.
$databaseName = 'AdventureWorks2014';
$serverName = '(local)';
$connectionInfo = array( "Database"=>$databaseName, "ConnectRetryCount"=>10, "ConnectRetryInterval"=>10 );

$conn = sqlsrv_connect( $serverName, $connectionInfo );
if( $conn === false)  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}

// A separate connection that will be used to break the main connection $conn
$conn_break = sqlsrv_connect( $serverName, array( "Database"=>$databaseName) );

// Create a statement to retrieve the contents of a table
$stmt1 = sqlsrv_query( $conn, "SELECT * FROM HumanResources.Employee",
                       array(), array( "Scrollable"=>"buffered" ) );
if( $stmt1 === false )
{
     echo "Error in statement 1.\n";
     die( print_r( sqlsrv_errors(), true ));
}
else
{
    echo "Statement 1 successful.\n";
    $rowcount = sqlsrv_num_rows( $stmt1 );
    echo $rowcount." rows in result set.\n";
}

// Now break the connection $conn
BreakConnection( $conn, $conn_break );

// Create another statement. The connection will be reestablished.
$stmt2 = sqlsrv_query( $conn, "SELECT * FROM HumanResources.Department",
                       array(), array( "Scrollable"=>"buffered" ) );
if( $stmt2 === false )
{
     echo "Error in statement 2.\n";
     die( print_r( sqlsrv_errors(), true ));
}
else
{
    echo "Statement 2 successful.\n";
    $rowcount = sqlsrv_num_rows( $stmt2 );
    echo $rowcount." rows in result set.\n";
}

sqlsrv_close( $conn );
sqlsrv_close( $conn_break );
?>
```
予想される出力:
```
Statement 1 successful.
290 rows in result set.
Statement 2 successful.
16 rows in result set.
```

## <a name="see-also"></a>参照
[Windows ODBC ドライバーの接続の復元性](https://docs.microsoft.com/en-us/sql/connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver)
