---
title: SQLFreeHandle 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0ddaae66e60f77156b2d7c7e975875bb78d56cb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537329"
---
# <a name="sqlfreehandle-function"></a>SQLFreeHandle 関数
**準拠**  
 バージョンが導入されました。ODBC 3.0 規格に準拠します。ISO 92  
  
 **まとめ**  
 **SQLFreeHandle**特定の環境、接続、ステートメント、または記述子ハンドルに関連付けられたリソースを解放します。  
  
> [!NOTE]
>  このハンドルを解放するジェネリック関数です。 ODBC 2.0 関数に置き換えられます**SQLFreeConnect** (接続ハンドルを解放) 用と**SQLFreeEnv** (の環境ハンドルを解放)。 **SQLFreeConnect**と**SQLFreeEnv** ODBC 3 で非推奨両方 *.x*します。 **SQLFreeHandle**も ODBC 2.0 関数は置き換えられます**SQLFreeStmt** (、SQL_DROP で*オプション*) のステートメント ハンドルを解放します。 詳細については、「コメントです。」を参照してください。 どのようなドライバー マネージャーは、ときに、マッピングするには、この関数、ODBC 3 の詳細については *.x*アプリケーションの操作は、ODBC 2 *.x*ドライバーを参照してください[後方のマッピング置換関数アプリケーションの互換性を](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]によって解放されるハンドルの型**SQLFreeHandle**します。 値は次のいずれかを指定する必要があります。  
  
-   SQL_HANDLE_DBC として  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV として  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN ハンドルは、ドライバー マネージャーとドライバーでのみ使用されます。 アプリケーションでは、この種類のハンドルは使用しないでください。 SQL_HANDLE_DBC_INFO_TOKEN の詳細については、次を参照してください。 [ODBC ドライバーで接続プールの認識を開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)します。  
  
 場合*HandleType*がこれらの値のいずれかの**SQLFreeHandle** SQL_INVALID_HANDLE が返されます。  
  
 *Handle*  
 [入力]解放するハンドル。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
 場合**SQLFreeHandle**がまだ有効で、ハンドル、SQL_ERROR を返します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLFreeHandle** SQL_ERROR、関連付けられている SQLSTATE 値を返します。 ハンドルの診断データの構造体から取得する**SQLFreeHandle**を解放しようとしましたが、できませんでした。 次の表に、によって返される通常の SQLSTATE 値**SQLFreeHandle** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM)、 *HandleType*引数を sql_handle_env として、少なくとも 1 つの接続が、割り当てられたまたは接続されている状態ででした。 **SQLDisconnect**と**SQLFreeHandle**で、 *HandleType*呼び出す前に、各接続の sql_handle_dbc として呼び出す必要がある**SQLFreeHandle**で、*HandleType* sql_handle_env としての。<br /><br /> (DM)、 *HandleType*引数が sql_handle_dbc として、および関数が呼び出す前に呼び出された**SQLDisconnect**接続します。<br /><br /> (DM)、 *HandleType*引数が sql_handle_dbc として。 非同期的に実行中の関数が呼び出されました*処理*関数は、この関数が呼び出されたときにまだ実行中だったとします。<br /><br /> (DM)、 *HandleType*引数が sql_handle_stmt として。 **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**が、ステートメント ハンドルで呼び出され、SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM)、 *HandleType*引数が sql_handle_stmt として。 ステートメント ハンドルで、または関連付けられている接続ハンドルで非同期的に実行中の関数が呼び出された、この関数が呼び出されたとき、関数が実行されています。<br /><br /> (DM)、 *HandleType*引数が SQL_HANDLE_DESC します。 関連付けられている接続ハンドル; で非同期的に実行中の関数が呼び出されましたこの関数が呼び出されたとき、関数が実行されています。<br /><br /> (DM) ハンドルのすべての関連会社とその他のリソースが解放されていない前に、 **SQLFreeHandle**が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に関連付けられているステートメント ハンドルのいずれかが呼び出された、*処理* *HandleType*を sql_handle_stmt として設定されたまたは SQL_HANDLE_DESC SQL_PARAM_DATA_AVAILABLE が返されます。 ストリームのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|*HandleType*引数が sql_handle_stmt としてまたは SQL_HANDLE_DESC、および基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY017|自動的に割り当てられた記述子ハンドルの使い方が正しくありません。|(DM)、*処理*引数は、自動的に割り当てられた記述子ハンドルに設定されました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM)、 *HandleType*引数が SQL_HANDLE_DESC、およびドライバーが、ODBC 2 *.x*ドライバー。<br /><br /> (DM)、 *HandleType*引数を sql_handle_stmt として、ドライバーは有効な ODBC ドライバーでした。|  
  
## <a name="comments"></a>コメント  
 **SQLFreeHandle**使用すると、次のセクションで説明した、環境、接続、ステートメント、および、記述子のハンドルを解放します。 ハンドルの詳細については、次を参照してください。[ハンドル](../../../odbc/reference/develop-app/handles.md)します。  
  
 解放するとします。 アプリケーションがハンドルを使用しないでください。ドライバー マネージャーでは、関数呼び出しでハンドルの有効性はチェックされません。  
  
## <a name="freeing-an-environment-handle"></a>環境ハンドルの解放  
 呼び出す前に**SQLFreeHandle**で、 *HandleType*を sql_handle_env としてのアプリケーションを呼び出す必要があります**SQLFreeHandle**で、 *HandleType*の環境で割り当てられているすべての接続を sql_handle_dbc として。 それ以外の場合、呼び出し**SQLFreeHandle** SQL_ERROR と、環境と、アクティブな接続が有効なを返します。 詳細については、次を参照してください。[環境処理](../../../odbc/reference/develop-app/environment-handles.md)と[環境ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)します。  
  
 環境が共有環境の場合は、アプリケーションを呼び出す**SQLFreeHandle**で、 *HandleType* sql_handle_env としてが、呼び出しの後に環境が環境へのアクセスが不要になったリソースは、必ずしも解放されません。 呼び出し**SQLFreeHandle**環境の参照カウントをデクリメントします。 参照カウントには、ドライバー マネージャーによっては維持されます。 場合は 0 には到達しません、共有環境は解放されず、まだ別のコンポーネントで使用されているためです。 参照カウントがゼロに達すると、共有環境のリソースが解放されます。  
  
## <a name="freeing-a-connection-handle"></a>接続ハンドルの解放  
 呼び出す前に**SQLFreeHandle**で、 *HandleType*を sql_handle_dbc としてのアプリケーションを呼び出す必要があります**SQLDisconnect**接続の接続がある場合処理*します。* それ以外の場合、呼び出し**SQLFreeHandle** SQL_ERROR と接続の有効なままを返します。  
  
 詳細については、次を参照してください。[接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)と[データ ソースまたはドライバーからの切断](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md)します。  
  
## <a name="freeing-a-statement-handle"></a>ステートメント ハンドルの解放  
 呼び出し**SQLFreeHandle**で、 *HandleType* sql_handle_stmt としてへの呼び出しによって割り当てられたすべてのリソースを解放**SQLAllocHandle**で、 *HandleType* sql_handle_stmt としての。 アプリケーションを呼び出すと**SQLFreeHandle**を保留中の結果を含むステートメントを解放するには、保留中の結果が削除されます。 アプリケーションでは、ステートメント ハンドルを解放、ドライバーは、そのハンドルに関連付けられた 4 つの自動的に割り当てられた記述子を解放します。 詳細については、次を参照してください。[ステートメントが処理](../../../odbc/reference/develop-app/statement-handles.md)と[ステートメント ハンドルの解放](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md)します。  
  
 注意**SQLDisconnect**接続でステートメントや開いている記述子を自動的に削除されます。  
  
## <a name="freeing-a-descriptor-handle"></a>記述子ハンドルの解放  
 呼び出し**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_DESC の記述子ハンドルを解放*処理*します。 呼び出し**SQLFreeHandle**任意のポインターのフィールド (SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、および SQL_DESC_OCTET_LENGTH_PTR を含む) で参照されているアプリケーションによって割り当てられたメモリを解放しません。記述子レコードの*処理*します。 ハンドルが解放されると、ポインター フィールドではないフィールド用のドライバーによって割り当てられたメモリは解放されます。 ユーザーに割り当てられた記述子ハンドルが解放されると、解放されたハンドルが関連付けられているすべてのステートメントは、それぞれ自動的に割り当てられた記述子ハンドルに戻ります。  
  
> [!NOTE]
>  ODBC 2 *.x*記述子ハンドルの割り当てをサポートしていないのと同様のドライバーが、記述子ハンドルの解放をサポートしています。  
  
 注意**SQLDisconnect**接続でステートメントや開いている記述子を自動的に削除されます。 アプリケーションでは、ステートメント ハンドルを解放、ドライバーは、そのハンドルに関連付けられたすべての自動生成された記述子を解放します。  
  
 記述子の詳細については、次を参照してください。[記述子](../../../odbc/reference/develop-app/descriptors.md)します。  
  
## <a name="code-example"></a>コード例  
 追加のコード サンプルでは、次を参照してください。 [SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)と[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)します。  
  
### <a name="code"></a>コード  
  
```cpp  
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
|ステートメントの処理をキャンセル|[SQLCance Functionl](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|カーソル名を設定します。|[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC のサンプル プログラム](../../../odbc/reference/sample-odbc-program.md)
