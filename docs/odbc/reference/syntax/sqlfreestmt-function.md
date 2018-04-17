---
title: SQLFreeStmt 関数 |Microsoft ドキュメント
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
ms.topic: article
apiname:
- SQLFreeStmt
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFreeStmt
helpviewer_keywords:
- SQLFreeStmt function [ODBC]
ms.assetid: 03408162-8b63-4470-90c4-e6c7d8d33892
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6f2f3e9021732f7d6b58e4d14641ae7874bf4c4e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlfreestmt-function"></a>SQLFreeStmt 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLFreeStmt**特定のステートメントに関連付けられている処理を停止する、保留中の結果、破棄、ステートメントに関連付けられた開いているカーソルを閉じますか、必要に応じて、ステートメント ハンドルに関連付けられているすべてのリソースを解放します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLFreeStmt(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Option);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドル  
  
 *オプション*  
 [入力]次のオプションのいずれかです。  
  
 Sql _ 閉じる: に関連付けられているカーソルを閉じて*StatementHandle* (定義されている) 場合し、保留中のすべての結果を破棄します。 アプリケーションをもう一度開くこのカーソル後で実行することによって、**選択**同じまたは異なるパラメーター値を使用してステートメントです。 カーソルが開いていない場合は、このオプションは、アプリケーションの影響を与えません。 **SQLCloseCursor**カーソルを閉じるには呼び出すこともできます。 詳細については、次を参照してください。[カーソルを閉じる](../../../odbc/reference/develop-app/closing-the-cursor.md)です。  
  
 SQL_DROP: このオプションは推奨されません。 呼び出し**SQLFreeStmt**で、*オプション*SQL_DROP のマップをドライバー マネージャーで[SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)です。  
  
 SQL_UNBIND: によってバインドされるセットのすべての列バッファーを解放する 0 に ARD SQL_DESC_COUNT フィールド**SQLBindCol**の指定された*StatementHandle*です。 これは、バインドは解除されませんブックマーク列です。ブックマーク列を ARD の SQL_DESC_DATA_PTR フィールドは NULL に設定されます。 複数のステートメントによって共有されている明示的に割り当てられた記述子でこの操作を実行すると、操作に影響すること、記述子を共有するすべてのステートメントのバインディングに注意してください。 詳細については、次を参照してください。[の概要を取得する結果の (基本)](../../../odbc/reference/develop-app/retrieving-results-basic.md)です。  
  
 SQL_RESET_PARAMS: 0 に設定すべてのパラメーター バッファーを解放する APD の SQL_DESC_COUNT フィールドを設定する**SQLBindParameter**の指定された*StatementHandle*です。 複数のステートメントによって共有されている明示的に割り当てられた記述子でこの操作を実行すると、この操作は、記述子を共有するすべてのステートメントのバインドに反映されます。 詳細については、次を参照してください。[パラメーターのバインド](../../../odbc/reference/develop-app/binding-parameters-odbc.md)です。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLFreeStmt** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLFreeStmt**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数ではときに実行されている**SQLFreeStmt**が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 この関数が呼び出された*オプション*ストリーミングのすべてのパラメーターのデータが取得される前に SQL_RESET_PARAMS に設定します。<br /><br /> (DM) の非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY092|範囲外のオプションの種類|引数の指定された値 (DM)*オプション*でした。<br /><br /> SQL_CLOSE SQL_DROP SQL_UNBIND SQL_RESET_PARAMS|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 呼び出す**SQLFreeStmt** with、SQL_CLOSE オプションは、呼び出すことと同じ**SQLCloseCursor**する点を除いて、 **SQLFreeStmt** SQL_CLOSE には影響しません、アプリケーションステートメントで開いているカーソルがない場合。 カーソルがない場合開くへの呼び出し**SQLCloseCursor** SQLSTATE 24000 (無効なカーソルの状態) を返します。  
  
 解放するとします。 アプリケーションが、ステートメント ハンドルを使用しないでください。ドライバー マネージャーは、関数呼び出しでハンドルの有効性をチェックしません。  
  
## <a name="example"></a>例  
 ハンドルを解放することをお勧めプログラミングすることをお勧めします。 ただし、便宜上、次の例はハンドルの割り当てを解放するコードを含まれません。 ハンドルを解放する方法の例は、次を参照してください。 [SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)です。  
  
```  
// SQLFreeStmt.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
  
int main() {  
   // declare and initialize the environment, connection, statement handles  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR *)"Driver={SQL Server}", SQL_NTS, connStrbuffer, 1024 + 1, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   retCode = SQLFreeStmt(hstmt, SQL_CLOSE);  
   retCode = SQLFreeStmt(hstmt, SQL_UNBIND);  
   retCode = SQLFreeStmt(hstmt, SQL_RESET_PARAMS);  
}  
```  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ハンドルの割り当てください。|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|カーソルを閉じる|[SQLCloseCursor 関数](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|ハンドルを解放します。|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|カーソル名の設定|[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
