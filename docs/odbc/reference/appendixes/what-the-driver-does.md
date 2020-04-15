---
title: ドライバの機能 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: 75dcdea6-ff6b-4ac8-aa11-a1f9edbeb8e6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c0438478f5aa625ffdd4d3bcd1c0a6f0f80d3367
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301393"
---
# <a name="what-the-driver-does"></a>ドライバーの機能
次の表は、ODBC *3.x*ドライバーがブロックカーソルとスクロール可能なカーソルに対して実装する関数とステートメント属性をまとめたものです。  
  
|機能または<br /><br /> ステートメント属性|説明|  
|-----------------------------------------|--------------|  
|SQL_ATTR_ROW_STATUS_PTR|**SQLFetch**および SQL フェッチスクロールによって入力される行の状態配列のアドレス**を設定します**。 ステートメント状態 S6 で**SQLSetPos**が呼び出された場合も、この配列は**SQLSetPos**によって埋められます。 状態 S7 で**SQLSetPos**が呼び出された場合、この配列は格納されませんが **、SQLExtendedFetch**の*RowStatusArray*引数によって指される配列が埋められます。 詳細については、「付録 B: ODBC 状態[遷移](../../../odbc/reference/appendixes/statement-transitions.md)テーブル」のステートメントの遷移を参照してください。|  
|SQL_ATTR_ROWS_FETCHED_PTR|フェッチされた行数**を返す****バッファー**のアドレスを設定します。 **SQLExtendedFetch**が呼び出された場合、このバッファーは格納されませんが、*引数 RowCountPtr*はフェッチされた行の数を指します。|  
|SQL_ATTR_ROW_ARRAY_SIZE|SQL フェッチおよび SQL**フェッチ**スクロールで使用される行セットのサイズ**を設定します**。|  
|SQL_ROWSET_SIZE|**SQLExtendedFetch**で使用される行セットのサイズを設定します。 ODBC *3.x*ドライバーは **、SQLExtendedFetch**または**SQLSetPos**を呼び出す ODBC *2.x*アプリケーションを使用する場合は、これを実装します。|  
|**オペレーション**|ODBC *3.x*ドライバーは、SQL_ADD*の操作*で**SQLSetPos**を使用する ODBC *2.x*アプリケーションで動作する必要がある場合、ドライバーは、SQL_ADDの*操作*で**SQLBulkOperations**に加えて、SQL_ADDの*操作*で**SQLSetPos**をサポートする必要があります。|  
|**フェッチ**|指定された行セットを返します。 ODBC *3.x*ドライバーは **、SQLExtendedFetch**または**SQLSetPos**を呼び出す ODBC *2.x*アプリケーションを使用する場合は、これを実装します。 実装の詳細を次に示します。<br /><br /> - ドライバーは、SQL_ROWSET_SIZE ステートメント属性の値から行セットのサイズを取得します。<br />- ドライバーは、SQL_ATTR_ROW_STATUS_PTR ステートメント属性ではなく *、RowStatusArray*引数から行の状態の配列のアドレスを取得します。 **呼**び出しで*の引数*は、NULL ポインターにすることはできません。 ODBC *3.x*では、SQL_ATTR_ROW_STATUS_PTR ステートメント属性は null ポインターにすることができます。<br />- ドライバーは、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性ではなく *、RowCountPtr*引数からフェッチされたバッファー行のアドレスを取得します。<br />- ドライバは SQLSTATE 01S01 (行内エラー) を返して **、SQLExtendedFetch**の呼び出しによって行がフェッチされた間にエラーが発生したことを示します。 ODBC *3.x*ドライバーは、SQLFetch または**SQLFetchScroll**が呼び出されたときにではなく **、SQLExtendedFetch**が呼び出**SQLFetchScroll**された場合にのみ SQLSTATE 01S01 (行のエラー) を返す必要があります。 下位互換性を維持するために **、SQLSTATE**01S01 (行のエラー) が SQLExtendedFetch によって返された場合、ドライバー マネージャーは[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)の「状態レコードのシーケンス」に記載されている規則に従って、エラー キューの状態レコードを並べ替えません。|  
|**SQLFetch**|次の行セットを返します。 実装の詳細を次に示します。<br /><br /> - ドライバーは、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性の値から行セットのサイズを取得します。<br />- ドライバーは、SQL_ATTR_ROW_STATUS_PTR ステートメント属性から行の状態の配列のアドレスを取得します。<br />- ドライバーは、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性からフェッチされたバッファー行のアドレスを取得します。<br />- アプリケーションは **、呼**び出しを組み合わせて使用**できます。**<br />-   列 0 がバインドされている場合 **、SQLFetch**はブックマークを返します。<br />-   **SQLFetch を**呼び出して、複数の行を返すことができます。<br />- SQLFetch の呼び出しによって行がフェッチされている間にエラーが発生したことを示す**SQLSTATE**01S01 (行のエラー) を返さないドライバー。|  
|**SQLFetchScroll**|指定された行セットを返します。 実装の詳細を次に示します。<br /><br /> - ドライバーは、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性から行セットのサイズを取得します。<br />- ドライバーは、SQL_ATTR_ROW_STATUS_PTR ステートメント属性から行の状態の配列のアドレスを取得します。<br />- ドライバーは、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性からフェッチされたバッファー行のアドレスを取得します。<br />- アプリケーションは **、呼**び出しを組み合わせて使用**できます。**<br />- **SQLFetchScroll**の呼び出しによって行がフェッチされている間にエラーが発生したことを示す SQLSTATE 01S01 (行のエラー) を返さないドライバー。|  
|**SQLSetPos**|さまざまな位置指定操作を実行します。 実装の詳細を次に示します。<br /><br /> - これは、ステートメント状態 S6 または S7 で呼び出すことができます。 詳細については、「付録 B: ODBC 状態[遷移](../../../odbc/reference/appendixes/statement-transitions.md)テーブル」のステートメントの遷移を参照してください。<br />- ステートメント状態 S5 または S6 で呼び出された場合、ドライバーは、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性から行セットのサイズを取得し、SQL_ATTR_ROW_STATUS_PTR ステートメント属性から行の状態の配列のアドレスを取得します。<br />- ステートメント状態 S7 で呼び出された場合、ドライバーは、SQL_ROWSET_SIZE ステートメント属性から行セットのサイズを取得し **、SQLExtendedFetch**の*RowStatusArray*引数から行状態の配列のアドレスを取得します。<br />- ドライバーは、関数が S7 で呼び出されたときに一括操作を実行する**SQLSetPos**の呼び出しによって行がフェッチされている間にエラーが発生したことを示すだけ SQLSTATE 01S01 (行のエラー) を返します。 下位互換性を維持するために **、SQLSTATE**01S01 (行のエラー) が SQLSetPos によって返された場合、ドライバー マネージャーは[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)の「状態レコードのシーケンス」に記載されている規則に従って、エラー キューの状態レコードを並べ替えません。<br />- ドライバーは、SQL_ADDの*操作*引数を指定して**SQLSetPos**を呼び出す ODBC *2.x*アプリケーションで動作する必要がある場合、ドライバーは、SQL_ADDの*操作*引数を使用して**SQLSetPos**をサポートする必要があります。|
