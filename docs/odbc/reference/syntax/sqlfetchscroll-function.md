---
title: SQLFetchScroll 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 20a1580503ad141817edcf8e01772dfcc8dc39a3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537355"
---
# <a name="sqlfetchscroll-function"></a>SQLFetchScroll 関数
**準拠**  
 バージョンが導入されました。ODBC 3.0 規格に準拠します。ISO 92  
  
 **まとめ**  
 **SQLFetchScroll**結果セットからデータの指定した行セットをフェッチし、すべてのバインドされた列のデータを返します。 絶対または相対位置にまたはブックマークによる行セットを指定できます。  
  
 ドライバー マネージャーがマップには、この関数で odbc 2.x を使用する場合**SQLExtendedFetch**します。 詳細については、次を参照してください。[アプリケーションの旧バージョンと互換性のマッピング置換関数](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
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
  
 詳細については、「配置、カーソルを」「コメント」セクションを参照してください。  
  
 *FetchOffset*  
 [入力]  
  
 フェッチする行の数。 この引数の解釈の値によって異なります、 *FetchOrientation*引数。 詳細については、「配置、カーソルを」「コメント」セクションを参照してください。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLFetchScroll** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる**SQLGetDiagRec** HandleType の sql_handle_stmt としてとのハンドルStatementHandle します。 次の表に、一般的にによって返される SQLSTATE 値**SQLFetchScroll** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。 1 つの列でエラーが発生した場合**SQLGetDiagField** ; でエラーが発生した列を決定する SQL_DIAG_COLUMN_NUMBER DiagIdentifier を呼び出すことができますと**SQLGetDiagField**呼び出すことができます行を決定する SQL_DIAG_ROW_NUMBER DiagIdentifier のでは、その列を含むです。  
  
 複数行の操作の 1 つ以上のただしすべてではなく行にエラーが発生した場合にエラーが発生した場合、SQL_ERROR が返されますをすべてその SQLSTATEs SQL_SUCCESS_WITH_INFO または SQL_ERROR (を除く 01xxx SQLSTATEs) を返すことができる、SQL_SUCCESS_WITH_INFO が返される、単一行の操作です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|文字列またはバイナリ データの列に対して返される空白文字または NULL 以外のバイナリ データの切り捨てが発生しました。 文字列値がいた場合は、右側から切り捨てられますことでした。|  
|01S01|行内のエラー|1 つまたは複数の行をフェッチ中にエラーが発生しました。<br /><br /> (この SQLSTATE が返されない場合、ODBC 3 *.x*アプリケーションの操作は、ODBC 2 *.x*ドライバー、無視できます)。|  
|01S06|結果セットには、最初の行セットが返される前に、フェッチしようとしてください。|要求された行セットには、FetchOrientation が SQL_FETCH_PRIOR、現在の位置が最初の行を超えるはあり、現在の行の数が行セットのサイズに等しいまたはそれよりも少ない場合の結果セットの開始が重複します。<br /><br /> 要求された行セットには、FetchOrientation SQL_FETCH_PRIOR が、現在の位置が結果セットの末尾を越えるがおよび行セットのサイズが、結果セットのサイズよりも大きい場合の結果セットの開始が重複します。<br /><br /> 要求された行セットには、FetchOrientation した SQL_FETCH_RELATIVE、FetchOffset が負の値、および FetchOffset の絶対値が行セットのサイズに等しいまたはそれよりも小さい場合の結果セットの開始がオーバー ラップします。<br /><br /> 要求された行セットの重複 FetchOrientation が SQL_FETCH_ABSOLUTE、FetchOffset が負の値、および FetchOffset の絶対値が結果セットのサイズよりも大きい場合の結果セットの先頭が行セットのサイズ。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S07|分数が切り捨てられました|列に対して返されるデータが切り捨てられました。 数値データ型、数値の小数部が切り捨てられました。 時刻、タイムスタンプ、および時間コンポーネントを含む interval データ型の場合は、時間の小数部が切り捨てられました。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|指定されたデータ型に結果セット内の列のデータ値を変換でした*TargetType*で**SQLBindCol**します。<br /><br /> SQL_C_BOOKMARK のデータ型にバインドされた列 0 と SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメントの属性が設定されました。<br /><br /> SQL_C_VARBOOKMARK のデータ型にバインドされた列 0 と SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメントの属性が設定されませんでした。|  
|07009|無効な記述子のインデックス|ドライバーが、ODBC 2 *.x*がサポートされていないドライバー **SQLExtendedFetch**列のバインドで指定された列数が 0 とします。<br /><br /> 列 0 がバインドされているし、SQL_UB_OFF に SQL_ATTR_USE_BOOKMARKS ステートメントの属性が設定されました。|  
|08S01|通信リンク エラー|関数が完了した処理の前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクに失敗しました。|  
|22001|文字列データで、右側が切り捨てられました|列に対して返される可変長のブックマークが切り捨てられました。|  
|22002|インジケーター変数が必要ですが、指定されていません|NULL データのフェッチの列にある*StrLen_or_IndPtr*によって設定**SQLBindCol** (またはによって設定 SQL_DESC_INDICATOR_PTR **SQLSetDescField**または**SQLSetDescRec**) が null ポインター。|  
|22003|数値が範囲外|(数値または文字列) として 1 つまたは複数のバインドされた列の数値の値を取得する原因となる (ではなく小数部) 整数部分が切り捨てられる数値。<br /><br /> 詳細については、次を参照してください[SQL から C データ型への変換データ](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)で[付録 d:。データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)します。|  
|22007|無効な datetime 形式|結果セット内の文字の列は、日付、時刻、またはタイムスタンプ C 構造体にバインドされましたし、列の値が、それぞれ、無効な日付、時刻、またはタイムスタンプ。|  
|22012|0 による除算|算術式の値がによって返される、その結果、除算 0。|  
|22015|Interval フィールド オーバーフロー|真数型または interval SQL 型から C の間隔の種類への割り当てと、先頭のフィールドに有効桁数の損失が発生します。<br /><br /> C の間隔の種類にデータをフェッチするときに C の間隔の種類の SQL 型の値の表現はありませんでした。|  
|22018|キャストの無効な文字の値|C 文字バッファーにバインドされた結果セット内の文字の列と列には、対象のバッファーの文字セットで表現がない文字が含まれています。<br /><br /> C 型は、真数または概数の数値、datetime、またはデータ間隔の種類。列の SQL 型が文字データ型。列の値がバインドされた C 型の有効なリテラルではありませんでした。|  
|24000|カーソル状態が無効|*StatementHandle*実行の状態でしたが、結果セットが関連付けられていない、 *StatementHandle*します。|  
|40001|シリアル化エラー|デッドロックを防止するフェッチが実行されたトランザクションが終了しました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を特定できません。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効に、 *StatementHandle*します。 関数が呼び出された、および実行を完了する前に**SQLCancel**または**SQLCancelHandle**が呼び出されて、 *StatementHandle*します。 後でもう一度関数が呼び出された、 *StatementHandle*します。<br /><br /> 関数が呼び出された、および実行を完了する前に**SQLCancel**または**SQLCancelHandle**が呼び出されて、 *StatementHandle*から別のスレッドで、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM) を非同期的に実行中の関数が呼び出された接続ハンドルに関連付けられているため、 *StatementHandle*します。 この非同期関数ではときに実行されている、 **SQLFetchScroll**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に対して呼び出された、 *StatementHandle* SQL_PARAM_DATA_ を返されます。ご利用いただけます。 ストリームのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM)、指定した*StatementHandle*実行の状態ではありませんでした。 最初に呼び出さず、関数が呼び出された**SQLExecDirect**、 **SQLExecute**またはカタログ関数。<br /><br /> (DM) を非同期的に実行中の関数 (いないこの"1") が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**に対して呼び出された、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) **SQLFetch**に対して呼び出された、 *StatementHandle*後**SQLExtendedFetch**が呼び出されたとする前に**SQLFreeStmt**で、sql _終了 オプションが呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|SQL_ATTR_USE_BOOKMARK ステートメント属性は SQL_UB_VARIABLE に設定されており、列 0 がの長さはこの結果セットに対してブックマークの最大の長さと等しくありませんでした。 バッファーにバインドされました。 (この長さは、IRD の SQL_DESC_OCTET_LENGTH フィールドで使用できますし、呼び出すことによって取得できる**SQLDescribeCol**、 **SQLColAttribute**、または**SQLGetDescField**)。|  
|HY106|フェッチの範囲外の型|DM) FetchOrientation 引数に指定された値が無効です。<br /><br /> (DM) 引数 FetchOrientation SQL_FETCH_BOOKMARK、あり SQL_ATTR_USE_BOOKMARKS ステートメント属性は、SQL_UB_OFF に設定されています。<br /><br /> SQL_ATTR_CURSOR_TYPE ステートメント属性の値は、SQL_CURSOR_FORWARD_ONLY、および FetchOrientation は SQL_FETCH_NEXT でした。 引数の値でした。<br /><br /> SQL_ATTR_CURSOR_SCROLLABLE ステートメント属性の値は、SQL_NONSCROLLABLE と FetchOrientation は SQL_FETCH_NEXT でした。 引数の値でした。|  
|HY107|行の値が範囲外|SQL_ATTR_CURSOR_TYPE ステートメント属性で指定された値が、SQL_CURSOR_KEYSET_DRIVEN が SQL_ATTR_KEYSET_SIZE ステートメント属性で指定された値が 0 より大きいと、SQL_ATTR_ROW_ARRAY_ で指定された値よりも小さいサイズのステートメント属性です。|  
|HY111|無効なブックマーク値|引数 FetchOrientation が SQL_FETCH_BOOKMARK、および、SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性の値で示されるブックマークが無効かが null ポインター。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースの組み合わせで指定された変換をサポートしていません、 *TargetType*で**SQLBindCol**と対応する列の SQL データ型。|  
|HYT00|タイムアウトが発生しました|クエリのタイムアウト期間は、要求された結果セットが返されるデータ ソースの前に有効期限が切れました。 SQLSetStmtAttr、SQL_ATTR_QUERY_TIMEOUT を通じて、タイムアウト期間が設定されています。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングは無効です。|通知のモデルを使用すると、常にポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了が呼び出されていません。|通知モードが有効になっている場合、ハンドルでは、前の関数呼び出しに SQL_STILL_EXECUTING が返された場合と**SQLCompleteAsync**後処理を行い、操作を完了するハンドルで呼び出す必要があります。|  
  
## <a name="comments"></a>コメント  
 **SQLFetchScroll**結果セットから指定した行セットを返します。 絶対または相対位置またはブックマークによる行セットを指定できます。 **SQLFetchScroll**呼び出すだけで結果セットが存在します - 中には、結果セットを作成する呼び出しの後に、カーソルの前に結果セット全体が閉じられることができます。 すべての列がバインドされている場合は、これらの列にデータを返します。 アプリケーションには、行の状態配列をフェッチされた行の数を返すバッファーへのポインターが指定した場合**SQLFetchScroll**もこの情報を返します。 呼び出す**SQLFetchScroll**への呼び出しに組み込むことができます**SQLFetch**への呼び出しを混在させることはできませんが、 **SQLExtendedFetch**します。  
  
 詳細については、次を参照してください。[ブロック カーソルを使用して](../../../odbc/reference/develop-app/using-block-cursors.md)と[スクロール可能なカーソルを使用して](../../../odbc/reference/develop-app/using-scrollable-cursors.md)します。  
  
## <a name="positioning-the-cursor"></a>カーソルを配置します。  
 結果セットが作成されると、カーソルは結果セットの開始前にします。 **SQLFetchScroll**の値に基づいて、ブロック カーソルを配置、 *FetchOrientation*と*FetchOffset*引数を次の表に示すようにします。 新しい行セットの開始を決定するための正確な規則は、次のセクションに表示されます。  
  
|FetchOrientation|説明|  
|----------------------|-------------|  
|SQL_FETCH_NEXT|次の行セットを返します。 これは、呼び出しに相当**SQLFetch**します。<br /><br /> **SQLFetchScroll**の値を無視します*FetchOffset*します。|  
|SQL_FETCH_PRIOR|前の行セットを返します。<br /><br /> **SQLFetchScroll**の値を無視します*FetchOffset*します。|  
|SQL_FETCH_RELATIVE|行セットを返す*FetchOffset*現在の行セットの開始から。|  
|SQL_FETCH_ABSOLUTE|行で始まる行セットを返す*FetchOffset*します。|  
|SQL_FETCH_FIRST|結果セット内の最初の行セットを返します。<br /><br /> **SQLFetchScroll**の値を無視します*FetchOffset*します。|  
|SQL_FETCH_LAST|結果セット内の最後の完全な行セットを返します。<br /><br /> **SQLFetchScroll**の値を無視します*FetchOffset*します。|  
|SQL_FETCH_BOOKMARK|SQL_ATTR_FETCH_BOOKMARK_PTR ステートメントの属性で指定されたブックマークから FetchOffset 行、行セットを返します。|  
  
 ドライバーは、フェッチの方向すべて; をサポートする必要はありません。アプリケーションを呼び出す**SQLGetInfo** SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、または (カーソルの種類) に応じて SQL_STATIC_CURSOR_ATTRIBUTES1 の情報の種類でどのフェッチを判断するには向きは、ドライバーでサポートされます。 アプリケーションは、これらの情報の種類で SQL_CA1_NEXT、SQL_CA1_RELATIVE、SQL_CA1_ABSOLUTE、および WQL_CA1_BOOKMARK ビットマスクを見てください。 さらに、カーソルは順方向専用と FetchOrientation SQL_FETCH_NEXT でない場合は、 **SQLFetchScroll** SQLSTATE HY106 を返します (フェッチの範囲外の型)。  
  
 SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性は、行セット内の行の数を指定します。 によって、行セットをフェッチされている場合、 **SQLFetchScroll** 、結果セットの末尾と重なる**SQLFetchScroll**部分的な行セットを返します。 つまり、S + R - L より大きい、S は、開始行フェッチされる行セット、R の行セットのサイズは、あり L は、最後の 1 行の結果セットし、最初の左辺にのみ場合 S + 1 行の行セットは有効です。 残りの行は空であり、sql_row_norow であっての状態を持っています。  
  
 後**SQLFetchScroll** 、現在の行が行セットの最初の行を返します。  
  
## <a name="cursor-positioning-rules"></a>カーソル位置の規則  
 次のセクションでは、FetchOrientation の各値に対して厳密な規則について説明します。 これらのルールは、次の表記を使用します。  
  
|表記法|説明|  
|--------------|-------------|  
|*開始する前に*|ブロック カーソルは結果セットの開始前に配置されます。 新しい行セットの最初の行は、結果セットの開始前に、する場合**SQLFetchScroll** sql_no_data が返されます。|  
|*終了後*|ブロック カーソルは、結果の最後の設定後に配置されます。 場合、新しい行セットの最初の行は、結果セットの終了後**SQLFetchScroll** sql_no_data が返されます。|  
|*CurrRowsetStart*|現在の行セットの最初の行の数。|  
|*LastResultRow*|結果セットの最後の行の数。|  
|*複合カーソル*|行セットのサイズ。|  
|*FetchOffset*|値、 *FetchOffset*引数。|  
|*BookmarkRow*|SQL_ATTR_FETCH_BOOKMARK_PTR ステートメントの属性で指定されたブックマークに対応する行。|  
  
## <a name="sqlfetchnext"></a>SQL_FETCH_NEXT  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*開始する前に*|1|  
|*CurrRowsetStart + RowsetSize*[1] *\<= LastResultRow*|*CurrRowsetStart + 複合カーソル*[1]|  
|*CurrRowsetStart + 複合カーソル*[1] *> LastResultRow*|*終了後*|  
|*終了後*|*終了後*|  
  
 [1] 行をフェッチする前に呼び出した後、行セット サイズが変わっている場合は、前の呼び出しで使用されていた行セット サイズになります。  
  
## <a name="sqlfetchprior"></a>SQL_FETCH_PRIOR  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*開始する前に*|*開始する前に*|  
|*CurrRowsetStart = 1*|*開始する前に*|  
|*1 < CurrRowsetStart < = 複合カーソル* <sup>[2]。</sup>|*1* <sup>[1]</sup>|  
|*CurrRowsetStart > RowsetSize* <sup>[2]</sup>|*CurrRowsetStart - RowsetSize* <sup>[2]</sup>|  
|*終了と LastResultRow 後 < 複合カーソル* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*終了と LastResultRow 後 > = 複合カーソル* <sup>[2]</sup>|*複合カーソルは + 1 - LastResultRow* <sup>[2]。</sup>|  
  
 [1] **SQLFetchScroll** SQLSTATE 01S06 を返します (結果セットには、最初の行セットが返される前に、フェッチしようとしています) と、SQL_SUCCESS_WITH_INFO。  
  
 [2] 行をフェッチする前に呼び出した後、行セット サイズが変わっている場合は、新しい行セット サイズになります。  
  
## <a name="sqlfetchrelative"></a>SQL_FETCH_RELATIVE  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*(開始前に、および FetchOffset > 0)または (終了と FetchOffset 後 < 0)*|*--* <sup>[1]</sup>|  
|*BeforeStart と FetchOffset < = 0*|*開始する前に*|  
|*CurrRowsetStart = 1 AND FetchOffset < 0*|*開始する前に*|  
|*CurrRowsetStart AND CurrRowsetStart + FetchOffset > 1 < 1 AND &#124; FetchOffset &#124; > 複合カーソル* <sup>[3]</sup>|*開始する前に*|  
|*CurrRowsetStart AND CurrRowsetStart + FetchOffset > 1 < 1 AND &#124; FetchOffset &#124; < = 複合カーソル* <sup>[3]</sup>|*1* <sup>[2]</sup>|  
|*1 < = CurrRowsetStart + FetchOffset \<LastResultRow を =*|*CurrRowsetStart + FetchOffset*|  
|*CurrRowsetStart + FetchOffset > LastResultRow*|*終了後*|  
|*終了と FetchOffset 後 > = 0*|*終了後*|  
  
 [1] ***SQLFetchScroll*** FetchOrientation SQL_FETCH_ABSOLUTE に設定で呼び出された場合と同じ行セットを返します。 詳細については、"SQL_FETCH_ABSOLUTE"セクションを参照してください。  
  
 [2] **SQLFetchScroll** SQLSTATE 01S06 を返します (結果セットには、最初の行セットが返される前に、フェッチしようとしています) と、SQL_SUCCESS_WITH_INFO。  
  
 [3] 行をフェッチする前に呼び出した後、行セット サイズが変わっている場合は、新しい行セット サイズになります。  
  
## <a name="sqlfetchabsolute"></a>SQL_FETCH_ABSOLUTE  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*FetchOffset < 0 AND &#124; FetchOffset &#124; < LastResultRow を =*|*LastResultRow FetchOffset + 1*|  
|*FetchOffset < 0 AND &#124; FetchOffset &#124; > LastResultRow AND &#124; FetchOffset &#124; > 複合カーソル* <sup>[2]</sup>|*開始する前に*|  
|*FetchOffset < 0 AND &#124; FetchOffset &#124; > LastResultRow AND &#124; FetchOffset &#124; < = 複合カーソル* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*FetchOffset = 0*|*開始する前に*|  
|*1 < = FetchOffset \<LastResultRow を =*|*FetchOffset*|  
|*FetchOffset > LastResultRow*|*終了後*|  
  
 [1] **SQLFetchScroll** SQLSTATE 01S06 を返します (結果セットには、最初の行セットが返される前に、フェッチしようとしています) と、SQL_SUCCESS_WITH_INFO。  
  
 [2] 行をフェッチする前に呼び出した後、行セット サイズが変わっている場合は、新しい行セット サイズになります。  
  
 動的カーソル内の行位置が決定できないために、動的カーソルに対して実行される絶対フェッチは、必要な結果を提供できません。 このような操作は fetch relative; の順にフェッチに相当静的カーソルで絶対フェッチは分割不可能な操作はありません。  
  
## <a name="sqlfetchfirst"></a>SQL_FETCH_FIRST  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*任意*|*1*|  
  
## <a name="sqlfetchlast"></a>SQL_FETCH_LAST  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*複合カーソル* <sup>[1]</sup> < LastResultRow を =|*複合カーソルは + 1 - LastResultRow* <sup>[1]</sup>|  
|*RowsetSize* <sup>[1]</sup> > LastResultRow|*1*|  
  
 [1] 行をフェッチする前に呼び出した後、行セット サイズが変わっている場合は、新しい行セット サイズになります。  
  
## <a name="sqlfetchbookmark"></a>SQL_FETCH_BOOKMARK  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*BookmarkRow + FetchOffset < 1*|*開始する前に*|  
|*1 < = BookmarkRow + FetchOffset \<LastResultRow を =*|*BookmarkRow + FetchOffset*|  
|*BookmarkRow + FetchOffset > LastResultRow*|*終了後*|  
  
 ブックマークの詳細については、次を参照してください。[ブックマーク (ODBC)](../../../odbc/reference/develop-app/bookmarks-odbc.md)します。  
  
## <a name="effect-of-deleted-added-and-error-rows-on-cursor-movement"></a>削除された、追加などの効果とカーソルの動きのエラー行  
 静的およびキーセット ドリブン カーソルは、結果に追加された行に設定し、結果セットから削除された行の削除を検出する場合があります。 呼び出して**SQLGetInfo** SQL_STATIC_CURSOR_ATTRIBUTES2 と SQL_KEYSET_CURSOR_ATTRIBUTES2 オプションし、SQL_CA2_SENSITIVITY_ADDITIONS、SQL_CA2_SENSITIVITY_DELETIONS、および SQL_CA2_SENSITIVITY_ を見る更新プログラムのビットマスクをアプリケーションでは、特定のドライバーによって実装されるカーソルがこれを行うかどうかを判断します。 削除された行を検出し、それらを削除するドライバーは、次の段落にこの動作の影響について説明します。 ドライバーは削除された行を検出できますが、削除できなくなるので、カーソルの動きに削除の影響がないと、次の段落は適用されません。  
  
 カーソル結果セットに追加された行を検出または結果セットから削除された行を削除、データをフェッチするときにのみこれらの変更を検出した場合とが表示されます。 場合と**SQLFetchScroll** FetchOrientation SQL_FETCH_RELATIVE を 0 に設定すると、同じ行セットを再フェッチ FetchOffset 設定を使用して呼び出したが、SQLSetPos が fOption sql _ に設定して呼び出されると、ケースは含まれません更新します。 後者の場合、行セットのバッファーでデータを更新するが再フェッチされません、および削除された行は結果セットから削除されません。 そのため、行がから削除、または現在の行セットに挿入されたときに、カーソルは行セットのバッファーは変更されません。 代わりに、任意の行セットをフェッチにしたときに、変更、削除された行が含まれていたまたは挿入された行が含まれていますが検出されます。  
  
 以下に例を示します。  
  
```cpp  
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
  
 ときに**SQLFetchScroll**を現在の行セットの相対位置を持つ新しい行セットを返す、FetchOrientation は SQL_FETCH_NEXT、SQL_FETCH_PRIOR、または SQL_FETCH_RELATIVE - 現在の行セットへの変更は含まれませんときに、新しい行セットの開始位置を計算します。 ただし、検出することは場合は、現在の行セットの外部で変更を含めることは。 さらに、 **SQLFetchScroll** - 現在の行セットの独立した位置が新しい行セットを返します SQL_FETCH_FIRST、SQL_FETCH_LAST、SQL_FETCH_ABSOLUTE、または SQL_FETCH_BOOKMARK - これは FetchOrientation があること現在の行セット内にある場合でも検出では、すべての変更が含まれています。  
  
 部分的な行セットは、最後の有効な行で終了すると見なされますを新しく追加された行が現在の行セットの内外でかどうかを判断するとき行の状態は sql_row_norow であって、最終行。 たとえば、カーソルが新しく追加された行を検出できる、現在の行セットは、部分的な行セット、アプリケーションは、新しい行を追加およびカーソルが結果セットの末尾にこれらの行を追加します。 アプリケーションを呼び出す場合**SQLFetchScroll** FetchOrientation SQL_FETCH_NEXT に設定と**SQLFetchScroll**新しく追加された最初の行で始まる行セットを返します。  
  
 たとえば、現在の行セットが 21 ~ 30 の行で構成されます、行セットのサイズは 10、カーソルが結果セットから削除された行を削除およびカーソルが結果セットに追加された行を検出します。 次の表は、行**SQLFetchScroll**さまざまな状況で返します。  
  
|[変更]|フェッチの型|FetchOffset|新しい行セット [1]|  
|------------|----------------|-----------------|---------------------|  
|21 行を削除します。|NEXT|0|31 ~ 40|  
|31 行を削除します。|NEXT|0|32 に 41|  
|行 21 と 22 の間に行を挿入します。|NEXT|0|31 ~ 40|  
|行 30、31 の間に行を挿入します。|NEXT|0|挿入された行、31 に 39|  
|21 行を削除します。|PRIOR|0|11 ~ 20|  
|20 行を削除します。|PRIOR|0|10 ~ 19|  
|行 21 と 22 の間に行を挿入します。|PRIOR|0|11 ~ 20|  
|行 20 と 21 の間に行を挿入します。|PRIOR|0|挿入された行は 12 ~ 20|  
|21 行を削除します。|RELATIVE|0|22 ~ 31<sup>[2]</sup>|  
|21 行を削除します。|RELATIVE|1|22 ~ 31|  
|行 21 と 22 の間に行を挿入します。|RELATIVE|0|挿入された行、21、22 ~ 29|  
|行 21 と 22 の間に行を挿入します。|RELATIVE|1|22 ~ 31|  
|21 行を削除します。|ABSOLUTE|21|22 ~ 31<sup>[2]</sup>|  
|22 行を削除します。|ABSOLUTE|21|21、31 日 23|  
|行 21 と 22 の間に行を挿入します。|ABSOLUTE|22|挿入された行、22 ~ 29|  
  
 [1] この列は、すべての行が挿入または削除する前に、行番号を使用します。  
  
 [2] この場合は、カーソルは、21 の行で始まる行を返そうとします。 21 行が削除されたため、最初の行が返されます、22 の行です。  
  
 エラー行 (つまり、状態の行 SQL_ROW_ERROR) では、カーソルの動きは影響しません。 たとえば、現在の行セットは、11 行目の状態で始まる場合に、11 行目は SQL_ROW_ERROR、呼び出す**SQLFetchScroll** FetchOrientation SQL_FETCH_RELATIVE に FetchOffset 設定では、5 に設定は行 16 以降行セットを返します。同様、11 行目の状態が SQL_SUCCESS の場合。  
  
## <a name="returning-data-in-bound-columns"></a>バインドされた列内のデータを返す  
 **SQLFetchScroll**と同じ方法でデータをバインドされた列を返す**SQLFetch**します。 詳細についてを参照してください「を返すデータにバインドされている列」 [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)します。  
  
 列がバインドされていない場合**SQLFetchScroll**データは返されませんは、指定した位置にブロック カーソルを移動します。 ブロック カーソルの非バインド列からデータを取得できるかどうか**SQLGetData**ドライバーによって異なります。 呼び出しの場合、この機能はサポートされて**SQLGetInfo** SQL_GETDATA_EXTENSIONS 情報の種類のビット SQL_GD_BLOCK を返します。  
  
## <a name="buffer-addresses"></a>バッファーのアドレス  
 **SQLFetchScroll**としてのデータと長さ/インジケーター バッファーのアドレスを決定する、同次数式を使用して**SQLFetch**します。 詳細については、「バッファー アドレス」を参照してください[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)します。  
  
## <a name="row-status-array"></a>行の状態の配列  
 **SQLFetchScroll** SQLFetch と同様に、行の状態配列に値を設定します。 詳細についてを参照してください「の行の状態の配列」 [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)します。  
  
## <a name="rows-fetched-buffer"></a>行がフェッチ バッファー  
 **SQLFetchScroll**と同様に、フェッチされた行のバッファーにフェッチされた行の数を返します**SQLFetch**します。 詳細についてを参照してください「の行のフェッチ バッファー」 [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)します。  
  
## <a name="error-handling"></a>エラー処理  
 アプリケーションを呼び出すと**SQLFetchScroll**ドライバー マネージャーは、ODBC 3.x ドライバー、 **SQLFetchScroll**ドライバー。 アプリケーションを呼び出すと**SQLFetchScroll** ODBC 2.x ドライバー、ドライバー マネージャーがドライバーで SQLExtendedFetch を呼び出します。 **SQLFetchScroll** SQLExtendedFetch 少し異なる方法でエラーを処理、アプリケーションからは、若干異なるエラー動作を呼び出すときに、 **SQLFetchScroll** odbc 2.x と ODBC3.x ドライバーです。  
  
 **SQLFetchScroll**と同じ方法でエラーと警告を返します**SQLFetch**; 詳細については、「エラーの処理」を参照してください**SQLFetch**します。 **SQLExtendedFetch**と同じ方法でエラーが返されます**SQLFetch**、次の例外。  
  
 警告が発生した行セット内の特定の行に適用される、SQLExtendedFetch は SQL_ROW_SUCCESS、SQL_ROW_SUCCESS_WITH_INFO しない行の状態配列内の対応するエントリを設定します。  
  
 行セット内のすべての行でエラーが発生した場合、SQLExtendedFetch はいない SQL_ERROR、SQL_SUCCESS_WITH_INFO を返します。  
  
 各グループの状態レコードの個別の行に適用される、SQLExtendedFetch によって返される最初の状態レコードは SQLSTATE 01S01 を含める必要があります (行のエラー)。**SQLFetchScroll**この SQLSTATE は返されません。 SQLExtendedFetch を返す追加 SQLSTATEs できない場合は、この SQLSTATE も返す必要があります。  
  
## <a name="sqlfetchscroll-and-optimistic-concurrency"></a>SQLFetchScroll とオプティミスティック同時実行制御  
 つまり、また、ステートメント属性 SQL_ATTR_CONCURRENCY に SQL_CONCUR_ROWVER、SQL_CONCUR_VALUES の値が、カーソルはオプティミスティック同時実行制御を使用して場合**SQLFetchScroll**データによって使用されているオプティミスティック同時実行制御値を更新行が変更されたかどうかを検出するソース。 これは、ようなときに**SQLFetchScroll**など、現在の行セットは変わりませんが、新しい行セットをフェッチします。 (を使用して呼び出した FetchOrientation SQL_FETCH_RELATIVE FetchOffset を 0 に設定を設定します。)  
  
## <a name="sqlfetchscroll-and-odbc-2x-drivers"></a>SQLFetchScroll および ODBC 2.x のドライバー  
 アプリケーションを呼び出すと**SQLFetchScroll** ODBC 2.x ドライバー、ドライバー マネージャーは、マップには、この呼び出し**SQLExtendedFetch**します。 次の引数の値を渡す**SQLExtendedFetch**します。  
  
|SQLExtendedFetch 引数|値|  
|-------------------------------|-----------|  
|StatementHandle|StatementHandle **SQLFetchScroll**します。|  
|FetchOrientation|FetchOrientation **SQLFetchScroll**します。|  
|FetchOffset|FetchOrientation でないかどうかに FetchOffset 引数の値である SQL_FETCH_BOOKMARK **SQLFetchScroll**使用されます。<br /><br /> FetchOrientation SQL_FETCH_BOOKMARK がある場合は、SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性によって指定されたアドレスに格納されている値が使用されます。|  
|RowCountPtr|SQL_ATTR_ROWS_FETCHED_PTR ステートメントの属性で指定されたアドレス。|  
|RowStatusArray|SQL_ATTR_ROW_STATUS_PTR ステートメントの属性で指定されたアドレス。|  
  
 詳細については、次を参照してください[ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)で付録 g:。旧バージョンとの互換性のためのガイドラインをドライバーです。  
  
## <a name="descriptors-and-sqlfetchscroll"></a>記述子および SQLFetchScroll  
 **SQLFetchScroll**記述子のと同じ方法で対話**SQLFetch**します。 詳細については、"記述子と SQLFetchScroll"セクションを参照してください。 [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)します。  
  
## <a name="code-example"></a>コード例  
 参照してください[列方向のバインド](../../../odbc/reference/develop-app/column-wise-binding.md)、[行方向のバインド](../../../odbc/reference/develop-app/row-wise-binding.md)、[位置指定更新と Delete ステートメント](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)、および[SQLSetPosによる行セットの行を更新しています](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md).  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|バッファーを結果セット内の列にバインドします。|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|Bulk insert、update、または削除操作を実行します。|[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|ステートメントの処理をキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|1 つの行または順方向専用の方向にデータのブロックをフェッチしています|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|ステートメントでカーソルを閉じる|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|結果の数を返すセットの列|[SQLNumResultCols 関数](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|カーソルを配置する、行セットのデータの更新や更新、または、結果セット内のデータを削除します。|[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
