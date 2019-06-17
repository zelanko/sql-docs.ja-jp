---
title: sqlsrv_server_info |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_server_info
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_server_info
- sqlsrv_server_info
ms.assetid: ef6fe2b7-d267-4379-b948-5626c4684367
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 797ddae6180e3641e94be582dab84587298b7876
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66782736"
---
# <a name="sqlsrvserverinfo"></a>sqlsrv_server_info
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

サーバーに関する情報を返します。 この関数を呼び出す前に、接続を確立する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
sqlsrv_server_info( resource $conn)  
```  
  
#### <a name="parameters"></a>パラメーター  
*$conn*: クライアントとサーバーを接続する接続リソース。  
  
## <a name="return-value"></a>戻り値  
次のキーを含む連想配列。  
  
|キー|[説明]|  
|-------|---------------|  
|CurrentDatabase|現在対象となっているデータベース。|  
|SQLServerVersion|SQL Server のバージョン。|  
|SQLServerName|サーバーの名前。|  
  
## <a name="example"></a>例  
次の例では、コマンドラインからこの例を実行すると、サーバー情報がコンソールに書き込まれます。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication. */  
$serverName = "(local)";  
$conn = sqlsrv_connect( $serverName);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
$server_info = sqlsrv_server_info( $conn);  
if( $server_info )  
{  
      foreach( $server_info as $key => $value)  
      {  
             echo $key.": ".$value."\n";  
      }  
}  
else  
{  
      echo "Error in retrieving server info.\n";  
      die( print_r( sqlsrv_errors(), true));  
}  
  
/* Free connection resources. */  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  

[ドキュメントのコード例について](../../connect/php/about-code-examples-in-the-documentation.md)  
  
