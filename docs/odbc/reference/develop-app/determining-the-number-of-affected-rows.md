---
title: 影響を受けた行の数を決定する |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- updating data [ODBC], number of rows affected
- number of rows affected by update [ODBC]
- data updates [ODBC], number of rows affected
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86408e2c18eb18ef9119d1fa11172e6eb1d674a5
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="determining-the-number-of-affected-rows"></a>影響を受けた行の数を決定します。
アプリケーションでは、更新、削除、または、行を挿入、後に呼び出すことができます**SQLRowCount**を影響を受けた行の数を決定します。 **SQLRowCount**更新、削除、または実行することによって挿入された行かどうかは、この値を返す、**更新**、**削除**、または**挿入**ステートメントでは、位置指定を実行して更新または delete ステートメントを呼び出した**SQLSetPos**です。  
  
 SQL ステートメントのバッチを実行すると場合、影響を受けた行の数は、バッチ内のすべてのステートメントの合計数またはバッチ内の各ステートメントの個別のカウント。 詳細については、次を参照してください。 [SQL ステートメントのバッチ](../../../odbc/reference/develop-app/batches-of-sql-statements.md)と[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)です。  
  
 影響を受けた行の数は、ステートメント ハンドルに関連付けられている診断の区分で SQL_DIAG_ROW_COUNT 診断ヘッダー フィールドにも返されます。 ただし、このフィールドのデータはリセット後、同じステートメント ハンドルにすべての関数の呼び出しによって返される値は**SQLRowCount**への呼び出しまでは同じ**SQLBulkOperations**、 **SQLExecute**、 **SQLExecDirect**、 **SQLPrepare**、または**SQLSetPos**です。
