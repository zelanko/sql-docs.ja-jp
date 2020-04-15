---
title: 関数の取得 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetFunctions
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLGetFunctions
helpviewer_keywords:
- SQLGetFunctions function [ODBC]
ms.assetid: 0451d2f9-0f4f-46ba-b252-670956a52183
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 15537b28ff2bae8a4fcd3e7be82426eb53aa83a8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285332"
---
# <a name="sqlgetfunctions-function"></a>SQLGetFunctions 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 ドライバー**が**特定の ODBC 関数をサポートしているかどうかに関する情報を返します。 この関数は、ドライバー マネージャーで実装されます。また、ドライバーで実装することもできます。 ドライバーが**SQLGetFunctions**を実装する場合、ドライバー マネージャーは、ドライバーの関数を呼び出します。 それ以外の場合は、関数自体を実行します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLGetFunctions(  
     SQLHDBC           ConnectionHandle,  
     SQLUSMALLINT      FunctionId,  
     SQLUSMALLINT *    SupportedPtr);  
```  
  
## <a name="arguments"></a>引数  
 *接続ハンドル*  
 [入力] 接続ハンドル。  
  
 *ファンクションId*  
 [入力]対象となる ODBC 関数を識別する **#define**値。**SQL_API_ODBC3_ALL_FUNCTIONSorSQL_API_ALL_FUNCTIONS**. **SQL_API_ODBC3_ALL_FUNCTIONS** ODBC 3 *.x*アプリケーションでは、ODBC 3 *.x*以前の関数のサポートを決定するために使用されます。 **SQL_API_ALL_FUNCTIONS** ODBC 2 *.x*アプリケーションは、ODBC 2 *.x*以前の関数のサポートを決定するために使用されます。  
  
 ODBC 関数を識別する **#define**値の一覧については、「コメント」の表を参照してください。  
  
 *サポートされているPtr*  
 [出力] *FunctionId が*単一の ODBC 関数を識別する場合 *、SupportedPtr*は、指定された関数がドライバーでサポートされている場合はSQL_TRUE、サポートされていない場合はSQL_FALSEされる単一の SQLUSMALLINT 値を指します。  
  
 *FunctionId が*SQL_API_ODBC3_ALL_FUNCTIONS場合、*サポートされたPtr*は、SQL_API_ODBC3_ALL_FUNCTIONS_SIZEに等しい要素の数を持つ SQLSMALLINT 配列を指します。 この配列は、ODBC 3 *.x*以前の関数がサポートされているかどうかを判断するために使用できる 4,000 ビット ビットマップとしてドライバー マネージャーによって扱われます。 関数サポートを決定するために、SQL_FUNC_EXISTS マクロが呼び出されます。 (「コメント」を参照してください。ODBC 3 *.x*アプリケーションは、ODBC 3 *.x*または ODBC 2 *.x*ドライバーに対してSQL_API_ODBC3_ALL_FUNCTIONSを使用して**SQLGetFunctions**を呼び出すことができます。  
  
 *関数Id*がSQL_API_ALL_FUNCTIONS場合、*サポートされたPtr*は100要素のSQLUSMALLINT配列を指します。 配列は、各 ODBC 関数を識別するために*FunctionId*によって使用される **#define**値によってインデックス付けされます。配列の一部の要素は未使用で、将来の使用のために予約されています。 要素は、ドライバーでサポートされている ODBC 2 *.x*以前の関数を識別する場合にSQL_TRUEされます。 ドライバーでサポートされていない ODBC 関数を識別するか、ODBC 関数を識別しない場合は、SQL_FALSE。  
  
 **SupportedPtr*で返される配列は、0 から始まるインデックスを使用します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetFunctions が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、関連付けられた SQLSTATE 値を取得するには、ハンドル型の SQL_HANDLE_DBC*ハンドル型*と*接続ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出します。 *Handle* 次の表は **、SQLGetFunctions**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------|-----|-----------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM) **SQL 関数は****、SQLConnect** **、SQL ブラウズコネクト**、または**SQL ドライバー接続**の前に呼び出されました。<br /><br /> (DM) **SQLBrowseConnect**が*接続ハンドル*に対して呼び出され、SQL_NEED_DATA返されました。 この関数は **、SQLBrowseConnect**がSQL_SUCCESS_WITH_INFOまたはSQL_SUCCESSを返す前に呼び出されました。<br /><br /> (DM) 接続*ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY095|関数の種類が範囲外です|(DM) 無効な*関数 Id*値が指定されました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
  
## <a name="comments"></a>説明  
 **SQLGet 関数は**常に **、SQLGet 関数** **、SQL データソース**、および SQL ドライバーがサポートされていることを返**します**。 これらの関数は、ドライバー マネージャーで実装されているため、これは行われます。 ドライバー マネージャーは、対応する Unicode 関数が存在する場合は、対応する Unicode 関数に ANSI 関数をマップし、ANSI 関数が存在する場合は、対応する ANSI 関数に Unicode 関数をマップします。 アプリケーションで**の SQLGetFunctions**の使用方法については、「[インターフェイス準拠レベル](../../../odbc/reference/develop-app/interface-conformance-levels.md)」を参照してください。  
  
 ISO 92 標準準拠レベルに準拠する関数の*FunctionId*の有効な値の一覧を次に示します。  
  
|関数Id値|関数Id値|  
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
  
 Open Group 標準準拠レベルに準拠する*関数の有効*な値を次に示します。  
  
|関数Id値|関数Id値|  
|-|-|  
|SQL_API_SQLCOLUMNS|SQL_API_SQLSTATISTICS|  
|SQL_API_SQLSPECIALCOLUMNS|SQL_API_SQLTABLES|  
  
 次に示す値は、ODBC 標準準拠レベルに準拠する関数の*有効*な値です。  
  
|関数Id値|関数Id値|  
|-|-|  
|SQL_API_SQLBINDPARAMETER|SQL_API_SQLNATIVESQL|  
|SQL_API_SQLBROWSECONNECT|SQL_API_SQLNUMPARAMS|  
|SQL_API_SQLBULKOPERATIONS[1]|SQL_API_SQLPRIMARYKEYS|  
|SQL_API_SQLCOLUMNPRIVILEGES|SQL_API_SQLPROCEDURECOLUMNS|  
|SQL_API_SQLDESCRIBEPARAM|SQL_API_SQLPROCEDURES|  
|SQL_API_SQLDRIVERCONNECT|SQL_API_SQLSETPOS|  
|SQL_API_SQLFOREIGNKEYS|SQL_API_SQLTABLEPRIVILEGES|  
|SQL_API_SQLMORERESULTS| |  
  
 ODBC 2 *.x*ドライバを使用する場合 **、SQLBulkOperations は**、次の両方の条件に該当する場合にのみ、サポートとして返 *.x*されます SQL_POS_ADD **SQLSetPos**SQL_POS_OPERATIONS。  
  
 ODBC 3.8 以降で導入された関数の*FunctionId*の有効な値の一覧を次に示します。  
  
|関数Id値|  
|-|  
|SQL_API_SQLCANCELHANDLE [2]|  
  
 [2] **SQL キャンセル ハンドル**は、ドライバーが両方の SQL キャンセルと SQL**キャンセルハンドル**をサポートしている場合にのみサポートされているとして返されます。 **SQLCancel** **SQL キャンセル**がサポートされているが **、SQLCancelHandle**がサポートされていない場合、アプリケーションはステートメント ハンドルで**SQLCancelHandle**を呼び出**SQLCancel**すことができます。  
  
## <a name="sql_func_exists-macro"></a>マクロSQL_FUNC_EXISTS  
 SQL_FUNC_EXISTS(*SupportedPtr*、 *FunctionID*) マクロは、関数*の引数を*指定して**呼**び出された後に ODBC 3 *.x*以前の関数のサポートを決定するために使用SQL_API_ODBC3_ALL_FUNCTIONS。 アプリケーションは、引数*SupportedPtr*を*SQLGetFunctions*で渡された*SupportedPtr*に設定し、関数の **#define**に設定された*関数 ID*引数を持つSQL_FUNC_EXISTSを呼び出します。 SQL_FUNC_EXISTS関数がサポートされている場合はSQL_TRUEを返し、それ以外の場合はSQL_FALSE返します。  
  
> [!NOTE]
>  ODBC 2 *.x*ドライバーを使用する場合 **、SQLAllocHandle が SQLAllocEnv、SQLAllocConnect、** または**SQLAllocConnect** **SQLAllocStmt**にマップされ **、SQL フリーハンドル**が**SQLFreeEnv、SQLFreeConnect、** または**SQLFreeStmt**にマップされているため、ODBC **SQLFreeConnect**3 *.x*ドライバー マネージャーは**SQLAllocHandle**と SQL フリー**ハンドル**のSQL_TRUEを返します。 **SQLAllocHandle** ただし、この場合は割り当てる ODBC 2 *.x*関数がないため、関数に対してSQL_TRUEが返される場合でも、SQL_HANDLE_DESCの*ハンドル*型引数を持つ**SQLAllocHandle**または**SQLFreeHandle**はサポートされていません。  
  
## <a name="code-example"></a>コード例  
 次の 3 つの例は、アプリケーションが**SQLGetFunctions を**使用して、ドライバーが**SQLTables** **、SQLColumns**、および**SQLStatistics**をサポートしているかどうかを判断する方法を示しています。 ドライバーがこれらの機能をサポートしていない場合、アプリケーションはドライバーから切断します。 最初の例では、関数ごとに 1 回**ずつ SQLGetFunctions を**呼び出します。  
  
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
  
 2 番目の例では、ODBC 3.x アプリケーションが**SQLGetFunctions**を呼び出し、その配列を渡して **、その**配列を渡します。  
  
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
  
 3 番目の例は、ODBC 2.x アプリケーションが**SQLGetFunctions**を呼び出し、**その**配列を渡す 100 要素の配列を渡します。  
  
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
  
|対象|参照先|  
|---------------------------|---------|  
|接続属性の設定を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|ドライバーまたはデータ ソースに関する情報を返す|[SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|ステートメント属性の設定を返す|[SQLGetStmtAttr 関数](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
