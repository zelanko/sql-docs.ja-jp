---
title: SQLPrepare 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLPrepare
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLPrepare
helpviewer_keywords:
- SQLPrepare function [ODBC]
ms.assetid: 332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e9aedd665df2a943627207902d592d597c503c63
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306883"
---
# <a name="sqlprepare-function"></a>SQLPrepare 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQL の**文字列を実行する準備をします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLPrepare(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     StatementText,  
     SQLINTEGER    TextLength);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *ステートメントテキスト*  
 [入力]SQL テキスト文字列。  
  
 *TextLength*  
 [入力]**文字のテキスト*の長さ。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLPrepare が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLPrepare**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S02|オプション値が変更されました|指定されたステートメント属性は、実装の動作条件のために無効であったため、同様の値が一時的に置換されました。 (**SQLGetStmtAttr**を呼び出して、一時的に置換された値が何であるかを判別できます。代替値は、カーソルが閉じられるまで*ステートメント ハンドル*に対して有効です。 変更できるステートメント属性は SQL_ATTR_KEYSET_SIZE SQL_ATTR_CURSOR_TYPE、SQL_ATTR_MAX_LENGTHSQL_ATTR_CONCURRENCYSQL_ATTR_MAX_LENGTHSQL_ATTR_CONCURRENCY SQL_ATTR_QUERY_TIMEOUTSQL_ATTR_MAX_ROWSSQL_ATTR_SIMULATE_CURSOR<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|21S01|値リストが列リストと一致しません|\**ステートメントテキストに* **INSERT**ステートメントが含まれていて、挿入する値の数が、派生テーブルの度合いと一致しませんでした。|  
|21S02|派生テーブルの次数が列リストと一致しません|\**ステートメントテキストに* **CREATE VIEW**ステートメントが含まれており、指定された名前の数が、照会指定で定義された派生表と同じ位数ではありません。|  
|22018|キャスト指定に無効な文字値|**ステートメントテキストに*リテラルまたはパラメーターを含む SQL ステートメントが含まれており、その値は関連付けられた表列のデータ・タイプと互換性がありません。|  
|22019|無効なエスケープ文字|引数*StatementText*には**WHERE**句に**ESCAPE**を含む**LIKE**述語が含まれており **、ESCAPE**の後のエスケープ文字の長さが 1 と等しくありません。|  
|22025|無効なエスケープ シーケンス|引数*のステートメントテキスト*には**WHERE**句に **"LIKE** _パターン値_ **ESCAPE エスケープ**_文字_" が含まれ、パターン値のエスケープ文字の後に続く文字は "%" でも "_" でもありませんでした。|  
|24000|カーソル状態が無効|(DM)*ステートメント ハンドル*でカーソルが開かれていたし **、SQL フェッチ**または**SQL フェッチスクロール**が呼び出されました。<br /><br /> *ステートメント ハンドル*でカーソルが開かれていたが **、SQLFetch**または**SQLFetchScroll が**呼び出されていませんでした。|  
|34000|カーソル名が無効|\**ステートメントテキストに*位置付け**DELETE**または位置指定**UPDATE**が含まれていて、準備中のステートメントが参照するカーソルが開かれていない。|  
|3D000|無効なカタログ名です|*ステートメント テキスト*で指定されたカタログ名が無効です。|  
|3F000|無効なスキーマ名です|*ステートメント テキスト*で指定されたスキーマ名が無効です。|  
|42000|構文エラーまたはアクセス違反|\**ステートメントテキストに*、修復できないか、構文エラーが含まれている SQL ステートメントが含まれていました。<br /><br /> **ステートメントテキスト*には、ユーザーが必要な特権を持っていないステートメントが含まれていました。|  
|42S01|ベース テーブルまたはビューは既に存在します|\**ステートメント・テキストに* **CREATE TABLE**ステートメントまたは**CREATE VIEW**ステートメントが含まれ、指定された表名またはビュー名が既に存在します。|  
|42S02|ベース テーブルまたはビューが見つかりません|\**ステートメント・テキストに* **DROP TABLE**ステートメントまたは**DROP VIEW**ステートメントが含まれていて、指定された表名またはビュー名が存在しませんでした。<br /><br /> \**ステートメントテキストに* **ALTER TABLE**ステートメントが含まれていますが、指定されたテーブル名が存在しませんでした。<br /><br /> \**ステートメントテキストに* **CREATE VIEW**ステートメントが含まれていて、照会指定で定義された表名またはビュー名が存在しませんでした。<br /><br /> \**ステートメント テキストに* **CREATE INDEX**ステートメントが含まれていますが、指定されたテーブル名が存在しませんでした。<br /><br /> \**ステートメント・テキストに* **GRANT**ステートメントまたは**REVOKE**ステートメントが含まれていて、指定された表名またはビュー名が存在しませんでした。<br /><br /> \**ステートメント テキストに* **SELECT**ステートメントが含まれていますが、指定されたテーブル名またはビュー名が存在しませんでした。<br /><br /> \**ステートメントテキストに* **DELETE**、**挿入**、または**UPDATE**ステートメントが含まれていて、指定されたテーブル名が存在しませんでした。<br /><br /> \**ステートメントテキストに* **CREATE TABLE**ステートメントが含まれていて、制約で指定されたテーブル (作成中のテーブル以外のテーブルを参照) が存在しませんでした。|  
|42S11|インデックスは既に存在します|\**ステートメントテキストに* **CREATE INDEX**ステートメントが含まれていて、指定されたインデックス名が既に存在しています。|  
|42S12|インデックスが見つかりません|\**ステートメントテキストに* **DROP INDEX**ステートメントが含まれていますが、指定されたインデックス名が存在しませんでした。|  
|42S21|列は既に存在します|\**ステートメント・テキスト*に**ALTER TABLE**ステートメントが含まれていて **、ADD**文節で指定された列が固有でないか、または基本表内の既存の列を識別します。|  
|42S22|列が見つかりません|\**ステートメントテキストに* **CREATE INDEX**ステートメントが含まれていて、列リストに指定された 1 つ以上の列名が存在しませんでした。<br /><br /> \**ステートメントテキストに* **GRANT**または**REVOKE**ステートメントが含まれていますが、指定された列名が存在しませんでした。<br /><br /> \**ステートメントテキストに***、SELECT**、**削除**、**挿入**、または**UPDATE**ステートメントが含まれていて、指定された列名が存在しませんでした。<br /><br /> \**ステートメントテキストに* **CREATE TABLE**ステートメントが含まれていて、制約で指定された列 (作成中のテーブル以外のテーブルを参照) が存在しませんでした。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、ステートメント ハンドルで**SQLCancel**または**SQLCancelHandle**が呼び出された後、*ステートメント ハンドル*で関数が再度呼び出されました。 *StatementHandle*<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY009|無効な null ポインターの使用|(DM)*ステートメントテキスト*はヌルポインタでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLPrepare**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*TextLength*が 0 以下でしたが、SQL_NTSと等しくありません。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|定義されたカーソルの種類に対して同時実行設定が無効でした。<br /><br /> SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_VARIABLE に設定され、SQL_ATTR_CURSOR_TYPE ステートメント属性が、ドライバーがブックマークをサポートしていないカーソルの種類に設定されました。|  
|ヒュット00|タイムアウトに達しました|データ ソースが結果セットを返す前にタイムアウト期間が切れました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUT**を**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 アプリケーションは**SQLPrepare**を呼び出して、準備のために SQL ステートメントをデータ ソースに送信します。 準備実行の詳細については、「[準備された実行](../../../odbc/reference/develop-app/prepared-execution-odbc.md)」を参照してください。 アプリケーションは、SQL ステートメントに 1 つ以上のパラメーター・マーカーを組み込むことができます。 パラメーター マーカーを含めるには、アプリケーションは SQL 文字列内の適切な位置に疑問符 (?) を埋め込みます。 パラメータの詳細については、「[ステートメント パラメータ](../../../odbc/reference/develop-app/statement-parameters.md)」を参照してください。  
  
> [!NOTE]  
>  アプリケーションが**SQLPrepare を**使用して準備を行い **、SQLExecute を**使用して**COMMIT**ステートメントまたは**ROLLBACK**ステートメントをサブミットする場合、DBMS 製品間で相互運用することはできません。 トランザクションをコミットまたはロールバックするには、 **SQLEndTran**を呼び出します。  
  
 ドライバーは、データ ソースで使用される SQL の形式を使用してステートメントを変更し、データ ソースに送信して準備を行うことができます。 特に、ドライバーは、特定の機能の SQL 構文を定義するために使用されるエスケープ シーケンスを変更します。 (SQL ステートメント文法の詳細については[、「ODBC のエスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)」および[「付録 C: SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)」を参照してください。ドライバーのステートメント ハンドルは、埋め込まれた SQL コード内のステートメント識別子に似ています。 データ ソースがステートメント識別子をサポートしている場合、ドライバーは、ステートメント識別子とパラメーター値をデータ ソースに送信できます。  
  
 ステートメントが準備されると、アプリケーションはステートメント・ハンドルを使用して、後の関数呼び出しでステートメントを参照します。 ステートメント ハンドルに関連付けられたプリペアド ステートメントは**SQLPrepare**、SQLFree を呼び出して**SQLExecDirect****SQLExecute** SQL_DROP**SQLFreeStmt**を呼び出して再実行できます。**SQLColumns** **SQLTables** アプリケーションは、ステートメントを準備すると、結果セットの形式に関する情報を要求できます。 一部の実装では **、SQLPrepare**の後に**SQLDescribeCol**または**SQLDescribe パラム**を呼び出すことは **、SQLExecute**または**SQLExecDirect**の後に関数を呼び出すほど効率的ではない可能性があります。  
  
 アプリケーションが**SQLPrepare**を呼び出すときに構文エラーやアクセス違反を返すことができないドライバーもあります。 ドライバーは構文エラーとアクセス違反、構文エラーのみ、または構文エラーやアクセス違反を処理できます。 したがって、**アプリケーションは、SQLNumResultCols** **、SQLDescribeCol、SQLCol****属性**、および**SQLExecute**などの後続の関連する関数を呼び出すときに、これらの条件を処理できる必要があります。  
  
 ドライバーとデータ ソースの機能によっては、ステートメントの準備時 (すべてのパラメーターがバインドされている場合) または実行時 (すべてのパラメーターがバインドされていない場合) に、パラメーター情報 (データ型など) がチェックされる場合があります。 相互運用性を最大限に高めるには、アプリケーションは、同じステートメントで新しい SQL ステートメントを準備する前に、古い SQL ステートメントに適用されたすべてのパラメーターをアンバインドする必要があります。 これにより、古いパラメータ情報が新しいステートメントに適用されたことによるエラーを防ぐことができます。  
  
> [!IMPORTANT]  
>  **SQLEndTran**を明示的に呼び出すか、自動コミット モードで動作することによってトランザクションをコミットすると、データ ソースが接続上のすべてのステートメントのアクセス プランを削除する可能性があります。 詳細については、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)のSQL_CURSOR_COMMIT_BEHAVIORおよびSQL_CURSOR_ROLLBACK_BEHAVIOR情報の種類、および[カーソルおよび準備されたステートメントに対するトランザクションの影響](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)を参照してください。  
  
## <a name="code-example"></a>コード例  
 「SQL[バインド パラメーター](../../../odbc/reference/syntax/sqlbindparameter-function.md) [、SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)、および[SQL セットポス](../../../odbc/reference/syntax/sqlsetpos-function.md)」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ステートメント ハンドルの割り当て|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|バッファーをパラメーターにバインドする|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|コミットまたはロールバック操作の実行|[SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|SQL ステートメントの実行|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|ステートメントの影響を受ける行数を返す|[SQLRowCount 関数](../../../odbc/reference/syntax/sqlrowcount-function.md)|  
|カーソル名の設定|[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
