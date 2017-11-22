---
title: "方法: 指定されたポートで接続 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: php
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: connecting to the server, specifying a port
ms.assetid: 65a154d1-375c-439b-a653-7815c9d70ff3
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c8f5fcabd257f602c9ceba97806b031e95142a76
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-connect-on-a-specified-port"></a>方法: 指定されたポートで接続する
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]を使用して、指定されたポートで SQL Server に接続する方法について説明します。  
  
### <a name="to-connect-on-a-specified-port"></a>指定されたポートで接続するには  
  
1.  サーバーが接続を受け入れるようにポートが構成されていることを確認します。 指定されたポートで接続を許可するサーバーを構成する方法の詳細については、次を参照してください。[する方法: 特定の TCP ポート (SQL Server 構成マネージャー) でリッスンするようにサーバーを構成する](http://go.microsoft.com/fwlink/?LinkId=121865)です。  
  
2.  必要なポートを追加、 *$serverName*のパラメーター、 [sqlsrv_connect](../../connect/php/sqlsrv-connect.md)関数。 サーバー名とポートをコンマで区切ります。 たとえば、次のコード行は SQLSRV ドライバーを使用して、ポート 1521 で *myServer* という名前のサーバーに接続する方法を示しています。  
  
    ```  
    $serverName = "myServer, 1521";  
    sqlsrv_connect( $serverName );  
    ```  
  
    次のコード行では、PDO_SQLSRV ドライバーを使用して、という名前のサーバーに接続する方法を示します*myServer*ポート 1521 で。  
  
    ```  
    $serverName = "(local), 1521";  
    $database = "AdventureWorks";  
    $conn = new PDO( "sqlsrv:server=$serverName;Database=$database", "", "");  
    ```  
  
## <a name="see-also"></a>参照  
[サーバーへの接続](../../connect/php/connecting-to-the-server.md)  
[プログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)
[作業の開始](../../connect/php/getting-started-with-the-php-sql-driver.md) 
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[PDO_SQLSRV ドライバー リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)  
  
