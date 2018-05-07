---
title: データの取得 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.component: php
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 3414992c-61c0-4e7d-b509-72517e52c1bb
caps.latest.revision: 42
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 433635c8260ca4ae2d3a3132f093f8eb5341fad0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="retrieving-data"></a>データの取得
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックと、このセクションのトピックでは、データを取得する方法について説明します。  
  
## <a name="sqlsrv-driver"></a>SQLSRV ドライバー  
[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] の SQLSRV ドライバーは、結果セットからデータを取得するための次のオプションを提供しています。  
  
-   [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)  
  
-   [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md)  
  
-   [sqlsrv_fetch](../../connect/php/sqlsrv-fetch.md)/[sqlsrv_get_field](../../connect/php/sqlsrv-get-field.md)  
  
> [!NOTE]  
> 上記のいずれかの関数を使用する場合は、ループの終了の条件として null 比較を避けてください。 **sqlsrv** 関数はエラーの発生時に false を返すため、次のコードは [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md)でエラー発生時に無限ループになる可能性があります。  
>   
> `/*``This code could result in an infinite loop. It is recommended that`  
>   
> `you do NOT use null comparisons as the criterion for exiting loops,`  
>   
> `as is done here. */`  
>   
> `do{`  
>   
> `$result = sqlsrv_fetch_array($stmt);`  
>   
> `} while( !is_null($result));`  
  
クエリで、複数の結果セットを取得する場合、 [sqlsrv_next_result](../../connect/php/sqlsrv-next-result.md)によって次の結果セットに移動できます。  
  
以降のバージョン 1.1 では、 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]、使用することができます[sqlsrv_has_rows](../../connect/php/sqlsrv-has-rows.md)結果セットに行が含まれているかどうか。  
  
## <a name="pdosqlsrv-driver"></a>PDO_SQLSRV ドライバー  
PDO_SQLSRV ドライバー、[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]結果セットからデータを取得するため、次のオプションを提供します。  
  
-   [PDOStatement::fetch](../../connect/php/pdostatement-fetch.md)  
  
-   [PDOStatement::fetchAll](../../connect/php/pdostatement-fetchall.md)  
  
-   [PDOStatement::fetchColumn](../../connect/php/pdostatement-fetchcolumn.md)  
  
-   [PDOStatement::fetchObject](../../connect/php/pdostatement-fetchobject.md)  
  
クエリで、複数の結果セットを取得する場合、 [PDOStatement::nextRowset](../../connect/php/pdostatement-nextrowset.md)によって次の結果セットに移動できます。  
  
スクロール可能なカーソルを指定し、 [PDOStatement::rowCount](../../connect/php/pdostatement-rowcount.md)を呼び出すと、結果セットに含まれる行数を確認できます。  
  
[PDO::prepare](../../connect/php/pdo-prepare.md) により、カーソルの種類を指定できます。 次に、 [PDOStatement::fetch](../../connect/php/pdostatement-fetch.md) によって、行を選択できます。 例および詳細については、 [PDO::prepare](../../connect/php/pdo-prepare.md) を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|---------|---------------|  
|[文字列としてデータを取得する](../../connect/php/retrieving-data-as-a-stream-using-the-sqlsrv-driver.md)|サーバーからデータをストリーミングする方法の概要を説明し、特定のユース ケースへのリンクを示します。|  
|[方向パラメーターを使用する](../../connect/php/using-directional-parameters.md)|ストアド プロシージャを呼び出す際に、方向パラメーターを使用する方法について説明します。|  
|[カーソルの種類を指定し、行を選択する](../../connect/php/specifying-a-cursor-type-and-selecting-rows.md)|SQLSRV ドライバーを使用する場合に、任意の順序でアクセスできる行を含む結果セットを作成する方法を説明します。|  
|[方法: SQLSRV ドライバーを利用し、日付/時刻型を取得する](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)|日付と時刻型を文字列として取得する方法について説明します。|  
  
## <a name="related-sections"></a>関連項目  
[方法: PHP データ型を指定する](../../connect/php/how-to-specify-php-data-types.md)  
  
## <a name="see-also"></a>参照  
[For PHP for SQL Server の Microsoft drivers ガイドのプログラミング](../../connect/php/programming-guide-for-php-sql-driver.md)

[データの取得](../../connect/php/retrieving-data.md)  
  
