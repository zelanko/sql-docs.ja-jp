---
title: 取得日付と時刻、SQLSRV ドライバーを使用して文字列として入力 |。Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- date and time types, retrieving as strings
ms.assetid: 58a974ea-4daf-4e3b-98ed-9731b9c9250f
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 054212489b4c30a8355eff64d5928be16018ff29
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver"></a>方法: SQLSRV ドライバーを利用し、日付/時刻型を取得する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

この機能は [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] のバージョン 1.1 に追加されました。 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]の SQLSRV ドライバーの利用時にのみ有効です。 PDO_SQLSRV ドライバーと共に ReturnDatesAsStrings 接続オプションを使用することは間違いです。  
  
日付と時刻型を取得することができます (**datetime**、**日付**、**時間**、 **datetime2**、および**datetimeoffset**)として文字列、接続文字列で、オプションを指定します。  
  
### <a name="to-retrieve-date-and-time-types-as-strings"></a>日付と時刻型を文字列として取得する方法  
  
-   次の接続オプションを使用します。  
  
    ```  
    'ReturnDatesAsStrings'=>true  
    ```  
  
    既定値は **false**です。つまり、 **datetime**、 **Date**、 **Time**、 **DateTime2**、および **DateTimeOffset** 型は PHP **Datetime** 型として返されます。  
  
## <a name="example"></a>例  
次は、日付/時刻型を文字列として取得する構文の例です。  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'ReturnDatesAsStrings '=> true);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>例  
次の例を使用して接続した場合でも、文字列を取得するときに、utf-8 を指定することで日付を文字列としてを取得できる`"ReturnDatesAsStrings" => false`です。  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", "ReturnDatesAsStrings" => false);  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0, SQLSRV_PHPTYPE_STRING("UTF-8"));  
  
if( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
echo $date;  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>例  
次の例では、utf-8 を指定することによって文字列としての日付を取得する方法と`"ReturnDatesAsStrings" => true`接続文字列にします。  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks", 'ReturnDatesAsStrings'=> true, "CharacterSet" => 'utf-8' );  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0 );  
  
if ( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
echo $date;  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="example"></a>例  
次のコード例では、日付を PHP 型として取得する方法を示します。 `'ReturnDatesAsStrings'=> false` は既定でオンです。  
  
```  
<?php  
$serverName = "MyServer";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false ) {  
   echo "Could not connect.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
$tsql = "SELECT VersionDate FROM AWBuildVersion";  
  
$stmt = sqlsrv_query( $conn, $tsql);  
  
if ( $stmt === false ) {  
   echo "Error in statement preparation/execution.\n";  
   die( print_r( sqlsrv_errors(), true));  
}  
  
sqlsrv_fetch( $stmt );  
  
// retrieve date as string  
$date = sqlsrv_get_field( $stmt, 0 );  
  
if ( $date === false ) {  
   die( print_r( sqlsrv_errors(), true ));  
}  
  
$date_string = date_format( $date, 'jS, F Y' );  
echo "Date = $date_string\n";  
  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>参照  
[データの取得](../../connect/php/retrieving-data.md)  
  
