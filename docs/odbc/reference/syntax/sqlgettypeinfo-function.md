---
title: "SQLGetTypeInfo 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLGetTypeInfo
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLGetTypeInfo
helpviewer_keywords: SQLGetTypeInfo function [ODBC]
ms.assetid: bdedb044-8924-4ca4-85f3-8b37578e0257
caps.latest.revision: "21"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f3ab63b576841aef6dec553ecc0c07ccec010319
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="sqlgettypeinfo-function"></a>SQLGetTypeInfo 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLGetTypeInfo**データ ソースによってサポートされるデータ型に関する情報を返します。 ドライバーは、SQL 結果セットの形式で情報を返します。 データ型はデータ定義言語 (DDL) ステートメントで使用するためのものです。  
  
> [!IMPORTANT]  
>  アプリケーションの TYPE_NAME 列に返される型名を使用する必要があります、 **SQLGetTypeInfo**の結果セット**ALTER TABLE**と**CREATE TABLE**ステートメントです。 **SQLGetTypeInfo** DATA_TYPE 列の値が同じ 2 つ以上の行を返す可能性があります。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLGetTypeInfo(  
     SQLHSTMT      StatementHandle,  
     SQLSMALLINT   DataType);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]結果セットのステートメント ハンドルです。  
  
 *データ型*  
 [入力]SQL データ型です。 これは内の値のいずれかをする必要があります、 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)付録 d: データ型、またはドライバー固有の SQL データ型のセクションです。 SQL_ALL_TYPES では、すべてのデータ型に関する情報が返されることを指定します。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetTypeInfo** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* SQL の_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLGetTypeInfo**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S02|オプション値が変更されました|指定されたステートメント属性は、ような値が一時的に置き換えるための実装の動作条件のため無効でした。 (呼び出し**SQLGetStmtAttr**を一時的に置換された値を決定します)。代替値は有効、 *StatementHandle*カーソルが閉じられるまでです。 変更可能なステートメント属性は、: SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE、SQL_ATTR_KEYSET_SIZE、SQL_ATTR_MAX_LENGTH、SQL_ATTR_MAX_ROWS、SQL_ATTR_QUERY_TIMEOUT、および SQL_ATTR_SIMULATE_CURSOR です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|24000|カーソル状態が無効|カーソルが開いて、 *StatementHandle、*と**SQLFetch**または**SQLFetchScroll**が呼び出されました。 このエラーが返されます、ドライバー マネージャーによって**SQLFetch**または**SQLFetchScroll** 、SQL_NO_DATA が返されなかったと場合、ドライバーによって返される**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されました。<br /><br /> 結果セットがで開かれていた、 *StatementHandle*が**SQLFetch**または**SQLFetchScroll**が呼び出されていません。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックによりロールバックされました。|  
|40003|不明なステートメント入力候補|この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY004|無効な SQL データ型|引数が指定された値*DataType*が ODBC SQL データ型の有効な識別子でも、ドライバーでサポートされているドライバー固有のデータ型の識別子。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*関数が呼び出されたし、実行を完了する前に**SQLCancel**または**SQLCancelHandle**されました呼び出される、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、実行を完了する前に**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLGetTypeInfo**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースによっては、SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE ステートメント属性の現在の設定の組み合わせはサポートされていません。<br /><br /> SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されており、SQL_ATTR_CURSOR_TYPE ステートメント属性は、ドライバーがブックマークにできないカーソルの種類に設定されました。|  
|HYT00|タイムアウトが発生しました|クエリのタイムアウト時間は、データ ソースには、結果セットが返される前に期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtAttr**、SQL_ATTR_QUERY_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に対応するドライバー、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 **SQLGetTypeInfo**結果を順序付けに DATA_TYPE をしにどのデータ型が、対応する ODBC SQL データ型にマップして、標準的な結果セットとして返します。 データ ソースで定義されているデータ型は、ユーザー定義データ型よりも優先されます。 その結果、並べ替え順序は必ずしも整合性がありませんが、まず DATA_TYPE として一般化、TYPE_NAME、昇順のどちらを続けています。 たとえば、データ ソースに、カウンターは、自動インクリメントは、整数およびカウンターのデータ型が定義されていると、ユーザー定義データ型 WHOLENUM も定義されていること。 これらは、整数、WHOLENUM の順に返され、カウンター、WHOLENUM ODBC SQL データに最も近い型マッピング SQL_INTEGER、自動インクリメント データ型、中に、データ ソースでサポートされている場合でもためにもマップされない密接に ODBC SQL データ型。 この情報の使用方法については、次を参照してください。 [DDL ステートメント](../../../odbc/reference/develop-app/ddl-statements.md)です。  
  
 場合、 *DataType*引数は、ドライバーでサポートされている ODBC のバージョンの有効なデータ型を指定します、ドライバーでサポートされていない場合、空の結果セットが返されます。  
  
> [!NOTE]  
>  一般的な使用、引数、および ODBC カタログ関数の返されたデータの詳細については、次を参照してください。[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)です。  
  
 次の列は、ODBC 3 の名前変更されています。*x*です。 列名の変更では、列番号により、アプリケーション バインドのための下位互換性は影響しません。  
  
|ODBC 2.0 列|ODBC 3 です。*x*列|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|MONEY|FIXED_PREC_SCALE|  
|AUTO_INCREMENT|AUTO_UNIQUE_VALUE|  
  
 によって返される結果セットに次の列が追加されて**SQLGetTypeInfo** ODBC 3 *。x*:  
  
-   SQL_DATA_TYPE  
  
-   INTERVAL_PRECISION  
  
-   SQL_DATETIME_SUB  
  
-   NUM_PREC_RADIX  
  
 次の表には、結果セット内の列が一覧表示します。 ドライバーでは、列 19 (INTERVAL_PRECISION) を超える追加の列を定義できます。 アプリケーションでは、明示的な位置を表す序数を指定するのではなく、結果セットの末尾からカウント ダウンによって、ドライバー固有の列へのアクセスを得る必要があります。 詳細については、次を参照してください。[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)です。  
  
> [!NOTE]  
>  **SQLGetTypeInfo**すべてのデータ型を返さない可能性があります。 たとえば、ドライバーはユーザー定義データ型を返さない可能性があります。 アプリケーションは、によって返されるかどうかに関係なく、任意の有効なデータ型を使用できます**SQLGetTypeInfo**です。 によって返されるデータ型**SQLGetTypeInfo**は、データ ソースによってサポートされています。 データ定義言語 (DDL) ステートメントで使用するためのものです。 ドライバーは、によって返される型以外のデータ型を使用してデータを結果セットを返すことができます**SQLGetTypeInfo**です。 カタログ関数の結果セットを作成するで、ドライバーは、データ ソースによってサポートされていないデータ型を使用する可能性があります。  
  
|列名|列<br /><br /> number|データ型|コメント|  
|-----------------|-----------------------|---------------|--------------|  
|TYPE_NAME (ODBC 2.0)|1|NULL でない Varchar|データ ソースに依存するデータ型名です。たとえば、"CHAR()"、"VARCHAR()"、"MONEY"、"LONG VARBINARY"、または「CHAR () FOR BIT DATA」です。 アプリケーションでこの名前を使用する必要があります**CREATE TABLE**と**ALTER TABLE**ステートメントです。|  
|DATA_TYPE (ODBC 2.0)|2|Smallint (NULL 以外)|SQL データ型です。 これには、ODBC SQL データ型またはドライバー固有の SQL データ型を指定できます。 Datetime 型または interval データ型は、この列は、簡潔なデータ型 (SQL_TYPE_TIME SQL_INTERVAL_YEAR_TO_MONTH など) を返します。 有効な ODBC SQL データ型の一覧は、次を参照してください。 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)付録 d: データ型にします。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。|  
|COLUMN_SIZE (ODBC 2.0)|3|Integer|このデータ型のサーバーでサポートされている列の最大サイズ。 数値データは、これは、最大有効桁数です。 文字列データの場合は、これは、文字の長さです。 Datetime データ型では、これは (秒部分の最大有効桁数を想定) の文字列形式の文字の長さです。 NULL が返されますのデータ型列のサイズは適用されません。 Interval データ型では、これは、文字形式のリテラルの間隔の文字数 (先頭の有効桁数です。 間隔の定義に従ってを参照してください。 [Interval データ型の長さ](../../../odbc/reference/appendixes/interval-data-type-length.md)付録 d: データ型)。<br /><br /> 列のサイズの詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。|  
|LITERAL_PREFIX (ODBC 2.0)|4|Varchar|文字または文字列リテラルのプレフィックスを使用します。たとえば、単一引用符 (') 文字データ型またはバイナリ データ型です。 0 xNULL を返しますのデータ型のリテラル プレフィックスは適用されません。|  
|LITERAL_SUFFIX (ODBC 2.0)|5|Varchar|文字または文字列リテラルを終了するために使用たとえば、文字データ型の単一の引用符 (')NULL を返しますのデータ型のリテラル サフィックスでは適用されません。|  
|CREATE_PARAMS (ODBC 2.0)|6|Varchar|キーワード、TYPE_NAME フィールドに返される名前を使用する場合、かっこ内にアプリケーションが指定できる各パラメーターに対応する、コンマ区切りの一覧です。 一覧のキーワードは、次のいずれかを指定できます。 長さ、有効桁数または小数点以下桁数です。 構文が使用することが必要である順序で表示されます。 たとえば、CREATE_PARAMS は 10 進数には「有効桁数、小数点以下桁数」です。「長さ」と等しくなる varchar CREATE_PARAMS 定義については、データ型です。 パラメーターがない場合は、NULL が返されます。たとえば、整数値です。<br /><br /> ドライバーが使用されている国/地域の言語で CREATE_PARAMS テキストを提供します。|  
|NULL 許容型 (ODBC 2.0)|7|Smallint (NULL 以外)|かどうか、データ型は、NULL 値を受け付けます。<br /><br /> SQL_NO_NULLS データ型を受け入れない場合は NULL 値です。<br /><br /> データ型は、NULL 値を受け入れる場合 SQL_NULLABLE です。<br /><br /> SQL_NULLABLE_UNKNOWN 列が NULL 値を受け入れるかどうかが不明の場合。|  
|CASE_SENSITIVE (ODBC 2.0)|8|Smallint (NULL 以外)|文字データを入力するかどうかは照合順序との比較で大文字小文字を区別します。<br /><br /> データ型は文字データ型であり、大文字小文字を区別する場合は SQL_TRUE にします。<br /><br /> SQL_FALSE データ型が文字データ型ではない、または小文字は区別されません。|  
|検索可能な (ODBC 2.0)|9|Smallint (NULL 以外)|データ型の使用方法、**場所**句。<br /><br /> SQL_PRED_NONE で列を使用できない場合、**場所**句。 (これは ODBC 2 で SQL_UNSEARCHABLE 値と同じです。*x*)。<br /><br /> SQL_PRED_CHAR では、列を使用する場合、**場所**句でのみ、**と同様に**述語。 (これは ODBC 2 で SQL_LIKE_ONLY 値と同じです。*x*)。<br /><br /> SQL_PRED_BASIC では、列を使用する場合、**場所**を除くすべての比較演算子を含む句**など**(比較、定量化された比較は、 **BETWEEN**、 **DISTINCT**、 **IN**、**一致**、および**UNIQUE**)。 (これは ODBC 2 で SQL_ALL_EXCEPT_LIKE 値と同じです。*x*)。<br /><br /> SQL_SEARCHABLE では、列を使用する場合、**場所**任意の比較演算子を含む句。|  
|UNSIGNED_ATTRIBUTE (ODBC 2.0)|10|Smallint|データを入力するかどうかが署名されていません。<br /><br /> データ型が署名されていない場合は SQL_TRUE します。<br /><br /> データ型が署名されている場合は SQL_FALSE にします。<br /><br /> 属性は、データ型に適用されませんまたはデータ型が数値でない場合は、NULL が返されます。|  
|FIXED_PREC_SCALE (ODBC 2.0)|11|Smallint (NULL 以外)|データ型が事前に定義されているかどうかには、有効桁数と小数点 (であるデータ ソース固有)、money データ型などが修正されました。<br /><br /> SQL_TRUE に事前定義された場合は、有効桁数と小数点以下桁数を固定します。<br /><br /> 定義済みの固定有効桁数と小数点以下桁数がない場合は SQL_FALSE にします。|  
|AUTO_UNIQUE_VALUE (ODBC 2.0)|12|Smallint|データ型が自動増分されるかどうか。<br /><br /> データ型が自動増分される場合は SQL_TRUE します。<br /><br /> データ型が自動増分ではない場合は SQL_FALSE にします。<br /><br /> 属性は、データ型に適用されませんまたはデータ型が数値でない場合は、NULL が返されます。<br /><br /> アプリケーションでは、この属性を持つ列に値を挿入することができますが、通常、列の値を更新することはできません。<br /><br /> 自動インクリメント列に挿入が行われると、挿入時に、一意の値が列に挿入されます。 増分値は定義されていませんがデータ ソース固有です。 アプリケーションはする特定の値によって、特定の時点または増分で自動インクリメント列が開始されると想定する必要があります。|  
|LOCAL_TYPE_NAME (ODBC 2.0)|13|Varchar|データ型のデータ ソースに依存する名前のローカライズされたバージョンです。 ローカライズされた名前がそのデータ ソースによってサポートされない場合は NULL が返されます。 この名前は表示のみ、ダイアログ ボックスのようにこのようなものです。|  
|MINIMUM_SCALE (ODBC 2.0)|14|Smallint|データ ソースでのデータ型の最小小数点以下桁数です。 データ型の小数点以下桁数が固定されている場合は、MINIMUM_SCALE 列および MAXIMUM_SCALE 列の両方にこの値が入ります。 たとえば、sql_type_timestamp 型の列では、秒の小数部の固定のスケールがあります。 小数点以下桁数が適用されない場合は NULL が返されます。 詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。|  
|MAXIMUM_SCALE (ODBC 2.0)|15|Smallint|データ ソースでのデータ型の最大の小数点以下桁数です。 小数点以下桁数が適用されない場合は NULL が返されます。 最大の小数点以下桁数が定義されていないとは別に、データ ソースの最大有効桁数と同じであると定義されている場合は、この列には、COLUMN_SIZE 列と同じ値が含まれています。 詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。|  
|SQL_DATA_TYPE (ODBC 3.0)|16|NULL でない Smallint|記述子の SQL_DESC_TYPE フィールドには、SQL データ型の値が表示されます。 この列は、間隔と datetime データ型を除く、DATA_TYPE 列と同じです。<br /><br /> 間隔および datetime データ型の SQL_INTERVAL または SQL_DATETIME、結果セットの SQL_DATA_TYPE フィールドが返されます、SQL_DATETIME_SUB フィールドには、特定の間隔または datetime データ型のサブコードが返されます。 (を参照してください[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md))。|  
|SQL_DATETIME_SUB (ODBC 3.0)|17|Smallint|SQL_DATA_TYPE の値が SQL_DATETIME または SQL_INTERVAL の場合は、この列には、datetime/間隔サブコードが含まれています。 Datetime と間隔以外のデータ型、このフィールドは NULL です。<br /><br /> 間隔型または datetime データ型に対して、SQL_INTERVAL または SQL_DATETIME、結果セットの SQL_DATA_TYPE フィールドが返されます、SQL_DATETIME_SUB フィールドには、特定の間隔または datetime データ型のサブコードが返されます。 (を参照してください[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md))。|  
|NUM_PREC_RADIX (ODBC 3.0)|18|Integer|データ型が概数型の場合は、この列には、COLUMN_SIZE がビット数を指定することを示すために 2 という値が含まれています。 真数型で、この列には、COLUMN_SIZE が 10 進数字の数を指定することを示すために 10 の値が含まれています。 それ以外は、この列は NULL です。|  
|INTERVAL_PRECISION (ODBC 3.0)|19|Smallint|データ型が interval データ型の場合は、この列は、間隔の主要な有効桁数の値を含みます。 (を参照してください[Interval データ型の有効桁数](../../../odbc/reference/appendixes/interval-data-type-precision.md)付録 d: データ型にします)。それ以外は、この列は NULL です。|  
  
 属性情報は、データ型にまたは、結果セット内の特定の列に適用できます。 **SQLGetTypeInfo**データ型に関連付けられている属性に関する情報を返します**SQLColAttribute**結果セット内の列に関連付けられている属性に関する情報を返します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLColAttribute 関数](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|1 つの行または順方向専用の方向にデータのブロックをフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|ドライバーまたはデータ ソースに関する情報を返す|[SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
