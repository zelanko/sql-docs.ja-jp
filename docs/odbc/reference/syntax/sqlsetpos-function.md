---
title: SQLSetPos 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e769949c8c57bbec56055c58c9002494fc6d37be
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53211991"
---
# <a name="sqlsetpos-function"></a>SQLSetPos 関数
**準拠**  
 バージョンが導入されました。ODBC 1.0 規格に準拠します。ODBC  
  
 **まとめ**  
 **SQLSetPos**行セットのカーソル位置を設定し、行セット内のデータを更新するかを結果セット内のデータ更新または削除できます。  
  
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
  
 詳細については、「コメントです。」を参照してください。  
  
 *操作*  
 [入力]操作を実行します。  
  
 SQL_POSITION SQL_REFRESH SQL_UPDATE SQL_DELETE  
  
> [!NOTE]
>  値は、SQL_ADD、*操作*ODBC 3 の引数が非推奨とされました *.x*します。 ODBC 3。*x*ドライバーは下位互換性のため SQL_ADD をサポートする必要があります。 この機能はへの呼び出しによって置き換えられました**SQLBulkOperations**で、*操作*SQL_ADD の。 ODBC 3 時にします。*x*アプリケーションは、ODBC 2 で動作します *。x*ドライバー、ドライバー マネージャーは、マップへの呼び出し**SQLBulkOperations**で、*操作*に SQL_ADD の**SQLSetPos**で、 *操作*SQL_ADD の。  
  
 詳細については、「コメントです。」を参照してください。  
  
 *LockType*  
 [入力]指定された操作を実行した後に行をロックする方法を指定します、*操作*引数。  
  
 SQL_LOCK_NO_CHANGE SQL_LOCK_EXCLUSIVE SQL_LOCK_UNLOCK  
  
 詳細については、「コメントです。」を参照してください。  
  
 **返します。**  
  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NEED_DATA、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLSetPos** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得される可能性があります**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*します。 次の表に、一般的にによって返される SQLSTATE 値**SQLSetPos** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
 複数行の操作の 1 つ以上のただしすべてではなく行にエラーが発生した場合にエラーが発生した場合、SQL_ERROR が返されますをすべてその SQLSTATEs SQL_SUCCESS_WITH_INFO または SQL_ERROR (を除く 01xxx SQLSTATEs) を返すことができる、SQL_SUCCESS_WITH_INFO が返される、単一行の操作です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01001|カーソル操作の競合|*操作*引数が SQL_DELETE または SQL_UPDATE、および行または複数の行が削除または更新します。 (1 つ以上の行に更新プログラムの詳細については、SQL_ATTR_SIMULATE_CURSOR の説明を参照してください*属性*で**SQLSetStmtAttr**。)。(関数は、SQL_SUCCESS_WITH_INFO を返します)。<br /><br /> *操作*引数が SQL_DELETE または SQL_UPDATE、およびオプティミスティック同時実行制御のため、操作に失敗しました。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データの右側が切り捨てられました|*操作*引数が SQL_REFRESH、および文字列またはバイナリ データの列またはの SQL_C_CHAR または SQL_C_BINARY データ型を持つ列に対して返される空白でない文字または NULL 以外のバイナリ データの切り捨てが発生しました。|  
|01S01|行内のエラー|*RowNumber*引数が 0 の場合とで指定された操作の実行中に 1 つまたは複数の行でエラーが発生しました、*操作*引数。<br /><br /> (SQL_SUCCESS_WITH_INFO が返されます、複数行の操作の 1 つ以上のただしすべてではなく行でエラーが発生し、単一行の操作でエラーが発生した場合、SQL_ERROR が返されます。)<br /><br /> (この SQLSTATE の場合にのみが返されます**SQLSetPos**が呼び出された後**SQLExtendedFetch**場合、ドライバーは ODBC 2 *。x*ドライバーおよびカーソル ライブラリは使用されません)。|  
|01S07|分数が切り捨てられました|*操作*引数が SQL_REFRESH、アプリケーションのバッファーのデータ型が SQL_C_CHAR または SQL_C_BINARY、および 1 つまたは複数の列のバッファーをアプリケーションに返されるデータが切り捨てられました。 数値データ型、数値の小数部が切り捨てられました。 時刻、タイムスタンプ、および時間コンポーネントを含む interval データ型の場合は、時間の小数部が切り捨てられました。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|指定されたデータ型に結果セット内の列のデータ値を変換でした*TargetType*への呼び出しで**SQLBindCol**します。|  
|07009|無効な記述子のインデックス|引数*操作*SQL_REFRESH または SQL_UPDATE、および列が結果セット内の列の数よりも大きい列番号でバインドされました。|  
|21S02|派生テーブルの次数が列の一覧と一致しません|引数*操作*SQL_UPDATE の列がない更新可能なすべての列がバインドされていない、読み取り専用、またはバインドされている長さ/インジケーター バッファーの値が SQL_COLUMN_IGNORE のためです。|  
|22001|文字列データの右側が切り捨てられました|*操作*引数は、SQL_UPDATE と文字値または列にバイナリ値の割り当て (文字) の空白または (バイナリ) の null 以外の文字またはバイトの切り捨てが発生しました。|  
|22003|数値が範囲外|引数*操作*SQL_UPDATE、結果セット内の列に数値の値の割り当ての原因となった (ではなく小数部) 整数部分が切り捨てられる数値。<br /><br /> 引数*操作*SQL_REFRESH を 1 つまたは複数のバインドされた列の数値の値を返す原因となる有効桁数が失われる。|  
|22007|無効な datetime 形式|引数*操作*SQL_UPDATE、年、月、または範囲外の日付フィールドに結果セット内の列に日付またはタイムスタンプの値の割り当てが発生します。<br /><br /> 引数*操作*SQL_REFRESH を 1 つまたは複数のバインドされた列の日付またはタイムスタンプの値を返す原因となる年、月、または範囲外となる日フィールド。|  
|22008|日付/時刻フィールドがオーバーフローしました|*操作*引数が SQL_UPDATE、および算術演算の結果セット内の列に送信されるデータを datetime のパフォーマンス結果の中の datetime フィールド (年、月、日、時間、分、または 2 番目のフィールド) が発生しました外部のフィールド、または無効である値の許容範囲 datetimes のグレゴリオ暦カレンダーの自然規則に基づいています。<br /><br /> *操作*引数が SQL_REFRESH、および算術演算の結果セットから取得されるデータを datetime のパフォーマンス結果の中の datetime フィールド (年、月、日、時間、分、または 2 番目のフィールド) が発生しました外部のフィールド、または無効である値の許容範囲 datetimes のグレゴリオ暦カレンダーの自然規則に基づいています。|  
|22015|Interval フィールド オーバーフロー|*操作*の正確な数値の割り当てまたは間隔 SQL データ型に C の間隔の種類は、有効桁数の損失を原因し、なった引数は、SQL_UPDATE します。<br /><br /> *操作*引数が SQL_UPDATE; 間隔 SQL 型に割り当てる際、SQL 型の間隔で C 型の値の表現がなかった。<br /><br /> *操作*引数が SQL_REFRESH、および先頭のフィールドの有効桁数の損失を原因と正確な numeric または間隔 SQL 型から C の間隔の種類を割り当てることです。<br /><br /> *操作*引数が sql _ 更新; に C の間隔の種類を割り当てるときは、C の間隔の種類の SQL 型の値の表現がなかった。|  
|22018|キャストの無効な文字の値|*操作*引数が SQL_REFRESH; C 型は、真数または概数の数値、datetime、または間隔のデータ型; 列の SQL 型が文字データ型の; と列の値が有効なリテラルのC 型をバインドします。<br /><br /> 引数*操作*SQL_UPDATE; SQL 型が、真数または概数の数値、datetime、または間隔のデータ型は C 型が SQL_C_CHAR;、列の値がバインドされた SQL 型の有効なリテラルではありませんでした。|  
|23000|整合性制約違反|引数*操作*SQL_DELETE または SQL_UPDATE、および整合性制約に違反していた。|  
|24000|カーソル状態が無効|*StatementHandle* 、実行の状態でしたが、結果セットが関連付けられていない、 *StatementHandle*します。<br /><br /> (DM)、カーソルが開いて、 *StatementHandle*が**SQLFetch**または**SQLFetchScroll**呼び出されていない必要があります。<br /><br /> カーソルが開いて、 *StatementHandle*、および**SQLFetch**または**SQLFetchScroll**が呼び出された、または後に、結果セットの開始前に、カーソルが配置されたが、結果セットの末尾。<br /><br /> 引数*操作*SQL_DELETE、SQL_REFRESH、または SQL_UPDATE、または結果セットの終了後に、結果セットの開始前に、カーソルが配置されました。|  
|40001|シリアル化エラー|トランザクションが別のトランザクションでリソース デッドロックによりロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を特定できません。|  
|42000|構文エラーまたはアクセス違反|ドライバーでの引数で要求された操作を実行する必要に応じて、行をロックできなかった*操作*します。<br /><br /> ドライバーで、引数で要求された行をロックできなかった*LockType*します。|  
|44000|WITH CHECK OPTION 違反|*操作*引数は、SQL_UPDATE と更新プログラムが表示されているテーブルに対して実行された、またはテーブルを指定することによって作成された表示されているテーブルに由来**WITH CHECK OPTION**ような 1 つまたは複数の行影響を受ける、更新プログラムは表示されているテーブル内に存在できなきます。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効に、 *StatementHandle*します。 関数が呼び出された、および実行を完了する前に**SQLCancel**または**SQLCancelHandle**が呼び出されて、 *StatementHandle*関数が呼び出された後、もう一度、 *StatementHandle*します。<br /><br /> 関数が呼び出された、および実行を完了する前に**SQLCancel**または**SQLCancelHandle**が呼び出されて、 *StatementHandle*から別のスレッドで、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM) を非同期的に実行中の関数が呼び出された接続ハンドルに関連付けられているため、 *StatementHandle*します。 この非同期関数は、SQLSetPos 関数が呼び出されたときにまだ実行中だった。<br /><br /> (DM)、指定した*StatementHandle*実行の状態ではありませんでした。 最初に呼び出さず、関数が呼び出された**SQLExecDirect**、 **SQLExecute**、またはカタログ関数。<br /><br /> (DM) を非同期的に実行中の関数 (いないこの"1") が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**に対して呼び出された、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) ドライバーは ODBC 2、でした。*x*ドライバー、および**SQLSetPos**に対して呼び出された、 *StatementHandle*後**SQLFetch**が呼び出されました。|  
|HY011|属性を設定できません。|(DM) ドライバーは ODBC 2、でした。*x*ドライバー;、し、SQL_ATTR_ROW_STATUS_PTR ステートメント属性が設定された、 **SQLSetPos**する前に呼び出された**SQLFetch**、 **SQLFetchScroll**、または**SQLExtendedFetch**が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|*操作*引数が SQL_UPDATE、データ値が null ポインター、および列の長さの値が 0、SQL_DATA_AT_EXEC、SQL_COLUMN_IGNORE、SQL_NULL_DATA、SQL_LEN_DATA_AT_EXEC_OFFSET 未満。<br /><br /> *操作*SQL_DATA_AT_EXEC、SQL_COLUMN_IGNORE と等しくありませんが引数が SQL_UPDATE; データ値が null ポインターではありませんでした C データ型が SQL_C_BINARY または SQL_C_CHAR; と列の長さの値が 0 未満でした。、、SQL_NTS または SQL_NULL_DATA、SQL_LEN_DATA_AT_EXEC_OFFSET 未満。<br /><br /> 長さ/インジケーター バッファーの値が SQL_DATA_AT_EXEC です。SQL 型がいずれかの SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長い形式のデータ ソースに固有のデータ型。SQL_NEED_LONG_DATA_LEN 情報の種類と**SQLGetInfo** "Y"でした。|  
|HY092|無効な属性の識別子|(DM) の指定された値、*操作*引数が無効です。<br /><br /> (DM) の指定された値、 *LockType*引数が無効です。<br /><br /> *操作*引数が SQL_UPDATE または SQL_DELETE、および SQL_ATTR_CONCURRENCY ステートメント属性されました SQL_ATTR_CONCUR_READ_ONLY します。|  
|HY107|行の値が範囲外|引数が指定された値*RowNumber*が行セットの行の数を超えていました。|  
|HY109|無効なカーソルの位置|関連付けられているカーソル、 *StatementHandle*カーソルが行セット内の配置されていませんでしたので、順方向専用として定義されました。 SQL_ATTR_CURSOR_TYPE 属性の説明を参照して**SQLSetStmtAttr**します。<br /><br /> *操作*引数が SQL_UPDATE、SQL_DELETE、または SQL_REFRESH とで識別される、行、 *RowNumber*引数に削除されたかがまだフェッチされていません。<br /><br /> (DM)、 *RowNumber*引数が 0 の場合、*操作*SQL_POSITION をされた引数。<br /><br /> **SQLSetPos**後が呼び出された**SQLBulkOperations**が呼び出されたとする前に**SQLFetchScroll**または**SQLFetch**が呼び出されました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースがで要求された操作をサポートしていません、*操作*引数または*LockType*引数。|  
|HYT00|タイムアウトが発生しました|データ ソースには、結果セットが返される前に、クエリのタイムアウト期間が終了しました。 によって、タイムアウト期間が設定されます**SQLSetStmtAttr**で、*属性*SQL_ATTR_QUERY_TIMEOUT の。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングは無効です。|通知のモデルを使用すると、常にポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了が呼び出されていません。|通知モードが有効になっている場合、ハンドルでは、前の関数呼び出しに SQL_STILL_EXECUTING が返された場合と**SQLCompleteAsync**後処理を行い、操作を完了するハンドルで呼び出す必要があります。|  
  
## <a name="comments"></a>コメント  
  
> [!CAUTION]
>  ステートメントについては、ことを示すため**SQLSetPos**呼び出すことができます ODBC 2 と互換性のために必要なものと *.x*アプリケーションを参照してください[ブロック カーソル、スクロール可能なカーソル、および旧バージョンとの互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)します。  
  
## <a name="rownumber-argument"></a>RowNumber 引数  
 *RowNumber*引数で指定された操作を実行する対象の行セット内の行の数を指定します、*操作*引数。 場合*RowNumber*が 0 の場合、操作は、行セット内のすべての行に適用されます。 *RowNumber*行セットの行の数を 0 値を指定する必要があります。  
  
> [!NOTE]  
>  C 言語では、配列は、0 から始まる、 *RowNumber*引数は 1 から始まります。 たとえば、行セットの 5 番目の行を更新するアプリケーション配列インデックス 4 行セットのバッファーを変更しますを指定します、 *RowNumber*は 5 です。  
  
 すべての操作がで指定した行にカーソルを位置付けます*RowNumber*します。 次の操作では、カーソル位置が必要です。  
  
-   更新プログラムの配置、および delete ステートメント。  
  
-   呼び出す**SQLGetData**します。  
  
-   呼び出す**SQLSetPos** SQL_DELETE、SQL_REFRESH、SQL_UPDATE オプションを使用します。  
  
 たとえば場合、 *RowNumber*への呼び出しの 2 は、 **SQLSetPos**で、*操作*行セットの 2 行目に SQL_DELETE のカーソルが配置されているし、その行が削除されました。 配列内の実装の行の状態 (し、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される) の 2 行目のエントリは SQL_ROW_DELETED に変更されます。  
  
 呼び出すときに、アプリケーションでカーソル位置を指定できます**SQLSetPos**します。 一般に、呼び出す**SQLSetPos**位置指定を実行する前に、カーソルを配置する SQL_POSITION または SQL_REFRESH の操作で更新または delete ステートメントを呼び出す**SQLGetData**します。  
  
## <a name="operation-argument"></a>演算の引数  
 *操作*引数は、次の操作をサポートしています。 アプリケーションが呼び出すオプションがデータ ソースでサポートされているかを判断する**SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、または SQL_STATIC_(カーソルの種類) に応じて CURSOR_ATTRIBUTES1 情報の種類。  
  
|*操作*<br /><br /> 引数 (argument)|操作|  
|------------------------------|---------------|  
|SQL_POSITION|ドライバーがで指定した行にカーソルを位置付けます*RowNumber*します。<br /><br /> SQL_ATTR_ROW_OPERATION_PTR ステートメント属性によって示される行の状態配列の内容は無視されます、SQL_POSITION*操作*します。|  
|SQL_REFRESH|ドライバーがで指定した行にカーソルを位置付けます*RowNumber*し、その行の行セットのバッファー内のデータを更新します。 ドライバーが行セットのバッファーでデータを返す方法の詳細については、行方向と列方向のバインドでの説明を参照してください。 **SQLBindCol**します。<br /><br /> **SQLSetPos**で、*操作*SQL_REFRESH の状態と現在のフェッチされた行セット内の行のコンテンツを更新します。 これには、ブックマークの更新が含まれます。 バッファー内のデータ更新は再フェッチできません、ため、行セット内のメンバシップは固定されています。 これは、呼び出しによって実行される更新とは異なります**SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_RELATIVE の*RowNumber*は変わりませんが、0これらの操作が、ドライバーと、カーソルによってサポートされている場合、削除されたデータを行セットから、結果セットに追加されたデータを表示し、削除できるようにします。<br /><br /> 正常に更新**SQLSetPos** SQL_ROW_DELETED の行の状態は変更されません。 削除された行、行セット内では、次のフェッチされるまで削除済みとしてマークし続けます。 カーソルは、パッキングをサポートしている場合、次のフェッチで、行は表示されなくなります (を後ろに続く**SQLFetch**または**SQLFetchScroll**削除された行は返されません)。<br /><br /> 更新時に行が表示されない追加**SQLSetPos**が実行されます。 この動作は異なる**SQLFetchScroll**で、 *FetchType* SQL_FETCH_RELATIVE の*RowNumber* 0 もが現在の行セットを更新します。追加したレコードを表示またはカーソルがこれらの操作がサポートされている場合は、削除されたレコードをパックします。<br /><br /> 正常に更新**SQLSetPos** SQL_ROW_ADDED の行の状態は (行の状態配列が存在する) 場合、SQL_ROW_SUCCESS に変更されます。<br /><br /> 正常に更新**SQLSetPos** SQL_ROW_UPDATED の行の状態は (行の状態配列が存在する) 場合、行の新しい状態に変更されます。<br /><br /> エラーが発生した場合、 **SQLSetPos**行に対する操作は、行の状態に設定されて SQL_ROW_ERROR (行の状態配列が存在する) 場合。<br /><br /> SQL_CONCUR_ROWVER、SQL_CONCUR_VALUES での更新のステートメント属性 SQL_ATTR_CONCURRENCY で開かれたカーソル**SQLSetPos**ことを検出するデータ ソースで使用するオプティミスティック同時実行制御値を更新することがあります、行が変更されました。 このような場合は、行セットのバッファーは、サーバーから更新されるたびに、行のバージョンまたはカーソルの同時実行の確認に使用される値が更新されました。 これは更新された行ごとに発生します。<br /><br /> SQL_ATTR_ROW_OPERATION_PTR ステートメント属性によって示される行の状態配列の内容は無視されます、SQL_REFRESH*操作*します。|  
|SQL_UPDATE|ドライバーがで指定した行にカーソルを位置付けます*RowNumber*行セットのバッファー内の値を基になる行のデータを更新している (、 *TargetValuePtr*引数**SQLBindCol**)。 長さ/インジケーター バッファーからのデータの長さを取得します (、 *StrLen_or_IndPtr*引数**SQLBindCol**)。 任意の列の長さが SQL_COLUMN_IGNORE の場合は、列は更新されません。 行を更新した後 (行の状態配列が存在する) 場合、ドライバーは SQL_ROW_UPDATED または SQL_ROW_SUCCESS_WITH_INFO 行の状態配列の対応する要素を変更します。<br /><br /> ドライバーで定義された動作は、どのような場合**SQLSetPos**で、*操作*SQL_UPDATE の引数が重複する列を含むカーソルで呼び出されます。 ドライバーは、ドライバーの定義済みの SQLSTATE を返す、ことができます、結果セットに表示される最初の列を更新したりその他のドライバーの定義済みの動作を実行できます。<br /><br /> SQL_ATTR_ROW_OPERATION_PTR ステートメント属性によって示される行操作配列を現在の行セット内の行を一括更新中に無視することを示すために使用できます。 詳細については、後でこの関数の参照に「状態と操作の配列」を参照してください。|  
|SQL_DELETE|ドライバーがで指定した行にカーソルを位置付けます*RowNumber*し、基になるのデータ行を削除します。 SQL_ROW_DELETED に対応する行の状態配列の要素を変更します。 行が削除されると、次は、行は無効です: 更新プログラムを配置および delete ステートメント、呼び出しを**SQLGetData**への呼び出しと**SQLSetPos**で*操作* SQL_POSITION 以外に設定します。 梱包をサポートするドライバーは、行は、新しいデータがデータ ソースから取得されると、カーソルから削除されます。<br /><br /> 行が表示されるかどうかは、カーソルの種類によって異なります。 たとえば、削除された行は、静的およびキーセット ドリブン カーソルを表示しながら、動的カーソルを非表示です。<br /><br /> SQL_ATTR_ROW_OPERATION_PTR ステートメント属性によって示される行操作配列を現在の行セット内の行を一括削除中に無視することを示すために使用できます。 詳細については、後でこの関数の参照に「状態と操作の配列」を参照してください。|  
  
## <a name="locktype-argument"></a>LockType 引数  
 *LockType*引数がアプリケーションを同時実行を制御するための手段を提供します。 SQL_LOCK_NO_CHANGE 値のみがサポートされるほとんどの場合、同時実行レベルとトランザクションをサポートするデータ ソース、 *LockType*引数。 *LockType*引数は、通常、ファイル ベースのサポートにのみ使用します。  
  
 *LockType*後の行のロックの状態を指定する引数**SQLSetPos**が実行されました。 ドライバーが要求された操作を実行するかを満たすために行をロックできない場合、 *LockType* SQL_ERROR と SQLSTATE 42000 (構文エラーまたはアクセス違反) を返しますが、引数。  
  
 ただし、 *LockType* 1 つのステートメントの引数が指定されて、ロック accords 接続ですべてのステートメントを同じ特権。 具体的には、同じ接続上で別のステートメントでは接続で 1 つのステートメントによって取得されたロックをロック解除することができます。  
  
 によってロックされている行**SQLSetPos**が、アプリケーションがロックされたまま**SQLSetPos**を持つ行の*LockType* SQL_LOCK_UNLOCK、またはアプリケーションまで設定呼び出し**SQLFreeHandle**ステートメントまたは**SQLFreeStmt** SQL_CLOSE オプションを使用します。 によってトランザクションをサポートするドライバーの場合、行がロックされている**SQLSetPos**アプリケーションを呼び出すときにロックが解除**SQLEndTran**コミットまたはロールバック トランザクションの接続で (この場合、カーソルを切断するにはトランザクションがコミットまたはロールバックし、によって返される SQL_CURSOR_COMMIT_BEHAVIOR と SQL_CURSOR_ROLLBACK_BEHAVIOR 情報の種類によって示されるときに**SQLGetInfo**)。  
  
 *LockType*引数は、次の種類のロックをサポートしています。 アプリケーションが呼び出すどのロックは、データ ソースでサポートされるかを判断する**SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、または SQL_STATIC_(カーソルの種類) に応じて CURSOR_ATTRIBUTES1 情報の種類。  
  
|*LockType*引数|ロックの種類|  
|-------------------------|---------------|  
|SQL_LOCK_NO_CHANGE|ドライバーまたはデータ ソースにより、行は前に、と同じロックまたはロック解除の状態が**SQLSetPos**が呼び出されました。 この値の*LockType*によって現在の同時実行とトランザクション分離レベルが必要なロックを使用する明示的な行レベルのロックをサポートしないデータ ソースができるようにします。|  
|SQL_LOCK_EXCLUSIVE|ドライバーまたはデータ ソースは、専用の行をロックします。 任意の行ロックを取得する別の接続で、または別のアプリケーションでのステートメントを使用できません。|  
|SQL_LOCK_UNLOCK|ドライバーまたはデータ ソースには、行がロック解除します。|  
  
 ドライバーは SQL_LOCK_EXCLUSIVE をサポートしていますが、SQL_LOCK_UNLOCK をサポートしていませんの場合は、前の段落で説明されている関数呼び出しのいずれかが発生するまでロックされている行がロックされている残ります。  
  
 ロックされている行をアプリケーションがロックされたままはドライバー SQL_LOCK_EXCLUSIVE をサポートしている SQL_LOCK_UNLOCK をサポートしていない場合は、 **SQLFreeHandle**ステートメントまたは**SQLFreeStmt**でSQL_CLOSE オプション。 ドライバーはトランザクションをサポートし、コミットや、アプリケーションが、トランザクションをロールバック時にカーソルをクローズかどうか**SQLEndTran**します。  
  
 Update および delete 操作の**SQLSetPos**、アプリケーションを使用して、 *LockType*引数を次のとおりです。  
  
-   アプリケーションを呼び出すが、取得後に、行が変更されないことを保証する**SQLSetPos**で*操作*SQL_REFRESH に設定し、 *LockType* SQL_LOCK_ に設定排他。  
  
-   設定されている場合*LockType*アプリケーション ステートメント属性 SQL_ATTR_CONCURRENCY に SQL_CONCUR_LOCK を指定する場合にのみ、更新または削除操作が成功するが、ドライバー、SQL_LOCK_NO_CHANGE を保証します。  
  
-   アプリケーションは、ステートメント属性 SQL_ATTR_CONCURRENCY に SQL_CONCUR_ROWVER、SQL_CONCUR_VALUES またはを指定する場合、ドライバーは行バージョンまたは値を比較し、アプリケーションの行をフェッチするために、行が変更された場合に、操作を拒否します。  
  
-   アプリケーションでは、また、ステートメント属性 SQL_ATTR_CONCURRENCY を SQL_CONCUR_READ_ONLY を指定する場合、ドライバーの更新プログラムを拒否または削除操作。  
  
 また、ステートメント属性 SQL_ATTR_CONCURRENCY の詳細については、次を参照してください。 [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)します。  
  
## <a name="status-and-operation-arrays"></a>状態と操作の配列  
 次の状態と操作の配列は、呼び出すときに使用します**SQLSetPos**:。  
  
-   行の状態配列など、IRD と SQL_ATTR_ROW_STATUS_ARRAY ステートメント属性で SQL_DESC_ARRAY_STATUS_PTR フィールドによって示される) には、行セット内のデータの各行の状態の値が含まれています。 ドライバーは、呼び出しの後にこの配列の状態の値を設定**SQLFetch**、 **SQLFetchScroll**、 **SQLBulkOperations**、または**SQLSetPos**. この配列は、し、SQL_ATTR_ROW_STATUS_PTR ステートメント属性を指しています。  
  
-   行操作配列など、ARD と SQL_ATTR_ROW_OPERATION_ARRAY ステートメント属性で SQL_DESC_ARRAY_STATUS_PTR フィールドによって示される) を示す行セットの各行の値を格納するかどうかを呼び出す**SQLSetPos**一括操作を無視またはを実行します。 配列内の各要素は、SQL_ROW_PROCEED (既定値) または SQL_ROW_IGNORE のいずれかに設定されます。 この配列は、SQL_ATTR_ROW_OPERATION_PTR ステートメント属性を指しています。  
  
 状態と操作の配列内の要素の数は、(、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性で定義) された行セット内の行の数に等しくなければなりません。  
  
 行の状態配列については、次を参照してください。 [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)します。 行操作配列については、「を無視して、行で、一括操作で、」このセクションの後半を参照してください。  
  
## <a name="using-sqlsetpos"></a>SQLSetPos の使用  
 アプリケーションを呼び出す前に**SQLSetPos**、次の一連の手順を実行する必要があります。  
  
1.  場合は、アプリケーションが呼び出す**SQLSetPos**で*操作*SQL_UPDATE、呼び出しに設定**SQLBindCol** (または**SQLSetDescRec**) ごとにデータ型を指定し、列のデータと長さのバッファーをバインドする列。  
  
2.  場合は、アプリケーションが呼び出す**SQLSetPos**で*操作*SQL_DELETE または SQL_UPDATE、呼び出しに設定**SQLColAttribute**ことを確認する列を削除するか更新します。更新します。  
  
3.  呼び出す**SQLExecDirect**、 **SQLExecute**、またはカタログ関数の結果セットを作成します。  
  
4.  呼び出す**SQLFetch**または**SQLFetchScroll**データを取得します。  
  
 使用しての詳細については**SQLSetPos**を参照してください[SQLSetPos によるデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)します。  
  
## <a name="deleting-data-using-sqlsetpos"></a>SQLSetPos を使用してデータを削除します。  
 使用してデータを削除する**SQLSetPos**、アプリケーションを呼び出す**SQLSetPos**で*RowNumber*を削除する行の数に設定し、*操作*SQL_DELETE に設定します。  
  
 データが削除されると、ドライバーは sql_row_deleted になります (または SQL_ROW_ERROR) に該当する行の実装の行の状態配列内の値を変更します。  
  
## <a name="updating-data-using-sqlsetpos"></a>SQLSetPos によるデータの更新  
 バインドされたデータ バッファーまたは 1 つまたは複数の呼び出しで、アプリケーションは、列の値を渡すことができます**SQLPutData**します。 列のデータが渡される**SQLPutData**と呼ばれます*実行時データ**列*します。 これらは、SQL_LONGVARBINARY データ型と SQL_LONGVARCHAR 列のデータの送信によく使用され、他の列とを混在させることができます。  
  
#### <a name="to-update-data-with-sqlsetpos-an-application"></a>SQLSetPos、アプリケーションでデータを更新します。  
  
1.  データと長さ/インジケーター バッファー内の場所の値がバインドされている**SQLBindCol**:  
  
    -   アプリケーションの場所で新しい列の値の通常の列の場合は、  *\*TargetValuePtr*バッファーとその値の長さ、  *\*StrLen_or_IndPtr*バッファー。 行が更新されない場合、アプリケーションは、行操作配列の要素の行の SQL_ROW_IGNORE を配置します。  
  
    -   実行時データ列の場合は、アプリケーションはで、列番号などのアプリケーション定義の値を配置、  *\*TargetValuePtr*バッファー。 値は、列を識別するために後で使用できます。  
  
         アプリケーションの場所の結果、SQL_LEN_DATA_AT_EXEC (*長さ*) マクロで、**StrLen_or_IndPtr*バッファー。 列の SQL データ型は SQL_LONGVARBINARY、SQL_LONGVARCHAR、または長い形式のデータ ソースに固有のデータ型と、ドライバーで SQL_NEED_LONG_DATA_LEN 情報の種類に"Y"を返す場合**SQLGetInfo**、*長さ* ; パラメーターに送信されるデータのバイト数は、それ以外の場合、負でない値を指定する必要があり、無視されます。  
  
2.  呼び出し**SQLSetPos**で、*操作*引数は、データの行を更新する SQL_UPDATE に設定します。  
  
    -   実行時データ列がない場合は、プロセスが完了しました。  
  
    -   実行時データ列がある場合、関数は SQL_NEED_DATA を返し、手順 3. に進みます。  
  
3.  呼び出し**SQLParamData**のアドレスを取得する、  *\*TargetValuePtr*処理する最初の実行時データ列のバッファー。 **SQLParamData** SQL_NEED_DATA を返します。 アプリケーションからのアプリケーション定義の値を取得する、  *\*TargetValuePtr*バッファー。  
  
    > [!NOTE]  
    >  値がによって返される実行時データ パラメーターは実行時データ列に似ていますが、 **SQLParamData**はそれぞれ異なります。  
  
    > [!NOTE]  
    >  実行時データ パラメーターは、SQL ステートメントでデータを送信でパラメーター **SQLPutData**でステートメントを実行すると**SQLExecDirect**または**SQLExecute**. バインドされている**SQLBindParameter**またはの記述子を設定して**SQLSetDescRec**します。 によって返される値**SQLParamData**に渡される 32 ビット値は、 **SQLBindParameter**で、 *ParameterValuePtr*引数。  
  
    > [!NOTE]  
    >  実行時データ列は列のデータを送信行セットで**SQLPutData**で行が更新された日時**SQLSetPos**します。 バインドされている**SQLBindCol**します。 によって返される値**SQLParamData**内の行のアドレスは、**TargetValuePtr*が処理されているバッファー。  
  
4.  呼び出し**SQLPutData**列のデータを送信する 1 つ以上の時間。 すべてのデータ値を返すことができない場合は、複数の呼び出しが必要な *\*TargetValuePtr*で指定されたバッファー **SQLPutData**; を複数回呼び出す**SQLPutData**文字、バイナリ、またはデータのソースに固有のデータ型の列に文字データを送信するときにのみ、または列が文字、バイナリ、C のバイナリ データを送信するときに、同じ列が許可されるか、データ ソースに固有のデータを入力します。  
  
5.  呼び出し**SQLParamData**列のすべてのデータが送信されたことを通知するには、もう一度です。  
  
    -   多くの実行時データ列がある場合**SQLParamData** SQL_NEED_DATA およびのアドレスを返します、 *TargetValuePtr*処理する次の実行時データ列のバッファー。 アプリケーションでは、手順 4. と 5. を繰り返します。  
  
    -   これ以上の実行時データ列がある場合は、プロセスが完了しました。 ステートメントが正常に実行された場合**SQLParamData** SQL_SUCCESS、SQL_SUCCESS_WITH_INFO; を返します、実行に失敗しました、SQL_ERROR が返されます。 この時点では、 **SQLParamData**によって返される任意の SQLSTATE を返すことができます**SQLSetPos**します。  
  
 データが更新された場合、ドライバーは SQL_ROW_UPDATED に該当する行の実装の行の状態配列内の値を変更します。  
  
 操作が取り消されたかどうか、またはエラーが発生**SQLParamData**または**SQLPutData**後**SQLSetPos** SQL_NEED_DATA を返しますのすべてのデータが送信される前にアプリケーションでのみ呼び出すことができます、実行時データ列**SQLCancel**、 **SQLGetDiagField**、 **SQLGetDiagRec**、 **SQLGetFunctions**、 **SQLParamData**、または**SQLPutData**ステートメントまたはステートメントに関連付けられた接続。 ステートメントまたはステートメントに関連付けられている接続の他の関数を呼び出して場合、SQL_ERROR と SQLSTATE HY010 関数を返します (関数のシーケンス エラーです)。  
  
 アプリケーションを呼び出す場合**SQLCancel**ドライバーでは、実行時データ列のデータが引き続き必要があります、中にドライバーが操作をキャンセルします。 アプリケーションを呼び出して**SQLSetPos**もう一度; 取り消すには影響しません、カーソルの状態または現在のカーソル位置。  
  
 ドライバーの定義は、ときに、カーソルに関連付けられているクエリ仕様の選択リストには、エラーが生成またはドライバーが重複している参照を無視し、要求された操作を実行するかどうか、同じ列への参照 1 つ以上にはが含まれています。  
  
## <a name="performing-bulk-operations"></a>一括操作を実行します。  
 場合、 *RowNumber*引数が 0 のドライバーで指定された操作を実行する場合、*操作*SQL_ROW_PROCEED の値の行の操作では、そのフィールドである行セット内のすべての行の引数SQL_ATTR_ROW_OPERATION_PTR ステートメント属性が指す配列。 これは、有効な値の*RowNumber*の引数、*操作*SQL_DELETE、SQL_REFRESH、または、SQL_UPDATE がない SQL_POSITION の引数。 **SQLSetPos**で、*操作*SQL_POSITION の*RowNumber* SQLSTATE HY109 0 を返します (無効なカーソルの位置)。  
  
 エラーが発生する場合は、SQLSTATE HYT00 など、行セット全体に関係 (タイムアウトになりました)、ドライバーは SQL_ERROR と適切な SQLSTATE を返します。 行セットのバッファーの内容は未定義、およびカーソルの位置は変更されません。  
  
 エラーが発生する場合は、ドライバー、単一の行に適用されます。  
  
-   SQL_ROW_ERROR にし、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される行の状態配列内の行の要素を設定します。  
  
-   エラー キュー内のエラーの 1 つまたは複数追加 SQLSTATEs を投稿し、診断データ構造で SQL_DIAG_ROW_NUMBER フィールドを設定します。  
  
 処理した後、エラーまたは警告、ドライバーが、行セット内の残りの行の操作を完了すると、SQL_SUCCESS_WITH_INFO が返されます。 そのため、エラーが返される行ごとに、エラー キューには 0 個以上の追加 SQLSTATEs が含まれます。 ドライバーは、エラーまたは警告を処理した後、操作を停止する場合は、SQL_ERROR が返されます。  
  
 ドライバーでは、警告、SQLSTATE 01004 など (データが切り捨てられました) が返された場合、行セット全体にまたは不明な行セットの行に適用すると、特定の行に適用されるエラー情報を返す前に警告を返します。 これらの行に関するその他のエラー情報と共に特定の行に対して警告を返します。  
  
 場合*RowNumber*が 0 と*操作*SQL_UPDATE、SQL_REFRESH、または SQL_DELETE、数の行を**SQLSetPos**動作を SQL_ATTR_ROWS を指しています_FETCHED_PTR ステートメント属性です。  
  
 場合*RowNumber*が 0 と*操作*SQL_DELETE、SQL_REFRESH、または SQL_UPDATE、現在の行の後、操作は、操作の前に、現在の行と同じです。  
  
## <a name="ignoring-a-row-in-a-bulk-operation"></a>一括操作内の行は無視されます。  
 使用して一括操作中に現在の行セット内の行を無視するかを示すために、行操作配列を使用できる**SQLSetPos**します。 一括操作中に 1 つまたは複数の行を無視するドライバーを送信するには、アプリケーションは、次の手順を実行する必要があります。  
  
1.  呼び出す**SQLSetStmtAttr** SQLUSMALLINTs の配列を指す SQL_ATTR_ROW_OPERATION_PTR ステートメント属性を設定します。 このフィールドを呼び出すことによって設定することもできます。 **SQLSetDescField**のアプリケーション記述子ハンドルを取得する必要があります、ARD SQL_DESC_ARRAY_STATUS_PTR ヘッダー フィールドを設定します。  
  
2.  2 つの値のいずれかに、行操作配列の各要素を設定します。  
  
    -   SQL_ROW_IGNORE を一括操作の行が除外されたことを示します。  
  
    -   SQL_ROW_PROCEED、一括操作で行を含めることを示す。 (これは既定値です)。  
  
3.  呼び出す**SQLSetPos**一括操作を実行します。  
  
 次の規則は、行操作配列に適用されます。  
  
-   SQL_ROW_IGNORE と SQL_ROW_PROCEED を使用して一括操作のみに影響**SQLSetPos**で、*操作*SQL_DELETE または SQL_UPDATE の。 呼び出しには影響しません**SQLSetPos**で、*操作*SQL_REFRESH または SQL_POSITION の。  
  
-   ポインターの設定を既定で null にします。  
  
-   ポインターが null の場合は、SQL_ROW_PROCEED にすべての要素が設定された場合とすべての行が更新されます。  
  
-   SQL_ROW_PROCEED に要素を設定しても、操作がその特定の行で発生するとは限りません。 たとえば、行セット内の特定の行に SQL_ROW_ERROR 状態がある場合は、ドライバー可能性があります、アプリケーションが SQL_ROW_PROCEED を指定するかどうかに関係なく、その行が更新できません。 アプリケーションでは、操作が成功したかどうかを表示する行の状態配列を常に確認する必要があります。  
  
-   SQL_ROW_PROCEED はヘッダー ファイルで 0 として定義されます。 アプリケーションでは、すべての行を処理するために、0 行操作配列を初期化できます。  
  
-   SQL_ROW_IGNORE に行操作配列内の要素数"n"が設定されている場合と**SQLSetPos**一括更新を実行または操作呼び出しの後の行セット変わりませんで n 番目の行を削除するために呼び出される**SQLSetPos**.  
  
-   アプリケーションは、SQL_ROW_IGNORE に読み取り専用の列を自動的に設定する必要があります。  
  
## <a name="ignoring-a-column-in-a-bulk-operation"></a>一括操作で列を無視します。  
 1 つまたは複数の読み取り専用の列に実行しようとした更新プログラムによって生成された不要な処理の診断を避けるためには、アプリケーションは SQL_COLUMN_IGNORE にバインドされている長さ/インジケーター バッファーで値を設定できます。 詳細については、次を参照してください。 [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)します。  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションは、ORDERS テーブルを参照し、注文ステータスを更新するユーザーをできます。 カーソルはキーセット ドリブンの行セットのサイズは 20 であり、行のバージョンを比較するオプティミスティック同時実行制御を使用します。 それぞれの行セットをフェッチすると、後に、アプリケーションはそれを出力しを選択し、注文の状態を更新できます。 アプリケーションを使用して**SQLSetPos**に選択した行にカーソルを移動し、行の位置指定更新を実行します。 (エラー処理はわかりやすくするため省略します。)  
  
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
  
 例については、次を参照してください。[配置の更新と削除ステートメント](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)と[SQLSetPos による行セット内の行の更新](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|バッファーを結果セット内の列にバインドします。|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ブロック カーソルの位置に関係なく一括操作を実行します。|[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|ステートメントの処理をキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|データのブロックをフェッチしています。 または、結果をスクロールの設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|記述子の 1 つのフィールドを取得します。|[SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|記述子の複数のフィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|記述子の 1 つのフィールドを設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|記述子の複数のフィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
