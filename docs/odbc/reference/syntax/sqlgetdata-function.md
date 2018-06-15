---
title: SQLGetData 関数 |Microsoft ドキュメント
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
- SQLGetData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetData
helpviewer_keywords:
- SQLGetData function [ODBC]
ms.assetid: e3c1356a-5db7-4186-85fd-8b74633317e8
caps.latest.revision: 46
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ab603b24536afcbe7304dae907c10ee911d3cfd9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32923707"
---
# <a name="sqlgetdata-function"></a>SQLGetData 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLGetData**結果セット内の 1 つの列のまたは後に 1 つのパラメーターのデータの取得**SQLParamData** SQL_PARAM_DATA_AVAILABLE を返します。 できます複数回呼び出す部分の可変長データを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLGetData(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   Col_or_Param_Num,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_IndPtr);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *Col_or_Param_Num*  
 [入力]列のデータを取得するために、データを返す対象の列数です。 結果セットの列は、列の昇順に 1 から始まる番号が付けられます。 ブックマーク列は、列番号 0;これは、ブックマークが有効になっているかどうかにのみ指定します。  
  
 パラメーターのデータを取得するには、1 から開始されると、パラメーターの序数です。  
  
 *TargetType*  
 [入力]C データ型の型の識別子、**TargetValuePtr*バッファー。 有効な C データ型と型識別子の一覧は、次を参照してください。、 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)付録 d: データ型」セクション。  
  
 場合*TargetType* SQL_ARD_TYPE、型識別子が、ARD の SQL_DESC_CONCISE_TYPE フィールドで指定したドライバーの使用がします。 場合*TargetType*は SQL_APD_TYPE、 **SQLGetData**で指定されている同じ C データ型を使用して、 **SQLBindParameter**です。 C データ型がでどのように指定する場合は、 **SQLGetData**で指定された C データ型をオーバーライド**SQLBindParameter**です。 SQL_C_DEFAULT である場合、ドライバーは、SQL データ型に基づいて、ソースの既定の C データ型を選択します。  
  
 拡張の C データ型を指定することもできます。 詳細については、次を参照してください。 [ODBC における C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)です。  
  
 *TargetValuePtr*  
 [出力]データを返すバッファーへのポインター。  
  
 *TargetValuePtr* NULL にすることはできません。  
  
 *BufferLength*  
 [入力]長さ、**TargetValuePtr*バッファーのバイト単位です。  
  
 ドライバーを使用して*BufferLength*の末尾を越えた書き込まれないように、 \* *TargetValuePtr*文字またはバイナリ データなどの可変長データを返すときにバッファーに格納します。 文字データを返すときに、ドライバーが、null 終端文字をカウントことに注意してください\* *TargetValuePtr*です。 **TargetValuePtr* null 終端文字用の領域を含める必要がありますので、ドライバーはデータの切り捨てまたはします。  
  
 ドライバーには、整数や日付構造体などの固定長データが返されるときに、ドライバーを無視*BufferLength*バッファーがデータを保持するのに十分な大きさを前提としています。 そのため固定長のデータを十分な大きさのバッファーを割り当て、アプリケーションにとって重要やドライバーは、バッファーの末尾を越えた記述です。  
  
 **SQLGetData** SQLSTATE HY090 が返されます (無効な文字列長またはバッファー長) と*BufferLength*が 0 未満の値が時ではなく*BufferLength*は 0 です。  
  
 *StrLen_or_IndPtr*  
 [出力]長さまたはインジケーターの値を返すバッファーへのポインター。 これが null ポインターである場合は、長さまたはインジケーターの値は返されません。 フェッチされるデータが NULL の場合、エラーが返されます。  
  
 **SQLGetData**長さ/インジケーター バッファーで、次の値を返すことができます。  
  
-   返される使用可能なデータの長さ  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 詳細については、次を参照してください。[長さ/インジケーターの値を使用する](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)とこのトピックでは、"コメント"です。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetData** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる**SQLGetDiagRec**で、 *HandleType*のSQL_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLGetData**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|すべての指定した列のデータ*Col_or_Param_Num*関数に 1 つの呼び出しで取得できませんでした。 SQL_NO_TOTAL を現在の呼び出しの前に指定された列の残りのデータの長さまたは**SQLGetData**で返される\* *StrLen_or_IndPtr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。<br /><br /> 複数の呼び出しを使用する方法についての**SQLGetData**列を 1 つは「コメント」を参照してください。|  
|01S07|小数部の切り捨て|1 つまたは複数の列に対して返されるデータが切り捨てられました。 数値データ型の数値の小数部が切り捨てられました。 時刻、タイムスタンプ、および時刻部分を含む interval データ型の場合は、時間の小数部が切り捨てられました。<br /><br /> (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|結果セット内の列のデータ値は、引数で指定された C データ型に変換できない*TargetType*です。|  
|07009|無効な記述子のインデックス|引数が指定された値*Col_or_Param_Num*が 0 の場合、SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_OFF に設定します。<br /><br /> 引数が指定された値*Col_or_Param_Num*が結果セット内の列の数を超えています。<br /><br /> *Col_or_Param_Num*値が使用可能なパラメーターの序数と同じではありませんでした。<br /><br /> (DM) 指定した列がバインドされました。 この説明は、ドライバーの SQL_GETDATA_EXTENSIONS オプションの SQL_GD_BOUND ビットマスクを返すには適用されません**SQLGetInfo**です。<br /><br /> (DM) 指定された列の数が、最高の連結された列の数以下がします。 この説明は、ドライバーの SQL_GETDATA_EXTENSIONS オプションの SQL_GD_ANY_COLUMN ビットマスクを返すには適用されません**SQLGetInfo**です。<br /><br /> (DM) アプリケーションは既に呼び出さ**SQLGetData** ; 現在の行の現在の呼び出しで指定された列の数が少なくなっていました; 上の呼び出しで指定された列の数よりもと、ドライバーには、sql _ は返しません。SQL_GETDATA_EXTENSIONS オプションのビットマスクを GD_ANY_ORDER **SQLGetInfo**です。<br /><br /> (DM)、 *TargetType*引数が SQL_ARD_TYPE、および*Col_or_Param_Num*記述子レコード、ARD で整合性チェックに失敗しました。<br /><br /> (DM)、 *TargetType*引数 SQL_ARD_TYPE であり、ARD の SQL_DESC_COUNT フィールドの値より小さい*Col_or_Param_Num*引数。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|22002|インジケーター変数が必要ですが、指定されていません|*StrLen_or_IndPtr*が null ポインターでしたおよび NULL データを取得します。|  
|22003|数値が範囲|(数値または文字列) として列の数値の値を取得する原因となる (ではなく小数部) 整数部分が切り捨てられる数値。<br /><br /> 詳細については、次を参照してください。[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)です。|  
|22007|無効な datetime 形式|結果セットで文字列 C 日付、時刻、またはタイムスタンプの構造体にバインドされましたし、列の値が無効な日付、時刻、またはタイムスタンプ、それぞれします。 詳細については、次を参照してください。[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)です。|  
|22012|0 による除算です。|0 による除算が発生する算術式の値が返されました。|  
|22015|間隔のフィールドがオーバーフローしました|真数型または interval SQL 型から C の間隔の種類を割り当てると、先頭のフィールドに有効桁数の損失が発生します。<br /><br /> 間隔 C 型にデータを返すときに、間隔 C 型の SQL の型の値の表現はありませんでした。|  
|22018|キャストは無効な文字値|C 文字バッファーに返された結果セット内の文字の列と列には、バッファーの文字セットの表現が発生しましたない文字が含まれています。<br /><br /> C 型が、真数または概数の数値、datetime、または、interval データ型です。列の SQL 型が文字データ型です。列の値がバインドされた C 型の有効なリテラルではありませんでした。|  
|24000|カーソル状態が無効|(DM)、関数が呼び出された最初呼び出さず**SQLFetch**または**SQLFetchScroll**に必要なデータの行にカーソルを移動します。<br /><br /> (DM)、 *StatementHandle*が実行された状態でしたが、結果セットが関連付けられていない、 *StatementHandle*です。<br /><br /> カーソルが開いて、 *StatementHandle*と**SQLFetch**または**SQLFetchScroll**が呼び出された、または後に結果セットの開始前に、カーソルが配置されたが、結果セットの終わりです。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、 *MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY003|範囲外のプログラムの種類|(DM) 引数*TargetType*有効なデータ型、SQL_C_DEFAULT、SQL_ARD_TYPE (列のデータを取得する) の場合または (が発生した場合のパラメーターのデータの取得) SQL_APD_TYPE ありませんでした。<br /><br /> (DM) 引数*Col_or_Param_Num* 0 であり、引数が*TargetType*でした SQL_C_BOOKMARK 固定長ブックマークまたは SQL_C_VARBOOKMARK の可変長ブックマーク。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*関数が呼び出されたし、再度、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションは、し、関数で呼び出されましたもう一度、 *StatementHandle*です。|  
|HY009|無効な null ポインターの使用|(DM) 引数*TargetValuePtr*が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM)、指定した*StatementHandle*実行された状態ではありませんでした。 最初の呼び出さずに、関数が呼び出された**SQLExecDirect**、 **SQLExecute**またはカタログ関数。<br /><br /> (DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLGetData**関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM)、 *StatementHandle*が実行された状態でしたが、結果セットが関連付けられていない、 *StatementHandle*です。<br /><br /> 呼び出し**SQLExeceute**、 **SQLExecDirect**、または**SQLMoreResults** SQL_PARAM_DATA_AVAILABLE が返されますが、 **SQLGetData**が呼び出されました、の代わりに**SQLParamData**です。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|引数の指定された値 (DM) *BufferLength*が 0 未満です。<br /><br /> 引数に指定された値*BufferLength* 4 より小さいをでした、 *Col_or_Param_Num*引数が 0 に設定して、ドライバーは ODBC 2 *.x*ドライバー。|  
|HY109|無効なカーソルの位置|カーソルの位置 (によって**SQLSetPos**、 **SQLFetch**、 **SQLFetchScroll**、または**SQLBulkOperations**) が削除された行にまたは、取得できませんでした。<br /><br /> カーソルが、順方向専用カーソルと行セットのサイズが 1 よりも大きいです。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースは、の使用をサポートしていない**SQLGetData**で複数の行で**SQLFetchScroll**です。 この説明は、ドライバーの SQL_GETDATA_EXTENSIONS オプションの SQL_GD_BLOCK ビットマスクを返すには適用されません**SQLGetInfo**です。<br /><br /> ドライバーまたはデータ ソースがの組み合わせで指定された変換をサポートしていない、 *TargetType*引数と対応する列の SQL データ型。 このエラーは、列の SQL データ型は、ドライバー固有の SQL データ型にマップされた場合にのみ適用されます。<br /><br /> ドライバーは、ODBC 2 のみをサポートしている *.x*、およびその引数*TargetType*次のいずれかの。<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> interval C データ型の一覧に示されたのと[C データ型](../../../odbc/reference/appendixes/c-data-types.md)付録 d: データ型にします。<br /><br /> ドライバーのみがサポート 3.50、および引数の前に ODBC バージョン*TargetType* SQL_C_GUID がします。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に対応するドライバー、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 **SQLGetData**指定された列のデータを返します。 **SQLGetData**ごとに結果セットから 1 つまたは複数の行がフェッチされた後にのみ呼び出すことができる**SQLFetch**、 **SQLFetchScroll**、または**SQLExtendedFetch**です。 可変長のデータが大きすぎるため、1 回の呼び出しで返される場合**SQLGetData** (制限のため、アプリケーションで)、 **SQLGetData**部分で取得できます。 行と呼び出しで一部の列をバインドすることは**SQLGetData**他のユーザーが、これは、いくつかの制限の対象とします。 詳細については、次を参照してください。[長い形式のデータを取得する](../../../odbc/reference/develop-app/getting-long-data.md)です。  
  
 使用方法について**SQLGetData**ストリーミングされる出力パラメーターを使用して、次を参照してください。 [SQLGetData を使用して出力パラメーターを取得する](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)です。  
  
## <a name="using-sqlgetdata"></a>SQLGetData を使用してください。  
 ドライバーは拡張機能をサポートしていない場合**SQLGetData**、関数が返すデータを数値にバインドされていない列に対してのみ、最後のバインドされた列の場合よりも大きいです。 さらに、行内のデータの値、 *Col_or_Param_Num*への各呼び出しで引数**SQLGetData**の値以上にする必要があります*Col_or_Param_Num*; 前の呼び出しでつまり、列番号の昇順にデータを取得する必要があります。 最後に拡張機能がサポートされていない場合は、 **SQLGetData**行セットのサイズが 1 より大きい場合に呼び出されることはできません。  
  
 ドライバーは、これらの制限の緩和にされています。 アプリケーションを呼び出してドライバーの制限を緩和どのような制限を確認するのに**SQLGetInfo** SQL_GETDATA_EXTENSIONS の次のオプションのいずれかとします。  
  
-   SQL_GD_OUTPUT_PARAMS = **SQLGetData**出力パラメーターの値を返すを呼び出すことができます。 詳細については、次を参照してください。 [SQLGetData を使用して出力パラメーターを取得する](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)です。  
  
-   SQL_GD_ANY_COLUMN です。 このオプションが返される場合は**SQLGetData**最後の列をバインドする前に含めて、任意のバインドされていない列を呼び出すことができます。  
  
-   SQL_GD_ANY_ORDER です。 このオプションが返される場合は**SQLGetData**任意の順序でバインドされていない列を呼び出すことができます。  
  
-   SQL_GD_BLOCK です。 このオプションは、によって返される場合**SQLGetInfo** SQL_GETDATA_EXTENSIONS 情報の種類には、ドライバーへの呼び出しをサポートしています**SQLGetData**行セットのサイズが 1 より大きいと、アプリケーションがを呼び出すことができます **。SQLSetPos** SQL_POSITION オプションを呼び出す前に正しい行にカーソルを置きに**SQLGetData です。**  
  
-   SQL_GD_BOUND です。 このオプションが返される場合は**SQLGetData**バインドされた列に対して呼び出すことができるだけでなく、列をバインド解除されました。  
  
 これらの制限事項とドライバーの権限を許可し、それらを緩和する 2 つの例外があります。 最初に、 **SQLGetData**呼び出さないで順方向専用カーソルの行セットのサイズが 1 より大きい場合。 第二に、ドライバーは、ブックマークをサポートする場合、必要があります常にサポートを呼び出す機能**SQLGetData**列 0 で、アプリケーションを呼び出すことはできない場合でも**SQLGetData**の他の列の最後より前に、バインドされた列です。 (アプリケーションが ODBC 2 扱うとき *.x*ドライバー、 **SQLGetData**で呼び出されると、ブックマークを正常に返す*Col_or_Param_Num*呼び出しの後に 0 に等しい**SQLFetch**ので、 **SQLFetch**は ODBC 3 によってもマップ *.x*ドライバー マネージャーを**SQLExtendedFetch** と*FetchOrientation* SQL_FETCH_NEXT のおよび**SQLGetData**で、 *Col_or_Param_Num* 0 は、ODBC 3 によってマップされて *.x*をドライバー マネージャー**SQLGetStmtOption**で、 *fOption* SQL_GET_BOOKMARK のです)。  
  
 **SQLGetData**だけ呼び出すことによって挿入された行のブックマークを取得するのには使用できません**SQLBulkOperations** SQL_ADD オプションを使用して、行にカーソルが配置されていないためです。 アプリケーションでは、このような行のブックマークを呼び出す前に、バインド列 0 によって取得できます**SQLBulkOperations**その場合は、SQL_ADD で**SQLBulkOperations**バインドされたバッファー内のブックマークを返します。 **SQLFetchScroll** sql_fetch_bookmark を指定してその行にカーソルの位置を変更すると呼ばれることができます。  
  
 場合、 *TargetType*の SQL_DESC_DATETIME_INTERVAL_PRECISION および SQL_DESC_PRECISION フィールドで設定されている引数は、interval データ型、既定の間隔先頭精度 (2) と既定の間隔 (秒) の有効桁数 (6)それぞれ、ARD は、データに使用されます。 場合、 *TargetType*引数 SQL_C_NUMERIC データ型、既定の有効桁数 (ドライバーの定義) と、ARD の SQL_DESC_PRECISION および SQL_DESC_SCALE フィールドで設定されている既定の (0)、小数点以下桁数は、データに使用されます。 既定の有効桁数または小数点以下桁数が適切でない場合、アプリケーションを明示的に設定、適切な記述子フィールドへの呼び出しによって**SQLSetDescField**または**SQLSetDescRec**です。 SQL_DESC_CONCISE_TYPE フィールド SQL_C_NUMERIC と呼び出しを設定できます**SQLGetData**で、 *TargetType*記述子フィールドで、有効桁数と小数点以下桁数の値を原因となる SQL_ARD_TYPE の引数使用されます。  
  
> [!NOTE]  
>  ODBC 2 で *.x*、アプリケーション設定*TargetType*を示すために、SQL_C_DATE、SQL_C_TIME、または SQL_C_TIMESTAMP \* *TargetValuePtr*日付、時刻、またはタイムスタンプの構造体。 ODBC 3 *.x*、アプリケーション設定*TargetType* SQL_C_TYPE_DATE、SQL_C_TYPE_TIME、または SQL_C_TYPE_TIMESTAMP にします。 ドライバー マネージャーにより、適切なマッピング情報に基づいて、必要な場合、アプリケーションとドライバーのバージョンにします。  
  
## <a name="retrieving-variable-length-data-in-parts"></a>部分の可変長データを取得します。  
 **SQLGetData**部分の可変長データを含む列からデータを取得するために使用できます: そのときに、SQL データ型の列の識別子は SQL_CHAR、SQL_VARCHAR、SQL_LONGVARCHAR、SQL_WCHAR、SQL_WVARCHAR、sql _WLONGVARCHAR、sql_binary 型、SQL_VARBINARY、SQL_LONGVARBINARY、または可変長型のドライバー固有の識別子。  
  
 アプリケーションの呼び出し部分内の列からデータを取得する**SQLGetData**同じ列の連続的に複数回です。 呼び出しごとに**SQLGetData**データの次の部分を返します。 文字データの中間部品から null 終端文字を削除するよう注意して、部品を再構成するため、アプリケーションの責任です。 十分なバッファーが終端文字に割り当てられたかを返す多くのデータがある場合**SQLGetData** SQL_SUCCESS_WITH_INFO と SQLSTATE 01004 (データが切り捨てられました) を返します。 データの最後の部分が返されるとき**SQLGetData** SQL_SUCCESS を返します。 SQL_NO_TOTAL も 0 が返されますの列からデータを取得する前回の有効な呼び出しでアプリケーションが存在しないための方法でわかればアプリケーション バッファー内のデータの量が無効です。 場合**SQLGetData**が呼び出されたこの後、SQL_NO_DATA を返します。 詳細については、次のセクションでは、「データの取得中に SQLGetData。」を参照してください。  
  
 可変長のブックマークでの部分で返される**SQLGetData**です。 他のデータへの呼び出しと同様に**SQLGetData**部分内の可変長のブックマーク戻ります SQLSTATE 01004 (文字列データの右側が切り捨てられました) と sql_success_with_info が返されるデータがある場合に戻ります。 これは、可変長のブックマークがへの呼び出しによって切り捨てられる場合とは異なる**SQLFetch**または**SQLFetchScroll**SQL_ERROR と SQLSTATE 22001 (文字列データの右側が切り捨てられました) が返されます。  
  
 **SQLGetData**部分で固定長のデータを返すには使用できません。 場合**SQLGetData**は行の 2 回以上呼び出されると固定長データを含む列に対して、sql_no_data が返されるすべての呼び出しに対して 1 つ目後です。  
  
## <a name="retrieving-streamed-output-parameters"></a>ストリーミングされる出力パラメーターを取得します。  
 アプリケーションが呼び出すことができる場合、ドライバーは、ストリーミングされる出力パラメーターをサポートする**SQLGetData**小規模なバッファーの回数を大きなパラメーター値を取得します。 ストリーミングされる出力パラメーターの詳細については、次を参照してください。 [SQLGetData を使用して出力パラメーターを取得する](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)です。  
  
## <a name="retrieving-data-with-sqlgetdata"></a>SQLGetData によるデータの取得  
 指定した列のデータを返す**SQLGetData**は、次の一連の手順を実行します。  
  
1.  SQL_NO_DATA が返されることが既に返された場合のすべての列のデータ。  
  
2.  セット\* *StrLen_or_IndPtr* SQL_NULL_DATA データが NULL の場合にします。 データが NULL の場合と*StrLen_or_IndPtr*が null ポインターで**SQLGetData** SQLSTATE 22002 (インジケーター変数に必要なが指定されていません) を返します。  
  
     列のデータが NULL の場合、 **SQLGetData**手順 3. に進みます。  
  
3.  文字またはバイナリ データは、列が含まれている場合、SQL_ATTR_MAX_LENGTH ステートメント属性が 0 以外の値に設定されている場合、 **SQLGetData**が既に呼び出されていないに SQL_ATTR_MAX_LENGTH を列に対して、データが切り捨てられますバイト数です。  
  
    > [!NOTE]  
    >  SQL_ATTR_MAX_LENGTH ステートメント属性はネットワーク トラフィックを削減するためのものです。 一般に、ネットワーク経由での返送前にデータが切り捨てられるデータ ソースによって実装されます。 ドライバーおよびデータ ソースは、それをサポートする必要はありません。 そのため、データが特定のサイズに切り捨てられたことを保証する、アプリケーションする必要がありますのサイズのバッファーを割り当てるし、サイズで指定、 *BufferLength*引数。  
  
4.  データで指定された型に変換*TargetType*です。 データには、そのデータ型の既定の有効桁数と小数点以下桁数は付与します。 場合*TargetType* SQL_ARD_TYPE、データは、ARD の SQL_DESC_CONCISE_TYPE フィールドの型を使用します。 場合*TargetType* SQL_ARD_TYPE は、データがで指定された有効桁数と小数点 SQL_DESC_DATETIME_INTERVAL_PRECISION、SQL_DESC_PRECISION、および、SQL_DESC_CONCISE の種類のデータの種類に応じて、ARD の SQL_DESC_SCALE フィールドください (_t) フィールドです。 既定の有効桁数または小数点以下桁数が適切でない場合、アプリケーションを明示的に設定、適切な記述子フィールドへの呼び出しによって**SQLSetDescField**または**SQLSetDescRec**です。  
  
5.  データが文字またはバイナリなどの可変長データ型に変換された場合**SQLGetData**データ長を超えているかどうかを確認*BufferLength*です。 (Null 終了文字を含む) の文字データの長さを超えた場合*BufferLength*、 **SQLGetData**にデータが切り捨てられます*BufferLength*長さ以下null 終了文字です。 Null で終端データ。 バイナリ データのデータ バッファーの長さを超えている場合**SQLGetData**まで切り捨てます*BufferLength*バイトです。  
  
     指定されたデータ バッファーが小さすぎる場合、null 終端文字を保持するために**SQLGetData** SQL_SUCCESS_WITH_INFO と SQLSTATE 01004 を返します。  
  
     **SQLGetData**決して切り捨てます固定長データ型に変換されたデータ以外の場合は常とみなされるの長さ **TargetValuePtr*データ型のサイズです。  
  
6.  変換された (および切り捨てられる可能性があります) のデータ配置\* *TargetValuePtr*です。 なお**SQLGetData**アウト オブ ラインのデータを返すことはできません。  
  
7.  内のデータの長さを配置\* *StrLen_or_IndPtr*です。 場合*StrLen_or_IndPtr*が null ポインターで**SQLGetData**長さは返しません。  
  
    -   文字またはバイナリ データでは、これは、データの長さの変換後と切り捨てを期限前に*BufferLength*です。 ドライバーを特定できない場合、データの長さ変換後、長い形式のデータの場合し、sql_success_with_info が返され、長 SQL_NO_TOTAL を設定します。 (を最後に呼び出した**SQLGetData**ゼロまたは SQL_NO_TOTAL ではない、データの長さを常に返す必要があります)。SQL_ATTR_MAX_LENGTH ステートメントによりデータが切り捨てられた場合は、属性、この属性の値: 実際の長さではなく — に配置されて\* *StrLen_or_IndPtr*です。 これは、この属性が、ドライバーはどのような実際の長さを判断する方法を持たないため、変換前に、サーバー上のデータの切り捨てを行うために設計されているためです。 ときに**SQLGetData**がこれには、現在の呼び出しの開始時に使用可能なデータの長さを連続して複数回呼び出されると、同じ列の以外の場合は後続の各呼び出しでは、長さが減ります。  
  
    -   他のすべてのデータ型では、これは、データの長さ変換後です。つまり、データの変換先の型のサイズです。  
  
8.  変換中に、有効桁数を失うことがなく、データが切り捨てられますかどうか (たとえば、実数 1.234 は切り捨てられます 1 の整数に変換すると)、または*BufferLength*が小さすぎます (たとえば、文字列"abcdef"が配置されます4 バイト バッファー) で**SQLGetData** SQLSTATE 01004 (データが切り捨てられました) と sql_success_with_info が返されます。 SQL_ATTR_MAX_LENGTH ステートメント属性のための有効桁数を失うことがなくデータが切り捨てられる場合**SQLGetData** SQL_SUCCESS を返し、SQLSTATE 01004 (データが切り捨てられました) は返されません。  
  
 バインドされたデータ バッファーの内容 (場合**SQLGetData**バインドされた列に対してを呼び出した) 長さ/インジケーター バッファーは不定と**SQLGetData** SQL_SUCCESS または SQL_SUCCESS_WITH_INFO を返しません。  
  
 連続して呼び出す**SQLGetData**要求された最後の列からデータが取得されます。 前のオフセットが無効になります。 たとえば、次の順序が行われる場合。  
  
```  
SQLGetData(icol=n), SQLGetData(icol=m), SQLGetData(icol=n)  
```  
  
 SQLGetData(icol=n) に 2 番目の呼び出しは、n 個の列の先頭からのデータを取得します。 以前の呼び出しにより、データ内の任意のオフセット**SQLGetData**列が有効ではなくなりました。  
  
## <a name="descriptors-and-sqlgetdata"></a>記述子および SQLGetData  
 **SQLGetData**記述子フィールドと直接やり取りしません。  
  
 場合*TargetType* SQL_ARD_TYPE、データは、ARD の SQL_DESC_CONCISE_TYPE フィールドの型を使用します。 場合*TargetType* SQL_ARD_TYPE または SQL_C_DEFAULT のいずれかが、データがで指定された有効桁数と小数点 SQL_DESC_DATETIME_INTERVAL_PRECISION、SQL_DESC_PRECISION、および種類のデータの種類に応じて、ARD SQL_DESC_SCALE フィールドSQL_DESC_CONCISE_TYPE フィールドです。  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションの実行、**選択**ステートメント Id、名、顧客の結果セットを返すし、電話番号の名前、ID、および電話番号で並べ替えられます。 各データ行では、それを呼び出し、 **SQLFetch**に次の行にカーソルを移動します。 呼び出す**SQLGetData**を取得するは、呼び出しでは、フェッチされたデータ以外のデータと返されるバイト数のバッファーを指定します。 **SQLGetData**です。 最後に、各従業員の名前、ID、および電話番号を出力します。  
  
```  
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
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列のストレージの割り当てください。|[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ブロック カーソルの位置に関係なく一括操作の実行|[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|1 行のデータまたは順方向専用の方向にデータのブロックをフェッチ|[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|実行時にパラメーターのデータを送信します。|[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|カーソルを配置するか、行セット内のデータを更新する、更新、または行セット内のデータを削除します。|[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
