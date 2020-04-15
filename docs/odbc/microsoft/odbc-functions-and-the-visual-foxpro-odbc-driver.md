---
title: ODBC 関数とビジュアル フォックスプロ ODBC ドライバー |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC level 2 API functions [ODBC]
- ODBC level 1 API functions [ODBC]
- functions [ODBC], API
- ODBC API functions [ODBC]
- level 1 API functions [ODBC]
- API functions [ODBC]
- core level API functions [ODBC]
- level 2 API functions [ODBC]
- ODBC core level API functions [ODBC]
ms.assetid: 512f9cee-ffad-439b-b612-b49c34c32658
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 26bb1f24a7dbb307d3048b8ec2a8ae293ddbe7ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298102"
---
# <a name="odbc-functions-and-the-visual-foxpro-odbc-driver"></a>ODBC 関数と Visual FoxPro ODBC ドライバー
このセクションのトピックでは、ODBC API 関数の概要と、Visual FoxPro 固有の詳細について説明します。  
  
> [!NOTE]  
>  ODBC 関数の一般情報については[、『ODBC](../../odbc/reference/syntax/odbc-api-reference.md)プログラマ ガイド』の ODBC API リファレンスを参照してください。  
  
 ここでは、ODBC API 関数は、コア レベル API 関数、レベル 1 API 関数、およびレベル 2 API 関数の 3 つの主要なカテゴリに分かれています。  
  
> [!NOTE]  
>  いくつかの関数は、データ ソースが[空きテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)(.dbf ファイル) のディレクトリへの接続として定義されているか、Visual FoxPro[データベース](../../odbc/microsoft/visual-foxpro-terminology.md)(.dbc ファイル) への接続として定義されているかによって異なります。 一部の操作は、データベース接続でのみサポートされます。  
  
## <a name="core-level-api-support"></a>コア レベル API のサポート  
 次の表に、ODBC コア レベル API 関数を示します。 これらの関数はすべて、ビジュアル フォックスプロ ODBC ドライバーでサポートされています。  
  
|||  
|-|-|  
|[コネクト](../../odbc/microsoft/sqlallocconnect-visual-foxpro-odbc-driver.md)|[SQLExecute](../../odbc/microsoft/sqlexecute-visual-foxpro-odbc-driver.md)|  
|[SQLAllocEnv](../../odbc/microsoft/sqlallocenv-visual-foxpro-odbc-driver.md)|[SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md)|  
|[をクリックします。](../../odbc/microsoft/sqlallocstmt-visual-foxpro-odbc-driver.md)|[コネクト](../../odbc/microsoft/sqlfreeconnect-visual-foxpro-odbc-driver.md)|  
|[SQLBindCol](../../odbc/microsoft/sqlbindcol-visual-foxpro-odbc-driver.md)|[を実行する](../../odbc/microsoft/sqlfreeenv-visual-foxpro-odbc-driver.md)|  
|[SQLCancel](../../odbc/microsoft/sqlcancel-visual-foxpro-odbc-driver.md)|[SQLFreeStmt](../../odbc/microsoft/sqlfreestmt-visual-foxpro-odbc-driver.md)|  
|[属性](../../odbc/microsoft/sqlcolattributes-visual-foxpro-odbc-driver.md)|[SQLGetCursorName](../../odbc/microsoft/sqlgetcursorname-visual-foxpro-odbc-driver.md)|  
|[SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md)|[SQLNumResultCols](../../odbc/microsoft/sqlnumresultcols-visual-foxpro-odbc-driver.md)|  
|[SQLDescribeCol](../../odbc/microsoft/sqldescribecol-visual-foxpro-odbc-driver.md)|[SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md)|  
|[接続解除](../../odbc/microsoft/sqldisconnect-visual-foxpro-odbc-driver.md)|[SQLRowCount](../../odbc/microsoft/sql-row-count-visual-foxpro-odbc-driver.md)|  
|[エラー](../../odbc/microsoft/sqlerror-visual-foxpro-odbc-driver.md)|[カーソルを設定します。](../../odbc/microsoft/sqlsetcursorname-visual-foxpro-odbc-driver.md)|  
|[SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)|[トランスアクト](../../odbc/microsoft/sqltransact-visual-foxpro-odbc-driver.md)|  
  
## <a name="level-1-api-support"></a>レベル 1 API のサポート  
 次の表に、ODBC レベル 1 の API 関数を示します。 これらの関数はすべて、Visual FoxPro ODBC ドライバーによって完全または部分的にサポートされています。  
  
|||  
|-|-|  
|[SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md)|[SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md)|  
|[SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)|[SQLParamData](../../odbc/microsoft/sqlparamdata-visual-foxpro-odbc-driver.md)|  
|[SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)|[SQLPutData](../../odbc/microsoft/sqlputdata-visual-foxpro-odbc-driver.md)|  
|[オプションを指定します。](../../odbc/microsoft/sqlgetconnectoption-visual-foxpro-odbc-driver.md)|[オプションを指定します。](../../odbc/microsoft/sqlsetconnectoption-visual-foxpro-odbc-driver.md)|  
|[SQLGetData](../../odbc/microsoft/sqlgetdata-visual-foxpro-odbc-driver.md)|[オプションを設定します。](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md)|  
|[SQLGetFunctions](../../odbc/microsoft/sqlgetfunctions-visual-foxpro-odbc-driver.md)|[SQLSpecialColumns](../../odbc/microsoft/sqlspecialcolumns-visual-foxpro-odbc-driver.md)|  
|[SQLGetInfo](../../odbc/microsoft/sqlgetinfo-visual-foxpro-odbc-driver.md)|[SQLStatistics](../../odbc/microsoft/sqlstatistics-visual-foxpro-odbc-driver.md)|  
|[オプションを指定します。](../../odbc/microsoft/sqlgetstmtoption-visual-foxpro-odbc-driver.md)|[SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)|  
  
## <a name="level-2-api-support"></a>レベル 2 API サポート  
 次の ODBC レベル 2 API 関数は、完全または部分的にサポートされています。  
  
-   [データベースソース](../../odbc/microsoft/sqldatasources-visual-foxpro-odbc-driver.md)  
  
-   [SQLDrivers](../../odbc/microsoft/sqldrivers-visual-foxpro-odbc-driver.md)  
  
-   [フェッチ](../../odbc/microsoft/sqlextendedfetch-visual-foxpro-odbc-driver.md)  
  
-   [SQLMoreResults](../../odbc/microsoft/sqlmoreresults-visual-foxpro-odbc-driver.md)  
  
-   [SQLNumParams](../../odbc/microsoft/sqlnumparams-visual-foxpro-odbc-driver.md)  
  
-   [オプション](../../odbc/microsoft/sqlparamoptions-visual-foxpro-odbc-driver.md)  
  
-   [SQLPrimaryKeys](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md)  
  
-   [SQLSetPos](../../odbc/microsoft/sqlsetpos-visual-foxpro-odbc-driver.md)  
  
-   [スクロールオプション](../../odbc/microsoft/sqlsetscrolloptions-visual-foxpro-odbc-driver.md)(部分的なサポート)  
  
 次のレベル 2 API 関数はサポートされていません。  
  
-   SQLBrowseConnect  
  
-   SQLColumnPrivileges  
  
-   SQLDescribeParam  
  
-   SQLForeignKeys  
  
-   SQLNativeSql  
  
-   SQLProcedureColumns  
  
-   SQLProcedures  
  
-   SQLTablePrivileges
