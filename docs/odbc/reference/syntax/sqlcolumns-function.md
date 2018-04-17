---
title: SQLColumns 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColumns
helpviewer_keywords:
- SQLColumns function [ODBC]
ms.assetid: 4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0
caps.latest.revision: 28
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 86cf72d9a0f061b4cdec3416df315c1e8f9fe91b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sqlcolumns-function"></a>SQLColumns 関数
**準拠**  
 バージョンが導入されています ODBC 1.0 標準への準拠: グループを開く。  
  
 **概要**  
 **SQLColumns**指定したテーブルに列名の一覧を返します。 ドライバーは結果セットとして指定したこの情報を返します*StatementHandle*です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLColumns(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      ColumnName,  
     SQLSMALLINT    NameLength4);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *カタログ名*  
 [入力]カタログの名前。 ドライバーは、いくつかのテーブルは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のカタログをサポートしている場合 ("") これらのテーブルのカタログがないことを示します。 *CatalogName*検索パターンに文字列を含めることはできません。  
  
> [!NOTE]  
>  SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*CatalogName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *CatalogName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。 詳細については、次を参照してください。[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)です。  
  
 *NameLength1*  
 [入力]文字の長さ **CatalogName*です。  
  
 *スキーマ名*  
 [入力]スキーマ名の文字列検索パターン。 ドライバーは、いくつかのテーブルは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のスキーマをサポートしている場合 ("") これらのテーブルのスキーマがないことを示します。  
  
> [!NOTE]  
>  SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*SchemaName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *SchemaName*パターン引数の値は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength2*  
 [入力]文字の長さ **SchemaName*です。  
  
 *TableName*  
 [入力]テーブル名の文字列の検索パターン。  
  
> [!NOTE]  
>  SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*TableName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *TableName*パターン引数の値は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength3*  
 [入力]文字の長さ **TableName*です。  
  
 *[ColumnName]*  
 [入力]列名の文字列の検索パターン。  
  
> [!NOTE]  
>  SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*ColumnName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *ColumnName*パターン引数の値は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength4*  
 [入力]文字の長さ **ColumnName*です。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLColumns** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLColumns**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|24000|カーソル状態が無効|カーソルが開いて、 *StatementHandle*、および**SQLFetch**または**SQLFetchScroll**が呼び出されました。 このエラーが返されます、ドライバー マネージャーによって**SQLFetch**または**SQLFetchScroll** 、SQL_NO_DATA が返されなかったと場合、ドライバーによって返される**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されました。<br /><br /> カーソルが開いて、 *StatementHandle*が**SQLFetch**または**SQLFetchScroll**が呼び出されていません。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックが原因ロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY009|無効な null ポインターの使用|SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定された、 *CatalogName*引数が null ポインターの場合と、SQL_CATALOG_NAME*情報の種類*カタログ名を返しますがサポートされています。<br /><br /> (DM) SQL_ATTR_METADATA_ID ステートメント属性が SQL_TRUE に設定、および*SchemaName*、 *TableName*、または*ColumnName*引数が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLColumns**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) 名長の引数のいずれかの値が 0 より小さい値は SQL_NTS に等しくありません。|  
|||名前の長さの引数のいずれかの値には、対応するカタログまたは名の最大長の値を超えています。 各カタログまたは名の最大長を呼び出すことによって取得できます**SQLGetInfo**で、*情報の種類*値。 (「コメント」を参照してください)|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|カタログ名が指定あり、ドライバーまたはデータ ソースがカタログをサポートしていません。<br /><br /> スキーマ名が指定された、およびドライバーまたはデータ ソースがスキーマをサポートしていません。<br /><br /> スキーマ名、テーブル名または列名の文字列の検索パターンが指定され、データ ソースがこれらの引数の 1 つ以上の検索パターンをサポートしていません。<br /><br /> ドライバーまたはデータ ソースによっては、SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE ステートメント属性の現在の設定の組み合わせはサポートされていません。<br /><br /> SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されており、SQL_ATTR_CURSOR_TYPE ステートメント属性は、ドライバーがブックマークにできないカーソルの種類に設定されました。|  
|HYT00|タイムアウトが発生しました|クエリのタイムアウト時間は、データ ソースには、結果セットが返される前に期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtAttr**、SQL_ATTR_QUERY_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 この関数は用いステートメントを実行する前にデータ ソースのカタログからテーブルまたはテーブルの列に関する情報を取得します。 **SQLColumns**によって返される項目のすべての種類のデータを取得するために使用できる**SQLTables**です。 ベース テーブルだけでなくこの可能性があります (ただしに限定されません) のビュー、シノニム、システム テーブル、およびなどです。 一方、関数は、 **SQLColAttribute**と**SQLDescribeCol**結果セットと、関数内の列について説明する**SQLNumResultCols**の数を返します結果セット内の列。 詳細については、次を参照してください。[カタログ データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)です。  
  
> [!NOTE]  
>  一般的な使用、引数、および ODBC カタログ関数の返されたデータの詳細については、次を参照してください。[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)です。  
  
 **SQLColumns** TABLE_CAT、TABLE_SCHEM、TABLE_NAME、および ORDINAL_POSITION 並べ、標準的な結果セットとして結果を返します。  
  
> [!NOTE]  
>  ときに、アプリケーションは、ODBC 2 で機能します。*x*ドライバー、ORDINAL_POSITION 列は返されません、結果セットにします。 結果として、ODBC 2 を使用する場合。*x*ドライバー、によって返される列リスト内の列の順序**SQLColumns**必ずしも列の順序と同じ場合は返されません、アプリケーションは、すべての SELECT ステートメントを実行そのテーブルの列。  
  
> [!NOTE]  
>  **SQLColumns**すべての列を返さない可能性があります。 たとえば、ドライバーは、Oracle ROWID などの擬似列に関する情報を返さない可能性があります。 によって返されるかどうか、アプリケーションは、任意の有効な列を使用できます**SQLColumns**です。  
>   
>  一部の列によって返される**SQLStatistics**では返されません**SQLColumns**です。 たとえば、 **SQLColumns**式またはフィルター、給与 + 利点や部門などを介して作成されたインデックスで列を返さない 0012 を = です。  
  
 Varchar 型の列の長さは、テーブルには表示されません。実際の長さは、データ ソースに依存します。 TABLE_CAT、TABLE_SCHEM、TABLE_NAME、COLUMN_NAME の各列の実際の長さを決定するには、アプリケーションが呼び出すことができます**SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、SQL_MAX_TABLE_NAME_LEN、および SQL_MAX_COLUMN_NAME_LEN オプション。  
  
 次の列は、ODBC 3 の名前変更されています。*x*です。 列名の変更では、列番号により、アプリケーション バインドのための下位互換性は影響しません。  
  
|ODBC 2.0 列|ODBC 3 です。*x*列|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 によって返される結果セットに次の列が追加されて**SQLColumns** ODBC 3 *。x*:  
  
|||  
|-|-|  
|CHAR_OCTET_LENGTH|ORDINAL_POSITION|  
|COLUMN_DEF|SQL_DATA_TYPE|  
|IS_NULLABLE|SQL_DATETIME_SUB|  
  
 次の表には、結果セット内の列が一覧表示します。 ドライバーでは、18 (によって IS_NULLABLE) の列を超える追加の列を定義できます。 アプリケーションは、結果の明示的な位置を表す序数を指定する代わりにセットの末尾からカウント ダウンしてドライバー固有の列へのアクセスを得る必要があります。 詳細については、次を参照してください。[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)です。  
  
|列名|列<br /><br /> number|データ型|コメント|  
|-----------------|-----------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|カタログ名です。データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどにいくつかのテーブルが、他のカタログをサポートする場合 ("")、それらのテーブルのカタログがないです。|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|スキーマ名です。データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどにいくつかのテーブルが、他のスキーマをサポートする場合 ("")、それらのテーブルのスキーマがないです。|  
|TABLE_NAME (ODBC 1.0)|3|NULL でない Varchar|テーブル名です。|  
|COLUMN_NAME (ODBC 1.0)|4|NULL でない Varchar|列名 ドライバーでは、名前がない列の空の文字列を返します。|  
|DATA_TYPE (ODBC 1.0)|5|Smallint (NULL 以外)|SQL データ型です。 これには、ODBC SQL データ型またはドライバー固有の SQL データ型を指定できます。 Datetime および間隔のデータ型については、この列は、簡潔なデータ型 (SQL_TYPE_DATE SQL_DATETIME または SQL_INTERVAL など nonconcise データ型ではなく、SQL_INTERVAL_YEAR_TO_MONTH など) を返します。 有効な ODBC SQL データ型の一覧は、次を参照してください。 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)付録 d: データ型にします。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。<br /><br /> ODBC 3 に対して返されたデータ型。*x*および ODBC 2 *。x*アプリケーションが異なる場合があります。 詳細については、次を参照してください。[旧バージョンとの互換性と標準の順守](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)です。|  
|TYPE_NAME (ODBC 1.0)|6|NULL でない Varchar|データ ソースに依存するデータ型の名前です。たとえば、"CHAR"、"VARCHAR"、"MONEY"、"LONG VARBINAR"または「CHAR () FOR BIT DATA」です。|  
|COLUMN_SIZE (ODBC 1.0)|7|Integer|DATA_TYPE が SQL_CHAR、SQL_VARCHAR またはの場合は、この列には、列の文字で最大の長さが含まれています。 Datetime データ型の文字に変換されるときに、値を表示するために必要な文字の合計数です。 数値データ型、これは総桁数またはの列で、許可されているビットの合計数のいずれかに従って NUM_PREC_RADIX 列です。 Interval データ型では、これは、文字形式のリテラルの間隔の文字数 (有効桁数を先頭期間によって定義されたを参照してください。 [Interval データ型の長さ](../../../odbc/reference/appendixes/interval-data-type-length.md)付録 d: データ型)。 詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。|  
|BUFFER_LENGTH 列 (ODBC 1.0)|8|Integer|SQL_C_DEFAULT が指定されている場合、データの長さ (バイト単位) は、SQLGetData、SQLFetch、または SQLFetchScroll 操作で転送されます。 数値データは、このサイズは、データ ソースに格納されているデータのサイズを異なる場合があります。 この値は、COLUMN_SIZE 列の文字データに対して異なる場合があります。 長さの詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。|  
|DECIMAL_DIGITS (ODBC 1.0)|9|Smallint|有効桁数、小数点の右側の合計数。 SQL_TYPE_TIME および sql_type_timestamp 型の場合は、この列には、秒の小数部コンポーネント内の数字の数が含まれています。 他のデータ型では、これは、データ ソース上の列の 10 進数字です。 間隔のデータの種類の時間コンポーネントが含まれている、この列には、(秒の小数部) の小数点の右側にある数字の数が含まれています。 時刻部分を含まない interval データ型、この列は 0 です。 小数点以下桁数の詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。 NULL が返されますのデータ型 DECIMAL_DIGITS は適用されません。|  
|NUM_PREC_RADIX (ODBC 1.0)|10|Smallint|数値データ型の 10 または 2 のいずれか。 10 の場合は、COLUMN_SIZE と DECIMAL_DIGITS の値は、列に格納できる 10 進数字の数を提供します。 たとえば、DECIMAL(12,5) 列は 10、12、COLUMN_SIZE と 5; DECIMAL_DIGITS の NUM_PREC_RADIX を返しますFLOAT 列では、10、15、COLUMN_SIZE と NULL の DECIMAL_DIGITS の NUM_PREC_RADIX を返す可能性があります。<br /><br /> 2 の場合は、COLUMN_SIZE と DECIMAL_DIGITS の値は、列に許容されるビット数を提供します。 たとえば、FLOAT 列では、2 の 53、COLUMN_SIZE と NULL の DECIMAL_DIGITS の基数を返すでした。<br /><br /> NULL が返されますのデータ型 NUM_PREC_RADIX は適用されません。|  
|NULL 許容型 (ODBC 1.0)|11|Smallint (NULL 以外)|SQL_NO_NULLS 列が含まれていない場合は NULL 値です。<br /><br /> 列が NULL 値を受け入れる場合 SQL_NULLABLE です。<br /><br /> SQL_NULLABLE_UNKNOWN 列が NULL 値を受け入れるかどうかが不明の場合。<br /><br /> この列に返される値は、によって IS_NULLABLE 列に返される値によって異なります。 列が null 値を受け入れることができますが、列が null 値を受け付けないことで示すことはできませんの確実性で null 許容の列を示します。 列が null 値を受け入れることはできませんが、列が null 値を受け入れることを明確に示すことはできませんの確実性でによって IS_NULLABLE 列を示します。|  
|「解説」(ODBC 1.0)|12|Varchar|列の説明です。|  
|COLUMN_DEF (ODBC 3.0)|13|Varchar|列の既定値です。 引用符で囲まれている場合、この列の値を文字列として解釈する必要があります。<br /><br /> NULL は、既定値として指定されている場合、この列は NULL の場合、引用符で囲まれていないという単語はします。 既定値は、切り捨てることがなく表現できない、この列は単一引用符に囲まれていないが切り捨てられてを含みます。 既定値が指定されていない場合、この列は NULL を使用します。<br /><br /> COLUMN_DEF の値は、値が切り捨てられてが含まれている場合を除く、新しい列定義の生成に使用できます。|  
|SQL_DATA_TYPE (ODBC 3.0)|14|Smallint (NULL 以外)|SQL データ型、IRD の SQL_DESC_TYPE レコード フィールドに表示されます。 これには、ODBC SQL データ型またはドライバー固有の SQL データ型を指定できます。 この列は、datetime および間隔のデータ型を除き、DATA_TYPE 列と同じです。 この列は、interval データ型と datetime (SQL_TYPE_DATE SQL_INTERVAL_YEAR_TO_MONTH など) の簡潔なデータ型ではなく、nonconcise などのデータ型 (SQL_DATETIME または SQL_INTERVAL) を返します。 この列を返す場合 SQL_DATETIME または SQL_INTERVAL、SQL_DATETIME_SUB 列から特定のデータ型を決定できます。 有効な ODBC SQL データ型の一覧は、次を参照してください。 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)付録 d: データ型にします。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。<br /><br /> ODBC 3 に対して返されたデータ型。*x*および ODBC 2 *。x*アプリケーションが異なる場合があります。 詳細については、次を参照してください。[旧バージョンとの互換性と標準の順守](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)です。|  
|SQL_DATETIME_SUB (ODBC 3.0)|15|Smallint|Datetime および interval データ型のサブタイプ コードです。 その他のデータ型の場合は、NULL が返されます。 Datetime および間隔のサブコードの詳細についてを参照してください"SQL_DESC_DATETIME_INTERVAL_CODE" [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)です。|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|16|Integer|文字またはバイナリ データの最大長 (バイト単位) は、列を入力します。 他のすべてのデータ型の場合、この列は NULL を返します。|  
|ORDINAL_POSITION (ODBC 3.0)|17|Integer (NULL 以外)|テーブル内の列の序数位置です。 テーブル内の最初の列は数値 1 です。|  
|によって IS_NULLABLE (ODBC 3.0)|18|Varchar|"NO"、列に null 値が含まれていない場合。<br /><br /> "YES"場合は、列に Null を含む可能性があります。<br /><br /> NULL が許可されているかどうかがわからない列は、長さ 0 の文字列を返します。<br /><br /> NULL 値の許容属性の検査は ISO の規則に従います。 ISO SQL に準拠した DBMS では、空の文字列を返すことはできません。<br /><br /> この列に返される値は、null 許容の列に対して返される値によって異なります。 (詳しくは、null 許容の列の説明を参照してください)。|  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションは、によって返される結果セットのバッファーを宣言しています**SQLColumns**です。 呼び出す**SQLColumns**従業員テーブル内の各列を説明する結果セットを返します。 呼び出して**SQLBindCol**に結果セットをバッファーに列をバインドします。 アプリケーションが最後を使用してデータの各行をフェッチ**SQLFetch**しそれを処理します。  
  
```  
// SQLColumns_Function.cpp  
// compile with: ODBC32.lib  
#include <windows.h>  
#include <sqlext.h>  
#define STR_LEN 128 + 1  
#define REM_LEN 254 + 1  
  
// Declare buffers for result set data  
SQLCHAR szSchema[STR_LEN];  
SQLCHAR szCatalog[STR_LEN];  
SQLCHAR szColumnName[STR_LEN];  
SQLCHAR szTableName[STR_LEN];  
SQLCHAR szTypeName[STR_LEN];  
SQLCHAR szRemarks[REM_LEN];  
SQLCHAR szColumnDefault[STR_LEN];  
SQLCHAR szIsNullable[STR_LEN];  
  
SQLINTEGER ColumnSize;  
SQLINTEGER BufferLength;  
SQLINTEGER CharOctetLength;  
SQLINTEGER OrdinalPosition;  
  
SQLSMALLINT DataType;  
SQLSMALLINT DecimalDigits;  
SQLSMALLINT NumPrecRadix;  
SQLSMALLINT Nullable;  
SQLSMALLINT SQLDataType;  
SQLSMALLINT DatetimeSubtypeCode;  
  
SQLHSTMT hstmt = NULL;  
  
// Declare buffers for bytes available to return  
SQLINTEGER cbCatalog;  
SQLINTEGER cbSchema;  
SQLINTEGER cbTableName;  
SQLINTEGER cbColumnName;  
SQLINTEGER cbDataType;  
SQLINTEGER cbTypeName;  
SQLINTEGER cbColumnSize;  
SQLLEN cbBufferLength;  
SQLINTEGER cbDecimalDigits;  
SQLINTEGER cbNumPrecRadix;  
SQLINTEGER cbNullable;  
SQLINTEGER cbRemarks;  
SQLINTEGER cbColumnDefault;  
SQLINTEGER cbSQLDataType;  
SQLINTEGER cbDatetimeSubtypeCode;  
SQLINTEGER cbCharOctetLength;  
SQLINTEGER cbOrdinalPosition;  
SQLINTEGER cbIsNullable;  
  
int main() {  
   SQLHENV henv;  
   SQLHDBC hdbc;  
   SQLHSTMT hstmt = 0;  
   SQLRETURN retcode;  
  
   retcode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER*)SQL_OV_ODBC3, 0);   
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);   
   retcode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)5, 0);  
   retcode = SQLConnect(hdbc, (SQLCHAR*) "Northwind", SQL_NTS, (SQLCHAR*) NULL, 0, NULL, 0);  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   retcode = SQLColumns(hstmt, NULL, 0, NULL, 0, (SQLCHAR*)"CUSTOMERS", SQL_NTS, NULL, 0);  
  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO) {  
      // Bind columns in result set to buffers  
      SQLBindCol(hstmt, 1, SQL_C_CHAR, szCatalog, STR_LEN,&cbCatalog);  
      SQLBindCol(hstmt, 2, SQL_C_CHAR, szSchema, STR_LEN, &cbSchema);  
      SQLBindCol(hstmt, 3, SQL_C_CHAR, szTableName, STR_LEN,&cbTableName);  
      SQLBindCol(hstmt, 4, SQL_C_CHAR, szColumnName, STR_LEN, &cbColumnName);  
      SQLBindCol(hstmt, 5, SQL_C_SSHORT, &DataType, 0, &cbDataType);  
      SQLBindCol(hstmt, 6, SQL_C_CHAR, szTypeName, STR_LEN, &cbTypeName);  
      SQLBindCol(hstmt, 7, SQL_C_SLONG, &ColumnSize, 0, &cbColumnSize);  
      SQLBindCol(hstmt, 8, SQL_C_SLONG, &BufferLength, 0, &cbBufferLength);  
      SQLBindCol(hstmt, 9, SQL_C_SSHORT, &DecimalDigits, 0, &cbDecimalDigits);  
      SQLBindCol(hstmt, 10, SQL_C_SSHORT, &NumPrecRadix, 0, &cbNumPrecRadix);  
      SQLBindCol(hstmt, 11, SQL_C_SSHORT, &Nullable, 0, &cbNullable);  
      SQLBindCol(hstmt, 12, SQL_C_CHAR, szRemarks, REM_LEN, &cbRemarks);  
      SQLBindCol(hstmt, 13, SQL_C_CHAR, szColumnDefault, STR_LEN, &cbColumnDefault);  
      SQLBindCol(hstmt, 14, SQL_C_SSHORT, &SQLDataType, 0, &cbSQLDataType);  
      SQLBindCol(hstmt, 15, SQL_C_SSHORT, &DatetimeSubtypeCode, 0, &cbDatetimeSubtypeCode);  
      SQLBindCol(hstmt, 16, SQL_C_SLONG, &CharOctetLength, 0, &cbCharOctetLength);  
      SQLBindCol(hstmt, 17, SQL_C_SLONG, &OrdinalPosition, 0, &cbOrdinalPosition);  
      SQLBindCol(hstmt, 18, SQL_C_CHAR, szIsNullable, STR_LEN, &cbIsNullable);  
  
      while (SQL_SUCCESS == retcode) {  
         retcode = SQLFetch(hstmt);  
         /*  
         if (retcode == SQL_ERROR || retcode == SQL_SUCCESS_WITH_INFO)  
            0;   // show_error();  
         if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
            0;   // Process fetched data  
         else  
            break;  
        */  
      }  
   }  
}  
```  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|列または列に対する権限を返す|[SQLColumnPrivileges 関数](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|複数行のデータのフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|行を一意に識別する列またはトランザクションが自動的に更新された列を返す|[SQLSpecialColumns 関数](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|テーブルの統計情報とインデックスを返す|[SQLStatistics 関数](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|データ ソース内のテーブルの一覧を返す|[SQLTables 関数](../../../odbc/reference/syntax/sqltables-function.md)|  
|テーブルまたはテーブルに対する権限を返す|[SQLTablePrivileges 関数](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
