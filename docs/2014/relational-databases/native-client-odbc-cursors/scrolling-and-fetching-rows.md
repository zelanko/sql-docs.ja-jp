---
title: スクロールとフェッチ行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
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
caps.latest.revision: 33
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c31b5a4d086fec3ac3db6e3eb1bfbd6bf54c8cb3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071172"
---
# <a name="scrolling-and-fetching-rows"></a>行のスクロールとフェッチ
  スクロール可能なカーソルを使用するには、ODBC アプリケーションでは次の操作を行う必要があります。  
  
-   使用してカーソル機能を設定[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)です。  
  
-   使用して、カーソルを開く**SQLExecute**または**SQLExecDirect**です。  
  
-   使用して行をスクロールおよびフェッチ**SQLFetch**または[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)です。  
  
 両方**SQLFetch**と**SQLFetchSroll**一度に行のブロックをフェッチすることができます。 使用して指定された行の数が返される**SQLSetStmtAttr** SQL_ATTR_ROW_ARRAY_SIZE パラメーターを設定します。  
  
 ODBC アプリケーションを使用できる**SQLFetch**順方向専用カーソルを介してフェッチを実行します。  
  
 **SQLFetchScroll**カーソルの周囲をスクロールするために使用します。 **SQLFetchScroll** 、次のフェッチをサポートしているだけでなく相対フェッチ前に、最初と最後の行セット (行セットをフェッチ*n*現在の行セットの先頭からの行) と絶対フェッチ (fetch、行セット行で始まる*n*)。 場合*n*は行が結果セットの最後から数えられます絶対フェッチで負の値。 たとえば、行 -1 の絶対フェッチは、結果セット内にある最後の行を起点とした行セットをフェッチします。  
  
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
  
-   [ODBC での行のブックマーク](scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a>参照  
 [カーソルを使用して&#40;ODBC&#41;](using-cursors-odbc.md)  
  
  