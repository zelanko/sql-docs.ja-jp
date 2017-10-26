---
title: "SQLSetPos 関数 |Microsoft ドキュメント"
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
- SQLSetPos
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetPos
helpviewer_keywords:
- SQLSetPos function [ODBC]
ms.assetid: 80190ee7-ae3b-45e5-92a9-693eb558f322
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6140625da489bcb573b3beb4ca2be0838805f8d5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetpos-function"></a>SQLSetPos 関数
**準拠**  
 バージョンが導入されています ODBC 1.0 標準への準拠: ODBC。  
  
 **概要**  
 **SQLSetPos**行セットのカーソル位置を設定し、により、アプリケーション、行セット内のデータを更新するか、結果セット内のデータ更新または削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLSetPos(  
      SQLHSTMT        StatementHandle,  
      SQLSETPOSIROW   RowNumber,  
      SQLUSMALLINT    Operation,  
      SQLUSMALLINT    LockType);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *RowNumber*  
 [入力]指定された操作を実行する対象の行セット内の行の位置、*操作*引数。 場合*RowNumber*が 0 の場合、操作は、行セット内のすべての行に適用されます。  
  
 詳細については、「コメント」を参照してください。  
  
 *操作*  
 [入力]操作を実行します。  
  
 SQL_POSITION SQL_REFRESH SQL_UPDATE SQL_DELETE  
  
> [!NOTE]  
>  値は、SQL_ADD、*操作*ODBC 3 の引数は廃止されて*.x*です。 ODBC 3 です。*x*ドライバーは下位互換性のため SQL_ADD をサポートする必要があります。 この機能がへの呼び出しによって置き換えられました**SQLBulkOperations**で、*操作*SQL_ADD のです。 ODBC 3 時にします。*x*アプリケーションが ODBC 2* 。x*ドライバー、ドライバー マネージャーは、マップの呼び出し**SQLBulkOperations**で、*操作*に SQL_ADD の**SQLSetPos**で、 *操作*SQL_ADD のです。  
  
 詳細については、「コメント」を参照してください。  
  
 *ロック。*  
 [入力]指定された操作を実行した後に行をロックする方法を指定、*操作*引数。  
  
 SQL_LOCK_NO_CHANGE SQL_LOCK_EXCLUSIVE SQL_LOCK_UNLOCK  
  
 詳細については、「コメント」を参照してください。  
  
 **返します。**  
  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NEED_DATA、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLSetPos** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得される可能性があります**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLSetPos**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
 すべてこれら SQLSTATEs SQL_SUCCESS_WITH_INFO または SQL_ERROR (を除く 01xxx SQLSTATEs) を返すことができる、SQL_SUCCESS_WITH_INFO が返されますでエラーが発生した場合は、SQL_ERROR が返されます複数行の操作の 1 つまたは複数の、は、すべての行にエラーが発生した場合、。単一行の操作です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01001|カーソル操作の競合|*操作*引数が SQL_DELETE または SQL_UPDATE、および行の存在しないか、複数の行が削除または更新します。 (複数の行の更新に関する詳細については、SQL_ATTR_SIMULATE_CURSOR の説明を参照してください*属性*で**SQLSetStmtAttr**。)。(関数は、SQL_SUCCESS_WITH_INFO を返します)。<br /><br /> *操作*引数が SQL_DELETE または SQL_UPDATE、およびオプティミスティック同時実行制御のため、操作に失敗しました。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データの右側が切り捨てられました|*操作*引数が SQL_REFRESH、および文字列または 1 つ以上の SQL_C_CHAR または SQL_C_BINARY データ型を持つ列に返されるバイナリ データが空白でない文字またはバイナリ データが NULL 以外の切り捨てが発生しました。|  
|01S01|行のエラー|*RowNumber*引数が 0 の場合とで指定された操作の実行中に 1 つまたは複数の行でエラーが発生、*操作*引数。<br /><br /> (SQL_SUCCESS_WITH_INFO が返されます複数行の操作の 1 つまたは複数は、すべての行にエラーが発生し、単一行の操作でエラーが発生した場合、SQL_ERROR が返されます。)<br /><br /> (この SQLSTATE がされる場合にのみ返されます**SQLSetPos**後に呼び出されます**SQLExtendedFetch**ドライバーが ODBC 2 である場合、* 。x*ドライバーと、カーソル ライブラリは使用されません)。|  
|01S07|小数部の切り捨て|*操作*引数が SQL_REFRESH、アプリケーション バッファーのデータ型が SQL_C_CHAR または SQL_C_BINARY、および 1 つまたは複数の列のバッファーをアプリケーションに返されるデータが切り捨てられました。 数値データ型の数値の小数部が切り捨てられました。 時刻、タイムスタンプ、および時刻部分を含む interval データ型の場合は、時間の小数部が切り捨てられました。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|結果セット内の列のデータ値がで指定されたデータ型に変換できませんでした*TargetType*への呼び出しで**SQLBindCol**です。|  
|07009|無効な記述子のインデックス|引数*操作*SQL_REFRESH または SQL_UPDATE、および列が結果セット内の列数よりも大きい列番号を持つバインドされました。|  
|21S02|派生テーブルの次数が列の一覧と一致しません|引数*操作*SQL_UPDATE、された、列がありませんでした更新可能なすべての列がバインドされていない、読み取り専用、またはバインドされている長さ/インジケーター バッファー内の値が SQL_COLUMN_IGNORE のためです。|  
|22001|文字列データの右側が切り捨てられました|*操作*引数が SQL_UPDATE、および特定の文字またはバイナリ列に値を代入 (文字) の空白または null でない (バイナリ) の文字またはバイトの切り捨てが発生しました。|  
|22003|数値が範囲|引数*操作*が SQL_UPDATE、され、結果セット内の列に数値の値の割り当て (ではなく小数部) 整数部分が切り捨てられる数値。<br /><br /> 引数*操作*SQL_REFRESH、1 つまたは複数のバインドされた列の数値の値を返す原因となる有効桁数の損失、します。|  
|22007|無効な datetime 形式|引数*操作*が SQL_UPDATE、され、結果セット内の列に日付またはタイムスタンプの値の代入と、年、月、または範囲外である日フィールドです。<br /><br /> 引数*操作*SQL_REFRESH、1 つまたは複数のバインドされた列の日付またはタイムスタンプの値を返す原因となる年、月、または範囲外である日フィールド、します。|  
|22008|日付/時刻フィールドがオーバーフローしました|*操作*引数が SQL_UPDATE、および datetime 算術演算の結果セット内の列に送信されるデータのパフォーマンスが、datetime フィールド (年、月、日、時間、分、または 2 番目のフィールド) の結果が発生しました外部のフィールドが無効の値の許容範囲は datetimes のグレゴリオ暦カレンダーの自然規則に基づいています。<br /><br /> *操作*引数 SQL_REFRESH、れ、datetime、結果セットから取得されるデータに算術演算のパフォーマンスが、datetime フィールド (年、月、日、時間、分、または 2 番目のフィールド) の結果が発生しました外部のフィールドが無効の値の許容範囲は datetimes のグレゴリオ暦カレンダーの自然規則に基づいています。|  
|22015|間隔のフィールドがオーバーフローしました|*操作*引数が SQL_UPDATE、され、正確な numeric の割り当てまたは C 間隔の種類を間隔 SQL データ型に有効桁数の損失です。<br /><br /> *操作*引数 SQL_UPDATE では、間隔の SQL 型の C 型の値の形式がなかった間隔 SQL 型に割り当てる際、します。<br /><br /> *操作*引数が SQL_REFRESH、され、真数型または interval SQL 型から C の間隔の種類に割り当てる有効桁数が失われる先頭のフィールドにします。<br /><br /> *操作*引数 _ 更新では、C の間隔の種類の SQL の型の値の表現がなかった間隔 C 型に割り当てる際、します。|  
|22018|キャストは無効な文字値|*操作*引数が SQL_REFRESH 以外の場合は C 型が、真数または概数の数値、datetime、または interval データ型以外の場合は、列の SQL 型が文字データ型です列の値なしでの有効なリテラル、。C 型を連結します。<br /><br /> 引数*操作*SQL_UPDATE 以外の場合は SQL 型が、真数または概数の数値、datetime、または interval データ型以外の場合は、C 型が SQL_C_CHAR;、列の値がバインドされた SQL 型の有効なリテラルではありませんでした。|  
|23000|整合性制約の違反|引数*操作*SQL_DELETE または SQL_UPDATE、および整合性制約の違反です。|  
|24000|カーソル状態が無効|*StatementHandle*が実行された状態でしたが、結果セットが関連付けられていない、 *StatementHandle*です。<br /><br /> (DM)、カーソルが開いて、 *StatementHandle*が**SQLFetch**または**SQLFetchScroll**が呼び出されていません。<br /><br /> カーソルが開いて、 *StatementHandle*、および**SQLFetch**または**SQLFetchScroll**が呼び出された、または後に結果セットの開始前に、カーソルが配置されたが、結果セットの末尾。<br /><br /> 引数*操作*SQL_DELETE、SQL_REFRESH、または SQL_UPDATE、または結果セットの終了後に結果セットの開始前に、カーソルが置かれています。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックによりロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|42000|構文エラーまたはアクセス違反|ドライバーは、引数で要求された操作の実行に必要に応じて、行をロックできませんでした*操作*です。<br /><br /> ドライバーは、引数で要求された行をロックできませんでした*LockType*です。|  
|44000|WITH CHECK OPTION 違反|*操作*引数は、SQL_UPDATE と更新プログラムが表示されていたテーブルに対して実行された、またはテーブル テーブルから派生した表示を指定することで作成された**WITH CHECK OPTION**ように、1 つまたは複数の行影響を受けた更新できなくなります表示されたテーブル内に存在します。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、 * \*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*関数が呼び出されたし、再度、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 SQLSetPos 関数が呼び出されたときに、この非同期関数が実行されています。<br /><br /> (DM)、指定した*StatementHandle*実行された状態ではありませんでした。 最初の呼び出さずに、関数が呼び出された**SQLExecDirect**、 **SQLExecute**、またはカタログ関数。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) ドライバーは ODBC 2、でした。*x*ドライバー、および**SQLSetPos**で呼び出され、 *StatementHandle*後**SQLFetch**が呼び出されました。|  
|HY011|属性を設定できません。|(DM) ドライバーは ODBC 2、でした。*x*ドライバー以外の SQL_ATTR_ROW_STATUS_PTR ステートメント属性が設定された、 **SQLSetPos**する前に呼び出された**SQLFetch**、 **SQLFetchScroll**、または**SQLExtendedFetch**が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|*操作*引数が SQL_UPDATE、データ値が null ポインター、および列の長さの値が 0、SQL_DATA_AT_EXEC、SQL_COLUMN_IGNORE、SQL_NULL_DATA、SQL_LEN_DATA_AT_EXEC_OFFSET 以下です。<br /><br /> *操作*引数されました SQL_UPDATE 以外のデータ値が null ポインター以外の場合は、C データ型は SQL_C_BINARY または SQL_C_CHAR; 列の長さの値が 0 より小さい値は SQL_COLUMN_IGNORE SQL_DATA_AT_EXEC に等しくないです。、、SQL_NTS または SQL_NULL_DATA、SQL_LEN_DATA_AT_EXEC_OFFSET 以下です。<br /><br /> 長さ/インジケーター バッファー内の値が SQL_DATA_AT_EXEC です。SQL 型が SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長い形式のデータ ソース固有のデータ型です。SQL_NEED_LONG_DATA_LEN 情報の種類と**SQLGetInfo** "Y"がします。|  
|HY092|無効な属性の識別子|(DM) の指定された値、*操作*引数が無効です。<br /><br /> (DM) の指定された値、 *LockType*引数が無効です。<br /><br /> *操作*引数 SQL_UPDATE または SQL_DELETE、また、ステートメント属性 SQL_ATTR_CONCURRENCY でした SQL_ATTR_CONCUR_READ_ONLY です。|  
|HY107|範囲外の行の値|引数が指定された値*RowNumber*が行セット内の行の数を超えています。|  
|HY109|無効なカーソルの位置|関連付けられているカーソル、 *StatementHandle*順方向専用とに定義されていたため、行セット内のカーソルを配置できませんでした。 SQL_ATTR_CURSOR_TYPE 属性の説明を参照して**SQLSetStmtAttr**です。<br /><br /> *操作*引数が SQL_UPDATE、SQL_DELETE、または SQL_REFRESH とで、行が識別される、 *RowNumber*引数が削除されたか、まだフェッチされていない必要があります。<br /><br /> (DM)、 *RowNumber*引数が 0 の場合、*操作*引数が SQL_POSITION です。<br /><br /> **SQLSetPos**後に呼び出された**SQLBulkOperations**が呼び出されたとする前に**SQLFetchScroll**または**SQLFetch**が呼び出されました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースがで要求された操作をサポートしていません、*操作*引数または*LockType*引数。|  
|HYT00|タイムアウトが発生しました|クエリのタイムアウト時間は、データ ソースには、結果セットが返される前に期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtAttr**で、*属性*SQL_ATTR_QUERY_TIMEOUT のです。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
  
> [!CAUTION]  
>  については、ステートメントは、ことを示すため**SQLSetPos**呼び出すことができ、ODBC 2 との互換性のために必要な*.x*アプリケーションを参照してください[ブロック カーソル、スクロール可能なカーソルと旧バージョンとの互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)です。  
  
## <a name="rownumber-argument"></a>RowNumber 引数  
 *RowNumber*引数で指定された操作を実行する対象の行セット内の行の数を指定します、*操作*引数。 場合*RowNumber*が 0 の場合、操作は、行セット内のすべての行に適用されます。 *RowNumber* 0、行セット内の行の数の値にする必要があります。  
  
> [!NOTE]  
>  C 言語の配列は、0 から始まる、 *RowNumber*引数は 1 から始まります。 たとえば、行セットの 5 番目の行を更新するには、アプリケーションによって変更されます 4 の配列インデックスで行セットのバッファーを指定します、 *RowNumber*は 5 です。  
  
 すべての操作がで指定される行にカーソルを置き*RowNumber*です。 次の操作には、カーソル位置が必要です。  
  
-   更新プログラムの配置、および delete ステートメント。  
  
-   呼び出す**SQLGetData**です。  
  
-   呼び出す**SQLSetPos** SQL_DELETE、SQL_REFRESH と SQL_UPDATE オプションを使用します。  
  
 たとえば場合、 *RowNumber*を呼び出すのための 2 は、 **SQLSetPos**で、*操作*行セットの 2 番目の行に SQL_DELETE のカーソルが配置されているし、その行が削除されました。 実装行の状態配列内 (SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される) の 2 番目の行エントリは SQL_ROW_DELETED に変更されます。  
  
 呼び出したときに、アプリケーションでカーソル位置を指定できます**SQLSetPos**です。 一般に、呼び出す**SQLSetPos**更新プログラム、位置指定を実行する前に、カーソルの位置に、SQL_POSITION または SQL_REFRESH 操作または delete ステートメントまたは呼び出し**SQLGetData**です。  
  
## <a name="operation-argument"></a>操作の引数  
 *操作*引数は、次の操作をサポートしています。 アプリケーションが呼び出す調べるには、データ ソースでどのオプションがサポートされている、 **SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、または SQL_STATIC_(カーソルの種類) に応じて CURSOR_ATTRIBUTES1 情報の種類。  
  
|*操作*<br /><br /> 引数 (argument)|操作|  
|------------------------------|---------------|  
|SQL_POSITION|ドライバーがで指定される行にカーソルを位置付けます*RowNumber*です。<br /><br /> SQL_ATTR_ROW_OPERATION_PTR ステートメント属性によって示される行の状態配列の内容は無視されます、SQL_POSITION*操作*です。|  
|SQL_REFRESH|ドライバーがで指定される行にカーソルを位置付けます*RowNumber*し、その行の行セットのバッファー内のデータを更新します。 ドライバーが行セットのバッファーでデータを返す方法の詳細については、行方向および列方向のバインドの説明を参照してください。 **SQLBindCol**です。<br /><br /> **SQLSetPos**で、*操作*SQL_REFRESH のステータスと現在のフェッチされた行セット内の行のコンテンツを更新します。 これには、ブックマークの更新が含まれます。 バッファー内のデータが更新されますが、再フェッチされませんであるため、行セットのメンバーシップは固定されています。 これとは異なるへの呼び出しによって実行される更新**SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_RELATIVE のおよび*RowNumber*は変わりませんが 0 に等しい結果セットに追加されたデータを表示し、削除できるようにから行セットは、これらの操作は、ドライバーと、カーソルによってサポートされている場合にデータを削除します。<br /><br /> 正常に更新**SQLSetPos** SQL_ROW_DELETED の行の状態は変更されません。 次のフェッチされるまで削除済みとしてマークする、行セット内で削除された行が続行されます。 カーソルが梱包をサポートしている場合、次のフェッチで、行は表示されなくなります (を後ろに続く**SQLFetch**または**SQLFetchScroll**は削除された行を返しません)。<br /><br /> 更新時に行が表示されない追加**SQLSetPos**を実行します。 この動作は異なる**SQLFetchScroll**で、 *FetchType* SQL_FETCH_RELATIVE のおよび*RowNumber*もは現在の行セットを更新する 0 に等しい追加されたレコードを表示またはカーソルがこれらの操作がサポートされている場合は、削除されたレコードをパックします。<br /><br /> 正常に更新**SQLSetPos** SQL_ROW_ADDED の行の状態が変わります SQL_ROW_SUCCESS (行の状態配列が存在する場合)。<br /><br /> 正常に更新**SQLSetPos** (行の状態配列が存在する) 場合は、SQL_ROW_UPDATED の行の状態を行の新しい状態に変更されます。<br /><br /> エラーが発生した場合、 **SQLSetPos**行に対する操作は、行の状態に設定されている SQL_ROW_ERROR、行の状態配列が存在する場合)。<br /><br /> 場合、カーソルを開く SQL_CONCUR_ROWVER、SQL_CONCUR_VALUES での更新の SQL_ATTR_CONCURRENCY ステートメント属性を持つ**SQLSetPos**ことを検出するデータ ソースが使用するオプティミスティック同時実行制御の値を更新することがあります、行が変更されました。 この場合、行のバージョンまたはカーソルの同時実行の確認に使用される値はたびに更新行セットのバッファーは、サーバーから更新されます。 これは更新された行ごとに発生します。<br /><br /> SQL_ATTR_ROW_OPERATION_PTR ステートメント属性によって示される行の状態配列の内容は無視されます、SQL_REFRESH*操作*です。|  
|SQL_UPDATE|ドライバーがで指定される行にカーソルを位置付けます*RowNumber*行セットのバッファー内の値で、基になるデータの行を更新し、(、 *TargetValuePtr*引数**SQLBindCol**)。 長さ/インジケーター バッファーからデータの長さを取得 (、 *StrLen_or_IndPtr*引数**SQLBindCol**)。 任意の列の長さが SQL_COLUMN_IGNORE の場合は、列は更新されません。 行を更新した後に行の状態配列が存在する場合)、ドライバーは SQL_ROW_UPDATED または SQL_ROW_SUCCESS_WITH_INFO 行状態配列の対応する要素を変更します。<br /><br /> ドライバーの定義とは動作場合**SQLSetPos**で、*操作*SQL_UPDATE の引数が重複する列を含むカーソルで呼び出されます。 ドライバーは、ドライバーの定義済みの SQLSTATE、ことができます、結果セットに表示される最初の列を更新したり、他のドライバーで定義された動作を実行します。<br /><br /> SQL_ATTR_ROW_OPERATION_PTR ステートメント属性を指す行操作配列は、現在の行セット内の行を一括更新中に無視することを示すために使用できます。 詳細については、この関数の参照の後で「状態と操作配列」を参照してください。|  
|SQL_DELETE|ドライバーがで指定される行にカーソルを位置付けます*RowNumber*し、基になるデータの行を削除します。 SQL_ROW_DELETED に対応する行の状態配列の要素を変更します。 次に、行の無効な行が削除された後: 更新プログラムの配置、および delete ステートメントへの呼び出し**SQLGetData**への呼び出しと**SQLSetPos**で*操作* SQL_POSITION 以外に設定します。 梱包をサポートするドライバー、に対して新しいデータがデータ ソースから取得されたときに、行は、カーソルから削除されます。<br /><br /> 行が表示されているかどうかは、カーソルの種類によって異なります。 たとえば、削除された行は静的カーソルとキーセット ドリブン カーソルに表示される動的カーソルを非表示します。<br /><br /> SQL_ATTR_ROW_OPERATION_PTR ステートメント属性を指す行操作配列は、現在の行セット内の行を一括削除中に無視することを示すために使用できます。 詳細については、この関数の参照の後で「状態と操作配列」を参照してください。|  
  
## <a name="locktype-argument"></a>LockType 引数  
 *LockType*引数はアプリケーションを同時実行を制御するための手段を提供します。 SQL_LOCK_NO_CHANGE 値のみにサポートされるほとんどの場合、同時実行レベルとトランザクションをサポートするデータ ソース、 *LockType*引数。 *LockType*引数は、通常、ファイル ベースのサポートにのみ使用します。  
  
 *LockType*引数を指定した後の行のロック状態**SQLSetPos**は実行されていません。 ドライバーは、要求された操作を実行するかを満たすために行をロックすることがない場合、 *LockType*引数、SQL_ERROR と返す SQLSTATE 42000 (構文エラーまたはアクセス違反です)。  
  
 ただし、 *LockType*単一のステートメントの引数が指定されて、ロック accords 接続ですべてのステートメントを同じ特権です。 具体的には、接続の 1 つのステートメントによって取得されたロック ロックを解除する、同じ接続で別のステートメント。  
  
 によってロックされている行**SQLSetPos**が、アプリケーションがロックされたまま**SQLSetPos**を持つ行の*LockType* SQL_LOCK_UNLOCK、またはアプリケーションまで設定呼び出し**SQLFreeHandle**ステートメントまたは**SQLFreeStmt** SQL_CLOSE オプションを使用します。 によってトランザクションをサポートするドライバーの行がロックされている**SQLSetPos**ロックが解除されて、アプリケーションが**SQLEndTran**コミットまたはロールバックするトランザクションの接続で (場合、カーソルを閉じるときに、トランザクションがコミットまたはロールバック、によって返される SQL_CURSOR_COMMIT_BEHAVIOR と SQL_CURSOR_ROLLBACK_BEHAVIOR 情報の種類によって示される**SQLGetInfo**)。  
  
 *LockType*引数は、次の種類のロックをサポートしています。 あるロックがデータ ソースによってサポートされているためには、アプリケーションが呼び出す**SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、または SQL_STATIC_(カーソルの種類) に応じて CURSOR_ATTRIBUTES1 情報の種類。  
  
|*LockType*引数|ロックの種類|  
|-------------------------|---------------|  
|SQL_LOCK_NO_CHANGE|ドライバーまたはデータ ソースにより、行が同じロックまたはロック解除状態で前に、と**SQLSetPos**が呼び出されました。 この値の*LockType*を現在の同時実行制御およびトランザクションの分離レベルで必要なすべてのロックを使用する明示的な行レベルのロックをサポートしないデータ ソースができるようにします。|  
|SQL_LOCK_EXCLUSIVE|ドライバーまたはデータ ソースでは、行が排他的ロックします。 ステートメントまたは別のアプリケーションで別の接続には、行のロックの取得を使用できません。|  
|SQL_LOCK_UNLOCK|ドライバーまたはデータ ソースには、行がロック解除します。|  
  
 ドライバー SQL_LOCK_EXCLUSIVE をサポートしている SQL_LOCK_UNLOCK をサポートしていない場合は、ロックされている行はロックされたままに前の段落で説明されている関数呼び出しのいずれかが発生するまでです。  
  
 ドライバーでは、SQL_LOCK_EXCLUSIVE をサポートしていますが、SQL_LOCK_UNLOCK をサポートしていません、ロックされている行はロック状態のまま、アプリケーションが**SQLFreeHandle**ステートメントまたは**SQLFreeStmt**とSQL_CLOSE のオプションです。 ドライバーがトランザクションをサポートし、コミットまたはロールバック、トランザクションでは、アプリケーションの呼び出し時にカーソルを閉じるかどうか**SQLEndTran**です。  
  
 内の update および delete 操作用**SQLSetPos**、アプリケーションを使用して、 *LockType*次のように引数。  
  
-   アプリケーションの呼び出しが取得された後に、行が変更されないことを保証する**SQLSetPos**で*操作*SQL_REFRESH に設定し、 *LockType* SQL_LOCK_ に設定排他。  
  
-   場合は、アプリケーションを設定する*LockType*アプリケーション SQL_ATTR_CONCURRENCY ステートメント属性 SQL_CONCUR_LOCK に指定された場合にのみ、更新または削除操作が成功するが、ドライバー、SQL_LOCK_NO_CHANGE を保証します。  
  
-   指定した場合、アプリケーション SQL_CONCUR_ROWVER、SQL_CONCUR_VALUES または SQL_ATTR_CONCURRENCY ステートメント属性をドライバーは行のバージョンまたは値を比較し、アプリケーションの行をフェッチするため、行が変更された場合は、操作を拒否します。  
  
-   アプリケーションで SQL_CONCUR_READ_ONLY SQL_ATTR_CONCURRENCY ステートメント属性を指定する場合、ドライバーの更新プログラムを拒否または削除の操作です。  
  
 また、ステートメント属性 SQL_ATTR_CONCURRENCY の詳細については、次を参照してください。 [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)です。  
  
## <a name="status-and-operation-arrays"></a>状態と操作の配列  
 呼び出すときに、次の状態および操作の配列が使用される**SQLSetPos**:  
  
-   行の状態配列 (ように、IRD と SQL_ATTR_ROW_STATUS_ARRAY ステートメント属性に SQL_DESC_ARRAY_STATUS_PTR フィールドによって示される) には、行セット内のデータの行ごとの状態の値が含まれています。 ドライバーでは、この配列に状態の値を設定への呼び出し後**SQLFetch**、 **SQLFetchScroll**、 **SQLBulkOperations**、または**SQLSetPos**. この配列は、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって参照されます。  
  
-   行操作配列 (ように、ARD および SQL_ATTR_ROW_OPERATION_ARRAY ステートメント属性で SQL_DESC_ARRAY_STATUS_PTR フィールドによって示される) を示す行セットの各行の値を格納するかどうかを呼び出す**SQLSetPos**一括操作を無視またはを実行します。 配列内の各要素は、SQL_ROW_PROCEED (既定) または SQL_ROW_IGNORE のいずれかに設定されます。 この配列は、SQL_ATTR_ROW_OPERATION_PTR ステートメント属性によって参照されます。  
  
 状態と操作の配列内の要素の数は、(で定義されている、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性)、行セット内の行の数に等しくなければなりません。  
  
 行の状態配列については、次を参照してください。 [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)です。 行操作配列については、「を無視して、行で、一括操作、」このセクションの後半を参照してください。  
  
## <a name="using-sqlsetpos"></a>SQLSetPos を使用します。  
 アプリケーションを呼び出す前に**SQLSetPos**、次の一連の手順を実行する必要があります。  
  
1.  場合は、アプリケーションが呼び出す**SQLSetPos**で*操作*SQL_UPDATE、呼び出しに設定**SQLBindCol** (または**SQLSetDescRec**) ごとにそのデータ型を指定し、列のデータと長さのバッファーをバインドする列。  
  
2.  場合は、アプリケーションが呼び出す**SQLSetPos**で*操作*SQL_DELETE または SQL_UPDATE、呼び出しに設定**SQLColAttribute**ことを確認する列を削除または更新します。更新します。  
  
3.  呼び出す**SQLExecDirect**、 **SQLExecute**、またはカタログ関数の結果セットを作成します。  
  
4.  呼び出す**SQLFetch**または**SQLFetchScroll**データを取得します。  
  
 使用しての詳細については**SQLSetPos**を参照してください[SQLSetPos でのデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)です。  
  
## <a name="deleting-data-using-sqlsetpos"></a>SQLSetPos を使用してデータを削除します。  
 使用してデータを削除する**SQLSetPos**、アプリケーションが呼び出す**SQLSetPos**で*RowNumber*を削除する行の数を設定および*操作*SQL_DELETE に設定します。  
  
 データが削除された後、ドライバーは SQL_ROW_DELETED (または SQL_ROW_ERROR) 実装行の状態配列内の該当する行の値を変更します。  
  
## <a name="updating-data-using-sqlsetpos"></a>SQLSetPos を使ったデータの更新  
 アプリケーションは 1 つまたは複数の呼び出しをまたはバインドされたデータ バッファーで列の値を渡すことができます**SQLPutData**です。 渡されるデータを含む列**SQLPutData**と呼ばれる*実行時データ**列*です。 これらは、SQL_LONGVARBINARY データ型と SQL_LONGVARCHAR 列のデータの送信に使用する一般的なされ、その他の列とを混在させることができます。  
  
#### <a name="to-update-data-with-sqlsetpos-an-application"></a>SQLSetPos、アプリケーションでデータを更新します。  
  
1.  データと長さ/インジケーター バッファー内の場所の値を使用してバインド**SQLBindCol**:  
  
    -   アプリケーションが、新しい列の値を配置する通常の列の* \*TargetValuePtr*バッファーと内でその値の長さ、 * \*StrLen_or_IndPtr*バッファー。 行が更新されない場合は、アプリケーションは、行操作配列の要素の行の SQL_ROW_IGNORE を配置します。  
  
    -   実行時データ列の場合、アプリケーションに配置列番号などのアプリケーション定義の値で、 * \*TargetValuePtr*バッファー。 値は、後で列を識別に使用できます。  
  
         アプリケーションが、SQL_LEN_DATA_AT_EXEC の結果を配置 (*長さ*) マクロで、**StrLen_or_IndPtr*バッファー。 列の SQL データ型は SQL_LONGVARBINARY、SQL_LONGVARCHAR、または長い形式のデータ ソース固有のデータ型と、ドライバーで SQL_NEED_LONG_DATA_LEN 情報の種類に"Y"が返されます場合**SQLGetInfo**、*長さ* ; パラメーターに送信されるデータのバイト数は、それ以外の場合は負でない値を指定し、無視されます。  
  
2.  呼び出し**SQLSetPos**で、*操作*引数は、データの行を更新する、SQL_UPDATE に設定されています。  
  
    -   実行時データ列が存在しない場合、プロセスが完了しました。  
  
    -   実行時データ列がある場合、この関数は SQL_NEED_DATA を返し、手順 3. に進みます。  
  
3.  呼び出し**SQLParamData**のアドレスを取得する、 * \*TargetValuePtr*処理する最初の実行時データ列のバッファー。 **SQLParamData** SQL_NEED_DATA を返します。 アプリケーションからのアプリケーション定義の値を取得する、 * \*TargetValuePtr*バッファー。  
  
    > [!NOTE]  
    >  実行時データ パラメーターは実行時データ列に似ていますが、によって返される値**SQLParamData**はごとに異なります。  
  
    > [!NOTE]  
    >  実行時データ パラメーターと、データを送信する SQL ステートメントのパラメーターには、 **SQLPutData**でステートメントを実行すると**SQLExecDirect**または**SQLExecute**. バインドされている**SQLBindParameter**またはと記述子を設定して**SQLSetDescRec**です。 によって返される値**SQLParamData**に渡された 32 ビット値は、 **SQLBindParameter**で、 *ParameterValuePtr*引数。  
  
    > [!NOTE]  
    >  実行時データ列は列のデータを送信する行セットで**SQLPutData**で行が更新された日時**SQLSetPos**です。 バインドされている**SQLBindCol**です。 によって返される値**SQLParamData**内の行のアドレスは、**TargetValuePtr*が処理されているバッファー。  
  
4.  呼び出し**SQLPutData** 1 回以上の列のデータを送信します。 すべてのデータ値を返せません場合、複数の呼び出しが必要、 * \*TargetValuePtr*で指定されたバッファー **SQLPutData**; を複数回呼び出す**SQLPutData**文字、バイナリ、またはデータ ソース固有のデータ型の列に文字データを送信するときにのみ、または列を文字、バイナリ、C のバイナリ データを送信するときに、同じ列が許可されるか、データ ソース固有のデータ型します。  
  
5.  呼び出し**SQLParamData**列のすべてのデータが送信されたことを通知するには、もう一度です。  
  
    -   多くの実行時データ列がある場合**SQLParamData** SQL_NEED_DATA およびのアドレスを返します、 *TargetValuePtr*処理する次の実行時データ列のバッファー。 アプリケーションでは、手順 4. と 5. を繰り返します。  
  
    -   これ以上の実行時データ列がある場合、プロセスが完了しました。 ステートメントが正常に実行された場合**SQLParamData** SQL_SUCCESS または; SQL_SUCCESS_WITH_INFO が返されます場合は、実行に失敗しました、SQL_ERROR を返します。 この時点では、 **SQLParamData**によって返される任意の SQLSTATE を返すことができる**SQLSetPos**です。  
  
 データが更新された場合、ドライバーは SQL_ROW_UPDATED に実装行の状態配列内の該当する行の値を変更します。  
  
 操作が取り消されたかどうか、またはでエラーが発生**SQLParamData**または**SQLPutData**の後に**SQLSetPos** SQL_NEED_DATA を返しますのすべてのデータが送信される前にアプリケーションでのみ呼び出すことができます、実行時データ列**SQLCancel**、 **SQLGetDiagField**、 **SQLGetDiagRec**、 **SQLGetFunctions**、 **SQLParamData**、または**SQLPutData**ステートメントまたはステートメントに関連付けられた接続。 ステートメントまたはステートメントに関連付けられている接続の他の関数を呼び出すこと、関数を返します SQL_ERROR と SQLSTATE HY010 (関数のシーケンス エラーです)。  
  
 アプリケーションを呼び出す場合**SQLCancel**ドライバーでは、実行時データ列のデータが引き続き必要があります、中に、ドライバー操作をキャンセルします。 アプリケーションが呼び出すことができますし、 **SQLSetPos**再度を取り消すには影響しません、カーソルの状態または現在のカーソル位置。  
  
 ドライバーの定義が場合カーソルに関連付けられているクエリ仕様の選択リストには、エラーが生成またはドライバーが重複している参照を無視し、要求された操作を実行するかどうか、同じ列への参照 1 つ以上にはが含まれています。  
  
## <a name="performing-bulk-operations"></a>一括操作の実行  
 場合、 *RowNumber*引数が 0 のドライバーで指定された操作を実行する場合、*操作*引数の値を持つ SQL_ROW_PROCEED の行の操作でそのフィールドに、行セット内のすべての行を配列を指す SQL_ATTR_ROW_OPERATION_PTR ステートメント属性。 これは、有効な値の*RowNumber*の引数、*操作*SQL_DELETE、SQL_REFRESH、または、SQL_UPDATE がない SQL_POSITION の引数。 **SQLSetPos**で、*操作*SQL_POSITION のおよび*RowNumber* SQLSTATE HY109 を 0 に等しいかどうかを返します (無効なカーソルの位置)。  
  
 SQLSTATE HYT00 など、行セット全体に関連するエラーが発生する場合 (タイムアウトの期限が切れた) ドライバーは SQL_ERROR と適切な SQLSTATE を返します。 行セットのバッファーの内容が定義と、カーソルの位置は変更されません。  
  
 エラーが発生する場合は、ドライバーが単一行に適用されます。  
  
-   SQL_ROW_ERROR に SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される行の状態配列内の行の要素を設定します。  
  
-   エラー キュー内のエラーの 1 つ以上の追加 SQLSTATEs をポストし、診断データ構造で SQL_DIAG_ROW_NUMBER フィールドを設定します。  
  
 処理した後、エラーまたは警告、ドライバーは、行セットの残りの行の操作を完了すると、SQL_SUCCESS_WITH_INFO が返されます。 したがって、エラーが返された行ごとに、エラー キューには 0 個以上の追加 SQLSTATEs が含まれます。 ドライバーは、エラーまたは警告を処理した後、操作を停止する場合は、SQL_ERROR が返されます。  
  
 ドライバーでは、すべての警告、SQLSTATE 01004 など (データが切り捨てられました) が返された場合は、特定の行に適用されるエラー情報を返す前に、行セット全体または行セット内の不明な行を適用する警告を返します。 これらの行に関するその他のエラー情報と共に、特定の行に警告が返されます。  
  
 場合*RowNumber*が 0 に等しいと*操作*SQL_UPDATE、SQL_REFRESH、または SQL_DELETE、数の行を**SQLSetPos**動作が指す、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性です。  
  
 場合*RowNumber*が 0 に等しいと*操作*SQL_DELETE、SQL_REFRESH、または SQL_UPDATE、現在の行の操作の後は、操作の前に、現在の行と同じです。  
  
## <a name="ignoring-a-row-in-a-bulk-operation"></a>一括操作で行を無視しています  
 行操作配列を使用してを使用して、一括操作中に現在の行セット内の行を無視するかを示す**SQLSetPos**です。 一括操作中に 1 つまたは複数の行を無視するドライバーを指示するには、アプリケーションは、次の手順を実行する必要があります。  
  
1.  呼び出す**SQLSetStmtAttr** SQLUSMALLINTs の配列を指す SQL_ATTR_ROW_OPERATION_PTR ステートメント属性を設定します。 このフィールドは、呼び出すことによって設定することも**SQLSetDescField**のアプリケーションが記述子ハンドルを取得する必要があります、ARD SQL_DESC_ARRAY_STATUS_PTR ヘッダー フィールドを設定します。  
  
2.  2 つの値のいずれかに、行操作配列の各要素を設定します。  
  
    -   SQL_ROW_IGNORE、一括操作に対して、行を除外することを示すためにします。  
  
    -   SQL_ROW_PROCEED、一括操作で行が含まれていることを示すためにします。 (これは既定値です)。  
  
3.  呼び出す**SQLSetPos**一括操作を実行します。  
  
 行操作配列に、次の規則が適用されます。  
  
-   SQL_ROW_IGNORE と SQL_ROW_PROCEED を使用して一括操作のみに影響**SQLSetPos**で、*操作*SQL_DELETE または SQL_UPDATE のです。 呼び出しには影響しません**SQLSetPos**で、*操作*SQL_REFRESH または SQL_POSITION のです。  
  
-   ポインターが設定されている既定によって null にします。  
  
-   ポインターが null の場合、すべての要素が SQL_ROW_PROCEED に設定された場合とすべての行が更新されます。  
  
-   SQL_ROW_PROCEED に要素の設定も、その特定の行で、操作を実行することとは限りません。 たとえば、行セット内の特定の行に状態 SQL_ROW_ERROR がある場合は、ドライバーできないことがあります、アプリケーションが SQL_ROW_PROCEED を指定するかどうかに関係なく、その行を更新します。 アプリケーションでは、操作が成功したかどうかを表示する行の状態配列を必ず確認する必要があります。  
  
-   SQL_ROW_PROCEED は、ヘッダー ファイルでは 0 として定義されます。 アプリケーションでは、すべての行を処理するために、0 行操作配列を初期化できます。  
  
-   行操作配列内の要素数"n"が SQL_ROW_IGNORE に設定されている場合と**SQLSetPos**または削除操作、呼び出しの後に変更されていない、行セットは残りの n 番目の行の一括更新を実行するために呼び出される**SQLSetPos**.  
  
-   アプリケーションは、読み取り専用の列を SQL_ROW_IGNORE 自動的に設定する必要があります。  
  
## <a name="ignoring-a-column-in-a-bulk-operation"></a>一括操作で列を無視しています  
 1 つまたは複数の読み取り専用の列を実行しようとした更新プログラムによって生成された不要な処理の診断を避けるためには、アプリケーションは SQL_COLUMN_IGNORE にバインドされている長さ/インジケーター バッファーで値を設定できます。 詳細については、次を参照してください。 [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)です。  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションは、ORDERS テーブルを参照し、注文ステータスを更新するユーザーをできます。 カーソルはキーセット ドリブンの行セット サイズが 20 であり、行のバージョンを比較するオプティミスティック同時実行制御を使用します。 それぞれの行セットをフェッチすると後、アプリケーションがそれを出力しを選択し、注文ステータスを更新することができます。 アプリケーションを使用して**SQLSetPos**に選択した行にカーソルを移動し、行の位置指定更新を実行します。 (エラー処理を省略するとわかりやすくするためです。)  
  
```  
#define ROWS 20  
#define STATUS_LEN 6  
  
SQLCHAR        szStatus[ROWS][STATUS_LEN], szReply[3];  
SQLINTEGER     cbStatus[ROWS], cbOrderID;  
SQLUSMALLINT   rgfRowStatus[ROWS];  
SQLUINTEGER    sOrderID, crow = ROWS, irow;  
SQLHSTMT       hstmtS, hstmtU;  
  
SQLSetStmtAttr(hstmtS, SQL_ATTR_CONCURRENCY, (SQLPOINTER) SQL_CONCUR_ROWVER, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER) SQL_CURSOR_KEYSET_DRIVEN, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);  
SQLSetStmtAttr(hstmtS, SQL_ATTR_ROW_STATUS_PTR, (SQLPOINTER) rgfRowStatus, 0);  
SQLSetCursorName(hstmtS, "C1", SQL_NTS);  
SQLExecDirect(hstmtS, "SELECT ORDERID, STATUS FROM ORDERS ", SQL_NTS);  
  
SQLBindCol(hstmtS, 1, SQL_C_ULONG, &sOrderID, 0, &cbOrderID);  
SQLBindCol(hstmtS, 2, SQL_C_CHAR, szStatus, STATUS_LEN, &cbStatus);  
  
while ((retcode == SQLFetchScroll(hstmtS, SQL_FETCH_NEXT, 0)) != SQL_ERROR) {  
   if (retcode == SQL_NO_DATA_FOUND)  
      break;  
   for (irow = 0; irow < crow; irow++) {  
      if (rgfRowStatus[irow] != SQL_ROW_DELETED)  
         printf("%2d %5d %*s\n", irow+1, sOrderID, NAME_LEN-1, szStatus[irow]);  
   }  
   while (TRUE) {  
      printf("\nRow number to update?");  
      gets_s(szReply, 3);  
      irow = atoi(szReply);  
      if (irow > 0 && irow <= crow) {  
         printf("\nNew status?");  
         gets_s(szStatus[irow-1], (ROWS * STATUS_LEN));  
         SQLSetPos(hstmtS, irow, SQL_POSITION, SQL_LOCK_NO_CHANGE);  
         SQLPrepare(hstmtU,  
          "UPDATE ORDERS SET STATUS=? WHERE CURRENT OF C1", SQL_NTS);  
         SQLBindParameter(hstmtU, 1, SQL_PARAM_INPUT,  
            SQL_C_CHAR, SQL_CHAR,  
            STATUS_LEN, 0, szStatus[irow], 0, NULL);  
         SQLExecute(hstmtU);  
      } else if (irow == 0) {  
         break;  
      }  
   }  
}  
```  
  
 例については、次を参照してください。[位置指定の Update ステートメントとステートメントの削除](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)と[SQLSetPos で行セット内の行の更新](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ブロック カーソルの位置に関係なく一括操作の実行|[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|記述子の 1 つのフィールドを取得します。|[SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|記述子の複数のフィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|記述子の 1 つのフィールドを設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|記述子の複数のフィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

