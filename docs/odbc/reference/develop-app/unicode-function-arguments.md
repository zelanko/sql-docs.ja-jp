---
title: Unicode 関数の引数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1fee0aa76bc5b903d65461261a8eb5dbc2349581
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68087763"
---
# <a name="unicode-function-arguments"></a>Unicode 関数の引数
ODBC 3.5 (またはそれ以降) のドライバー マネージャーは、その引数の文字の文字列または SQLPOINTER へのポインターをそのまま使用するすべての関数の ANSI および Unicode の両方のバージョンをサポートします。 Unicode 関数の関数として実装されます (のサフィックスを持つ*W*) マクロではなく、します。 ANSI 関数 (サフィックスの有無を呼び出すことが*A*) は、現在の ODBC API 関数と同じです。  
  
## <a name="remarks"></a>コメント  
 常に返すか、文字列または長の引数を取得する Unicode 関数は、文字の数をカウントとして渡されます。 サーバーのデータの長さの情報を返す関数の場合、文字数で表示サイズと有効桁数がについて説明します。 長さ (データの転送サイズ) は、文字列または文字列以外のデータを参照できます、オクテット長の長さが説明します。 たとえば、 **SQLGetInfoW**バイト数と長さが、実行中は**SQLExecDirectW**文字の数をカウントを使用します。  
  
 文字の数をカウントには、ANSI 関数 (オクテット) のバイト数および UNICODE 関数の WCHAR (16 ビット ワード) の数を指します。 具体的には、2 バイト文字のシーケンス (DBCS) またはマルチバイト文字シーケンス (MBCS) の複数のバイトを構成できます。 複数の WCHARs の utf-16 Unicode 文字のシーケンスを構成できます。  
  
 Unicode (W) および ANSI (A) の両方のバージョンをサポートする ODBC API 関数の一覧を次には。  
  
|||  
|-|-|  
|**SQLBrowseConnect**|**SQLGetDiagField**|  
|**SQLColAttribute**|**SQLGetDiagRec**|  
|**SQLColAttributes**|**SQLGetInfo**|  
|**SQLColumnPrivileges**|**SQLGetStmtAttr**|  
|**SQLColumns**|**SQLNativeSQL**|  
|**SQLConnect**|**SQLPrepare**|  
|**SQLDataSources**|**SQLPrimaryKeys**|  
|**SQLDescribeCol**|**SQLProcedureColumns**|  
|**SQLDriverConnect**|**SQLProcedures**|  
|**SQLDrivers**|**SQLSetConnectAttr**|  
|**Sqlerror 関数**|**SQLSetConnectOption**|  
|**SQLExecDirect**|**SQLSetCursorName**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**SQLGetConnectOption**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
  
 次は Unicode (W) および ANSI (A) の両方のバージョンをサポートする ODBC インストーラーと ODBC トランスレーター関数の一覧です。  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**SQLInstallDriverManager**|  
|**SQLCreateDataSource**|**SQLInstallerError**|  
|**SQLDataSourceToDriver**|**SQLInstallODBC**|  
|**SQLDriverToDataSource**|**SQLReadFileDSN**|  
|**SQLGetAvailableDrivers**|**SQLRemoveDSNFromINI**|  
|**SQLGetInstalledDrivers**|**SQLValidDSN**|  
|**SQLGetTranslator**|**SQLWriteDSNToINI**|  
|**SQLInstallDriver**||  
  
> [!NOTE]
>  非推奨の関数には Unicode から ANSI マッピングのサポートがあるため、ODBC *3.x*ドライバー マネージャーは、ODBC を再コンパイルをサポートしている*2.x* 、UNICODE を使用したアプリケーション **#define**.  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Unicode アプリケーション](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Unicode ドライバー](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [ドライバー マネージャーの関数マッピング](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
