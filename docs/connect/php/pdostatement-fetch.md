---
title: Pdostatement::fetch |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4368e362-5bda-4da1-8462-33714683c39f
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 499175b3e75c27b82df93ef84f8b17a049265356
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35308421"
---
# <a name="pdostatementfetch"></a>PDOStatement::fetch
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

結果セットから行を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
mixed PDOStatement::fetch ([ $fetch_style[, $cursor_orientation[, $cursor_offset]]] );  
```  
  
#### <a name="parameters"></a>パラメーター  
$*fetch_style*: 行データの形式を指定する省略可能な (整数) シンボル。 $ を使用できる値の一覧については、「解説」セクションを参照してください*fetch_style*です。 既定値は PDO::FETCH_BOTH です。 $*fetch_style*のフェッチで、メソッドはオーバーライド $*fetch_style* pdo::query メソッドで指定します。  
  
$*cursor_orientation*: 準備のステートメントを指定すると、取得する行を示す省略可能な (整数) シンボル`PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL`です。 $ を使用できる値の一覧については、「解説」セクションを参照してください*cursor_orientation*です。 スクロール可能なカーソルを使用する例については、「 [PDO::prepare](../../connect/php/pdo-prepare.md) 」を参照してください。  
  
$*cursor_offset*: 場合にフェッチする行を指定する省略可能な (整数) シンボル $*cursor_orientation* :fetch_ori_abs または pdo::fetch_ori_rel および pdo::attr_cursor が pdo::cursor_scroll です。  
  
## <a name="return-value"></a>戻り値  
行を返す複合値または false です。  
  
## <a name="remarks"></a>コメント  
フェッチが呼び出されると、カーソルは自動的に前進します。 次の表には、可能な $ の一覧が含まれています。*fetch_style*値。  
  
|$*fetch_style*|説明|  
|-------------------|---------------|  
|PDO::FETCH_ASSOC|列名でインデックス付けされた配列を指定します。|  
|PDO::FETCH_BOTH|列名でインデックス付けされた 0 から始まる配列を指定します。 既定値です。|  
|PDO::FETCH_BOUND|True を返し、 [PDOStatement::bindColumn](../../connect/php/pdostatement-bindcolumn.md)で指定された値を割り当てます。|  
|PDO::FETCH_CLASS|インスタンスを作成し、列を名前付きプロパティにマップします。<br /><br />フェッチを呼び出す前に、 [PDOStatement::setFetchMode](../../connect/php/pdostatement-setfetchmode.md) を呼び出します。|  
|PDO::FETCH_INTO|要求されたクラスのインスタンスを更新します。<br /><br />フェッチを呼び出す前に、 [PDOStatement::setFetchMode](../../connect/php/pdostatement-setfetchmode.md) を呼び出します。|  
|PDO::FETCH_LAZY|アクセス時に変数名を作成し、名前のないオブジェクトを作成します。|  
|PDO::FETCH_NUM|列の順が 0 から開始するインデックス付きの配列を指定します。|  
|PDO::FETCH_OBJ|列名にマップされるプロパティ名を持つ名前のないオブジェクトを指定します。|  
  
カーソルが結果セットの最後にあり (最後の行が取得され、カーソルが結果セットの境界範囲を超えたところにあります)、カーソルが前進のみの場合 (PDO::ATTR_CURSOR = PDO::CURSOR_FWDONLY)、それ以降のフェッチ呼び出しは失敗します。  
  
カーソルがスクロール可能な場合 (PDO::ATTR_CURSOR = PDO::CURSOR_SCROLL)、フェッチは結果セットの境界内にカーソルを移動します。 次の表には、可能な $ の一覧が含まれています。*cursor_orientation*値。  
  
|$*cursor_orientation*|説明|  
|--------------------------|---------------|  
|PDO::FETCH_ORI_NEXT|次の行を取得します。 既定値です。|  
|PDO::FETCH_ORI_PRIOR|前の行を取得します。|  
|PDO::FETCH_ORI_FIRST|1 番目の行を取得します。|  
|PDO::FETCH_ORI_LAST|最後の行を取得します。|  
|:Fetch_ori_abs、 *num*|$ で要求された行を取得する*cursor_offset*行番号。|  
|Pdo::fetch_ori_rel、 *num*|$ で要求された行を取得する*cursor_offset*現在位置からの相対位置でします。|  
  
$ 値が指定されている場合*cursor_offset*または $*cursor_orientation*結果セットの境界外に位置、フェッチは失敗します。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
  
```  
<?php  
   $server = "(local)";  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
   print( "\n---------- PDO::FETCH_CLASS -------------\n" );  
   $stmt = $conn->query( "select * from HumanResources.Department order by GroupName" );  
  
   class cc {  
      function __construct( $arg ) {  
         echo "$arg";  
      }  
  
      function __toString() {  
         return $this->DepartmentID . "; " . $this->Name . "; " . $this->GroupName;  
      }  
   }  
  
   $stmt->setFetchMode(PDO::FETCH_CLASS, 'cc', array( "arg1 " ));  
   while ( $row = $stmt->fetch(PDO::FETCH_CLASS)) {   
      print($row . "\n");   
   }  
  
   print( "\n---------- PDO::FETCH_INTO -------------\n" );  
   $stmt = $conn->query( "select * from HumanResources.Department order by GroupName" );  
   $c_obj = new cc( '' );  
  
   $stmt->setFetchMode(PDO::FETCH_INTO, $c_obj);  
   while ( $row = $stmt->fetch(PDO::FETCH_INTO)) {   
      echo "$c_obj\n";  
   }  
  
   print( "\n---------- PDO::FETCH_ASSOC -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_ASSOC );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_NUM -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_NUM );  
   print_r ($result );  
  
   print( "\n---------- PDO::FETCH_BOTH -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_BOTH );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_LAZY -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_LAZY );  
   print_r( $result );  
  
   print( "\n---------- PDO::FETCH_OBJ -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $result = $stmt->fetch( PDO::FETCH_OBJ );  
   print $result->Name;  
   print( "\n \n" );  
  
   print( "\n---------- PDO::FETCH_BOUND -------------\n" );  
   $stmt = $conn->query( "select * from Person.ContactType where ContactTypeID < 5 " );  
   $stmt->bindColumn('Name', $name);  
   $result = $stmt->fetch( PDO::FETCH_BOUND );  
   print $name;  
   print( "\n \n" );  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)

[PDO](http://php.net/manual/book.pdo.php)  
  
