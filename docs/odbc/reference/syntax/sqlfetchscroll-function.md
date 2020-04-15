---
title: 関数を呼び出す |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLFetchScroll
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLFetchScroll
helpviewer_keywords:
- SQLFetchScroll function [ODBC]
ms.assetid: c0243667-428c-4dda-ae91-3c307616a1ac
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6c65ef71f5c2cb9202ab788cac5e00357674f4a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285882"
---
# <a name="sqlfetchscroll-function"></a>SQLFetchScroll 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLFetchScroll**は、指定されたデータの行セットを結果セットからフェッチし、すべてのバインドされた列のデータを返します。 行セットは、絶対位置または相対位置またはブックマークで指定できます。  
  
 ODBC 2.x ドライバーを操作する場合、ドライバー マネージャーは、この関数を**SQLExtendedFetch**にマップします。 詳細については、「[アプリケーションの下位互換性を確保するための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLFetchScroll(  
      SQLHSTMT      StatementHandle,  
      SQLSMALLINT   FetchOrientation,  
      SQLLEN        FetchOffset);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *フェッチオリエンテーション*  
 [入力]  
  
 フェッチのタイプ:  
  
 SQL_FETCH_NEXT  
  
 SQL_FETCH_PRIOR  
  
 SQL_FETCH_FIRST  
  
 SQL_FETCH_LAST  
  
 SQL_FETCH_ABSOLUTE  
  
 SQL_FETCH_RELATIVE  
  
 SQL_FETCH_BOOKMARK  
  
 詳細については、「コメント」セクションの「カーソルの位置」を参照してください。  
  
 *フェッチオフセット*  
 [入力]  
  
 フェッチする行の番号。 この引数の解釈は、*引数の値によって*異なります。 詳細については、「コメント」セクションの「カーソルの位置」を参照してください。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLFetchScroll が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返す場合、SQL_HANDLE_STMTのハンドル型とステートメント ハンドルハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLFetchScroll**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。 1 つの列でエラーが発生した場合は、エラーが発生した列を判別するために、SQL_DIAG_COLUMN_NUMBERの DiagIdentifier を使用して**SQLGetDiagField**を呼び出すことができます。**SQLGetDiagField**は、その列を含む行を決定するSQL_DIAG_ROW_NUMBERの DiagIdentifier を使用して呼び出すことができます。  
  
 SQL_SUCCESS_WITH_INFOまたはSQL_ERRORを返すことができるすべての SQLSTATE (01xxx SQLSTATE を除く) では、複数行操作の 1 つ以上の行でエラーが発生した場合はSQL_SUCCESS_WITH_INFOが返され、単一行操作でエラーが発生した場合はSQL_ERRORが返されます。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|列に対して返された文字列データまたはバイナリ データの結果、空白以外の文字または NULL 以外のバイナリ データが切り捨てられます。 文字列値の場合は、右に切り捨てられます。|  
|01S01|行内エラー|1 つ以上の行をフェッチ中にエラーが発生しました。<br /><br /> (ODBC 3 *.x*アプリケーションが ODBC 2 *.x*ドライバーを使用しているときにこの SQLSTATE が返される場合は、無視できます。|  
|01S06|結果セットが最初の行セットを返す前にフェッチを試みる|FetchOrientation がSQL_FETCH_PRIORされ、現在の位置が最初の行を超え、現在の行の数が行セット サイズ以下であった場合に、要求された行セットが結果セットの先頭と重なっていました。<br /><br /> FetchOrientation がSQL_FETCH_PRIORされ、現在の位置が結果セットの末尾を超え、行セットのサイズが結果セットのサイズより大きかった場合に、要求された行セットが結果セットの開始位置と重なっていました。<br /><br /> FetchOrientation がSQL_FETCH_RELATIVEされ、FetchOffset が負の値であり、FetchOffset の絶対値が行セット サイズ以下であった場合に、要求された行セットが結果セットの開始と重なっていました。<br /><br /> FetchOrientation がSQL_FETCH_ABSOLUTEされ、FetchOffset が負の値であり、FetchOffset の絶対値が結果セットサイズより大きく、行セットサイズ以下であった場合に、要求された行セットが結果セットの開始と重なりました。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S07|分数切り捨て|列に対して返されたデータが切り捨てられました。 数値データ型の場合、数値の小数部分は切り捨てられました。 時間、タイム・スタンプ、および時間コンポーネントを含む間隔データ・タイプの場合、時間の小数部分は切り捨てられました。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07006|制限付きデータ型属性違反|結果セット内の列のデータ値を **、SQLBindCol**で*TargetType*で指定されたデータ型に変換できませんでした。<br /><br /> 列 0 は、SQL_C_BOOKMARKのデータ型でバインドされ、SQL_ATTR_USE_BOOKMARKSステートメント属性がSQL_UB_VARIABLEに設定されました。<br /><br /> 列 0 は SQL_C_VARBOOKMARK のデータ型でバインドされ、SQL_ATTR_USE_BOOKMARKS ステートメント属性がSQL_UB_VARIABLEに設定されていません。|  
|07009|記述子インデックスが無効です|ドライバは**SQLExtendedFetch**をサポートしない ODBC 2 *.x*ドライバであり、列のバインドで指定された列番号は 0 でした。<br /><br /> 列 0 がバインドされ、SQL_ATTR_USE_BOOKMARKS ステートメント属性がSQL_UB_OFFに設定されました。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|22001|文字列データ(右切り捨て)|列に対して返された可変長ブックマークが切り捨てられました。|  
|22002|インジケーター変数が必要ですが、指定されていません|NULL データは **、SQLBindCol**によって設定された*StrLen_or_IndPtr* (または**SQLSetDesc フィールドまたは SQLSetDescRec**によって設定SQL_DESC_INDICATOR_PTR) が NULL ポインターである列にフェッチされました。 **SQLSetDescRec**|  
|22003|範囲外の数値|1 つ以上のバインドされた列の数値 (数値または文字列) を返すと、数値の整数部分 (小数部ではなく) が切り捨てられます。<br /><br /> 詳細については、「 付録 D : データ型 」の[「SQL から C データ型への](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)データの変換」を[参照してください](../../../odbc/reference/appendixes/appendix-d-data-types.md)。|  
|22007|日付/時刻形式が無効です|結果セット内の文字列が日付、時刻、またはタイム・スタンプ C の構造にバインドされ、列の値がそれぞれ無効な日付、時刻、またはタイム・スタンプであった。|  
|22012|ゼロ除算|算術式の値が返され、結果として 0 除算が行われました。|  
|22015|間隔フィールドのオーバーフロー|正確な数値または間隔の SQL タイプから間隔 C タイプに割り当てると、先行フィールドの有効桁数が失われます。<br /><br /> データを間隔 C 型にフェッチする場合、間隔 C 型の SQL 型の値の表現はありませんでした。|  
|22018|キャスト指定に無効な文字値|結果セット内の文字列が文字 C バッファーにバインドされ、その列にバッファーの文字セットに表現が含まれていない文字が含まれていました。<br /><br /> C 型は、正確な数値または概数、日時、または間隔のデータ型でした。列の SQL 型は文字データ型でした。列の値が、バインドされた C 型の有効なリテラルではありません。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*は実行済み状態でしたが、結果セットはステートメント ハンドルに関連付*けられません*。|  
|40001|シリアル化の失敗|デッドロックを防ぐために、フェッチが実行されたトランザクションが終了しました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、*ステートメント ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、関数は*ステートメント ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLFetchScroll**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM) 指定された*ステートメント ハンドル*が実行状態にありません。 関数は、最初に呼び出**さずに****呼**び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM) **SQLFetch**は **、SQLExtendedFetch**が呼び出された後、およびSQL_CLOSE オプションを指定した**SQLFreeStmt**が呼び出される前にステートメント*ハンドル*に対して呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|SQL_ATTR_USE_BOOKMARKステートメント属性がSQL_UB_VARIABLE に設定され、列 0 は、この結果セットのブックマークの最大長と等しくない長さのバッファーにバインドされました。 (この長さは IRD のSQL_DESC_OCTET_LENGTH フィールドで使用でき **、SQLDescribeCol** **、SQLCol 属性**、または**SQLGetDescField**を呼び出すことによって取得できます。|  
|HY106|フェッチタイプが範囲外です|DM) 引数 FetchOrientation に指定された値が無効です。<br /><br /> (DM) 引数 FetchOrientation がSQL_FETCH_BOOKMARKされ、SQL_ATTR_USE_BOOKMARKSステートメント属性がSQL_UB_OFFに設定されました。<br /><br /> SQL_ATTR_CURSOR_TYPE ステートメント属性の値がSQL_CURSOR_FORWARD_ONLYされ、引数 FetchOrientation の値がSQL_FETCH_NEXTされませんでした。<br /><br /> SQL_ATTR_CURSOR_SCROLLABLE ステートメント属性の値がSQL_NONSCROLLABLEされ、引数 FetchOrientation の値がSQL_FETCH_NEXTされませんでした。|  
|HY107|行の値が範囲外です|SQL_ATTR_CURSOR_TYPEステートメント属性で指定された値はSQL_CURSOR_KEYSET_DRIVENされましたが、SQL_ATTR_KEYSET_SIZEステートメント属性で指定された値が 0 より大きく、SQL_ATTR_ROW_ARRAY_SIZEステートメント属性で指定された値より小さくなっています。|  
|HY111|ブックマーク値が無効です|引数 FetchOrientation がSQL_FETCH_BOOKMARKされ、SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性の値が指すブックマークが無効であるか、null ポインターでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|ドライバーまたはデータ ソースは **、SQLBindCol**の*ターゲットの種類*と、対応する列の SQL データ型の組み合わせで指定された変換をサポートしていません。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが要求された結果セットを返しました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUTSQLSetStmtAttr を使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 **結果**セットから指定された行セットを返します。 行セットは、絶対位置または相対位置またはブックマークで指定できます。 **SQLFetchScroll**は、結果セットが存在する場合、つまり、結果セットを作成する呼び出しの後、その結果セットに対するカーソルが閉じられる前にだけ呼び出すことができます。 列がバインドされている場合は、それらの列のデータを返します。 アプリケーションが、フェッチされた行の数を返す行状態配列またはバッファーへのポインターを指定した場合は **、SQLFetchScroll**もこの情報を返します。 **SQLFetchScroll**の呼び出しは **、SQLFetch**の呼び出しと混在できますが、**呼**び出しとを混合することはできません。  
  
 詳細については、「[ブロック カーソルの使用](../../../odbc/reference/develop-app/using-block-cursors.md)および[スクロール可能なカーソルの使用](../../../odbc/reference/develop-app/using-scrollable-cursors.md)」を参照してください。  
  
## <a name="positioning-the-cursor"></a>カーソルの位置決め  
 結果セットが作成されると、カーソルは結果セットの先頭の前に置かれます。 **次**の表に示すように、*フェッチの位置*指定と*フェッチオフセット*の引数の値に基づいて、ブロック カーソルを配置します。 新しい行セットの開始を決定するための正確な規則を次のセクションに示します。  
  
|フェッチオリエンテーション|意味|  
|----------------------|-------------|  
|SQL_FETCH_NEXT|次の行セットを返します。 これは **、 SQLFetch**を呼び出すのと同じです。<br /><br /> **の**値を無視*します*。|  
|SQL_FETCH_PRIOR|前の行セットを返します。<br /><br /> **の**値を無視*します*。|  
|SQL_FETCH_RELATIVE|現在の行セットの先頭から行セット*FetchOffset*を返します。|  
|SQL_FETCH_ABSOLUTE|行*フェッチオフセット*から始まる行セットを返します。|  
|SQL_FETCH_FIRST|結果セットの最初の行セットを返します。<br /><br /> **の**値を無視*します*。|  
|SQL_FETCH_LAST|結果セット内の最後の完全な行セットを返します。<br /><br /> **の**値を無視*します*。|  
|SQL_FETCH_BOOKMARK|SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性で指定されたブックマークから、行セット FetchOffset 行を返します。|  
  
 ドライバは、すべてのフェッチの向きをサポートする必要はありません。アプリケーションは、(カーソルの種類に応じて) SQL_DYNAMIC_CURSOR_ATTRIBUTES1、SQL_KEYSET_CURSOR_ATTRIBUTES1、またはSQL_STATIC_CURSOR_ATTRIBUTES1の情報の種類を使用して**SQLGetInfo**を呼び出して、ドライバーでサポートされているフェッチの向きを決定します。 アプリケーションでは、これらの情報タイプのSQL_CA1_NEXT、SQL_CA1_RELATIVE、SQL_CA1_ABSOLUTE、およびWQL_CA1_BOOKMARKビットマスクを調べてください。 さらに、カーソルが前方専用であり、フェッチオリエンテーションがSQL_FETCH_NEXTされていない場合は **、SQLFetchScroll は**SQLSTATE HY106 (フェッチタイプが範囲外) を返します。  
  
 SQL_ATTR_ROW_ARRAY_SIZEステートメント属性は、行セット内の行数を指定します。 **SQLFetchScroll**によってフェッチされている行セットが結果セットの末尾と重なる**場合、部分的**な行セットが返されます。 つまり、S + R - 1 が L より大きい場合、S がフェッチされる行セットの開始行、R が行セットのサイズ、L が結果セットの最後の行、行セットの最初の L - S + 1 行のみが有効です。 残りの行は空で、ステータスはSQL_ROW_NOROWです。  
  
 **SQLFetchScroll が**戻った後、現在の行は行セットの最初の行です。  
  
## <a name="cursor-positioning-rules"></a>カーソルの位置指定規則  
 次のセクションでは、フェッチオリエンテーションの各値の正確な規則について説明します。 これらの規則は、次の表記法を使用します。  
  
|Notation|意味|  
|--------------|-------------|  
|*開始前*|ブロック カーソルは、結果セットの先頭の前に配置されます。 新しい行セットの最初の行が結果セットの開始より前の場合 **、SQLFetchScroll は**SQL_NO_DATAを返します。|  
|*終了後*|ブロック カーソルは、結果セットの終了後に位置付けられます。 新しい行セットの最初の行が結果セットの終了後にある場合 **、SQLFetchScroll は**SQL_NO_DATAを返します。|  
|*カーロウセットスタート*|現在の行セットの最初の行の番号。|  
|*ラストプロスロウ*|結果セットの最後の行の番号。|  
|*行セットサイズ*|行セットのサイズ。|  
|*フェッチオフセット*|引数の*値*。|  
|*ブックマーク行*|SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性で指定されたブックマークに対応する行。|  
  
## <a name="sql_fetch_next"></a>SQL_FETCH_NEXT  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*開始前*|1|  
|*カーロウセットスタート + 行セットサイズ*[1] * \<= 最後の結果行*|*カーロウセットスタート + 行セットサイズ*[1]|  
|*カーロウセットスタート + 行セットサイズ*[1]*>最終結果行*|*終了後*|  
|*終了後*|*終了後*|  
  
 [1] 行をフェッチする前の呼び出し以降に行セットのサイズが変更された場合、これは前の呼び出しで使用された行セットサイズです。  
  
## <a name="sql_fetch_prior"></a>SQL_FETCH_PRIOR  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*開始前*|*開始前*|  
|*カーロウセットスタート = 1*|*開始前*|  
|*1 <カーロウセットスタート<= 行セットサイズ* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*カーロウセット>行セットサイズ* <sup>[2]</sup>|*カーロウセットスタート - 行セットサイズ* <sup>[2]</sup>|  
|*終了後と最後の結果行<行セットサイズ* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*終了後と最後の結果行>= 行セットサイズ* <sup>[2]</sup>|*最後の結果行 - 行セットサイズ + 1* <sup>[2]</sup>|  
  
 [1] **SQLFetchScroll は**SQLSTATE 01S06 (結果セットが最初の行セットを返す前にフェッチを試みる) を返し、SQL_SUCCESS_WITH_INFO。  
  
 [2] 行をフェッチする前の呼び出し以降に行セットのサイズが変更された場合、これは新しい行セットサイズです。  
  
## <a name="sql_fetch_relative"></a>SQL_FETCH_RELATIVE  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*(開始前に AND フェッチオフセット > 0)OR (終了後およびフェッチオフセット< 0)*|*--*<sup>[1]</sup>|  
|*開始前とフェッチオフセット<= 0*|*開始前*|  
|*カーロウセットスタート = 1 およびフェッチオフセット < 0*|*開始前*|  
|*カーロウセットスタート > 1 とカーロウセットスタート + フェッチオフセット < 1 および&#124;フェッチオフセット &#124; > 行セットサイズ* <sup>[3]</sup>|*開始前*|  
|*カーロウセットスタート > 1 and currRowsetStart + フェッチオフセット < 1 と &#124;フェッチオフセット &#124; <= 行セットサイズ =行オフセット* <sup>[3]</sup>|*1* <sup>[2]</sup>|  
|*1 <= カーロウセットスタート\<+ フェッチオフセット = 最後の結果行*|*カローセットスタート + フェッチオフセット*|  
|*カーロウセットスタート + フェッチオフセット>最後の結果行*|*終了後*|  
|*終了後およびフェッチオフセット>= 0*|*終了後*|  
  
 [1] ***SQLFetchScroll は***、フェッチオリエンテーションがSQL_FETCH_ABSOLUTEに設定された場合に呼び出された場合と同じ行セットを返します。 詳細については、「SQL_FETCH_ABSOLUTE」セクションを参照してください。  
  
 [2] **SQLFetchScroll は**SQLSTATE 01S06 (結果セットが最初の行セットを返す前にフェッチを試みる) を返し、SQL_SUCCESS_WITH_INFO。  
  
 [3] 行をフェッチする前の呼び出し以降に行セットのサイズが変更された場合、これは新しい行セットサイズです。  
  
## <a name="sql_fetch_absolute"></a>SQL_FETCH_ABSOLUTE  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*フェッチオフセット < 0 とフェッチオフセット &#124; <= 最後の結果行&#124;*|*ラストプロスロウ + フェッチオフセット + 1*|  
|*フェッチ オフセット < 0 と &#124; フェッチ オフセット &#124; > 最後の結果行と&#124;フェッチ オフセット &#124; > 行セットサイズ* <sup>[2]</sup>|*開始前*|  
|*フェッチ オフセット < 0 と&#124; フェッチ オフセット &#124; > 最後の結果行と&#124; フェッチ オフセット &#124; <= 行セット サイズ* <sup>[2]</sup>|*1* <sup>[1]</sup>|  
|*フェッチオフセット = 0*|*開始前*|  
|*1 <=\<フェッチオフセット = 最終結果行*|*フェッチオフセット*|  
|*最後の結果行>オフセットをフェッチ*|*終了後*|  
  
 [1] **SQLFetchScroll は**SQLSTATE 01S06 (結果セットが最初の行セットを返す前にフェッチを試みる) を返し、SQL_SUCCESS_WITH_INFO。  
  
 [2] 行をフェッチする前の呼び出し以降に行セットのサイズが変更された場合、これは新しい行セットサイズです。  
  
 動的カーソルの行位置が未定であるため、動的カーソルに対して実行された絶対フェッチは、必要な結果を提供できません。 このような操作は、フェッチと、最初にフェッチの後にフェッチ相対値が続く操作と同じです。静的カーソルの絶対フェッチと同様に、アトミック操作ではありません。  
  
## <a name="sql_fetch_first"></a>SQL_FETCH_FIRST  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*[任意]*|*1*|  
  
## <a name="sql_fetch_last"></a>SQL_FETCH_LAST  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*行セットサイズ* <sup>[1]</sup> <= 最後の結果行|*最後の結果行 - 行セットサイズ + 1* <sup>[1]</sup>|  
|*行セットサイズ* <sup>[1]</sup> >最終結果行|*1*|  
  
 [1] 行をフェッチする前の呼び出し以降に行セットのサイズが変更された場合、これは新しい行セットサイズです。  
  
## <a name="sql_fetch_bookmark"></a>SQL_FETCH_BOOKMARK  
 次の規則が適用されます。  
  
|条件|新しい行セットの最初の行|  
|---------------|-----------------------------|  
|*ブックマーク行 + フェッチオフセット < 1*|*開始前*|  
|*1 <= ブックマーク行\<+ フェッチオフセット = 最終結果行*|*ブックマーク行 + フェッチオフセット*|  
|*ブックマーク行 + フェッチオフセット>最終結果行*|*終了後*|  
  
 ブックマークの詳細については、「[ブックマーク (ODBC) 」](../../../odbc/reference/develop-app/bookmarks-odbc.md)を参照してください。  
  
## <a name="effect-of-deleted-added-and-error-rows-on-cursor-movement"></a>カーソル移動に対する削除、追加、およびエラー行の影響  
 静的カーソルおよびキーセット ドリブン カーソルは、結果セットに追加された行を検出し、結果セットから削除された行を削除することがあります。 SQL_STATIC_CURSOR_ATTRIBUTES2およびSQL_KEYSET_CURSOR_ATTRIBUTES2オプションを指定して**SQLGetInfo**を呼び出し、SQL_CA2_SENSITIVITY_ADDITIONS、SQL_CA2_SENSITIVITY_DELETIONS、およびSQL_CA2_SENSITIVITY_UPDATESビットマスクを調べて、アプリケーションは、特定のドライバーによって実装されたカーソルがこれを行うかどうかを判断します。 削除された行を検出して削除できるドライバについては、次の段落でこの動作の影響について説明します。 削除された行を検出できるが削除できないドライバの場合、削除はカーソルの動きには影響を与えません。  
  
 カーソルが結果セットに追加された行を検出するか、結果セットから削除された行を削除すると、データをフェッチするときにのみ、これらの変更が検出されたかのように見えます。 これには、**フェッチ**オリエンテーションをSQL_FETCH_RELATIVEに設定し、FetchOffset を 0 に設定して同じ行セットを再フェッチする場合も含まれますが、SQL_REFRESHに設定された fOption を使用して SQLSetPos が呼び出された場合は含まれません。 後者の場合、行セット バッファーのデータは更新されますが、再フェッチは行われず、削除された行は結果セットから削除されません。 したがって、現在の行セットから行が削除されるか、または現在の行セットに挿入された場合、カーソルは行セット バッファーを変更しません。 その代わりに、削除された行を含む行セット、または挿入された行が含まれている行セットをフェッチしたときに、変更が検出されます。  
  
 次に例を示します。  
  
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
  
 **SQLFetchScroll**が現在の行セットに対する相対的な位置を持つ新しい行セットを返す場合 (つまり、FetchOrientation がSQL_FETCH_NEXT、SQL_FETCH_PRIOR、またはSQL_FETCH_RELATIVE) は、新しい行セットの開始位置を計算するときに、現在の行セットに対する変更を含みません。 ただし、現在の行セットの外部での変更は検出可能な場合は含まれません。 さらに **、SQLFetchScroll**が現在の行セットとは無関係の位置を持つ新しい行セットを返す場合 (つまり、FetchOrientation はSQL_FETCH_FIRST、SQL_FETCH_LAST、SQL_FETCH_ABSOLUTE、またはSQL_FETCH_BOOKMARK) には、現在の行セットに含まれている場合でも、検出可能なすべての変更が含まれます。  
  
 新しく追加された行が現在の行セットの内側か外側かを判断する場合、部分行セットは最後の有効な行で終了すると見なされます。つまり、行の状態がSQL_ROW_NOROWされていない最後の行。 たとえば、カーソルが新しく追加された行を検出でき、現在の行セットが部分的な行セットになり、アプリケーションが新しい行を追加し、カーソルがこれらの行を結果セットの末尾に追加するとします。 アプリケーションが SQL_FETCH_NEXT に設定されたフェッチオリエンテーションを使用して**SQLFetchScroll**を呼び出した場合、**最初**に追加された行から始まる行セットが返されます。  
  
 たとえば、現在の行セットが行 21 から 30、行セットサイズが 10、カーソルが結果セットから削除された行を削除し、カーソルが結果セットに追加された行を検出するとします。 次の表は、さまざまな状況で**SQLFetchScroll が**返す行を示しています。  
  
|Change|フェッチタイプ|フェッチオフセット|新しい行セット[1]|  
|------------|----------------|-----------------|---------------------|  
|行 21 の削除|NEXT|0|31~40|  
|行 31 の削除|NEXT|0|32~41|  
|行 21 と 22 の間に行を挿入します。|NEXT|0|31~40|  
|行 30 と 31 の間に行を挿入します。|NEXT|0|挿入された行、31から39|  
|行 21 の削除|PRIOR|0|11~20|  
|行 20 を削除する|PRIOR|0|10~19|  
|行 21 と 22 の間に行を挿入します。|PRIOR|0|11~20|  
|行 20 と 21 の間に行を挿入します。|PRIOR|0|12 から 20、挿入された行|  
|行 21 の削除|RELATIVE|0|22 から 31<sup>[2]</sup>|  
|行 21 の削除|RELATIVE|1|22~31|  
|行 21 と 22 の間に行を挿入します。|RELATIVE|0|21、挿入された行、22から29|  
|行 21 と 22 の間に行を挿入します。|RELATIVE|1|22~31|  
|行 21 の削除|ABSOLUTE|21|22 から 31<sup>[2]</sup>|  
|行 22 を削除する|ABSOLUTE|21|21、23、31|  
|行 21 と 22 の間に行を挿入します。|ABSOLUTE|22|挿入された行、22から29|  
  
 [1] この列は、行が挿入または削除される前の行番号を使用します。  
  
 [2] この場合、カーソルは行 21 から始まる行を返そうとします。 行 21 が削除されたため、返される最初の行は行 22 です。  
  
 エラー行 (ステータスがSQL_ROW_ERRORの行) は、カーソルの移動には影響しません。 たとえば、現在の行セットが行 11 で始まり、行 11 のステータスがSQL_ROW_ERROR場合、FetchOrientation を SQL_FETCH_RELATIVE に設定し、FetchOffset を 5 に設定して**SQLFetchScroll**を呼び出すと、行 16 から始まる行セット SQL_SUCCESSが返されます。  
  
## <a name="returning-data-in-bound-columns"></a>バインドされた列のデータを返す  
 **SQLFetchScroll と**同じ方法でバインドされた列にデータを返**します**。 詳細については、 [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)の「バインドされた列のデータを返す」を参照してください。  
  
 列がバインドされていない場合 **、SQLFetchScroll**はデータを返しませんが、ブロック カーソルを指定された位置に移動します。 **SQLGetData**を使用してブロック カーソルの非バインド列からデータを取得できるかどうかは、ドライバーによって異なります。 **SQLGetInfo**の呼び出しがSQL_GETDATA_EXTENSIONS情報の種類のSQL_GD_BLOCK ビットを返す場合、この機能はサポートされます。  
  
## <a name="buffer-addresses"></a>バッファ アドレス  
 **SQLFetchScroll は**、同じ数式を使用して **、SQLFetch**とデータのアドレスと長さ/インジケーター バッファーを決定します。 詳細については、 [SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)の「バッファ アドレス」を参照してください。  
  
## <a name="row-status-array"></a>行の状態の配列  
 **行**の状態の配列に値を設定する SQLFetch と同じ方法です。 詳細については、 [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)の「行の状態の配列」を参照してください。  
  
## <a name="rows-fetched-buffer"></a>行フェッチバッファ  
 **SQLFetchScroll と**同じ方法で、フェッチされたバッファー行でフェッチされた行の**数を返**します。 詳細については、 [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)の「バッファをフェッチした行」を参照してください。  
  
## <a name="error-handling"></a>エラー処理  
 アプリケーションが ODBC 3.x ドライバーで**SQLFetchScroll**を呼び出すと、ドライバー マネージャーは、ドライバーで**SQLFetchScroll**を呼び出します。 アプリケーションは、ODBC 2.x ドライバーで**SQLFetchScroll**を呼び出すと、ドライバー マネージャーは、ドライバーで SQLExtendedFetch を呼び出します。 **SQLFetchScroll**と SQLExtendedFetch は、エラーを処理する方法が少し異なるため、アプリケーションは、ODBC 2.x と ODBC 3.x ドライバーで**SQLFetchScroll**を呼び出すときに、わずかに異なるエラーの動作を参照してください。  
  
 **エラー**と警告を**SQLFetch**と同じ方法で返します。詳細については、 **SQLFetch**の「エラー処理」を参照してください。 **SQLExtendedFetch は**、次の例外を除き **、SQLFetch**と同じ方法でエラーを返します。  
  
 行セット内の特定の行に適用される警告が発生すると、SQLExtendedFetch は行の状態配列内の対応するエントリをSQL_ROW_SUCCESS_WITH_INFOではなくSQL_ROW_SUCCESSに設定します。  
  
 行セット内のすべての行でエラーが発生した場合、SQLExtendedFetch はSQL_ERRORではなくSQL_SUCCESS_WITH_INFOを返します。  
  
 個々の行に適用される状態レコードの各グループでは、SQLExtendedFetch によって返される最初の状態レコードに SQLSTATE 01S01 (行内エラー) が含まれている必要があります。**この SQL**ステートを返しません。 追加の SQLSTATE を返すことができない場合、この SQLSTATE を返す必要があります。  
  
## <a name="sqlfetchscroll-and-optimistic-concurrency"></a>SQL フェッチスクロールとオプティミスティック同時実行制御  
 カーソルがオプティミスティック同時実行制御を使用している場合 、つまり、SQL_ATTR_CONCURRENCY ステートメント属性の値がSQL_CONCUR_VALUESまたはSQL_CONCUR_ROWVERの場合 **、SQLFetchScroll**はデータ ソースが使用するオプティミスティック同時実行制御値を更新して、行が変更されたかどうかを検出します。 これは **、SQLFetchScroll**が新しい行セットをフェッチするたびに発生します( 現在の行セットを再フェッチするときも含む)。 (これは、フェッチオリエンテーションがSQL_FETCH_RELATIVEに設定され、FetchOffset が 0 に設定された場合に呼び出されます。  
  
## <a name="sqlfetchscroll-and-odbc-2x-drivers"></a>SQL フェッチスクロールと ODBC 2.x ドライバー  
 アプリケーションが ODBC 2.x ドライバーで**SQLFetchScroll**を呼び出すと、ドライバー マネージャーは、この呼び出しを**SQLExtendedFetch**にマップします。 **これは、SQLExtendedFetch**の引数に次の値を渡します。  
  
|引数|[値]|  
|-------------------------------|-----------|  
|ステートメントハンドル|ステートメントハンドルの**SQL フェッチスクロール**.|  
|フェッチオリエンテーション|**のフェッチ**オリエンテーション。|  
|フェッチオフセット|フェッチオリエンテーションがSQL_FETCH_BOOKMARKされていない場合は **、SQLFetchScroll**の引数の値が使用されます。<br /><br /> FetchOrientation がSQL_FETCH_BOOKMARK場合は、SQL_ATTR_FETCH_BOOKMARK_PTR ステートメント属性で指定されたアドレスに格納されている値が使用されます。|  
|行カウントプター|SQL_ATTR_ROWS_FETCHED_PTR ステートメント属性で指定されたアドレス。|  
|行の状態の配列|SQL_ATTR_ROW_STATUS_PTR ステートメント属性で指定されたアドレス。|  
  
 詳細については、「付録 G: 下位互換性のためのドライバガイドライン」の[「ブロック カーソル、スクロール可能なカーソル、および後方互換性](../../../odbc/reference/appendixes/block-cursors-scrollable-cursors-and-backward-compatibility.md)」を参照してください。  
  
## <a name="descriptors-and-sqlfetchscroll"></a>記述子と SQL フェッチスクロール  
 **SQLFetch と**同じ方法で記述子と**対話します。** 詳細については[、SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)の「記述子と SQL フェッチスクロール」セクションを参照してください。  
  
## <a name="code-example"></a>コード例  
 [SQLSetPos を使用して行セットの行を更新](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)する、[列方向のバインド](../../../odbc/reference/develop-app/column-wise-binding.md)、[行方向のバインド](../../../odbc/reference/develop-app/row-wise-binding.md)、[位置指定更新および削除ステートメント](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)、および行の更新 を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|一括挿入、更新、または削除操作の実行|[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|SQL ステートメントの実行|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|単一行またはデータブロックを順方向方向にフェッチする|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|ステートメントのカーソルをクローズする|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|結果セット列の数を返す|[SQLNumResultCols 関数](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
|カーソルの位置、行セット内のデータの更新、または結果セット内のデータの更新または削除|[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
|ステートメント属性の設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
