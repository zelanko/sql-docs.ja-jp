---
title: 10 進数文字列と金額の書式設定 (PDO_SQLSRV ドライバー) | Microsoft Docs
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- formatting, decimal types, money values
author: yitam
ms.author: v-yitam
manager: mbarwin
ms.openlocfilehash: 35626c192c3d74ad0201cee3c5e97adbce92a3aa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62669697"
---
# <a name="formatting-decimal-strings-and-money-values-pdosqlsrv-driver"></a>10 進数文字列と金額の書式設定 (PDO_SQLSRV ドライバー)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

精度を保持するために[decimal 型または numeric 型](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql)が常に、正確な精度と小数点を含む文字列としてフェッチします。 任意の値が 1 未満の場合は、先行ゼロがありません。 固定桁数が 4 に等しい 10 進数のフィールドは money と smallmoney フィールドと同じです。

## <a name="add-leading-zeroes-if-missing"></a>不足している場合は、先頭のゼロを追加します。
以降では、バージョン 5.6.0、接続、またはステートメント属性`PDO::SQLSRV_ATTR_FORMAT_DECIMALS`により、ユーザーは、10 進数値文字列の形式を指定します。 この属性は、ブール値を (true または false) が必要ですが、フェッチされた結果の 10 進数または数値の値の書式設定にのみ影響します。 つまり、この属性は、挿入や更新などその他の操作に影響を与えません。

既定では、`PDO::SQLSRV_ATTR_FORMAT_DECIMALS` は **false** です。 場合は true、10 進数値文字列に先頭のゼロに設定は、1 未満の 10 進値に対する追加されます。

## <a name="configure-number-of-decimal-places"></a>小数点以下桁数を構成します。
`PDO::SQLSRV_ATTR_FORMAT_DECIMALS`有効で、もう 1 つの接続やステートメント属性`PDO::SQLSRV_ATTR_DECIMAL_PLACES`money と smallmoney データを表示するときに、小数点以下桁数を構成することができます。 範囲の整数値を受け取って [0, 4] に表示するときに発生する可能性があります丸め処理を行うとします。 ただし、基になるの money 型データは同じです。

ステートメント属性は、常に対応する接続設定をオーバーライドします。 なお、`PDO::SQLSRV_ATTR_DECIMAL_PLACES`オプション**のみ**money のデータと`PDO::SQLSRV_ATTR_FORMAT_DECIMALS`設定する必要がありますを true にします。 それ以外の場合、書式設定がオフに関係なく`PDO::SQLSRV_ATTR_DECIMAL_PLACES`設定します。

> [!NOTE]
> 設定するため、money または smallmoney フィールドがあるスケール 4 は、`PDO::SQLSRV_ATTR_DECIMAL_PLACES`を負の数値またはその値を超えるを設定すると 4 は無視されます。 すべての計算を入力として書式設定されたコスト データを使用することは推奨されません。

### <a name="to-set-the-connection-attributes"></a>接続属性を設定するには

-   接続の時点での属性を設定します。

    ```php
    $attrs = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => true,
                   PDO::SQLSRV_ATTR_DECIMAL_PLACES => 2);

    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password, $attrs);
    ```

-   Post 接続属性を設定します。

    ```php
    $conn = new PDO("sqlsrv:Server = myServer; Database = myDB", $username, $password);
    $conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
    $conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);
    ```

## <a name="example---format-money-data"></a>Money 型データの形式の使用例
次の例を使用してコスト データをフェッチする方法を示しています[pdostatement::bindcolumn](../../connect/php/pdostatement-bindcolumn.md):。

```php
<?php
$database = "myDB";
$server = "(local)";
$conn = new PDO( "sqlsrv:server=$server; Database = $database", "", "");
$conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);

$numDigits = 3;
$query = "SELECT smallmoney1 FROM aTable";
$options = array(PDO::SQLSRV_ATTR_DECIMAL_PLACES => $numDigits);
$stmt = $conn->prepare($query, $options);
$stmt->execute();

$stmt->bindColumn('smallmoney1', $field);
$result = $stmt->fetch(PDO::FETCH_BOUND);
echo $field;    // expect a number string with 3 decimal places

unset($stmt);
unset($conn);
?>
```

## <a name="example---override-connection-attributes"></a>例 - 接続属性のオーバーライド
次の例では、接続属性をオーバーライドする方法を示します。

```php
<?php
$database = 'myDatabase';
$server = 'myServer';
$username = 'myuser';
$password = 'mypassword'

$conn = new PDO("sqlsrv:server=$server; Database = $database", $username, $password);
$conn->setAttribute(PDO::SQLSRV_ATTR_FORMAT_DECIMALS, true);
$conn->setAttribute(PDO::SQLSRV_ATTR_DECIMAL_PLACES, 2);

$query = 'SELECT smallmoney1 FROM testTable1';
$options = array(PDO::SQLSRV_ATTR_FORMAT_DECIMALS => false);
$stmt = $conn->prepare($query, $options);
$stmt->execute();

$stmt->bindColumn('smallmoney1', $field);
$result = $stmt->fetch(PDO::FETCH_BOUND);  
echo $field;   // expect a number string showing the original scale -- 4 decimal places

unset($stmt);
unset($conn);
?>
```

## <a name="see-also"></a>参照
[10 進数文字列と金額の書式設定 (SQLSRV ドライバー)](../../connect/php/formatting-decimals-sqlsrv-driver.md)

[データの取得](../../connect/php/retrieving-data.md)
