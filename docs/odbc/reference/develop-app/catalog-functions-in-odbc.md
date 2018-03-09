---
title: "カタログ関数 (ODBC の) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- catalog functions [ODBC], listed
- functions [ODBC], catalog functions
ms.assetid: 4f28f557-7eca-4905-aa6d-45a6cf501a66
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e38bcf3158ba294d09d6898b4ab55b6ecbd33b10
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="catalog-functions-in-odbc"></a>Odbc カタログ関数
ODBC には、次のカタログ関数が含まれています。  
  
|機能|Description|  
|--------------|-----------------|  
|**SQLTables**|データ ソースのカタログ、スキーマ、テーブル、またはテーブル型の一覧を返します。|  
|**SQLColumns**|1 つまたは複数のテーブル内の列の一覧を返します。|  
|**SQLStatistics**|1 つのテーブルに関する統計情報の一覧を返します。 そのテーブルに関連付けられているインデックスの一覧を返します。|  
|**SQLSpecialColumns**|1 つのテーブル内の行を一意に識別する列の一覧を返します。 自動的に更新されるテーブル内の列の一覧を返します。|  
|**SQLPrimaryKeys**|1 つのテーブルの主キーを構成する列の一覧を返します。|  
|**SQLForeignKeys**|1 つのテーブルまたはその他の 1 つのテーブルを参照するテーブルの外部キーの一覧内の外部キーの一覧を返します。|  
|**SQLTablePrivileges**|1 つまたは複数のテーブルに関連付けられた権限の一覧を返します。|  
|**SQLColumnPrivileges**|1 つのテーブル内の 1 つまたは複数の列に関連付けられた権限の一覧を返します。|  
|**SQLProcedures**|データ ソース内のプロシージャの一覧を返します。|  
|**SQLProcedureColumns**|1 つのプロシージャの結果セットには、入力呼び出し力パラメーター、戻り値、および列の一覧を返します。|  
|**SQLGetTypeInfo**|データ ソースによってサポートされる SQL データ型の一覧を返します。 通常、これらのデータ型で使用**CREATE TABLE**と**ALTER TABLE**ステートメントです。|  
  
 **SQLTables**、 **SQLColumns**、 **SQLStatistics**、および**SQLSpecialColumns**開くグループの CLI とに準拠して**SQLGetTypeInfo** 92 CLI、ISO に準拠している、ほとんどのドライバーによって実装されます。 残りのカタログ関数は、ODBC 準拠のレベルでです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [スキーマ ビュー](../../../odbc/reference/develop-app/schema-views.md)
