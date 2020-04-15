---
title: 非同期実行 (ポーリングメソッド) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- asynchronous execution [ODBC]
ms.assetid: 8cd21734-ef8e-4066-afd5-1f340e213f9c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ca7b3d5fa16be44bf4c2ef8f8df8953ae081235d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293402"
---
# <a name="asynchronous-execution-polling-method"></a>非同期実行 (ポーリング メソッド)
ODBC 3.8 および Windows 7 SDK より前のバージョンでは、非同期操作はステートメント関数でのみ許可されていました。 詳細については、このトピックの「**ステートメントの非同期操作の実行**」を参照してください。  
  
 Windows 7 SDK の ODBC 3.8 では、接続関連の操作で非同期実行が導入されました。 詳細については、このトピックの後半の「**非同期での接続操作の実行**」セクションを参照してください。  
  
 Windows 7 SDK では、非同期ステートメントまたは接続操作の場合、アプリケーションはポーリング メソッドを使用して非同期操作が完了したと判断しました。 Windows 8 SDK 以降では、通知メソッドを使用して非同期操作が完了したことを確認できます。 詳細については、「[非同期実行 (通知メソッド)」](../../../odbc/reference/develop-app/asynchronous-execution-notification-method.md)を参照してください。  
  
 既定では、ドライバーは ODBC 関数を同期的に実行します。つまり、アプリケーションは関数を呼び出し、ドライバーは、関数の実行が終了するまで、アプリケーションに制御を返しません。 ただし、一部の関数は非同期で実行できます。つまり、アプリケーションは関数を呼び出し、ドライバーは、最小限の処理の後、アプリケーションに制御を返します。 アプリケーションは、最初の関数がまだ実行中に他の関数を呼び出すことができます。  
  
 非同期実行は、接続の確立、SQL ステートメントの準備と実行、メタデータの取得、データのフェッチ、トランザクションのコミットなどの、データ ソースで実行されるほとんどの関数でサポートされています。 この機能は、データ ソースで実行されるタスクに、ログイン プロセスや大規模なデータベースに対する複雑なクエリなど、時間がかかる場合に最も便利です。  
  
 アプリケーションが非同期処理を有効にしたステートメントまたは接続を使用して関数を実行すると、ドライバーは最小限の処理 (エラーの引数のチェックなど) を実行し、データ ソースに手で処理し、SQL_STILL_EXECUTING戻りコードを使用してアプリケーションに制御を返します。 その後、アプリケーションは他のタスクを実行します。 非同期関数が終了したタイミングを判断するために、アプリケーションは、最初に使用したのと同じ引数を使用して関数を呼び出すことによって、定期的にドライバーをポーリングします。 関数がまだ実行中の場合は、SQL_STILL_EXECUTING返します。実行が終了すると、SQL_SUCCESS、SQL_ERROR、SQL_NEED_DATAなど、同期的に実行されていたコードが返されます。  
  
 関数が同期的に実行されるか非同期的に実行されるかは、ドライバー固有です。 たとえば、結果セットのメタデータがドライバーにキャッシュされるとします。 この場合 **、SQLDescribeCol**を実行するのに非常に時間がかかりませんし、ドライバーは、単に実行を人為的に遅延するのではなく、関数を実行する必要があります。 一方、ドライバーは、データ ソースからメタデータを取得する必要がある場合は、これを行っている間、アプリケーションに制御を返す必要があります。 したがって、アプリケーションは、関数を最初に非同期に実行するときにSQL_STILL_EXECUTING以外のリターン コードを処理できる必要があります。  
  
## <a name="executing-statement-operations-asynchronously"></a>ステートメント操作を非同期に実行する  
 次のステートメント関数は、データ ソースに対して動作し、非同期で実行できます。  
  
||||  
|-|-|-|  
|[オペレーション](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|[SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|  
|[SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|  
  
 非同期ステートメントの実行は、データ ソースに応じて、ステートメントごとまたは接続ごとに制御されます。 つまり、アプリケーションは、特定の関数が非同期で実行されるのではなく、特定のステートメントで実行される関数を非同期で実行することを指定します。 サポートされているアプリケーションを見つけるには、アプリケーションは、SQL_ASYNC_MODEのオプションを使用して[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)を呼び出します。 SQL_AM_CONNECTIONは、接続レベルの非同期実行 (ステートメント・ハンドルの場合) がサポートされている場合に戻されます。SQL_AM_STATEMENTステートメントレベルの非同期実行がサポートされている場合。  
  
 特定のステートメントで実行される関数を非同期的に実行するように指定するには、アプリケーションは SQL_ATTR_ASYNC_ENABLE属性を指定して**SQLSetStmtAttr**を呼び出し、SQL_ASYNC_ENABLE_ONに設定します。 接続レベルの非同期処理がサポートされている場合、SQL_ATTR_ASYNC_ENABLE ステートメント属性は読み取り専用であり、その値は、ステートメントが割り振られた接続の接続属性と同じになります。 ステートメント属性の値が、ステートメントの割り当て時以降に設定されるかどうかは、ドライバー固有です。 設定しようとすると、SQL_ERRORと SQLSTATE HYC00 (オプション機能は実装されていません) が返されます。  
  
 特定の接続で実行される関数を非同期的に実行するように指定するには、アプリケーションは SQL_ATTR_ASYNC_ENABLE属性を指定して**SQLSetConnectAttr**を呼び出し、SQL_ASYNC_ENABLE_ONに設定します。 接続に割り当てられた将来のステートメント ハンドルはすべて、非同期実行に対して有効になります。既存のステートメント ハンドルがこのアクションによって有効になるかどうかは、ドライバー定義です。 SQL_ATTR_ASYNC_ENABLEを SQL_ASYNC_ENABLE_OFF に設定すると、接続上のすべてのステートメントは同期モードになります。 接続上にアクティブなステートメントがある間に非同期実行が有効になっている場合は、エラーが返されます。  
  
 非同期モードで、ドライバーが特定の接続でサポートできるアクティブな同時実行ステートメントの最大数を決定するには、アプリケーションは、SQL_MAX_ASYNC_CONCURRENT_STATEMENTS オプションを使用して**SQLGetInfo**を呼び出します。  
  
 次のコードは、ポーリング モデルのしくみを示しています。  
  
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
  
 関数が非同期に実行されている間、アプリケーションは他のステートメントで関数を呼び出すことができます。 アプリケーションは、非同期ステートメントに関連付けられているものを除き、任意の接続で関数を呼び出すこともできます。 しかし、アプリケーションは、ステートメント操作がSQL_STILL_EXECUTINGを返した後、元の関数と次の関数 (ステートメント ハンドルまたはその関連付けられた接続、環境ハンドル) のみを呼び出すことができます。  
  
-   [SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)  
  
-   [(ステートメント ハンドル](../../../odbc/reference/syntax/sqlcancelhandle-function.md)上)  
  
-   [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)  
  
-   [SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)  
  
-   [ハンドル](../../../odbc/reference/syntax/sqlallochandle-function.md)  
  
-   [アズ・ビジトル](../../../odbc/reference/syntax/sqlgetenvattr-function.md)  
  
-   [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
-   [データベースソース](../../../odbc/reference/syntax/sqldatasources-function.md)  
  
-   [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)  
  
-   [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
-   [SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
-   [SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)  
  
 アプリケーションが、非同期ステートメントまたは関連付けられた接続を使用して他の関数を呼び出した場合、この関数は SQLSTATE HY010 (関数シーケンスエラーなど) を返します。  
  
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
  
 アプリケーションが関数を呼び出して、非同期的に実行されているかどうかを判断する場合は、元のステートメント ハンドルを使用する必要があります。 これは、非同期実行がステートメントごとに追跡されるためです。 アプリケーションは、ドライバー マネージャーで過去のエラー チェックを取得する他の引数 (元の引数が行う) に対しても有効な値を指定する必要があります。 ただし、ドライバーは、ステートメント ハンドルをチェックし、ステートメントが非同期で実行されていることを判断した後、他のすべての引数を無視します。  
  
 関数が非同期に実行されている間 、つまり、SQL_STILL_EXECUTING返された後、別のコードを返す前に、アプリケーションは同じステートメント ハンドルを使用して SQLCancel または**SQLCancelHandle**を呼び出して、関数をキャンセルできます。 **SQLCancelHandle** これは、関数の実行をキャンセルする保証はありません。 たとえば、関数は既に終了している可能性があります。 さらに **、SQLCancel**または**SQLCancelHandle**によって返されるコードは、関数をキャンセルしようとした場合に成功したかどうかのみを示し、関数を実際にキャンセルしたかどうかではありません。 関数が取り消されたかどうかを判断するために、アプリケーションは関数を再度呼び出します。 関数が取り消された場合、SQL_ERRORと SQLSTATE HY008 (操作は取り消されました) が返されます。 関数が取り消されなかった場合は、SQL_SUCCESS、SQL_STILL_EXECUTING、または別の SQLSTATE を持つSQL_ERRORなどの別のコードを返します。  
  
 ドライバーがステートメント レベルの非同期処理をサポートしている場合に特定のステートメントの非同期実行を無効にするには、アプリケーションは、SQL_ATTR_ASYNC_ENABLE属性を使用して**SQLSetStmtAttr**を呼び出し、SQL_ASYNC_ENABLE_OFFに設定します。 ドライバーが接続レベルの非同期処理をサポートしている場合、アプリケーションは**SQLSetConnectAttr**を呼び出してSQL_ATTR_ASYNC_ENABLEを SQL_ASYNC_ENABLE_OFF に設定します。  
  
 アプリケーションは、元の関数の繰り返しループで診断レコードを処理する必要があります。 非同期関数の実行中に**SQLGetDiagField**または**SQLGetDiagRec**が呼び出された場合、診断レコードの現在の一覧が返されます。 元の関数呼び出しが繰り返されるたびに、以前の診断レコードがクリアされます。  
  
## <a name="executing-connection-operations-asynchronously"></a>接続操作を非同期に実行する  
 ODBC 3.8 より前は、カタログ メタデータ操作だけでなく、準備、実行、フェッチなどのステートメント関連の操作に対して非同期実行が許可されていました。 ODBC 3.8 以降では、接続、切断、コミット、ロールバックなどの接続関連の操作に対しても非同期実行が可能です。  
  
 ODBC 3.8 の詳細については[、「ODBC 3.8 の新機能](../../../odbc/reference/what-s-new-in-odbc-3-8.md)」を参照してください。  
  
 次のシナリオでは、接続操作を非同期に実行すると便利です。  
  
-   スレッド数が少ない場合、データレートが非常に高い多数のデバイスを管理する。 応答性とスケーラビリティを最大限に高めるには、すべての操作を非同期にすることが望ましいです。  
  
-   複数の接続でデータベース操作をオーバーラップして、転送経過時間を短縮する場合。  
  
-   効率的な非同期 ODBC 呼び出しと接続操作を取り消す機能により、アプリケーションは、タイムアウトを待たずに、低速な操作をキャンセルできます。  
  
 接続ハンドルを操作する次の関数を非同期で実行できるようになりました。  
  
||||  
|-|-|-|  
|[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|[接続解除](../../../odbc/reference/syntax/sqldisconnect-function.md)|  
|[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
  
 ドライバーがこれらの関数の非同期操作をサポートするかどうかを判断するには、アプリケーションは、SQL_ASYNC_DBC_FUNCTIONSを使用して**SQLGetInfo**を呼び出します。 非同期操作がサポートされている場合は、SQL_ASYNC_DBC_CAPABLEが返されます。 非同期操作がサポートされていない場合は、SQL_ASYNC_DBC_NOT_CAPABLEが返されます。  
  
 特定の接続で実行される関数を非同期的に実行するように指定するには、アプリケーションは**SQLSetConnectAttr**を呼び出し、SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE属性をSQL_ASYNC_DBC_ENABLE_ONに設定します。 接続を確立する前に接続属性を設定すると、常に同期的に実行されます。 また **、SQLSetConnectAttr**を使用してSQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE接続属性を設定する操作は、常に同期的に実行されます。  
  
 アプリケーションは、接続を確立する前に非同期操作を有効にできます。 ドライバ マネージャは接続を確立する前にどのドライバを使用するかを判断できないため、ドライバ マネージャは**SQLSetConnectAttr**で成功を返します。 ただし、ODBC ドライバーが非同期操作をサポートしていない場合は、接続に失敗する可能性があります。  
  
 一般に、特定の接続ハンドルまたはステートメント ハンドルに関連付けられた、非同期に実行される関数は、1 つ以上存在します。 ただし、接続ハンドルには複数のステートメント ハンドルを関連付けることができます。 接続ハンドルで実行されている非同期操作がない場合は、関連付けられたステートメント ハンドルが非同期操作を実行できます。 同様に、関連付けられたステートメント ハンドルで進行中の非同期操作がない場合は、接続ハンドルに対して非同期操作を行うことができます。 現在非同期操作を実行しているハンドルを使用して非同期操作を実行しようとすると、HY010「関数シーケンスエラー」が返されます。  
  
 接続操作がSQL_STILL_EXECUTINGを返す場合、アプリケーションは元の関数とその接続ハンドルに対して次の関数のみを呼び出すことができます。  
  
-   **(接続ハンドル**上)  
  
-   **SQLGetDiagField**  
  
-   **SQLGetDiagRec**  
  
-   **ハンドル**(ENV/DBC の割り当て)  
  
-   **を**割り当てる (ENV/DBC を割り当てる)  
  
-   **アズ・ビジトル**  
  
-   **SQLGetConnectAttr**  
  
-   **データベースソース**  
  
-   **SQLDrivers**  
  
-   **SQLGetInfo**  
  
-   **SQLGetFunctions**  
  
 アプリケーションは、元の関数の繰り返しループで診断レコードを処理する必要があります。 非同期関数の実行中に SQLGetDiagField または SQLGetDiagRec が呼び出された場合、診断レコードの現在の一覧が返されます。 元の関数呼び出しが繰り返されるたびに、以前の診断レコードがクリアされます。  
  
 接続が非同期的に開かれているか閉じられている場合、アプリケーションが元の関数呼び出しでSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを受け取ると、操作は完了します。  
  
 新しい関数が ODBC 3.8 SQL**キャンセル ハンドル**に追加されました。 この関数は、6 つの接続関数 **(SQL ブラウズ接続****、SQL 接続****、SQL 切断、SQL****ドライバー接続、SQLEndTran**、および**SQLSetConnectAttr**) を取り消します。 **SQLEndTran** アプリケーションは、ドライバーが**SQLCancelHandle**をサポートしているかどうかを判断する**SQLGetFunctions**を呼び出す必要があります。 **SQLCancel**と同様に **、SQLCancelHandle**が成功を返す場合、操作がキャンセルされたことを意味しません。 アプリケーションは、操作が取り消されたかどうかを判断するために、元の関数を再度呼び出す必要があります。 **SQLCancelHandle**を使用すると、接続ハンドルまたはステートメント ハンドルの非同期操作をキャンセルできます。 ステートメント ハンドルの操作をキャンセルする**SQLCancelHandle**を使用すると、呼び出し**SQLCancel**と同じです。  
  
 **SQLCancelHandle**と非同期接続操作の両方を同時にサポートする必要はありません。 ドライバーは、非同期接続操作をサポートできますが **、SQLCancelHandle**をサポートすることはできません。またはその逆も同様です。  
  
 非同期接続操作と**SQLCancelHandle** ODBC 3.x および ODBC 2.x アプリケーションでは、ODBC 3.8 ドライバーと ODBC 3.8 ドライバー マネージャーで使用することもできます。 古いアプリケーションで新しい機能を新しいバージョンの ODBC で使用できるようにする方法については、「[互換性マトリックス](../../../odbc/reference/develop-app/compatibility-matrix.md)」を参照してください。  
  
### <a name="connection-pooling"></a>接続のプール  
 接続プールが有効になっている場合、非同期操作は接続の確立 **(SQLConnect**および**SQLDriverConnect**を使用) および**SQLDisconnect**を使用した接続のクローズに対してのみ最小限にサポートされます。 しかし、アプリケーションは**SQLConnect 、SQLDriverConnect**、および**SQLDriverConnect****SQLDisconnect**からのSQL_STILL_EXECUTING戻り値を処理できる必要があります。  
  
 接続プールが有効な場合、非同期操作では**SQLEndTran**と**SQLSetConnectAttr**がサポートされます。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例は **、SQLSetConnectAttr**を使用して、接続関連関数の非同期実行を有効にする方法を示しています。  
  
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
  
### <a name="description"></a>説明  
 この例では、非同期コミット操作を示します。 ロールバック操作もこの方法で実行できます。  
  
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
 [ステートメントの実行 (ODBC)](../../../odbc/reference/develop-app/executing-statements-odbc.md)
