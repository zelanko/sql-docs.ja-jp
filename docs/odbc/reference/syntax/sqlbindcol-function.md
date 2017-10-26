---
title: "SQLBindCol 関数 |Microsoft ドキュメント"
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
- SQLBindCol
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLBindCol
helpviewer_keywords:
- SQLBindCol function [ODBC]
ms.assetid: 41a37655-84cd-423f-9daa-e0b47b88dc54
caps.latest.revision: 37
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 641b08ab3d3aec59f66dd0405770cf19d4690769
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlbindcol-function"></a>SQLBindCol 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLBindCol**結果セット内の列にアプリケーション データのバッファーをバインドします。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLBindCol(  
      SQLHSTMT       StatementHandle,  
      SQLUSMALLINT   ColumnNumber,  
      SQLSMALLINT    TargetType,  
      SQLPOINTER     TargetValuePtr,  
      SQLLEN         BufferLength,  
      SQLLEN *       StrLen_or_Ind);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *ColumnNumber*  
 [入力]結果の数は、バインドする列を設定します。 列は、列の昇順に列 0 がブックマーク列を 0 から始まる番号が付けられます。 ブックマークが使用されていない場合: SQL_UB_OFF に SQL_ATTR_USE_BOOKMARKS ステートメント属性の設定は、-、列番号は 1 から始まります。  
  
 *TargetType*  
 [入力]C データ型の識別子、 \* *TargetValuePtr*バッファー。 使用して、データ ソースからデータを取得してそのとき**SQLFetch**、 **SQLFetchScroll**、 **SQLBulkOperations**、または**SQLSetPos**では、ドライバーは、データをこの型に変換します。使用して、データ ソースにデータを送信すると**SQLBulkOperations**または**SQLSetPos**ドライバーは、この種類のデータを変換します。 有効な C データ型と型識別子の一覧は、次を参照してください。、 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)付録 d: データ型」セクション。  
  
 場合、 *TargetType*の SQL_DESC_DATETIME_INTERVAL_PRECISION および SQL_DESC_PRECISION フィールドで設定されている引数は、interval データ型、既定の間隔先頭精度 (2) と既定の間隔 (秒) の有効桁数 (6)それぞれ、ARD は、データに使用されます。 場合、 *TargetType*引数 SQL_C_NUMERIC、既定の有効桁数 (ドライバーの定義) と、ARD の SQL_DESC_PRECISION および SQL_DESC_SCALE フィールドで設定されている既定の (0)、小数点以下桁数は、データに使用されます。 既定の有効桁数または小数点以下桁数が適切でない場合、アプリケーションを明示的に設定、適切な記述子フィールドへの呼び出しによって**SQLSetDescField**または**SQLSetDescRec**です。  
  
 拡張の C データ型を指定することもできます。 詳細については、次を参照してください。 [ODBC における C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)です。  
  
 *TargetValuePtr*  
 [遅延入力/出力]列にバインドするデータ バッファーへのポインター。 **SQLFetch**と**SQLFetchScroll**このバッファーにデータを返します。 **SQLBulkOperations**これでデータを返す場合にバッファー*操作*SQL_FETCH_BY_BOOKMARK; は、これからデータを取得場合にバッファー*操作*SQL_ADD または SQL_UPDATE_BY_BOOKMARK. **SQLSetPos**これでデータを返す場合にバッファー*操作*SQL_REFRESH; は、これからデータを取得場合にバッファー*操作*SQL_UPDATE がします。  
  
 場合*TargetValuePtr* null ポインターでは、ドライバーは、列のデータ バッファーをバインド解除します。 アプリケーションは、すべての列をバインド解除を呼び出して**SQLFreeStmt** SQL_UNBIND オプションを使用します。 アプリケーションが列のデータ バッファーをバインド解除が場合に、列のバインドされる長さ/インジケーター バッファーをまだ、 *TargetValuePtr*への呼び出しで引数**SQLBindCol** null ポインターしますですが、*StrLen_or_IndPtr*引数が有効な値です。  
  
 *BufferLength*  
 [入力]長さ、**TargetValuePtr*バッファーのバイト単位です。  
  
 ドライバーを使用して*BufferLength*の末尾を越えた書き込まれないように、 \* *TargetValuePtr*文字またはバイナリ データなどの可変長データを返すときにバッファーに格納します。 ドライバーが文字データが返されるときに、null 終端文字がカウントされることを確認\* *TargetValuePtr*です。 **TargetValuePtr*スペースを含める必要がありますのでの null 終了文字またはドライバーのデータが切り捨てられます。  
  
 ドライバーには、整数や日付構造体などの固定長データが返されるときに、ドライバーを無視*BufferLength*バッファーがデータを保持するのに十分な大きさを前提としています。 したがって、固定長のデータを十分な大きさのバッファーを割り当て、アプリケーションにとって重要であるまたは、ドライバーは、バッファーの末尾を越えた書き込みます。  
  
 **SQLBindCol** SQLSTATE HY090 が返されます (無効な文字列長またはバッファー長) と*BufferLength*が 0 未満の値が時ではなく*BufferLength*は 0 です。 ただし場合、 *TargetType*文字の種類を指定しますアプリケーションは設定しないでください*BufferLength*を 0 に ISO CLI – 準拠のドライバーは SQLSTATE HY090 を返すため (無効な文字列長またはバッファー長) で。大文字にします。  
  
 *StrLen_or_IndPtr*  
 [遅延入力/出力]列にバインドする長さ/インジケーター バッファーへのポインター。 **SQLFetch**と**SQLFetchScroll**このバッファーの値を返します。 **SQLBulkOperations**場合に、この値を取得バッファー*操作*SQL_ADD、SQL_UPDATE_BY_BOOKMARK、または SQL_DELETE_BY_BOOKMARK です。 **SQLBulkOperations**場合にこの値を返しますバッファー*操作*SQL_FETCH_BY_BOOKMARK がします。 **SQLSetPos**場合にこの値を返しますバッファー*操作*SQL_REFRESH; は、これから値を取得場合にバッファー*操作*SQL_UPDATE がします。  
  
 **SQLFetch**、 **SQLFetchScroll**、 **SQLBulkOperations**、および**SQLSetPos**長さ/インジケーター バッファーで、次の値を返すことができます。  
  
-   返される使用可能なデータの長さ  
  
-   SQL_NO_TOTAL  
  
-   SQL_NULL_DATA  
  
 アプリケーションは、長さ/インジケーター バッファーで使用するために、次の値を配置できる**SQLBulkOperations**または**SQLSetPos**:  
  
-   送信されるデータの長さ  
  
-   SQL_NTS  
  
-   SQL_NULL_DATA  
  
-   SQL_DATA_AT_EXEC  
  
-   SQL_LEN_DATA_AT_EXEC マクロの結果  
  
-   SQL_COLUMN_IGNORE  
  
 インジケーターのバッファー長バッファーと別のバッファーには、長バッファーは、その他のすべての値を返すことができますが、インジケーター バッファーはのみの SQL_NULL_DATA を返すことができます。  
  
 詳細については、次を参照してください[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)、 [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)、 [SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)、および[長さ/インジケーター値を使用する。](../../../odbc/reference/develop-app/using-length-and-indicator-values.md).  
  
 場合*StrLen_or_IndPtr*は null ポインター、いない長さまたはインジケーターの値を使用します。 これは、データとデータのフェッチが NULL の場合のエラーです。  
  
 参照してください[ODBC 64 ビット情報](../../../odbc/reference/odbc-64-bit-information.md)、64 ビット オペレーティング システム、アプリケーションが実行される場合。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLBindCol** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLBindCol**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|(DM)、 *ColumnNumber*引数が 0 の場合、 *TargetType* SQL_C_BOOKMARK または SQL_C_VARBOOKMARK 引数がありませんでした。|  
|07009|無効な記述子のインデックス|引数が指定された値*ColumnNumber*結果セット内の列の最大数を超えました。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、 * \*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY003|無効なアプリケーション バッファーの種類|引数*TargetType*有効なデータ型でも SQL_C_DEFAULT がします。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数ではときに実行されている**SQLBindCol**が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|引数の指定された値 (DM) *BufferLength*が 0 未満です。<br /><br /> (DM) ドライバーは ODBC 2、でした。*x*ドライバー、 *ColumnNumber*引数が 0 であり、引数に指定された値に設定された*BufferLength* 4 に等しいでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースがの組み合わせで指定された変換をサポートしていない、 *TargetType*引数と対応する列のドライバー固有の SQL データ型。<br /><br /> 引数*ColumnNumber*が 0 と、ドライバーはブックマークをサポートしていません。<br /><br /> ドライバーには、ODBC 2 のみがサポートしています。*x*と引数*TargetType*次のいずれかの。<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> interval C データ型の一覧に示されたのと[C データ型](../../../odbc/reference/appendixes/c-data-types.md)付録 d: データ型にします。<br /><br /> ドライバーのみがサポート 3.50、および引数の前に ODBC バージョン*TargetType* SQL_C_GUID がします。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 **SQLBindCol**関連付けるには、使用または*をバインドする*結果内の列がデータ バッファーと、アプリケーションで長さ/インジケーター バッファーに設定します。 アプリケーションを呼び出すと**SQLFetch**、 **SQLFetchScroll**、または**SQLSetPos**以外の指定したバッファー内のデータのフェッチにドライバーが、バインドされた列のデータを返します詳細についてを参照してください[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)です。 アプリケーションを呼び出すと**SQLBulkOperations**を更新または行を挿入または**SQLSetPos**ドライバーが; 詳細については、バインドされた列を指定されたバッファーからのデータを取得する行を更新するには、を参照してください[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)または[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)です。 バインディングの詳細については、次を参照してください。[を取得する結果 (基本)](../../../odbc/reference/develop-app/retrieving-results-basic.md)です。  
  
 列を持ちませんそれらからデータを取り出すにバインドすることがわかります。 アプリケーションが呼び出すことができますも**SQLGetData**列からデータを取得します。 行と呼び出しで一部の列をバインドすることはできますが**SQLGetData**他のユーザーが、これはいくつかの制限される可能性があります。 詳細については、次を参照してください。 [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)です。  
  
## <a name="binding-unbinding-and-rebinding-columns"></a>列のバインド、バインド解除、および再バインド  
 列のバインド、バインドされていない、またはデータが結果セットからフェッチした後でも、いつでも再バインドできます。 新しいバインディングは、バインディングを使用する関数が呼び出されると、次回を有効になります。 たとえば、アプリケーションが、結果セットと呼び出し内の列をバインド**SQLFetch**です。 ドライバーは、バインドされたバッファーにデータを返します。 今すぐアプリケーション バインドを列バッファーの別のセットにあるとします。 ドライバーは新しくバインドされたバッファーに単にフェッチされた行のデータを格納されません。 代わりに、まで待機して**SQLFetch**が再度呼び出され、新しくバインドされたバッファー内の次の行のデータを配置します。  
  
> [!NOTE]  
>  ステートメント属性 SQL_ATTR_USE_BOOKMARKS は、列 0 をバインドする前に常に設定する必要があります。 これは必要ありませんが、強くお勧めします。  
  
## <a name="binding-columns"></a>列のバインド  
 アプリケーションが呼び出すの列にバインドする**SQLBindCol**し、列数、種類、アドレス、およびデータ バッファーの長さと長さ/インジケーター バッファーのアドレスを渡します。 これらのアドレスを使用する方法については、「バッファー アドレス、」このセクションの後半を参照してください。 バインド列の詳細については、次を参照してください。[を使用して SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)です。  
  
 これらのバッファーの使用が延期されます。アプリケーションにバインドして**SQLBindCol**されますが、ドライバーが他の関数にアクセスして、つまり**SQLBulkOperations**、 **SQLFetch**、 **SQLFetchScroll**、または**SQLSetPos**です。 アプリケーションの責任で、ポインターが指定されているかどうかを確認する**SQLBindCol**バインドが有効に限り有効なままです。 アプリケーションでは、これらのポインターが無効になる場合: たとえば、バッファーを解放 — し、それらを有効にする期待している関数を呼び出して、結果は未定義とします。 詳細については、次を参照してください。[遅延バッファー](../../../odbc/reference/develop-app/deferred-buffers.md)です。  
  
 バインディングは、新しいバインドによって置き換えられる、列は、バインド、または、ステートメントが解放されるまで有効です。  
  
## <a name="unbinding-columns"></a>列のバインドを解除  
 アプリケーションを呼び出す 1 つの列のバインドを解除する**SQLBindCol**で*ColumnNumber*その列の数に設定し、 *TargetValuePtr* null ポインターを設定します。 場合*ColumnNumber* 、バインドされていない列を参照**SQLBindCol** SQL_SUCCESS が返されます。  
  
 アプリケーションが呼び出すすべての列のバインドを解除する**SQLFreeStmt**で*fOption* SQL_UNBIND に設定します。 これは、ゼロに ARD の SQL_DESC_COUNT フィールドを設定して実現できます。  
  
## <a name="rebinding-columns"></a>列を再バインド  
 アプリケーションは、バインディングを変更する 2 つの操作のいずれかを実行できます。  
  
-   呼び出す**SQLBindCol**は既にバインドされている列の新しいバインディングを指定します。 ドライバーでは、新しい古いバインドが上書きされます。  
  
-   バインディングの呼び出しによって指定されたバッファーのアドレスに追加するオフセットを指定する**SQLBindCol**です。 詳細については、次のセクションでは、「バインドのオフセットです。」を参照してください。  
  
## <a name="binding-offsets"></a>オフセットのバインド  
 バインディングのオフセットは、データと長さ/インジケーター バッファーのアドレスに追加される値 (で指定されたとおり、 *TargetValuePtr*と*StrLen_or_IndPtr*引数) を逆参照する前にします。 オフセットを使用している場合、バインディングとは、アプリケーションのバッファーを配置する方法の"template"とアプリケーションは、オフセットを変更することによってメモリの異なる領域にこの"template"を移動することができます。 各バインディングでは、各アドレスに同じオフセットを追加するための異なる列バッファー間での相対オフセットは、バッファーの各セット内で同じでなければなりません。 これは、常に true の場合行方向のバインドが使用されます。アプリケーションは、これを列方向のバインドを使用する場合に true にするには、そのバッファーをレイアウトする必要があります慎重にします。  
  
 バインディング オフセットを使用して基本的に同じ効果を呼び出して列の再バインドとして**SQLBindCol**です。 その違いは、新しい呼び出しを**SQLBindCol**バインディングのオフセットとしての使用は、アドレスは変わりませんが、それらにオフセットを加算するだけが、データ バッファーおよび長さ/インジケーター バッファーの新しいアドレスを指定します。 必要があると、このオフセットは常に最初にバインドされたアドレスに追加されるたびに、アプリケーションでは、新しいオフセットを指定できます。 具体的には、オフセットが 0 に設定されている場合、または null ポインターには、ステートメント属性が設定されている場合は、ドライバーは最初にバインドされたアドレスを使用します。  
  
 バインディングのオフセットを指定するには、アプリケーションは、SQLINTEGER バッファーのアドレスを SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性を設定します。 アプリケーションがバインドを使用する関数を呼び出す前にこのバッファーのバイト オフセットを格納します。 を使用するバッファーのアドレスを特定するのには、ドライバーは、アドレス、バインディングにオフセットを追加します。 アドレスとオフセットの合計は、有効なアドレスである必要がありますが、有効なオフセットを追加するアドレスがありません。 バインディングのオフセットを使用する方法の詳細については、「バッファー アドレス、」このセクションの後半を参照してください。  
  
## <a name="binding-arrays"></a>配列のバインド  
 行セットのサイズ (SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性の値) が 1 より大きい場合は、アプリケーションは 1 つのバッファーではなくバッファーの配列をバインドします。 詳細については、次を参照してください。[ブロック カーソル](../../../odbc/reference/develop-app/block-cursors.md)です。  
  
 アプリケーションは、2 つの方法で配列をバインドできます。  
  
-   配列を各列にバインドします。 これを呼びます*列方向のバインド*各データ構造体 (配列) には、1 つの列のデータが含まれているためです。  
  
-   行全体のデータを保持し、これらの構造体の配列をバインドする構造体を定義します。 これを呼びます*行方向のバインド*データ構造ごとに 1 つの行のデータが含まれているためです。  
  
 各配列の各バッファーの行セットのサイズと少なくとも同じ数の要素が必要です。  
  
> [!NOTE]  
>  アプリケーションは、配置が有効であることを確認する必要があります。 配置に関する考慮事項の詳細については、次を参照してください。[配置](../../../odbc/reference/develop-app/alignment.md)です。  
  
## <a name="column-wise-binding"></a>列方向のバインド  
 列方向のバインドでは、そのアプリケーションが別のデータと長さ/インジケーターの配列を各列にバインドします。  
  
 列方向のバインドを使用するには、アプリケーションはまずを SQL_BIND_BY_COLUMN に SQL_ATTR_ROW_BIND_TYPE ステートメント属性を設定します。 (これは、既定値です)。各列をバインドするには、アプリケーションは、次の手順を実行します。  
  
1.  データ バッファーの配列を割り当てます。  
  
2.  長さ/インジケーター バッファーの配列を割り当てます。  
  
    > [!NOTE]  
    >  アプリケーションは、列方向のバインドを使用する場合に、記述子に直接書き込まれる場合、は、データの長さとインジケーター データの別の配列を使用できます。  
  
3.  呼び出し**SQLBindCol**次の引数で。  
  
    -   *TargetType*データ バッファーの配列内の単一要素の型です。  
  
    -   *TargetValuePtr*データ バッファー配列のアドレスです。  
  
    -   *BufferLength*データ バッファーの配列内の単一要素のサイズです。 *BufferLength*データが固定長のデータの場合、引数は無視されます。  
  
    -   *StrLen_or_IndPtr*長さ/インジケーター配列のアドレスです。  
  
 この情報を使用する方法の詳細については、「バッファー アドレス、」このセクションの後半を参照してください。 列方向のバインドの詳細については、次を参照してください。[列方向のバインド](../../../odbc/reference/develop-app/column-wise-binding.md)です。  
  
## <a name="row-wise-binding"></a>行方向のバインド  
 行方向のバインドでは、アプリケーションは、各列をバインドするためのデータと長さ/インジケーター バッファーを格納する構造体を定義します。  
  
 行方向のバインドを使用するのには、アプリケーションは、次の手順を実行します。  
  
1.  データ (データと長さ/インジケーター バッファーを含む) の 1 つの行を格納する構造体を定義し、これらの構造体の配列を割り当てます。  
  
    > [!NOTE]  
    >  アプリケーションは、行方向のバインドを使用する場合に、記述子に直接書き込まれる場合、は、データの長さとインジケーター データの個別のフィールドを使用できます。  
  
2.  1 行のデータを格納する構造体のサイズまたは結果の列のバインド先のバッファーのインスタンスのサイズには、SQL_ATTR_ROW_BIND_TYPE ステートメント属性を設定します。 長さは、バインドされたすべての列および構造体またはバインドされた列のアドレスの指定した長さでインクリメント時に、結果が次の行に同じ列の先頭を指すがかどうかを確認する、バッファーの埋め込み用の領域を含める必要があります。 使用する場合、 *sizeof* ANSI c 演算子は、この動作が保証されます。  
  
3.  呼び出し**SQLBindCol**をバインドするには、各列に対して次の引数で。  
  
    -   *TargetType*を列にバインドするデータ バッファーのメンバーの種類です。  
  
    -   *TargetValuePtr*バッファーのデータ メンバー配列の最初の要素のアドレスです。  
  
    -   *BufferLength*データ バッファーのメンバーのサイズです。  
  
    -   *StrLen_or_IndPtr*バインドされる長さ/インジケーター メンバーのアドレスです。  
  
 この情報を使用する方法の詳細については、「バッファー アドレス、」このセクションの後半を参照してください。 列方向のバインドの詳細については、次を参照してください。[行方向のバインド](../../../odbc/reference/develop-app/row-wise-binding.md)です。  
  
## <a name="buffer-addresses"></a>バッファーのアドレス  
 *バッファー アドレス*データまたは長さ/インジケーター バッファーの実際のアドレスです。 ドライバーは、(中に取得時間など)、バッファーに書き込む直前に、バッファーのアドレスを計算します。 次の数式で指定されたアドレスを使用しているから算出されます、 *TargetValuePtr*と*StrLen_or_IndPtr*引数、バインディングのオフセット、および行番号。  
  
 *アドレスをバインド* + *オフセットをバインド*+ ((*行数*– 1) x*要素サイズ*)  
  
 数式の変数が定義されているように、次の表で説明します。  
  
|変数|Description|  
|--------------|-----------------|  
|*アドレスをバインドします。*|データ バッファーの指定したアドレス、 *TargetValuePtr*引数**SQLBindCol**です。<br /><br /> 長さ/インジケーター バッファーの指定したアドレス、 *StrLen_or_IndPtr*引数**SQLBindCol**です。 詳細については、"記述子および SQLBindCol"セクションの「追加コメント」を参照してください。<br /><br /> バインドされたアドレスが 0 でのデータ値が返されない場合でも、前の式で計算されたアドレスは 0 以外。|  
|*オフセットのバインド*|行方向のバインドを使用する場合 SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性を持つアドレスに格納された値を指定します。<br /><br /> 列方向のバインドを使用する場合、または SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性の値が null ポインターで*バインディング オフセット*は 0 です。|  
|*行番号*|1 から始まる行セットの行の数。 単一行のフェッチは、既定値は、これは 1 です。|  
|*要素のサイズ*|バインドの配列内の要素のサイズ。<br /><br /> 列方向のバインドを使用すると、これは**sizeof(SQLINTEGER)**長さ/インジケーター バッファーの場合。 値では、データ バッファーを*BufferLength*引数**SQLBindCol**場合は、データ型が固定長データ型が変数の長さ、およびデータ型のサイズの場合。<br /><br /> 場合は行方向のバインドを使用すると、これは、両方のデータと長さ/インジケーター バッファーの SQL_ATTR_ROW_BIND_TYPE ステートメント属性の値。|  
  
## <a name="descriptors-and-sqlbindcol"></a>記述子および SQLBindCol  
 次のセクションで説明する方法**SQLBindCol**記述子と対話します。  
  
> [!CAUTION]  
>  呼び出す**SQLBindCol**の 1 つのステートメントが他のステートメントを与えることができます。 これは、ステートメントに関連付けられている ARD が明示的に割り当てられているし、その他のステートメントに関連付けられてもときに発生します。 **SQLBindCol**記述子を変更、変更は、この記述子が関連付けられているすべてのステートメントに適用します。 呼び出す前に場合は、必要な動作でない場合は、アプリケーションが、他のステートメントからこの記述子の関連付けを解除する必要があります**SQLBindCol**です。  
  
## <a name="argument-mappings"></a>引数のマップ  
 概念的には、 **SQLBindCol**シーケンスでは、次の手順を実行します。  
  
1.  呼び出し**SQLGetStmtAttr** ARD ハンドルを取得します。  
  
2.  呼び出し**SQLGetDescField**この記述子の SQL_DESC_COUNT のフィールドを取得する場合の値、 *ColumnNumber*引数 SQL_DESC_COUNT、呼び出しの値を超えています**SQLSetDescField**に SQL_DESC_COUNT の値を大きく*ColumnNumber*です。  
  
3.  呼び出し**SQLSetDescField** ARD の次のフィールドに値を割り当てるを複数回します。  
  
    -   SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE の値に設定*TargetType*する点を除いて、場合*TargetType*は 1 つ、datetime または間隔サブタイプの簡潔な識別子の SQL_DESC_TYPE に設定 sql _DATETIME フィールド型または SQL_INTERVAL、それぞれします。SQL_DESC_CONCISE_TYPE を簡潔な識別子に設定します。および対応する日付時刻または間隔サブコードに SQL_DESC_DATETIME_INTERVAL_CODE を設定します。  
  
    -   SQL_DESC_LENGTH、SQL_DESC_PRECISION、SQL_DESC_SCALE、および SQL_DESC_DATETIME_INTERVAL_PRECISION の 1 つ以上を設定に応じて適切な*TargetType*です。  
  
    -   SQL_DESC_OCTET_LENGTH フィールドの値に設定*BufferLength*です。  
  
    -   SQL_DESC_DATA_PTR フィールドの値に設定*ターゲット値*です。  
  
    -   SQL_DESC_INDICATOR_PTR フィールドの値に設定*StrLen_or_Ind*です。 (詳しくは、次の段落を参照してください)。  
  
    -   SQL_DESC_OCTET_LENGTH_PTR フィールドの値に設定*StrLen_or_Ind*です。 (詳しくは、次の段落を参照してください)。  
  
 変数を*StrLen_or_Ind*引数を指すインジケーターと長さの両方の情報に使用します。 この変数に格納フェッチには、列の null 値が検出されると、SQL_NULL_DATAそれ以外の場合、この変数にデータの長さを格納します。 として null ポインターを渡す*StrLen_or_Ind*データ長を返すからフェッチ操作の保持が失敗する場合は、null 値を検出し、SQL_NULL_DATA を返すことはできません、フェッチは、します。  
  
 場合に呼び出し**SQLBindCol**失敗は、ARD で設定した記述子フィールドの内容が定義されていませんし、ARD の SQL_DESC_COUNT フィールドの値は変更されません。  
  
## <a name="implicit-resetting-of-count-field"></a>カウント フィールドの暗黙の型をリセットします。  
 **SQLBindCol** SQL_DESC_COUNT の値に設定、 *ColumnNumber* SQL_DESC_COUNT の値が増加するこのする場合にのみ引数。 場合の値、 *TargetValuePtr*引数が null ポインターの値、 *ColumnNumber*引数が SQL_DESC_COUNT (つまり、バインドするとき、最高のバインドを解除する列)、し SQL_DESC_カウントは、最高の残りのバインドされた列の数に設定されます。  
  
## <a name="cautions-regarding-sqldefault"></a>SQL_DEFAULT に関する注意事項  
 列のデータを正常に取得するをアプリケーションはアプリケーション バッファー内のデータの開始位置と長さ正しく調べます必要があります。 アプリケーションが、明示的なを指定*TargetType*アプリケーションの誤解を容易に検出します。 ただし、アプリケーションを指定すると、 *TargetType* SQL_DEFAULT の**SQLBindCol**から適用できます別のデータ型の列に 1 つの目的のいずれかの変更から、アプリケーションで、メタデータまたは別の列に、コードを適用します。 ここでは、アプリケーションが常を特定できません開始またはフェッチされた列のデータの長さ。 これは、報告されないデータのエラーまたはメモリ違反が発生する可能性があります。  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションの実行、**選択**名前により、結果セットを返す、顧客の Id、名前、および電話番号、Customers テーブルでのステートメントが並べ替えられます。 呼び出して**SQLBindCol**のローカル バッファーにデータの列をバインドします。 アプリケーションが最後を使用してデータの各行をフェッチ**SQLFetch**各顧客の名前、ID、および電話番号を出力します。  
  
 コード例については、次を参照してください[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)、 [SQLColumns 関数](../../../odbc/reference/syntax/sqlcolumns-function.md)、 [SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)、および[SQLSetPos 関数。](../../../odbc/reference/syntax/sqlsetpos-function.md).  
  
```  
// SQLBindCol_ref.cpp  
// compile with: odbc32.lib  
#include <windows.h>  
#include <stdio.h>  
  
#define UNICODE  
#include <sqlext.h>  
  
#define NAME_LEN 50  
#define PHONE_LEN 20  
  
void show_error() {  
   printf("error\n");  
}  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt = 0;  
   SQLRETURN retcode;  
   SQLWCHAR szName[NAME_LEN], szPhone[PHONE_LEN], sCustID[NAME_LEN];  
   SQLLEN cbName = 0, cbCustID = 0, cbPhone = 0;  
  
   // Allocate environment handle  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
  
   // Set the ODBC version environment attribute  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
  
      // Allocate connection handle  
      if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
         retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
  
         // Set login timeout to 5 seconds  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
            SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
  
            // Connect to data source  
            retcode = SQLConnect(hdbc, (SQLWCHAR*) L"NorthWind", SQL_NTS, (SQLWCHAR*) NULL, 0, NULL, 0);  
  
            // Allocate statement handle  
            if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {   
               retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);   
  
               retcode = SQLExecDirect(hstmt, (SQLWCHAR *) L"SELECT CustomerID, ContactName, Phone FROM CUSTOMERS ORDER BY 2, 1, 3", SQL_NTS);  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
  
                  // Bind columns 1, 2, and 3  
                  retcode = SQLBindCol(hstmt, 1, SQL_C_CHAR, &sCustID, 100, &cbCustID);  
                  retcode = SQLBindCol(hstmt, 2, SQL_C_CHAR, szName, NAME_LEN, &cbName);  
                  retcode = SQLBindCol(hstmt, 3, SQL_C_CHAR, szPhone, PHONE_LEN, &cbPhone);   
  
                  // Fetch and print each row of data. On an error, display a message and exit.  
                  for (i ; ; i++) {  
                     retcode = SQLFetch(hstmt);  
                     if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
                        show_error();  
                     if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
                        wprintf(L"%d: %S %S %S\n", i + 1, sCustID, szName, szPhone);  
                     else  
                        break;  
                  }  
               }  
  
               // Process data  
               if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
                  SQLCancel(hstmt);  
                  SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
               }  
  
               SQLDisconnect(hdbc);  
            }  
  
            SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
         }  
      }  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   }  
}  
```  
  
 参照してください、[サンプル ODBC プログラム](../../../odbc/reference/sample-odbc-program.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|複数行のデータのフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|ステートメントで列のバッファーを解放します。|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|データの列の一部またはすべてのフェッチ|[SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|結果の数を返すセットの列|[SQLNumResultCols 関数](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

