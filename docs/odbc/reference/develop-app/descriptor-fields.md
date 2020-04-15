---
title: 記述子フィールド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], fields
- header fields [ODBC]
- record fields [ODBC]
ms.assetid: f38623c8-fdd4-4601-b1f0-97c593d31177
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94e70de7d237c2eca9aee81979cb19d5295561b5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305923"
---
# <a name="descriptor-fields"></a>記述子フィールド
記述子には、列またはパラメーターを完全に記述する*ヘッダー*フィールドと*レコード*フィールドが含まれます。  
  
 記述子には、次のヘッダー フィールドのコピーが 1 つ含まれています。 ヘッダー フィールドを変更すると、すべての列またはパラメーターに影響します。  
  
|||  
|-|-|  
|SQL_DESC_ALLOC_TYPE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_COUNT|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 記述子に 0 個以上の記述子レコードが含まれています。 各レコードは、記述子のタイプに応じて、列またはパラメーターを記述します。 新しい列またはパラメーターがバインドされると、記述子に新しいレコードが追加されます。 列またはパラメーターがバインド解除されると、レコードは記述子から削除されます。 各レコードには、次のフィールドのコピーが 1 つ含まれています。  
  
|||  
|-|-|  
|SQL_DESC_AUTO_UNIQUE_VALUE|SQL_DESC_LOCAL_TYPE_NAME|  
|SQL_DESC_BASE_COLUMN_NAME|SQL_DESC_NAME|  
|SQL_DESC_BASE_TABLE_NAME|SQL_DESC_NULLABLE|  
|SQL_DESC_CASE_SENSITIVE|SQL_DESC_OCTET_LENGTH|  
|SQL_DESC_CATALOG_NAME|SQL_DESC_OCTET_LENGTH_PTR|  
|SQL_DESC_CONCISE_TYPE|SQL_DESC_PARAMETER_TYPE|  
|SQL_DESC_DATA_PTR|SQL_DESC_PRECISION|  
|SQL_DESC_DATETIME_INTERVAL_CODE|SQL_DESC_SCALE|  
|SQL_DESC_DATETIME_INTERVAL_PRECISION|SQL_DESC_SCHEMA_NAME|  
|SQL_DESC_DISPLAY_SIZE|SQL_DESC_SEARCHABLE|  
|SQL_DESC_FIXED_PREC_SCALE|SQL_DESC_TABLE_NAME|  
|SQL_DESC_INDICATOR_PTR|SQL_DESC_TYPE|  
|SQL_DESC_LABEL|SQL_DESC_TYPE_NAME|  
|SQL_DESC_LENGTH|SQL_DESC_UNNAMED|  
|SQL_DESC_LITERAL_PREFIX|SQL_DESC_UNSIGNED|  
|SQL_DESC_LITERAL_SUFFIX|SQL_DESC_UPDATABLE|  
  
 多くのステートメント属性は、記述子のヘッダー・フィールドに対応します。 これらの属性を**SQLSetStmtAttr**の呼び出しで設定し **、SQLSetDescField**を呼び出して対応する記述子ヘッダー フィールドを設定しても、同じ効果があります。 同じ情報を取得する**SQLGetStmtAttr**と**SQLGetDescField**についても同じことが言えます。 記述子関数の代わりにステートメント関数を呼び出す場合、記述子ハンドルを取得する必要がなされないという利点があります。  
  
 ステートメント属性を設定すると、次のヘッダー フィールドを設定できます。  
  
|||  
|-|-|  
|SQL_DESC_ARRAY_SIZE|SQL_DESC_BIND_TYPE|  
|SQL_DESC_ARRAY_STATUS_PTR|SQL_DESC_ROWS_PROCESSED_PTR|  
|SQL_DESC_BIND_OFFSET_PTR||  
  
 このセクションでは、次のトピックを扱います。  
  
-   [レコード カウント](../../../odbc/reference/develop-app/record-count.md)  
  
-   [バインドされた記述子レコード](../../../odbc/reference/develop-app/bound-descriptor-records.md)  
  
-   [遅延フィールド](../../../odbc/reference/develop-app/deferred-fields.md)  
  
-   [整合性チェック](../../../odbc/reference/develop-app/consistency-check.md)
