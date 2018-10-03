---
title: Pdo::prepare |Microsoft Docs
ms.custom: ''
ms.date: 07/31/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: a8b16fdc-c748-49be-acf2-a6ac7432d16b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ca5e1a4d0dd3f76b3fabefa6549eb644a894845a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47745140"
---
# <a name="pdoprepare"></a>PDO::prepare
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

実行するステートメントを準備します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PDOStatement PDO::prepare ( $statement [, array(key_pair)] )  
```  
  
#### <a name="parameters"></a>パラメーター  
$*statement*: SQL ステートメントを含む文字列。  
  
*key_pair*: 属性の名前と値を含む配列。 詳細については、「解説」を参照してください。  
  
## <a name="return-value"></a>戻り値  
成功した場合は、PDOStatement オブジェクトを返します。 失敗した場合は、PDOException オブジェクトまたは PDO::ATTR_ERRMODE の値によっては false を返します。  
  
## <a name="remarks"></a>Remarks  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] では、実行されるまで準備されたステートメントを検証しません。  
  
次の表は、使用可能な *key_pair* の値を一覧しています。  
  
|Key|[説明]|  
|-------|---------------|  
|PDO::ATTR_CURSOR|カーソル動作を定義します。 既定値は、PDO::CURSOR_FWDONLY です。 PDO::CURSOR_SCROLL は、静的カーソルです。<br /><br />たとえば、 `array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY )`のようにします。<br /><br />PDO::CURSOR_SCROLL を使用する場合は、以下で説明するように、PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE を使用できます。<br /><br />PDO_SQLSRV ドライバーの結果セットとカーソルに関する詳細については、「[カーソルの種類 &#40;PDO_SQLSRV ドライバー&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)」を参照してください。|  
|PDO::ATTR_EMULATE_PREPARES|既定では、この属性が false の場合、これによって変更できます`PDO::ATTR_EMULATE_PREPARES => true`します。 参照してください[準備エミュレート](#emulate-prepare)詳細と例。|
|PDO::SQLSRV_ATTR_ENCODING|PDO::SQLSRV_ENCODING_UTF8 (既定値)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|  
|PDO::SQLSRV_ATTR_DIRECT_QUERY|True の場合、直接クエリの実行を指定します。 False は、準備されたステートメントの実行です。 PDO::SQLSRV_ATTR_DIRECT_QUERY の詳細については、「[PDO_SQLSRV ドライバーでの直接ステートメントの実行と準備されたステートメントの実行](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)」を参照してください。|  
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|詳細については、「 [PDO::setAttribute](../../connect/php/pdo-setattribute.md)」を参照してください。|  
  
PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL を使用する場合は、PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE を使用できます。 例を次に示します。  
  
```  
array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_DYNAMIC));  
```  
  
次の表では、使用可能な PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE の値を示します。  
  
|ReplTest1|[説明]|  
|---------|---------------|  
|PDO::SQLSRV_CURSOR_BUFFERED|クライアント側 (バッファー済み) の静的カーソルを作成します。 クライアント側カーソルの詳細については、「[カーソルの種類 &#40;PDO_SQLSRV ドライバー&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)」を参照してください。|  
|PDO::SQLSRV_CURSOR_DYNAMIC|サーバー側 (バッファーなし) の動的カーソルを作成します。これは、任意の順序で行にアクセスすることができ、変更内容がデータベースに反映されます。|  
|PDO::SQLSRV_CURSOR_KEYSET_DRIVEN|サーバー側のキーセット カーソルを作成します。 行がテーブルから削除される場合 (削除された行は、値なしで返されます)、キーセット カーソルは行の数を更新しません。|  
|PDO::SQLSRV_CURSOR_STATIC|サーバー側の静的カーソルを作成します。これは、任意の順序で行にアクセスできますが、変更内容はデータベースに反映されません。<br /><br />PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL implies PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_STATIC.|  
  
PDOStatement オブジェクトを閉じるには、オブジェクトを null に設定します。  
  
## <a name="example"></a>例  
この例では、パラメーター マーカーと順方向専用カーソルで PDO::prepare メソッドを使用する方法を示します。  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$col1 = 'a';  
$col2 = 'b';  
  
$query = "insert into Table1(col1, col2) values(?, ?)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( $col1, $col2 ) );  
print $stmt->rowCount();  
echo "\n";  
  
$query = "insert into Table1(col1, col2) values(:col1, :col2)";  
$stmt = $conn->prepare( $query, array( PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY, PDO::SQLSRV_ATTR_QUERY_TIMEOUT => 1  ) );  
$stmt->execute( array( ':col1' => $col1, ':col2' => $col2 ) );  
print $stmt->rowCount();  
  
$stmt = null  
?>  
```  

## <a name="example"></a>例  
この例では、クライアント側のカーソルで PDO::prepare メソッドを使用する方法を示します。 サーバー側カーソルの例については、「[カーソルの種類 &#40;PDO_SQLSRV ドライバー&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)」を参照してください。  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL));  
$stmt->execute();  
  
echo "\n";  
  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print "$row[Name]\n";  
}  
echo "\n..\n";  
  
$row = $stmt->fetch( PDO::FETCH_BOTH, PDO::FETCH_ORI_FIRST );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_ASSOC, PDO::FETCH_ORI_REL, 1 );  
print "$row[Name]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_NEXT );  
print "$row[1]\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_PRIOR );  
print "$row[1]..\n";  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_ABS, 0 );  
print_r($row);  
  
$row = $stmt->fetch( PDO::FETCH_NUM, PDO::FETCH_ORI_LAST );  
print_r($row);  
?>  
```  

<a name="emulate-prepare" />

## <a name="example"></a>例 

この例は、pdo::prepare メソッドを使用する方法を示しています。`PDO::ATTR_EMULATE_PREPARES`を true に設定します。 

```
<?php
$serverName = "yourservername";
$username = "yourusername";
$password = "yourpassword";
$database = "tempdb";
$conn = new PDO("sqlsrv:server = $serverName; Database = $database", $username, $password);

$pdo_options = array();
$pdo_options[PDO::ATTR_EMULATE_PREPARES] = true;
$pdo_options[PDO::SQLSRV_ATTR_ENCODING] = PDO::SQLSRV_ENCODING_UTF8;

$stmt = $conn->prepare("CREATE TABLE TEST([id] [int] IDENTITY(1,1) NOT NULL, 
                                          [name] nvarchar(max))", 
                                          $pdo_options);
$stmt->execute();

$prefix = '가각';
$name = '가각ácasa';
$name2 = '가각sample2';

$stmt = $conn->prepare("INSERT INTO TEST(name) VALUES(:p0)", $pdo_options);
$stmt->execute(['p0' => $name]);
unset($stmt);

$stmt = $conn->prepare("SELECT * FROM TEST WHERE NAME LIKE :p0", $pdo_options);
$stmt->execute(['p0' => "$prefix%"]);
foreach ($stmt as $row) {
    echo "\n" . 'FOUND: ' . $row['name'];
}

unset($stmt);
unset($conn);
?>
```

PDO_SQLSRV ドライバーは内部的にによってバインドされているパラメーターを使用して、すべてのプレース ホルダーを置き換えます[PDOStatement::bindParam()](../../connect/php/pdostatement-bindparam.md)します。 そのため、なしのプレース ホルダーを含む SQL クエリ文字列は、サーバーに送信されます。 この例を検討してください。

```
$statement = $PDO->prepare("INSERT into Customers (CustomerName, ContactName) VALUES (:cus_name, :con_name)");
$statement->bindParam(:cus_name, "Cardinal");
$statement->bindParam(:con_name, "Tom B. Erichsen");
$statement->execute();
```

`PDO::ATTR_EMULATE_PREPARES`データベースに送信されるデータは、false (既定のケース) に設定します。

```
"INSERT into Customers (CustomerName, ContactName) VALUES (:cus_name, :con_name)"
Information on :cus_name parameter
Information on :con_name parameter
```

サーバーは、パラメーターをバインドするため、パラメーター化クエリ機能を使用してクエリを実行します。 その一方で`PDO::ATTR_EMULATE_PREPARES`は、基本的に、サーバーに送信されるクエリを true に設定します。

```
"INSERT into Customers (CustomerName, ContactName) VALUES ('Cardinal', 'Tom B. Erichsen')"
```

設定`PDO::ATTR_EMULATE_PREPARES`に true は、SQL Server でいくつかの制限をバイパスできます。 たとえば、SQL Server は、いくつかの TRANSACT-SQL の句で名前付きまたは位置指定パラメーターをできません。 さらに、SQL Server は、バインド 2100 パラメーターに制限します。

> [!NOTE]
> エミュレートを true に設定を準備します。 パラメーター化クエリのセキュリティは無効です。 そのため、アプリケーションでは、パラメーターにバインドされたデータに、悪意のある Transact-SQL コードが含まれていないことを確認する必要があります。

### <a name="encoding"></a>[エンコード]

ユーザーの異なるエンコーディング (utf-8 またはバイナリなど) のパラメーターをバインドする場合、ユーザー明確にで PHP スクリプトのエンコードを指定する必要があります。

PDO_SQLSRV ドライバーを最初に指定されたエンコーディング チェック`PDO::bindParam()`(たとえば、 `$statement->bindParam(:cus_name, "Cardinal", PDO::PARAM_STR, 10, PDO::SQLSRV_ENCODING_UTF8)`)。 

かどうか、ドライバー チェック任意のエンコーディングを設定するかどうか`PDO::prepare()`または`PDOStatement::setAttribute()`します。 それ以外の場合、ドライバーがで指定されたエンコーディングを使用するが`PDO::__construct()`または`PDO::setAttribute()`します。

### <a name="limitations"></a>制限事項

ご覧のように、ドライバーによってバインディングが内部的に行われます。 有効なクエリは、パラメーターを指定しないで実行するために、サーバーに送信されます。 通常のケースと比較して、いくつかの制限は、パラメーター化クエリ機能が使用されていないときに発生します。

- パラメーターとしてバインドされているは機能しません`PDO::PARAM_INPUT_OUTPUT`します。
    - ユーザーが指定すると`PDO::PARAM_INPUT_OUTPUT`で`PDO::bindParam()`、PDO 例外がスローされます。
- 出力パラメーターとしてバインドされているパラメーターには機能しません。
    - 出力パラメーターの場合は、ユーザー作成準備されたステートメントのプレース ホルダーを (つまりなどのプレース ホルダーの直後後には、等号 (=) を持つ、 `SELECT ? = COUNT(*) FROM Table1`)、PDO 例外がスローされます。
    - 出力パラメーターの引数として、準備されたステートメントがプレース ホルダーを持つストアド プロシージャを呼び出すと、ドライバーは出力パラメーターを検出できないため、例外はスローされません。 ただし、ユーザーは、出力パラメーターの変数は変更されません。
- バイナリ エンコードされたパラメーターの重複のプレース ホルダーは機能しません

## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
