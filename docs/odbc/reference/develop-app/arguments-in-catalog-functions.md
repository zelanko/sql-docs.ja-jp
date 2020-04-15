---
title: カタログ関数の引数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], about arguments
- functions [ODBC], catalog functions
ms.assetid: f5e0abec-8f24-42e0-b94f-16dd1f2004fd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 819c10d0b137d5e0999c1e10bf22810392509f76
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288168"
---
# <a name="arguments-in-catalog-functions"></a>カタログ関数の引数
すべてのカタログ関数は、アプリケーションが返されるデータの範囲を制限できる引数を受け入れます。 たとえば、次のコードの**SQLTables**の最初の呼び出しと 2 番目の呼び出しは、すべてのテーブルに関する情報を含む結果セットを返し、3 番目の呼び出しは Orders テーブルに関する情報を返します。  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 カタログ関数の文字列引数は、通常引数 (OA)、パターン値引数 (PV)、識別子引数 (ID)、および値リスト引数 (VL) の 4 つの異なる型に分類されます。 ほとんどの文字列引数は、SQL_ATTR_METADATA_ID ステートメント属性の値に応じて、2 つの異なる型のいずれかになります。 次の表は、各カタログ関数の引数と、SQL_ATTR_METADATA_ID のSQL_TRUEまたはSQL_FALSE値の引数の型を示しています。  
  
|機能|引数|SQL_時に入力<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_FALSE|SQL_時に入力<br /><br /> ATTR_METADATA_<br /><br /> ID = SQL_TRUE|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*カタログ名**スキーマ名**テーブル名**列名*|OA OA OA PV|ID ID ID ID|  
|**SQLColumns**|*カタログ名**スキーマ名**テーブル名**列名*|OA PV PV PV|ID ID ID ID|  
|**SQLForeignKeys**|*を**PKTableName**FKCatalogName**FKSchemaName*使用*します**。*|OA OA OA OA OA OA|ID ID ID ID ID ID|  
|**SQLPrimaryKeys**|*カタログ名**スキーマ名**テーブル名*|OA OA OA|ID ID ID|  
|**SQLProcedureColumns**|*カタログ名**スキーマ名**プロシージャ名**列名*|OA PV PV PV|ID ID ID ID|  
|**SQLProcedures**|*カタログ名**スキーマ名**をクリックします。*|OA PV PV|ID ID ID|  
|**SQLSpecialColumns**|*カタログ名**スキーマ名**テーブル名*|OA OA OA|ID ID ID|  
|**SQLStatistics**|*カタログ名**スキーマ名**テーブル名*|OA OA OA|ID ID ID|  
|**SQLTablePrivileges**|*カタログ名**スキーマ名**テーブル名*|OA PV PV|ID ID ID|  
|**SQLTables**|*カタログ名**スキーマ名**テーブル名**テーブルタイプ*|PV PV PV VL|ID ID ID VL|  
  
 このセクションでは、次のトピックを扱います。  
  
-   [通常の引数](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [パターン値の引数](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [識別子の引数](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [値リストの引数](../../../odbc/reference/develop-app/value-list-arguments.md)
