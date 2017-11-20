---
title: "SQLProcedureColumns 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: db80c3c1fbf8e4d22f09849c95dde4bc4319bedf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlprocedurecolumns-function"></a>SQLProcedureColumns 関数
**準拠**  
 バージョンが導入されています ODBC 1.0 標準への準拠: ODBC。  
  
 **概要**  
 **SQLProcedureColumns**入力と出力パラメーターとして指定したプロシージャの結果セットを構成する列の一覧を返します。 ドライバーは、結果セットとして指定されたステートメントの情報を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *カタログ名*  
 [入力]プロシージャのカタログ名。 ドライバーは、一部のプロシージャは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のカタログをサポートしている場合 ("") のカタログはありません。 それらの手順を示します。 *CatalogName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*CatalogName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *CatalogName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。 詳細については、次を参照してください。[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)です。  
  
 *NameLength1*  
 [入力]文字の長さ **CatalogName*です。  
  
 *スキーマ名*  
 [入力]プロシージャのスキーマ名の文字列の検索パターン。 ドライバーは、一部のプロシージャは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のスキーマをサポートしている場合 ("") のスキーマはありません。 それらの手順を示します。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*SchemaName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *SchemaName*パターン引数の値は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength2*  
 [入力]文字の長さ **SchemaName*です。  
  
 *ProcName*  
 [入力]プロシージャ名の文字列の検索パターン。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*ProcName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *ProcName*パターン引数の値は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength3*  
 [入力]文字の長さ **ProcName*です。  
  
 *ColumnName*  
 [入力]列名の文字列の検索パターン。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*ColumnName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *ColumnName*パターン引数の値は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength4*  
 [入力]文字の長さ **ColumnName*です。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLProcedureColumns** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType*sql_handle_stmt としての*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLProcedureColumns**ですこの関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバーによって返される SQLSTATEs の説明。マネージャーです。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|24000|カーソル状態が無効|カーソルが開いて、 *StatementHandle*、および**SQLFetch**または**SQLFetchScroll**が呼び出されました。 このエラーが返されます、ドライバー マネージャーによって**SQLFetch**または**SQLFetchScroll** 、SQL_NO_DATA が返されなかったと場合、ドライバーによって返される**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されました。<br /><br /> カーソルが開いて、 *StatementHandle*が**SQLFetch**または**SQLFetchScroll**が呼び出されていません。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックによりロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLError**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY009|無効な null ポインターの使用|SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定された、 *CatalogName*引数が null ポインターの場合と、SQL_CATALOG_NAME*情報の種類*カタログ名を返しますがサポートされています。<br /><br /> (DM) SQL_ATTR_METADATA_ID ステートメント属性が SQL_TRUE に設定、および*SchemaName*、 *ProcName*、または*ColumnName*引数が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 SQLProcedureColumns 関数が呼び出されたときに、この aynschronous 関数が実行されています。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) 名長の引数のいずれかの値が 0 より小さい値は SQL_NTS に等しくありません。<br /><br /> 名前の長さの引数のいずれかの値には、対応するカタログ、スキーマ、プロシージャ、または列名の最大長の値を超えています。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|プロシージャのカタログが指定されていると、ドライバーまたはデータ ソースがカタログをサポートしていません。<br /><br /> プロシージャのスキーマが指定されました、ドライバーまたはデータ ソースがスキーマをサポートしていません。<br /><br /> プロシージャのスキーマ、プロシージャ名、または列名の文字列の検索パターンが指定され、データ ソースがこれらの引数の 1 つ以上の検索パターンをサポートしていません。<br /><br /> ドライバーまたはデータ ソースによっては、SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE ステートメント属性の現在の設定の組み合わせはサポートされていません。<br /><br /> SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されており、SQL_ATTR_CURSOR_TYPE ステートメント属性は、ドライバーがブックマークにできないカーソルの種類に設定されました。|  
|HYT00|タイムアウトが発生しました|データ ソースには、結果セットが返される前に、タイムアウト期間が期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtAttr**、SQL_ATTR_QUERY_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 この関数は、プロシージャのパラメーターと存在する場合は、結果セットやプロシージャによって返されるセットを構成する列に関する情報を取得するステートメントを実行する前に通常使用されます。 詳細については、次を参照してください。[プロシージャ](../../../odbc/reference/develop-app/procedures-odbc.md)です。  
  
> [!NOTE]  
>  **SQLProcedureColumns**プロシージャで使用されるすべての列を返さない可能性があります。 たとえば、ドライバーには、手順と生成結果セットの列によって使用されるパラメーターに関する情報だけが返されます。  
  
 *SchemaName*、 *ProcName*、および*ColumnName*引数には、検索パターンがそのまま使用します。 有効な検索パターンの詳細については、次を参照してください。[パターン値の引数](../../../odbc/reference/develop-app/pattern-value-arguments.md)です。  
  
> [!NOTE]  
>  一般的な使用、引数、および ODBC カタログ関数の返されたデータの詳細については、次を参照してください。[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)です。  
  
 **SQLProcedureColumns** PROCEDURE_CAT、PROCEDURE_SCHEM、PROCEDURE_NAME、および COLUMN_TYPE 並べ、標準的な結果セットとして結果を返します。 次の順序で各手順の列名が返されます。 戻り値の名前、呼び出し順)、プロシージャの呼び出しで各パラメーターの名前、および列の順序) の「プロシージャによって返される結果セット内の各列の名前。  
  
 アプリケーションでは、結果セットの末尾からの相対ドライバー固有の列をバインドする必要があります。 詳細については、次を参照してください。[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)です。  
  
 PROCEDURE_CAT、PROCEDURE_SCHEM、PROCEDURE_NAME、および COLUMN_NAME 列の実際の長さを決定するには、アプリケーションが呼び出すことができます**SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、SQL_MAX_ とPROCEDURE_NAME_LEN、および SQL_MAX_COLUMN_NAME_LEN オプション。  
  
 次の列は、ODBC 3 の名前変更されています。*x*です。 列名の変更では、列番号により、アプリケーション バインドのための下位互換性は影響しません。  
  
|ODBC 2.0 列|ODBC 3 です。*x*列|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|プロシージャ _OWNER|PROCEDURE_SCHEM|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
|RADIX|NUM_PREC_RADIX|  
  
 によって返される結果セットに次の列が追加されて**SQLProcedureColumns** ODBC 3 *。x*:  
  
-   COLUMN_DEF  
  
-   DATETIME_CODE  
  
-   CHAR_OCTET_LENGTH  
  
-   ORDINAL_POSITION  
  
-   IS_NULLABLE  
  
 次の表には、結果セット内の列が一覧表示します。 ドライバーでは、列 19 (によって IS_NULLABLE) を超える追加の列を定義できます。 アプリケーションでは、明示的な位置を表す序数を指定するのではなく、結果セットの末尾からカウント ダウンによって、ドライバー固有の列へのアクセスを得る必要があります。 詳細については、次を参照してください。[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)です。  
  
|列名|列番号|データ型|コメント|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2.0)|1|Varchar|プロシージャのカタログ名です。データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどに一部のプロシージャが、他のカタログをサポートする場合 ("") のカタログはありません。 それらの手順をします。|  
|PROCEDURE_SCHEM (ODBC 2.0)|2|Varchar|プロシージャのスキーマ名です。データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどに一部のプロシージャが、他のスキーマをサポートする場合 ("") のスキーマはありません。 それらの手順です。|  
|PROCEDURE_NAME (ODBC 2.0)|3|NULL でない Varchar|プロシージャの名前。 プロシージャの名前がない、空の文字列が返されます。|  
|COLUMN_NAME (ODBC 2.0)|4|NULL でない Varchar|プロシージャ列の名前。 ドライバーでは、名前がないプロシージャ列の空の文字列を返します。|  
|COLUMN_TYPE (ODBC 2.0)|5|Smallint (NULL 以外)|プロシージャのパラメーターとして列または結果セット列を定義します。<br /><br /> SQL_PARAM_TYPE_UNKNOWN: プロシージャの列は、パラメーターの型が不明です。 (ODBC 1.0)<br /><br /> SQL_PARAM_INPUT: プロシージャの列は、入力パラメーターです。 (ODBC 1.0)<br /><br /> SQL_PARAM_INPUT_OUTPUT: プロシージャの列は、入力/出力パラメーターです。 (ODBC 1.0)<br /><br /> SQL_PARAM_OUTPUT: プロシージャの列は、出力パラメーターです。 (ODBC 2.0)<br /><br /> SQL_RETURN_VALUE: プロシージャの列は、プロシージャの戻り値です。 (ODBC 2.0)<br /><br /> SQL_RESULT_COL: プロシージャの列は、結果セット列です。 (ODBC 1.0)|  
|DATA_TYPE (ODBC 2.0)|6|Smallint (NULL 以外)|SQL データ型です。 これには、ODBC SQL データ型またはドライバー固有の SQL データ型を指定できます。 Datetime および間隔のデータ型については、この列は、簡潔なデータ型 (たとえば、SQL_TYPE_TIME または SQL_INTERVAL_YEAR_TO_MONTH) を返します。 有効な ODBC SQL データ型の一覧は、次を参照してください。 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)付録 d: データ型にします。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。|  
|TYPE_NAME (ODBC 2.0)|7|NULL でない Varchar|データ ソースに依存するデータ型の名前です。たとえば、"CHAR"、"VARCHAR"、"MONEY"、"LONG VARBINARY"、または「CHAR () FOR BIT DATA」です。|  
|COLUMN_SIZE (ODBC 2.0)|8|Integer|データ ソースでプロシージャの列の列のサイズ。 NULL が返されますのデータ型列のサイズは適用されません。 詳細については有効桁数を参照してください[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)付録 d: データ型にします。|  
|BUFFER_LENGTH 列 (ODBC 2.0)|9|Integer|転送されるデータの長さ (バイト単位)、 **SQLGetData**または**SQLFetch** SQL_C_DEFAULT が指定されている場合に操作します。 数値データは、このサイズは、データ ソースに格納されているデータのサイズとは異なる可能性があります。 詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)、付録 d: データ型にします。|  
|DECIMAL_DIGITS (ODBC 2.0)|10|Smallint|データ ソースでプロシージャの列の 10 進数字。 NULL を返しますのデータ型の小数点以下桁数は適用されません。 詳細については小数点以下桁数を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)、付録 d: データ型にします。|  
|NUM_PREC_RADIX (ODBC 2.0)|11|Smallint|数値データ型の 10 または 2 のいずれか。<br /><br /> 場合は、10、COLUMN_SIZE と DECIMAL_DIGITS の値は、列に格納できる 10 進数字の数を提供します。 たとえば、DECIMAL(12,5) 列は 10、12、COLUMN_SIZE と 5; DECIMAL_DIGITS の NUM_PREC_RADIX を返しますFLOAT 列では、10、15、COLUMN_SIZE と NULL の DECIMAL_DIGITS の NUM_PREC_RADIX を返す可能性があります。<br /><br /> 2 の場合、COLUMN_SIZE と DECIMAL_DIGITS の値は、列に許容されるビット数を提供します。 たとえば、FLOAT 列では、2 53 の COLUMN_SIZE と NULL の DECIMAL_DIGITS の NUM_PREC_RADIX を返すでした。<br /><br /> NULL が返されますのデータ型 NUM_PREC_RADIX は適用されません。|  
|NULL 許容型 (ODBC 2.0)|12|Smallint (NULL 以外)|かどうか、プロシージャの列は、NULL 値を受け付けます。<br /><br /> SQL_NO_NULLS: プロシージャの列では NULL 値は受け入れられません。<br /><br /> SQL_NULLABLE: プロシージャの列は、NULL 値を指定できます。<br /><br /> SQL_NULLABLE_UNKNOWN: かは不明プロシージャの列が NULL 値を受け入れる場合です。|  
|「解説」(ODBC 2.0)|13|Varchar|プロシージャの列の説明です。|  
|COLUMN_DEF (ODBC 3.0)|14|Varchar|列の既定値です。<br /><br /> NULL は、既定値として指定されている場合、この列は NULL の場合、引用符で囲まれていないという単語はします。 既定値は、切り捨てることがなく表現できない、この列はありませんそれを囲む単一引用符が切り捨てられてを含みます。 既定値が指定されていない場合、この列は NULL を使用します。<br /><br /> COLUMN_DEF の値は、値が切り捨てられてが含まれている場合を除く、新しい列定義の生成に使用できます。|  
|SQL_DATA_TYPE (ODBC 3.0)|15|Smallint (NULL 以外)|記述子の SQL_DESC_TYPE フィールドには、SQL データ型の値が表示されます。 この列は、datetime および間隔のデータ型を除き、DATA_TYPE 列と同じです。<br /><br /> Datetime および間隔のデータ型の SQL_INTERVAL または SQL_DATETIME、結果セットの SQL_DATA_TYPE フィールドが返されます、SQL_DATETIME_SUB フィールドには、特定の間隔または datetime データ型のサブコードが返されます。 (を参照してください[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md))。|  
|SQL_DATETIME_SUB (ODBC 3.0)|16|Smallint|Datetime および interval データ型のサブタイプ コードです。 その他のデータ型の場合は、NULL が返されます。|  
|CHAR_OCTET_LENGTH (ODBC 3.0)|17|Integer|文字またはバイナリ データの最大長 (バイト単位) は、列を入力します。 他のすべてのデータ型の場合、この列は NULL を返します。|  
|ORDINAL_POSITION (ODBC 3.0)|18|Integer (NULL 以外)|入力呼び出し力パラメーターの場合 (パラメーター、昇順に 1 から始まります) プロシージャの定義でパラメーターの序数位置。 戻り値 (存在する場合)、0 が返されます。 結果内の列の序数位置が設定の結果セット列に設定されている結果の最初の列番号は 1 です。 複数の結果セットがある場合は、列の序数位置は、ドライバー固有の方法で返されます。|  
|によって IS_NULLABLE (ODBC 3.0)|19|Varchar|"NO"、列に null 値が含まれていない場合。<br /><br /> "YES"場合は、列が null 値を含めることができます。<br /><br /> NULL が許可されているかどうかがわからない列は、長さ 0 の文字列を返します。<br /><br /> NULL 値の許容属性の検査は ISO の規則に従います。 ISO SQL に準拠した DBMS では、空の文字列を返すことはできません。<br /><br /> この列に返される値は、NULLABLE 列に返される値とは異なります。 (詳しくは、null 許容の列の説明を参照してください)。|  
  
## <a name="code-example"></a>コード例  
 参照してください[プロシージャ呼び出し](../../../odbc/reference/develop-app/procedure-calls.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|1 つの行または順方向専用の方向にデータのブロックをフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|データ ソース内のプロシージャの一覧を返す|[SQLProcedures 関数](../../../odbc/reference/syntax/sqlprocedures-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

