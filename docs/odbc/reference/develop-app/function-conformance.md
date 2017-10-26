---
title: "関数への準拠 |Microsoft ドキュメント"
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
- conformance levels [ODBC], function
- function conformance levels [ODBC]
- data sources [ODBC], conformance levels
- ODBC drivers [ODBC], conformance levels
ms.assetid: bb5d68cf-d238-481e-babc-2e9401b4700e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 48ed4bc9b52b6a905972e566870e7e2f86fc4734
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="function-conformance"></a>関数への準拠
次の表では、これは適切に定義された ODBC の各関数の準拠レベルを示します。  
  
|関数|準拠レベル|  
|--------------|-----------------------|  
|**SQLAllocHandle**|コア|  
|**SQLBindCol**|コア|  
|**SQLBindParameter**|コア [1]|  
|**SQLBrowseConnect**|[レベル 1]|  
|**SQLBulkOperations**|[レベル 1]|  
|**SQLCancel**|コア [1]|  
|**SQLCloseCursor**|コア|  
|**SQLColAttribute**|コア [1]|  
|**SQLColumnPrivileges**|[レベル 2]|  
|**SQLColumns**|コア|  
|**SQLConnect**|コア|  
|**SQLCopyDesc**|コア|  
|**SQLDataSources**|コア|  
|**SQLDescribeCol**|コア [1]|  
|**SQLDescribeParam**|[レベル 2]|  
|**SQLDisconnect**|コア|  
|**SQLDriverConnect**|コア|  
|**SQLDrivers**|コア|  
|**SQLEndTran**|コア [1]|  
|**SQLExecDirect**|コア|  
|**SQLExecute**|コア|  
|**SQLFetch**|コア|  
|**SQLFetchScroll**|コア [1]|  
|**SQLForeignKeys**|[レベル 2]|  
|**SQLFreeHandle**|コア|  
|**SQLFreeStmt**|コア|  
|**SQLGetConnectAttr**|コア|  
|**SQLGetCursorName**|コア|  
|**SQLGetData**|コア|  
|**SQLGetDescField**|コア|  
|**Sqlgetdescrec による**|コア|  
|**SQLGetDiagField**|コア|  
|**SQLGetDiagRec**|コア|  
|**SQLGetEnvAttr**|コア|  
|**SQLGetFunctions**|コア|  
|**SQLGetInfo**|コア|  
|**SQLGetStmtAttr**|コア|  
|**SQLGetTypeInfo**|コア|  
|**SQLMoreResults**|[レベル 1]|  
|**SQLNativeSql**|コア|  
|**SQLNumParams**|コア|  
|**SQLNumResultCols**|コア|  
|**SQLParamData**|コア|  
|**SQLPrepare**|コア|  
|**SQLPrimaryKeys**|[レベル 1]|  
|**SQLProcedureColumns**|[レベル 1]|  
|**SQLProcedures**|[レベル 1]|  
|**SQLPutData**|コア|  
|**SQLRowCount**|コア|  
|**SQLSetConnectAttr**|[2] のコア|  
|**SQLSetCursorName**|コア|  
|**Sqlsetdescfield による**|コア [1]|  
|**Sqlsetdescrec による**|コア|  
|**SQLSetEnvAttr**|[2] のコア|  
|**SQLSetPos**|レベル 1 [1]|  
|**SQLSetStmtAttr**|[2] のコア|  
|**SQLSpecialColumns**|コア [1]|  
|**SQLStatistics**|コア|  
|**SQLTablePrivileges**|[レベル 2]|  
|**SQLTables**|コア|  
  
 [1] 重要な機能がこの関数は、上位の準拠レベルでのみ使用可能なです。  
  
 [2] の特定の属性を既定以外の値に設定すると、準拠レベルに依存します。 詳細については、次のセクションを参照してください。[属性への準拠](../../../odbc/reference/develop-app/attribute-conformance.md)です。

