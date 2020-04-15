---
title: データ型識別子の使用 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8be8eef0441d48ed03ea6ccf8f656627c1dd9b63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301423"
---
# <a name="using-data-type-identifiers"></a>データ型識別子の使用
アプリケーションでは、データ型識別子を使用する 2 つの方法: ドライバーにバッファーを記述し、ドライバーから結果セットに関するメタデータを取得して、データの格納に使用する C バッファーの種類を決定できるようにします。 アプリケーションは、次の関数を呼び出してこれらのタスクを実行します。  
  
-   アプリケーション バッファーの C データ型を記述する**SQLBindParameter** **、SQLBindCol**、および**SQLGetData。**  
  
-   **SQLBindパラメータ -** 動的パラメータのSQLデータ型を記述します。  
  
-   **SQLCol 属性**と**SQLDescribeCol** - 結果セット列の SQL データ型を取得します。  
  
-   **パラメーターの**SQL データ型を取得します。  
  
-   **SQLColumns** **、SQL プロシージャカラム**、および**SQL 特殊列**- さまざまなスキーマ情報の SQL データ型を取得します。  
  
-   **サポート**されているデータ型の一覧を取得します。  
  
 データ型識別子は、記述子のSQL_DESC_CONCISE_TYPE フィールドに格納されます。 記述子関数**SQLSetDescField**と**SQLSetDescRec**は、前のリストに示したタスクを実行するのに適切な型と共に使用できます。 詳細については、「 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)」を参照してください。
