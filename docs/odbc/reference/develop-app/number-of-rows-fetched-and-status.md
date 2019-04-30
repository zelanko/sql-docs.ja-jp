---
title: フェッチされた行の数と状態 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- row status array [ODBC]
- number of rows fetched [ODBC]
- result sets [ODBC], row status array
ms.assetid: a069b979-5108-4905-932f-8ae8e7905ff2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab4830ddd56335959dd7049a1dabdcc3a0354213
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63149329"
---
# <a name="number-of-rows-fetched-and-status"></a>フェッチされた行の数と状態
SQL_ATTR_ROWS_FETCHED_PTR ステートメントの属性が設定されている場合、呼び出しからフェッチされた行の数を返すバッファーを指定します。 **SQLFetch**または**SQLFetchScroll**、およびエラーの行。 (この数は、状態 SQL_ROW_NO_ROWS がないすべての行の数です)。呼び出しの後に**SQLBulkOperations**または**SQLSetPos**バッファーには、関数によって実行される一括操作の影響を受けた行の数が含まれています。 SQL_ATTR_ROW_STATUS_PTR ステートメントの属性が設定されている場合**SQLFetch**または**SQLFetchScroll**を返します、*行の状態の配列、* 各の状態を提供します。返された行。 アプリケーションによって割り当てられ、ドライバーによって設定されます。 これらのフィールドによって示されるバッファーの両方が。 アプリケーションは、カーソルが閉じられるまでこれらのポインターが有効であることを確認してください。  
  
 行の状態配列内のエントリが更新されたかどうか、各行が正常にフェッチされたかどうかは、追加、または、行をフェッチ中にエラーが発生したかどうかと、前回フェッチされた以降に削除されました。 場合**SQLFetch**または**SQLFetchScroll**を複数行の行セットの 1 つの行を取得中にエラーが発生した場合、または**SQLBulkOperations**で、*操作* SQL_FETCH_BY_BOOKMARK の引数には、一括取得が実行中にエラーが発生した、SQL_ROW_ERROR、行の状態配列内の対応する値の設定は引き続き、行をフェッチし、SQL_SUCCESS_WITH_INFO が返されます。 エラー処理と行の状態配列の詳細については、次を参照してください。、 [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)と[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)関数の説明。
