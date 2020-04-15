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
- SQLFetch
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFetch
helpviewer_keywords:
- SQLFetch function [ODBC]
ms.assetid: 6c6611d2-bc6a-4390-87c9-1c5dd9cfe07c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bc7e2da6996d8d6b2ee66befdc90794efec5617b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285972"
---
# <a name="sqlfetch-function"></a>SQLFetch 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLFetch**は、結果セットからデータの次の行セットをフェッチし、すべてのバインドされた列のデータを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLFetch(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLFetch**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、関連付けられた SQLSTATE 値を取得するには *、SQL_HANDLE_STMTのハンドル型*と*ステートメント ハンドル*の*ハンドル*を指定して[SQLGetDiagRec 関数](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)を呼び出します。 次の表は **、SQLFetch**によって返される SQLSTATE 値を一覧し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。 1 つの列でエラーが発生した場合は、エラーが発生した列を判別するために、SQL_DIAG_COLUMN_NUMBERの*DiagIdentifier を*指定して[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)を呼び出すことができます。**SQLGetDiagField**は、その列を含む行を決定するSQL_DIAG_ROW_NUMBERの*DiagIdentifier*を使用して呼び出すことができます。  
  
 SQL_SUCCESS_WITH_INFOまたはSQL_ERRORを返すことができるすべての SQLSTATE (01xxx SQLSTATE を除く) では、複数行操作の 1 つ以上の行でエラーが発生した場合はSQL_SUCCESS_WITH_INFOが返され、単一行操作でエラーが発生した場合はSQL_ERRORが返されます。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|列に対して返された文字列データまたはバイナリ データの結果、空白以外の文字または NULL 以外のバイナリ データが切り捨てられます。 文字列値の場合は、右に切り捨てられます。|  
|01S01|行内エラー|1 つ以上の行をフェッチ中にエラーが発生しました。<br /><br /> (ODBC 3 *.x*アプリケーションが ODBC 2 *.x*ドライバーを使用しているときにこの SQLSTATE が返される場合は、無視できます。|  
|01S07|分数切り捨て|列に対して返されたデータが切り捨てられました。 数値データ型の場合、数値の小数部分は切り捨てられました。 時間コンポーネントを含む時間、タイムスタンプ、および間隔のデータ型については、時間の小数部分が切り捨てられました。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07006|制限付きデータ型属性違反|結果セット内の列のデータ値を **、SQLBindCol**で*TargetType*で指定されたデータ型に変換できませんでした。<br /><br /> 列 0 は、SQL_C_BOOKMARKのデータ型でバインドされ、SQL_ATTR_USE_BOOKMARKSステートメント属性がSQL_UB_VARIABLEに設定されました。<br /><br /> 列 0 は SQL_C_VARBOOKMARK のデータ型でバインドされ、SQL_ATTR_USE_BOOKMARKS ステートメント属性がSQL_UB_VARIABLEに設定されていません。|  
|07009|記述子インデックスが無効です|ドライバは**SQLExtendedFetch**をサポートしない ODBC 2 *.x*ドライバであり、列のバインドで指定された列番号は 0 でした。<br /><br /> 列 0 がバインドされ、SQL_ATTR_USE_BOOKMARKS ステートメント属性がSQL_UB_OFFに設定されました。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|22001|文字列データ(右切り捨て)|列に対して返された可変長ブックマークが切り捨てられました。|  
|22002|インジケーター変数が必要ですが、指定されていません|NULL データは **、SQLBindCol**によって設定された*StrLen_or_IndPtr* (または**SQLSetDesc フィールドまたは SQLSetDescRec**によって設定SQL_DESC_INDICATOR_PTR) が NULL ポインターである列にフェッチされました。 **SQLSetDescRec**|  
|22003|範囲外の数値|1 つ以上のバインドされた列の数値または文字列として数値を返すと、数値の整数部分 (小数部ではなく) が切り捨てられる可能性があります。<br /><br /> 詳細については、「付録 D:[データ型」の「SQL から C データ型への](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)データの変換」を参照してください。|  
|22007|日付/時刻形式が無効です|結果セット内の文字列が日付、時刻、またはタイム・スタンプ C の構造にバインドされ、列の値がそれぞれ無効な日付、時刻、またはタイム・スタンプであった。|  
|22012|ゼロ除算|算術式の値が返され、結果として 0 除算が行われました。|  
|22015|間隔フィールドのオーバーフロー|正確な数値または間隔の SQL タイプから間隔 C タイプに割り当てると、先行フィールドの有効桁数が失われます。<br /><br /> データを間隔 C 型にフェッチする場合、間隔 C 型の SQL 型の値の表現はありませんでした。|  
|22018|キャスト指定に無効な文字値|結果セット内の文字列が文字 C バッファーにバインドされ、その列にバッファーの文字セットに表現が含まれていない文字が含まれていました。<br /><br /> C 型は、正確な数値または概数、日時、または間隔のデータ型でした。列の SQL 型は文字データ型でした。列の値が、バインドされた C 型の有効なリテラルではありません。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*は実行済み状態でしたが、結果セットはステートメント ハンドルに関連付*けられません*。|  
|40001|シリアル化の失敗|デッドロックを防ぐために、フェッチが実行されたトランザクションが終了しました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 **SQLFetch**関数が呼び出され、実行が完了する前に、*ステートメント ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、ステートメント*ハンドル*で**SQLFetch**関数が再度呼び出されました。<br /><br /> または **、SQLFetch**関数が呼び出され、実行が完了する前に、マルチスレッド アプリケーションの別のスレッドからステートメント ハンドルに対して**SQLCancel**または**SQLCancelHandle**が呼び出されました。 *StatementHandle*|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLFetch**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM) 指定された*ステートメント ハンドル*が実行状態にありません。 関数は、最初に呼び出**さずに****呼**び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM) **SQLFetch**は **、SQLExtendedFetch**が呼び出された後、およびSQL_CLOSE オプションを指定した**SQLFreeStmt**が呼び出される前にステートメント*ハンドル*に対して呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|SQL_ATTR_USE_BOOKMARKステートメント属性がSQL_UB_VARIABLE に設定され、列 0 は、この結果セットのブックマークの最大長と等しくない長さのバッファーにバインドされました。 (この長さは IRD のSQL_DESC_OCTET_LENGTH フィールドで使用でき **、SQLDescribeCol** **、SQLCol 属性**、または**SQLGetDescField**を呼び出すことによって取得できます。|  
|HY107|行の値が範囲外です|SQL_ATTR_CURSOR_TYPEステートメント属性で指定された値はSQL_CURSOR_KEYSET_DRIVENされましたが、SQL_ATTR_KEYSET_SIZEステートメント属性で指定された値が 0 より大きく、SQL_ATTR_ROW_ARRAY_SIZEステートメント属性で指定された値より小さくなっています。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|ドライバーまたはデータ ソースは **、SQLBindCol**の*ターゲットの種類*と、対応する列の SQL データ型の組み合わせで指定された変換をサポートしていません。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが要求された結果セットを返しました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUTSQLSetStmtAttr を使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 **SQLFetch は**、結果セット内の次の行セットを返します。 これは、結果セットが存在する場合、つまり、結果セットを作成する呼び出しの後、その結果セット上のカーソルが閉じられる前にだけ呼び出すことができます。 列がバインドされている場合は、それらの列のデータを返します。 アプリケーションが、フェッチされた行数を返す行状態配列またはバッファーへのポインターを指定した場合 **、SQLFetch はこの**情報も返します。 **SQLFetch**への呼び出しは **、SQLFetchScroll**の呼び出しと混在させることができますが、**呼**び出しとを混合することはできません。 詳細については、「[データ行のフェッチ](../../../odbc/reference/develop-app/fetching-a-row-of-data.md)」を参照してください。  
  
 ODBC 3 *.x*アプリケーションが ODBC 2 *.x*ドライバーで動作する場合、ドライバー マネージャーは **、SQLExtendedFetch**をサポートする ODBC 2 *.x*ドライバーの**SQLExtendedFetch**呼び出しを**マップ**します。 ODBC 2 *.x*ドライバーが**SQLExtendedFetch**をサポートしていない場合、ドライバー マネージャーは **、1**つの行のみをフェッチできる ODBC 2 *.x*ドライバーで**SQLFetch**呼び出しをマップします。  
  
 詳細については、「付録 G: 下位互換性のためのドライバガイドライン」の[「ブロック カーソル、スクロール可能なカーソル、および後方互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)」を参照してください。  
  
## <a name="positioning-the-cursor"></a>カーソルの位置決め  
 結果セットが作成されると、カーソルは結果セットの先頭の前に置かれます。 **次の**行セットをフェッチします。 これは、SQL_FETCH_NEXTに設定*されたフェッチオリエンテーション*を使用して**SQLFetchScroll**を呼び出すのと同じです。 カーソルの詳細については、「[カーソル](../../../odbc/reference/develop-app/cursors.md)と[ブロック カーソル](../../../odbc/reference/develop-app/block-cursors.md)」を参照してください。  
  
 SQL_ATTR_ROW_ARRAY_SIZEステートメント属性は、行セット内の行数を指定します。 **SQLFetch**によってフェッチされる行セットが結果セットの末尾と重なる場合 **、SQLFetch は**部分的な行セットを返します。 つまり、S + R - 1 が L より大きい場合、S がフェッチされる行セットの開始行、R が行セットのサイズ、L が結果セットの最後の行、行セットの最初の L - S + 1 行のみが有効です。 残りの行は空で、ステータスはSQL_ROW_NOROWです。  
  
 **SQLFetch が**戻った後、現在の行は行セットの最初の行です。  
  
 次の表に示すルールでは、このセクションの 2 番目の表に示した条件に基づいて **、 SQLFetch**を呼び出した後のカーソルの位置を示します。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|開始前|1|  
|*カーロウセットスタート*\<= *ラスト結果行 - 行セットサイズ*[1]|*行セットの開始* + *サイズ*[2]|  
|*カーロウセットスタート* > *ラスト結果行 - 行セットサイズ*[1]|終了後|  
|終了後|終了後|  
  
 [1] フェッチの間に行セットのサイズが変更された場合、これは前のフェッチで使用された行セットサイズです。  
  
 [2] フェッチの間に行セットのサイズが変更された場合、これは新しいフェッチで使用された行セットサイズです。  
  
|Notation|意味|  
|--------------|-------------|  
|開始前|ブロック カーソルは、結果セットの先頭の前に配置されます。 新しい行セットの最初の行が結果セットの開始前の場合 **、SQLFetch は**SQL_NO_DATAを返します。|  
|終了後|ブロック カーソルは、結果セットの終了後に位置付けられます。 新しい行セットの最初の行が結果セットの終了後にある場合 **、SQLFetch は**SQL_NO_DATAを返します。|  
|*カーロウセットスタート*|現在の行セットの最初の行の番号。|  
|*ラストプロスロウ*|結果セットの最後の行の番号。|  
|*行セットサイズ*|行セットのサイズ。|  
  
 たとえば、結果セットに 100 行があり、行セットのサイズが 5 であるとします。 次の表は **、SQLFetch**が返す、さまざまな開始位置の行セットと戻りコードを示しています。  
  
|現在の行セット|リターン コード|新しい行セット|取得された行数|  
|--------------------|-----------------|----------------|------------------------|  
|開始前|SQL_SUCCESS|1から5まで|5|  
|1から5まで|SQL_SUCCESS|6~10|5|  
|52~56|SQL_SUCCESS|57~61|5|  
|91から95まで|SQL_SUCCESS|96~100|5|  
|93~97|SQL_SUCCESS|98から100まで。 行の状態配列の行 4 と 5 は、SQL_ROW_NOROW に設定されます。|3|  
|96~100|SQL_NO_DATA|なし。|0|  
|99から100まで|SQL_NO_DATA|なし。|0|  
|終了後|SQL_NO_DATA|なし。|0|  
  
## <a name="returning-data-in-bound-columns"></a>バインドされた列のデータを返す  
 **SQLFetch は**各行を返すので、その列にバインドされたバッファー内の各バインドされた列のデータを格納します。 列がバインドされていない場合 **、SQLFetch**はデータを返しませんが、ブロック カーソルを前方に移動します。 **SQLGetData**を使用してデータを取得できます。 カーソルが複数行カーソルの場合 (つまり、SQL_ATTR_ROW_ARRAY_SIZEが 1 より大きい場合)、情報*型*をSQL_GETDATA_EXTENSIONSに指定して**SQLGetInfo**が呼び出されたときにSQL_GD_BLOCKが返された場合にのみ **、SQLGetData**を呼び出すことができます。 (詳細については[、「SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)」を参照してください)。  
  
 行のバインドされた列ごとに **、SQLFetch**は次の処理を行います。  
  
1.  長さ/インジケーター バッファーをSQL_NULL_DATAに設定し、データが NULL の場合は次の列に進みます。 データが NULL で、長さ/標識バッファーがバインドされていない場合 **、SQLFetch**は行に対して SQLSTATE 22002 (標識変数が必要だが、指定されていない) を戻し、次の行に進みます。 長さ/インジケーター バッファーのアドレスを決定する方法については、 [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)の「バッファー アドレス」を参照してください。  
  
     列のデータが NULL でない場合 **、SQLFetch**は手順 2 に進みます。  
  
2.  SQL_ATTR_MAX_LENGTH ステートメント属性が 0 以外の値に設定され、列に文字またはバイナリ データが含まれている場合、データは SQL_ATTR_MAX_LENGTH バイトに切り捨てられます。  
  
    > [!NOTE]  
    >  SQL_ATTR_MAX_LENGTHステートメント属性は、ネットワーク・トラフィックを削減することを目的としています。 通常はデータ ソースによって実装され、データをネットワーク経由で返す前に切り捨てられます。 ドライバーとデータ ソースは、それをサポートする必要はありません。 したがって、データが特定のサイズに切り捨てられることを保証するために、アプリケーションはそのサイズのバッファーを割り当て **、SQLBindCol**の*引数 cbValueMax*にサイズを指定する必要があります。  
  
3.  **データを、SQLBindCol**で*指定された型*に変換します。  
  
4.  データが文字やバイナリなどの可変長データ型に変換された場合 **、SQLFetch**はデータの長さがデータ バッファーの長さを超えているかどうかをチェックします。 文字データの長さ (ヌル終了文字を含む) がデータ・バッファーの長さを超えた場合 **、SQLFetch**はデータ・バッファーの長さから NULL 終了文字の長さを減らすデータを切り捨てます。 その後、データを null 終了します。 バイナリ データの長さがデータ バッファーの長さを超える場合 **、SQLFetch**はデータ バッファーの長さに切り捨てます。 データ バッファーの長さは、 **SQLBindCol**の*バッファー長*で指定します。  
  
     **SQLFetch**は、固定長データ型に変換されたデータを切り捨てることはありません。常にデータ バッファーの長さがデータ型のサイズであると想定します。  
  
5.  変換された (場合によっては切り捨てられた) データをデータ バッファーに格納します。 データ バッファーのアドレスを決定する方法については、 [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)の「バッファー アドレス」を参照してください。  
  
6.  データの長さを長さ/インジケーター バッファーに入れます。 標識ポインターと長さポインターの両方が同じバッファーに設定されている場合 **(SQLBindCol**の呼び出しが行うように)、長さは有効なデータのバッファーに書き込まれ、SQL_NULL_DATAは NULL データのバッファーに書き込まれます。 長さ/インジケーター バッファーがバインドされていない場合 **、SQLFetch**は長さを返しません。  
  
    -   文字データまたはバイナリ データの場合、これは、データ バッファーが小さすぎるため、変換後と切り捨て前のデータの長さです。 ドライバーは、変換後にデータの長さを決定できない場合は、長いデータの場合もある場合は、SQL_NO_TOTALに長さを設定します。 SQL_ATTR_MAX_LENGTHステートメント属性のためにデータが切り捨てられた場合、この属性の値は実際の長さの代わりに長さ/標識バッファーに入れられます。 これは、この属性は変換前にサーバー上のデータを切り捨てるように設計されているため、ドライバーは実際の長さを把握する方法がありません。  
  
    -   その他のすべてのデータ型では、変換後のデータの長さになります。つまり、データの変換先の型のサイズです。  
  
     長さ/インジケーター バッファーのアドレスを決定する方法については、 [SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)の「バッファー アドレス」を参照してください。  
  
7.  変換時に有効桁が失われずにデータが切り捨てられる場合 (例えば、変換時に実数 1.234 が整数 1 に切り捨てられる場合 **)、SQLFetch**は SQLSTATE 01S07 (分数切り捨て) を返し、SQL_SUCCESS_WITH_INFO。 データ バッファーの長さが小さすぎるためにデータが切り捨てられる場合 (たとえば、文字列 "abcdef" が 4 バイト のバッファーに入れられて) **SQLFetch**は SQLSTATE 01004 (データの切り捨て) を返し、SQL_SUCCESS_WITH_INFO。 SQL_ATTR_MAX_LENGTHステートメント属性が原因でデータが切り捨てられる場合 **、SQLFetch**はSQL_SUCCESSを戻し、SQLSTATE 01S07 (分数切り捨て) または SQLSTATE 01004 (データ切り捨て) を戻しません。 変換時にデータが切り捨てられ、有効桁が失われる場合 (たとえば、100,000 を超えるSQL_INTEGER値がSQL_C_TINYINTに変換された場合 **)、SQLFetch**は SQLSTATE 22003 (数値が範囲外) またはSQL_SUCCESS_WITH_INFO (行セット・サイズが 1 より大きい場合 SQL_ERROR) を戻します。  
  
 SQLFetch または**SQLFetchScroll**がSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返さない場合、バインドされた**SQLFetchScroll**データ バッファーと長さ/インジケーター バッファーの内容は未定義です。  
  
## <a name="row-status-array"></a>行の状態の配列  
 行の状態配列は、行セットの各行の状態を返すために使用されます。 この配列のアドレスは、SQL_ATTR_ROW_STATUS_PTR ステートメント属性で指定されます。 配列はアプリケーションによって割り当てられ、SQL_ATTR_ROW_ARRAY_SIZEステートメント属性で指定された数の要素が必要です。 値は **、SQLFetch** **、SQLFetchScroll、** および**SQLBulkOperations**または**SQLSetPos**によって設定されます (カーソルが**SQLExtendedFetch**によって配置された後に呼び出された場合を除く)。 SQL_ATTR_ROW_STATUS_PTRステートメント属性の値が null ポインターの場合、これらの関数は行の状態を返しません。  
  
 行の状態の配列バッファーの内容は **、SQLFetch**または**SQLFetchScroll**がSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返さない場合は未定義です。  
  
 行の状態の配列に次の値が返されます。  
  
|行ステータス配列値|説明|  
|----------------------------|-----------------|  
|SQL_ROW_SUCCESS|行は正常にフェッチされ、この結果セットから最後にフェッチされてから変更されていません。|  
|SQL_ROW_SUCCESS_WITH_INFO|行は正常にフェッチされ、この結果セットから最後にフェッチされてから変更されていません。 ただし、行に関する警告が返されました。|  
|SQL_ROW_ERROR|行のフェッチ中にエラーが発生しました。|  
|SQL_ROW_UPDATED[1]、[2]、および[3]|行は正常にフェッチされ、この結果セットから最後にフェッチされてから変更されました。 この結果セットから行が再度フェッチされるか **、SQLSetPos**によって更新された場合、ステータスは行の新しい状態に変更されます。|  
|SQL_ROW_DELETED[3]|この行は、この結果セットから最後にフェッチされてから削除されています。|  
|SQL_ROW_ADDED[4]|行は **、SQLBulkOperations**によって挿入されました。 この結果セットから行が再度フェッチされるか **、SQLSetPos**によって更新された場合、その状態はSQL_ROW_SUCCESS。|  
|SQL_ROW_NOROW|行セットは結果セットの末尾と重なり合っており、行ステータス配列のこの要素に対応する行は返されませんでした。|  
  
 [1] キーセット、混合、および動的カーソルの場合、キー値が更新された場合、データ行は削除されたと見なされ、新しい行が追加されます。  
  
 [2] 一部のドライバはデータの更新を検出できないため、この値を返すことができません。 ドライバーが再フェッチされた行の更新を検出できるかどうかを判断するには、アプリケーションは、SQL_ROW_UPDATES オプションを使用して**SQLGetInfo**を呼び出します。  
  
 **[3] SQLFetch の**呼び出しとの混合の場合にのみ、この値を返すことができます。 **SQLFetchScroll** これは **、SQLFetch**が結果セットを順方向に移動し、排他的に使用される場合は、行を再フェッチしないためです。 行は再フェッチされないため **、SQLFetch**は、以前にフェッチされた行に対して行われた変更を検出しません。 ただし **、SQLFetchScroll**が以前にフェッチされた行の前にカーソルを配置し **、SQLFetch**を使用してそれらの行をフェッチすると **、SQLFetch**はそれらの行に対する変更を検出できます。  
  
 [4] SQLBulk オペレーションによってのみ返されます。 **SQL フェッチ**または SQL**フェッチスクロール**によって設定されていません。  
  
### <a name="rows-fetched-buffer"></a>行フェッチバッファ  
 フェッチされた行バッファは、フェッチ中にエラーが発生したためにデータが返されなかった行を含め、フェッチされた行数を返すために使用されます。 つまり、行の状態配列の値がSQL_ROW_NOROWされていない行数です。 このバッファーのアドレスは、SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性で指定されます。 バッファはアプリケーションによって割り当てられます。 これは **、SQL フェッチ**と**SQL フェッチスクロール**によって設定されます。 SQL_ATTR_ROWS_FETCHED_PTRステートメント属性の値が null ポインターの場合、これらの関数はフェッチされた行数を返しません。 結果セット内の現在の行の数を確認するために、アプリケーションは、SQL_ATTR_ROW_NUMBER属性を指定して**SQLGetStmtAttr**を呼び出すことができます。  
  
 sqlFetch または**SQLFetchScroll**がSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返**SQLFetchScroll**さない場合、SQL_NO_DATAが返される場合を除き、フェッチされたバッファーの行の内容は未定義です。  
  
### <a name="error-handling"></a>エラー処理  
 エラーと警告は、個々の行または関数全体に適用できます。 診断レコードの詳細については、「[診断](../../../odbc/reference/develop-app/diagnostics.md)と[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)」を参照してください。  
  
#### <a name="errors-and-warnings-on-the-entire-function"></a>関数全体のエラーと警告  
 SQLSTATE HYT00 (タイムアウト期限切れ) や SQLSTATE 24000 (無効なカーソル状態) などのエラーが関数全体に適用される場合 **、SQLFetch は**SQL_ERRORおよび該当する SQLSTATE を戻します。 行セット バッファーの内容は未定義で、カーソル位置は変更されません。  
  
 警告が関数全体に適用される場合 **、SQLFetch は**SQL_SUCCESS_WITH_INFOと該当する SQLSTATE を返します。 関数全体に適用される警告の状況レコードは、個々の行に適用される状況レコードの前に戻されます。  
  
#### <a name="errors-and-warnings-in-individual-rows"></a>個々の行のエラーと警告  
 エラー (SQLSTATE 22012 (ゼロ除算) など) または警告 (SQLSTATE 01004 (データ切り捨て) など) が 1 行に該当する場合 **、SQLFetch**は次の処理を実行します。  
  
-   エラーの場合は、行の状態配列の対応する要素をSQL_ROW_ERROR、警告のSQL_ROW_SUCCESS_WITH_INFOに設定します。  
  
-   エラーまたは警告に対して SQLSTATE を含むゼロ個以上の状況レコードを追加します。  
  
-   ステータス レコードの行番号と列番号フィールドを設定します。 **SQLFetch が**行番号または列番号を判別できない場合は、その番号をそれぞれ SQL_ROW_NUMBER_UNKNOWN または SQL_COLUMN_NUMBER_UNKNOWN に設定します。 ステータス レコードが特定の列に適用されない場合 **、SQLFetch**は列番号をSQL_NO_COLUMN_NUMBERに設定します。  
  
 **SQLFetch は**、行セット内のすべての行をフェッチするまで、行のフェッチを続行します。 行セットのすべての行 (ステータス SQL_ROW_NOROWを含まない行を除く) でエラーが発生しない限り、SQL_SUCCESS_WITH_INFOを返 SQL_ERRORします。 特に、行セットのサイズが 1 で、その行にエラーが発生した場合 **、SQLFetch は**SQL_ERRORを返します。  
  
 **SQLFetch は**、行番号順の状態レコードを返します。 つまり、不明な行 (存在する場合) のすべての状態レコードを返します。次に、最初の行のすべての状態レコード (存在する場合) を返し、2 番目の行 (存在する場合) のすべての状態レコードを返します。 各行のステータスレコードは、ステータスレコードの順序付けの通常の規則に従って順序付けられます。詳細については、 [SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)の「状態レコードのシーケンス」を参照してください。  
  
### <a name="descriptors-and-sqlfetch"></a>記述子と SQL フェッチ  
 以下のセクションでは **、SQLFetch**が記述子と対話する方法について説明します。  
  
#### <a name="argument-mappings"></a>引数マッピング  
 ドライバーは**SQLFetch**の引数に基づいて記述子フィールドを設定しません。  
  
#### <a name="other-descriptor-fields"></a>その他の記述子フィールド  
 次の記述子フィールドは**SQLFetch**によって使用されます。  
  
|記述子フィールド|Desc。|フィールドの入力|設定スルー|  
|----------------------|-----------|--------------|-----------------|  
|SQL_DESC_ARRAY_SIZE|Ard|header|SQL_ATTR_ROW_ARRAY_SIZEステートメント属性|  
|SQL_DESC_ARRAY_STATUS_PTR|Ird|header|SQL_ATTR_ROW_STATUS_PTRステートメント属性|  
|SQL_DESC_BIND_OFFSET_PTR|Ard|header|SQL_ATTR_ROW_BIND_OFFSET_PTRステートメント属性|  
|SQL_DESC_BIND_TYPE|Ard|header|SQL_ATTR_ROW_BIND_TYPEステートメント属性|  
|SQL_DESC_COUNT|Ard|header|*列番号*引数**SQLBindCol**|  
|SQL_DESC_DATA_PTR|Ard|records|*TargetValuePtr***引数を指定します。**|  
|SQL_DESC_INDICATOR_PTR|Ard|records|*StrLen_or_IndPtr*引数**SQLBindCol**|  
|SQL_DESC_OCTET_LENGTH|Ard|records|**バッファ***長引数*|  
|SQL_DESC_OCTET_LENGTH_PTR|Ard|records|*StrLen_or_IndPtr*引数**SQLBindCol**|  
|SQL_DESC_ROWS_PROCESSED_PTR|Ird|header|SQL_ATTR_ROWS_FETCHED_PTRステートメント属性|  
|SQL_DESC_TYPE|Ard|records|*ターゲットタイプ*引数**SQLBindCol**|  
  
 すべての記述子フィールドは **、 SQLSetDescField を**使用して設定することもできます。  
  
#### <a name="separate-length-and-indicator-buffers"></a>長さとインジケーターのバッファを分離  
 アプリケーションは、長さと標識の値を保持するために使用できる単一のバッファーまたは 2 つの別個のバッファーをバインドできます。 アプリケーションが**SQLBindCol**を呼び出すと、ドライバーは、StrLen_or_IndPtr*引数に*渡される同じアドレスに、ARD のSQL_DESC_OCTET_LENGTH_PTRとSQL_DESC_INDICATOR_PTRフィールドを設定します。 アプリケーションが呼び出すとき**に、SQLSetDescField**または**SQLSetDescRec**これらの 2 つのフィールドを異なるアドレスに設定できます。  
  
 **SQLFetch**は、アプリケーションが別の長さとインジケーター バッファーを指定するかどうかを決定します。 この場合、データが NULL でない場合 **、SQLFetch**は、インジケーター バッファーを 0 に設定し、長さのバッファーの長さを返します。 データが NULL の場合 **、SQLFetch**はインジケーター バッファーをSQL_NULL_DATAに設定し、長さのバッファーを変更しません。  
  
### <a name="code-example"></a>コード例  
 「SQL[バインドコル](../../../odbc/reference/syntax/sqlbindcol-function.md) [、SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md) [、SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)、および SQL プロシージャ 」を[参照してください](../../../odbc/reference/syntax/sqlprocedures-function.md)。  
  
### <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|SQL ステートメントの実行|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|ステートメントのカーソルをクローズする|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|データ列の一部または全部をフェッチする|[SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|結果セット列の数を返す|[SQLNumResultCols 関数](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|実行のためのステートメントの準備|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
