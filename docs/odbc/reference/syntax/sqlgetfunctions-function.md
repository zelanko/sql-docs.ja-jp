---
title: SQLGetFunctions 関数 |Microsoft ドキュメント
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
- SQLGetFunctions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetFunctions
helpviewer_keywords:
- SQLGetFunctions function [ODBC]
ms.assetid: 0451d2f9-0f4f-46ba-b252-670956a52183
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 698e78ca1cbb0d6396c6319ef8618d813191c67e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetfunctions-function"></a>SQLGetFunctions 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLGetFunctions**ドライバーが、特定の ODBC 関数をサポートしているかどうかに関する情報を返します。 この関数では、ドライバー マネージャーで; を実装します。ドライバーで実装することもできます。 ドライバーを実装する場合**SQLGetFunctions**、ドライバー マネージャーは、ドライバーで関数を呼び出します。 それ以外の場合、関数自体を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLGetFunctions(  
     SQLHDBC           ConnectionHandle,  
     SQLUSMALLINT      FunctionId,  
     SQLUSMALLINT *    SupportedPtr);  
```  
  
## <a name="arguments"></a>引数  
 *ConnectionHandle*  
 [入力]接続ハンドルです。  
  
 *FunctionId が不適切*  
 [入力]A **#define**目的; の ODBC 関数を識別する値**SQL_API_ODBC3_ALL_FUNCTIONS orSQL_API_ALL_FUNCTIONS**です。 **SQL_API_ODBC3_ALL_FUNCTIONS** ODBC 3 で使用される *.x*アプリケーションで ODBC 3 のサポートを判断する *.x*と以前の関数。 **SQL_API_ALL_FUNCTIONS** ODBC 2 で使用される *.x*アプリケーションで ODBC 2 のサポートを判断する *.x*と以前の関数。  
  
 一覧については **#define** ODBC 関数を識別する値は、「コメント」内のテーブルを参照してください。  
  
 *SupportedPtr*  
 [出力] 場合*FunctionId* 1 つの ODBC 関数を識別*SupportedPtr*を 1 つのポイント SQLUSMALLINT 値が SQL_TRUE されていない場合に、ドライバー、および sql_false を受け取りますが、指定した関数がサポートされている場合サポートされています。  
  
 場合*FunctionId* SQL_API_ODBC3_ALL_FUNCTIONS は、 *SupportedPtr* SQL_API_ODBC3_ALL_FUNCTIONS_SIZE と等しい要素の数が SQLSMALLINT 配列を指します。 この配列では、ドライバー マネージャーでは ODBC 3 かどうかを決定するために使用できる 4,000 ビットのビットマップとして処理 *.x* earlier 関数がサポートされているか。 SQL_FUNC_EXISTS マクロは、関数のサポートの決定に呼び出されます。 (「コメント」を参照してください)ODBC 3 *.x*アプリケーションが呼び出すことができます**SQLGetFunctions**でいずれか、ODBC 3 に対して SQL_API_ODBC3_ALL_FUNCTIONS *.x*または ODBC 2 *.x*ドライバーです。  
  
 場合*FunctionId*は SQL_API_ALL_FUNCTIONS、 *SupportedPtr* 100 個の要素の SQLUSMALLINT 配列を指します。 配列のインデックスを **#define**によって使用される値*FunctionId* ; 各 ODBC 関数を識別する、配列の要素の一部は未使用および将来使用するために予約済みです。 ODBC 2 を特定すると、要素が SQL_TRUE *.x*またはドライバーでサポートされている以前の関数。 ドライバーでサポートされていない ODBC 関数を識別または ODBC 関数を識別しない場合は、SQL_FALSE を勧めします。  
  
 返される配列 **SupportedPtr* 0 から始まるインデックスを使用します。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetFunctions** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType*のSql_handle_dbc としてと*処理*の*ConnectionHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLGetFunctions**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------|-----|-----------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM) **SQLGetFunctions**する前に呼び出された**SQLConnect**、 **SQLBrowseConnect**、または**SQLDriverConnect**です。<br /><br /> (DM) **SQLBrowseConnect**で呼び出され、 *ConnectionHandle* SQL_NEED_DATA が返されます。 この関数が呼び出されました**SQLBrowseConnect** SQL_SUCCESS_WITH_INFO または SQL_SUCCESS が返されます。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *ConnectionHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY095|関数の範囲外の型|(DM) に無効な*FunctionId*値が指定されました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
  
## <a name="comments"></a>コメント  
 **SQLGetFunctions**を常に返します**SQLGetFunctions**、 **SQLDataSources**、および**SQLDrivers**はサポートされています。 これは、これらの関数には、ドライバー マネージャーでは実装されているためです。 ドライバー マネージャーは、Unicode 関数が存在し、Unicode 関数は、ANSI 関数が存在する場合、対応する ANSI 関数にマップする場合は、ANSI 関数を対応する Unicode 関数にマップされます。 アプリケーションの使用方法に関する情報の**SQLGetFunctions**を参照してください[インターフェイスへの準拠レベル](../../../odbc/reference/develop-app/interface-conformance-levels.md)です。  
  
 有効な値の一覧を次に示します*FunctionId* ISO 92 標準 – への準拠レベルに準拠している関数。  
  
|FunctionId 値|FunctionId 値|  
|----------|----------|  
|SQL_API_SQLALLOCHANDLE|SQL_API_SQLGETDESCFIELD|  
|SQL_API_SQLBINDCOL|SQL_API_SQLGETDESCREC|  
|SQL_API_SQLCANCEL|SQL_API_SQLGETDIAGFIELD|  
|SQL_API_SQLCLOSECURSOR|SQL_API_SQLGETDIAGREC|  
|SQL_API_SQLCOLATTRIBUTE|SQL_API_SQLGETENVATTR|  
|SQL_API_SQLCONNECT|SQL_API_SQLGETFUNCTIONS|  
|SQL_API_SQLCOPYDESC|SQL_API_SQLGETINFO|  
|SQL_API_SQLDATASOURCES|SQL_API_SQLGETSTMTATTR|  
|SQL_API_SQLDESCRIBECOL|SQL_API_SQLGETTYPEINFO|  
|SQL_API_SQLDISCONNECT|SQL_API_SQLNUMRESULTCOLS|  
|SQL_API_SQLDRIVERS|SQL_API_SQLPARAMDATA|  
|SQL_API_SQLENDTRAN|SQL_API_SQLPREPARE|  
|SQL_API_SQLEXECDIRECT|SQL_API_SQLPUTDATA|  
|SQL_API_SQLEXECUTE|SQL_API_SQLROWCOUNT|  
|SQL_API_SQLFETCH|SQL_API_SQLSETCONNECTATTR|  
|SQL_API_SQLFETCHSCROLL|SQL_API_SQLSETCURSORNAME|  
|SQL_API_SQLFREEHANDLE|SQL_API_SQLSETDESCFIELD|  
|SQL_API_SQLFREESTMT|SQL_API_SQLSETDESCREC|  
|SQL_API_SQLGETCONNECTATTR|SQL_API_SQLSETENVATTR|  
|SQL_API_SQLGETCURSORNAME|SQL_API_SQLSETSTMTATTR|  
|SQL_API_SQLGETDATA| |  
  
 有効な値の一覧を次に示します*FunctionId* Open Group 標準 – への準拠レベルに準拠している関数。  
  
|FunctionId 値|FunctionId 値|  
|-|-|  
|SQL_API_SQLCOLUMNS|SQL_API_SQLSTATISTICS|  
|SQL_API_SQLSPECIALCOLUMNS|SQL_API_SQLTABLES|  
  
 有効な値の一覧を次に示します*FunctionId* ODBC 標準 – への準拠レベルに準拠している関数です。  
  
|FunctionId 値|FunctionId 値|  
|-|-|  
|SQL_API_SQLBINDPARAMETER|SQL_API_SQLNATIVESQL|  
|SQL_API_SQLBROWSECONNECT|SQL_API_SQLNUMPARAMS|  
|SQL_API_SQLBULKOPERATIONS [1]|SQL_API_SQLPRIMARYKEYS|  
|SQL_API_SQLCOLUMNPRIVILEGES|SQL_API_SQLPROCEDURECOLUMNS|  
|SQL_API_SQLDESCRIBEPARAM|SQL_API_SQLPROCEDURES|  
|SQL_API_SQLDRIVERCONNECT|SQL_API_SQLSETPOS|  
|SQL_API_SQLFOREIGNKEYS|SQL_API_SQLTABLEPRIVILEGES|  
|SQL_API_SQLMORERESULTS| |  
  
 [1]、ODBC 2 を使用するときに *.x*ドライバー、 **SQLBulkOperations**が返されますのみサポートされているかどうかは、次の両方に当てはまる: ODBC 2 *.x*ドライバーをサポートしています**SQLSetPos**、SQL_POS_OPERATIONS 情報の種類をセットとして SQL_POS_ADD ビットを返します。  
  
 次の有効な値の一覧は*FunctionId* ODBC 3.8 またはそれ以降に導入された関数の。  
  
|FunctionId 値|  
|-|  
|SQL_API_SQLCANCELHANDLE [2]|  
  
 [2] **SQLCancelHandle**が返されますのみサポートされているかどうか、ドライバーはサポート両方**SQLCancel**と**SQLCancelHandle**です。 場合**SQLCancel**はサポートされてが**SQLCancelHandle**は、アプリケーションが呼び出すことができますも**SQLCancelHandle**ステートメント ハンドルで、にマップするため**SQLCancel**です。  
  
## <a name="sqlfuncexists-macro"></a>SQL_FUNC_EXISTS マクロ  
 SQL_FUNC_EXISTS (*SupportedPtr*、 *FunctionID*) マクロを使用して、ODBC 3 のサポートの決定 *.x*または以前の関数の後に**SQLGetFunctions**で呼び出されましたが、 *FunctionId* SQL_API_ODBC3_ALL_FUNCTIONS の引数。 アプリケーションを呼び出すと SQL_FUNC_EXISTS、 *SupportedPtr*引数に設定されて、 *SupportedPtr*に渡された*SQLGetFunctions*を使用して、 *FunctionID*引数に設定されて、 **#define**関数。 SQL_FUNC_EXISTS では、関数がサポートされている場合は SQL_TRUE および SQL_FALSE をそれ以外の場合を返します。  
  
> [!NOTE]  
>  ODBC 2 を使用するときに *.x*ドライバー、ODBC 3 *.x*ドライバー マネージャーの SQL_TRUE を返します**SQLAllocHandle**と**SQLFreeHandle**ため**SQLAllocHandle**にマップされて**SQLAllocEnv**、 **SQLAllocConnect**、または**SQLAllocStmt**、および**SQLFreeHandle**にマップされて**SQLFreeEnv**、 **SQLFreeConnect**、または**SQLFreeStmt**です。 **SQLAllocHandle**または**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_DESC の引数はサポートされていません、ただし、場合でも、SQL_TRUE が関数では、返されるがあるためありませんODBC 2 *.x*ここでにマップする関数。  
  
## <a name="code-example"></a>コード例  
 次の 3 つの例は、アプリケーションでの使用方法を表示する**SQLGetFunctions**ドライバーをサポートしているかどうかは**SQLTables**、 **SQLColumns**、および**SQLStatistics**です。 ドライバーがこれらの関数をサポートしていない場合、アプリケーションは、ドライバーから切断します。 最初の例では、 **SQLGetFunctions**関数ごとに 1 回です。  
  
```  
SQLUSMALLINT TablesExists, ColumnsExists, StatisticsExists;  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
  
retcodeTables = SQLGetFunctions(hdbc, SQL_API_SQLTABLES, &TablesExists);  
retcodeColumns = SQLGetFunctions(hdbc, SQL_API_SQLCOLUMNS, &ColumnsExists);  
retcodeStatistics = SQLGetFunctions(hdbc, SQL_API_SQLSTATISTICS, &StatisticsExists);  
  
// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.  
if (retcodeTables == SQL_SUCCESS && TablesExists == SQL_TRUE &&   
retcodeColumns == SQL_SUCCESS && ColumnsExists == SQL_TRUE &&   
retcodeStatistics == SQL_SUCCESS && StatisticsExists == SQL_TRUE)   
{  
  
   // Continue with application  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
 ODBC 3.x アプリケーションを呼び出す 2 番目の例では、 **SQLGetFunctions**で配列を渡し、 **SQLGetFunctions**に関するすべての ODBC 情報を返します 3.x と以前の関数。  
  
```  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
SQLUSMALLINT fExists[SQL_API_ODBC3_ALL_FUNCTIONS_SIZE];  
  
retcode = SQLGetFunctions(hdbc, SQL_API_ODBC3_ALL_FUNCTIONS, fExists);  
  
// SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver.  
if (reccode == SQL_SUCCESS &&   
SQL_FUNC_EXISTS(fExists, SQL_API_SQLTABLES) == SQL_TRUE &&  
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLCOLUMNS) == SQL_TRUE &&  
   SQL_FUNC_EXISTS(fExists, SQL_API_SQLSTATISTICS) == SQL_TRUE)   
{  
  
   // Continue with application  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
 3 番目の例では、ODBC 2.x アプリケーション呼び出し**SQLGetFunctions**を 100 個の要素の配列を渡します**SQLGetFunctions**に関するすべての ODBC 情報を返します 2.x と以前の関数。  
  
```  
#define FUNCTIONS 100  
  
RETCODE retcodeTables, retcodeColumns, retcodeStatistics  
SQLUSMALLINT fExists[FUNCTIONS];  
  
retcode = SQLGetFunctions(hdbc, SQL_API_ALL_FUNCTIONS, fExists);  
  
/* SQLGetFunctions is completed successfully and SQLTables, SQLColumns, and SQLStatistics are supported by the driver. */  
if (retcode == SQL_SUCCESS &&   
fExists[SQL_API_SQLTABLES] == SQL_TRUE &&  
   fExists[SQL_API_SQLCOLUMNS] == SQL_TRUE &&  
   fExists[SQL_API_SQLSTATISTICS] == SQL_TRUE)   
{  
  
   /* Continue with application */  
  
}  
  
SQLDisconnect(hdbc);  
```  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|接続属性の設定値を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|ドライバーまたはデータ ソースに関する情報を返す|[SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|ステートメント属性の設定値を返す|[SQLGetStmtAttr 関数](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
