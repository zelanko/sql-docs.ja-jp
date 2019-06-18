---
title: 10 進数文字列と金額の書式設定 (SQLSRV ドライバー) | Microsoft Docs
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
ms.openlocfilehash: 76b6d27acedcfe2ec462a764559237a1a2218f78
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "62669604"
---
# <a name="formatting-decimal-strings-and-money-values-sqlsrv-driver"></a>10 進数文字列と金額の書式設定 (SQLSRV ドライバー)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

精度を保持するために[decimal 型または numeric 型](https://docs.microsoft.com/sql/t-sql/data-types/decimal-and-numeric-transact-sql)が常に、正確な精度と小数点を含む文字列としてフェッチします。 任意の値が 1 未満の場合は、先行ゼロがありません。 固定桁数が 4 に等しい 10 進数のフィールドは money と smallmoney フィールドと同じです。

## <a name="add-leading-zeroes-if-missing"></a>不足している場合は、先頭のゼロを追加します。
バージョン 5.6.0、オプションで始まる`FormatDecimals`sqlsrv 接続とステートメントのレベルに追加できるユーザーは、10 進数値文字列の形式を指定します。 このオプションは、ブール値を (true または false) が必要ですが、フェッチされた結果の値を 10 進数または数値の書式設定にのみ影響します。 つまり、`FormatDecimals`オプションは挿入や更新などその他の操作に影響を与えません。

既定では、`FormatDecimals` は **false** です。 場合は true、10 進数値文字列に先頭のゼロに設定は、1 未満の 10 進値に対する追加されます。

## <a name="configure-number-of-decimal-places"></a>小数点以下桁数を構成します。
`FormatDecimals`有効で、別のオプション、 `DecimalPlaces`money と smallmoney データを表示するときに、小数点以下桁数を構成することができます。 範囲の整数値を受け取って [0, 4] に表示するときに発生する可能性があります丸め処理を行うとします。 ただし、基になるの money 型データは同じです。

両方のオプションは、接続またはステートメント レベルに設定することができ、設定は常にステートメントが対応する接続設定を上書きします。 なお、`DecimalPlaces`オプション**のみ**money データと`FormatDecimals`に設定する必要がありますの場合は true。`DecimalPlaces`を有効にします。 それ以外の場合、書式設定がオフに関係なく`DecimalPlaces`設定します。

> [!NOTE]
> 設定するため、money または smallmoney フィールドがあるスケール 4 は、`DecimalPlaces`を負の数値または任意の値は無視されます 4 より大きい値です。 すべての計算を入力として書式設定されたコスト データを使用することは推奨されません。

## <a name="example---a-simple-fetch"></a>例 - 単純なフェッチ
次の例では、単純なフェッチの新しいオプションを使用する方法を示します。

```php
<?php
$username = 'myusername';
$password = 'mypasword';
$tableName = 'mytable';

$connectionInfo = array("UID" => $username, "PWD" => $password, "Database" => "myDB", "FormatDecimals" => true);  
$server = "myServer";  // IP address also works
$conn = sqlsrv_connect( $server, $connectionInfo);  

$numDigits = 2;
$query = "SELECT money1 FROM $tableName";
$options = array("DecimalPlaces" => $numDigits);
$stmt = sqlsrv_prepare($conn, $query, array(), $options);
sqlsrv_execute($stmt);

if (sqlsrv_fetch($stmt)) {
    $field = sqlsrv_get_field($stmt, 0);  
    echo $field;   // expect a numeric value string with 2 decimal places
}

sqlsrv_free_stmt($stmt);
sqlsrv_close($conn);
?>
```

## <a name="example---format-the-output-parameter"></a>出力パラメーターの形式の使用例
10 進数または数値フィールドとして返された場合、[出力パラメーター](../../connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)、返される値は標準の varchar 文字列として見なされます。 ただし場合 SQLSRV_SQLTYPE_DECIMAL または SQLSRV_SQLTYPE_NUMERIC のいずれかを指定すると、設定できます`FormatDecimals`に先頭のゼロ数値の文字列値の不足しているがないことを確認する場合は true。 詳細については、「[方法: SQLSRV ドライバーを使用して出力パラメーターを取得する](../..//connect/php/how-to-retrieve-output-parameters-using-the-sqlsrv-driver.md)」をご覧ください。

次の例では、decimal(8,4) 値を返すストアド プロシージャの出力パラメーター書式を設定する方法を示します。

```php
$outString = '';
$outSql = '{CALL myStoredProc(?)}';
$stmt = sqlsrv_prepare($conn, 
                       $outSql, 
                       array(array(&$outString, SQLSRV_PARAM_OUT, null, SQLSRV_SQLTYPE_DECIMAL(8, 4))),
                       array('FormatDecimals' => true));

if (sqlsrv_execute($stmt)) {
    echo $outString;  // expect a numeric value string with no missing leading zero
}
```

## <a name="see-also"></a>参照
[10 進数文字列と金額の書式設定 (PDO_SQLSRV ドライバー)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md)

[データの取得](../../connect/php/retrieving-data.md)
