---
title: 非推奨の関数のマッピング |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], about mapping deprecated functions
- backward compatibility [ODBC], mapping deprecated functions
- deprecated functions [ODBC]
- compatibility [ODBC], mapping deprecated functions
- functions [ODBC], mapping deprecated functions
- mapping deprecated functions [ODBC]
ms.assetid: ee462617-1d79-4c88-afeb-b129cff34cc6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b59d2604dd9d4b7c3166027c1917dea096b331d9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181318"
---
# <a name="mapping-deprecated-functions"></a>非推奨の関数のマッピング
このセクションには、どのように非推奨の関数がについて説明します、ODBC 3 によってマップされます *.x* ODBC 3 の旧バージョンとの互換性を保証するために、ドライバー マネージャー *.x*ドライバーは ODBC 2 で使用される *。x*アプリケーション。 ドライバー マネージャーは、アプリケーションのバージョンに関係なく、このマッピングを実行します。 ため、各 ODBC 2。*x*関数は、次の一覧は、対応する ODBC 3 にマップされて *.x*関数、ODBC 3 で呼び出されると *.x*ドライバー、ODBC 3 *.x*ドライバーは、ODBC 2 を実装する必要はありません。*x*関数。  
  
 リスト内のマッピングは、ドライバーは、ODBC 3 ときにトリガーされる *.x*ドライバーとドライバーがマップされる関数をサポートしていません。  
  
 次の表に、ODBC 3 で導入された機能がすべての重複 *.x*します。  
  
|ODBC 2。*x*関数|ODBC 3 *.x*関数|  
|-------------------------|-------------------------|  
|**SQLAllocConnect**|**SQLAllocHandle**|  
|**SQLAllocEnv**|**SQLAllocHandle**|  
|**SQLAllocStmt**|**SQLAllocHandle**|  
|**SQLBindParam**[1]|**SQLBindParameter**|  
|**SQLColAttributes**|**SQLColAttribute**|  
|**SQLError**|**SQLGetDiagRec**|  
|**SQLFreeConnect**|**SQLFreeHandle**|  
|**SQLFreeEnv**|**SQLFreeHandle**|  
|**SQLFreeStmt**で、*オプション*SQL_DROP の|**SQLFreeHandle**|  
|**SQLGetConnectOption**|**SQLGetConnectAttr**|  
|**SQLGetStmtOption**|**SQLGetStmtAttr**|  
|**SQLParamOptions**|**SQLSetStmtAttr**|  
|**SQLSetConnectOption**|**SQLSetConnectAttr**|  
|**SQLSetParam**[2]|**SQLBindParameter**|  
|**SQLSetScrollOption**|**SQLSetStmtAttr**|  
|**SQLSetStmtOption**|**SQLSetStmtAttr**|  
|**SQLTransact**|**SQLEndTran**|  
  
 [1] この関数は、ODBC 2 には存在しなかった場合でも *.x*、Open Group と ISO 標準になっています。  
  
 [2] これは、ODBC 1.0 関数です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQLAllocConnect のマッピング](../../../odbc/reference/appendixes/sqlallocconnect-mapping.md)  
  
-   [SQLAllocEnv のマッピング](../../../odbc/reference/appendixes/sqlallocenv-mapping.md)  
  
-   [SQLAllocStmt のマッピング](../../../odbc/reference/appendixes/sqlallocstmt-mapping.md)  
  
-   [SQLBindParam のマッピング](../../../odbc/reference/appendixes/sqlbindparam-mapping.md)  
  
-   [SQLColAttributes のマッピング](../../../odbc/reference/appendixes/sqlcolattributes-mapping.md)  
  
-   [SQLError のマッピング](../../../odbc/reference/appendixes/sqlerror-mapping.md)  
  
-   [SQLFreeConnect のマッピング](../../../odbc/reference/appendixes/sqlfreeconnect-mapping.md)  
  
-   [SQLFreeEnv のマッピング](../../../odbc/reference/appendixes/sqlfreeenv-mapping.md)  
  
-   [SQLFreeStmt のマッピング](../../../odbc/reference/appendixes/sqlfreestmt-mapping.md)  
  
-   [SQLGetConnectOption のマッピング](../../../odbc/reference/appendixes/sqlgetconnectoption-mapping.md)  
  
-   [SQLGetStmtOption のマッピング](../../../odbc/reference/appendixes/sqlgetstmtoption-mapping.md)  
  
-   [SQLInstallTranslator のマッピング](../../../odbc/reference/appendixes/sqlinstalltranslator-mapping.md)  
  
-   [SQLParamOptions のマッピング](../../../odbc/reference/appendixes/sqlparamoptions-mapping.md)  
  
-   [SQLSetConnectOption のマッピング](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)  
  
-   [SQLSetParam のマッピング](../../../odbc/reference/appendixes/sqlsetparam-mapping.md)  
  
-   [SQLSetScrollOptions のマッピング](../../../odbc/reference/appendixes/sqlsetscrolloptions-mapping.md)  
  
-   [SQLSetStmtOption のマッピング](../../../odbc/reference/appendixes/sqlsetstmtoption-mapping.md)  
  
-   [SQLTransact のマッピング](../../../odbc/reference/appendixes/sqltransact-mapping.md)
