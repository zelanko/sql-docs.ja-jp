---
title: "記憶域を割り当てる |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-results
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- column-wise binding [ODBC]
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLBindCol function
- storing data [ODBC]
- result sets [ODBC], storage
- SQL Server Native Client ODBC driver, data storage
- row-wise binding
- binding result sets [SQL Server Native Client]
- array binding
ms.assetid: 11c81955-5300-495f-925f-9256f2587b58
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 863050ece0400e842b9421ffae8bf55f9132a144
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="assigning-storage"></a>ストレージの割り当て
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  アプリケーションでは、SQL ステートメントの実行前後に、結果用のストレージを割り当てることができます。 アプリケーションで最初に SQL ステートメントを準備または実行すると、結果のストレージを割り当てる前に、結果セットに関する情報を取得できます。 たとえば、結果セットが不明であれば、アプリケーションでは、列にストレージを割り当てる前に、列数を取得する必要があります。  
  
 アプリケーションが呼び出す関連付けるにはデータの列に対する記憶域、 [SQLBindCol](../../relational-databases/native-client-odbc-api/sqlbindcol.md)渡します。  
  
-   データの変換先のデータ型。  
  
-   データの出力バッファーのアドレス。  
  
     アプリケーションではこのバッファーを割り当てる必要があります。このバッファーは、変換後の形式でデータを保持するのに十分な大きさを確保する必要があります。  
  
-   出力バッファーの長さ。  
  
     この値は、返されるデータが C の固定幅データ (整数、実数、日付構造体など) の場合は無視されます。  
  
-   使用できるデータのバイト数を返すストレージ バッファーのアドレス。  
  
 また、アプリケーションは、結果セットの列をプログラム変数の配列にバインドして、結果セットの行をブロック単位でフェッチする機能をサポートすることもできます。 配列のバインドの 2 つの異なる種類あります。  
  
-   列方向のバインドは、各列を変数の独自の配列にバインドすると終了します。  
  
     呼び出して、列方向のバインドが指定されて[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)で*属性*sql_attr_row_bind_type と*ValuePtr*を SQL_BIND_BY_COLUMN に設定します。 すべての配列には、同じ数の要素を保持する必要があります。  
  
-   行方向のバインドは、SQL ステートメント内のすべてのパラメーターを 1 単位として、パラメーターの各変数を保持する構造体の配列にバインドすると終了します。  
  
     呼び出して、行方向のバインドが指定されて**SQLSetStmtAttr**で*属性*sql_attr_row_bind_type と*ValuePtr*保留されている構造体のサイズに設定、結果を受け取る変数は、列を設定します。  
  
 また、アプリケーションでは、SQL_ATTR_ROW_ARRAY_SIZE を列または行の配列内の要素数に設定し、SQL_ATTR_ROW_STATUS_PTR と SQL_ATTR_ROWS_FETCHED_PTR も設定します。  
  
## <a name="see-also"></a>参照  
 [処理結果 &#40;ODBC&#41;](../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
  
