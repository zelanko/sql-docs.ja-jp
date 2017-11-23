---
title: "ODBC 3.x ドライバーの記述 |Microsoft ドキュメント"
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
helpviewer_keywords:
- upgrading drivers [ODBC]
- ODBC drivers [ODBC], upgrading
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 9b75f59b-623f-4711-9ca2-e751b3622e00
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5ea639a8bde008d657cff558183220d7e68fe568
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="writing-odbc-3x-drivers"></a>書き込み ODBC 3.x ドライバー
次の表は、ODBC 3 関数のサポートを示します。*x*ドライバーと ODBC アプリケーションでは、ODBC 3 に対して関数が呼び出されると、ドライバー マネージャーでを実行するマッピング*。x*ドライバー。  
  
|関数|Supported<br /><br /> で、<br /><br /> ODBC 3 です。*x*<br /><br /> ドライバーですか。|Supported<br /><br /> で、<br /><br /> ODBC 3 です。*x*<br /><br /> アプリケーションか。|マップ サポート<br /><br /> ODBC 3 です。*x*<br /><br /> ドライバー マネージャー<br /><br /> ODBC 3 の場合。*x*ドライバーですか?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|不可|[1]|可|  
|**SQLAllocEnv**|不可|[1]|可|  
|**SQLAllocHandle**|可|可|不可|  
|**SQLAllocStmt**|不可|[1]|可|  
|**SQLBindCol**|可|可|不可|  
|**SQLBindParam**|不可|[2] を [はい]|可|  
|**SQLBindParameter**|可|可|不可|  
|**SQLBrowseConnect**|可|可|不可|  
|**SQLBulkOperations**|可|可|不可|  
|**SQLCancel**|可|可|不可|  
|**SQLCloseCursor**|可|可|不可|  
|**SQLColAttribute**|可|可|不可|  
|**SQLColAttributes**|[3]|不可|可|  
|**SQLColumnPrivileges**|可|可|不可|  
|**SQLColumns**|可|可|不可|  
|**SQLConnect**|可|可|不可|  
|**SQLCopyDesc**|可|可|[はい] [4]|  
|**SQLDataSources**|不可|はい|可|  
|**SQLDescribeCol**|可|可|不可|  
|**SQLDescribeParam**|可|可|不可|  
|**SQLDisconnect**|可|可|不可|  
|**SQLDriverConnect**|可|可|不可|  
|**SQLDrivers**|不可|はい|可|  
|**SQLEndTran**|可|可|不可|  
|**SQLError**|不可|[1]|可|  
|**SQLExecDirect**|可|可|不可|  
|**SQLExecute**|可|可|不可|  
|**SQLExtendedFetch**|可|いいえ|不可|  
|**SQLFetch**|可|可|不可|  
|**SQLFetchScroll**|可|可|不可|  
|**SQLForeignKeys**|可|可|不可|  
|**SQLFreeConnect**|不可|[1] を [はい]|可|  
|**SQLFreeEnv**|不可|[1] を [はい]|可|  
|**SQLFreeHandle**|可|可|不可|  
|**SQLFreeStmt**|可|可|不可|  
|**SQLGetConnectAttr**|可|可|不可|  
|**SQLGetConnectOption**|[5]|[1]|可|  
|**SQLGetCursorName**|可|可|不可|  
|**SQLGetData**|可|可|不可|  
|**SQLGetDescField**|可|可|不可|  
|**SQLGetDescRec**|可|可|不可|  
|**SQLGetDiagField**|可|可|不可|  
|**SQLGetDiagRec**|可|可|不可|  
|**SQLGetEnvAttr**|可|可|不可|  
|**SQLGetFunctions**|[6]|可|可|  
|**SQLGetInfo**|可|可|不可|  
|**SQLGetStmtAttr**|可|可|不可|  
|**SQLGetStmtOption**|[5]|[1]|可|  
|**SQLGetTypeInfo**|可|可|不可|  
|**SQLMoreResults**|可|可|不可|  
|**SQLNativeSql**|可|可|不可|  
|**SQLNumParams**|可|可|不可|  
|**SQLNumResultCols**|可|可|不可|  
|**SQLParamData**|可|可|不可|  
|**SQLParamOptions**|不可|いいえ|可|  
|**SQLPrepare**|可|可|不可|  
|**SQLPrimaryKeys**|可|可|不可|  
|**SQLProcedureColumns**|可|可|不可|  
|**SQLProcedures**|可|可|不可|  
|**SQLPutData**|可|可|不可|  
|**SQLRowCount**|可|可|不可|  
|**SQLSetConnectAttr**|可|可|不可|  
|**SQLSetConnectOption**|[5]|[1]|可|  
|**SQLSetCursorName**|可|可|不可|  
|**SQLSetDescField**|可|可|不可|  
|**SQLSetDescRec**|可|可|不可|  
|**SQLSetEnvAttr**|可|可|不可|  
|**SQLSetPos**|可|可|不可|  
|**SQLSetParam**|不可|いいえ|可|  
|**SQLSetScrollOption**|可|可|不可|  
|**SQLSetStmtAttr**|可|可|不可|  
|**SQLSetStmtOption**|[5]|[1]|可|  
|**SQLSpecialColumns**|可|可|不可|  
|**SQLStatistics**|可|可|不可|  
|**SQLTablePrivileges**|可|可|不可|  
|**SQLTables**|可|可|不可|  
|**SQLTransact**|不可|[1]|可|  
  
 [1] この関数は、ODBC 3 で廃止されました。*x*です。 ODBC 3 です。*x*アプリケーションでは、この関数は使用する必要があります。 ただし、Open Group または ISO CLI 互換のアプリケーションは、この関数を呼び出すことができます。  
  
 [2] ODBC 3 です。*x*アプリケーションを使用する必要があります**SQLBindParameter**の代わりに**SQLBindParam**です。 ただし、Open Group または ISO CLI 互換のアプリケーションは、この関数を呼び出すことができます。  
  
 [3] のドライバーの作成者に注意してくださいを ODBC 2 です。*x*列属性で SQL_COLUMN_PRECISION、SQL_COLUMN_SCALE、および SQL_COLUMN_LENGTH をサポートする必要があります**SQLColAttribute**です。  
  
 [4] **SQLCopyDesc**接続を介して別のドライバーに属している、記述子がコピーされるときに、ドライバー マネージャーによって部分的に実装します。 ドライバーがサポートするために必要な**SQLCopyDesc**が自分の接続の 2 つのです。 などの関数**SQLDrivers**、ドライバー マネージャーによってのみ実装されているが、この一覧に表示されません。  
  
 [5]、特定の状況下にあるドライバーは、この関数をサポートする必要があります。 詳細については、この関数のリファレンス ページを参照してください。  
  
 [6]、ドライバーがサポートするために選択できます**SQLGetFunctions**ドライバーでサポートされる関数のセットは異なる接続から接続する場合。
