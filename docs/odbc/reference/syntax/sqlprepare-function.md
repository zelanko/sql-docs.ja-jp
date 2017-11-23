---
title: "SQLPrepare 関数 |Microsoft ドキュメント"
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
apiname: SQLPrepare
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLPrepare
helpviewer_keywords: SQLPrepare function [ODBC]
ms.assetid: 332e1b4b-b0ed-4e7a-aa4d-4f35f4f4476b
caps.latest.revision: "23"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d46a8b14663b03e05f6791468e1a5687375b8ac1
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlprepare-function"></a>SQLPrepare 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLPrepare**の実行、SQL 文字列を準備します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLPrepare(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     StatementText,  
     SQLINTEGER    TextLength);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *StatementText*  
 [入力]SQL のテキスト文字列です。  
  
 *TextLength*  
 [入力]長さ **StatementText*文字です。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLPrepare** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLPrepare**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S02|オプション値が変更されました|指定されたステートメント属性は、ような値が一時的に置き換えるための実装の動作条件のため無効でした。 (**SQLGetStmtAttr**一時的に置換された値の特定を呼び出すことができます)。代替値は有効、 *StatementHandle*カーソルが閉じられるまでです。 変更可能なステートメント属性は、: SQL_ATTR_CONCURRENCY SQL_ATTR_CURSOR_TYPE SQL_ATTR_KEYSET_SIZE SQL_ATTR_MAX_LENGTH SQL_ATTR_MAX_ROWS SQL_ATTR_QUERY_TIMEOUT SQL_ATTR_SIMULATE_CURSOR<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|21S01|挿入値のリストが列の一覧と一致しません|\**StatementText*に含まれる、**挿入**ステートメント、および挿入する値の数と一致しませんでした、派生テーブルの次数。|  
|21S02|派生テーブルの次数が列の一覧と一致しません|\**StatementText*に含まれる、 **CREATE VIEW**ステートメント、および指定した名前の数は、クエリの仕様で定義されている派生テーブルと同じレベルではありません。|  
|22018|キャストは無効な文字値|**StatementText*リテラルまたはパラメーターが含まれる SQL ステートメントが含まれているし、値が関連付けられているテーブル列のデータ型と互換性がありません。|  
|22019|無効なエスケープ文字|引数*StatementText*に含まれる、**など**() 述語が、**エスケープ**で、**場所**句とエスケープの長さ続く文字**エスケープ**を 1 に等しいでした。|  
|22025|無効なエスケープ シーケンス|引数*StatementText*に含まれる"**など***パターン値***エスケープ***エスケープ文字*"で、**場所**句、およびパターン値のエスケープ文字を次の文字が「%」でも「_」。|  
|24000|カーソル状態が無効|(DM)、カーソルが開いて、 *StatementHandle*、および**SQLFetch**または**SQLFetchScroll**が呼び出されました。<br /><br /> カーソルが開いて、 *StatementHandle*が**SQLFetch**または**SQLFetchScroll**が呼び出されていません。|  
|34000|カーソル名が無効|\**StatementText*位置指定に含まれる**削除**または位置指定**更新**、し、準備されているステートメントによって参照されたカーソルが開いていませんでした。|  
|3D000|無効なカタログ名|指定されたカタログ名*StatementText*が無効です。|  
|3F000|無効なスキーマ名|指定されたスキーマ名*StatementText*が無効です。|  
|42000|構文エラーまたはアクセス違反|\**StatementText*準備可能ながないか、構文エラーが含まれている SQL ステートメントが含まれています。<br /><br /> **StatementText*ユーザーが必要な特権をいないステートメントが含まれています。|  
|42S01|ベース テーブルまたはビューが既に存在します。|\**StatementText*に含まれる、 **CREATE TABLE**または**CREATE VIEW**ステートメントでは、テーブル名やビューの指定名は既に存在します。|  
|42S02|ベース テーブルまたはビューが見つかりません|\**StatementText*に含まれる、 **DROP TABLE**または**DROP VIEW**ステートメント、および指定したテーブル名またはビュー名がありませんでした。<br /><br /> \**StatementText*に含まれる、 **ALTER TABLE**ステートメントと指定したテーブル名は存在しませんでした。<br /><br /> \**StatementText*に含まれる、 **CREATE VIEW**ステートメント、およびテーブル名またはビューのクエリの仕様で定義されている名前がありませんでした。<br /><br /> \**StatementText*に含まれる、 **CREATE INDEX**ステートメントと指定したテーブル名は存在しませんでした。<br /><br /> \**StatementText*に含まれる、 **GRANT**または**取り消す**ステートメント、および指定したテーブル名またはビュー名がありませんでした。<br /><br /> \**StatementText*に含まれる、**選択**ステートメント、および指定したテーブル名またはビュー名がありませんでした。<br /><br /> \**StatementText*に含まれる、**削除**、**挿入**、または**更新**ステートメントと指定したテーブル名は存在しませんでした。<br /><br /> \**StatementText*に含まれる、 **CREATE TABLE**ステートメント、および制約 (テーブルを参照する以外の 1 つ作成される) で指定されたテーブルは提供されません。|  
|42S11|インデックスが既に存在します。|\**StatementText*に含まれる、 **CREATE INDEX**ステートメント、および指定したインデックス名が既に存在します。|  
|42S12|インデックスが見つかりません|\**StatementText*に含まれる、 **DROP INDEX**ステートメントと指定したインデックス名は存在しませんでした。|  
|42S21|列が既に存在します。|\**StatementText*に含まれる、 **ALTER TABLE**ステートメントとで指定された列、**追加**句が一意でないか、ベース テーブルの既存の列を識別します。|  
|42S22|列が見つかりません。|\**StatementText*に含まれる、 **CREATE INDEX**ステートメント、および 1 つ以上の列リストで指定した名前が存在しない列です。<br /><br /> \**StatementText*に含まれる、 **GRANT**または**取り消す**ステートメントと指定された列名は存在しませんでした。<br /><br /> \**StatementText*に含まれる、**選択**、**削除**、**挿入**、または**更新**ステートメント、および指定された列名前は存在しません。<br /><br /> \**StatementText*に含まれる、 **CREATE TABLE**ステートメント、および制約 (テーブルを参照する以外の 1 つ作成される) で指定された列は提供されません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*関数が呼び出されたし、再度、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY009|無効な null ポインターの使用|(DM) *StatementText*が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLPrepare**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) 引数*TextLength*がより小さいか等しい 0 は SQL_NTS に等しくないです。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|同時実行の設定は、定義されたカーソルの種類に対して無効でした。<br /><br /> SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されており、SQL_ATTR_CURSOR_TYPE ステートメント属性は、ドライバーがブックマークにできないカーソルの種類に設定されました。|  
|HYT00|タイムアウトが発生しました|データ ソースには、結果セットが返される前に、タイムアウト期間が期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtAttr**、SQL_ATTR_QUERY_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 アプリケーションの呼び出し**SQLPrepare**準備のため、データ ソースに SQL ステートメントを送信します。 準備実行の詳細については、次を参照してください。[準備された実行](../../../odbc/reference/develop-app/prepared-execution-odbc.md)です。 アプリケーションは、SQL ステートメントで 1 つまたは複数のパラメーター マーカーを含めることができます。 パラメーター マーカーを含めるには、アプリケーションは、適切な位置にある SQL 文字列に疑問符 (?) を埋め込みます。 パラメーターについては、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)です。  
  
> [!NOTE]  
>  アプリケーションで使用する場合**SQLPrepare**を準備および**SQLExecute**を送信する、**コミット**または**ロールバック**ステートメントでは、ことはできませんDBMS の製品間で相互運用可能です。 コミットまたはロールバック、トランザクション、呼び出す**SQLEndTran**です。  
  
 ドライバーは、データ ソースで使用される SQL の形式を使用して、準備のため、データ ソースに送信するステートメントを変更できます。 具体的には、ドライバーは、特定の機能の SQL 構文を定義するために使用するエスケープ シーケンスを変更します。 (SQL ステートメントの文法の説明は、次を参照してください[odbc エスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)と[付録 c: SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)。)。ドライバーは、ステートメント ハンドルは埋め込み SQL コードにステートメントの識別子に似ています。 データ ソースは、ステートメントの識別子をサポートする場合、ドライバーは、データ ソースにステートメントの識別子とパラメーターの値を送信できます。  
  
 ステートメントを準備すると、アプリケーションは、ステートメント ハンドルを使用して、後の関数呼び出しでステートメントを参照してください。 呼び出して、ステートメント ハンドルに関連付けられている、準備されたステートメントを再実行することができます**SQLExecute**アプリケーションへの呼び出しでステートメントをによって解放されるまで**SQLFreeStmt** SQL_DROP オプションを使用して、または呼び出しでは、ステートメント ハンドルで使用されるまで**SQLPrepare**、 **SQLExecDirect**、または、カタログ関数の 1 つ (**SQLColumns**、 **SQLTables**など)。 アプリケーションは、ステートメントを準備した後、結果セットの形式に関する情報を要求できます。 実装によって呼び出す**SQLDescribeCol**または**SQLDescribeParam**後**SQLPrepare**ほど効率的で後に、関数を呼び出すことができない可能性があります**SQLExecute**または**SQLExecDirect**です。  
  
 いくつかのドライバーが構文エラーが返されることはできませんまたはアプリケーションを呼び出すと、アクセス違反**SQLPrepare**です。 ドライバーは、構文エラーを処理し、アクセス違反、のみ、構文エラーまたは構文エラーでもアクセス違反が発生します。 そのため、アプリケーションがあります関数など、関連する後続の呼び出し時に、これらの条件を処理する**SQLNumResultCols**、 **SQLDescribeCol**、 **SQLColAttribute**、および**SQLExecute**です。  
  
 データ ソースのドライバーの機能、に応じて (すべてのパラメーターがバインドされている) 場合、ステートメントが準備されたときに、パラメーター情報 (などのデータ型) をチェックする可能性がありますかで実行されるとき (すべてのパラメーターがバインドされていない) 場合。 相互運用性を最大にするため、アプリケーションは、同じステートメントで新しい SQL ステートメントを準備する前に古い SQL ステートメントに適用されるすべてのパラメーターをバインド解除する必要があります。 これは、新しいステートメントに適用されるパラメーターの情報が古いため、エラーを防ぎます。  
  
> [!IMPORTANT]  
>  いずれかを明示的に呼び出して、トランザクションをコミットする**SQLEndTran**で自動コミット モードで作業している可能性があります、アクセス ステートメントのプランをすべてが接続を削除するデータ ソースまたはします。 詳細についてで SQL_CURSOR_COMMIT_BEHAVIOR と SQL_CURSOR_ROLLBACK_BEHAVIOR 情報の種類を参照してください。 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)と[カーソルおよび準備されたステートメントでトランザクションの効果](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)です。  
  
## <a name="code-example"></a>コード例  
 参照してください[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)、 [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)、および[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ステートメント ハンドルの割り当てください。|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|パラメーターへのバッファーのバインド|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|コミットまたはロールバック操作を実行します。|[SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|ステートメントによって影響を受ける行の数を返す|[SQLRowCount 関数](../../../odbc/reference/syntax/sqlrowcount-function.md)|  
|カーソル名の設定|[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
