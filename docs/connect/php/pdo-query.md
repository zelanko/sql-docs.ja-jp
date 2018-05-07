---
title: Pdo::query |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: f6f5e6d4-8ca9-4f06-89ed-de65ad3952a2
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fb23a63d77461cb13784c515bd0638af277e63b6
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="pdoquery"></a>PDO::query
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

SQL クエリを実行し、PDOStatement オブジェクトとして結果セットを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PDOStatement PDO::query ($statement[, $fetch_style);  
```  
  
#### <a name="parameters"></a>パラメーター  
*$statement*: 実行する SQL ステートメント。  
  
*$fetch_style*: クエリを実行する方法については省略可能です。 詳細については、「解説」を参照してください。 $*fetch_style* pdo::query の $ でオーバーライドできる*fetch_style* pdo::fetch にします。  
  
## <a name="return-value"></a>戻り値  
呼び出しに成功すると、PDO::query は PDOStatement オブジェクトを返します。 呼び出しに失敗すると、PDO::ATTR_ERRMODE の設定に応じて PDO::query は PDOException オブジェクトをスローするか、false を返します。  
  
## <a name="exceptions"></a>例外  
PDOException。  
  
## <a name="remarks"></a>解説  
Pdo::query で実行されるクエリが準備されたいずれかのステートメントを実行できる pdo::sqlsrv_attr_direct_query の設定に応じて、直接またはします。 詳細については、「 [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)」 (PDO_SQLSRV ドライバーでの直接ステートメント実行と準備されたステートメントの実行) を参照してください。  
  
Pdo::sqlsrv_attr_query_timeout; pdo::exec の動作にも影響します。詳細については、次を参照してください。 [pdo::setattribute](../../connect/php/pdo-setattribute.md)です。  
  
次のオプションを指定するには $*fetch_style*です。  
  
|style|Description|  
|---------|---------------|  
|Pdo::fetch_column、 *num*|指定された列内のデータを照会します。 テーブルの最初の列は 0 です。|  
|Pdo::fetch_class、'*classname*'、配列 ( *arglist* )|クラスのインスタンスを作成し、列名をクラスのプロパティに割り当てます。 クラス コンストラクターに 1 つ以上のパラメーターを指定できる場合、 *arglist*を渡すこともできます。|  
|Pdo::fetch_class、'*classname*'|既存のクラスのプロパティに列名を割り当てます。|  
  
PDOStatement::closeCursor を呼び出して、PDOStatement オブジェクトに関連付けられたデータベース リソースを解放してから、もう一度 PDO::query を呼び出します。  
  
PDOStatement オブジェクトを閉じるには、オブジェクトを null に設定します。  
  
結果セット内のすべてのデータがフェッチされていない場合でも、次の PDO::query の呼び出しは失敗しません。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
この例では、いくつかのクエリを使用します。  
  
```  
<?php  
$database = "AdventureWorks";  
$conn = new PDO( "sqlsrv:server=(local) ; Database = $database", "", "");  
$conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
$conn->setAttribute( PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 1 );  
  
$query = 'select * from Person.ContactType';  
  
// simple query  
$stmt = $conn->query( $query );  
while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
   print_r( $row['Name'] ."\n" );  
}  
  
echo "\n........ query for a column ............\n";  
  
// query for one column  
$stmt = $conn->query( $query, PDO::FETCH_COLUMN, 1 );  
while ( $row = $stmt->fetch() ){  
   echo "$row\n";  
}  
  
echo "\n........ query with a new class ............\n";  
$query = 'select * from HumanResources.Department order by GroupName';  
// query with a class  
class cc {  
   function __construct( $arg ) {  
      echo "$arg";  
   }  
  
   function __toString() {  
      return $this->DepartmentID . "; " . $this->Name . "; " . $this->GroupName;  
   }  
}  
  
$stmt = $conn->query( $query, PDO::FETCH_CLASS, 'cc', array( "arg1 " ));  
  
while ( $row = $stmt->fetch() ){  
   echo "$row\n";  
}  
  
echo "\n........ query into an existing class ............\n";  
$c_obj = new cc( '' );  
$stmt = $conn->query( $query, PDO::FETCH_INTO, $c_obj );  
while ( $stmt->fetch() ){  
   echo "$c_obj\n";  
}  
  
$stmt = null;  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
