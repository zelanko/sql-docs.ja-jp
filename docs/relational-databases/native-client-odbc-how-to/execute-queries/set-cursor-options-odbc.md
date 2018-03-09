---
title: "カーソル オプション (ODBC) を設定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-how-to
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: cursors [ODBC], options
ms.assetid: 0e72b48a-fc5a-4656-8cf5-39f57d8c1565
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7ef7e7b54b88e72e77d92213013b0a6b8d036068
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="set-cursor-options-odbc"></a>カーソル オプションの設定 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  カーソル オプションを設定するには、呼び出し[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を設定または[SQLGetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlgetstmtattr.md)カーソル動作を制御するステートメントのオプションを取得します。  
  
|*属性*|指定対象|  
|-----------------|---------------|  
|SQL_ATTR_CURSOR_TYPE|カーソルの種類。順方向専用、静的、動的、キーセット ドリブンのいずれか|  
|SQL_ATTR_CONCURRENCY|同時実行制御オプション。読み取り専用、ロック、タイムスタンプを使用するオプティミスティック、値を使用するオプティミスティックのいずれか|  
|SQL_ATTR_ROW_ARRAY_SIZE|フェッチごとに取得される行数|  
|SQL_ATTR_CURSOR_SENSITIVITY|他の接続によるカーソル行の更新を、カーソルで表示するかしないか|  
|SQL_ATTR_CURSOR_SCROLLABLE|カーソルを前後にスクロール可能|  
  
 これらの属性の既定値 (順方向専用、読み取り専用、行セット サイズ 1) では、サーバー カーソルを使用しません。 サーバー カーソルを使用するには、少なくともこれらの属性のいずれかを既定値以外に設定する必要があります。また、実行するステートメントを、単一の SELECT ステートメントか、単一の SELECT ステートメントを含むストアド プロシージャにする必要があります。 サーバー カーソルの使用時に、サーバー カーソルによってサポートされていない句 (COMPUTE、COMPUTE BY、FOR BROWSE、および INTO) を SELECT ステートメントで使用することはできません。  
  
 SQL_ATTR_CURSOR_TYPE および SQL_ATTR_CONCURRENCY を設定するか、SQL_ATTR_CURSOR_SENSITIVITY と SQL_ATTR_CURSOR_SCROLLABLE を設定して使用するカーソルの種類を制御できます。 カーソルの動作を指定するこの 2 つの方法を組み合わせて実行しないでください。  
  
## <a name="example"></a>例  
 次のサンプルでは、ステートメント ハンドルを割り当て、行のバージョンに基づくオプティミスティック同時実行を使用する動的カーソルを種類として設定してから、SELECT を実行します。  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_DYNAMIC, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQLPOINTER)SQL_CONCUR_ROWVER, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, SELECT au_lname FROM authors", SQL_NTS);  
```  
  
## <a name="example"></a>例  
 次のサンプルでは、ステートメント ハンドルを割り当て、スクロール可能な反映型カーソルを設定してから、SELECT を実行します。  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
  
// Set the cursor options and execute the statement.  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SCROLLABLE, SQLPOINTER)SQL_SCROLLABLE, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SENSITIVITY, SQLPOINTER)SQL_INSENSITIVE, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, select au_lname from authors", SQL_NTS);  
```  
  
## <a name="see-also"></a>参照  
 [実行中のクエリの操作方法に関するトピック &#40; ODBC &#41;](../../../relational-databases/native-client-odbc-how-to/execute-queries/executing-queries-how-to-topics-odbc.md)  
  
  
