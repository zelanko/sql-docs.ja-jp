---
title: 行のスクロールとフェッチ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0ae9f1079f329951045d4b3f61b39c12efc153fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302494"
---
# <a name="scrolling-and-fetching-rows"></a>行のスクロールとフェッチ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  スクロール可能なカーソルを使用するには、ODBC アプリケーションでは次の操作を行う必要があります。  
  
-   カーソル機能を設定する場合[は、SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を使用します。  
  
-   カーソルを開くには **、SQL 実行**または**SQLExecDirect**を使用します。  
  
-   SQL フェッチまたは**SQL**フェッチ[スクロール](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)を使用して行をスクロールおよびフェッチします。  
  
 SQLFetch と**SQLFetchSroll**の両方が一度に行のブロックをフェッチできます。 **SQLFetch** 返される行数は **、SQLSetStmtAttr**を使用してSQL_ATTR_ROW_ARRAY_SIZE パラメーターを設定することによって指定されます。  
  
 ODBC アプリケーションは **、SQLFetch**を使用して、前方のみのカーソルを通じてフェッチできます。  
  
 カーソルをスクロールする場合は **、SQLFetchScroll**を使用します。 **SQLFetchScroll**は、相対フェッチ (現在の行セットの先頭から行セット*n*行をフェッチ) と絶対フェッチ (行*n*から始まる行セットをフェッチ) に加えて、次の行セット、前、最初、最後の行セットのフェッチをサポートします。 n*が絶対*フェッチで負の値の場合、行は結果セットの末尾からカウントされます。 たとえば、行 -1 の絶対フェッチは、結果セット内にある最後の行を起点とした行セットをフェッチします。  
  
 **SQLFetchScroll**を使用するアプリケーションは、レポートなどのブロック カーソル機能でのみ、次の行セットをフェッチするオプションのみを使用して、結果セットを 1 回通過する可能性があります。 一方、画面ベースのアプリケーションは、 **SQLFetchScroll**のすべての機能を利用できます。 アプリケーションが行セットのサイズを画面に表示される行数に設定し、画面バッファーを結果セットにバインドすると、スクロール バーの操作を**SQLFetchScroll**の呼び出しに直接変換できます。  
  
|スクロール バーの操作|SQLFetchScroll のスクロール操作|  
|--------------------------|-------------------------------------|  
|1 画面分上へ移動 (PageUp)|SQL_FETCH_PRIOR|  
|1 画面分下へ移動 (PageDown)|SQL_FETCH_NEXT|  
|1 行上へ移動|フェッチオフセットが -1 のSQL_FETCH_RELATIVE|  
|1 行下へ移動|FetchOffset に 1 を指定した SQL_FETCH_RELATIVE |  
|スクロール ボックスを先頭に移動|SQL_FETCH_FIRST|  
|スクロール ボックスを末尾に移動|SQL_FETCH_LAST|  
|スクロール ボックスを任意の位置に移動|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [ODBC での行のブックマーク](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;カーソルの使用](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
