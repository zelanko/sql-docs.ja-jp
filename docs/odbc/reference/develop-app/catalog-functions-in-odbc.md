---
title: ODBC のカタログ関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- catalog functions [ODBC], listed
- functions [ODBC], catalog functions
ms.assetid: 4f28f557-7eca-4905-aa6d-45a6cf501a66
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c6731018b99f2f3043e48ee7c174a08cb9ef71fc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306233"
---
# <a name="catalog-functions-in-odbc"></a>ODBC のカタログ関数
ODBC には、次のカタログ関数が含まれています。  
  
|機能|説明|  
|--------------|-----------------|  
|**SQLTables**|データ ソース内のカタログ、スキーマ、テーブル、またはテーブル型の一覧を返します。|  
|**SQLColumns**|1 つ以上のテーブルの列のリストを返します。|  
|**SQLStatistics**|単一のテーブルに関する統計情報の一覧を返します。 また、そのテーブルに関連付けられているインデックスの一覧も返します。|  
|**SQLSpecialColumns**|単一のテーブル内の行を一意に識別する列のリストを返します。 また、自動的に更新されるテーブル内の列の一覧も返します。|  
|**SQLPrimaryKeys**|単一テーブルの主キーを構成する列のリストを返します。|  
|**SQLForeignKeys**|単一のテーブル内の外部キーのリスト、または単一のテーブルを参照する他のテーブルの外部キーのリストを返します。|  
|**SQLTablePrivileges**|1 つ以上のテーブルに関連付けられている権限のリストを返します。|  
|**SQLColumnPrivileges**|1 つのテーブル内の 1 つ以上の列に関連付けられている特権の一覧を返します。|  
|**SQLProcedures**|データ ソース内のプロシージャの一覧を返します。|  
|**SQLProcedureColumns**|1 つのプロシージャの結果セットの入力パラメータと出力パラメータ、戻り値、および列のリストを返します。|  
|**SQLGetTypeInfo**|データ ソースでサポートされている SQL データ型の一覧を返します。 これらのデータ型は、通常 **、CREATE TABLE**ステートメントおよび**ALTER TABLE**ステートメントで使用されます。|  
  
 **SQLTables** **、SQLColumns** **、SQL 統計、** および**SQL 特殊列**は、オープン グループの CLI に準拠し **、SQLGetTypeInfo**は、ほとんどのドライバーによって実装されます。 残りのカタログ関数は、ODBC 準拠レベルです。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)  
  
-   [カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)  
  
-   [スキーマ ビュー](../../../odbc/reference/develop-app/schema-views.md)
