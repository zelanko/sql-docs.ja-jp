---
title: ODBC 3.x のブロックおよびスクロール可能なカーソルの互換性 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c526eff6e19014c923f05ad91551a7d7c66f5294
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306343"
---
# <a name="block-cursors-scrollable-cursors-and-backward-compatibility-for-odbc-3x-applications"></a>ODBC 3.x アプリケーション用のブロック カーソル、スクロール可能なカーソル、および下位互換性
**SQLFetchScroll**と**SQLExtendedFetch**の両方の存在は、アプリケーション プログラミング インターフェイス (API) の間の ODBC で最初の明確な分割を表します。アプリケーションが呼び出す関数のセットであるサービス プロバイダー インターフェイス (SPI) は、ドライバーが実装する関数のセットです。 この分割は **、SQLFetchScroll**を使用する ODBC *3.x*の要件のバランスをとり、標準に合わせて **、SQLExtendedFetch**を使用する ODBC *2.x*と互換性を持つために必要です。  
  
 ODBC *3.x* API は、アプリケーションが呼び出す関数のセットであり **、SQLFetchScroll**および関連するステートメント属性を含みます。 ODBC *3.x* SPI は、ドライバーが実装する関数のセットであり **、SQLFetchScroll** **、SQLExtendedFetch**、および関連するステートメント属性を含みます。 ODBC では、API と SPI の間でこの分割が正式に強制されないため、ODBC *3.x*アプリケーションが**SQLExtendedFetch**および関連するステートメント属性を呼び出すことができます。 ただし、ODBC *3.x*アプリケーションがこれを行う理由はありません。 API と SIS の詳細については、「 ODBC[アーキテクチャ](../../../odbc/reference/odbc-architecture.md)の概要 」を参照してください。  
  
 ODBC *3.x*ドライバー マネージャーは、ODBC *2.x*と ODBC *3.x*ドライバーへの呼び出しをマップする方法、および ODBC *3.x*ドライバーが実装する関数とステートメント属性、ブロックおよびスクロール可能なカーソルについては、「付録 G: 下位互換性のためのドライバーのガイドライン」の「ドライバー[の動作」](../../../odbc/reference/appendixes/what-the-driver-does.md)を参照してください。  
  
 次の表は、ODBC *3.x*アプリケーションがブロックカーソルとスクロール可能カーソルで使用する関数およびステートメント属性をまとめたものです。 ODBC *2.x*と ODBC *2.x*のドライバーと互換性のある ODBC *3.x*アプリケーションに注意する必要があるこの領域の ODBC 2.x と ODBC *3.x*の間の変更も一覧表示します。  
  
|機能または<br /><br /> ステートメント属性|説明|  
|-----------------------------------------|--------------|  
|SQL_ATTR_FETCH_BOOKMARK_PTR|**SQLFetchScroll**で使用するブックマークへのポイント。<br /><br /> アプリケーションが ODBC *2.x*ドライバーでこれを設定する場合、これは固定長のブックマークを指す必要があります。|  
|SQL_ATTR_ROW_STATUS_PTR|**SQL フェッチ、SQL****フェッチスクロール、SQLBulk****操作**、および**SQLSetPos**で埋められた行の状態配列へのポイント。<br /><br /> アプリケーションが ODBC *2.x*ドライバーでこれを設定し、呼び出す前に SQL_ADD の*操作*を使用して**SQLBulkOperation**を呼び出した場合 **、 SQLFetchScroll** **、SQLFetch**、または**SQLExtendedFetch**を呼び出す前に、SQLSTATE HY011 (属性を設定できません) が返されます。<br /><br /> アプリケーションが ODBC *2.x*ドライバーで**SQLFetch**を呼び出すと **、SQLFetch**は**SQLExtendedFetch**にマップされ、したがって、この配列の値を返します。|  
|SQL_ATTR_ROWS_FETCHED_PTR|フェッチされた行数**を返す****バッファー**へのポイント。<br /><br /> アプリケーションが ODBC *2.x*ドライバーで**SQLFetch**を呼び出すと **、SQLFetch**は**SQLExtendedFetch**にマップされ、したがって、このバッファー内の値を返します。|  
|SQL_ATTR_ROW_ARRAY_SIZE|行セットのサイズを設定します。<br /><br /> アプリケーションが ODBC *2.x*ドライバーで*SQL_ADD操作を*使用して**SQLBulkOperations**を呼び出した場合、呼び出 SQL_ATTR_ROW_ARRAY_SIZEしはSQL_ROWSET_SIZEを使用する SQL_ADD の*操作*で**SQLSetPos**にマップされるため、SQL_ROWSET_SIZE呼び出しに使用されます。<br /><br /> ODBC *2.x*ドライバーでの SQL_ADD または**SQLExtendedFetch**の*操作*を使用して**SQLSetPos**を呼び出すと、SQL_ROWSET_SIZEが使用されます。<br /><br /> ODBC *2.x*ドライバーで**SQL フェッチ**または**SQL フェッチスクロール**を呼び出すと、SQL_ATTR_ROW_ARRAY_SIZEが使用されます。|  
|**オペレーション**|挿入およびブックマーク操作を実行します。 ODBC *2.x*ドライバでSQL_ADD*操作*を伴う**SQLBulkOperations**が呼び出されると、SQL_ADDの*操作*で**SQLSetPos**にマップされます。 実装の詳細を次に示します。<br /><br /> - ODBC *2.x*ドライバを使用する場合、アプリケーションは *、StatementHandle*に関連付けられた暗黙的に割り当てられた ARD のみを使用する必要があります。明示的な記述子操作は ODBC *2.x*ドライバーではサポートされていないため、行を追加するために別の ARD を割り当てることはできません。 アプリケーションは **、SQLBindCol**を使用して **、SQLSetDescField**または**SQLSetDescRec**ではなく、ARD にバインドする必要があります。<br />- ODBC *3.x*ドライバーを呼び出すとき、アプリケーションは **、SQLFetch**または**SQLFetchScroll**を呼び出す前に、SQL_ADD*の操作*を使用して**SQLBulkOperations を**呼び出すことができます。 ODBC *2.x*ドライバーを呼び出すとき、アプリケーションは、SQL_ADDの操作を使用して**SQLBulkOperations**を呼び出す前に**SQLFetchScroll**を呼び出す必要があります。|  
|**SQLFetch**|次の行セットを返します。 実装の詳細を次に示します。<br /><br /> - アプリケーションが ODBC *2.x*ドライバーで**SQLFetch**を呼び出すと、SQLExtendedFetch にマップされます。 **SQLExtendedFetch**<br />- アプリケーションが ODBC *3.x*ドライバーで**SQLFetch**を呼び出すと、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性で指定された行数を返します。|  
|**SQLFetchScroll**|指定された行セットを返します。 実装の詳細を次に示します。<br /><br /> - アプリケーションが ODBC *2.x*ドライバーで**SQLFetchScroll**を呼び出すと、1 つの行に適用される各エラーの前に SQLSTATE 01S01 (行のエラー) を返します。 これは、ODBC *3.x*ドライバー マネージャーが**SQLExtendedFetch**にマップし **、SQLExtendedFetch**がこの SQLSTATE を返すためだけこれを行います。 アプリケーションが ODBC *3.x*ドライバーで**SQLFetchScroll**を呼び出すと、SQLSTATE 01S01 (行内エラー) を返すことはありません。<br />- アプリケーションが、フェッチ*オリエンテーションが*SQL_FETCH_BOOKMARKに設定された ODBC *2.x*ドライバーで**SQLFetchScroll**を呼び出す場合は、*引数 FetchOffset*を 0 に設定する必要があります。 ODBC *2.x*ドライバを使用してオフセットベースのブックマークの取得を試行すると、SQLSTATE HYC00 (オプション機能は実装されていません) が返されます。|  
  
> [!NOTE]  
>  ODBC *3.x*アプリケーションでは **、SQLExtendedFetch**またはSQL_ROWSET_SIZE ステートメント属性を使用しないでください。 代わりに **、SQLFetchScroll**とSQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を使用する必要があります。 ODBC *3.x*アプリケーションでは **、sqlSetPos**をSQL_ADD*操作*で使用しないでくださいが、SQL_ADDの*操作*で**SQLBulkOperations**を使用する必要があります。
