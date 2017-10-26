---
title: "ドライバーの動作 |Microsoft ドキュメント"
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
- scrollable cursors [ODBC]
- cursors [ODBC], backward compatibility
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- block cursors [ODBC]
ms.assetid: 75dcdea6-ff6b-4ac8-aa11-a1f9edbeb8e6
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 07e94046370f8140fdacec2cf708de0a62311a27
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="what-the-driver-does"></a>ドライバーの動作
次の表に、どのような関数とステートメント属性 ODBC 3*.x*ブロックとスクロール可能なカーソルのドライバーを実装する必要があります。  
  
|関数または<br /><br /> ステートメント属性|コメント|  
|-----------------------------------------|--------------|  
|SQL_ATTR_ROW_STATUS_PTR|埋められた行の状態配列のアドレス セット**SQLFetch**と**SQLFetchScroll**です。 この配列がで埋められたも**SQLSetPos**場合**SQLSetPos**ステートメント状態 S6 で呼び出されます。 場合**SQLSetPos**が呼び出された状態 S7、この配列が指定されていませんが、配列を指す、 *RowStatusArray*の引数**SQLExtendedFetch**入力されます。 詳細については、次を参照してください。[ステートメント遷移](../../../odbc/reference/appendixes/statement-transitions.md)付録 b: ODBC 状態遷移表でします。|  
|SQL_ATTR_ROWS_FETCHED_PTR|バッファーのアドレスを設定**SQLFetch**と**SQLFetchScroll**フェッチされた行の数を返します。 場合**SQLExtendedFetch**が呼び出されると、このバッファーが指定されていませんが、 *RowCountPtr*引数がフェッチされた行の数を指します。|  
|SQL_ATTR_ROW_ARRAY_SIZE|によって使用される行セット サイズ設定**SQLFetch**と**SQLFetchScroll**です。|  
|SQL_ROWSET_SIZE|によって使用される行セット サイズ設定**SQLExtendedFetch**です。 ODBC 3*.x*ドライバーではこれが実装される ODBC 2 を使用する場合*。x*を呼び出すアプリケーションに**SQLExtendedFetch**または**SQLSetPos**です。|  
|**SQLBulkOperations**|場合、ODBC 3*.x*ドライバーは、ODBC 2 を使用する必要があります*。x*を使用するアプリケーション**SQLSetPos**で、*操作*SQL_ADD のドライバーをサポートする必要があります**SQLSetPos**で、 *操作*に加えて SQL_ADD の**SQLBulkOperations**で、*操作*SQL_ADD のです。|  
|**SQLExtendedFetch**|指定した行セットを返します。 ODBC 3*.x*ドライバーではこれが実装される ODBC 2 を使用する場合*。x*を呼び出すアプリケーションに**SQLExtendedFetch**または**SQLSetPos**です。 実装の詳細を次に示します。<br /><br /> -ドライバーは、SQL_ROWSET_SIZE ステートメント属性の値から行セットのサイズを取得します。<br />-ドライバーからの行の状態配列のアドレスを取得する、 *RowStatusArray*引数、SQL_ATTR_ROW_STATUS_PTR ステートメント属性ではありません。 *RowStatusArray*への呼び出しで引数**SQLExtendedFetch** null ポインターをすることはできません。 (ODBC 3 なお*.x*、SQL_ATTR_ROW_STATUS_PTR ステートメント属性は null ポインターであることができます)。<br />-ドライバーからフェッチされた行のバッファーのアドレスを取得する、 *RowCountPtr*引数、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性ではありません。<br />-ドライバーは SQLSTATE 01S01 を返します (行でエラー) への呼び出しによって行がフェッチされたときにエラーが発生したことを示すために**SQLExtendedFetch**です。 ODBC 3*.x*ドライバーは SQLSTATE 01S01 を返す必要があります (行でエラー) される場合にのみ**SQLExtendedFetch**が呼び出されたがないとき**SQLFetch**または**SQLFetchScroll**と呼びます。 旧バージョンとの互換性を維持するときに SQLSTATE 01S01 (行でエラー) がによって返される**SQLExtendedFetch**、ドライバー マネージャーは、順序付けしません状態レコード"シーケンスの状態で説明したルールに従ってエラー キューレコード数"のセクション[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)です。|  
|**SQLFetch**|次の行セットを返します。 実装の詳細を次に示します。<br /><br /> -ドライバーは、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性の値から行セットのサイズを取得します。<br />-ドライバーは、SQL_ATTR_ROW_STATUS_PTR ステートメント属性からの行の状態配列のアドレスを取得します。<br />-ドライバーは、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性からバッファーをフェッチされた行のアドレスを取得します。<br />-アプリケーションは、間の呼び出しを混在させることが**SQLFetchScroll**と**SQLFetch**です。<br />-   **SQLFetch**列 0 がバインドされている場合は、ブックマークを返します。<br />-   **SQLFetch** 1 つ以上の行を返すと呼ばれることができます。<br />-ドライバーは SQLSTATE 01S01 を返さないこと (行でエラー) への呼び出しによって行がフェッチされたときにエラーが発生したことを示すために**SQLFetch**です。|  
|**SQLFetchScroll**|指定した行セットを返します。 実装の詳細を次に示します。<br /><br /> -ドライバーは、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性から行セットのサイズを取得します。<br />-ドライバーは、SQL_ATTR_ROW_STATUS_PTR ステートメント属性からの行の状態配列のアドレスを取得します。<br />-ドライバーは、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性からバッファーをフェッチされた行のアドレスを取得します。<br />-アプリケーションは、間の呼び出しを混在させることが**SQLFetchScroll**と**SQLFetch**です。<br />-ドライバーは SQLSTATE 01S01 を返さないこと (行でエラー) への呼び出しによって行がフェッチされたときにエラーが発生したことを示すために**SQLFetchScroll**です。|  
|**SQLSetPos**|さまざまな位置指定操作を実行します。 実装の詳細を次に示します。<br /><br /> -これは、S6 または S7 ステートメントの状態で呼び出すことができます。 詳細については、次を参照してください。[ステートメント遷移](../../../odbc/reference/appendixes/statement-transitions.md)付録 b: ODBC 状態遷移表でします。<br />-これは、呼び出された場合 S5 または S6 ステートメントの状態で、ドライバーは SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性と、SQL_ATTR_ROW_STATUS_PTR ステートメント属性からの行の状態配列のアドレスから行セットのサイズを取得します。<br />場合、これは、ステートメントの状態 S7 で呼び出される、行セットのサイズから取り出します SQL_ROWSET_SIZE ステートメント属性と、行の状態配列からのアドレス、 *RowStatusArray*の引数**SQLExtendedFetch**です。<br />-ドライバーは SQLSTATE 01S01 を返します (行でエラー) への呼び出しによって行がフェッチされたときにエラーが発生したことを示すためにのみ**SQLSetPos** S7 の状態で、関数が呼び出されると、一括操作を実行します。 場合は、旧バージョンとの互換性を保持するために SQLSTATE 01S01 (行でエラー) がによって返される**SQLSetPos**、ドライバー マネージャーは、順序付けしません状態レコード「シーケンスの状態レコード」に記載されている規則に従ってエラー キューセクション[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)です。<br />場合は、ドライバーは、ODBC 2 で動作する必要があります。*x*を呼び出すアプリケーションに**SQLSetPos**で、*操作*SQL_ADD の引数は、ドライバーをサポートする必要があります**SQLSetPos** と*操作*SQL_ADD の引数。|

