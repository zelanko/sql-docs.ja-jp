---
title: '方法: 送信し、Linux および macOS (SQL) での ASCII データの取得 |Microsoft Docs'
ms.custom: ''
ms.date: 01/16/2018
ms.prod: sql
ms.prod_service: connectivity
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- retrieving data, ASCII data
- sending data
- linux
- macOS
author: yitam
ms.author: v-yitam
manager: mbarwin
ms.openlocfilehash: 0cf0256c337d8851f6223ea895eb7e6d90e30665
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785317"
---
# <a name="how-to-send-and-retrieve-ascii-data-in-linux-and-macos"></a>方法: Linux および macOS での ASCII データの送信と取得 
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

この記事では、ASCII (UTF 8 ではない) のロケールが生成されたまたは、Linux または macOS システムにインストールされている前提としています。 

送信または ASCII を取得するには、文字は、サーバーを設定します。  

1.  目的のロケールでない場合、システム環境の既定の設定を呼び出すように`setlocale(LC_ALL, $locale)`最初の接続を行う前にします。 PHP の setlocale() 関数は、現在のスクリプトのみのロケールを変更し、最初の接続を行った後に呼び出される場合は無視可能性があります。
 
2.  SQLSRV ドライバーを使用する場合を指定できます`'CharacterSet' => SQLSRV_ENC_CHAR`接続としてオプションがこの手順は省略可能ですが、既定のエンコーディングします。

3.  PDO_SQLSRV ドライバーを使用する場合は、2 つの方法があります。 最初に、接続を確立するときに設定`PDO::SQLSRV_ATTR_ENCODING`に`PDO::SQLSRV_ENCODING_SYSTEM`(接続オプションの設定の例は、次を参照してください。 [:: _ _construct](../../connect/php/pdo-construct.md))。 代わりに、正常に接続した後、この行を追加します。 `$conn->setAttribute(PDO::SQLSRV_ATTR_ENCODING, PDO::SQLSRV_ENCODING_SYSTEM);` 
  
(SQLSRV) でリソースを接続または接続オブジェクト (PDO_SQLSRV) のエンコードを指定すると、その他の接続オプション文字列には、その同じエンコーディングを使用するドライバーが前提とします。 サーバー名およびクエリ文字列も同じ文字セットを使用すると見なします。  
  
PDO_SQLSRV ドライバーの既定のエンコーディングは、SQLSRV ドライバーとは異なり、utf-8 (pdo::sqlsrv_encoding_utf8) が。 これらの定数の詳細については、「[定数 &#40;Microsoft Drivers for PHP for SQL Server&#41;](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)」を参照してください。 
  
## <a name="example"></a>例  
次の例では、接続を確立する前に特定のロケールを指定することで SQL Server 用 PHP ドライバーを使用してデータを ASCII を送受信する方法を示します。 さまざまな Linux プラットフォームでのロケールは、macOS で同じロケールから異なるということがあります。 たとえば、米国-iso-8859-1 (Latin 1) ロケールは`en_US.ISO-8859-1`macOS では、名前は、Linux で`en_US.ISO8859-1`します。
  
例では、ある[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]をサーバーにインストールされます。 ブラウザーからこの例を実行すると、すべての出力はブラウザーに書き込まれます。  
  
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
  
