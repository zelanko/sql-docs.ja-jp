---
title: SQLDescribeParam 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDescribeParam
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDescribeParam
helpviewer_keywords:
- SQLDescribeParam function [ODBC]
ms.assetid: 1f5b63c4-2f3e-44da-b155-876405302281
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 62d61d43638c0ca6e3e43da83367dff461033463
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982293"
---
# <a name="sqldescribeparam-function"></a>SQLDescribeParam 関数
**準拠**  
 バージョンが導入されました。ODBC 1.0 規格に準拠します。ODBC  
  
 **まとめ**  
 **SQLDescribeParam**準備された SQL ステートメントに関連付けられているパラメーター マーカーの説明を返します。 この情報は、IPD のフィールドも使用可能です。  
  
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
 [入力]パラメーター マーカーの数で順番に順番に増加パラメーターの順序、1 から始まります。  
  
 *DataTypePtr*  
 [出力]パラメーターの SQL データ型を返すバッファーへのポインター。 この値は、IPD の SQL_DESC_CONCISE_TYPE レコード フィールドから読み取られます。 内の値の 1 つ、 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)付録 d: のセクションデータ型、またはドライバーに固有の SQL データ型。  
  
 ODBC 3。*x*、SQL_TYPE_DATE、SQL_TYPE_TIME、または SQL_TYPE_TIMESTAMP で返される *\*DataTypePtr*の日付、時刻、またはタイムスタンプ データ、ODBC 2 にそれぞれ;.*x*SQL_DATE、SQL_TIME、または SQL_TIMESTAMP が返されます。 ドライバー マネージャーは、ODBC 2 時に、必要なマッピングを実行します。*x*アプリケーションは、ODBC 3 の操作します *。x*ドライバーまたはとき、ODBC 3 *。x* ODBC 2 を利用するアプリケーション *。x*ドライバー。  
  
 ときに*ColumnNumber*と等しいで返される SQL_BINARY (ブックマーク列) を 0 に *\*DataTypePtr*の可変長のブックマーク。 (SQL_INTEGER は ODBC の 3 つのブックマークを使用する場合に返されます。*x* ODBC 2 を使用するアプリケーション *。x*ドライバーまたは ODBC 2 *。x*アプリケーションは、ODBC 3 の操作します *。x*ドライバー)。  
  
 詳細については、次を参照してください[SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)付録 d:。データ型。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。  
  
 *ParameterSizePtr*  
 [出力]データ ソースで定義されている対応するパラメーター マーカーの式または列の文字のサイズを返すバッファーへのポインター。 列のサイズの詳細については、次を参照してください。[列のサイズ、10 進数字、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)します。  
  
 *DecimalDigitsPtr*  
 [出力]データ ソースで定義されている列の 10 進数字または式の対応するパラメーターの数を返すバッファーへのポインター。 10 進数字の詳細については、次を参照してください。[列のサイズ、10 進数字、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)します。  
  
 *NullablePtr*  
 [出力]パラメーターが NULL 値を許容するかどうかを示す値を返すバッファーへのポインター。 この値は、IPD の SQL_DESC_NULLABLE フィールドから読み取られます。 次のいずれかです。  
  
-   SQL_NO_NULLS:パラメーターでは、NULL 値が (これは、既定値) は許可されません。  
  
-   SQL_NULLABLE:パラメーターは、NULL 値を許可します。  
  
-   SQL_NULLABLE_UNKNOWN:ドライバーは、パラメーターが NULL 値を許容するかどうかを判断できません。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLDescribeParam** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得できる**SQLGetDiagRec**で、 *HandleType*のSql_handle_stmt として、*処理*の*StatementHandle*します。 次の表に、によって返される通常の SQLSTATE 値**SQLDescribeParam** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07009|無効な記述子のインデックス|引数に指定された値 (DM) *ParameterNumber*が 1 未満です。<br /><br /> 引数が指定された値*ParameterNumber*が関連付けられている SQL ステートメントのパラメーターの数を超えていました。<br /><br /> パラメーター マーカーは、非 DML ステートメントの一部でした。<br /><br /> パラメーター マーカーの一部であった、**選択**一覧。|  
|08S01|通信リンク エラー|関数が完了した処理の前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクに失敗しました。|  
|21S01|挿入値のリストは、列リストと一致しません|パラメーターの数、**挿入**ステートメントがステートメントでという名前のテーブルの列の数と一致しました。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効に、 *StatementHandle*します。 関数が呼び出された、および実行を完了する前に**SQLCancel**または**SQLCancelHandle**が呼び出されて、 *StatementHandle*します。 後でもう一度関数が呼び出された、 *StatementHandle*します。<br /><br /> 関数が呼び出された、および実行を完了する前に**SQLCancel**または**SQLCancelHandle**が呼び出されて、 *StatementHandle*から別のスレッドで、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM) 関数が呼び出す前に呼び出された**SQLPrepare**または**SQLExecDirect**の*StatementHandle*します。<br /><br /> (DM) を非同期的に実行中の関数が呼び出された接続ハンドルに関連付けられているため、 *StatementHandle*します。 この非同期関数ではときに実行されている、 **SQLDescribeParam**関数が呼び出されました。<br /><br /> (DM) を非同期的に実行中の関数 (いないこの"1") が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**に対して呼び出された、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングは無効です。|通知のモデルを使用すると、常にポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了が呼び出されていません。|通知モードが有効になっている場合、ハンドルでは、前の関数呼び出しに SQL_STILL_EXECUTING が返された場合と**SQLCompleteAsync**後処理を行い、操作を完了するハンドルで呼び出す必要があります。|  
  
## <a name="comments"></a>コメント  
 パラメーター マーカーは、パラメーター、昇順に SQL ステートメントに表示される順序で、1 から始まる番号が付けられます。  
  
 **SQLDescribeParam** SQL ステートメントのパラメーターの型 (入力、入力/出力、または出力) は返されません。 ただし、プロシージャの呼び出しでは、SQL ステートメントのすべてのパラメーターは、入力パラメーターが。 アプリケーションを呼び出すプロシージャへの呼び出し内の各パラメーターの種類を決定する**SQLProcedureColumns**します。  
  
 詳細については、次を参照してください。[を記述するパラメーター](../../../odbc/reference/develop-app/describing-parameters.md)します。  
  
## <a name="code-example"></a>コード例  
 次の例では、SQL ステートメントのユーザーを要求し、し、そのステートメントを準備します。 次に、呼び出す**SQLNumParams**ステートメントにパラメーターが含まれるかどうかを確認します。 呼び出し、ステートメントにパラメーターが含まれている場合**SQLDescribeParam**これらのパラメーターを記述して**SQLBindParameter**これらをバインドできます。 最後に、パラメーターの値はユーザー要求し、ステートメントを実行します。  
  
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
|バッファーをパラメーターにバインドします。|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|ステートメントの処理をキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|実行するステートメントを準備します。|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
