---
title: "SQLFetchScroll (カーソル ライブラリ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SQLFetchScroll function [ODBC], Cursor Library
ms.assetid: 4417e57c-31dd-475e-8fe9-eab00a459c80
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7e864cf48e199f414d4cb012c5513be0fc844820
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlfetchscroll-cursor-library"></a>SQLFetchScroll (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないように、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLFetchScroll**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLFetchScroll**を参照してください[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)です。  
  
 カーソル ライブラリを実装する**SQLFetchScroll**を繰り返し呼び出して**SQLFetch**ドライバーにします。 データ転送、ドライバーからアプリケーションによって提供される行セットのバッファーを取得します。 また、メモリやディスク ファイルにデータをキャッシュします。 アプリケーションの新しい行セットを要求するとき、カーソル ライブラリ取得 (これは以前まだフェッチされていない) 場合、ドライバーまたはキャッシュから必要に応じて、(以前フェッチした) 場合します。 最後に、カーソル ライブラリは、キャッシュされたデータの状態を保持し、行の状態配列内のアプリケーションにこの情報を返します。  
  
 カーソル ライブラリを使用する場合を呼び出す**SQLFetchScroll**いずれかへの呼び出しを混在させることはできません**SQLFetch**または**SQLExtendedFetch**です。  
  
 カーソル ライブラリを使用する場合を呼び出す**SQLFetchScroll**は ODBC 2 の両方をサポートします*。x* 、ODBC 3 *。x*ドライバー。  
  
## <a name="rowset-buffers"></a>バッファーの行セット  
 カーソル ライブラリは、ドライバーから場合に、アプリケーションによって提供される行セット バッファーへのデータの転送を最適化します。  
  
-   アプリケーションでは、行方向のバインドを使用します。  
  
-   アプリケーションを 1 行のデータを保持するために宣言する構造体のフィールドの間で使用されていないバイトはありません。  
  
-   これでフィールド**SQLFetch**または**SQLFetchScroll**長さ/インジケーター列がその列に対してバッファーに依存して、[次へ] の列に対してバッファーの前のデータを返します。 これらのフィールドは省略可能です。  
  
 アプリケーションの新しい行セットを要求するとき、カーソル ライブラリは、必要に応じて、ドライバーとそのキャッシュからデータを取得します。 新規および既存の行セットが重なっている場合、カーソル ライブラリは、行セットのバッファーの重複する部分からデータを再利用してそのパフォーマンスを最適化できます。 したがって、ない場合は、新旧の行セットの重複は行セットのバッファーの重複するセクションでは、変更は、行セットのバッファーに保存されていない変更は失われます。 変更を保存するには、アプリケーションは、位置指定の update ステートメントを送信します。  
  
 アプリケーションを呼び出すと、カーソル ライブラリがそのキャッシュからのデータを行セットのバッファーを常に更新される注**SQLFetchScroll**で、 *FetchOrientation*引数 SQL_FETCH_RELATIVE に設定し、*FetchOffset*引数を 0 に設定されています。  
  
 カーソル ライブラリ呼び出しをサポートする**SQLSetStmtAttr**で、*属性*カーソルが開いている間、行セットのサイズを変更する sql_attr_row_array_size を指定します。 新しい行セットのサイズを反映次回**SQLFetchScroll**と呼びます。  
  
## <a name="result-set-membership"></a>結果セットのメンバーシップ  
 カーソル ライブラリは、アプリケーションを要求する場合にのみ、ドライバーからデータを取得します。 このデータ ソースとに応じて SQL_CONCURRENCY ステートメント属性の設定、次のような影響があります。  
  
-   カーソル ライブラリによって取得されるデータは、ステートメントの実行時に使用したデータから異なる場合があります。 たとえば、カーソルを開いた後に現在のカーソル位置より後ろに挿入された行をいくつかのドライバーによって取得できます。  
  
-   結果セット内のデータは、カーソル ライブラリのデータ ソースによってロックされている可能性があり、ために他のユーザーに利用できません。  
  
 カーソル ライブラリには、データの行がキャッシュされた後、基になるデータ ソース (位置指定更新および削除が、同じカーソルのキャッシュで動作している) を除くその行に対する変更を検出できません。 これは、呼び出しのために**SQLFetchScroll**、カーソル ライブラリは、データ ソースからデータを決して変わりません。 代わりに、そのキャッシュからデータを変わりません。  
  
## <a name="scrolling"></a>スクロール  
 カーソル ライブラリで次のフェッチの種類をサポートしている**SQLFetchScroll**です。  
  
|カーソルの種類|フェッチの種類|  
|-----------------|-----------------|  
|順方向専用|SQL_FETCH_NEXT|  
|静的|SQL_FETCH_NEXT<br /><br /> SQL_FETCH_PRIOR<br /><br /> SQL_FETCH_FIRST<br /><br /> SQL_FETCH_LAST<br /><br /> SQL_FETCH_RELATIVE<br /><br /> SQL_FETCH_ABSOLUTE<br /><br /> SQL_FETCH_BOOKMARK|  
  
## <a name="errors"></a>エラー  
 ときに**SQLFetchScroll**が呼び出されたへの呼び出しのいずれかと**SQLFetch** SQL_ERROR、カーソル ライブラリが実行を次のように返します。 次の手順が完了すると、カーソル ライブラリの処理が続行されます。  
  
1.  呼び出し**SQLGetDiagRec**ドライバーからエラー情報を取得し、これをドライバー マネージャーでの診断レコードとしてポストします。  
  
2.  適切な値に診断レコードの SQL_DIAG_ROW_NUMBER フィールドを設定します。  
  
3.  SQL_DIAG_COLUMN_NUMBER フィールド レコード内の設定、診断、適切な値に該当する場合です。それ以外の場合、これを 0 に設定します。  
  
4.  SQL_ROW_ERROR 行の状態配列内のエラーの行の値を設定します。  
  
 カーソルより後ライブラリと呼ばれる**SQLFetch**の実装で複数回**SQLFetchScroll**、エラーまたは警告への呼び出しのいずれかによって返される**SQLFetch**診断レコードになり、への呼び出しによって取得できる**SQLGetDiagRec**です。 場合は、フェッチされたときに、データが切り捨てられました、切り捨てられたデータは、カーソル ライブラリのキャッシュに現在存在します。 後続の呼び出し**SQLFetchScroll**を持つ行にスクロールする切り捨てられたデータが切り捨てられたデータを返すし、カーソル ライブラリのキャッシュからのデータをフェッチするための警告は発生しません。 バッファーに返されるデータが切り捨てられているかどうかを決定できるように返されるデータの長さを追跡するため、アプリケーションは長さ/インジケーター バッファーをバインドする必要があります。  
  
## <a name="bookmark-operations"></a>ブックマークの操作  
 カーソル ライブラリ呼び出しをサポートする**SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_BOOKMARK のです。 内のオフセットを指定することもサポート、 *FetchOffset*ブックマーク操作で使用できる引数。 これは、カーソル ライブラリがサポートされる唯一のブックマーク操作です。 カーソル ライブラリには、呼び出すことはできません。 **SQLBulkOperations**です。  
  
 場合は、アプリケーションでは、SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定され、ブックマーク列にバインドが、カーソル ライブラリは固定長のブックマークを生成し、アプリケーションに返します。 カーソル ライブラリを作成し、; を使用して、それらのブックマークの保持これは、データ ソースで保存されているブックマークには使用されません。 ときに**SQLFetchScroll**が呼び出されたカーソル ライブラリのキャッシュからデータを取得、データ ソースから既にフェッチされているデータのブロックを取得します。 ブックマークがへの呼び出しで使用されるため、 **SQLFetchScroll**で、 *FetchOrientation*の sql_fetch_bookmark を指定してを作成し、カーソル ライブラリで保持されている必要があります。  
  
## <a name="interaction-with-other-functions"></a>その他の機能とのやり取り  
 アプリケーションを呼び出す必要があります**SQLFetch**または**SQLFetchScroll**更新または delete ステートメントでそれを準備または実行する前に配置されているいずれか。
