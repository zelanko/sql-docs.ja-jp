---
title: SQLFetch 関数 |Microsoft ドキュメント
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
- SQLFetch
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLFetch
helpviewer_keywords:
- SQLFetch function [ODBC]
ms.assetid: 6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c
caps.latest.revision: 27
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2a340283066558215e5534e327026350cdcab589
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlfetch-function"></a>SQLFetch 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLFetch**結果セットからデータの次の行セットをフェッチされ、すべてのバインドされた列のデータを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLFetch(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLFetch** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる[SQLGetDiagRec 関数](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)で、 *HandleType*sql_handle_stmt としての*処理*の*StatementHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLFetch**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。 単一の列にエラーが発生した場合[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)で呼び出すことができる、 *DiagIdentifier* SQL_DIAG_COLUMN_NUMBER; でエラーが発生した列を判断するのと**SQLGetDiagField**で呼び出すことができる、 *DiagIdentifier* SQL_DIAG_ROW_NUMBER その列を含む行を決定するのです。  
  
 すべてこれら SQLSTATEs SQL_SUCCESS_WITH_INFO または SQL_ERROR (を除く 01xxx SQLSTATEs) を返すことができる、SQL_SUCCESS_WITH_INFO が返されますでエラーが発生した場合は、SQL_ERROR が返されます複数行の操作の 1 つまたは複数の、は、すべての行にエラーが発生した場合、。単一行の操作です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|文字列または列に対して返されるバイナリ データは、空白でない文字またはバイナリ データが NULL 以外の切り捨てが発生しました。 文字列値が、右側の切り捨てでした。|  
|01S01|行のエラー|1 つまたは複数の行をフェッチ中にエラーが発生しました。<br /><br /> (ODBC 3 時に、この SQLSTATE が返される場合は *.x* ODBC 2 を利用するアプリケーション *.x*ドライバー、無視することができます)。|  
|01S07|小数部の切り捨て|列に対して返されるデータが切り捨てられました。 数値データ型の数値の小数部が切り捨てられました。 時刻、タイムスタンプ、および時刻部分を含む interval データ型の場合は、時間の小数部が切り捨てられました。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|結果セット内の列のデータ値がで指定されたデータ型に変換できませんでした*TargetType*で**SQLBindCol**です。<br /><br /> SQL_C_BOOKMARK のデータ型にバインドされていた列 0 と SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されました。<br /><br /> SQL_C_VARBOOKMARK のデータ型にバインドされていた列 0 と SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されませんでした。|  
|07009|無効な記述子のインデックス|ドライバーは ODBC 2 *.x*ドライバーをサポートしない**SQLExtendedFetch**列のバインドで指定された列の数が 0 とします。<br /><br /> 列 0 がバインドされているし、SQL_UB_OFF に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されました。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|22001|文字列データで、右側が切り捨てられました|列に対して返さ可変長のブックマークが切り捨てられました。|  
|22002|インジケーター変数が必要ですが、指定されていません|NULL のデータがフェッチされました列にある*StrLen_or_IndPtr*によって設定**SQLBindCol** (またはによって設定 SQL_DESC_INDICATOR_PTR **SQLSetDescField**または**SQLSetDescRec**) が null ポインターでした。|  
|22003|数値が範囲|数値として数値の値またはバインドされた列の 1 つまたは複数の文字列を返す原因となる (ではなく小数部) 整数部分が切り捨てられる数値。<br /><br /> 詳細については、次を参照してください。[に変換するデータを SQL から C データ型に](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)付録 d: データ型にします。|  
|22007|無効な datetime 形式|結果セット内の文字の列は、日付、時刻、またはタイムスタンプ C 構造にバインドされていたし、列の値が、それぞれに、無効な日付、時刻、またはタイムスタンプ。|  
|22012|0 による除算です。|算術式の値が返されました、その結果、除算を 0 で。|  
|22015|間隔のフィールドがオーバーフローしました|真数型または interval SQL 型から C の間隔の種類を割り当てると、先頭のフィールドに有効桁数の損失が発生します。<br /><br /> 間隔 C 型にデータをフェッチするときに、間隔 C 型の SQL の型の値の表現はありませんでした。|  
|22018|キャストは無効な文字値|C 文字バッファーにバインドされていた、結果セット内の文字の列と列には、バッファーの文字セットの表現が発生しましたない文字が含まれています。<br /><br /> C 型が、真数または概数の数値、datetime、または、interval データ型です。列の SQL 型が文字データ型です。列の値がバインドされた C 型の有効なリテラルではありませんでした。|  
|24000|カーソル状態が無効|*StatementHandle*実行状態でしたが、結果セットが関連付けられていない、 *StatementHandle*です。|  
|40001|シリアル化のエラー|フェッチが実行されたトランザクションは、デッドロックを防ぐために終了しました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 **SQLFetch**関数が呼び出され、実行を完了する前に**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*. 続いて、 **SQLFetch**関数がもう一度、 *StatementHandle*です。<br /><br /> また、 **SQLFetch**関数が呼び出され、実行を完了する前に**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*マルチ スレッド アプリケーションで別のスレッドからです。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLFetch**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM)、指定した*StatementHandle*実行された状態ではありませんでした。 最初の呼び出さずに、関数が呼び出された**SQLExecDirect**、 **SQLExecute**またはカタログ関数。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) **SQLFetch**の呼び出された、 *StatementHandle*後**SQLExtendedFetch**が呼び出されたとする前に**SQLFreeStmt** sql _ と終了 オプションが呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|SQL_ATTR_USE_BOOKMARK ステートメント属性は SQL_UB_VARIABLE に設定され、列 0 の長さは、この結果セットのブックマークの最大の長さと等しいでしたバッファーにバインドされました。 (この長さは、IRD の SQL_DESC_OCTET_LENGTH フィールドで利用可能と呼び出すことによって取得できます**SQLDescribeCol**、 **SQLColAttribute**、または**SQLGetDescField**)。|  
|HY107|範囲外の行の値|SQL_ATTR_CURSOR_TYPE ステートメント属性で指定された値が SQL_CURSOR_KEYSET_DRIVEN、にもかかわらず、SQL_ATTR_KEYSET_SIZE ステートメント属性を持つ指定された値が 0 より大きいと、SQL_ATTR_ROW_ARRAY_ で指定した値よりも小さいサイズのステートメント属性です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースがの組み合わせで指定された変換をサポートしていない、 *TargetType*で**SQLBindCol**と対応する列の SQL データ型。|  
|HYT00|タイムアウトが発生しました|要求された結果セットが返されるデータ ソースの前に、クエリのタイムアウト期間が期限切れです。 SQLSetStmtAttr、SQL_ATTR_QUERY_TIMEOUT を通じて、タイムアウト期間が設定されています。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 **SQLFetch**結果セットに次の行セットを返します。 結果セットが存在するときにのみ呼び出すことができます。 つまり、結果セットを作成する呼び出しの後に、カーソルの前に結果セット全体が閉じられます。 すべての列がバインドされている場合は、これらの列にデータを返します。 アプリケーションには、行の状態配列をフェッチされた行の数を返すバッファーへのポインターが指定されている場合**SQLFetch**もこの情報を返します。 呼び出す**SQLFetch**の呼び出しを混在させることができます**SQLFetchScroll**の呼び出しを混在させることはできませんが、 **SQLExtendedFetch**です。 詳細については、次を参照してください。[行のデータのフェッチ](../../../odbc/reference/develop-app/fetching-a-row-of-data.md)です。  
  
 場合、ODBC 3 *.x*アプリケーションが ODBC 2 *.x*ドライバー、ドライバー マネージャーは、マップ**SQLFetch**呼び出し**SQLExtendedFetch**用、ODBC 2 *.x*をサポートするドライバー **SQLExtendedFetch**です。 場合、ODBC 2 *.x*ドライバーがサポートしていません**SQLExtendedFetch**、ドライバー マネージャーは、マップ**SQLFetch**呼び出し**SQLFetch** ODBC 2 *.x*ドライバーで、1 つの行のみをフェッチできます。  
  
 詳細については、次を参照してください。[ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。  
  
## <a name="positioning-the-cursor"></a>カーソルを配置します。  
 結果セットが作成されると、カーソルが結果セットの開始前に位置付けられます。 **SQLFetch**次の行セットをフェッチします。 呼び出すことと等価である**SQLFetchScroll**で*FetchOrientation* SQL_FETCH_NEXT に設定します。 カーソルの詳細については、次を参照してください。[カーソル](../../../odbc/reference/develop-app/cursors.md)と[ブロック カーソル](../../../odbc/reference/develop-app/block-cursors.md)です。  
  
 SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性は、行セット内の行の数を指定します。 場合は、行セットをフェッチする**SQLFetch**結果セットの末尾が重複しています**SQLFetch**部分的な行セットを返します。 つまり、S + R – 1 L より大きい、S はフェッチされる行セット、R の開始行は、行セットのサイズ、および L は、最後は行の結果セットにし、最初の L – のみ場合 S + 行セットの 1 行が有効です。 残りの行は空であり、SQL_ROW_NOROW の状態を持っています。  
  
 後に**SQLFetch** 、現在の行は、行セットの最初の行を返します。  
  
 次の表に記載されている規則の説明への呼び出し後にカーソルの位置決め**SQLFetch**のこのセクションの 2 番目の表に示す条件に基づいて、します。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|開始する前に|1|  
|*CurrRowsetStart* \< =  *LastResultRow – 複合カーソル*[1]|*CurrRowsetStart* + *複合カーソル*[2]|  
|*CurrRowsetStart* > *LastResultRow – 複合カーソル*[1]|末尾の後に|  
|末尾の後に|末尾の後に|  
  
 [1] のフェッチで、行セット サイズが変更された場合、前回フェッチで使用した行セット サイズです。  
  
 [2] のフェッチで、行セット サイズが変更された場合、新しくフェッチで使用した行セット サイズです。  
  
|表記法|意味|  
|--------------|-------------|  
|開始する前に|ブロック カーソルが結果セットの開始前に位置付けられます。 場合は、新しい行セットの最初の行は結果セットの開始前に、 **SQLFetch** SQL_NO_DATA が返されます。|  
|末尾の後に|ブロック カーソルが結果の末尾を設定後します。 場合は、新しい行セットの最初の行が結果セットの終了後は**SQLFetch** SQL_NO_DATA が返されます。|  
|*CurrRowsetStart*|現在の行セットの最初の行の数。|  
|*LastResultRow*|結果セットの最後の行の数。|  
|*複合カーソル*|行セットのサイズ。|  
  
 たとえば、結果セットの 100 行があり、行セットのサイズが 5 に設定するとします。 次の表に、によって返される行セットとリターン コード**SQLFetch**の別の開始位置。  
  
|現在の行セット|リターン コード|新しい行セット|フェッチされた行の数|  
|--------------------|-----------------|----------------|------------------------|  
|開始する前に|SQL_SUCCESS|1 ~ 5|5|  
|1 ~ 5|SQL_SUCCESS|6 ~ 10|5|  
|52 に 56|SQL_SUCCESS|57 に 61|5|  
|値が 91 ~ 95|SQL_SUCCESS|96 ~ 100|5|  
|93 に 97|SQL_SUCCESS|98 ~ 100 です。 行 4 と 5 の行の状態配列は、SQL_ROW_NOROW に設定されます。|3|  
|96 ~ 100|SQL_NO_DATA|[なし] :|0|  
|99 に 100|SQL_NO_DATA|[なし] :|0|  
|末尾の後に|SQL_NO_DATA|[なし] :|0|  
  
## <a name="returning-data-in-bound-columns"></a>バインドされた列内のデータを返す  
 として**SQLFetch**を返します。 各の行に、その列にバインドされたバッファーにバインドされた各列のデータを格納します。 列がバインドされていない場合**SQLFetch**データは返されませんは、ブロック カーソルを前方移動します。 データを使用して引き続き取得できる**SQLGetData**です。 カーソルが複数行のカーソルの場合 (つまり、SQL_ATTR_ROW_ARRAY_SIZE が 1 より大きい)、 **SQLGetData** SQL_GD_BLOCK が返される場合にのみ呼び出すことができる**SQLGetInfo**してを呼び出すと、 *情報の種類*SQL_GETDATA_EXTENSIONS のです。 (詳細については、次を参照してください[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)。)。  
  
 行にバインドされた各列**SQLFetch**は次の実行します。  
  
1.  SQL_NULL_DATA を長さ/インジケーター バッファーに設定し、データが NULL の場合、次の列に行われます。 場合は、データが NULL および長さ/インジケーター バッファーがバインドされていません**SQLFetch**行の SQLSTATE 22002 (インジケーター変数に必要なが指定されていません) を返し、次の行に進みます。 長さ/インジケーター バッファーのアドレスを決定する方法についてを参照してください「バッファー アドレス」 [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)です。  
  
     列のデータが NULL の場合、 **SQLFetch**手順 2. に進みます。  
  
2.  SQL_ATTR_MAX_LENGTH ステートメント属性が 0 以外の値に設定列には、文字またはバイナリ データが含まれている場合は、データは SQL_ATTR_MAX_LENGTH バイトに切り捨てられます。  
  
    > [!NOTE]  
    >  SQL_ATTR_MAX_LENGTH ステートメント属性はネットワーク トラフィックを削減するためのものです。 一般に、ネットワーク経由での返送前にデータが切り捨てられるデータ ソースによって実装されます。 ドライバーおよびデータ ソースは、それをサポートする必要はありません。 そのため、データが特定のサイズに切り捨てられたことを保証する、アプリケーションする必要がありますのサイズのバッファーを割り当てるし、サイズで指定、 *cbValueMax*引数**SQLBindCol**です。  
  
3.  データで指定された型に変換*TargetType*で**SQLBindCol**です。  
  
4.  データが文字またはバイナリなどの可変長データ型に変換された場合**SQLFetch**データの長さがデータ バッファーの長さを超えたかどうかを確認します。 文字データ (null 終了文字を含む) のデータ バッファーの長さを超えている場合**SQLFetch**データを null 終端文字の長さ以下のデータ バッファーの長さに切り捨てます。 Null で終端データ。 バイナリ データのデータ バッファーの長さを超えている場合**SQLFetch**データ バッファーの長さに切り捨てます。 データ バッファーの長さが指定*BufferLength*で**SQLBindCol**です。  
  
     **SQLFetch**切り捨てますしない固定長データ型に変換されたデータ以外のデータ バッファーの長さは、データ型のサイズを常に想定します。  
  
5.  変換された (および切り捨てられる可能性があります) のデータ、データ バッファーに配置します。 データ バッファーのアドレスを決定する方法についてを参照してください「バッファー アドレス」 [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)です。  
  
6.  長さ/インジケーター バッファー内のデータの長さを格納します。 インジケーター ポインターと長さのポインターが両方設定されている場合、同じバッファーに (への呼び出しとして**SQLBindCol**は)、長さが有効なデータのバッファーに書き込まれるおよび SQL_NULL_DATA が NULL のデータのバッファーに書き込まれます。 長さ/インジケーター バッファーがバインドされていない場合**SQLFetch**長さは返しません。  
  
    -   文字またはバイナリ データでは、これは、データの長さの変換後と切り捨て前に、データ バッファーが小さすぎるためです。 ドライバーを特定できない場合、データの長さ、変換後と長い形式のデータの場合となる場合があります、SQL_NO_TOTAL に長さを設定します。 SQL_ATTR_MAX_LENGTH ステートメント属性により、データが切り捨てられた、この属性の値は、実際の長さではなく長さ/インジケーター バッファーに配置されます。 これは、ドライバーには、実際の長さを判断する方法があるないように、この属性が、変換前に、サーバー上のデータの切り捨てを行うために設計されているためです。  
  
    -   他のすべてのデータ型では、これは、データの長さ変換後です。つまり、データの変換先の型のサイズです。  
  
     長さ/インジケーター バッファーのアドレスを決定する方法についてを参照してください「バッファー アドレス」 [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)です。  
  
7.  有効桁数の損失なしの変換中に、データが切り詰められます (たとえば、実数 1.234 が切り捨てられた整数変換する場合は 1) **SQLFetch** SQLSTATE 01S07 を返します (小数部の切り捨て) と sql _SUCCESS_WITH_INFO です。 データ バッファーの長さが小さすぎるため、データが切り捨てられる場合 (たとえば、文字列"abcdef"がバッファーに格納 4 バイト)、 **SQLFetch** SQLSTATE 01004 (データが切り捨てられました) と sql_success_with_info が返されます。 SQL_ATTR_MAX_LENGTH ステートメント属性によりデータが切り捨てられる場合**SQLFetch** SQL_SUCCESS を返し、SQLSTATE 01S07 は返されません (小数部の切り捨て) または SQLSTATE 01004 (データが切り捨てられます)。 (たとえば、100,000 を超える SQL_INTEGER 値が、SQL_C_TINYINT に変換された場合)、有効桁数の損失に変換中にデータが切り捨てられる場合**SQLFetch** SQLSTATE 22003 (数値が範囲) を返しますおよび SQL_ERROR (行セットのサイズが 1 の場合) または sql_success_with_info が (行セットのサイズが 1 より大きい場合)。  
  
 バインドされたデータ バッファーおよび長さ/インジケーター バッファーの内容は不定**SQLFetch**または**SQLFetchScroll** SQL_SUCCESS または SQL_SUCCESS_WITH_INFO を返しません。  
  
## <a name="row-status-array"></a>行の状態配列  
 行の状態配列は、行セットの行ごとの状態を返すに使用されます。 この配列のアドレスは、SQL_ATTR_ROW_STATUS_PTR ステートメント属性で指定されます。 配列は、アプリケーションによって割り当てられているし、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性で指定された数の要素があります。 その値を設定**SQLFetch**、 **SQLFetchScroll**、および**SQLBulkOperations**または**SQLSetPos** (それらが呼び出された場合を除く後で、カーソルが位置付けられている**SQLExtendedFetch**)。 SQL_ATTR_ROW_STATUS_PTR ステートメント属性の値が null ポインターの場合は、これらの関数は行の状態が返されません。  
  
 行の状態配列バッファーの内容は不定**SQLFetch**または**SQLFetchScroll** SQL_SUCCESS または SQL_SUCCESS_WITH_INFO を返しません。  
  
 行の状態配列では、次の値が返されます。  
  
|行の状態配列の値|Description|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|この行はフェッチに成功しましたれ、結果セットから最後にフェッチした後は変更されていません。|  
|SQL_ROW_SUCCESS_WITH_INFO|この行はフェッチに成功しましたれ、結果セットから最後にフェッチした後は変更されていません。 ただし、行に関する警告が返されました。|  
|SQL_ROW_ERROR|行をフェッチ中にエラーが発生しました。|  
|SQL_ROW_UPDATED [1]、[2] と [3]|行はフェッチに成功しましたし、結果セットから最後にフェッチした後に変更されました。 行が結果セットから再度フェッチまたはによって更新されるかどうか**SQLSetPos**状態は、行の新しい状態に変更します。|  
|SQL_ROW_DELETED [3]|この結果セットから最後にフェッチしたので、行が削除されました。|  
|SQL_ROW_ADDED [4]|によって、行が挿入された**SQLBulkOperations**です。 行が結果セットから再度フェッチまたはによって更新されるかどうか**SQLSetPos**、その状態は SQL_ROW_SUCCESS します。|  
|SQL_ROW_NOROW|行セットには、結果セットの末尾がオーバー ラップされ、行の状態配列のこの要素に対応する行が返されません。|  
  
 [1] keyset、混合、および動的カーソルでは、キーの値が更新された場合、データの行が削除されていると見なされます、新しい行を追加します。  
  
 [2] のドライバーでは、データの更新を検出できないし、そのため、この値を返すことはできません。 ドライバーが行の再フェッチの更新を検出できるかどうかを決定するには、アプリケーションが呼び出す**SQLGetInfo** SQL_ROW_UPDATES オプションを使用します。  
  
 [3] **SQLFetch**への呼び出しでの混在がある場合のみ、この値を返すことができます**SQLFetchScroll**です。 これは、ため**SQLFetch**結果セットを前方に移動し、のみ使用すると、ときに任意の行を更新できません。 行が再フェッチされませんので**SQLFetch**以前にフェッチした行に加えられた変更を検出しません。 ただし場合、 **SQLFetchScroll**いずれかの以前の行をフェッチする前に、カーソルを配置および**SQLFetch**それらの行をフェッチするために使用**SQLFetch**への変更を検出できますこれらの行。  
  
 [4] SQLBulkOperations によってのみ返されます。 設定されていない**SQLFetch**または**SQLFetchScroll**です。  
  
### <a name="rows-fetched-buffer"></a>行がフェッチ バッファー  
 バッファーをフェッチされた行を使用して、対象のデータが返されなかったされたをフェッチ中にエラーが発生したため、これらの行を含め、フェッチされた行の数を取得します。 つまり、行の状態配列内の値のない SQL_ROW_NOROW 行の数を勧めします。 このバッファーのアドレスは、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性で指定されます。 バッファーは、アプリケーションによって割り当てられます。 設定されます。 **SQLFetch**と**SQLFetchScroll**です。 SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性の値が null ポインターの場合は、これらの関数はフェッチされた行の数が返されません。 結果セットの現在の行の数を決定するには、アプリケーションが呼び出すことができます**SQLGetStmtAttr** SQL_ATTR_ROW_NUMBER 属性を持つ。  
  
 フェッチされた行のバッファーの内容は不定**SQLFetch**または**SQLFetchScroll**返さない SQL_SUCCESS または SQL_SUCCESS_WITH_INFO、SQL_NO_DATA が返される場合、その場合を除き、バッファーをフェッチされた行の値は 0 に設定します。  
  
### <a name="error-handling"></a>エラー処理  
 エラーと警告は、関数全体または個々 の行に適用できます。 診断レコードの詳細については、次を参照してください。[診断](../../../odbc/reference/develop-app/diagnostics.md)と[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)です。  
  
#### <a name="errors-and-warnings-on-the-entire-function"></a>関数全体に関するエラーと警告  
 かどうか、エラーは SQLSTATE HYT00 など、関数全体に適用されます。 (タイムアウト) または SQLSTATE 24000 (無効なカーソルの状態)、 **SQLFetch** SQL_ERROR と適切な SQLSTATE を返します。 行セットのバッファーの内容は未定義と、カーソルの位置は変更されません。  
  
 警告は、関数全体に適用される場合**SQLFetch** SQL_SUCCESS_WITH_INFO と適切な SQLSTATE を返します。 個々 の行に適用される状態レコードより前に、関数全体に適用される警告の状態レコードが返されます。  
  
#### <a name="errors-and-warnings-in-individual-rows"></a>個々 の行のエラーや警告  
 (SQLSTATE 22012 (ゼロによる除算)) などのエラーまたは警告 (SQLSTATE 01004 (データが切り捨てられました)) などは、1 つの行に適用される場合**SQLFetch**は次の実行します。  
  
-   警告用のエラーまたは SQL_ROW_SUCCESS_WITH_INFO、SQL_ROW_ERROR を行の状態配列の対応する要素を設定します。  
  
-   エラーまたは警告の SQLSTATEs を含む 0 個以上の状態のレコードを追加します。  
  
-   状態レコード内の行および列番号のフィールドを設定します。 場合**SQLFetch**行または列の数を決定することはできません、その番号 SQL_ROW_NUMBER_UNKNOWN または SQL_COLUMN_NUMBER_UNKNOWN、それぞれ設定します。 状態レコードが特定の列に適用されない場合**SQLFetch** SQL_NO_COLUMN_NUMBER への列数を設定します。  
  
 **SQLFetch**まで、行セット内のすべての行をフェッチした行のフェッチが続行されます。 後者 SQL_ERROR が返されます (SQL_ROW_NOROW の状態を持つ行を除く)、行セットのすべての行でエラーが発生しない限り、SQL_SUCCESS_WITH_INFO が返されます。 行セットのサイズが 1 で、その行にエラーが発生した場合、特に**SQLFetch** SQL_ERROR を返します。  
  
 **SQLFetch**行番号の順に状態レコードを返します。 つまり、不明な行 (あれば); のすべての状態レコードを返します次に、最初の行 (存在する場合)、すべての状態レコードが返され、2 番目の行 (あれば) のすべての状態レコードが返されます。 行ごとに状態レコードは通常状態レコードの順序の規則に従って順序付け詳細についてを参照してください「の状態レコードのシーケンス」 [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)です。  
  
### <a name="descriptors-and-sqlfetch"></a>記述子および SQLFetch  
 次のセクションで説明する方法**SQLFetch**記述子と対話します。  
  
#### <a name="argument-mappings"></a>引数のマップ  
 ドライバーの引数に基づいた記述子フィールドを設定していない**SQLFetch**です。  
  
#### <a name="other-descriptor-fields"></a>その他の記述子フィールド  
 により、次の記述子フィールドが使用**SQLFetch**です。  
  
|記述子フィールド|Desc です。|内のフィールド|使用して設定します。|  
|----------------------|-----------|--------------|-----------------|  
|SQL_DESC_ARRAY_SIZE|ARD|ヘッダー|SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性|  
|SQL_DESC_ARRAY_STATUS_PTR|IRD|ヘッダー|SQL_ATTR_ROW_STATUS_PTR ステートメント属性|  
|SQL_DESC_BIND_OFFSET_PTR|ARD|ヘッダー|SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性|  
|SQL_DESC_BIND_TYPE|ARD|ヘッダー|SQL_ATTR_ROW_BIND_TYPE ステートメント属性|  
|SQL_DESC_COUNT|ARD|ヘッダー|*ColumnNumber*の引数**SQLBindCol**|  
|SQL_DESC_DATA_PTR|ARD|レコード|*TargetValuePtr*の引数**SQLBindCol**|  
|SQL_DESC_INDICATOR_PTR|ARD|レコード|*StrLen_or_IndPtr*引数**SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH|ARD|レコード|*BufferLength*引数**SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH_PTR|ARD|レコード|*StrLen_or_IndPtr*引数**SQLBindCol**|  
|SQL_DESC_ROWS_PROCESSED_PTR|IRD|ヘッダー|SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性|  
|SQL_DESC_TYPE|ARD|レコード|*TargetType*引数**SQLBindCol**|  
  
 すべての記述子フィールドを設定することも**SQLSetDescField**です。  
  
#### <a name="separate-length-and-indicator-buffers"></a>別の長さとインジケーター バッファー  
 アプリケーションには、1 つのバッファー、または長さおよびインジケーターの値を保持するために使用できる 2 つの個別のバッファーをバインドできます。 アプリケーションを呼び出すと**SQLBindCol**、ドライバーに渡された、同じアドレスを ARD の SQL_DESC_OCTET_LENGTH_PTR および SQL_DESC_INDICATOR_PTR フィールドを設定する、 *StrLen_or_IndPtr*引数。 アプリケーションを呼び出すと**SQLSetDescField**または**SQLSetDescRec**、異なるアドレスにこれら 2 つのフィールドを設定できます。  
  
 **SQLFetch**アプリケーションが別の長さとインジケーターのバッファーを指定するかどうかを決定します。 この例では、ときに、データが NULL でない**SQLFetch**インジケーター バッファーを 0 に設定し、長バッファーの長さを返します。 データが NULL の場合、 **SQLFetch** SQL_NULL_DATA をインジケーター バッファーに設定し、長バッファーは変更されません。  
  
### <a name="code-example"></a>コード例  
 参照してください[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)、 [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)、 [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)、および[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)です。  
  
### <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|ステートメントでカーソルを閉じる|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|データの列の一部またはすべてのフェッチ|[SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|結果の数を返すセットの列|[SQLNumResultCols 関数](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|実行のためのステートメントを準備します。|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
