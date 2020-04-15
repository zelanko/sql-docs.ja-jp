---
title: フェッチされた行数とステータス |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 20e1632e8da765b0da2785bd846b67d13ebe01ed
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302363"
---
# <a name="number-of-rows-fetched-and-status"></a>フェッチされた行の数と状態
SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性が設定されている場合は **、SQLFetch または SQLFetchScroll**の呼び出しによってフェッチされた行**SQLFetchScroll**数とエラー行を返すバッファーを指定します。 (この数は、ステータスがSQL_ROW_NO_ROWSされていないすべての行のカウントです。**SQLBulkOperations**または**SQLSetPos**の呼び出しの後、バッファーには、関数によって実行された一括操作の影響を受けた行の数が含まれています。 SQL_ATTR_ROW_STATUS_PTRステートメント属性が設定されている場合 **、SQLFetch**または**SQLFetchScroll**は、返された各行の状態を提供する*行の状態配列*を返します。 これらのフィールドによって指されるバッファーの両方がアプリケーションによって割り当てられ、ドライバーによって設定されます。 アプリケーションは、カーソルがクローズされるまで、これらのポインターが有効であることを確認する必要があります。  
  
 行の状態配列のエントリには、各行が正常にフェッチされたかどうか、最後にフェッチされてから更新、追加、または削除されたかどうか、および行のフェッチ中にエラーが発生したかどうかが示されます。 SQLFetch または**SQLFetchScroll**は、複数行セットの 1 行を取得するときにエラーが発生した場合、または一括フェッチの実行中に*SQL_FETCH_BY_BOOKMARK の操作*引数を指定した**SQLBulkOperation**がエラーを検出した場合、行の状態配列内の対応する値をSQL_ROW_ERRORに設定し、行のフェッチを続行し、SQL_SUCCESS_WITH_INFOを返します。 **SQLFetchScroll** エラー処理と行の状態配列の詳細については[、SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)関数と[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)関数の説明を参照してください。
