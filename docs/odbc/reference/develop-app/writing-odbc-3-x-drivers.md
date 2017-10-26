---
title: "ODBC 3.x ドライバーの記述 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- upgrading drivers [ODBC]
- ODBC drivers [ODBC], upgrading
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 9b75f59b-623f-4711-9ca2-e751b3622e00
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 41ca6ddf1535899ed8e5e0f065cf2f5f0ca19dca
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="writing-odbc-3x-drivers"></a>書き込み ODBC 3.x ドライバー
次の表は、ODBC 3 関数のサポートを示します。*x*ドライバーと ODBC アプリケーションでは、ODBC 3 に対して関数が呼び出されると、ドライバー マネージャーでを実行するマッピング*。x*ドライバー。  
  
|関数|Supported<br /><br /> で、<br /><br /> ODBC 3 です。*x*<br /><br /> ドライバーですか。|Supported<br /><br /> で、<br /><br /> ODBC 3 です。*x*<br /><br /> アプリケーションか。|マップ サポート<br /><br /> ODBC 3 です。*x*<br /><br /> ドライバー マネージャー<br /><br /> ODBC 3 の場合。*x*ドライバーですか?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|不可|[1]|はい|  
|**SQLAllocEnv**|不可|[1]|はい|  
|**SQLAllocHandle**|はい|可|不可|  
|**SQLAllocStmt**|不可|[1]|はい|  
|**SQLBindCol**|はい|可|不可|  
|**SQLBindParam**|不可|[2] を [はい]|はい|  
|**SQLBindParameter**|はい|可|不可|  
|**SQLBrowseConnect**|はい|可|不可|  
|**SQLBulkOperations**|はい|可|不可|  
|**SQLCancel**|はい|可|不可|  
|**SQLCloseCursor**|はい|可|不可|  
|**SQLColAttribute**|はい|可|不可|  
|**SQLColAttributes**|[3]|不可|はい|  
|**SQLColumnPrivileges**|はい|可|不可|  
|**SQLColumns**|はい|可|不可|  
|**SQLConnect**|はい|可|不可|  
|**SQLCopyDesc**|はい|はい|[はい] [4]|  
|**SQLDataSources**|不可|はい|はい|  
|**SQLDescribeCol**|はい|可|不可|  
|**SQLDescribeParam**|はい|可|不可|  
|**SQLDisconnect**|はい|可|不可|  
|**SQLDriverConnect**|はい|可|不可|  
|**SQLDrivers**|不可|はい|はい|  
|**SQLEndTran**|はい|可|不可|  
|**SQLError**|不可|[1]|はい|  
|**SQLExecDirect**|はい|可|不可|  
|**SQLExecute**|はい|可|不可|  
|**SQLExtendedFetch**|はい|いいえ|不可|  
|**SQLFetch**|はい|可|不可|  
|**SQLFetchScroll**|はい|可|不可|  
|**SQLForeignKeys**|はい|可|不可|  
|**SQLFreeConnect**|不可|[1] を [はい]|はい|  
|**SQLFreeEnv**|不可|[1] を [はい]|はい|  
|**SQLFreeHandle**|はい|可|不可|  
|**SQLFreeStmt**|はい|可|不可|  
|**SQLGetConnectAttr**|はい|可|不可|  
|**SQLGetConnectOption**|[5]|[1]|はい|  
|**SQLGetCursorName**|はい|可|不可|  
|**SQLGetData**|はい|可|不可|  
|**SQLGetDescField**|はい|可|不可|  
|**Sqlgetdescrec による**|はい|可|不可|  
|**SQLGetDiagField**|はい|可|不可|  
|**SQLGetDiagRec**|はい|可|不可|  
|**SQLGetEnvAttr**|はい|可|不可|  
|**SQLGetFunctions**|[6]|はい|はい|  
|**SQLGetInfo**|はい|可|不可|  
|**SQLGetStmtAttr**|はい|可|不可|  
|**SQLGetStmtOption**|[5]|[1]|はい|  
|**SQLGetTypeInfo**|はい|可|不可|  
|**SQLMoreResults**|はい|可|不可|  
|**SQLNativeSql**|はい|可|不可|  
|**SQLNumParams**|はい|可|不可|  
|**SQLNumResultCols**|はい|可|不可|  
|**SQLParamData**|はい|可|不可|  
|**SQLParamOptions**|不可|いいえ|はい|  
|**SQLPrepare**|はい|可|不可|  
|**SQLPrimaryKeys**|はい|可|不可|  
|**SQLProcedureColumns**|はい|可|不可|  
|**SQLProcedures**|はい|可|不可|  
|**SQLPutData**|はい|可|不可|  
|**SQLRowCount**|はい|可|不可|  
|**SQLSetConnectAttr**|はい|可|不可|  
|**SQLSetConnectOption**|[5]|[1]|はい|  
|**SQLSetCursorName**|はい|可|不可|  
|**Sqlsetdescfield による**|はい|可|不可|  
|**Sqlsetdescrec による**|はい|可|不可|  
|**SQLSetEnvAttr**|はい|可|不可|  
|**SQLSetPos**|はい|可|不可|  
|**SQLSetParam**|不可|いいえ|はい|  
|**SQLSetScrollOption**|はい|可|不可|  
|**SQLSetStmtAttr**|はい|可|不可|  
|**SQLSetStmtOption**|[5]|[1]|はい|  
|**SQLSpecialColumns**|はい|可|不可|  
|**SQLStatistics**|はい|可|不可|  
|**SQLTablePrivileges**|はい|可|不可|  
|**SQLTables**|はい|可|不可|  
|**SQLTransact**|不可|[1]|はい|  
  
 [1] この関数は、ODBC 3 で廃止されました。*x*です。 ODBC 3 です。*x*アプリケーションでは、この関数は使用する必要があります。 ただし、Open Group または ISO CLI 互換のアプリケーションは、この関数を呼び出すことができます。  
  
 [2] ODBC 3 です。*x*アプリケーションを使用する必要があります**SQLBindParameter**の代わりに**SQLBindParam**です。 ただし、Open Group または ISO CLI 互換のアプリケーションは、この関数を呼び出すことができます。  
  
 [3] のドライバーの作成者に注意してくださいを ODBC 2 です。*x*列属性で SQL_COLUMN_PRECISION、SQL_COLUMN_SCALE、および SQL_COLUMN_LENGTH をサポートする必要があります**SQLColAttribute**です。  
  
 [4] **SQLCopyDesc**接続を介して別のドライバーに属している、記述子がコピーされるときに、ドライバー マネージャーによって部分的に実装します。 ドライバーがサポートするために必要な**SQLCopyDesc**が自分の接続の 2 つのです。 などの関数**SQLDrivers**、ドライバー マネージャーによってのみ実装されているが、この一覧に表示されません。  
  
 [5]、特定の状況下にあるドライバーは、この関数をサポートする必要があります。 詳細については、この関数のリファレンス ページを参照してください。  
  
 [6]、ドライバーがサポートするために選択できます**SQLGetFunctions**ドライバーでサポートされる関数のセットは異なる接続から接続する場合。

