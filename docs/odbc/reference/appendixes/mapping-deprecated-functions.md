---
title: 非推奨関数のマッピング |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a4e89cd9281520e70ec5fb289c6050e77ec6194c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299882"
---
# <a name="mapping-deprecated-functions"></a>非推奨の関数のマッピング
このセクションでは、ODBC 2.x アプリケーションで使用される ODBC *3.x*ドライバーの下位互換性を保証するために、ODBC *3.x* *2.x*ドライバー マネージャーによって、非推奨関数がどのようにマップされるかについて説明します。 ドライバー マネージャーは、アプリケーションのバージョンに関係なく、このマッピングを実行します。 ODBC 3.x ドライバで呼び出された ODBC *3.x*ドライバでは、次のリストに示す ODBC *2.x*関数がそれぞれ対応する ODBC *3.x*関数にマップされるため、ODBC *3.x*ドライバは ODBC *2.x*関数を実装する必要がありません。  
  
 一覧のマッピングは、ドライバーが ODBC *3.x*ドライバーであり、ドライバーがマップされている関数をサポートしていない場合にトリガーされます。  
  
 次の表は、ODBC *3.x*で導入されたすべての重複した機能の一覧です。  
  
|ODBC *2.x*関数|ODBC *3.x*関数|  
|-------------------------|-------------------------|  
|**コネクト**|**ハンドル**|  
|**SQLAllocEnv**|**ハンドル**|  
|**をクリックします。**|**ハンドル**|  
|**SQL バインドパラム**[1]|**SQLBindParameter**|  
|**属性**|**SQLColAttribute**|  
|**エラー**|**SQLGetDiagRec**|  
|**コネクト**|**SQLFreeHandle**|  
|**を実行する**|**SQLFreeHandle**|  
|SQL_DROPの*オプション*を持つ**SQLFreeStmt**|**SQLFreeHandle**|  
|**オプションを指定します。**|**SQLGetConnectAttr**|  
|**オプションを指定します。**|**SQLGetStmtAttr**|  
|**オプション**|**SQLSetStmtAttr**|  
|**オプションを指定します。**|**SQLSetConnectAttr**|  
|**SQL セットパラム**[2]|**SQLBindParameter**|  
|**スクロールオプション**|**SQLSetStmtAttr**|  
|**オプションを設定します。**|**SQLSetStmtAttr**|  
|**トランスアクト**|**SQLEndTran**|  
  
 [1] この関数は ODBC *2.x*に存在しないにもかかわらず、オープングループおよび ISO 標準に含まれています。  
  
 [2] これは ODBC 1.0 関数です。  
  
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
