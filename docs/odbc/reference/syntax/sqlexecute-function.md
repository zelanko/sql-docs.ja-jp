---
title: "SQLExecute 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLExecute
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLExecute
helpviewer_keywords:
- SQLExecute function [ODBC]
ms.assetid: 9286a01d-cde2-4b90-af94-9fd7f8da48bf
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e81f813f00513add62298c5f7ebb2d0dd3e85a50
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlexecute-function"></a>SQLExecute 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLExecute**ステートメントですべてのパラメーター マーカーが存在しない場合は、パラメーター マーカー変数の現在の値を使用して、準備されたステートメントを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLExecute(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NEED_DATA、SQL_STILL_EXECUTING、SQL_ERROR、SQL_NO_DATA、SQL_INVALID_HANDLE、または SQL_PARAM_DATA_AVAILABLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLExecute** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる**SQLGetDiagRec**で、 *HandleType*のSQL_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLExecute**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01001|カーソル操作の競合|準備済みステートメントに関連付けられている、 *StatementHandle*包含の位置指定更新または delete ステートメント、および行の存在しないか、複数の行が更新または削除します。 (複数の行の更新に関する詳細については、SQL_ATTR_SIMULATE_CURSOR の説明を参照してください*属性*で**SQLSetStmtAttr**。)。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01003|NULL 値は set 関数で削除されました|準備済みステートメントに関連付けられている*StatementHandle* set 関数に含まれる (など**AVG**、 **MAX**、 **MIN**など) は対象外**カウント**関数、および関数が適用される前に、値が除外された NULL 引数を設定します。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|文字列または出力パラメーターに対して返されるバイナリ データは、空白でない文字またはバイナリ データが NULL 以外の切り捨てが発生しました。 文字列値が、右側の切り捨てでした。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01006|権限が失効していません。|準備済みステートメントに関連付けられている、 *StatementHandle*が、**取り消す**指定された権限はステートメント、およびユーザーでがありませんでした。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01007|権限が与えられていません|準備済みステートメントに関連付けられている、 *StatementHandle*されました、 **GRANT**ステートメント、およびユーザーは許可されませんでした、指定した権限です。|  
|01S02|オプション値が変更されました|指定されたステートメント属性は、ような値が一時的に置き換えるための実装の動作条件のため無効でした。 (**SQLGetStmtAttr**一時的に置換された値の特定を呼び出すことができます)。代替値は有効、 *StatementHandle*カーソルが閉じられるまで、ステートメント属性はこの時点で、前の値に元に戻します。 変更可能なステートメント属性は、: SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE、SQL_ATTR_KEYSET_SIZE、SQL_ATTR_MAX_LENGTH、SQL_ATTR_MAX_ROWS、SQL_ATTR_QUERY_TIMEOUT、および SQL_ATTR_SIMULATE_CURSOR です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S07|小数部の切り捨て|入力/出力のデータが返される、または出力パラメーターが数値データ型の小数部が切り捨てられたか、時刻、タイムスタンプ、または期間のデータ型の時刻部分の小数部が切り捨てられましたになるように切り詰められました。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07002|COUNT フィールドが正しくありません。|指定されたパラメーターの数**SQLBindParameter**に含まれる SQL ステートメントのパラメーターの数より少なくなった\* *StatementText*です。<br /><br /> **SQLBindParameter**で呼び出されました*ParameterValuePtr*を null ポインターでは、設定*StrLen_or_IndPtr* SQL_NULL_DATA または SQL_DATA_AT_EXEC に設定されていないと*InputOutputType*に設定されていない SQL_PARAM_OUTPUT、パラメーターの数で指定できるように**SQLBindParameter**に含まれる SQL ステートメントのパラメーターの数よりも大きかった **StatementText*です。|  
|07006|制限付きのデータ型の属性違反|識別されるデータ値、 *ValueType*引数**SQLBindParameter**で識別されるデータ型にバインドされたパラメーターを変換できませんでしたの*ParameterType*引数**SQLBindParameter**です。<br /><br /> SQL_PARAM_INPUT_OUTPUT または SQL_PARAM_OUTPUT で識別されるデータ型に変換できませんとしてバインドされたパラメーターのデータ値が返されます、 *ValueType*引数**SQLBindParameter**です。<br /><br /> (1 つまたは複数の行のデータ値を変換できませんでしたが、1 つまたは複数の行が正常に返される、この関数 sql_success_with_info が返されます。)|  
|07007|制限付きのパラメーターの値違反|パラメーターの型 SQL_PARAM_INPUT_OUTPUT_STREAM は部分にデータを送受信するパラメーターのみ使用されます。 このパラメーターの型には、入力バインドされたバッファーすることはできません。<br /><br /> このエラーは、パラメーターの型は、SQL_PARAM_INPUT_OUTPUT とき、および、 \* *StrLen_or_IndPtr*で指定された**SQLBindParameter**が SQL_NULL_DATA、SQL_DEFAULT_ と等しくないです。PARAM、SQL_LEN_DATA_AT_EXEC(len)、または SQL_DATA_AT_EXEC です。|  
|07S01|既定のパラメーターの使い方が正しくありません。|パラメーターの値の設定と**SQLBindParameter**SQL_DEFAULT_PARAM が、および対応するパラメーターが、ODBC 標準的なプロシージャ呼び出しのパラメーターです。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|21S02|派生テーブルの次数が列の一覧と一致しません|準備済みステートメントに関連付けられている、 *StatementHandle*に含まれる、 **CREATE VIEW**ステートメント、および修飾されていない列の一覧 (ビューで、指定された列の数、 *列識別子*SQL ステートメントの引数) で定義されている派生テーブルの列数よりも多くの名が含まれている、*クエリ仕様*SQL ステートメントの引数。|  
|22001|文字列データの右側が切り捨てられました|文字またはバイナリ列に値の割り当ては、空白 (文字) または null (バイナリ) の文字またはバイトの切り捨てが発生しました。|  
|22002|インジケーター変数が必要ですが、指定されていません|NULL のデータが出力パラメーターにバインドされましたが*StrLen_or_IndPtr*によって設定**SQLBindParameter**が null ポインターでした。|  
|22003|数値が範囲|準備済みステートメントに関連付けられている、 *StatementHandle*パラメーターの値は、切り詰められる数値を関連付けられているに割り当てられているのではなく小数部) 全体の一部を原因し、なった、数値パラメーターのバインドに含まれるテーブルの列です。<br /><br /> 1 つまたは複数の入力/出力パラメーターまたは出力パラメーターの (数値または文字列) としての数値の値を返す原因となる (ではなく小数部) 整数部分が切り捨てられる数値。|  
|22007|無効な datetime 形式|準備済みステートメントに関連付けられている、 *StatementHandle*日付、時刻、または、バインド パラメーターとしてのタイムスタンプの構造体に含まれる SQL ステートメントが含まれているし、パラメーターが、それぞれ、無効な日付、時刻、またはタイムスタンプです。<br /><br /> 入力/出力パラメーターと出力パラメーターは、日付、時刻、またはタイムスタンプ C 構造にバインドされていたし、返されるパラメーターの値が、それぞれに、無効な日付、時刻、またはタイムスタンプ。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|22008|Datetime フィールド オーバーフロー|準備済みステートメントに関連付けられている、 *StatementHandle*包含 datetime 式が、計算、結果、日付の場合、時刻、またはタイムスタンプ構造体が含まれている SQL ステートメントが無効でした。<br /><br /> Datetime 式が入力/出力の計算、または出力パラメーターの日付、時刻、または無効なタイムスタンプ C の構造体が発生しました。|  
|22012|0 による除算です。|準備済みステートメントに関連付けられている、 *StatementHandle* 0 による除算の原因となった算術式が含まれています。<br /><br /> 算術式の入力/出力の計算または 0 による除算では、出力パラメーターが発生しました。|  
|22015|間隔のフィールドがオーバーフローしました|*\*StatementText*正確な数値型または interval パラメーターが含まれている、間隔の SQL データ型に変換する場合に有効桁数の損失が発生しました。<br /><br /> *\*StatementText*フィールドが 1 つ以上の間隔のパラメーターが含まれていること、列の数値データ型に変換するときにない表現数値データ型。<br /><br /> *\*StatementText*間隔 SQL 型に割り当てられているパラメーターのデータが含まれているし、SQL 型の間隔で、C 型の値の形式がありませんでした。<br /><br /> 正確な numeric または有効桁数の損失の原因となった間隔 C 型への SQL 型の間隔が、入力/出力または出力パラメーターを割り当てます。<br /><br /> 間隔 C 構造体を入力/出力パラメーターと出力パラメーターが割り当てられると、間隔のデータ構造内のデータの表現はありませんでした。|  
|22018|キャストは無効な文字値|*\*StatementText* C 型が含まれているが、真数または概数の数値、datetime、または interval データ型以外の場合は列の SQL 型が文字データ型です。 と列の値がバインドされた C 型の有効なリテラルではありませんでした。<br /><br /> 入力/出力パラメーターと出力パラメーターが返されると、SQL 型が、真数または概数の数値、datetime、または、interval データ型です。C 型が SQL_C_CHAR です。列の値がバインドされた SQL 型の有効なリテラルではありませんでした。|  
|22019|無効なエスケープ文字|準備済みステートメントに関連付けられている*StatementHandle*に含まれる、**と同様に**() 述語が、**エスケープ**で、**場所**句、および続くエスケープ文字の長さ**エスケープ**を 1 に等しいでした。|  
|22025|無効なエスケープ シーケンス|準備済みステートメントに関連付けられている*StatementHandle*に含まれる"**など***パターン値***エスケープ***エスケープ文字*"で、**場所**句、およびパターン値のエスケープ文字を次の文字が「%」または「_」のいずれか。|  
|23000|整合性制約の違反|準備済みステートメントに関連付けられている、 *StatementHandle*パラメーターが含まれています。 パラメーターの値が関連付けられているテーブルの列に NOT NULL として定義されている列の NULL が、一意の値のみを含めるに制約されている列の重複する値が指定されてまたはその他の整合性制約の違反です。|  
|24000|カーソル状態が無効|カーソルが配置された、 *StatementHandle*によって**SQLFetch**または**SQLFetchScroll**です。 このエラーが返されます、ドライバー マネージャーによって**SQLFetch**または**SQLFetchScroll** 、SQL_NO_DATA が返されなかったと場合、ドライバーによって返される**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されました。<br /><br /> カーソルが開いて、 *StatementHandle*です。<br /><br /> 準備済みステートメントに関連付けられている、 *StatementHandle*位置指定更新が含まれているか、または結果セットの終了後に結果セットの開始前に配置された削除 statemen、-t およびカーソル。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックによりロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|42000|構文エラーまたはアクセス違反|ユーザーに関連付けられている、準備されたステートメントを実行する権限を持っていません、 *StatementHandle*です。|  
|44000|WITH CHECK OPTION 違反|準備済みステートメントに関連付けられている*StatementHandle*に含まれる、**挿入**表示されたテーブルに対して実行されるステートメントまたはを指定することによって作成された、表示されたテーブルから派生したテーブル**WITH CHECK OPTION**、そのような 1 つまたは複数の行が影響を受けました、**挿入**ステートメントできなくなります表示されたテーブル内に存在します。<br /><br /> 準備済みステートメントに関連付けられている、 *StatementHandle*に含まれる、**更新**表示されたテーブルに対して実行されるステートメントまたはを指定することによって作成された、表示されたテーブルから派生したテーブル**WITH CHECK OPTION**、そのような 1 つまたは複数の行が影響を受けました、**更新**ステートメントできなくなります表示されたテーブル内に存在します。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLExecute**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM)、 *StatementHandle*準備されていませんでした。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|パラメーターの値が設定**SQLBindParameter**が null ポインターの場合、およびパラメーターの長さの値が 0、SQL_NULL_DATA、SQL_DATA_AT_EXEC、SQL_DEFAULT_PARAM、SQL_LEN_DATA_AT_EXEC_OFFSET 以下です。<br /><br /> パラメーターの値の設定と**SQLBindParameter**が null ポインター以外の場合は、C データ型が、SQL_C_BINARY または SQL_C_CHAR; およびパラメーターの長さの値が 0 未満の値がでした SQL_NTS、SQL_NULL_DATA、SQL_DEFAULT_PARAM、または SQL_DATA_AT_EXEC、SQL_LEN_DATA_AT_EXEC_OFFSET 以下です。<br /><br /> パラメーターの長さの値がによってバインドされる**SQLBindParameter** SQL_DATA_AT_EXEC に設定された以外の場合は、SQL 型が SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長い形式のデータ ソース固有のデータ型以外および SQL_NEED_LONG_DATA_LEN 情報入力**SQLGetInfo** "Y"がします。|  
|HY105|無効なパラメーターの型|引数が指定された値*InputOutputType*で**SQLBindParameter** SQL_PARAM_OUTPUT、パラメーターが入力パラメーターをでした。|  
|HY109|無効なカーソルの位置|準備されたステートメントが位置指定の update または delete ステートメントと、カーソルが置かれている (によって**SQLSetPos**または**SQLFetchScroll**) の行が削除されたか、取得できませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースによっては、SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE ステートメント属性の現在の設定の組み合わせはサポートされていません。<br /><br /> SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されており、SQL_ATTR_CURSOR_TYPE ステートメント属性は、ドライバーがブックマークにできないカーソルの種類に設定されました。|  
|HYT00|タイムアウトが発生しました|クエリのタイムアウト時間は、データ ソースには、結果セットが返される前に期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtAttr**、SQL_ATTR_QUERY_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
 **SQLExecute**によって返される任意の SQLSTATE を返すことができる**SQLPrepare**に基づいてデータ ソースが、ステートメントに関連付けられている SQL ステートメントを評価するときに、します。  
  
## <a name="comments"></a>コメント  
 **SQLExecute**によって準備されたステートメントが実行された**SQLPrepare**です。 アプリケーションで処理するかへの呼び出しの結果を破棄した後**SQLExecute**、アプリケーションが呼び出すことができます**SQLExecute**新しいパラメーター値を指定しています。 準備実行の詳細については、次を参照してください。[準備された実行](../../../odbc/reference/develop-app/prepared-execution-odbc.md)です。  
  
 実行する、**選択**ステートメントが複数回、アプリケーションを呼び出す必要があります**SQLCloseCursor**の前に、**選択**ステートメントです。  
  
 データ ソースが (明示的なトランザクションの開始に使用が必要) 手動コミット モードでは、トランザクションは既に開始されていない場合は、ドライバーは、SQL ステートメントを送信する前に、トランザクションを開始します。 詳細については、次を参照してください。[トランザクション](../../../odbc/reference/develop-app/transactions-odbc.md)です。  
  
 アプリケーションで使用する場合**SQLPrepare**を準備および**SQLExecute**を送信する、**コミット**または**ロールバック**ステートメントでは、ことはできませんDBMS の製品間で相互運用可能です。 コミットまたはロールバック、トランザクション、呼び出す**SQLEndTran**です。  
  
 場合**SQLExecute**実行時データ パラメーターが見つかった SQL_NEED_DATA が返されます。 アプリケーションを使用して、データは送信**SQLParamData**と**SQLPutData**です。 参照してください[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)、 [SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)、 [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)、および[長い形式のデータを送信する](../../../odbc/reference/develop-app/sending-long-data.md)です。  
  
 場合**SQLExecute**検索更新、挿入、またはデータ ソースへの呼び出しですべての行は影響しない delete ステートメントを実行**SQLExecute** SQL_NO_DATA が返されます。  
  
 SQL_ATTR_PARAMSET_SIZE ステートメント属性の値が 1 より大きいと、SQL ステートメントには、少なくとも 1 つのパラメーター マーカーが含まれています**SQLExecute** 、配列内のパラメーター値のセットごとに、SQL ステートメントを実行。によって示される、  *\*ParameterValuePtr*への呼び出しで引数**SQLBindParameter**です。 詳細については、次を参照してください。[パラメーター値の配列](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)です。  
  
 ブックマークが有効になっており、クエリが実行される場合は、ブックマークをサポートすることはできません、属性値を変更し、SQLSTATE 01S02 を返すことでブックマークをサポートしている環境を強制するべきでは、ドライバー (オプションの値が変更されました)。 属性は変更できない場合、ドライバーは SQLSTATE HY024 を返す必要があります (無効な属性値)。  
  
> [!NOTE]  
>  アプリケーションがなど、データベースまたはデータベースのコンテキストを変更する SQL ステートメントを実行する必要がありますされません接続プールを使用する場合、**使用***データベース*を変更する SQL Server 内のステートメントデータ ソースによって使用されるカタログ。  
  
## <a name="code-example"></a>コード例  
 参照してください[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)、 [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)、 [SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)、および[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|カーソルを閉じる|[SQLCloseCursor 関数](../../../odbc/reference/syntax/sqlclosecursor-function.md)|  
|コミットまたはロールバック操作を実行します。|[SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|複数行のデータのフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|ステートメント ハンドルを解放します。|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|カーソル名を返す|[SQLGetCursorName 関数](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|  
|データの列の一部またはすべてのフェッチ|[SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|データを送信する次のパラメーターを返す|[SQLParamData 関数](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|実行のためのステートメントを準備します。|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|実行時にパラメーターのデータを送信します。|[SQLPutData 関数](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|カーソル名の設定|[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

