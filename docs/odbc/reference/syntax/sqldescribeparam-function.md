---
title: "SQLDescribeParam 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLDescribeParam
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLDescribeParam
helpviewer_keywords: SQLDescribeParam function [ODBC]
ms.assetid: 1f5b63c4-2f3e-44da-b155-876405302281
caps.latest.revision: "28"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0e17df1233e49700b9089961ff3648b73d2f6ca3
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqldescribeparam-function"></a>SQLDescribeParam 関数
**準拠**  
 バージョンが導入されています ODBC 1.0 標準への準拠: ODBC。  
  
 **概要**  
 **SQLDescribeParam**準備された SQL ステートメントに関連付けられているパラメーター マーカーの説明を返します。 この情報も表示されます、IPD のフィールドにします。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLDescribeParam(  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ParameterNumber,  
      SQLSMALLINT *   DataTypePtr,  
      SQLULEN *       ParameterSizePtr,  
      SQLSMALLINT *   DecimalDigitsPtr,  
      SQLSMALLINT *   NullablePtr);  
```  
  
## <a name="argument"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *ParameterNumber*  
 [入力]パラメーター マーカー番号順に内で順序昇順パラメーター 1 から始まります。  
  
 *DataTypePtr*  
 [出力]パラメーターの SQL データ型を返すバッファーへのポインター。 この値は、IPD の SQL_DESC_CONCISE_TYPE レコード フィールドから読み取られます。 内の値の 1 つ、 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)付録 d: データ型、またはドライバー固有の SQL データ型のセクションです。  
  
 ODBC 3 です。*x*、SQL_TYPE_DATE、SQL_TYPE_TIME、または SQL_TYPE_TIMESTAMP で返されます *\*DataTypePtr*の日付、時刻、またはタイムスタンプ データ、ODBC 2 にそれぞれ;.*x*SQL_DATE、SQL_TIME、または SQL_TIMESTAMP が返されます。 ドライバー マネージャーでは、ODBC 2 時に、必須のマッピングを実行します。*x* ODBC 3 を利用するアプリケーション*。x*ドライバーまたは ODBC 3 *。x* ODBC 2 を利用するアプリケーション*。x*ドライバー。  
  
 ときに*ColumnNumber*と等しいで 0 (ブックマーク列)、sql_binary 型が返されます *\*DataTypePtr*の可変長のブックマークです。 (SQL_INTEGER は ODBC 3 でブックマークが使用されている場合に返されます。*x* ODBC 2 を使用するアプリケーション*。x*ドライバーまたは ODBC 2 *。x* ODBC 3 を使用するアプリケーション*。x*ドライバーです)。  
  
 詳細については、次を参照してください。 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)付録 d: データ型にします。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。  
  
 *ParameterSizePtr*  
 [出力]データ ソースで定義されている、対応するパラメーター マーカーの式または列の文字のサイズを返すバッファーへのポインター。 列のサイズの詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)です。  
  
 *DecimalDigitsPtr*  
 [出力]データ ソースで定義されている列の 10 進数字または対応するパラメーターの式の数を返すバッファーへのポインター。 小数点以下桁数の詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)です。  
  
 *NullablePtr*  
 [出力]パラメーターが NULL 値を許可するかどうかを示す値を返すバッファーへのポインター。 この値は、IPD の SQL_DESC_NULLABLE フィールドから読み取られます。 次のいずれかです。  
  
-   SQL_NO_NULLS: パラメーターでは (これは、既定値) の NULL 値は許可されません。  
  
-   SQL_NULLABLE: パラメーターは、NULL 値を許可します。  
  
-   SQL_NULLABLE_UNKNOWN: ドライバーを特定できませんパラメーターが NULL 値を許容するかどうか。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLDescribeParam** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType*のSQL_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLDescribeParam**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07009|無効な記述子のインデックス|引数の指定された値 (DM) *ParameterNumber*が 1 より小さい。<br /><br /> 引数が指定された値*ParameterNumber*が関連付けられている SQL ステートメントのパラメーターの数を超えています。<br /><br /> パラメーター マーカーは、非 DML ステートメントの一部でした。<br /><br /> パラメーター マーカーの一部であった、**選択** ボックスの一覧です。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|21S01|挿入値のリストが列の一覧と一致しません|パラメーターの数、**挿入**ステートメントは、ステートメントで指定したテーブルの列数と一致しませんでした。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM) 関数が呼び出す前に呼び出された**SQLPrepare**または**SQLExecDirect**の*StatementHandle*です。<br /><br /> (DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLDescribeParam**関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 パラメーター マーカーは、パラメーター、昇順に、SQL ステートメントの順序で、1 から始まる番号が付けられます。  
  
 **SQLDescribeParam** SQL ステートメントにパラメーターの型 (入力、入力/出力、または出力) は返しません。 ただし、プロシージャの呼び出しでは、SQL ステートメントのすべてのパラメーターは、入力パラメーターが。 アプリケーションを呼び出すプロシージャへの呼び出しで各パラメーターの型を決定するには、 **SQLProcedureColumns**です。  
  
 詳細については、次を参照してください。[を記述するパラメーター](../../../odbc/reference/develop-app/describing-parameters.md)です。  
  
## <a name="code-example"></a>コード例  
 次の例では、SQL ステートメントのユーザーを要求し、そのステートメントを準備します。 次に、呼び出す**SQLNumParams**ステートメントにパラメーターが含まれるかどうかを決定します。 ステートメントにパラメーターが含まれる場合を呼び出して**SQLDescribeParam**をこれらのパラメーターを記述して**SQLBindParameter**これらをバインドします。 最後はユーザーの任意のパラメーターの値を要求し、ステートメントを実行します。  
  
```  
SQLCHAR       Statement[100];  
SQLSMALLINT   NumParams, i, DataType, DecimalDigits, Nullable;  
SQLUINTEGER   ParamSize;  
SQLHSTMT      hstmt;  
  
// Prompt the user for an SQL statement and prepare it.  
GetSQLStatement(Statement);  
SQLPrepare(hstmt, Statement, SQL_NTS);  
  
// Check to see if there are any parameters. If so, process them.  
SQLNumParams(hstmt, &NumParams);  
if (NumParams) {  
   // Allocate memory for three arrays. The first holds pointers to buffers in which  
   // each parameter value will be stored in character form. The second contains the  
   // length of each buffer. The third contains the length/indicator value for each  
   // parameter.  
   SQLPOINTER * PtrArray = (SQLPOINTER *) malloc(NumParams * sizeof(SQLPOINTER));  
   SQLINTEGER * BufferLenArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));  
   SQLINTEGER * LenOrIndArray = (SQLINTEGER *) malloc(NumParams * sizeof(SQLINTEGER));  
  
   for (i = 0; i < NumParams; i++) {  
   // Describe the parameter.  
   SQLDescribeParam(hstmt, i + 1, &DataType, &ParamSize, &DecimalDigits, &Nullable);  
  
   // Call a helper function to allocate a buffer in which to store the parameter  
   // value in character form. The function determines the size of the buffer from  
   // the SQL data type and parameter size returned by SQLDescribeParam and returns  
   // a pointer to the buffer and the length of the buffer.  
   AllocParamBuffer(DataType, ParamSize, &PtrArray[i], &BufferLenArray[i]);  
  
   // Bind the memory to the parameter. Assume that we only have input parameters.  
   SQLBindParameter(hstmt, i + 1, SQL_PARAM_INPUT, SQL_C_CHAR, DataType, ParamSize,  
         DecimalDigits, PtrArray[i], BufferLenArray[i],  
         &LenOrIndArray[i]);  
  
   // Prompt the user for the value of the parameter and store it in the memory  
   // allocated earlier. For simplicity, this function does not check the value  
   // against the information returned by SQLDescribeParam. Instead, the driver does  
   // this when the statement is executed.  
   GetParamValue(PtrArray[i], BufferLenArray[i], &LenOrIndArray[i]);  
   }  
}  
  
// Execute the statement.  
SQLExecute(hstmt);  
  
// Process the statement further, such as retrieving results (if any) and closing the  
// cursor (if any). Code not shown.  
  
// Free the memory allocated for each parameter and the memory allocated for the arrays  
// of pointers, buffer lengths, and length/indicator values.  
for (i = 0; i < NumParams; i++) free(PtrArray[i]);  
free(PtrArray);  
free(BufferLenArray);  
free(LenOrIndArray);  
```  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|パラメーターへのバッファーのバインド|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|実行のためのステートメントを準備します。|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
