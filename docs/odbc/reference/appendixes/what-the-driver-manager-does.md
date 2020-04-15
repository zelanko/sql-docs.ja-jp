---
title: ドライバー マネージャーの機能 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC], backward compatibility
- compatibility [ODBC], driver manager
- ODBC driver manager [ODBC]
- backward compatibility [ODBC], driver manager
ms.assetid: 57f65c38-d9ee-46c8-9051-128224a582c6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 07ab0784e6f6ad4487a02a179a5fa3be2617c930
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306563"
---
# <a name="what-the-driver-manager-does"></a>ドライバー マネージャーの機能
次の表は、ODBC *3.x*ドライバー マネージャーは、ODBC *2.x*と ODBC *3.x*ドライバーに呼び出しをマップする方法をまとめます。  
  
|機能または<br /><br /> ステートメント属性|説明|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|**SQLFetchScroll**で使用するブックマークへのポイント。 実装の詳細を次に示します。<br /><br /> - アプリケーションが ODBC *2.x*ドライバーでこれを設定すると、ODBC *3.x*ドライバー マネージャーは、それをキャッシュします。 このメソッドは、後でアプリケーションから**SQLFetchScroll**が呼び出されたときに、ポインターを逆参照し **、SQLExtendedFetch** *の引数の*ODBC *2.x*ドライバーに値を渡します。<br />- アプリケーションが ODBC *3.x*ドライバーでこれを設定すると、ODBC *3.x*ドライバー マネージャーは、ドライバーに呼び出しを渡します。|  
|SQL_ATTR_ROW_STATUS_PTR|**SQL フェッチ、SQL****フェッチスクロール、SQLBulk****操作**、および**SQLSetPos**で埋められた行の状態配列へのポイント。 実装の詳細を次に示します。<br /><br /> - アプリケーションが ODBC *2.x*ドライバーでこれを設定すると、ODBC *3.x*ドライバー マネージャーは、その値をキャッシュします。 この値は **、SQLFetchScroll**または**SQLFetch**が呼び出されたときに **、SQLExtendedFetch**の*行状態配列*引数の ODBC *2.x*ドライバーに渡されます。<br />- アプリケーションが ODBC *3.x*ドライバーでこれを設定すると、ODBC *3.x*ドライバー マネージャーは、ドライバーに呼び出しを渡します。<br />- 状態 S6 では、アプリケーションがSQL_ATTR_ROW_STATUS_PTRを設定し **、SQLBulkOperations**を呼び出した場合 *(SQL_ADD操作*を使用して) または**SQLSFetchScroll**を最初に呼び出さずに**SQLSetPos**を呼び出すと、SQLSTATE HY011 (属性を設定できません) が返されます。 **SQLFetchScroll**|  
|SQL_ATTR_ROWS_FETCHED_PTR|フェッチされた行数**を返す****バッファー**へのポイント。 実装の詳細を次に示します。<br /><br /> - アプリケーションが ODBC *2.x*ドライバーでこれを設定すると、ODBC *3.x*ドライバー マネージャーは、その値をキャッシュします。 この値は、アプリケーションによって SQLFetch または**SQLFetchScroll**が呼び出**されたときに、SQLExtendedFetch**の*引数の ODBC* *2.x*ドライバーに渡します。 **SQLFetch**<br />- アプリケーションが ODBC *3.x*ドライバーでこれを設定すると、ODBC *3.x*ドライバー マネージャーは、ドライバーに呼び出しを渡します。|  
|SQL_ATTR_ROW_ARRAY_SIZE|行セットのサイズを設定します。 実装の詳細を次に示します。<br /><br /> - アプリケーションが ODBC *2.x*ドライバーでこれを設定すると、ODBC *3.x*ドライバー マネージャーは、SQL_ROWSET_SIZE ステートメント属性にマップします。<br />- アプリケーションが ODBC *3.x*ドライバーでこれを設定すると、ODBC *3.x*ドライバー マネージャーは、ドライバーに呼び出しを渡します。<br />- ODBC *3.x*ドライバーを使用して動作するアプリケーションが**SQLSetScrollOptions**を呼び出すと、基になるドライバーが**SQLSetScrollOptions**をサポートしていない場合、SQL_ROWSET_SIZEは*RowsetSize*引数の値に設定されます。|  
|SQL_ROWSET_SIZE|ODBC *2.x*アプリケーションによって**SQLExtendedFetch**が呼び出されたときに **、SQLExtendedFetch**によって使用される行セットのサイズを設定します。 実装の詳細を次に示します。<br /><br /> - アプリケーションがこれを設定すると、ODBC *3.x*ドライバー マネージャーは、ドライバーのバージョンに関係なく、ドライバーに呼び出しを渡します。<br />- ODBC *2.x*ドライバーを使用するアプリケーションが**SQLSetScrollOptions**を呼び出すと、SQL_ROWSET_SIZEは**RowsetSize**引数の値に設定されます。|  
|**オペレーション**|ブックマーク操作による挿入操作、または更新、削除、または取得を実行します。 実装の詳細を次に示します。<br /><br /> - アプリケーションが ODBC *2.x*ドライバーでSQL_ADDの*操作*を使用して**SQLBulkOperations**を呼び出すと、ODBC *3.x*ドライバー マネージャーは、SQL_ADDの*操作*を使用して**SQLSetPos**にマップします。<br />- SQL_ADD*の操作*で**SQLSetPos**をサポートしていない ODBC *2.x*ドライバーを操作する場合、ODBC *3.x*ドライバー マネージャーは、SQL_ADDの*操作*を使用して**SQLBulkOperations**にSQL_ADDの*操作*と**SQLSetPos**をマップしません。 これは、ODBC *2.x*で**SQLSetPos**を呼び出すことができる唯一の状態であった状態 S7 で**SQLBulkOperations**を呼び出すことができないためです。<br />- アプリケーションは **、SQLFetchScroll**を呼び出す前に、ODBC *2.x*ドライバーでSQL_ADDの*操作*を使用して**SQLBulkOperations**を呼び出す場合は、ODBC *3.x*ドライバー マネージャーはエラーを返します。|  
|**フェッチ**|指定された行セットを返します。 上記の制限を除き、ODBC *3.x*ドライバー マネージャーは、ドライバーのバージョンに関係なく、ドライバーに**呼**び出しを渡します。|  
|**SQLFetch**|次の行セットを返します。 実装の詳細を次に示します。<br /><br /> - アプリケーションが ODBC *2.x*ドライバーで**SQLFetch**を呼び出すと、ODBC *3.x*ドライバー マネージャーは**SQLExtendedFetch**にマップします。 引数の*フェッチ***は**、SQL_FETCH_NEXTに設定されます。 ドライバー マネージャーは、SQL_ATTR_ROW_STATUS_PTR ステートメント属性のキャッシュ値を使用して *、 RowStatusArray*引数と *、引数の*SQL_ATTR_ROWS_FETCHED_PTRステートメント属性のキャッシュ値をキャッシュします。<br />- ODBC *3.x*アプリケーションは、ODBC 2.x ドライバーで呼び**出すと、** アプリケーションが SQLFetch を**SQLExtendedFetch**にマップ*するため、ODBC* *2.x*ドライバー*2.x*で**SQL フェッチ**と**SQL フェッチスクロール**の呼び出しを混在させることができます。<br />- ODBC *2.x*ドライバーが**SQLExtendedFetch**をサポートしていない場合、ODBC *3.x*ドライバー マネージャーは、アプリケーションがそのドライバーでそれを呼び出すときに**SQLFetch**または**SQLFetchScroll**を**SQLExtendedFetch**にマップしません。 アプリケーションが SQL_ATTR_ROW_ARRAY_SIZEを 1 より大きい値に設定しようとすると、SQLSTATE HYC00 (オプション機能が実装されていません) が返されます。<br />- 上記の制限を除き、ODBC *3.x*ドライバー マネージャーは、ドライバーのバージョンに関係なく、ドライバーに**SQLFetch**への呼び出しを渡します。|  
|**SQLFetchScroll**|指定された行セットを返します。 実装の詳細を次に示します。<br /><br /> - アプリケーションが ODBC *2.x*ドライバーで**SQLFetchScroll**を呼び出すと、ODBC *3.x*ドライバー マネージャーは**SQLExtendedFetch**にマップします。 この引数では *、rowStatusArray*引数に対してSQL_ATTR_ROW_STATUS_PTRステートメント属性のキャッシュ値、および*RowCountPtr*引数のSQL_ATTR_ROWS_FETCHED_PTRステートメント属性のキャッシュ値を使用します。 引数が*SQL_FETCH_BOOKMARK*場合、**引数**は *、fetchOffset*引数にSQL_ATTR_FETCH_BOOKMARK_PTRステートメント属性のキャッシュ値を使用し **、SQLFetchScroll**の*FetchOffset*引数が 0 でない場合はエラーを返します。<br />- アプリケーションが ODBC *3.x*ドライバーでこれを呼び出すと、ODBC *3.x*ドライバー マネージャーは、ドライバーに呼び出しを渡します。|  
|**SQLSetPos**|さまざまな位置指定操作を実行します。 ODBC *3.x*ドライバー マネージャーは、ドライバーのバージョンに関係なく、ドライバーに**SQLSetPos**への呼び出しを渡します。|  
|**スクロールオプション**|ドライバー マネージャーは **、SQLSetScrollOptions**をサポートしていない ODBC *3.x*ドライバーを使用して作業するアプリケーションの**SQLSetScrollOptions**をマップすると、ドライバー マネージャーは、SQL_ATTR_ROW_ARRAY_SIZE ステートメント*RowsetSize*属性ではなく、SQL_ROWSET_SIZE ステートメント**オプションを設定**します。 その結果、SQLFetch または**SQLFetchScroll**の呼び出しによって複数の行をフェッチする場合、アプリケーションで**SQLSetScrollOptions** **を**使用することはできません。 **SQLExtendedFetch**の呼び出しによって複数の行をフェッチする場合にのみ使用できます。|
