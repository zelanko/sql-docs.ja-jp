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
- SQLColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColumns
helpviewer_keywords:
- SQLColumns function [ODBC]
ms.assetid: 4a3618b7-d2b8-43c6-a1fd-7a4e6fa8c7d0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 36293c1f2393e9a57351fc8cd19dcc6e3338f5cc
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301258"
---
# <a name="sqlcolumns-function"></a>SQLColumns 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: オープングループ  
  
 **まとめ**  
 **指定**したテーブルの列名のリストを返します。 ドライバーは、指定された*ステートメント ハンドル*の結果セットとして、この情報を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
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
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *カタログ名*  
 [入力]カタログ名。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしているが、他のテーブルについてはサポートされていない場合は、空の文字列 (") は、カタログを持たないテーブルを示します。 *カタログ名に*文字列検索パターンを含めることはできません。  
  
> [!NOTE]  
>  SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、CatalogName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合 *、CatalogName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。 詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。  
  
 *NameLength1*  
 [入力]* カタログ*名*の文字での長さ。  
  
 *Schemaname*  
 [入力]スキーマ名の文字列検索パターン。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、スキーマを持たないテーブルを示す空の文字列 (") が表示されます。  
  
> [!NOTE]  
>  SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、SchemaName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合、*スキーマ名*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 2*  
 [入力]**スキーマ名*の文字での長さ。  
  
 *TableName*  
 [入力]テーブル名の文字列検索パターン。  
  
> [!NOTE]  
>  SQL_ATTR_METADATA_IDステートメント属性が SQL_TRUE に設定されている場合 *、TableName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合 *、TableName*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 3*  
 [入力]**テーブル名*の文字での長さ。  
  
 *[ColumnName]*  
 [入力]列名の文字列検索パターン。  
  
> [!NOTE]  
>  SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、ColumnName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合、*列名*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ4*  
 [入力]**列名*の文字での長さ。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLColumns が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec** *を呼*び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は、SQLColumns によって返される**SQLSTATE**値の一覧と、この関数のコンテキストでの各値の説明です。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*でカーソルが開かれていたし **、SQL フェッチ**または SQL**フェッチスクロール**が呼び出されました。 このエラーは、ドライバー マネージャーが返す SQLFetch または**SQLFetchScrollSQL_NO_DATA**返されていない場合、ドライバー ドライバー マネージャーが返す **、SQL_NO_DATA****返された**場合は、ドライバーによって返されます。 **SQLFetch**<br /><br /> *ステートメント ハンドル*でカーソルが開かれていたが、SQLFetch または**SQLFetchScroll**が呼び出されていませんでした。 **SQLFetchScroll**|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、*ステートメント ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、関数は*ステートメント ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY009|無効な null ポインターの使用|SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、*引数 CatalogName*が null ポインターであり、SQL_CATALOG_NAME *InfoType*はカタログ名がサポートされていることを返します。<br /><br /> (DM) SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、引数*のスキーマ名*、*テーブル名*、*または列名*が null ポインターでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLColumns**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 名前長引数の 1 つの値が 0 より小さいが、SQL_NTSと等しくない。|  
|||名前の長さ引数の 1 つの値が、対応するカタログまたは名前の最大長の値を超えました。 各カタログまたは名前の最大長は、*情報の種類*の値を使用して**SQLGetInfo**を呼び出すことによって取得できます。 (「コメント」を参照してください。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|カタログ名が指定され、ドライバまたはデータ ソースがカタログをサポートしていません。<br /><br /> スキーマ名が指定され、ドライバーまたはデータ ソースがスキーマをサポートしていません。<br /><br /> スキーマ名、テーブル名、または列名に文字列検索パターンが指定されていますが、データ ソースは、これらの引数の 1 つ以上の検索パターンをサポートしていません。<br /><br /> SQL_ATTR_CONCURRENCYの現在の設定とSQL_ATTR_CURSOR_TYPEステートメント属性の組み合わせは、ドライバーまたはデータ ソースでサポートされていません。<br /><br /> SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_VARIABLE に設定され、SQL_ATTR_CURSOR_TYPE ステートメント属性が、ドライバーがブックマークをサポートしていないカーソルの種類に設定されました。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが結果セットを返しました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUT**を**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 この関数は、通常、データ ソースのカタログからテーブルの列に関する情報を取得するために、ステートメントの実行前に使用されます。 **SQLColumns を**使用して **、SQLTables**によって返されるすべての種類のアイテムのデータを取得できます。 ベース テーブルに加えて、ビュー、シノニム、システム テーブルなどが含まれます (ただしこれらに限定されません)。 これに対し **、SQLCol 属性**関数と**SQLDescribeCol 関数**は結果セット内の列を記述し、関数**SQLNumResultCols は**結果セット内の列の数を返します。 詳細については、「カタログ[データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)」を参照してください。  
  
> [!NOTE]  
>  ODBC カタログ関数の一般的な使用、引数、および返されるデータの詳細については、「[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)」を参照してください。  
  
 **SQLColumns は**、結果を標準の結果セットとして、TABLE_CAT、TABLE_SCHEM、TABLE_NAME、およびORDINAL_POSITION順に返します。  
  
> [!NOTE]  
>  アプリケーションが ODBC 2 で動作する場合。*x*ドライバー、ORDINAL_POSITION列は、結果セットに返されません。 その結果、ODBC 2 を使用する場合。*x*ドライバーでは **、SQLColumns**によって返される列の列の順序は、アプリケーションがそのテーブル内のすべての列に対して SELECT ステートメントを実行するときに返される列の順序と必ずしも同じではありません。  
  
> [!NOTE]  
>  **SQLColumns が**すべての列を返すわけではありません。 たとえば、ドライバーは、Oracle ROWID などの疑似列に関する情報を返さない場合があります。 アプリケーションは、 **SQLColumns**から返されるかどうかに関係なく、任意の有効な列を使用できます。  
>   
>  **SQLStatistics**によって返される可能性がある一部の列は、 **SQLColumns**によって返されません。 たとえば **、SQLColumns は**、式またはフィルターを使用して作成されたインデックス内の列 (SALARY + BENEFITS、DEPT = 0012 など) を返しません。  
  
 VARCHAR 列の長さは表に示されていません。実際の長さはデータ ソースによって異なります。 TABLE_CAT、TABLE_SCHEM、TABLE_NAME、およびCOLUMN_NAME列の実際の長さを決定するために、アプリケーションは**SQLGetInfo**を呼び出して、SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、SQL_MAX_TABLE_NAME_LEN、およびSQL_MAX_COLUMN_NAME_LENオプションを指定できます。  
  
 次の列は、ODBC 3 の名前が変更されました。*x .* 列名の変更は、アプリケーションが列番号でバインドするため、下位互換性には影響しません。  
  
|ODBC 2.0 列|ODBC 3.*x*列|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 ODBC 3 の**SQLColumns**によって返される結果セットに、次の列が追加されました。*x*:  
  
|||  
|-|-|  
|CHAR_OCTET_LENGTH|ORDINAL_POSITION|  
|COLUMN_DEF|SQL_DATA_TYPE|  
|IS_NULLABLE|SQL_DATETIME_SUB|  
  
 次の表は、結果セット内の列の一覧です。 列 18 (IS_NULLABLE) を超える追加の列は、ドライバーによって定義できます。 アプリケーションは、明示的な序数の位置を指定するのではなく、結果セットの末尾からカウントダウンして、ドライバー固有の列にアクセスする必要があります。 詳細については、「[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)」を参照してください。  
  
|列名|列<br /><br /> number|データ型|説明|  
|-----------------|-----------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|カタログ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしているが、他のテーブルについてはサポートしない場合は、カタログを持たないテーブルの空の文字列 ("" ) を返します。|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|スキーマ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、スキーマを持たないテーブルの空の文字列 ("" ) を返します。|  
|TABLE_NAME (ODBC 1.0)|3|NULL ではないヴァルチャー|テーブル名。|  
|COLUMN_NAME (ODBC 1.0)|4|NULL ではないヴァルチャー|列名。 ドライバーは、名前を持たない列の空の文字列を返します。|  
|DATA_TYPE (ODBC 1.0)|5|Smallint (NULL 以外)|SQL データ型。 これは、ODBC SQL データ型またはドライバー固有の SQL データ型です。 日時データ型および間隔データ型の場合、この列は、SQL_DATETIMEやSQL_INTERVALなどの非コンシーズ データ型ではなく、簡潔なデータ型 (SQL_TYPE_DATE やSQL_INTERVAL_YEAR_TO_MONTHなど) を返します。 有効な ODBC SQL データ型の一覧については、「付録 D: データ型」の[SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)を参照してください。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。<br /><br /> ODBC 3 に対して返されるデータ型。*x*と ODBC 2。*x*アプリケーションは異なる場合があります。 詳細については、「[下位互換性と標準準拠](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)」を参照してください。|  
|TYPE_NAME (ODBC 1.0)|6|NULL ではないヴァルチャー|データ ソース依存のデータ型名。たとえば、"CHAR" "VARCHAR" "VARCHAR" "、"お金"、"ロング VARBINAR"、または "CHAR ( ビット データ" の場合) です。|  
|COLUMN_SIZE (ODBC 1.0)|7|Integer|DATA_TYPEがSQL_CHARまたはSQL_VARCHARの場合、この列には列の最大文字数が含まれます。 datetime データ型の場合、これは、値を文字に変換するときに表示するために必要な文字数の合計です。 数値データ型の場合、これは、NUM_PREC_RADIX列に従って、合計桁数または列で許容されるビット数のいずれかです。 間隔データ型の場合、これは間隔リテラルの文字表現の文字数です (間隔先行精度で定義されているとおり、「付録 D: データ型」の[「間隔データ型の長さ](../../../odbc/reference/appendixes/interval-data-type-length.md)」を参照)。 詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長さ」および「表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|BUFFER_LENGTH (ODBC 1.0)|8|Integer|SQL_C_DEFAULT指定されている場合に、SQLGetData、SQLFetch、または SQLFetchScroll 操作で転送されるデータのバイト数で示されます。 数値データの場合、このサイズはデータ ソースに格納されているデータのサイズと異なる場合があります。 この値は、文字データCOLUMN_SIZE列と異なる場合があります。 長さの詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|DECIMAL_DIGITS (ODBC 1.0)|9|Smallint|小数点の右側にある有効桁数の合計。 SQL_TYPE_TIMEとSQL_TYPE_TIMESTAMPの場合、この列には秒の小数部の数値が含まれます。 その他のデータ型の場合、これはデータ ソースの列の 10 進数の数字です。 時間コンポーネントを含む間隔データ型の場合、この列には小数点の右側の桁数 (秒の小数部) が含まれます。 時間コンポーネントを含まない間隔データ型の場合、この列は 0 です。 10 進数の詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。 DECIMAL_DIGITSが適用されないデータ型に対しては NULL が返されます。|  
|NUM_PREC_RADIX (ODBC 1.0)|10|Smallint|数値データ型の場合は、10 または 2。 10 の場合、COLUMN_SIZEおよびDECIMAL_DIGITSの値は、列に許可されている 10 進数の桁数を示します。 たとえば、DECIMAL(12,5) 列は、NUM_PREC_RADIX 10、COLUMN_SIZE 12、および DECIMAL_DIGITS 5 を返します。FLOAT 列は、10 のNUM_PREC_RADIX、15 のCOLUMN_SIZE、および null のDECIMAL_DIGITSを返します。<br /><br /> 2 の場合、COLUMN_SIZEの値とDECIMAL_DIGITS列で許容されるビット数を指定します。 例えば、FLOAT 列は、2 の RADIX、53 のCOLUMN_SIZE、および null のDECIMAL_DIGITSを戻します。<br /><br /> null は、NUM_PREC_RADIXが適用されないデータ型に対して返されます。|  
|NULL 可能 (ODBC 1.0)|11|Smallint (NULL 以外)|列に NULL 値を含むことができなかった場合にSQL_NO_NULLSします。<br /><br /> 列が NULL 値を受け入れる場合にSQL_NULLABLEします。<br /><br /> 列が NULL 値を受け入れるかどうかが不明な場合はSQL_NULLABLE_UNKNOWNします。<br /><br /> この列に対して返される値は、IS_NULLABLE列に対して返される値と異なります。 NULLABLE 列は、列が NULL を受け入れることは確実ですが、列が NULL を受け入れないことを確実に示すことはできません。 IS_NULLABLE列は、列がヌルを受け入れることはできないが、列が UL を受け入れることを確実に示すことができないことを確実に示します。|  
|注釈 (ODBC 1.0)|12|Varchar|列の説明。|  
|COLUMN_DEF (ODBC 3.0)|13|Varchar|列の既定値です。 この列の値は、引用符で囲まれている場合は文字列として解釈されます。<br /><br /> NULL がデフォルト値として指定されている場合、この列は NULL という単語で、引用符で囲まれません。 切り捨てなしでデフォルト値を表すことができない場合、この列には、単一引用符を囲まずに TRUNCATED が入ります。 デフォルト値が指定されていない場合、この列は NULL になります。<br /><br /> COLUMN_DEFの値は、値 TRUNCATED が含まれている場合を除き、新しい列定義を生成するときに使用できます。|  
|SQL_DATA_TYPE (ODBC 3.0)|14|Smallint (NULL 以外)|SQL データ型 (IRD のSQL_DESC_TYPEレコード フィールドに表示される) これは、ODBC SQL データ型またはドライバー固有の SQL データ型です。 この列は、日時および間隔のデータ・タイプを除き、DATA_TYPE列と同じです。 この列は、日時データ型および間隔データ型の簡潔なデータ型 (SQL_TYPE_DATE やSQL_INTERVAL_YEAR_TO_MONTHなど) ではなく、非コンシーズ型 (SQL_DATETIME やSQL_INTERVALなど) を返します。 この列がSQL_DATETIMEまたはSQL_INTERVALを返す場合は、SQL_DATETIME_SUB列から特定のデータ型を決定できます。 有効な ODBC SQL データ型の一覧については、「付録 D: データ型」の[SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)を参照してください。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。<br /><br /> ODBC 3 に対して返されるデータ型。*x*と ODBC 2。*x*アプリケーションは異なる場合があります。 詳細については、「[下位互換性と標準準拠](../../../odbc/reference/develop-app/backward-compatibility-and-standards-compliance.md)」を参照してください。|  
|SQL_DATETIME_SUB (ODBC 3.0)|15|Smallint|日時データ型および間隔データ型のサブタイプ コード。 その他のデータ型の場合、この列は NULL を返します。 日付と間隔のサブコードの詳細については、 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)の「SQL_DESC_DATETIME_INTERVAL_CODE」を参照してください。|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|16|Integer|文字型またはバイナリ データ型列の最大長 (バイト単位)。 その他のすべてのデータ型の場合、この列は NULL を返します。|  
|ORDINAL_POSITION (ODBC 3.0)|17|Integer (NULL 以外)|テーブル内の列の序数位置です。 テーブルの最初の列は 1 です。|  
|IS_NULLABLE (ODBC 3.0)|18|Varchar|列にヌルが含まれていない場合は「NO」。<br /><br /> 列にヌルを含めることができる場合は"YES"。<br /><br /> NULL 値の許容が不明な場合、この列は長さ 0 の文字列を返します。<br /><br /> ISO 規則に従って、NULL 値の許容を決定します。 ISO SQL 準拠の DBMS は空の文字列を返すことができません。<br /><br /> この列に対して返される値は、NULLABLE 列に対して返される値と異なります。 (NULL 可能列の説明を参照してください)。|  
  
## <a name="code-example"></a>コード例  
 次の例では、アプリケーションが**SQLColumns**によって返される結果セットのバッファーを宣言します。 このステートメントは **、SQLColumns**を呼び出して、EMPLOYEE 表の各列を記述する結果セットを戻します。 次に **、SQLBindCol**を呼び出して、結果セット内の列をバッファーにバインドします。 最後に、アプリケーションは**SQLFetch**を使用してデータの各行をフェッチし、それを処理します。  
  
```cpp  
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
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|列の特権の取得|[SQLColumnPrivileges 関数](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|複数行のデータのフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|行を一意に識別する列、またはトランザクションによって自動的に更新される列を返す|[SQLSpecialColumns 関数](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|  
|テーブルの統計とインデックスを返す|[SQLStatistics 関数](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|データ ソース内のテーブルの一覧を返す|[SQLTables 関数](../../../odbc/reference/syntax/sqltables-function.md)|  
|表の特権の戻り|[SQLTablePrivileges 関数](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
