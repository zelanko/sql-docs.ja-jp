---
title: サポートされている ODBC API 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ODBC, API functions
- ODBC SQL grammar, API functions mapped to driver (table) [ODBC]
ms.assetid: b28a8ed6-09b1-4acf-bf3e-f90bb32422de
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f3a6b01a0b0fc8c9f822d8a8a0ad97142d6de1f3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="supported-odbc-api-functions"></a>サポートされている ODBC API 関数
平準化の目的は、どのような機能を利用して、ドライバーからアプリケーションに通知を開始します。 Microsoft ODBC のデスクトップ データベース ドライバーでは、すべてのコアと第 1 レベルの関数をサポートします。  
  
 関数や文法の準拠レベルの詳細については、次を参照してください。[準拠レベル](../../odbc/reference/develop-app/conformance-levels.md)で、 *ODBC プログラマ リファレンス*です。  
  
 ODBC API 関数のサポートは、使用するドライバーに依存することができます。 次の表は、関数のサポートをまとめたものです。 左端の列は、各関数の一般的なリファレンス ページへのリンクを提供します。 これらのリファレンス ページがアルファベット順に表示されている、 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)セクションの  [ODBC プログラマ リファレンス](../../odbc/reference/odbc-programmer-s-reference.md)です。 それぞれについて、ドライバー固有の注意事項に右を指定してリンクする列には、関数がサポートされています。 これらのドライバー固有のトピックは、各ドライバーの他のプログラミングの詳細」セクションに表示されます。 代わりに、関数に関する同じ注釈は、すべての ODBC デスクトップ データベース ドライバーに適用される場合、右端の列はその関数のサポートをデスクトップ データベース ドライバーの概要について説明するトピックへのリンクを提供します。 これらのトピックは、現在のセクション ("サポートされている ODBC API 関数") の末尾に表示されます。  
  
|ODBC 関数|アクセスのドライバー固有の注意事項|dBASE ドライバー固有の注意事項|Paradox ドライバー固有の注意事項|テキスト ファイル ドライバー固有の注意事項|Excel ドライバー固有の注意事項|すべてのドライバーに関連する注意事項|  
|-------------------|-----------------------------------|----------------------------------|------------------------------------|--------------------------------------|----------------------------------|-----------------------------------|  
|[SQLBindParameter](../../odbc/reference/syntax/sqlbindparameter-function.md)|||||[Excel](../../odbc/microsoft/sqlbindparameter-excel-driver.md)||  
|[SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md)|[アクセス](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[DBASE](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLColumns](../../odbc/reference/syntax/sqlcolattributes-function.md)|[アクセス](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[DBASE](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLConfigDataSource](../../odbc/reference/syntax/sqlconfigdatasource-function.md)|[アクセス](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)|[DBASE](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)|[Excel](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)||  
|[SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)|[アクセス](../../odbc/microsoft/sqldriverconnect-access-driver.md)|[DBASE](../../odbc/microsoft/sqldriverconnect-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqldriverconnect-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqldriverconnect-text-file-driver.md)|[Excel](../../odbc/microsoft/sqldriverconnect-excel-driver.md)||  
|[SQLGetCursorName](../../odbc/reference/syntax/sqlgetcursorname-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlgetcursorname-desktop-database-drivers.md)|  
|[SQLGetData](../../odbc/reference/syntax/sqlgetdata-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)|  
|[SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md)|[アクセス](../../odbc/microsoft/sqlgetinfo-access-driver.md)|[DBASE](../../odbc/microsoft/sqlgetinfo-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlgetinfo-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlgetinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgetinfo-excel-driver.md)||  
GetStmtOption] (../Topic/SQLGetStmtOption%20Function.md)|[すべてのドライバー](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)||||||  
|[SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[アクセス](../../odbc/microsoft/sqlgettypeinfo-access-driver.md)|[DBASE](../../odbc/microsoft/sqlgettypeinfo-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlgettypeinfo-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlgettypeinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgettypeinfo-excel-driver.md)||  
|[SQLMoreResults](../../odbc/reference/syntax/sqlmoreresults-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)|  
|[SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)|  
|[SQLProcedureColumns](../../odbc/reference/syntax/sqlprocedurecolumns-function.md)||||||[アクセス](../../odbc/microsoft/sqlprocedurecolumns-access-driver.md)|  
|[SQLProcedures](../../odbc/reference/syntax/sqlprocedures-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)|  
|[SQLSetConnectOption](../../odbc/reference/syntax/sqlsetconnectoption-function.md)|[アクセス](../../odbc/microsoft/sqlsetconnectoption-access-driver.md)|[DBASE](../../odbc/microsoft/sqlsetconnectoption-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlsetconnectoption-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlsetconnectoption-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlsetconnectoption-excel-driver.md)||  
|[SQLSetCursorName](../../odbc/reference/syntax/sqlsetcursorname-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)|  
|[SQLSetPos](../../odbc/reference/syntax/sqlsetpos-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)|  
|[SQLSetScrollOptions](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)|  
|[SQLSetStmtOption](../../odbc/reference/syntax/sqlsetstmtoption-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)|  
|[SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)|  
|[SQLStatistics](../../odbc/reference/syntax/sqlstatistics-function.md)|[アクセス](../../odbc/microsoft/sqlstatistics-access-driver.md)|[DBASE](../../odbc/microsoft/sqlstatistics-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqlstatistics-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlstatistics-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlstatistics-excel-driver.md)||  
|[SQLTables](../../odbc/reference/syntax/sqltables-function.md)|[アクセス](../../odbc/microsoft/sqltables-access-driver.md)|[DBASE](../../odbc/microsoft/sqltables-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqltables-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqltables-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltables-excel-driver.md)||  
Transact] (../Topic/SQLTransact%20Function.md)|[アクセス](../../odbc/microsoft/sqltransact-access-driver.md)|[DBASE](../../odbc/microsoft/sqltransact-dbase-driver.md)|[Paradox](../../odbc/microsoft/sqltransact-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqltransact-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltransact-excel-driver.md)||  
  
 次のトピックでは、ODBC 関数についての解説を提供します。 これらの注釈は、すべてのデスクトップ ODBC データベース ドライバーに適用されます。  
  
-   [SQLGetData (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)  
  
-   [SQLGetStmtOption (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)  
  
-   [SQLMoreResults (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)  
  
-   [SQLPrepare (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)  
  
-   [SQLProcedures (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)  
  
-   [SQLSetCursorName (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)  
  
-   [SQLSetPos (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)  
  
-   [SQLSetScrollOptions (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)  
  
-   [SQLSetStmtOption (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)  
  
-   [SQLSpecialColumns (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)
