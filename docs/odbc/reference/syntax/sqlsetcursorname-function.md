---
title: 関数を設定する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetCursorName
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetCursorName
helpviewer_keywords:
- SQLSetCursorName function [ODBC]
ms.assetid: 4e055946-12d4-4589-9891-41617a50f34e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6a3bcd07a39401d49be04d141e50c671179efb16
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287342"
---
# <a name="sqlsetcursorname-function"></a>SQLSetCursorName 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **カーソル名を**アクティブステートメントに関連付けます。 アプリケーションが**SQLSetCursorName**を呼び出さない場合、ドライバーは SQL ステートメントの処理に必要なカーソル名を生成します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLSetCursorName(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CursorName,  
     SQLSMALLINT   NameLength);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *カーソル名*  
 [入力]カーソル名。 処理を効率的に行うため、カーソル名の先頭または末尾にスペースを含めず、カーソル名に区切り文字を含める場合は、区切り文字をカーソル名の最初の文字として配置する必要があります。  
  
 *NameLength*  
 [入力]**カーソル名*の文字で長さ。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLSetCursorName が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec** *を呼*び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLSetCursorName**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|カーソル名が最大制限を超えたため、最大許容文字数のみが使用されました。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*に対応するステートメントは、既に実行済みまたはカーソル位置の状態です。|  
|34000|カーソル名が無効|**CursorName*で指定されたカーソル名は、ドライバの定義に従って最大長を超えたか、または "SQLCUR" または "SQL_CURで開始されたため、無効です。|  
|3C000|カーソル名が重複しています|* CursorName に指定された*カーソル名*は既に存在します。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY009|無効な null ポインターの使用|(DM) 引数*カーソル名*は、null ポインターでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 このアインクロナス関数は **、SQLSetCursorName**関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM) 非同期に実行される関数が呼び出されました、 *StatementHandle、* この関数が呼び出されたときに実行されています。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*NameLength*が 0 未満でしたが、SQL_NTSと等しくありません。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 カーソル名は、位置指定更新および削除ステートメント (たとえば **、UPDATE** _table-name_ .**カーソル名の現在**_の_場所 。 詳細については、「[位置指定更新ステートメントとステートメントの削除](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)」を参照してください。 アプリケーションがカーソル名を定義するために**SQLSetCursorName**を呼び出さない場合、クエリ ステートメントの実行時に、ドライバーは文字SQL_CURで始まり、長さが 18 文字を超えない名前を生成します。  
  
 接続内のすべてのカーソル名は一意である必要があります。 カーソル名の最大長は、ドライバーによって定義されます。 相互運用性を最大限に高めるには、アプリケーションでカーソル名を 18 文字以内に制限することをお勧めします。 ODBC 3 *.x*では、カーソル名が引用符で囲まれた識別子である場合、カーソル名は大文字と小文字を区別して扱われ、SQL の構文が許可しない文字や、ブランクや予約キーワードなどの特別な文字を含めることができます。 カーソル名を大文字と小文字を区別して扱う必要がある場合は、引用符で囲まれた識別子として渡す必要があります。  
  
 明示的または暗黙的に設定されたカーソル名は **、SQLFreeHandle**を使用して、関連付けられているステートメントがドロップされるまで設定されたままになります。 **SQLSetCursorName**は、カーソルが割り振りまたは準備された状態である限り、ステートメント上のカーソルの名前を変更するために呼び出すことができます。  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションは**SQLSetCursorName**を使用してステートメントのカーソル名を設定します。 その後、そのステートメントを使用して、CUSTOMERS テーブルから結果を取得します。 最後に、ジョン・スミスの電話番号を変更するために位置指定更新を実行します。 アプリケーションでは **、SELECT**ステートメントと**UPDATE**ステートメントに対して異なるステートメント ハンドルを使用していることに注意してください。  
  
 別のコード例については、「 [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)」を参照してください。  
  
```cpp  
#define NAME_LEN 50  
#define PHONE_LEN 10  
  
SQLHSTMT     hstmtSelect,  
SQLHSTMT     hstmtUpdate;  
SQLRETURN    retcode;  
SQLHDBC      hdbc;  
SQLCHAR      szName[NAME_LEN], szPhone[PHONE_LEN];  
SQLINTEGER   cbName, cbPhone;  
  
/* Allocate the statements and set the cursor name. */  
  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmtSelect);  
SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmtUpdate);  
SQLSetCursorName(hstmtSelect, "C1", SQL_NTS);  
  
/* SELECT the result set and bind its columns to local buffers. */  
  
SQLExecDirect(hstmtSelect,  
      "SELECT NAME, PHONE FROM CUSTOMERS",  
      SQL_NTS);  
SQLBindCol(hstmtSelect, 1, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
SQLBindCol(hstmtSelect, 2, SQL_C_CHAR, szPhone, PHONE_LEN, &cbPhone);  
  
/* Read through the result set until the cursor is */  
/* positioned on the row for John Smith. */  
  
do  
 retcode = SQLFetch(hstmtSelect);  
while ((retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) &&  
   (strcmp(szName, "Smith, John") != 0));  
  
/* Perform a positioned update of John Smith's name. */  
  
if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
   SQLExecDirect(hstmtUpdate,  
   "UPDATE EMPLOYEE SET PHONE=\"2064890154\" WHERE CURRENT OF C1",  
   SQL_NTS);  
}  
```  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|SQL ステートメントの実行|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|カーソル名を返す|[SQLGetCursorName 関数](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|カーソルスクロールオプションの設定|[SQLSetScrollOptions 関数](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
