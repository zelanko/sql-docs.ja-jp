---
title: "マッピング関数の廃止 |Microsoft ドキュメント"
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
- mapping deprecated functions [ODBC], about mapping deprecated functions
- backward compatibility [ODBC], mapping deprecated functions
- deprecated functions [ODBC]
- compatibility [ODBC], mapping deprecated functions
- functions [ODBC], mapping deprecated functions
- mapping deprecated functions [ODBC]
ms.assetid: ee462617-1d79-4c88-afeb-b129cff34cc6
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 61d05017039673989e1477501feb17b3da6d7220
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="mapping-deprecated-functions"></a>使用されなくなった関数のマッピング
このセクションの内容がどのように使用されなくなった関数について説明します、ODBC 3 でマッピングされます*.x* ODBC 3 の下位互換性を保証するためにドライバー マネージャー*.x* ODBC 2 で使用されるドライバー* 。x*アプリケーションです。 ドライバー マネージャーでは、アプリケーションのバージョンに関係なく、このマッピングを実行します。 ODBC 2 の各します。*x*次の一覧内の関数は、対応する ODBC 3 にマップされて*.x*関数、ODBC 3 で呼び出されると*.x*ドライバー、ODBC 3*.x*ドライバーは、ODBC 2 を実装する必要はありません。*x*関数。  
  
 リスト内のマッピングは、ドライバーは ODBC 3 ときにトリガーされる*.x*ドライバーとドライバーがマップされている関数をサポートしていません。  
  
 次の表に、ODBC 3 で導入された機能がすべての重複*.x*です。  
  
|ODBC 2 です。*x*関数|ODBC 3*.x*関数|  
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
  
 [1] この関数は、ODBC 2 には存在しなかった場合でも*.x*、Open Group および ISO 標準になっています。  
  
 [2] これは、ODBC 1.0 関数です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [SQLAllocConnect マッピング](../../../odbc/reference/appendixes/sqlallocconnect-mapping.md)  
  
-   [SQLAllocEnv マッピング](../../../odbc/reference/appendixes/sqlallocenv-mapping.md)  
  
-   [SQLAllocStmt マッピング](../../../odbc/reference/appendixes/sqlallocstmt-mapping.md)  
  
-   [SQLBindParam マッピング](../../../odbc/reference/appendixes/sqlbindparam-mapping.md)  
  
-   [SQLColAttributes マッピング](../../../odbc/reference/appendixes/sqlcolattributes-mapping.md)  
  
-   [SQLError マッピング](../../../odbc/reference/appendixes/sqlerror-mapping.md)  
  
-   [SQLFreeConnect マッピング](../../../odbc/reference/appendixes/sqlfreeconnect-mapping.md)  
  
-   [SQLFreeEnv マッピング](../../../odbc/reference/appendixes/sqlfreeenv-mapping.md)  
  
-   [SQLFreeStmt マッピング](../../../odbc/reference/appendixes/sqlfreestmt-mapping.md)  
  
-   [SQLGetConnectOption マッピング](../../../odbc/reference/appendixes/sqlgetconnectoption-mapping.md)  
  
-   [SQLGetStmtOption マッピング](../../../odbc/reference/appendixes/sqlgetstmtoption-mapping.md)  
  
-   [SQLInstallTranslator マッピング](../../../odbc/reference/appendixes/sqlinstalltranslator-mapping.md)  
  
-   [SQLParamOptions マッピング](../../../odbc/reference/appendixes/sqlparamoptions-mapping.md)  
  
-   [SQLSetConnectOption マッピング](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md)  
  
-   [SQLSetParam マッピング](../../../odbc/reference/appendixes/sqlsetparam-mapping.md)  
  
-   [SQLSetScrollOptions マッピング](../../../odbc/reference/appendixes/sqlsetscrolloptions-mapping.md)  
  
-   [SQLSetStmtOption マッピング](../../../odbc/reference/appendixes/sqlsetstmtoption-mapping.md)  
  
-   [SQLTransact マッピング](../../../odbc/reference/appendixes/sqltransact-mapping.md)

