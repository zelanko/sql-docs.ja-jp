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
- SQLProcedureColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLProcedureColumns
helpviewer_keywords:
- SQLProcedureColumns function [ODBC]
ms.assetid: 4ca37b28-a6df-465b-8988-d422d37fc025
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d81e44b116ed6f26319d31430999a61a8a17f21
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306853"
---
# <a name="sqlprocedurecolumns-function"></a>SQLProcedureColumns 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: ODBC  
  
 **まとめ**  
 **SQLProcedureColumns は**、入力パラメーターと出力パラメーターの一覧と、指定されたプロシージャの結果セットを構成する列を返します。 ドライバーは、指定されたステートメントの結果セットとして情報を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLProcedureColumns(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     ProcName,  
     SQLSMALLINT   NameLength3,  
     SQLCHAR *     ColumnName,  
     SQLSMALLINT   NameLength4);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *カタログ名*  
 [入力]プロシージャ カタログ名。 ドライバーが異なる DBMS からデータを取得する場合など、一部のプロシージャのカタログをサポートしている場合、空の文字列 (") は、カタログを持たないプロシージャを表します。 *カタログ名に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、CatalogName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合 *、CatalogName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。 詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。  
  
 *NameLength1*  
 [入力]* カタログ*名*の文字での長さ。  
  
 *Schemaname*  
 [入力]プロシージャ スキーマ名の文字列検索パターン。 ドライバーが異なる DBMS からデータを取得する場合など、一部のプロシージャのスキーマをサポートしているドライバーの場合は、空の文字列 (") は、スキーマを持たないプロシージャを表します。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、SchemaName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合、*スキーマ名*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 2*  
 [入力]**スキーマ名*の文字での長さ。  
  
 *プロク名*  
 [入力]プロシージャ名の文字列検索パターン。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、ProcName*は識別子として扱われ、その大文字と小文字は意味がありません。 SQL_FALSE場合 *、ProcName*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 3*  
 [入力]* の文字での長*さ*です。  
  
 *[ColumnName]*  
 [入力]列名の文字列検索パターン。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、ColumnName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合、*列名*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ4*  
 [入力]**列名*の文字での長さ。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLProcedureColumns が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLProcedureColumns によって**一般的に返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*でカーソルが開かれていたし **、SQL フェッチ**または SQL**フェッチスクロール**が呼び出されました。 このエラーは、ドライバー マネージャーが返す SQLFetch または**SQLFetchScrollSQL_NO_DATA**返されていない場合、ドライバー ドライバー マネージャーが返す **、SQL_NO_DATA****返された**場合は、ドライバーによって返されます。 **SQLFetch**<br /><br /> *ステートメント ハンドル*でカーソルが開かれていたが **、SQLFetch**または**SQLFetchScroll が**呼び出されていませんでした。|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 SQLError によって返**SQLError**されるエラー メッセージ*は、メッセージ テキスト バッファーにエラーとその原因を記述\** します。|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、*ステートメント ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、関数は*ステートメント ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY009|無効な null ポインターの使用|SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、*引数 CatalogName*が null ポインターであり、SQL_CATALOG_NAME *InfoType*はカタログ名がサポートされていることを返します。<br /><br /> (DM) SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、引数*のスキーマ名*、*プロシージャ名*、*または列名*が null ポインターでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この aynschronous 関数は、SQLProcedureColumns 関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY090|無効な文字列またはバッファ長|(DM) 名前長引数の 1 つの値が 0 より小さいが、SQL_NTSと等しくない。<br /><br /> 名前長引数の 1 つの値が、対応するカタログ、スキーマ、プロシージャー、または列名の最大長の値を超えました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|プロシージャ カタログが指定され、ドライバまたはデータ ソースがカタログをサポートしていません。<br /><br /> プロシージャ スキーマが指定され、ドライバまたはデータ ソースがスキーマをサポートしていません。<br /><br /> プロシージャ スキーマ、プロシージャ名、または列名に文字列検索パターンが指定されていますが、データ ソースは、これらの引数の 1 つ以上の検索パターンをサポートしていません。<br /><br /> SQL_ATTR_CONCURRENCYの現在の設定とSQL_ATTR_CURSOR_TYPEステートメント属性の組み合わせは、ドライバーまたはデータ ソースでサポートされていません。<br /><br /> SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_VARIABLE に設定され、SQL_ATTR_CURSOR_TYPE ステートメント属性が、ドライバーがブックマークをサポートしていないカーソルの種類に設定されました。|  
|ヒュット00|タイムアウトに達しました|データ ソースが結果セットを返す前にタイムアウト期間が切れました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUT**を**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 この関数は、通常、プロシージャのパラメータと、プロシージャによって返される結果セットを構成する列 (存在する場合) に関する情報を取得するために、ステートメントの実行前に使用されます。 詳細については、「[プロシージャ](../../../odbc/reference/develop-app/procedures-odbc.md)」を参照してください。  
  
> [!NOTE]  
>  **プロシージャで**使用されるすべての列が返されない場合があります。 たとえば、ドライバーは、プロシージャによって使用されるパラメーターに関する情報のみを返し、結果セットの列は返さない場合があります。  
  
 *スキーマ名*、*プロシージャ名*、および*列名*の引数は、検索パターンを受け入れます。 有効な検索パターンの詳細については、「[パターン値の引数](../../../odbc/reference/develop-app/pattern-value-arguments.md)」を参照してください。  
  
> [!NOTE]  
>  ODBC カタログ関数の一般的な使用、引数、および返されるデータの詳細については、「[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)」を参照してください。  
  
 **結果**は、PROCEDURE_CAT、PROCEDURE_SCHEM、PROCEDURE_NAME、およびCOLUMN_TYPE順に並べられた標準の結果セットとして返されます。 各プロシージャの列名は、戻り値の名前、プロシージャ呼び出しの各パラメーターの名前 (呼び出し順) 、およびプロシージャによって返される結果セット内の各列の名前 (列順) の順に返されます。  
  
 アプリケーションは、結果セットの末尾に関連するドライバー固有の列をバインドする必要があります。 詳細については、「[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)」を参照してください。  
  
 PROCEDURE_CAT、PROCEDURE_SCHEM、PROCEDURE_NAME、およびCOLUMN_NAME列の実際の長さを決定するために、アプリケーションは、SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、SQL_MAX_PROCEDURE_NAME_LEN、およびSQL_MAX_COLUMN_NAME_LENのオプションを指定して**SQLGetInfo**を呼び出すことができます。  
  
 次の列は、ODBC 3 の名前が変更されました。*x .* 列名の変更は、アプリケーションが列番号でバインドするため、下位互換性には影響しません。  
  
|ODBC 2.0 列|ODBC 3.*x*列|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|手順_OWNER|PROCEDURE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 ODBC 3 の**SQLProcedureColumns**によって返される結果セットに、次の列が追加されました。*x*:  
  
-   COLUMN_DEF  
  
-   DATETIME_CODE  
  
-   CHAR_OCTET_LENGTH  
  
-   ORDINAL_POSITION  
  
-   IS_NULLABLE  
  
 次の表は、結果セット内の列の一覧です。 列 19 (IS_NULLABLE) を超える追加の列は、ドライバーによって定義できます。 アプリケーションは、明示的な序数の位置を指定するのではなく、結果セットの末尾からカウントダウンして、ドライバー固有の列にアクセスする必要があります。 詳細については、「[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)」を参照してください。  
  
|列名|列番号|データ型|説明|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2.0)|1|Varchar|プロシージャ カタログ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる Dbms からデータを取得する場合など、一部のプロシージャのカタログをサポートしている場合、ドライバーは、カタログを持たないプロシージャの空の文字列 ("" ) を返します。|  
|PROCEDURE_SCHEM (ODBC 2.0)|2|Varchar|プロシージャ スキーマ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる Dbms からデータを取得する場合など、一部のプロシージャのスキーマをサポートしているドライバーは、スキーマを持たないプロシージャの空の文字列 ("" ) を返します。|  
|PROCEDURE_NAME (ODBC 2.0)|3|NULL ではないヴァルチャー|プロシージャ名。 名前を持たないプロシージャに対して空の文字列が返されます。|  
|COLUMN_NAME (ODBC 2.0)|4|NULL ではないヴァルチャー|プロシージャ列名。 ドライバーは、名前を持たないプロシージャ列の空の文字列を返します。|  
|COLUMN_TYPE (ODBC 2.0)|5|Smallint (NULL 以外)|プロシージャ列をパラメータまたは結果セット列として定義します。<br /><br /> SQL_PARAM_TYPE_UNKNOWN: プロシージャ列は、型が不明なパラメータです。 (ODBC 1.0)<br /><br /> SQL_PARAM_INPUT: プロシージャ列は入力パラメータです。 (ODBC 1.0)<br /><br /> SQL_PARAM_INPUT_OUTPUT: プロシージャ列は入力/出力パラメータです。 (ODBC 1.0)<br /><br /> SQL_PARAM_OUTPUT: プロシージャ列は出力パラメータです。 (ODBC 2.0)<br /><br /> SQL_RETURN_VALUE: プロシージャ列はプロシージャの戻り値です。 (ODBC 2.0)<br /><br /> SQL_RESULT_COL: プロシージャ列は結果セット列です。 (ODBC 1.0)|  
|DATA_TYPE (ODBC 2.0)|6|Smallint (NULL 以外)|SQL データ型。 これは、ODBC SQL データ型またはドライバー固有の SQL データ型です。 日時データ型と間隔データ型の場合、この列は、簡潔なデータ型 (SQL_TYPE_TIME、SQL_INTERVAL_YEAR_TO_MONTHなど) を返します。 有効な ODBC SQL データ型の一覧については、「付録 D: データ型」の[SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)を参照してください。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。|  
|TYPE_NAME (ODBC 2.0)|7|NULL ではないヴァルチャー|データ ソース依存のデータ型名。たとえば、"CHAR" "VARCHAR" "VARCHAR" "、"MONEY"、"ロング VARBINARY"、または "CHAR ( ) (ビット データ" の場合) などです。|  
|COLUMN_SIZE (ODBC 2.0)|8|Integer|データ ソースのプロシージャ列の列サイズ。 列サイズが適用されないデータ型に対して NULL が返されます。 精度の詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|BUFFER_LENGTH (ODBC 2.0)|9|Integer|SQL_C_DEFAULT指定されている場合に **、SQLGetData**または**SQLFetch**操作で転送されるデータのバイト数です。 数値データの場合、このサイズはデータ ソースに格納されているデータのサイズと異なる場合があります。 詳細については、「付録 D: データ型」の[「列サイズ、10 進数、オクテットの長さの転送、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|DECIMAL_DIGITS (ODBC 2.0)|10|Smallint|データ ソースのプロシージャ列の 10 進数の数字。 10 進数が適用できないデータ・タイプの場合は、NULL が戻されます。 10 進数の詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|NUM_PREC_RADIX (ODBC 2.0)|11|Smallint|数値データ型の場合は、10 または 2。<br /><br /> 10 の場合、COLUMN_SIZEとDECIMAL_DIGITSの値は、列に許容される小数点以下の桁数を示します。 たとえば、DECIMAL(12,5) 列は、NUM_PREC_RADIX 10、COLUMN_SIZE 12、および DECIMAL_DIGITS 5 を返します。FLOAT 列は、10 のNUM_PREC_RADIX、15 のCOLUMN_SIZE、および null のDECIMAL_DIGITSを返します。<br /><br /> 2 の場合、COLUMN_SIZEおよびDECIMAL_DIGITSの値は、列で許容されるビット数を示します。 例えば、FLOAT 列は、NUM_PREC_RADIX 2、COLUMN_SIZE 53、および null のDECIMAL_DIGITSを戻します。<br /><br /> null は、NUM_PREC_RADIXが適用されないデータ型に対して返されます。|  
|NULL 可能 (ODBC 2.0)|12|Smallint (NULL 以外)|プロシージャ列が NULL 値を受け入れるかどうか。<br /><br /> SQL_NO_NULLS: プロシージャ列は NULL 値を受け入れません。<br /><br /> SQL_NULLABLE: プロシージャ列は NULL 値を受け入れます。<br /><br /> SQL_NULLABLE_UNKNOWN: プロシージャー列が NULL 値を受け入れるかどうかは不明です。|  
|注釈 (ODBC 2.0)|13|Varchar|プロシージャ列の説明。|  
|COLUMN_DEF (ODBC 3.0)|14|Varchar|列の既定値です。<br /><br /> NULL がデフォルト値として指定されている場合、この列は NULL という単語で、引用符で囲まれません。 切り捨てなしでデフォルト値を表すことができない場合、この列には TRUNCATED が含まれます。 デフォルト値が指定されていない場合、この列は NULL になります。<br /><br /> COLUMN_DEFの値は、値 TRUNCATED が含まれている場合を除き、新しい列定義を生成するときに使用できます。|  
|SQL_DATA_TYPE (ODBC 3.0)|15|Smallint (NULL 以外)|記述子のSQL_DESC_TYPE フィールドに表示される SQL データ型の値。 この列は、日時および間隔のデータ・タイプを除き、DATA_TYPE列と同じです。<br /><br /> 日時および間隔のデータ型の場合、結果セットのSQL_DATA_TYPEフィールドはSQL_INTERVALまたはSQL_DATETIMEを返し、SQL_DATETIME_SUB フィールドは特定の間隔または日時データ型のサブコードを返します。 ([付録 D: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)を参照してください。|  
|SQL_DATETIME_SUB (ODBC 3.0)|16|Smallint|日時データ型および間隔データ型のサブタイプ コード。 その他のデータ型の場合、この列は NULL を返します。|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|17|Integer|文字型またはバイナリ データ型列の最大長 (バイト単位)。 その他のすべてのデータ型の場合、この列は NULL を返します。|  
|ORDINAL_POSITION (ODBC 3.0)|18|Integer (NULL 以外)|入力パラメーターおよび出力パラメーターの場合、プロシージャー定義内のパラメーターの順序位置 (パラメーターの順序の増加順で 1 から始まる)。 戻り値がある場合は、0 が返されます。 結果セット列の場合、結果セット内の列の序数の位置を、結果セットの最初の列が 1 になります。 複数の結果セットがある場合、列の序数の位置は、ドライバー固有の方法で返されます。|  
|IS_NULLABLE (ODBC 3.0)|19|Varchar|列にヌルが含まれていない場合は「NO」。<br /><br /> 列にヌルを含めることができる場合は「YES」。<br /><br /> NULL 値の許容が不明な場合、この列は長さ 0 の文字列を返します。<br /><br /> ISO 規則に従って、NULL 値の許容を決定します。 ISO SQL 準拠の DBMS は空の文字列を返すことができません。<br /><br /> この列に返される値は、NULLABLE 列に返される値とは異なります。 (NULL 可能列の説明を参照してください)。|  
  
## <a name="code-example"></a>コード例  
 [「プロシージャ コール」を](../../../odbc/reference/develop-app/procedure-calls.md)参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|単一行またはデータブロックを順方向方向にフェッチする|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|データ ソース内のプロシージャの一覧を返す|[SQLProcedures 関数](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
