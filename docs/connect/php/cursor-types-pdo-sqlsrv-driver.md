---
title: カーソルの種類 (PDO_SQLSRV ドライバー) |Microsoft Docs
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
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38062359"
---
# <a name="cursor-types-pdosqlsrv-driver"></a>カーソルの種類 (PDO_SQLSRV ドライバー)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO_SQLSRV ドライバーでは、複数のカーソルのいずれかのスクロール可能な結果セットを作成できます。  
  
PDO_SQLSRV ドライバーを使用してカーソルを指定する方法について、およびコード サンプルを参照してください。 [pdo::prepare](../../connect/php/pdo-prepare.md)します。  
  
## <a name="pdosqlsrv-and-server-side-cursors"></a>PDO_SQLSRV とサーバー側カーソル  
バージョン 3.0 より前、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]、PDO_SQLSRV ドライバーを使用すると、サーバー側の前方参照専用、または静的カーソルを含む結果セットを作成します。 以降のバージョン 3.0 では、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]、キーセット カーソルと動的カーソルも利用できます。  
  
サーバー側カーソルの種類を指定するには、pdo::prepare または pdostatement::setattribute を使用して、カーソルの種類を選択します。  
  
-   PDO::ATTR_CURSOR = &GT; PDO::CURSOR_FWDONLY  
  
-   PDO::ATTR_CURSOR = &GT; PDO::CURSOR_SCROLL  
  
Pdo::attr_cursor を指定することで、キーセット カーソルまたは動的カーソルを要求することができます = > pdo::cursor_scroll および pdo::sqlsrv_attr_cursor_scroll_type をパス、適切な値。 Pdo::sqlsrv_attr_cursor_scroll_type を渡すことができる使用可能な値は次のとおりです。  
  
-   PDO::SQLSRV_CURSOR_BUFFERED  
  
-   PDO::SQLSRV_CURSOR_DYNAMIC  
  
-   PDO::SQLSRV_CURSOR_KEYSET_DRIVEN  
  
-   PDO::SQLSRV_CURSOR_STATIC  
  
## <a name="pdosqlsrv-and-client-side-cursors"></a>PDO_SQLSRV とクライアント側カーソル  
クライアント側のカーソルは、のバージョン 3.0 で追加された、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]メモリ セット全体の結果をキャッシュすることができます。 利点の 1 つは、クエリの実行後に行の数が使用可能なことです。  
  
クライアント側のカーソルは、小規模から中規模の結果セットに対して使用する必要があります。 大きな結果セットには、サーバー側カーソルを使用する必要があります。  
  
クエリは、バッファーが結果をクライアント側のカーソルを使用する場合のセット全体を保持するために十分な大きさでない場合は false を返します。 PHP メモリの上限に達するまでバッファー サイズを増やすことができます。  
  
PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE 属性を使用して結果セットを保持するバッファーのサイズを構成する[pdo::setattribute](../../connect/php/pdo-setattribute.md)または[pdostatement::setattribute](../../connect/php/pdostatement-setattribute.md)します。 Pdo_sqlsrv.client_buffer_max_kb_size で php.ini ファイルの最大バッファー サイズを設定することもできます (たとえば、pdo_sqlsrv.client_buffer_max_kb_size = 1024)。  
  
Pdo::prepare または pdostatement::setattribute を使用してクライアント側カーソルを目的し、pdo::attr_cursor を選択することを示す = > pdo::cursor_scroll カーソルの種類。  Pdo::sqlsrv_attr_cursor_scroll_type を指定します = > PDO::SQLSRV_CURSOR_BUFFERED します。  
  
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
  
