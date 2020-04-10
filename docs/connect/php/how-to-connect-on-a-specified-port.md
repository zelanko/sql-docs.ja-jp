---
title: 方法:指定されたポートで接続する | Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connecting to the server, specifying a port
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 44df1e9c8809fed016a5c041d34f0f46cae83654
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80916502"
---
# <a name="how-to-connect-on-a-specified-port"></a>方法:指定されたポートで接続する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]を使用して、指定されたポートで SQL Server に接続する方法について説明します。  
  
### <a name="to-connect-on-a-specified-port"></a>指定されたポートで接続するには  
  
1.  サーバーが接続を受け入れるようにポートが構成されていることを確認します。 指定されたポートで接続を受け入れるようにサーバーを構成する方法については、[特定の TCP ポートでリッスンするようにサーバーを構成する方法 (SQL Server 構成マネージャー)](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md)に関するページを参照してください。  
  
2.  目的のポートを [sqlsrv_connect](../../connect/php/sqlsrv-connect.md) 関数の *$serverName* パラメーターに追加します。 サーバー名とポートをコンマで区切ります。 たとえば、次のコード行は SQLSRV ドライバーを使用して、ポート 1521 で *myServer* という名前のサーバーに接続する方法を示しています。  
  
    ```  
    $serverName = "myServer, 1521";  
    sqlsrv_connect( $serverName );  
    ```  
  
    次のコード行は PDO_SQLSRV ドライバーを使用して、ポート 1521 で *myServer* という名前のサーバーに接続する方法を示しています。  
  
    ```  
    $serverName = "(local), 1521";  
    $database = "AdventureWorks";  
    $conn = new PDO( "sqlsrv:server=$serverName;Database=$database", "", "");  
    ```  
  
## <a name="see-also"></a>参照  
[サーバーへの接続](../../connect/php/connecting-to-the-server.md)

[SQL Server 用 Microsoft Drivers for PHP のためのプログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)

[Microsoft Drivers for PHP for SQL Server の概要](../../connect/php/getting-started-with-the-php-sql-driver.md)

[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)

[PDO_SQLSRV ドライバー リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
