---
title: カーソルの種類 (PDO_SQLSRV ドライバー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 49ea6a6e-78d4-40f8-85eb-180b527f0537
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72cf83b4c4903c7df0b6a857746937e848fccf80
ms.sourcegitcommit: f16003fd1ca28b5e06d5700e730f681720006816
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2018
ms.locfileid: "35306991"
---
# <a name="cursor-types-pdosqlsrv-driver"></a>カーソルの種類 (PDO_SQLSRV ドライバー)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO_SQLSRV ドライバーでは、複数のカーソルのいずれかのスクロール可能な結果セットを作成できます。  
  
PDO_SQLSRV ドライバーを使用してカーソルを指定する方法、およびコード サンプルを参照して[pdo::prepare](../../connect/php/pdo-prepare.md)です。  
  
## <a name="pdosqlsrv-and-server-side-cursors"></a>PDO_SQLSRV とサーバー側カーソル  
バージョン 3.0 の前に、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]、PDO_SQLSRV ドライバーを使用すると、結果セットには、サーバー側順方向専用カーソルまたは静的カーソルを作成します。 バージョン 3.0 以降で、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]キーセットと動的カーソルも使用できます。  
  
サーバー側カーソルの種類を指定するには、pdo::prepare または pdostatement::setattribute を使用して、カーソルの種類を選択します。  
  
-   PDO::ATTR_CURSOR = &GT; PDO::CURSOR_FWDONLY  
  
-   PDO::ATTR_CURSOR = &GT; PDO::CURSOR_SCROLL  
  
Pdo::attr_cursor を指定することで、キーセット カーソルまたは動的カーソルを要求することができます = > pdo::cursor_scroll および pdo::sqlsrv_attr_cursor_scroll_type をしに渡したり、適切な値です。 Pdo::sqlsrv_attr_cursor_scroll_type に渡すことが可能な値は次のとおりです。  
  
-   PDO::SQLSRV_CURSOR_BUFFERED  
  
-   PDO::SQLSRV_CURSOR_DYNAMIC  
  
-   PDO::SQLSRV_CURSOR_KEYSET_DRIVEN  
  
-   PDO::SQLSRV_CURSOR_STATIC  
  
## <a name="pdosqlsrv-and-client-side-cursors"></a>PDO_SQLSRV とクライアント側カーソル  
クライアント側のカーソルは、version 3.0 で追加された、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]結果セット全体をメモリにキャッシュすることができます。 1 つの利点は、クエリが実行された後に行の数が使用できることです。  
  
クライアント側のカーソルは、小規模から中規模の結果セットに使用する必要があります。 大きな結果セットには、サーバー側カーソルを使用する必要があります。  
  
クエリは、バッファーが結果全体をクライアント側カーソルを使用するときに設定を保持するのに十分でない場合は false を返します。 PHP メモリの上限に達するまでバッファー サイズを増やすことができます。  
  
結果の PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE 属性を持つセットを保持するバッファーのサイズを構成する[pdo::setattribute](../../connect/php/pdo-setattribute.md)または[pdostatement::setattribute](../../connect/php/pdostatement-setattribute.md)です。 Pdo_sqlsrv.client_buffer_max_kb_size で php.ini ファイルで、バッファーの最大サイズを設定することもできます (たとえば、pdo_sqlsrv.client_buffer_max_kb_size = 1024)。  
  
Pdo::prepare または pdostatement::setattribute を使用してクライアント側カーソルを目的し、選択、pdo::attr_cursor ことを指定する = > pdo::cursor_scroll カーソルの種類。  Pdo::sqlsrv_attr_cursor_scroll_type を指定する = > PDO::SQLSRV_CURSOR_BUFFERED です。  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$query = "select * from Person.ContactType";  
$stmt = $conn->prepare( $query, array(PDO::ATTR_CURSOR => PDO::CURSOR_SCROLL, PDO::SQLSRV_ATTR_CURSOR_SCROLL_TYPE => PDO::SQLSRV_CURSOR_BUFFERED));  
$stmt->execute();  
print $stmt->rowCount();  
  
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
[カーソルの種類を指定し、行を選択する](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)  
  
