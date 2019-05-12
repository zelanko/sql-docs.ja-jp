---
title: SQLBindCol 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 17b907be3e2641fe1dcbbb8fbd96586132e054ca
ms.sourcegitcommit: 7a3243c45830cb3f49a7fa71c2991a9454fd6f5a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/11/2019
ms.locfileid: "65538072"
---
# <a name="sqlbindcol-function"></a>SQLBindCol 関数
**準拠**  
 バージョンが導入されました。ODBC 1.0 規格に準拠します。ISO 92  
  
 **まとめ**  
 **SQLBindCol**アプリケーション データのバッファーを結果セット内の列にバインドします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
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
 [入力]結果の数は、バインドする列を設定します。 列は、列の昇順に列 0 のブックマーク列がある、0 から始まる番号が付けられます。 SQL_UB_OFF - に SQL_ATTR_USE_BOOKMARKS ステートメント属性を設定するは、ブックマークを使用していない場合、列番号は 1 から始まります。  
  
 *TargetType*  
 [入力]C データ型の識別子、 \* *TargetValuePtr*バッファー。 データ ソースからデータを取得してそのとき**SQLFetch**、 **SQLFetchScroll**、 **SQLBulkOperations**、または**SQLSetPos**、ドライバーでデータをこの型に変換します。データ ソースにデータを送信すると**SQLBulkOperations**または**SQLSetPos**ドライバーは、この種類のデータを変換します。 有効な C データ型と型識別子の一覧は、次を参照してください、 [C データ型](../../../odbc/reference/appendixes/c-data-types.md)付録 d: セクション。データ型。  
  
 場合、 *TargetType*引数の SQL_DESC_DATETIME_INTERVAL_PRECISION および SQL_DESC_PRECISION のフィールド セットとして、interval データ型を既定の間隔の主要な精度 (2) と既定の間隔 (秒) の有効桁数 (6) は、それぞれ、ARD データに使用されます。 場合、 *TargetType*引数 SQL_C_NUMERIC、(ドライバー定義) の既定の精度は、ARD の SQL_DESC_PRECISION および SQL_DESC_SCALE フィールドで設定されている既定のスケール (0)、データに使用されます。 呼び出して場合、アプリケーションで明示的に適切な記述子フィールドを設定、既定の有効桁数または小数点が適切でない場合**SQLSetDescField**または**SQLSetDescRec**します。  
  
 拡張の C データ型を指定することもできます。 詳細については、次を参照してください。 [ODBC における C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)します。  
  
 *TargetValuePtr*  
 [遅延の入力/出力]列にバインドするデータ バッファーへのポインター。 **SQLFetch**と**SQLFetchScroll**このバッファーにデータを返します。 **SQLBulkOperations**これでデータを返す場合にバッファー*操作*SQL_FETCH_BY_BOOKMARK; は、これからデータを取得場合にバッファー*操作*SQL_ADD SQL_UPDATE_BY_BOOKMARK か。 **SQLSetPos**これでデータを返す場合にバッファー*操作*SQL_REFRESH; は、これからデータを取得場合にバッファー*操作*SQL_UPDATE が。  
  
 場合*TargetValuePtr* null ポインターの場合は、ドライバーは、列のデータ バッファーをバインド解除します。 アプリケーションは、すべての列をバインド解除を呼び出して**SQLFreeStmt** SQL_UNBIND オプションを使用します。 アプリケーションが列のデータ バッファーをバインド解除が場合に、列のバインドされる長さ/インジケーター バッファーをまだ、 *TargetValuePtr*への呼び出しで引数**SQLBindCol** null ポインターしますですが、*StrLen_or_IndPtr*引数は有効な値です。  
  
 *BufferLength*  
 [入力]長さ、**TargetValuePtr*バッファー (バイト単位)。  
  
 ドライバーを使用して*BufferLength*の末尾を越えて書き込みを回避するために、 \* *TargetValuePtr* 文字またはバイナリ データなどの可変長データが返されるときにバッファーします。 ドライバーが文字データが返されるときに、null 終端文字がカウントされることを確認\* *TargetValuePtr* します。 **TargetValuePtr* スペースを含める必要がありますので、null 終了文字またはドライバーにデータを切り捨てるの。  
  
 ドライバーには整数、日付構造体などの固定長データが返されるときに、ドライバーは無視されます*BufferLength*バッファーが、データを保持するのに十分な大きさを前提としています。 そのため、または固定長のデータを十分な大きさのバッファーを割り当てられません。 アプリケーションの重要なことが、ドライバーは、バッファーの末尾を越えて書き込み。  
  
 **SQLBindCol** SQLSTATE HY090 が返されます (無効な文字列長またはバッファー長) と*BufferLength*が 0 未満の値がときではなく*BufferLength*は 0 です。 ただし場合、 *TargetType*文字の種類を指定します、アプリケーションに設定する必要がありますいない*BufferLength*を 0 に CLI の ISO 準拠のドライバーは SQLSTATE HY090 を返すため、(無効な文字列長またはバッファー長) で大文字にします。  
  
 *StrLen_or_IndPtr*  
 [遅延の入力/出力]列にバインドする長さ/インジケーター バッファーへのポインター。 **SQLFetch**と**SQLFetchScroll**このバッファーの値を返します。 **SQLBulkOperations**場合にこの値を取得しますバッファー*操作*SQL_ADD、SQL_UPDATE_BY_BOOKMARK、または SQL_DELETE_BY_BOOKMARK します。 **SQLBulkOperations**場合にこの値を返しますバッファー*操作*SQL_FETCH_BY_BOOKMARK です。 **SQLSetPos**場合にこの値を返しますバッファー*操作*SQL_REFRESH; は、これから値を取得場合にバッファー*操作*SQL_UPDATE が。  
  
 **SQLFetch**、 **SQLFetchScroll**、 **SQLBulkOperations**、および**SQLSetPos**長さ/インジケーター バッファーでは、次の値を返すことができます。  
  
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
  
 インジケーター バッファーおよび長さのバッファーは、別のバッファーには、長さのバッファーは、その他のすべての値を返すことができますが、インジケーター バッファーはのみの SQL_NULL_DATA を取得できます。  
  
 詳細については、次を参照してください[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)、 [SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)、 [SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)、および[長さ/インジケーター値を使用する](../../../odbc/reference/develop-app/using-length-and-indicator-values.md)。  
  
 場合*StrLen_or_IndPtr* null ポインター、いない長さまたはインジケーターの値が使用されます。 これは、データとデータをフェッチしていますが、NULL の場合のエラーです。  
  
 参照してください[ODBC 64 ビットの情報](../../../odbc/reference/odbc-64-bit-information.md)場合、アプリケーションが 64 ビットのオペレーティング システムで実行します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLBindCol** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得できる**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*します。 次の表に、によって返される通常の SQLSTATE 値**SQLBindCol** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|(DM)、 *ColumnNumber*引数が 0 の場合、 *TargetType* SQL_C_BOOKMARK または SQL_C_VARBOOKMARK 引数がありませんでした。|  
|07009|無効な記述子のインデックス|引数が指定された値*ColumnNumber*結果セット内の列の最大数を超えています。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY003|無効なアプリケーション バッファーの種類|引数*TargetType*が有効なデータ型も SQL_C_DEFAULT でもないです。|  
|HY010|関数のシーケンス エラー|(DM) を非同期的に実行中の関数が呼び出された接続ハンドルに関連付けられているため、 *StatementHandle*します。 この非同期関数ではときに実行されている**SQLBindCol**が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に対して呼び出された、 *StatementHandle* SQL_PARAM_DATA_ を返されます。ご利用いただけます。 ストリームのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) を非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**に対して呼び出された、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|引数に指定された値 (DM) *BufferLength*が 0 未満でした。<br /><br /> (DM) ドライバーは ODBC 2、でした。*x*ドライバー、 *ColumnNumber*引数が 0、および引数が指定された値に設定された*BufferLength* 4 に等しいでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースの組み合わせで指定された変換をサポートしていません、 *TargetType*引数と対応する列のドライバー固有の SQL データ型。<br /><br /> 引数*ColumnNumber*が 0 と、ドライバーは、ブックマークをサポートしていません。<br /><br /> ドライバーには、ODBC 2 のみがサポートしています。*x*と引数*TargetType*が、次のいずれか。<br /><br /> SQL_C_NUMERIC SQL_C_SBIGINT SQL_C_UBIGINT<br /><br /> 間隔の C データ型のいずれかと[C データ型](../../../odbc/reference/appendixes/c-data-types.md)付録 d:データ型。<br /><br /> ドライバーのみ、3.50 と引数の前に ODBC バージョンをサポートする*TargetType* SQL_C_GUID でした。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 **SQLBindCol**に関連付けるには、使用または*バインド、* 結果内の列は、データ バッファーと、アプリケーションで長さ/インジケーター バッファーに設定します。 アプリケーションを呼び出すと**SQLFetch**、 **SQLFetchScroll**、または**SQLSetPos**は指定されたバッファーにデータをフェッチするドライバーが、バインドされた列のデータを返します詳細についてを参照してください[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)します。 アプリケーションを呼び出すと**SQLBulkOperations**を更新または行を挿入または**SQLSetPos**ドライバー行を更新するには、指定したバッファーから、バインドされた列の詳細については、データを取得しますを参照してください[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)または[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)します。 バインドの詳細については、次を参照してください。 [(Basic) を取得する結果](../../../odbc/reference/develop-app/retrieving-results-basic.md)します。  
  
 そこからデータの取得にバインドする列がないことに注意してください。 アプリケーションを呼び出すことも**SQLGetData**列からデータを取得します。 行と呼び出しで一部の列をバインドすることはできますが**SQLGetData**それ以外の場合これはいくつかの制限によって異なります。 詳細については、次を参照してください。 [SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)します。  
  
## <a name="binding-unbinding-and-rebinding-columns"></a>列のバインド、バインド解除、および再バインド  
 列のバインド、バインドされていない場合、またはデータが結果セットからフェッチされた後でも、いつでも再バインドできます。 新しいバインドは次回のバインドを使用する関数が呼び出されるとに有効にします。 たとえば、結果セットと呼び出し内の列にバインドするアプリケーション**SQLFetch**します。 ドライバーは、バインドされたバッファーにデータを返します。 ここでアプリケーションのバインドをバッファーの別のセットに列とします。 ドライバーは新しくバインドされたバッファーにだけフェッチされる行のデータを配置していません。 代わりに、まで待機**SQLFetch**が再度呼び出され、新しくバインドされたバッファー内の次の行のデータを配置します。  
  
> [!NOTE]  
>  SQL_ATTR_USE_BOOKMARKS ステートメント属性は、列 0 をバインドする前に常に設定する必要があります。 これは必要ありませんが、強くお勧めします。  
  
## <a name="binding-columns"></a>バインディング列  
 列をバインドするアプリケーションを呼び出す**SQLBindCol**し、列数、種類、アドレス、およびデータ バッファーの長さと長さ/インジケーター バッファーのアドレスを渡します。 これらのアドレスを使用する方法については、このセクションの後半の「バッファー アドレス」を参照してください。 バインド列の詳細については、次を参照してください。[を使用して SQLBindCol](../../../odbc/reference/develop-app/using-sqlbindcol.md)します。  
  
 これらのバッファーの使用は延期されます。つまり、アプリケーションがバインドに**SQLBindCol**ドライバーにアクセスしてからその他の関数 - namely が**SQLBulkOperations**、 **SQLFetch**、 **SQLFetchScroll**、または**SQLSetPos**します。 アプリケーションの責任で、ポインターが指定されているかどうかを確認する**SQLBindCol**バインディングが有効な限り、有効なままです。 アプリケーションでは、これらのポインターが無効になる - たとえば、-、バッファーを解放しを有効にすることが必要とする関数を呼び出して、結果は未定義です。 詳細については、次を参照してください。[遅延バッファー](../../../odbc/reference/develop-app/deferred-buffers.md)します。  
  
 バインディングは、新しいバインドによって置き換えられる、列は、バインドがまたはステートメントが解放されるまで有効です。  
  
## <a name="unbinding-columns"></a>列のバインドを解除  
 アプリケーションを呼び出す 1 つの列のバインドを解除する**SQLBindCol**で*ColumnNumber*その列の数に設定し、 *TargetValuePtr* null ポインターを設定します。 場合*ColumnNumber* 、バインドされていない列を表します**SQLBindCol** SQL_SUCCESS が返されます。  
  
 アプリケーションが呼び出すすべての列のバインドを解除する**SQLFreeStmt**で*fOption*を SQL_UNBIND に設定します。 これは、ゼロに ARD の SQL_DESC_COUNT フィールドを設定しても実現できます。  
  
## <a name="rebinding-columns"></a>列を再バインド  
 アプリケーションは、バインディングを変更する 2 つの操作のいずれかを実行できます。  
  
-   呼び出す**SQLBindCol**は既にバインドされている列の新しいバインディングを指定します。 ドライバーは、新しいで古いバインドを上書きします。  
  
-   バインディングの呼び出しで指定したバッファーのアドレスに追加するオフセットを指定する**SQLBindCol**します。 詳細については、次のセクションでは、「バインディングのオフセット。」を参照してください。  
  
## <a name="binding-offsets"></a>オフセットのバインド  
 バインディングのオフセットは、データと長さ/インジケーター バッファーのアドレスに追加される値 (で指定されている、 *TargetValuePtr*と*StrLen_or_IndPtr*引数) は逆参照する前にします。 オフセットを使用している場合、バインディングでは、アプリケーションのバッファーをレイアウトする方法の「テンプレート」と、アプリケーションは、オフセットを変更することでメモリの異なる領域にこの"template"を移動することができます。 各バインディングでは、各アドレスに同じオフセットを追加するための異なる列バッファー間での相対オフセットはバッファーの各セット内で同じにする必要があります。 これは常に true と行方向のバインドが使用されます。アプリケーションのバッファーが、これが、列方向のバインドを使用する場合は true。 慎重にレイアウトする必要があります。  
  
 バインディングのオフセットを使用して呼び出すことによって列の再バインドと同じ効果では基本的に**SQLBindCol**します。 違いは、新しい呼び出しを提供する**SQLBindCol**バインディングのオフセットの使用は、アドレスは変わりませんが、それらへのオフセットを追加するだけですが、データ バッファーおよび長さ/インジケーター バッファーの新しいアドレスを指定します。 このオフセットは常に最初にバインドされたアドレスを追加するたびに、アプリケーションは、新しいオフセットを指定できます。 具体的には、オフセットが 0 に設定されている場合、または null ポインターには、ステートメント属性が設定されている場合、ドライバーは、最初にバインドされたアドレスを使用します。  
  
 バインディングのオフセットを指定するには、アプリケーションは、SQLINTEGER バッファーのアドレスに SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性を設定します。 アプリケーションのバインドを使用する関数を呼び出す前に、このバッファー内のバイトのオフセットを書き込みます。 を使用するバッファーのアドレスを確認するのには、ドライバーは、バインディングのアドレスにオフセットを追加します。 アドレスとオフセットの合計は有効なアドレスである必要がありますが、オフセットを追加するアドレスが有効にする必要はありません。 バインディングのオフセットを使用する方法の詳細については、このセクションの後半の「バッファー アドレス」を参照してください。  
  
## <a name="binding-arrays"></a>配列のバインド  
 行セットのサイズ (SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性の値) が 1 より大きい場合は、アプリケーションは、1 つのバッファーではなくバッファーの配列をバインドします。 詳細については、次を参照してください。[ブロック カーソル](../../../odbc/reference/develop-app/block-cursors.md)します。  
  
 アプリケーションでは、2 つの方法で配列をバインドできます。  
  
-   配列を各列にバインドします。 呼ばれる*列方向のバインド*各データ構造 (配列) には、1 つの列のデータが含まれています。  
  
-   行全体のデータを保持し、これらの構造体の配列をバインドする構造体を定義します。 呼ばれる*行方向のバインド*データ構造ごとに 1 つの行のデータが含まれています。  
  
 各配列バッファーの行セットのサイズと少なくとも同じ数の要素が必要です。  
  
> [!NOTE]  
>  アプリケーションは、配置が有効であることを確認する必要があります。 配置に関する考慮事項の詳細については、次を参照してください。[配置](../../../odbc/reference/develop-app/alignment.md)します。  
  
## <a name="column-wise-binding"></a>列方向のバインド  
 列方向のバインドでは、そのアプリケーションが別のデータと長さ/インジケーター配列を各列にバインドします。  
  
 列方向のバインドを使用するには、アプリケーションはまず SQL_BIND_BY_COLUMN に SQL_ATTR_ROW_BIND_TYPE ステートメント属性を設定します。 (これは、既定値です)。各列にバインドするには、アプリケーションは、次の手順を実行します。  
  
1.  データ バッファーの配列を割り当てます。  
  
2.  長さ/インジケーター バッファーの配列を割り当てます。  
  
    > [!NOTE]  
    >  場合は、アプリケーションは、列方向のバインドを使用する場合に、記述子に直接書き込む、個別の配列の長さとインジケーター データを使用できます。  
  
3.  呼び出し**SQLBindCol**次の引数で。  
  
    -   *TargetType*データ バッファーの配列内の単一要素の種類です。  
  
    -   *TargetValuePtr*データ バッファーの配列のアドレスです。  
  
    -   *BufferLength*データ バッファーの配列内の単一要素のサイズです。 *BufferLength*データが固定長のデータの場合、引数は無視されます。  
  
    -   *StrLen_or_IndPtr*長さ/インジケーター配列のアドレスです。  
  
 この情報を使用する方法の詳細については、このセクションの後半の「バッファー アドレス」を参照してください。 列方向のバインドの詳細については、次を参照してください。[列方向のバインド](../../../odbc/reference/develop-app/column-wise-binding.md)します。  
  
## <a name="row-wise-binding"></a>行方向のバインド  
 行方向のバインドでは、アプリケーションは、バインドするには、各列のデータと長さ/インジケーター バッファーに格納する構造体を定義します。  
  
 行方向のバインドを使用するには、アプリケーションは、次の手順を実行します。  
  
1.  データ (データと長さ/インジケーター バッファーを含む) の 1 つの行を格納する構造体を定義し、これらの構造体の配列を割り当てます。  
  
    > [!NOTE]  
    >  場合は、アプリケーションは、行方向のバインドを使用する場合に、記述子に直接書き込む、個別のフィールドの長さとインジケーター データを使用できます。  
  
2.  1 行のデータを格納する構造体のサイズまたは結果の列のバインド先のバッファーのインスタンスのサイズには、SQL_ATTR_ROW_BIND_TYPE ステートメント属性を設定します。 長さは、バインドされたすべての列および構造体またはバインドされた列のアドレスが指定した長さでインクリメントされた場合は、結果は次の行に同じ列の先頭にポイントを確認する、バッファーの埋め込み用の領域を含める必要があります。 使用する場合、 *sizeof* ANSI c 演算子は、この動作が保証されます。  
  
3.  呼び出し**SQLBindCol**にバインドするには、各列に対して次の引数で。  
  
    -   *TargetType*列にバインドするデータ バッファーのメンバーの種類です。  
  
    -   *TargetValuePtr*は配列の最初の要素のデータ バッファーのメンバーのアドレスです。  
  
    -   *BufferLength*データ バッファーのメンバーのサイズです。  
  
    -   *StrLen_or_IndPtr*はバインドされる長さ/インジケーターのメンバーのアドレスです。  
  
 この情報を使用する方法の詳細については、このセクションの後半の「バッファー アドレス」を参照してください。 列方向のバインドの詳細については、次を参照してください。[行方向のバインド](../../../odbc/reference/develop-app/row-wise-binding.md)します。  
  
## <a name="buffer-addresses"></a>バッファーのアドレス  
 *バッファーのアドレス*データまたは長さ/インジケーター バッファーの実際のアドレスです。 ドライバーは、(中に取得時間など) をバッファーに書き込む前にだけ、バッファーのアドレスを計算します。 指定されたアドレスを使用して、次の式から算出されます、 *TargetValuePtr*と*StrLen_or_IndPtr*引数、バインディングのオフセット、および行番号。  
  
 *アドレスをバインド* + *オフセットをバインド*+ ((*行数*- 1) x*要素のサイズ*)  
  
 数式の変数が定義されているように、次の表で説明します。  
  
|変数|説明|  
|--------------|-----------------|  
|*アドレスをバインドします。*|データのバッファーで指定したアドレス、 *TargetValuePtr*引数**SQLBindCol**します。<br /><br /> 長さ/インジケーター バッファーのアドレスが指定された、 *StrLen_or_IndPtr*引数**SQLBindCol**します。 詳細については、"記述子と SQLBindCol"セクションでは、「その他のコメント」を参照してください。<br /><br /> バインドされたアドレスが 0 の場合のデータ値が返されない場合でも、前の式で計算されたアドレスが 0 以外。|  
|*バインディングのオフセット*|行方向のバインドを使用する場合、SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性アドレスに格納されている値を指定します。<br /><br /> 列方向のバインドを使用する場合、または SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性の値が null ポインターの場合*バインド オフセット*は 0 です。|  
|*行番号*|1 から始まる行セットの行の数。 単一行のフェッチは、既定値は、これは 1 です。|  
|*要素のサイズ*|バインドの配列内の要素のサイズ。<br /><br /> これは、列方向のバインドを使用する場合**sizeof(SQLINTEGER)** 長さ/インジケーター バッファーの場合。 データのバッファーの値、 *BufferLength*引数**SQLBindCol**場合は、データ型が固定長データ型が変数の長さ、およびデータ型のサイズの場合。<br /><br /> 行方向のバインドを使用する場合の両方のデータと長さ/インジケーター バッファー SQL_ATTR_ROW_BIND_TYPE ステートメント属性の値になります。|  
  
## <a name="descriptors-and-sqlbindcol"></a>記述子および SQLBindCol  
 次のセクションで説明する方法**SQLBindCol**記述子と対話します。  
  
> [!CAUTION]  
>  呼び出す**SQLBindCol**の 1 つのステートメントの他のステートメントに影響することができます。 これには、ステートメントに関連付けられている ARD が明示的に割り当てられているし、他のステートメントに関連付けられてもときに発生します。 **SQLBindCol**記述子を変更します。 この記述子が関連付けられているすべてのステートメントに変更を適用します。 呼び出す前に必要な動作でない場合、アプリケーションが、他のステートメントからこの記述子の関連付けを解除する必要があります**SQLBindCol**します。  
  
## <a name="argument-mappings"></a>引数マッピング  
 概念的には、 **SQLBindCol**シーケンスでは、次の手順を実行します。  
  
1.  呼び出し**SQLGetStmtAttr** ARD ハンドルを取得します。  
  
2.  呼び出し**SQLGetDescField**この記述子の SQL_DESC_COUNT のフィールドを取得する場合の値、 *ColumnNumber* SQL_DESC_COUNT、呼び出しの引数を超える**SQLSetDescField**に SQL_DESC_COUNT の値を大きく*ColumnNumber*します。  
  
3.  呼び出し**SQLSetDescField** ARD の次のフィールドに値を割り当てるを複数回します。  
  
    -   SQL_DESC_TYPE、SQL_DESC_CONCISE_TYPE の値に設定*TargetType*ただし、場合*TargetType*は 1 つ SQL_DESC_TYPE を sql _、datetime または間隔のサブタイプの簡潔な識別子の設定、DATETIME または SQL_INTERVAL の場合、それぞれします。SQL_DESC_CONCISE_TYPE を簡潔な識別子に設定します。対応する datetime 間隔サブコードに SQL_DESC_DATETIME_INTERVAL_CODE を設定します。  
  
    -   SQL_DESC_LENGTH、SQL_DESC_PRECISION、SQL_DESC_SCALE、および、SQL_DESC_DATETIME_INTERVAL_PRECISION の 1 つ以上を設定に適した*TargetType*します。  
  
    -   SQL_DESC_OCTET_LENGTH フィールドの値に設定*BufferLength*します。  
  
    -   SQL_DESC_DATA_PTR フィールドの値に設定*ターゲット値*します。  
  
    -   SQL_DESC_INDICATOR_PTR フィールドの値に設定*StrLen_or_Ind*します。 (詳しくは、次の段落を参照してください)。  
  
    -   SQL_DESC_OCTET_LENGTH_PTR フィールドの値に設定*StrLen_or_Ind*します。 (詳しくは、次の段落を参照してください)。  
  
 変数を*StrLen_or_Ind*引数が参照するインジケーターと長さの両方の情報に使用します。 この変数に格納、フェッチには、列の null 値が検出されると、SQL_NULL_DATAそれ以外の場合、この変数にデータの長さを格納します。 として null ポインターを渡す*StrLen_or_Ind*フェッチで、null 値が含まれてし、SQL_NULL_DATA を返す方法がない場合、失敗、ですが、データの長さを返すからフェッチ操作を強めたりします。  
  
 場合に呼び出し**SQLBindCol**失敗、ARD で設定は、記述子フィールドの内容が定義されていませんし、ARD SQL_DESC_COUNT フィールドの値は変更されません。  
  
## <a name="implicit-resetting-of-count-field"></a>数のフィールドの暗黙の型をリセットします。  
 **SQLBindCol** SQL_DESC_COUNT の値に設定、 *ColumnNumber*この SQL_DESC_COUNT の値が増加する場合にのみ引数。 場合の値、 *TargetValuePtr*引数が null ポインターの値、 *ColumnNumber*引数は SQL_DESC_COUNT と等しく (つまり、バインドするときに最高の値をバインド解除列)、SQL_DESC_ しカウントは、最高の残りのバインドされた列の数に設定されます。  
  
## <a name="cautions-regarding-sqldefault"></a>SQL_DEFAULT に関する注意事項を確認します。  
 列のデータを正常に取得するには、アプリケーションはアプリケーション バッファー内のデータの開始位置と長さ正しく判断する必要があります。 アプリケーションを明示的に指定した場合*TargetType*アプリケーションの誤解を容易に検出します。 ただし、アプリケーションを指定すると、 *TargetType* SQL_DEFAULT の**SQLBindCol**から適用できます別のデータ型の列に 1 つの目的のいずれかの変更から、アプリケーションで、メタデータ、コードを別の列に適用しています。 ここでは、アプリケーションが常を特定できません開始またはフェッチされた列のデータの長さ。 これは、報告されないデータのエラーまたはメモリ違反が発生する可能性があります。  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションを実行、**選択**Id、名、および電話番号、顧客の結果セットが返される Customers テーブルでのステートメントが名前で並べ替えられます。 呼び出して**SQLBindCol**ローカル バッファーにデータの列をバインドします。 アプリケーションでデータの各行をフェッチする最後に、 **SQLFetch**各顧客の名前、ID、および電話番号を出力します。  
  
 コード例については、次を参照してください[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)、 [SQLColumns 関数](../../../odbc/reference/syntax/sqlcolumns-function.md)、 [SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)、および[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)。  
  
```cpp  
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
  
 参照してください、 [ODBC のサンプル プログラム](../../../odbc/reference/sample-odbc-program.md)します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列に関する情報を返す|[SQLDescribeCol 関数](../../../odbc/reference/syntax/sqldescribecol-function.md)|  
|データのブロックをフェッチしています。 または、結果をスクロールの設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|複数行のデータをフェッチしています|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|ステートメントで列のバッファーを解放します。|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|列のデータの一部またはすべてをフェッチしています|[SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
|結果の数を返すセットの列|[SQLNumResultCols 関数](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
