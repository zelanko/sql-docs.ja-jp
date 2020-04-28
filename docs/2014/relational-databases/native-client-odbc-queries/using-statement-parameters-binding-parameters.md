---
title: パラメーターのバインド |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89b124ea6c73b9ebb80ab5a047b6d7e4cafe2e81
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175857"
---
# <a name="binding-parameters"></a>パラメーターのバインド
  SQL ステートメントの各パラメーター マーカーは、ステートメントを実行する前にアプリケーション内の変数に関連付ける、つまりバインドする必要があります。 これは、 [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)関数を呼び出すことによって行われます。 **SQLBindParameter**は、ドライバーへのプログラム変数 (Address、C データ型など) を記述します。 また、序数値を示すことでパラメーター マーカーを識別してから、そのパラメーター マーカーが表す SQL オブジェクト表現 (SQL データ型、有効桁数など) を記述します。

 パラメーター マーカーは、ステートメントの実行前にいつでもバインドまたは再バインドできます。 次のいずれかの操作を行うまでは、パラメーターのバインドは有効なままです。

-   *Option*パラメーターをに設定して[SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md)を呼び出すと、ステートメントハンドルにバインドされているすべてのパラメーターが SQL_RESET_PARAMS 解放されます。

-   *Parameternumber*をバインドされたパラメーターマーカーの序数に設定して**SQLBindParameter**を呼び出すと、前のバインドが自動的に解放されます。

 アプリケーションでは、パラメーターをプログラム変数の配列にバインドし、SQL ステートメントをバッチで処理することもできます。 配列のバインドには、次の 2 種類があります。

-   列方向のバインドは、各パラメーターを変数の独自の配列にバインドすることで行います。

     列方向のバインドは、*属性*を SQL_ATTR_PARAM_BIND_TYPE に設定し、 *valueptr*を SQL_PARAM_BIND_BY_COLUMN に設定して、 [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)を呼び出すことによって指定します。

-   行方向のバインドは、SQL ステートメント内のすべてのパラメーターを 1 単位として、パラメーターの各変数を保持する構造体の配列にバインドすることで行います。

     行方向のバインドは、*属性*を SQL_ATTR_PARAM_BIND_TYPE に設定し、 *valueptr*をプログラム変数を保持する構造体のサイズに設定して、 **SQLSetStmtAttr**を呼び出すことによって指定します。

 Native Client [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC ドライバーは、文字またはバイナリ文字列パラメーターをサーバーに送信するときに、 **SQLBindParameter** *columnsize*パラメーターで指定された長さに値を埋め込みます。 ODBC 2.x アプリケーションで*Columnsize*に0が指定されている場合、ドライバーは、パラメーター値をデータ型の有効桁数に埋め込みます。 有効桁数は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバーに接続している場合は 8,000、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続している場合は 255 です。 バリアント型の列の場合、 *Columnsize*はバイト単位です。

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ストアド プロシージャ パラメーターの名前を定義できます。 また、ODBC 3.5 では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャを呼び出すときに使用する名前付きパラメーターのサポートも導入されました。 このサポートは次の目的に使用します。

-   ストアド プロシージャを呼び出し、そのストアド プロシージャ用に定義したパラメーターのサブセットに値を提供します。

-   アプリケーション内で、ストアド プロシージャの作成時に指定した順序とは異なる順序でパラメーターを指定します。

 名前付きパラメーターは、 [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE`ステートメントまたは ODBC CALL エスケープシーケンスを使用してストアドプロシージャを実行する場合にのみサポートされます。

 ストアド プロシージャ パラメーターに `SQL_DESC_NAME` を設定する場合、クエリ内のすべてのストアド プロシージャ パラメーターにも `SQL_DESC_NAME` を設定する必要があります。  パラメーター `SQL_DESC_NAME`が設定されているストアドプロシージャの呼び出しでリテラルを使用する場合、リテラルでは *' name*=*value*' という形式を使用する必要があります。ここで、 *name*はストアドプロシージャのパラメーター名 (たとえば、 @p1) です。 詳細については、「[名前によるパラメーターのバインド (名前付きパラメーター)](https://go.microsoft.com/fwlink/?LinkId=167215)」を参照してください。

## <a name="see-also"></a>参照
 [ステートメント パラメーターの使用](using-statement-parameters.md)


