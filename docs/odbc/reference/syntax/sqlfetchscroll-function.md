---
title: "SQLFetchScroll 関数 |Microsoft ドキュメント"
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
- SQLFetchScroll
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFetchScroll
helpviewer_keywords:
- SQLFetchScroll function [ODBC]
ms.assetid: c0243667-428c-4dda-ae91-3c307616a1ac
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 79224469fe1e6e4f0840eceb394b30cec63fcd2a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlfetchscroll-function"></a>SQLFetchScroll 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLFetchScroll**結果セットからデータの指定した行セットをフェッチされ、すべてのバインドされた列のデータを返します。 絶対または相対位置にまたはブックマークによる行セットを指定できます。  
  
 ドライバー マネージャーは、マップするには、この関数で ODBC 2.x ドライバーを使用するときに**SQLExtendedFetch**です。 詳細については、次を参照してください。[アプリケーションの旧バージョンと互換性を保つための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLFetchScroll(  
      SQLHSTMT      StatementHandle,  
      SQLSMALLINT   FetchOrientation,  
      SQLLEN        FetchOffset);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *FetchOrientation*  
 [入力]  
  
 フェッチの種類です。  
  
 SQL_FETCH_NEXT  
  
 SQL_FETCH_PRIOR  
  
 SQL_FETCH_FIRST  
  
 SQL_FETCH_LAST  
  
 SQL_FETCH_ABSOLUTE  
  
 SQL_FETCH_RELATIVE  
  
 SQL_FETCH_BOOKMARK  
  
 詳細については、"位置指定、Cursor"「コメント」セクションを参照してください。  
  
 *FetchOffset*  
 [入力]  
  
 フェッチする行の数です。 この引数の解釈は、の値によって異なります、 *FetchOrientation*引数。 詳細については、"位置指定、Cursor"「コメント」セクションを参照してください。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLFetchScroll** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる**SQLGetDiagRec** HandleType の SQL_HANDLE_STMT とのハンドルStatementHandle です。 次の表に、一般的にによって返される SQLSTATE 値**SQLFetchScroll**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。 単一の列にエラーが発生した場合**SQLGetDiagField** ; でエラーが発生した列を調べるに SQL_DIAG_COLUMN_NUMBER DiagIdentifier ので呼び出されると**SQLGetDiagField**呼び出すことができます行を決定する SQL_DIAG_ROW_NUMBER DiagIdentifier のでは、その列を含むです。  
  
 すべてこれら SQLSTATEs SQL_SUCCESS_WITH_INFO または SQL_ERROR (を除く 01xxx SQLSTATEs) を返すことができる、SQL_SUCCESS_WITH_INFO が返されますでエラーが発生した場合は、SQL_ERROR が返されます複数行の操作の 1 つまたは複数の、は、すべての行にエラーが発生した場合、。単一行の操作です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|文字列または列に対して返されるバイナリ データは、空白でない文字またはバイナリ データが NULL 以外の切り捨てが発生しました。 文字列値が、右側の切り捨てでした。|  
|01S01|行のエラー|1 つまたは複数の行をフェッチ中にエラーが発生しました。<br /><br /> (ODBC 3 時に、この SQLSTATE が返される場合は*.x* ODBC 2 を利用するアプリケーション*.x*ドライバー、無視することができます)。|  
|01S06|結果セットには、最初の行セットが返される前に、フェッチしようとしてください。|要求された行セットには、FetchOrientation SQL_FETCH_PRIOR が、現在の位置が最初の行を超える行がおよび、現在の行の数が行セットのサイズに等しいまたはそれよりも少ない場合の結果セットの開始が重なり合っています。<br /><br /> 要求された行セットには、FetchOrientation SQL_FETCH_PRIOR、現在の位置が結果セットの末尾を越えるがれ、行セットのサイズが、結果セットのサイズよりも大きい場合の結果セットの開始が重なり合っています。<br /><br /> 要求された行セットには、FetchOrientation した SQL_FETCH_RELATIVE、FetchOffset が負の値、および FetchOffset の絶対値が行セットのサイズに等しいまたはそれよりも小さい場合の結果セットの開始が重なり合っています。<br /><br /> オーバー ラップ FetchOrientation が SQL_FETCH_ABSOLUTE、FetchOffset が負の値、および FetchOffset の絶対値が結果セットのサイズよりも大きい場合の結果セットの開始を要求された行セットが、行セットのサイズを小さくします。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S07|小数部の切り捨て|列に対して返されるデータが切り捨てられました。 数値データ型の数値の小数部が切り捨てられました。 時刻、タイムスタンプ、および時刻部分を含む interval データ型の場合は、時間の小数部が切り捨てられました。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|結果セット内の列のデータ値がで指定されたデータ型に変換できませんでした*TargetType*で**SQLBindCol**です。<br /><br /> SQL_C_BOOKMARK のデータ型にバインドされていた列 0 と SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されました。<br /><br /> SQL_C_VARBOOKMARK のデータ型にバインドされていた列 0 と SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されませんでした。|  
|07009|無効な記述子のインデックス|ドライバーは ODBC 2*.x*ドライバーをサポートしない**SQLExtendedFetch**列のバインドで指定された列の数が 0 とします。<br /><br /> 列 0 がバインドされているし、SQL_UB_OFF に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されました。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|22001|文字列データで、右側が切り捨てられました|列に対して返さ可変長のブックマークが切り捨てられました。|  
|22002|インジケーター変数が必要ですが、指定されていません|NULL のデータがフェッチされました列にある*StrLen_or_IndPtr*によって設定**SQLBindCol** (またはによって設定 SQL_DESC_INDICATOR_PTR **SQLSetDescField**または**SQLSetDescRec**) が null ポインターでした。|  
|22003|数値が範囲|(数値または文字列) として 1 つまたは複数のバインドされた列の数値を返す原因となる (ではなく小数部) 整数部分が切り捨てられる数値。<br /><br /> 詳細については、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)で[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)です。|  
|22007|無効な datetime 形式|結果セット内の文字の列は、日付、時刻、またはタイムスタンプ C 構造にバインドされていたし、列の値が、それぞれに、無効な日付、時刻、またはタイムスタンプ。|  
|22012|0 による除算です。|算術式の値が返されました、その結果、除算を 0 で。|  
|22015|間隔のフィールドがオーバーフローしました|真数型または interval SQL 型から C の間隔の種類を割り当てると、先頭のフィールドに有効桁数の損失が発生します。<br /><br /> 間隔 C 型にデータをフェッチするときに、間隔 C 型の SQL の型の値の表現はありませんでした。|  
|22018|キャストは無効な文字値|C 文字バッファーにバインドされていた、結果セット内の文字の列と列には、バッファーの文字セットの表現が発生しましたない文字が含まれています。<br /><br /> C 型が、真数または概数の数値、datetime、または、interval データ型です。列の SQL 型が文字データ型です。列の値がバインドされた C 型の有効なリテラルではありませんでした。|  
|24000|カーソル状態が無効|*StatementHandle*実行状態でしたが、結果セットが関連付けられていない、 *StatementHandle*です。|  
|40001|シリアル化のエラー|フェッチが実行されたトランザクションは、デッドロックを防ぐために終了しました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、 * \*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLFetchScroll**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM)、指定した*StatementHandle*実行された状態ではありませんでした。 最初の呼び出さずに、関数が呼び出された**SQLExecDirect**、 **SQLExecute**またはカタログ関数。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) **SQLFetch**の呼び出された、 *StatementHandle*後**SQLExtendedFetch**が呼び出されたとする前に**SQLFreeStmt** sql _ と終了 オプションが呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|SQL_ATTR_USE_BOOKMARK ステートメント属性は SQL_UB_VARIABLE に設定され、列 0 の長さは、この結果セットのブックマークの最大の長さと等しいでしたバッファーにバインドされました。 (この長さは、IRD の SQL_DESC_OCTET_LENGTH フィールドで利用可能と呼び出すことによって取得できます**SQLDescribeCol**、 **SQLColAttribute**、または**SQLGetDescField**)。|  
|HY106|フェッチの範囲外の型|DM) FetchOrientation 引数に指定された値が無効でした。<br /><br /> (DM) 引数 FetchOrientation sql_fetch_bookmark を指定して、あり SQL_ATTR_USE_BOOKMARKS ステートメント属性は、SQL_UB_OFF に設定されています。<br /><br /> SQL_ATTR_CURSOR_TYPE ステートメント属性の値はでした SQL_CURSOR_FORWARD_ONLY、および FetchOrientation でした SQL_FETCH_NEXT 引数の値です。<br /><br /> SQL_ATTR_CURSOR_SCROLLABLE ステートメント属性の値はでした SQL_NONSCROLLABLE と FetchOrientation でした SQL_FETCH_NEXT 引数の値です。|  
|HY107|範囲外の行の値|SQL_ATTR_CURSOR_TYPE ステートメント属性で指定された値が SQL_CURSOR_KEYSET_DRIVEN、にもかかわらず、SQL_ATTR_KEYSET_SIZE ステートメント属性を持つ指定された値が 0 より大きいと、SQL_ATTR_ROW_ARRAY_ で指定した値よりも小さいサイズのステートメント属性です。|  
|HY111|無効なブックマークの値|引数 FetchOrientation sql_fetch_bookmark を指定して、SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性の値によって示されるブックマークが無効かが null ポインターでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースがの組み合わせで指定された変換をサポートしていない、 *TargetType*で**SQLBindCol**と対応する列の SQL データ型。|  
|HYT00|タイムアウトが発生しました|要求された結果セットが返されるデータ ソースの前に、クエリのタイムアウト期間が期限切れです。 SQLSetStmtAttr、SQL_ATTR_QUERY_TIMEOUT を通じて、タイムアウト期間が設定されています。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 **SQLFetchScroll**結果セットから指定した行セットを返します。 絶対パスまたは相対位置またはによってブックマーク行セットを指定することができます。 **SQLFetchScroll**結果セットが存在するときにのみ呼び出すことができます: つまり、結果セットを作成する呼び出しの後に、カーソルの前に結果セット全体が閉じられます。 すべての列がバインドされている場合は、これらの列にデータを返します。 アプリケーションには、行の状態配列をフェッチされた行の数を返すバッファーへのポインターが指定されている場合**SQLFetchScroll**もこの情報を返します。 呼び出す**SQLFetchScroll**の呼び出しを混在させることができます**SQLFetch**の呼び出しを混在させることはできませんが、 **SQLExtendedFetch**です。  
  
 詳細については、次を参照してください。[ブロック カーソルを使用して](../../../odbc/reference/develop-app/using-block-cursors.md)と[スクロール可能なカーソルを使用して](../../../odbc/reference/develop-app/using-scrollable-cursors.md)です。  
  
## <a name="positioning-the-cursor"></a>カーソルを配置します。  
 結果セットが作成されると、カーソルが結果セットの開始前に位置付けられます。 **SQLFetchScroll**ブロック カーソルを値に基づいて、 *FetchOrientation*と*FetchOffset*引数次の表に示すようにします。 新しい行セットの開始を決定するための正確な規則は、次のセクションに表示されます。  
  
|FetchOrientation|意味|  
|----------------------|-------------|  
|SQL_FETCH_NEXT|次の行セットを返します。 これは、呼び出すことと同じ**SQLFetch**です。<br /><br /> **SQLFetchScroll**の値を無視*FetchOffset*です。|  
|SQL_FETCH_PRIOR|前の行セットを返します。<br /><br /> **SQLFetchScroll**の値を無視*FetchOffset*です。|  
|SQL_FETCH_RELATIVE|行セットのリターン*FetchOffset*現在の行セットの先頭からです。|  
|SQL_FETCH_ABSOLUTE|行で始まる行セットを返す*FetchOffset*です。|  
|SQL_FETCH_FIRST|結果セット内の最初の行セットを返します。<br /><br /> **SQLFetchScroll**の値を無視*FetchOffset*です。|  
|SQL_FETCH_LAST|結果セットの最後の完全な行セットを返します。<br /><br /> **SQLFetchScroll**の値を無視*FetchOffset*です。|  
|SQL_FETCH_BOOKMARK|SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性によって指定されたブックマークから FetchOffset 行、行セットを返します。|  
  
 ドライバーがすべてフェッチの方向; をサポートする必要はありません。アプリケーションが呼び出す**SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、または (カーソルの種類) に応じて SQL_STATIC_CURSOR_ATTRIBUTES1 の情報の種類にどのフェッチを決定するには向きは、ドライバーによってサポートされます。 アプリケーションは、これらの種類の情報で SQL_CA1_NEXT、SQL_CA1_RELATIVE、SQL_CA1_ABSOLUTE、および WQL_CA1_BOOKMARK ビットマスクを見てください。 さらに、カーソルは順方向専用、FetchOrientation されません、SQL_FETCH_NEXT 場合**SQLFetchScroll** SQLSTATE HY106 を返します (フェッチの範囲外の型)。  
  
 SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性は、行セット内の行の数を指定します。 場合は、行セットをフェッチする**SQLFetchScroll**結果セットの末尾が重複しています**SQLFetchScroll**部分的な行セットを返します。 つまり、S + R – 1 L より大きい、S はフェッチされる行セット、R の開始行は、行セットのサイズ、および L は、最後は行の結果セットにし、最初の L – のみ場合 S + 行セットの 1 行が有効です。 残りの行は空であり、SQL_ROW_NOROW の状態を持っています。  
  
 後に**SQLFetchScroll** 、現在の行は、行セットの最初の行を返します。  
  
## <a name="cursor-positioning-rules"></a>カーソル位置の規則  
 次のセクションでは、FetchOrientation の各値の正確な規則について説明します。 これらのルールは、次の表記を使用します。  
  
|表記法|意味|  
|--------------|-------------|  
|*開始する前に*|ブロック カーソルが結果セットの開始前に位置付けられます。 場合は、新しい行セットの最初の行は結果セットの開始前に、 **SQLFetchScroll** SQL_NO_DATA が返されます。|  
|*末尾の後に*|ブロック カーソルが結果の末尾を設定後します。 場合は、新しい行セットの最初の行が結果セットの終了後は**SQLFetchScroll** SQL_NO_DATA が返されます。|  
|*CurrRowsetStart*|現在の行セットの最初の行の数。|  
|*LastResultRow*|結果セットの最後の行の数。|  
|*複合カーソル*|行セットのサイズ。|  
|*FetchOffset*|値、 *FetchOffset*引数。|  
|*BookmarkRow*|SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性によって指定されたブックマークに対応する行。|  
  
## <a name="sqlfetchnext"></a>SQL_FETCH_NEXT  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*開始する前に*|1|  
|*CurrRowsetStart + 複合カーソル*[1] * \<LastResultRow を =*|*CurrRowsetStart + 複合カーソル*[1]|  
|*CurrRowsetStart + 複合カーソル*[1]*> LastResultRow*|*末尾の後に*|  
|*末尾の後に*|*末尾の後に*|  
  
 [1] 行セットのサイズは、行をフェッチする前の呼び出し以降変更されているが場合、前の呼び出しで使用した行セット サイズです。  
  
## <a name="sqlfetchprior"></a>SQL_FETCH_PRIOR  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*開始する前に*|*開始する前に*|  
|*CurrRowsetStart = 1*|*開始する前に*|  
|*1 < CurrRowsetStart < = 複合カーソル* <sup>[2]。</sup>|*1* <sup>[1]</sup>|  
|*CurrRowsetStart > 複合カーソル* <sup>[2]</sup>|*CurrRowsetStart – 複合カーソル* <sup>[2]</sup>|  
|*終了と LastResultRow 後 < 複合カーソル* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*終了と LastResultRow 後 > = 複合カーソル* <sup>[2]</sup>|*LastResultRow – 複合カーソルは + 1* <sup>[2]。</sup>|  
  
 [1] **SQLFetchScroll** SQLSTATE 01S06 を返します (結果セットには、最初の行セットが返される前に、フェッチしようとしています) と、SQL_SUCCESS_WITH_INFO です。  
  
 [2]、行セット サイズが行をフェッチする前の呼び出し以降変更されて、これが新しい行セットのサイズ。  
  
## <a name="sqlfetchrelative"></a>SQL_FETCH_RELATIVE  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*(開始前に、および FetchOffset > 0)または (末尾および FetchOffset の後に < 0)*|*--* <sup>[1]</sup>|  
|*BeforeStart と FetchOffset < = 0*|*開始する前に*|  
|*CurrRowsetStart = 1 AND FetchOffset < 0*|*開始する前に*|  
|*CurrRowsetStart AND CurrRowsetStart + FetchOffset > 1 < 1 AND & #124 です。FetchOffset & #124 です。> 複合カーソル* <sup>[3]</sup>|*開始する前に*|  
|*CurrRowsetStart AND CurrRowsetStart + FetchOffset > 1 < 1 AND & #124 です。FetchOffset & #124 です。< = 複合カーソル* <sup>[3]</sup>|*1* <sup>[2]</sup>|  
|*1 < = CurrRowsetStart + FetchOffset \<LastResultRow を =*|*CurrRowsetStart + FetchOffset*|  
|*CurrRowsetStart + FetchOffset > LastResultRow*|*末尾の後に*|  
|*終了と FetchOffset 後 > 0 を =*|*末尾の後に*|  
  
 [1] ***SQLFetchScroll*** FetchOrientation SQL_FETCH_ABSOLUTE に設定が呼び出された場合と同じ行セットを返します。 詳細については、「SQL_FETCH_ABSOLUTE」セクションを参照してください。  
  
 [2] **SQLFetchScroll** SQLSTATE 01S06 を返します (結果セットには、最初の行セットが返される前に、フェッチしようとしています) と SQL_SUCCESS_WITH_INFO です。  
  
 [3]、行セット サイズが行をフェッチする前の呼び出し以降変更されて場合、は、新しい行セット サイズになります。  
  
## <a name="sqlfetchabsolute"></a>SQL_FETCH_ABSOLUTE  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*FetchOffset < 0 AND & #124 です。FetchOffset & #124 です。< LastResultRow を =*|*LastResultRow + FetchOffset + 1*|  
|*FetchOffset < 0 AND & #124 です。FetchOffset & #124 です。> LastResultRow AND & #124 です。FetchOffset & #124 です。> 複合カーソル* <sup>[2]</sup>|*開始する前に*|  
|*FetchOffset < 0 AND & #124 です。FetchOffset & #124 です。> LastResultRow AND & #124 です。FetchOffset & #124 です。< = 複合カーソル* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*FetchOffset 0 を =*|*開始する前に*|  
|*1 < = FetchOffset \<LastResultRow を =*|*FetchOffset*|  
|*FetchOffset > LastResultRow*|*末尾の後に*|  
  
 [1] **SQLFetchScroll** SQLSTATE 01S06 を返します (結果セットには、最初の行セットが返される前に、フェッチしようとしています) と、SQL_SUCCESS_WITH_INFO です。  
  
 [2]、行セット サイズが行をフェッチする前の呼び出し以降変更されて、これが新しい行セットのサイズ。  
  
 動的カーソル内の行の位置が決定されないために、動的カーソルに対して実行される絶対フェッチは、必要な結果を提供できません。 このような操作は、fetch relative です。 続いて、最初のフェッチに相当ありません分割不可能な操作は、静的カーソルで絶対フェッチします。  
  
## <a name="sqlfetchfirst"></a>SQL_FETCH_FIRST  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*任意*|*1*|  
  
## <a name="sqlfetchlast"></a>SQL_FETCH_LAST  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*複合カーソル* <sup>[1]</sup> < LastResultRow を =|*LastResultRow – 複合カーソルは + 1* <sup>[1]</sup>|  
|*複合カーソル* <sup>[1]</sup> > LastResultRow|*1*|  
  
 [1] 行セットのサイズは、行をフェッチする前の呼び出し以降変更されているが場合、これは、新しい行セットのサイズ。  
  
## <a name="sqlfetchbookmark"></a>SQL_FETCH_BOOKMARK  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*BookmarkRow + FetchOffset < 1*|*開始する前に*|  
|*1 < = BookmarkRow + FetchOffset \<LastResultRow を =*|*BookmarkRow + FetchOffset*|  
|*BookmarkRow + FetchOffset > LastResultRow*|*末尾の後に*|  
  
 ブックマークの詳細については、次を参照してください。[ブックマーク (ODBC)](../../../odbc/reference/develop-app/bookmarks-odbc.md)です。  
  
## <a name="effect-of-deleted-added-and-error-rows-on-cursor-movement"></a>カーソルの動きで、エラー行と削除、追加などの影響  
 静的カーソルとキーセット ドリブン カーソルは、結果に追加された行に設定し、結果セットから削除された行を削除を検出する場合があります。 呼び出して**SQLGetInfo** SQL_STATIC_CURSOR_ATTRIBUTES2 と SQL_KEYSET_CURSOR_ATTRIBUTES2 オプションし、SQL_CA2_SENSITIVITY_ADDITIONS、SQL_CA2_SENSITIVITY_DELETIONS、および SQL_CA2_SENSITIVITY_ を見る更新プログラムのビットマスク、アプリケーションでは、特定のドライバーによって実装されるカーソルが、これを行うかどうかを決定します。 削除された行を検出し、それらを削除するドライバーの場合、次の段落はこの動作の影響について説明します。 削除された行を検出できますが、削除されることはドライバーでは、削除がカーソルの動作に影響を与えるなく、次の段落は適用されません。  
  
 カーソル結果セットに追加された行を検出または結果セットから削除された行を削除、データをフェッチするときにのみこれらの変更が検出された場合のように表示されます。 これには、大文字と小文字が含まれますと**SQLFetchScroll**が FetchOrientation SQL_FETCH_RELATIVE および 0 に設定すると、同じ行セットを再フェッチ FetchOffset に設定して呼び出されましたが、SQLSetPos fOption sql _ に設定を呼び出すときに大文字と小文字は含まれません更新します。 後者の場合、行セットのバッファーでデータを更新するが再フェッチされません、および削除された行は結果セットから削除されません。 したがって、行がから削除されるか、現在の行セットに挿入された、カーソルによって行セットのバッファーは変更されません。 代わりに、すべての行セットをフェッチにしたときに、変更、削除された行が含まれていたまたは挿入された行が含まれていますが検出されます。  
  
 例:  
  
```  
// Fetch the next rowset.  
SQLFetchScroll(hstmt, SQL_FETCH_NEXT, 0);  
// Delete third row of the rowset. Does not modify the rowset buffers.  
SQLSetPos(hstmt, 3, SQL_DELETE, SQL_LOCK_NO_CHANGE);  
// The third row has a status of SQL_ROW_DELETED after this call.  
SQLSetPos(hstmt, 3, SQL_REFRESH, SQL_LOCK_NO_CHANGE);  
// Refetch the same rowset. The third row is removed, replaced by what  
// was previously the fourth row.  
SQLFetchScroll(hstmt, SQL_FETCH_RELATIVE, 0);  
```  
  
 ときに**SQLFetchScroll**を現在の行セットに対する相対位置を持つ新しい行セットを返します: その FetchOrientation は SQL_FETCH_NEXT、SQL_FETCH_PRIOR、または SQL_FETCH_RELATIVE: 現在の行セットへの変更は含まれません新しい行セットの開始位置を計算するときに ただし場合に、検出することは現在の行セットの外部で変更が含まれてです。 さらに、 **SQLFetchScroll**を現在の行セットの独立した位置を持つ新しい行セットを返します — FetchOrientation は SQL_FETCH_FIRST、SQL_FETCH_LAST、SQL_FETCH_ABSOLUTE、または sql_fetch_bookmark を指定して、つまり、:、現在の行セットである場合でも、検出は、すべての変更が含まれます。  
  
 新しく追加された行が現在の行セットの内外かどうかを決定するときに行セットの一部と見なされます。 最後の有効な行で終了対象の行の状態が SQL_ROW_NOROW 最後の行は、します。 たとえば、カーソルが新しく追加された行を検出できる、現在の行セットは行セットの一部、アプリケーションは、新しい行を追加、およびカーソルが結果セットの末尾にこれらの行を追加します。 アプリケーションを呼び出す場合**SQLFetchScroll** FetchOrientation SQL_FETCH_NEXT に設定と**SQLFetchScroll**最初の新しく追加された行で始まる行セットを返します。  
  
 たとえば、現在の行セットは 21 から 30 の行で構成、行セットのサイズは 10、カーソルが結果セットから削除された行を削除、カーソルが結果セットに追加された行を検出します。 次の表は、行**SQLFetchScroll**さまざまな状況で返します。  
  
|変更|フェッチの型|FetchOffset|新しい行セット [1]|  
|------------|----------------|-----------------|---------------------|  
|21 行を削除します。|NEXT|0|31 ~ 40|  
|31 の行を削除します。|NEXT|0|32 を 41|  
|行 21、22 の間に行を挿入します。|NEXT|0|31 ~ 40|  
|行 30、31 の間に行を挿入します。|NEXT|0|挿入された行を 31 に 39|  
|21 行を削除します。|PRIOR|0|11 ~ 20|  
|20 行を削除します。|PRIOR|0|10 ~ 19|  
|行 21、22 の間に行を挿入します。|PRIOR|0|11 ~ 20|  
|行 20 と 21 の間に行を挿入します。|PRIOR|0|12 ~ 20 挿入された行|  
|21 行を削除します。|RELATIVE|0|22 ~ 31<sup>[2]</sup>|  
|21 行を削除します。|RELATIVE|1|22 ~ 31|  
|行 21、22 の間に行を挿入します。|RELATIVE|0|挿入された行、21、22 ~ 29|  
|行 21、22 の間に行を挿入します。|RELATIVE|1|22 ~ 31|  
|21 行を削除します。|ABSOLUTE|21|22 ~ 31<sup>[2]</sup>|  
|22 の行を削除します。|ABSOLUTE|21|21、23 ~ 31|  
|行 21、22 の間に行を挿入します。|ABSOLUTE|22|挿入された行、22 ~ 29|  
  
 [1] この列は、すべての行が挿入または削除する前に、行番号を使用します。  
  
 [2] この場合は、カーソルは、21 の行で始まる行を返そうとします。 21 の行が削除されたため最初の行が返されます、行 22 です。  
  
 エラー行 (つまり、状態の行 SQL_ROW_ERROR) は、カーソルの移動には影響しません。 たとえば、現在の行セットは 11 行目との状態で開始した場合に、行 11 が SQL_ROW_ERROR、呼び出す**SQLFetchScroll** FetchOrientation SQL_FETCH_RELATIVE と FetchOffset に設定とは、5 に設定されては 16 ですが、行で始まる行セットを返します。同様に 11 行目の状態が SQL_SUCCESS の場合。  
  
## <a name="returning-data-in-bound-columns"></a>バインドされた列内のデータを返す  
 **SQLFetchScroll**と同じ方法でバインドされた列のデータを返します**SQLFetch**です。 詳細についてを参照してください「を返すデータにバインドされている列」 [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)です。  
  
 列がバインドされていない場合**SQLFetchScroll**データは返されませんが、指定した位置に、ブロック カーソルでは移動します。 ブロックのカーソルの非バインド列からデータを取得できるかどうか**SQLGetData**ドライバーに依存します。 呼び出し、この機能はサポートされて**SQLGetInfo** SQL_GETDATA_EXTENSIONS 情報の種類のビット SQL_GD_BLOCK を返します。  
  
## <a name="buffer-addresses"></a>バッファーのアドレス  
 **SQLFetchScroll**としてのデータと長さ/インジケーター バッファーのアドレスを決定する、同次数式を使用して**SQLFetch**です。 詳細についてを参照してください「バッファー アドレス」 [SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)です。  
  
## <a name="row-status-array"></a>行の状態配列  
 **SQLFetchScroll** SQLFetch と同じ方法で行の状態配列内の値を設定します。 詳細についてを参照してください「の行の状態配列」 [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)です。  
  
## <a name="rows-fetched-buffer"></a>行がフェッチ バッファー  
 **SQLFetchScroll**と同じ方法で行がフェッチ バッファーにフェッチされた行の数を返します**SQLFetch**です。 詳細についてを参照してください「の行がフェッチ バッファー」 [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)です。  
  
## <a name="error-handling"></a>エラー処理  
 アプリケーションを呼び出すと**SQLFetchScroll** ODBC 3.x ドライバー、ドライバー マネージャーで**SQLFetchScroll**ドライバーにします。 アプリケーションを呼び出すと**SQLFetchScroll** driver では、ODBC 2.x、ドライバー マネージャーがドライバーで SQLExtendedFetch を呼び出します。 **SQLFetchScroll** SQLExtendedFetch 少し異なる方法でエラーを処理、アプリケーションが若干異なるエラー動作を呼び出すとき、 **SQLFetchScroll** odbc 2.x、および ODBC3.x ドライバーです。  
  
 **SQLFetchScroll**と同じ方法でエラーと警告を返します**SQLFetch**。 詳細については、"エラーの処理」を参照してください**SQLFetch**です。 **SQLExtendedFetch**と同じ方法でエラーが返されます**SQLFetch**、次の例外。  
  
 警告発生すると、行セット内の特定の行に適用される SQLExtendedFetch SQL_ROW_SUCCESS、SQL_ROW_SUCCESS_WITH_INFO いない行の状態配列内の対応するエントリを設定します。  
  
 行セット内のすべての行にエラーが発生した場合、SQLExtendedFetch はいない SQL_ERROR、SQL_SUCCESS_WITH_INFO を返します。  
  
 SQLExtendedFetch によって返される最初の状態レコードの各グループで状態レコードの個別の行に適用される、SQLSTATE 01S01 を含める必要があります (行でのエラー)。**SQLFetchScroll**この SQLSTATE は返しません。 SQLExtendedFetch を返す追加 SQLSTATEs できない場合は、この SQLSTATE も返す必要があります。  
  
## <a name="sqlfetchscroll-and-optimistic-concurrency"></a>SQLFetchScroll とオプティミスティック同時実行制御  
 カーソルはオプティミスティック同時実行制御を使用している場合、SQL_ATTR_CONCURRENCY ステートメント属性は、SQL_CONCUR_ROWVER、SQL_CONCUR_VALUES またはの値: **SQLFetchScroll**データが使用するオプティミスティック同時実行制御の値を更新行が変更されたかどうかを検出するためにソースです。 これは、発生するたびに**SQLFetchScroll**など、現在の行セットは変わりませんが、新しい行セットをフェッチします。 (使用して呼び出した FetchOrientation SQL_FETCH_RELATIVE および 0 に設定 FetchOffset に設定します。)  
  
## <a name="sqlfetchscroll-and-odbc-2x-drivers"></a>SQLFetchScroll および ODBC 2.x のドライバー  
 アプリケーションを呼び出すと**SQLFetchScroll**では、ODBC 2.x ドライバー、ドライバー マネージャーがこの呼び出しをマップ**SQLExtendedFetch**です。 次の引数の値を渡す**SQLExtendedFetch**です。  
  
|SQLExtendedFetch 引数|値|  
|-------------------------------|-----------|  
|StatementHandle|StatementHandle **SQLFetchScroll**です。|  
|FetchOrientation|FetchOrientation **SQLFetchScroll**です。|  
|FetchOffset|FetchOrientation が sql_fetch_bookmark を指定してに FetchOffset 引数の値ではないかどうかは**SQLFetchScroll**を使用します。<br /><br /> SQL_FETCH_BOOKMARK を FetchOrientation には、SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性によって指定されたアドレスに格納された値が使用されます。|  
|RowCountPtr|SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性によって指定されたアドレスです。|  
|RowStatusArray|SQL_ATTR_ROW_STATUS_PTR ステートメント属性によって指定されたアドレスです。|  
  
 詳細については、次を参照してください。[ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。  
  
## <a name="descriptors-and-sqlfetchscroll"></a>記述子および SQLFetchScroll  
 **SQLFetchScroll**記述子と同じ方法で対話**SQLFetch**です。 詳細についてを参照してください"記述子および SQLFetchScroll" [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)です。  
  
## <a name="code-example"></a>コード例  
 参照してください[列方向のバインド](../../../odbc/reference/develop-app/column-wise-binding.md)、[行方向のバインド](../../../odbc/reference/develop-app/row-wise-binding.md)、 [Update および Delete ステートメントを配置](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)、および[SQLSetPosで行セット内の行を更新](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Bulk insert、update、または削除操作を実行します。|[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|1 つの行または順方向専用の方向にデータのブロックをフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|ステートメントでカーソルを閉じる|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|結果の数を返すセットの列|[SQLNumResultCols 関数](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|行セット内のデータの更新や更新、または結果セット内のデータを削除すると、カーソルを配置します。|[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

