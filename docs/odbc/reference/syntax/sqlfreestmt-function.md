---
title: SQLFreeStmt 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f3cca214aeb63720e193f57f06a22481ae7d369f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63259319"
---
# <a name="sqlfreestmt-function"></a>SQLFreeStmt 関数
**準拠**  
 バージョンが導入されました。ODBC 1.0 規格に準拠します。ISO 92  
  
 **まとめ**  
 **SQLFreeStmt**特定のステートメントに関連付けられている処理を停止する、保留中の結果、破棄、ステートメントに関連付けられた開いているカーソルを閉じるまたは、必要に応じて、ステートメント ハンドルに関連付けられたすべてのリソースを解放します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLFreeStmt(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Option);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドル  
  
 *Option*  
 [入力]次のオプションのいずれか:  
  
 SQL _ 閉じる:関連付けられているカーソルをクローズ*StatementHandle* (定義されている) 場合と、保留中のすべての結果を破棄します。 アプリケーションが実行することによってこのカーソルを後で再度ことができます、**選択**同じまたは別のパラメーター値を使用してステートメントです。 カーソルが開いていない場合、このオプションは、アプリケーションに影響を与えません。 **SQLCloseCursor**カーソルを閉じるには呼び出すこともできます。 詳細については、次を参照してください。[カーソルを閉じる](../../../odbc/reference/develop-app/closing-the-cursor.md)します。  
  
 SQL_DROP:このオプションは非推奨とされます。 呼び出し**SQLFreeStmt**で、*オプション*SQL_DROP のマップをドライバー マネージャーで[SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)します。  
  
 SQL_UNBIND:によってバインドされるすべての列バッファーを解放する 0 に ARD の SQL_DESC_COUNT フィールド セット**SQLBindCol**の指定された*StatementHandle*します。 これは、バインドは解除されません。 ブックマーク列そのためには、ブックマーク列 ARD の SQL_DESC_DATA_PTR フィールドが NULL に設定されます。 1 つ以上のステートメントによって共有されている、明示的に割り当てられた記述子でこの操作を実行すると、操作に影響する記述子を共有するすべてのステートメントのバインドに注目してください。 詳細については、次を参照してください。[の概要を取得する結果の (Basic)](../../../odbc/reference/develop-app/retrieving-results-basic.md)します。  
  
 SQL_RESET_PARAMS:0 に設定すべてのパラメーター バッファーを解放する、APD の SQL_DESC_COUNT フィールドを設定します**SQLBindParameter**の指定された*StatementHandle*します。 1 つ以上のステートメントによって共有されている、明示的に割り当てられた記述子でこの操作を実行すると、この操作は、記述子を共有するすべてのステートメントのバインディングに反映されます。 詳細については、次を参照してください。[パラメーターのバインド](../../../odbc/reference/develop-app/binding-parameters-odbc.md)します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLFreeStmt** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得できる**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*します。 次の表に、によって返される通常の SQLSTATE 値**SQLFreeStmt** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM) を非同期的に実行中の関数が呼び出された接続ハンドルに関連付けられているため、 *StatementHandle*します。 この非同期関数ではときに実行されている**SQLFreeStmt**が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に対して呼び出された、 *StatementHandle* SQL_PARAM_DATA_ を返されます。ご利用いただけます。 この関数が呼び出すと*オプション*ストリームのすべてのパラメーターのデータが取得される前に SQL_RESET_PARAMS に設定します。<br /><br /> (DM) を非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**に対して呼び出された、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY092|範囲外のオプションの種類|引数に指定された値 (DM)*オプション*でした。<br /><br /> SQL_CLOSE SQL_DROP SQL_UNBIND SQL_RESET_PARAMS|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 呼び出す**SQLFreeStmt** 、SQL_CLOSE オプションは呼び出しに相当**SQLCloseCursor**ことを除いて、 **SQLFreeStmt** SQL_CLOSE ではアプリケーションに影響せず、カーソルがない場合は、ステートメントで開きます。 カーソルがない場合を開くへの呼び出し**SQLCloseCursor** SQLSTATE 24000 (無効なカーソル状態) を返します。  
  
 解放するとします。 アプリケーションが、ステートメント ハンドルを使用しないでください。ドライバー マネージャーでは、関数呼び出しでハンドルの有効性はチェックされません。  
  
## <a name="example"></a>例  
 ハンドルを解放する場合は、適切なプログラミング手法を勧めします。 ただし、わかりやすくするために、次の例はハンドルの割り当てを解放するコードを含まれません。 ハンドルを解放する方法の例は、次を参照してください。 [SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)します。  
  
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
|ステートメントの処理をキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|カーソルを終了します。|[SQLCloseCursor 関数](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|ハンドルの解放|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|カーソル名を設定します。|[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
