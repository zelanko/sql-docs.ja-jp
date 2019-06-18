---
title: '方法: PDO_SQLSRV ドライバーを使用して日付/時刻型を PHP DateTime オブジェクトとして取得する | Microsoft Docs'
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date and time types, retrieving as datetime objects
author: yitam
ms.author: v-yitam
manager: mbarwin
ms.openlocfilehash: 54e5b5c9c1ba59ed64db740fbbb1a643e7cb1b2c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63210435"
---
# <a name="how-to-retrieve-date-and-time-types-as-php-datetime-objects-using-the-pdosqlsrv-driver"></a>方法: PDO_SQLSRV ドライバーを使用して日付/時刻型を PHP DateTime オブジェクトとして取得する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

バージョン 5.6.0 で追加された、この機能は、PDO_SQLSRV ドライバーを使用する場合にのみ有効です、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]します。

### <a name="to-retrieve-date-and-time-types-as-datetime-objects"></a>DateTime オブジェクトとして型を日付と時刻を取得するには

PDO_SQLSRV を使用するときに日付と時刻型 (**smalldatetime**、 **datetime**、**日付**、**時間**、 **datetime2**、および**datetimeoffset**) は、既定の文字列として返されます。 PDO::ATTR_STRINGIFY_FETCHES も PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE 属性は、任意の影響です。 日付と時刻の型として取得するために[PHP DateTime](http://php.net/manual/en/class.datetime.php)オブジェクト、接続やステートメント属性を設定する`PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE`に**true** (は**false**既定で)。

> [!NOTE]
> この接続またはステートメント属性は、DateTime オブジェクトを出力パラメーターとして指定することはできませんので、日付と時刻型の定期的なフェッチにのみ適用されます。

## <a name="example---use-the-connection-attribute"></a>例 - 接続属性を使用して、
次の例では、わかりやすくするためのエラー チェックを省略します。 この 1 つは、接続属性を設定する方法を示します。

```php
<?php
$server = 'myserver';
$databaseName = 'mydatabase';
$username = 'myusername';
$passwd = 'mypasword';
$tableName = 'mytable';

$conn = new PDO("sqlsrv:Server = $server; Database = $databaseName", $username, $passwd);

// To set the connection attribute
$conn->setAttribute(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE, true);
$query = "SELECT DateTimeCol FROM $tableName";
$stmt = $conn->prepare($query);
$stmt->execute();

// Expect a DateTimeCol value as a PHP DateTime type
$row = $stmt->fetch(PDO::FETCH_ASSOC);
var_dump($row);

unset($stmt);
unset($conn);
?>
```

## <a name="example---use-the-statement-attribute"></a>例 - ステートメント属性を使用して、
この例では、ステートメント属性を設定する方法を示します。

```php
<?php
$database = "test";
$server = "(local)";
$conn = new PDO("sqlsrv:server = $server; Database = $database", "", "");
$query = "SELECT DateTimeCol FROM myTable";
$stmt = $conn->prepare($query);
$stmt->setAttribute(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE, true);
$stmt->execute();

// Expect a DateTimeCol value as a PHP DateTime type
$row = $stmt->fetch(PDO::FETCH_NUM);
var_dump($row);

unset($stmt);
unset($conn);
?>
```

## <a name="example---use-the-statement-option"></a>例 - ステートメント オプションを使用
また、オプションとして、ステートメント属性を設定できます。

```php
<?php
$database = "test";
$server = "(local)";
$conn = new PDO("sqlsrv:server = $server; Database = $database", "", "");

$dateObj = null;
$query = "SELECT DateTimeCol FROM aTable";
$options = array(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE => true);
$stmt = $conn->prepare($query, $options);
$stmt->execute();
$stmt->bindColumn(1, $dateObj, PDO::PARAM_LOB);
$row = $stmt->fetch(PDO::FETCH_BOUND);
var_dump($dateObj);

unset($stmt);
unset($conn);
?>
```

## <a name="example---retrieve-datetime-types-as-strings"></a>例 - datetime 型を文字列として取得
次の例では、(これは本当に必要な既定値があるためです)、その逆を実現する方法を示します。

```php
<?php
$database = "MyData";
$conn = new PDO("sqlsrv:server = (local); Database = $database");

$dateStr = null;
$query = 'SELECT DateTimeCol FROM table1';
$options = array(PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE => false);
$stmt = $conn->prepare($query, $options);
$stmt->execute();
$stmt->bindColumn(1, $dateStr);
$row = $stmt->fetch(PDO::FETCH_BOUND);
echo $dateStr . PHP_EOL;

unset($stmt);
unset($conn);
?>
```

## <a name="see-also"></a>参照
[データの取得](../../connect/php/retrieving-data.md)

[SQLSRV ドライバーを使用して日付/時刻型を文字列として取得する](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)