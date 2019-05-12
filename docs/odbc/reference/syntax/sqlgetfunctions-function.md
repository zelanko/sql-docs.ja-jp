---
title: SQLGetFunctions 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e0a44320072f11a56b735502be3f1776f29cc1c0
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2019
ms.locfileid: "65538020"
---
# <a name="sqlgetfunctions-function"></a>SQLGetFunctions 関数
**準拠**  
 バージョンが導入されました。ODBC 1.0 規格に準拠します。ISO 92  
  
 **まとめ**  
 **SQLGetFunctions**ドライバーが、特定の ODBC 関数をサポートするかどうかに関する情報を返します。 この関数には、ドライバー マネージャーでは実装されてドライバーで実装することもできます。 ドライバーが実装されている場合**SQLGetFunctions**、ドライバー マネージャーがドライバーで関数を呼び出します。 それ以外の場合、関数自体を実行します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLGetFunctions(  
     SQLHDBC           ConnectionHandle,  
     SQLUSMALLINT      FunctionId,  
     SQLUSMALLINT *    SupportedPtr);  
```  
  
## <a name="arguments"></a>引数  
 *ConnectionHandle*  
 [入力]接続ハンドルです。  
  
 *FunctionId*  
 [入力]A **#define** ; 目的の ODBC 関数を識別する値**SQL_API_ODBC3_ALL_FUNCTIONS orSQL_API_ALL_FUNCTIONS**します。 **SQL_API_ODBC3_ALL_FUNCTIONS** 、ODBC 3 を使って *.x* ODBC 3 のサポートを確認するアプリケーション *.x*と以前の関数。 **SQL_API_ALL_FUNCTIONS** ODBC 2 を使って *.x* ODBC 2 のサポートを確認するアプリケーション *.x*と以前の関数。  
  
 一覧については **#define** ODBC 関数を識別する値は、「コメントです。」内のテーブルを参照してください。  
  
 *SupportedPtr*  
 [出力] 場合*FunctionId* 1 つの ODBC 関数を識別する*SupportedPtr*単一ポイント SQLUSMALLINT 値が SQL_TRUE でない場合に、ドライバー、および sql_false を受け取りますが、指定した関数がサポートされている場合サポートされています。  
  
 場合*FunctionId*は SQL_API_ODBC3_ALL_FUNCTIONS、 *SupportedPtr* SQL_API_ODBC3_ALL_FUNCTIONS_SIZE と等しい要素の数が SQLSMALLINT 配列を指します。 この配列によっては、ODBC 3 かどうかを判断するために使用できる 4,000 ビット ビットマップとしてドライバー マネージャーによってが扱われます *.x* earlier 関数がサポートされていますか。 関数のサポートを確認する SQL_FUNC_EXISTS マクロと呼びます。 (「コメントです」を参照してください)ODBC 3 *.x*アプリケーションが呼び出すことができます**SQLGetFunctions**でいずれか、ODBC 3 に対して SQL_API_ODBC3_ALL_FUNCTIONS *.x*または ODBC 2 *.x*ドライバー。  
  
 場合*FunctionId*は SQL_API_ALL_FUNCTIONS、 *SupportedPtr* 100 個の要素の SQLUSMALLINT 配列を指します。 配列のインデックスを作成して **#define**によって使用される値*FunctionId* ODBC の各関数を識別するために、配列の要素の一部が使用されていないと、将来使用するために予約します。 ODBC 2 を指定する場合の要素が SQL_TRUE *.x*またはドライバーでサポートされている以前の関数。 ドライバーでサポートされていない ODBC 関数を識別するか ODBC 関数を識別しない場合 SQL_FALSE になります。  
  
 返された配列 **SupportedPtr* 0 から始まるインデックスを使用します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetFunctions** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得できる**SQLGetDiagRec**で、 *HandleType*のSql_handle_dbc として、*処理*の*ConnectionHandle*します。 次の表に、一般的にによって返される SQLSTATE 値**SQLGetFunctions** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|説明|  
|--------|-----|-----------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンク エラー|関数が完了した処理の前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクに失敗しました。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM) **SQLGetFunctions**する前に呼び出された**SQLConnect**、 **SQLBrowseConnect**、または**SQLDriverConnect**します。<br /><br /> (DM) **SQLBrowseConnect**に対して呼び出された、 *ConnectionHandle* SQL_NEED_DATA が返されます。 この関数が呼び出されました**SQLBrowseConnect** SQL_SUCCESS_WITH_INFO または SQL_SUCCESS が返されます。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に対して呼び出された、 *ConnectionHandle* SQL_PARAM_DATA_ を返されます。ご利用いただけます。 ストリームのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY095|範囲外の関数の型|(DM)、無効な*FunctionId*値が指定されました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
  
## <a name="comments"></a>コメント  
 **SQLGetFunctions**は常に返します**SQLGetFunctions**、 **SQLDataSources**、および**SQLDrivers**はサポートされています。 これは、これらの関数は、ドライバー マネージャーで実装されるためです。 ドライバー マネージャーは、Unicode 関数が存在し、Unicode 関数は、ANSI 関数が存在する場合、対応する ANSI 関数にマップする場合は、ANSI の関数を対応する Unicode 関数にマップされます。 アプリケーションの使用方法については**SQLGetFunctions**を参照してください[インターフェイスの適合性レベル](../../../odbc/reference/develop-app/interface-conformance-levels.md)します。  
  
 有効な値の一覧を次に*FunctionId* ISO 92 標準準拠のレベルに準拠している関数。  
  
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
  
 有効な値の一覧を次に*FunctionId* Open Group 標準準拠のレベルに準拠している関数。  
  
|FunctionId 値|FunctionId 値|  
|-|-|  
|SQL_API_SQLCOLUMNS|SQL_API_SQLSTATISTICS|  
|SQL_API_SQLSPECIALCOLUMNS|SQL_API_SQLTABLES|  
  
 有効な値の一覧を次に*FunctionId*関数、ODBC 標準準拠のレベルに準拠しています。  
  
|FunctionId 値|FunctionId 値|  
|-|-|  
|SQL_API_SQLBINDPARAMETER|SQL_API_SQLNATIVESQL|  
|SQL_API_SQLBROWSECONNECT|SQL_API_SQLNUMPARAMS|  
|SQL_API_SQLBULKOPERATIONS[1]|SQL_API_SQLPRIMARYKEYS|  
|SQL_API_SQLCOLUMNPRIVILEGES|SQL_API_SQLPROCEDURECOLUMNS|  
|SQL_API_SQLDESCRIBEPARAM|SQL_API_SQLPROCEDURES|  
|SQL_API_SQLDRIVERCONNECT|SQL_API_SQLSETPOS|  
|SQL_API_SQLFOREIGNKEYS|SQL_API_SQLTABLEPRIVILEGES|  
|SQL_API_SQLMORERESULTS| |  
  
 [1]、ODBC 2 と *.x*ドライバー、 **SQLBulkOperations**が返されますのみサポートされているため、次の両方に該当するかどうか: ODBC 2 *.x*ドライバーをサポートしています**SQLSetPos**、SQL_POS_OPERATIONS 情報の種類がセットとして SQL_POS_ADD ビットを返します。  
  
 有効な値の一覧を次に*FunctionId* ODBC 3.8 以降に導入された関数。  
  
|FunctionId 値|  
|-|  
|SQL_API_SQLCANCELHANDLE [2]|  
  
 [2] **SQLCancelHandle**が返されますのみサポートされているかどうかは両方のドライバーがサポートされます**SQLCancel**と**SQLCancelHandle**します。 場合**SQLCancel**はサポートされてが**SQLCancelHandle**アプリケーション呼び出すことも可能ではない**SQLCancelHandle**ステートメント ハンドルではにマップするため、**SQLCancel**します。  
  
## <a name="sqlfuncexists-macro"></a>SQL_FUNC_EXISTS マクロ  
 SQL_FUNC_EXISTS (*SupportedPtr*、 *FunctionID*) マクロを使用して、ODBC 3 のサポートを確認 *.x*または以前の関数の後**SQLGetFunctions**で呼び出されましたが、 *FunctionId* SQL_API_ODBC3_ALL_FUNCTIONS の引数。 アプリケーションの呼び出しで SQL_FUNC_EXISTS、 *SupportedPtr*引数に設定、 *SupportedPtr*で渡される*SQLGetFunctions*を使用して、 *FunctionID*引数に設定、 **#define**関数。 SQL_FUNC_EXISTS はそれ以外の場合、関数がサポートされている場合は SQL_TRUE および sql_false を受け取りますに返します。  
  
> [!NOTE]
>  ODBC 2 を使用する場合 *.x*ドライバー、ODBC 3 *.x*ドライバー マネージャーの SQL_TRUE を返します**SQLAllocHandle**と**SQLFreeHandle**ため**SQLAllocHandle**にマップされて**SQLAllocEnv**、 **SQLAllocConnect**、または**SQLAllocStmt**と**SQLFreeHandle**にマップされて**SQLFreeEnv**、 **SQLFreeConnect**、または**SQLFreeStmt**します。 **SQLAllocHandle**または**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_DESC の引数はサポートされていません、ただしが SQL_TRUE が関数では、返される場合でもありませんODBC 2 *.x*にここで割り当てる関数。  
  
## <a name="code-example"></a>コード例  
 次の 3 つの例は、アプリケーションでの使用方法を表示する**SQLGetFunctions**ドライバーをサポートしているかを判断する**SQLTables**、 **SQLColumns**、および**SQLStatistics**します。 ドライバーがこれらの関数をサポートしていない場合、アプリケーションは、ドライバーから切断します。 最初の例では、 **SQLGetFunctions**関数ごとに 1 回です。  
  
```cpp  
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
  
 ODBC 3.x アプリケーションを呼び出すと 2 番目の例では、 **SQLGetFunctions**で配列を渡します**SQLGetFunctions**に関するすべての ODBC 情報を返します 3.x と以前の関数。  
  
```cpp  
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
  
 3 番目の例は、ODBC 2.x アプリケーションを呼び出す**SQLGetFunctions**を 100 個の要素の配列を渡します**SQLGetFunctions**に関するすべての ODBC 情報を返します 2.x と以前の関数。  
  
```cpp  
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
|接続属性の設定を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|ドライバーまたはデータ ソースに関する情報を返す|[SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|ステートメント属性の設定を返す|[SQLGetStmtAttr 関数](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
