---
title: SQLBulkOperations 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLBulkOperations
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLBulkOperations
helpviewer_keywords:
- SQLBulkOperations function [ODBC]
ms.assetid: 7029d0da-b0f2-44e6-9114-50bd96f47196
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3f0e2dd99a350d3bb1bfb17d6d9ccdba46f9473e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlbulkoperations-function"></a>SQLBulkOperations 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ODBC。  
  
 **概要**  
 **SQLBulkOperations**一括挿入や一括ブックマークを実行する操作 (更新プログラムを含む) は、削除、およびブックマークでフェッチします。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLBulkOperations(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Operation);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *操作*  
 [入力]操作を実行します。  
  
 SQL_ADD SQL_UPDATE_BY_BOOKMARK SQL_DELETE_BY_BOOKMARK SQL_FETCH_BY_BOOKMARK  
  
 詳細については、「コメント」を参照してください。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NEED_DATA、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLBulkOperations** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType*のSQL_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLBulkOperations**ですこの関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
 すべてこれら SQLSTATEs SQL_SUCCESS_WITH_INFO または SQL_ERROR (を除く 01xxx SQLSTATEs) を返すことができる、SQL_SUCCESS_WITH_INFO が返されますでエラーが発生した場合は、SQL_ERROR が返されます複数行の操作の 1 つまたは複数の、は、すべての行にエラーが発生した場合、。単一行の操作です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データの右側が切り捨てられました|*操作*引数が SQL_FETCH_BY_BOOKMARK、および文字列または 1 つ以上の SQL_C_CHAR または SQL_C_BINARY データ型を持つ列に返されるバイナリ データが空白でない文字またはバイナリ データが NULL 以外の切り捨てが発生しました。|  
|01S01|行のエラー|*操作*引数 SQL_ADD で、操作を実行しているときに 1 つまたは複数の行でエラーが発生しましたが、少なくとも 1 つの行が正常に追加します。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。<br /><br /> (このエラーは、アプリケーションは、ODBC 2 と連携して場合にのみ発生します。*x*ドライバーです)。|  
|01S07|小数部の切り捨て|*操作*引数が SQL_FETCH_BY_BOOKMARK、アプリケーション バッファーのデータ型が SQL_C_CHAR または SQL_C_BINARY、および 1 つまたは複数の列のバッファーをアプリケーションに返されるデータが切り捨てられました。 (数値の C データ型の数値の小数部が切り捨てられました。 時刻、タイムスタンプ、および時刻部分を含む interval C データ型の場合は、時間の小数部が切り捨てられました。)<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|*操作*引数 SQL_FETCH_BY_BOOKMARK、れ、結果セット内の列のデータ値がで指定されたデータ型に変換できませんでした、 *TargetType* への呼び出しで引数**SQLBindCol**です。<br /><br /> *操作*引数が SQL_UPDATE_BY_BOOKMARK または SQL_ADD、およびアプリケーションのバッファーのデータ値を結果セット内の列のデータ型に変換できませんでした。|  
|07009|無効な記述子のインデックス|引数*操作*SQL_ADD の列が結果セット内の列数よりも大きい列番号を持つバインドされました。|  
|21S02|派生テーブルの次数が列の一覧と一致しません|引数*操作*SQL_UPDATE_BY_BOOKMARK; が、列がありませんでした更新可能なすべての列がバインドされていないか読み取り専用、またはバインドされている長さ/インジケーター バッファー内の値が SQL_COLUMN_IGNORE のためです。|  
|22001|文字列データの右側が切り捨てられました|文字またはバイナリ列に値を結果セット内の割り当て (文字) の空白または null でない (バイナリ) の文字またはバイトの切り捨てが発生しました。|  
|22003|数値が範囲|*操作*引数が SQL_ADD または SQL_UPDATE_BY_BOOKMARK、され、結果セット内の列に数値の値の代入と、切り捨てられるように数値のではなく小数部) 全体の一部です。<br /><br /> 引数*操作*SQL_FETCH_BY_BOOKMARK、1 つまたは複数のバインドされた列の数値の値を返す原因となる有効桁数の損失、します。|  
|22007|無効な datetime 形式|*操作*引数が SQL_ADD または SQL_UPDATE_BY_BOOKMARK、され、結果セット内の列に日付またはタイムスタンプの値の代入と、年、月、または範囲外である日フィールドです。<br /><br /> 引数*操作*SQL_FETCH_BY_BOOKMARK、1 つまたは複数のバインドされた列の日付またはタイムスタンプの値を返す原因となる年、月、または範囲外である日フィールド、します。|  
|22008|日付/時刻フィールドがオーバーフローしました|*操作*引数が SQL_ADD または SQL_UPDATE_BY_BOOKMARK、および datetime フィールド (年、月、日、時間、分、または秒の datetime の結果セット内の列に送信されるデータに算術演算のパフォーマンスが発生しましたフィールド値の許容範囲外のフィールドまたはが無効 datetimes のグレゴリオ暦カレンダーの自然規則に基づいて、結果の)。<br /><br /> *操作*引数が SQL_FETCH_BY_BOOKMARK、および datetime の結果セットから取得されるデータに算術演算のパフォーマンスの結果、datetime フィールド (年、月、日、時間、分、または 2 番目のフィールド) の結果フィールドの値の許容範囲外解消発生しているかどうかが無効では、datetimes のグレゴリオ暦カレンダーの自然規則に基づいています。|  
|22015|間隔のフィールドがオーバーフローしました|*操作*引数が SQL_ADD または SQL_UPDATE_BY_BOOKMARK、され、正確な numeric の割り当てまたは C 間隔の種類を間隔 SQL データ型に有効桁数の損失です。<br /><br /> *操作*引数 SQL_ADD または SQL_UPDATE_BY_BOOKMARK では、間隔の SQL 型の C 型の値の形式がなかった間隔 SQL 型に割り当てる際、します。<br /><br /> *操作*引数が SQL_FETCH_BY_BOOKMARK、され、真数型または interval SQL 型から C の間隔の種類に割り当てる有効桁数が失われる先頭のフィールドにします。<br /><br /> *操作*引数 SQL_FETCH_BY_BOOKMARK は C の間隔の種類での SQL 型の値の形式がなかった間隔 C 型に割り当てる際、します。|  
|22018|キャストは無効な文字値|*操作*引数 SQL_FETCH_BY_BOOKMARK 以外の場合は C 型が、真数または概数の数値、datetime、または interval データ型以外の場合は、列の SQL 型が文字データ型は、列の値が、無効バインドされた C 型のリテラルです。<br /><br /> 引数*操作*SQL_ADD または SQL_UPDATE_BY_BOOKMARK 以外の場合は SQL 型が、真数または概数の数値、datetime、または interval データ型以外の場合は、C 型 SQL_C_CHAR; れ、列の値が無効なリテラルのバインドされた SQL 型です。|  
|23000|整合性制約の違反|*操作*引数が SQL_ADD、SQL_DELETE_BY_BOOKMARK、または SQL_UPDATE_BY_BOOKMARK、および整合性制約の違反です。<br /><br /> *操作*引数は、SQL_ADD とが関連付けられていない列を NOT NULL を既定値を含まないとして定義します。<br /><br /> *操作*引数は、バインドで指定された長さである SQL_ADD *StrLen_or_IndPtr*バッファーが SQL_COLUMN_IGNORE、および列が、既定値はありませんでした。|  
|24000|カーソル状態が無効|*StatementHandle*が実行された状態でしたが、結果セットが関連付けられていない、 *StatementHandle*です。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックが原因ロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|42000|構文エラーまたはアクセス違反|ドライバーで要求された操作の実行に必要に応じて、行をロックできなかった、*操作*引数。|  
|44000|WITH CHECK OPTION 違反|*操作*引数が SQL_ADD または SQL_UPDATE_BY_BOOKMARK での挿入または更新が表示されたテーブルで実行された (またはテーブルが表示されていたテーブルから派生) を指定することによって作成された**WITH CHECK OPTION**、このような形で、挿入によって 1 つまたは複数の行が影響を受けるか、更新プログラムが表示されたテーブル内に存在しなくをすることです。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLBulkOperations**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM)、指定した*StatementHandle*実行された状態ではありませんでした。 最初の呼び出さずに、関数が呼び出された**SQLExecDirect**、 **SQLExecute**、またはカタログ関数。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) ドライバーは ODBC 2、でした。*x*ドライバー、および**SQLBulkOperations**で呼び出され、 *StatementHandle*する前に**SQLFetchScroll**または**SQLFetch**が呼び出されました。<br /><br /> (DM) **SQLBulkOperations**後に呼び出された**SQLExtendedFetch**で呼び出されましたが、 *StatementHandle*です。|  
|HY011|属性を設定できません。|(DM) ドライバーは ODBC 2、でした。*x*ドライバー、および SQL_ATTR_ROW_STATUS_PTR ステートメント属性は、呼び出しの間で設定された**SQLFetch**または**SQLFetchScroll**と**SQLBulkOperations**.|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|*操作*引数されました SQL_ADD または SQL_UPDATE_BY_BOOKMARK 以外のデータ値が null ポインター以外の場合は、C データ型は SQL_C_BINARY または SQL_C_CHAR; 列の長さの値が 0 より小さいは SQL_DATA_AT_EXEC に等しくないです。、SQL_COLUMN_IGNORE、SQL_NTS、または SQL_NULL_DATA、SQL_LEN_DATA_AT_EXEC_OFFSET 以下です。<br /><br /> 長さ/インジケーター バッファー内の値が SQL_DATA_AT_EXEC です。SQL 型が SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長い形式のデータ ソース固有のデータ型です。SQL_NEED_LONG_DATA_LEN 情報の種類と**SQLGetInfo** "Y"がします。<br /><br /> *操作*引数が SQL_ADD、SQL_ATTR_USE_BOOKMARK ステートメント属性は SQL_UB_VARIABLE に設定され、列 0 の長さは、この結果セットのブックマークの最大の長さと等しいでしたバッファーにバインドされました。 (この長さは、IRD の SQL_DESC_OCTET_LENGTH フィールドで利用可能と呼び出すことによって取得できます**SQLDescribeCol**、 **SQLColAttribute**、または**SQLGetDescField**)。|  
|HY092|無効な属性の識別子|(DM) の指定された値、*操作*引数が無効です。<br /><br /> *操作*引数 SQL_ADD、SQL_UPDATE_BY_BOOKMARK、または SQL_DELETE_BY_BOOKMARK、また、ステートメント属性 SQL_ATTR_CONCURRENCY を SQL_CONCUR_READ_ONLY に設定されました。<br /><br /> *操作*引数が SQL_DELETE_BY_BOOKMARK、SQL_FETCH_BY_BOOKMARK、または SQL_UPDATE_BY_BOOKMARK、およびブックマーク列がバインドされていないまたは SQL_UB_OFF に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースがで要求された操作をサポートしていません、*操作*引数。|  
|HYT00|タイムアウトが発生しました|クエリのタイムアウト時間は、データ ソースには、結果セットが返される前に期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtAttr**で、*属性*SQL_ATTR_QUERY_TIMEOUT の引数。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
  
> [!CAUTION]  
>  どのようなステートメントの状態に関する情報の**SQLBulkOperations**呼び出すことができ、ODBC 2 と互換性のために行う必要があります*。x*アプリケーションを参照してください、[ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」セクション。  
  
 アプリケーションを使用して**SQLBulkOperations**ベース テーブルまたは現在のクエリに対応するビューの次の操作を実行します。  
  
-   新しい行を追加します。  
  
-   一連の各行がブックマークによって識別される行を更新します。  
  
-   一連の各行がブックマークによって識別される行を削除します。  
  
-   一連の各行がブックマークによって識別される行をフェッチします。  
  
 呼び出しの後に**SQLBulkOperations**、ブロック カーソルの位置が定義されていません。 アプリケーションが呼び出す、 **SQLFetchScroll**カーソルの位置を設定します。 アプリケーションを呼び出す必要があります**SQLFetchScroll**でのみ、 *FetchOrientation* SQL_FETCH_FIRST、SQL_FETCH_LAST、SQL_FETCH_ABSOLUTE、または SQL_FETCH_BOOKMARK の引数。 アプリケーションを呼び出す場合、カーソルの位置が定義されていない**SQLFetch**または**SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_PRIOR、SQL_FETCH_NEXT の引数またはSQL_FETCH_RELATIVE です。  
  
 呼び出しによって実行される一括操作で列を無視できます**SQLBulkOperations**への呼び出しで指定された列の長さ/インジケーター バッファーを設定して**SQLBindCol**SQL_COLUMN_IGNORE にします。  
  
 アプリケーションを呼び出すときに、SQL_ATTR_ROW_OPERATION_PTR ステートメント属性を設定する必要はありません**SQLBulkOperations**のため、この関数での一括操作の実行時に行を無視することはできません。  
  
 SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性が指すバッファーへの呼び出しによって影響を受ける行の数が含まれている**SQLBulkOperations**です。  
  
 ときに、*操作*はドライバーで定義されているかどうか、エラーの引数は、SQL_ADD または SQL_UPDATE_BY_BOOKMARK、カーソルに関連付けられているクエリ仕様の選択リストには、同じ列に複数の参照が含まれています。生成されるか、ドライバーが重複している参照を無視し、要求された操作を実行します。  
  
 使用する方法の詳細についての**SQLBulkOperations**を参照してください[SQLBulkOperations でのデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)です。  
  
## <a name="performing-bulk-inserts"></a>一括挿入の実行  
 使用してデータを挿入する**SQLBulkOperations**アプリケーションは、次の一連の手順を実行します。  
  
1.  結果セットを返すクエリを実行します。  
  
2.  SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を挿入する必要がある行の数に設定します。  
  
3.  呼び出し**SQLBindCol**を挿入する必要があるデータをバインドします。 データは、SQL_ATTR_ROW_ARRAY_SIZE の値が、サイズと等しい、配列にバインドされます。  
  
    > [!NOTE]  
    >  SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される配列のサイズは、SQL_ATTR_ROW_ARRAY_SIZE 等しいか、SQL_ATTR_ROW_STATUS_PTR null ポインターである必要がありますいずれかでなければなりません。  
  
4.  呼び出し**SQLBulkOperations**(*StatementHandle、* SQL_ADD) を挿入を実行します。  
  
5.  アプリケーションが、SQL_ATTR_ROW_STATUS_PTR ステートメント属性を設定すると、操作の結果を表示するには、この配列に調査することができます。  
  
 呼び出す前に 0 の列にバインドされた場合**SQLBulkOperations**で、*操作*SQL_ADD の引数は、ドライバーが更新されますバインドされた列 0 バッファーのブックマークの値、新しく。行を挿入します。 この場合、アプリケーションする必要がありますが、SQL_ATTR_USE_BOOKMARKS ステートメント属性を設定 SQL_UB_VARIABLE ステートメントを実行する前にします。 (は機能しない ODBC 2 です。*x*ドライバーです)。  
  
 長い形式のデータは、その SQLBulkOperations、によって呼び出し SQLParamData と SQLPutData を使用して部分に追加できます。 詳細については、この関数の参照の後で"を提供する時間がかかるデータの一括挿入および更新"を参照してください。  
  
 呼び出すアプリケーションの必要はありません**SQLFetch**または**SQLFetchScroll**を呼び出す前に**SQLBulkOperations** (ODBC 2 に対して予定の場合を除く*。x*ドライバー; 参照してください[旧バージョンとの互換性と標準の順守](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md))。  
  
 動作は、ドライバーの定義済み場合**SQLBulkOperations**で、*操作*SQL_ADD の引数が重複する列を含むカーソルで呼び出されます。 ドライバーは、ドライバー固有の SQLSTATE を返す、結果に表示される最初の列にデータの設定、またはその他のドライバーで定義された動作の実行を追加できます。  
  
## <a name="performing-bulk-updates-by-using-bookmarks"></a>ブックマークを使用した一括更新を実行します。  
 ブックマークを使用した一括更新を実行する**SQLBulkOperations**アプリケーションは、シーケンスの次の手順を実行します。  
  
1.  SQL_UB_VARIABLE を SQL_ATTR_USE_BOOKMARKS ステートメント属性を設定します。  
  
2.  結果セットを返すクエリを実行します。  
  
3.  SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を更新する行の数に設定します。  
  
4.  呼び出し**SQLBindCol**を更新するデータをバインドします。 データは、SQL_ATTR_ROW_ARRAY_SIZE の値が、サイズと等しい、配列にバインドされます。 呼び出しも**SQLBindCol**列 0 (ブックマーク列) にバインドします。  
  
5.  コピーを対象の配列への更新の行のブックマークは、列 0 にバインドされます。  
  
6.  バインドされたバッファー内のデータを更新します。  
  
    > [!NOTE]  
    >  SQL_ATTR_ROW_ARRAY_SIZE に一致するか、SQL_ATTR_ROW_STATUS_PTR null ポインターである必要があります、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される配列のサイズをする必要があります。  
  
7.  呼び出し**SQLBulkOperations**(*StatementHandle、* SQL_UPDATE_BY_BOOKMARK)。  
  
    > [!NOTE]  
    >  アプリケーションが、SQL_ATTR_ROW_STATUS_PTR ステートメント属性を設定すると、操作の結果を表示するには、この配列に調査することができます。  
  
8.  必要に応じて呼び出す**SQLBulkOperations**(*StatementHandle*SQL_FETCH_BY_BOOKMARK) データ更新が発生したことを確認する、バインドされたアプリケーション バッファーをフェッチします。  
  
9. データが更新された場合、ドライバーは SQL_ROW_UPDATED に適切な行の行の状態配列内の値を変更します。  
  
 によって実行される更新プログラムを一括**SQLBulkOperations**呼び出しを使用して、長い形式のデータを含めることができます**SQLParamData**と**SQLPutData**です。 詳細については、この関数の参照の後で"を提供する時間がかかるデータの一括挿入および更新"を参照してください。  
  
 カーソルの間でブックマークが解決しない場合、アプリケーションする必要はありません呼び出す**SQLFetch**または**SQLFetchScroll**ブックマークを更新する前にします。 以前のカーソルから保存されているブックマークを使用できます。 ブックマークは、カーソルの間で保持されない、アプリケーションは、呼び出す**SQLFetch**または**SQLFetchScroll**をそれらのブックマークを取得します。  
  
 動作は、ドライバーの定義済み場合**SQLBulkOperations**で、*操作*SQL_UPDATE_BY_BOOKMARK の引数が重複する列を含むカーソルで呼び出されます。 ドライバーでは、ドライバー固有の SQLSTATE を返す、結果セットに表示される最初の列を更新、またはその他のドライバーで定義された動作を実行できます。  
  
## <a name="performing-bulk-fetches-using-bookmarks"></a>ブックマークを使用してフェッチ一括を実行します。  
 ブックマークを使用して一括フェッチを実行する**SQLBulkOperations**アプリケーションは、シーケンスの次の手順を実行します。  
  
1.  SQL_UB_VARIABLE を SQL_ATTR_USE_BOOKMARKS ステートメント属性を設定します。  
  
2.  結果セットを返すクエリを実行します。  
  
3.  SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性をフェッチする必要がある行の数に設定します。  
  
4.  呼び出し**SQLBindCol**をフェッチする必要があるデータをバインドします。 データは、SQL_ATTR_ROW_ARRAY_SIZE の値が、サイズと等しい、配列にバインドされます。 呼び出しも**SQLBindCol**列 0 (ブックマーク列) にバインドします。  
  
5.  コピーを対象の配列へのフェッチの行のブックマークは、列 0 にバインドされます。 (これは前提アプリケーションが、それらのブックマークを個別に取得して既にいる。)  
  
    > [!NOTE]  
    >  SQL_ATTR_ROW_ARRAY_SIZE に一致するか、SQL_ATTR_ROW_STATUS_PTR null ポインターである必要があります、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される配列のサイズをする必要があります。  
  
6.  呼び出し**SQLBulkOperations**(*StatementHandle、* SQL_FETCH_BY_BOOKMARK)。  
  
7.  アプリケーションが、SQL_ATTR_ROW_STATUS_PTR ステートメント属性を設定すると、操作の結果を表示するには、この配列に調査することができます。  
  
 カーソルの間でブックマークが解決しない場合、アプリケーションする必要はありません呼び出す**SQLFetch**または**SQLFetchScroll**ブックマークによってフェッチする前にします。 以前のカーソルから保存されているブックマークを使用できます。 ブックマークは、カーソルの間で保持されない、アプリケーションは、呼び出す**SQLFetch**または**SQLFetchScroll**すると、それらのブックマークを取得します。  
  
## <a name="performing-bulk-deletes-using-bookmarks"></a>一括を実行するには、ブックマークの使用を削除します  
 ブックマークを使用して一括削除を実行する**SQLBulkOperations**アプリケーションは、シーケンスの次の手順を実行します。  
  
1.  SQL_UB_VARIABLE を SQL_ATTR_USE_BOOKMARKS ステートメント属性を設定します。  
  
2.  結果セットを返すクエリを実行します。  
  
3.  SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を削除する行の数に設定します。  
  
4.  呼び出し**SQLBindCol**列 0 (ブックマーク列) にバインドします。  
  
5.  コピーする、対象の配列を削除する行のブックマークは、列 0 にバインドされます。  
  
    > [!NOTE]  
    >  SQL_ATTR_ROW_ARRAY_SIZE に一致するか、SQL_ATTR_ROW_STATUS_PTR null ポインターである必要があります、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される配列のサイズをする必要があります。  
  
6.  呼び出し**SQLBulkOperations**(*StatementHandle、* SQL_DELETE_BY_BOOKMARK)。  
  
7.  アプリケーションが、SQL_ATTR_ROW_STATUS_PTR ステートメント属性を設定すると、操作の結果を表示するには、この配列に調査することができます。  
  
 呼び出すアプリケーションがない場合はブックマークは、カーソルの後も維持、 **SQLFetch**または**SQLFetchScroll**ブックマークを削除する前にします。 以前のカーソルから保存されているブックマークを使用できます。 ブックマークは、カーソルの間で保持されない、アプリケーションは、呼び出す**SQLFetch**または**SQLFetchScroll**すると、それらのブックマークを取得します。  
  
## <a name="providing-long-data-for-bulk-inserts-and-updates"></a>一括挿入と更新プログラムの長い形式のデータを提供します。  
 一括挿入と更新プログラムへの呼び出しによって実行される長い形式のデータを指定することができます**SQLBulkOperations**です。 挿入するか長いデータを更新するのには、アプリケーションは、「一括挿入を実行する」および「を実行する一括更新を使用してブックマーク」セクションでは、このトピックの前半で説明する手順に加えて、次の手順を実行します。  
  
1.  使用してデータをバインドに**SQLBindCol**、アプリケーション内の列番号などのアプリケーション定義の値の配置、  *\*TargetValuePtr*実行時データのバッファー列です。 値は、後で列を識別に使用できます。  
  
     アプリケーションが、SQL_LEN_DATA_AT_EXEC の結果を配置 (*長さ*) でマクロ、  *\*StrLen_or_IndPtr*バッファー。 列の SQL データ型は SQL_LONGVARBINARY、SQL_LONGVARCHAR、または長い形式のデータ ソース固有のデータ型と、ドライバーで SQL_NEED_LONG_DATA_LEN 情報の種類に"Y"が返されます場合**SQLGetInfo**、*長さ* ; パラメーターに送信されるデータのバイト数は、それ以外の場合は負でない値を指定しは無視されます。  
  
2.  ときに**SQLBulkOperations**実行時データ列、関数の戻り値 SQL_NEED_DATA およびに依存して手順 3 に進みますがある場合は、呼び出されます。 (実行時データ列が存在しない場合、プロセスが完了しました。)  
  
3.  アプリケーションの呼び出し**SQLParamData**のアドレスを取得する、  *\*TargetValuePtr*処理する最初の実行時データ列のバッファー。 **SQLParamData** SQL_NEED_DATA を返します。 アプリケーションからのアプリケーション定義の値を取得する、  *\*TargetValuePtr*バッファー。  
  
    > [!NOTE]  
    >  値がによって返される実行時データ パラメーターには、実行時データ列が似ています、 **SQLParamData**はごとに異なります。  
  
     実行時データ列は列のデータを送信する行セットで**SQLPutData**行が更新または挿入**SQLBulkOperations**です。 バインドされている**SQLBindCol**です。 によって返される値**SQLParamData**内の行のアドレスは、**TargetValuePtr*が処理されているバッファー。  
  
4.  アプリケーションの呼び出し**SQLPutData** 1 回以上の列のデータを送信します。 すべてのデータ値を返すことはできない場合、複数の呼び出しが必要、  *\*TargetValuePtr*で指定されたバッファー **SQLPutData**; を複数回呼び出す**SQLPutData**文字、バイナリ、またはデータ ソース固有のデータ型の列に文字データを送信するときにのみ、または列を文字、バイナリ、C のバイナリ データを送信するときに、同じ列が許可されるか、データ ソース固有のデータ型します。  
  
5.  アプリケーションの呼び出し**SQLParamData**列のすべてのデータが送信されたことを通知するには、もう一度です。  
  
    -   多くの実行時データ列がある場合**SQLParamData** SQL_NEED_DATA およびのアドレスを返します、 *TargetValuePtr*処理する次の実行時データ列のバッファー。 アプリケーションでは、手順 4. と 5. を繰り返します。  
  
    -   これ以上の実行時データ列がある場合、プロセスが完了しました。 ステートメントが正常に実行された場合**SQLParamData** SQL_SUCCESS または; SQL_SUCCESS_WITH_INFO が返されます場合は、実行に失敗しました、SQL_ERROR を返します。 この時点では、 **SQLParamData**によって返される任意の SQLSTATE を返すことができる**SQLBulkOperations**です。  
  
 操作が取り消されたかどうか、またはでエラーが発生**SQLParamData**または**SQLPutData**後**SQLBulkOperations** SQL_NEED_DATA を返しますのすべてのデータが送信される前にアプリケーションでのみ呼び出すことができます、実行時データ列**SQLCancel**、 **SQLGetDiagField**、 **SQLGetDiagRec**、 **SQLGetFunctions**、 **SQLParamData**、または**SQLPutData**ステートメントまたはステートメントに関連付けられた接続。 ステートメントまたはステートメントに関連付けられている接続の他の関数を呼び出すこと、関数を返します SQL_ERROR と SQLSTATE HY010 (関数のシーケンス エラーです)。  
  
 アプリケーションを呼び出す場合**SQLCancel**ドライバーでは、実行時データ列のデータが引き続き必要があります、中に、ドライバー操作をキャンセルします。 アプリケーションが呼び出すことができますし、 **SQLBulkOperations**再度を取り消すには影響しません、カーソルの状態または現在のカーソル位置。  
  
## <a name="row-status-array"></a>行の状態配列  
 行の状態配列が呼び出しの後に、行セット内のデータの行ごとの状態の値を含む**SQLBulkOperations**です。 ドライバーでは、この配列に状態の値を設定への呼び出し後**SQLFetch**、 **SQLFetchScroll**、 **SQLSetPos**、または**SQLBulkOperations**. この配列は、最初にへの呼び出しによって設定されます**SQLBulkOperations**場合**SQLFetch**または**SQLFetchScroll**が前に呼び出されていない**SQLBulkOperations。**. この配列は、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって参照されます。 行の状態配列内の要素の数は、(で定義されている、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性)、行セット内の行の数に等しくなければなりません。 この行の状態配列については、次を参照してください。 [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)です。  
  
## <a name="code-example"></a>コード例  
 次の例では、Customers テーブルから一度に 10 行のデータをフェッチします。 ユーザーにアクションを実行し、メッセージが表示されます。 ネットワーク トラフィックを減らすためは、例のバッファーは、更新、削除、し、バインドの配列では、過去の行セットのデータ オフセット位置にローカルに挿入します。 コードが適切にオフセット、バインドを設定しを呼び出す場合、ユーザーは、更新、削除、送信するによって選択され、データ ソースへの挿入、 **SQLBulkOperations**です。 わかりやすくするため、ユーザーは、10 個より多くの更新、削除、または挿入バッファーことはできません。  
  
```  
// SQLBulkOperations_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include "stdio.h"  
  
#define UPDATE_ROW 100  
#define DELETE_ROW 101  
#define ADD_ROW 102  
#define SEND_TO_DATA_SOURCE 103  
#define UPDATE_OFFSET 10  
#define INSERT_OFFSET 20  
#define DELETE_OFFSET 30  
  
// Define structure for customer data (assume 10 byte maximum bookmark size).  
typedef struct tagCustStruct {  
   SQLCHAR Bookmark[10];  
   SQLINTEGER BookmarkLen;  
   SQLUINTEGER CustomerID;  
   SQLINTEGER CustIDInd;  
   SQLCHAR CompanyName[51];  
   SQLINTEGER NameLenOrInd;  
   SQLCHAR Address[51];  
   SQLINTEGER AddressLenOrInd;  
   SQLCHAR Phone[11];  
   SQLINTEGER PhoneLenOrInd;  
} CustStruct;  
  
// Allocate 40 of these structures. Elements 0-9 are for the current rowset,  
// elements 10-19 are for the buffered updates, elements 20-29 are for  
// the buffered inserts, and elements 30-39 are for the buffered deletes.  
CustStruct CustArray[40];  
SQLUSMALLINT RowStatusArray[10], Action, RowNum, NumUpdates = 0, NumInserts = 0,  
NumDeletes = 0;  
SQLLEN BindOffset = 0;  
SQLRETURN retcode;  
SQLHENV henv = NULL;  
SQLHDBC hdbc = NULL;  
SQLHSTMT hstmt = NULL;  
  
int main() {  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
  
   // Set the following statement attributes:  
   // SQL_ATTR_CURSOR_TYPE:           Keyset-driven  
   // SQL_ATTR_ROW_BIND_TYPE:         Row-wise  
   // SQL_ATTR_ROW_ARRAY_SIZE:        10  
   // SQL_ATTR_USE_BOOKMARKS:         Use variable-length bookmarks  
   // SQL_ATTR_ROW_STATUS_PTR:        Points to RowStatusArray  
   // SQL_ATTR_ROW_BIND_OFFSET_PTR:   Points to BindOffset  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_KEYSET_DRIVEN, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER)sizeof(CustStruct), 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)10, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_USE_BOOKMARKS, (SQLPOINTER)SQL_UB_VARIABLE, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_STATUS_PTR, RowStatusArray, 0);  
   retcode = SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_BIND_OFFSET_PTR, &BindOffset, 0);  
  
   // Bind arrays to the bookmark, CustomerID, CompanyName, Address, and Phone columns.  
   retcode = SQLBindCol(hstmt, 0, SQL_C_VARBOOKMARK, CustArray[0].Bookmark, sizeof(CustArray[0].Bookmark), &CustArray[0].BookmarkLen);  
   retcode = SQLBindCol(hstmt, 1, SQL_C_ULONG, &CustArray[0].CustomerID, 0, &CustArray[0].CustIDInd);  
   retcode = SQLBindCol(hstmt, 2, SQL_C_CHAR, CustArray[0].CompanyName, sizeof(CustArray[0].CompanyName), &CustArray[0].NameLenOrInd);  
   retcode = SQLBindCol(hstmt, 3, SQL_C_CHAR, CustArray[0].Address, sizeof(CustArray[0].Address), &CustArray[0].AddressLenOrInd);  
   retcode = SQLBindCol(hstmt, 4, SQL_C_CHAR, CustArray[0].Phone, sizeof(CustArray[0].Phone), &CustArray[0].PhoneLenOrInd);  
  
   // Execute a statement to retrieve rows from the Customers table.  
   retcode = SQLExecDirect(hstmt, (SQLCHAR*)"SELECT CustomerID, CompanyName, Address, Phone FROM Customers", SQL_NTS);  
  
   // Fetch and display the first 10 rows.  
   retcode = SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
   // DisplayCustData(CustArray, 10);  
  
   // Call GetAction to get an action and a row number from the user.  
   // while (GetAction(&Action, &RowNum)) {  
   Action = SQL_FETCH_NEXT;  
   RowNum = 2;  
   switch (Action) {  
      case SQL_FETCH_NEXT:  
      case SQL_FETCH_PRIOR:  
      case SQL_FETCH_FIRST:  
      case SQL_FETCH_LAST:  
      case SQL_FETCH_ABSOLUTE:  
      case SQL_FETCH_RELATIVE:  
         // Fetch and display the requested data.  
         SQLFetchScroll(hstmt, Action, RowNum);  
         // DisplayCustData(CustArray, 10);  
         break;  
  
      case UPDATE_ROW:  
         // Check if we have reached the maximum number of buffered updates.  
         if (NumUpdates < 10) {  
            // Get the new customer data and place it in the next available element of  
            // the buffered updates section of CustArray, copy the bookmark of the row  
            // being updated to the same element, and increment the update counter.  
            // Checking to see we have not already buffered an update for this  
            // row not shown.  
            // GetNewCustData(CustArray, UPDATE_OFFSET + NumUpdates);  
            memcpy(CustArray[UPDATE_OFFSET + NumUpdates].Bookmark,  
               CustArray[RowNum - 1].Bookmark,  
               CustArray[RowNum - 1].BookmarkLen);  
            CustArray[UPDATE_OFFSET + NumUpdates].BookmarkLen =  
               CustArray[RowNum - 1].BookmarkLen;  
            NumUpdates++;  
         } else {  
            printf("Buffers full. Send buffered changes to the data source.");  
         }  
         break;  
      case DELETE_ROW:  
         // Check if we have reached the maximum number of buffered deletes.  
         if (NumDeletes < 10) {  
            // Copy the bookmark of the row being deleted to the next available element  
            // of the buffered deletes section of CustArray and increment the delete  
            // counter. Checking to see we have not already buffered an update for  
            // this row not shown.  
            memcpy(CustArray[DELETE_OFFSET + NumDeletes].Bookmark,  
               CustArray[RowNum - 1].Bookmark,  
               CustArray[RowNum - 1].BookmarkLen);  
  
            CustArray[DELETE_OFFSET + NumDeletes].BookmarkLen =  
               CustArray[RowNum - 1].BookmarkLen;  
  
            NumDeletes++;  
         } else  
            printf("Buffers full. Send buffered changes to the data source.");  
         break;  
  
      case ADD_ROW:  
         // reached maximum number of buffered inserts?  
         if (NumInserts < 10) {  
            // Get the new customer data and place it in the next available element of  
            // the buffered inserts section of CustArray and increment insert counter.  
            // GetNewCustData(CustArray, INSERT_OFFSET + NumInserts);  
            NumInserts++;  
         } else  
            printf("Buffers full. Send buffered changes to the data source.");  
         break;  
  
      case SEND_TO_DATA_SOURCE:  
         // If there are any buffered updates, inserts, or deletes, set the array size  
         // to that number, set the binding offset to use the data in the buffered  
         // update, insert, or delete part of CustArray, and call SQLBulkOperations to  
         // do the updates, inserts, or deletes. Because we will never have more than  
         // 10 updates, inserts, or deletes, we can use the same row status array.  
         if (NumUpdates) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumUpdates, 0);  
            BindOffset = UPDATE_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_UPDATE_BY_BOOKMARK);  
            NumUpdates = 0;  
         }  
  
         if (NumInserts) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumInserts, 0);  
            BindOffset = INSERT_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_ADD);  
            NumInserts = 0;  
         }  
  
         if (NumDeletes) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)NumDeletes, 0);  
            BindOffset = DELETE_OFFSET * sizeof(CustStruct);  
            SQLBulkOperations(hstmt, SQL_DELETE_BY_BOOKMARK);  
            NumDeletes = 0;  
         }  
  
         // If there were any updates, inserts, or deletes, reset the binding offset  
         // and array size to their original values.  
         if (NumUpdates || NumInserts || NumDeletes) {  
            SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)10, 0);  
            BindOffset = 0;  
         }  
         break;  
   }  
   // }  
  
   // Close the cursor.  
   SQLFreeStmt(hstmt, SQL_CLOSE);  
}  
```  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|記述子の 1 つのフィールドを取得します。|[SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|記述子の複数のフィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|記述子の 1 つのフィールドを設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|記述子の複数のフィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|カーソルを配置するか、行セット内のデータを更新する、更新、または行セット内のデータを削除します。|[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
