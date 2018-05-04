---
title: カタログ関数の引数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- arguments in catalog functions [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], about arguments
- functions [ODBC], catalog functions
ms.assetid: f5e0abec-8f24-42e0-b94f-16dd1f2004fd
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 81eb0874d8737ec76736bf4caffb8e646bee29cb
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="arguments-in-catalog-functions"></a>カタログ関数の引数
すべてのカタログ関数では、引数として使用するアプリケーションが返されるデータのスコープを制限できますを受け取ります。 たとえば、最初と 2 番目の呼び出し**SQLTables**次のコードには、3 番目の呼び出しを Orders テーブルに関する情報を返すときに、すべてのテーブルに関する情報を含む結果セットを返します。  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, NULL, 0, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "%", SQL_NTS, NULL, 0);  
SQLTables(hstmt3, NULL, 0, NULL, 0, "Orders", SQL_NTS, NULL, 0);  
```  
  
 カタログ関数の文字列引数は 4 つの種類に分類されます。 通常の引数 (OA)、パターン値の引数 (PV)、id の引数 (ID)、および値リストの引数 (VL)。 ほとんどの文字列引数は、SQL_ATTR_METADATA_ID ステートメント属性の値に基づいて、2 つの異なる型のいずれかの指定できます。 次の表は、各カタログ関数の引数と SQL_ATTR_METADATA_ID の SQL_TRUE または SQL_FALSE 値の引数の型を示しています。  
  
|関数|引数|入力時に sql _<br /><br /> ATTR_METADATA_<br /><br /> ID SQL_FALSE を =|入力時に sql _<br /><br /> ATTR_METADATA_<br /><br /> ID SQL_TRUE を =|  
|--------------|--------------|---------------------------------------------------------------|--------------------------------------------------------------|  
|**SQLColumnPrivileges**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA OA OA PV|ID ID ID の ID|  
|**SQLColumns**|*CatalogName* *SchemaName* *TableName* *ColumnName*|OA PV PV PV|ID ID ID の ID|  
|**SQLForeignKeys**|*PKCatalogName* *PKSchemaName* *PKTableName* *FKCatalogName* *FKSchemaName* *FKTableName*|OA OA OA OA OA OA|ID ID ID ID ID ID|  
|**SQLPrimaryKeys**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID の ID の ID|  
|**SQLProcedureColumns**|*CatalogName* *SchemaName* *ProcName* *ColumnName*|OA PV PV PV|ID ID ID の ID|  
|**SQLProcedures**|*CatalogName* *SchemaName* *ProcName*|OA PV PV|ID の ID の ID|  
|**SQLSpecialColumns**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID の ID の ID|  
|**SQLStatistics**|*CatalogName* *SchemaName* *TableName*|OA OA OA|ID の ID の ID|  
|**SQLTablePrivileges**|*CatalogName* *SchemaName* *TableName*|OA PV PV|ID の ID の ID|  
|**SQLTables**|*CatalogName* *SchemaName* *TableName* *TableType*|PV PV PV VL|ID ID ID VL|  
  
 このセクションでは、次のトピックを扱います。  
  
-   [通常の引数](../../../odbc/reference/develop-app/ordinary-arguments.md)  
  
-   [パターン値の引数](../../../odbc/reference/develop-app/pattern-value-arguments.md)  
  
-   [識別子の引数](../../../odbc/reference/develop-app/identifier-arguments.md)  
  
-   [値リストの引数](../../../odbc/reference/develop-app/value-list-arguments.md)
