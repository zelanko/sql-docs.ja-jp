---
title: Pdo::quote |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab9ddc48-42f8-4edf-aa8b-b0fc66706161
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f01bccbf722566a35116c1baa21629b84c809883
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="pdoquote"></a>PDO::quote
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

基になる SQL Server データベースでの必要に応じて、入力文字列を引用符で囲むことにより、クエリで使用できるように文字列を処理します。 PDO::quote は、SQL Server に適した引用符スタイルを使用して、入力文字列内の特殊文字をエスケープします。  
  
## <a name="syntax"></a>構文  
  
```  
  
string PDO::quote( $string[, $parameter_type ] )  
```  
  
#### <a name="parameters"></a>パラメーター  
$*string*: 引用符で囲む文字列。  
  
$*parameter_type*: データ型を示す省略可能な (整数) シンボル。  既定は PDO::PARAM_STR です。  
  
## <a name="return-value"></a>戻り値  
SQL ステートメントに渡すことができる引用符で囲まれた文字列、または失敗した場合は false。  
  
## <a name="remarks"></a>解説  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
  
```  
<?php  
$database = "test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$param = 'a \' g';  
$param2 = $conn->quote( $param );  
  
$query = "INSERT INTO Table1 VALUES( ?, '1' )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param));  
  
$query = "INSERT INTO Table1 VALUES( ?, ? )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param, $param2));  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
