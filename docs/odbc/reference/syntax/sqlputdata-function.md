---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPutData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPutData
helpviewer_keywords:
- SQLPutData function [ODBC]
ms.assetid: 9a60f004-1477-4c54-a20c-7378e1116713
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c4e704d96924942812904ea63d0e3d4fce8748e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300042"
---
# <a name="sqlputdata-function"></a>SQLPutData 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLPutData**を使用すると、アプリケーションは、ステートメントの実行時に、パラメーターまたは列のデータをドライバーに送信できます。 この関数を使用すると、文字型またはバイナリ データ値を、文字型、バイナリ型、またはデータ ソース固有のデータ型 (SQL_LONGVARBINARY型やSQL_LONGVARCHAR型のパラメーターなど) を持つ列に、部分の文字またはバイナリ データ値を送信できます。 **SQLPutData**は、基になるドライバーが Unicode データをサポートしていない場合でも、Unicode C データ型へのバインドをサポートします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLPutData(  
      SQLHSTMT     StatementHandle,  
      SQLPOINTER   DataPtr,  
      SQLLEN       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *データプラー*  
 [入力]パラメーターまたは列の実際のデータを格納しているバッファーへのポインター。 データは **、SQLBindParameter**の*ValueType*引数で指定された C データ型 (パラメーター データの場合) または**SQLBindCol**の*TargetType*引数 (列データの場合) にする必要があります。  
  
 *StrLen_or_Ind*  
 [入力]\**データPtr*の長さ 。 **SQLPutData**への呼び出しで送信されるデータの量を指定します。 データの量は、指定されたパラメーターまたは列の呼び出しごとに異なる場合があります。 *StrLen_or_Ind*は、次のいずれかの条件を満たしていない限り無視されます。  
  
-   *StrLen_or_Ind*は、SQL_NTS、SQL_NULL_DATA、またはSQL_DEFAULT_PARAMです。  
  
-   SQLBind パラメーターまたは**SQLBindCol** **SQLBindCol**で指定された C データ型は、SQL_C_CHARまたはSQL_C_BINARY。  
  
-   C データ型はSQL_C_DEFAULT、指定された SQL データ型の既定の C データ型はSQL_C_CHARまたはSQL_C_BINARYです。  
  
 その他のすべての C データの場合 *、StrLen_or_Ind*がSQL_NULL_DATAまたはSQL_DEFAULT_PARAMされていない場合、ドライバーは\**、DataPtr*バッファーのサイズが*ValueType*または*TargetType*で指定された C データ型のサイズであると見なし、データ値全体を送信します。 詳細については、「付録 D:[データ型」の「C から SQL データ型への](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)データの変換」を参照してください。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLPutData が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec** *を呼*び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLPutData**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|出力パラメータに対して返された文字列またはバイナリ データは、空白以外の文字または NULL 以外のバイナリ データの切り捨てになります。 文字列値の場合は、右に切り捨てられます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07006|制限付きデータ型属性違反|バインドされたパラメーターの**SQLBindParameter**の*値型*引数で識別されるデータ値を **、SQLBindParameter**の*引数 ParameterType*で識別されるデータ型に変換できませんでした。|  
|07S01|既定のパラメーターの使用が無効です|**SQLBindParameter**で設定されたパラメーター値がSQL_DEFAULT_PARAMされ、対応するパラメーターに既定値が設定されていません。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|22001|文字列データ、右切り捨て|列に文字またはバイナリー値を割り当てると、ブランク (文字) 以外の文字または非ヌル (バイナリー) 文字またはバイトが切り捨てされました。<br /><br /> **SQLGetInfo**のSQL_NEED_LONG_DATA_LEN情報型は "Y" で **、SQLBindParameter**で*StrLen_or_IndPtr*引数を指定した場合よりも長いパラメーター (データ型がSQL_LONGVARCHAR、SQL_LONGVARBINARY、または長いデータ ソース固有のデータ型) に対して送信されたデータが多かった。<br /><br /> **SQLGetInfo**のSQL_NEED_LONG_DATA_LEN情報の種類は "Y" で **、SQLBulkOperations で**追加または更新されたデータ行の列に対応する長さバッファーに指定された長さバッファーに指定された長さバッファーに指定されたデータよりも長い列 (データ型がSQL_LONGVARCHAR、SQL_LONGVARBINARY、または長いデータ ソース固有のデータ型) に送信されたデータが**多かった。**|  
|22003|範囲外の数値|バインドされた数値パラメータまたは列に送信されたデータにより、関連付けられたテーブル列に割り当てられると、数値の全体 (小数部ではなく) 部分が切り捨てられました。<br /><br /> 1 つ以上の入出力パラメーターまたは出力パラメーターの数値 (数値またはストリング) を戻すと、数値の全体 (小数部ではなく) 部分が切り捨てられる可能性があります。|  
|22007|日付/時刻形式が無効です|日付、時刻、またはタイム・スタンプ構造にバインドされたパラメーターまたは列に対して送信されたデータが、それぞれ無効な日付、時刻、またはタイム・スタンプであった。<br /><br /> 入力/出力または出力パラメーターが日付、時刻、またはタイム・スタンプ C の構造体にバインドされており、戻り値の値がそれぞれ無効な日付、時刻、またはタイム・スタンプでした。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|22008|日時フィールドのオーバーフロー|入力/出力パラメータまたは出力パラメータに対して計算された日時式の結果、無効な日付、時刻、またはタイムスタンプ C の構造体が生成されました。|  
|22012|ゼロ除算|入力/出力パラメータまたは出力パラメータで計算された算術式の結果、0 で除算されます。|  
|22015|間隔フィールドのオーバーフロー|正確な数値または間隔の列またはパラメーターに対して、間隔 SQL データ・タイプに送信されたデータが、有効数字の損失を引き起こしました。<br /><br /> 複数のフィールドを持つ区間列またはパラメーターに対してデータが送信され、数値データ型に変換され、数値データ型に表現が含まれていなかった。<br /><br /> 列またはパラメーター・データに送信されたデータがインターバル SQL タイプに割り当てられ、間隔 SQL タイプの C タイプの値の表現が存在しなかった。<br /><br /> 正確な数値または間隔 C 列または間隔 C の列またはパラメーターに対して送信されたデータが、有効数字の損失を引き起こしました。<br /><br /> 列またはパラメーター・データに送信されたデータが、インターバル C 構造に割り当てられ、間隔データ構造内にデータの表現がなかった。|  
|22018|キャスト指定に無効な文字値|C 型は、正確な数値または概数、日時、または間隔のデータ型でした。列の SQL 型は文字データ型でした。列またはパラメーターの値が、バインドされた C 型の有効なリテラルではありません。<br /><br /> SQL タイプは、正確または概数、日時、または間隔データ型でした。C 型はSQL_C_CHAR。列またはパラメーターの値が、バインドされた SQL 型の有効なリテラルではありません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、*ステートメント ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、関数は*ステートメント ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY009|無効な null ポインターの使用|(DM)*引数 DataPtr*がヌル・ポインターであり、*引数 StrLen_or_Ind*が 0、SQL_DEFAULT_PARAM、またはSQL_NULL_DATAではありませんでした。|  
|HY010|関数シーケンス エラー|(DM) 以前の関数呼び出しは **、SQLPutData**または**SQLParamData**への呼び出しではありませんでした。<br /><br /> (DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は、SQLPutData 関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY019|文字以外のデータとバイナリ以外のデータを分割して送信|**SQLPutData**は、パラメーターまたは列に対して複数回呼び出され、文字 C データを文字、バイナリ、またはデータ ソース固有のデータ型を持つ列に送信したり、バイナリ C データを文字、バイナリ、またはデータ ソース固有のデータ型の列に送信したりするために使用されていませんでした。|  
|HY020|NULL 値を連結しようとしました。|**SQLPutData**は、SQL_NEED_DATAを返した呼び出し以降に複数回呼び出されましたが、その呼び出しの 1 つで *、StrLen_or_Ind*引数にSQL_NULL_DATAまたはSQL_DEFAULT_PARAMが含まれていました。|  
|HY090|無効な文字列またはバッファ長|引数*DataPtr*が null ポインターではなく、引数*StrLen_or_Ind*が 0 未満でしたが、SQL_NTSまたはSQL_NULL_DATAと等しくありません。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
 **SQLPutData**が SQL ステートメント内のパラメーターのデータを送信しているときに呼び出された場合、ステートメントを実行するために呼び出される関数によって返される SQLSTATE を返すことができます (**SQLExecute**または**SQLExecDirect**) 。 更新または追加される列のデータを送信中に呼び出された場合、または**SQLSetPos**で更新されている列のデータを呼び出す場合は **、SQLBulkOperations**または**SQLSetPos**によって返される可能性のある SQLSTATE を返すことができます。 **SQLSetPos**  
  
## <a name="comments"></a>説明  
 **SQLPutData**を呼び出して **、2**つの用途に対して実行データデータを提供できます。 **SQLExecDirect** **SQLBulkOperations** **SQLSetPos**  
  
 アプリケーションが**SQLParamData**を呼び出して送信するデータを決定すると、ドライバーは、アプリケーションがどのパラメーター データを送信するか、列データを見つけることができるかを決定するために使用できるインジケーターを返します。 また、SQL_NEED_DATA返すのもアプリケーションに示す指標であり、データを送信するために**SQLPutData**を呼び出す必要があります。 引数*DataPtr*から**SQLPutData**に対する引数では、アプリケーションは、パラメーターまたは列の実際のデータを格納しているバッファーへのポインターを渡します。  
  
 ドライバーは **、SQLPutData**のSQL_SUCCESSを返すと、アプリケーションは、再び**SQLParamData**を呼び出します。 さらに多くのデータを送信する必要がある場合は **、sqlParamData**はSQL_NEED_DATAを**SQLPutData**返します。 すべての実行時データが送信された場合は、SQL_SUCCESSを返します。 その後、アプリケーションは再び**SQLParamData を**呼び出します。 ドライバーが SQL_NEED_DATAを返し*\*、ValuePtrPtr*に別のインジケーターを返す場合は、別のパラメーターまたは列の**データが必要**です。 ドライバーがSQL_SUCCESSを返す場合は、実行時にデータのすべてのデータが送信され、SQL ステートメントを実行するか **、SQLBulkOperations**または**SQLSetPos**呼び出しを処理できます。  
  
 ステートメント実行時に実行時データパラメーター・データを渡す方法の詳細については、 [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)の「パラメーター値の引き渡し」および[「長いデータの送信](../../../odbc/reference/develop-app/sending-long-data.md)」を参照してください。 実行時のデータ列データの更新または追加方法の詳細については[、SQLSetPos の「SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)の使用[」、SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)の「ブックマークを使用した一括更新の実行」、および[長いデータと SQLSetPos および SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)を参照してください。  
  
> [!NOTE]  
>  アプリケーションは、文字 C データを文字、バイナリ、またはデータ ソース固有のデータ型を持つ列に送信する場合、または文字、バイナリ、またはデータ ソース固有のデータ型を持つ列にバイナリ C データを送信する場合にのみ **、SQLPutData**を使用してデータを送信できます。 **SQLPutData**が他の条件下で複数回呼び出された場合、SQL_ERRORと SQLSTATE HY019 (非文字データと非バイナリー・データが分割して送信される) が戻されます。  
  
## <a name="example"></a>例  
 次のサンプルでは、Test という名前のデータ ソース名を想定しています。 関連付けられたデータベースには、次のように作成できるテーブルが必要です。  
  
```sql  
CREATE TABLE emp4 (NAME char(30), AGE int, BIRTHDAY datetime, Memo1 text)  
```  
  
```cpp  
// SQLPutData.cpp  
// compile with: odbc32.lib user32.lib  
#include <stdio.h>  
#include <windows.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define TEXTSIZE  12000  
#define MAXBUFLEN 256  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // SQLBindParameter variables.  
   SQLLEN cbTextSize, lbytes;  
  
   // SQLParamData variable.  
   PTR pParmID;  
  
   // SQLPutData variables.  
   UCHAR  Data[] =   
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwxyz"  
      "abcdefghijklmnopqrstuvwxyz";  
  
   SDWORD cbBatch = (SDWORD)sizeof(Data) - 1;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set parameters based on total data to send.  
   lbytes = (SDWORD)TEXTSIZE;  
   cbTextSize = SQL_LEN_DATA_AT_EXEC(lbytes);  
  
   // Bind the parameter marker.  
   retcode = SQLBindParameter (hstmt1,           // hstmt  
                               1,                // ipar  
                               SQL_PARAM_INPUT,  // fParamType  
                               SQL_C_CHAR,       // fCType  
                               SQL_LONGVARCHAR,  // FSqlType  
                               lbytes,           // cbColDef  
                               0,                // ibScale  
                               (VOID *)1,        // rgbValue  
                               0,                // cbValueMax  
                               &cbTextSize);     // pcbValue  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLBindParameter Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the command.  
   retcode =   
      SQLExecDirect(hstmt1, (UCHAR*)"INSERT INTO emp4 VALUES('Paul Borm', 46,'1950-11-12 00:00:00', ?)", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_NEED_DATA) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Check to see if NEED_DATA; if yes, use SQLPutData.  
   retcode = SQLParamData(hstmt1, &pParmID);  
   if (retcode == SQL_NEED_DATA) {  
      while (lbytes > cbBatch) {  
         SQLPutData(hstmt1, Data, cbBatch);  
         lbytes -= cbBatch;  
      }  
      // Put final batch.  
      retcode = SQLPutData(hstmt1, Data, lbytes);   
   }  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLParamData Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Make final SQLParamData call.  
   retcode = SQLParamData(hstmt1, &pParmID);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("Final SQLParamData Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clean up.  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|バッファーをパラメーターにバインドする|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|SQL ステートメントの実行|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|データを送信する次のパラメータを返す|[SQLParamData 関数](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
