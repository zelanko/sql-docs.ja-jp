---
title: バインド パラメータ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 01e179d2abc6ef786f94b6d7938f0e21938c5a59
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304633"
---
# <a name="using-statement-parameters---binding-parameters"></a>ステートメント パラメーターの使用 - パラメーターのバインド
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  SQL ステートメントの各パラメーター マーカーは、ステートメントを実行する前にアプリケーション内の変数に関連付ける、つまりバインドする必要があります。 これは、[関数](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)を呼び出すことによって行われます。 **SQLBindParameter**ドライバーにプログラム変数 (アドレス、C データ型など) を記述します。 また、序数値を示すことでパラメーター マーカーを識別してから、そのパラメーター マーカーが表す SQL オブジェクト表現 (SQL データ型、有効桁数など) を記述します。  
  
 パラメーター マーカーは、ステートメントの実行前にいつでもバインドまたは再バインドできます。 次のいずれかの操作を行うまでは、パラメーターのバインドは有効なままです。  
  
-   *Option*パラメーターを設定して[SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md)を呼び出すと、SQL_RESET_PARAMSに設定されたステートメント ハンドルにバインドされているすべてのパラメーターが解放されます。  
  
-   バインドされたパラメーター・マーカーの序数にパラメーター*番号*が設定された**SQLBindParameter**の呼び出しは、直前のバインディングを自動的に解放します。  
  
 アプリケーションでは、パラメーターをプログラム変数の配列にバインドし、SQL ステートメントをバッチで処理することもできます。 配列のバインドには、次の 2 種類があります。  
  
-   列方向のバインドは、各パラメーターを変数の独自の配列にバインドすることで行います。  
  
     列方向のバインディングは、*属性*を SQL_ATTR_PARAM_BIND_TYPE に設定し *、ValuePtr*を SQL_PARAM_BIND_BY_COLUMN に設定して[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)を呼び出すことによって指定します。  
  
-   行方向のバインドは、SQL ステートメント内のすべてのパラメーターを 1 単位として、パラメーターの各変数を保持する構造体の配列にバインドすることで行います。  
  
     行方向のバインディングは、*属性*を SQL_ATTR_PARAM_BIND_TYPE に設定し *、ValuePtr*をプログラム変数を保持する構造体のサイズに設定して **、 SQLSetStmtAttr**を呼び出すことによって指定されます。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント ODBC ドライバーは、文字またはバイナリ文字列パラメーターをサーバーに送信するときに、**パラメーター SQLBindParameter** *ColumnSize*で指定された長さに値を埋め込みます。 ODBC 2.x アプリケーションで*ColumnSize*に 0 を指定すると、ドライバーはパラメーター値をデータ型の精度に埋め込みます。 有効桁数は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバーに接続している場合は 8,000、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続している場合は 255 です。 *列サイズ*は、バリアント型の列のバイト単位です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ストアド プロシージャ パラメーターの名前を定義できます。 また、ODBC 3.5 では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャを呼び出すときに使用する名前付きパラメーターのサポートも導入されました。 このサポートは次の目的に使用します。  
  
-   ストアド プロシージャを呼び出し、そのストアド プロシージャ用に定義したパラメーターのサブセットに値を提供します。  
  
-   アプリケーション内で、ストアド プロシージャの作成時に指定した順序とは異なる順序でパラメーターを指定します。  
  
 名前付きパラメーターは[!INCLUDE[tsql](../../includes/tsql-md.md)]**、EXECUTE**ステートメントまたは ODBC CALL エスケープ シーケンスを使用してストアド プロシージャを実行する場合にのみサポートされます。  
  
 ストアド プロシージャ パラメータ**にSQL_DESC_NAME**を設定する場合、クエリ内のすべてのストアド プロシージャ パラメータも**SQL_DESC_NAME**設定する必要があります。  パラメータが設定されているストアド プロシージャ呼び出しでリテラルを使用する場合、*name*リテラル**SQL_DESC_NAME**には *'name*=*value*' という形式を使用する必要があります。 @p1 詳細については、「[名前によるパラメーターのバインド (名前付きパラメーター)」](https://go.microsoft.com/fwlink/?LinkId=167215)を参照してください。  
  
## <a name="see-also"></a>参照  
 [ステートメント パラメーターの使用](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
  
