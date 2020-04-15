---
title: 影響を受ける行の数を決定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- updating data [ODBC], number of rows affected
- number of rows affected by update [ODBC]
- data updates [ODBC], number of rows affected
ms.assetid: 1e56297d-a786-415e-b66d-b42d1b2a8d45
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 156a5fe41d2c9b57a33bbc2bdb4540d1f5b00340
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305893"
---
# <a name="determining-the-number-of-affected-rows"></a>影響を受ける行数の決定
アプリケーションが行を更新、削除、または挿入した後 **、SQLRowCount**を呼び出して、影響を受けた行数を判断できます。 **SQLRowCount**は **、UPDATE** **、DELETE、** または**INSERT**ステートメントを実行するか、位置指定された更新または削除ステートメントを実行するか **、SQLSetPos**を呼び出すことによって、行が更新、削除、または挿入されたかどうかに関係なく、この値を返します。  
  
 SQL ステートメントのバッチが実行される場合、影響を受ける行のカウントは、バッチ内のすべてのステートメントの合計カウント、またはバッチ内の各ステートメントの個別のカウントになります。 詳細については、「 [SQL ステートメントのバッチ](../../../odbc/reference/develop-app/batches-of-sql-statements.md)と[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)」を参照してください。  
  
 影響を受ける行の数は、ステートメント ハンドルに関連付けられた診断領域のSQL_DIAG_ROW_COUNT診断ヘッダー フィールドにも返されます。 ただし、このフィールドのデータは、同じステートメント ハンドルでの各関数呼び出し後にリセットされますが **、SQLRowCount**によって返される値は **、SQLBulkOperations** **、SQLExecute、SQLExecDirect、SQLPrepare**、または**SQLSetPos**の呼び出しまでは変わりません。 **SQLExecDirect** **SQLPrepare**
