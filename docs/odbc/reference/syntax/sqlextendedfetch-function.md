---
title: SQLExtendedFetch 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLExtendedFetch
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLExtendedFetch
helpviewer_keywords:
- SQLExtendedFetch function [ODBC]
ms.assetid: 940b5cf7-581c-4ede-8533-c67d5e9ef488
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1a02b1c2e050b6fc7a0724286c7f023cb376e7bb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32922807"
---
# <a name="sqlextendedfetch-function"></a>SQLExtendedFetch 関数
**準拠**  
 バージョンで導入された: ODBC 1.0 標準準拠: 非推奨  
  
 **概要**  
 **SQLExtendedFetch**結果セットからデータの指定した行セットをフェッチされ、すべてのバインドされた列のデータを返します。 絶対または相対位置にまたはブックマークによる行セットを指定できます。  
  
> [!NOTE]  
>  ODBC 3 *.x*、 **SQLExtendedFetch**代わりました**SQLFetchScroll**です。 ODBC 3 *.x*アプリケーションを呼び出す必要がありますいない**SQLExtendedFetch**; 代わりに呼び出すことによって**SQLFetchScroll**です。 ドライバー マネージャーは、マップ**SQLFetchScroll**に**SQLExtendedFetch** ODBC 2 を使用するときに *.x*ドライバー。 ODBC 3 *.x*ドライバーをサポートする必要があります**SQLExtendedFetch** ODBC 2 を使用する場合は *.x*それを呼び出すアプリケーションです。 詳細については、「コメント」を参照してください。 および[ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLExtendedFetch(  
      SQLHSTMT         StatementHandle,  
      SQLUSMALLINT     FetchOrientation,  
      SQLLEN           FetchOffset,  
      SQLULEN *        RowCountPtr,  
      SQLUSMALLINT *   RowStatusArray);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *FetchOrientation*  
 [入力]フェッチの型。 これは、同じ*FetchOrientation*で**SQLFetchScroll**です。  
  
 *FetchOffset*  
 [入力]フェッチする行の数です。 これは、同じ*FetchOffset*で**SQLFetchScroll**、1 つの例外を使用します。 ときに*FetchOrientation*は sql_fetch_bookmark を指定して、 *FetchOffset*ブックマークからオフセットではなく、固定長ブックマークします。 つまり、 **SQLExtendedFetch** not SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性は、この引数からブックマークを取得します。 可変長のブックマークをサポートしていませんし、ブックマークからの (0) 以外のオフセットに行セットのフェッチをサポートしていません。  
  
 *RowCountPtr*  
 [出力]実際にフェッチされた行の数を返すバッファーへのポインター。 このバッファーは SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性によって指定されたバッファーと同じ方法で使用されます。 このバッファーでのみ使用**SQLExtendedFetch**です。 によって使用されていない**SQLFetch**または**SQLFetchScroll**です。  
  
 *RowStatusArray*  
 [出力]行ごとの状態を返す配列へのポインター。 この配列は、SQL_ATTR_ROW_STATUS_PTR ステートメント属性に指定された配列と同じ方法で使用されます。  
  
 ただし、この配列のアドレスは、IRD の SQL_DESC_STATUS_ARRAY_PTR フィールドには格納されません。 さらに、この配列のみが使用**SQLExtendedFetch**および**SQLBulkOperations**で、*操作*SQL_ADD のまたは**SQLSetPos**後に呼び出されたとき**SQLExtendedFetch**です。 によって使用されていない**SQLFetch**または**SQLFetchScroll**で使用されていないと**SQLBulkOperations**または**SQLSetPos**後に呼び出されるとき**SQLFetch**または**SQLFetchScroll**です。 ない場合に使用**SQLBulkOperations**で、*操作*SQL_ADD と呼ばれる、フェッチ関数が呼び出される前にします。 つまり、ステートメントの状態 S7 でのみ使用されます。 S5 または S6 ステートメントの状態では使用されません。 詳細については、次を参照してください。[ステートメント遷移](../../../odbc/reference/appendixes/statement-transitions.md)付録 b: ODBC 状態遷移表でします。  
  
 アプリケーションで有効なポインターを提供する必要があります、 *RowStatusArray*引数以外の場合の動作**SQLExtendedFetch**への呼び出しの動作と**SQLBulkOperations**または**SQLSetPos**によってカーソルが位置付けられている後**SQLExtendedFetch**は定義されていません。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLExtendedFetch** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる**SQLError**です。 次の表に、一般的にによって返される SQLSTATE 値**SQLExtendedFetch**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。 単一の列にエラーが発生した場合**SQLGetDiagField**で呼び出すことができる、 *DiagIdentifier* SQL_DIAG_COLUMN_NUMBER; でエラーが発生した列を判断するのと**SQLGetDiagField**で呼び出すことができる、 *DiagIdentifier* SQL_DIAG_ROW_NUMBER その列を含む行を決定するのです。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|文字列または列に対して返されるバイナリ データは、空白でない文字またはバイナリ データが NULL 以外の切り捨てが発生しました。 文字列値が、右側の切り捨てでした。 数値の値が、数の小数部が切り捨てられました。  (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S01|行のエラー|1 つまたは複数の行をフェッチ中にエラーが発生しました。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S06|結果セットには、最初の行セットが返される前に、フェッチしようとしてください。|要求された行セットには、現在の位置が最初の行を超えると、場合の結果セットの開始がオーバー ラップした*FetchOrientation*が SQL_PRIOR または*FetchOrientation*で SQL_RELATIVE が、負の値*FetchOffset*絶対値が現在 SQL_ROWSET_SIZE 小さくします。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S07|小数部の切り捨て|列に対して返されるデータが切り捨てられました。 数値データ型の数値の小数部が切り捨てられました。 時刻、タイムスタンプ、および時刻部分を含む interval データ型の場合は、時間の小数部が切り捨てられました。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|データ値がで指定された C データ型に変換できませんでした*TargetType*で**SQLBindCol**です。|  
|07009|無効な記述子のインデックス|バインドされていた列 0 **SQLBindCol**SQL_UB_OFF に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されたとします。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|22002|インジケーター変数が必要ですが、指定されていません|NULL のデータがフェッチされました列にある*StrLen_or_IndPtr*によって設定**SQLBindCol**が null ポインターでした。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|22003|数値が範囲|(数値または文字列) として 1 つまたは複数の列の数値の値を取得する原因となる (ではなく小数部) 整数部分が切り捨てられる数値。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。<br /><br /> 詳細については、次を参照してください。[間隔と数値のデータ型に関するガイドライン](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md)付録 d: データ型にします。|  
|22007|無効な datetime 形式|結果セット内の文字の列は、日付、時刻、またはタイムスタンプ C 構造にバインドされていたし、列の値が、それぞれに、無効な日付、時刻、またはタイムスタンプ。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|22012|0 による除算です。|算術式の値が返されました、その結果、除算を 0 で。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|22015|間隔のフィールドがオーバーフローしました|真数型または interval SQL 型から C の間隔の種類を割り当てると、先頭のフィールドに有効桁数の損失が発生します。<br /><br /> 間隔 C 型にデータをフェッチするときに、間隔 C 型の SQL の型の値の表現はありませんでした。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|22018|キャストは無効な文字値|C 型が、真数または概数の数値、datetime、または、interval データ型です。列の SQL 型が文字データ型です。列の値がバインドされた C 型の有効なリテラルではありませんでした。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|24000|カーソル状態が無効|*StatementHandle*が実行された状態でしたが、結果セットが関連付けられていない、 *StatementHandle*です。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLError**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*関数が呼び出されたし、再度、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLExtendedFetch**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM)、指定した*StatementHandle*実行された状態ではありませんでした。 最初の呼び出さずに、関数が呼び出された**SQLExecDirect**、 **SQLExecute**、またはカタログ関数。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) **SQLExtendedFetch**で呼び出され、 *StatementHandle*後**SQLFetch**または**SQLFetchScroll**が呼び出されたとの前に**SQLFreeStmt** SQL_CLOSE オプションで呼び出されました。<br /><br /> (DM) **SQLBulkOperations**に対して前に、ステートメントが呼び出されました**SQLFetch**、 **SQLFetchScroll**、または**SQLExtendedFetch**呼び出されましたが、**SQLExtendedFetch**する前に呼び出された**SQLFreeStmt** SQL_CLOSE オプションで呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY106|フェッチの範囲外の型|引数の指定された値 (DM) *FetchOrientation*が無効です。 (「コメント」を参照してください)<br /><br /> 引数*FetchOrientation* sql_fetch_bookmark を指定して、あり SQL_UB_OFF に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されています。<br /><br /> SQL_CURSOR_TYPE ステートメント オプションの値が引数の値と SQL_CURSOR_FORWARD_ONLY、 *FetchOrientation* SQL_FETCH_NEXT でした。<br /><br /> 引数*FetchOrientation* SQL_FETCH_RESUME がします。|  
|HY107|範囲外の行の値|SQL_CURSOR_TYPE ステートメント オプションで指定された値が SQL_CURSOR_KEYSET_DRIVEN、にもかかわらず、SQL_KEYSET_SIZE ステートメント属性を持つ指定された値が 0 より大きいと SQL_ROWSET_SIZE ステートメント属性を持つ指定された値よりも小さい.|  
|HY111|無効なブックマークの値|引数*FetchOrientation*が sql_fetch_bookmark を指定して、で指定されたブックマーク、 *FetchOffset*引数が無効です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースは、指定されたフェッチの型をサポートしていません。<br /><br /> ドライバーまたはデータ ソースがの組み合わせで指定された変換をサポートしていない、 *TargetType*で**SQLBindCol**と対応する列の SQL データ型。 このエラーは、列の SQL データ型は、ドライバー固有の SQL データ型にマップされた場合にのみ適用されます。|  
|HYT00|タイムアウトが発生しました|クエリのタイムアウト時間は、データ ソースには、結果セットが返される前に期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtOption**、SQL_QUERY_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 動作**SQLExtendedFetch**はのものと同じ**SQLFetchScroll**、次の例外。  
  
-   **SQLExtendedFetch**と**SQLFetchScroll**フェッチされた行の数を返します異なる方法を使用します。 **SQLExtendedFetch**にフェッチされた行の数を返します *\*RowCountPtr*です。**SQLFetchScroll** SQL_ATTR_ROWS_FETCHED_PTR が指すバッファーに直接フェッチされた行の数を返します。 詳細については、次を参照してください。、 *RowCountPtr*引数。  
  
-   **SQLExtendedFetch**と**SQLFetchScroll**さまざまな配列の各の行の状態が返されます。 詳細については、次を参照してください。、 *RowStatusArray*引数。  
  
-   **SQLExtendedFetch**と**SQLFetchScroll**さまざまな方法を使用して、ブックマークを取得するときに*FetchOrientation* SQL_FETCH_BOOKMARK がします。 **SQLExtendedFetch**は可変長のブックマークまたはブックマークから 0 以外のオフセットに行セットをフェッチできません。 詳細については、次を参照してください。、 *FetchOffset*引数。  
  
-   **SQLExtendedFetch**と**SQLFetchScroll**別の行セット サイズを使用します。 **SQLExtendedFetch** SQL_ROWSET_SIZE ステートメント属性の値を使用し、 **SQLFetchScroll** SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性の値を使用します。  
  
-   **SQLExtendedFetch**処理のセマンティクスよりも若干異なるエラー **SQLFetchScroll**です。 詳細については、「エラーでの処理」の「コメント」セクションを参照してください[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)です。  
  
-   **SQLExtendedFetch**バインディング オフセット (SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性) をサポートしていません。  
  
-   呼び出す**SQLExtendedFetch**の呼び出しを混在させることはできません**SQLFetch**または**SQLFetchScroll**、場合**SQLBulkOperations**は呼び出されますすべてのフェッチ関数を呼び出す前に**SQLExtendedFetch**カーソルを閉じて再度開くまでに呼び出すことができません。 つまり、 **SQLExtendedFetch**ステートメント状態 S7 でのみ呼び出すことができます。 詳細については、次を参照してください。[ステートメント遷移](../../../odbc/reference/appendixes/statement-transitions.md)付録 b: ODBC 状態遷移表でします。  
  
 アプリケーションを呼び出すと**SQLFetchScroll** ODBC 2 を使用しているときに *.x*ドライバー、ドライバー マネージャーは、マップするには、この呼び出し**SQLExtendedFetch**です。 詳細については、次を参照してください。"SQLFetchScroll および ODBC 2 *.x*ドライバー"で[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)です。  
  
 ODBC 2 で *.x*、 **SQLExtendedFetch**を複数の行をフェッチが呼び出されたと**SQLFetch**を 1 つの行をフェッチが呼び出されました。 ODBC 3 *.x*、その一方で、 **SQLFetch**複数行のフェッチを呼び出すことができます。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Bulk insert、update、または削除操作を実行します。|[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|結果の数を返すセットの列|[SQLNumResultCols 関数](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|行セット内のデータの更新や更新、または結果セット内のデータを削除すると、カーソルを配置します。|[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
