---
title: "データ型識別子を使用して |Microsoft ドキュメント"
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
- data types [ODBC], identifiers
- identifiers [ODBC], data types
ms.assetid: 467e0c0c-a818-4737-8a24-3d8e15c7e162
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9f29b6e27866b5893c6875ee5c438d7c13a996e9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="using-data-type-identifiers"></a>データ型識別子の使用
アプリケーションでは、2 つの方法でのデータ型識別子を使用します。 ドライバーにバッファーを記述すると結果を使用してデータを格納するバッファーの C の種類を判別できるように、ドライバーからセットに関するメタデータを取得します。 アプリケーションでは、これらのタスクを実行するには、次の関数を呼び出します。  
  
-   **SQLBindParameter**、 **SQLBindCol**、および**SQLGetData** — アプリケーション バッファーの C データ型を記述します。  
  
-   **SQLBindParameter** : 動的パラメーターの SQL データ型を記述します。  
  
-   **SQLColAttribute**と**SQLDescribeCol** — を結果セット列の SQL データ型を取得します。  
  
-   **SQLDescribeParameter** : パラメーターの SQL データ型を取得します。  
  
-   **SQLColumns**、 **SQLProcedureColumns**、および**SQLSpecialColumns** — さまざまなスキーマの情報の SQL データ型を取得するには  
  
-   **SQLGetTypeInfo** — サポートされるデータ型の一覧を取得するには  
  
 データ型識別子は、記述子の SQL_DESC_CONCISE_TYPE フィールドに格納されます。 記述子関数**SQLSetDescField**と**SQLSetDescRec**上記の一覧に表示されるタスクを実行する適切な型で使用できます。 詳細については、次を参照してください。 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)です。

