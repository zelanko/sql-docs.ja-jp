---
title: ユニコード関数の引数 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a25dd6fe0a77aad5c5ec9ba15eaf12bd2ec3fc18
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81284292"
---
# <a name="unicode-function-arguments"></a>Unicode 関数の引数
ODBC 3.5 (またはそれ以降) ドライバ マネージャは、引数に文字列または SQLPOINTER へのポインタを受け入れるすべての関数の ANSI バージョンと Unicode バージョンの両方をサポートします。 Unicode 関数は、マクロとしてではなく、関数として実装されます (W*のサフィックス*を持つ)。 ANSI 関数 *(A*のサフィックスを付けても使用しなくても呼び出すことができます) は、現在の ODBC API 関数と同じです。  
  
## <a name="remarks"></a>解説  
 文字列または長さの引数を常に返す、または受け取る Unicode 関数は、文字数のカウントとして渡されます。 サーバー・データの長さ情報を戻す関数の場合、表示サイズと精度は文字数で記述されます。 長さ (データの転送サイズ) がストリングまたは非ストリング・データを参照できる場合、長さはオクテットの長さで記述されます。 たとえば **、SQLGetInfoW**はバイト数として長さを引き続き受け取りますが **、SQLExecDirectW**は文字数を使用します。  
  
 文字数は、ANSI 関数のバイト数 (オクテット) と UNICODE 関数の WCHAR (16 ビットワード) の数を指します。 特に、2 バイト文字シーケンス (DBCS) またはマルチバイト文字シーケンス (MBCS) は、複数バイトで構成できます。 UTF-16 ユニコード文字シーケンスは、複数の WCHA で構成できます。  
  
 次に、Unicode (W) バージョンと ANSI (A) バージョンの両方をサポートする ODBC API 関数の一覧を示します。  
  
|||  
|-|-|  
|**SQLBrowseConnect**|**SQLGetDiagRec**|  
|**SQLColAttribute**|**SQLGetInfo**|  
|**属性**|**SQLGetStmtAttr**|  
|**SQLColumnPrivileges**|**SQLGetTypeInfo**|  
|**SQLColumns**|**を実行します。**|  
|**SQLConnect**|**SQLPrepare**|  
|**データベースソース**|**SQLPrimaryKeys**|  
|**SQLDescribeCol**|**SQLProcedureColumns**|  
|**SQLDriverConnect**|**SQLProcedures**|  
|**SQLDrivers**|**SQLSetConnectAttr**|  
|**エラー**|**オプションを指定します。**|  
|**SQLExecDirect**|**カーソルを設定します。**|  
|**SQLForeignKeys**|**SQLSetDescField**|  
|**SQLGetConnectAttr**|**SQLSetStmtAttr**|  
|**オプションを指定します。**|**SQLSpecialColumns**|  
|**SQLGetCursorName**|**SQLStatistics**|  
|**SQLGetDescField**|**SQLTablePrivileges**|  
|**SQLGetDescRec**|**SQLTables**|  
|**SQLGetDiagField**||  
  
 以下は、ユニコード (W) と ANSI (A) の両方のバージョンをサポートする ODBC インストーラ関数と ODBC トランスレータ関数の一覧です。  
  
|||  
|-|-|  
|**SQLConfigDataSource**|**ドライバー マネージャー**|  
|**データ ソースを作成します。**|**エラー**|  
|**ドライバーを使用します。**|**を使用します。**|  
|**データ ソース**|**ファイルを読み取るDSN**|  
|**利用可能なドライバー**|**インスムースDSN**|  
|**ドライバーを取得します。**|**を指定します。**|  
|**トランスレータを取得します。**|**を使用します。**|  
|**ドライバーのインストール**||  
  
> [!NOTE]
>  ODBC *3.x*ドライバー マネージャーは、UNICODE **#define**を使用して ODBC *2.x*アプリケーションの再コンパイルをサポートしているため、非推奨の関数は、Unicode- ansi マッピングのサポートを持っています。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [Unicode アプリケーション](../../../odbc/reference/develop-app/unicode-applications.md)  
  
-   [Unicode ドライバー](../../../odbc/reference/develop-app/unicode-drivers.md)  
  
-   [ドライバー マネージャーの関数マッピング](../../../odbc/reference/develop-app/function-mapping-in-the-driver-manager.md)
