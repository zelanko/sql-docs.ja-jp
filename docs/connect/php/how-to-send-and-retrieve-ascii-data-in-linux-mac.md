---
title: '方法: 送信し、Linux および macOS (SQL) で ASCII データの取得 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 01/16/2018
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- retrieving data, ASCII data
- sending data
- linux
- macOS
author: yitam
ms.author: v-yitam
manager: mbarwin
ms.workload: On Demand
ms.openlocfilehash: 7f4fae285dbda78011f5e56d6c063fb402ae856f
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-send-and-retrieve-ascii-data-in-linux-and-macos"></a>方法: 送信し、Linux および macOS で ASCII データの取得 
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

この記事では、ASCII (非 utf-8) のロケールが生成されたか、Linux または macOS システムにインストールされていると仮定します。 

送信するか、サーバーに ASCII 文字セットを取得します。  

1.  目的のロケールでない場合、システム環境での既定を呼び出すように`setlocale(LC_ALL, $locale)`最初の接続を行う前にします。 PHP setlocale() 関数は、現在のスクリプトのみのロケールを変更して、呼び出される場合、最初の接続を行った後、それを無視してかまいません。
 
2.  SQLSRV ドライバーを使用する場合を指定すること`'CharacterSet' => SQLSRV_ENC_CHAR`接続としてオプションがこの手順は省略可能なであるため、既定のエンコーディングします。

3.  PDO_SQLSRV ドライバーを使用する場合は、次の 2 つの方法があります。 まず、接続時に、設定`PDO::SQLSRV_ATTR_ENCODING`に`PDO::SQLSRV_ENCODING_SYSTEM`(接続オプションの設定の例は、次を参照してください。 [:: _ _construct](../../connect/php/pdo-construct.md))。 代わりに、正常に接続後、この行を追加します。 `$conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);` 
  
接続リソース (SQLSRV) または接続オブジェクト (PDO_SQLSRV) のエンコーディングを指定する場合、ドライバーは、その他の接続オプション文字列がその同じエンコードを使用すると見なします。 サーバー名およびクエリ文字列も同じ文字セットを使用すると見なします。  
  
PDO_SQLSRV ドライバーの既定のエンコーディング utf-8 (pdo::sqlsrv_encoding_utf8) とは、SQLSRV ドライバー異なります。 これらの定数の詳細については、次を参照してください。[定数&#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)です。 
  
## <a name="example"></a>例  
次の例では、接続を確立する前に特定のロケールを指定することによって SQL Server 用 PHP ドライバーを使用してデータを ASCII を送受信する方法を示します。 さまざまな Linux プラットフォームにロケールは、macOS で同じロケールからが異なるということがあります。 たとえば、米国 ISO 8859-1 (ラテン 1) ロケールは`en_US.ISO-8859-1`macOS では、名前は、Linux で`en_US.ISO8859-1`です。
  
例では、あると想定[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]サーバーにインストールします。 例では、ブラウザーから実行時に、すべての出力はブラウザーに書き込まれます。  
  
```  
<?php  
  
// SQLSRV Example
//
// Setting locale for the script is only necessary if Latin 1 is not the default 
// in the environment
$locale = strtoupper(PHP_OS) === 'LINUX' ? 'en_US.ISO-8859-1' : 'en_US.ISO8859-1';
setlocale(LC_ALL, $locale);
        
$serverName = 'MyServer';
$database = 'Test';
$connectionInfo = array('Database'=>'Test', 'UID'=>$uid, 'PWD'=>$pwd);
$conn = sqlsrv_connect($serverName, $connectionInfo);
  
if ($conn === false) {
    echo "Could not connect.<br>";  
    die(print_r(sqlsrv_errors(), true));
}  
  
// Set up the Transact-SQL query to create a test table
//   
$stmt = sqlsrv_query($conn, "CREATE TABLE [Table1] ([c1_int] int, [c2_varchar] varchar(512))");

// Insert data using a parameter array 
//
$tsql = "INSERT INTO [Table1] (c1_int, c2_varchar) VALUES (?, ?)";
  
// Execute the query, $value being some ASCII string
//   
$stmt = sqlsrv_query($conn, $tsql, array(1, array($value, SQLSRV_PARAM_IN, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR))));
  
if ($stmt === false) {
    echo "Error in statement execution.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  
else {  
    echo "The insertion was successfully executed.<br>";  
}  
  
// Retrieve the newly inserted data
//   
$stmt = sqlsrv_query($conn, "SELECT * FROM Table1");
$outValue = null;  
if ($stmt === false) {  
    echo "Error in statement execution.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  
  
// Retrieve and display the data
//   
if (sqlsrv_fetch($stmt)) {  
    $outValue = sqlsrv_get_field($stmt, 1, SQLSRV_PHPTYPE_STRING(SQLSRV_ENC_CHAR));
    echo "Value: " . $outValue . "<br>";
    if ($value !== $outValue) {
        echo "Data retrieved, \'$outValue\', is unexpected!<br>";
    }
}  
else {  
    echo "Error in fetching data.<br>";  
    die(print_r(sqlsrv_errors(), true));  
}  

// Free statement and connection resources
//   
sqlsrv_free_stmt($stmt);  
sqlsrv_close($conn);  
?>  
```  
  
```
<?php  
  
// PDO_SQLSRV Example:
//
// Setting locale for the script is only necessary if Latin 1 is not the default 
// in the environment
$locale = strtoupper(PHP_OS) === 'LINUX' ? 'en_US.ISO-8859-1' : 'en_US.ISO8859-1';
setlocale(LC_ALL, $locale);
        
$serverName = 'MyServer';
$database = 'Test';

try {
    $conn = new PDO("sqlsrv:Server=$serverName;Database=$database;", $uid, $pwd);
    $conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);
    
    // Set up the Transact-SQL query to create a test table
    //   
    $stmt = $conn->query("CREATE TABLE [Table1] ([c1_int] int, [c2_varchar] varchar(512))");
    
    // Insert data using parameters, $value being some ASCII string
    //
    $stmt = $conn->prepare("INSERT INTO [Table1] (c1_int, c2_varchar) VALUES (:var1, :var2)");
    $stmt->bindValue(1, 1);
    $stmt->bindParam(2, $value);
    $stmt->execute();
    
    // Retrieve and display the data
    //
    $stmt = $conn->query("SELECT * FROM [Table1]");
    $outValue = null;
    if ($row = $stmt->fetch()) {
        $outValue = $row[1];
        echo "Value: " . $outValue . "<br>";
        if ($value !== $outValue) {
            echo "Data retrieved, \'$outValue\', is unexpected!<br>";
        }
    }
} catch (PDOException $e) {
    echo $e->getMessage() . "<br>";
} finally {
    // Free statement and connection resources
    //
    unset($stmt);
    unset($conn);
}

?>  
```  

## <a name="see-also"></a>参照  
[データの取得](../../connect/php/retrieving-data.md)  
[Utf-8 データを扱う](../../connect/php/how-to-send-and-retrieve-utf-8-data-using-built-in-utf-8-support.md)
[データの更新&#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/updating-data-microsoft-drivers-for-php-for-sql-server.md)  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[定数 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  
[サンプル アプリケーション &#40;SQLSRV ドライバー&#41;](../../connect/php/example-application-sqlsrv-driver.md)  
  
