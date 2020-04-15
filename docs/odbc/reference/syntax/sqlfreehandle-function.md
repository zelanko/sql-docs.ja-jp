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
- SQLFreeHandle
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFreeHandle
helpviewer_keywords:
- SQLFreeHandle function [ODBC]
ms.assetid: 17a6fcdc-b05a-4de7-be93-a316f39696a1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0b136dec98a19676aa67c78615d8fe931f62aafa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285773"
---
# <a name="sqlfreehandle-function"></a>SQLFreeHandle 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLFreeHandle**は、特定の環境、接続、ステートメント、または記述子ハンドルに関連付けられているリソースを解放します。  
  
> [!NOTE]
>  この関数は、ハンドルを解放するための汎用関数です。 ODBC 2.0 関数**SQLFreeConnect** (接続ハンドルを解放する) と**SQLFreeEnv** (環境ハンドルを解放するための) を置き換えます。 **ODBC** 3 *.x***では、どちらも**非推奨です。 **また**、ステートメント ハンドルを解放するために、ODBC 2.0 関数**SQLFreeStmt** (SQL_DROP*オプション*) を置き換えます。 詳細については、「コメント」を参照してください。 ODBC 3 *.x*アプリケーションが ODBC 2 *.x*ドライバーを使用して動作している場合にドライバー マネージャーがこの関数をマップする方法の詳細については、「[アプリケーションの下位互換性を確保するための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLFreeHandle(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]**によって**解放されるハンドルの型。 次のいずれかの値を指定する必要があります。  
  
-   SQL_HANDLE_DBC  
  
-   SQL_HANDLE_DBC_INFO_TOKEN  
  
-   SQL_HANDLE_DESC  
  
-   SQL_HANDLE_ENV  
  
-   SQL_HANDLE_STMT  
  
 SQL_HANDLE_DBC_INFO_TOKEN ハンドルは、ドライバー マネージャーとドライバーによってのみ使用されます。 アプリケーションでは、このハンドル型を使用しないでください。 SQL_HANDLE_DBC_INFO_TOKENの詳細については[、「ODBC ドライバーでの接続プール認識の開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)」を参照してください。  
  
 *ハンドル型*がこれらの値の 1 つでない**場合は**、SQL_INVALID_HANDLE返します。  
  
 *Handle*  
 [入力]解放されるハンドル。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
 **SQLFreeHandle が**SQL_ERRORを返す場合、ハンドルは有効です。  
  
## <a name="diagnostics"></a>診断  
 **SQLFreeHandle**がSQL_ERRORを返すときに、関連付けられた SQLSTATE 値は **、SQLFreeHandle**が解放しようとしたができなかったハンドルの診断データ構造体から取得される可能性があります。 次の表は、通常**SQLFreeHandle**によって返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM)*引数 HandleType*がSQL_HANDLE_ENVされ、少なくとも 1 つの接続が割り当て済みまたは接続状態でした。 SQL_HANDLE_DBCの*ハンドル型*を持つ**SQLDisconnect**と**SQLFreeHandle**は、SQL_HANDLE_ENVの*ハンドル*型で**SQLFreeHandle**を呼び出す前に、各接続に対して呼び出す必要があります。<br /><br /> (DM)*引数handleType*がSQL_HANDLE_DBCされ、接続用の**SQLDisconnect**を呼び出す前に関数が呼び出されました。<br /><br /> (DM)*引数*がSQL_HANDLE_DBCされました。 非同期に実行される関数が*Handle*で呼び出され、この関数が呼び出されたときに関数がまだ実行されていました。<br /><br /> (DM)*引数が*SQL_HANDLE_STMTされました。 **ステートメント**ハンドル**を**使用して呼**SQLBulkOperations**び出され、SQL_NEED_DATA**返されました。** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM)*引数が*SQL_HANDLE_STMTされました。 非同期に実行される関数が、ステートメント ハンドルまたは関連付けられた接続ハンドルで呼び出され、この関数が呼び出されたときに関数がまだ実行されていました。<br /><br /> (DM)*引数*がSQL_HANDLE_DESCされました。 関連付けられた接続ハンドルで非同期に実行される関数が呼び出されました。この関数が呼び出されたとき、関数はまだ実行されていました。<br /><br /> (DM) **SQLFreeHandle**が呼び出される前に、すべての補助ハンドルおよびその他のリソースが解放されませんでした。<br /><br /> (DM)*ハンドル*に関連付けられたステートメント ハンドルの 1 つに対して呼び出された、 SQL**実行**クエリ 、**または SQLMoreResultsSQL_PARAM_DATA_AVAILABLESQL_HANDLE_STMT**またはSQL_HANDLE_DESC返されたSQL_PARAM_DATA_AVAILABLE。 **SQLExecDirect** *HandleType* この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。|  
|HY013|メモリ管理エラー|*引数 HandleType*がSQL_HANDLE_STMTまたはSQL_HANDLE_DESCされ、メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY017|自動的に割り振られている記述子ハンドルの使用が無効です。|(DM)*引数*は、自動的に割り当てられた記述子のハンドルに設定されています。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*引数を引数を*SQL_HANDLE_DESCし、ドライバーは ODBC 2 *.x*ドライバーでした。<br /><br /> (DM)*引数 HandleType*がSQL_HANDLE_STMTされ、ドライバが有効な ODBC ドライバではありませんでした。|  
  
## <a name="comments"></a>説明  
 **SQLFreeHandle**は、次のセクションで説明するように、環境、接続、ステートメント、および記述子のハンドルを解放するために使用されます。 ハンドルの一般情報については、「[ハンドル](../../../odbc/reference/develop-app/handles.md)」を参照してください。  
  
 アプリケーションは、解放された後でハンドルを使用しないでください。ドライバー マネージャーは、関数呼び出しでハンドルの有効性をチェックしません。  
  
## <a name="freeing-an-environment-handle"></a>環境ハンドルの解放  
 SQL_HANDLE_ENVの*ハンドル型*で**SQLFreeHandle**を呼び出す前に、アプリケーションは、環境下で割り当てられたすべての接続に対して*ハンドル型*のSQL_HANDLE_DBCを使用して**SQLFreeHandle**を呼び出す必要があります。 それ以外の場合 **、SQLFreeHandle**の呼び出しはSQL_ERRORを返し、環境とアクティブな接続は有効なままです。 詳細については、「[環境ハンドル](../../../odbc/reference/develop-app/environment-handles.md)と[環境ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-the-environment-handle.md)」を参照してください。  
  
 環境が共有環境の場合 *、HandleType* SQL_HANDLE_ENV を指定して**SQLFreeHandle**を呼び出すアプリケーションは、呼び出し後に環境にアクセスできなくなりますが、環境のリソースは必ずしも解放されません。 **SQLFreeHandle**の呼び出しは、環境の参照カウントをデクリメントします。 参照カウントは、ドライバー マネージャーによって保持されます。 ゼロに達しない場合、共有環境は別のコンポーネントによって使用されているため、解放されません。 参照カウントがゼロになると、共有環境のリソースが解放されます。  
  
## <a name="freeing-a-connection-handle"></a>接続ハンドルの解放  
 SQL_HANDLE_DBCの*ハンドル型*で**SQLFreeHandle**を呼び出す前に、アプリケーションは、このハンドルに接続がある場合、接続に対して**SQLDisconnect**を呼び出す必要があります *。* それ以外の場合 **、SQLFreeHandle**の呼び出しはSQL_ERRORを返し、接続は有効なままです。  
  
 詳細については、「[接続ハンドル](../../../odbc/reference/develop-app/connection-handles.md)」および「[データ ソースまたはドライバからの切断](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md)」を参照してください。  
  
## <a name="freeing-a-statement-handle"></a>ステートメント ハンドルの解放  
 SQL_HANDLE_STMT の*ハンドル型*を使用して**SQLFreeHandle**を呼び出すと、SQL_HANDLE_STMTの*HandleType*を使用して**SQLAllocHandle**の呼び出しによって割り当てられたすべてのリソースが解放されます。 アプリケーションが**SQLFreeHandle**を呼び出して、保留中の結果を持つステートメントを解放すると、保留中の結果は削除されます。 アプリケーションがステートメント ハンドルを解放すると、ドライバーは、そのハンドルに関連付けられている 4 つの自動的に割り当てられた記述子を解放します。 詳細については、「ステートメント[ハンドルとステートメント](../../../odbc/reference/develop-app/statement-handles.md)[ハンドルの解放](../../../odbc/reference/develop-app/freeing-a-statement-handle-odbc.md)」を参照してください。  
  
 **SQLDisconnect**は、接続で開いているステートメントと記述子を自動的に削除します。  
  
## <a name="freeing-a-descriptor-handle"></a>記述子ハンドルの解放  
 *ハンドル*型を持つ**SQLFreeHandle**を呼び出すと、ハンドルSQL_HANDLE_DESC*で記述子*ハンドルが解放されます。 **SQLFreeHandle**の呼び出しでは *、Handle*の記述子レコードのポインター フィールド (SQL_DESC_DATA_PTR、SQL_DESC_INDICATOR_PTR、SQL_DESC_OCTET_LENGTH_PTRなど) によって参照される可能性のあるアプリケーションによって割り当てられたメモリは解放されません。 ポインター フィールドではないフィールドのドライバーによって割り当てられたメモリは、ハンドルが解放されたときに解放されます。 ユーザー割り当て記述子ハンドルが解放されると、解放されたハンドルが関連付けられたすべてのステートメントは、自動的に割り当てられたそれぞれの記述子ハンドルに戻ります。  
  
> [!NOTE]
>  ODBC 2 *.x*ドライバーは記述子ハンドルの割り当てをサポートしていないのと同様に、記述子ハンドルの解放をサポートしていません。  
  
 **SQLDisconnect**は、接続で開いているステートメントと記述子を自動的に削除します。 アプリケーションがステートメント ハンドルを解放すると、ドライバーは、そのハンドルに関連付けられているすべての自動生成された記述子を解放します。  
  
 記述子の詳細については、[記述子](../../../odbc/reference/develop-app/descriptors.md)を参照してください。  
  
## <a name="code-example"></a>コード例  
 その他のコード サンプルについては[、「SQL ブラウズ接続](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)と[SQLConnect」](../../../odbc/reference/syntax/sqlconnect-function.md)を参照してください。  
  
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
  
|対象|参照先|  
|---------------------------|---------|  
|ハンドルの割り当て|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|ステートメント処理のキャンセル|[関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|カーソル名の設定|[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [ODBC のサンプル プログラム](../../../odbc/reference/sample-odbc-program.md)
