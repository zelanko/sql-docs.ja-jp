---
title: 関数の設定 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetPos
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetPos
helpviewer_keywords:
- SQLSetPos function [ODBC]
ms.assetid: 80190ee7-ae3b-45e5-92a9-693eb558f322
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7a8839f1ae540ac9e5f29e144f7f57fb754e50ff
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287332"
---
# <a name="sqlsetpos-function"></a>SQLSetPos 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: ODBC  
  
 **まとめ**  
 **SQLSetPos**は、行セット内のカーソル位置を設定し、アプリケーションが行セット内のデータを更新したり、結果セット内のデータを更新または削除できるようにします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLSetPos(  
      SQLHSTMT        StatementHandle,  
      SQLSETPOSIROW   RowNumber,  
      SQLUSMALLINT    Operation,  
      SQLUSMALLINT    LockType);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *行番号*  
 [入力]*引数 Operation*で指定された操作を実行する行セット内の行の位置。 *RowNumber が*0 の場合、この操作は行セット内のすべての行に適用されます。  
  
 詳細については、「コメント」を参照してください。  
  
 *Operation*  
 [入力]実行する操作:  
  
 SQL_UPDATE SQL_DELETESQL_POSITIONSQL_REFRESH  
  
> [!NOTE]
>  ODBC *3.x*では *、演算*引数のSQL_ADD値は非推奨になりました。 ODBC *3.x*ドライバは、下位互換性を保つためにSQL_ADDをサポートする必要があります。 この機能は、SQL_ADDの*操作*を使用した**SQLBulkOperations**の呼び出しに置き換えられました。 ODBC *3.x*アプリケーションが ODBC *2.x*ドライバーと連携する場合、ドライバー マネージャーは、SQL_ADDの*操作*を使用して**SQLSetPos** *Operation*にSQL_ADD操作を使用して**SQLBulkOperations**への呼び出しをマップします。  
  
 詳細については、「コメント」を参照してください。  
  
 *LockType*  
 [入力]*引数 Operation*で指定された操作を実行した後に行をロックする方法を指定します。  
  
 SQL_LOCK_EXCLUSIVESQL_LOCK_UNLOCKSQL_LOCK_NO_CHANGE  
  
 詳細については、「コメント」を参照してください。  
  
 **戻り値**  
  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NEED_DATA、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLSetPos**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときに、関連付けられた SQLSTATE 値を取得するには、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出します。 次の表は **、SQLSetPos**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
 SQL_SUCCESS_WITH_INFOまたはSQL_ERRORを返すことができるすべての SQLSTATE (01xxx SQLSTATE を除く) では、複数行操作の 1 つ以上の行でエラーが発生した場合はSQL_SUCCESS_WITH_INFOが返され、単一行操作でエラーが発生した場合はSQL_ERRORが返されます。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01001|カーソル操作の競合|*引数 Operation*がSQL_DELETEまたはSQL_UPDATEされ、削除または更新された行または行が 1 つもありません。 (複数の行に対する更新の詳細については **、SQLSetStmtAttr**のSQL_ATTR_SIMULATE_CURSOR*属性*の説明を参照してください。(関数はSQL_SUCCESS_WITH_INFOを返します。<br /><br /> *Operation*引数がSQL_DELETEまたはSQL_UPDATEされ、オプティミスティック同時実行制御のために操作が失敗しました。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データの右切り捨て|*引数が*SQL_REFRESHされ、データ型が SQL_C_CHAR またはSQL_C_BINARYの列に対して返された文字列またはバイナリ データは、空白以外の文字または NULL 以外のバイナリ データの切り捨て結果になりました。|  
|01S01|行内エラー|*引数 RowNumber*が 0 で、*引数 Operation*で指定された操作を実行しているときに 1 つ以上の行でエラーが発生しました。<br /><br /> (SQL_SUCCESS_WITH_INFOは、複数行操作の 1 つ以上の行でエラーが発生した場合に返され、単一行操作でエラーが発生した場合はSQL_ERROR返されます。<br /><br /> (この SQLSTATE は、ドライバーが ODBC *2.x*ドライバーであり、カーソル ライブラリが使用されていない場合は **、SQLExtendedFetch**の後に**SQLSetPos**が呼び出された場合にのみ返されます。|  
|01S07|分数切り捨て|*引数 Operation*がSQL_REFRESHされ、アプリケーション バッファーのデータ型がSQL_C_CHARまたはSQL_C_BINARYされず、1 つ以上の列のアプリケーション バッファに返されたデータが切り捨てられました。 数値データ型の場合、数値の小数部分は切り捨てられました。 時間、タイム・スタンプ、および時間コンポーネントを含む間隔データ・タイプの場合、時間の小数部分は切り捨てられました。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07006|制限付きデータ型属性違反|結果セット内の列のデータ値を **、SQLBindCol**の呼び出しで*TargetType*で指定されたデータ型に変換できませんでした。|  
|07009|記述子インデックスが無効です|引数*Operation*がSQL_REFRESHまたはSQL_UPDATEされ、列が結果セット内の列数より大きい列番号でバインドされました。|  
|21S02|派生テーブルの次数が列リストと一致しません|引数*Operation*がSQL_UPDATEされ、すべての列が非バインド、読み取り専用、またはバインドされた長さ/インジケーター バッファーの値がSQL_COLUMN_IGNOREされたため、列は更新できませんでした。|  
|22001|文字列データ、右切り捨て|*Operation*引数がSQL_UPDATEされ、列に文字またはバイナリー値を割り当てると、ブランク以外の文字 (文字の場合) または非 NULL (バイナリーの場合) 文字またはバイトが切り捨てられました。|  
|22003|範囲外の数値|引数*Operation*がSQL_UPDATEされ、結果セット内の列に数値を割り当てると、数値の整数部分 (小数部ではなく) が切り捨てられました。<br /><br /> 引数*Operation*がSQL_REFRESHされ、1 つ以上のバインドされた列の数値を返すと、有効桁数が失われる可能性があります。|  
|22007|日付/時刻形式が無効です|引数*Operation*がSQL_UPDATEされ、結果セット内の列に日付またはタイム・スタンプ値が割り当てられた場合、年、月、または日のフィールドが範囲外になります。<br /><br /> 引数*Operation*がSQL_REFRESHされ、1 つ以上のバインドされた列の日付またはタイムスタンプ値を返すと、年、月、または日のフィールドが範囲外になります。|  
|22008|日付/時刻フィールドのオーバーフロー|*引数の演算*がSQL_UPDATEされ、結果セット内の列に送信されるデータに対する日時演算のパフォーマンスが、結果がフィールドの許容範囲外にあるか、グレゴリオ暦の自然な日付時刻規則に基づいて無効であったりする結果が、日付時刻フィールド (年、月、日、時、分、秒) に設定されました。<br /><br /> *引数が*SQL_REFRESHされ、結果セットから取得されるデータに対する日時演算のパフォーマンスが、結果がフィールドの許容範囲外にある場合や、グレゴリオ暦の日付時刻に対する自然な規則に基づいて無効であった場合に、結果として日付時刻フィールド (年、月、日、時、分、秒) が発生しました。|  
|22015|間隔フィールドのオーバーフロー|*Operation*引数がSQL_UPDATEされ、正確な数値または間隔 C 型を間隔 SQL データ型に割り当てると、有効桁数が失われました。<br /><br /> *演算*引数はSQL_UPDATE。間隔 SQL タイプに割り当てるときに、間隔 SQL タイプの C 型の値の表現が存在しません。<br /><br /> *Operation*引数がSQL_REFRESHされ、正確な数値または間隔の SQL タイプから間隔 C タイプに割り当てると、先行フィールドの有効桁数が失われました。<br /><br /> *演算*引数は REFRESH SQL_。インターバル C タイプに割り当てるとき、間隔 C 型の SQL タイプの値の表現はありませんでした。|  
|22018|キャスト指定に無効な文字値|*演算*引数はSQL_REFRESH。C 型は、正確な数値または概算数値、日時、または間隔データ型でした。列の SQL 型は文字データ型でした。列の値が、バインドされた C 型の有効なリテラルではありません。<br /><br /> 引数*操作*はSQL_UPDATE。SQL タイプは、正確または概数、日時、または間隔データ型でした。C 型はSQL_C_CHAR。列の値がバインドされた SQL 型の有効なリテラルではありません。|  
|23000|整合性制約違反|引数*Operation*は SQL_DELETE または SQL_UPDATEで、整合性制約に違反しました。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*は実行済み状態でしたが、結果セットはステートメント ハンドルに関連付*けられません*。<br /><br /> (DM)*ステートメント ハンドル*でカーソルが開かれていたが、SQLFetch または**SQLFetchScroll** **が**呼び出されていません。<br /><br /> *ステートメント ハンドル*でカーソルが開かれて、SQLFetch または**SQLFetchScroll**が呼び出されましたが、カーソルは結果セットの開始前または結果セットの終了後に配置されました。 **SQLFetchScroll**<br /><br /> 引数*Operation*がSQL_DELETE、SQL_REFRESH、またはSQL_UPDATEで、カーソルが結果セットの開始前または結果セットの終了後に位置付けされました。|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|42000|構文エラーまたはアクセス違反|ドライバは、引数*Operation*で要求された操作を実行するために必要な行をロックできませんでした。<br /><br /> ドライバは、引数*LockType*で要求されたとおりに行をロックできませんでした。|  
|44000|WITH CHECK OPTION 違反|*Operation*引数がSQL_UPDATEされ、更新の影響を受ける 1 つ以上の行が表示テーブルに存在しないように **、WITH CHECK OPTION**を指定して作成されたビュー テーブルまたはビュー テーブルから派生したテーブルに対して更新が実行されました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、ステートメント ハンドルで**SQLCancel**または**SQLCancelHandle**が呼び出された後、*ステートメント ハンドル*で関数が再度呼び出されました。 *StatementHandle*<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は、SQLSetPos 関数が呼び出されたときに実行されていました。<br /><br /> (DM) 指定された*ステートメント ハンドル*が実行状態にありません。 関数は、最初に呼び出**さずに****呼**び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM) ドライバーは ODBC *2.x*ドライバーであり **、SQL フェッチ**が呼び出された後にステートメント*ハンドル*に対して**SQLSetPos**が呼び出されました。|  
|HY011|属性を今設定できません|(DM) ドライバは ODBC *2.x*ドライバでした。SQL_ATTR_ROW_STATUS_PTRステートメント属性が設定されました。その後 **、SQL フェッチ** **SQLFetch** **、SQL フェッチスクロール**、または**SQL エクステンドフェッチ**が呼び出される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|*引数が*SQL_UPDATE、データ値が null ポインター、列長の値が 0、SQL_DATA_AT_EXEC、SQL_COLUMN_IGNORE、SQL_NULL_DATA、または SQL_LEN_DATA_AT_EXEC_OFFSET 以下であった。<br /><br /> *演算*引数はSQL_UPDATE。データ値が NULL ポインタではありませんでした。C データ型がSQL_C_BINARYまたはSQL_C_CHAR。列の長さの値が 0 未満であったが、SQL_DATA_AT_EXEC、SQL_COLUMN_IGNORE、SQL_NTS、またはSQL_NULL_DATAに等しくないか、またはSQL_LEN_DATA_AT_EXEC_OFFSET以下であった。<br /><br /> 長さ/インジケーター バッファーの値はSQL_DATA_AT_EXEC。SQL 型は、SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長いデータ ソース固有のデータ型です。**SQLGetInfo**のSQL_NEED_LONG_DATA_LEN情報の種類は "Y" でした。|  
|HY092|無効な属性識別子|(DM)*演算*引数に指定された値が無効です。<br /><br /> (DM)*引数 LockType*に指定された値が無効です。<br /><br /> *引数 Operation*がSQL_UPDATEまたはSQL_DELETEされ、SQL_ATTR_CONCURRENCY ステートメント属性がSQL_ATTR_CONCUR_READ_ONLYされました。|  
|HY107|行の値が範囲外です|*引数 RowNumber*に指定された値が、行セットの行数より大きかった。|  
|HY109|カーソル位置が無効です|*ステートメント ハンドル*に関連付けられたカーソルが前方専用として定義されていたため、カーソルを行セット内に配置できませんでした。 **SQLSetStmtAttr**のSQL_ATTR_CURSOR_TYPE属性の説明を参照してください。<br /><br /> *引数が*SQL_UPDATE、SQL_DELETE、またはSQL_REFRESHされ *、RowNumber*引数によって識別された行が削除されたか、フェッチされていません。<br /><br /> (DM)*引数 RowNumber*が 0 で、*演算*引数がSQL_POSITION。<br /><br /> **SQL データセットが**呼び出されたのは **、SQL の一括操作**が呼び出された後、および**SQL フェッチスクロール**または**SQL フェッチ**が呼び出される前に呼び出されました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|ドライバーまたはデータ ソースは、*操作*引数または*LockType*引数で要求された操作をサポートしていません。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが結果セットを返しました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUTの*属性*を持つ**SQLSetStmtAttr**を使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
  
> [!CAUTION]
>  **SQLSetPos**を呼び出すことができるステートメントの状態と ODBC *2.x*アプリケーションとの互換性のために必要な処理については、「[ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)」を参照してください。  
  
## <a name="rownumber-argument"></a>行番号の引数  
 *RowNumber*引数は *、Operation*引数で指定された操作を実行する行セットの行番号を指定します。 *RowNumber が*0 の場合、この操作は行セット内のすべての行に適用されます。 *RowNumber は*、0 から行セットの行数までの値である必要があります。  
  
> [!NOTE]  
>  C 言語では、配列は 0 から *、RowNumber*引数は 1 からなります。 たとえば、行セットの 5 行目を更新するには、アプリケーションは配列インデックス 4 の行セット バッファーを変更しますが *、RowNumber 5*を指定します。  
  
 すべての操作は *、RowNumber*で指定された行にカーソルを置きます。 以下の操作にはカーソル位置が必要です。  
  
-   位置指定更新および削除ステートメント。  
  
-   を呼び出**します**。  
  
-   SQL_DELETE、SQL_REFRESH、およびSQL_UPDATEオプションを指定して**SQLSetPos**を呼び出します。  
  
 たとえば、SQL_DELETE*の操作*を使用して**SQLSetPos**を呼び出す場合*に RowNumber*が 2 の場合、カーソルは行セットの 2 行目に位置し、その行は削除されます。 2 行目の実装行ステータス配列 (SQL_ATTR_ROW_STATUS_PTRステートメント属性で示される) のエントリがSQL_ROW_DELETEDに変更されます。  
  
 アプリケーションは **、 SQLSetPos**を呼び出すときにカーソル位置を指定できます。 通常、SQL_POSITIONまたはSQL_REFRESH操作を使用して**SQLSetPos**を呼び出して、位置指定された更新または削除ステートメントを実行するか **、SQLGetData**を呼び出す前にカーソルを配置します。  
  
## <a name="operation-argument"></a>操作の引数  
 *Operation*引数は、次の操作をサポートします。 データ ソースでサポートされるオプションを決定するために、アプリケーションは、(カーソルの種類に応じて) SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、またはSQL_STATIC_CURSOR_ATTRIBUTES1情報の種類を指定して**SQLGetInfo**を呼び出します。  
  
|*Operation*<br /><br /> 引数|Operation|  
|------------------------------|---------------|  
|SQL_POSITION|ドライバは *、RowNumber*で指定された行にカーソルを移動します。<br /><br /> SQL_ATTR_ROW_OPERATION_PTR ステートメント属性によって示される行の状態配列の内容は、SQL_POSITION*操作*では無視されます。|  
|SQL_REFRESH|ドライバーは *、RowNumber*で指定された行にカーソルを配置し、その行の行セット バッファー内のデータを更新します。 ドライバーが行セット バッファー内のデータを返す方法の詳細については、 **SQLBindCol**の行方向および列方向のバインディングの説明を参照してください。<br /><br /> SQL_REFRESH*の操作*を使用した**SQLSetPos**は、現在フェッチされた行セット内の行の状態と内容を更新します。 これには、ブックマークの更新も含まれます。 バッファー内のデータは更新されますが、再フェッチされないため、行セットのメンバーシップは固定されます。 これは、SQL_FETCH_RELATIVEの FetchOrientation と 0 に等しい*RowNumber*を使用した**SQLFetchScroll**の呼び出しによって実行される更新とは異なり、ドライバーとカーソルでサポートされている操作が追加されたデータを表示し、削除されたデータを削除できるように、結果セットから行セットを再フェッチします。 *FetchOrientation*<br /><br /> **SQLSetPos**での更新が正常に行われると、行の状態は変更SQL_ROW_DELETED。 行セット内で削除された行は、次のフェッチまで削除済みとしてマークされ続けます。 カーソルがパッキングをサポートしている場合 (後続の SQLFetch または**SQLFetchScroll**が削除された行を返さない) 場合、次の**フェッチ**時に行は表示されなくなります。<br /><br /> 追加された行は **、SQLSetPos**を使用して更新を実行するときに表示されません。 この動作は、SQL_FETCH_RELATIVEの FetchType と*RowNumber*が 0 の**SQLFetchScroll**とは異なり、現在の行セットも更新されますが、追加されたレコードが表示されるか、これらの操作がカーソルでサポートされている場合は削除されたレコードがパックされます。 *FetchType*<br /><br /> **SQLSetPos**を使用して正常に更新すると、行の状態がSQL_ROW_SUCCESSにSQL_ROW_ADDEDの行の状態が変更されます (行の状態配列が存在する場合)。<br /><br /> **SQLSetPos**を使用して正常に更新すると、行の状態がSQL_ROW_UPDATED行の新しい状態に変更されます (行の状態配列が存在する場合)。<br /><br /> 行に対する**SQLSetPos**操作でエラーが発生した場合、行の状態はSQL_ROW_ERRORに設定されます (行の状態配列が存在する場合)。<br /><br /> SQL_CONCUR_ROWVERまたはSQL_CONCUR_VALUESのSQL_ATTR_CONCURRENCYステートメント属性で開かれたカーソルの場合 **、SQLSetPos**を使用した更新では、データ ソースが使用するオプティミスティック同時実行制御値を更新して、行が変更されたことを検出する場合があります。 この場合、カーソルの同時実行性を確保するために使用される行のバージョンまたは値は、行セット バッファーがサーバーから更新されるたびに更新されます。 これは、更新された各行に対して発生します。<br /><br /> SQL_REFRESH*の操作*では、SQL_ATTR_ROW_OPERATION_PTR ステートメント属性によって示される行の状態配列の内容は無視されます。|  
|SQL_UPDATE|ドライバーは *、行番号*で指定された行にカーソルを配置し、行セット バッファー内の値を使用してデータの基になる行を更新します **(SQLBindCol**の*TargetValuePtr*引数)。 長さ/インジケーター バッファー **(SQLBindCol**の*StrLen_or_IndPtr*引数) からデータの長さを取得します。 列の長さがSQL_COLUMN_IGNORE場合、その列は更新されません。 行を更新した後、ドライバーは行の状態配列の対応する要素をSQL_ROW_UPDATEDまたはSQL_ROW_SUCCESS_WITH_INFO (行の状態配列が存在する場合) に変更します。<br /><br /> これは、SQL_UPDATEの*操作*引数を持つ**SQLSetPos**が重複する列を含むカーソルで呼び出された場合の動作をドライバー定義です。 ドライバーは、ドライバー定義の SQLSTATE を返す、結果セットに表示される最初の列を更新したり、その他のドライバー定義の動作を実行できます。<br /><br /> SQL_ATTR_ROW_OPERATION_PTR ステートメント属性によって示される行操作配列を使用して、一括更新時に現在の行セット内の行を無視することを示すことができます。 詳細については、後の「状態と操作の配列」を参照してください。|  
|SQL_DELETE|ドライバーは *、RowNumber*で指定された行にカーソルを配置し、データの基になる行を削除します。 行ステータス配列の対応する要素をSQL_ROW_DELETEDに変更します。 行が削除された後は、位置指定更新および削除ステートメント **、SQLGetData**の呼び出し、および*SQL_POSITION*以外の操作を行う**SQLSetPos**の呼び出しは、行に対して無効になります。 パッキングをサポートするドライバーの場合、新しいデータがデータ ソースから取得されるときに、カーソルから行が削除されます。<br /><br /> 行が可視のままであるかどうかは、カーソルの種類によって異なります。 たとえば、削除された行は静的カーソルとキーセット ドリブン カーソルでは可視ですが、動的カーソルには表示されません。<br /><br /> SQL_ATTR_ROW_OPERATION_PTR ステートメント属性によって示される行操作配列を使用して、一括削除時に現在の行セット内の行を無視することを示すことができます。 詳細については、後の「状態と操作の配列」を参照してください。|  
  
## <a name="locktype-argument"></a>ロックタイプ引数  
 *LockType*引数は、アプリケーションが同時実行を制御する方法を提供します。 ほとんどの場合、同時実行レベルとトランザクションをサポートするデータ ソースは *、LockType*引数のSQL_LOCK_NO_CHANGE値のみをサポートします。 *LockType*引数は、通常、ファイル ベースのサポートにのみ使用されます。  
  
 *LockType*引数は **、SQLSetPos**が実行された後の行のロック状態を指定します。 ドライバーは、要求された操作を実行したり *、LockType*引数を満たすために、行をロックできない場合は、SQL_ERRORと SQLSTATE 42000 (構文エラーまたはアクセス違反) を返します。  
  
 *LockType*引数は 1 つのステートメントに対して指定されますが、ロックは接続上のすべてのステートメントに対して同じ特権を付与します。 特に、ある接続上の 1 つのステートメントによって獲得されたロックは、同じ接続上の別のステートメントによってロック解除できます。  
  
 **SQLSetPos**を介してロックされた行は、アプリケーションが SQL_LOCK_UNLOCK に設定された*LockType*の行に対して**SQLSetPos**を呼び出すか、またはアプリケーションがSQL_CLOSE オプションを指定してステートメントまたは**SQLFreeStmt**を呼び出すまで、ロックされたままになります。 **SQLFreeHandle** トランザクションをサポートするドライバーの場合 **、SQLSetPos**を通じてロックされた行は、アプリケーションが接続上のトランザクションをコミットまたはロールバックするために**SQLEndTran**を呼び出すとロック解除されます **(SQL_CURSOR_COMMIT_BEHAVIOR**および SQL_CURSOR_ROLLBACK_BEHAVIOR情報の種類によって示されるように、トランザクションがコミットまたはロールバックされたときにカーソルが閉じられた場合)。  
  
 *LockType*引数は、次の種類のロックをサポートします。 データ ソースでサポートされているロックを確認するために、アプリケーションは、(カーソルの種類に応じて) SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、またはSQL_STATIC_CURSOR_ATTRIBUTES1情報の種類を指定して**SQLGetInfo**を呼び出します。  
  
|*ロックタイプ*引数|ロックの種類|  
|-------------------------|---------------|  
|SQL_LOCK_NO_CHANGE|ドライバーまたはデータ ソースは、行が**SQLSetPos**が呼び出される前と同じロック状態またはロック解除された状態であることを確認します。 *LockType*のこの値を使用すると、明示的な行レベルのロックをサポートしていないデータ ソースは、現在の同時実行性レベルとトランザクション分離レベルで必要なロックを使用できます。|  
|SQL_LOCK_EXCLUSIVE|ドライバーまたはデータ ソースは、行を排他的にロックします。 別の接続上のステートメントまたは別のアプリケーションのステートメントを使用して、行のロックを取得することはできません。|  
|SQL_LOCK_UNLOCK|ドライバまたはデータ ソースが行のロックを解除します。|  
  
 ドライバーがSQL_LOCK_EXCLUSIVEをサポートしていない場合SQL_LOCK_UNLOCK、ロックされている行は、前の段落で説明した関数呼び出しのいずれかが発生するまでロックされたままになります。  
  
 ドライバーがSQL_LOCK_EXCLUSIVEをサポートしているが、SQL_LOCK_UNLOCKをサポートしていない場合、ロックされている行は、アプリケーションがステートメントの**SQLFreeHandle**を呼び出すか、SQL_CLOSE オプションを指定して**SQLFreeStmt**を呼び出すまでロックされたままになります。 ドライバーがトランザクションをサポートし、トランザクションのコミットまたはロールバック時にカーソルを閉じる場合、アプリケーションは**SQLEndTran**を呼び出します。  
  
 **SQLSetPos**での更新および削除操作では、アプリケーションは次のように*LockType*引数を使用します。  
  
-   行が取得された後に変更されないことを保証するために、アプリケーションは、操作をSQL_REFRESH*に設定し**、LockType*を SQL_LOCK_EXCLUSIVE に設定して**SQLSetPos**を呼び出します。  
  
-   アプリケーションが*LockType*を SQL_LOCK_NO_CHANGE に設定した場合、ドライバーは、アプリケーションがSQL_ATTR_CONCURRENCY ステートメント属性に対してSQL_CONCUR_LOCK指定した場合にのみ、更新または削除操作が成功することを保証します。  
  
-   アプリケーションがSQL_ATTR_CONCURRENCYステートメント属性に対してSQL_CONCUR_ROWVERまたはSQL_CONCUR_VALUESを指定した場合、ドライバーは行のバージョンまたは値を比較し、アプリケーションが行をフェッチしてから行が変更された場合は操作を拒否します。  
  
-   アプリケーションがSQL_ATTR_CONCURRENCY ステートメント属性のSQL_CONCUR_READ_ONLYを指定した場合、ドライバーは、更新または削除操作を拒否します。  
  
 SQL_ATTR_CONCURRENCY ステートメント属性の詳細については、「 [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)」を参照してください。  
  
## <a name="status-and-operation-arrays"></a>ステータスおよび操作配列  
 **SQLSetPos**を呼び出すときに、次の状態と操作の配列が使用されます。  
  
-   行の状態配列 (IRD のSQL_DESC_ARRAY_STATUS_PTR フィールドと SQL_ATTR_ROW_STATUS_ARRAY ステートメント属性が示す) には、行セット内の各データ行の状態値が含まれます。 ドライバーは **、SQL フェッチ、SQL****フェッチスクロール、SQLBulkOperations**、または**SQLSetPos**への呼び出し後に、この配列の状態値を設定します。 **SQLBulkOperations** この配列は、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示されます。  
  
-   行操作配列 (ARD のSQL_DESC_ARRAY_STATUS_PTR フィールドと SQL_ATTR_ROW_OPERATION_ARRAY ステートメント属性によって示される) には、行セット内の各行の値が含まれ、一括操作に対する**SQLSetPos**の呼び出しが無視されるか実行されるかを示します。 配列内の各要素は、SQL_ROW_PROCEED (既定値) またはSQL_ROW_IGNOREに設定されます。 この配列は、SQL_ATTR_ROW_OPERATION_PTRステートメント属性によって示されます。  
  
 ステータス配列および操作配列内の要素の数は、行セット内の行数と同じでなければなりません (SQL_ATTR_ROW_ARRAY_SIZEステートメント属性で定義されている)。  
  
 行の状態配列については、 [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)を参照してください。 行操作配列については、このセクションの「一括操作で行を無視する」を参照してください。  
  
## <a name="using-sqlsetpos"></a>を使用する  
 アプリケーションが**SQLSetPos**を呼び出す前に、次の手順を実行する必要があります。  
  
1.  アプリケーションが SQL_UPDATE に*設定された操作*で**SQLSetPos**を呼び出す場合は、各列に対して**SQLBindCol** (または**SQLSetDescRec)** を呼び出して、そのデータ型を指定し、列のデータと長さのバッファーをバインドします。  
  
2.  アプリケーションが操作をSQL_DELETEまたはSQL_UPDATE*に設定して* **SQLSetPos**を呼び出す場合は **、SQLColAttribute**を呼び出して、削除または更新する列が更新可能であることを確認します。  
  
3.  **SQLExecDirect** **、SQLExecute、** またはカタログ関数を呼び出して、結果セットを作成します。  
  
4.  **データを取得するには、SQLFetch**または**SQLFetchScroll**を呼び出します。  
  
 **SQLSetPos**の使用の詳細については、「 [SQLSetPos を使用したデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlsetpos.md)」を参照してください。  
  
## <a name="deleting-data-using-sqlsetpos"></a>SQL セットポスを使用したデータの削除  
 **SQLSetPos**を使用してデータを削除するには、アプリケーションは *、削除する行*の番号に設定された行番号とSQL_DELETEに設定された*操作*を使用して**SQLSetPos**を呼び出します。  
  
 データが削除された後、ドライバーは、実装行の状態の配列の値をSQL_ROW_DELETED (またはSQL_ROW_ERROR) に変更します。  
  
## <a name="updating-data-using-sqlsetpos"></a>SQL セットポスを使用したデータの更新  
 アプリケーションは、バインドされたデータ バッファー内の列の値を渡すか **、SQLPutData**への 1 つ以上の呼び出しを使用して渡すことができます。 **SQLPutData**を使用してデータが渡される列は、*実行時データ**列*と呼ばれます。 これらは、SQL_LONGVARBINARY列やSQL_LONGVARCHAR列のデータを送信するために一般的に使用され、他の列と混合することができます。  
  
#### <a name="to-update-data-with-sqlsetpos-an-application"></a>アプリケーションを使用してデータを更新するには、  
  
1.  **SQLBindCol**でバインドされたデータおよび長さ/インジケーター バッファーに値を配置します。  
  
    -   通常の列の場合、アプリケーションは新しい列の値を*\*TargetValuePtr*バッファーに格納し、その値の長さを*\*StrLen_or_IndPtr*バッファーに格納します。 行を更新しない場合、アプリケーションは行操作配列のその行の要素にSQL_ROW_IGNOREを配置します。  
  
    -   実行時データ列の場合、アプリケーションは、列番号などのアプリケーション定義の値を*\*TargetValuePtr*バッファーに格納します。 この値は、後で列を識別するために使用できます。  
  
         アプリケーションは、SQL_LEN_DATA_AT_EXEC(*length*) マクロの結果を **StrLen_or_IndPtr*バッファーに入れます。 列の SQL データ型がSQL_LONGVARBINARY、SQL_LONGVARCHAR、または長いデータ ソース固有のデータ型であり、ドライバーが**SQLGetInfo**のSQL_NEED_LONG_DATA_LEN情報型に対して "Y" を返す場合、*長さは*パラメーターに送信されるデータのバイト数です。それ以外の場合は、負でない値でなければならず、無視されます。  
  
2.  データ行を更新するために *、SQL_UPDATE*に設定された操作引数を指定して**SQLSetPos**を呼び出します。  
  
    -   実行時のデータ列がない場合、プロセスは完了です。  
  
    -   実行時のデータ列がある場合、関数はSQL_NEED_DATAを返し、ステップ 3 に進みます。  
  
3.  **SQLParamData**を呼び出して、処理される最初の実行時の列の*\*TargetValuePtr*バッファーのアドレスを取得します。 **SQL_NEED_DATAを返します**。 アプリケーションは、アプリケーション定義の値を*\*取得、 TargetValuePtr*バッファー。  
  
    > [!NOTE]  
    >  実行時のデータ パラメーターは実行時のデータ列と似ていますが **、SQLParamData**によって返される値はそれぞれ異なります。  
  
    > [!NOTE]  
    >  実行時データ パラメーターは、SQL ステートメントのパラメーターであり、SQLPutData ステートメントが**SQLExecDirect**または**SQLExecute**を使用して実行されるときに **、SQLPutData**と共にデータが送信されます。 これらは **、SQLBindParameter**を使用するか、記述子を設定することによってバインド**されます**。 **SQLParamData**によって返される値は、*引数の* **SQLBind パラメーター**に渡される 32 ビット値です。  
  
    > [!NOTE]  
    >  実行時のデータ列は、行が**SQLSetPos**で更新されたときに**SQLPutData**と共にデータが送信される行セット内の列です。 これらの値は **、SQLBindCol**にバインドされています。 **SQLParamData**によって返される値は、処理されている **TargetValuePtr*バッファー内の行のアドレスです。  
  
4.  列のデータを送信するために**SQLPutData**を 1 回以上呼び出します。 **SQLPutData**で指定された*\*TargetValuePtr*バッファーにすべてのデータ値を返すことができない場合は、複数の呼び出しが必要です。同じ列に対する**SQLPutData**の複数回の呼び出しは、文字 C データを文字、バイナリ、またはデータ ソース固有のデータ型を持つ列に送信する場合、または文字、バイナリ、またはデータ ソース固有のデータ型を持つ列にバイナリ C データを送信する場合にのみ許可されます。  
  
5.  **SQLParamData**を再度呼び出して、列に対してすべてのデータが送信されたことを通知します。  
  
    -   実行時のデータ列が多い場合 **、SQLParamData**は、SQL_NEED_DATAと、次に処理される実行時の列の*TargetValuePtr*バッファーのアドレスを返します。 アプリケーションは、手順 4 と 5 を繰り返します。  
  
    -   実行時のデータ列がなくなった場合、プロセスは完了です。 ステートメントが正常に実行された場合 **、SQLParamData は**SQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返します。実行が失敗した場合は、SQL_ERRORを返します。 この時点で **、SQLParamData は** **SQLSetPos**によって返すことができる任意の SQLSTATE を返すことができます。  
  
 データが更新された場合、ドライバーは、実装行の状態の配列の値を変更SQL_ROW_UPDATED。  
  
 操作がキャンセルされた場合、または**SQLParamData**または**SQLPutData**でエラーが発生した場合 **、SQLSetPos**がSQL_NEED_DATAを返した後、および実行時のすべてのデータ列に対してデータが送信される前に、アプリケーションはステートメントまたはステートメントに関連付けられた接続に対して SQLCancel、SQLGetDiagField、SQLGetDiagRec、SQLGetFunctions、SQLParamData、または**SQLGetFunctions****SQLPutData**のみを呼び出すことができます。 **SQLCancel** **SQLGetDiagField** **SQLGetDiagRec** **SQLParamData** ステートメントまたはステートメントに関連付けられた接続に対して他の関数を呼び出す場合、関数は SQL_ERROR および SQLSTATE HY010 (関数シーケンス・エラー) を戻します。  
  
 ドライバーが実行時のデータ列のデータを必要としている間にアプリケーションが**SQLCancel**を呼び出す場合、ドライバーは操作をキャンセルします。 アプリケーションは、再び**SQL セットポスを**呼び出すことができます。キャンセルしても、カーソル状態や現在のカーソル位置には影響しません。  
  
 カーソルに関連付けられているクエリ仕様の SELECT リストに、同じ列への複数の参照が含まれている場合、エラーが生成されるか、ドライバーが重複した参照を無視して要求された操作を実行するかは、ドライバー定義です。  
  
## <a name="performing-bulk-operations"></a>一括操作の実行  
 *RowNumber*引数が 0 の場合、ドライバーは、ステートメント属性によって指す行操作配列のフィールドにSQL_ROW_PROCEED値を持つ行セット内のすべての行に対して *、Operation*引数で指定された操作SQL_ATTR_ROW_OPERATION_PTR実行します。 これは、SQL_DELETE、SQL_REFRESH、またはSQL_UPDATEの*Operation*引数の*RowNumber*引数の有効な値ですが、SQL_POSITIONではありません。 SQL_POSITION*の演算*と*行番号*が 0 の**SQLSetPos**は、SQLSTATE HY109 (無効なカーソル位置) を返します。  
  
 SQLSTATE HYT00 (タイムアウト期限切れ) などの行セット全体に関連するエラーが発生した場合、ドライバーはSQL_ERRORと適切な SQLSTATE を返します。 行セット バッファーの内容は未定義で、カーソル位置は変更されません。  
  
 1 行に関連するエラーが発生した場合、ドライバーは次のようになります。  
  
-   SQL_ATTR_ROW_STATUS_PTR ステートメント属性が指す行の状態配列内の行の要素をSQL_ROW_ERRORに設定します。  
  
-   エラー・キュー内のエラーに対して 1 つ以上の追加 SQLSTATE をポストし、診断データ構造の SQL_DIAG_ROW_NUMBER フィールドを設定します。  
  
 エラーまたは警告を処理した後、ドライバーが行セットの残りの行の操作を完了すると、SQL_SUCCESS_WITH_INFO返します。 したがって、エラーを返した各行に対して、エラー待ち行列にはゼロ個以上の追加 SQLSTATE が入っています。 エラーまたは警告の処理後にドライバが操作を停止すると、SQL_ERROR返します。  
  
 ドライバーは、SQLSTATE 01004 (データが切り捨てられた) などの警告を返す場合は、特定の行に適用されるエラー情報を返す前に、行セット全体または行セット内の不明な行に適用される警告を返します。 特定の行に関する警告と、それらの行に関するその他のエラー情報を返します。  
  
 *RowNumber*が 0 で、*操作*がSQL_UPDATE、SQL_REFRESH、またはSQL_DELETEの場合 **、SQLSetPos**が処理する行の数は、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性によって示されます。  
  
 *RowNumber*が 0 で、*演算*がSQL_DELETE、SQL_REFRESH、またはSQL_UPDATEの場合、操作の後の現在の行は、操作の前の現在の行と同じになります。  
  
## <a name="ignoring-a-row-in-a-bulk-operation"></a>一括操作で行を無視する  
 行操作配列を使用して **、SQLSetPos**を使用した一括操作中に、現在の行セット内の行を無視する必要があることを示すことができます。 一括操作中に 1 つ以上の行を無視するようにドライバーに指示するには、アプリケーションは次の手順を実行する必要があります。  
  
1.  **SQLSetStmtAttr**を呼び出して、SQL_ATTR_ROW_OPERATION_PTR ステートメント属性を設定して、SQLUSMALLINTs の配列を指します。 このフィールドは **、SQLSetDescField**を呼び出して、アプリケーションが記述子ハンドルを取得する必要がある、ARD のSQL_DESC_ARRAY_STATUS_PTRヘッダー フィールドを設定することによっても設定できます。  
  
2.  行操作配列の各要素を次の 2 つの値のいずれかに設定します。  
  
    -   SQL_ROW_IGNORE、行が一括操作用に除外されることを示します。  
  
    -   SQL_ROW_PROCEED、行が一括操作に含まれることを示します。 (これは既定値です)。  
  
3.  一括操作を実行するには **、SQLSetPos**を呼び出します。  
  
 行操作配列には、次の規則が適用されます。  
  
-   SQL_ROW_IGNOREとSQL_ROW_PROCEEDは、SQL_DELETEまたはSQL_UPDATEの操作で**SQLSetPos**を使用する一括*操作*にのみ影響します。 SQL_REFRESHまたはSQL_POSITIONの*操作*を使用した**SQLSetPos**の呼び出しには影響しません。  
  
-   ポインターは、既定では null に設定されています。  
  
-   ポインターが null の場合、すべての要素がSQL_ROW_PROCEEDに設定されているかのように、すべての行が更新されます。  
  
-   要素をSQL_ROW_PROCEEDに設定しても、その特定の行で操作が実行される保証はありません。 たとえば、行セットの特定の行にSQL_ROW_ERROR状態がある場合、アプリケーションがSQL_ROW_PROCEED指定されているかどうかに関係なく、ドライバーはその行を更新できない可能性があります。 アプリケーションは、常に行の状態配列をチェックして、操作が成功したかどうかを確認する必要があります。  
  
-   SQL_ROW_PROCEEDは、ヘッダー ファイルで 0 として定義されます。 アプリケーションは、行の操作配列を 0 に初期化して、すべての行を処理できます。  
  
-   行操作配列の要素番号 "n" が SQL_ROW_IGNORE に設定され、一括更新または削除操作を実行するために**SQLSetPos**が呼び出された場合、行セットの n 行は**SQLSetPos**の呼び出し後も変更されません。  
  
-   アプリケーションでは、読み取り専用の列を自動的にSQL_ROW_IGNOREに設定する必要があります。  
  
## <a name="ignoring-a-column-in-a-bulk-operation"></a>一括操作での列の無視  
 1 つ以上の読み取り専用列に対する更新の試行によって生成される不要な処理診断を回避するために、アプリケーションはバインドされた長さ/インジケーター バッファーの値をSQL_COLUMN_IGNOREに設定できます。 詳細については、「 [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)」を参照してください。  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションはユーザーが ORDERS テーブルを参照し、注文ステータスを更新することを許可します。 カーソルはキーセットドリブンで、行セット サイズは 20 で、行バージョンを比較するオプティミスティック同時実行制御を使用します。 各行セットがフェッチされると、アプリケーションはそれを印刷し、ユーザーが注文のステータスを選択して更新できるようにします。 アプリケーションは **、SQLSetPos**を使用して、選択した行にカーソルを配置し、行の位置指定更新を実行します。 (エラー処理は、わかりやすくするために省略されています。  
  
```cpp  
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
  
 その他の例については、「 [SQLSetPos を使用した行セットの](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)[位置指定更新およびステートメントの削除](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)」および「行の更新」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ブロック カーソル位置に関連しない一括操作の実行|[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|記述子の単一フィールドの取得|[SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|記述子の複数のフィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|記述子の単一フィールドの設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|記述子の複数のフィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|ステートメント属性の設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
