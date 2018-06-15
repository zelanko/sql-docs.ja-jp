---
title: SQLSetCursorName 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64c560f2934d04b098ed26c347d2819d90948e5f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32920577"
---
# <a name="sqlsetcursorname-function"></a>SQLSetCursorName 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLSetCursorName**カーソル名をアクティブなステートメントに関連付けます。 アプリケーションが要求されていない場合**SQLSetCursorName**ドライバーで SQL ステートメントの処理に必要なカーソル名が生成されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLSetCursorName(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CursorName,  
     SQLSMALLINT   NameLength);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *カーソル名*  
 [入力]カーソルの名前です。 効率的な処理は、カーソル名では、カーソル名の先頭または末尾の空白含めないでし、カーソル名の最初の文字として、区切り記号を配置する必要があります、カーソル名には、区切られた識別子が含まれている場合。  
  
 *NameLength*  
 [入力]文字の長さ **カーソル名*です。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLSetCursorName** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType*のSQL_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLSetCursorName**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|カーソル名の最大値を超過、ので文字の最大許容数のみが使用されました。|  
|24000|カーソル状態が無効|対応するステートメント*StatementHandle*が既に実行された、またはカーソルの置かれている状態にします。|  
|34000|カーソル名が無効|指定されたカーソル名 **カーソル名*ドライバーで定義されている最大長を超えたか、"SQLCUR"または"SQL_CUR"起動時のため無効でした|  
|3C000|カーソル名が重複してください。|指定されたカーソル名 **カーソル名*既に存在します。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY009|無効な null ポインターの使用|(DM) 引数*カーソル名*が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLSetCursorName**関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) 引数*NameLength* SQL_NTS に等しくないが、0 より小さいをでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 カーソル名が位置指定更新でのみ使用および delete ステートメント (たとえば、**更新***テーブル名*.**WHERE CURRENT OF** *カーソル名*)。 詳細については、次を参照してください。[位置指定の Update ステートメントとステートメントの削除](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)です。 アプリケーションが要求されていない場合**SQLSetCursorName**ドライバーが SQL_CUR 文字で始まり、かつ 18 文字の長さを超えていない名前を生成クエリ ステートメントの実行時に、カーソル名を定義します。  
  
 接続内のすべてのカーソル名は一意である必要があります。 カーソル名の最大長は、ドライバーによって定義されます。 相互運用性を最大にするため、アプリケーションは 18 個までの文字にカーソル名を制限することをお勧めします。 ODBC 3 *.x*カーソル名は引用符で囲まれた識別子かどうかは、大文字小文字を区別の方法で扱われ、SQL の構文について、ことを認めていないまたは空白などの特別な処理、または予約済みキーワードで、文字を含めることができます。 カーソル名は、大文字小文字を区別の方法で扱う必要があるを場合は、引用符で囲まれた識別子として渡す必要があります。  
  
 カーソル名を明示的に設定されて、または暗黙的に設定を使用して、それが関連付けられているステートメントが削除されるまで**SQLFreeHandle**です。 **SQLSetCursorName**カーソルが割り当てられているまたは準備された状態である限り、ステートメントのカーソルの名前を変更するに呼び出せることができます。  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションを使用して**SQLSetCursorName**ステートメントのカーソル名を設定します。 そのステートメントを使用して、CUSTOMERS テーブルから結果を取得します。 最後に、John Smith の電話番号を変更する位置指定更新を実行します。 別のステートメント ハンドルを使用して、アプリケーション、**選択**と**更新**ステートメントです。  
  
 別のコード例では、次を参照してください。 [SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)です。  
  
```  
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
  
|詳細|参照先|  
|---------------------------|---------|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|カーソル名を返す|[SQLGetCursorName 関数](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|カーソルがスクロール オプションの設定|[SQLSetScrollOptions 関数](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
