---
title: "ドライバー マネージャーは |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver manager [ODBC], backward compatibility
- compatibility [ODBC], driver manager
- ODBC driver manager [ODBC]
- backward compatibility [ODBC], driver manager
ms.assetid: 57f65c38-d9ee-46c8-9051-128224a582c6
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a4d94cc3308964a97e5355de0f68306dcd375058
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="what-the-driver-manager-does"></a>ドライバー マネージャーの新機能
次の表方法 ODBC 3*.x*ドライバー マネージャーは、ODBC 2 への呼び出しをマップします*。x*と ODBC 3*.x*ドライバー。  
  
|関数または<br /><br /> ステートメント属性|コメント|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|使用する、ブックマークを指す**SQLFetchScroll**です。 実装の詳細を次に示します。<br /><br /> 場合、アプリケーション設定この ODBC 2 でします。*x*ドライバー、ODBC 3*.x*ドライバー マネージャーがそれをキャッシュします。 ポインターを逆参照し、値を ODBC 2 に渡します。*x*内のドライバー、 *FetchOffset*の引数**SQLExtendedFetch**とき**SQLFetchScroll**は、後で、アプリケーションによって呼び出されます。<br />-ODBC 3 でのアプリケーション設定この*.x*ドライバー、ODBC 3*.x*ドライバー マネージャーがドライバーに呼び出しを渡します。|  
|SQL_ATTR_ROW_STATUS_PTR|行の状態配列へのポインターがで埋められた**SQLFetch**、 **SQLFetchScroll**、 **SQLBulkOperations**、および**SQLSetPos**です。 実装の詳細を次に示します。<br /><br /> 場合、アプリケーション設定この ODBC 2 でします。*x*ドライバー、ODBC 3*.x*ドライバー マネージャーがその値をキャッシュします。 この値は、ODBC 2 を渡します。*x*内のドライバー、 *RowStatusArray*の引数**SQLExtendedFetch**とき**SQLFetchScroll**または**SQLFetch**と呼びます。<br />-ODBC 3 でのアプリケーション設定この*.x*ドライバー、ODBC 3*.x*ドライバー マネージャーがドライバーに呼び出しを渡します。<br />状態 S6、アプリケーション SQL_ATTR_ROW_STATUS_PTR を設定するを呼び出す場合に**SQLBulkOperations** (で、*操作*SQL_ADD の) または**SQLSetPos**最初呼び出さず**SQLFetch**または**SQLFetchScroll**、SQLSTATE HY011 (属性はここで設定することはできません) が返されます。|  
|SQL_ATTR_ROWS_FETCHED_PTR|バッファーを指す**SQLFetch**と**SQLFetchScroll**フェッチされた行の数を返します。 実装の詳細を次に示します。<br /><br /> 場合、アプリケーション設定この ODBC 2 でします。*x*ドライバー、ODBC 3*.x*ドライバー マネージャーがその値をキャッシュします。 この値は、ODBC 2 を渡します。*x*内のドライバー、 *RowCountPtr*の引数**SQLExtendedFetch**とき**SQLFetch**または**SQLFetchScroll**はアプリケーションによって呼び出されます。<br />-ODBC 3 でのアプリケーション設定この*.x*ドライバー、ODBC 3*.x*ドライバー マネージャーがドライバーに呼び出しを渡します。|  
|SQL_ATTR_ROW_ARRAY_SIZE|行セットのサイズを設定します。 実装の詳細を次に示します。<br /><br /> 場合、アプリケーション設定この ODBC 2 でします。*x*ドライバー、ODBC 3*.x*ドライバー マネージャーが SQL_ROWSET_SIZE ステートメント属性にマップします。<br />-ODBC 3 でのアプリケーション設定この*.x*ドライバー、ODBC 3*.x*ドライバー マネージャーがドライバーに呼び出しを渡します。<br />場合、ODBC 3 を使用するアプリケーション*.x*ドライバー呼び出し**SQLSetScrollOptions**、SQL_ROWSET_SIZE がの値に設定されている、*複合カーソル*引数場合、基になります。ドライバーがサポートしていません**SQLSetScrollOptions**です。|  
|SQL_ROWSET_SIZE|によって使用される行セット サイズ設定**SQLExtendedFetch**とき**SQLExtendedFetch** ODBC 2 によって呼び出される*.x*アプリケーションです。 実装の詳細を次に示します。<br /><br /> -アプリケーションが、これを設定する ODBC 3*.x*ドライバー マネージャーがドライバーのバージョンに関係なく、ドライバーに呼び出しを渡します。<br />-場合、アプリケーションが ODBC 2 を使用します。*x*ドライバー呼び出し**SQLSetScrollOptions**、SQL_ROWSET_SIZE がの値に設定されている、**複合カーソル**引数。|  
|**SQLBulkOperations**|Insert 操作、または update、delete、またはブックマーク操作によってフェッチを実行します。 実装の詳細を次に示します。<br /><br /> のアプリケーションを呼び出すと**SQLBulkOperations**で、*操作*の ODBC 2 で SQL_ADD *。x*ドライバー、ODBC 3*.x*ドライバー マネージャーにマップ**SQLSetPos**で、*操作*SQL_ADD のです。<br />場合、ODBC 2 を使用します。*x*ドライバーをサポートしない**SQLSetPos**で、*操作*SQL_ADD、ODBC 3 の*.x*ドライバー マネージャーががマップされていない**SQLSetPos**で、*操作*に SQL_ADD の**SQLBulkOperations**で、*操作*SQL_ADD のです。 これは、ため**SQLBulkOperations**状態 S7、どの ODBC 2 では呼び出すことはできません*。x*を唯一の状態が**SQLSetPos**呼び出すことができます。<br />場合は、アプリケーションが呼び出す**SQLBulkOperations**で、*操作*ODBC 2 で SQL_ADD の*。x*呼び出す前にドライバー **SQLFetchScroll**、ODBC 3*.x*ドライバー マネージャーでエラーが返されます。|  
|**SQLExtendedFetch**|指定した行セットを返します。 ODBC 3 示した、制限を除き*.x*ドライバー マネージャーへの呼び出しに渡します**SQLExtendedFetch**ドライバーのバージョンに関係なく、ドライバーにします。|  
|**SQLFetch**|次の行セットを返します。 実装の詳細を次に示します。<br /><br /> のアプリケーションを呼び出すと**SQLFetch** ODBC 2 *。x*ドライバー、ODBC 3*.x*ドライバー マネージャーにマップ**SQLExtendedFetch**です。 *FetchOrientation*の引数**SQLExtendedFetch** SQL_FETCH_NEXT に設定されています。 ドライバー マネージャーが、SQL_ATTR_ROW_STATUS_PTR ステートメント属性用のキャッシュされた値を使用して、 *RowStatusArray*引数と SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性のキャッシュされた値、 *RowCountPtr*引数。<br />ODBC 3*.x*への呼び出しを混在させることがアプリケーション**SQLFetch**と**SQLFetchScroll** ODBC 2 *。x*ドライバーのため ODBC 3*.x*ドライバー マネージャー マップ**SQLFetch**に**SQLExtendedFetch**アプリケーションを呼び出すと、ODBC 2 *。x*ドライバー。<br />場合は ODBC 2 です。*x*ドライバーがサポートしていません**SQLExtendedFetch**、ODBC 3*.x*ドライバー マネージャーがマップされていない**SQLFetch**または**SQLFetchScroll**に**SQLExtendedFetch**アプリケーションを呼び出すと、そのドライバーにします。 アプリケーションが、SQL_ATTR_ROW_ARRAY_SIZE を 1、SQLSTATE HYC00 より大きい値に設定しようとしています。 場合 (省略可能な機能が実装されていません) が返されます。<br />-以外の前述の制限だけ、ODBC 3*.x*ドライバー マネージャーへの呼び出しに渡します**SQLFetch**ドライバーのバージョンに関係なく、ドライバーにします。|  
|**SQLFetchScroll**|指定した行セットを返します。 実装の詳細を次に示します。<br /><br /> のアプリケーションを呼び出すと**SQLFetchScroll** ODBC 2 *。x*ドライバー、ODBC 3*.x*ドライバー マネージャーにマップ**SQLExtendedFetch**です。 SQL_ATTR_ROW_STATUS_PTR ステートメント属性のキャッシュされた値を使用して、 *RowStatusArray*引数と SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性のキャッシュされた値、 *RowCountPtr*引数。 場合、 *FetchOrientation*引数**SQLFetchScroll** sql_fetch_bookmark を指定しては、SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性のキャッシュされた値を使用して、 *FetchOffset*引数エラーを返す場合、 *FetchOffset*の引数**SQLFetchScroll**が 0 ではありません。<br />-アプリケーションを呼び出すとこの ODBC 3*.x*ドライバー、ODBC 3*.x*ドライバー マネージャーがドライバーに呼び出しを渡します。|  
|**SQLSetPos**|さまざまな位置指定操作を実行します。 ODBC 3*.x*ドライバー マネージャーへの呼び出しに渡します**SQLSetPos**ドライバーのバージョンに関係なく、ドライバーにします。|  
|**SQLSetScrollOptions**|ドライバー マネージャーのマップと**SQLSetScrollOptions** ODBC 3 を使用するアプリケーションの*.x*ドライバーをサポートしない**SQLSetScrollOptions**、ドライバーマネージャーに SQL_ROWSET_SIZE ステートメントのオプション、not、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を設定、*複合カーソル*引数**SQLSetScrollOption**です。 その結果、 **SQLSetScrollOptions**への呼び出しによって複数の行をフェッチするときに、アプリケーションでは使用できません**SQLFetch**または**SQLFetchScroll**です。 フェッチの複数の行への呼び出しによって場合にのみ使用できます**SQLExtendedFetch**です。|
