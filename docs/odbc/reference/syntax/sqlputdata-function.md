---
title: "SQLPutData 関数 |Microsoft ドキュメント"
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
apiname: SQLPutData
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLPutData
helpviewer_keywords: SQLPutData function [ODBC]
ms.assetid: 9a60f004-1477-4c54-a20c-7378e1116713
caps.latest.revision: "28"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 60d6ad48f44d4d4301b8570c51fc83f7aa42d734
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlputdata-function"></a>SQLPutData 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLPutData**により、ステートメントの実行時にドライバーをパラメーターまたは列のデータを送信するアプリケーション。 この関数は、部分の文字、バイナリ、またはデータ ソース固有のデータ型 (たとえば、SQL_LONGVARBINARY または SQL_LONGVARCHAR 型のパラメーター) を持つ列に文字またはバイナリ データ値を送信する使用できます。 **SQLPutData**基になるドライバーが Unicode データをサポートしていない場合でも、Unicode の C データ型へのバインドをサポートしています。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLPutData(  
      SQLHSTMT     StatementHandle,  
      SQLPOINTER   DataPtr,  
      SQLLEN       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *DataPtr*  
 [入力]パラメーターまたは列の実際のデータを格納するバッファーへのポインター。 データがで指定された C データ型である必要があります、 *ValueType*の引数**SQLBindParameter** (のパラメーターのデータ)、または*TargetType*の引数**SQLBindCol** (の列のデータ)。  
  
 *StrLen_or_Ind*  
 [入力]長さ\* *DataPtr*です。 呼び出しに送られるデータの量を指定**SQLPutData**です。 データの量には、指定されたパラメーターまたは列の各呼び出しはによって異なります。 *StrLen_or_Ind*は、次の条件を満たしている場合を除き、無視されます。  
  
-   *StrLen_or_Ind* SQL_NTS、SQL_NULL_DATA、または SQL_DEFAULT_PARAM がします。  
  
-   C データ型がで指定された**SQLBindParameter**または**SQLBindCol** SQL_C_CHAR または SQL_C_BINARY です。  
  
-   C データ型は SQL_C_DEFAULT、および指定した SQL データ型の既定の C データ型は、SQL_C_CHAR または SQL_C_BINARY です。  
  
 すべての他の種類の C データ場合*StrLen_or_Ind* SQL_NULL_DATA または SQL_DEFAULT_PARAM ではないドライバーと見なしますのサイズ、 \* *DataPtr*バッファーが指定された C データ型のサイズ*ValueType*または*TargetType*し、データ値全体を送信します。 詳細については、次を参照してください。[に変換するデータを C から SQL データ型を](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)付録 d: データ型にします。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLPutData** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLPutData**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|文字列または出力パラメーターに対して返されるバイナリ データは、空白でない文字またはバイナリ データが NULL 以外の切り捨てが発生しました。 文字列値が、右側の切り捨てでした。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|識別されるデータ値、 *ValueType*引数**SQLBindParameter**で識別されるデータ型にバインドされたパラメーターを変換できませんでしたの*ParameterType*引数**SQLBindParameter**です。|  
|07S01|既定のパラメーターの使い方が正しくありません。|パラメーターの値の設定と**SQLBindParameter**SQL_DEFAULT_PARAM が、および対応するパラメーターが、既定値はありませんでした。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|22001|文字列データの右側が切り捨てられました|文字またはバイナリ列に値の割り当ては、空白 (文字) または null (バイナリ) の文字またはバイトの切り捨てが発生しました。<br /><br /> SQL_NEED_LONG_DATA_LEN 情報の種類で**SQLGetInfo** "Y"、指定された数より長いパラメーター (データ型は、SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長い形式のデータ ソース固有のデータ型をされました) のより多くのデータが送信されました*StrLen_or_IndPtr*引数**SQLBindParameter**です。<br /><br /> SQL_NEED_LONG_DATA_LEN 情報の種類で**SQLGetInfo** "Y"で指定されたよりも長い列 (データ型は、SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長い形式のデータ ソース固有のデータ型をいました) に多くのデータが送信された、追加または更新されたデータの行の列に対応する長バッファー **SQLBulkOperations**またはで更新された**SQLSetPos**です。|  
|22003|数値が範囲|列に関連付けられているテーブルの列に割り当てられている場合に切り捨てられるように数値のではなく小数部) 全体の一部が原因となったまたはバインドされた数値パラメーターのデータが送信されます。<br /><br /> 1 つまたは複数の入力/出力パラメーターまたは出力パラメーターの (数値または文字列) としての数値の値を返す原因となる (ではなく小数部) 整数部分が切り捨てられる数値。|  
|22007|無効な datetime 形式|パラメーターまたは日付、時刻、またはタイムスタンプの構造体にバインドされている列に送信されるデータが、それぞれに、無効な日付、時刻、またはタイムスタンプ。<br /><br /> 入力/出力パラメーターと出力パラメーターは、日付、時刻、またはタイムスタンプ C 構造にバインドされていたし、返されるパラメーターの値が、それぞれに、無効な日付、時刻、またはタイムスタンプ。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|22008|Datetime フィールド オーバーフロー|Datetime 式が入力/出力の計算、または出力パラメーターの日付、時刻、または無効なタイムスタンプ C の構造体が発生しました。|  
|22012|0 による除算です。|算術式の入力/出力の計算または 0 による除算では、出力パラメーターが発生しました。|  
|22015|間隔のフィールドがオーバーフローしました|間隔 SQL データ型のパラメーターの有効桁数が失われる原因となったまたは正確な数値型または interval 列のデータが送信されます。<br /><br /> データは、期間列または複数のフィールドを持つパラメーターの送信された、数値データ型に変換されましたおよび数値データ型の表現がなかった。<br /><br /> 間隔 SQL 型に割り当てられた列に送信されるデータまたはパラメーターのデータと、SQL 型の間隔で、C 型の値の形式がありませんでした。<br /><br /> 正確な numeric または間隔 C 列またはパラメーター間隔 C 型を送信するデータには、有効桁数の損失が発生します。<br /><br /> 列に送信されるデータまたはパラメーターのデータは、間隔 C 構造に割り当てられたおよび間隔のデータ構造内のデータの表現がありませんでした。|  
|22018|キャストは無効な文字値|C 型が、真数または概数の数値、datetime、または、interval データ型です。列の SQL 型が文字データ型です。列またはパラメーターの値がバインドされた C 型の有効なリテラルではありませんでした。<br /><br /> SQL 型が、真数または概数の数値、datetime、または、interval データ型です。C 型が SQL_C_CHAR です。列またはパラメーターの値がバインドされた SQL 型の有効なリテラルではありませんでした。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY009|無効な null ポインターの使用|(DM) 引数*DataPtr*が null ポインターの場合と、引数*StrLen_or_Ind*でした 0、SQL_DEFAULT_PARAM、または SQL_NULL_DATA です。|  
|HY010|関数のシーケンス エラー|(DM) 前の関数呼び出しがへの呼び出し**SQLPutData**または**SQLParamData**です。<br /><br /> (DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 SQLPutData 関数が呼び出されたときに、この非同期関数が実行されています。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY019|個別に送信される文字またはバイナリ以外のデータ|**SQLPutData**と呼ばれる複数の 1 回パラメーターまたは列をそれが使用されていない文字、バイナリ、またはデータ ソース固有のデータ型を持つ列を文字データを送信するか、文字の列にバイナリの C データを送信するには、バイナリ、またはデータ ソース固有のデータ型。|  
|HY020|Null 値を連結しようとしてください。|**SQLPutData** 、SQL_NEED_DATA が返されますの呼び出し以降とそれらの呼び出しのいずれかで複数回呼び出された、 *StrLen_or_Ind* SQL_NULL_DATA または SQL_DEFAULT_PARAM 引数が含まれています。|  
|HY090|文字列またはバッファーの長さが無効です。|引数*DataPtr*が null ポインターの場合と、引数*StrLen_or_Ind* SQL_NTS または SQL_NULL_DATA 等しくないが、0 より小さいをでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
 場合**SQLPutData**が呼び出された SQL ステートメントにパラメーターのデータを送信中に、ステートメントを実行すると呼ばれる、関数によって返される任意の SQLSTATE を返すこと (**SQLExecute**または**SQLExecDirect**)。 列のデータを送信中に呼び出されると更新または追加された**SQLBulkOperations**で更新されているまたは**SQLSetPos**、によって返される任意の SQLSTATE を返すことができます**SQLBulkOperations**または**SQLSetPos**です。  
  
## <a name="comments"></a>コメント  
 **SQLPutData** 2 つの用途の実行時データのデータを指定するに呼び出せる: パラメーターのデータへの呼び出しで使用される**SQLExecute**または**SQLExecDirect**、または列のデータ行がある場合に使用します。更新またはへの呼び出しによって追加**SQLBulkOperations**への呼び出しによって更新または**SQLSetPos**です。  
  
 アプリケーションを呼び出すと**SQLParamData**データを決定するを送る、ドライバーは、アプリケーション パラメーター データを送信する決定を使用している、または列のデータがあるインジケーターを返します。 また、これを呼び出して、アプリケーションにインジケーターは SQL_NEED_DATA を返します**SQLPutData**データを送信します。 *DataPtr*引数**SQLPutData**アプリケーションが、パラメーターまたは列の実際のデータを格納するバッファーへのポインターを渡します。  
  
 ドライバーでの SQL_SUCCESS が返されるときに**SQLPutData**、アプリケーション呼び出し**SQLParamData**もう一度です。 **SQLParamData** SQL_NEED_DATA より多くのデータを送信する必要がある場合は、アプリケーションの呼び出しが返されます**SQLPutData**もう一度です。 実行時データのすべてのデータが送信された場合は関係なく SQL_SUCCESS を返します。 その後、アプリケーションを呼び出す**SQLParamData**もう一度です。 ドライバーが SQL_NEED_DATA とで別のインジケーターを返す場合 *\*ValuePtrPtr*、別のパラメーターまたは列にデータが必要と**SQLPutData**が再度呼び出されます。 データが送信され、SQL ステートメントを実行することができる場合は、ドライバー SQL_SUCCESS を返します、し、すべての実行時データまたは**SQLBulkOperations**または**SQLSetPos**呼び出しを処理することができます。  
  
 方法の実行時データ パラメーターのデータの詳細については、ステートメントの実行時に渡されたを参照してください「パラメーターの値の引き渡し」 [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)と[長い形式のデータを送信する](../../../odbc/reference/develop-app/sending-long-data.md)です。 方法の実行時データ列のデータの詳細については、更新または追加のセクションを参照して"を使用して SQLSetPos" [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)、「を実行する一括更新プログラムを使用してブックマーク」で[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)、および[長い形式のデータおよび SQLSetPos SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)です。  
  
> [!NOTE]  
>  アプリケーションで使用できます**SQLPutData**文字、バイナリ、またはデータ ソース固有のデータ型の列に文字データを送信するときにのみ、または列を文字、バイナリ、C のバイナリ データを送信するときに部分のデータまたはデータを送信するにはソース固有のデータを入力します。 場合**SQLPutData**は呼び出されますも複数回、他の条件下で SQL_ERROR と返す SQLSTATE HY019 (文字でないと非バイナリのデータを個別に送信する場合)。  
  
## <a name="example"></a>例  
 次の例では、Test」という名前のデータ ソース名と仮定します。 関連付けられたデータベースは、次のように、作成できるテーブルが必要です。  
  
```  
CREATE TABLE emp4 (NAME char(30), AGE int, BIRTHDAY datetime, Memo1 text)  
```  
  
```  
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
  
|詳細|参照先|  
|---------------------------|---------|  
|パラメーターへのバッファーのバインド|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|データを送信する次のパラメーターを返す|[SQLParamData 関数](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
