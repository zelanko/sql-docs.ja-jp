---
title: 文字列パラメータを受け入れる関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- desktop database drivers [ODBC], string parameters
- ODBC desktop database drivers [ODBC], string parameters
- Jet-based ODBC drivers [ODBC], string parameters
- functions [ODBC], string parameters
- string parameters [ODBC]
ms.assetid: 869b8421-f71e-4dfd-adce-691bd3012b16
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 01d0f143c72f57e946f7fe2bf52a50910d4e56aa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286302"
---
# <a name="functions-accepting-string-parameters"></a>文字列パラメーターを受け入れる関数
文字列パラメータを受け取る関数はすべて、Unicode に変換されます。 (関数の "W" 形式がエクスポートされます。バイト数は、該当する ODBC API の文字数に変換されます。 これは、以下の機能に適用されます。  
  
-   **SQLConnect**  
  
-   **SQLDriverConnect**  
  
-   **属性**  
  
-   **SQLDescribeCol**  
  
-   **SQL エラー** (置換**されたフィールド**)  
  
-   **SQLExecDirect**  
  
-   **SQLGetCursorName**  
  
-   **カーソルを設定します。**  
  
-   **SQLGetStmtAttr**  
  
-   **SQLGetInfo**  
  
-   **オプション**を指定します **。**  
  
-   **オプションを**設定します **。**  
  
-   **オプションを指定します。**  
  
-   **オプションを指定します。**  
  
-   **SQLGetTypeInfo**  
  
-   **SQLStatistics**  
  
-   **SQLTables**  
  
-   **を実行します。**  
  
-   **SQLSpecialColumns**  
  
-   **コンフィデックス**  
  
-   **構成DSN**
