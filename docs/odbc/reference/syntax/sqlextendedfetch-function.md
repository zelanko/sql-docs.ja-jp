---
title: 関数を拡張する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLExtendedFetch
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLExtendedFetch
helpviewer_keywords:
- SQLExtendedFetch function [ODBC]
ms.assetid: 940b5cf7-581c-4ede-8533-c67d5e9ef488
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dc832e5a20b1d3c0a1ad63b3e2a070563de2b46d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285982"
---
# <a name="sqlextendedfetch-function"></a>SQLExtendedFetch 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: 非推奨  
  
 **まとめ**  
 **SQLExtendedFetch**は、指定されたデータの行セットを結果セットからフェッチし、バインドされたすべての列のデータを返します。 行セットは、絶対位置または相対位置またはブックマークで指定できます。  
  
> [!NOTE]
>  ODBC 3 *.x*では **、SQL エクステンドフェッチ**が**SQL フェッチスクロール**に置き換えられました。 ODBC 3 *.x*アプリケーションは **、SQLExtendedFetch を**呼び出すべきではありません。代わりに **、SQLFetchScroll を**呼び出す必要があります。 ドライバー マネージャーは **、ODBC** 2 *.x*ドライバーを操作するときに SQL フェッチスクロールを**SQLExtendedFetch**にマップします。 ODBC 3 *.x*ドライバーは、それを呼び出す ODBC 2 *.x*アプリケーションで動作する場合は **、SQLExtendedFetch**をサポートする必要があります。 詳細については、「付録 G: 下位互換性のためのドライバガイドライン」の「コメント」と「[ブロックカーソル」、「スクロール可能なカーソル」、および後方互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLExtendedFetch(  
      SQLHSTMT         StatementHandle,  
      SQLUSMALLINT     FetchOrientation,  
      SQLLEN           FetchOffset,  
      SQLULEN *        RowCountPtr,  
      SQLUSMALLINT *   RowStatusArray);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *フェッチオリエンテーション*  
 [入力]フェッチのタイプ。 これは **、SQL**フェッチスクロールの*フェッチオリエンテーション*と同じです。  
  
 *フェッチオフセット*  
 [入力]フェッチする行の番号。 これは、1 つの例外を除いて **、SQLFetchScroll**の*フェッチオフセット*と同じです。 *フェッチオリエンテーション*がSQL_FETCH_BOOKMARK場合 *、FetchOffset*は固定長のブックマークであり、ブックマークからのオフセットではありません。 つまり **、SQLExtendedFetch**は、SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性ではなく、この引数からブックマークを取得します。 可変長のブックマークはサポートされず、ブックマークからのオフセット (0 以外) での行セットのフェッチはサポートされていません。  
  
 *行カウントプター*  
 [出力]実際にフェッチされた行数を返すバッファーへのポインター。 このバッファーは、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性で指定されたバッファーと同じ方法で使用されます。 このバッファーは **、SQLExtendedFetch**によってのみ使用されます。 **これは、SQL フェッチ**または**SQL フェッチスクロール**では使用されません。  
  
 *行の状態の配列*  
 [出力]各行の状態を返す配列へのポインター。 この配列は、SQL_ATTR_ROW_STATUS_PTRステートメント属性で指定された配列と同じ方法で使用されます。  
  
 ただし、この配列のアドレスは、IRD のSQL_DESC_STATUS_ARRAY_PTR フィールドには格納されません。 さらに、この配列は **、SQLExtendedFetch および SQLExtendedFetch**の後に呼び出されたときに、SQL_ADDまたは**SQL セットポス**の*操作*を伴う**SQLBulkOperations**によってのみ使用されます。 **SQLExtendedFetch** SQL フェッチまたは**SQL** **フェッチスクロール**では使用されず、SQL フェッチまたは SQL フェッチスクロールの後に呼び出されたときには **、SQL** **バルクオペレーション**または**SQL****セットポス**によって使用されません。 また、SQL_ADDの*操作*を伴う**SQLBulkOperation**が、フェッチ関数が呼び出される前に呼び出される場合にも使用されません。 つまり、ステートメント状態 S7 でのみ使用されます。 ステートメント状態 S5 または S6 では使用されません。 詳細については、「付録 B: ODBC 状態[遷移](../../../odbc/reference/appendixes/statement-transitions.md)テーブル」のステートメントの遷移を参照してください。  
  
 アプリケーションは *、RowStatusArray*引数に有効なポインターを提供する必要があります。ない場合は **、SQLExtendedFetch**の動作と、カーソルが配置された後の**SQLBulk 操作**または**SQLSetPos**への呼び出しの**動作は未**定義です。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLExtendedFetch が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQLError を呼び出すことによって関連付けられた**SQLSTATE**値を取得できます。 次の表は **、SQLExtendedFetch**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。 1 つの列でエラーが発生した場合は、エラーが発生した列を判別するために、SQL_DIAG_COLUMN_NUMBERの*DiagIdentifier を*指定して**SQLGetDiagField**を呼び出すことができます。**SQLGetDiagField**は、その列を含む行を決定するSQL_DIAG_ROW_NUMBERの*DiagIdentifier*を使用して呼び出すことができます。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|列に対して返された文字列データまたはバイナリ データの結果、空白以外の文字または NULL 以外のバイナリ データが切り捨てられます。 文字列値の場合は、右に切り捨てられます。 数値の場合、数値の小数部分は切り捨てられます。  (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S01|行内エラー|1 つ以上の行をフェッチ中にエラーが発生しました。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S06|結果セットが最初の行セットを返す前にフェッチを試みる|要求された行セットは、現在の位置が最初の行を越えたときに結果セットの開始と重なり合い *、FetchOrientation*がSQL_PRIORされたか、または*FetchOrientation*が現在のSQL_ROWSET_SIZE以下の絶対値を持つ負の*FetchOffset*でSQL_RELATIVEされました。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S07|分数切り捨て|列に対して返されたデータが切り捨てられました。 数値データ型の場合、数値の小数部分は切り捨てられました。 時間、タイム・スタンプ、および時間コンポーネントを含む間隔データ・タイプの場合、時間の小数部分は切り捨てられました。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07006|制限付きデータ型属性違反|データ値を**SQLBindCol**で*TargetType*で指定された C データ型に変換できませんでした。|  
|07009|記述子インデックスが無効です|列 0 が**SQLBindCol**でバインドされ、SQL_ATTR_USE_BOOKMARKSステートメント属性が SQL_UB_OFF に設定されました。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|22002|インジケーター変数が必要ですが、指定されていません|**SQLBindCol**によって設定された*StrLen_or_IndPtr*が NULL ポインターである列に NULL データがフェッチされました。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|22003|範囲外の数値|1 つ以上の列の数値 (数値または文字列) を返すと、数値の整数部分 (小数部ではなく) が切り捨てられる可能性があります。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。<br /><br /> 詳細については、「付録 D:[データ型」の「間隔データ型と数値データ型のガイドライン](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md)」を参照してください。|  
|22007|日付/時刻形式が無効です|結果セット内の文字列が日付、時刻、またはタイム・スタンプ C の構造にバインドされ、列の値がそれぞれ無効な日付、時刻、またはタイム・スタンプであった。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|22012|ゼロ除算|算術式の値が返され、結果として 0 除算が行われました。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|22015|間隔フィールドのオーバーフロー|正確な数値または間隔の SQL タイプから間隔 C タイプに割り当てると、先行フィールドの有効桁数が失われます。<br /><br /> データを間隔 C 型にフェッチする場合、間隔 C 型の SQL 型の値の表現はありませんでした。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|22018|キャスト指定に無効な文字値|C 型は、正確な数値または概数、日時、または間隔のデータ型でした。列の SQL 型は文字データ型でした。列の値が、バインドされた C 型の有効なリテラルではありません。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*は実行済み状態でしたが、結果セットはステートメント ハンドルに関連付*けられません*。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 SQLError によって返**SQLError**されるエラー メッセージ*は、メッセージ テキスト バッファーにエラーとその原因を記述\** します。|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、ステートメント ハンドルで**SQLCancel**または**SQLCancelHandle**が呼び出された後、*ステートメント ハンドル*で関数が再度呼び出されました。 *StatementHandle*<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLExtendedFetch**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM) 指定された*ステートメント ハンドル*が実行状態にありません。 関数は、最初に呼び出**さずに****呼**び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM) SQLFetch または**SQLFetchScroll** **SQLFetch**が呼び**SQLFetchScroll**出された後、および SQL_CLOSE オプションを使用して**SQLFreeStmt**が呼び出される前にステートメント*ハンドル*に対して呼び出されました。<br /><br /> (DM) **SQLBulk操作**は **、SQLFetch、SQLFetchScroll、** または**SQLExtendedFetch**が呼び出される前にステートメントに対して呼び出され、その後、SQL_CLOSE オプションを指定して**SQLFreeStmt**が呼び出される前に**SQLExtendedFetch**が呼び出されました。 **SQLFetchScroll**|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY106|フェッチタイプが範囲外です|(DM) 引数*FetchOrientation*に指定された値が無効です。 (「コメント」を参照してください。<br /><br /> 引数*FetchOrientation*がSQL_FETCH_BOOKMARKされ、SQL_ATTR_USE_BOOKMARKSステートメント属性がSQL_UB_OFFに設定されました。<br /><br /> SQL_CURSOR_TYPEステートメント・オプションの値がSQL_CURSOR_FORWARD_ONLYされ、引数*FetchOrientation*の値がSQL_FETCH_NEXTされませんでした。<br /><br /> 引数*FetchOrientation が*SQL_FETCH_RESUMEされました。|  
|HY107|行の値が範囲外です|SQL_CURSOR_TYPEステートメント・オプションで指定された値はSQL_CURSOR_KEYSET_DRIVENされましたが、SQL_KEYSET_SIZEステートメント属性で指定された値が 0 より大きく、SQL_ROWSET_SIZEステートメント属性で指定された値より小さくなっています。|  
|HY111|ブックマーク値が無効です|引数*FetchOrientation が*SQL_FETCH_BOOKMARKされ、引数*FetchOffset*で指定されたブックマークが無効です。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|ドライバまたはデータ ソースは、指定されたフェッチタイプをサポートしていません。<br /><br /> ドライバーまたはデータ ソースは **、SQLBindCol**の*ターゲットの種類*と、対応する列の SQL データ型の組み合わせで指定された変換をサポートしていません。 このエラーは、列の SQL データ型がドライバー固有の SQL データ型にマップされている場合にのみ適用されます。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが結果セットを返しました。 タイムアウト期間は、SQL_QUERY_TIMEOUT**を**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 **SQL エクステンドフェッチ**の動作は、次の例外を除いて **、SQLFetchScroll**の動作と同じです。  
  
-   **フェッチされた**行数を返すために、異なるメソッド**を使用します**。 **フェッチ**された行*\*数を*返します。**sqlFetchScroll**は、SQL_ATTR_ROWS_FETCHED_PTRが指すバッファーに直接フェッチされた行数を返します。 詳細については、*引数を参照*してください。  
  
-   **SQLExtendedFetch**と**SQLFetchScroll は**、異なる配列内の各行の状態を返します。 詳細については、*引数*を参照してください。  
  
-   **フェッチオリエンテーションが**SQL_FETCH_BOOKMARKされている場合 **、** ブックマークを取得するのには、異なるメソッド*を*使用します。 **SQLExtendedFetch**は、可変長のブックマークをサポートしないか、または行セットをブックマークから 0 以外のオフセットでフェッチします。 詳細については、*引数のフェッチを*参照してください。  
  
-   **SQL 拡張フェッチ**と**SQL フェッチスクロールは**、異なる行セット サイズを使用します。 **SQLExtendedFetch**はSQL_ROWSET_SIZE ステートメント属性の値を使用し **、SQLFetchScroll**はSQL_ATTR_ROW_ARRAY_SIZE ステートメント属性の値を使用します。  
  
-   **SQL エクステンドフェッチ**は **、SQLFetchScroll**とは若干異なるエラー処理セマンティクスがあります。 詳細については、 [SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)の「コメント」セクションの「エラー処理」を参照してください。  
  
-   **バインド**オフセット (SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性) はサポートされていません。  
  
-   **SQLExtendedFetch**への呼び出しを**SQLFetch**または**SQLFetchScroll**の呼び出しと混合することはできませんし、フェッチ関数が呼び出される前に**SQLBulkOperations**が呼び出された場合、カーソルが閉じられ、再び開かれるまで **、SQLExtendedFetch**を呼び出すことはできません。 つまり、ステートメント状態 S7 でのみ**呼**び出すことができます。 詳細については、「付録 B: ODBC 状態[遷移](../../../odbc/reference/appendixes/statement-transitions.md)テーブル」のステートメントの遷移を参照してください。  
  
 アプリケーションが ODBC 2 *.x*ドライバーを使用しているときに**SQLFetchScroll**を呼び出すと、ドライバー マネージャーは、この呼び出しを**SQLExtendedFetch**にマップします。 詳細については、SQL フェッチスクロールの「SQL フェッチスクロールと ODBC 2 *.x*ドライバー」を[参照してください](../../../odbc/reference/syntax/sqlfetchscroll-function.md)。  
  
 ODBC 2 *.x*では、複数の行をフェッチするために**SQLExtendedFetch**が呼び出され、1 つの行をフェッチするために**SQLFetch**が呼び出されました。 ODBC 3 *.x*では **、SQLFetch**を呼び出して複数の行をフェッチできます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|一括挿入、更新、または削除操作の実行|[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|SQL ステートメントの実行|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|結果セット列の数を返す|[SQLNumResultCols 関数](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|カーソルの位置、行セット内のデータの更新、または結果セット内のデータの更新または削除|[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|ステートメント属性の設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
