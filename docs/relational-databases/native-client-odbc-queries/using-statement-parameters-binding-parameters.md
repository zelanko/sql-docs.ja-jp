---
title: "パラメーターをバインド |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-queries
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
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
caps.latest.revision: "31"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 6f94d2fe217f63e522b8a3d49196e13da0e12451
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="using-statement-parameters---binding-parameters"></a>ステートメント パラメーターのバインド パラメーターの使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  SQL ステートメントの各パラメーター マーカーは、ステートメントを実行する前にアプリケーション内の変数に関連付ける、つまりバインドする必要があります。 これは、呼び出すことで、 [SQLBindParameter](../../relational-databases/native-client-odbc-api/sqlbindparameter.md)関数。 **SQLBindParameter**ドライバーにプログラム変数 (アドレス、C データ型など) について説明します。 また、序数値を示すことでパラメーター マーカーを識別してから、そのパラメーター マーカーが表す SQL オブジェクト表現 (SQL データ型、有効桁数など) を記述します。  
  
 パラメーター マーカーは、ステートメントの実行前にいつでもバインドまたは再バインドできます。 次のいずれかの操作を行うまでは、パラメーターのバインドは有効なままです。  
  
-   呼び出し[SQLFreeStmt](../../relational-databases/native-client-odbc-api/sqlfreestmt.md)で、*オプション*SQL_RESET_PARAMS に設定するパラメーターが、ステートメント ハンドルにバインドされているすべてのパラメーターを解放します。  
  
-   呼び出し**SQLBindParameter**で*ParameterNumber*バインドされたパラメーター マーカーの序数を設定が自動的に以前のバインドを解放します。  
  
 アプリケーションでは、パラメーターをプログラム変数の配列にバインドし、SQL ステートメントをバッチで処理することもできます。 配列のバインドには、次の 2 種類があります。  
  
-   列方向のバインドは、各パラメーターを変数の独自の配列にバインドすることで行います。  
  
     呼び出して、列方向のバインドが指定されて[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)で*属性*SQL_ATTR_PARAM_BIND_TYPE に設定し、 *ValuePtr* SQL_PARAM_BIND_BY_COLUMN に設定します。  
  
-   行方向のバインドは、SQL ステートメント内のすべてのパラメーターを 1 単位として、パラメーターの各変数を保持する構造体の配列にバインドすることで行います。  
  
     呼び出して、行方向のバインドが指定されて**SQLSetStmtAttr**で*属性*SQL_ATTR_PARAM_BIND_TYPE に設定し、 *ValuePtr*保留されている構造体のサイズに設定、プログラム変数。  
  
 ときに、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーが文字またはバイナリ文字列パラメーターをサーバーに送信で指定された長さの値を埋めます**SQLBindParameter** *ColumnSize*パラメーター。 ODBC 2.x アプリケーションの場合は 0 を指定する場合*ColumnSize*ドライバーはデータ型の有効桁数のパラメーターの値を埋めます。 有効桁数は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバーに接続している場合は 8,000、以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続している場合は 255 です。 *ColumnSize*はバリアント型の列のバイト単位です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ストアド プロシージャ パラメーターの名前を定義できます。 また、ODBC 3.5 では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ストアド プロシージャを呼び出すときに使用する名前付きパラメーターのサポートも導入されました。 このサポートは次の目的に使用します。  
  
-   ストアド プロシージャを呼び出し、そのストアド プロシージャ用に定義したパラメーターのサブセットに値を提供します。  
  
-   アプリケーション内で、ストアド プロシージャの作成時に指定した順序とは異なる順序でパラメーターを指定します。  
  
 名前付きパラメーターを使用する場合のみサポート、 [!INCLUDE[tsql](../../includes/tsql-md.md)] **EXECUTE**ステートメントまたはストアド プロシージャを実行する ODBC CALL エスケープ シーケンスです。  
  
 場合**SQL_DESC_NAME**設定されているストアド プロシージャのパラメーター、クエリのすべてのストアド プロシージャ パラメーターを設定する必要がありますも**SQL_DESC_NAME**です。  かどうかリテラルは、使用、ストアド プロシージャの呼び出しでパラメーターのある**SQL_DESC_NAME**形式を使用して、リテラルの必要がありますを設定すると、 *' 名*=*値*'、ここで*名前*ストアド プロシージャのパラメーター名は、(たとえば、 @p1)。 詳細については、次を参照してください。[名前 (名前付きパラメーター) でのパラメーターのバインド](http://go.microsoft.com/fwlink/?LinkId=167215)です。  
  
## <a name="see-also"></a>参照  
 [ステートメント パラメーターの使用](../../relational-databases/native-client-odbc-queries/using-statement-parameters.md)  
  
  
