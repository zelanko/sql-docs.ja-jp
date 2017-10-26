---
title: "非同期実行 (ポーリング メソッド) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous execution [ODBC]
ms.assetid: 8cd21734-ef8e-4066-afd5-1f340e213f9c
caps.latest.revision: 40
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1d4237eddad4847840d16440fbd4cb0940a61d40
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="asynchronous-execution-polling-method"></a>非同期実行 (ポーリング メソッド)
ODBC 3.8 および Windows 7 SDK より前の非同期操作は、ステートメントの関数でのみ可能でした。 詳細については、次を参照してください。、**ステートメントの操作を非同期に実行する**、このトピックで後述します。  
  
 Windows 7 SDK で ODBC 3.8 は、接続関連の操作での非同期実行を導入されました。 詳細については、次を参照してください。、**接続の操作を非同期に実行する** セクションで、このトピックで後述します。  
  
 非同期ステートメントまたは接続操作で、Windows 7 SDK では、アプリケーションは、非同期操作がポーリング メソッドを使用して完了したことを決定します。 以降、Windows 8 SDK では、非同期操作が、通知方法を使用して完了したことを確認できます。 詳細については、次を参照してください。[非同期実行 (通知方法)](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md)です。  
  
 既定では、ドライバーの ODBC 関数同期的に実行します。つまり、アプリケーション関数を呼び出し、関数の実行が終了するまで、ドライバーがアプリケーションにコントロールを返されません。 ただし、一部の関数を非同期的に実行できるつまり、関数を呼び出し、アプリケーションとは、ドライバー、最小限の処理後に制御を返すアプリケーションです。 アプリケーションは、最初の関数はまだ実行中に、他の関数を呼び出すし、ことができます。  
  
 非同期実行をサポートするほとんどの関数、データ ソースで実行されるほとんどの接続の確立、準備、および SQL ステートメントを実行する関数は、メタデータを取得などのデータをフェッチし、トランザクションをコミットします。 データ ソースで実行されているタスク、ログイン プロセスや、大きなデータベースに対する複雑なクエリなど、時間がかかる場合に便利です。  
  
 アプリケーションでは、ステートメントまたは非同期処理を有効になっている接続を持つ関数を実行するとき、ドライバー (エラーの引数をチェック) などの処理量が最小限に抑える、データ ソースへの処理に渡しますを行いを返しますリターン コードを SQL_STILL_EXECUTING アプリケーションに制御します。 その後、アプリケーションでは、その他のタスクを実行します。 調べるには、非同期関数が終了するは、アプリケーションは、最初に使用されたことと同じ引数を持つ関数を呼び出すことによって、一定の間隔で、ドライバーをポーリングします。 関数はまだ実行中の場合、SQL_STILL_EXECUTING 以外を返します実行が終了する場合は、これが返されるが、同期的に実行、SQL_SUCCESS や SQL_ERROR、SQL_NEED_DATA などのコードを返します。  
  
 関数が同期または非同期でを実行するかどうかは、特定のドライバーです。 たとえば、ドライバーで結果セットのメタデータをキャッシュします。 この場合、非常に簡単にかかる時間実行**SQLDescribeCol**ドライバー必要があります関数を実行するだけなく、意図的に実行を遅延します。 その一方で場合、ドライバーは、データ ソースからメタデータを取得する必要がありますを返しますコントロールをアプリケーションにこれを実行中にします。 そのため、アプリケーションは、SQL_STILL_EXECUTING 以外のリターン コードを最初に実行すると、関数に非同期的に処理できる必要があります。  
  
## <a name="executing-statement-operations-asynchronously"></a>ステートメントの操作を非同期的に実行します。  
 次のステートメントの関数は、データ ソースに対して機能し、非同期的に実行できます。  
  
||||  
|-|-|-|  
|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|[SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
  
 非同期のステートメントの実行は、ステートメントごとまたはデータ ソースによっては、接続ごとのいずれかで制御されます。 アプリケーションは、特定の関数は、非同期的に実行することが、特定のステートメントで実行された任意の関数が非同期的に実行されること、いない指定します。 検索にどれがサポートされているか、アプリケーションが呼び出す[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) SQL_ASYNC_MODE、オプションでします。 接続レベルの非同期実行 (用、ステートメント ハンドル) がサポートされる場合は、SQL_AM_CONNECTION が返されます。SQL_AM_STATEMENT ステートメント レベルの非同期実行がサポートされている場合。  
  
 特定のステートメントを使用して実行された関数があることを指定する非同期的に実行、アプリケーション呼び出し**SQLSetStmtAttr** SQL_ATTR_ASYNC_ENABLE 属性およびを SQL_ASYNC_ENABLE_ON に設定します。 接続レベルの非同期処理がサポートされている場合は、SQL_ATTR_ASYNC_ENABLE ステートメント属性は読み取り専用とその値は、ステートメントが割り当てられている接続の接続属性と同じです。 これは、ステートメントの割り当て時、またはそれ以降には、ステートメント属性の値を設定するかどうかドライバーに固有です。 SQL_ERROR と SQLSTATE HYC00 を返すように設定しようとしていますが (省略可能な機能が実装されていません)。  
  
 特定の接続で実行される関数があることを指定する非同期的に実行、アプリケーション呼び出し**SQLSetConnectAttr** SQL_ATTR_ASYNC_ENABLE 属性およびを SQL_ASYNC_ENABLE_ON に設定します。 接続上に割り当てられたすべての将来のステートメント ハンドルは非同期実行を有効にします。これはドライバーで定義されているこのアクションでの既存のステートメント ハンドルの有効かどうかです。 SQL_ATTR_ASYNC_ENABLE が SQL_ASYNC_ENABLE_OFF に設定されている場合、接続ですべてのステートメントは、同期モードでは。 接続でアクティブなステートメントがあるときに、非同期実行が有効になっている場合、エラーが返されます。  
  
 アプリケーションの呼び出しをすると、ドライバーでは、特定の接続をサポートする非同期モードでのアクティブな同時実行ステートメントの最大数を調べるには、 **SQLGetInfo** SQL_MAX_ASYNC_CONCURRENT_STATEMENTS オプションを使用します。  
  
 次のコードでは、ポーリング モデルの動作方法を示しています。  
  
```  
SQLHSTMT  hstmt1;  
SQLRETURN rc;  
  
// Specify that the statement is to be executed asynchronously.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_ASYNC_ENABLE, SQL_ASYNC_ENABLE_ON, 0);  
  
// Execute a SELECT statement asynchronously.  
while ((rc=SQLExecDirect(hstmt1,"SELECT * FROM Orders",SQL_NTS))==SQL_STILL_EXECUTING) {  
   // While the statement is still executing, do something else.  
   // Do not use hstmt1, because it is being used asynchronously.  
}  
  
// When the statement has finished executing, retrieve the results.  
```  
  
 関数の非同期的に実行中、アプリケーションは、その他のステートメントで関数を呼び出すことができます。 アプリケーションは、非同期のステートメントに関連付けられている 1 つを除く、すべての接続で関数を呼び出してもできます。 アプリケーションがのみを呼び出しては元の関数と (が、ステートメント ハンドル、または、関連する接続環境ハンドル)、次の関数ステートメント操作の後に SQL_STILL_EXECUTING を返します。  
  
-   [SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md) (、ステートメント ハンドルで)  
  
-   [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
-   [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
-   [SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
-   [SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)  
  
-   [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
-   [SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)  
  
-   [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)  
  
-   [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   [SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
-   [SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
 アプリケーションが非同期のステートメントを使用して、またはそのステートメントに関連付けられている接続で他の任意の関数を呼び出す場合、関数は、SQLSTATE HY010 を返します (関数のシーケンス エラー) は、例を示します。  
  
```  
SQLHDBC       hdbc1, hdbc2;  
SQLHSTMT      hstmt1, hstmt2, hstmt3;  
SQLCHAR *     SQLStatement = "SELECT * FROM Orders";  
SQLUINTEGER   InfoValue;  
SQLRETURN     rc;  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt2);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc2, &hstmt3);  
  
// Specify that hstmt1 is to be executed asynchronously.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_ASYNC_ENABLE, SQL_ASYNC_ENABLE_ON, 0);  
  
// Execute hstmt1 asynchronously.  
while ((rc = SQLExecDirect(hstmt1, SQLStatement, SQL_NTS)) == SQL_STILL_EXECUTING) {  
   // The following calls return HY010 because the previous call to  
   // SQLExecDirect is still executing asynchronously on hstmt1. The  
   // first call uses hstmt1 and the second call uses hdbc1, on which  
   // hstmt1 is allocated.  
   SQLExecDirect(hstmt1, SQLStatement, SQL_NTS);   // Error!  
   SQLGetInfo(hdbc1, SQL_UNION, (SQLPOINTER) &InfoValue, 0, NULL);   // Error!  
  
   // The following calls do not return errors. They use a statement  
   // handle other than hstmt1 or a connection handle other than hdbc1.  
   SQLExecDirect(hstmt2, SQLStatement, SQL_NTS);   // OK  
   SQLTables(hstmt3, NULL, 0, NULL, 0, NULL, 0, NULL, 0);   // OK  
   SQLGetInfo(hdbc2, SQL_UNION, (SQLPOINTER) &InfoValue, 0, NULL);   // OK  
}  
```  
  
 アプリケーションを確認するかどうか、まだ実行中に非同期的に関数を呼び出すときに、元のステートメント ハンドルを使用して必要があります。 これは、非同期実行はステートメントごとに追跡されるためです。 アプリケーションは、その他の引数の有効な値も指定する必要があります:、元の引数が行う — エラー ドライバー マネージャーでのチェックを通過します。 ただし、ドライバーが、ステートメント ハンドルをチェックして、ステートメントが非同期的に実行しているかを決定した後は、その他のすべての引数を無視します。  
  
 関数は非同期的に実行中に-つまり、SQL_STILL_EXECUTING が返った後、およびコードを返します異なる-アプリケーションを呼び出すことで取り消すことができます**SQLCancel**または**SQLCancelHandle** 、同じステートメント ハンドルを使用します。 関数の実行をキャンセルするこれは保証されません。 たとえば、関数を既に完了が可能性があります。 によって返される、コードのさらに、 **SQLCancel**または**SQLCancelHandle**のみ関数を実際に取り消されたか、関数をキャンセルの試行が成功すると、かどうかを示します。 関数がキャンセルされたかどうかを判断するのには、アプリケーションは、関数を再度呼び出します。 SQLSTATE HY008、SQL_ERROR を返します、関数が取り消された場合 (操作が取り消されました)。 関数が取り消されない場合は、SQL_SUCCESS、SQL_STILL_EXECUTING、または別の sqlstate SQL_ERROR など、別のコードを返します。  
  
 ドライバーは、ステートメント レベルの非同期処理、アプリケーションの呼び出しをサポートしている場合は、特定のステートメントの非同期実行を無効にする**SQLSetStmtAttr**属性に、SQL_ATTR_ASYNC_ENABLE し sql _ に設定ASYNC_ENABLE_OFF です。 ドライバーは接続レベルの非同期処理をサポートする場合、アプリケーションは呼び出し**SQLSetConnectAttr** SQL_ASYNC_ENABLE_OFF で、すべてのステートメントの非同期実行を無効にする SQL_ATTR_ASYNC_ENABLE を設定する、接続です。  
  
 アプリケーションでは、元の関数の繰り返し、ループ内の診断レコードを処理する必要があります。 場合**SQLGetDiagField**または**SQLGetDiagRec**非同期関数を実行するときに呼び出される現在の診断レコードの一覧が返されます。 で、元の関数呼び出しが繰り返されるたびに、前の診断レコードを消去します。  
  
## <a name="executing-connection-operations-asynchronously"></a>接続操作を非同期的に実行します。  
 ODBC 3.8 する前にステートメント関連の操作の準備などの非同期実行が許可されて、実行、およびフェッチもカタログ メタデータの操作です。 以降で ODBC 3.8 は、非同期実行ことも、接続の切断などの接続に関連する操作、commit、およびロールバックにできます。  
  
 ODBC 3.8 の詳細については、次を参照してください。 [ODBC 3.8 新](../../../odbc/reference/what-s-new-in-odbc-3-8.md)です。  
  
 接続操作を非同期的に実行は、次のシナリオに便利です。  
  
-   ときにスレッドの数が少ないは、多数の非常に高いデータ レートでデバイスを管理します。 応答性とスケーラビリティを最大化するには、すべての操作を非同期にすることをお勧めします。  
  
-   転送の経過時間を短縮する複数の接続でデータベース操作が重複する場合。  
  
-   効率的な非同期 ODBC 呼び出しとの接続操作をキャンセルする機能は、ユーザーがタイムアウトまで待機することがなく、低速な処理をキャンセルできるようにするアプリケーションを有効にします。  
  
 次の関数は、接続ハンドルの操作が非同期で実行するようになりましたことができます。  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 ドライバーがこれらの関数で、非同期操作をサポートしているかどうかを決定するには、アプリケーションが呼び出す**SQLGetInfo** SQL_ASYNC_DBC_FUNCTIONS とします。 非同期操作がサポートされている場合は、SQL_ASYNC_DBC_CAPABLE が返されます。 非同期操作がサポートされていない場合は、SQL_ASYNC_DBC_NOT_CAPABLE が返されます。  
  
 特定の接続で実行される関数があることを指定する非同期的に実行、アプリケーション呼び出し**SQLSetConnectAttr** SQL_ASYNC_DBC_ENABLE を SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE 属性を設定_ON です。 常に接続を確立する前に、接続属性を設定するは、同期的に実行します。 またで SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE の属性、操作を設定すると、接続**SQLSetConnectAttr**常に同期的に実行します。  
  
 アプリケーションは、接続を行う前に非同期操作を有効にできます。 ドライバー マネージャーは、接続を行う前に使用するドライバーを特定できないため、ドライバー マネージャーが常に成功を返します**SQLSetConnectAttr**です。 ただし、ODBC ドライバーは非同期操作をサポートしていない場合に接続することがあります。  
  
 一般があります多くて関数を非同期的に実行するか、特定の接続ハンドルまたはステートメント ハンドルに関連付けられているいずれか。 ただし、接続ハンドルでは、1 つ以上関連付けられているステートメント ハンドルを持つことができます。 接続ハンドルで実行する非同期操作がない場合は、関連付けられているステートメント ハンドルは非同期操作を実行できます。 同様に、関連付けられているステートメント ハンドルのいずれかで、進行中の非同期操作が存在しない場合は、接続ハンドルでの非同期操作を持つことができます。 現在の非同期操作を実行しているハンドルを使用して非同期操作を実行するとは、HY010、「関数のシーケンス エラー」に戻ります。  
  
 接続操作では、SQL_STILL_EXECUTING が返された場合、アプリケーション呼び出すことができますのみ元の関数と、次の関数、接続ハンドルの。  
  
-   **SQLCancelHandle** (、接続ハンドルで)  
  
-   **SQLGetDiagField**  
  
-   **SQLGetDiagRec**  
  
-   **SQLAllocHandle** (ENV/DBC の割り当て)  
  
-   **SQLAllocHandleStd** (ENV/DBC の割り当て)  
  
-   **SQLGetEnvAttr**  
  
-   **SQLGetConnectAttr**  
  
-   **SQLDataSources**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 アプリケーションでは、元の関数の繰り返し、ループ内の診断レコードを処理する必要があります。 SQLGetDiagField または SQLGetDiagRec が呼び出された場合、非同期関数を実行するときには、診断レコードの現在の一覧を返します。 で、元の関数呼び出しが繰り返されるたびに、前の診断レコードを消去します。  
  
 接続されている場合、操作が完了しているアプリケーションが SQL_SUCCESS または sql_success_with_info が元の関数呼び出しの受信を開く場合、または非同期的に終了しました。  
  
 ODBC 3.8 に追加された新しい関数**SQLCancelHandle**です。 この関数は、6 つの接続の機能をキャンセル (**SQLBrowseConnect**、 **SQLConnect**、 **SQLDisconnect**、 **SQLDriverConnect**、**SQLEndTran**、および**SQLSetConnectAttr**)。 アプリケーションを呼び出す必要があります**SQLGetFunctions**ドライバーをサポートしているかどうかは**SQLCancelHandle**です。 同様に**SQLCancel**場合は、 **SQLCancelHandle**成功した場合を返しますというではありません、操作が取り消されました。 アプリケーションでは、操作が取り消されたかどうかを判断するには、もう一度元の関数を呼び出す必要があります。 **SQLCancelHandle**接続ハンドルやステートメント ハンドルで、非同期操作を取り消すことができます。 使用して**SQLCancelHandle**ステートメントで操作を中止するハンドルは、呼び出した場合と同じ**SQLCancel**です。  
  
 両方をサポートする必要はありません**SQLCancelHandle**と同時に操作を非同期接続します。 ドライバーは、非同期の接続操作をサポートできますが**SQLCancelHandle**、またはその逆です。  
  
 非同期の接続操作と**SQLCancelHandle** ODBC によっても使用できます 3.x および ODBC 2.x アプリケーション ODBC 3.8 ドライバーと ODBC 3.8 ドライバー マネージャーを使用します。 後の ODBC バージョンでの新機能を使用する以前のバージョンのアプリケーションを有効にする方法については、次を参照してください。[の互換性対応表](../../../odbc/reference/develop-app/compatibility-matrix.md)です。  
  
### <a name="connection-pooling"></a>接続のプール  
 接続を確立するための非同期操作はサポートされて最小限に抑えるだけ接続プールが有効になっているときに (で**SQLConnect**と**SQLDriverConnect**) との接続を閉じる**SQLDisconnect**です。 アプリケーションから SQL_STILL_EXECUTING の戻り値を処理できる必要がありますが、 **SQLConnect**、 **SQLDriverConnect**、および**SQLDisconnect**です。  
  
 接続プールを有効にすると、 **SQLEndTran**と**SQLSetConnectAttr**は非同期操作はサポートされています。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>Description  
 次の例は、使用する方法を示しています。 **SQLSetConnectAttr**接続関連の関数の非同期実行を有効にします。  
  
### <a name="code"></a>コード  
  
```  
BOOL AsyncConnect (SQLHANDLE hdbc)   
{  
   SQLRETURN r;  
   SQLHANDLE hdbc;  
  
   // Enable asynchronous execution of connection functions.  
   // This must be executed synchronously, that is r != SQL_STILL_EXECUTING  
   r = SQLSetConnectAttr(  
         hdbc,   
         SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE,  
         reinterpret_cast<SQLPOINTER> (SQL_ASYNC_DBC_ENABLE_ON),  
         0);  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
  
   TCHAR szConnStrIn[256] = _T("DSN=AsyncDemo");  
  
   r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
  
   if (r == SQL_ERROR)   
   {  
      // Use SQLGetDiagRec to process the error.  
      // If SQLState is HY114, the driver does not support asynchronous execution.  
      return FALSE;  
   }  
  
   while (r == SQL_STILL_EXECUTING)   
   {  
      // Do something else.  
  
      // Check for completion, with the same set of arguments.  
      r = SQLDriverConnect(hdbc, NULL, (SQLTCHAR *) szConnStrIn, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT);  
   }  
  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
  
   return TRUE;  
}  
  
```  
  
## <a name="example"></a>例  
  
### <a name="description"></a>Description  
 この例では、非同期コミット操作が表示されます。 ロールバック操作は、このように実行できます。  
  
### <a name="code"></a>コード  
  
```  
BOOL AsyncCommit ()   
{  
   SQLRETURN r;   
  
   // Assume that SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE is SQL_ASYNC_DBC_ENABLE_ON.  
  
   r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   while (r == SQL_STILL_EXECUTING)   
   {  
      // Do something else.  
  
      // Check for completion with the same set of arguments.  
      r = SQLEndTran(SQL_HANDLE_DBC, hdbc, SQL_COMMIT);  
   }  
  
   if (r != SQL_SUCCESS && r != SQL_SUCCESS_WITH_INFO)   
   {  
      return FALSE;  
   }  
   return TRUE;  
}  
```  
  
## <a name="see-also"></a>参照  
 [ODBC ステートメントの実行](../../../odbc/reference/develop-app/executing-statements-odbc.md)

