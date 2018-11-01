---
title: アイドル状態の接続の回復性
ms.date: 07/13/2017
ms.prod: sql
ms.prod_service: connectivity
ms.custom: ''
ms.technology: connectivity
ms.topic: conceptual
author: david-puglielli
ms.author: v-dapugl
manager: v-hakaka
ms.openlocfilehash: 34d4bc2342397f5809ef16ef59ed342d6c86d421
ms.sourcegitcommit: ef78cc196329a10fc5c731556afceaac5fd4cb13
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/19/2018
ms.locfileid: "49460377"
---
# <a name="idle-connection-resiliency"></a>アイドル状態の接続の回復性
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[接続の回復性](https://msdn.microsoft.com/library/dn632678.aspx)は、壊れているアイドル状態の接続を再確立する、特定の制約内で原則です。 Microsoft SQL Server への接続に失敗した場合は、自動的に接続を再確立しようとするクライアントが、接続の回復できます。 接続の回復性は、データ ソースのプロパティ唯一の SQL Server 2014 以降と Azure SQL Database は、接続の回復性をサポートします。

接続文字列に追加できる 2 つの接続キーワードを持つ接続の回復性が実装されている: **ConnectRetryCount**と**ConnectRetryInterval**します。

|Keyword|値|既定|[説明]|
|-|-|-|-|
|**ConnectRetryCount**| 0 ~ 255 (両端を含む) の整数|1|を行う前に切断された接続を再確立を試みるの最大数。 既定では、発生した場合に、接続を再確立するため 1 回の試行が行われます。 値の 0 の場合は、再接続は試行されません。|
|**ConnectRetryInterval**| 1 ~ 60 (包括) の整数|1| 時間 (秒単位) の間には、接続が再確立を試行します。 アプリケーションで、途切れた接続を検出するとすぐに再接続を試みますあり待機し**ConnectRetryInterval**してから再試行するまでの秒。 場合、このキーワードは無視されます**ConnectRetryCount**が 0 です。

場合、製品の**ConnectRetryCount**を乗算して**ConnectRetryInterval**よりも大きい**LoginTimeout**、1 回の接続を試みているクライアントが停止し、 **LoginTimeout**に達するまで再接続しようとするそれ以外の場合、これは引き続き**ConnectRetryCount**に到達します。

#### <a name="remarks"></a>Remarks

接続がアイドル状態のとき、接続の回復性が適用されます。 たとえば、トランザクションの実行は再接続の試行はトリガーされません中に発生する障害が予想とは失敗します。 回復不可能のセッションの状態と呼ばれる、次の状況では、再接続の試行はトリガーされません。

* 一時テーブル
* グローバルとローカル カーソル
* トランザクションのコンテキストとセッション レベルのトランザクションのロック
* アプリケーション ロック
* EXECUTE AS]、[セキュリティ コンテキストを元に戻す
* OLE オートメーション処理します。
* 準備済みの XML ハンドル
* トレース フラグ

## <a name="example"></a>例

次のコードでは、データベースに接続し、クエリを実行します。 セッションを強制終了して、接続が中断され、切断された接続を使用して新しいクエリを試行します。 この例では、[AdventureWorks](https://msdn.microsoft.com/library/ms124501%28v=sql.100%29.aspx) サンプル データベースを使用します。

この例では、接続を解除する前に、バッファー内のカーソルを指定します。 バッファー内のカーソルを指定していない場合、アクティブなサーバー側カーソルがあるし、そのため、接続がアイドル状態にならないが壊れているため、接続が再確立されませんが。 ただし、場合 sqlsrv_free_stmt()、カーソルのシンプロビジョニングへの接続を解除する前に呼び出すことが、接続が正常に再確立します。

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
[Windows ODBC ドライバーの接続の復元性](https://docs.microsoft.com/sql/connect/odbc/windows/connection-resiliency-in-the-windows-odbc-driver)
