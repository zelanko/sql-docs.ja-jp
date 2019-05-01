---
title: SQLBulkOperations 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 06a1997b482c45ea4b529c1230ef1cb2c61dc873
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63237857"
---
# <a name="sqlbulkoperations-function"></a>SQLBulkOperations 関数
**準拠**  
 バージョンが導入されました。ODBC 3.0 規格に準拠します。ODBC  
  
 **まとめ**  
 **SQLBulkOperations**一括挿入や一括ブックマークを実行します。 更新プログラムを含む、操作は、削除、およびブックマークでフェッチします。  
  
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
  
 詳細については、「コメントです。」を参照してください。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NEED_DATA、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLBulkOperations** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得できる**SQLGetDiagRec**で、 *HandleType*のSql_handle_stmt として、*処理*の*StatementHandle*します。 次の表に、によって通常返される SQLSTATE 値**SQLBulkOperations**ですこの関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
 複数行の操作の 1 つ以上のただしすべてではなく行にエラーが発生した場合にエラーが発生した場合、SQL_ERROR が返されますをすべてその SQLSTATEs SQL_SUCCESS_WITH_INFO または SQL_ERROR (を除く 01xxx SQLSTATEs) を返すことができる、SQL_SUCCESS_WITH_INFO が返される、単一行の操作です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データの右側が切り捨てられました|*操作*引数が SQL_FETCH_BY_BOOKMARK、および文字列またはバイナリ データの列またはの SQL_C_CHAR または SQL_C_BINARY データ型を持つ列に対して返される空白でない文字または NULL 以外のバイナリ データの切り捨てが発生しました。|  
|01S01|行内のエラー|*操作*引数は、SQL_ADD と操作の実行中に 1 つまたは複数の行でエラーが発生しましたが、少なくとも 1 つの行が正常に追加します。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。<br /><br /> (このエラーは、アプリケーションは、ODBC 2 の影響を使用する場合にのみ発生します。*x*ドライバー)。|  
|01S07|分数が切り捨てられました|*操作*引数が SQL_FETCH_BY_BOOKMARK、アプリケーションのバッファーのデータ型が SQL_C_CHAR または SQL_C_BINARY、および 1 つまたは複数の列のバッファーをアプリケーションに返されるデータが切り捨てられました。 (数値の C データ型の数値の小数部が切り捨てられました。 時刻、タイムスタンプ、および時刻部分が含まれている interval C データ型の場合は、時間の小数部が切り捨てられました。)<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|*操作*引数が SQL_FETCH_BY_BOOKMARK、し、結果セット内の列のデータ値で指定されたデータ型に変換されませんでした、 *TargetType* への呼び出しで引数**SQLBindCol**します。<br /><br /> *操作*引数が SQL_UPDATE_BY_BOOKMARK または SQL_ADD、およびアプリケーション バッファーのデータ値を結果セット内の列のデータ型に変換できませんでした。|  
|07009|無効な記述子のインデックス|引数*操作*SQL_ADD の列が結果セット内の列の数よりも大きい列番号でバインドされました。|  
|21S02|派生テーブルの次数が列の一覧と一致しません|引数*操作*SQL_UPDATE_BY_BOOKMARK; で、列がない更新可能なすべての列がバインドされていないか読み取り専用、またはバインドされている長さ/インジケーター バッファーの値が SQL_COLUMN_IGNORE のためです。|  
|22001|文字列データの右側が切り捨てられました|文字またはバイナリ値に結果セット内の列の割り当て (文字) の空白または (バイナリ) の null 以外の文字またはバイトの切り捨てが発生しました。|  
|22003|数値が範囲外|*操作*結果セット内の列に数値の値の割り当てが (ではなく小数部) 整数部分が切り捨てられる数を原因し、なった引数が SQL_ADD または SQL_UPDATE_BY_BOOKMARK、します。<br /><br /> 引数*操作*SQL_FETCH_BY_BOOKMARK を 1 つまたは複数のバインドされた列の数値の値を返す原因となる有効桁数が失われる。|  
|22007|無効な datetime 形式|*操作*引数が SQL_ADD または SQL_UPDATE_BY_BOOKMARK、および年、月、または範囲外の日付フィールドに結果セット内の列に日付またはタイムスタンプの値の割り当てが発生します。<br /><br /> 引数*操作*SQL_FETCH_BY_BOOKMARK を 1 つまたは複数のバインドされた列の日付またはタイムスタンプの値を返す原因となる年、月、または範囲外となる日フィールド。|  
|22008|日付/時刻フィールドがオーバーフローしました|*操作*引数が SQL_ADD または SQL_UPDATE_BY_BOOKMARK、および算術演算の結果セット内の列に送信されるデータを datetime のパフォーマンスの結果 (年、月、日、時間、分、または秒を datetime フィールドフィールドのフィールドの値の許容範囲が無効である datetimes のグレゴリオ暦カレンダーの自然なルールに基づいて結果)。<br /><br /> *操作*引数が SQL_FETCH_BY_BOOKMARK、および算術演算の結果セットから取得されるデータを datetime のパフォーマンスの結果の datetime フィールド (年、月、日、時間、分、または 2 番目のフィールド)、結果フィールドの値の許容範囲を以下にあるか、有効なグレゴリオ暦の自然な datetimes 規則に基づきます。|  
|22015|Interval フィールド オーバーフロー|*操作*の正確な数値の割り当てまたは間隔 C 型を間隔の SQL データ型には、有効桁数の損失を原因し、なった引数が SQL_ADD または SQL_UPDATE_BY_BOOKMARK、します。<br /><br /> *操作*引数が SQL_ADD または SQL_UPDATE_BY_BOOKMARK; 間隔 SQL 型に割り当てる際、SQL 型の間隔で C 型の値の表現がなかった。<br /><br /> *操作*引数が SQL_FETCH_BY_BOOKMARK、および先頭のフィールドの有効桁数の損失を原因と正確な numeric または間隔 SQL 型から C の間隔の種類を割り当てることです。<br /><br /> *操作*引数が SQL_FETCH_BY_BOOKMARK; に C の間隔の種類を割り当てるときは、C の間隔の種類の SQL 型の値の表現がなかった。|  
|22018|キャストの無効な文字の値|*操作*引数が SQL_FETCH_BY_BOOKMARK; C 型は、真数または概数の数値、datetime、または間隔のデータ型; 列の SQL 型が文字データ型の; と列の値が、無効ですバインドされた C 型のリテラルです。<br /><br /> 引数*操作*SQL_ADD または SQL_UPDATE_BY_BOOKMARK; SQL 型が、真数または概数の数値、datetime、または間隔のデータ型は C 型が SQL_C_CHAR; と列の値が有効なリテラルのバインドされた SQL 型です。|  
|23000|整合性制約違反|*操作*引数が SQL_ADD、SQL_DELETE_BY_BOOKMARK、または SQL_UPDATE_BY_BOOKMARK、および整合性制約に違反していた。<br /><br /> *操作*引数は、SQL_ADD とバインドされていない列を NOT NULL し、既定値を持たないとして定義します。<br /><br /> *操作*引数が、バインドで指定された長さである SQL_ADD *StrLen_or_IndPtr*バッファーが SQL_COLUMN_IGNORE、および列は、既定値はありませんでした。|  
|24000|カーソル状態が無効|*StatementHandle* 、実行の状態でしたが、結果セットが関連付けられていない、 *StatementHandle*します。|  
|40001|シリアル化エラー|トランザクションが別のトランザクションでリソース デッドロックによりロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を特定できません。|  
|42000|構文エラーまたはアクセス違反|ドライバーによってで要求された操作を実行するために必要な行はロックされませんでした、*操作*引数。|  
|44000|WITH CHECK OPTION 違反|*操作*引数が SQL_ADD または SQL_UPDATE_BY_BOOKMARK、および挿入または更新プログラムが表示されているテーブルに対して実行された (またはテーブルが表示されているテーブルから派生) を指定して作成された**WITH CHECK OPTION**、1 つまたは複数の行の挿入によって影響を受けること、または更新は表示されているテーブル内に存在できなくようにします。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効に、 *StatementHandle*します。 関数が呼び出された、および実行を完了する前に**SQLCancel**または**SQLCancelHandle**が呼び出されて、 *StatementHandle*します。 後でもう一度関数が呼び出された、 *StatementHandle*します。<br /><br /> 関数が呼び出された、および実行を完了する前に**SQLCancel**または**SQLCancelHandle**が呼び出されて、 *StatementHandle*から別のスレッドで、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM) を非同期的に実行中の関数が呼び出された接続ハンドルに関連付けられているため、 *StatementHandle*します。 この非同期関数ではときに実行されている、 **SQLBulkOperations**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に対して呼び出された、 *StatementHandle* SQL_PARAM_DATA_ を返されます。ご利用いただけます。 ストリームのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM)、指定した*StatementHandle*実行の状態ではありませんでした。 最初に呼び出さず、関数が呼び出された**SQLExecDirect**、 **SQLExecute**、またはカタログ関数。<br /><br /> (DM) を非同期的に実行中の関数 (いないこの"1") が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLSetPos**に対して呼び出された、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) ドライバーは ODBC 2、でした。*x*ドライバー、および**SQLBulkOperations**に対して呼び出された、 *StatementHandle*する前に**SQLFetchScroll**または**SQLFetch**が呼び出されました。<br /><br /> (DM) **SQLBulkOperations**後が呼び出された**SQLExtendedFetch**が呼び出されて、 *StatementHandle*します。|  
|HY011|属性を設定できません。|(DM) ドライバーは ODBC 2、でした。*x*ドライバー、および、し、SQL_ATTR_ROW_STATUS_PTR ステートメント属性は、呼び出しの間で設定された**SQLFetch**または**SQLFetchScroll**と**SQLBulkOperations**.|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|*操作*SQL_DATA_AT_EXEC に等しくないが、引数が SQL_ADD または SQL_UPDATE_BY_BOOKMARK; データ値が null ポインターではありませんでした C データ型が SQL_C_BINARY または SQL_C_CHAR; と列の長さの値が 0 未満。、SQL_COLUMN_IGNORE、SQL_NTS、または SQL_NULL_DATA、SQL_LEN_DATA_AT_EXEC_OFFSET 未満。<br /><br /> 長さ/インジケーター バッファーの値が SQL_DATA_AT_EXEC です。SQL 型がいずれかの SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長い形式のデータ ソースに固有のデータ型。SQL_NEED_LONG_DATA_LEN 情報の種類と**SQLGetInfo** "Y"でした。<br /><br /> *操作*引数が SQL_ADD、SQL_ATTR_USE_BOOKMARK ステートメント属性は、SQL_UB_VARIABLE に設定されており、列 0 がの長さはこの結果セットに対してブックマークの最大の長さと等しくありませんでした。 バッファーにバインドされました。 (この長さは、IRD の SQL_DESC_OCTET_LENGTH フィールドで使用できますし、呼び出すことによって取得できる**SQLDescribeCol**、 **SQLColAttribute**、または**SQLGetDescField**)。|  
|HY092|無効な属性の識別子|(DM) の指定された値、*操作*引数が無効です。<br /><br /> *操作*引数が SQL_ADD、SQL_UPDATE_BY_BOOKMARK、または SQL_DELETE_BY_BOOKMARK、および SQL_ATTR_CONCURRENCY のステートメント属性 SQL_CONCUR_READ_ONLY に設定されています。<br /><br /> *操作*引数が SQL_DELETE_BY_BOOKMARK、SQL_FETCH_BY_BOOKMARK、または SQL_UPDATE_BY_BOOKMARK、およびブックマーク列がバインドされていないまたは SQL_UB_OFF に SQL_ATTR_USE_BOOKMARKS ステートメントの属性が設定されました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースがで要求された操作をサポートしていません、*操作*引数。|  
|HYT00|タイムアウトが発生しました|データ ソースには、結果セットが返される前に、クエリのタイムアウト期間が終了しました。 によって、タイムアウト期間が設定されます**SQLSetStmtAttr**で、*属性*SQL_ATTR_QUERY_TIMEOUT の引数。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングは無効です。|通知のモデルを使用すると、常にポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了が呼び出されていません。|通知モードが有効になっている場合、ハンドルでは、前の関数呼び出しに SQL_STILL_EXECUTING が返された場合と**SQLCompleteAsync**後処理を行い、操作を完了するハンドルで呼び出す必要があります。|  
  
## <a name="comments"></a>コメント  
  
> [!CAUTION]  
>  どのようなステートメントの状態について**SQLBulkOperations**呼び出すことができ、ODBC 2 と互換性のために行う必要があります *。x*アプリケーションを参照してください、[ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)付録 g: セクション旧バージョンとの互換性のためのガイドラインをドライバーです。  
  
 アプリケーションを使用して**SQLBulkOperations**ベース テーブルまたは現在のクエリに対応するビューでは、次の操作を実行します。  
  
-   新しい行を追加します。  
  
-   一連の行のブックマークで各の行を識別する場所を更新します。  
  
-   一連の行のブックマークで各の行を識別する場所を削除します。  
  
-   一連の各行が、ブックマークで識別される、行をフェッチします。  
  
 呼び出しの後に**SQLBulkOperations**、ブロック カーソルの位置が定義されていません。 アプリケーションが呼び出される**SQLFetchScroll**カーソル位置を設定します。 アプリケーションを呼び出す必要があります**SQLFetchScroll**でのみ、 *FetchOrientation* SQL_FETCH_FIRST、SQL_FETCH_LAST、SQL_FETCH_ABSOLUTE、または SQL_FETCH_BOOKMARK の引数。 アプリケーションが呼び出す場合、カーソルの位置は定義されません**SQLFetch**または**SQLFetchScroll**で、 *FetchOrientation* SQL_FETCH_PRIOR、SQL_FETCH_NEXT の引数またはSQL_FETCH_RELATIVE します。  
  
 呼び出しによって実行される一括操作で列を無視できる**SQLBulkOperations**への呼び出しで指定された列の長さ/インジケーター バッファーを設定して**SQLBindCol**SQL_COLUMN_IGNORE にします。  
  
 アプリケーションを呼び出すときに、SQL_ATTR_ROW_OPERATION_PTR ステートメント属性を設定する必要はありません**SQLBulkOperations**のため、この関数を使用した一括操作を実行するときに、行が無視されることはできません。  
  
 SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性によって指し示されるバッファーへの呼び出しによって影響を受ける行の数を格納する**SQLBulkOperations**します。  
  
 ときに、*操作*引数は、SQL_ADD または SQL_UPDATE_BY_BOOKMARK と、カーソルに関連付けられているクエリ仕様の選択リストに同じ列への参照 1 つ以上にはが含まれています、これは、ドライバーの定義済みエラーかどうか生成またはドライバーが重複している参照を無視し、要求された操作を実行します。  
  
 使用する方法の詳細についての**SQLBulkOperations**を参照してください[SQLBulkOperations を使ったデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)します。  
  
## <a name="performing-bulk-inserts"></a>一括挿入の実行  
 使用してデータを挿入する**SQLBulkOperations**アプリケーションは、次の一連の手順を実行します。  
  
1.  結果セットを返すクエリを実行します。  
  
2.  SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を挿入する行の数に設定します。  
  
3.  呼び出し**SQLBindCol**を挿入するデータをバインドします。 データは、SQL_ATTR_ROW_ARRAY_SIZE の値と等しいサイズの配列にバインドされます。  
  
    > [!NOTE]  
    >  SQL_ATTR_ROW_ARRAY_SIZE に等しいまたはし、SQL_ATTR_ROW_STATUS_PTR null ポインターである必要がありますし、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される配列のサイズがありますか。  
  
4.  呼び出し**SQLBulkOperations**(*StatementHandle、* SQL_ADD) 挿入を実行します。  
  
5.  アプリケーションが、し、SQL_ATTR_ROW_STATUS_PTR ステートメント属性を設定すると、操作の結果を表示するには、この配列を検査ができます。  
  
 呼び出す前に 0 列にバインドされた場合**SQLBulkOperations**で、*操作*SQL_ADD の引数は、ドライバーは、バインドされた列 0 バッファー値で更新ブックマークの新しく行を挿入します。 これを行うには、アプリケーションする必要がありますが、SQL_ATTR_USE_BOOKMARKS ステートメント属性を設定 SQL_UB_VARIABLE ステートメントを実行する前にします。 (ODBC 2 では復元されません。*x*ドライバー)。  
  
 長い形式のデータは、その SQLBulkOperations、によって呼び出し SQLParamData と SQLPutData を使用して部分に追加できます。 詳細については、この関数の参照の後で"を提供する時間がかかるデータの一括挿入と更新」を参照してください。  
  
 呼び出すアプリケーションの必要はありません**SQLFetch**または**SQLFetchScroll**を呼び出す前に**SQLBulkOperations** (ODBC 2 に対して予定の場合を除く *。x*ドライバー; を参照してください[旧バージョンとの互換性と標準準拠](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md))。  
  
 動作は、ドライバー定義場合**SQLBulkOperations**で、*操作*SQL_ADD の引数が重複する列を含むカーソルで呼び出されます。 ドライバーがドライバーの定義済みの SQLSTATE を返す、追加の結果に表示される最初の列にデータの設定、またはその他のドライバーの定義済みの動作を実行できます。  
  
## <a name="performing-bulk-updates-by-using-bookmarks"></a>ブックマークを使用して一括更新を実行します。  
 ブックマークを使用して一括更新を実行する**SQLBulkOperations**アプリケーションのシーケンスで、次の手順を実行します。  
  
1.  SQL_UB_VARIABLE SQL_ATTR_USE_BOOKMARKS ステートメント属性に設定します。  
  
2.  結果セットを返すクエリを実行します。  
  
3.  SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を更新する行の数に設定します。  
  
4.  呼び出し**SQLBindCol**を更新するデータをバインドします。 データは、SQL_ATTR_ROW_ARRAY_SIZE の値と等しいサイズの配列にバインドされます。 呼び出しも**SQLBindCol**列 0 (ブックマーク列) にバインドします。  
  
5.  コピー配列に更新中に対象の行のブックマークは、0 の列にバインドします。  
  
6.  バインドされたバッファー内のデータを更新します。  
  
    > [!NOTE]  
    >  SQL_ATTR_ROW_ARRAY_SIZE に等しいまたはし、SQL_ATTR_ROW_STATUS_PTR null ポインターである必要がありますし、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される配列のサイズがあります。  
  
7.  呼び出し**SQLBulkOperations**(*StatementHandle、* SQL_UPDATE_BY_BOOKMARK)。  
  
    > [!NOTE]  
    >  アプリケーションが、し、SQL_ATTR_ROW_STATUS_PTR ステートメント属性を設定すると、操作の結果を表示するには、この配列を検査ができます。  
  
8.  必要に応じて呼び出す**SQLBulkOperations**(*StatementHandle*SQL_FETCH_BY_BOOKMARK) データ更新が発生したことを確認する、バインドされたアプリケーションのバッファーをフェッチします。  
  
9. データが更新された場合、ドライバーは SQL_ROW_UPDATED に適切な行の行の状態配列内の値を変更します。  
  
 一括更新によって実行される**SQLBulkOperations**呼び出しを使用して、長い形式のデータを含めることができます**SQLParamData**と**SQLPutData**します。 詳細については、この関数の参照の後で"を提供する時間がかかるデータの一括挿入と更新」を参照してください。  
  
 アプリケーションを呼び出す必要はない場合、ブックマークは、カーソルによって維持、 **SQLFetch**または**SQLFetchScroll**ブックマークを更新する前にします。 前のカーソル位置からに格納されているブックマークを使用できます。 ブックマークは、カーソルの間で保持はされないアプリケーションは、呼び出す**SQLFetch**または**SQLFetchScroll**ブックマークを取得します。  
  
 動作は、ドライバー定義場合**SQLBulkOperations**で、*操作*SQL_UPDATE_BY_BOOKMARK の引数が重複する列を含むカーソルで呼び出されます。 ドライバーはドライバーの定義済みの SQLSTATE を返す、結果セットに表示される最初の列を更新または他のドライバーの定義済みの動作を実行します。  
  
## <a name="performing-bulk-fetches-using-bookmarks"></a>ブックマークを使用してフェッチ一括を実行します。  
 ブックマークを使用して一括フェッチを実行する**SQLBulkOperations**アプリケーションのシーケンスで、次の手順を実行します。  
  
1.  SQL_UB_VARIABLE SQL_ATTR_USE_BOOKMARKS ステートメント属性に設定します。  
  
2.  結果セットを返すクエリを実行します。  
  
3.  SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性をフェッチする行の数に設定します。  
  
4.  呼び出し**SQLBindCol**をフェッチするデータをバインドします。 データは、SQL_ATTR_ROW_ARRAY_SIZE の値と等しいサイズの配列にバインドされます。 呼び出しも**SQLBindCol**列 0 (ブックマーク列) にバインドします。  
  
5.  コピー配列へのフェッチで対象の行のブックマークは、0 の列にバインドします。 (これは前提アプリケーションが、ブックマークを個別に取得して既にいる。)  
  
    > [!NOTE]  
    >  SQL_ATTR_ROW_ARRAY_SIZE に等しいまたはし、SQL_ATTR_ROW_STATUS_PTR null ポインターである必要がありますし、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される配列のサイズがあります。  
  
6.  呼び出し**SQLBulkOperations**(*StatementHandle、* SQL_FETCH_BY_BOOKMARK)。  
  
7.  アプリケーションが、し、SQL_ATTR_ROW_STATUS_PTR ステートメント属性を設定すると、操作の結果を表示するには、この配列を検査ができます。  
  
 アプリケーションを呼び出す必要はない場合、ブックマークは、カーソルによって維持、 **SQLFetch**または**SQLFetchScroll**ブックマークでフェッチする前にします。 前のカーソル位置からに格納されているブックマークを使用できます。 ブックマークは、カーソルの間で保持はされないアプリケーションは、呼び出す**SQLFetch**または**SQLFetchScroll**ブックマークを取得する 1 つの時間。  
  
## <a name="performing-bulk-deletes-using-bookmarks"></a>一括を実行するには、ブックマークの使用が削除されます。  
 ブックマークを使用して一括削除を実行する**SQLBulkOperations**アプリケーションのシーケンスで、次の手順を実行します。  
  
1.  SQL_UB_VARIABLE SQL_ATTR_USE_BOOKMARKS ステートメント属性に設定します。  
  
2.  結果セットを返すクエリを実行します。  
  
3.  SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性を削除する行の数に設定します。  
  
4.  呼び出し**SQLBindCol**列 0 (ブックマーク列) にバインドします。  
  
5.  コピー配列の削除中に対象の行のブックマークは、0 の列にバインドします。  
  
    > [!NOTE]  
    >  SQL_ATTR_ROW_ARRAY_SIZE に等しいまたはし、SQL_ATTR_ROW_STATUS_PTR null ポインターである必要がありますし、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示される配列のサイズがあります。  
  
6.  呼び出し**SQLBulkOperations**(*StatementHandle、* SQL_DELETE_BY_BOOKMARK)。  
  
7.  アプリケーションが、し、SQL_ATTR_ROW_STATUS_PTR ステートメント属性を設定すると、操作の結果を表示するには、この配列を検査ができます。  
  
 呼び出すアプリケーションがいない場合、ブックマークは、カーソルによって維持、 **SQLFetch**または**SQLFetchScroll**ブックマークを削除する前にします。 前のカーソル位置からに格納されているブックマークを使用できます。 ブックマークは、カーソルの間で保持はされないアプリケーションは、呼び出す**SQLFetch**または**SQLFetchScroll**ブックマークを取得する 1 つの時間。  
  
## <a name="providing-long-data-for-bulk-inserts-and-updates"></a>一括挿入と更新プログラムの長い形式のデータを提供します。  
 一括挿入と更新プログラムの呼び出しで実行された長い形式のデータを指定することができます**SQLBulkOperations**します。 を挿入または更新の長い形式のデータには、アプリケーションは、このトピックの「一括挿入を実行する」と「を実行する一括更新を使用してブックマーク」のセクションで説明されている手順に加え、次の手順を実行します。  
  
1.  使用して、データをバインドに**SQLBindCol**、アプリケーションの場所での列番号などのアプリケーション定義の値、  *\*TargetValuePtr*実行時のデータのバッファー列です。 値は、列を識別するために後で使用できます。  
  
     アプリケーションの場所の結果、SQL_LEN_DATA_AT_EXEC (*長さ*) マクロで、  *\*StrLen_or_IndPtr*バッファー。 列の SQL データ型は SQL_LONGVARBINARY、SQL_LONGVARCHAR、または長い形式のデータ ソースに固有のデータ型と、ドライバーで SQL_NEED_LONG_DATA_LEN 情報の種類に"Y"を返す場合**SQLGetInfo**、*長さ* ; パラメーターに送信されるデータのバイト数は、それ以外の場合、負以外の値を指定する必要があり、無視されます。  
  
2.  ときに**SQLBulkOperations**を呼び出す場合は、実行時データ列、関数の戻り値 SQL_NEED_DATA およびに依存して手順 3. に進みます。 (実行時データ列がない場合、プロセスが完了しました。)  
  
3.  アプリケーション呼び出し**SQLParamData**のアドレスを取得する、  *\*TargetValuePtr*処理する最初の実行時データ列のバッファー。 **SQLParamData** SQL_NEED_DATA を返します。 アプリケーションからのアプリケーション定義の値を取得する、  *\*TargetValuePtr*バッファー。  
  
    > [!NOTE]  
    >  値がによって返される実行時データ パラメーターには、実行時データ列が似ています、 **SQLParamData**はそれぞれ異なります。  
  
     実行時データ列は列のデータを送信行セットで**SQLPutData**行が更新または挿入**SQLBulkOperations**します。 バインドされている**SQLBindCol**します。 によって返される値**SQLParamData**内の行のアドレスは、**TargetValuePtr*が処理されているバッファー。  
  
4.  アプリケーション呼び出し**SQLPutData**列のデータを送信する 1 つ以上の時間。 すべてのデータ値を返すことができない場合は、複数の呼び出しが必要な *\*TargetValuePtr*で指定されたバッファー **SQLPutData**; を複数回呼び出す**SQLPutData**文字、バイナリ、またはデータのソースに固有のデータ型の列に文字データを送信するときにのみ、または列が文字、バイナリ、C のバイナリ データを送信するときに、同じ列が許可されるか、データ ソースに固有のデータを入力します。  
  
5.  アプリケーション呼び出し**SQLParamData**列のすべてのデータが送信されたことを通知するには、もう一度です。  
  
    -   多くの実行時データ列がある場合**SQLParamData** SQL_NEED_DATA およびのアドレスを返します、 *TargetValuePtr*処理する次の実行時データ列のバッファー。 アプリケーションでは、手順 4. と 5. を繰り返します。  
  
    -   これ以上の実行時データ列がある場合は、プロセスが完了しました。 ステートメントが正常に実行された場合**SQLParamData** SQL_SUCCESS、SQL_SUCCESS_WITH_INFO; を返します、実行に失敗しました、SQL_ERROR が返されます。 この時点では、 **SQLParamData**によって返される任意の SQLSTATE を返すことができます**SQLBulkOperations**します。  
  
 操作が取り消されたかどうか、またはエラーが発生**SQLParamData**または**SQLPutData**後**SQLBulkOperations** SQL_NEED_DATA を返しますのすべてのデータが送信される前にアプリケーションでのみ呼び出すことができます、実行時データ列**SQLCancel**、 **SQLGetDiagField**、 **SQLGetDiagRec**、 **SQLGetFunctions**、 **SQLParamData**、または**SQLPutData**ステートメントまたはステートメントに関連付けられた接続。 ステートメントまたはステートメントに関連付けられている接続の他の関数を呼び出して場合、SQL_ERROR と SQLSTATE HY010 関数を返します (関数のシーケンス エラーです)。  
  
 アプリケーションを呼び出す場合**SQLCancel**ドライバーでは、実行時データ列のデータが引き続き必要があります、中にドライバーが操作をキャンセルします。 アプリケーションを呼び出して**SQLBulkOperations**もう一度; 取り消すには影響しません、カーソルの状態または現在のカーソル位置。  
  
## <a name="row-status-array"></a>行の状態の配列  
 行の状態配列が呼び出しの後に、行セット内のデータの行ごとの状態の値を含む**SQLBulkOperations**します。 ドライバーは、呼び出しの後にこの配列の状態の値を設定**SQLFetch**、 **SQLFetchScroll**、 **SQLSetPos**、または**SQLBulkOperations**. この配列は、最初にへの呼び出しによって設定されます**SQLBulkOperations**場合**SQLFetch**または**SQLFetchScroll**が前に呼び出されていない**SQLBulkOperations。**. この配列は、し、SQL_ATTR_ROW_STATUS_PTR ステートメント属性を指しています。 行の状態配列内の要素の数は、(、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性で定義) された行セット内の行の数に等しくなければなりません。 この行の状態配列については、次を参照してください。 [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)します。  
  
## <a name="code-example"></a>コード例  
 次の例では、Customers テーブルから、一度に 10 行のデータをフェッチします。 次にユーザーのアクションを実行するように求めます。 ネットワーク トラフィックを減らすためには、例のバッファーは更新、削除、およびローカル バインドの配列では、以前の行セットのデータのオフセット位置に挿入します。 コードがオフセットが適切にバインドを設定し、呼び出すユーザーは、更新、削除、送信することを選択し、データ ソースに挿入、 **SQLBulkOperations**します。 わかりやすくするため、ユーザーは、10 個を超える更新、削除、または挿入バッファーことはできません。  
  
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
|バッファーを結果セット内の列にバインドします。|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理をキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|データのブロックをフェッチしています。 または、結果をスクロールの設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|記述子の 1 つのフィールドを取得します。|[SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|記述子の複数のフィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|記述子の 1 つのフィールドを設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|記述子の複数のフィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|カーソルを配置するか、行セットでデータを更新、更新、または行セット内のデータを削除します。|[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
