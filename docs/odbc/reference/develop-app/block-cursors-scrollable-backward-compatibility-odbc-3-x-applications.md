---
title: ブロックと ODBC のカーソルのスクロール可能な互換性 3.x |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- compatibility [ODBC], cursors
- backward compatibility [ODBC], cursors
- SQLExtendedFetch function [ODBC], block cursors
- cursors [ODBC], compatibility issues
- SQLFetchScroll function [ODBC], block cursors
ms.assetid: 82f6cf68-cfde-4417-9788-d6382ca14bf8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0bc45169a3c5eee2e23f581a66d5232c22e89b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47740316"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>ODBC 3.x アプリケーション用のブロック カーソル、スクロール可能なカーソル、および下位互換性
両方が存在する**SQLFetchScroll**と**SQLExtendedFetch** odbc の間で、アプリケーション プログラミング インターフェイス (API)、一連の関数である最初の平文の分割は、アプリケーションの呼び出し、およびサービス プロバイダー インターフェイス (SPI) 関数のセットである、ドライバーが実装されます。 この分割は、ODBC 3 要件のバランスを取る必要があります。*x*、使用する**SQLFetchScroll**、標準の連携と、ODBC 2 との互換性します *。x*、使用する**SQLExtendedFetch**します。  
  
 ODBC 3 *.x*は API のセットにアプリケーション呼び出しの機能が含まれています**SQLFetchScroll**および関連するステートメント属性。 ODBC 3 *.x* 、SPI は、一連の関数のドライバーを実装して、含まれています**SQLFetchScroll**、 **SQLExtendedFetch**、および関連するステートメント属性。 ODBC は、この分割、API と SPI を正式には適用されません、ため、ODBC 3 のことが *.x*を呼び出すアプリケーション**SQLExtendedFetch**および関連するステートメント属性。 ただし、ODBC 3 の理由はありません *.x*これを行うアプリケーション。 Api および Spi の詳細についてはの概要を参照してください。 [ODBC アーキテクチャ](../../../odbc/reference/odbc-architecture.md)します。  
  
 方法については、ODBC 3。*x*ドライバー マネージャーは、ODBC 2 への呼び出しをマップします *。x*および ODBC 3 *。x*ドライバー、およびどのような関数とステートメント属性を ODBC 3 *。x*ドライバーがブロックとスクロール可能なカーソルを実装する必要がありますを参照してください[、ドライバーが何](../../../odbc/reference/appendixes/what-the-driver-does.md)付録 g: ドライバーとの下位互換性のためのガイドラインにします。  
  
 次の表は、どのような機能をまとめたものです。 ステートメント属性を ODBC 3.*x*ブロックとカーソルのスクロール可能なアプリケーションを使用する必要があります。 ODBC 2 の間での変更も一覧表示されます。*x*および ODBC 3 *。x*この領域で、ODBC 3 *。x* ODBC 2 と互換性があるアプリケーションが認識する必要があります *。x*ドライバー。  
  
|関数または<br /><br /> ステートメント属性|コメント|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|使用したブックマークを指す**SQLFetchScroll**します。<br /><br /> 設定した場合、アプリケーションこれで、ODBC 2。*x*ドライバー、固定長のブックマークをポイントする必要があります。|  
|SQL_ATTR_ROW_STATUS_PTR|埋められた行の状態配列を指す**SQLFetch**、 **SQLFetchScroll**、 **SQLBulkOperations**、および**SQLSetPos**します。<br /><br /> 場合は、アプリケーションでは、ODBC 2 でこれを設定します。*x*ドライバーと呼び出し**SQLBulkOperation**で、*操作*の呼び出しの前に SQL_ADD **SQLFetchScroll**、 **SQLFetch**、または**SQLExtendedFetch**、SQLSTATE HY011 (属性はここで設定することはできません) が返されます。<br /><br /> アプリケーションを呼び出すと**SQLFetch** 、ODBC 2 *。x*ドライバー、 **SQLFetch**にマップされて**SQLExtendedFetch**したがってこの配列の値を返します。|  
|SQL_ATTR_ROWS_FETCHED_PTR|バッファーを指す**SQLFetch**と**SQLFetchScroll**フェッチされた行の数を返します。<br /><br /> アプリケーションを呼び出すと**SQLFetch** 、ODBC 2 *。x*ドライバー、 **SQLFetch**にマップされて**SQLExtendedFetch**したがってこのバッファーに値を返します。|  
|SQL_ATTR_ROW_ARRAY_SIZE|行セットのサイズを設定します。<br /><br /> アプリケーションを呼び出す場合**SQLBulkOperations**で、*操作*SQL_ADD ODBC 2 での *。x*呼び出しにマップされていない SQL_ATTR_ROW_ARRAY_SIZE を呼び出しに使用するドライバー、SQL_ROWSET_SIZE **SQLSetPos**で、*操作*SQL_ADD を使用してのSQL_ROWSET_SIZE します。<br /><br /> 呼び出す**SQLSetPos**で、*操作*SQL_ADD のまたは**SQLExtendedFetch** odbc 2 *。x*ドライバーは SQL_ROWSET_SIZE を使用します。<br /><br /> 呼び出す**SQLFetch**または**SQLFetchScroll** odbc 2 *。x*ドライバーは、SQL_ATTR_ROW_ARRAY_SIZE を使用します。|  
|**SQLBulkOperations**|挿入とブックマークの操作を実行します。 ときに**SQLBulkOperations**で、*操作*SQL_ADD は、ODBC 2 で呼び出されます *。x*にマップされたドライバー、 **SQLSetPos**で、*操作*SQL_ADD の。 次に、実装の詳細を示します。<br /><br /> -場合は、ODBC 2 を使用します。*x*ドライバー、アプリケーションに関連付けられている、暗黙的に割り当てられた ARD のみを使用する必要があります、 *StatementHandle*; ため明示的な記述子の操作は、行を追加するため別 ARD が割り当てることができませんODBC 2 ではサポートされていません。*x*ドライバー。 アプリケーションを使用する必要があります**SQLBindCol**されません、ARD にバインドする**SQLSetDescField**または**SQLSetDescRec**します。<br />ODBC 3 を呼び出すときにします。*x*ドライバー、アプリケーションが呼び出すことができます**SQLBulkOperations**で、*操作*の呼び出しの前に SQL_ADD **SQLFetch**または**SQLFetchScroll**します。 ODBC 2 を呼び出すときにします。*x*ドライバー、アプリケーションが呼び出す必要があります**SQLFetchScroll**呼び出す前に**SQLBulkOperations**操作の SQL_ADD とします。|  
|**SQLFetch**|次の行セットを返します。 次に、実装の詳細を示します。<br /><br /> のアプリケーションを呼び出すと**SQLFetch** 、ODBC 2 *。x*にマップされたドライバー、 **SQLExtendedFetch**します。<br />のアプリケーションを呼び出すと**SQLFetch** 、ODBC 3 *。x* SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性で指定された行の番号を返すドライバー。|  
|**SQLFetchScroll**|指定した行セットを返します。 次に、実装の詳細を示します。<br /><br /> のアプリケーションを呼び出すと**SQLFetchScroll** 、ODBC 2 *。x*ドライバー、SQLSTATE 01S01 を返します (行内のエラー) の 1 行に適用される各エラーの前にします。 だけであるためこれは、ODBC 3 *.x*ドライバー マネージャーをマップする**SQLExtendedFetch**と**SQLExtendedFetch**この SQLSTATE を返します。 アプリケーションを呼び出すと**SQLFetchScroll** 、ODBC 3 *。x*ドライバー、決して返します SQLSTATE 01S01 (行内のエラー)。<br />のアプリケーションを呼び出すと**SQLFetchScroll** 、ODBC 2 *。x*ドライバー *FetchOrientation*に SQL_FETCH_BOOKMARK、設定、 *FetchOffset*引数を 0 に設定する必要があります。 SQLSTATE HYC00 オフセットに基づくブックマークをフェッチしていますが、ODBC 2 試みられると、(省略可能な機能が実装されていません) が返されます。*x*ドライバー。|  
  
> [!NOTE]  
>  ODBC 3。*x*アプリケーションは使用しないでください**SQLExtendedFetch**または SQL_ROWSET_SIZE ステートメントの属性。 代わりに、使用する必要があります**SQLFetchScroll**と SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性。 ODBC 3。*x*アプリケーションは使用しないでください**SQLSetPos**で、*操作*SQL_ADD の使用する必要がありますが、 **SQLBulkOperations** で*操作*SQL_ADD の。
