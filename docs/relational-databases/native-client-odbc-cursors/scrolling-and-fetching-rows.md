---
title: "スクロールとフェッチ行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-cursors
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f84d14d3ab2eb2bd3be56e61d34741916446aa48
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="scrolling-and-fetching-rows"></a>行のスクロールとフェッチ
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  スクロール可能なカーソルを使用するには、ODBC アプリケーションでは次の操作を行う必要があります。  
  
-   使用してカーソル機能を設定[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)です。  
  
-   使用して、カーソルを開く**SQLExecute**または**SQLExecDirect**です。  
  
-   使用して行をスクロールおよびフェッチ**SQLFetch**または[SQLFetchScroll](../../relational-databases/native-client-odbc-api/sqlfetchscroll.md)です。  
  
 両方**SQLFetch**と**SQLFetchSroll**一度に行のブロックをフェッチすることができます。 使用して指定された行の数が返される**SQLSetStmtAttr** SQL_ATTR_ROW_ARRAY_SIZE パラメーターを設定します。  
  
 ODBC アプリケーションを使用できる**SQLFetch**順方向専用カーソルを介してフェッチを実行します。  
  
 **SQLFetchScroll**カーソルの周囲をスクロールするために使用します。 **SQLFetchScroll** 、次のフェッチをサポートしているだけでなく相対フェッチ前に、最初と最後の行セット (行セットをフェッチ *n* 現在の行セットの先頭からの行) と絶対フェッチ (フェッチ行で始まる行セット *n* )。 場合 *n* は行が結果セットの最後から数えられます絶対フェッチで負の値。 たとえば、行 -1 の絶対フェッチは、結果セット内にある最後の行を起点とした行セットをフェッチします。  
  
 使用するアプリケーション**SQLFetchScroll**そのブロックにのみレポートなどのカーソル機能は、1 回、結果セットを通過する可能性がありますオプションのみを使用して、次の行セットをフェッチします。 スクリーン ベースのアプリケーションでは、その一方で、活用することのすべての機能**SQLFetchScroll**です。 スクロール バー操作を直接の呼び出しを変換できる場合は、アプリケーションでは、画面に表示される行数を行セットのサイズに設定しを結果セットに、画面バッファーをバインド、 **SQLFetchScroll**です。  
  
|スクロール バーの操作|SQLFetchScroll のスクロール操作|  
|--------------------------|-------------------------------------|  
|1 画面分上へ移動 (PageUp)|SQL_FETCH_PRIOR|  
|1 画面分下へ移動 (PageDown)|SQL_FETCH_NEXT|  
|1 行上へ移動|指定した FetchOffset-1 に等しく SQL_FETCH_RELATIVE|  
|1 行下へ移動|FetchOffset に 1 を指定した SQL_FETCH_RELATIVE |  
|スクロール ボックスを先頭に移動|SQL_FETCH_FIRST|  
|スクロール ボックスを末尾に移動|SQL_FETCH_LAST|  
|スクロール ボックスを任意の位置に移動|SQL_FETCH_ABSOLUTE|  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [ODBC での行のブックマーク](../../relational-databases/native-client-odbc-cursors/scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>参照  
 [使用してカーソル &#40;ODBC&#41;](../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
