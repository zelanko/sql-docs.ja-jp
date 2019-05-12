---
title: SQLExtendedFetch 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 63030b34e4b607b850f25a67357d62a7184467c8
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2019
ms.locfileid: "65537186"
---
# <a name="sqlextendedfetch-function"></a>SQLExtendedFetch 関数
**準拠**  
 バージョンが導入されました。ODBC 1.0 規格に準拠します。非推奨  
  
 **まとめ**  
 **SQLExtendedFetch**結果セットからデータの指定した行セットをフェッチし、すべてのバインドされた列のデータを返します。 絶対または相対位置にまたはブックマークによる行セットを指定できます。  
  
> [!NOTE]
>  ODBC 3 *.x*、 **SQLExtendedFetch**置き換わりました**SQLFetchScroll**します。 ODBC 3 *.x*アプリケーションは呼び出さないでください**SQLExtendedFetch**; 代わりに呼び出す必要がある**SQLFetchScroll**します。 ドライバー マネージャー マップ**SQLFetchScroll**に**SQLExtendedFetch** ODBC 2 を使用する場合 *.x*ドライバー。 ODBC 3 *.x*ドライバーをサポートする必要があります**SQLExtendedFetch** ODBC 2 を使用する場合は *.x*付けますアプリケーション。 詳細については、「コメント」を参照してくださいと[ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)で付録 g:旧バージョンとの互換性のためのガイドラインをドライバーです。  
  
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
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *FetchOrientation*  
 [入力]フェッチの型。 これは、同じ*FetchOrientation*で**SQLFetchScroll**します。  
  
 *FetchOffset*  
 [入力]フェッチする行の数。 これは、同じ*FetchOffset*で**SQLFetchScroll**、1 つの例外。 ときに*FetchOrientation*は SQL_FETCH_BOOKMARK、 *FetchOffset*は、固定長のブックマークをブックマークからオフセットではなくです。 つまり、 **SQLExtendedFetch** not SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性は、この引数からブックマークを取得します。 可変長のブックマークをサポートしていませんし、ブックマークからのオフセット位置 (0) 以外で行セットのフェッチをサポートしません。  
  
 *RowCountPtr*  
 [出力]実際にフェッチされる行数を返すバッファーへのポインター。 このバッファーは、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性で指定したバッファーと同じ方法で使用されます。 このバッファーでのみ使用**SQLExtendedFetch**します。 によって使用されていない**SQLFetch**または**SQLFetchScroll**します。  
  
 *RowStatusArray*  
 [出力]各行のステータスが返される配列へのポインター。 この配列は、し、SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって指定された配列と同じ方法で使用されます。  
  
 ただし、この配列のアドレスは、IRD の SQL_DESC_STATUS_ARRAY_PTR フィールドには格納されません。 さらに、この配列がでのみ使用される**SQLExtendedFetch**および**SQLBulkOperations**で、*操作*SQL_ADD のまたは**SQLSetPos**後に呼び出されます**SQLExtendedFetch**します。 によって使用されていない**SQLFetch**または**SQLFetchScroll**で使用されていないと**SQLBulkOperations**または**SQLSetPos**後に呼び出されますが**SQLFetch**または**SQLFetchScroll**します。 ない場合に使用**SQLBulkOperations**で、*操作*SQL_ADD の前に呼び出される、フェッチ関数が呼び出されます。 つまり、ステートメントの状態 S7 でのみ使用されます。 S5 または S6 ステートメントの状態では使用されません。 詳細については、次を参照してください[ステートメントの遷移](../../../odbc/reference/appendixes/statement-transitions.md)で付録 b:。ODBC の状態遷移のテーブル。  
  
 アプリケーションで有効なポインターを提供する必要があります、 *RowStatusArray*引数かどうかの動作**SQLExtendedFetch**への呼び出しの動作と**SQLBulkOperations**または**SQLSetPos**によってカーソルが位置付けられている後**SQLExtendedFetch**は定義されていません。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLExtendedFetch** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します、関連付けられた SQLSTATE 値を呼び出すことによって取得できる**SQLError**します。 次の表に、一般的にによって返される SQLSTATE 値**SQLExtendedFetch** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。 1 つの列でエラーが発生した場合**SQLGetDiagField**で呼び出すことができます、 *DiagIdentifier* SQL_DIAG_COLUMN_NUMBER; でエラーが発生した列を判断するのと**SQLGetDiagField**で呼び出すことができます、 *DiagIdentifier* SQL_DIAG_ROW_NUMBER その列を含む行を決定するのです。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|文字列またはバイナリ データの列に対して返される空白文字または NULL 以外のバイナリ データの切り捨てが発生しました。 文字列値がいた場合は、右側から切り捨てられますことでした。 数値を指定した場合、数値の小数部が切り捨てられました。  (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S01|行内のエラー|1 つまたは複数の行をフェッチ中にエラーが発生しました。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S06|結果セットには、最初の行セットが返される前に、フェッチしようとしてください。|要求された行セットには、現在の位置が最初の行を超えると、場合の結果セットの開始がオーバー ラップした*FetchOrientation*が SQL_PRIOR または*FetchOrientation*で SQL_RELATIVE が、負の値*FetchOffset*絶対値が現在 SQL_ROWSET_SIZE 小さい。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S07|分数が切り捨てられました|列に対して返されるデータが切り捨てられました。 数値データ型、数値の小数部が切り捨てられました。 時刻、タイムスタンプ、および時間コンポーネントを含む interval データ型の場合は、時間の小数部が切り捨てられました。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|C データ型を指定するデータ値を変換できません*TargetType*で**SQLBindCol**します。|  
|07009|無効な記述子のインデックス|バインドされた列 0 **SQLBindCol**SQL_ATTR_USE_BOOKMARKS のステートメント属性 SQL_UB_OFF に設定されているとします。|  
|08S01|通信リンク エラー|関数が完了した処理の前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクに失敗しました。|  
|22002|インジケーター変数が必要ですが、指定されていません|NULL データのフェッチの列にある*StrLen_or_IndPtr*によって設定**SQLBindCol**が null ポインター。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|22003|数値が範囲外|(数値または文字列) として 1 つまたは複数の列の数値の値を取得する原因となる (ではなく小数部) 整数部分が切り捨てられる数値。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。<br /><br /> 詳細については、次を参照してください[間隔と数値データ型に関するガイドライン](../../../odbc/reference/appendixes/guidelines-for-interval-and-numeric-data-types.md)付録 d:。データ型。|  
|22007|無効な datetime 形式|結果セット内の文字の列は、日付、時刻、またはタイムスタンプ C 構造体にバインドされましたし、列の値が、それぞれ、無効な日付、時刻、またはタイムスタンプ。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|22012|0 による除算|算術式の値がによって返される、その結果、除算 0。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|22015|Interval フィールド オーバーフロー|真数型または interval SQL 型から C の間隔の種類への割り当てと、先頭のフィールドに有効桁数の損失が発生します。<br /><br /> C の間隔の種類にデータをフェッチするときに C の間隔の種類の SQL 型の値の表現はありませんでした。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|22018|キャストの無効な文字の値|C 型は、真数または概数の数値、datetime、またはデータ間隔の種類。列の SQL 型が文字データ型。列の値がバインドされた C 型の有効なリテラルではありませんでした。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|24000|カーソル状態が無効|*StatementHandle* 、実行の状態でしたが、結果セットが関連付けられていない、 *StatementHandle*します。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLError**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効に、 *StatementHandle*します。 関数が呼び出された、および実行を完了する前に**SQLCancel**または**SQLCancelHandle**が呼び出されて、 *StatementHandle*関数が呼び出された後、もう一度、 *StatementHandle*します。<br /><br /> 関数が呼び出された、および実行を完了する前に**SQLCancel**または**SQLCancelHandle**が呼び出されて、 *StatementHandle*から別のスレッドで、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM) を非同期的に実行中の関数が呼び出された接続ハンドルに関連付けられているため、 *StatementHandle*します。 この非同期関数ではときに実行されている、 **SQLExtendedFetch**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に対して呼び出された、 *StatementHandle* SQL_PARAM_DATA_ を返されます。ご利用いただけます。 ストリームのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM)、指定した*StatementHandle*実行の状態ではありませんでした。 最初に呼び出さず、関数が呼び出された**SQLExecDirect**、 **SQLExecute**、またはカタログ関数。<br /><br /> (DM) を非同期的に実行中の関数 (いないこの"1") が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**に対して呼び出された、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) **SQLExtendedFetch**に対して呼び出された、 *StatementHandle*後**SQLFetch**または**SQLFetchScroll**が呼び出された前に**SQLFreeStmt** SQL_CLOSE オプションで呼び出されました。<br /><br /> (DM) **SQLBulkOperations**の前にステートメントが呼び出された**SQLFetch**、 **SQLFetchScroll**、または**SQLExtendedFetch**が呼び出されると**SQLExtendedFetch**する前に呼び出された**SQLFreeStmt** SQL_CLOSE オプションで呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY106|フェッチの範囲外の型|引数に指定された値 (DM) *FetchOrientation*が無効です。 (「コメントです」を参照してください)<br /><br /> 引数*FetchOrientation* SQL_FETCH_BOOKMARK、あり SQL_UB_OFF に SQL_ATTR_USE_BOOKMARKS ステートメントの属性が設定されています。<br /><br /> SQL_CURSOR_TYPE ステートメント オプションの値が SQL_CURSOR_FORWARD_ONLY、および引数の値*FetchOrientation* SQL_FETCH_NEXT でした。<br /><br /> 引数*FetchOrientation* SQL_FETCH_RESUME でした。|  
|HY107|行の値が範囲外|SQL_CURSOR_TYPE ステートメントのオプションで指定された値が、SQL_CURSOR_KEYSET_DRIVEN であるにもかかわらず、SQL_KEYSET_SIZE ステートメント属性で指定された値が 0 より大きいと、SQL_ROWSET_SIZE ステートメント属性で指定された値よりも小さい.|  
|HY111|無効なブックマーク値|引数*FetchOrientation*が SQL_FETCH_BOOKMARK とで指定されたブックマーク、 *FetchOffset*引数が無効です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースは、指定されたフェッチの型をサポートしていません。<br /><br /> ドライバーまたはデータ ソースの組み合わせで指定された変換をサポートしていません、 *TargetType*で**SQLBindCol**と対応する列の SQL データ型。 このエラーは、列の SQL データ型は、ドライバー固有の SQL データ型にマップされていた場合にのみ適用されます。|  
|HYT00|タイムアウトが発生しました|データ ソースには、結果セットが返される前に、クエリのタイムアウト期間が終了しました。 によって、タイムアウト期間が設定されます**SQLSetStmtOption**、SQL_QUERY_TIMEOUT します。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 動作**SQLExtendedFetch**と同じですが**SQLFetchScroll**、次の例外。  
  
-   **SQLExtendedFetch**と**SQLFetchScroll**さまざまな方法を使用して、フェッチされた行の数を返します。 **SQLExtendedFetch**でフェッチされた行の数を返します *\*RowCountPtr*;**SQLFetchScroll** SQL_ATTR_ROWS_FETCHED_PTR が指すバッファーに直接フェッチされた行の数を返します。 詳細については、次を参照してください。、 *RowCountPtr*引数。  
  
-   **SQLExtendedFetch**と**SQLFetchScroll**さまざまな配列の各行のステータスを返します。 詳細については、次を参照してください。、 *RowStatusArray*引数。  
  
-   **SQLExtendedFetch**と**SQLFetchScroll**さまざまな方法を使用して、ブックマークを取得するときに*FetchOrientation* SQL_FETCH_BOOKMARK です。 **SQLExtendedFetch**可変長のブックマークやブックマークから 0 以外のオフセットのフェッチの行セットをサポートしません。 詳細については、次を参照してください。、 *FetchOffset*引数。  
  
-   **SQLExtendedFetch**と**SQLFetchScroll**別の行セットのサイズを使用します。 **SQLExtendedFetch** SQL_ROWSET_SIZE ステートメント属性の値を使用し、 **SQLFetchScroll** SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性の値を使用します。  
  
-   **SQLExtendedFetch**が処理のセマンティクスがよりも若干異なるエラー **SQLFetchScroll**します。 詳細については、の [コメント] セクションでは「エラー処理」を参照してください[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)します。  
  
-   **SQLExtendedFetch**バインディングのオフセット (SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性) をサポートしていません。  
  
-   呼び出す**SQLExtendedFetch**への呼び出しを混在させることはできません**SQLFetch**または**SQLFetchScroll**、場合**SQLBulkOperations**が呼び出されますすべてのフェッチ関数が呼び出される前に**SQLExtendedFetch**カーソルを閉じてから再度開くまでに呼び出すことはできません。 つまり、 **SQLExtendedFetch**ステートメント状態 S7 でのみ呼び出すことができます。 詳細については、次を参照してください[ステートメントの遷移](../../../odbc/reference/appendixes/statement-transitions.md)で付録 b:。ODBC の状態遷移のテーブル。  
  
 アプリケーションを呼び出すと**SQLFetchScroll** 、ODBC 2 を使用しているときに *.x*ドライバー、ドライバー マネージャーは、マップするには、この呼び出し**SQLExtendedFetch**します。 詳細については、次を参照してください。"SQLFetchScroll および ODBC 2 *.x*ドライバー"で[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)します。  
  
 ODBC 2 *.x*、 **SQLExtendedFetch**を複数の行のフェッチが呼び出されたと**SQLFetch**を 1 つの行のフェッチが呼び出されました。 ODBC 3 *.x*、その一方で、 **SQLFetch**複数行のフェッチを呼び出すことができます。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|バッファーを結果セット内の列にバインドします。|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Bulk insert、update、または削除操作を実行します。|[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|ステートメントの処理をキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|結果の数を返すセットの列|[SQLNumResultCols 関数](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|カーソルを配置する、行セットのデータの更新や更新、または、結果セット内のデータを削除します。|[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
