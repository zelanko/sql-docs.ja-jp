---
title: 実行関数の比較 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- executing queries
ms.assetid: 130fc0fd-87dd-46b2-918f-de9dc572c769
caps.latest.revision: ''
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a906ec1a197cb6ede1570c9202cc955f8432ff79
ms.sourcegitcommit: 2e130e9f3ce8a7ffe373d7fba8b09e937c216386
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/28/2018
---
# <a name="comparing-execution-functions"></a>実行関数の比較
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] は、関数を実行するためのいくつかのオプションを提供します。  

## <a name="sqlsrv-execution-functions"></a>SQLSRV 実行関数  
SQLSRV ドライバーを使用している場合、 [sqlsrv_query](../../connect/php/sqlsrv-query.md) を使用して、1 つのクエリを実行し、 [sqlsrv_execute](../../connect/php/sqlsrv-prepare.md) で [sqlsrv_prepare](../../connect/php/sqlsrv-execute.md) を使用して、準備されたステートメントを実行のたびに異なるパラメーター値で複数回実行します。  

## <a name="pdosqlsrv-execution-functions"></a>PDO_SQLSRV 実行関数 
PDO_SQLSRV ドライバーを使用している場合は、次のいずれかでクエリを実行できます。  
  
-   [PDO::exec](../../connect/php/pdo-exec.md)  
  
-   [PDO::query](../../connect/php/pdo-query.md)  
  
-   「[PDO::prepare](../../connect/php/pdo-prepare.md) 」および「 [PDOStatement::execute](../../connect/php/pdostatement-execute.md)」  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)

[PDO_SQLSRV ドライバー リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)

[For PHP for SQL Server の Microsoft drivers ガイドのプログラミング](../../connect/php/programming-guide-for-php-sql-driver.md)
  
