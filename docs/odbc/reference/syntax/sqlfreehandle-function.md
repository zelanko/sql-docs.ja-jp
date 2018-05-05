---
title: SQLFreeHandle 関数 |Microsoft ドキュメント
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
apiname:
- SQLFreeHandle
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFreeHandle
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
ms.assetid: 17a6fcdc-b05a-4de7-be93-a316f39696a1
caps.latest.revision: 35
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 41ed0af53844edfe55203e8310ce326fb2c4e2b8
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfreehandle-function"></a>SQLFreeHandle 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLFreeHandle**特定の環境、接続、ステートメント、または記述子ハンドルに関連付けられているリソースを解放します。  
  
> [!NOTE]  
>  このハンドルを解放するための汎用関数です。 ODBC 2.0 関数に置き換えられます**SQLFreeConnect** (接続ハンドルを解放) 用と**SQLFreeEnv** (の環境ハンドルを解放)。 **SQLFreeConnect**と**SQLFreeEnv** ODBC 3 で非推奨両方 *.x*です。 **SQLFreeHandle**も ODBC 2.0 関数を置き換えます**SQLFreeStmt** (、SQL_DROP で*オプション*) のステートメント ハンドルを解放します。 詳細については、「コメント」を参照してください。 詳細については、どのようなドライバー マネージャーは、この関数にする際にマップ ODBC 3 *.x* ODBC 2 を利用するアプリケーション *.x*ドライバーを参照してください[後方の置換関数のマッピングアプリケーションの互換性を](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]によって解放されるハンドルの種類**SQLFreeHandle**です。 次の値のいずれかを指定する必要があります。  
  
-   SQL_HANDLE_DBC として  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN ハンドルは、ドライバー マネージャーとドライバーのによってのみ使用されます。 アプリケーションでは、この種類のハンドルは使用しないでください。 SQL_HANDLE_DBC_INFO_TOKEN の詳細については、次を参照してください。 [ODBC ドライバーで接続プールの認識開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)です。  
  
 場合*HandleType*はこれらの値のいずれかの**SQLFreeHandle** SQL_INVALID_HANDLE が返されます。  
  
 *Handle*  
 [入力]解放されるハンドル。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
 場合**SQLFreeHandle**がまだ有効 SQL_ERROR、ハンドル値を取得します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLFreeHandle**ハンドルの診断データの構造体から取得できる SQL_ERROR、関連付けられた SQLSTATE 値を返しますを**SQLFreeHandle**を解放しようとしましたが、見つかりませんでした。 次の表に、によって通常返される SQLSTATE 値**SQLFreeHandle**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM)、 *HandleType*引数が SQL_HANDLE_ENV とには、少なくとも 1 つの接続は、割り当てられた、または接続されている状態にします。 **SQLDisconnect**と**SQLFreeHandle**で、 *HandleType*呼び出す前に各接続の sql_handle_dbc として呼び出す必要があります**SQLFreeHandle**で、*HandleType* SQL_HANDLE_ENV のです。<br /><br /> (DM)、 *HandleType*引数が sql_handle_dbc として、および関数が呼び出す前に呼び出された**SQLDisconnect**接続します。<br /><br /> (DM)、 *HandleType*引数が sql_handle_dbc として。 非同期的に実行中の関数が呼び出されました*処理*関数は、この関数が呼び出されたときに実行されているとします。<br /><br /> (DM)、 *HandleType*引数が SQL_HANDLE_STMT です。 **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**されたステートメント ハンドルで呼び出され、SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM)、 *HandleType*引数が SQL_HANDLE_STMT です。 ステートメント ハンドルで、または、関連付けられている接続ハンドルに非同期的に実行中の関数が呼び出された関数は、この関数が呼び出されたときに実行されている.<br /><br /> (DM)、 *HandleType*引数が SQL_HANDLE_DESC です。 関連付けられた接続ハンドルで非同期的に実行中の関数が呼び出されましたこの関数が呼び出されたとき、関数が実行されています。<br /><br /> (DM) すべての子会社ハンドルおよびその他のリソースが解放されていない前に、 **SQLFreeHandle**が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に関連付けられているステートメント ハンドルのいずれかで呼び出され、*処理*および*HandleType* SQL_HANDLE_STMT を設定または SQL_HANDLE_DESC SQL_PARAM_DATA_AVAILABLE が返されます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|*HandleType*引数が SQL_HANDLE_STMT または SQL_HANDLE_DESC、および基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY017|自動的に割り当てられた記述子ハンドルの使い方が正しくありません。|(DM)、*処理*引数は、自動的に割り当てられた記述子ハンドルに設定されました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM)、 *HandleType*引数 SQL_HANDLE_DESC、れ、ドライバーは ODBC 2 *.x*ドライバー。<br /><br /> (DM)、 *HandleType*引数 SQL_HANDLE_STMT、れ、ドライバーは無効な ODBC ドライバー、でした。|  
  
## <a name="comments"></a>コメント  
 **SQLFreeHandle**使用すると、次のセクションで説明されている、環境、接続、ステートメント、および記述子のハンドルを解放します。 ハンドルに関する概要については、次を参照してください。[ハンドル](../../../odbc/reference/develop-app/handles.md)です。  
  
 解放するとします。 アプリケーションがハンドルを使用しないでください。ドライバー マネージャーは、関数呼び出しでハンドルの有効性をチェックしません。  
  
## <a name="freeing-an-environment-handle"></a>環境ハンドルを解放します。  
 呼び出す前に**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_ENV のアプリケーションを呼び出す必要があります**SQLFreeHandle**で、 *HandleType*の環境で割り当てられているすべての接続を sql_handle_dbc として。 それ以外の場合、呼び出し**SQLFreeHandle** SQL_ERROR と、環境と、アクティブな接続の有効なままを返します。 詳細については、次を参照してください。[環境処理](../../../odbc/reference/develop-app/environment-handles.md)と[環境ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)です。  
  
 環境が共有環境の場合は、アプリケーションを呼び出す**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_ENV の呼び出しの後、環境が環境へのアクセスがなくなったリソースは必ずしもは解放されません。 呼び出し**SQLFreeHandle**環境の参照カウントをデクリメントします。 参照カウントには、ドライバー マネージャーでは維持されます。 0 は達しません場合、共有環境は解放されず、別のコンポーネントはまだ使用されているためです。 参照カウントには、ゼロに達すると、共有環境のリソースが解放されます。  
  
## <a name="freeing-a-connection-handle"></a>接続ハンドルを解放します。  
 呼び出す前に**SQLFreeHandle**で、 *HandleType* sql_handle_dbc としてのアプリケーションを呼び出す必要があります**SQLDisconnect**接続の接続がある場合処理*です。* それ以外の場合、呼び出し**SQLFreeHandle** SQL_ERROR と接続の有効なままを返します。  
  
 詳細については、次を参照してください。[接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)と[データ ソースまたはドライバーからの切断](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md)です。  
  
## <a name="freeing-a-statement-handle"></a>ステートメント ハンドルを解放します。  
 呼び出し**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_STMT への呼び出しによって割り当てられたすべてのリソースを解放**SQLAllocHandle**で、 *HandleType* SQL_HANDLE_STMT のです。 アプリケーションを呼び出すと**SQLFreeHandle**を保留中の結果は、ステートメントを解放するには、保留中の結果が削除されます。 アプリケーションでは、ステートメント ハンドルを解放、ドライバーは、そのハンドルに関連付けられた 4 つ自動的に割り当てられた記述子を解放します。 詳細については、次を参照してください。[ステートメント処理](../../../odbc/reference/develop-app/statement-handles.md)と[ステートメント ハンドルの解放](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md)です。  
  
 注意して**SQLDisconnect**接続でステートメントや開いている記述子が自動的に削除します。  
  
## <a name="freeing-a-descriptor-handle"></a>記述子ハンドルの解放  
 呼び出し**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_DESC の解放で記述子ハンドル*処理*です。 呼び出し**SQLFreeHandle**任意の参照できるは、ポインター フィールド (SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、SQL_DESC_OCTET_LENGTH_PTR など) によって、アプリケーションによって割り当てられたメモリを解放しません記述子レコード*処理*です。 ハンドルが解放されると、ポインター フィールドではないフィールド用のドライバーによって割り当てられたメモリが解放されます。 ユーザーに割り当てられた記述子ハンドルが解放されると、解放されたハンドルが関連付けられているすべてのステートメントは、それぞれ自動的に割り当てられた記述子ハンドルに戻します。  
  
> [!NOTE]  
>  ODBC 2 *.x*記述子ハンドルの割り当てをサポートするいないと同様のドライバーが、記述子ハンドルの解放をサポートしています。  
  
 注意して**SQLDisconnect**接続でステートメントや開いている記述子が自動的に削除します。 アプリケーションでは、ステートメント ハンドルを解放、ドライバーは、そのハンドルに関連付けられているすべての自動生成された記述子を解放します。  
  
 記述子の詳細については、次を参照してください。[記述子](../../../odbc/reference/develop-app/descriptors.md)です。  
  
## <a name="code-example"></a>コード例  
 追加のコード サンプルでは、次を参照してください。 [SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)と[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)です。  
  
### <a name="code"></a>コード  
  
```  
// SQLFreeHandle.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <stdio.h>  
  
int main() {  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
  
   // Initialize the environment, connection, statement handles.  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   // Allocate the environment.  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set environment attributes.  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
  
   // Allocate the connection.  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
   // Set the login timeout.  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
  
   // Let the user select the data source and connect to the database.  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR *)"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1025, &connStrBufferLen, SQL_DRIVER_PROMPT);  
  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // Free handles, and disconnect.     
   if (hstmt) {   
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
      hstmt = NULL;   
   }  
   if (hdbc) {   
      SQLDisconnect(hdbc);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
      hdbc = NULL;   
   }  
   if (henv) {   
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
      henv = NULL;   
   }  
}  
```  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ハンドルの割り当てください。|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|ステートメントの処理を取り消す|[SQLCance Functionl](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|カーソル名の設定|[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC のサンプル プログラム](../../../odbc/reference/sample-odbc-program.md)
