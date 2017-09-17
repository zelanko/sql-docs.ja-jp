---
title: ": _ _Construct |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ee53aff-6fe4-44cd-a15b-51770c98c712
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 71404af3dfbcc0599d53bdb719f4150c77cac332
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="pdoconstruct"></a>PDO::__construct
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベースへの接続を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
PDO::__construct($dsn [,$username [,$password [,$driver_options ]]] )  
```  
  
#### <a name="parameters"></a>パラメーター  
*$dsn*: プレフィックス名を表す文字列 (常に`sqlsrv`)、コロン、および、Server キーワード。 たとえば、 `"sqlsrv:server=(local)"`があります。 オプションで他の接続キーワードを指定することも可能です。 Server キーワードおよびその他の接続キーワードの詳細については、「 [Connection Options](../../connect/php/connection-options.md) 」を参照してください。 *$dsn* は全体が引用符で囲まれているので、各接続キーワードは個別に囲まないようにする必要があります。  
  
*$username*: 省略可です。 ユーザー名を含む文字列です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 認証を使用して接続する場合、ログイン ID を指定します。 Windows 認証を使用して接続するには、 `""`を指定します。  
  
*$password*: 省略可です。 ユーザー パスワードを含む文字列です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 認証を使用して接続する場合、パスワードを指定します。 Windows 認証を使用して接続するには、 `""`を指定します。  
  
*$ を指定する*: 省略可能です。 PDO ドライバー マネージャーの属性を指定できますと[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]固有のドライバー属性--pdo::sqlsrv_attr_encoding、pdo::sqlsrv_attr_direct_query です。 無効な属性では、例外は生成されません。 無効な属性を [PDO::setAttribute](../../connect/php/pdo-setattribute.md)と共に指定すると、例外が生成されます。  
  
## <a name="return-value"></a>戻り値  
PDO オブジェクトを返します。 失敗した場合は、PDOException オブジェクトを返します。  
  
## <a name="exceptions"></a>例外  
PDOException  
  
## <a name="remarks"></a>解説  
インスタンスを null に設定して、接続オブジェクトを閉じることができます。  
  
接続後、PDO::errorCode には 00000 の代わりに 01000 が表示されます。  
  
何らかの理由で PDO::__construct が失敗する場合、PDO::ATTR_ERRMODE が PDO::ERRMODE_SILENT に設定されていても例外がスローされます。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
この例では、Windows 認証を使用してサーバーに接続し、データベースを指定する方法を示します。  
  
```  
<?php  
   $c = new PDO( "sqlsrv:Server=(local) ; Database = AdventureWorks ", "", "", array(PDO::SQLSRV_ATTR_DIRECT_QUERY => true));   
  
   $query = 'SELECT * FROM Person.ContactType';   
   $stmt = $c->query( $query );   
   while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ) {   
      print_r( $row );   
   }  
   $c = null;   
?>  
```  
  
## <a name="example"></a>例  
この例では、サーバーへの接続方法を示します。後でデータベースを指定します。  
  
```  
<?php  
   $c = new PDO( "sqlsrv:server=(local)");  
  
   $c->exec( "USE AdventureWorks");  
   $query = 'SELECT * FROM Person.ContactType';  
   $stmt = $c->query( $query );  
   while ( $row = $stmt->fetch( PDO::FETCH_ASSOC ) ){  
      print_r( $row );  
   }  
   $c = null;  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)  
[PDO](http://go.microsoft.com/fwlink/?LinkID=187441)  
  

