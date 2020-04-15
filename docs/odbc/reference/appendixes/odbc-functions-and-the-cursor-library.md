---
title: ODBC 関数とカーソル ライブラリ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c609d0fb-787a-4b39-9673-332d411b3d63
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d8293e9bc952fc1dffc5a8f796f5a066b91ae811
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304343"
---
# <a name="odbc-functions-and-the-cursor-library"></a>ODBC 関数およびカーソル ライブラリ
> [!IMPORTANT]  
>  この機能は、今後のバージョンの Windows で削除される予定です。 新しい開発作業でこの機能を使用することは避け、現在この機能を使用しているアプリケーションを変更する予定です。 マイクロソフトでは、ドライバーのカーソル機能を使用することをお勧めします。  
  
 ODBC カーソル ライブラリが接続に対して有効になっている場合、ドライバー マネージャーは、ドライバーではなく、カーソル ライブラリ内の関数を呼び出します。 カーソル ライブラリは、関数を実行するか、指定されたドライバーで呼び出します。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [カーソル ライブラリによって実行される ODBC 関数](../../../odbc/reference/appendixes/odbc-functions-executed-by-the-cursor-library.md)  
  
-   [カーソル ライブラリによって実行されない ODBC 関数](../../../odbc/reference/appendixes/odbc-functions-not-executed-by-the-cursor-library.md)  
  
-   [SQLBindCol (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlbindcol-cursor-library.md)  
  
-   [SQLBindParameter (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlbindparameter-cursor-library.md)  
  
-   [操作 (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlbulkoperations-and-the-cursor-library.md)  
  
-   [カーソルを閉じる (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlclosecursor-odbc.md)  
  
-   [SQLEndTran (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlendtran-cursor-library.md)  
  
-   [SQLExtendedFetch (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlextendedfetch-cursor-library.md)  
  
-   [SQLFetch (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlfetch-cursor-library.md)  
  
-   [SQLFetchScroll (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlfetchscroll-cursor-library.md)  
  
-   [SQLFreeStmt (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlfreestmt-cursor-library.md)  
  
-   [SQLGetData (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlgetdata-cursor-library.md)  
  
-   [SQLGetDescField および SQLGetDescRec (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlgetdescfield-and-sqlgetdescrec-cursor-library.md)  
  
-   [SQLGetFunctions (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlgetfunctions-cursor-library.md)  
  
-   [SQLGetInfo (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlgetinfo-cursor-library.md)  
  
-   [SQLGetStmtAttr (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlgetstmtattr-cursor-library.md)  
  
-   [SQLGetStmtOption (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlgetstmtoption-cursor-library.md)  
  
-   [SQLNativeSql (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlnativesql-cursor-library.md)  
  
-   [SQLRowCount (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlrowcount-cursor-library.md)  
  
-   [SQLSetConnectAttr (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlsetconnectattr-cursor-library.md)  
  
-   [SQLSetDescField および SQLSetDescRec (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlsetdescfield-and-sqlsetdescrec-cursor-library.md)  
  
-   [SQL セットエンバトル (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlsetenvattr-and-the-cursor-library.md)  
  
-   [SQLSetPos (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlsetpos-cursor-library.md)  
  
-   [SQLSetScrollOptions (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlsetscrolloptions-cursor-library.md)  
  
-   [SQLSetStmtAttr (カーソル ライブラリ)](../../../odbc/reference/appendixes/sqlsetstmtattr-cursor-library.md)
