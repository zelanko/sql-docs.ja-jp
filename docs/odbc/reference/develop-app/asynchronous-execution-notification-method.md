---
title: 非同期実行 (通知メソッド) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e509dad9-5263-4a10-9a4e-03b84b66b6b3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 250e71dcb47d44a6e437d12c269ea23fa6fb3c2c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306413"
---
# <a name="asynchronous-execution-notification-method"></a>非同期実行 (通知方法)
ODBC では、接続とステートメントの操作を非同期に実行できます。 アプリケーション スレッドは、非同期モードで ODBC 関数を呼び出すことができますし、操作が完了する前に関数を返すことができる、アプリケーション スレッドは、他のタスクを実行できます。 Windows 7 SDK では、非同期ステートメントまたは接続操作の場合、アプリケーションはポーリング メソッドを使用して非同期操作が完了したと判断しました。 詳細については、「[非同期実行 (ポーリング メソッド)」](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)を参照してください。 Windows 8 SDK 以降では、通知メソッドを使用して非同期操作が完了したことを確認できます。  
  
 ポーリング メソッドでは、アプリケーションは操作の状態を必要とするたびに非同期関数を呼び出す必要があります。 通知メソッドはコールバックと同様ADO.NET。 ただし、ODBC では、通知オブジェクトとして Win32 イベントが使用されます。  
  
 ODBC カーソル ライブラリと ODBC 非同期通知は同時に使用できません。 両方の属性を設定すると、SQLSTATE S1119 でエラーが返されます (カーソル ライブラリと非同期通知を同時に有効にすることはできません)。  
  
 ドライバー開発者[向けの情報については、「非同期関数の完了の通知](../../../odbc/reference/develop-driver/notification-of-asynchronous-function-completion.md)」を参照してください。  
  
> [!NOTE]  
>  通知方法は、カーソル ライブラリではサポートされていません。 アプリケーションは、通知メソッドが有効になっているときに、SQLSetConnectAttr を使用してカーソル ライブラリを有効にしようとすると、エラー メッセージを受け取ります。  
  
## <a name="overview"></a>概要  
 ODBC 関数が非同期モードで呼び出されると、コントロールは呼び出し元のアプリケーションにすぐに戻りコードSQL_STILL_EXECUTING戻ります。 アプリケーションは、SQL_STILL_EXECUTING以外の値を返すまで、関数を繰り返しポーリングする必要があります。 ポーリング ループは CPU 使用率を増加させ、多くの非同期シナリオでパフォーマンスが低下します。  
  
 通知モデルを使用すると、ポーリング モデルが無効になります。 アプリケーションは、元の関数を再度呼び出す必要はありません。 [非同期操作を完了するには、SQLCompleteAsync 関数](../../../odbc/reference/syntax/sqlcompleteasync-function.md)を呼び出します。 非同期操作が完了する前にアプリケーションが元の関数を再度呼び出すと、呼び出しは SQLSTATE IM017 (非同期通知モードではポーリングが無効) でSQL_ERRORを返します。  
  
 通知モデルを使用する場合、アプリケーションは**SQLCancel**または**SQLCancelHandle**を呼び出してステートメントまたは接続操作をキャンセルできます。 キャンセル要求が成功すると、ODBC はSQL_SUCCESS返します。 このメッセージは、関数が実際に取り消されたことを示すものではありません。キャンセル要求が処理されたことを示します。 関数が実際に取り消されるかどうかは、ドライバーに依存し、データ ソースに依存します。 操作がキャンセルされた場合、ドライバー マネージャーは、イベントを通知します。 ドライバー マネージャーは、リターン コード バッファーにSQL_ERRORを返し、状態は SQLSTATE HY008 (操作がキャンセルされました) の取り消しが成功したことを示します。 関数が通常の処理を完了した場合、ドライバー マネージャーはSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返します。  
  
### <a name="downlevel-behavior"></a>ダウンレベルの動作  
 この通知が完了した時点でサポートされている ODBC ドライバー マネージャーのバージョンは ODBC 3.81 です。  
  
|アプリケーション ODBC バージョン|ドライバー マネージャーのバージョン|ドライバーのバージョン|動作|  
|------------------------------|----------------------------|--------------------|--------------|  
|任意の ODBC バージョンの新しいアプリケーション|ODBC 3.81|ODBC 3.80 ドライバ|アプリケーションは、ドライバーがこの機能をサポートしている場合、この機能を使用できます、それ以外の場合は、ドライバー マネージャーがエラーになります。|  
|任意の ODBC バージョンの新しいアプリケーション|ODBC 3.81|ODBC 3.80 以前のドライバ|ドライバー マネージャーは、ドライバーがこの機能をサポートしていない場合はエラーが発生します。|  
|任意の ODBC バージョンの新しいアプリケーション|ODBC 3.81 より前|Any|アプリケーションがこの機能を使用すると、古いドライバー マネージャーは、ドライバー固有の属性として新しい属性を参照し、ドライバーがエラーになる必要があります。新しいドライバー マネージャーは、ドライバーにこれらの属性を渡しません。|  
  
 アプリケーションは、この機能を使用する前に、ドライバー マネージャーのバージョンを確認する必要があります。 それ以外の場合、不適切な記述されたドライバーでエラーが発生せず、ドライバー マネージャーのバージョンが ODBC 3.81 より前のバージョンである場合、動作は未定義です。  
  
## <a name="use-cases"></a>例  
 このセクションでは、非同期実行のユース ケースとポーリング メカニズムを示します。  
  
### <a name="integrate-data-from-multiple-odbc-sources"></a>複数の ODBC ソースからのデータの統合  
 データ統合アプリケーションは、複数のデータ ソースから非同期的にデータをフェッチします。 データの一部はリモート データ ソースから取得され、一部のデータはローカル ファイルから取得されます。 非同期操作が完了するまで、アプリケーションを続行できません。  
  
 操作を繰り返しポーリングして完了したかどうかを判断する代わりに、アプリケーションはイベント オブジェクトを作成し、ODBC 接続ハンドルまたは ODBC ステートメント ハンドルに関連付けることができます。 次に、アプリケーションはオペレーティング システムの同期 API を呼び出して、1 つのイベント オブジェクトまたは多くのイベント オブジェクト (ODBC イベントとその他の Windows イベントの両方) を待機します。 ODBC は、対応する ODBC 非同期操作が完了すると、イベント オブジェクトに通知します。  
  
 Windows では、Win32 イベント オブジェクトが使用され、ユーザーに統一されたプログラミング モデルが提供されます。 他のプラットフォームのドライバー マネージャーは、これらのプラットフォームに固有のイベント オブジェクトの実装を使用できます。  
  
 次のコード サンプルでは、接続とステートメントの非同期通知の使用方法を示します。  
  
```  
// This function opens NUMBER_OPERATIONS connections and executes one query on statement of each connection.  
// Asynchronous Notification is used  
  
#define NUMBER_OPERATIONS 5  
int AsyncNotificationSample(void)  
{  
    RETCODE     rc;  
  
    SQLHENV     hEnv              = NULL;  
    SQLHDBC     arhDbc[NUMBER_OPERATIONS]         = {NULL};  
    SQLHSTMT    arhStmt[NUMBER_OPERATIONS]        = {NULL};  
  
    HANDLE      arhDBCEvent[NUMBER_OPERATIONS]    = {NULL};  
    RETCODE     arrcDBC[NUMBER_OPERATIONS]        = {0};  
    HANDLE      arhSTMTEvent[NUMBER_OPERATIONS]   = {NULL};  
    RETCODE     arrcSTMT[NUMBER_OPERATIONS]       = {0};  
  
    rc = SQLAllocHandle(SQL_HANDLE_ENV, NULL, &hEnv);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    rc = SQLSetEnvAttr(hEnv,  
        SQL_ATTR_ODBC_VERSION,  
        (SQLPOINTER) SQL_OV_ODBC3_80,  
        SQL_IS_INTEGER);  
    if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
  
    // Connection operations begin here  
  
    // Alloc NUMBER_OPERATIONS connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_DBC, hEnv, &arhDbc[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable DBC Async on all connection handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE, (SQLPOINTER)SQL_ASYNC_DBC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Application must create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhDBCEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhDBCEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all connection handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetConnectAttr(arhDbc[i], SQL_ATTR_ASYNC_DBC_EVENT, arhDBCEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate connect establishing  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLDriverConnect(arhDbc[i], NULL, (SQLTCHAR*)TEXT("Driver={ODBC Driver 11 for SQL Server};SERVER=dp-srv-sql2k;DATABASE=pubs;UID=sa;PWD=XYZ;"), SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE); // Wait All  
  
    // Complete connect API calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], & arrcDBC[i]);  
    }  
  
    BOOL fFail = FALSE; // Whether some connection openning fails.  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcDBC[i]) )   
            fFail = TRUE;  
    }  
  
    // If some SQLDriverConnect() fail, clean up.  
    if (fFail)  
    {  
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {  
                SQLDisconnect(arhDbc[i]); // This is also async  
            }  
            else  
            {  
                SetEvent(arhDBCEvent[i]); // Previous SQLDriverConnect() failed. No need to call SQLDisconnect().  
            }  
        }  
        WaitForMultipleObjects(NUMBER_OPERATIONS, arhDBCEvent, TRUE, INFINITE);   
        for (int i=0; i<NUMBER_OPERATIONS; i++)  
        {  
            if (SQL_SUCCEEDED(arrcDBC[i]) )   
            {     
                SQLCompleteAsync(SQL_HANDLE_DBC, arhDbc[i], &arrcDBC[i]);; // To Complete  
            }  
        }  
  
        goto Cleanup;  
    }  
  
    // Statement Operations begin here  
  
    // Alloc statement handle  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLAllocHandle(SQL_HANDLE_STMT, arhDbc[i], &arhStmt[i]);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Enable STMT Async on all statement handles  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc = SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_ENABLE, (SQLPOINTER)SQL_ASYNC_ENABLE_ON, SQL_IS_INTEGER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Create event objects  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        arhSTMTEvent[i] = CreateEvent(NULL, FALSE, FALSE, NULL); // Auto-reset, initial state is not-signaled  
        if (!arhSTMTEvent[i]) goto Cleanup;  
    }  
  
    // Enable notification on all statement handles  
    // Event  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        rc= SQLSetStmtAttr(arhStmt[i], SQL_ATTR_ASYNC_STMT_EVENT, arhSTMTEvent[i], SQL_IS_POINTER);  
        if ( !SQL_SUCCEEDED(rc) ) goto Cleanup;  
    }  
  
    // Initiate SQLExecDirect() calls  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLExecDirect(arhStmt[i], (SQLTCHAR*)TEXT("select au_lname, au_fname from authors"), SQL_NTS);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE); // Wait All  
  
    // Now, call SQLCompleteAsync to complete the operation and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return values  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        //Do some binding jobs here, set SQL_ATTR_ROW_ARRAY_SIZE   
    }  
  
    // Now, initiate fetching  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLFetch(arhStmt[i]);  
    }  
  
    // Can do some other staff before calling WaitForMultipleObjects  
    WaitForMultipleObjects(NUMBER_OPERATIONS, arhSTMTEvent, TRUE, INFINITE);   
  
    // Now, to complete the operations and get return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        SQLCompleteAsync(SQL_HANDLE_STMT, arhStmt[i], &arrcSTMT[i]);  
    }  
  
    // Check return code  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if ( !SQL_SUCCEEDED(arrcSTMT[i]) ) goto Cleanup;  
    }  
  
    // USE fetched data here!!  
  
Cleanup:  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhStmt[NUMBER_OPERATIONS])  
        {  
            SQLFreeHandle(SQL_HANDLE_STMT, arhStmt[i]);  
            arhStmt[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhSTMTEvent[i])  
        {  
            CloseHandle(arhSTMTEvent[i]);  
            arhSTMTEvent[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDbc[i])  
        {  
            SQLFreeHandle(SQL_HANDLE_DBC, arhDbc[i]);  
            arhDbc[i] = NULL;  
        }  
    }  
  
    for (int i=0; i<NUMBER_OPERATIONS; i++)  
    {  
        if (arhDBCEvent[i])  
        {  
            CloseHandle(arhDBCEvent[i]);  
            arhDBCEvent[i] = NULL;  
        }  
    }  
  
    if (hEnv)  
    {  
        SQLFreeHandle(SQL_HANDLE_ENV, hEnv);  
        hEnv = NULL;  
    }  
  
    return 0;  
}  
  
```  
  
### <a name="determining-if-a-driver-supports-asynchronous-notification"></a>ドライバーが非同期通知をサポートするかどうかを決定する  
 ODBC アプリケーションは、ODBC ドライバーが非同期通知をサポートするかどうかを[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)を呼び出すことによって判断できます。 ODBC ドライバー マネージャーは、結果として、SQL_ASYNC_NOTIFICATIONを使用してドライバーの**SQLGetInfo**を呼び出します。  
  
```  
SQLUINTEGER InfoValue;  
SQLLEN      cbInfoLength;  
  
SQLRETURN retcode;  
retcode = SQLGetInfo (hDbc,   
                      SQL_ASYNC_NOTIFICATION,   
                      &InfoValue,  
                      sizeof(InfoValue),  
                      NULL);  
if (SQL_SUCCEEDED(retcode))  
{  
if (SQL_ASYNC_NOTIFICATION_CAPABLE == InfoValue)  
      {  
          // The driver supports asynchronous notification  
      }  
      else if (SQL_ASYNC_NOTIFICATION_NOT_CAPABLE == InfoValue)  
      {  
          // The driver does not support asynchronous notification  
      }  
}  
```  
  
### <a name="associating-a-win32-event-handle-with-an-odbc-handle"></a>Win32 イベント ハンドルと ODBC ハンドルの関連付け  
 アプリケーションは、対応する Win32 関数を使用して Win32 イベント オブジェクトを作成します。 アプリケーションは、1 つの Win32 イベント ハンドルを 1 つの ODBC 接続ハンドルまたは 1 つの ODBC ステートメント ハンドルに関連付けることができます。  
  
 接続属性SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLEし、ODBC を非同期モードで実行するかどうか、ODBC が接続ハンドルの通知モードを有効にするかどうかを決定SQL_ATTR_ASYNC_DBC_EVENT。 ステートメント属性SQL_ATTR_ASYNC_ENABLEされ、ODBC が非同期モードで実行されるかどうか、および ODBC がステートメント ハンドルの通知モードを有効にするかどうかを決定SQL_ATTR_ASYNC_STMT_EVENT。  
  
|SQL_ATTR_ASYNC_ENABLEまたはSQL_ATTR_ASYNC_DBC_FUNCTION_ENABLE|SQL_ATTR_ASYNC_STMT_EVENTまたはSQL_ATTR_ASYNC_DBC_EVENT|モード|  
|-------------------------------------------------------------------------|-------------------------------------------------------------------|----------|  
|有効化|非 null|非同期通知|  
|有効化|null|非同期ポーリング|  
|Disable|any|同期|  
  
 アプリケーションは、非同期操作モードを一時的に無効にすることができます。 ODBC は、接続レベルの非同期操作が無効になっている場合、SQL_ATTR_ASYNC_DBC_EVENTの値を無視します。 ステートメント レベルの非同期操作が無効になっている場合、ODBC はSQL_ATTR_ASYNC_STMT_EVENTの値を無視します。  
  
 同期呼び出しの**SQL セットStmtAttr**と**SQL セットコネクトアトトル**  
 -   **SQLSetConnectAttr**は非同期操作をサポートしていますが、SQL_ATTR_ASYNC_DBC_EVENTを設定するための**SQLSetConnectAttr**の呼び出しは常に同期的です。  
  
-   **非同期実行は**サポートされていません。  
  
 エラーアウトシナリオ  
 接続を確立する前に**SQLSetConnectAttr**が呼び出されると、ドライバー マネージャーは、使用するドライバーを決定できません。 そのため、ドライバー マネージャーは **、SQLSetConnectAttr**の成功を返しますが、属性は、ドライバーで設定する準備ができていない可能性があります。 ドライバー マネージャーは、アプリケーションが接続関数を呼び出すときにこれらの属性を設定します。 ドライバー マネージャーは、ドライバーが非同期操作をサポートしていないためにエラーが発生する可能性があります。  
  
 接続属性の継承  
 通常、接続のステートメントは接続属性を継承します。 ただし、属性SQL_ATTR_ASYNC_DBC_EVENTは継承可能ではなく、接続操作にのみ影響します。  
  
 ODBC アプリケーションは、イベント ハンドルを ODBC 接続ハンドルに関連付けるため、ODBC API **SQLSetConnectAttr**を呼び出し、属性としてSQL_ATTR_ASYNC_DBC_EVENTを指定し、イベント ハンドルを属性値として指定します。 新しい ODBC 属性SQL_ATTR_ASYNC_DBC_EVENTは、SQL_IS_POINTER型です。  
  
```  
HANDLE hEvent;  
hEvent = CreateEvent(   
            NULL,                // default security attributes  
            FALSE,               // auto-reset event  
            FALSE,               // initial state is non-signaled  
            NULL                 // no name  
            );  
```  
  
 通常、アプリケーションは自動リセット イベント オブジェクトを作成します。 ODBC はイベント オブジェクトをリセットしません。 非同期 ODBC 関数を呼び出す前に、アプリケーションでオブジェクトがシグナルステートでないことを確認する必要があります。  
  
```  
SQLRETURN retcode;  
retcode = SQLSetConnectAttr ( hDBC,  
                              SQL_ATTR_ASYNC_DBC_EVENT, // Attribute name  
                              (SQLPOINTER) hEvent,      // Win32 Event handle  
                              SQL_IS_POINTER);          // Length Indicator  
```  
  
 SQL_ATTR_ASYNC_DBC_EVENTは、ドライバー マネージャー専用の属性で、ドライバーで設定されません。  
  
 SQL_ATTR_ASYNC_DBC_EVENTの既定値は NULL です。 ドライバーが非同期通知をサポートしていない場合、取得または設定SQL_ATTR_ASYNC_DBC_EVENT SQLSTATE HY092 (無効な属性/オプション識別子) とSQL_ERRORを返します。  
  
 ODBC 接続ハンドルに設定された最後のSQL_ATTR_ASYNC_DBC_EVENT値が NULL でなく、SQL_ASYNC_DBC_ENABLE_ONを持つ属性SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLEを設定してアプリケーションが非同期モードを有効にした場合、非同期モードをサポートする ODBC 接続関数を呼び出すと、完了通知が表示されます。 ODBC 接続ハンドルに設定されている最後のSQL_ATTR_ASYNC_DBC_EVENT値が NULL の場合、ODBC は非同期モードが有効になっているかどうかに関係なく、アプリケーションに通知を送信しません。  
  
 アプリケーションは、属性SQL_ATTR_ASYNC_DBC_FUNCTION_ENABLEの設定前または設定後にSQL_ATTR_ASYNC_DBC_EVENTを設定できます。  
  
 アプリケーションは、接続関数 ( SQLConnect 、**SQLBrowseConnect**、 **SQLBrowseConnect** **SQLDriverConnect**) を呼び出す前に、ODBC 接続ハンドルに SQL_ATTR_ASYNC_DBC_EVENT属性を設定できます。 ODBC ドライバー マネージャーは、アプリケーションが使用する ODBC ドライバーを認識しないため、SQL_SUCCESS返します。 アプリケーションが接続関数を呼び出すと、ODBC ドライバー マネージャーは、ドライバーが非同期通知をサポートしているかどうかを確認します。 ドライバーが非同期通知をサポートしていない場合は、ODBC ドライバー マネージャーは SQLSTATE S1_118 (ドライバーは非同期通知をサポートしていません) とSQL_ERRORを返します。 ドライバーが非同期通知をサポートしている場合は、ODBC ドライバー マネージャーは、ドライバーを呼び出し、SQL_ATTR_ASYNC_DBC_NOTIFICATION_CALLBACKとSQL_ATTR_ASYNC_DBC_NOTIFICATION_CONTEXTに対応する属性を設定します。  
  
 同様に、アプリケーションは ODBC ステートメント ハンドルで**SQLSetStmtAttr**を呼び出し、ステートメント レベルの非同期通知を有効または無効にするSQL_ATTR_ASYNC_STMT_EVENT属性を指定します。 ステートメント関数は、接続が確立された後に常に呼び出されるため、対応するドライバーが非同期操作をサポートしていない場合、またはドライバーが非同期操作をサポートしていない場合 **、SQLSetStmtAttr**は SQLSTATE S1_118をSQL_ERRORをすぐに返します (ドライバーは非同期の通知をサポートしていませんが、非同期通知をサポートしていません)。  
  
```  
SQLRETURN retcode;  
retcode = SQLSetStmtAttr ( hSTMT,  
                           SQL_ATTR_ASYNC_STMT_EVENT, // Attribute name   
                           (SQLPOINTER) hEvent,       // Win32 Event handle  
                           SQL_IS_POINTER);           // length Indicator  
```  
  
 SQL_ATTR_ASYNC_STMT_EVENTは NULL に設定できますが、ドライバー マネージャー専用の属性で、ドライバーで設定されません。  
  
 SQL_ATTR_ASYNC_STMT_EVENTの既定値は NULL です。 ドライバーが非同期通知をサポートしていない場合、取得またはSTMT_EVENT属性をSQL_ATTR_ASYNC_を設定すると、SQLSTATE HY092 (無効な属性/オプション識別子) とSQL_ERRORが返されます。  
  
 アプリケーションでは、同じイベント ハンドルを複数の ODBC ハンドルに関連付けないようにする必要があります。 それ以外の場合、同じイベント ハンドルを共有する 2 つのハンドルで 2 つの非同期 ODBC 関数呼び出しが完了すると、1 つの通知が失われます。 接続ハンドルから同じイベント・ハンドルを継承するステートメント・ハンドルを避けるために、ODBC は、アプリケーションが接続ハンドルにSQL_ATTR_ASYNC_STMT_EVENT設定した場合に、SQLSTATE IM016 (ステートメント属性を接続ハンドルに設定できません) を持つSQL_ERRORを返します。  
  
### <a name="calling-asynchronous-odbc-functions"></a>非同期 ODBC 関数の呼び出し  
 非同期通知を有効にして非同期操作を開始した後、アプリケーションは任意の ODBC 関数を呼び出すことができます。 関数が非同期操作をサポートする関数セットに属している場合、アプリケーションは、操作が完了したときに、関数が失敗したか成功したかにかかわらず、完了通知を受け取ります。  唯一の例外は、アプリケーションが無効な接続またはステートメント ハンドルを使用して ODBC 関数を呼び出す場合です。 この場合、ODBC はイベント ハンドルを取得せず、シグナル状態に設定します。  
  
 アプリケーションは、対応する ODBC ハンドルで非同期操作を開始する前に、関連付けられたイベント オブジェクトが非シグナル状態であることを確認する必要があります。 ODBC はイベント オブジェクトをリセットしません。  
  
### <a name="getting-notification-from-odbc"></a>ODBC からの通知の取得  
 アプリケーション スレッドは **、WaitForSingleObject**を呼び出して 1 つのイベント ハンドルを待機したり **、WaitForMultipleObjects**を呼び出してイベント ハンドルの配列を待機したり、イベント オブジェクトの 1 つまたはすべてがシグナル状態になるか、タイムアウト間隔が経過するまで中断したりできます。  
  
```  
DWORD dwStatus = WaitForSingleObject(  
                        hEvent,  // The event associated with the ODBC handle  
                        5000     // timeout is 5000 millisecond   
);  
  
If (dwStatus == WAIT_TIMEOUT)  
{  
    // time-out interval elapsed before all the events are signaled.   
}  
Else  
{  
    // Call the corresponding Asynchronous ODBC API to complete all processing and retrieve the return code.  
}  
```
