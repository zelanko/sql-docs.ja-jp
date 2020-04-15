---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLBulkOperations
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLBulkOperations
helpviewer_keywords:
- SQLBulkOperations function [ODBC]
ms.assetid: 7029d0da-b0f2-44e6-9114-50bd96f47196
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61f4f294a6d84856bc3065b599a370bb5658e3ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301332"
---
# <a name="sqlbulkoperations-function"></a>SQLBulkOperations 関数
**適合 性**  
 バージョン導入: ODBC 3.0 標準準拠: ODBC  
  
 **まとめ**  
 **SQLBulkOperations は**、一括挿入と一括ブックマーク操作 (更新、削除、およびブックマークによるフェッチを含む) を実行します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLBulkOperations(  
     SQLHSTMT       StatementHandle,  
     SQLUSMALLINT   Operation);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *Operation*  
 [入力]実行する操作:  
  
 SQL_DELETE_BY_BOOKMARK SQL_FETCH_BY_BOOKMARKSQL_UPDATE_BY_BOOKMARKSQL_ADD  
  
 詳細については、「コメント」を参照してください。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NEED_DATA、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLBulkOperations が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は、通常**SQLBulkOperations**によって返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
 SQL_SUCCESS_WITH_INFOまたはSQL_ERRORを返すことができるすべての SQLSTATE (01xxx SQLSTATE を除く) では、複数行操作の 1 つ以上の行でエラーが発生した場合はSQL_SUCCESS_WITH_INFOが返され、単一行操作でエラーが発生した場合はSQL_ERRORが返されます。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データの右切り捨て|*引数が*SQL_FETCH_BY_BOOKMARKされ、SQL_C_CHARまたはSQL_C_BINARYのデータ型の列に対して文字列またはバイナリ データが返された場合、空白以外の文字または NULL 以外のバイナリ データが切り捨てられました。|  
|01S01|行内エラー|*Operation*引数がSQL_ADDされ、操作の実行中に 1 つ以上の行でエラーが発生しましたが、少なくとも 1 つの行が正常に追加されました。 (関数はSQL_SUCCESS_WITH_INFOを返します。<br /><br /> (このエラーは、アプリケーションが ODBC 2 を使用している場合にのみ発生します。*x*ドライバ。|  
|01S07|分数切り捨て|*引数 Operation*がSQL_FETCH_BY_BOOKMARKされ、アプリケーション バッファーのデータ型がSQL_C_CHARまたはSQL_C_BINARYされず、1 つ以上の列のアプリケーション バッファに返されたデータが切り捨てられました。 (数値 C データ型の場合、数値の小数部分は切り捨てられました。 時間、タイム・スタンプ、および時間の構成要素を含むインターバル C データ・タイプの場合、時間の小数部分は切り捨てられました。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07006|制限付きデータ型属性違反|*Operation*引数がSQL_FETCH_BY_BOOKMARKされ、結果セット内の列のデータ値を **、SQLBindCol**の呼び出しで*引数 TargetType*で指定されたデータ型に変換できませんでした。<br /><br /> *引数 Operation*がSQL_UPDATE_BY_BOOKMARKまたはSQL_ADDされ、アプリケーション バッファー内のデータ値を結果セット内の列のデータ型に変換できませんでした。|  
|07009|記述子インデックスが無効です|引数*Operation*がSQL_ADDされ、列が結果セットの列数より大きい列番号でバインドされました。|  
|21S02|派生テーブルの次数が列リストと一致しません|引数*操作*はSQL_UPDATE_BY_BOOKMARK。すべての列が非バインドまたは読み取り専用であったか、またはバインドされた長さ/インジケーター バッファーの値がSQL_COLUMN_IGNOREされたため、列は更新できませんでした。|  
|22001|文字列データの右切り捨て|結果セット内の列に文字またはバイナリー値を割り当てると、ブランク以外の文字 (文字の場合) または非 NULL (バイナリーの場合) の文字またはバイトが切り捨てされました。|  
|22003|範囲外の数値|*引数の演算*がSQL_ADDまたはSQL_UPDATE_BY_BOOKMARKされ、結果セット内の列に数値を代入すると、数値の整数部分 (小数部ではなく) が切り捨てられました。<br /><br /> 引数*Operation*がSQL_FETCH_BY_BOOKMARKされ、1 つ以上のバインドされた列の数値を返すと、有効桁数が失われる可能性があります。|  
|22007|日付/時刻形式が無効です|*引数 Operation*がSQL_ADDまたはSQL_UPDATE_BY_BOOKMARKされ、結果セット内の列に日付またはタイム・スタンプ値が割り当てられていた場合、年、月、または日のフィールドが範囲外になります。<br /><br /> 引数*Operation*がSQL_FETCH_BY_BOOKMARKされ、1 つ以上のバインドされた列の日付またはタイムスタンプ値を返すと、年、月、または日のフィールドが範囲外になります。|  
|22008|日付/時刻フィールドのオーバーフロー|*引数の演算*がSQL_ADDまたはSQL_UPDATE_BY_BOOKMARKされ、結果セット内の列に送信されるデータに対する日時演算のパフォーマンスが、結果として、フィールドの許容範囲を超える結果またはグレゴリオ暦の自然な日付時刻規則に基づいて無効になった結果 (年、月、日、時、分、または 2 番目のフィールド) が得られました。<br /><br /> *演算*引数がSQL_FETCH_BY_BOOKMARKされ、結果セットから取得されるデータに対する日時演算のパフォーマンスが、結果として、フィールドの許容範囲を超えた結果またはグレゴリオ暦の日付時刻の自然ルールに基づいて無効になった結果が、日付時刻フィールド (年、月、日、時、分、秒) に設定されました。|  
|22015|間隔フィールドのオーバーフロー|*Operation*引数がSQL_ADDまたはSQL_UPDATE_BY_BOOKMARKされ、正確な数値または間隔 C 型を間隔 SQL データ型に割り当てると、有効桁数が失われました。<br /><br /> *演算*引数がSQL_ADDまたはSQL_UPDATE_BY_BOOKMARKされました。間隔 SQL タイプに割り当てるときに、間隔 SQL タイプの C 型の値の表現が存在しません。<br /><br /> *Operation*引数がSQL_FETCH_BY_BOOKMARKされ、正確な数値または間隔の SQL タイプから間隔 C タイプに割り当てると、先行フィールドの有効桁数が失われました。<br /><br /> *演算*引数はSQL_FETCH_BY_BOOKMARK。インターバル C タイプに割り当てるとき、間隔 C 型の SQL タイプの値の表現はありませんでした。|  
|22018|キャスト指定に無効な文字値|*演算*引数はSQL_FETCH_BY_BOOKMARK。C 型は、正確な数値または概算数値、日時、または間隔データ型でした。列の SQL 型は文字データ型でした。列の値が、バインドされた C 型の有効なリテラルではありません。<br /><br /> 引数*操作*はSQL_ADDまたはSQL_UPDATE_BY_BOOKMARK。SQL タイプは、正確または概数、日時、または間隔データ型でした。C 型はSQL_C_CHAR。列の値がバインドされた SQL 型の有効なリテラルではありません。|  
|23000|整合性制約違反|*引数の操作*がSQL_ADD、SQL_DELETE_BY_BOOKMARK、またはSQL_UPDATE_BY_BOOKMARKされ、整合性制約に違反しました。<br /><br /> *Operation*引数がSQL_ADDされ、バインドされていない列は NOT NULL として定義され、デフォルトはありません。<br /><br /> *引数 Operation*がSQL_ADDされ、バインドされた*StrLen_or_IndPtr*バッファに指定された長さがSQL_COLUMN_IGNOREされ、列に既定値が設定されていません。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*は実行済み状態でしたが、結果セットはステートメント ハンドルに関連付*けられません*。|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|42000|構文エラーまたはアクセス違反|ドライバーは、*操作*の引数で要求された操作を実行するために必要な行をロックできませんでした。|  
|44000|WITH CHECK OPTION 違反|*引数 Operation*がSQL_ADDまたはSQL_UPDATE_BY_BOOKMARKされ、挿入または更新の影響を受ける 1 つ以上の行が表示テーブルに存在しないように **、WITH CHECK OPTION**を指定して作成された表示テーブル (または表示テーブルから派生したテーブル) に対して挿入または更新が実行されました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、*ステートメント ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、関数は*ステートメント ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLBulkOperations**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM) 指定された*ステートメント ハンドル*が実行状態にありません。 関数は、最初に呼び出**さずに****呼**び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル***に対**して呼び**出され**、SQL_NEED_DATA返されました。 この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM) ドライバは ODBC 2 です。*x*ドライバー、および SQL フェッチスクロールまたは*StatementHandle* **SQLFetch**が呼び**SQLFetch**出される前にステートメント ハンドルに対して**呼**び出されました。<br /><br /> **(DM) SQLBulk操作は、** ステートメント*ハンドル*で**SQLExtendedFetch**が呼び出された後に呼び出されました。|  
|HY011|属性を今設定できません|(DM) ドライバは ODBC 2 です。*x*ドライバー、およびステートメント属性SQL_ATTR_ROW_STATUS_PTR SQLFetch または**SQLFetchScroll**と**SQLBulk 操作**の呼び出しの間に設定されました。 **SQLFetchScroll**|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|*演算*引数がSQL_ADDまたはSQL_UPDATE_BY_BOOKMARKされました。データ値が NULL ポインタではありませんでした。C データ型がSQL_C_BINARYまたはSQL_C_CHAR。列の長さの値が 0 未満であったが、SQL_DATA_AT_EXEC、SQL_COLUMN_IGNORE、SQL_NTS、またはSQL_NULL_DATAに等しくないか、またはSQL_LEN_DATA_AT_EXEC_OFFSET以下であった。<br /><br /> 長さ/インジケーター バッファーの値はSQL_DATA_AT_EXEC。SQL 型は、SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長いデータ ソース固有のデータ型です。**SQLGetInfo**のSQL_NEED_LONG_DATA_LEN情報の種類は "Y" でした。<br /><br /> *Operation*引数がSQL_ADDされ、SQL_ATTR_USE_BOOKMARKステートメント属性がSQL_UB_VARIABLE に設定され、列 0 は、この結果セットのブックマークの最大長と等しくない長さのバッファーにバインドされました。 (この長さは IRD のSQL_DESC_OCTET_LENGTH フィールドで使用でき **、SQLDescribeCol** **、SQLCol 属性**、または**SQLGetDescField**を呼び出すことによって取得できます。|  
|HY092|無効な属性識別子|(DM)*演算*引数に指定された値が無効です。<br /><br /> *引数の演算*がSQL_ADD、SQL_UPDATE_BY_BOOKMARK、またはSQL_DELETE_BY_BOOKMARKされ、SQL_ATTR_CONCURRENCYステートメント属性がSQL_CONCUR_READ_ONLYに設定されました。<br /><br /> *引数が*SQL_DELETE_BY_BOOKMARK、SQL_FETCH_BY_BOOKMARK、またはSQL_UPDATE_BY_BOOKMARKされ、ブックマーク列がバインドされていないか、SQL_ATTR_USE_BOOKMARKSステートメント属性がSQL_UB_OFFに設定されています。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|ドライバーまたはデータ ソースは、*操作*の引数で要求された操作をサポートしていません。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが結果セットを返しました。 タイムアウト期間は、属性*引数が*SQL_ATTR_QUERY_TIMEOUTの**SQLSetStmtAttr**を使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
  
> [!CAUTION]  
>  **SQLBulkOperations**を呼び出すことができるステートメントの状態と、ODBC 2 との互換性のために何を行う必要があるかについて説明します。*x*アプリケーションについては、「付録 G: 下位互換性のためのドライバガイドライン」の[「ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)」のセクションを参照してください。  
  
 アプリケーションは**SQLBulkOperations を**使用して、現在のクエリに対応するベース テーブルまたはビューに対して次の操作を実行します。  
  
-   新しい行を追加します。  
  
-   各行がブックマークによって識別される行のセットを更新します。  
  
-   各行がブックマークによって識別される行のセットを削除します。  
  
-   各行がブックマークによって識別される行のセットを取得します。  
  
 **SQLBulkOperations**への呼び出しの後、ブロック カーソルの位置は未定義です。 アプリケーションは、カーソル位置を設定するために**SQLFetchScroll**を呼び出す必要があります。 アプリケーションは、SQL_FETCH_FIRST、SQL_FETCH_LAST、SQL_FETCH_ABSOLUTE、またはSQL_FETCH_BOOKMARKの FetchOrientation 引数を指定して**のみ SQLFetchScroll**を呼び出す必要があります。 *FetchOrientation* アプリケーションが、SQL_FETCH_PRIOR、SQL_FETCH_NEXT、またはSQL_FETCH_RELATIVEの*フェッチオリエンテーション*引数を指定して**SQLFetch**または**SQLFetchScroll**を呼び出した場合、カーソル位置は未定義です。  
  
 **SQLBulkOperations**の呼び出しによって実行される一括操作では **、SQLBindCol**の呼び出しで指定された列の長さ/インジケーター バッファーをSQL_COLUMN_IGNOREに設定することで、列を無視できます。  
  
 **SQLBulkOperations**を呼び出すときに、アプリケーションが SQL_ATTR_ROW_OPERATION_PTR ステートメント属性を設定する必要はありません。  
  
 SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性によって指すバッファーには **、 SQLBulkOperations**の呼び出しによって影響を受ける行数が含まれています。  
  
 *Operation*引数がSQL_ADDまたはSQL_UPDATE_BY_BOOKMARKされ、カーソルに関連付けられているクエリ仕様の select リストに同じ列への複数の参照が含まれている場合、エラーが生成されるか、ドライバーが重複した参照を無視して要求された操作を実行するかは、ドライバー定義されます。  
  
 **SQLBulkOperations**を使用する方法の詳細については、「 [SQLBulkOperations を使用したデータの更新](../../../odbc/reference/develop-app/updating-data-with-sqlbulkoperations.md)」を参照してください。  
  
## <a name="performing-bulk-inserts"></a>一括挿入の実行  
 **SQLBulkOperations**を使用してデータを挿入するには、アプリケーションは次の手順を実行します。  
  
1.  結果セットを返すクエリを実行します。  
  
2.  SQL_ATTR_ROW_ARRAY_SIZEステートメント属性を、挿入する行数に設定します。  
  
3.  挿入するデータをバインドするために**SQLBindCol**を呼び出します。 データは、SQL_ATTR_ROW_ARRAY_SIZEの値と同じサイズの配列にバインドされます。  
  
    > [!NOTE]  
    >  SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって指される配列のサイズは、SQL_ATTR_ROW_ARRAY_SIZE に等しいか、SQL_ATTR_ROW_STATUS_PTR null ポインターである必要があります。  
  
4.  挿入を実行するために**SQLBulkOperations**(*ステートメント ハンドル、SQL_ADD)* を呼び出します。  
  
5.  アプリケーションが SQL_ATTR_ROW_STATUS_PTR ステートメント属性を設定している場合、この配列を検査して操作の結果を確認できます。  
  
 アプリケーションが SQL_ADD の*操作*引数を使用して**SQLBulkOperations**を呼び出す前に列 0 をバインドする場合、ドライバーは、バインドされた列 0 バッファーを新しく挿入された行のブックマーク値で更新します。 これを行うには、アプリケーションは、ステートメントを実行する前にSQL_ATTR_USE_BOOKMARKSステートメント属性をSQL_UB_VARIABLEに設定しておく必要があります。 (これは ODBC 2 では動作しません。*x*ドライバ。  
  
 長いデータは、SQLParamData および SQLPutData の呼び出しを使用して、SQLBulkOperations によって部分的に追加できます。 詳細については、後の「一括挿入と更新のための長いデータの提供」を参照してください。  
  
 アプリケーションが**SQLBulkOperations**を呼び出す前に**SQLFetch**または**SQLFetchScroll**を呼び出す必要はありません (ODBC 2 に対して行く場合を除く)。*x*ドライバ。[後方互換性と標準準拠](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)を参照してください。  
  
 この動作は、重複する列を含むカーソルで **、sqlBulkOperations**関数が SQL_ADD の*操作*引数を持つ場合にドライバー定義されます。 ドライバーは、ドライバー定義の SQLSTATE を返す、結果セットに表示される最初の列にデータを追加、またはその他のドライバー定義の動作を実行できます。  
  
## <a name="performing-bulk-updates-by-using-bookmarks"></a>ブックマークを使用した一括更新の実行  
 **SQLBulkOperations**でブックマークを使用して一括更新を実行するには、アプリケーションは次の手順を順番に実行します。  
  
1.  SQL_ATTR_USE_BOOKMARKSステートメント属性をSQL_UB_VARIABLEに設定します。  
  
2.  結果セットを返すクエリを実行します。  
  
3.  SQL_ATTR_ROW_ARRAY_SIZEステートメント属性を更新する行数に設定します。  
  
4.  **SQLBindCol**を呼び出して、更新するデータをバインドします。 データは、SQL_ATTR_ROW_ARRAY_SIZEの値と同じサイズの配列にバインドされます。 また、列 0 (ブックマーク列) をバインドするために**SQLBindCol**を呼び出します。  
  
5.  列 0 にバインドされた配列に、更新する行のブックマークをコピーします。  
  
6.  バインドされたバッファー内のデータを更新します。  
  
    > [!NOTE]  
    >  SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって指される配列のサイズは、SQL_ATTR_ROW_ARRAY_SIZEに等しいか、SQL_ATTR_ROW_STATUS_PTR null ポインターである必要があります。  
  
7.  呼び出し**SQLBulkオペレーション**(*ステートメントハンドル、SQL_UPDATE_BY_BOOKMARK)。*  
  
    > [!NOTE]  
    >  アプリケーションが SQL_ATTR_ROW_STATUS_PTR ステートメント属性を設定している場合、この配列を検査して操作の結果を確認できます。  
  
8.  必要に応じて **、SQLBulkOperations**(*ステートメントハンドル*、 SQL_FETCH_BY_BOOKMARK) を呼び出して、バインドされたアプリケーション バッファにデータをフェッチし、更新が発生したことを確認します。  
  
9. データが更新されている場合、ドライバーは、適切な行の行の状態の配列の値を変更SQL_ROW_UPDATED。  
  
 **SQLBulk 操作**によって実行される一括更新には **、SQLParamData**および**SQLPutData**への呼び出しを使用して長いデータを含めることができます。 詳細については、後の「一括挿入と更新のための長いデータの提供」を参照してください。  
  
 ブックマークがカーソル間で保持される場合、アプリケーションは、ブックマークで更新する前に**SQLFetch**または**SQLFetchScroll**を呼び出す必要はありません。 前のカーソルから保存したブックマークを使用できます。 ブックマークがカーソル間で保持されない場合、アプリケーションは SQLFetch または**SQLFetchScroll**を呼び出してブックマークを取得する必要があります。 **SQLFetchScroll**  
  
 この動作は **、sqlBulkOperations**が、SQL_UPDATE_BY_BOOKMARKの*操作*引数を持つ場合にドライバー定義されます。 ドライバーは、ドライバー定義の SQLSTATE を返す、結果セットに表示される最初の列を更新、またはその他のドライバー定義の動作を実行できます。  
  
## <a name="performing-bulk-fetches-using-bookmarks"></a>ブックマークを使用した一括フェッチの実行  
 **SQLBulkOperations**を使用してブックマークを使用して一括フェッチを実行するには、アプリケーションは次の手順を順番に実行します。  
  
1.  SQL_ATTR_USE_BOOKMARKSステートメント属性をSQL_UB_VARIABLEに設定します。  
  
2.  結果セットを返すクエリを実行します。  
  
3.  SQL_ATTR_ROW_ARRAY_SIZEステートメント属性を、フェッチする行数に設定します。  
  
4.  取得するデータをバインドするために**SQLBindCol**を呼び出します。 データは、SQL_ATTR_ROW_ARRAY_SIZEの値と同じサイズの配列にバインドされます。 また、列 0 (ブックマーク列) をバインドするために**SQLBindCol**を呼び出します。  
  
5.  列 0 にバインドされた配列に、フェッチする対象の行のブックマークをコピーします。 (これは、アプリケーションがブックマークを個別に取得していることを前提としています。  
  
    > [!NOTE]  
    >  SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって指される配列のサイズは、SQL_ATTR_ROW_ARRAY_SIZEに等しいか、SQL_ATTR_ROW_STATUS_PTR null ポインターである必要があります。  
  
6.  呼び出し**SQLBulk操作**(*ステートメントハンドル、SQL_FETCH_BY_BOOKMARK)。*  
  
7.  アプリケーションが SQL_ATTR_ROW_STATUS_PTR ステートメント属性を設定している場合、この配列を検査して操作の結果を確認できます。  
  
 ブックマークがカーソル間で保持される場合、アプリケーションは、ブックマークを使用してフェッチする前に**SQLFetch**または**SQLFetchScroll**を呼び出す必要はありません。 前のカーソルから保存したブックマークを使用できます。 ブックマークがカーソル間で保持されない場合、アプリケーションは SQLFetch または**SQLFetchScroll**を呼び出してブックマークを取得する必要があります。 **SQLFetchScroll**  
  
## <a name="performing-bulk-deletes-using-bookmarks"></a>ブックマークを使用した一括削除の実行  
 **SQLBulkOperations**でブックマークを使用して一括削除を実行するには、アプリケーションは次の手順を順番に実行します。  
  
1.  SQL_ATTR_USE_BOOKMARKSステートメント属性をSQL_UB_VARIABLEに設定します。  
  
2.  結果セットを返すクエリを実行します。  
  
3.  SQL_ATTR_ROW_ARRAY_SIZEステートメント属性を削除する行数に設定します。  
  
4.  列 0 (ブックマーク列) をバインドする**SQLBindCol**を呼び出します。  
  
5.  削除する行のブックマークを、列 0 にバインドされた配列にコピーします。  
  
    > [!NOTE]  
    >  SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって指される配列のサイズは、SQL_ATTR_ROW_ARRAY_SIZEに等しいか、SQL_ATTR_ROW_STATUS_PTR null ポインターである必要があります。  
  
6.  呼び出し**SQLBulk操作**(*ステートメント ハンドル、SQL_DELETE_BY_BOOKMARK)。*  
  
7.  アプリケーションが SQL_ATTR_ROW_STATUS_PTR ステートメント属性を設定している場合、この配列を検査して操作の結果を確認できます。  
  
 ブックマークがカーソル間で保持される場合、アプリケーションはブックマークで削除する前に**SQLFetch**または**SQLFetchScroll**を呼び出す必要はありません。 前のカーソルから保存したブックマークを使用できます。 ブックマークがカーソル間で保持されない場合、アプリケーションは SQLFetch または**SQLFetchScroll**を呼び出してブックマークを取得する必要があります。 **SQLFetchScroll**  
  
## <a name="providing-long-data-for-bulk-inserts-and-updates"></a>一括挿入および更新のための長いデータの提供  
 **SQLBulkOperations**の呼び出しによって実行される一括挿入および更新に対して、長いデータを提供できます。 長いデータを挿入または更新する場合、アプリケーションは、このトピックで前述した「一括挿入の実行」および「ブックマークを使用した一括更新の実行」で説明した手順に加えて、次の手順を実行します。  
  
1.  **SQLBindCol**を使用してデータをバインドする場合、アプリケーションは、実行時のデータ列の*\*TargetValuePtr*バッファーに列番号などのアプリケーション定義の値を格納します。 この値は、後で列を識別するために使用できます。  
  
     アプリケーションは、SQL_LEN_DATA_AT_EXEC(*length*) マクロの結果を*\*StrLen_or_IndPtr*バッファーに入れます。 列の SQL データ型がSQL_LONGVARBINARY、SQL_LONGVARCHAR、または長いデータ ソース固有のデータ型であり、ドライバーが**SQLGetInfo**のSQL_NEED_LONG_DATA_LEN情報型に対して "Y" を返す場合、*長さは*パラメーターに送信されるデータのバイト数です。それ以外の場合は、負でない値でなければならず、無視されます。  
  
2.  **SQLBulkOperations**が呼び出されると、実行時のデータ列がある場合、関数はSQL_NEED_DATAを返し、次の手順 3 に進みます。 (実行時のデータ列がない場合は、処理は完了です)。  
  
3.  アプリケーションは、最初に処理される実行時のデータ列の*\*TargetValuePtr*バッファーのアドレスを取得する**SQLParamData**を呼び出します。 **SQL_NEED_DATAを返します**。 アプリケーションは、アプリケーション定義の値を*\*取得、 TargetValuePtr*バッファー。  
  
    > [!NOTE]  
    >  実行時のデータ パラメーターは実行時のデータ列に似ていますが **、SQLParamData**によって返される値はそれぞれ異なります。  
  
     実行データ列は、行が更新されるか、または**SQLBulkOperations**を使用して挿入されるときに **、SQLPutData**と共にデータが送信される行セット内の列です。 これらの値は **、SQLBindCol**にバインドされています。 **SQLParamData**によって返される値は、処理されている **TargetValuePtr*バッファー内の行のアドレスです。  
  
4.  アプリケーションは、列のデータを送信するために**SQLPutData**を 1 回以上呼び出します。 **SQLPutData**で指定された*\*TargetValuePtr*バッファーにすべてのデータ値を返すことができない場合は、複数の呼び出しが必要です。同じ列に対する**SQLPutData**の複数回の呼び出しは、文字 C データを文字、バイナリ、またはデータ ソース固有のデータ型を持つ列に送信する場合、または文字、バイナリ、またはデータ ソース固有のデータ型を持つ列にバイナリ C データを送信する場合にのみ許可されます。  
  
5.  アプリケーションは、列のすべてのデータが送信されたことを示すために **、SQLParamData**を再度呼び出します。  
  
    -   実行時のデータ列が多い場合 **、SQLParamData**は、SQL_NEED_DATAと、次に処理される実行時の列の*TargetValuePtr*バッファーのアドレスを返します。 アプリケーションは、手順 4 と 5 を繰り返します。  
  
    -   実行時のデータ列がなくなった場合、プロセスは完了です。 ステートメントが正常に実行された場合 **、SQLParamData は**SQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返します。実行が失敗した場合は、SQL_ERRORを返します。 この時点で **、SQLParamData は** **SQLBulk オペレーション**によって返される可能性のある任意の SQLSTATE を返すことができます。  
  
 操作がキャンセルされた場合、または**SQLBulkOperations**がSQL_NEED_DATAを返した後、および実行データのすべての列に対してデータが送信される前に**SQLParamData**または**SQLPutData**でエラーが発生した場合、アプリケーションは、ステートメントまたはステートメントに関連付けられた接続に対して、SQLCancel、SQLGetDiagField、SQLGetDiagRec、SQLGetFunctions、SQLParamData、または**SQLGetFunctions****SQLPutData**のみを呼び出すことができます。 **SQLCancel** **SQLGetDiagField** **SQLGetDiagRec** **SQLParamData** ステートメントまたはステートメントに関連付けられた接続に対して他の関数を呼び出す場合、関数は SQL_ERROR および SQLSTATE HY010 (関数シーケンス・エラー) を戻します。  
  
 ドライバーが実行時のデータ列のデータを必要としている間にアプリケーションが**SQLCancel**を呼び出す場合、ドライバーは操作をキャンセルします。 アプリケーションは、再び**SQLBulk オペレーションを**呼び出すことができます。キャンセルしても、カーソル状態や現在のカーソル位置には影響しません。  
  
## <a name="row-status-array"></a>行の状態の配列  
 行の状態の配列には **、SQLBulkOperations**への呼び出し後の行セット内のデータの各行の状態値が含まれています。 ドライバーは **、SQLFetch、SQLフェッチ****スクロール、SQL****セットPos、** または**SQLBulkOperations**への呼び出し後に、この配列の状態値を設定します。 この配列は、SQL フェッチまたは SQL**フェッチ****スクロール**が**SQLBulkOperations**の前に呼び出されていない場合は、最初に**SQLBulkOperations の**呼び出しによって設定されます。 この配列は、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって示されます。 行ステータス配列内の要素数は、行セット内の行数と同じでなければなりません (SQL_ATTR_ROW_ARRAY_SIZEステートメント属性で定義されている)。 この行の状態の配列については、 [SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)を参照してください。  
  
## <a name="code-example"></a>コード例  
 次の例では、Customers テーブルから一度に 10 行のデータをフェッチします。 次に、ユーザーにアクションを実行するよう求めます。 ネットワーク トラフィックを減らすために、この例では、バインドされた配列の中でローカルに更新、削除、挿入を行いますが、行セット データを越えたオフセットでバッファを取得します。 ユーザーがデータ ソースに更新、削除、挿入を送信することを選択すると、コードはバインド オフセットを適切に設定し **、SQLBulkOperations**を呼び出します。 わかりやすくするため、ユーザーは 10 個を超える更新、削除、または挿入をバッファに格納できません。  
  
```cpp  
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
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|記述子の単一フィールドの取得|[SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|記述子の複数のフィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|記述子の単一フィールドの設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|記述子の複数のフィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
|カーソルの位置、行セット内のデータの更新、または行セット内のデータの更新または削除|[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|ステートメント属性の設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
