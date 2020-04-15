---
title: 関数の説明 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDescribeParam
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLDescribeParam
helpviewer_keywords:
- SQLDescribeParam function [ODBC]
ms.assetid: 1f5b63c4-2f3e-44da-b155-876405302281
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: be6d076ca121923a4b6769c7dad5269c3fd642ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301162"
---
# <a name="sqldescribeparam-function"></a>SQLDescribeParam 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: ODBC  
  
 **まとめ**  
 **準備**された SQL ステートメントに関連付けられたパラメーター・マーカーの記述を戻します。 この情報は、IPD のフィールドでも使用できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLDescribeParam(  
      SQLHSTMT        StatementHandle,  
      SQLUSMALLINT    ParameterNumber,  
      SQLSMALLINT *   DataTypePtr,  
      SQLULEN *       ParameterSizePtr,  
      SQLSMALLINT *   DecimalDigitsPtr,  
      SQLSMALLINT *   NullablePtr);  
```  
  
## <a name="argument"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *パラメータ番号*  
 [入力]パラメータマーカー番号は、1から始まる増加パラメータ順に順番に並べ替えられます。  
  
 *データ型Ptr*  
 [出力]パラメーターの SQL データ・タイプを戻すバッファーへのポインター。 この値は、IPD のSQL_DESC_CONCISE_TYPEレコード・フィールドから読み取られます。 これは、「付録 D:[データ型」の「SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)」セクションの値の 1 つ、またはドライバー固有の SQL データ型です。  
  
 ODBC 3 で。*x*、SQL_TYPE_DATE、SQL_TYPE_TIME、またはSQL_TYPE_TIMESTAMPは、それぞれ日付、時刻、またはタイムスタンプのデータの*\*DataTypePtr*に返されます。ODBC 2 で使用します。*x*、SQL_DATE、SQL_TIME、またはSQL_TIMESTAMPが返されます。 ドライバー マネージャーは、ODBC 2 の場合に必要なマッピングを実行します。*x*アプリケーションは ODBC 3 で動作しています。*x*ドライバまたは ODBC 3 の場合。*x*アプリケーションは ODBC 2 で動作しています。*x*ドライバ。  
  
 *ColumnNumber*が 0 (ブックマーク列の場合) の場合、可変長ブックマークの場合は*\*DataTypePtr*にSQL_BINARYが返されます。 (ODBC 3 でブックマークが使用されている場合は、SQL_INTEGERが返されます。*x*アプリケーションは ODBC 2 で動作します。*x*ドライバまたは ODBC 2 を使用します。*x*アプリケーションは ODBC 3 で動作します。*x*ドライバ。  
  
 詳細については、「付録 D:[データ型](../../../odbc/reference/appendixes/sql-data-types.md)」の SQL データ型を参照してください。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。  
  
 *パラメーターサイズプラー*  
 [出力]データ ソースで定義されている、対応するパラメーター マーカーの列または式のサイズを文字で返すバッファーへのポインター。 列サイズの詳細については、「[列サイズ、10 進数、オクテット長の転送、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。  
  
 *10 進数の桁数Ptr*  
 [出力]データ ソースで定義されている、対応するパラメーターの列または式の 10 進数の桁数を返すバッファーへのポインター。 10 進数の詳細については、「[列サイズ、10 進数、オクテット長の転送、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。  
  
 *Null 可能なPtr*  
 [出力]パラメーターが NULL 値を許可するかどうかを示す値を返すバッファーへのポインター。 この値は IPD のSQL_DESC_NULLABLEフィールドから読み取られます。 次のいずれか:  
  
-   SQL_NO_NULLS: パラメーターは NULL 値を許可しません (これはデフォルト値です)。  
  
-   SQL_NULLABLE: パラメーターは NULL 値を許可します。  
  
-   SQL_NULLABLE_UNKNOWN: パラメーターが NULL 値を許可するかどうかを判断できません。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLDescribeParam**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は、通常**SQLDescribe パラム**によって返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07009|記述子インデックスが無効です|(DM)*引数パラメータ数*に指定された値が 1 未満です。<br /><br /> *引数 ParameterNumber*に指定された値が、関連する SQL ステートメントのパラメーター数より大きかった。<br /><br /> パラメーター・マーカーは、非 DML ステートメントの一部でした。<br /><br /> パラメータ マーカーは**SELECT**リストの一部でした。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|21S01|値リストが列リストと一致しません|**INSERT**ステートメントのパラメーター数が、ステートメントで指定された表の列数と一致しませんでした。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、*ステートメント ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、関数は*ステートメント ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY010|関数シーケンス エラー|(DM) 関数は、*ステートメント ハンドル*の**SQLPrepare**または**SQLExecDirect**を呼び出す前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLDescribeParam**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 パラメーター・マーカーは、SQL ステートメントに出現する順に、1 から始まる増加パラメーター順で番号付けされます。  
  
 **SQLDescribe パラム**は、SQL ステートメント内のパラメーターの型 (入力、入出力、または出力) を返しません。 プロシージャーの呼び出しを除き、SQL ステートメント内のすべてのパラメーターは入力パラメーターです。 プロシージャの呼び出しで各パラメーターの型を確認するには、アプリケーションは**SQLProcedureColumns を**呼び出します。  
  
 詳細については、「[パラメータの記述」](../../../odbc/reference/develop-app/describing-parameters.md)を参照してください。  
  
## <a name="code-example"></a>コード例  
 次の例では、SQL ステートメントの入力を求めるメッセージを表示し、そのステートメントを準備します。 次に **、SQLNumParams**を呼び出して、ステートメントにパラメーターが含まれているかどうかを判断します。 ステートメントにパラメーターが含まれている場合は **、SQLDescribe パラム**を呼び出してそれらのパラメーターを記述し、それらをバインドする**SQLBindParameter**を呼び出します。 最後に、パラメーターの値をユーザーに求めるプロンプトを表示し、ステートメントを実行します。  
  
```cpp  
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
  
|対象|参照先|  
|---------------------------|---------|  
|バッファーをパラメーターにバインドする|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|実行のためのステートメントの準備|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
