---
title: 接続のプール (Microsoft SQL Server 用 Drivers for PHP) | Microsoft Docs
ms.custom: ''
ms.date: 08/01/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection pooling support
ms.assetid: 4d9a83d4-08de-43a1-975c-0a94005edc94
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e6dc56d020af182d657ec2766d996601e5442686
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47624990"
---
# <a name="connection-pooling-microsoft-drivers-for-php-for-sql-server"></a>接続のプール (Microsoft SQL Server 用 Drivers for PHP)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]の接続のプールについて重要な点は、次のとおりです。  
  
-   [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] では ODBC 接続プールが使用されます。  
  
-   Windows の既定では、接続プールは有効になっています。 ODBC 接続プールが有効な場合にのみ、Linux と macOS で接続がプールされる (を参照してください[接続プールの有効化/無効化](#enablingdisabling-connection-pooling))。 接続プールが有効にすると、サーバーに接続する、ドライバーは、新しいものを作成する前に、プールされた接続を使用しようとします。 プールに同等の接続がない場合、新しい接続が構築され、プールに追加されます。 ドライバーは、接続文字列の比較に基づき、接続が同等かどうかを判断します。  
  
-   プールの接続が使用されると、接続状態がリセットされます。  
  
-   接続を閉じると、接続がプールに返されます。  
  
接続のプールについて詳しくは、「[ドライバー マネージャーの接続プール](../../odbc/reference/develop-app/driver-manager-connection-pooling.md)」をご覧ください。  
  
## <a name="enablingdisabling-connection-pooling"></a>有効化/無効にする接続プール
### <a name="windows"></a>Windows
(接続プールで同等の接続を探す代わりに) 新しい接続を構築するようにドライバーに強制できます。その場合、接続文字列の *ConnectionPooling* 属性を **false** (または 0) に設定します。  
  
接続文字列から *ConnectionPooling* 属性を省略する場合、あるいは **true** (または 1) に設定する場合、同等の接続が接続プールに存在しないときにのみ、ドライバーは新しい接続を構築します。  
  
その他の接続属性の詳細については、「 [Connection Options](../../connect/php/connection-options.md)」を参照してください。  
### <a name="linux-and-macos"></a>Linux および macOS
*ConnectionPooling*属性を使用して、接続プールを有効または無効にすることはできません。 

接続プール有効/無効にできます odbcinst.ini の構成ファイルを編集します。 ドライバーを有効にする変更を再読み込みする必要があります。

設定`Pooling`に`Yes`、正の値と`CPTimeout`odbcinst.ini ファイル内の値は、接続プールを有効になります。 
```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
CPTimeout=<int value>
```
  
少なくとも、odbcinst.ini ファイルは、この例のようになる必要があります。

```
[ODBC]
Pooling=Yes

[ODBC Driver 13 for SQL Server]
Description=Microsoft ODBC Driver 13 for SQL Server
Driver=/opt/microsoft/msodbcsql/lib64/libmsodbcsql-13.1.so.3.0
UsageCount=1
CPTimeout=120
```

設定`Pooling`に`No`odbcinst.ini 内ファイルが新しい接続を作成するドライバーを強制します。
```
[ODBC]
Pooling=No
```

## <a name="remarks"></a>Remarks
- Linux または macOS では、odbcinst.ini ファイルにプールが有効になっている場合、すべての接続がプールされます。 つまり、ConnectionPooling 接続オプションが影響を与えません。 プーリングを無効にするには、プールを設定 = odbcinst.ini ファイル内の No とドライバーを再読み込みします。
  - unixODBC < 2.3.4 = エラー メッセージ、警告および情報メッセージなどの適切な診断情報は (Linux と macOS) で返すしない可能性があります
  - この理由から、SQLSRV と PDO_SQLSRV ドライバーを文字列として (xml、バイナリ) などの長い形式のデータを正しく取得できませんできません可能性があります。 回避策としてストリームとして、長い形式のデータをフェッチすることができます。 SQLSRV は、次の例を参照してください。

```
<?php
$connectionInfo = array("Database"=>"test", "UID"=>"username", "PWD"=>"password");

$conn1 = sqlsrv_connect("servername", $connectionInfo);

$longSample = str_repeat("a", 8500);
$xml1 = 
'<ParentXMLTag>
  <ChildTag01>'.$longSample.'</ChildTag01>
</ParentXMLTag>';

// Create table and insert xml string into it
sqlsrv_query($conn1, "CREATE TABLE xml_table (field xml)");
sqlsrv_query($conn1, "INSERT into xml_table values ('$xml1')");

// retrieve the inserted xml
$column1 = getColumn($conn1);

// return the connection to the pool
sqlsrv_close($conn1);

// This connection is from the pool
$conn2 = sqlsrv_connect("servername", $connectionInfo);
$column2 = getColumn($conn2);

sqlsrv_query($conn2, "DROP TABLE xml_table");
sqlsrv_close($conn2);

function getColumn($conn)
{
    $tsql = "SELECT * from xml_table";
    $stmt = sqlsrv_query($conn, $tsql);
    sqlsrv_fetch($stmt);
    // This might fail in Linux and macOS
    // $column = sqlsrv_get_field($stmt, 0, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR));
    // The workaround is to fetch it as a stream
    $column = sqlsrv_get_field($stmt, 0, SQLSRV_PHPTYPE_STREAM(SQLSRV_ENC_CHAR));
    sqlsrv_free_stmt($stmt);
    return ($column);
}
?>
```


## <a name="see-also"></a>参照  
[方法: Windows 認証を使用して接続する](../../connect/php/how-to-connect-using-windows-authentication.md)

[方法: SQL Server 認証を使用して接続する](../../connect/php/how-to-connect-using-sql-server-authentication.md)  
  
