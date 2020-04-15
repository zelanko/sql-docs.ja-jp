---
title: サポートされている ODBC API 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC, API functions
- ODBC SQL grammar, API functions mapped to driver (table) [ODBC]
ms.assetid: b28a8ed6-09b1-4acf-bf3e-f90bb32422de
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec6ceaf57d8fe3c5325f85a9644cf4c8016663e4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304103"
---
# <a name="supported-odbc-api-functions"></a>サポートされている ODBC API 関数
平準化の目的は、ドライバーから、アプリケーションに利用可能な機能を通知することです。 Microsoft ODBC デスクトップ データベース ドライバは、コアおよびレベル 1 のすべての機能をサポートします。  
  
 関数および文法の準拠レベルの詳細については *、『ODBC プログラマ リファレンス*』の[「準拠レベル](../../odbc/reference/develop-app/conformance-levels.md)」を参照してください。  
  
 ODBC API 関数のサポートは、使用するドライバーに依存できます。 次の表は、関数のサポートをまとめたものです。 左端の列は、各関数の一般参照ページへのリンクを提供します。 これらのリファレンス ページは[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の[「ODBC プログラマ リファレンス](../../odbc/reference/odbc-programmer-s-reference.md)」の下のアルファベット順にリストされています。 右側の列には、サポートされている各関数に関するドライバー固有のメモへのリンクが示されています。 これらのドライバー固有のトピックは、各ドライバーの「その他のプログラミングの詳細」セクションに記載されています。 または、関数に関する同じ注釈がすべての ODBC デスクトップ データベース ドライバに当てはまる場合、右端の列には、その関数に対するデスクトップ データベース ドライバのサポートをまとめたトピックへのリンクが表示されます。 これらのトピックは、現在のセクションの最後にリストされています (「サポートされている ODBC API 関数」)。  
  
|ODBC 機能|アクセス ドライバー固有のメモ|dBASE ドライバー固有の注意事項|パラドックス ドライバー固有の注意事項|テキスト ファイル ドライバ固有のメモ|Excel ドライバー固有の注意事項|すべてのドライバに関連するメモ|  
|-------------------|-----------------------------------|----------------------------------|------------------------------------|--------------------------------------|----------------------------------|-----------------------------------|  
|[SQLBindParameter](../../odbc/reference/syntax/sqlbindparameter-function.md)|||||[Excel](../../odbc/microsoft/sqlbindparameter-excel-driver.md)||  
|[属性](../../odbc/reference/syntax/sqlcolattributes-function.md)|[Access (アクセス)](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[Dbase](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[パラドックス](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLColumns](../../odbc/reference/syntax/sqlcolattributes-function.md)|[Access (アクセス)](../../odbc/microsoft/sqlcolattributes-access-driver.md)|[Dbase](../../odbc/microsoft/sqlcolattributes-dbase-driver.md)|[パラドックス](../../odbc/microsoft/sqlcolattributes-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlcolattributes-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlcolattributes-excel-driver.md)||  
|[SQLConfigDataSource](../../odbc/reference/syntax/sqlconfigdatasource-function.md)|[Access (アクセス)](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)|[Dbase](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)|[パラドックス](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)|[Excel](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)||  
|[SQLDriverConnect](../../odbc/reference/syntax/sqldriverconnect-function.md)|[Access (アクセス)](../../odbc/microsoft/sqldriverconnect-access-driver.md)|[Dbase](../../odbc/microsoft/sqldriverconnect-dbase-driver.md)|[パラドックス](../../odbc/microsoft/sqldriverconnect-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqldriverconnect-text-file-driver.md)|[Excel](../../odbc/microsoft/sqldriverconnect-excel-driver.md)||  
|[SQLGetCursorName](../../odbc/reference/syntax/sqlgetcursorname-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlgetcursorname-desktop-database-drivers.md)|  
|[SQLGetData](../../odbc/reference/syntax/sqlgetdata-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)|  
|[SQLGetInfo](../../odbc/reference/syntax/sqlgetinfo-function.md)|[Access (アクセス)](../../odbc/microsoft/sqlgetinfo-access-driver.md)|[Dbase](../../odbc/microsoft/sqlgetinfo-dbase-driver.md)|[パラドックス](../../odbc/microsoft/sqlgetinfo-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlgetinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgetinfo-excel-driver.md)|
|[オプションを指定します。](../../odbc/reference/syntax/sqlgetstmtoption-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)|  
|[SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[Access (アクセス)](../../odbc/microsoft/sqlgettypeinfo-access-driver.md)|[Dbase](../../odbc/microsoft/sqlgettypeinfo-dbase-driver.md)|[パラドックス](../../odbc/microsoft/sqlgettypeinfo-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlgettypeinfo-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlgettypeinfo-excel-driver.md)||  
|[SQLMoreResults](../../odbc/reference/syntax/sqlmoreresults-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)|  
|[SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)|  
|[SQLProcedureColumns](../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[Access (アクセス)](../../odbc/microsoft/sqlprocedurecolumns-access-driver.md)||||||  
|[SQLProcedures](../../odbc/reference/syntax/sqlprocedures-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)|  
|[オプションを指定します。](../../odbc/reference/syntax/sqlsetconnectoption-function.md)|[Access (アクセス)](../../odbc/microsoft/sqlsetconnectoption-access-driver.md)|[Dbase](../../odbc/microsoft/sqlsetconnectoption-dbase-driver.md)|[パラドックス](../../odbc/microsoft/sqlsetconnectoption-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlsetconnectoption-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlsetconnectoption-excel-driver.md)||  
|[カーソルを設定します。](../../odbc/reference/syntax/sqlsetcursorname-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)|  
|[SQLSetPos](../../odbc/reference/syntax/sqlsetpos-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)|  
|[スクロールオプション](../../odbc/reference/syntax/sqlsetscrolloptions-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)|  
|[オプションを設定します。](../../odbc/reference/syntax/sqlsetstmtoption-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)|  
|[SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md)||||||[すべてのドライバー](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)|  
|[SQLStatistics](../../odbc/reference/syntax/sqlstatistics-function.md)|[Access (アクセス)](../../odbc/microsoft/sqlstatistics-access-driver.md)|[Dbase](../../odbc/microsoft/sqlstatistics-dbase-driver.md)|[パラドックス](../../odbc/microsoft/sqlstatistics-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqlstatistics-text-file-driver.md)|[Excel](../../odbc/microsoft/sqlstatistics-excel-driver.md)||  
|[SQLTables](../../odbc/reference/syntax/sqltables-function.md)|[Access (アクセス)](../../odbc/microsoft/sqltables-access-driver.md)|[Dbase](../../odbc/microsoft/sqltables-dbase-driver.md)|[パラドックス](../../odbc/microsoft/sqltables-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqltables-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltables-excel-driver.md)|  
|[トランスアクト](../../odbc/reference/syntax/sqltransact-function.md)|[Access (アクセス)](../../odbc/microsoft/sqltransact-access-driver.md)|[Dbase](../../odbc/microsoft/sqltransact-dbase-driver.md)|[パラドックス](../../odbc/microsoft/sqltransact-paradox-driver.md)|[テキスト ファイル](../../odbc/microsoft/sqltransact-text-file-driver.md)|[Excel](../../odbc/microsoft/sqltransact-excel-driver.md)||  
  
 次のトピックでは、ODBC 関数に関する解説を提供します。 これらの説明は、すべての ODBC デスクトップ データベース ドライバに適用されます。  
  
-   [SQLGetData (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlgetdata-desktop-database-drivers.md)  
  
-   [オプション (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlgetstmtoption-desktop-database-drivers.md)  
  
-   [SQLMoreResults (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlmoreresults-desktop-database-drivers.md)  
  
-   [SQLPrepare (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlprepare-desktop-database-drivers.md)  
  
-   [SQLProcedures (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlprocedures-desktop-database-drivers.md)  
  
-   [SQLSetCursorName (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlsetcursorname-desktop-database-drivers.md)  
  
-   [SQLSetPos (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlsetpos-desktop-database-drivers.md)  
  
-   [SQLSetScrollOptions (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlsetscrolloptions-desktop-database-drivers.md)  
  
-   [SQLSetStmtOption (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlsetstmtoption-desktop-database-drivers.md)  
  
-   [SQLSpecialColumns (デスクトップ データベース ドライバー)](../../odbc/microsoft/sqlspecialcolumns-desktop-database-drivers.md)
