---
title: Unicode 関数の引数 |Microsoft ドキュメント
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
ms.topic: conceptual
helpviewer_keywords:
- Unicode [ODBC], functions
- functions [ODBC], Unicode functions
ms.assetid: eafe8c7e-f6d2-44d7-99ee-cf2148a30f4f
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1267e54f1f0ce50493558be36531138c00a067b9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="unicode-function-arguments"></a>Unicode 関数の引数
ODBC 3.5 (またはそれ以降) のドライバー マネージャーは、ANSI と Unicode の両方の引数の文字列や文字の SQLPOINTER へのポインターをそのまま使用するすべての関数のバージョンをサポートします。 Unicode 関数は、関数として実装されます (のサフィックスを持つ*W*) マクロではなく、します。 ANSI 関数 (のサフィックスの有無を呼び出すことができる*A*) 現在の ODBC API 関数と同じです。  
  
## <a name="remarks"></a>解説  
 常に返したり、文字列、または長の引数を受け取る Unicode 関数は、文字の数をカウントとして渡されます。 サーバーのデータの長さの情報を返す関数、表示サイズと有効桁数に記載されている文字数。 長さ (データの転送サイズ) は、文字列または文字列以外のデータを参照できます、ときに、長さは、オクテットの長さの説明です。 たとえば、 **SQLGetInfoW**バイト数と長さが、実行中は**SQLExecDirectW**の文字の数をカウントを使用します。  
  
 文字の数をカウントには、バイト数 (オクテット) 関数の ANSI および UNICODE 関数の WCHAR (16 ビット ワード) の数を指します。 具体的には、複数のバイトの 2 バイト文字のシーケンス (DBCS) またはマルチバイト文字シーケンス (MBCS) を構成することできます。 複数の WCHARs の utf-16 Unicode 文字のシーケンスを構成できます。  
  
 Unicode (W) や ANSI (A) の両方のバージョンをサポートする ODBC API 関数の一覧を次に示します。  
  
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
|**SQLError**|**SQLSetConnectOption**|  
|**SQLExecDirect**|**SQLSetCursorName**|  
|**SQLForeignKeys**|**Sqlsetdescfield による**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**SQLGetConnectOption**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**Sqlgetdescrec による**|**SQLTables**|  
  
 Unicode (W) や ANSI (A) の両方のバージョンをサポートする ODBC インストーラーと ODBC トランスレーター関数の一覧を次に示します。  
  
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
>  使用されなくなった関数には Unicode から ANSI へのマッピングのサポートがあるため、ODBC 3 *.x*ドライバー マネージャーは、ODBC 2 を再コンパイルをサポートしています*。x* 、UNICODE を使用アプリケーション **#define**です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Unicode アプリケーション](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Unicode ドライバー](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [ドライバー マネージャーの関数マッピング](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
