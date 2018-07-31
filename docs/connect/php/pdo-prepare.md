---
title: Pdo::prepare |Microsoft Docs
ms.custom: ''
ms.date: 07/10/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: a8b16fdc-c748-49be-acf2-a6ac7432d16b
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 717657cabc469488565985e3e37d111bb9d592b8
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37979767"
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
|PDO::ATTR_EMULATE_PREPARES|Pdo::attr_emulate_prepares が on の場合、準備されたステートメント内のプレース ホルダーは、バインドされたパラメーターに置き換えられます。 なしのプレース ホルダーを含む完全な SQL ステートメントが実行時のデータベースに送信されます。 <br /><br />Pdo::attr_emulate_prepares は、SQL Server でいくつかの制限のバイパスを使用できます。 たとえば、SQL Server は、いくつかの TRANSACT-SQL の句で名前付きまたは位置指定パラメーターをできません。 また、SQL Server では、バインド 2100 パラメーターの制限があります。<br /><br />Pdo::attr_emulate_prepares 属性を true に設定できます。 例 :<br /><br />`PDO::ATTR_EMULATE_PREPARES => true`<br /><br />既定では、この属性は false に設定されます。<br /><br />**注:** `PDO::ATTR_EMULATE_PREPARES => true`を使用する場合、パラメーター化されたクエリのセキュリティは適用されません。 アプリケーションでは、パラメーターにバインドされたデータに、悪意のある Transact-SQL コードが含まれていないことを確認する必要があります。<br /><br />**制限事項:**: パラメーターでは、データベースのパラメーター化クエリ機能を使用してバインドされていない、ため input_output と出力パラメーターがサポートされません。|  
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
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
