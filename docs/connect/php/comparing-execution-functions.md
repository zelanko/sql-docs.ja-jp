---
title: "実行関数の比較 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- executing queries
ms.assetid: 130fc0fd-87dd-46b2-918f-de9dc572c769
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e74c7433ab2e3a831d6aa800a2a1a9abbbda5863
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="comparing-execution-functions"></a>実行関数の比較
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] は、関数を実行するためのいくつかのオプションを提供します。  
  
SQLSRV ドライバーを使用している場合、 [sqlsrv_query](../../connect/php/sqlsrv-query.md) を使用して、1 つのクエリを実行し、 [sqlsrv_execute](../../connect/php/sqlsrv-prepare.md) で [sqlsrv_prepare](../../connect/php/sqlsrv-execute.md) を使用して、準備されたステートメントを実行のたびに異なるパラメーター値で複数回実行します。  
  
PDO_SQLSRV ドライバーを使用している場合は、次のいずれかでクエリを実行できます。  
  
-   [PDO::exec](../../connect/php/pdo-exec.md)  
  
-   [PDO::query](../../connect/php/pdo-query.md)  
  
-   「[PDO::prepare](../../connect/php/pdo-prepare.md) 」および「 [PDOStatement::execute](../../connect/php/pdostatement-execute.md)」  
  
## <a name="see-also"></a>参照  
[SQLSRV ドライバー API リファレンス](../../connect/php/sqlsrv-driver-api-reference.md)  
[PDO_SQLSRV ドライバー リファレンス](../../connect/php/pdo-sqlsrv-driver-reference.md)  
[プログラミング ガイド](../../connect/php/programming-guide-for-php-sql-driver.md)
  

