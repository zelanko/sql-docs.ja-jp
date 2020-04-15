---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFreeStmt
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFreeStmt
helpviewer_keywords:
- SQLFreeStmt function [ODBC]
ms.assetid: 03408162-8b63-4470-90c4-e6c7d8d33892
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e252769c26a5491100094b1243b9c2c6bb67d94d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285702"
---
# <a name="sqlfreestmt-function"></a>SQLFreeStmt 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLFreeStmt は**、特定のステートメントに関連付けられた処理を停止し、そのステートメントに関連付けられたオープン・カーソルをクローズし、保留結果を破棄するか、またはオプションでステートメント・ハンドルに関連付けられたすべてのリソースを解放します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLFreeStmt(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Option);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル  
  
 *オプション*  
 [入力]次のいずれかのオプション:  
  
 SQL_ CLOSE:*ステートメントハンドル*に関連付けられたカーソルを閉じ (定義されている場合)、保留中のすべての結果を破棄します。 アプリケーションは、同じまたは異なるパラメーター値を使用して**SELECT**ステートメントを再度実行することにより、後でこのカーソルを再オープンできます。 カーソルがオープンされていない場合、このオプションはアプリケーションに対して何の効果も持たなくなります。 **カーソルを閉じるには、SQLCloseCursor**を呼び出すこともできます。 詳細については、「[カーソルを閉じる」を](../../../odbc/reference/develop-app/closing-the-cursor.md)参照してください。  
  
 SQL_DROP: このオプションは非推奨です。 SQL_DROP*オプションを指定*した**SQLFreeStmt**への呼び出しは、ドライバー マネージャーで[SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)にマップされます。  
  
 SQL_UNBIND: 指定された*ステートメント ハンドル*に対して**SQLBindCol**によってバインドされたすべての列バッファーを解放する、ARD のSQL_DESC_COUNT フィールドを 0 に設定します。 これにより、ブックマーク列のバインドは解除されません。そのためには、ブックマーク列の ARD のSQL_DESC_DATA_PTRフィールドが NULL に設定されます。 この操作が、複数のステートメントで共有される明示的に割り当てられた記述子に対して実行される場合、その操作は記述子を共有するすべてのステートメントのバインディングに影響を与えます。 詳細については、「[結果の取得の概要 (基本)](../../../odbc/reference/develop-app/retrieving-results-basic.md)」を参照してください。  
  
 SQL_RESET_PARAMS: APD のSQL_DESC_COUNT フィールドを 0 に設定し、指定された*ステートメント ハンドル*に対して**SQLBindParameter**によって設定されたすべてのパラメーター バッファーを解放します。 この操作が、複数のステートメントによって共有される明示的に割り当てられた記述子に対して実行される場合、この操作は記述子を共有するすべてのステートメントのバインディングに影響を与えます。 詳細については、「[パラメータのバインド](../../../odbc/reference/develop-app/binding-parameters-odbc.md)」を参照してください。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLFreeStmt**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は、通常**SQLFreeStmt**によって返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLFreeStmt**が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、すべてのストリーミング パラメータに対してデータが取得される前に *、Option*をSQL_RESET_PARAMSに設定して呼び出されました。<br /><br /> (DM) 非同期に実行される関数が呼び出されました、 *StatementHandle、* この関数が呼び出されたときに実行されています。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY092|オプションの種類が範囲外です|(DM)*引数 Option*に指定された値は、次の値ではありませんでした。<br /><br /> SQL_UNBINDSQL_RESET_PARAMSSQL_DROPSQL_CLOSE|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 SQL_CLOSEオプションを指定して**SQLFreeStmt**を呼び出すことは、ステートメントでカーソルがオープンされていない場合に、SQL_CLOSEを持つ**SQLFreeStmt**がアプリケーションに影響を与えない点を除いて **、SQLCloseCursor**を呼び出すのと同じです。 カーソルがオープンされていない場合 **、SQLCloseCursor**を呼び出すと SQLSTATE 24000 (無効なカーソル状態) が返されます。  
  
 アプリケーションは、解放された後はステートメント ハンドルを使用しないでください。ドライバー マネージャーは、関数呼び出しでハンドルの有効性をチェックしません。  
  
## <a name="example"></a>例  
 ハンドルを解放するには、プログラミングの習慣として適しています。 ただし、簡略化のため、次のサンプルには割り当てられたハンドルを解放するコードは含まれていません。 ハンドルを解放する方法の例については、 [SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)を参照してください。  
  
```cpp  
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
  
|対象|参照先|  
|---------------------------|---------|  
|ハンドルの割り当て|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|カーソルを閉じる|[SQLCloseCursor 関数](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|ハンドルを解放する|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|カーソル名の設定|[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
