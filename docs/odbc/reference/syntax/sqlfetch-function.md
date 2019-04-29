---
title: SQLFetch 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 001238b4e5d47b22ca991efcd8b4ee28971d7af7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982305"
---
# <a name="sqlfetch-function"></a>SQLFetch 関数
**準拠**  
 バージョンが導入されました。ODBC 1.0 規格に準拠します。ISO 92  
  
 **まとめ**  
 **SQLFetch**結果セットからデータの次の行セットをフェッチし、すべてのバインドされた列のデータを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLFetch(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLFetch** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる[SQLGetDiagRec 関数](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)で、 *HandleType*sql_handle_stmt としての*処理*の*StatementHandle*します。 次の表に、によって返される通常の SQLSTATE 値**SQLFetch** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。 1 つの列でエラーが発生した場合[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)で呼び出すことができます、 *DiagIdentifier* SQL_DIAG_COLUMN_NUMBER; でエラーが発生した列を判断するのと**SQLGetDiagField**で呼び出すことができます、 *DiagIdentifier* SQL_DIAG_ROW_NUMBER その列を含む行を決定するのです。  
  
 複数行の操作の 1 つ以上のただしすべてではなく行にエラーが発生した場合にエラーが発生した場合、SQL_ERROR が返されますをすべてその SQLSTATEs SQL_SUCCESS_WITH_INFO または SQL_ERROR (を除く 01xxx SQLSTATEs) を返すことができる、SQL_SUCCESS_WITH_INFO が返される、単一行の操作です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|文字列またはバイナリ データの列に対して返される空白文字または NULL 以外のバイナリ データの切り捨てが発生しました。 文字列値がいた場合は、右側から切り捨てられますことでした。|  
|01S01|行内のエラー|1 つまたは複数の行をフェッチ中にエラーが発生しました。<br /><br /> (この SQLSTATE が返されない場合、ODBC 3 *.x*アプリケーションの操作は、ODBC 2 *.x*ドライバー、無視できます)。|  
|01S07|分数が切り捨てられました|列に対して返されるデータが切り捨てられました。 数値データ型、数値の小数部が切り捨てられました。 時刻、タイムスタンプ、および時刻部分が含まれている interval データ型の場合は、時間の小数部が切り捨てられました。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|指定されたデータ型に結果セット内の列のデータ値を変換でした*TargetType*で**SQLBindCol**します。<br /><br /> SQL_C_BOOKMARK のデータ型にバインドされた列 0 と SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメントの属性が設定されました。<br /><br /> SQL_C_VARBOOKMARK のデータ型にバインドされた列 0 と SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメントの属性が設定されませんでした。|  
|07009|無効な記述子のインデックス|ドライバーが、ODBC 2 *.x*がサポートされていないドライバー **SQLExtendedFetch**列のバインドで指定された列数が 0 とします。<br /><br /> 列 0 がバインドされているし、SQL_UB_OFF に SQL_ATTR_USE_BOOKMARKS ステートメントの属性が設定されました。|  
|08S01|通信リンク エラー|関数が完了した処理の前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクに失敗しました。|  
|22001|文字列データで、右側が切り捨てられました|列に対して返される可変長のブックマークが切り捨てられました。|  
|22002|インジケーター変数が必要ですが、指定されていません|NULL データのフェッチの列にある*StrLen_or_IndPtr*によって設定**SQLBindCol** (またはによって設定 SQL_DESC_INDICATOR_PTR **SQLSetDescField**または**SQLSetDescRec**) が null ポインター。|  
|22003|数値が範囲外|数値として数値の値またはバインドされた列の 1 つまたは複数の文字列を取得する原因となる (ではなく小数部) 整数部分が切り捨てられる数値。<br /><br /> 詳細については、次を参照してください[SQL から C データ型への変換データ](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)付録 d:。データ型。|  
|22007|無効な datetime 形式|結果セット内の文字の列は、日付、時刻、またはタイムスタンプ C 構造体にバインドされましたし、列の値が、それぞれ、無効な日付、時刻、またはタイムスタンプ。|  
|22012|0 による除算|算術式の値がによって返される、その結果、除算 0。|  
|22015|Interval フィールド オーバーフロー|真数型または interval SQL 型から C の間隔の種類への割り当てと、先頭のフィールドに有効桁数の損失が発生します。<br /><br /> C の間隔の種類にデータをフェッチするときに C の間隔の種類の SQL 型の値の表現はありませんでした。|  
|22018|キャストの無効な文字の値|C 文字バッファーにバインドされた結果セット内の文字の列と列には、対象のバッファーの文字セットで表現がない文字が含まれています。<br /><br /> C 型は、真数または概数の数値、datetime、またはデータ間隔の種類。列の SQL 型が文字データ型。列の値がバインドされた C 型の有効なリテラルではありませんでした。|  
|24000|カーソル状態が無効|*StatementHandle*実行の状態でしたが、結果セットが関連付けられていない、 *StatementHandle*します。|  
|40001|シリアル化エラー|デッドロックを防止するフェッチが実行されたトランザクションが終了しました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を特定できません。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効に、 *StatementHandle*します。 **SQLFetch**関数が呼び出され、実行を完了する前に**SQLCancel**または**SQLCancelHandle**が呼び出されて、 *StatementHandle*. 次に、 **SQLFetch**で関数が再度呼び出されました、 *StatementHandle*します。<br /><br /> また、 **SQLFetch**関数が呼び出され、実行を完了する前に**SQLCancel**または**SQLCancelHandle**が呼び出されて、 *StatementHandle*マルチ スレッド アプリケーションで別のスレッドから。|  
|HY010|関数のシーケンス エラー|(DM) を非同期的に実行中の関数が呼び出された接続ハンドルに関連付けられているため、 *StatementHandle*します。 この非同期関数ではときに実行されている、 **SQLFetch**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に対して呼び出された、 *StatementHandle* SQL_PARAM_DATA_ を返されます。ご利用いただけます。 ストリームのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM)、指定した*StatementHandle*実行の状態ではありませんでした。 最初に呼び出さず、関数が呼び出された**SQLExecDirect**、 **SQLExecute**またはカタログ関数。<br /><br /> (DM) を非同期的に実行中の関数 (いないこの"1") が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**に対して呼び出された、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) **SQLFetch**に対して呼び出された、 *StatementHandle*後**SQLExtendedFetch**が呼び出されたとする前に**SQLFreeStmt**で、sql _終了 オプションが呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|SQL_ATTR_USE_BOOKMARK ステートメント属性は SQL_UB_VARIABLE に設定されており、列 0 がの長さはこの結果セットに対してブックマークの最大の長さと等しくありませんでした。 バッファーにバインドされました。 (この長さは、IRD の SQL_DESC_OCTET_LENGTH フィールドで使用できますし、呼び出すことによって取得できる**SQLDescribeCol**、 **SQLColAttribute**、または**SQLGetDescField**)。|  
|HY107|行の値が範囲外|SQL_ATTR_CURSOR_TYPE ステートメント属性で指定された値が、SQL_CURSOR_KEYSET_DRIVEN が SQL_ATTR_KEYSET_SIZE ステートメント属性で指定された値が 0 より大きいと、SQL_ATTR_ROW_ARRAY_ で指定された値よりも小さいサイズのステートメント属性です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースの組み合わせで指定された変換をサポートしていません、 *TargetType*で**SQLBindCol**と対応する列の SQL データ型。|  
|HYT00|タイムアウトが発生しました|クエリのタイムアウト期間は、要求された結果セットが返されるデータ ソースの前に有効期限が切れました。 SQLSetStmtAttr、SQL_ATTR_QUERY_TIMEOUT を通じて、タイムアウト期間が設定されています。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングは無効です。|通知のモデルを使用すると、常にポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了が呼び出されていません。|通知モードが有効になっている場合、ハンドルでは、前の関数呼び出しに SQL_STILL_EXECUTING が返された場合と**SQLCompleteAsync**後処理を行い、操作を完了するハンドルで呼び出す必要があります。|  
  
## <a name="comments"></a>コメント  
 **SQLFetch**結果セット内の次の行セットを返します。 結果セットが存在する間だけ呼び出すことができます。 つまり、呼び出しの後に結果セットを作成すると、結果セット全体が閉じているカーソルの前に。 すべての列がバインドされている場合は、これらの列にデータを返します。 アプリケーションには、行の状態配列をフェッチされた行の数を返すバッファーへのポインターが指定した場合**SQLFetch**もこの情報を返します。 呼び出す**SQLFetch**への呼び出しに組み込むことができます**SQLFetchScroll**への呼び出しを混在させることはできませんが、 **SQLExtendedFetch**します。 詳細については、次を参照してください。[行のデータのフェッチ](../../../odbc/reference/develop-app/fetching-a-row-of-data.md)します。  
  
 場合、ODBC 3 *.x*アプリケーションが動作する ODBC 2 *.x*ドライバー、ドライバー マネージャーは、マップ**SQLFetch**呼び出し**SQLExtendedFetch**のODBC 2 *.x*をサポートするドライバー **SQLExtendedFetch**します。 場合、ODBC 2 *.x*ドライバーがサポートしていない**SQLExtendedFetch**、ドライバー マネージャーは、マップ**SQLFetch**呼び出し**SQLFetch** ODBC 2 *.x*ドライバーで、1 つの行のみをフェッチすることができます。  
  
 詳細については、次を参照してください[ブロック カーソル、スクロール可能なカーソル、および下位互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)で付録 g:。旧バージョンとの互換性のためのガイドラインをドライバーです。  
  
## <a name="positioning-the-cursor"></a>カーソルを配置します。  
 結果セットが作成されると、カーソルは結果セットの開始前にします。 **SQLFetch**次の行セットをフェッチします。 呼び出すことと同じである**SQLFetchScroll**で*FetchOrientation* SQL_FETCH_NEXT に設定します。 カーソルの詳細については、次を参照してください。[カーソル](../../../odbc/reference/develop-app/cursors.md)と[ブロック カーソル](../../../odbc/reference/develop-app/block-cursors.md)します。  
  
 SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性は、行セット内の行の数を指定します。 によって、行セットをフェッチされている場合、 **SQLFetch** 、結果セットの末尾と重なる**SQLFetch**部分的な行セットを返します。 つまり、S + R - L より大きい、S は、開始行フェッチされる行セット、R の行セットのサイズは、あり L は、最後の 1 行の結果セットし、最初の左辺にのみ場合 S + 1 行の行セットは有効です。 残りの行は空であり、sql_row_norow であっての状態を持っています。  
  
 後**SQLFetch** 、現在の行が行セットの最初の行を返します。  
  
 次の表に記載されている規則は、呼び出しの後にカーソルの位置決めについて説明する**SQLFetch**このセクションでは、2 番目の表に示す条件に基づいて、します。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|開始する前に|1|  
|*CurrRowsetStart* \<= *LastResultRow - RowsetSize*[1]|*CurrRowsetStart* + *RowsetSize*[2]|  
|*CurrRowsetStart* > *LastResultRow - 複合カーソル*[1]|終了後|  
|終了後|終了後|  
  
 [1] のフェッチ、行セットのサイズが変更された場合、前回フェッチで使用されていた行セットのサイズになります。  
  
 [2] のフェッチ、行セットのサイズが変更された場合、新しくフェッチで使用されていた行セットのサイズになります。  
  
|表記法|説明|  
|--------------|-------------|  
|開始する前に|ブロック カーソルは結果セットの開始前に配置されます。 新しい行セットの最初の行は、結果セットの開始前に、する場合**SQLFetch** sql_no_data が返されます。|  
|終了後|ブロック カーソルは、結果の最後の設定後に配置されます。 場合、新しい行セットの最初の行は、結果セットの終了後**SQLFetch** sql_no_data が返されます。|  
|*CurrRowsetStart*|現在の行セットの最初の行の数。|  
|*LastResultRow*|結果セットの最後の行の数。|  
|*複合カーソル*|行セットのサイズ。|  
  
 たとえば、結果セットが 100 行、行セットのサイズを 5 に設定するとします。 次の表に、によって返される行セットとリターン コード**SQLFetch**の別の開始位置。  
  
|現在の行セット|リターン コード|新しい行セット|フェッチされた行の数|  
|--------------------|-----------------|----------------|------------------------|  
|開始する前に|SQL_SUCCESS|1 ~ 5|5|  
|1 ~ 5|SQL_SUCCESS|6 ~ 10|5|  
|52 に 56|SQL_SUCCESS|57 に 61|5|  
|91 ~ 95|SQL_SUCCESS|96 ~ 100|5|  
|93 から 97 に|SQL_SUCCESS|98 ~ 100 です。 行 4 と 5 行の状態配列は、sql_row_norow であってに設定されます。|3|  
|96 ~ 100|SQL_NO_DATA|[なし] :|0|  
|99 ~ 100|SQL_NO_DATA|[なし] :|0|  
|終了後|SQL_NO_DATA|[なし] :|0|  
  
## <a name="returning-data-in-bound-columns"></a>バインドされた列内のデータを返す  
 として**SQLFetch**を返します。 それぞれの行に、その列にバインドされるバッファーにバインドされた各列のデータを入れします。 列がバインドされていない場合**SQLFetch**データは返されませんは、ブロック カーソルを前方移動します。 データを使用して引き続き取得できる**SQLGetData**します。 カーソルが複数行のカーソルの場合 (つまり、SQL_ATTR_ROW_ARRAY_SIZE が 1 より大きい)、 **SQLGetData** SQL_GD_BLOCK が返される場合にのみ呼び出すことができます**SQLGetInfo**を呼び出すと、 *情報の種類*SQL_GETDATA_EXTENSIONS の。 (詳細については、次を参照してください[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)。)。  
  
 バインドされた各列の行**SQLFetch**は次の処理します。  
  
1.  SQL_NULL_DATA を長さ/インジケーター バッファーに設定し、データが NULL の場合は、次の列に進みます。 データが NULL で、長さ/インジケーター バッファーがバインドされていない、 **SQLFetch**行の SQLSTATE 22002 (インジケーター変数に必要なが指定されていません) を返し、次の行に進みます。 長さ/インジケーター バッファーのアドレスを確認する方法については、「バッファー アドレス」を参照してください[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)します。  
  
     列のデータが NULL でない場合**SQLFetch**手順 2. に進みます。  
  
2.  SQL_ATTR_MAX_LENGTH ステートメント属性は、0 以外の値に設定されて、列には、文字またはバイナリ データが含まれている場合は、データは SQL_ATTR_MAX_LENGTH バイトに切り捨てられます。  
  
    > [!NOTE]  
    >  SQL_ATTR_MAX_LENGTH ステートメント属性は、ネットワーク トラフィックを削減するものです。 一般に、ネットワーク経由で返す前に、データが切り捨てられますデータ ソースによって実装されます。 ドライバーとデータ ソースは、それをサポートする必要はありません。 そのため、データが特定のサイズに切り捨てられたことを確実に、アプリケーションする必要がありますそのサイズのバッファーを割り当てるし、サイズで指定、 *cbValueMax*引数**SQLBindCol**します。  
  
3.  指定された型にデータを変換*TargetType*で**SQLBindCol**します。  
  
4.  データが文字またはバイナリなどの可変長データ型に変換された場合**SQLFetch**データの長さが、データ バッファーの長さを超えるかどうかを確認します。 (Null 終了文字を含む) の文字データのデータ バッファーの長さを超えている場合**SQLFetch** null 終了文字の長さ未満のデータ バッファーの長さのデータを切り捨てます。 Null 終端データ。 バイナリ データのデータ バッファーの長さを超えている場合**SQLFetch**データ バッファーの長さに切り捨てます。 データ バッファーの長さを指定した*BufferLength*で**SQLBindCol**します。  
  
     **SQLFetch**切り捨てますしない固定長データ型に変換されたデータは、常に想定する、データ バッファーの長さはデータ型のサイズ。  
  
5.  変換された (および切り捨てられる可能性があります) のデータをデータ バッファーになります。 データ バッファーのアドレスを確認する方法については、「バッファー アドレス」を参照してください[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)します。  
  
6.  データの長さを長さ/インジケーター バッファーになります。 同じバッファーには、インジケーターのポインターと長さポインター両方設定されている場合 (への呼び出しとして**SQLBindCol**は)、長さが有効なデータのバッファーに書き込まれるおよび SQL_NULL_DATA が NULL のデータのバッファーに書き込まれます。 長さ/インジケーター バッファーがバインドされていない場合**SQLFetch**長さは返されません。  
  
    -   文字またはバイナリ データは、これは、データの長さの変換後と切り捨て前に、データのバッファーが小さすぎるため。 場合は、ドライバーは長い形式のデータの場合、変換後、データの長さを決定することはできません、SQL_NO_TOTAL に長さを設定します。 SQL_ATTR_MAX_LENGTH のステートメント属性によりデータが切り捨てられる場合は、この属性の値が実際の長さではなく長さ/インジケーター バッファーに格納されます。 これは、ドライバーには実際の長さを判断する方法があるないように、この属性が、変換前に、サーバー上のデータを切り捨てるに設計されているためにです。  
  
    -   その他のすべてのデータ型の変換後、データの長さは、このこれは、データが変換される型のサイズがあります。  
  
     長さ/インジケーター バッファーのアドレスを確認する方法については、「バッファー アドレス」を参照してください[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)します。  
  
7.  有効桁数を失うことがなく変換中にデータが切り捨てられるかどうか (たとえば、実数 1.234 が切り捨てられるは整数 1 が変換されるときに) **SQLFetch** SQLSTATE 01S07 を返します (分数が切り捨てられました) と sql _SUCCESS_WITH_INFO します。 データ バッファーの長さが小さすぎるため、データが切り捨てられる場合 (たとえば、文字列"abcdef"がバッファーに格納 4 バイト)、 **SQLFetch** SQLSTATE 01004 (データが切り捨てられました) と、SQL_SUCCESS_WITH_INFO を返します。 SQL_ATTR_MAX_LENGTH ステートメント属性によりデータが切り捨てられる場合**SQLFetch** SQL_SUCCESS を返し、SQLSTATE 01S07 は返されません (分数が切り捨てられました) または SQLSTATE 01004 (データが切り捨てられます)。 (たとえば、100,000 より大きい SQL_INTEGER 値が、SQL_C_TINYINT に変換された場合)、有効桁数の損失が変換中にデータが切り捨てられる場合**SQLFetch** SQLSTATE 22003 (範囲外の数値の値) を返します(行セットのサイズが 1 の場合)、SQL_ERROR または SQL_SUCCESS_WITH_INFO (行セットのサイズが 1 より大きい場合)。  
  
 バインドされたデータ バッファーおよび長さ/インジケーター バッファーの内容は定義されていない場合は**SQLFetch**または**SQLFetchScroll** SQL_SUCCESS または SQL_SUCCESS_WITH_INFO が返されません。  
  
## <a name="row-status-array"></a>行の状態の配列  
 行の状態配列は、行セットの各行のステータスを返すに使用されます。 この配列のアドレスは、し、SQL_ATTR_ROW_STATUS_PTR ステートメント属性で指定されます。 配列は、アプリケーションが割り当てられる、SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性で指定された数の要素を必要とします。 その値によって設定**SQLFetch**、 **SQLFetchScroll**、および**SQLBulkOperations**または**SQLSetPos** (それらが呼び出された場合を除く後で、カーソルが位置付けられている**SQLExtendedFetch**)。 SQL_ATTR_ROW_STATUS_PTR ステートメント属性の値が null ポインターの場合は、これらの関数は行のステータスを返しません。  
  
 行の状態配列バッファーの内容は定義されていない場合は**SQLFetch**または**SQLFetchScroll** SQL_SUCCESS または SQL_SUCCESS_WITH_INFO が返されません。  
  
 行の状態配列では、次の値が返されます。  
  
|行の状態の配列の値|説明|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|この行が正常にフェッチされたれ、この結果セットから最後にフェッチした後は変更されていません。|  
|SQL_ROW_SUCCESS_WITH_INFO|この行が正常にフェッチされたれ、この結果セットから最後にフェッチした後は変更されていません。 ただし、行の詳細については、警告が返されました。|  
|SQL_ROW_ERROR|行のフェッチ中にエラーが発生しました。|  
|SQL_ROW_UPDATED [1]、[2] と [3]|行が正常にフェッチし、この結果セットから最後にフェッチした後に変更されました。 行をこの結果セットから、再びフェッチはによって更新されますか**SQLSetPos**状態は、行の新しい状態に変更されます。|  
|SQL_ROW_DELETED[3]|この結果セットから最後にフェッチしたため、行が削除されました。|  
|SQL_ROW_ADDED[4]|行が挿入された**SQLBulkOperations**します。 行をこの結果セットから、再びフェッチはによって更新されますか**SQLSetPos**、その状態が SQL_ROW_SUCCESS します。|  
|SQL_ROW_NOROW であって|行セットには、結果セットの末尾がオーバー ラップされ、この要素の行の状態配列に対応する行が返されません。|  
  
 [1] の keyset、混合、および動的カーソルでは、データの行が削除されていると見なされますキー値が更新された場合と新しい行を追加します。  
  
 [2] のドライバーでは、データへの更新を検出できないし、そのため、この値を返すことはできません。 アプリケーションを呼び出すドライバーが行の再フェッチの更新を検出できるかどうかを判断する**SQLGetInfo** SQL_ROW_UPDATES オプションを使用します。  
  
 [3] **SQLFetch**への呼び出しでの混在がある場合のみ、この値を返すことができます**SQLFetchScroll**します。 これは、ため**SQLFetch**結果セットを前方に移動します。 とのみ使用する場合が任意の行を更新できません。 行が再フェッチしないため、 **SQLFetch**以前にフェッチした行に加えられた変更を検出しません。 ただし場合、 **SQLFetchScroll**いずれかが以前に行をフェッチする前にカーソルが置かれますと**SQLFetch**これらの行をフェッチするために使用**SQLFetch**への変更を検出できますこれらの行。  
  
 [4] SQLBulkOperations によってのみ返されます。 設定されていない**SQLFetch**または**SQLFetchScroll**します。  
  
### <a name="rows-fetched-buffer"></a>行がフェッチ バッファー  
 バッファーをフェッチされた行は、対象のデータが返されなかったがフェッチされているときにエラーが発生したため、これらの行を含む、フェッチされた行の数を返すために使用します。 つまり、行の状態配列内の値のない sql_row_norow であって行の数になります。 このバッファーのアドレスは、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性で指定されます。 バッファーは、アプリケーションによって割り当てられます。 によって設定された**SQLFetch**と**SQLFetchScroll**します。 SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性の値が null ポインターの場合は、これらの関数にフェッチされる行数は返されません。 結果セットの現在の行の数を決定するには、アプリケーションを呼び出すことができます**SQLGetStmtAttr** SQL_ATTR_ROW_NUMBER 属性を持つ。  
  
 フェッチされた行のバッファーの内容は定義されていない場合は**SQLFetch**または**SQLFetchScroll**返さない SQL_SUCCESS または SQL_SUCCESS_WITH_INFO、SQL_NO_DATA が返される場合、その場合を除く、バッファーをフェッチされた行の値は 0 に設定されます。  
  
### <a name="error-handling"></a>エラー処理  
 エラーと警告は、個々 の行にまたは関数全体を適用できます。 診断レコードの詳細については、次を参照してください。[診断](../../../odbc/reference/develop-app/diagnostics.md)と[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)します。  
  
#### <a name="errors-and-warnings-on-the-entire-function"></a>関数全体に関するエラーと警告  
 かどうか、エラーは SQLSTATE HYT00 など、関数全体に適用されます。 (タイムアウトの期限切れ) または SQLSTATE 24000 (無効なカーソルの状態)、 **SQLFetch** SQL_ERROR と適切な SQLSTATE を返します。 行セットのバッファーの内容は定義されていないと、カーソル位置は変更されません。  
  
 警告は、関数全体に適用される場合**SQLFetch** SQL_SUCCESS_WITH_INFO と適切な SQLSTATE を返します。 状態レコードの個々 の行に適用される前に、関数全体に適用される警告の状態レコードが返されます。  
  
#### <a name="errors-and-warnings-in-individual-rows"></a>個々 の行でエラーや警告  
 (SQLSTATE 22012 (ゼロによる除算)) などのエラーまたは警告 (SQLSTATE 01004 (データが切り捨てられました)) などは、1 つの行に適用される場合**SQLFetch**は次の処理します。  
  
-   警告のエラーや SQL_ROW_SUCCESS_WITH_INFO、SQL_ROW_ERROR に行の状態配列の対応する要素を設定します。  
  
-   エラーまたは警告の SQLSTATEs を含む 0 個以上の状態レコードを追加します。  
  
-   状態レコード内の行と列の数値フィールドを設定します。 場合**SQLFetch**行または列の数を決定することはできませんそれぞれを SQL_ROW_NUMBER_UNKNOWN または SQL_COLUMN_NUMBER_UNKNOWN、その番号に設定にします。 状態レコードが特定の列に適用されない場合**SQLFetch** SQL_NO_COLUMN_NUMBER 列番号を設定します。  
  
 **SQLFetch**まで、行セット内のすべての行をフェッチした行のフェッチが続行されます。 後者 SQL_ERROR を返します (sql_row_norow であっての状態を持つ行を除く)、行セットのすべての行でエラーが発生しない限り、SQL_SUCCESS_WITH_INFO を返します。 行セットのサイズが 1 で、その行でエラーが発生した場合、特に**SQLFetch** SQL_ERROR を返します。  
  
 **SQLFetch**行番号の順序で状態レコードを返します。 つまり、不明な行 (あれば) のすべての状態レコードを返します最初の行 (あれば) では、すべての状態レコードが返されます次と 2 番目の行 (あれば)、すべての状態レコードを返します。 行ごとに状態レコードは通常の状態レコードの順序の規則に従って順序付け詳細についてを参照してください「の状態レコードのシーケンス」 [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)します。  
  
### <a name="descriptors-and-sqlfetch"></a>記述子および SQLFetch  
 次のセクションで説明する方法**SQLFetch**記述子と対話します。  
  
#### <a name="argument-mappings"></a>引数マッピング  
 ドライバーの引数に基づいた任意の記述子フィールドを設定しない**SQLFetch**します。  
  
#### <a name="other-descriptor-fields"></a>その他の記述子フィールド  
 次の記述子フィールドを使って**SQLFetch**します。  
  
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
  
 すべての記述子フィールドを設定することも**SQLSetDescField**します。  
  
#### <a name="separate-length-and-indicator-buffers"></a>別の長さとインジケーター バッファー  
 アプリケーションには、1 つのバッファーまたは長さとインジケーターの値を保持するために使用できる 2 つの独立したバッファーをバインドできます。 アプリケーションを呼び出すと**SQLBindCol**、ドライバーでは、同じアドレスに、ARD の SQL_DESC_OCTET_LENGTH_PTR および SQL_DESC_INDICATOR_PTR のフィールドを設定する、 *StrLen_or_IndPtr*引数。 アプリケーションを呼び出すと**SQLSetDescField**または**SQLSetDescRec**、異なるアドレスにこれら 2 つのフィールドを設定できます。  
  
 **SQLFetch**アプリケーションが別の長さとインジケーターのバッファーを指定するかどうかを決定します。 この場合は、ときに、データが NULL でない**SQLFetch**インジケーター バッファーを 0 に設定し、長さのバッファーの長さを返します。 データが null の場合、 **SQLFetch** SQL_NULL_DATA をインジケーター バッファーに設定し、長さのバッファーは変更されません。  
  
### <a name="code-example"></a>コード例  
 参照してください[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)、 [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)、 [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)、および[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)します。  
  
### <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|バッファーを結果セット内の列にバインドします。|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理をキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|データのブロックをフェッチしています。 または、結果をスクロールの設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|ステートメントでカーソルを閉じる|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|列のデータの一部またはすべてをフェッチしています|[SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|結果の数を返すセットの列|[SQLNumResultCols 関数](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|実行するステートメントを準備します。|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
