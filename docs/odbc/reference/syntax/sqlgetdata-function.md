---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetData
helpviewer_keywords:
- SQLGetData function [ODBC]
ms.assetid: e3c1356a-5db7-4186-85fd-8b74633317e8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ac11505b8e47dae8df53af27c64a7ee6372b3f28
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285508"
---
# <a name="sqlgetdata-function"></a>SQLGetData 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **結果**セット内の単一の列、または**SQLParamData**がSQL_PARAM_DATA_AVAILABLEを返した後の単一のパラメーターのデータを取得します。 これは、複数の時間を呼び出して、可変長データを部分的に取得できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLGetData(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   Col_or_Param_Num,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_IndPtr);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *Col_or_Param_Num*  
 [入力]列データを取得する場合は、データを返す列の番号です。 結果セット列は、1 から始まる列の昇順で番号付けされます。 ブックマーク列は列番号 0 です。ブックマークが有効になっている場合にのみ指定できます。  
  
 パラメータ データを取得する場合は、パラメータの序数が 1 から始まります。  
  
 *Targettype*  
 [入力]**ターゲット値Ptr*バッファーの C データ型の型識別子。 有効な C データ型と型識別子の一覧については、「付録 D:[データ型」の「C データ型](../../../odbc/reference/appendixes/c-data-types.md)」セクションを参照してください。  
  
 *TargetType*がSQL_ARD_TYPE場合、ドライバーは、ARD のSQL_DESC_CONCISE_TYPE フィールドで指定された型識別子を使用します。 *ターゲットの種類*がSQL_APD_TYPE場合 **、SQLGetData**は **、SQLBindParameter**で指定されたのと同じ C データ型を使用します。 それ以外の場合は **、SQLGetData**で指定された C データ型は **、SQLBindParameter**で指定された C データ型をオーバーライドします。 SQL_C_DEFAULT場合、ドライバーは、ソースの SQL データ型に基づいて既定の C データ型を選択します。  
  
 拡張 C データ型を指定することもできます。 詳細については[、「ODBC での C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)」を参照してください。  
  
 *ターゲット値Ptr*  
 [出力]データを返すバッファーへのポインター。  
  
 *ターゲット値Ptr*を NULL にすることはできません。  
  
 *BufferLength*  
 [入力]**ターゲット値Ptr*バッファの長さ (バイト単位)。  
  
 ドライバーは、文字やバイナリ データなどの可変長データを\*返すときに *、TargetValuePtr*バッファーの末尾を超えて書き込みを回避するのには *、BufferLength*を使用します。 ドライバーは、文字データを\**TargetValuePtr*に返すときに、null 終端文字をカウントすることに注意してください。 **したがって、TargetValuePtr*には null 終端文字用の領域が含まれている必要があります。  
  
 ドライバーは、整数や日付構造体などの固定長データを返す場合、ドライバーは無視*BufferLength、* バッファーは、データを保持するのに十分な大きさであると仮定します。 したがって、アプリケーションが固定長データに十分な大きさのバッファーを割り当てることが重要であるか、ドライバーがバッファーの末尾を過ぎて書き込みます。  
  
 **SQLGetData は***、バッファー長*が 0 未満の場合に SQLSTATE HY090 (無効な文字列またはバッファー長) を返しますが、*バッファー長*が 0 の場合は返しません。  
  
 *StrLen_or_IndPtr*  
 [出力]長さまたは標識値を戻すバッファーへのポインター。 これがヌル・ポインターの場合、長さも標識値も戻されません。 これは、フェッチされるデータが NULL の場合にエラーを返します。  
  
 **SQLGetData は**、長さ/インジケーター バッファーに次の値を返すことができます。  
  
-   返されるデータの長さ  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 詳細については、このトピックの[「長さ/インジケーター値の使用](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)」および「コメント」を参照してください。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetData が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLGetData**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|指定した列*Col_or_Param_Num*のデータの一部を、関数の 1 回の呼び出しで取得できませんでした。 **SQL_NO_TOTAL、または現在の SQLGetData**呼び出しの前に指定した列に残っているデータ\*の長さが*StrLen_or_IndPtr*で返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。<br /><br /> 1 つの列に対して**SQLGetData**への複数の呼び出しを使用する方法の詳細については、「コメント」を参照してください。|  
|01S07|分数切り捨て|1 つ以上の列に対して返されたデータが切り捨てられました。 数値データ型の場合、数値の小数部分は切り捨てられました。 時間、タイム・スタンプ、および時間コンポーネントを含む間隔データ・タイプの場合、時間の小数部分は切り捨てられました。<br /><br /> (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07006|制限付きデータ型属性違反|結果セット内の列のデータ値を引数*TargetType*で指定された C データ型に変換することはできません。|  
|07009|記述子インデックスが無効です|引数*Col_or_Param_Num*に指定された値は 0 で、SQL_ATTR_USE_BOOKMARKSステートメント属性はSQL_UB_OFFに設定されています。<br /><br /> 引数*Col_or_Param_Num*に指定された値が、結果セット内の列数より大きかった。<br /><br /> *Col_or_Param_Num*値が、使用可能なパラメーターの序数と等しくありません。<br /><br /> (DM) 指定された列がバインドされました。 この説明は、 **SQLGetInfo**の SQL_GETDATA_EXTENSIONS オプションのSQL_GD_BOUND ビットマスクを返すドライバーには適用されません。<br /><br /> (DM) 指定された列の数が、最大バインド列の数以下でした。 この説明は、 **SQLGetInfo**の SQL_GETDATA_EXTENSIONS オプションのSQL_GD_ANY_COLUMN ビットマスクを返すドライバーには適用されません。<br /><br /> (DM) アプリケーションは、現在の行に対して**SQLGetData**を既に呼び出しています。現在の呼び出しで指定された列の数が、直前の呼び出しで指定された列の数より少なかった。ドライバは**SQLGetInfo**のSQL_GETDATA_EXTENSIONS オプションのSQL_GD_ANY_ORDER ビットマスクを返しません。<br /><br /> (DM)*引数 TargetType*がSQL_ARD_TYPEされ、ARD 内の*Col_or_Param_Num*記述子レコードが整合性チェックに失敗しました。<br /><br /> (DM)*引数 TargetType*がSQL_ARD_TYPEされ、ARD のSQL_DESC_COUNT フィールドの値が*Col_or_Param_Num*引数より小さかった。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|22002|インジケーター変数が必要ですが、指定されていません|*StrLen_or_IndPtr*は NULL ポインタであり、NULL データが取得されました。|  
|22003|範囲外の数値|列の数値 (数値または文字列) を返すと、数値の整数部分 (小数部ではなく) が切り捨てられます。<br /><br /> 詳細については、「[付録 D : データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)」を参照してください。|  
|22007|日付/時刻形式が無効です|結果セット内の文字列が C の日付、時刻、またはタイム・スタンプ構造にバインドされ、列の値がそれぞれ無効な日付、時刻、またはタイム・スタンプであった。 詳細については、「[付録 D : データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)」を参照してください。|  
|22012|ゼロ除算|0 で除算された算術式の値が返されました。|  
|22015|間隔フィールドのオーバーフロー|正確な数値または間隔の SQL タイプから間隔 C タイプに割り当てると、先行フィールドの有効桁数が失われます。<br /><br /> データをインターバル C タイプに戻す場合、間隔 C 型の SQL 型の値は表現されません。|  
|22018|キャスト指定に無効な文字値|結果セットの文字列が文字 C バッファーに戻され、その列にバッファーの文字セットに表現がない文字が含まれていました。<br /><br /> C 型は、正確な数値または概数、日時、または間隔のデータ型でした。列の SQL 型は文字データ型でした。列の値が、バインドされた C 型の有効なリテラルではありません。|  
|24000|カーソル状態が無効|(DM) 関数は、必要なデータの行にカーソルを配置するために、最初に**SQLFetch**または**SQLFetchScroll**を呼び出さずに呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*は実行済み状態でしたが、結果セットはステートメント ハンドルに関連付*けられません*。<br /><br /> *ステートメント ハンドル*でカーソルが開いていて、SQLFetch または**SQLFetchScroll**が呼び出されましたが、カーソルは結果セットの開始前または結果セットの終了後に位置付けされていました。 **SQLFetchScroll**|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 *メッセージ テキスト*バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY003|プログラムの種類が範囲外です|(DM)*引数 TargetType*は有効なデータ型、SQL_C_DEFAULT、SQL_ARD_TYPE (列データを取得する場合)、またはSQL_APD_TYPE (パラメーター データを取得する場合) ではありませんでした。<br /><br /> (DM) 引数*Col_or_Param_Num*が 0 であり、引数*TargetType*が固定長ブックマークに対してSQL_C_BOOKMARKまたは可変長ブックマークのSQL_C_VARBOOKMARKされていません。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、ステートメント ハンドルで**SQLCancel**または**SQLCancelHandle**が呼び出された後、*ステートメント ハンドル*で関数が再度呼び出されました。 *StatementHandle*<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出された後、*ステートメント ハンドル*で関数が再度呼び出されました。|  
|HY009|無効な null ポインターの使用|(DM) 引数*TargetValuePtr*は null ポインターでした。|  
|HY010|関数シーケンス エラー|(DM) 指定された*ステートメント ハンドル*が実行状態にありません。 関数は、最初に呼び出**さずに****呼**び出されました。<br /><br /> (DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLGetData**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*は実行済み状態でしたが、結果セットはステートメント ハンドルに関連付*けられません*。<br /><br /> **SQLExeceute** **、SQLExecDirect**、または**SQLMoreResults**への呼び出しはSQL_PARAM_DATA_AVAILABLE返されましたが **、SQLGetData**が**呼**び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*BufferLength*に指定された値が 0 より小さかった。<br /><br /> 引数*BufferLength*に指定された値が 4 未満 *、Col_or_Param_Num*引数が 0 に設定され、ドライバーが ODBC 2 *.x*ドライバーでした。|  
|HY109|カーソル位置が無効です|カーソルが、削除された行またはフェッチできなかった行に **(SQLSetPos** **、SQLFetch** **、SQLFetchScroll**、または**SQLBulkOperations**によって) 配置されました。<br /><br /> カーソルが前方専用カーソルで、行セットのサイズが 1 より大きかった。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|ドライバーまたはデータ ソースは **、SQLFetchScroll**で複数の行で**SQLGetData**の使用をサポートしていません。 この説明は、 **SQLGetInfo**の SQL_GETDATA_EXTENSIONS オプションのSQL_GD_BLOCK ビットマスクを返すドライバーには適用されません。<br /><br /> ドライバーまたはデータ ソースは、*引数の*引数と対応する列の SQL データ型の組み合わせで指定された変換をサポートしていません。 このエラーは、列の SQL データ型がドライバー固有の SQL データ型にマップされている場合にのみ適用されます。<br /><br /> ドライバーは ODBC 2 *.x*のみをサポートし、引数*TargetType*は次のいずれかでした。<br /><br /> SQL_C_SBIGINTSQL_C_UBIGINTSQL_C_NUMERIC<br /><br /> 「付録 D: データ型」の[C データ型](../../../odbc/reference/appendixes/c-data-types.md)にリストされている間隔 C データ型。<br /><br /> ドライバーは、3.50 より前の ODBC バージョンのみをサポートし、引数*TargetType*がSQL_C_GUIDされました。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に対応するドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 **指定**した列のデータを返します。 **SQLGetData を**呼び出すことができるのは **、SQLFetch** **、SQLFetchScroll、** または**SQLExtendedFetch**によって結果セットから 1 つ以上の行がフェッチされた後だけです。 可変長データが**SQLGetData**への 1 回の呼び出しで返すには大きすぎる場合 (アプリケーションの制限により) **SQLGetData**は、それを部分的に取得できます。 行の一部の列をバインドし、他の列に対して**SQLGetData**を呼び出す場合もありますが、これにはいくつかの制限が適用されます。 詳細については、「[長いデータの取得](../../../odbc/reference/develop-app/getting-long-data.md)」を参照してください。  
  
 ストリーミング出力パラメーターで**の SQLGetData**の使用については、「 [SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)」を参照してください。  
  
## <a name="using-sqlgetdata"></a>SQL データの使用  
 ドライバーが**SQLGetData**の拡張機能をサポートしていない場合、関数は、最後にバインドされた列の数値よりも大きい数値を持つ非バインド列のデータのみを返すことができます。 さらに、データ行内では **、SQLGetData**の各呼び出しにおける*Col_or_Param_Num*引数の値は、前の呼び出しの*Col_or_Param_Num*の値以上でなければなりません。つまり、データは列番号の増加順で取得する必要があります。 最後に、拡張がサポートされていない場合、行セットのサイズが 1 より大きい場合は**SQLGetData**を呼び出すことができません。  
  
 ドライバーは、これらの制限のいずれかを緩和することができます。 ドライバーが緩和する制限を決定するには、アプリケーションは、次のSQL_GETDATA_EXTENSIONS オプションのいずれかを使用して**SQLGetInfo**を呼び出します。  
  
-   SQL_GD_OUTPUT_PARAMS = **SQLGetData**を呼び出して、出力パラメーター値を返すことができます。 詳細については、「 [SQLGetData を使用した出力パラメータの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)」を参照してください。  
  
-   SQL_GD_ANY_COLUMN。 このオプションが返された場合、最後にバインドされた列の前の列を含め、バインドされていない列に対して**SQLGetData**を呼び出すことができます。  
  
-   SQL_GD_ANY_ORDER。 このオプションが返された場合、任意の順序で非バインド列に対して**SQLGetData**を呼び出すことができます。  
  
-   SQL_GD_BLOCK。 このオプションが SQL_GETDATA_EXTENSIONS InfoType の**SQLGetInfo**によって返される場合、ドライバーは、行セットのサイズが 1 より大きい場合に**SQLGetData**の呼び出しをサポートし、アプリケーションは **、SQLGetData**を呼び出す前に正しい行にカーソルを配置するオプションSQL_POSITIONを使用して**SQLSetPos**を呼び出すことができます。  
  
-   SQL_GD_BOUND。 このオプションが返された場合、バインドされていない列だけでなく、バインドされた列に対しても**SQLGetData**を呼び出すことができます。  
  
 これらの制限には 2 つの例外があり、ドライバーはこれらを緩和できます。 まず、行セットのサイズが 1 より大きい場合 **、SQLGetData**を前方専用カーソルに対して呼び出す必要があります。 次に、ドライバーがブックマークをサポートしている場合は、アプリケーションが最後にバインドされた列の前に他の列の**SQLGetData**を呼び出すことを許可しない場合でも、列 0 の**SQLGetData**を呼び出す機能を常にサポートする必要があります。 (アプリケーションが ODBC *fOption* 2 *.x*ドライバーを使用している場合、SQL SQL_GET_BOOKMARK *.x* *Col_or_Param_Num* *.x* **SQLGetStmtOption** **SQLGetData** *FetchOrientation* **SQL_FETCH_NEXTGetData**は**SQLExtendedFetch****、SQLFetch**の呼び出し後**SQLFetch**に*Col_or_Param_Num* 0 と呼び出されるとブックマークを正常に返します。  
  
 カーソルが行に配置されていないため **、sqlBulkOperations**を SQL_ADD呼び出して挿入した行のブックマークを取得するには **、SQLGetData**を使用できません。 アプリケーションは、SQL_ADDを指定して**SQLBulkOperations**を呼び出す前に列 0 をバインド**SQLBulkOperations**することによって、このような行のブックマークを取得できます。 その後、SQL_FETCH_BOOKMARKを指定して**SQLFetchScroll**を呼び出して、その行にカーソルを再配置できます。  
  
 引数*TargetType*が間隔データ型の場合、ARD のSQL_DESC_DATETIME_INTERVAL_PRECISIONフィールドとSQL_DESC_PRECISIONフィールドで設定されているデフォルトの間隔先行精度 (2) とデフォルトの間隔秒精度 (6) がデータにそれぞれ使用されます。 引数*TargetType*がSQL_C_NUMERICデータ型の場合、ARD のSQL_DESC_PRECISIONフィールドおよびSQL_DESC_SCALEフィールドで設定されている既定の精度 (ドライバー定義) と既定のスケール (0) がデータに使用されます。 デフォルトの精度または位取りが適切でない場合、アプリケーションは**SQLSetDescField**または**SQLSetDescRec**の呼び出しによって適切な記述子フィールドを明示的に設定する必要があります。 SQL_DESC_CONCISE_TYPEフィールドをSQL_C_NUMERICに設定し、SQL_ARD_TYPEの*TargetType*引数を指定して**SQLGetData**を呼び出すと、記述子フィールドの精度とスケールの値が使用されます。  
  
> [!NOTE]
>  ODBC 2 *.x*では、アプリケーション*は TargetType*を SQL_C_DATE、SQL_C_TIME、またはSQL_C_TIMESTAMPに設定して\**、TargetValuePtr*が日付、時刻、またはタイムスタンプの構造体であることを示します。 ODBC 3 *.x*では、アプリケーション*は TargetType*をSQL_C_TYPE_DATE、SQL_C_TYPE_TIME、またはSQL_C_TYPE_TIMESTAMPに設定します。 ドライバー マネージャーは、アプリケーションとドライバーのバージョンに基づいて、必要に応じて適切なマッピングを行います。  
  
## <a name="retrieving-variable-length-data-in-parts"></a>部品内の可変長データの取得  
 **SQLGetData**を使用すると、列の SQL データ型の識別子がSQL_CHAR、SQL_VARCHAR、SQL_LONGVARCHAR、SQL_WCHAR、SQL_WVARCHAR、SQL_WLONGVARCHAR、SQL_BINARY、SQL_VARBINARY、SQL_LONGVARBINARY、または可変長型のドライバー固有の識別子が含まれる列からデータを取得できます。  
  
 列からデータを取得するには、アプリケーションは同じ列に対して**SQLGetData**を複数回連続して呼び出します。 呼び出しごとに、**データ**の次の部分が返されます。 部品を再構成するのはアプリケーション次第であり、文字データの中間部分から NULL 終端文字を削除するように注意してください。 戻すデータが多い場合、または終了文字に十分なバッファーが割り振られていない場合 **、SQLGetData**は SQL_SUCCESS_WITH_INFOおよび SQLSTATE 01004 (データの切り捨て) を戻します。 データの最後の部分を返すと **、SQLGetData は**SQL_SUCCESSを返します。 アプリケーションは、アプリケーション バッファー内のデータの量が有効であるかを知る手段を持たないため、列からデータを取得する最後の有効な呼び出しでSQL_NO_TOTALもゼロも返されません。 この後**に SQLGetData**が呼び出された場合、SQL_NO_DATA返します。 詳細については、次のセクション「SQLGetData を使用したデータの取得」を参照してください。  
  
 可変長ブックマークは、 **SQLGetData**によって一部に返される可能性があります。 他のデータと同様に、可変長のブックマークを一部で返す**SQLGetData**の呼び出しは、SQLSTATE 01004 (文字列データ、右切り捨て) を返し、返されるデータが増えたときにSQL_SUCCESS_WITH_INFO返します。 これは、sqlFetch または**SQLFetchScroll**の呼び出しによって可変長ブックマークが切**SQLFetchScroll**り捨てられる場合とは異なり、SQL_ERRORと SQLSTATE 22001 (文字列データ、右切り捨て) を返します。  
  
 **SQLGetData を**使用して、固定長データを部分で返すことはできません。 固定長データを含む列に対して**SQLGetData**が 1 行に複数回呼び出された場合、最初の呼び出しの後のすべての呼び出しに対して SQL_NO_DATA が返されます。  
  
## <a name="retrieving-streamed-output-parameters"></a>ストリーミング出力パラメーターの取得  
 ドライバーは、ストリーミング出力パラメーターをサポートしている場合、アプリケーションは、大きなパラメーター値を取得する場合は、小さなバッファーを使用して**SQLGetData**を何度も呼び出すことができます。 ストリーム出力パラメーターの詳細については、「 [SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)」を参照してください。  
  
## <a name="retrieving-data-with-sqlgetdata"></a>SQLGetData を使用したデータの取得  
 指定した列のデータを返すために **、SQLGetData**は次の手順のシーケンスを実行します。  
  
1.  列のすべてのデータが既に返されている場合は、SQL_NO_DATAを返します。  
  
2.  データ\**が*NULL の場合にSQL_NULL_DATAStrLen_or_IndPtrを設定します。 データが NULL で *、StrLen_or_IndPtr*が NULL ポインターであった場合 **、SQLGetData**は SQLSTATE 22002 (標識変数が必要ですが、指定されていない) を戻します。  
  
     列のデータが NULL でない場合 **、SQLGetData**は手順 3 に進みます。  
  
3.  SQL_ATTR_MAX_LENGTH ステートメント属性が 0 以外の値に設定されている場合、列に文字またはバイナリ データが含まれている場合、および**SQLGetData**が以前に列に対して呼び出されていない場合、データは SQL_ATTR_MAX_LENGTH バイトに切り捨てられます。  
  
    > [!NOTE]  
    >  SQL_ATTR_MAX_LENGTHステートメント属性は、ネットワーク・トラフィックを削減することを目的としています。 通常はデータ ソースによって実装され、データはネットワーク経由で返される前に切り捨てられます。 ドライバーとデータ ソースは、それをサポートする必要はありません。 したがって、データが特定のサイズに切り捨てられることを保証するために、アプリケーションはそのサイズのバッファーを割り当て *、BufferLength*引数にサイズを指定する必要があります。  
  
4.  データを*TargetType*で指定された型に変換します。 データには、そのデータ型の既定の精度と小数点以下桁数が指定されます。 *TargetType*がSQL_ARD_TYPE場合、ARD のSQL_DESC_CONCISE_TYPE フィールドのデータ型が使用されます。 *TargetType*がSQL_ARD_TYPE場合、データには、SQL_DESC_CONCISE_TYPE フィールドのデータ型に応じて、ARD のSQL_DESC_DATETIME_INTERVAL_PRECISION、SQL_DESC_PRECISION、およびSQL_DESC_SCALEフィールドの精度と桁数が指定されます。 デフォルトの精度または位取りが適切でない場合、アプリケーションは**SQLSetDescField**または**SQLSetDescRec**の呼び出しによって適切な記述子フィールドを明示的に設定する必要があります。  
  
5.  データが文字やバイナリなどの可変長データ型に変換された場合 **、SQLGetData**はデータの長さが*BufferLength*を超えているかどうかをチェックします。 文字データの長さ (NULL 終了文字を含む) が*BufferLength*を超えた場合 **、SQLGetData**はデータを*BufferLength*に切り捨て、NULL 終端文字の長さを減らします。 その後、データを null 終了します。 バイナリ データの長さがデータ バッファーの長さを超える場合 **、SQLGetData**は *、バッファー長*のバイトに切り捨てます。  
  
     指定されたデータ・バッファーが小さすぎてヌル終了文字を保持できなければ **、SQLGetData**は SQL_SUCCESS_WITH_INFO および SQLSTATE 01004 を戻します。  
  
     **SQLGetData は**、固定長データ型に変換されたデータを切り捨てることはありません。常に **TargetValuePtr*の長さはデータ型のサイズであると想定します。  
  
6.  変換された (場合によっては切り捨てられた)\*データを*TargetValuePtr*に配置します。 **SQLGetData は**、行外のデータを返すことができないことに注意してください。  
  
7.  データの長さを\**StrLen_or_IndPtr*に配置します。 *StrLen_or_IndPtr*が null ポインターであった場合 **、SQLGetData**は長さを返しません。  
  
    -   文字データまたはバイナリ データの場合、これは変換後と BufferLength による切り捨て前のデータの長*さです*。 ドライバーは、変換後にデータの長さを決定できない場合は、長いデータの場合もある場合は、SQL_SUCCESS_WITH_INFOを返し、SQL_NO_TOTALに長さを設定します。 **(SQLGetData**の最後の呼び出しは、常に、ゼロまたはSQL_NO_TOTALではなく、データの長さを返す必要があります。SQL_ATTR_MAX_LENGTH ステートメント属性によってデータが切り捨てられた場合、この属性の値は、実際の長さとは対照的に\**StrLen_or_IndPtr*に入れられます。 これは、この属性は変換前にサーバー上のデータを切り捨てるように設計されているため、ドライバーは実際の長さを把握する方法がありません。 **SQLGetData**が同じ列に対して連続して複数回呼び出される場合、これは現在の呼び出しの開始時に使用可能なデータの長さです。つまり、その後の呼び出しごとに長さが減少します。  
  
    -   その他のすべてのデータ型では、変換後のデータの長さになります。つまり、データの変換先の型のサイズです。  
  
8.  変換中にデータが重要度を失うことなく切り捨てられる場合 (例えば、整数 1 に変換すると実数 1.234 が切り捨てられる)、または*BufferLength*が小さすぎる (例えば、文字列 "abcdef" が 4 バイトのバッファーに入れられる) 場合 **、SQLGetData**は SQLSTATE 01004 (データ切り捨て) を返し、SQL_SUCCESS_WITH_INFO。 SQL_ATTR_MAX_LENGTHステートメント属性により、データが有意性を失わずに切り捨てられる場合 **、SQLGetData**はSQL_SUCCESSを戻し、SQLSTATE 01004 (データ切り捨て) を戻しません。  
  
 バインドされたデータ バッファーの内容 (バインドされた列で**SQLGetData**が呼び出された場合) と **、SQLGetData**がSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返さない場合、長さ/インジケーター バッファーが定義されていません。  
  
 **SQLGetData**の連続呼び出しは、最後に要求された列からデータを取得します。以前のオフセットは無効になります。 たとえば、次のシーケンスが実行される場合は、次のようになります。  
  
```cpp  
SQLGetData(icol=n), SQLGetData(icol=m), SQLGetData(icol=n)  
```  
  
 2 回目の呼び出しでは、sqlGetData(icol=n) は、n 列の先頭からデータを取得します。 列に対する**SQLGetData**の以前の呼び出しによるデータ内のオフセットは、無効になります。  
  
## <a name="descriptors-and-sqlgetdata"></a>記述子と SQLGet データ  
 **SQLGetData**は、記述子フィールドと直接対話しません。  
  
 *TargetType*がSQL_ARD_TYPE場合、ARD のSQL_DESC_CONCISE_TYPE フィールドのデータ型が使用されます。 *TargetType*がSQL_ARD_TYPEまたはSQL_C_DEFAULTの場合、SQL_DESC_CONCISE_TYPE フィールドのデータ型に応じて、データには ARD のSQL_DESC_DATETIME_INTERVAL_PRECISION、SQL_DESC_PRECISION、およびSQL_DESC_SCALEフィールドの精度とスケールが指定されます。  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションが**SELECT ステートメント**を実行して、名前、ID、電話番号で並べ替えられた顧客 ID、名前、電話番号の結果セットを返します。 データの各行に対して **、SQLFetch**を呼び出してカーソルを次の行に配置します。 フェッチされたデータを取得するために**SQLGetData**を呼び出します。データのバッファーと返されるバイト数は **、 SQLGetData**の呼び出しで指定されます。 最後に、各従業員の名前、ID、および電話番号を出力します。  
  
```cpp  
#define NAME_LEN 50  
#define PHONE_LEN 50  
  
SQLCHAR      szName[NAME_LEN], szPhone[PHONE_LEN];  
SQLINTEGER   sCustID, cbName, cbAge, cbBirthday;  
SQLRETURN    retcode;  
SQLHSTMT     hstmt;  
  
retcode = SQLExecDirect(hstmt,  
   "SELECT CUSTID, NAME, PHONE FROM CUSTOMERS ORDER BY 2, 1, 3",  
   SQL_NTS);  
  
if (retcode == SQL_SUCCESS) {  
   while (TRUE) {  
      retcode = SQLFetch(hstmt);  
      if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO) {  
         show_error();  
      }  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO){  
  
         /* Get data for columns 1, 2, and 3 */  
  
         SQLGetData(hstmt, 1, SQL_C_ULONG, &sCustID, 0, &cbCustID);  
         SQLGetData(hstmt, 2, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
         SQLGetData(hstmt, 3, SQL_C_CHAR, szPhone, PHONE_LEN,  
            &cbPhone);  
  
         /* Print the row of data */  
  
         fprintf(out, "%-5d %-*s %*s", sCustID, NAME_LEN-1, szName,   
            PHONE_LEN-1, szPhone);  
      } else {  
         break;  
      }  
   }  
}  
```  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列のストレージの割り当て|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ブロック カーソル位置に関連しない一括操作の実行|[オペレーション](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|SQL ステートメントの実行|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|単一行のデータまたはデータブロックを順方向方向にフェッチする|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|実行時にパラメータデータを送信する|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|カーソルの位置、行セット内のデータの更新、または行セット内のデータの更新または削除|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
