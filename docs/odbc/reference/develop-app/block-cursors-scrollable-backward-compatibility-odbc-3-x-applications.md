---
title: "ブロックや ODBC の互換性のスクロール可能なカーソル 3.x |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- SQLExtendedFetch function [ODBC], block cursors
- cursors [ODBC], compatibility issues
- SQLFetchScroll function [ODBC], block cursors
ms.assetid: 82f6cf68-cfde-4417-9788-d6382ca14bf8
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 56543f0de0d95bad6fa85fc415dddd7da58f3667
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>ブロック カーソル、スクロール可能なカーソル、および ODBC 3.x アプリケーションの旧バージョンとの互換性
両方の存在**SQLFetchScroll**と**SQLExtendedFetch** ODBC の間で、アプリケーション プログラミング インターフェイス (API)、これは、一連の関数の最初のクリアが分割を表します、アプリケーションの呼び出し、およびサービス プロバイダー インターフェイス (SPI) の関数のセットからなるドライバーを実装します。 この分割は、ODBC 3 要件のバランスをとる必要があります。*x*が使用される**SQLFetchScroll**と位置を合わせたり、標準の ODBC 2 と互換性がある*。x*が使用される**SQLExtendedFetch**です。  
  
 ODBC 3*.x*は API のセットがアプリケーションの呼び出しの機能にも含まれます**SQLFetchScroll**に関連するステートメント属性とします。 ODBC 3*.x*セットからなる SPI 関数のドライバーを実装して、含まれています**SQLFetchScroll**、 **SQLExtendedFetch**、関連するステートメント属性とします。 ODBC は、API と SPI がこのような単位に分割を正式には適用しません、ため、ODBC 3 可能性が*.x*アプリケーションを呼び出す**SQLExtendedFetch**に関連するステートメント属性とします。 ただし、ODBC 3 の理由はありません*.x*これを行うアプリケーション。 Api および Spi の詳細については、の紹介」を参照してください。 [ODBC アーキテクチャ](../../../odbc/reference/odbc-architecture.md)です。  
  
 方法については、ODBC 3 です。*x*ドライバー マネージャーは、ODBC 2 への呼び出しをマップします*。x*および ODBC 3 *。x*ドライバー、およびどのような関数とステートメント属性 ODBC 3 *。x*ドライバーがブロックとスクロール可能なカーソルを実装する必要がありますを参照してください[、ドライバーが何](../../../odbc/reference/appendixes/what-the-driver-does.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。  
  
 次の表に、どのような関数とステートメントは、ODBC 3 を属性します。*x*アプリケーションは、ブロックとスクロール可能なカーソルを使用する必要があります。 また、ODBC 2 の間の変更も表示されます。*x*および ODBC 3 *。x*この領域で、ODBC 3 *。x*アプリケーションは ODBC 2 と互換性があることを認識する必要があります*。x*ドライバー。  
  
|関数または<br /><br /> ステートメント属性|コメント|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|使用する、ブックマークを指す**SQLFetchScroll**です。<br /><br /> 設定した場合、アプリケーションこの ODBC 2 でします。*x*ドライバー、固定長のブックマークへポイントこの必要があります。|  
|SQL_ATTR_ROW_STATUS_PTR|行の状態配列へのポインターがで埋められた**SQLFetch**、 **SQLFetchScroll**、 **SQLBulkOperations**、および**SQLSetPos**です。<br /><br /> 場合は、アプリケーションは、ODBC 2 でこれを設定します。*x*ドライバーと呼び出し**SQLBulkOperation**で、*操作*呼び出す前に SQL_ADD の**SQLFetchScroll**、 **SQLFetch**、または**SQLExtendedFetch**、SQLSTATE HY011 (属性はここで設定することはできません) が返されます。<br /><br /> アプリケーションを呼び出すと**SQLFetch** ODBC 2 *。x*ドライバー、 **SQLFetch**にマップされて**SQLExtendedFetch**したがってこの配列の値を返します。|  
|SQL_ATTR_ROWS_FETCHED_PTR|バッファーを指す**SQLFetch**と**SQLFetchScroll**フェッチされた行の数を返します。<br /><br /> アプリケーションを呼び出すと**SQLFetch** ODBC 2 *。x*ドライバー、 **SQLFetch**にマップされて**SQLExtendedFetch**したがってこのバッファーに値を返します。|  
|SQL_ATTR_ROW_ARRAY_SIZE|行セットのサイズを設定します。<br /><br /> アプリケーションを呼び出す場合**SQLBulkOperations**で、*操作*の ODBC 2 で SQL_ADD *。x*への呼び出しがマップされているためできません SQL_ATTR_ROW_ARRAY_SIZE を呼び出しに使用するドライバー、SQL_ROWSET_SIZE **SQLSetPos**で、*操作*SQL_ADD を使用してのSQL_ROWSET_SIZE です。<br /><br /> 呼び出す**SQLSetPos**で、*操作*SQL_ADD のまたは**SQLExtendedFetch** odbc 2 *。x*ドライバーは SQL_ROWSET_SIZE を使用します。<br /><br /> 呼び出す**SQLFetch**または**SQLFetchScroll** odbc 2 *。x*ドライバーは、SQL_ATTR_ROW_ARRAY_SIZE を使用します。|  
|**SQLBulkOperations**|Insert およびブックマークの操作を実行します。 ときに**SQLBulkOperations**で、*操作*SQL_ADD は、ODBC 2 で呼び出されます*。x*ドライバーにマップされている**SQLSetPos**で、*操作*SQL_ADD のです。 実装の詳細を次に示します。<br /><br /> 場合、ODBC 2 を使用します。*x*ドライバー、アプリケーションに関連付けられた暗黙的に割り当てられた ARD のみを使用する必要があります、 *StatementHandle*; 明示的な記述子の操作があるためには、行を追加する別の ARD が割り当てることができませんODBC 2 ではサポートされていません。*x*ドライバー。 アプリケーションを使用する必要があります**SQLBindCol**されません、ARD にバインドする**SQLSetDescField**または**SQLSetDescRec**です。<br />、ODBC 3 を呼び出すときにします。*x*ドライバー、アプリケーションが呼び出すことができます**SQLBulkOperations**で、*操作*呼び出す前に SQL_ADD の**SQLFetch**または**SQLFetchScroll**です。 ODBC 2 を呼び出すとき。*x*ドライバー、アプリケーションを呼び出す必要があります**SQLFetchScroll**呼び出す前に**SQLBulkOperations**操作の SQL_ADD とします。|  
|**SQLFetch**|次の行セットを返します。 実装の詳細を次に示します。<br /><br /> のアプリケーションを呼び出すと**SQLFetch** ODBC 2 *。x*ドライバーにマップされている**SQLExtendedFetch**です。<br />のアプリケーションを呼び出すと**SQLFetch** ODBC 3 *。x*ドライバー、その行数を返します、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を使って指定します。|  
|**SQLFetchScroll**|指定した行セットを返します。 実装の詳細を次に示します。<br /><br /> のアプリケーションを呼び出すと**SQLFetchScroll** ODBC 2 *。x*ドライバー、SQLSTATE 01S01 を返します (行がエラーの) 1 つの行に適用される各エラーの前にします。 これは、だけであるため、ODBC 3*.x*ドライバー マネージャーをマップする**SQLExtendedFetch**と**SQLExtendedFetch**この SQLSTATE を返します。 アプリケーションを呼び出すと**SQLFetchScroll** ODBC 3 *。x*ドライバー、決して返します SQLSTATE 01S01 (行でエラー)。<br />のアプリケーションを呼び出すと**SQLFetchScroll** ODBC 2 *。x*ドライバーと*FetchOrientation*に sql_fetch_bookmark を指定して、設定、 *FetchOffset*引数を 0 に設定する必要があります。 SQLSTATE HYC00 ODBC 2 オフセットに基づくブックマークをフェッチが実行されると (省略可能な機能が実装されていません) が返されます。*x*ドライバー。|  
  
> [!NOTE]  
>  ODBC 3 です。*x*アプリケーションを使用しないでください**SQLExtendedFetch**または SQL_ROWSET_SIZE ステートメント属性。 代わりに、使用する必要があります**SQLFetchScroll**および SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性。 ODBC 3 です。*x*アプリケーションを使用しないでください**SQLSetPos**で、*操作*SQL_ADD の使用する必要がありますが、 **SQLBulkOperations** で*操作*SQL_ADD のです。

