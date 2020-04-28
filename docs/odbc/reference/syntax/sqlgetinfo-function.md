---
title: SQLGetInfo 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetInfo
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetInfo
helpviewer_keywords:
- SQLGetInfo function [ODBC]
ms.assetid: 49dceccc-d816-4ada-808c-4c6138dccb64
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 514922fd085cfd2ba19eb5c07dd844db82d55202
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303344"
---
# <a name="sqlgetinfo-function"></a>SQLGetInfo 関数
**互換性**  
 導入されたバージョン: ODBC 1.0 標準準拠: ISO 92  
  
 **まとめ**  
 **SQLGetInfo**は、接続に関連付けられているドライバーとデータソースに関する一般的な情報を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLGetInfo(  
     SQLHDBC         ConnectionHandle,  
     SQLUSMALLINT    InfoType,  
     SQLPOINTER      InfoValuePtr,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *ConnectionHandle*  
 [入力] 接続ハンドル。  
  
 *InfoType*  
 代入情報の種類。  
  
 *インフォ Valueptr*  
 Output情報を返すバッファーへのポインター。 要求された*InfoType*に応じて、返される情報は次のいずれかになります。 null で終わる文字列、SQLUS悪意のある値、SQLUINTEGER ビットマスク、SQLUINTEGER フラグ、SQLUINTEGER バイナリ値、または SQLULEN 値。  
  
 *InfoType*引数が SQL_DRIVER_HDESC または SQL_DRIVER_HSTMT の場合、 *infovalueptr*引数は入力と出力の両方になります。 (詳細については、この関数の説明で後述する SQL_DRIVER_HDESC または SQL_DRIVER_HSTMT の記述子を参照してください)。  
  
 *Infovalueptr*が NULL の場合でも、 *stringlength Ptr*は、 *infovalueptr*が指すバッファー内で返されるバイトの合計数 (文字データの NULL 終端文字を除く) を返します。  
  
 *BufferLength*  
 代入\**インフォ valueptr*バッファーの長さ。 * \*Infovalueptr*の値が文字列でない場合、または*infovalueptr*が null ポインターの場合、 *bufferlength*引数は無視されます。 ドライバーは、InfoType に基づいて、 * \*インフォ valueptr*のサイズが sqlus悪意のある SQLUINTEGER または*InfoType*であることを前提としています。 * \*Infovalueptr*が Unicode 文字列の場合 ( **sqlgetinfow**を呼び出すとき)、 *bufferlength*引数は偶数である必要があります。それ以外の場合は、SQLSTATE HY090 (無効な文字列またはバッファー長) が返されます。  
  
 *Stringlength Ptr*  
 Output**Infovalueptr*で返すことができるバイト数の合計 (文字データの null 終端文字を除く) を返すバッファーへのポインター。  
  
 文字データの場合、返される使用可能なバイト数が*bufferlength*以上の場合、 \* *infovalueptr*内の情報は、 *bufferlength*バイトから null 終端文字の長さを引いた値に切り捨てられ、ドライバーによって null で終了されます。  
  
 他のすべての種類のデータについては、 *bufferlength*の値は無視されます\*。ドライバーは、 *InfoType*に応じて、 *infovalueptr*のサイズが sqlus悪意のあるものであることを前提としています。  
  
## <a name="return-value"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetInfo**が SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返す場合、関連付けられた SQLSTATE 値を取得するには、 *handletype* SQL_HANDLE_DBC および*connectionhandle*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出します。 次の表に、 **SQLGetInfo**によって通常返される SQLSTATE 値と、この関数のコンテキストにおけるそれぞれの説明を示します。"(DM)" という表記は、ドライバーマネージャーによって返される SQLSTATEs の説明の前にあります。 特に記載がない限り、各 SQLSTATE 値に関連付けられているリターンコードは SQL_ERROR ます。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般警告|ドライバー固有の情報メッセージ。 (関数は SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データ、右側が切り捨てられました|バッファー \* *infovalueptr*は、要求されたすべての情報を返すには十分な大きさではありませんでした。 そのため、情報は切り捨てられました。 切り捨てられていない形式の要求された情報の長さは、**Stringlength ptr*に返されます。 (関数は SQL_SUCCESS_WITH_INFO を返します)。|  
|08003|接続が開かれていません|(DM) *InfoType*で要求された情報の種類には、開いている接続が必要です。 ODBC によって予約されている情報の種類のうち、開いている接続を使用せずに SQL_ODBC_VER だけを返すことができます。|  
|08S01|通信リンクの失敗|関数が処理を完了する前に、ドライバーと、ドライバーが接続されていたデータソースとの間の通信リンクが失敗しました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 Messagetext バッファーの**SQLGetDiagRec**によって返されるエラーメッセージには、エラーとその原因が記述されています。 * \**|  
|HY001|メモリ割り当てエラー|ドライバーは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンスエラー|(DM) **Sqlexecute**、 **SQLExecDirect**、または**Sqlmoreresults**が*StatementHandle*に対して呼び出され、SQL_PARAM_DATA_AVAILABLE が返されました。 この関数は、ストリーミングされたすべてのパラメーターのデータが取得される前に呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリオブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。メモリ不足の状態が原因である可能性があります。|  
|HY024|無効な属性値|(DM) *InfoType*引数が SQL_DRIVER_HSTMT、 *infovalueptr*によってポイントされた値が有効なステートメントハンドルではありませんでした。<br /><br /> (DM) *InfoType*引数が SQL_DRIVER_HDESC、 *infovalueptr*によってポイントされた値が有効な記述子ハンドルではありませんでした。|  
|HY090|文字列またはバッファーの長さが無効です|(DM) 引数*Bufferlength*に指定された値が0未満でした。<br /><br /> (DM) *bufferlength*に指定された値は奇数で、 * \*infovalueptr*は Unicode データ型でした。|  
|HY096|情報の種類が有効範囲にありません|引数*InfoType*に指定された値は、ドライバーでサポートされている ODBC のバージョンに対して無効です。|  
|HY117|トランザクションの状態が不明なため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については、「 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)」を参照してください。|  
|HYC00|省略可能なフィールドが実装されていません|引数*InfoType*に指定された値はドライバー固有の値であり、ドライバーではサポートされていません。|  
|HYT01|接続タイムアウトの期限が切れました|データソースが要求に応答する前に、接続のタイムアウト期間が経過しました。 接続タイムアウト期間は、 **SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT によって設定されます。|  
|IM001|ドライバーはこの機能をサポートしていません|(DM) *Connectionhandle*に対応するドライバーでは、関数はサポートされていません。|  
  
## <a name="comments"></a>説明  
 現在定義されている情報の種類は、このセクションの「情報の種類」に記載されています。さまざまなデータソースを活用するために、より多くのデータソースが定義されることが予想されます。 ODBC では、さまざまな種類の情報が予約されています。ドライバー開発者は、オープングループから独自のドライバー固有の使用のために値を予約する必要があります。 **SQLGetInfo**は、Unicode 変換または*サンキング*を*実行しませ*ん (「付録 a: *odbc プログラマーズリファレンス*の[odbc エラーコード](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md)」を参照してください)。 詳細については、「[ドライバー固有のデータ型、記述子の型、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)」を参照してください。 \* *Infovalueptr*で返される情報の形式は、要求された*InfoType*によって異なります。 **SQLGetInfo**は、5つの異なる形式のいずれかで情報を返します。  
  
-   Null で終わる文字列  
  
-   SQLUS悪意のある値  
  
-   SQLUINTEGER ビットマスク  
  
-   SQLUINTEGER 値  
  
-   SQLUINTEGER バイナリ値  
  
 次の各種類の情報の形式は、型の説明に記載されています。 アプリケーションは、必要に応じて、**Infovalueptr*に返された値をキャストする必要があります。 アプリケーションが SQLUINTEGER ビットマスクからデータを取得する方法の例については、「コード例」を参照してください。  
  
 ドライバーは、次の表に定義されている情報の種類ごとに値を返す必要があります。 情報の種類がドライバーまたはデータソースに適用されない場合、ドライバーは次の表に示すいずれかの値を返します。  
  
 文字列 ("Y" または "N")  
 "N"  
  
 文字列 ("Y" または "N" ではない)  
 空の文字列  
  
 SQLUSマル糸  
 0  
  
 SQLUINTEGER ビットマスクまたは SQLUINTEGER バイナリ値  
 0L  
  
 たとえば、データソースでプロシージャがサポートされていない場合、 **SQLGetInfo**は、プロシージャに関連する*InfoType*の値について、次の表に示す値を返します。  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 空の文字列  
  
 **SQLGetInfo**は、odbc で使用するために予約されている情報の種類の範囲内にある*InfoType*の値の SQLSTATE HY096 (無効な引数値) を返しますが、ドライバーでサポートされている odbc のバージョンでは定義されていません。 ドライバーが準拠している ODBC のバージョンを確認するために、アプリケーションは SQL_DRIVER_ODBC_VER 情報の種類を使用して**SQLGetInfo**を呼び出します。 **SQLGetInfo**は、ドライバー固有の使用のために予約されているがドライバーでサポートされていない情報の種類の範囲内にある*InfoType*の値に対して、SQLSTATE HYC00 (実装されていないオプションの機能) を返します。  
  
 *InfoType*が SQL_ODBC_VER 場合を除き、 **SQLGetInfo**へのすべての呼び出しには、ドライバーマネージャーのバージョンを返す、開いている接続が必要です。  
  
## <a name="information-types"></a>情報の種類  
 このセクションでは、 **SQLGetInfo**でサポートされている情報の種類を示します。 情報の種類は、明確ににグループ化され、アルファベット順に表示されます。 ODBC 3.x で追加または名前が変更された情報の種類も*表示され*ます。  
  
## <a name="driver-information"></a>ドライバー情報  
 *InfoType*引数の次の値は、アクティブなステートメントの数、データソース名、およびインターフェイスの標準のコンプライアンスレベルなど、ODBC ドライバーに関する情報を返します。  
  
|||  
|-|-|  
|SQL_ACTIVE_ENVIRONMENTS|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
|SQL_ASYNC_DBC_FUNCTIONS|SQL_FILE_USAGE|  
|SQL_ASYNC_MODE|SQL_GETDATA_EXTENSIONS|  
|SQL_ASYNC_NOTIFICATION|SQL_INFO_SCHEMA_VIEWS|  
|SQL_BATCH_ROW_COUNT|SQL_KEYSET_CURSOR_ATTRIBUTES1|  
|SQL_BATCH_SUPPORT|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
|SQL_DATA_SOURCE_NAME|SQL_MAX_ASYNC_CONCURRENT_STATEMENTS|  
|SQL_DRIVER_AWARE_POOLING_SUPPORTED|SQL_MAX_CONCURRENT_ACTIVITIES|  
|SQL_DRIVER_HDBC|SQL_MAX_DRIVER_CONNECTIONS|  
|SQL_DRIVER_HDESC|SQL_ODBC_INTERFACE_CONFORMANCE|  
|SQL_DRIVER_HENV|SQL_ODBC_STANDARD_CLI_CONFORMANCE|  
|SQL_DRIVER_HLIB|SQL_ODBC_VER|  
|SQL_DRIVER_HSTMT|SQL_PARAM_ARRAY_ROW_COUNTS|  
|SQL_DRIVER_NAME|SQL_PARAM_ARRAY_SELECTS|  
|SQL_DRIVER_ODBC_VER|SQL_ROW_UPDATES|  
|SQL_DRIVER_VER|SQL_SEARCH_PATTERN_ESCAPE|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|SQL_SERVER_NAME|  
|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|SQL_STATIC_CURSOR_ATTRIBUTES1|  
|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|SQL_STATIC_CURSOR_ATTRIBUTES2|  
  
> [!NOTE]  
>  **SQLGetInfo**を実装する場合、ドライバーは、サーバーから情報が送信または要求される回数を最小限に抑えることで、パフォーマンスを向上させることができます。  
  
## <a name="dbms-product-information"></a>DBMS 製品情報  
 *InfoType*引数の次の値は、dbms の名前やバージョンなど、dbms 製品に関する情報を返します。  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>データソース情報  
 *InfoType*引数の次の値は、カーソルの特性やトランザクション機能など、データソースに関する情報を返します。  
  
|||  
|-|-|  
|SQL_ACCESSIBLE_PROCEDURES|SQL_MULT_RESULT_SETS|  
|SQL_ACCESSIBLE_TABLES|SQL_MULTIPLE_ACTIVE_TXN|  
|SQL_BOOKMARK_PERSISTENCE|SQL_NEED_LONG_DATA_LEN|  
|SQL_CATALOG_TERM|SQL_NULL_COLLATION|  
|SQL_COLLATION_SEQ|SQL_PROCEDURE_TERM|  
|SQL_CONCAT_NULL_BEHAVIOR|SQL_SCHEMA_TERM|  
|SQL_CURSOR_COMMIT_BEHAVIOR|SQL_SCROLL_OPTIONS|  
|SQL_CURSOR_ROLLBACK_BEHAVIOR|SQL_TABLE_TERM|  
|SQL_CURSOR_SENSITIVITY|SQL_TXN_CAPABLE|  
|SQL_DATA_SOURCE_READ_ONLY|SQL_TXN_ISOLATION_OPTION|  
|SQL_DEFAULT_TXN_ISOLATION|SQL_USER_NAME|  
|SQL_DESCRIBE_PARAMETER||  
  
## <a name="supported-sql"></a>サポートされている SQL  
 *InfoType*引数の次の値は、データソースでサポートされている SQL ステートメントに関する情報を返します。 これらの情報の種類で記述されている各機能の SQL 構文は、SQL-92 構文です。 これらの情報の種類は、SQL-92 の文法全体を徹底的に記述するものではありません。 代わりに、一般的には、データソースがさまざまなレベルのサポートを提供する文法の部分について説明します。 具体的には、SQL-92 の DDL ステートメントのほとんどが対象となります。  
  
 アプリケーションでは、SQL_SQL_CONFORMANCE 情報の種類からサポートされる文法の一般レベルを決定し、その他の情報の種類を使用して、記載されている標準のコンプライアンスレベルのバリエーションを判断する必要があります。  
  
|||  
|-|-|  
|SQL_AGGREGATE_FUNCTIONS|SQL_DROP_TABLE|  
|SQL_ALTER_DOMAIN|SQL_DROP_TRANSLATION|  
|SQL_ALTER_SCHEMA|SQL_DROP_VIEW|  
|SQL_ALTER_TABLE|SQL_EXPRESSIONS_IN_ORDERBY|  
|SQL_ANSI_SQL_DATETIME_LITERALS|SQL_GROUP_BY|  
|SQL_CATALOG_LOCATION|SQL_IDENTIFIER_CASE|  
|SQL_CATALOG_NAME|SQL_IDENTIFIER_QUOTE_CHAR|  
|SQL_CATALOG_NAME_SEPARATOR|SQL_INDEX_KEYWORDS|  
|SQL_CATALOG_USAGE|SQL_INSERT_STATEMENT|  
|SQL_COLUMN_ALIAS|SQL_INTEGRITY|  
|SQL_CORRELATION_NAME|SQL_KEYWORDS|  
|SQL_CREATE_ASSERTION|SQL_LIKE_ESCAPE_CLAUSE|  
|SQL_CREATE_CHARACTER_SET|SQL_NON_NULLABLE_COLUMNS|  
|SQL_CREATE_COLLATION|SQL_SQL_CONFORMANCE|  
|SQL_CREATE_DOMAIN|SQL_OJ_CAPABILITIES|  
|SQL_CREATE_SCHEMA|SQL_ORDER_BY_COLUMNS_IN_SELECT|  
|SQL_CREATE_TABLE|SQL_OUTER_JOINS|  
|SQL_CREATE_TRANSLATION|SQL_PROCEDURES|  
|SQL_DDL_INDEX|SQL_QUOTED_IDENTIFIER_CASE|  
|SQL_DROP_ASSERTION|SQL_SCHEMA_USAGE|  
|SQL_DROP_CHARACTER_SET|SQL_SPECIAL_CHARACTERS|  
|SQL_DROP_COLLATION|SQL_SUBQUERIES|  
|SQL_DROP_DOMAIN|SQL_UNION|  
|SQL_DROP_SCHEMA||  
  
## <a name="sql-limits"></a>SQL の制限  
 *InfoType*引数の次の値は、SQL ステートメント内の識別子および句に適用される制限に関する情報を返します。たとえば、識別子の最大長や選択リスト内の列の最大数などです。 制限は、ドライバーまたはデータソースのいずれかで行うことができます。  
  
|||  
|-|-|  
|SQL_MAX_BINARY_LITERAL_LEN|SQL_MAX_IDENTIFIER_LEN|  
|SQL_MAX_CATALOG_NAME_LEN|SQL_MAX_INDEX_SIZE|  
|SQL_MAX_CHAR_LITERAL_LEN|SQL_MAX_PROCEDURE_NAME_LEN|  
|SQL_MAX_COLUMN_NAME_LEN|SQL_MAX_ROW_SIZE|  
|SQL_MAX_COLUMNS_IN_GROUP_BY|SQL_MAX_ROW_SIZE_INCLUDES_LONG|  
|SQL_MAX_COLUMNS_IN_INDEX|SQL_MAX_SCHEMA_NAME_LEN|  
|SQL_MAX_COLUMNS_IN_ORDER_BY|SQL_MAX_STATEMENT_LEN|  
|SQL_MAX_COLUMNS_IN_SELECT|SQL_MAX_TABLE_NAME_LEN|  
|SQL_MAX_COLUMNS_IN_TABLE|SQL_MAX_TABLES_IN_SELECT|  
|SQL_MAX_CURSOR_NAME_LEN|SQL_MAX_USER_NAME_LEN|  
  
## <a name="scalar-function-information"></a>スカラー関数の情報  
 *InfoType*引数の次の値は、データソースとドライバーでサポートされているスカラー関数に関する情報を返します。 スカラー関数の詳細については、「[付録 E: スカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)」を参照してください。  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>変換情報  
 *InfoType*引数の次の値は、データソースが指定された sql データ型を**convert**スカラー関数に変換できる sql データ型の一覧を返します。  
  
|||  
|-|-|  
|SQL_CONVERT_BIGINT|SQL_CONVERT_LONGVARBINARY|  
|SQL_CONVERT_BINARY|SQL_CONVERT_LONGVARCHAR|  
|SQL_CONVERT_BIT|SQL_CONVERT_NUMERIC|  
|SQL_CONVERT_CHAR|SQL_CONVERT_REAL|  
|SQL_CONVERT_DATE|SQL_CONVERT_SMALLINT|  
|SQL_CONVERT_DECIMAL|SQL_CONVERT_TIME|  
|SQL_CONVERT_DOUBLE|SQL_CONVERT_TIMESTAMP|  
|SQL_CONVERT_FLOAT|SQL_CONVERT_TINYINT|  
|SQL_CONVERT_INTEGER|SQL_CONVERT_VARBINARY|  
|SQL_CONVERT_INTERVAL_YEAR_MONTH|SQL_CONVERT_VARCHAR|  
|SQL_CONVERT_INTERVAL_DAY_TIME||  
  
## <a name="information-types-added-for-odbc-3x"></a>ODBC 3.x 用に追加された情報の種類  
 ODBC 3.x には、 *InfoType*引数の次の値が追加*されています。*  
  
|||  
|-|-|  
|SQL_ACTIVE_ENVIRONMENTS|SQL_DRIVER_AWARE_POOLING_SUPPORTED|  
|SQL_AGGREGATE_FUNCTIONS|SQL_DRIVER_HDESC|  
|SQL_ALTER_DOMAIN|SQL_DROP_ASSERTION|  
|SQL_ALTER_SCHEMA|SQL_DROP_CHARACTER_SET|  
|SQL_ANSI_SQL_DATETIME_LITERALS|SQL_DROP_COLLATION|  
|SQL_ASYNC_DBC_FUNCTIONS|SQL_DROP_DOMAIN|  
|SQL_ASYNC_MODE|SQL_DROP_SCHEMA|  
|SQL_ASYNC_NOTIFICATION|SQL_DROP_TABLE|  
|SQL_BATCH_ROW_COUNT|SQL_DROP_TRANSLATION|  
|SQL_BATCH_SUPPORT|SQL_DROP_VIEW|  
|SQL_CATALOG_NAME|SQL_DYNAMIC_CURSOR_ATTRIBUTES1|  
|SQL_COLLATION_SEQ|SQL_DYNAMIC_CURSOR_ATTRIBUTES2|  
|SQL_CONVERT_INTERVAL_YEAR_MONTH|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1|  
|SQL_CONVERT_INTERVAL_DAY_TIME|SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2|  
|SQL_CREATE_ASSERTION|SQL_INFO_SCHEMA_VIEWS|  
|SQL_CREATE_CHARACTER_SET|SQL_INSERT_STATEMENT|  
|SQL_CREATE_COLLATION|SQL_KEYSET_CURSOR_ATTRIBUTES1|  
|SQL_CREATE_DOMAIN|SQL_KEYSET_CURSOR_ATTRIBUTES2|  
|SQL_CREATE_SCHEMA|SQL_MAX_ASYNC_CONCURRENT_STATEMENTS|  
|SQL_CREATE_TABLE|SQL_MAX_IDENTIFIER_LEN|  
|SQL_CREATE_TRANSLATION|SQL_PARAM_ARRAY_ROW_COUNTS|  
|SQL_CURSOR_SENSITIVITY|SQL_PARAM_ARRAY_SELECTS|  
|SQL_DDL_INDEX|SQL_STATIC_CURSOR_ATTRIBUTES1|  
|SQL_DESCRIBE_PARAMETER|SQL_STATIC_CURSOR_ATTRIBUTES2|  
|SQL_DM_VER|SQL_XOPEN_CLI_YEAR|  
  
## <a name="information-types-renamed-for-odbc-3x"></a>ODBC 3. x の名前が変更された情報の種類  
 ODBC 3.x では、 *InfoType*引数の次の値の名前が変更*されました。*  
  
 SQL_ACTIVE_CONNECTIONS  
 SQL_MAX_DRIVER_CONNECTIONS  
  
 SQL_ACTIVE_STATEMENTS  
 SQL_MAX_CONCURRENT_ACTIVITIES  
  
 SQL_MAX_OWNER_NAME_LEN  
 SQL_MAX_SCHEMA_NAME_LEN  
  
 SQL_MAX_QUALIFIER_NAME_LEN  
 SQL_MAX_CATALOG_NAME_LEN  
  
 SQL_ODBC_SQL_OPT_IEF  
 SQL_INTEGRITY  
  
 SQL_OWNER_TERM  
 SQL_SCHEMA_TERM  
  
 SQL_OWNER_USAGE  
 SQL_SCHEMA_USAGE  
  
 SQL_QUALIFIER_LOCATION  
 SQL_CATALOG_LOCATION  
  
 SQL_QUALIFIER_NAME_SEPARATOR  
 SQL_CATALOG_NAME_SEPARATOR  
  
 SQL_QUALIFIER_TERM  
 SQL_CATALOG_TERM  
  
 SQL_QUALIFIER_USAGE  
 SQL_CATALOG_USAGE  
  
## <a name="information-types-deprecated-in-odbc-3x"></a>ODBC 3.x で非推奨とされる情報の種類  
 *InfoType*引数の次の値は、ODBC 3.x では非推奨と*されました。* Odbc 2.x*ドライバーは*、odbc*2.x アプリケーションと*の下位互換性を維持するために、これらの情報の種類を引き続きサポートする必要があります。 (これらの型の詳細については、「付録 G: 旧バージョンとの互換性のためのドライバーガイドライン」の「 [SQLGetInfo Support](../../../odbc/reference/appendixes/sqlgetinfo-support.md) 」を参照してください)。  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>情報の種類の説明  
 次の表は、それぞれの情報の種類、ODBC のバージョン、および説明をアルファベット順に示しています。  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1.0)  
 文字列 "Y": ユーザーが**sqlprocedures**によって返されたすべてのプロシージャを実行できる場合は、ユーザーが実行できないプロシージャが返された場合は、"N"。  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 文字列: ユーザーが**Sqltables**によって返されるすべてのテーブルに対して**SELECT**権限を持っている場合は、"Y" になります。ユーザーがアクセスできないテーブルが返された場合は、"N"。  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 ドライバーがサポートできるアクティブな環境の最大数を指定する SQLUS悪意のある値。 制限が指定されていない場合、または制限が不明な場合、この値は0に設定されます。  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3.0)  
 集計関数のサポートを列挙する SQLUINTEGER ビットマスク。  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 SQL-92 エントリレベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **ALTER DOMAIN**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。 SQL-92 完全レベル準拠のドライバーは、常にすべてのビットマスクを返します。 戻り値 "0" は、 **ALTER DOMAIN**ステートメントがサポートされていないことを意味します。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの横にかっこで囲まれています。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = ドメイン制約の追加がサポートされています (完全レベル)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter domain> \<set domain DEFAULT 句> サポートされています (完全レベル)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<制約名の定義句> は、名前付けドメインの制約 (中間レベル) でサポートされています  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<DROP DOMAIN CONSTRAINT 句> サポートされています (完全レベル)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter domain> \<DROP domain DEFAULT 句> サポートされています (完全レベル)  
  
 次のビットは、add \<domain constraint> が\<サポートされている場合 (SQL_AD_ADD_DOMAIN_CONSTRAINT ビットが設定されている場合)> サポートされる制約属性を指定します。  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (完全レベル) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (完全レベル) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (完全レベル) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (完全レベル)  
  
 SQL_ALTER_TABLE (ODBC 2.0)  
 データソースでサポートされている**ALTER TABLE**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの横にかっこで囲まれています。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<列の追加> 句がサポートされていますが、列の照合順序 (完全なレベル) を指定する機能があります (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<列の追加> 句がサポートされ、列の既定値を指定するファシリティ (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<列の追加> がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT = \<列の追加> 句がサポートされており、列の制約を指定するファシリティ (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<ADD TABLE 制約> 句がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<制約名の定義> 列およびテーブルの制約の名前付け (中間レベル) でサポートされています (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<列の削除> CASCADE がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<列の変更\<> DROP column DEFAULT 句> サポートされています (中間レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<DROP COLUMN> RESTRICT がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<DROP COLUMN> RESTRICT がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<列の変更\<> SET column DEFAULT 句> サポートされています (中間レベル) (ODBC 3.0)  
  
 次のビットでは、 \<列またはテーブルの制約を指定する場合> サポート制約属性が指定されています (SQL_AT_ADD_CONSTRAINT ビットが設定されています)。  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (フルレベル) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (完全レベル) (odbc 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (フルレベル) (odbc 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (完全レベル) (odbc 3.0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3.8)  
 ドライバーが接続ハンドルで関数を非同期的に実行できるかどうかを示す SQLUINTEGER 値。  
  
 SQL_ASYNC_DBC_CAPABLE = ドライバーは、接続関数を非同期的に実行できます。  
  
 SQL_ASYNC_DBC_NOT_CAPABLE = ドライバーは、接続関数を非同期的に実行することはできません。  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 ドライバーの非同期サポートのレベルを示す SQLUINTEGER 値。  
  
 SQL_AM_CONNECTION = 接続レベルの非同期実行はサポートされています。 特定の接続ハンドルに関連付けられているすべてのステートメントハンドルが非同期モードであるか、またはすべてが同期モードであるかのいずれかです。 接続のステートメントハンドルを非同期モードにすることはできません。同じ接続上の別のステートメントハンドルは同期モードであり、その逆も同様です。  
  
 SQL_AM_STATEMENT = ステートメントレベルの非同期実行がサポートされています。 接続ハンドルに関連付けられている一部のステートメントハンドルは非同期モードである場合がありますが、同じ接続上の他のステートメントハンドルは同期モードです。  
  
 SQL_AM_NONE = 非同期モードはサポートされていません。  
  
 SQL_ASYNC_NOTIFICATION  
 ドライバーが非同期通知をサポートするかどうかを示す SQLUINTEGER 値。  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE**非同期実行通知は、ドライバーによってサポートされています。  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE**非同期実行通知は、ドライバーではサポートされていません。  
  
 ODBC の非同期操作には、接続レベルの非同期操作とステートメントレベルの非同期操作の2つのカテゴリがあります。  ドライバーが SQL_ASYNC_NOTIFICATION_CAPABLE を返す場合、非同期に実行できるすべての Api の通知をサポートする必要があります。  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 行数の可用性に関してドライバーの動作を列挙する SQLUINTEGER ビットマスク。 次のビットマスクは、情報の種類と共に使用されます。  
  
 SQL_BRC_ROLLED_UP = 連続する INSERT、DELETE、または UPDATE ステートメントの行数が1にロールアップされます。 このビットが設定されていない場合は、ステートメントごとに行数を使用できます。  
  
 SQL_BRC_PROCEDURES = 行カウント (存在する場合) は、ストアドプロシージャでバッチが実行されるときに使用できます。 行数が使用可能な場合は、SQL_BRC_ROLLED_UP ビットに応じて、ロールアップすることも、個別に使用することもできます。  
  
 SQL_BRC_EXPLICIT = 行カウント (存在する場合) は、 **Sqlexecute**または**SQLExecDirect**を呼び出すことによって直接バッチが実行されるときに使用できます。 行数が使用可能な場合は、SQL_BRC_ROLLED_UP ビットに応じて、ロールアップすることも、個別に使用することもできます。  
  
 SQL_BATCH_SUPPORT (ODBC 3.0)  
 バッチのドライバーのサポートを列挙する SQLUINTEGER ビットマスク。 サポートされているレベルを判別するには、次のビットマスクを使用します。  
  
 SQL_BS_SELECT_EXPLICIT = ドライバーは、結果セットを生成するステートメントを持つことができる明示的なバッチをサポートしています。  
  
 SQL_BS_ROW_COUNT_EXPLICIT = ドライバーは、行カウントを生成するステートメントを持つことができる明示的なバッチをサポートしています。  
  
 SQL_BS_SELECT_PROC = ドライバーは、結果セットを生成するステートメントを作成できる明示的なプロシージャをサポートしています。  
  
 SQL_BS_ROW_COUNT_PROC = ドライバーは、行カウントを生成するステートメントを持つことができる明示的なプロシージャをサポートしています。  
  
 SQL_BOOKMARK_PERSISTENCE (ODBC 2.0)  
 ブックマークが永続化される操作を列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクをフラグと共に使用して、ブックマークを保持するオプションを決定します。  
  
 SQL_BP_CLOSE = ブックマークは、アプリケーションが SQL_CLOSE オプションを使用して**SQLFreeStmt**を呼び出した後 **、または**ステートメントに関連付けられているカーソルを閉じる場合に有効です。  
  
 SQL_BP_DELETE = 行が削除された後、その行のブックマークは有効です。  
  
 SQL_BP_DROP = ブックマークは、アプリケーションが SQL_HANDLE_STMT の*Handletype*を使用して**sqlfreehandle**を呼び出し、ステートメントを削除した後に有効になります。  
  
 SQL_BP_TRANSACTION = ブックマークは、アプリケーションがトランザクションをコミットまたはロールバックした後に有効になります。  
  
 SQL_BP_UPDATE = 行のブックマークは、その行の列が更新された後 (キー列を含む) に有効になります。  
  
 SQL_BP_OTHER_HSTMT = 1 つのステートメントに関連付けられているブックマークは、別のステートメントと共に使用できます。 SQL_BP_CLOSE または SQL_BP_DROP が指定されていない場合は、最初のステートメントのカーソルが開いている必要があります。  
  
 SQL_CATALOG_LOCATION (ODBC 2.0)  
 修飾されたテーブル名のカタログの位置を示す SQLUS悪意のある値。  
  
 SQL_CL_STARTSQL_CL_END  
  
 たとえば、Xbase ドライバーは SQL_CL_START を返します。これは、\EMPDATA\EMP. のように、ディレクトリ (カタログ) 名がテーブル名の先頭にあるためです。.DBF. ORACLE サーバードライバーは SQL_CL_END を返します。これは、カタログがのようにADMIN.EMP@EMPDATAテーブル名の末尾にあるためです。  
  
 SQL-92 の完全なレベルに準拠したドライバーは、常に SQL_CL_START を返します。 データソースでカタログがサポートされていない場合は、値0が返されます。 カタログがサポートされているかどうかを判断するために、アプリケーションは SQL_CATALOG_NAME 情報の種類を使用して**SQLGetInfo**を呼び出します。  
  
 Odbc 2.0 *InfoType* SQL_QUALIFIER_LOCATION から、odbc 3.0 のこの*InfoType*の名前が変更されました。  
  
 SQL_CATALOG_NAME (ODBC 3.0)  
 文字列。サーバーでカタログ名がサポートされている場合は "Y"、そうでない場合は "N" です。  
  
 SQL-92 完全レベル準拠のドライバーは、常に "Y" を返します。  
  
 SQL_CATALOG_NAME_SEPARATOR (ODBC 1.0)  
 文字列: カタログ名と、その後またはその前にある修飾名要素との間の区切り記号として、データソースが定義する文字または文字。  
  
 カタログがデータソースでサポートされていない場合は、空の文字列が返されます。 カタログがサポートされているかどうかを判断するために、アプリケーションは SQL_CATALOG_NAME 情報の種類を使用して**SQLGetInfo**を呼び出します。 SQL-92 完全レベル準拠のドライバーは、常に "." を返します。  
  
 Odbc 2.0 *InfoType* SQL_QUALIFIER_NAME_SEPARATOR から、odbc 3.0 のこの*InfoType*の名前が変更されました。  
  
 SQL_CATALOG_TERM (ODBC 1.0)  
 データソースベンダーのカタログ名を含む文字列。たとえば、"database" や "directory" などです。 この文字列の大文字と小文字の区別、または大文字と小文字を混在させることができます。  
  
 カタログがデータソースでサポートされていない場合は、空の文字列が返されます。 カタログがサポートされているかどうかを判断するために、アプリケーションは SQL_CATALOG_NAME 情報の種類を使用して**SQLGetInfo**を呼び出します。 SQL-92 完全レベル準拠のドライバーは、常に "catalog" を返します。  
  
 Odbc 2.0 *InfoType* SQL_QUALIFIER_TERM から、odbc 3.0 のこの*InfoType*の名前が変更されました。  
  
 SQL_CATALOG_USAGE (ODBC 2.0)  
 カタログを使用できるステートメントを列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクは、カタログを使用できる場所を決定するために使用されます。  
  
 SQL_CU_DML_STATEMENTS = カタログは、すべてのデータ操作言語ステートメントでサポートされています。 **select**、 **INSERT**、 **UPDATE**、 **DELETE**、およびサポートされている場合は**select、update** 、および where update および DELETE ステートメント。  
  
 SQL_CU_PROCEDURE_INVOCATION = カタログは、ODBC プロシージャ呼び出しステートメントでサポートされています。  
  
 SQL_CU_TABLE_DEFINITION = カタログは、すべてのテーブル定義ステートメント ( **CREATE TABLE**、 **CREATE VIEW**、 **ALTER Table**、 **drop table**、 **drop view**) でサポートされています。  
  
 SQL_CU_INDEX_DEFINITION = カタログは、 **CREATE index**および**DROP INDEX**のすべてのインデックス定義ステートメントでサポートされています。  
  
 SQL_CU_PRIVILEGE_DEFINITION = カタログは、すべての特権定義ステートメント ( **GRANT**および**REVOKE**) でサポートされます。  
  
 データソースでカタログがサポートされていない場合は、値0が返されます。 カタログがサポートされているかどうかを判断するために、アプリケーションは SQL_CATALOG_NAME 情報の種類を使用して**SQLGetInfo**を呼び出します。 SQL-92 の完全な準拠のドライバーは、これらのすべてのビットが設定されたビットマスクを常に返します。  
  
 Odbc 2.0 *InfoType* SQL_QUALIFIER_USAGE から、odbc 3.0 のこの*InfoType*の名前が変更されました。  
  
 SQL_COLLATION_SEQ (ODBC 3.0)  
 照合順序の名前。 このサーバーの既定の文字セットの既定の照合順序の名前を示す文字列を指定します (たとえば、' ISO 8859-1 ' や EBCDIC)。 この値が不明な場合は、空の文字列が返されます。 SQL-92 完全レベル準拠のドライバーは、常に空でない文字列を返します。  
  
 SQL_COLUMN_ALIAS (ODBC 2.0)  
 文字列。データソースで列の別名がサポートされている場合は "Y" になります。それ以外の場合は、"N" です。  
  
 列の別名は、AS 句を使用して、選択リスト内の列に対して指定できる代替名です。 SQL-92 エントリレベル準拠のドライバーは、常に "Y" を返します。  
  
 SQL_CONCAT_NULL_BEHAVIOR (ODBC 1.0)  
 データソースが null 値以外の文字データ型の列を持つ NULL 値文字データ型の列の連結を処理する方法を示す SQLUS悪意のある値。  
  
 SQL_CB_NULL = 結果が NULL 値です。  
  
 SQL_CB_NON_NULL = 結果は、NULL 以外の値の列を連結したものです。  
  
 SQL-92 エントリレベル準拠のドライバーは、常に SQL_CB_NULL を返します。  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1.0)  
 SQLUINTEGER ビットマスクです。 ビットマスクは、 *InfoType*で指定された型のデータに対する**CONVERT**スカラー関数を使用して、データソースによってサポートされる変換を示します。 ビットマスクが0の場合、データソースは、同じデータ型への変換を含め、名前付きの型のデータからの変換をサポートしていません。  
  
 たとえば、データソースが SQL_INTEGER データから SQL_BIGINT データ型への変換をサポートしているかどうかを判断するために、アプリケーションは SQL_CONVERT_INTEGER の*InfoType*を使用して**SQLGetInfo**を呼び出します。 アプリケーションは、返されたビットマスクと SQL_CVT_BIGINT を使用**して and**演算を実行します。 結果の値が0以外の場合は、変換がサポートされます。  
  
 サポートされている変換を判断するには、次のビットマスクを使用します。  
  
 SQL_CVT_BIGINT (ODBC 1.0) SQL_CVT_BINARY (ODBC 1.0) SQL_CVT_BIT (ODBC 1.0) SQL_CVT_GUID (ODBC 3.5) SQL_CVT_CHAR (ODBC 1.0) SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DECIMAL (ODBC 1.0) SQL_CVT_DOUBLE (ODBC 1.0) SQL_CVT_FLOAT (ODBC 1.0) SQL_CVT_INTEGER (ODBC 1.0) SQL_CVT_INTERVAL_YEAR_MONTH (ODBC 1.0) SQL_CVT_INTERVAL_DAY_TIME (ODBC 1.0) SQL_CVT_LONGVARBINARY (ODBC 1.0) SQL_CVT_LONGVARCHAR (ODBC 1.0) SQL_CVT_NUMERICCVT_REAL ODBC 1.0) SQL_CVT_SMALLINT (ODBC 1.0) SQL_CVT_TIME (ODBC 1.0) SQL_CVT_TIMESTAMP (ODBC 1.0) SQL_CVT_TINYINT (ODBC 1.0) SQL_CVT_VARBINARY (ODBC 1.0) SQL_CVT_VARCHAR (ODBC 1.0)  
  
 SQL_CONVERT_FUNCTIONS (ODBC 1.0)  
 ドライバーと関連付けられたデータソースでサポートされているスカラー変換関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている変換関数を確認するには、次のビットマスクを使用します。  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME (ODBC 1.0)  
 テーブル相関名がサポートされているかどうかを示す SQLUS悪意のある値。  
  
 SQL_CN_NONE = 相関名はサポートされていません。  
  
 SQL_CN_DIFFERENT = 相関名はサポートされていますが、それが表すテーブルの名前とは異なる必要があります。  
  
 SQL_CN_ANY = 相関名はサポートされており、任意の有効なユーザー定義名を指定できます。  
  
 SQL-92 エントリレベル準拠のドライバーは、常に SQL_CN_ANY を返します。  
  
 SQL_CREATE_ASSERTION (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **CREATE ASSERTION**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_CA_CREATE_ASSERTION  
  
 制約属性を明示的に指定する機能がサポートされている場合、次のビットはサポートされる制約属性を指定します (SQL_ALTER_TABLE と SQL_CREATE_TABLE の情報の種類を参照してください)。  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 SQL-92 フルレベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。 戻り値 "0" は、 **CREATE ASSERTION**ステートメントがサポートされていないことを意味します。  
  
 SQL_CREATE_CHARACTER_SET (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **CREATE CHARACTER SET**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 SQL-92 フルレベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。 戻り値 "0" は、 **CREATE CHARACTER SET**ステートメントがサポートされていないことを意味します。  
  
 SQL_CREATE_COLLATION (ODBC 3.0)  
 データソースでサポートされている、SQL-92 で定義されている**CREATE COLLATION**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_CCOL_CREATE_COLLATION  
  
 SQL-92 の完全なレベルに準拠したドライバーは、常にサポート対象としてこのオプションを返します。 戻り値 "0" は、 **CREATE COLLATION**ステートメントがサポートされていないことを意味します。  
  
 SQL_CREATE_DOMAIN (ODBC 3.0)  
 データソースでサポートされている、SQL-92 で定義されている**CREATE DOMAIN**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_CDO_CREATE_DOMAIN = CREATE DOMAIN ステートメントがサポートされています (中間レベル)。  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION = \<制約名の定義>、ドメインの制約の名前付け (中間レベル) でサポートされています。  
  
 列の制約を作成する機能を指定するには、次のビットを指定します。 SQL_CDO_DEFAULT = ドメインの制約の指定はサポートされています (中間レベル) SQL_CDO_CONSTRAINT = ドメインの既定値の指定はサポートされています (中間レベル) SQL_CDO_COLLATION = ドメインの照合順序の指定はサポートされていません  
  
 次のビットは、ドメインの制約を指定する場合にサポートされる制約属性を指定します (SQL_CDO_DEFAULT が設定されています)。  
  
 SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (完全レベル) SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (完全レベル) SQL_CDO_CONSTRAINT_DEFERRABLE (完全レベル) SQL_CDO_CONSTRAINT_NON_DEFERRABLE (完全レベル)  
  
 戻り値 "0" は、 **CREATE DOMAIN**ステートメントがサポートされていないことを意味します。  
  
 SQL_CREATE_SCHEMA (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **CREATE SCHEMA**ステートメントの句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 SQL 92 の中間レベル準拠のドライバーは、常に SQL_CS_CREATE_SCHEMA と SQL_CS_AUTHORIZATION のオプションをサポート対象として返します。 これらは、sql-92 エントリレベルでもサポートされている必要がありますが、必ずしも SQL ステートメントとは限りません。 SQL-92 フルレベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。  
  
 SQL_CREATE_TABLE (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **CREATE TABLE**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの横にかっこで囲まれています。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_CT_CREATE_TABLE = CREATE TABLE ステートメントはサポートされています。 (エントリレベル)  
  
 SQL_CT_TABLE_CONSTRAINT = テーブル制約の指定はサポートされています (FIPS 移行レベル)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION = 列\<およびテーブルの制約の名前付け (中間レベル) では、制約名の定義> 句がサポートされています。  
  
 次のビットは、一時テーブルを作成する機能を指定します。  
  
 SQL_CT_COMMIT_PRESERVE = 削除された行はコミット時に保持されます。 (完全レベル)SQL_CT_COMMIT_DELETE = 削除された行はコミット時に削除されます。 (完全レベル)SQL_CT_GLOBAL_TEMPORARY = グローバル一時テーブルを作成できます。 (完全レベル)SQL_CT_LOCAL_TEMPORARY = ローカル一時テーブルを作成できます。 (完全レベル)  
  
 次のビットは、列制約を作成する機能を指定します。  
  
 SQL_CT_COLUMN_CONSTRAINT = 列の制約の指定はサポートされています (FIPS 移行レベル) SQL_CT_COLUMN_DEFAULT = 列の既定値の指定はサポートされています (FIPS 移行レベル) SQL_CT_COLUMN_COLLATION = 列の照合順序の指定はサポートされています (完全レベル)  
  
 次のビットは、列またはテーブルの制約を指定する場合にサポートされる制約属性を指定します。  
  
 SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (完全レベル) SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (完全レベル) SQL_CT_CONSTRAINT_DEFERRABLE (完全レベル) SQL_CT_CONSTRAINT_NON_DEFERRABLE (完全レベル)  
  
 SQL_CREATE_TRANSLATION (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **CREATE TRANSLATION**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 SQL-92 完全レベル準拠のドライバーは、常にこれらのオプションをサポート対象として返します。 戻り値 "0" は、 **CREATE TRANSLATION**ステートメントがサポートされていないことを意味します。  
  
 SQL_CREATE_VIEW (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **CREATE VIEW**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 戻り値 "0" は、 **CREATE VIEW**ステートメントがサポートされていないことを意味します。  
  
 SQL-92 エントリレベル準拠のドライバーは、常に SQL_CV_CREATE_VIEW と SQL_CV_CHECK_OPTION のオプションをサポート対象として返します。  
  
 SQL-92 フルレベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。  
  
 SQL_CURSOR_COMMIT_BEHAVIOR (ODBC 1.0)  
 データソース内のカーソルおよび準備されたステートメントに**コミット**操作がどのように影響するかを示す SQLUS悪意のある値 (トランザクションのコミット時のデータソースの動作)。  
  
 この属性の値には、次の設定の現在の状態が反映されます: SQL_COPT_SS_PRESERVE_CURSORS。  
  
 SQL_CB_DELETE = カーソルを閉じ、準備されたステートメントを削除します。 再びカーソルを使用するには、アプリケーションでステートメントを再準備し、再実行する必要があります。  
  
 SQL_CB_CLOSE = カーソルを閉じる。 準備されたステートメントの場合、アプリケーションは**SQLPrepare**を再度呼び出すことなく、ステートメントに対して**sqlexecute**を呼び出すことができます。 SQL ODBC ドライバーの既定値は SQL_CB_CLOSE です。 これは、トランザクションをコミットするときに、SQL ODBC ドライバーがカーソルを閉じることを意味します。  
  
 SQL_CB_PRESERVE =**コミット**操作前と同じ位置にカーソルを保持します。 アプリケーションはデータのフェッチを続行できます。また、再準備せずに、カーソルを閉じてステートメントを再実行することもできます。  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR (ODBC 1.0)  
 データソース内のカーソルおよび準備されたステートメントに**ロールバック**操作がどのように影響するかを示す SQLUS悪意のある値。  
  
 SQL_CB_DELETE = カーソルを閉じ、準備されたステートメントを削除します。 再びカーソルを使用するには、アプリケーションでステートメントを再準備し、再実行する必要があります。  
  
 SQL_CB_CLOSE = カーソルを閉じる。 準備されたステートメントの場合、アプリケーションは**SQLPrepare**を再度呼び出すことなく、ステートメントに対して**sqlexecute**を呼び出すことができます。  
  
 SQL_CB_PRESERVE =**ロールバック**操作前と同じ位置にカーソルを保持します。 アプリケーションでは、データのフェッチを続行することも、カーソルを閉じて再準備せずにステートメントを再実行することもできます。  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3.0)  
 カーソルの感度のサポートを示す SQLUINTEGER 値:  
  
 SQL_INSENSITIVE = ステートメントハンドルのすべてのカーソルは、同じトランザクション内の他のカーソルによって行われた変更を反映せずに、結果セットを表示します。  
  
 SQL_UNSPECIFIED = ステートメントハンドル上のカーソルが、同じトランザクション内の別のカーソルによって結果セットに加えられた変更を表示するかどうかは指定されていません。 ステートメントハンドルのカーソルによって、none、some、またはすべての変更が表示される場合があります。  
  
 SQL_SENSITIVE = カーソルは、同じトランザクション内の他のカーソルによって行われた変更の影響を受けます。  
  
 SQL-92 エントリレベル準拠のドライバーは、常に SQL_UNSPECIFIED オプションをサポート対象として返します。  
  
 SQL-92 の完全なレベルに準拠したドライバーは、常に SQL_INSENSITIVE オプションをサポート対象として返します。  
  
 SQL_DATA_SOURCE_NAME (ODBC 1.0)  
 接続時に使用されたデータソース名を含む文字列。 アプリケーションが**SQLConnect**を呼び出した場合、これは*szdsn*引数の値です。 アプリケーションが**SQLDriverConnect**または**SQLBrowseConnect**という名前の場合、これはドライバーに渡された接続文字列の DSN キーワードの値になります。 接続文字列に**DSN**キーワードが含まれていない場合 ( **DRIVER**キーワードが含まれている場合など)、これは空の文字列になります。  
  
 SQL_DATA_SOURCE_READ_ONLY (ODBC 1.0)  
 文字列。 データソースが読み取り専用モードに設定されている場合は "Y"、それ以外の場合は "N"。  
  
 この特性は、データソース自体にのみ関連します。データソースへのアクセスを可能にするドライバーの特性ではありません。 読み取り/書き込み可能なドライバーは、読み取り専用のデータソースで使用できます。 ドライバーが読み取り専用の場合、そのすべてのデータソースは読み取り専用である必要があり、SQL_DATA_SOURCE_READ_ONLY を返す必要があります。  
  
 SQL_DATABASE_NAME (ODBC 1.0)  
 "Database" という名前のオブジェクトがデータソースによって定義されている場合は、現在のデータベース名を使用した文字列。  
  
> [!NOTE]
>  ODBC 3.x で*は、この* *InfoType*に対して返される値は、SQL_ATTR_CURRENT_CATALOG の*属性*引数を指定して**sqlgetconnectattr**を呼び出すことによっても返すことができます。  
  
 SQL_DATETIME_LITERALS (ODBC 3.0)  
 データソースでサポートされている SQL 92 datetime リテラルを列挙する SQLUINTEGER ビットマスク。 これらは、SQL-92 仕様に記載されている datetime リテラルであり、ODBC で定義されている datetime リテラルエスケープ句とは別のものであることに注意してください。 ODBC datetime リテラルエスケープ句の詳細については、「[日付、時刻、およびタイムスタンプリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)」を参照してください。  
  
 FIPS 移行レベル準拠のドライバーは、次の一覧にあるビットのビットマスクの "1" 値を常に返します。 値 "0" は、SQL-92 の datetime リテラルがサポートされていないことを意味します。  
  
 サポートされているリテラルを判別するには、次のビットマスクを使用します。  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME (ODBC 1.0)  
 ドライバーによってアクセスされる DBMS 製品の名前を含む文字列。  
  
 SQL_DBMS_VER (ODBC 1.0)  
 ドライバーによってアクセスされる DBMS 製品のバージョンを示す文字列。 バージョンの形式は # #. # #. # # # # です。最初の2桁はメジャーバージョン、次の2桁はマイナーバージョン、最後の4桁はリリースバージョンです。 ドライバーは DBMS 製品バージョンをこの形式で表示する必要がありますが、DBMS 製品固有バージョンを追加することもできます。 たとえば、"04.01.0000 Rdb 4.1" のようになります。  
  
 SQL_DDL_INDEX (ODBC 3.0)  
 インデックスの作成と削除のサポートを示す SQLUINTEGER 値:  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION (ODBC 1.0)  
 ドライバーまたはデータソースでサポートされている既定のトランザクション分離レベルを示す SQLUINTEGER 値。データソースでトランザクションがサポートされていない場合は0。 トランザクション分離レベルを定義するには、次の用語を使用します。  
  
 **ダーティリード**トランザクション1行を変更します。 トランザクション2は、トランザクション1が変更をコミットする前に、変更された行を読み取ります。 トランザクション1が変更をロールバックすると、トランザクション2は、存在していないと見なされる行を読み取ります。  
  
 **反復不能読み取り**トランザクション1行を読み取ります。 トランザクション2は、その行を更新または削除し、この変更をコミットします。 トランザクション1が行を再読み込みしようとすると、異なる行値を受け取るか、その行が削除されたことが検出されます。  
  
 **ファントム**トランザクション1は、いくつかの検索条件を満たす行のセットを読み取ります。 トランザクション2では、検索条件に一致する1つ以上の行 (挿入または更新のいずれか) が生成されます。 トランザクション1が行を読み取るステートメントを再実行すると、別の行のセットが返されます。  
  
 データソースでトランザクションがサポートされている場合、ドライバーは次のビットマスクのうちの1つを返します。  
  
 SQL_TXN_READ_UNCOMMITTED = ダーティリード、反復不能な読み取り、およびファントムが可能です。  
  
 SQL_TXN_READ_COMMITTED = ダーティリードは使用できません。 反復不可能な読み取りとファントムが可能です。  
  
 SQL_TXN_REPEATABLE_READ = ダーティ読み取りと反復不可能な読み取りは使用できません。 ファントムが可能です。  
  
 SQL_TXN_SERIALIZABLE = トランザクションはシリアル化できます。 シリアル化可能なトランザクションでは、ダーティリード、反復不能読み取り、またはファントムは使用できません。  
  
 SQL_DESCRIBE_PARAMETER (ODBC 3.0)  
 文字列。パラメーターを記述できる場合は "Y"。"N" (存在しない場合)。  
  
 SQL-92 完全レベル準拠のドライバーは、通常、"Y" を返します。これは、**記述の INPUT**ステートメントをサポートするためです。 ただし、これによって基になる SQL サポートが直接指定されるわけではないため、SQL 92 の完全な準拠のドライバーであっても、パラメーターの記述はサポートされていない可能性があります。  
  
 SQL_DM_VER (ODBC 3.0)  
 ドライバーマネージャーのバージョンを含む文字列。 バージョンは、# #. # #. # # # #. # # # # の形式になります。  
  
 2桁の最初のセットは、定数 SQL_SPEC_MAJOR によって指定された主要な ODBC バージョンです。  
  
 2桁の2番目のセットは、定数 SQL_SPEC_MINOR によって指定されたマイナー ODBC バージョンです。  
  
 4桁の3番目のセットは、ドライバーマネージャーのメジャービルド番号です。  
  
 最後の4桁の数字は、ドライバーマネージャーのマイナービルド番号です。  
  
 Windows 7 Driver Manager のバージョンは03.80 です。 Windows 8 Driver Manager バージョンは03.81 です。  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3.8)  
 ドライバーがドライバー対応のプーリングをサポートするかどうかを示す SQLUINTEGER 値。 (詳細については、「[ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)」を参照してください。  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE は、ドライバーがドライバー対応のプーリング機構をサポートしていることを示します。  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE は、ドライバーがドライバー対応のプーリング機構をサポートしていないことを示します。  
  
 ドライバーは SQL_DRIVER_AWARE_POOLING_SUPPORTED を実装する必要がなく、ドライバーマネージャーはドライバーの戻り値を受け入れません。  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV (ODBC 1.0)  
 引数*InfoType*によって決定される、ドライバーの環境ハンドルまたは接続ハンドルである SQLULEN 値。  
  
 これらの情報の種類は、ドライバーマネージャーだけで実装されています。  
  
 SQL_DRIVER_HDESC (ODBC 3.0)  
 ドライバーマネージャーの記述子ハンドルによって決定されるドライバーの記述子ハンドルである sqlulen 値。アプリケーションから\* *infovalueptr*の入力に渡す必要があります。 この場合、 *Infovalueptr*は入力引数と出力引数の両方です。 \* *Infovalueptr*で渡された入力記述子ハンドルは、明示的に、または*connectionhandle*で暗黙的に割り当てられている必要があります。  
  
 アプリケーションは、この情報型を使用して**SQLGetInfo**を呼び出す前に、ドライバーマネージャーの記述子ハンドルのコピーを作成して、ハンドルが出力時に上書きされないようにする必要があります。  
  
 この情報の種類は、ドライバーマネージャーだけで実装されています。  
  
 SQL_DRIVER_HLIB (ODBC 2.0)  
 Microsoft Windows オペレーティングシステムにドライバー DLL が読み込まれたとき、またはそれと同等のオペレーティングシステムに対応するために、ロードライブラリからドライバーマネージャーに返された*hinst*の SQLULEN 値。 ハンドルは、 **SQLGetInfo**の呼び出しで指定された接続ハンドルに対してのみ有効です。  
  
 この情報の種類は、ドライバーマネージャーだけで実装されています。  
  
 SQL_DRIVER_HSTMT (ODBC 1.0)  
 ドライバーマネージャーのステートメントハンドルによって決定されるドライバーのステートメントハンドルである sqlulen 値。アプリケーションから\* *infovalueptr*の入力で渡す必要があります。 この場合、 *Infovalueptr*は入力引数と出力引数の両方です。 \* *Infovalueptr*で渡された入力ステートメントハンドルは、引数*connectionhandle*で割り当てられている必要があります。  
  
 アプリケーションは、この情報の種類を使用して**SQLGetInfo**を呼び出す前に、ドライバーマネージャーのステートメントハンドルのコピーを作成して、ハンドルが出力時に上書きされないようにする必要があります。  
  
 この情報の種類は、ドライバーマネージャーだけで実装されています。  
  
 SQL_DRIVER_NAME (ODBC 1.0)  
 データソースへのアクセスに使用するドライバーのファイル名を含む文字列。  
  
 SQL_DRIVER_ODBC_VER (ODBC 2.0)  
 ドライバーがサポートしている ODBC のバージョンを含む文字列。 バージョンは # #. # # の形式です。最初の2桁はメジャーバージョンで、次の2桁はマイナーバージョンです。 SQL_SPEC_MAJOR と SQL_SPEC_MINOR は、メジャーバージョン番号とマイナーバージョン番号を定義します。 このマニュアルに記載されている ODBC のバージョンでは、これらは3と0であり、ドライバーは "03.00" を返します。  
  
 ODBC ドライバーマネージャーは、既存のアプリケーションの旧バージョンとの互換性を維持するために、SQLGetInfo (SQL_DRIVER_ODBC_VER) の戻り値を変更しません。 ドライバーでは、返される値を指定します。 ただし、C データ型の拡張機能をサポートするドライバーは、SQL_ATTR_ODBC_VERSION を3.8 に設定するために**SQLSetEnvAttr**を呼び出すときに 3.8 (またはそれ以降) を返す必要があります。 詳細については、「 [ODBC の C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)」を参照してください。  
  
 SQL_DRIVER_VER (ODBC 1.0)  
 ドライバーのバージョンを含む文字列。必要に応じて、ドライバーの説明を指定します。 少なくとも、バージョンは # #. # #. # # # # という形式です。最初の2桁はメジャーバージョン、次の2桁はマイナーバージョン、最後の4桁はリリースバージョンです。  
  
 SQL_DROP_ASSERTION (ODBC 3.0)  
 データソースでサポートされている、SQL-92 で定義されている**DROP ASSERTION**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_DA_DROP_ASSERTION  
  
 SQL-92 の完全なレベルに準拠したドライバーは、常にサポート対象としてこのオプションを返します。  
  
 SQL_DROP_CHARACTER_SET (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **DROP CHARACTER SET**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 SQL-92 の完全なレベルに準拠したドライバーは、常にサポート対象としてこのオプションを返します。  
  
 SQL_DROP_COLLATION (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されている**DROP COLLATION**ステートメントの句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_DC_DROP_COLLATION  
  
 SQL-92 の完全なレベルに準拠したドライバーは、常にサポート対象としてこのオプションを返します。  
  
 SQL_DROP_DOMAIN (ODBC 3.0)  
 データソースでサポートされている、SQL-92 で定義されている**DROP DOMAIN**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 SQL 92 の中間レベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。  
  
 SQL_DROP_SCHEMA (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **DROP SCHEMA**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 SQL 92 の中間レベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。  
  
 SQL_DROP_TABLE (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **DROP TABLE**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 FIPS 移行レベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。  
  
 SQL_DROP_TRANSLATION (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **DROP TRANSLATION**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_DTR_DROP_TRANSLATION  
  
 SQL-92 の完全なレベルに準拠したドライバーは、常にサポート対象としてこのオプションを返します。  
  
 SQL_DROP_VIEW (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **DROP VIEW**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 FIPS 移行レベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (ODBC 3.0)  
 ドライバーによってサポートされる動的カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の最初のサブセットが含まれます。2番目のサブセットについては、「SQL_DYNAMIC_CURSOR_ATTRIBUTES2」を参照してください。  
  
 サポートされている属性を判別するには、次のビットマスクを使用します。  
  
 SQL_CA1_NEXT = カーソルが動的カーソルの場合、 **Sqlfetchscroll**を呼び出すと、SQL_FETCH_NEXT の*fetchorientation*引数がサポートされます。  
  
 SQL_CA1_ABSOLUTE = カーソルが動的カーソルの場合、 **Sqlfetchscroll**を呼び出すと、SQL_FETCH_FIRST、SQL_FETCH_LAST、および SQL_FETCH_ABSOLUTE の*fetchorientation*引数がサポートされます。 (フェッチされる行セットは、現在のカーソル位置とは無関係です)。  
  
 SQL_CA1_RELATIVE = カーソルが動的カーソルの場合、 **Sqlfetchscroll**の呼び出しでは、SQL_FETCH_PRIOR と SQL_FETCH_RELATIVE の*fetchorientation*引数がサポートされています。 (フェッチされる行セットは、現在のカーソル位置によって異なります。 これは、順方向専用カーソルでは SQL_FETCH_NEXT のみがサポートされているため、SQL_FETCH_NEXT から分離されていることに注意してください。)  
  
 SQL_CA1_BOOKMARK = カーソルが動的カーソルの場合、 **Sqlfetchscroll**を呼び出すと、SQL_FETCH_BOOKMARK の*fetchorientation*引数がサポートされます。  
  
 SQL_CA1_LOCK_EXCLUSIVE = カーソルが動的カーソルの場合、 **SQLSetPos**の呼び出しでは SQL_LOCK_EXCLUSIVE の*LockType*引数がサポートされます。  
  
 SQL_CA1_LOCK_NO_CHANGE = カーソルが動的カーソルの場合、 **SQLSetPos**の呼び出しでは SQL_LOCK_NO_CHANGE の*LockType*引数がサポートされます。  
  
 SQL_CA1_LOCK_UNLOCK = カーソルが動的カーソルの場合、 **SQLSetPos**の呼び出しでは SQL_LOCK_UNLOCK の*LockType*引数がサポートされます。  
  
 SQL_CA1_POS_POSITION = カーソルが動的カーソルの場合、 **SQLSetPos**の呼び出しでは SQL_POSITION の*操作*引数がサポートされます。  
  
 SQL_CA1_POS_UPDATE = カーソルが動的カーソルの場合、 **SQLSetPos**の呼び出しでは SQL_UPDATE の*操作*引数がサポートされます。  
  
 SQL_CA1_POS_DELETE = カーソルが動的カーソルの場合、 **SQLSetPos**の呼び出しでは SQL_DELETE の*操作*引数がサポートされます。  
  
 SQL_CA1_POS_REFRESH = カーソルが動的カーソルの場合、 **SQLSetPos**の呼び出しでは SQL_REFRESH の*操作*引数がサポートされます。  
  
 SQL_CA1_POSITIONED_UPDATE = カーソルが動的カーソルの場合、現在の SQL ステートメントがサポートされている更新プログラムです。 (SQL-92 エントリレベル準拠のドライバーは、常にこのオプションをサポート対象として返します)。  
  
 SQL_CA1_POSITIONED_DELETE = カーソルが動的カーソルの場合は、現在の SQL ステートメントがサポートされている DELETE です。 (SQL-92 エントリレベル準拠のドライバーは、常にこのオプションをサポート対象として返します)。  
  
 SQL_CA1_SELECT_FOR_UPDATE = カーソルが動的カーソルの場合は、SELECT FOR UPDATE SQL ステートメントがサポートされます。 (SQL-92 エントリレベル準拠のドライバーは、常にこのオプションをサポート対象として返します)。  
  
 SQL_CA1_BULK_ADD = カーソルが動的カーソルの場合、 **Sqlbulkoperations**の呼び出しでは SQL_ADD の*操作*引数がサポートされます。  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK = カーソルが動的カーソルの場合、 **Sqlbulkoperations**の呼び出しでは SQL_UPDATE_BY_BOOKMARK の*操作*引数がサポートされます。  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK = カーソルが動的カーソルの場合、 **Sqlbulkoperations**の呼び出しでは SQL_DELETE_BY_BOOKMARK の*操作*引数がサポートされます。  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK = カーソルが動的カーソルの場合、 **Sqlbulkoperations**の呼び出しでは SQL_FETCH_BY_BOOKMARK の*操作*引数がサポートされます。  
  
 SQL 92 の中間レベル準拠のドライバーでは、通常、SQL_CA1_NEXT、SQL_CA1_ABSOLUTE、および SQL_CA1_RELATIVE のオプションがサポート対象として返されます。これは、埋め込み SQL FETCH ステートメントを使用してスクロール可能なカーソルをサポートするためです。 ただし、これによって基になる SQL のサポートが直接決定されるわけではないため、SQL 92 の中間レベル準拠のドライバーであっても、スクロール可能なカーソルはサポートされない可能性があります。  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (ODBC 3.0)  
 ドライバーによってサポートされる動的カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の2番目のサブセットが含まれます。最初のサブセットについては、「SQL_DYNAMIC_CURSOR_ATTRIBUTES1」を参照してください。  
  
 サポートされている属性を判別するには、次のビットマスクを使用します。  
  
 SQL_CA2_READ_ONLY_CONCURRENCY = 更新が許可されていない読み取り専用の動的カーソルがサポートされています。 (SQL_ATTR_CONCURRENCY ステートメント属性は、動的カーソルに対して SQL_CONCUR_READ_ONLY できます)。  
  
 SQL_CA2_LOCK_CONCURRENCY = 行を更新できるかどうかを確認するために十分なロックレベルを使用する動的カーソルがサポートされています。 (SQL_ATTR_CONCURRENCY ステートメント属性は、動的カーソルに対して SQL_CONCUR_LOCK できます)。これらのロックは、SQL_ATTR_TXN_ISOLATION 接続属性で設定されたトランザクション分離レベルと一致している必要があります。  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY = 行バージョンを比較するオプティミスティック同時実行制御を使用する動的カーソルがサポートされています。 (SQL_ATTR_CONCURRENCY ステートメント属性は、動的カーソルに対して SQL_CONCUR_ROWVER できます)。  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY = オプティミスティック同時実行制御を使用して値を比較する動的カーソルがサポートされています。 (SQL_ATTR_CONCURRENCY ステートメント属性は、動的カーソルに対して SQL_CONCUR_VALUES できます)。  
  
 SQL_CA2_SENSITIVITY_ADDITIONS = 追加された行は動的カーソルから参照できます。カーソルはその行までスクロールできます。 (これらの行がカーソルに追加される場所は、ドライバーによって異なります)。  
  
 SQL_CA2_SENSITIVITY_DELETIONS = 削除された行は、動的カーソルでは使用できなくなります。また、結果セットに "パンチ穴" を残しません。動的カーソルが削除された行からスクロールすると、その行に戻ることはできません。  
  
 SQL_CA2_SENSITIVITY_UPDATES = 行の更新は動的カーソルから参照できます。動的カーソルがからスクロールして更新された行に戻ると、カーソルによって返されるデータは、元のデータではなく更新されたデータになります。  
  
 SQL_CA2_MAX_ROWS_SELECT = カーソルが動的カーソルの場合、SQL_ATTR_MAX_ROWS statement 属性は**SELECT**ステートメントに影響します。  
  
 SQL_CA2_MAX_ROWS_INSERT = カーソルが動的カーソルの場合、SQL_ATTR_MAX_ROWS statement 属性は**INSERT**ステートメントに影響します。  
  
 SQL_CA2_MAX_ROWS_DELETE = カーソルが動的カーソルの場合、SQL_ATTR_MAX_ROWS statement 属性は**DELETE**ステートメントに影響します。  
  
 SQL_CA2_MAX_ROWS_UPDATE = カーソルが動的カーソルの場合、SQL_ATTR_MAX_ROWS statement 属性は**UPDATE**ステートメントに影響します。  
  
 SQL_CA2_MAX_ROWS_CATALOG = カーソルが動的カーソルの場合、SQL_ATTR_MAX_ROWS statement 属性は**カタログ**の結果セットに影響を及ぼします。  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL = カーソルが動的カーソルの場合、SQL_ATTR_MAX_ROWS statement 属性は、 **SELECT**、 **INSERT**、 **DELETE**、および**UPDATE**ステートメント、および**カタログ**の結果セットに影響します。  
  
 SQL_CA2_CRC_EXACT = カーソルが動的カーソルの場合、SQL_DIAG_CURSOR_ROW_COUNT 診断フィールドで正確な行数を使用できます。  
  
 SQL_CA2_CRC_APPROXIMATE = カーソルが動的カーソルの場合、SQL_DIAG_CURSOR_ROW_COUNT 診断フィールドにおおよその行数を使用できます。  
  
 SQL_CA2_SIMULATE_NON_UNIQUE = ドライバーは、カーソルが動的カーソルの場合に、シミュレートされた位置指定 update または delete ステートメントが1行にしか影響しないことを保証しません。このことを保証するのは、アプリケーションの役割です。 (ステートメントが複数の行に影響する場合、 **Sqlexecute**または**SQLExecDirect**は SQLSTATE 01001 [カーソル操作の競合] を返します)。この動作を設定するために、アプリケーションは SQL_ATTR_SIMULATE_CURSOR 属性を SQL_SC_NON_UNIQUE に設定して**SQLSetStmtAttr**を呼び出します。  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE = ドライバーは、カーソルが動的カーソルの場合に、シミュレートされた位置指定の update または delete ステートメントが1行にのみ影響することを保証しようとします。 ドライバーは、一意のキーがない場合など、複数の行に影響する可能性がある場合でも、常にこのようなステートメントを実行します。 (ステートメントが複数の行に影響する場合、 **Sqlexecute**または**SQLExecDirect**は SQLSTATE 01001 [カーソル操作の競合] を返します)。この動作を設定するために、アプリケーションは SQL_ATTR_SIMULATE_CURSOR 属性を SQL_SC_TRY_UNIQUE に設定して**SQLSetStmtAttr**を呼び出します。  
  
 SQL_CA2_SIMULATE_UNIQUE = ドライバーは、カーソルが動的カーソルの場合に、シミュレートされた位置指定 update または delete ステートメントが1行にしか影響しないことを保証します。 ドライバーが特定のステートメントに対してこれを保証できない場合、 **SQLExecDirect**または**SQLPrepare**は SQLSTATE 01001 (カーソル操作の競合) を返します。 この動作を設定するために、アプリケーションは SQL_ATTR_SIMULATE_CURSOR 属性を SQL_SC_UNIQUE に設定して**SQLSetStmtAttr**を呼び出します。  
  
 SQL_EXPRESSIONS_IN_ORDERBY (ODBC 1.0)  
 文字列: "Y" (データソースが**ORDER BY**リスト内の式をサポートする場合)。そうでない場合は "N" になります。  
  
 SQL_FILE_USAGE (ODBC 2.0)  
 1層ドライバーがデータソース内のファイルを直接どのように扱うかを示す SQLUS悪意のある値。  
  
 SQL_FILE_NOT_SUPPORTED = ドライバーが単一層のドライバーではありません。 たとえば、ORACLE ドライバーは2層ドライバーです。  
  
 SQL_FILE_TABLE = 1 層ドライバーは、データソース内のファイルをテーブルとして扱います。 たとえば、Xbase ドライバーでは、各 Xbase ファイルがテーブルとして扱われます。  
  
 SQL_FILE_CATALOG = 1 層ドライバーは、データソース内のファイルをカタログとして扱います。 たとえば、Microsoft Access ドライバーは、各 Microsoft Access ファイルを完全なデータベースとして扱います。  
  
 アプリケーションでこれを使用して、ユーザーがデータを選択する方法を決定する場合があります。 たとえば、Xbase ユーザーは多くの場合、データをファイルに格納していると考えていますが、ORACLE と Microsoft Access のユーザーは一般にテーブルに格納されているデータを考えます。  
  
 ユーザーが Xbase データソースを選択すると、[Windows**ファイルオープン**コモン] ダイアログボックスが表示されることがあります。ユーザーが Microsoft Access または ORACLE のデータソースを選択すると、アプリケーションで **[テーブルの選択**] ダイアログボックスが表示される場合があります。  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1 (ODBC 3.0)  
 ドライバーでサポートされている順方向専用カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の最初のサブセットが含まれます。2番目のサブセットについては、「SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2」を参照してください。  
  
 サポートされている属性を判別するには、次のビットマスクを使用します。  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 これらのビットマスクの説明については、「SQL_DYNAMIC_CURSOR_ATTRIBUTES1」を参照してください (および「動的カーソル」の「順方向専用カーソル」を参照してください)。  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2 (ODBC 3.0)  
 ドライバーでサポートされている順方向専用カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の2番目のサブセットが含まれます。最初のサブセットについては、「SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1」を参照してください。  
  
 サポートされている属性を判別するには、次のビットマスクを使用します。  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 これらのビットマスクの説明については、「SQL_DYNAMIC_CURSOR_ATTRIBUTES2」を参照してください (および「動的カーソル」の「順方向専用カーソル」を参照してください)。  
  
 SQL_GETDATA_EXTENSIONS (ODBC 2.0)  
 **SQLGetData**の拡張を列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクをフラグと共に使用して、ドライバーが**SQLGetData**に対してサポートする共通の拡張機能を決定します。  
  
 SQL_GD_ANY_COLUMN = **SQLGetData**は、バインドされていない列 (最後にバインドされた列の前を含む) に対して呼び出すことができます。 SQL_GD_ANY_ORDER も返されない限り、列を昇順に並べ替える必要があることに注意してください。  
  
 SQL_GD_ANY_ORDER = **SQLGetData**は、バインドされていない列に対して任意の順序で呼び出すことができます。 SQLGetData も返される SQL_GD_ANY_COLUMN 場合を除き、 **SQLGetData**は、最後にバインドされた列の後の列に対してのみ呼び出すことができます。  
  
 SQL_GD_BLOCK = **SQLSetPos**を使用してその行に配置した後、ブロック内の任意の行 (行セットサイズが1より大きい) のバインドされていない列に対しては、 **SQLGetData**を呼び出すことができます。  
  
 SQL_GD_BOUND = バインドされていない列に加えて、バインドされた列に対して**SQLGetData**を呼び出すことができます。 ドライバーは SQL_GD_ANY_COLUMN も返す場合を除き、この値を返すことはできません。  
  
 SQL_GD_OUTPUT_PARAMS = **SQLGetData**を呼び出して、出力パラメーターの値を返すことができます。 詳細については、「 [SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)」を参照してください。  
  
 **SQLGetData**は、最後にバインドされた列の後に出現するバインドされていない列からのみデータを返す必要があります。また、列番号が増加する順に呼び出され、行のブロックの行には含まれません。  
  
 ドライバーがブックマーク (固定長または可変長) をサポートしている場合は、列0の**SQLGetData**の呼び出しをサポートする必要があります。 このサポートは、ドライバーが SQL_GETDATA_EXTENSIONS *InfoType*を持つ**SQLGetInfo**の呼び出しに対して返す内容に関係なく必要です。  
  
 SQL_GROUP_BY (ODBC 2.0)  
 Select リスト内の**GROUP by**句の列と非集計の列の間のリレーションシップを指定する SQLUS悪意のある値。  
  
 SQL_GB_COLLATE = **COLLATE**句は、各グループ化列の最後に指定できます。 (ODBC 3.0)  
  
 SQL_GB_NOT_SUPPORTED = **GROUP BY**句はサポートされていません。 (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT = **GROUP BY**句には、選択リスト内のすべての非集計列が含まれている必要があります。 他の列を含めることはできません。 たとえば、 **[部門]、[部門別] の順に選択し**ます。 (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT = **GROUP BY**句には、選択リスト内のすべての非集計列が含まれている必要があります。 選択リストに含まれていない列を含めることができます。 たとえば、[部門]、 **[最大値 (給与)] の順に選択し**ます。 (ODBC 2.0)  
  
 SQL_GB_NO_RELATION = **GROUP by**句の列と選択リストが関連付けられていません。 グループ化されていない、選択リスト内の非集計列の意味は、データソースに依存します。 たとえば、 **[dept, SALARY BY dept, AGE] を選択し**ます。 (ODBC 2.0)  
  
 SQL-92 エントリレベル準拠のドライバーは、常に SQL_GB_GROUP_BY_EQUALS_SELECT オプションをサポート対象として返します。 SQL-92 の完全なレベルに準拠したドライバーは、常に SQL_GB_COLLATE オプションをサポート対象として返します。 どのオプションもサポートされていない場合、 **GROUP by**句はデータソースでサポートされません。  
  
 SQL_IDENTIFIER_CASE (ODBC 1.0)  
 次のような SQLUS悪意のある値。  
  
 SQL_IC_UPPER = SQL の識別子は大文字と小文字が区別されず、システムカタログでは大文字で格納されます。  
  
 SQL_IC_LOWER = SQL の識別子は大文字と小文字が区別されず、システムカタログで小文字で格納されます。  
  
 SQL_IC_SENSITIVE = SQL の識別子は大文字と小文字が区別され、システムカタログ内の大文字と小文字が混在して格納されます。  
  
 SQL_IC_MIXED = SQL の識別子は大文字と小文字が区別されず、システムカタログ内の大文字と小文字が混在して格納されます。  
  
 SQL-92 の識別子は大文字と小文字が区別されないため、厳密に SQL-92 (任意のレベル) に準拠しているドライバーは、SQL_IC_SENSITIVE オプションをサポート対象として返すことはありません。  
  
 SQL_IDENTIFIER_QUOTE_CHAR (ODBC 1.0)  
 SQL ステートメントで引用符で囲まれた (区切られた) 識別子の開始と終了の区切り記号として使用される文字列。 (ODBC 関数の引数として渡された識別子を引用符で囲む必要はありません)。データソースが引用符で囲まれた識別子をサポートしていない場合は、空白が返されます。  
  
 接続属性 SQL_ATTR_METADATA_ID が SQL_TRUE に設定されている場合は、この文字列を使用してカタログ関数の引数を引用符で囲むこともできます。  
  
 SQL-92 の識別子の引用符文字は二重引用符 (") であるため、厳密に SQL-92 に準拠しているドライバーは、常に二重引用符文字を返します。  
  
 SQL_INDEX_KEYWORDS (ODBC 3.0)  
 ドライバーでサポートされている CREATE INDEX ステートメント内のキーワードを列挙する SQLUINTEGER ビットマスク。  
  
 SQL_IK_NONE = キーワードはサポートされていません。  
  
 SQL_IK_ASC = ASC キーワードはサポートされています。  
  
 SQL_IK_DESC = DESC キーワードがサポートされています。  
  
 SQL_IK_ALL = すべてのキーワードがサポートされています。  
  
 CREATE INDEX ステートメントがサポートされているかどうかを確認するには、アプリケーションは SQL_DLL_INDEX 情報型を使用して**SQLGetInfo**を呼び出します。  
  
 SQL_INFO_SCHEMA_VIEWS (ODBC 3.0)  
 ドライバーでサポートされている INFORMATION_SCHEMA 内のビューを列挙する SQLUINTEGER ビットマスク。 INFORMATION_SCHEMA のビューおよびの内容は、SQL-92 で定義されています。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの横にかっこで囲まれています。  
  
 サポートされているビューを判別するには、次のビットマスクを使用します。  
  
 SQL_ISV_ASSERTIONS = 特定のユーザーによって所有されているカタログのアサーションを識別します。 (完全レベル)  
  
 SQL_ISV_CHARACTER_SETS = 特定のユーザーがアクセスできるカタログの文字セットを識別します。 (中間レベル)  
  
 SQL_ISV_CHECK_CONSTRAINTS = 特定のユーザーが所有する CHECK 制約を識別します。 (中間レベル)  
  
 SQL_ISV_COLLATIONS = 特定のユーザーがアクセスできるカタログの文字の照合順序を識別します。 (完全レベル)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE = カタログに定義されているドメインに依存し、特定のユーザーによって所有されているカタログの列を識別します。 (中間レベル)  
  
 SQL_ISV_COLUMN_PRIVILEGES = 特定のユーザーが使用できる、または特定のユーザーによって許可される永続テーブルの列に対する権限を識別します。 (FIPS 移行レベル)  
  
 SQL_ISV_COLUMNS = 特定のユーザーがアクセスできる永続テーブルの列を識別します。 (FIPS 移行レベル)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE = CONSTRAINT_TABLE_USAGE ビューに似ていますが、特定のユーザーによって所有されているさまざまな制約に対して列が識別されます。 (中間レベル)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE = 制約 (参照、一意、およびアサーション) によって使用され、特定のユーザーによって所有されているテーブルを識別します。 (中間レベル)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS = 特定のユーザーがアクセスできるドメインの制約 (カタログ内のドメイン) を識別します。 (中間レベル)  
  
 SQL_ISV_DOMAINS = ユーザーがアクセスできるカタログに定義されているドメインを識別します。 (中間レベル)  
  
 SQL_ISV_KEY_COLUMN_USAGE = 特定のユーザーによってキーとして制約されているカタログで定義されている列を識別します。 (中間レベル)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS = 特定のユーザーによって所有されている参照制約を識別します。 (中間レベル)  
  
 SQL_ISV_SCHEMATA = 特定のユーザーが所有するスキーマを識別します。 (中間レベル)  
  
 SQL_ISV_SQL_LANGUAGES = SQL の実装でサポートされている SQL の準拠レベル、オプション、および言語を識別します。 (中間レベル)  
  
 SQL_ISV_TABLE_CONSTRAINTS = 特定のユーザーが所有するテーブル制約を識別します。 (中間レベル)  
  
 SQL_ISV_TABLE_PRIVILEGES = 特定のユーザーが使用できる、または特定のユーザーによって許可される永続テーブルに対する権限を識別します。 (FIPS 移行レベル)  
  
 SQL_ISV_TABLES = 特定のユーザーがアクセスできる、カタログに定義されている永続テーブルを識別します。 (FIPS 移行レベル)  
  
 SQL_ISV_TRANSLATIONS = 特定のユーザーがアクセスできるカタログの文字変換を識別します。 (完全レベル)  
  
 SQL_ISV_USAGE_PRIVILEGES = 特定のユーザーが使用できる、または特定のユーザーが所有するカタログオブジェクトの使用権限を識別します。 (FIPS 移行レベル)  
  
 SQL_ISV_VIEW_COLUMN_USAGE = 特定のユーザーによって所有されているカタログのビューが依存している列を識別します。 (中間レベル)  
  
 SQL_ISV_VIEW_TABLE_USAGE = 特定のユーザーによって所有されているカタログのビューが依存しているテーブルを識別します。 (中間レベル)  
  
 SQL_ISV_VIEWS = 特定のユーザーがアクセスできる、このカタログに定義されている表示テーブルを識別します。 (FIPS 移行レベル)  
  
 SQL_INSERT_STATEMENT (ODBC 3.0)  
 **INSERT**ステートメントのサポートを示す SQLUINTEGER ビットマスク。  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 SQL-92 エントリレベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。  
  
 SQL_INTEGRITY (ODBC 1.0)  
 文字列: "Y"。データソースが整合性拡張機能をサポートしている場合は、そうでない場合は "N" になります。  
  
 Odbc 2.0 *InfoType* SQL_ODBC_SQL_OPT_IEF から、odbc 3.0 のこの*InfoType*の名前が変更されました。  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1 (ODBC 3.0)  
 ドライバーでサポートされているキーセットカーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の最初のサブセットが含まれます。2番目のサブセットについては、「SQL_KEYSET_CURSOR_ATTRIBUTES2」を参照してください。  
  
 サポートされている属性を判別するには、次のビットマスクを使用します。  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 これらのビットマスクの説明については、「SQL_DYNAMIC_CURSOR_ATTRIBUTES1」を参照してください。また、「動的カーソル」の「キーセットドリブンカーソル」を参照してください。  
  
 SQL-92 中間レベル準拠のドライバーは、通常、SQL_CA1_NEXT、SQL_CA1_ABSOLUTE、および SQL_CA1_RELATIVE オプションをサポート対象として返します。これは、ドライバーが埋め込み SQL FETCH ステートメントを使用してスクロール可能なカーソルをサポートするためです。 ただし、これによって基になる SQL のサポートが直接決定されるわけではないため、SQL 92 の中間レベル準拠のドライバーであっても、スクロール可能なカーソルはサポートされない可能性があります。  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2 (ODBC 3.0)  
 ドライバーでサポートされているキーセットカーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の2番目のサブセットが含まれます。最初のサブセットについては、「SQL_KEYSET_CURSOR_ATTRIBUTES1」を参照してください。  
  
 サポートされている属性を判別するには、次のビットマスクを使用します。  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 これらのビットマスクの説明については、「SQL_DYNAMIC_CURSOR_ATTRIBUTES1」を参照してください。また、「動的カーソル」の「キーセットドリブンカーソル」を参照してください。  
  
 SQL_KEYWORDS (ODBC 2.0)  
 データソース固有のすべてのキーワードのコンマ区切りの一覧を含む文字列。 この一覧には、データソースと ODBC の両方で使用される ODBC またはキーワードに固有のキーワードは含まれません。 この一覧は、すべての予約済みキーワードを表します。相互運用可能なアプリケーションでは、オブジェクト名にこれらの単語を使用しないでください。  
  
 ODBC キーワードの一覧については、「[付録 C: SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)」の「[予約済みキーワード](../../../odbc/reference/appendixes/reserved-keywords.md)」を参照してください。 **#Define**値 SQL_ODBC_KEYWORDS には、コンマ区切りの ODBC キーワードの一覧が含まれています。  
  
 付録 C: SQL 文法  
  
 SQL_LIKE_ESCAPE_CLAUSE (ODBC 2.0)  
 文字列: "Y" (データソースがパーセント文字 (%) のエスケープ文字をサポートしている場合)**like**述語ではアンダースコア文字 (_) が使用され、ドライバーは**like**述語エスケープ文字を定義するための ODBC 構文をサポートしています。それ以外の場合は "N"。  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS (ODBC 3.0)  
 指定された接続でドライバーがサポートできる非同期モードのアクティブな同時実行ステートメントの最大数を指定する SQLUINTEGER 値です。 特定の制限がない場合、または制限が不明な場合、この値は0になります。  
  
 SQL_MAX_BINARY_LITERAL_LEN (ODBC 2.0)  
 SQL ステートメントのバイナリリテラルの最大長 (16 進文字のうち、 **SQLGetTypeInfo**によって返されるリテラルプレフィックスとサフィックスを除く) を指定する SQLUINTEGER 値です。 たとえば、バイナリリテラル0xFFAA の長さは4です。 最大長がない場合、または長さが不明な場合、この値は0に設定されます。  
  
 SQL_MAX_CATALOG_NAME_LEN (ODBC 1.0)  
 データソース内のカタログ名の最大長を指定する SQLUS悪意のある値。 最大長がない場合、または長さが不明な場合、この値は0に設定されます。  
  
 FIPS 完全準拠のドライバーは、少なくとも128を返します。  
  
 Odbc 2.0 *InfoType* SQL_MAX_QUALIFIER_NAME_LEN から、odbc 3.0 のこの*InfoType*の名前が変更されました。  
  
 SQL_MAX_CHAR_LITERAL_LEN (ODBC 2.0)  
 SQL ステートメント内の文字リテラルの最大長 (文字数は、リテラルプレフィックスと**SQLGetTypeInfo**によって返されるサフィックスを除く) を指定する SQLUINTEGER 値です。 最大長がない場合、または長さが不明な場合、この値は0に設定されます。  
  
 SQL_MAX_COLUMN_NAME_LEN (ODBC 1.0)  
 データソース内の列名の最大長を指定する SQLUS悪意のある値。 最大長がない場合、または長さが不明な場合、この値は0に設定されます。  
  
 FIPS エントリレベル準拠のドライバーは、少なくとも18を返します。 FIPS 中間レベル準拠のドライバーは、少なくとも128を返します。  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY (ODBC 2.0)  
 **GROUP by**句で許容される列の最大数を指定する SQLUS悪意のある値。 制限が指定されていない場合、または制限が不明な場合、この値は0に設定されます。  
  
 FIPS エントリレベル準拠のドライバーは、少なくとも6を返します。 FIPS 中間レベル準拠のドライバーは、少なくとも15を返します。  
  
 SQL_MAX_COLUMNS_IN_INDEX (ODBC 2.0)  
 インデックスで許容される列の最大数を指定する SQLUS悪意のある値。 制限が指定されていない場合、または制限が不明な場合、この値は0に設定されます。  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY (ODBC 2.0)  
 **ORDER by**句で許容される列の最大数を指定する SQLUS悪意のある値。 制限が指定されていない場合、または制限が不明な場合、この値は0に設定されます。  
  
 FIPS エントリレベル準拠のドライバーは、少なくとも6を返します。 FIPS 中間レベル準拠のドライバーは、少なくとも15を返します。  
  
 SQL_MAX_COLUMNS_IN_SELECT (ODBC 2.0)  
 選択リストで許可されている列の最大数を指定する SQLUS悪意のある値。 制限が指定されていない場合、または制限が不明な場合、この値は0に設定されます。  
  
 FIPS エントリレベル準拠のドライバーは、少なくとも100を返します。 FIPS 中間レベル準拠のドライバーは、少なくとも250を返します。  
  
 SQL_MAX_COLUMNS_IN_TABLE (ODBC 2.0)  
 テーブルで許容される列の最大数を指定する SQLUS悪意のある値。 制限が指定されていない場合、または制限が不明な場合、この値は0に設定されます。  
  
 FIPS エントリレベル準拠のドライバーは、少なくとも100を返します。 FIPS 中間レベル準拠のドライバーは、少なくとも250を返します。  
  
 SQL_MAX_CONCURRENT_ACTIVITIES (ODBC 1.0)  
 ドライバーが接続に対してサポートできるアクティブなステートメントの最大数を指定する SQLUS悪意のある値。 ステートメントは、結果が保留になっている場合にアクティブとして定義されます。 "結果" という用語は、 **select**操作の行、または**挿入**、**更新**、または**削除**操作 (行数など) によって影響を受ける行を意味します。また、NEED_DATA 状態である場合はです。 この値には、ドライバーまたはデータソースによって課される制限が反映されます。 制限が指定されていない場合、または制限が不明な場合、この値は0に設定されます。  
  
 Odbc 2.0 *InfoType* SQL_ACTIVE_STATEMENTS から、odbc 3.0 のこの*InfoType*の名前が変更されました。  
  
 SQL_MAX_CURSOR_NAME_LEN (ODBC 1.0)  
 データソース内のカーソル名の最大長を指定する SQLUS悪意のある値。 最大長がない場合、または長さが不明な場合、この値は0に設定されます。  
  
 FIPS エントリレベル準拠のドライバーは、少なくとも18を返します。 FIPS 中間レベル準拠のドライバーは、少なくとも128を返します。  
  
 SQL_MAX_DRIVER_CONNECTIONS (ODBC 1.0)  
 環境に対してドライバーがサポートできるアクティブな接続の最大数を指定する SQLUS悪意のある値。 この値には、ドライバーまたはデータソースによって課される制限が反映されます。 制限が指定されていない場合、または制限が不明な場合、この値は0に設定されます。  
  
 Odbc 2.0 *InfoType* SQL_ACTIVE_CONNECTIONS から、odbc 3.0 のこの*InfoType*の名前が変更されました。  
  
 SQL_MAX_IDENTIFIER_LEN (ODBC 3.0)  
 データソースがユーザー定義名に対してサポートする最大文字数を示す SQLUS悪意のある文字。  
  
 FIPS エントリレベル準拠のドライバーは、少なくとも18を返します。 FIPS 中間レベル準拠のドライバーは、少なくとも128を返します。  
  
 SQL_MAX_INDEX_SIZE (ODBC 2.0)  
 インデックスの結合されたフィールドで許容される最大バイト数を指定する SQLUINTEGER 値です。 制限が指定されていない場合、または制限が不明な場合、この値は0に設定されます。  
  
 SQL_MAX_PROCEDURE_NAME_LEN (ODBC 1.0)  
 データソース内のプロシージャ名の最大長を指定する SQLUS悪意のある値。 最大長がない場合、または長さが不明な場合、この値は0に設定されます。  
  
 SQL_MAX_ROW_SIZE (ODBC 2.0)  
 テーブル内の1行の最大長を指定する SQLUINTEGER 値です。 制限が指定されていない場合、または制限が不明な場合、この値は0に設定されます。  
  
 FIPS エントリレベル準拠のドライバーは、少なくとも2000を返します。 FIPS 中間レベル準拠のドライバーは、少なくとも8000を返します。  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG (ODBC 3.0)  
 文字列 "Y": SQL_MAX_ROW_SIZE 情報型に対して返される行の最大サイズに、その行のすべての SQL_LONGVARCHAR と SQL_LONGVARBINARY の列の長さが含まれている場合は、それ以外の場合は "N"。  
  
 SQL_MAX_SCHEMA_NAME_LEN (ODBC 1.0)  
 データソース内のスキーマ名の最大長を指定する SQLUS悪意のある値。 最大長がない場合、または長さが不明な場合、この値は0に設定されます。  
  
 FIPS エントリレベル準拠のドライバーは、少なくとも18を返します。 FIPS 中間レベル準拠のドライバーは、少なくとも128を返します。  
  
 Odbc 2.0 *InfoType* SQL_MAX_OWNER_NAME_LEN から、odbc 3.0 のこの*InfoType*の名前が変更されました。  
  
 SQL_MAX_STATEMENT_LEN (ODBC 2.0)  
 SQL ステートメントの最大長 (空白を含む文字数) を指定する SQLUINTEGER 値です。 最大長がない場合、または長さが不明な場合、この値は0に設定されます。  
  
 SQL_MAX_TABLE_NAME_LEN (ODBC 1.0)  
 データソース内のテーブル名の最大長を指定する SQLUS悪意のある値。 最大長がない場合、または長さが不明な場合、この値は0に設定されます。  
  
 FIPS エントリレベル準拠のドライバーは、少なくとも18を返します。 FIPS 中間レベル準拠のドライバーは、少なくとも128を返します。  
  
 SQL_MAX_TABLES_IN_SELECT (ODBC 2.0)  
 **SELECT**ステートメントの**from**句で許可されるテーブルの最大数を指定する sqlus悪意のある値。 制限が指定されていない場合、または制限が不明な場合、この値は0に設定されます。  
  
 FIPS エントリレベル準拠のドライバーは、少なくとも15を返します。 FIPS 中間レベル準拠のドライバーは、少なくとも50を返します。  
  
 SQL_MAX_USER_NAME_LEN (ODBC 2.0)  
 データソース内のユーザー名の最大長を指定する SQLUS悪意のある値。 最大長がない場合、または長さが不明な場合、この値は0に設定されます。  
  
 SQL_MULT_RESULT_SETS (ODBC 1.0)  
 文字列。データソースが複数の結果セットをサポートしている場合は "Y"、そうでない場合は "N" になります。  
  
 複数の結果セットの詳細については、「[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)」を参照してください。  
  
 SQL_MULTIPLE_ACTIVE_TXN (ODBC 1.0)  
 文字列: "Y"。ドライバーで同時に複数のアクティブなトランザクションがサポートされている場合は、いつでも1つのトランザクションをアクティブにできる場合は "N"。  
  
 この情報の種類に対して返される情報は、分散トランザクションの場合には適用されません。  
  
 SQL_NEED_LONG_DATA_LEN (ODBC 2.0)  
 値がデータソースに送信される前にデータソースが長いデータ値 (データ型が SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長いデータソース固有のデータ型) の長さを必要とする場合は、"Y" という文字列になります。それ以外の場合は "N" になります。 詳細については、「 [SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)と[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)」を参照してください。  
  
 SQL_NON_NULLABLE_COLUMNS (ODBC 1.0)  
 データソースが列に NOT NULL をサポートするかどうかを指定する SQLUS悪意のある値。  
  
 SQL_NNC_NULL = すべての列で null 値を許容する必要があります。  
  
 SQL_NNC_NON_NULL = 列を null 許容にすることはできません。 (データソースでは、 **CREATE TABLE**ステートメント内の**not NULL**列制約がサポートされています)。  
  
 SQL-92 エントリレベル準拠のドライバーは SQL_NNC_NON_NULL を返します。  
  
 SQL_NULL_COLLATION (ODBC 2.0)  
 結果セット内で Null が並べ替えられる場所を指定する SQLUS悪意のある値。  
  
 SQL_NC_END = Null は、ASC または DESC キーワードに関係なく、結果セットの最後に並べ替えられます。  
  
 SQL_NC_HIGH = Null は、ASC または DESC キーワードに応じて、結果セットの上限に基づいて並べ替えられます。  
  
 SQL_NC_LOW = Null は、ASC または DESC キーワードに応じて、結果セットの下限で並べ替えられます。  
  
 SQL_NC_START = Null は、ASC または DESC キーワードに関係なく、結果セットの先頭で並べ替えられます。  
  
 SQL_NUMERIC_FUNCTIONS (ODBC 1.0)  
 注: 情報の種類は ODBC 1.0 で導入されました。各ビットマスクには、それが導入されたバージョンのラベルが付けられています。  
  
 ドライバーと関連付けられたデータソースでサポートされているスカラー数値関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている数値関数を判別するには、次のビットマスクを使用します。  
  
 SQL_FN_NUM_ABS (ODBC 1.0) SQL_FN_NUM_ACOS (ODBC 1.0) SQL_FN_NUM_ASIN (ODBC 1.0) SQL_FN_NUM_ATAN (ODBC 1.0) SQL_FN_NUM_ATAN2 (ODBC 1.0) SQL_FN_NUM_CEILING (ODBC 1.0) SQL_FN_NUM_COS (ODBC 1.0) SQL_FN_NUM_COT (ODBC 1.0) SQL_FN_NUM_DEGREES (ODBC 1.0) SQL_FN_NUM_EXP (ODBC 1.0) SQL_FN_NUM_FLOOR (ODBC 1.0) SQL_FN_NUM_LOG (ODBC 1.0) SQL_FN_NUM_LOG10 (ODBC 2.0) SQL_FN_NUM_MOD (ODBC 1.0) SQL_FN_NUM_PI (ODBC 1.0) SQL_FN_NUM_POWER (ODBC 2.0) SQL_FN_NUM_RADIANS (ODBC 2.0) SQL_FN_NUM_RAND (ODBC 1.0) SQL_FN_NUM_ROUND (ODBC 1.0) SQL_FN_NUM_SIGN (ODBC 1.0) SQL_FN_NUM_SIN (ODBC 1.0) SQL_FN_NUM_SQRT (ODBC 1.0) SQL_FN_NUM_TAN (ODBC 1.0) SQL_FN_NUM_TRUNCATE (ODBC 2.0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE (ODBC 3.0)  
 ドライバーが準拠している ODBC 3 *. x*インターフェイスのレベルを示す SQLUINTEGER 値。  
  
 SQL_OIC_CORE: すべての ODBC ドライバーが準拠していると予想される最小レベル。 このレベルには、接続関数、SQL ステートメントを準備および実行するための関数、基本的な結果セットのメタデータ関数、基本的なカタログ関数など、基本的なインターフェイス要素が含まれています。  
  
 SQL_OIC_LEVEL1: コア標準のコンプライアンスレベルの機能、スクロール可能なカーソル、ブックマーク、位置指定更新、削除などを含むレベル。  
  
 SQL_OIC_LEVEL2: レベル1の標準準拠レベルの機能に加えて、機密性の高いカーソルなどの高度な機能を含むレベルです。ブックマークによる更新、削除、および更新ストアドプロシージャのサポート主キーと外部キーのカタログ関数マルチカタログのサポート。などなど。  
  
 詳細については、「[インターフェイスの準拠レベル](../../../odbc/reference/develop-app/interface-conformance-levels.md)」を参照してください。  
  
 SQL_ODBC_VER (ODBC 1.0)  
 ドライバーマネージャーが準拠する ODBC のバージョンを含む文字列。 バージョンの形式は # #. # #. 0000 です。最初の2桁はメジャーバージョンで、次の2桁はマイナーバージョンです。 これは、ドライバーマネージャーでのみ実装されます。  
  
 SQL_OJ_CAPABILITIES (ODBC 2.01)  
 ドライバーとデータソースでサポートされている外部結合の種類を列挙する SQLUINTEGER ビットマスク。 サポートされている型を判断するには、次のビットマスクを使用します。  
  
 SQL_OJ_LEFT = 左外部結合はサポートされています。  
  
 SQL_OJ_RIGHT = 右外部結合がサポートされています。  
  
 SQL_OJ_FULL = 完全外部結合はサポートされています。  
  
 SQL_OJ_NESTED = 入れ子になった外部結合がサポートされています。  
  
 SQL_OJ_NOT_ORDERED = 外部結合の ON 句の列名は、 **OUTER join**句の各テーブル名と同じ順序である必要はありません。  
  
 SQL_OJ_INNER = 内部テーブル (左外部結合の右テーブルまたは右外部結合の左テーブル) は、内部結合でも使用できます。 これは、内部テーブルを持たない完全外部結合には適用されません。  
  
 SQL_OJ_ALL_COMPARISON_OPS = ON 句の比較演算子には、任意の ODBC 比較演算子を使用できます。 このビットが設定されていない場合、外部結合では等号 (=) 比較演算子のみを使用できます。  
  
 これらのオプションのいずれもサポートされていない場合は、外部結合句はサポートされません。  
  
 SQL-92 で定義されているように、SELECT ステートメントでの関係結合演算子のサポートの詳細については、「SQL_SQL92_RELATIONAL_JOIN_OPERATORS」を参照してください。  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT (ODBC 2.0)  
 **ORDER BY**句の列が選択リストに含まれている必要がある場合は、"Y" という文字列。それ以外の場合は、"N" です。  
  
 SQL_PARAM_ARRAY_ROW_COUNTS (ODBC 3.0)  
 パラメーター化された実行での行数の可用性に関するドライバーのプロパティを列挙する SQLUINTEGER。 の値は次のとおりです。  
  
 SQL_PARC_BATCH = 個々の行の数は、パラメーターのセットごとに使用できます。 これは、概念的には、配列内の各パラメーターセットに1つずつ、SQL ステートメントのバッチを生成するドライバーに相当します。 拡張エラー情報を取得するには、SQL_PARAM_STATUS_PTR 記述子フィールドを使用します。  
  
 SQL_PARC_NO_BATCH = 使用可能な行数は1つだけです。これは、パラメーターの配列全体に対してステートメントを実行した結果として得られる累積行数です。 これは、ステートメントを完全なパラメーター配列と共に1つのアトミック単位として扱うことと概念的には同じです。 エラーは、1つのステートメントが実行された場合と同じように処理されます。  
  
 SQL_PARAM_ARRAY_SELECTS (ODBC 3.0)  
 パラメーター化された実行での結果セットの可用性に関するドライバーのプロパティを列挙する SQLUINTEGER。 の値は次のとおりです。  
  
 SQL_PAS_BATCH = パラメーターのセットごとに1つの結果セットを使用できます。 これは、概念的には、配列内の各パラメーターセットに1つずつ、SQL ステートメントのバッチを生成するドライバーに相当します。  
  
 SQL_PAS_NO_BATCH = 使用できる結果セットは1つだけです。これは、パラメーターの配列全体に対してステートメントを実行した結果セットを累積した結果セットを表します。 これは、ステートメントを完全なパラメーター配列と共に1つのアトミック単位として扱うことと概念的には同じです。  
  
 SQL_PAS_NO_SELECT = A ドライバーでは、パラメーターの配列を使用して結果セットの生成ステートメントを実行することはできません。  
  
 SQL_PROCEDURE_TERM (ODBC 1.0)  
 データソースベンダーのプロシージャ名を含む文字列。たとえば、「データベースプロシージャ」、「ストアドプロシージャ」、「プロシージャ」、「パッケージ」、「ストアドクエリ」などです。  
  
 SQL_PROCEDURES (ODBC 1.0)  
 文字列。データソースでプロシージャがサポートされている場合は "Y"、ODBC プロシージャの呼び出し構文がサポートされている場合はです。それ以外の場合は "N"。  
  
 SQL_POS_OPERATIONS (ODBC 2.0)  
 **SQLSetPos**のサポート操作を列挙する SQLINTEGER ビットマスク。  
  
 次のビットマスクをフラグと共に使用して、どのオプションがサポートされているかを判断します。  
  
 SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)  
  
 SQL_QUOTED_IDENTIFIER_CASE (ODBC 2.0)  
 次のような SQLUS悪意のある値。  
  
 SQL_IC_UPPER = SQL の引用符で囲まれた識別子では大文字と小文字が区別されず、システムカタログに大文字で格納されます。  
  
 SQL_IC_LOWER = SQL の引用符で囲まれた識別子では大文字と小文字が区別されず、システムカタログに小文字で格納されます。  
  
 SQL_IC_SENSITIVE = SQL で引用符で囲まれた識別子は大文字と小文字が区別され、システムカタログ内の大文字と小文字が混在して格納されます。 (SQL 92 準拠のデータベースでは、引用符で囲まれた識別子は常に大文字と小文字が区別されます)。  
  
 SQL_IC_MIXED = SQL の引用符で囲まれた識別子では大文字と小文字が区別されず、システムカタログ内で大文字と小文字が混在して格納されます。  
  
 SQL-92 エントリレベル準拠のドライバーは、常に SQL_IC_SENSITIVE を返します。  
  
 SQL_ROW_UPDATES (ODBC 1.0)  
 文字列: "Y" キーセットドリブンカーソルまたは混合カーソルが、フェッチされたすべての行の行バージョンまたは値を保持している場合に、行が最後にフェッチされた後にユーザーによって行に対して行われたすべての更新を検出できます。 (これは更新プログラムにのみ適用され、削除や挿入には適用されません)。ドライバーは、 **Sqlfetchscroll**が呼び出されたときに、SQL_ROW_UPDATED フラグを行の状態配列に返すことができます。 それ以外の場合は、"N" です。  
  
 SQL_SCHEMA_TERM (ODBC 1.0)  
 データソースベンダーのスキーマ名を含む文字列。たとえば、"owner"、"Authorization ID"、"Schema" などです。  
  
 文字列は、大文字、小文字、または大文字で返すことができます。  
  
 SQL-92 エントリレベル準拠のドライバーは、常に "schema" を返します。  
  
 Odbc 2.0 *InfoType* SQL_OWNER_TERM から、odbc 3.0 のこの*InfoType*の名前が変更されました。  
  
 SQL_SCHEMA_USAGE (ODBC 2.0)  
 スキーマを使用できるステートメントを列挙する SQLUINTEGER ビットマスク。  
  
 SQL_SU_DML_STATEMENTS = スキーマは、すべてのデータ操作言語ステートメント ( **SELECT**、 **INSERT**、 **UPDATE**、 **DELETE**) でサポートされます。サポートされている場合は、Update および where update および DELETE ステートメントを**選択**します。  
  
 SQL_SU_PROCEDURE_INVOCATION = スキーマは、ODBC プロシージャ呼び出しステートメントでサポートされています。  
  
 SQL_SU_TABLE_DEFINITION = スキーマは、すべてのテーブル定義ステートメント ( **CREATE TABLE**、 **CREATE VIEW**、 **ALTER Table**、 **drop table**、 **drop view**) でサポートされています。  
  
 SQL_SU_INDEX_DEFINITION = スキーマは、 **CREATE index**および**DROP INDEX**のすべてのインデックス定義ステートメントでサポートされています。  
  
 SQL_SU_PRIVILEGE_DEFINITION = スキーマは、すべての特権定義ステートメント ( **GRANT**および**REVOKE**) でサポートされます。  
  
 SQL-92 エントリレベル準拠のドライバーは、サポートされているように、SQL_SU_DML_STATEMENTS、SQL_SU_TABLE_DEFINITION、および SQL_SU_PRIVILEGE_DEFINITION のオプションを常に返します。  
  
 Odbc 2.0 *InfoType* SQL_OWNER_USAGE から、odbc 3.0 のこの*InfoType*の名前が変更されました。  
  
 SQL_SCROLL_OPTIONS (ODBC 1.0)  
 注: 情報の種類は ODBC 1.0 で導入されました。各ビットマスクには、それが導入されたバージョンのラベルが付けられています。  
  
 スクロール可能なカーソルに対してサポートされているスクロールオプションを列挙する SQLUINTEGER ビットマスク。  
  
 サポートされているオプションを判別するには、次のビットマスクを使用します。  
  
 SQL_SO_FORWARD_ONLY = カーソルは前方にのみスクロールします。 (ODBC 1.0)  
  
 SQL_SO_STATIC = 結果セットのデータは静的です。 (ODBC 2.0)  
  
 SQL_SO_KEYSET_DRIVEN = ドライバーは、結果セット内のすべての行について、キーを保存して使用します。 (ODBC 1.0)  
  
 SQL_SO_DYNAMIC = ドライバーは、行セット内のすべての行のキーを保持します (キーセットのサイズは行セットのサイズと同じです)。 (ODBC 1.0)  
  
 SQL_SO_MIXED = ドライバーはキーセット内のすべての行のキーを保持し、キーセットのサイズは行セットのサイズよりも大きくなります。 カーソルはキーセット内のキーセットであり、キーセットの外部で動的に行われます。 (ODBC 1.0)  
  
 スクロール可能なカーソルの詳細については、「スクロール可能な[カーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)」を参照してください。  
  
 SQL_SEARCH_PATTERN_ESCAPE (ODBC 1.0)  
 パターンマッチのメタデータのアンダースコア (_) とパーセント記号 (%) の使用を許可するエスケープ文字としてドライバーがサポートする文字を指定する文字列。検索パターンで有効な文字として。 このエスケープ文字は、検索文字列をサポートするカタログ関数の引数に対してのみ適用されます。 この文字列が空の場合、ドライバーは検索パターンのエスケープ文字をサポートしていません。  
  
 この情報の種類は、 **LIKE**述語でのエスケープ文字の一般的なサポートを示すものではないため、SQL-92 にはこの文字列の要件は含まれません。  
  
 この*InfoType*は、カタログ関数に限定されています。 検索パターン文字列でエスケープ文字を使用する方法の詳細については、「 [Pattern 値の引数](../../../odbc/reference/develop-app/pattern-value-arguments.md)」を参照してください。  
  
 SQL_SERVER_NAME (ODBC 1.0)  
 実際のデータソース固有のサーバー名を持つ文字列。**SQLConnect**、 **SQLDriverConnect**、および**SQLBrowseConnect**中にデータソース名を使用する場合に便利です。  
  
 SQL_SPECIAL_CHARACTERS (ODBC 2.0)  
 データソース上の識別子名 (テーブル名、列名、インデックス名など) で使用できるすべての特殊文字 (つまり、a ~ z、A ~ Z、0 ~ 9、およびアンダースコアを除くすべての文字) を含む文字列です。 たとえば、"# $ ^" のようになります。 識別子にこれらの文字が1つ以上含まれている場合、識別子は区切られた識別子である必要があります。  
  
 SQL_SQL_CONFORMANCE (ODBC 3.0)  
 ドライバーでサポートされている SQL 92 のレベルを示す SQLUINTEGER 値。  
  
 SQL_SC_SQL92_ENTRY = エントリレベル SQL-92 準拠。  
  
 SQL_SC_FIPS127_2_TRANSITIONAL = FIPS 127-2 移行レベル準拠。  
  
 SQL_SC_SQL92_FULL = 完全なレベルの SQL-92 準拠。  
  
 SQL_SC_ SQL92_INTERMEDIATE = 中間レベルの SQL-92 準拠。  
  
 SQL_SQL92_DATETIME_FUNCTIONS (ODBC 3.0)  
 92で定義されているように、ドライバーおよび関連付けられたデータソースでサポートされている datetime スカラー関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている datetime 関数を判別するには、次のビットマスクを使用します。  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE (ODBC 3.0)  
 SQL-92 で定義されている**DELETE**ステートメント内の外部キーに対してサポートされている規則を列挙する SQLUINTEGER ビットマスク。  
  
 データソースでサポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 FIPS 移行レベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE (ODBC 3.0)  
 SQL-92 で定義されているように、 **UPDATE**ステートメントで外部キーに対してサポートされている規則を列挙する SQLUINTEGER ビットマスク。  
  
 データソースでサポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 SQL-92 フルレベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。  
  
 SQL_SQL92_GRANT (ODBC 3.0)  
 SQL-92 で定義されている**GRANT**ステートメントでサポートされている句を列挙する SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの横にかっこで囲まれています。  
  
 データソースでサポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_SG_DELETE_TABLE (エントリレベル) SQL_SG_INSERT_COLUMN (中間レベル) SQL_SG_INSERT_TABLE (エントリレベル) SQL_SG_REFERENCES_TABLE (エントリレベル) SQL_SG_REFERENCES_COLUMN (エントリレベル) SQL_SG_SELECT_TABLE (エントリレベル) SQL_SG_UPDATE_COLUMN (エントリレベル) SQL_SG_UPDATE_TABLE (エントリレベル) SQL_SG_USAGE_ON_DOMAIN (FIPS 移行レベル) SQL_SG_USAGE_ON_CHARACTER_SET (FIPS 移行レベル) SQL_SG_USAGE_ON_COLLATION (fips 移行レベル) SQL_SG_USAGE_ON_TRANSLATION (fips 移行レベル) SQL_SG_WITH_GRANT_OPTION (エントリレベル)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS (ODBC 3.0)  
 92で定義されているように、ドライバーおよび関連付けられたデータソースでサポートされている数値スカラー関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている数値関数を判別するには、次のビットマスクを使用します。  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES (ODBC 3.0)  
 SQL-92 で定義されているように、 **SELECT**ステートメントでサポートされている述語を列挙する SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの横にかっこで囲まれています。  
  
 データソースでサポートされているオプションを判別するには、次のビットマスクを使用します。  
  
 SQL_SP_BETWEEN (エントリレベル) SQL_SP_COMPARISON (エントリレベル) SQL_SP_EXISTS (エントリレベル) SQL_SP_IN (エントリレベル) SQL_SP_ISNOTNULL (エントリレベル) SQL_SP_ISNULL (エントリレベル) SQL_SP_LIKE ((エントリレベル) SQL_SP_MATCH_FULL (完全レベル) SQL_SP_MATCH_PARTIAL (完全レベル) SQL_SP_MATCH_UNIQUE_FULL (完全レベル) SQL_SP_MATCH_UNIQUE_PARTIAL (完全レベル) SQL_SP_OVERLAPS (入力レベル) SQL_SP_QUANTIFIED_COMPARISON (エントリレベル)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS (ODBC 3.0)  
 SQL-92 で定義されているように、 **SELECT**ステートメントでサポートされている関係結合演算子を列挙する SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの横にかっこで囲まれています。  
  
 データソースでサポートされているオプションを判別するには、次のビットマスクを使用します。  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (中間レベル) SQL_SRJO_CROSS_JOIN (完全レベル) SQL_SRJO_EXCEPT_JOIN (中間レベル) SQL_SRJO_FULL_OUTER_JOIN (中間レベル) SQL_SRJO_INNER_JOIN (FIPS 移行レベル) SQL_SRJO_INTERSECT_JOIN (中間レベル) SQL_SRJO_LEFT_OUTER_JOIN (FIPS 移行レベル) SQL_SRJO_NATURAL_JOIN (FIPS 移行レベル) SQL_SRJO_RIGHT_OUTER_JOIN (FIPS 移行レベル) SQL_SRJO_UNION_JOIN (全レベル)  
  
 SQL_SRJO_INNER_JOIN は、内部結合機能ではなく**内部結合**構文のサポートを示します。 **内部結合**の構文のサポートは FIPS に移行されますが、内部結合機能のサポートは**ENTRY**です。  
  
 SQL_SQL92_REVOKE (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **REVOKE**ステートメントでサポートされている句を列挙する SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの横にかっこで囲まれています。  
  
 データソースでサポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_SR_CASCADE (FIPS 移行レベル) SQL_SR_DELETE_TABLE (エントリレベル) SQL_SR_GRANT_OPTION_FOR (中間レベル) SQL_SR_INSERT_COLUMN (中間レベル) SQL_SR_INSERT_TABLE (エントリレベル) SQL_SR_REFERENCES_COLUMN (エントリレベル) SQL_SR_REFERENCES_TABLE (エントリレベル) SQL_SR_RESTRICT (FIPS 移行レベル) SQL_SR_SELECT_TABLE (エントリレベル) SQL_SR_UPDATE_COLUMN (エントリレベル) SQL_SR_UPDATE_TABLE (エントリレベル) SQL_SR_USAGE_ON_DOMAIN (FIPS 移行レベル) SQL_SR_USAGE_ON_CHARACTER_セット (FIPS 移行レベル) SQL_SR_USAGE_ON_COLLATION (fips 移行レベル) SQL_SR_USAGE_ON_TRANSLATION (FIPS 移行レベル)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR (ODBC 3.0)  
 SQL-92 で定義されているように、 **SELECT**ステートメントでサポートされている行値コンストラクター式を列挙する SQLUINTEGER ビットマスク。 データソースでサポートされているオプションを判別するには、次のビットマスクを使用します。  
  
 SQL_SRVC_VALUE_EXPRESSION SQL_SRVC_NULL SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS (ODBC 3.0)  
 92で定義されているように、ドライバーおよび関連付けられたデータソースでサポートされている文字列スカラー関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている文字列関数を判別するには、次のビットマスクを使用します。  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS (ODBC 3.0)  
 SQL-92 で定義されている、サポートされている値式を列挙する SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの横にかっこで囲まれています。  
  
 データソースでサポートされているオプションを判別するには、次のビットマスクを使用します。  
  
 SQL_SVE_CASE (中間レベル) SQL_SVE_CAST (FIPS 移行レベル) SQL_SVE_COALESCE (中間レベル) SQL_SVE_NULLIF (中間レベル)  
  
 SQL_STANDARD_CLI_CONFORMANCE (ODBC 3.0)  
 ドライバーが準拠している CLI 標準または標準規格を列挙する SQLUINTEGER ビットマスク。 次のビットマスクは、ドライバーが準拠しているレベルを判断するために使用されます。  
  
 SQL_SCC_XOPEN_CLI_VERSION1: ドライバーは、Open Group CLI バージョン1に準拠しています。  
  
 SQL_SCC_ISO92_CLI: ドライバーは ISO 92 CLI に準拠しています。  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1 (ODBC 3.0)  
 ドライバーでサポートされている静的カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の最初のサブセットが含まれます。2番目のサブセットについては、「SQL_STATIC_CURSOR_ATTRIBUTES2」を参照してください。  
  
 サポートされている属性を判別するには、次のビットマスクを使用します。  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 これらのビットマスクの説明については、「SQL_DYNAMIC_CURSOR_ATTRIBUTES1」を参照してください (および「動的カーソル」の「静的カーソル」を参照してください)。  
  
 SQL-92 中間レベル準拠のドライバーは、通常、SQL_CA1_NEXT、SQL_CA1_ABSOLUTE、および SQL_CA1_RELATIVE オプションをサポート対象として返します。これは、ドライバーが埋め込み SQL FETCH ステートメントを使用してスクロール可能なカーソルをサポートするためです。 ただし、これによって基になる SQL のサポートが直接決定されるわけではないため、SQL 92 の中間レベル準拠のドライバーであっても、スクロール可能なカーソルはサポートされない可能性があります。  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2 (ODBC 3.0)  
 ドライバーでサポートされている静的カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の2番目のサブセットが含まれます。最初のサブセットについては、「SQL_STATIC_CURSOR_ATTRIBUTES1」を参照してください。  
  
 サポートされている属性を判別するには、次のビットマスクを使用します。  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 これらのビットマスクの説明については、「SQL_DYNAMIC_CURSOR_ATTRIBUTES2」を参照してください (および「動的カーソル」の「静的カーソル」を参照してください)。  
  
 SQL_STRING_FUNCTIONS (ODBC 1.0)  
 注: 情報の種類は ODBC 1.0 で導入されました。各ビットマスクには、それが導入されたバージョンのラベルが付けられています。  
  
 ドライバーと関連付けられたデータソースでサポートされているスカラー文字列関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている文字列関数を判別するには、次のビットマスクを使用します。  
  
 SQL_FN_STR_ASCII (ODBC 1.0) SQL_FN_STR_BIT_LENGTH (ODBC 3.0) SQL_FN_STR_CHAR (ODBC 1.0) SQL_FN_STR_CHAR_LENGTH (ODBC 3.0) SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0) SQL_FN_STR_CONCAT (ODBC 1.0) SQL_FN_STR_DIFFERENCE (ODBC 1.0) SQL_FN_STR_INSERT (ODBC 1.0) SQL_FN_STR_LCASE (ODBC 1.0) SQL_FN_STR_LEFT (ODBC 1.0) SQL_FN_STR_LENGTH (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) SQL_FN_STR_LTRIM (ODBC1.0) SQL_FN_STR_OCTET_LENGTH (ODBC 3.0) SQL_FN_STR_POSITION (ODBC 3.0) SQL_FN_STR_REPEAT (ODBC 1.0) SQL_FN_STR_REPLACE (ODBC 1.0) SQL_FN_STR_RIGHT (ODBC 1.0) SQL_FN_STR_RTRIM (ODBC 1.0) SQL_FN_STR_SOUNDEX (ODBC 1.0) SQL_FN_STR_SPACE (ODBC 2.0) SQL_FN_STR_SUBSTRING (ODBC 1.0) SQL_FN_STR_UCASE (ODBC 1.0)  
  
 アプリケーションで、 *string_exp1*、 *string_exp2*、*開始*の各引数を使用して**検索**のスカラー関数を呼び出すことができる場合、ドライバーは SQL_FN_STR_LOCATE ビットマスクを返します。 アプリケーションで、 *string_exp1*引数と*string_exp2*引数のみを使用して検索スカラー関数を呼び出すことができる場合、ドライバーは SQL_FN_STR_LOCATE_2 ビットマスクを返します。 **検索**スカラー関数を完全にサポートするドライバーは、両方のビットマスクを返します。  
  
 (詳細については、「付録 E の[文字列関数](../../../odbc/reference/appendixes/string-functions.md)」、「スカラー関数」を参照してください)。  
  
 SQL_SUBQUERIES (ODBC 2.0)  
 サブクエリをサポートする述語を列挙する SQLUINTEGER ビットマスク。  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 SQL_SQ_CORRELATED_SUBQUERIES ビットマスクは、サブクエリをサポートするすべての述語が相関サブクエリをサポートしていることを示します。  
  
 SQL-92 エントリレベル準拠のドライバーは、すべてのビットが設定されているビットマスクを常に返します。  
  
 SQL_SYSTEM_FUNCTIONS (ODBC 1.0)  
 ドライバーと関連付けられたデータソースでサポートされているスカラーシステム関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされているシステム関数を判別するには、次のビットマスクを使用します。  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM (ODBC 1.0)  
 データソースベンダーのテーブル名を含む文字列。たとえば、"table" または "file" のようになります。  
  
 この文字列には、大文字、小文字、または大文字を混在させることができます。  
  
 SQL-92 エントリレベル準拠のドライバーは、常に "table" を返します。  
  
 SQL_TIMEDATE_ADD_INTERVALS (ODBC 2.0)  
 ドライバーによってサポートされているタイムスタンプの間隔と、タイムスタンプ追加スカラー関数の関連データソースを列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクは、サポートされる間隔を決定するために使用されます。  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 FIPS 移行レベル準拠のドライバーは、すべてのビットが設定されているビットマスクを常に返します。  
  
 SQL_TIMEDATE_DIFF_INTERVALS (ODBC 2.0)  
 ドライバーによってサポートされているタイムスタンプの間隔と、タイムスタンプ DIFF スカラー関数に関連付けられたデータソースを列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクは、サポートされる間隔を決定するために使用されます。  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 FIPS 移行レベル準拠のドライバーは、すべてのビットが設定されているビットマスクを常に返します。  
  
 SQL_TIMEDATE_FUNCTIONS (ODBC 1.0)  
 注: 情報の種類は ODBC 1.0 で導入されました。各ビットマスクには、それが導入されたバージョンのラベルが付けられています。  
  
 ドライバーと関連付けられたデータソースでサポートされているスカラー日付と時刻関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている日付と時刻の関数を判別するには、次のビットマスクを使用します。  
  
 SQL_FN_TD_CURRENT_DATE ODBC 3.0) SQL_FN_TD_CURRENT_TIME (ODBC 3.0) SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0) SQL_FN_TD_CURDATE (ODBC 1.0) SQL_FN_TD_CURTIME (ODBC 1.0 1.0) SQL_FN_TD_DAYNAME (ODBC 1.0) SQL_FN_TD_DAYOFMONTH (ODBC 1.0) SQL_FN_TD_DAYOFWEEK (ODBC 1.0) SQL_FN_TD_DAYOFYEAR (ODBC 1.0) SQL_FN_TD_EXTRACT (ODBC 1.0) SQL_FN_TD_HOUR (ODBC (ODBC 1.0) SQL_FN_TD_MINUTE (ODBC 1.0) SQL_FN_TD_MONTH (ODBC1.0) SQL_FN_TD_MONTHNAME (ODBC 2.0) SQL_FN_TD_NOW (ODBC 1.0) SQL_FN_TD_QUARTER (ODBC 1.0) SQL_FN_TD_SECOND (ODBC 1.0) SQL_FN_TD_TIMESTAMPADD (ODBC 1.0) SQL_FN_TD_TIMESTAMPDIFF (ODBC 2.0) SQL_FN_TD_WEEK (ODBC 1.0) SQL_FN_TD_YEAR (ODBC 1.0)  
  
 SQL_TXN_CAPABLE (ODBC 1.0)  
 注: 情報の種類は ODBC 1.0 で導入されました。各戻り値には、それが導入されたバージョンのラベルが付けられます。  
  
 ドライバーまたはデータソースでのトランザクションのサポートを記述する SQLUS悪意のある値。  
  
 SQL_TC_NONE = トランザクションはサポートされていません。 (ODBC 1.0)  
  
 SQL_TC_DML = トランザクションには、データ操作言語 (DML) ステートメント (**SELECT**、 **INSERT**、 **UPDATE**、 **DELETE**) のみを含めることができます。 トランザクションでデータ定義言語 (DDL) ステートメントが発生したため、エラーが発生しました。 (ODBC 1.0)  
  
 SQL_TC_DDL_COMMIT = トランザクションに含めることができるのは DML ステートメントだけです。 トランザクションで発生した DDL ステートメント (**CREATE TABLE**、 **DROP INDEX**など) によって、トランザクションがコミットされます。 (ODBC 2.0)  
  
 SQL_TC_DDL_IGNORE = トランザクションに含めることができるのは DML ステートメントだけです。 トランザクションで発生した DDL ステートメントは無視されます。 (ODBC 2.0)  
  
 SQL_TC_ALL = トランザクションには、DDL ステートメントと DML ステートメントを任意の順序で含めることができます。 (ODBC 1.0)  
  
 (SQL-92 ではトランザクションのサポートが必須であるため、SQL-92 に準拠しているドライバー [any level] は SQL_TC_NONE を返しません)。  
  
 SQL_TXN_ISOLATION_OPTION (ODBC 1.0)  
 ドライバーまたはデータソースから使用できるトランザクション分離レベルを列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクをフラグと共に使用して、どのオプションがサポートされているかを判断します。  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 これらの分離レベルの詳細については、SQL_DEFAULT_TXN_ISOLATION の説明を参照してください。  
  
 トランザクション分離レベルを設定するには、アプリケーションが**SQLSetConnectAttr**を呼び出して、SQL_ATTR_TXN_ISOLATION 属性を設定します。 詳細については、「 [SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)」を参照してください。  
  
 SQL-92 エントリレベル準拠のドライバーは、常にサポート対象として SQL_TXN_SERIALIZABLE を返します。 FIPS 移行レベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。  
  
 SQL_UNION (ODBC 2.0)  
 **UNION**句のサポートを列挙する SQLUINTEGER ビットマスク。  
  
 SQL_U_UNION = データソースでは、 **UNION**句がサポートされています。  
  
 SQL_U_UNION_ALL = データソースでは、 **UNION**句の**ALL**キーワードがサポートされています。 (**SQLGetInfo**は SQL_U_UNION と SQL_U_UNION_ALL の両方を返します)。  
  
 SQL-92 エントリレベル準拠のドライバーは、これらのオプションの両方をサポート対象として常に返します。  
  
 SQL_USER_NAME (ODBC 1.0)  
 特定のデータベースで使用されている名前を持つ文字列。これは、ログイン名とは異なる場合があります。  
  
 SQL_XOPEN_CLI_YEAR (ODBC 3.0)  
 ODBC ドライバーマネージャーのバージョンが完全に準拠している Open Group specification の発行年を示す文字列。  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1.0)  
 文字列 "Y": ユーザーが**sqlprocedures**によって返されたすべてのプロシージャを実行できる場合は、ユーザーが実行できないプロシージャが返された場合は、"N"。  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 文字列: ユーザーが**Sqltables**によって返されるすべてのテーブルに対して**SELECT**権限を持っている場合は、"Y" になります。ユーザーがアクセスできないテーブルが返された場合は、"N"。  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 ドライバーがサポートできるアクティブな環境の最大数を指定する SQLUS悪意のある値。 制限が指定されていない場合、または制限が不明な場合、この値は0に設定されます。  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3.0)  
 集計関数のサポートを列挙する SQLUINTEGER ビットマスク。  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 SQL-92 エントリレベル準拠のドライバーは、常にこれらのオプションをすべてサポート対象として返します。  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 データソースでサポートされている SQL-92 で定義されているように、 **ALTER DOMAIN**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。 SQL-92 完全レベル準拠のドライバーは、常にビットマスクをすべて返します。 戻り値 "0" は、 **ALTER DOMAIN**ステートメントがサポートされていないことを意味します。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの横にかっこで囲まれています。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = ドメイン制約の追加がサポートされています (完全レベル)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT = \<alter domain> \<set domain DEFAULT 句> サポートされています (完全レベル)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION = \<制約名の定義句> は、名前付けドメインの制約 (中間レベル) でサポートされています  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<DROP DOMAIN CONSTRAINT 句> サポートされています (完全レベル)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT = \<alter domain> \<DROP domain DEFAULT 句> サポートされています (完全レベル)  
  
 次のビットは、add \<domain constraint> が\<サポートされている場合 (SQL_AD_ADD_DOMAIN_CONSTRAINT ビットが設定されている場合)> サポートされる制約属性を指定します。  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (完全レベル) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (完全レベル) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (完全レベル) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (完全レベル)  
  
 SQL_ALTER_TABLE (ODBC 2.0)  
 データソースでサポートされている**ALTER TABLE**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの横にかっこで囲まれています。  
  
 サポートされている句を判別するには、次のビットマスクを使用します。  
  
 SQL_AT_ADD_COLUMN_COLLATION = \<列の追加> 句がサポートされていますが、列の照合順序 (完全なレベル) を指定する機能があります (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT = \<列の追加> 句がサポートされ、列の既定値を指定するファシリティ (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE = \<列の追加> がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT = \<列の追加> 句がサポートされており、列の制約を指定するファシリティ (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT = \<ADD TABLE 制約> 句がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION = \<制約名の定義> 列およびテーブルの制約の名前付け (中間レベル) でサポートされています (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE = \<列の削除> CASCADE がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT = \<列の変更\<> DROP column DEFAULT 句> サポートされています (中間レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT = \<DROP COLUMN> RESTRICT がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT = \<DROP COLUMN> RESTRICT がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT = \<列の変更\<> SET column DEFAULT 句> サポートされています (中間レベル) (ODBC 3.0)  
  
 次のビットでは、 \<列またはテーブルの制約を指定する場合> サポート制約属性が指定されています (SQL_AT_ADD_CONSTRAINT ビットが設定されています)。  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (フルレベル) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (完全レベル) (odbc 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (フルレベル) (odbc 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (完全レベル) (odbc 3.0)  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 ドライバーの非同期サポートのレベルを示す SQLUINTEGER 値。  
  
 SQL_AM_CONNECTION = 接続レベルの非同期実行はサポートされています。 特定の接続ハンドルに関連付けられているすべてのステートメントハンドルが非同期モードであるか、またはすべてが同期モードであるかのいずれかです。 接続のステートメントハンドルを非同期モードにすることはできません。同じ接続上の別のステートメントハンドルは同期モードであり、その逆も同様です。  
  
 SQL_AM_STATEMENT = ステートメントレベルの非同期実行がサポートされています。 接続ハンドルに関連付けられている一部のステートメントハンドルは非同期モードにすることができますが、同じ接続上の他のステートメントハンドルは同期モードになります。  
  
 SQL_AM_NONE = 非同期モードはサポートされていません。  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 行カウントの可用性に関してドライバーの動作を列挙する SQLUINTEGER ビットマスク。 次のビットマスクは、情報の種類と共に使用されます。  
  
 SQL_BRC_ROLLED_UP = 連続する INSERT、DELETE、または UPDATE ステートメントの行数が1にロールアップされます。 このビットが設定されていない場合は、ステートメントごとに行数を使用できます。  
  
 SQL_BRC_PROCEDURES = 行カウント (存在する場合) は、ストアドプロシージャでバッチが実行されるときに使用できます。 行数が使用可能な場合は、SQL_BRC_ROLLED_UP ビットに応じて、ロールアップすることも、個別に使用することもできます。  
  
 SQL_BRC_EXPLICIT = 行カウント (存在する場合) は、 **Sqlexecute**または**SQLExecDirect**を呼び出すことによって直接バッチが実行されるときに使用できます。 行数が使用可能な場合は、SQL_BRC_ROLLED_UP ビットに応じて、ロールアップすることも、個別に使用することもできます。  
  
## <a name="example"></a>例  
 **SQLGetInfo**は、サポートされているオプションの一覧を **INFOVALUEPTR*の SQLUINTEGER ビットマスクとして返します。 各オプションのビットマスクは、オプションがサポートされているかどうかを判断するためにフラグと共に使用されます。  
  
 たとえば、アプリケーションで次のコードを使用して、その接続に関連付けられているドライバーによって部分文字列スカラー関数がサポートされているかどうかを判断できます。  
  
 **SQLGetInfo**を使用する別の例については、「 [sqltables 関数](../../../odbc/reference/syntax/sqltables-function.md)」を参照してください。  
  
```cpp  
SQLUINTEGER fFuncs;  
  
SQLGetInfo(hdbc,   
           SQL_STRING_FUNCTIONS,  
           (SQLPOINTER)&fFuncs,  
           sizeof(fFuncs),  
           NULL);  
  
// SUBSTRING supported  
if (fFuncs & SQL_FN_STR_SUBSTRING)   
   ;   // do something  
  
// SUBSTRING not supported  
else  
   ;   // do something else  
```  
  
## <a name="related-functions"></a>関連する関数  
 接続属性の設定を返す  
 [SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
 ドライバーが関数をサポートしているかどうかを判断する  
 [SQLGetFunctions 関数](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 ステートメント属性の設定を返す  
 [SQLGetStmtAttr 関数](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 データソースのデータ型に関する情報を返す  
 [SQLGetTypeInfo 関数](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
