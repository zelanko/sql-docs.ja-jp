---
title: ODBC 3.x ドライバーの記述 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading drivers [ODBC]
- ODBC drivers [ODBC], upgrading
- backward compatibility [ODBC], drivers
- compatibility [ODBC], drivers
ms.assetid: 9b75f59b-623f-4711-9ca2-e751b3622e00
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9b926d45e6556b53957ecd2934d7068418f3101
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="writing-odbc-3x-drivers"></a>書き込み ODBC 3.x ドライバー
次の表は、ODBC 3 関数のサポートを示します。*x*ドライバーと ODBC アプリケーションでは、ODBC 3 に対して関数が呼び出されると、ドライバー マネージャーでを実行するマッピング*。x*ドライバー。  
  
|関数|Supported<br /><br /> で、<br /><br /> ODBC 3 です。*x*<br /><br /> ドライバーですか。|Supported<br /><br /> で、<br /><br /> ODBC 3 です。*x*<br /><br /> アプリケーションか。|マップ サポート<br /><br /> ODBC 3 です。*x*<br /><br /> ドライバー マネージャー<br /><br /> ODBC 3 の場合。*x*ドライバーですか?|  
|--------------|----------------------------------------------------|---------------------------------------------------------|---------------------------------------------------------------------------------------------|  
|**SQLAllocConnect**|いいえ|[1]|はい|  
|**SQLAllocEnv**|いいえ|[1]|はい|  
|**SQLAllocHandle**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLAllocStmt**|いいえ|[1]|はい|  
|**SQLBindCol**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLBindParam**|いいえ|[2] を [はい]|はい|  
|**SQLBindParameter**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLBrowseConnect**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLBulkOperations**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLCancel**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLCloseCursor**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLColAttribute**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLColAttributes**|[3]|いいえ|はい|  
|**SQLColumnPrivileges**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLColumns**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLConnect**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLCopyDesc**|はい|はい|[はい] [4]|  
|**SQLDataSources**|いいえ|[ユーザー アカウント制御]|はい|  
|**SQLDescribeCol**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLDescribeParam**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLDisconnect**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLDriverConnect**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLDrivers**|いいえ|[ユーザー アカウント制御]|はい|  
|**SQLEndTran**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLError**|いいえ|[1]|はい|  
|**SQLExecDirect**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLExecute**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLExtendedFetch**|はい|いいえ|いいえ|  
|**SQLFetch**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLFetchScroll**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLForeignKeys**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLFreeConnect**|いいえ|[1] を [はい]|はい|  
|**SQLFreeEnv**|いいえ|[1] を [はい]|はい|  
|**SQLFreeHandle**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLFreeStmt**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLGetConnectAttr**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLGetConnectOption**|[5]|[1]|はい|  
|**SQLGetCursorName**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLGetData**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLGetDescField**|はい|[ユーザー アカウント制御]|いいえ|  
|**Sqlgetdescrec による**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLGetDiagField**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLGetDiagRec**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLGetEnvAttr**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLGetFunctions**|[6]|はい|はい|  
|**SQLGetInfo**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLGetStmtAttr**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLGetStmtOption**|[5]|[1]|はい|  
|**SQLGetTypeInfo**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLMoreResults**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLNativeSql**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLNumParams**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLNumResultCols**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLParamData**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLParamOptions**|いいえ|いいえ|はい|  
|**SQLPrepare**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLPrimaryKeys**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLProcedureColumns**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLProcedures**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLPutData**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLRowCount**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLSetConnectAttr**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLSetConnectOption**|[5]|[1]|はい|  
|**SQLSetCursorName**|はい|[ユーザー アカウント制御]|いいえ|  
|**Sqlsetdescfield による**|はい|[ユーザー アカウント制御]|いいえ|  
|**Sqlsetdescrec による**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLSetEnvAttr**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLSetPos**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLSetParam**|いいえ|いいえ|はい|  
|**SQLSetScrollOption**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLSetStmtAttr**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLSetStmtOption**|[5]|[1]|はい|  
|**SQLSpecialColumns**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLStatistics**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLTablePrivileges**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLTables**|はい|[ユーザー アカウント制御]|いいえ|  
|**SQLTransact**|いいえ|[1]|はい|  
  
 [1] この関数は、ODBC 3 で廃止されました。*x*です。 ODBC 3 です。*x*アプリケーションでは、この関数は使用する必要があります。 ただし、Open Group または ISO CLI 互換のアプリケーションは、この関数を呼び出すことができます。  
  
 [2] ODBC 3 です。*x*アプリケーションを使用する必要があります**SQLBindParameter**の代わりに**SQLBindParam**です。 ただし、Open Group または ISO CLI 互換のアプリケーションは、この関数を呼び出すことができます。  
  
 [3] のドライバーの作成者に注意してくださいを ODBC 2 です。*x*列属性で SQL_COLUMN_PRECISION、SQL_COLUMN_SCALE、および SQL_COLUMN_LENGTH をサポートする必要があります**SQLColAttribute**です。  
  
 [4] **SQLCopyDesc**接続を介して別のドライバーに属している、記述子がコピーされるときに、ドライバー マネージャーによって部分的に実装します。 ドライバーがサポートするために必要な**SQLCopyDesc**が自分の接続の 2 つのです。 などの関数**SQLDrivers**、ドライバー マネージャーによってのみ実装されているが、この一覧に表示されません。  
  
 [5]、特定の状況下にあるドライバーは、この関数をサポートする必要があります。 詳細については、この関数のリファレンス ページを参照してください。  
  
 [6]、ドライバーがサポートするために選択できます**SQLGetFunctions**ドライバーでサポートされる関数のセットは異なる接続から接続する場合。
