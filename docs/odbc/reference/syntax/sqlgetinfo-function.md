---
title: "SQLGetInfo 関数 |Microsoft ドキュメント"
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
- SQLGetInfo
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetInfo
helpviewer_keywords:
- SQLGetInfo function [ODBC]
ms.assetid: 49dceccc-d816-4ada-808c-4c6138dccb64
caps.latest.revision: 48
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 57ba22ee8645f1d3548be91adc9aafb4fc016c79
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetinfo-function"></a>SQLGetInfo 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLGetInfo**接続に関連付けられているドライバーとデータ ソースに関する全般情報を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLGetInfo(  
     SQLHDBC         ConnectionHandle,  
     SQLUSMALLINT    InfoType,  
     SQLPOINTER      InfoValuePtr,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *ConnectionHandle*  
 [入力]接続ハンドルです。  
  
 *情報の種類*  
 [入力]情報の種類。  
  
 *InfoValuePtr*  
 [出力]情報を返すバッファーへのポインター。 によって、*情報の種類*要求されると、返される情報はいずれかに、次の: null で終わる文字列、SQLUSMALLINT 値、SQLUINTEGER ビットマスク、SQLUINTEGER フラグ、SQLUINTEGER のバイナリ値またはSQLULEN 値です。  
  
 場合、*情報の種類*引数が SQL_DRIVER_HDESC または SQL_DRIVER_HSTMT、 *InfoValuePtr*引数が両方の入力し、出力します。 (詳細についてはこの関数の説明の後半 SQL_DRIVER_HDESC または SQL_DRIVER_HSTMT 記述子を参照してください)。  
  
 場合*InfoValuePtr* null、 *StringLengthPtr*はまだバイト (文字データの null 終端文字を除く) の合計数を返しますが指すバッファーに返される使用可能な*InfoValuePtr*です。  
  
 *BufferLength*  
 [入力]長さ、 \* *InfoValuePtr*バッファー。 場合の値 *\*InfoValuePtr*文字の文字列ではない場合、または*InfoValuePtr* null ポインターでは、 *BufferLength*引数は無視されます。 ドライバーでのサイズ *\*InfoValuePtr* SQLUSMALLINT または SQLUINTEGER、に基づいて、*情報の種類*です。 場合 *\*InfoValuePtr* Unicode 文字列です (呼び出し時に**SQLGetInfoW**) では、 *BufferLength* SQLSTATE HY090 (されていない場合、引数が偶数; をする必要があります無効な文字列長またはバッファー長) が返されます。  
  
 *StringLengthPtr*  
 [出力]バイト (文字データの null 終端文字を除く) の合計数を返すバッファーへのポインターで返される使用可能な **InfoValuePtr*です。  
  
 文字データの場合は、使用できるバイト数を返すより大きいまたは等しい*BufferLength*の情報は、 \* *InfoValuePtr*に切り捨てられます*BufferLength* null 終了の長さマイナス バイト文字し、ドライバーによって null で終了します。  
  
 他のすべての種類の値のデータの*BufferLength*は無視されます、ドライバーのサイズを想定して\* *InfoValuePtr*によって SQLUSMALLINT または SQLUINTEGER には、 *情報の種類*です。  
  
## <a name="return-value"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetInfo** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる**SQLGetDiagRec**で、 *HandleType*のSql_handle_dbc としてと*処理*の*ConnectionHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLGetInfo**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|バッファー \* *InfoValuePtr*要求されたすべての情報を返すのに十分な大きさがありません。 そのため、情報が切り詰められました。 切り詰められていない形式で要求された情報の長さが返される **StringLengthPtr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08003|接続は開いていません|(DM) で情報の種類が要求された*情報の種類*開いている接続が必要です。 ODBC によって予約されている情報の種類の接続を開くことがなく SQL_ODBC_VER のみが返されます。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY024|無効な属性値|(DM)、*情報の種類*引数 SQL_DRIVER_HSTMT、れ、値を指す*InfoValuePtr*が有効なステートメントのハンドル。<br /><br /> (DM)、*情報の種類*引数 SQL_DRIVER_HDESC、れ、値を指す*InfoValuePtr*が有効な記述子ハンドル。|  
|HY090|文字列またはバッファーの長さが無効です。|引数の指定された値 (DM) *BufferLength*が 0 未満です。<br /><br /> (DM) の指定された値*BufferLength* 、奇数と *\*InfoValuePtr*されましたが、Unicode データ型。|  
|HY096|範囲外の情報の種類|引数が指定された値*情報の種類*が ODBC ドライバーでサポートされているのバージョンは無効です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能なフィールドが実装されていません|引数が指定された値*情報の種類*ドライバーでサポートされていないドライバー固有の値がします。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に対応するドライバー、 *ConnectionHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 「情報の種類、」このセクションの後半に現在定義されている情報の種類が表示されます。詳細がさまざまなデータ ソースを活用するために定義されることが必要です。 さまざまな種類の情報は ODBC; によって予約されています。ドライバーの開発者は、Open Group から独自ドライバー固有の値を予約する必要があります。 **SQLGetInfo** Unicode 変換は行われませんか*サンキング*(を参照してください[付録 a: ODBC エラー コード](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md)の*ODBC プログラマ リファレンス*) のドライバーの定義済み*InfoTypes*です。 詳細については、次を参照してください。[ドライバー固有のデータ型、記述子の種類、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)です。 返される情報の形式\* *InfoValuePtr*によって異なります、*情報の種類*を要求します。 **SQLGetInfo**は 5 つの異なる形式のいずれかの情報を返します。  
  
-   Null で終わる文字の文字列  
  
-   SQLUSMALLINT 値  
  
-   SQLUINTEGER ビットマスク  
  
-   SQLUINTEGER 値  
  
-   SQLUINTEGER バイナリ値  
  
 形式は次の情報の種類のそれぞれに、型の説明に表示されます。 アプリケーションに返される値をキャストする必要があります **InfoValuePtr*それに従っています。 アプリケーションが SQLUINTEGER ビットマスクからデータを取得できなかった方法の例は、「コード例」を参照してください。  
  
 ドライバーは、次の表で定義されている情報の種類ごとの値を返す必要があります。 情報の種類が適用される場合、ドライバーまたはデータ ソースに、ドライバーは、次の表に示された値のいずれかを返します。  
  
 文字の文字列 ("Y"または"N")  
 "N"  
  
 文字の文字列 ("Y"または"N"ではありません)  
 空の文字列  
  
 SQLUSMALLINT  
 0  
  
 SQLUINTEGER ビットマスクまたは SQLUINTEGER バイナリ値  
 0 L  
  
 たとえば、データ ソースは、プロシージャをサポートしていない場合**SQLGetInfo**の値については、次の表に示された値を返します*情報の種類*プロシージャに関連します。  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 空の文字列  
  
 **SQLGetInfo** SQLSTATE HY096 を返します (無効な引数値) の値が*情報の種類*を ODBC 用に予約の種類の情報の範囲は、ドライバーでサポートされている ODBC のバージョンで定義されていません。 アプリケーションを呼び出す ODBC のバージョンに準拠しているドライバーを特定するのに**SQLGetInfo** SQL_DRIVER_ODBC_VER 情報の種類とします。 **SQLGetInfo** SQLSTATE HYC00 を返します (省略可能な機能が実装されていません) の値が*情報の種類*をドライバー固有の使用に予約の種類の情報の範囲内にあるが、ドライバーによってサポートされていません。  
  
 すべての呼び出しを**SQLGetInfo**場合を除き、開いている接続が必要、*情報の種類*は SQL_ODBC_VER、ドライバー マネージャーのバージョンが返されます。  
  
## <a name="information-types"></a>情報の種類  
 このセクションでサポートされている種類の情報を一覧表示**SQLGetInfo**です。 情報の種類では、明確化され、アルファベット順に表示します。 追加または ODBC 3 の名前が変更された情報の種類*.x*も一覧表示されます。  
  
## <a name="driver-information"></a>ドライバー情報  
 次の値、*情報の種類*引数には、アクティブなステートメント、データ ソース名、およびインターフェイスの標準準拠のレベルの数など、ODBC ドライバーに関する情報が返されます。  
  
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
>  実装するときに**SQLGetInfo**ドライバーの情報が送信されるか、サーバーから要求する回数を最小限に抑え、パフォーマンスが向上します。  
  
## <a name="dbms-product-information"></a>DBMS の製品情報  
 次の値、*情報の種類*引数には、DBMS 名とバージョンなど、DBMS 製品に関する情報が返されます。  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>データ ソースの情報  
 次の値、*情報の種類*引数は、カーソルの特性やトランザクション機能など、データ ソースに関する情報を返します。  
  
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
  
## <a name="supported-sql"></a>サポートされる SQL  
 次の値、*情報の種類*引数は、データ ソースでサポートされる SQL ステートメントに関する情報を返します。 これらの種類の情報が記載されている各機能の SQL 構文は、SQL 92 構文です。 これらの種類の情報入念説明ではありません、全体の SQL 92 文法をします。 代わりに、データのソース通常提供してさまざまなレベルのサポートの文法の一部がについて説明します。 具体的には、sql-92 で DDL ステートメントの多くがについて説明します。  
  
 アプリケーションは、SQL_SQL_CONFORMANCE 情報の種類からのサポートされている文法の一般的なレベルを確認してに説明した標準準拠のレベルからのバリエーションを特定するその他の種類の情報を使用する必要があります。  
  
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
  
## <a name="sql-limits"></a>SQL の制限事項  
 次の値、*情報の種類*引数は、識別子と識別子、および選択リスト内の列の最大数の最大の長さなどの SQL ステートメント内の句に適用される制限に関する情報を返します。 制限事項は、ドライバーまたはデータ ソースのいずれかによって課されることができます。  
  
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
 次の値、*情報の種類*引数は、データ ソースと、ドライバーでサポートされているスカラー関数に関する情報を返します。 スカラー関数の詳細については、次を参照してください。[付録 e: のスカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)です。  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>変換の情報  
 次の値、*情報の種類*引数は、データ ソースが、指定した SQL データ型を変換する SQL データ型の一覧を返す、**変換**スカラー関数。  
  
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
  
## <a name="information-types-added-for-odbc-3x"></a>ODBC 用の種類の情報が追加された 3.x  
 次の値、*情報の種類*ODBC 3 の引数が追加されました*.x*:  
  
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
  
## <a name="information-types-renamed-for-odbc-3x"></a>ODBC の名前が変更の種類の情報 3.x  
 次の値、*情報の種類*ODBC 3 の名前を変更した引数*.x*です。  
  
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
  
## <a name="information-types-deprecated-in-odbc-3x"></a>ODBC では非推奨の種類の情報 3.x  
 次の値、*情報の種類*ODBC 3 で廃止された引数*.x*です。 ODBC 3*.x*ドライバーは ODBC 2 の旧バージョンと互換性のため、これらの種類の情報をサポートするために続行する必要があります*.x*アプリケーションです。 (これらの型の詳細については、次を参照してください[SQLGetInfo サポート](../../../odbc/reference/appendixes/sqlgetinfo-support.md)旧バージョンとの互換性のための付録 g: ドライバーのガイドライン」にします。)。  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>情報の種類の説明  
 次の表は、情報の種類ごと、導入された ODBC とその説明のバージョンにアルファベット順に一覧表示します。  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1.0)  
 文字の文字列:"Y"、ユーザーは、によって返されるすべてのプロシージャを実行できる場合**SQLProcedures**です。"N"プロシージャがある場合は、ユーザーが実行できないことを返されます。  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 文字の文字列:"Y"、ユーザーが保証される場合**選択**によって返されるすべてのテーブル特権**SQLTables**です。"N"のテーブルがある場合に、ユーザーがアクセスできないことが返されます。  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 ドライバーをサポートできるアクティブな環境の最大数を指定する SQLUSMALLINT 値です。 指定された制限がないか、上限が不明な場合、この値は 0 に設定します。  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3.0)  
 集計関数のサポートを列挙する SQLUINTEGER ビットマスク。  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 SQL 92 エントリのレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、 **ALTER ドメイン**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。 SQL 92 完全レベルに準拠したドライバーは、すべてのビットマスクを常に返します。 「0」の戻り値は、つまり、 **ALTER ドメイン**ステートメントはサポートされていません。  
  
 この機能をサポートする必要があります、sql-92 または FIPS 準拠のレベルが各ビットマスクの横にあるかっこ内に表示されます。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT ドメイン制約がサポートされている追加の = (フル レベル)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT =\<ドメインを alter > \<set ドメイン既定句 > はサポートされて (フル レベル)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION =\<制約定義名句 > ドメイン制約 (中間レベル) の名前付けのサポート  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<drop ドメイン制約句 > はサポートされて (フル レベル)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT =\<ドメインを alter > \<drop ドメイン既定句 > はサポートされて (フル レベル)  
  
 次のビットをサポートされている指定\<制約属性 > 場合\<ドメイン制約の追加 > はサポートされて (SQL_AD_ADD_DOMAIN_CONSTRAINT ビットが設定されます)。  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (完全レベル) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (完全レベル) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (完全レベル) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (完全レベル)  
  
 SQL_ALTER_TABLE (ODBC 2.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、 **ALTER TABLE**ステートメント、データ ソースによってサポートされています。  
  
 この機能をサポートする必要があります、sql-92 または FIPS 準拠のレベルが各ビットマスクの横にあるかっこ内に表示されます。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_AT_ADD_COLUMN_COLLATION =\<列の追加 > 句はサポートされて、列の照合順序 (完全レベル) を指定する機能を使用 (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT =\<列の追加 > 句はサポートされて、列の既定値 (FIPS 過渡期レベル) を指定する機能を使用 (ODBC 3.0)  
  
 Sql_at_add_column_single、=\<列の追加 > は (FIPS 過渡期レベル) のサポート (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT =\<列の追加 > 句はサポートされて、列の制約 (FIPS 過渡期レベル) を指定する機能を使用 (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT =\<テーブル制約の追加 > 句がサポートされている (FIPS 過渡期レベル) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION =\<制約名の定義 > は列とテーブルの制約 (中間レベル) の名前付けのサポート (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE =\<ドロップ列 > CASCADE がサポートされている (FIPS 過渡期レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT =\<列を alter > \<drop 列の既定の句 > は (中間レベル) のサポート (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT =\<ドロップ列 > 制限がサポートされている (FIPS 過渡期レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT =\<ドロップ列 > 制限がサポートされている (FIPS 過渡期レベル) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT =\<列を alter >\<セット列の default 句 > は (中間レベル) をサポート (ODBC 3.0)  
  
 次のビットのサポートを指定する\<制約属性 > の列またはテーブルの制約の指定がサポートされている場合 (SQL_AT_ADD_CONSTRAINT ビットが設定されます)。  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (完全レベル) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (完全レベル) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (完全レベル) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (完全レベル) (ODBC 3.0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3.8)  
 かどうか、ドライバーに対して実行できます関数に非同期的に、接続ハンドルを示す SQLUINTEGER 値。  
  
 SQL_ASYNC_DBC_CAPABLE = ドライバーでは、接続の機能を非同期的に実行できます。  
  
 SQL_ASYNC_DBC_NOT_CAPABLE = ドライバーの接続の機能を非同期的に実行いないことができます。  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 ドライバーでの非同期のサポートのレベルを示す SQLUINTEGER 値:  
  
 SQL_AM_CONNECTION = 接続レベルの非同期実行をサポートします。 か、指定された接続ハンドルに関連付けられたすべてのステートメント ハンドルは非同期モードで、または同期モードではすべて。 接続のステートメント ハンドルは、同じ接続上の別のステートメント ハンドルが同期モードでは、その逆で非同期モードですることはできません。  
  
 SQL_AM_STATEMENT = ステートメント レベルの非同期実行がサポートされています。 接続ハンドルに関連付けられているいくつかのステートメント ハンドルを同期モードで、同じ接続で他のステートメント ハンドルされているときに非同期モードで指定できます。  
  
 SQL_AM_NONE = 非同期モードはサポートされていません。  
  
 SQL_ASYNC_NOTIFICATION  
 ドライバーが非同期通知をサポートしているかを示す SQLUINTEGER 値:  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE**非同期実行の通知は、ドライバーでサポートされています。  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE**非同期実行の通知は、ドライバーによってサポートされていません。  
  
 ODBC の非同期操作の 2 つのカテゴリがあります: 接続レベルの非同期操作およびステートメント レベルの非同期操作です。  SQL_ASYNC_NOTIFICATION_CAPABLE をドライバーに返された場合は、非同期的に実行できるすべての Api の通知をサポートしてする必要があります。  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 行の可用性に対するドライバーの動作を列挙する SQLUINTEGER ビットマスクをカウントします。 以下のビットマスクは、情報の種類と共に使用されます。  
  
 SQL_BRC_ROLLED_UP = 行数は、連続する INSERT、DELETE、または UPDATE ステートメントを 1 つにロールアップします。 このビットが設定されていない場合は、各ステートメントに対して行カウントがあります。  
  
 SQL_BRC_PROCEDURES = ストアド プロシージャのバッチを実行すると、いずれかが使用可能な場合、行カウントします。 行数が使用可能な場合は、上または SQL_BRC_ROLLED_UP ビットによって、個別に使用できる、ロールできます。  
  
 SQL_BRC_EXPLICIT バッチを呼び出すことによって直接実行すると、いずれかが使用可能な場合は、行のカウントを = **SQLExecute**または**SQLExecDirect**です。 行数が使用可能な場合は、上または SQL_BRC_ROLLED_UP ビットによって、個別に使用できる、ロールできます。  
  
 SQL_BATCH_SUPPORT (ODBC 3.0)  
 バッチのドライバーのサポートを列挙する SQLUINTEGER ビットマスクです。 以下のビットマスクを使用して、どのレベルがサポートされているを調べます。  
  
 SQL_BS_SELECT_EXPLICIT = ドライバー サポート明示的なバッチをことができますが結果セットのステートメントを生成します。  
  
 SQL_BS_ROW_COUNT_EXPLICIT = ドライバー サポート明示的なバッチを生成するステートメントの行の数を持つことができます。  
  
 SQL_BS_SELECT_PROC = ドライバー サポート明示的な手順では、ことができますが結果セットのステートメントを生成します。  
  
 SQL_BS_ROW_COUNT_PROC = のドライバー サポート明示的なプロシージャを生成するステートメントの行の数を持つことができます。  
  
 SQL_BOOKMARK_PERSISTENCE (ODBC 2.0)  
 使用されるブックマークを永続化操作を列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを使用して、フラグと共に判断オプション ブックマークの永続化します。  
  
 SQL_BP_CLOSE = アプリケーションの呼び出し後、ブックマークは有効な**SQLFreeStmt** SQL_CLOSE オプション、または**SQLCloseCursor**ステートメントに関連付けられているカーソルを閉じます。  
  
 SQL_BP_DELETE、行が有効ではその行を削除した後、ブックマークを = です。  
  
 SQL_BP_DROP = アプリケーションの呼び出し後、ブックマークは有効な**SQLFreeHandle**で、 *HandleType* sql_handle_stmt としてステートメントを削除するのです。  
  
 SQL_BP_TRANSACTION = アプリケーションをコミットまたはトランザクションをロールバックした後、ブックマークは有効です。  
  
 SQL_BP_UPDATE 行が有効ではその行の任意の列が更新された後、キー列を含むブックマークを = です。  
  
 SQL_BP_OTHER_HSTMT いずれかに関連付けられているブックマークを = ステートメントは、別のステートメントで使用できます。 SQL_BP_CLOSE または SQL_BP_DROP が指定されていない限り、最初のステートメントでカーソルが開いていなければなりません。  
  
 SQL_CATALOG_LOCATION (ODBC 2.0)  
 修飾テーブル名に、カタログの位置を示す SQLUSMALLINT 値:  
  
 SQL_CL_STARTSQL_CL_END  
  
 たとえば、Xbase ドライバーは、ディレクトリ (カタログ) 名が \EMPDATA\EMP と同様に、テーブル名の先頭にあるために、SQL_CL_START を返します。DBF です。 ORACLE Server ドライバーでは、カタログが、テーブル名の末尾としてため SQL_CL_END が返されますADMIN.EMP@EMPDATAです。  
  
 SQL 92 全体のレベル – 準拠ドライバーでは、SQL_CL_START は常に返します。 カタログは、データ ソースによってサポートされていない場合、値 0 が返されます。 カタログがサポートされているかどうかを決定するには、アプリケーションが呼び出す**SQLGetInfo** SQL_CATALOG_NAME 情報の種類とします。  
  
 これは、*情報の種類*名前が変更された ODBC 2.0 から 3.0 の ODBC*情報の種類*SQL_QUALIFIER_LOCATION です。  
  
 SQL_CATALOG_NAME (ODBC 3.0)  
 文字の文字列:"Y"場合はそうでない場合、カタログ名または"N"をサーバーがサポートされます。  
  
 SQL 92 全体のレベル – 準拠ドライバーでは、"Y"は常に返します。  
  
 SQL_CATALOG_NAME_SEPARATOR (ODBC 1.0)  
 文字の文字列: カタログ名、および依存するか、その前にあるされる修飾名要素間の区切り記号として、データ ソースを定義する文字。  
  
 カタログは、データ ソースによってサポートされていない場合は、空の文字列が返されます。 カタログがサポートされているかどうかを決定するには、アプリケーションが呼び出す**SQLGetInfo** SQL_CATALOG_NAME 情報の種類とします。 SQL 92 全体のレベル – 準拠するドライバーは常に返します"です。"です。  
  
 これは、*情報の種類*名前が変更された ODBC 2.0 から 3.0 の ODBC*情報の種類*SQL_QUALIFIER_NAME_SEPARATOR です。  
  
 SQL_CATALOG_TERM (ODBC 1.0)  
 カタログ; のデータ ソースの仕入先の名前を持つ文字の文字列たとえば、"database"または"directory"です。 この文字列は、上部、下部、または大文字と小文字にすることができます。  
  
 カタログは、データ ソースによってサポートされていない場合は、空の文字列が返されます。 カタログがサポートされているかどうかを決定するには、アプリケーションが呼び出す**SQLGetInfo** SQL_CATALOG_NAME 情報の種類とします。 SQL 92 全体のレベル – 準拠ドライバーでは、「カタログ」は常に返します。  
  
 これは、*情報の種類*名前が変更された ODBC 2.0 から 3.0 の ODBC*情報の種類*SQL_QUALIFIER_TERM です。  
  
 SQL_CATALOG_USAGE (ODBC 2.0)  
 カタログを使用することができますステートメントを列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを使用して、カタログを使用できる場所を調べます。  
  
 SQL_CU_DML_STATEMENTS = カタログがすべてのデータ操作言語ステートメントでサポートされて:**選択**、**挿入**、**更新**、 **DELETE**、サポートされている場合**更新用に選択**更新を配置し、ステートメントを削除します。  
  
 SQL_CU_PROCEDURE_INVOCATION = カタログが ODBC プロシージャ呼び出しステートメントでサポートされています。  
  
 SQL_CU_TABLE_DEFINITION = カタログがすべてのテーブル定義ステートメントでサポートされて: **CREATE TABLE**、 **CREATE VIEW**、 **ALTER TABLE**、 **DROP TABLE**、および**ドロップ ビュー**です。  
  
 SQL_CU_INDEX_DEFINITION = カタログがすべてのインデックス定義ステートメントでサポートされて: **CREATE INDEX**と**DROP INDEX**です。  
  
 SQL_CU_PRIVILEGE_DEFINITION = カタログがすべての特権定義ステートメントでサポートされて: **GRANT**と**取り消す**です。  
  
 カタログは、データ ソースによってサポートされていない場合、値 0 が返されます。 カタログがサポートされているかどうかを決定するには、アプリケーションが呼び出す**SQLGetInfo** SQL_CATALOG_NAME 情報の種類とします。 SQL 92 全体のレベル – 準拠するドライバーは、これらのビット セットのすべてのビットマスクを常に返します。  
  
 これは、*情報の種類*名前が変更された ODBC 2.0 から 3.0 の ODBC*情報の種類*SQL_QUALIFIER_USAGE です。  
  
 SQL_COLLATION_SEQ (ODBC 3.0)  
 照合順序の名前。 これは、既定の文字がこのサーバーのセットの既定の照合順序の名前を示す文字の文字列 (たとえば、' ISO 8859-1' または EBCDIC)。 これが不明の場合は、空の文字列が返されます。 SQL 92 全体のレベル – 準拠するドライバーには、常に空でない文字列が返されます。  
  
 SQL_COLUMN_ALIAS (ODBC 2.0)  
 文字の文字列:"Y"データ ソースは、列の別名をサポートしている場合それ以外の場合、"N"です。  
  
 列の別名は、AS 句を使用して、選択リスト内の列に指定できる代替名です。 SQL 92 エントリのレベル – 準拠ドライバーでは、"Y"は常に返します。  
  
 SQL_CONCAT_NULL_BEHAVIOR (ODBC 1.0)  
 データ ソースが NULL を連結したものを処理する方法を示す SQLUSMALLINT 値には、NULL 以外の値を持つ文字データ型の列と文字データ型の列が値。  
  
 SQL_CB_ = NULL 値になります。  
  
 SQL_CB_NON_ = 結果が NULL 以外の値を持つ列または列を連結します。  
  
 SQL 92 エントリのレベル – 準拠ドライバーでは、SQL_CB_ は常に返します。  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1.0)  
 SQLUINTEGER ビットマスクです。 ビットマスクを使用して、データ ソースでサポートされる変換を示します、**変換**という名前で型のデータのスカラー関数、*情報の種類*です。 対応するビットマスクが 0 に等しい場合、データ ソースには、同じデータ型への変換を含む、名前付きの型のデータから、変換はできません。  
  
 たとえば、調べるには、データ ソースが SQL_INTEGER データの SQL_BIGINT データ型への変換をサポートしているかどうか、アプリケーションが呼び出す**SQLGetInfo**で、*情報の種類*SQL_CONVERT_INTEGER のです。 アプリケーションの実行、 **AND** SQL_CVT_BIGINT と返されるビットマスクで操作します。 結果の値が 0 以外の場合は、変換はサポートされています。  
  
 以下のビットマスクを使用して、どの変換がサポートされているを調べます。  
  
 SQL_CVT_BIGINT (ODBC 1.0) SQL_CVT_BINARY (ODBC 1.0) SQL_CVT_BIT (ODBC 1.0) SQL_CVT_GUID (ODBC 3.5) SQL_CVT_CHAR (ODBC 1.0) SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DECIMAL (ODBC 1.0) SQL_CVT_DOUBLE (ODBC 1.0) (ODBC 1.0) SQL_CVT_FLOAT、SQL_CVT_INTEGER (ODBC 1.0) SQL_CVT_INTERVAL_YEAR_MONTH (ODBC 3.0) SQL_CVT_INTERVAL_DAY_TIME (ODBC 3.0) SQL_CVT_LONGVARBINARY (ODBC 1.0) SQL_CVT_LONGVARCHAR (ODBC 1.0) SQL_CVT_NUMERIC (ODBC 1.0) SQL_CVT_REAL ODBC 1.0) (ODBC 1.0) SQL_CVT_SMALLINT、SQL_CVT_TIME (ODBC 1.0) SQL_CVT_タイムスタンプ (ODBC 1.0) (ODBC 1.0) を SQL_CVT_TINYINT、SQL_CVT_VARBINARY、(ODBC 1.0)、SQL_CVT_VARCHAR、(ODBC 1.0)  
  
 SQL_CONVERT_FUNCTIONS (ODBC 1.0)  
 ドライバーと関連付けられているデータ ソースでサポートされているスカラー変換関数を列挙する SQLUINTEGER ビットマスクです。  
  
 次のビットマスクを使用してがサポートする変換関数を調べます。  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME (ODBC 1.0)  
 テーブルの相関名がサポートされるかどうかを示す SQLUSMALLINT 値:  
  
 SQL_CN_NONE = 相関名はサポートされません。  
  
 SQL_CN_DIFFERENT = 相関名がサポートされますが、それらが表すテーブルの名前と異なる必要があります。  
  
 SQL_CN_ANY = 相関名はサポートされているし、有効なユーザー定義の名前を指定できます。  
  
 SQL 92 エントリのレベル – 準拠ドライバーでは、SQL_CN_ANY は常に返します。  
  
 SQL_CREATE_ASSERTION (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、**作成アサーション**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_CA_CREATE_ASSERTION  
  
 制約の属性を明示的に指定する機能がサポートされている場合、次のビットがサポートされている制約属性を指定 (SQL_ALTER_TABLE と SQL_CREATE_TABLE 情報の種類を参照してください)。  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 SQL 92 全体のレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。 「0」の戻り値は、つまり、**作成アサーション**ステートメントはサポートされていません。  
  
 SQL_CREATE_CHARACTER_SET (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、**文字セットの作成**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 SQL 92 全体のレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。 「0」の戻り値は、つまり、**文字セットの作成**ステートメントはサポートされていません。  
  
 SQL_CREATE_COLLATION (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、**照合順序の作成**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 次に対応するビットマスクを使用して、どの句がサポートされているかを調べます。  
  
 SQL_CCOL_CREATE_COLLATION  
  
 SQL 92 フルのレベル – 準拠ドライバーでは、サポートされている、このオプションは常に返します。 「0」の戻り値は、つまり、**照合順序の作成**ステートメントはサポートされていません。  
  
 SQL_CREATE_DOMAIN (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、**ドメインの作成**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_CDO_CREATE_DOMAIN = ドメインの作成ステートメントは、サポート (中間レベル)。  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION =\<制約名の定義 > ドメイン制約 (中間レベル) の名前付けのサポートされています。  
  
 次のビット列の制約: SQL_CDO_DEFAULT を作成する機能を指定する = ドメイン制約を指定することは (中間レベル) SQL_CDO_CONSTRAINT = ドメインの既定値を指定することは (中間レベル) SQL_CDO_COLLATION =ドメインの照合順序を指定することは (フル レベル)  
  
 ドメインの制約を指定することがサポートされている場合、次のビットがサポートされている制約の属性を指定 (SQL_CDO_DEFAULT が設定されます)。  
  
 SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (完全レベル) SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE (完全レベル) SQL_CDO_CONSTRAINT_DEFERRABLE (完全レベル) SQL_CDO_CONSTRAINT_NON_DEFERRABLE (完全レベル)  
  
 「0」の戻り値は、つまり、**ドメインの作成**ステートメントはサポートされていません。  
  
 SQL_CREATE_SCHEMA (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、 **CREATE SCHEMA**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 SQL 92 中級者向けの準拠レベル ドライバーでは、サポートされている、SQL_CS_CREATE_SCHEMA と SQL_CS_AUTHORIZATION オプションは常に返します。 これらはまた、SQL 92 エントリ レベルでは必ずしも SQL ステートメントとしてサポートする必要があります。 SQL 92 全体のレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。  
  
 SQL_CREATE_TABLE (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、 **CREATE TABLE**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 この機能をサポートする必要があります、sql-92 または FIPS 準拠のレベルが各ビットマスクの横にあるかっこ内に表示されます。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_CT_CREATE_TABLE =「CREATE TABLE ステートメントはサポートされています。 (Entry レベル)  
  
 SQL_CT_TABLE_CONSTRAINT = テーブル制約を指定することは (FIPS 過渡期レベル)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION =、\<制約名の定義 > 句は、列およびテーブルの制約 (中間レベル) の名前付けのサポート  
  
 次のビットは、一時テーブルを作成する機能を指定します。  
  
 SQL_CT_COMMIT_PRESERVE = 削除された行がコミット時に保持されます。 (完全レベル)SQL_CT_COMMIT_DELETE = 削除された行がコミット時に削除されます。 (完全レベル)SQL_CT_GLOBAL_TEMPORARY = グローバル一時テーブルを作成することができます。 (完全レベル)SQL_CT_LOCAL_TEMPORARY = ローカル一時テーブルを作成することができます。 (完全レベル)  
  
 次のビットは、列の制約を作成する権限を指定します。  
  
 SQL_CT_COLUMN_CONSTRAINT = 列の制約を指定することは (FIPS 過渡期レベル) SQL_CT_COLUMN_DEFAULT = 列の既定値を指定することは (FIPS 過渡期レベル) SQL_CT_COLUMN_COLLATION = 列の照合順序の指定(完全レベル) のサポート  
  
 次のビットは、列またはテーブルの制約の指定がサポートされている場合に、サポートされている制約属性を指定します。  
  
 SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (完全レベル) SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE (完全レベル) SQL_CT_CONSTRAINT_DEFERRABLE (完全レベル) SQL_CT_CONSTRAINT_NON_DEFERRABLE (完全レベル)  
  
 SQL_CREATE_TRANSLATION (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、**作成翻訳**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 次に対応するビットマスクを使用して、どの句がサポートされているかを調べます。  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 SQL 92 全体のレベル – 準拠ドライバーでは、サポートされている、これらのオプションは常に返します。 「0」の戻り値は、つまり、**翻訳の作成**ステートメントはサポートされていません。  
  
 SQL_CREATE_VIEW (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、 **CREATE VIEW**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 「0」の戻り値は、つまり、 **CREATE VIEW**ステートメントはサポートされていません。  
  
 SQL 92 エントリのレベル – 準拠ドライバーでは、サポートされている、SQL_CV_CREATE_VIEW と SQL_CV_CHECK_OPTION オプションは常に返します。  
  
 SQL 92 全体のレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。  
  
 SQL_CURSOR_COMMIT_BEHAVIOR (ODBC 1.0)  
 示す SQLUSMALLINT 値方法、**コミット**操作は、カーソルと、データ ソース (トランザクションをコミットする場合、データ ソースの動作) で準備されたステートメントに影響します。  
  
 この属性の値は、次の設定の現在の状態が反映されます。 SQL_COPT_SS_PRESERVE_CURSORS です。  
  
 SQL_CB_DELETE = カーソルを閉じると、準備されたステートメントを削除します。 カーソルを使用するには、もう一度アプリケーションする必要がありますを再び準備し、ステートメントを再実行します。  
  
 SQL_CB_CLOSE 閉じるカーソルを = です。 アプリケーションを呼び出して、準備されたステートメントは、用**SQLExecute**呼び出さずに、ステートメントで**SQLPrepare**もう一度です。 SQL ODBC ドライバーの既定値は、SQL_CB_CLOSE です。 これは、トランザクションをコミットする場合に、SQL ODBC ドライバーが、カーソルを閉じることを意味します。  
  
 SQL_CB_PRESERVE 以前と同じ位置に保持するカーソルを =、**コミット**操作します。 アプリケーションは、データをフェッチし続けることができます、またはカーソルを閉じて、再度準備せずに、ステートメントを再実行します。  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR (ODBC 1.0)  
 示す SQLUSMALLINT 値方法、**ロールバック**操作は、カーソルと、データ ソースで準備されたステートメントに影響します。  
  
 SQL_CB_DELETE = カーソルを閉じると、準備されたステートメントを削除します。 カーソルを使用するには、もう一度アプリケーションする必要がありますを再び準備し、ステートメントを再実行します。  
  
 SQL_CB_CLOSE 閉じるカーソルを = です。 アプリケーションを呼び出して、準備されたステートメントは、用**SQLExecute**呼び出さずに、ステートメントで**SQLPrepare**もう一度です。  
  
 SQL_CB_PRESERVE 以前と同じ位置に保持するカーソルを =、**ロールバック**操作します。 アプリケーションは、データをフェッチし続けることができますか、カーソルを閉じて再びその準備せず、ステートメントを再実行されます。  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3.0)  
 カーソルと小文字の区別のサポートを示す SQLUINTEGER 値:  
  
 SQL_INSENSITIVE、同じトランザクション内の他のすべてのカーソルが結果セットのことに加えられた変更を反映せず、ステートメント ハンドル上のすべてのカーソルを = です。  
  
 SQL_UNSPECIFIED = かどうかのカーソル ステートメント ハンドルに表示されるように、同じトランザクション内の別のカーソルが結果セットに対して行った変更指定ではありません。 ステートメント ハンドルにカーソルが表示されるようになしでは、このようないくつか、またはすべての変更。  
  
 SQL_SENSITIVE = カーソルは、同じトランザクション内の他のカーソルによって行われた変更に影響します。  
  
 SQL 92 エントリのレベル – 準拠ドライバーでは、サポートされている、SQL_UNSPECIFIED オプションは常に返します。  
  
 SQL 92 フルのレベル – 準拠ドライバーでは、サポートされている、SQL_INSENSITIVE オプションは常に返します。  
  
 SQL_DATA_SOURCE_NAME (ODBC 1.0)  
 接続時に使用したデータ ソース名を持つ文字列を返します。 アプリケーションが呼び出された場合**SQLConnect**、これは、値、 *szDSN*引数。 アプリケーションが呼び出された場合**SQLDriverConnect**または**SQLBrowseConnect**、これは、DSN キーワードと、ドライバーに渡された接続文字列内の値。 接続文字列が含まれていない場合、 **DSN**キーワード (に含まれている場合など、**ドライバー**キーワード)、これは、空の文字列。  
  
 SQL_DATA_SOURCE_READ_ONLY (ODBC 1.0)  
 文字列を返します。 "Y"場合は、それ以外の場合がある場合、データ ソースが読み取り専用モード、"N"に設定します。  
  
 この特性は、データ ソース自体にのみ関連します。データ ソースにアクセスできるようにするドライバーの特性はありません。 読み取り/書き込みであるドライバーは、読み取り専用であるデータ ソースで使用できます。 ドライバーが読み取り専用の場合は、すべてのデータ ソースの読み取り専用にする必要があり、SQL_DATA_SOURCE_READ_ONLY を返す必要があります。  
  
 SQL_DATABASE_NAME (ODBC 1.0)  
 文字は、データ ソースには「データベース」と呼ばれる名前付きオブジェクトが定義されている場合、使用して、現在のデータベースの名前の文字列です。  
  
> [!NOTE]  
>  ODBC 3*.x*、この値が返される*情報の種類*呼び出しによって返されることができますも**SQLGetConnectAttr**で、*属性*SQL_ATTR_CURRENT_CATALOG の引数。  
  
 SQL_DATETIME_LITERALS (ODBC 3.0)  
 データ ソースによってサポートされる SQL 92 日付時刻リテラルが列挙する SQLUINTEGER ビットマスクです。 日付時刻リテラルが、SQL 92 仕様に記載され、ODBC で定義されている datetime リテラルのエスケープ句とは別に注意してください。 ODBC 日付時刻リテラルのエスケープ句の詳細については、次を参照してください。[日付、時刻、およびタイムスタンプのリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)です。  
  
 FIPS 過渡期のレベル – 準拠するドライバーは、次の一覧内のビットのビットマスクの「1」の値を常に返します。 「0」の場合は、sql-92 日付時刻リテラルがサポートされていないことの値です。  
  
 以下のビットマスクを使用して、どのリテラルがサポートされているを調べます。  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME (ODBC 1.0)  
 ドライバーによってアクセスされる DBMS の製品の名前を持つ文字列を返します。  
  
 SQL_DBMS_VER (ODBC 1.0)  
 ドライバーによってアクセスされる DBMS の製品のバージョンを示す文字列。 バージョンの形式は、##. ##. ###、ここで最初の 2 桁はメジャー バージョン、次の 2 桁はマイナーのバージョンであり、最後の 4 桁の数字は、リリース バージョン。 ドライバーは、このフォームで DBMS の製品のバージョンをレンダリングする必要がありますが、DBMS の製品に固有のバージョンでも追加できます。 たとえば、"04.01.0000 Rdb 4.1"です。  
  
 SQL_DDL_INDEX (ODBC 3.0)  
 作成し、インデックスのドロップのサポートを示す SQLUINTEGER 値:  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION (ODBC 1.0)  
 データ ソースのドライバーまたはデータ ソース、または場合は 0 でサポートされる既定のトランザクション分離レベルを示す SQLUINTEGER 値は、トランザクションをサポートしていません。 トランザクション分離レベルを定義する、次の用語が使用されます。  
  
 **ダーティ リード**トランザクション 1 が行を変更します。 トランザクション 2 は、トランザクション 1 が変更をコミットする前に、変更された行を読み取ります。 トランザクション 1 は、変更をロールバック場合、トランザクション 2 が行を読み取ることは、存在しないと見なされます。  
  
 **反復不能読み取り**トランザクション 1 が、行を読み取ります。 トランザクション 2 は、更新、またはその行を削除し、この変更をコミットします。 トランザクション 1 が、行を再読み込みしようとすると場合を別の行の値を受け取るまたは、行が削除されたことを検出します。  
  
 **ファントム**トランザクション 1 が一部の検索条件に適合する行のセットを読み取ります。 トランザクション 2 は、検索条件に一致する (挿入または更新のいずれか) を通じて 1 つまたは複数の行を生成します。 トランザクション 1 では、行を読み取り、ステートメントを reexecutes 場合、異なる一連の行を受け取ります。  
  
 データ ソースは、トランザクションをサポートする場合、ドライバーは以下のビットマスクのいずれかのディメンションを返します。  
  
 SQL_TXN_READ_UNCOMMITTED = ダーティ リード、反復不能読み取り、およびファントムがあります。  
  
 SQL_TXN_READ_COMMITTED = Dirty 読み取りは可能でありません。 反復不能読み取りやファントムが可能です。  
  
 SQL_TXN_REPEATABLE_READ = ダーティ リード、反復不能読み取りは可能でありません。 ファントム場合があります。  
  
 SQL_TXN_SERIALIZABLE = トランザクションはシリアル化します。 シリアル化可能なトランザクションでは、ダーティ リード、反復不能読み取りやファントムは使用できません。  
  
 SQL_DESCRIBE_PARAMETER (ODBC 3.0)  
 文字の文字列:"Y"パラメーターを記述する場合"N"、されていない場合。  
  
 サポートするため、SQL 92 フルのレベル – 準拠するドライバーは"Y"を返します通常は、**説明の入力**ステートメントです。 この直接指定していないので、基になる SQL サポート、ただし、パラメーターを記述する可能な SQL 92 完全レベル – 準拠ドライバーであってもします。  
  
 SQL_DM_VER (ODBC 3.0)  
 ドライバー マネージャーのバージョンと文字の文字列。 形式は、バージョン ##. ##. ###. ###、どこで。  
  
 最初の 2 桁の数字のセットは、定数 SQL_SPEC_MAJOR によって指定されている、主要な ODBC バージョンです。  
  
 2 桁の数字の 2 番目のセットは、ODBC のマイナー バージョン、定数 SQL_SPEC_MINOR によって指定されたです。  
  
 4 桁の数字の 3 番目のセットは、ドライバー マネージャーのメジャー ビルド番号です。  
  
 4 桁の数字の最後のセットは、ドライバー マネージャーのマイナー ビルド番号です。  
  
 Windows 7 のドライバー マネージャーのバージョンでは、03.80 です。 Windows 8 のドライバー マネージャーのバージョンでは、03.81 です。  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3.8)  
 SQLUINTEGER 値を示す場合は、ドライバーがドライバーに対応するプールをサポートします。 (詳細については、次を参照してください。[ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)です。  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLE では、ドライバーがドライバー対応のプーリング メカニズムをサポートできることを示します。  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLE では、ドライバーがドライバー対応のプーリング メカニズムをサポートできないことを示します。  
  
 ドライバーは SQL_DRIVER_AWARE_POOLING_SUPPORTED を実装する必要はありませんし、ドライバー マネージャーは、ドライバーの戻り値には許可されません。  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV (ODBC 1.0)  
 SQLULEN 値、ドライバーの環境ハンドルまたは接続ハンドルを引数によって決まります*情報の種類*です。  
  
 これらの種類の情報は、ドライバー マネージャーによってのみ実装されます。  
  
 SQL_DRIVER_HDESC (ODBC 3.0)  
 値の SQLULEN での入力を渡す必要がある、ドライバー マネージャーの記述子ハンドルによって決定されます、ドライバーの記述子ハンドル\* *InfoValuePtr*アプリケーションからです。 この場合、 *InfoValuePtr*入力と出力の両方の引数です。 入力記述子ハンドルが渡されました\* *InfoValuePtr*必要があります明示的または暗黙的に割り当てられて上、 *ConnectionHandle*です。  
  
 アプリケーションが処理を呼び出す前に、ドライバー マネージャーの記述子のコピーを作成する必要があります**SQLGetInfo**でこの情報の種類、出力時に、ハンドルが上書きされないことを確認します。  
  
 この情報の種類は、ドライバー マネージャーによってのみ実装されます。  
  
 SQL_DRIVER_HLIB (ODBC 2.0)  
 SQLULEN 値では、 *hinst*ロード ライブラリから返されるドライバー マネージャーに Microsoft Windows オペレーティング システム、またはそれと同等の別のオペレーティング システムでドライバー DLL が読み込まれるときにします。 ハンドルがへの呼び出しで指定された接続ハンドルでのみ有効**SQLGetInfo**です。  
  
 この情報の種類は、ドライバー マネージャーによってのみ実装されます。  
  
 SQL_DRIVER_HSTMT (ODBC 1.0)  
 値の SQLULEN での入力を渡す必要がある、ドライバー マネージャーのステートメント ハンドルによって決定されます、ドライバーのステートメント ハンドル\* *InfoValuePtr*アプリケーションからです。 この場合、 *InfoValuePtr*は入力と出力引数の両方です。 入力ステートメント ハンドルが渡されました\* *InfoValuePtr*引数に対して割り当てられている必要があります*ConnectionHandle*です。  
  
 アプリケーションが処理を呼び出す前に、ドライバー マネージャーのステートメントのコピーを作成する必要があります**SQLGetInfo**ハンドルが出力時に上書きされないようにする、この情報の種類とします。  
  
 この情報の種類は、ドライバー マネージャーによってのみ実装されます。  
  
 SQL_DRIVER_NAME (ODBC 1.0)  
 データ ソースにアクセスするために使用するドライバーのファイル名を持つ文字列を返します。  
  
 SQL_DRIVER_ODBC_VER (ODBC 2.0)  
 ドライバーがサポートする ODBC のバージョンと文字の文字列。 バージョンの形式は、##. ##、ここで最初の 2 つの数字、メジャー バージョンとは、次の 2 つの数字はマイナー バージョン。 SQL_SPEC_MAJOR と SQL_SPEC_MINOR、メジャーおよびマイナー バージョン番号を定義します。 バージョンについては、このマニュアルで説明されている ODBC のこれらは 3 と 0 の場合と、ドライバーは、「03.00」で返す必要があります。  
  
 ODBC ドライバー マネージャーでは、既存のアプリケーションの旧バージョンとの互換性を維持する SQLGetInfo(SQL_DRIVER_ODBC_VER) の戻り値は変更されません。 ドライバーは、返される値を指定します。 データ型の C 拡張機能をサポートするドライバーが 3.8 (またはそれ以降) の場合に返す必要がありますただし、アプリケーションが呼び出す**SQLSetEnvAttr** 3.8 にまたを設定します。 詳細については、次を参照してください。 [ODBC における C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)です。  
  
 SQL_DRIVER_VER (ODBC 1.0)  
 ドライバーのバージョン、および必要に応じて、ドライバーの説明の文字列を返します。 形式では、バージョンには、少なくとも ##. ##. ###、ここで最初の 2 桁はメジャー バージョン、次の 2 桁はマイナーのバージョンであり、最後の 4 桁の数字は、リリース バージョン。  
  
 SQL_DROP_ASSERTION (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、**ドロップ アサーション**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 次に対応するビットマスクを使用して、どの句がサポートされているかを調べます。  
  
 SQL_DA_DROP_ASSERTION  
  
 SQL 92 フルのレベル – 準拠ドライバーでは、サポートされている、このオプションは常に返します。  
  
 SQL_DROP_CHARACTER_SET (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、**文字セットの削除**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 次に対応するビットマスクを使用して、どの句がサポートされているかを調べます。  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 SQL 92 フルのレベル – 準拠ドライバーでは、サポートされている、このオプションは常に返します。  
  
 SQL_DROP_COLLATION (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、**照合順序のドロップ**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 次に対応するビットマスクを使用して、どの句がサポートされているかを調べます。  
  
 SQL_DC_DROP_COLLATION  
  
 SQL 92 フルのレベル – 準拠ドライバーでは、サポートされている、このオプションは常に返します。  
  
 SQL_DROP_DOMAIN (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、 **DROP DOMAIN**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 SQL 92 中級者向けのレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。  
  
 SQL_DROP_SCHEMA (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、 **DROP SCHEMA**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 SQL 92 中級者向けのレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。  
  
 SQL_DROP_TABLE (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、 **DROP TABLE**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 FIPS 過渡期のレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。  
  
 SQL_DROP_TRANSLATION (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、**ドロップ翻訳**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 次に対応するビットマスクを使用して、どの句がサポートされているかを調べます。  
  
 SQL_DTR_DROP_TRANSLATION  
  
 SQL 92 フルのレベル – 準拠ドライバーでは、サポートされている、このオプションは常に返します。  
  
 SQL_DROP_VIEW (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、 **DROP VIEW**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 FIPS 過渡期のレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 ドライバーでサポートされている、動的カーソルの属性を記述する SQLUINTEGER ビットマスクです。 このビットマスクには、属性の最初のサブセットが含まれています。2 番目のサブセット SQL_DYNAMIC_CURSOR_ATTRIBUTES2 を参照してください。  
  
 以下のビットマスクを使用して、どの属性がサポートされているを調べます。  
  
 Sql_ca1_next、A を = *FetchOrientation* SQL_FETCH_NEXT の引数がへの呼び出しでサポートされている**SQLFetchScroll**カーソルが動的カーソルの場合。  
  
 SQL_CA1_ABSOLUTE = *FetchOrientation* SQL_FETCH_FIRST、SQL_FETCH_LAST、および SQL_FETCH_ABSOLUTE の引数がへの呼び出しでサポートされている**SQLFetchScroll**カーソルが動的カーソルの場合。 (フェッチされる行セットは、現在のカーソル位置に依存しない)。  
  
 SQL_CA1_RELATIVE = *FetchOrientation* SQL_FETCH_PRIOR SQL_FETCH_RELATIVE の引数がへの呼び出しでサポートされている**SQLFetchScroll**カーソルが動的カーソルの場合。 (フェッチされる行セットは、現在のカーソル位置によって異なります。 ただし、順方向専用カーソルで SQL_FETCH_NEXT のみがサポートされているため、これは SQL_FETCH_NEXT から分離します。  
  
 SQL_CA1_BOOKMARK A を = *FetchOrientation* SQL_FETCH_BOOKMARK の引数がへの呼び出しでサポートされている**SQLFetchScroll**カーソルが動的カーソルの場合。  
  
 SQL_CA1_LOCK_EXCLUSIVE A を = *LockType* SQL_LOCK_EXCLUSIVE の引数がへの呼び出しでサポートされている**SQLSetPos**カーソルが動的カーソルの場合。  
  
 Sql_ca1_lock_no_change、A を = *LockType* SQL_LOCK_NO_CHANGE の引数がへの呼び出しでサポートされている**SQLSetPos**カーソルが動的カーソルの場合。  
  
 SQL_CA1_LOCK_UNLOCK A を = *LockType* SQL_LOCK_UNLOCK の引数がへの呼び出しでサポートされている**SQLSetPos**カーソルが動的カーソルの場合。  
  
 SQL_CA1_POS_POSITION =、*操作*SQL_POSITION の引数がへの呼び出しでサポートされている**SQLSetPos**カーソルが動的カーソルの場合。  
  
 SQL_CA1_POS_UPDATE =、*操作*SQL_UPDATE の引数がへの呼び出しでサポートされている**SQLSetPos**カーソルが動的カーソルの場合。  
  
 SQL_CA1_POS_DELETE =、*操作*SQL_DELETE の引数がへの呼び出しでサポートされている**SQLSetPos**カーソルが動的カーソルの場合。  
  
 Sql_ca1_pos_refresh、=、*操作*SQL_REFRESH の引数がへの呼び出しでサポートされている**SQLSetPos**カーソルが動的カーソルの場合。  
  
 Sql_ca1_positioned_update、=、更新プログラムが現在の SQL ステートメントは、カーソルが動的カーソルの場合はサポートします。 (SQL 92 エントリのレベル – 準拠ドライバー常にサポートが返されます、このオプションです。)  
  
 SQL_CA1_POSITIONED_DELETE = 削除、現在の SQL ステートメントは、カーソルが動的カーソルをサポートします。 (SQL 92 エントリのレベル – 準拠ドライバー常にサポートが返されます、このオプションです。)  
  
 SQL_CA1_SELECT_FOR_UPDATE SELECT = カーソルが動的カーソルの場合、UPDATE SQL ステートメントはサポートされています。 (SQL 92 エントリのレベル – 準拠ドライバー常にサポートが返されます、このオプションです。)  
  
 Sql_ca1_bulk_add、=、*操作*SQL_ADD の引数がへの呼び出しでサポートされている**SQLBulkOperations**カーソルが動的カーソルの場合。  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK =、*操作*SQL_UPDATE_BY_BOOKMARK の引数がへの呼び出しでサポートされている**SQLBulkOperations**カーソルが動的カーソルの場合。  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK =、*操作*SQL_DELETE_BY_BOOKMARK の引数がへの呼び出しでサポートされている**SQLBulkOperations**カーソルが動的カーソルの場合。  
  
 Sql_ca1_bulk_fetch_by_bookmark、=、*操作*SQL_FETCH_BY_BOOKMARK の引数がへの呼び出しでサポートされている**SQLBulkOperations**カーソルが動的カーソルの場合。  
  
 SQL 92 中級者向けのレベル – 準拠するドライバー通常サポートが返されます、SQL_CA1_NEXT、SQL_CA1_ABSOLUTE、および SQL_CA1_RELATIVE オプション、埋め込みの SQL の FETCH ステートメントを通じてスクロール可能なカーソルをサポートするためです。 これは直接を決定できなかったため、基になる SQL サポート、ただし、スクロール可能なカーソルがサポートされていない、SQL 92 中級者向けのレベル – 準拠するドライバーに対しても。  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 ドライバーでサポートされている、動的カーソルの属性を記述する SQLUINTEGER ビットマスクです。 このビットマスクには、属性の 2 つ目のサブセットが含まれています。最初のサブセット SQL_DYNAMIC_CURSOR_ATTRIBUTES1 を参照してください。  
  
 以下のビットマスクを使用して、どの属性がサポートされているを調べます。  
  
 SQL_CA2_READ_ONLY_CONCURRENCY = 読み取り専用で更新することはありません、動的カーソルはサポートされています。 (動的カーソル、SQL_ATTR_CONCURRENCY ステートメント属性では SQL_CONCUR_READ_ONLY を指定できます。)  
  
 SQL_CA2_LOCK_CONCURRENCY = 最下位レベルを使用する動的カーソルを確認するための十分なロックの行を更新することはサポートされています。 (動的カーソル、SQL_ATTR_CONCURRENCY ステートメント属性では SQL_CONCUR_LOCK を使用できます)。これらのロックは、SQL_ATTR_TXN_ISOLATION 接続属性で、トランザクション分離レベルと一致する必要があります。  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY、動的カーソルはオプティミスティック同時実行制御の比較する行のバージョンがサポートされていることを = です。 (動的カーソル、SQL_ATTR_CONCURRENCY ステートメント属性では SQL_CONCUR_ROWVER を使用できます)。  
  
 Sql_ca2_opt_values_concurrency、動的カーソルはオプティミスティック同時実行制御の比較値がサポートされていることを = です。 (動的カーソル、SQL_ATTR_CONCURRENCY ステートメント属性では SQL_CONCUR_VALUES を使用できます)。  
  
 SQL_CA2_SENSITIVITY_ADDITIONS = 追加された行がカーソルは動的カーソルに表示されます。これらの行にカーソルがスクロールできます。 (これらの行がカーソルに追加されます、ドライバーによって異なります。)  
  
 SQL_CA2_SENSITIVITY_DELETIONS = 削除された行は動的カーソルに利用できなくと、結果セット内の「穴」のままにしないでください動的カーソルはスクロール削除された行から後、は、その行を返すことはできません。  
  
 SQL_CA2_SENSITIVITY_UPDATES = 行の更新がカーソルは動的カーソルに表示されます。動的カーソルからまでスクロールし、更新された行を返します、カーソルによって返されるデータが元のデータではなく、更新されたデータ。  
  
 SQL_CA2_MAX_ROWS_SELECT、SQL_ATTR_MAX_ROWS ステートメント属性に影響を =**選択**カーソルは動的カーソル ステートメント。  
  
 SQL_CA2_MAX_ROWS_INSERT、SQL_ATTR_MAX_ROWS ステートメント属性に影響を =**挿入**カーソルは動的カーソル ステートメント。  
  
 SQL_CA2_MAX_ROWS_DELETE、SQL_ATTR_MAX_ROWS ステートメント属性に影響を =**削除**カーソルは動的カーソル ステートメント。  
  
 SQL_CA2_MAX_ROWS_UPDATE、SQL_ATTR_MAX_ROWS ステートメント属性に影響を =**更新**カーソルは動的カーソル ステートメント。  
  
 SQL_CA2_MAX_ROWS_CATALOG、SQL_ATTR_MAX_ROWS ステートメント属性に影響を =**カタログ**カーソルが動的カーソルの場合、結果セットです。  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL、SQL_ATTR_MAX_ROWS ステートメント属性に影響を =**選択**、**挿入**、**削除**、および**更新**ステートメント、および**カタログ**カーソルが動的カーソルの場合、結果セットです。  
  
 SQL_CA2_CRC_EXACT、正確な = 行の数が使用可能な SQL_DIAG_CURSOR_ROW_COUNT 診断フィールドにカーソルが動的カーソルであるときです。  
  
 SQL_CA2_CRC_APPROXIMATE 概算値 = 行の数が使用可能な SQL_DIAG_CURSOR_ROW_COUNT 診断フィールドにカーソルが動的カーソルであるときです。  
  
 SQL_CA2_SIMULATE_NON_UNIQUE ドライバーを = がシミュレートされるという保証されません更新または位置指定 delete ステートメントがカーソルは動的カーソル; とに 1 行のみに影響これを保証するために、アプリケーションの責任です。 (ステートメントが複数の行に影響する場合**SQLExecute**または**SQLExecDirect** SQLSTATE 01001 [カーソル操作の競合] が返されます)。この動作では、アプリケーションの呼び出しを設定する**SQLSetStmtAttr** SQL_ATTR_SIMULATE_CURSOR で属性 SQL_SC_NON_UNIQUE に設定します。  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE シミュレーションの位置指定更新または削除ステートメントに影響すること 1 行のみ、カーソルが動的カーソルを保証するためにドライバーの試行を = です。 ドライバーはこのようなステートメントを常に実行する場合など、複数の行に影響を与える可能性がある場合でも一意のキーはありません。 (ステートメントが複数の行に影響する場合**SQLExecute**または**SQLExecDirect** SQLSTATE 01001 [カーソル操作の競合] が返されます)。この動作では、アプリケーションの呼び出しを設定する**SQLSetStmtAttr** SQL_ATTR_SIMULATE_CURSOR で属性 SQL_SC_TRY_UNIQUE に設定します。  
  
 SQL_CA2_SIMULATE_UNIQUE = ドライバーをシミュレートすることが保証には、更新プログラムが配置されている、または delete ステートメントがカーソルは動的カーソルとに 1 行のみに影響します。 ドライバーは特定のステートメントでは、これを保証できない場合**SQLExecDirect**または**SQLPrepare** SQLSTATE 01001 (カーソル操作 conflict) を返します。 この動作では、アプリケーションの呼び出しを設定する**SQLSetStmtAttr** SQL_ATTR_SIMULATE_CURSOR で属性 SQL_SC_UNIQUE に設定します。  
  
 SQL_EXPRESSIONS_IN_ORDERBY (ODBC 1.0)  
 文字の文字列:"Y"データ ソース内の式をサポートしている場合、 **ORDER BY**ボックスの一覧です。"N"存在しない場合。  
  
 SQL_FILE_USAGE (ODBC 2.0)  
 1 階層のドライバーが直接データ ソース内のファイルを処理方法を示す SQLUSMALLINT 値:  
  
 SQL_FILE_NOT_SUPPORTED =、ドライバーは、1 階層ドライバーではありません。 たとえば、ORACLE ドライバは、2 層ドライバーです。  
  
 SQL_FILE_TABLE データ ソースのテーブルとして 1 階層のドライバーの扱いのファイルを = です。 たとえば、Xbase ドライバーでは、各 Xbase ファイルがテーブルとして扱われます。  
  
 SQL_FILE_CATALOG カタログとしてデータ ソース内の 1 階層ドライバー扱うファイルを = です。 たとえば、Microsoft Access ドライバーでは、Microsoft Access の各ファイルが完全なデータベースとして扱われます。  
  
 アプリケーションは、ユーザーがデータを選択する方法を決定するのにこれを使用できます。 たとえば、Xbase ユーザー多くの場合、データと見なすファイルに格納されている ORACLE および Microsoft Access のユーザーと考えることデータのテーブルに格納されている一方です。  
  
 ユーザー Xbase データ ソースを選択すると、アプリケーションが、Windows を表示でした**ファイルを開く**コモン ダイアログ ボックス以外の場合は、ユーザーが Microsoft Access や ORACLE のデータ ソースを選択すると、アプリケーションは、カスタム表示でした**テーブルを選択して** ダイアログ ボックス。  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 ドライバーでサポートされている、順方向専用カーソルの属性を記述する SQLUINTEGER ビットマスクです。 このビットマスクには、属性の最初のサブセットが含まれています。2 番目のサブセット SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2 を参照してください。  
  
 以下のビットマスクを使用して、どの属性がサポートされているを調べます。  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 これらのビットマスクの説明については、SQL_DYNAMIC_CURSOR_ATTRIBUTES1 を参照してください (および"順方向専用カーソル"の説明に示される「動的カーソル」を置き換えます)。  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 ドライバーでサポートされている、順方向専用カーソルの属性を記述する SQLUINTEGER ビットマスクです。 このビットマスクには、属性の 2 つ目のサブセットが含まれています。最初のサブセット SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1 を参照してください。  
  
 以下のビットマスクを使用して、どの属性がサポートされているを調べます。  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 これらのビットマスクの説明については、SQL_DYNAMIC_CURSOR_ATTRIBUTES2 を参照してください (および"順方向専用カーソル"の説明に示される「動的カーソル」を置き換えます)。  
  
 SQL_GETDATA_EXTENSIONS (ODBC 2.0)  
 拡張機能を列挙する SQLUINTEGER ビットマスク**SQLGetData**です。  
  
 以下のビットマスクを使用して、フラグと共に判断のドライバーをサポートしているどのような一般的な拡張子**SQLGetData**:  
  
 SQL_GD_ANY_COLUMN = **SQLGetData**最後の列をバインドする前に含めて、任意のバインドされていない列を呼び出すことができます。 SQL_GD_ANY_ORDER も返されない限り、列番号を昇順の順序で列を呼び出す必要がありますに注意してください。  
  
 SQL_GD_ANY_ORDER = **SQLGetData**任意の順序でバインドされていない列を呼び出すことができます。 なお**SQLGetData** SQL_GD_ANY_COLUMN も返されない限り、最後の列がバインドされた後に、列に対してのみ呼び出すことができます。  
  
 SQL_GD_BLOCK = **SQLGetData**を持つには、その行に配置した後、(行セットのサイズが 1 より大きい) のデータ ブロックの任意の行に非バインド列に対して呼び出すことが**SQLSetPos**です。  
  
 SQL_GD_BOUND = **SQLGetData**連結された列の非バインド列だけでなく呼び出すことができます。 ドライバーは、SQL_GD_ANY_COLUMN も返しますしない限り、この値を返すことができません。  
  
 SQL_GD_OUTPUT_PARAMS = **SQLGetData**出力パラメーターの値を返すを呼び出すことができます。 詳細については、次を参照してください。 [SQLGetData を使用して出力パラメーターを取得する](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)です。  
  
 **SQLGetData**は最後の列にバインドされた後に発生する非バインド列からのみデータを列数を増やすことの順序で呼び出されます、中でない行のブロック内の行を返すときに必要です。  
  
 呼び出しをサポートする必要があります、ドライバーは、ブックマーク (固定長または可変長のいずれか) をサポートする場合**SQLGetData**列 0 にします。 このサポートはドライバーを返しますを呼び出すのために関係なく必要な**SQLGetInfo** 、SQL_GETDATA_EXTENSIONS で*情報の種類*です。  
  
 SQL_GROUP_BY (ODBC 2.0)  
 内の列間のリレーションシップを示す SQLUSMALLINT 値、 **GROUP BY**句と select リストで非集計列。  
  
 SQL_GB_COLLATE A を = **COLLATE**句をグループ化の各列の末尾に指定できます。 (ODBC 3.0)  
  
 SQL_GB_NOT_SUPPORTED = **GROUP BY**句はサポートされていません。 (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT =、 **GROUP BY**句は、選択リスト内のすべての非集計列を含める必要があります。 その他の列は使用できません。 たとえば、**部門、MAX(SALARY) から EMPLOYEE グループの選択で DEPT**です。 (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT =、 **GROUP BY**句は、選択リスト内のすべての非集計列を含める必要があります。 選択リストに含まれていない列を格納できます。 たとえば、 **BY 部署の部門、MAX(SALARY) から EMPLOYEE グループの選択、変更禁止期間**です。 (ODBC 2.0)  
  
 SQL_GB_NO_RELATION = 内の列、 **GROUP BY**句と select リストは関連しません。 選択リストに nongrouped、非集計列の意味は、データ ソースに依存します。 たとえば、 **、期間、部署、給与の従業員グループの選択で DEPT**です。 (ODBC 2.0)  
  
 SQL 92 エントリのレベル – 準拠ドライバーでは、サポートされている、SQL_GB_GROUP_BY_EQUALS_SELECT オプションは常に返します。 SQL 92 フルのレベル – 準拠ドライバーでは、サポートされている、SQL_GB_COLLATE オプションは常に返します。 いずれのオプションはサポートされている場合、 **GROUP BY**句は、データ ソースによってサポートされていません。  
  
 SQL_IDENTIFIER_CASE (ODBC 1.0)  
 SQLUSMALLINT 値次のとおりです。  
  
 SQL_IC_UPPER = SQL の識別子が小文字は区別されませんに格納されている場合は、システム カタログに大文字です。  
  
 SQL_IC_LOWER = SQL の識別子の大文字小文字が区別されない、システム カタログ内の小文字で格納されます。  
  
 SQL_IC_SENSITIVE = SQL の識別子の大文字と小文字は、システム カタログ内の大文字小文字混在で格納します。  
  
 SQL_IC_MIXED = SQL の識別子が小文字は区別されず、、システム カタログ内の大文字小文字混在で格納します。  
  
 Sql-92 で識別子が大文字小文字が区別されないため (すべてのレベル)、sql-92 に厳密に準拠したドライバーを返さない SQL_IC_SENSITIVE オプション サポートされています。  
  
 SQL_IDENTIFIER_QUOTE_CHAR (ODBC 1.0)  
 引用符で囲まれたの開始と終了区切り記号として使用する文字の文字列 (区切り) SQL ステートメント内の識別子。 (ODBC 関数を引数として渡された識別子はありません引用符で囲む。)データ ソースが引用符で囲まれた識別子をサポートしていない場合は空白が返されます。  
  
 この文字の文字列は、接続属性 SQL_ATTR_METADATA_ID が SQL_TRUE に設定されているときに、カタログ関数の引数を引用符で囲むためにも使用できます。  
  
 SQL 92 識別子引用符文字は、二重引用符 (") であるため、準拠しているドライバー厳密に sql-92 には常に返します二重引用符文字。  
  
 SQL_INDEX_KEYWORDS (ODBC 3.0)  
 ドライバーでサポートされている、CREATE INDEX ステートメントでキーワードを列挙する SQLUINTEGER ビットマスク。  
  
 SQL_IK_NONE = None キーワードはサポートされています。  
  
 SQL_IK_ASC = ASC キーワードはサポートされています。  
  
 SQL_IK_DESC = DESC キーワードはサポートされています。  
  
 SQL_IK_ALL = All キーワードがサポートされています。  
  
 CREATE INDEX ステートメントがサポートされているかどうかを表示するには、アプリケーションが呼び出す**SQLGetInfo** SQL_DLL_INDEX 情報の種類とします。  
  
 SQL_INFO_SCHEMA_VIEWS (ODBC 3.0)  
 ドライバーでサポートされている、INFORMATION_SCHEMA ビューを列挙する SQLUINTEGER ビットマスクです。 では、ビューの内容 INFORMATION_SCHEMA は、sql-92 で定義されています。  
  
 この機能をサポートする必要があります、sql-92 または FIPS 準拠のレベルが各ビットマスクの横にあるかっこ内に表示されます。  
  
 以下のビットマスクを使用して、どのビューはサポートされてを調べます。  
  
 SQL_ISV_ASSERTIONS = 特定のユーザーによって所有されているカタログのアサーションを識別します。 (完全レベル)  
  
 SQL_ISV_CHARACTER_SETS = 特定のユーザーによってアクセスできるカタログの文字セットを識別します。 (中間レベル)  
  
 SQL_ISV_CHECK_CONSTRAINTS = の識別、チェック制約は、特定のユーザーによって所有されています。 (中間レベル)  
  
 SQL_ISV_COLLATIONS = 特定のユーザーによってアクセスできるカタログの文字の照合順序を識別します。 (完全レベル)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE = カタログで定義されているドメインに依存し、特定のユーザーによって所有されているカタログの列を識別します。 (中間レベル)  
  
 SQL_ISV_COLUMN_PRIVILEGES = が使用または付与特定のユーザーによって永続的なテーブルの列に対する権限を識別します。 (FIPS 過渡期レベル)  
  
 SQL_ISV_COLUMNS = 特定のユーザーによってアクセスできる永続的なテーブルの列を識別します。 (FIPS 過渡期レベル)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE と同様の = CONSTRAINT_TABLE_USAGE ビューに列が特定のユーザーによって所有されているさまざまな制約を識別します。 (中間レベル)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE = 制約によって使用されているテーブルを識別 (参照、一意でとアサーション)、および特定のユーザーによって所有されます。 (中間レベル)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS = 特定のユーザーによってアクセスできます (カタログ内のドメイン) のドメインの制約を識別します。 (中間レベル)  
  
 SQL_ISV_DOMAINS = ユーザーがアクセスできるカタログで定義されているドメインを識別します。 (中間レベル)  
  
 SQL_ISV_KEY_COLUMN_USAGE キーとして特定のユーザーによって制限されているように、カタログで定義されている識別列を = です。 (中間レベル)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS = 特定のユーザーによって所有されている参照に関する制約を識別します。 (中間レベル)  
  
 SQL_ISV_SCHEMATA = 特定のユーザーによって所有されているスキーマを識別します。 (中間レベル)  
  
 SQL_ISV_SQL_LANGUAGES = SQL 実装によってサポートされる SQL への準拠レベル、オプション、および言語を識別します。 (中間レベル)  
  
 SQL_ISV_TABLE_CONSTRAINTS = は、特定のユーザーによって所有されているテーブル制約を識別します。 (中間レベル)  
  
 SQL_ISV_TABLE_PRIVILEGES = 永続的な使用可能なテーブルまたは付与して、特定のユーザーに権限を識別します。 (FIPS 過渡期レベル)  
  
 SQL_ISV_TABLES = 特定のユーザーによってアクセスできるカタログで定義されている永続的なテーブルを識別します。 (FIPS 過渡期レベル)  
  
 SQL_ISV_TRANSLATIONS = 特定のユーザーによってアクセスできるカタログの文字変換を識別します。 (完全レベル)  
  
 SQL_ISV_USAGE_PRIVILEGES = が利用できるまたは特定のユーザーによって所有されているカタログ オブジェクトへの権限の使用状況を識別します。 (FIPS 過渡期レベル)  
  
 SQL_ISV_VIEW_COLUMN_USAGE = 特定のユーザーによって所有されているカタログのビュー列を識別が依存しています。 (中間レベル)  
  
 SQL_ISV_VIEW_TABLE_USAGE = 特定のユーザーによって所有されているカタログのビューのテーブルを識別が依存しています。 (中間レベル)  
  
 SQL_ISV_VIEWS = 特定のユーザーによってアクセスできるこのカタログで定義されている、表示済みテーブルを識別します。 (FIPS 過渡期レベル)  
  
 SQL_INSERT_STATEMENT (ODBC 3.0)  
 サポートを示す SQLUINTEGER ビットマスク**挿入**ステートメント。  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 SQL 92 エントリのレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。  
  
 SQL_INTEGRITY (ODBC 1.0)  
 文字の文字列:"Y"データ ソースが Integrity Enhancement Facility; をサポートしている場合"N"存在しない場合。  
  
 これは、*情報の種類*名前が変更された ODBC 2.0 から 3.0 の ODBC*情報の種類*SQL_ODBC_SQL_OPT_IEF です。  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 ドライバーでサポートされている、キーセット カーソルの属性を記述する SQLUINTEGER ビットマスクです。 このビットマスクには、属性の最初のサブセットが含まれています。2 番目のサブセット SQL_KEYSET_CURSOR_ATTRIBUTES2 を参照してください。  
  
 以下のビットマスクを使用して、どの属性がサポートされているを調べます。  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 これらのビットマスクの説明については、SQL_DYNAMIC_CURSOR_ATTRIBUTES1 を参照してください (および"キーセット ドリブン カーソル"の説明に示される「動的カーソル」を置き換えます)。  
  
 SQL 92 中級者向けの準拠レベル ドライバー通常サポートが返されます、SQL_CA1_NEXT、SQL_CA1_ABSOLUTE、および SQL_CA1_RELATIVE オプション、ドライバーが埋め込み SQL FETCH ステートメントを通じてスクロール可能なカーソルをサポートしているためです。 これは直接を決定できなかったため、基になる SQL サポート、ただし、スクロール可能なカーソルがサポートされていない、SQL 92 中級者向けのレベル – 準拠するドライバーに対しても。  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 ドライバーでサポートされている、キーセット カーソルの属性を記述する SQLUINTEGER ビットマスクです。 このビットマスクには、属性の 2 つ目のサブセットが含まれています。最初のサブセット SQL_KEYSET_CURSOR_ATTRIBUTES1 を参照してください。  
  
 以下のビットマスクを使用して、どの属性がサポートされているを調べます。  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 これらのビットマスクの説明については、SQL_DYNAMIC_CURSOR_ATTRIBUTES1 を参照してください (および"キーセット ドリブン カーソル"の説明に示される「動的カーソル」を置き換えます)。  
  
 SQL_KEYWORDS (ODBC 2.0)  
 すべてのデータ ソース固有のキーワードのコンマ区切りの一覧を含む文字列。 この一覧には、ODBC に固有のキーワードまたはデータ ソースと ODBC の両方で使用されるキーワードがありません。 この一覧は、すべての予約済みキーワードを表します相互運用可能アプリケーションは、オブジェクト名でこれらの単語を使用しないようにします。  
  
 ODBC キーワードの一覧は、次を参照してください。[予約済みキーワード](../../../odbc/reference/appendixes/reserved-keywords.md)で[付録 c: SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)です。 **#Define**値 SQL_ODBC_KEYWORDS ODBC キーワードのコンマ区切りの一覧が含まれています。  
  
 付録 c: SQL の文法  
  
 SQL_LIKE_ESCAPE_CLAUSE (ODBC 2.0)  
 文字の文字列:"Y"データ ソースは、パーセント (%) の文字のエスケープ文字をサポートしている場合、およびアンダー スコア文字 (_)、**と同様に**述語ドライバーでサポートされると、ODBC 構文を定義するため、 **など**述語エスケープ文字です。"N"それ以外の場合。  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS (ODBC 3.0)  
 ドライバーでは、特定の接続をサポートする非同期モードでアクティブな同時実行ステートメントの最大数を指定する SQLUINTEGER 値です。 特定の制限がないか、上限が不明な場合、この値は 0 を使用します。  
  
 SQL_MAX_BINARY_LITERAL_LEN (ODBC 2.0)  
 最大長を指定する SQLUINTEGER 値 (リテラル プレフィックスおよびサフィックスによって返される除外、16 進数の文字数**SQLGetTypeInfo**) の SQL ステートメント内のバイナリ リテラルです。 たとえば、バイナリ リテラル 0xFFAA が 4 の長さ。 最大長がないか、長さが不明場合、この値は 0 に設定します。  
  
 SQL_MAX_CATALOG_NAME_LEN (ODBC 1.0)  
 データ ソースのカタログ名の最大長を指定する SQLUSMALLINT 値です。 最大長がないか、長さが不明場合、この値は 0 に設定します。  
  
 FIPS 全体のレベル – 準拠ドライバーでは、少なくとも 128 を返します。  
  
 これは、*情報の種類*名前が変更された ODBC 2.0 から 3.0 の ODBC*情報の種類*SQL_MAX_QUALIFIER_NAME_LEN です。  
  
 SQL_MAX_CHAR_LITERAL_LEN (ODBC 2.0)  
 最大長を指定する SQLUINTEGER 値 (文字、リテラル プレフィックスおよびサフィックスによって返される除外の番号**SQLGetTypeInfo**) の SQL ステートメント内の文字リテラル。 最大長がないか、長さが不明場合、この値は 0 に設定します。  
  
 SQL_MAX_COLUMN_NAME_LEN (ODBC 1.0)  
 データ ソースの列名の最大長を指定する SQLUSMALLINT 値です。 最大長がないか、長さが不明場合、この値は 0 に設定します。  
  
 FIPS エントリのレベル – 準拠ドライバーでは、少なくとも 18 を返します。 FIPS 中級者向けの準拠レベル ドライバーでは、少なくとも 128 を返します。  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY (ODBC 2.0)  
 許可されている列の最大数を指定する SQLUSMALLINT 値、 **GROUP BY**句。 指定された制限がないか、上限が不明な場合、この値は 0 に設定します。  
  
 FIPS エントリのレベル – 準拠するドライバーは、少なくとも 6 を返します。 FIPS 中級者向けの準拠レベル ドライバーでは、少なくとも 15 を返します。  
  
 SQL_MAX_COLUMNS_IN_INDEX (ODBC 2.0)  
 インデックスで許可されている列の最大数を示す SQLUSMALLINT 値。 指定された制限がないか、上限が不明な場合、この値は 0 に設定します。  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY (ODBC 2.0)  
 許可されている列の最大数を指定する SQLUSMALLINT 値、 **ORDER BY**句。 指定された制限がないか、上限が不明な場合、この値は 0 に設定します。  
  
 FIPS エントリのレベル – 準拠するドライバーは、少なくとも 6 を返します。 FIPS 中級者向けの準拠レベル ドライバーでは、少なくとも 15 を返します。  
  
 SQL_MAX_COLUMNS_IN_SELECT (ODBC 2.0)  
 選択リストで許可されている列の最大数を示す SQLUSMALLINT 値。 指定された制限がないか、上限が不明な場合、この値は 0 に設定します。  
  
 FIPS エントリのレベル – 準拠ドライバーでは、少なくとも 100 を返します。 FIPS 中級者向けの準拠レベル ドライバーでは、少なくとも 250 を返します。  
  
 SQL_MAX_COLUMNS_IN_TABLE (ODBC 2.0)  
 テーブルで許可されている列の最大数を示す SQLUSMALLINT 値。 指定された制限がないか、上限が不明な場合、この値は 0 に設定します。  
  
 FIPS エントリのレベル – 準拠ドライバーでは、少なくとも 100 を返します。 FIPS 中級者向けの準拠レベル ドライバーでは、少なくとも 250 を返します。  
  
 SQL_MAX_CONCURRENT_ACTIVITIES (ODBC 1.0)  
 ドライバーが接続をサポートできるアクティブなステートメントの最大数を指定する SQLUSMALLINT 値です。 用語「結果」意味行と、保留中の結果がある場合に、アクティブとしてステートメントが定義されている、**選択**操作または影響を受ける行、**挿入**、**更新**、または**削除**操作 (など、行の数)、または NEED_DATA 状態にある場合。 この値は、ドライバーまたはデータ ソースのいずれかでの制限事項を反映できます。 指定された制限がないか、上限が不明な場合、この値は 0 に設定します。  
  
 これは、*情報の種類*名前が変更された ODBC 2.0 から 3.0 の ODBC*情報の種類*SQL_ACTIVE_STATEMENTS です。  
  
 SQL_MAX_CURSOR_NAME_LEN (ODBC 1.0)  
 データ ソースでカーソル名の最大長を示す SQLUSMALLINT 値。 最大長がないか、長さが不明場合、この値は 0 に設定します。  
  
 FIPS エントリのレベル – 準拠ドライバーでは、少なくとも 18 を返します。 FIPS 中級者向けの準拠レベル ドライバーでは、少なくとも 128 を返します。  
  
 SQL_MAX_DRIVER_CONNECTIONS (ODBC 1.0)  
 環境のドライバーをサポートできるアクティブな接続の最大数を指定する SQLUSMALLINT 値です。 この値は、ドライバーまたはデータ ソースのいずれかでの制限事項を反映できます。 指定された制限がないか、上限が不明な場合、この値は 0 に設定します。  
  
 これは、*情報の種類*名前が変更された ODBC 2.0 から 3.0 の ODBC*情報の種類*SQL_ACTIVE_CONNECTIONS です。  
  
 SQL_MAX_IDENTIFIER_LEN (ODBC 3.0)  
 ユーザー定義の名前のデータ ソースをサポートする文字の最大サイズを示す SQLUSMALLINT です。  
  
 FIPS エントリのレベル – 準拠ドライバーでは、少なくとも 18 を返します。 FIPS 中級者向けの準拠レベル ドライバーでは、少なくとも 128 を返します。  
  
 SQL_MAX_INDEX_SIZE (ODBC 2.0)  
 インデックスの結合されたフィールドに許可されるバイトの最大数を指定する SQLUINTEGER 値です。 指定された制限がないか、上限が不明な場合、この値は 0 に設定します。  
  
 SQL_MAX_PROCEDURE_NAME_LEN (ODBC 1.0)  
 データ ソースでプロシージャ名の最大長を示す SQLUSMALLINT 値。 最大長がないか、長さが不明場合、この値は 0 に設定します。  
  
 SQL_MAX_ROW_SIZE (ODBC 2.0)  
 テーブルの 1 つの行の最大長を指定する SQLUINTEGER 値です。 指定された制限がないか、上限が不明な場合、この値は 0 に設定します。  
  
 FIPS エントリのレベル – 準拠ドライバーでは、少なくとも 2,000 を返します。 FIPS 中級者向けの準拠レベル ドライバーでは、少なくとも、8,000 を返します。  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG (ODBC 3.0)  
 文字の文字列: SQL_MAX_ROW_SIZE 情報の種類には行にあるすべての SQL_LONGVARCHAR および SQL_LONGVARBINARY 列の長さが含まれています、最大行サイズが返される場合は"Y""N"それ以外の場合。  
  
 SQL_MAX_SCHEMA_NAME_LEN (ODBC 1.0)  
 データ ソースのスキーマ名の最大長を指定する SQLUSMALLINT 値です。 最大長がないか、長さが不明場合、この値は 0 に設定します。  
  
 FIPS エントリのレベル – 準拠ドライバーでは、少なくとも 18 を返します。 FIPS 中級者向けの準拠レベル ドライバーでは、少なくとも 128 を返します。  
  
 これは、*情報の種類*名前が変更された ODBC 2.0 から 3.0 の ODBC*情報の種類*SQL_MAX_OWNER_NAME_LEN です。  
  
 SQL_MAX_STATEMENT_LEN (ODBC 2.0)  
 SQL ステートメントの最大長 (文字などの空白文字数) を指定する SQLUINTEGER 値です。 最大長がないか、長さが不明場合、この値は 0 に設定します。  
  
 SQL_MAX_TABLE_NAME_LEN (ODBC 1.0)  
 データ ソースのテーブル名の最大長を指定する SQLUSMALLINT 値です。 最大長がないか、長さが不明場合、この値は 0 に設定します。  
  
 FIPS エントリのレベル – 準拠ドライバーでは、少なくとも 18 を返します。 FIPS 中級者向けの準拠レベル ドライバーでは、少なくとも 128 を返します。  
  
 SQL_MAX_TABLES_IN_SELECT (ODBC 2.0)  
 許容されるテーブルの最大数を指定する SQLUSMALLINT 値、 **FROM**の句、**選択**ステートメントです。 指定された制限がないか、上限が不明な場合、この値は 0 に設定します。  
  
 FIPS エントリのレベル – 準拠ドライバーでは、少なくとも 15 を返します。 FIPS 中級者向けの準拠レベル ドライバーでは、少なくとも 50 を返します。  
  
 SQL_MAX_USER_NAME_LEN (ODBC 2.0)  
 データ ソースのユーザー名の最大長を指定する SQLUSMALLINT 値です。 最大長がないか、長さが不明場合、この値は 0 に設定します。  
  
 SQL_MULT_RESULT_SETS (ODBC 1.0)  
 文字の文字列。 そうでない場合、データ ソースが複数の結果セットでは、"N"をサポートする場合は"Y"です。  
  
 複数の結果セットの詳細については、次を参照してください。[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)です。  
  
 SQL_MULTIPLE_ACTIVE_TXN (ODBC 1.0)  
 文字の文字列:"Y"、ドライバーは、いつでもにアクティブにできる 1 つのトランザクションだけの場合、同時に、"N"の 2 つ以上のアクティブなトランザクションをサポートしている場合。  
  
 この情報の種類に対して返される情報は、分散トランザクションの場合は適用されません。  
  
 SQL_NEED_LONG_DATA_LEN (ODBC 2.0)  
 文字の文字列。 そうでない場合は、"Y"データ ソースには、その値の前に長いデータ値 (データ型、SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長い形式のデータ ソース固有のデータ型) の長さが必要がある場合を"N"であるデータ ソースに送信します。 詳細については、次を参照してください。 [SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)と[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)です。  
  
 SQL_NON_NULLABLE_COLUMNS (ODBC 1.0)  
 データ ソースが列に NOT NULL をサポートするかどうかを指定する SQLUSMALLINT 値:  
  
 SQL_NNC_NULL = すべての列を null 許容にする必要があります。  
  
 SQL_NNC_NON_NULL = 列は null 値を許容することはできません。 (データ ソースのサポート、 **NOT NULL**内の列制約**CREATE TABLE**ステートメントです)。  
  
 SQL 92 エントリのレベル – 準拠ドライバーでは、SQL_NNC_NON_NULL を返します。  
  
 SQL_NULL_COLLATION (ODBC 2.0)  
 結果セット内の Null の配置場所を指定する SQLUSMALLINT 値:  
  
 SQL_NC_END = null 値は ASC または DESC キーワードに関係なく、結果セットの末尾に並べ替えられます。  
  
 SQL_NC_HIGH = null 値は、高 ASC または DESC キーワードに応じて、結果セットの最後に並べ替えられます。  
  
 SQL_NC_LOW = 低 ASC または DESC キーワードに応じて、結果セットの末尾に null 値を並べ替えます。  
  
 SQL_NC_START = ASC または DESC キーワードに関係なく、結果セットの開始時に null 値が並べ替えられます。  
  
 SQL_NUMERIC_FUNCTIONS (ODBC 1.0)  
 注: 情報の種類が ODBC 1.0; で導入されました。各ビットマスクには、導入されたバージョンが付いています。  
  
 ドライバーと関連付けられているデータ ソースでサポートされている数値のスカラー関数を列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを使用してがサポートする数値の関数を調べます。  
  
 SQL_FN_NUM_ABS (ODBC 1.0) SQL_FN_NUM_ACOS (ODBC 1.0) SQL_FN_NUM_ASIN (ODBC 1.0) SQL_FN_NUM_ATAN (ODBC 1.0) SQL_FN_NUM_ATAN2 (ODBC 1.0) SQL_FN_NUM_CEILING (ODBC 1.0) SQL_FN_NUM_COS (ODBC 1.0) SQL_FN_NUM_COT (ODBC 1.0) SQL_FN_NUM_DEGREES (ODBC 2.0) SQL _FN_NUM_EXP (ODBC 1.0) SQL_FN_NUM_FLOOR (ODBC 1.0) SQL_FN_NUM_LOG (ODBC 1.0) SQL_FN_NUM_LOG10 (ODBC 2.0) SQL_FN_NUM_MOD (ODBC 1.0) SQL_FN_NUM_PI (ODBC 1.0) SQL_FN_NUM_POWER (ODBC 2.0) SQL_FN_NUM_RADIANS (ODBC 2.0) SQL_FN_NUM_RAND (ODBC 1.0) SQL_FN_NUM_ROUND (ODBC 2.0) SQL_FN_NUM_SIGN (ODBC 1.0) SQL_FN_NUM_SIN (ODBC 1.0) (ODBC 1.0) SQL_FN_NUM_SQRT、SQL_FN_NUM_TAN (ODBC 1.0) SQL_FN_NUM_TRUNCATE (ODBC 2.0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE (ODBC 3.0)  
 ODBC 3 のレベルを示す SQLUINTEGER 値*.x*インターフェイスに準拠しているドライバーです。  
  
 SQL_OIC_CORE: に準拠するすべての ODBC ドライバーが最低限のレベルが必要です。 このレベルには、接続の機能、準備し、SQL ステートメントを実行するための関数、基本的な結果セットのメタデータ関数、基本的なカタログ関数などの基本インターフェイス要素が含まれます。  
  
 SQL_OIC_LEVEL1: 位置、コア標準準拠のレベルの機能と、カーソルがスクロール可能なブックマークを含むレベルを更新、削除し。  
  
 SQL_OIC_LEVEL2。 レベルはレベル 1 の標準準拠の機能レベル、plus 機密性の高いカーソル; などの高度な機能を含む、更新、削除、およびブックマーク; での更新ストアド プロシージャのサポート。カタログ関数の主キーと外部キーです。複数のカタログのサポート。などなど。  
  
 詳細については、次を参照してください。[インターフェイスへの準拠レベル](../../../odbc/reference/develop-app/interface-conformance-levels.md)です。  
  
 SQL_ODBC_VER (ODBC 1.0)  
 ODBC ドライバー マネージャーは、準拠しているのバージョンと文字の文字列。 バージョンの形式は、##. ##. 0000、ここで最初の 2 つの数字は、メジャー バージョンが、次の 2 桁マイナー バージョン。 これにより、ドライバー マネージャーでのみが実装されます。  
  
 SQL_OJ_CAPABILITIES (ODBC 2.01)  
 ドライバーとデータ ソースでサポートされている外部結合の種類を列挙する SQLUINTEGER ビットマスクです。 以下のビットマスクを使用して、どの型がサポートされているを調べます。  
  
 SQL_OJ_LEFT = 左外部結合はサポートされています。  
  
 SQL_OJ_RIGHT = 右外部結合はサポートされています。  
  
 SQL_OJ_FULL = Full outer 結合はサポートされています。  
  
 SQL_OJ_NESTED = 入れ子になった外部結合はサポートされています。  
  
 SQL_OJ_NOT_ORDERED = 列の外部結合の ON 句で名は、内のそれぞれのテーブル名と同じ順序にする必要はありません、**外部結合**句。  
  
 SQL_OJ_INNER = 内部テーブル (左外部結合の右側のテーブル) または右外部結合の左側のテーブルは、inner join でも使用できます。 これは、内部テーブルがないため、完全外部結合には適用されません。  
  
 SQL_OJ_ALL_COMPARISON_OPS、比較を = ON 句内の演算子には、ODBC の比較演算子のいずれかを指定できます。 このビットが設定されていない場合、外部結合で = (等号) 比較演算子のみを使用できます。  
  
 サポートされているこれらのオプションのいずれも返される場合は、外部結合句はサポートされません。  
  
 サポートについては、SELECT ステートメント内のリレーショナル結合演算子のように、sql-92 で定義されている、SQL_SQL92_RELATIONAL_JOIN_OPERATORS を参照してください。  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT (ODBC 2.0)  
 文字の文字列:"Y"場合内の列、 **ORDER BY**句が select リストである必要がありますそれ以外の場合、"N"です。  
  
 SQL_PARAM_ARRAY_ROW_COUNTS (ODBC 3.0)  
 パラメーター化された実行中の行の可用性に関する、ドライバーのプロパティの列挙、SQLUINTEGER をカウントします。 次の値があります。  
  
 SQL_PARC_BATCH 個人を = 行の数はパラメーターのセットごとに使用できます。 これは、各パラメーターの配列にセットのいずれかの SQL ステートメントのバッチを生成するドライバーと概念的に同じです。 拡張エラー情報は、SQL_PARAM_STATUS_PTR 記述子フィールドを使用して取得できます。  
  
 SQL_PARC_NO_BATCH = 1 つの行の数が、使用可能なパラメーターの配列全体のステートメントの実行結果として、累積的な行の数であります。 これは、完全なパラメーター配列と共にステートメントを 1 つのアトミック単位として扱う方法を概念的に同じものです。 1 つのステートメントが実行された場合に、エラーは、同じで処理されます。  
  
 SQL_PARAM_ARRAY_SELECTS (ODBC 3.0)  
 パラメーター化された実行の結果の可用性に関する、ドライバーのプロパティの列挙、SQLUINTEGER を設定します。 次の値があります。  
  
 SQL_PAS_BATCH = 1 つの結果がパラメーターのセットごとに使用可能なセットがあります。 これは、各パラメーターの配列にセットのいずれかの SQL ステートメントのバッチを生成するドライバーと概念的に同じです。  
  
 SQL_PAS_NO_BATCH = パラメーターの完全な配列のステートメントの実行結果として、累積的な結果を表す 1 つだけの結果、使用可能なセットのセットが存在します。 これは、完全なパラメーター配列と共にステートメントを 1 つのアトミック単位として扱う方法を概念的に同じものです。  
  
 SQL_PAS_NO_SELECT A を = ドライバーには、パラメーターの配列で実行される結果セットを生成するステートメントはできません。  
  
 SQL_PROCEDURE_TERM (ODBC 1.0)  
 プロシージャのデータ ソースの仕入先の名前を持つ文字の文字列たとえば、「データベース プロシージャ」、「ストアド プロシージャ」、「プロシージャ」、"package"、または「ストアド クエリ」です。  
  
 SQL_PROCEDURES (ODBC 1.0)  
 文字の文字列:"Y"データ ソースには、プロシージャがサポートしているし、ドライバーは、ODBC のプロシージャの呼び出し構文をサポートしている場合"N"それ以外の場合。  
  
 SQL_POS_OPERATIONS (ODBC 2.0)  
 内の操作でサポートを列挙する SQLINTEGER ビットマスク**SQLSetPos**です。  
  
 以下のビットマスクを決定するオプションがサポートされているフラグと共に使用されます。  
  
 SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)  
  
 SQL_QUOTED_IDENTIFIER_CASE (ODBC 2.0)  
 SQLUSMALLINT 値次のとおりです。  
  
 SQL_IC_UPPER 引用符で囲まれた = SQL の識別子が小文字は区別されませんに格納されている場合は、システム カタログに大文字です。  
  
 SQL_IC_LOWER 引用符で囲まれた = SQL の識別子は、小文字は区別されず、システム カタログ内の小文字で格納されます。  
  
 SQL_IC_SENSITIVE 引用符で囲まれた = SQL の識別子の大文字と小文字は、システム カタログ内の大文字小文字混在で格納します。 (データベースでは SQL 92 – 準拠、引用符で囲まれた識別子は常に大文字小文字を区別) です。  
  
 SQL_IC_MIXED 引用符で囲まれた = SQL の識別子が小文字は区別されず、、システム カタログ内の大文字小文字混在で格納します。  
  
 SQL 92 エントリのレベル – 準拠ドライバーでは、SQL_IC_SENSITIVE は常に返します。  
  
 SQL_ROW_UPDATES (ODBC 1.0)  
 文字の文字列:"Y"場合は、キーセット ドリブン カーソルまたは混合カーソル行のバージョンを保持するか、すべての値が行をフェッチし、後に加えられた行をすべてのユーザーが、行が最後にフェッチした更新プログラムを検出できます。 (これのみに適用されませんを削除または挿入、更新プログラム)。ドライバーは、行の状態、SQL_ROW_UPDATED フラグを返すことができる場合に配列**SQLFetchScroll**と呼びます。 それ以外の場合、"N"です。  
  
 SQL_SCHEMA_TERM (ODBC 1.0)  
 スキーマのデータ ソースの仕入先の名前を持つ文字の文字列たとえば、「所有者」、"承認 ID"または"Schema"にします。  
  
 文字の文字列は、上部、下部、または混在のケースで返されます。  
  
 SQL 92 エントリのレベル – 準拠ドライバーでは、「スキーマ」は常に返します。  
  
 これは、*情報の種類*名前が変更された ODBC 2.0 から 3.0 の ODBC*情報の種類*SQL_OWNER_TERM です。  
  
 SQL_SCHEMA_USAGE (ODBC 2.0)  
 スキーマを使用することができますステートメントを列挙する SQLUINTEGER ビットマスク。  
  
 SQL_SU_DML_STATEMENTS = すべてのデータ操作言語ステートメントでスキーマがサポートされている:**選択**、**挿入**、**更新**、 **DELETE**、サポートされている場合**更新用に選択**更新を配置し、ステートメントを削除します。  
  
 SQL_SU_PROCEDURE_INVOCATION = ODBC プロシージャ呼び出しステートメントでスキーマがサポートされています。  
  
 SQL_SU_TABLE_DEFINITION = すべてのテーブル定義ステートメントでスキーマがサポートされている: **CREATE TABLE**、 **CREATE VIEW**、 **ALTER TABLE**、 **DROP TABLE**、および**ドロップ ビュー**です。  
  
 SQL_SU_INDEX_DEFINITION = すべてのインデックス定義ステートメントでスキーマがサポートされている: **CREATE INDEX**と**DROP INDEX**です。  
  
 SQL_SU_PRIVILEGE_DEFINITION = すべての特権定義ステートメントでスキーマがサポートされている: **GRANT**と**取り消す**です。  
  
 SQL 92 エントリのレベル – 準拠ドライバーでは、サポートされている、SQL_SU_DML_STATEMENTS、SQL_SU_TABLE_DEFINITION、および SQL_SU_PRIVILEGE_DEFINITION のオプションは常に返します。  
  
 これは、*情報の種類*名前が変更された ODBC 2.0 から 3.0 の ODBC*情報の種類*SQL_OWNER_USAGE です。  
  
 SQL_SCROLL_OPTIONS (ODBC 1.0)  
 注: 情報の種類が ODBC 1.0; で導入されました。各ビットマスクには、導入されたバージョンが付いています。  
  
 スクロール可能なカーソルのサポートされる scroll オプションを列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを使用して、どのオプションがサポートされているを調べます。  
  
 SQL_SO_FORWARD_ONLY カーソルだけスクロール フォワードを = です。 (ODBC 1.0)  
  
 SQL_SO_STATIC = データ結果セットが静的です。 (ODBC 2.0)  
  
 SQL_SO_KEYSET_DRIVEN = ドライバー保存し、結果セット内のすべての行のキーを使用します。 (ODBC 1.0)  
  
 SQL_SO_DYNAMIC、ドライバーが保持 (キーセットのサイズは、行セット サイズ)、行セット内のすべての行のキーを = です。 (ODBC 1.0)  
  
 SQL_SO_MIXED、キーセット カーソルとキーセットのサイズのすべての行が行セットのサイズよりも大きい値では、ドライバーが保持、キーを = です。 カーソル、キーセット内でキーセット ドリブン動的、キーセットの外側です。 (ODBC 1.0)  
  
 スクロール可能なカーソルについては、次を参照してください。[スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)です。  
  
 SQL_SEARCH_PATTERN_ESCAPE (ODBC 1.0)  
 ドライバーのサポートの検索パターンでは有効な文字としてパターン一致のあるメタ文字をアンダー スコア (_)、パーセント記号 (%) の使用を許可するエスケープ文字として指定する文字列を返します。 このエスケープ文字は、検索文字列をサポートするこれらのカタログ関数の引数にのみ適用されます。 この文字列が空の場合、ドライバーは、検索パターンのエスケープ文字をサポートしません。  
  
 この情報の種類が、エスケープ文字の一般的なサポートを示していませんので、**と同様に**述語、sql-92 含まないこの文字の文字列の要件です。  
  
 これは、*情報の種類*カタログ関数に限定されます。 検索パターン文字列にエスケープ文字の使用については、次を参照してください。[パターン値の引数](../../../odbc/reference/develop-app/pattern-value-arguments.md)です。  
  
 SQL_SERVER_NAME (ODBC 1.0)  
 文字の文字列の実際のデータ ソース固有サーバーの名前です。データ ソース名を使用する際に便利です。 **SQLConnect**、 **SQLDriverConnect**、および**SQLBrowseConnect**です。  
  
 SQL_SPECIAL_CHARACTERS (ODBC 2.0)  
 すべての特殊文字 (つまり、すべての文字 a ~ z、A ~ Z、0 ~ 9、およびアンダー スコア)、テーブル名、列名、またはデータ ソース上のインデックス名など、識別子名で使用できるを表す文字列。 たとえば、"#$^"です。 1 つ以上のこれらの文字が識別子が含まれる場合、識別子が区切られた識別子でなければなりません。  
  
 SQL_SQL_CONFORMANCE (ODBC 3.0)  
 Sql-92、ドライバーによってサポートのレベルを示す SQLUINTEGER 値:  
  
 SQL_SC_SQL92_ENTRY エントリ レベルの sql-92 準拠を = です。  
  
 SQL_SC_FIPS127_2_TRANSITIONAL FIPS 127-2 過渡期レベルの準拠を = です。  
  
 SQL_SC_SQL92_FULL = 完全レベル sql-92 に準拠していません。  
  
 SQL_SC_ SQL92_INTERMEDIATE 中間レベルの sql-92 準拠を = です。  
  
 SQL_SQL92_DATETIME_FUNCTIONS(ODBC 3.0)  
 Sql-92 で定義されている、ドライバーと関連付けられたデータ ソースによってサポートされている datetime スカラー関数を列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを使用してがサポートする日付時刻関数を調べます。  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE(ODBC 3.0)  
 内の外部キーのサポートされているルールの列挙 SQLUINTEGER ビットマスク、**削除**ステートメントでは、sql-92 で定義されています。  
  
 以下のビットマスクを使用して、どの句が、データ ソースによってサポートされてを調べます。  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 FIPS 過渡期のレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE(ODBC 3.0)  
 内の外部キーのサポートされているルールの列挙 SQLUINTEGER ビットマスク、**更新**ステートメントでは、sql-92 で定義されています。  
  
 以下のビットマスクを使用して、どの句が、データ ソースによってサポートされてを調べます。  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 SQL 92 全体のレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。  
  
 SQL_SQL92_GRANT(ODBC 3.0)  
 サポートされている句を列挙する SQLUINTEGER ビットマスク、 **GRANT**ステートメントでは、sql-92 で定義されています。  
  
 この機能をサポートする必要があります、sql-92 または FIPS 準拠のレベルが各ビットマスクの横にあるかっこ内に表示されます。  
  
 以下のビットマスクを使用して、どの句が、データ ソースによってサポートされてを調べます。  
  
 SQL_SG_DELETE_TABLE (Entry レベル) SQL_SG_INSERT_COLUMN (中間レベル) SQL_SG_INSERT_TABLE (Entry レベル) SQL_SG_REFERENCES_TABLE (Entry レベル) SQL_SG_REFERENCES_COLUMN (Entry レベル) SQL_SG_SELECT_TABLE (Entry レベル) SQL_SG_UPDATE_COLUMN (Entry レベル) SQL_SG_UPDATE_TABLE (Entry レベル) SQL_SG_USAGE_ON_DOMAIN (FIPS 過渡期レベル) SQL_SG_USAGE_ON_CHARACTER_SET (FIPS 過渡期レベル) SQL_SG_USAGE_ON_COLLATION (FIPS 過渡期レベル) SQL_SG_USAGE_ON_TRANSLATION 規格 (FIPS:移行中レベル) SQL_SG_WITH_GRANT_OPTION (Entry レベル)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS(ODBC 3.0)  
 Sql-92 で定義されているドライバーと関連付けられたデータ ソースでサポートされている数値の値のスカラー関数を列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを使用してがサポートする数値の関数を調べます。  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES(ODBC 3.0)  
 サポートされる述語を列挙する SQLUINTEGER ビットマスク、**選択**ステートメントでは、sql-92 で定義されています。  
  
 この機能をサポートする必要があります、sql-92 または FIPS 準拠のレベルが各ビットマスクの横にあるかっこ内に表示されます。  
  
 以下のビットマスクを使用して、どのオプションは、データ ソースでサポートを調べます。  
  
 SQL_SP_BETWEEN (Entry レベル) SQL_SP_COMPARISON (Entry レベル) SQL_SP_EXISTS (Entry レベル) SQL_SP_IN (Entry レベル) SQL_SP_ISNOTNULL (Entry レベル) SQL_SP_ISNULL (Entry レベル) SQL_SP_LIKE (Entry レベル) SQL_SP_MATCH_FULL (完全レベル) SQL_SP_MATCH_PARTIAL(完全レベル)SQL_SP_MATCH_UNIQUE_FULL (完全レベル) SQL_SP_MATCH_UNIQUE_PARTIAL (完全レベル) SQL_SP_OVERLAPS (FIPS 過渡期レベル) SQL_SP_QUANTIFIED_COMPARISON (Entry レベル)、SQL_SP_UNIQUE (Entry レベル)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS(ODBC 3.0)  
 サポートされているリレーショナル結合演算子を列挙する SQLUINTEGER ビットマスク、**選択**ステートメントでは、sql-92 で定義されています。  
  
 この機能をサポートする必要があります、sql-92 または FIPS 準拠のレベルが各ビットマスクの横にあるかっこ内に表示されます。  
  
 以下のビットマスクを使用して、どのオプションは、データ ソースでサポートを調べます。  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (中間レベル) SQL_SRJO_CROSS_JOIN (完全レベル) SQL_SRJO_EXCEPT_JOIN (中間レベル) SQL_SRJO_FULL_OUTER_JOIN (中間レベル) (FIPS 過渡期レベル) sql_srjo_inner_join、SQL_SRJO_INTERSECT_JOIN(中間レベル)SQL_SRJO_LEFT_OUTER_JOIN (FIPS 過渡期レベル) SQL_SRJO_NATURAL_JOIN (FIPS 過渡期レベル)、(FIPS 過渡期レベル) sql_srjo_right_outer_join、SQL_SRJO_UNION_JOIN (完全レベル)  
  
 Sql_srjo_inner_join がのサポートを示す、 **INNER JOIN**内部結合機能ではなく、構文です。 サポート、 **INNER JOIN**構文が FIPS 移行中に、内部結合機能は、サポート**エントリ**です。  
  
 SQL_SQL92_REVOKE(ODBC 3.0)  
 サポートされている句を列挙する SQLUINTEGER ビットマスク、**取り消す**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。  
  
 この機能をサポートする必要があります、sql-92 または FIPS 準拠のレベルが各ビットマスクの横にあるかっこ内に表示されます。  
  
 以下のビットマスクを使用して、どの句が、データ ソースによってサポートされてを調べます。  
  
 SQL_SR_CASCADE (FIPS 過渡期レベル) SQL_SR_DELETE_TABLE (Entry レベル) SQL_SR_GRANT_OPTION_FOR (中間レベル) SQL_SR_INSERT_COLUMN (中間レベル) SQL_SR_INSERT_TABLE (Entry レベル) SQL_SR_REFERENCES_COLUMN (Entry レベル) SQL_SR_REFERENCES_TABLE (Entry レベル) SQL_SR_RESTRICT (FIPS 過渡期レベル) SQL_SR_SELECT_TABLE (Entry レベル) SQL_SR_UPDATE_COLUMN (Entry レベル) SQL_SR_UPDATE_TABLE (Entry レベル) SQL_SR_USAGE_ON_DOMAIN (FIPS 過渡期レベル) SQL_SR_USAGE_ON_CHARACTER_SET (FIPS 過渡期レベル) SQL_SR_USAGE_ON_COLLATION (FIPS 過渡期レベル) SQL_SR_USAGE_ON_TRANSLATION (FIPS 過渡期レベル)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR(ODBC 3.0)  
 サポートされている行値コンス トラクター式を列挙する SQLUINTEGER ビットマスク、**選択**ステートメントでは、sql-92 で定義されています。 以下のビットマスクを使用して、どのオプションは、データ ソースでサポートを調べます。  
  
 SQL_SRVC_VALUE_EXPRESSION、SQL_SRVC_ SQL_SRVC_DEFAULT SQL_SRVC_ROW_SUBQUERY  
  
 SQL_SQL92_STRING_FUNCTIONS(ODBC 3.0)  
 Sql-92 で定義されているドライバーと関連付けられたデータ ソースでサポートされる文字列のスカラー関数を列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを使用してがサポートする文字列関数を調べます。  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS(ODBC 3.0)  
 Sql-92 で定義されている、サポートされている値の式を列挙する SQLUINTEGER ビットマスクです。  
  
 この機能をサポートする必要があります、sql-92 または FIPS 準拠のレベルが各ビットマスクの横にあるかっこ内に表示されます。  
  
 以下のビットマスクを使用して、どのオプションは、データ ソースでサポートを調べます。  
  
 (中間レベル) SQL_SVE_CASE、SQL_SVE_CAST (FIPS 過渡期レベル)、(中間レベル) sql_sve_coalesce、SQL_SVE_NULLIF (中間レベル)  
  
 SQL_STANDARD_CLI_CONFORMANCE (ODBC 3.0)  
 ドライバーが準拠する CLI 規格または標準を列挙する SQLUINTEGER ビットマスクです。 以下のビットマスクを使用して、どのレベルに準拠しているドライバーを調べます。  
  
 SQL_SCC_XOPEN_CLI_VERSION1: 開いているグループ CLI バージョン 1 を使用して、ドライバーが準拠しています。  
  
 SQL_SCC_ISO92_CLI: ISO 92 CLI を使用して、ドライバーが準拠しています。  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 ドライバーでサポートされている静的カーソルの属性を記述する SQLUINTEGER ビットマスクです。 このビットマスクには、属性の最初のサブセットが含まれています。2 番目のサブセット SQL_STATIC_CURSOR_ATTRIBUTES2 を参照してください。  
  
 以下のビットマスクを使用して、どの属性がサポートされているを調べます。  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 これらのビットマスクの説明については、SQL_DYNAMIC_CURSOR_ATTRIBUTES1 を参照してください (と説明に示される「動的カーソル」を"静的 cursor"に置き換える)。  
  
 SQL 92 中級者向けの準拠レベル ドライバー通常サポートが返されます、SQL_CA1_NEXT、SQL_CA1_ABSOLUTE、および SQL_CA1_RELATIVE オプション、ドライバーが埋め込み SQL FETCH ステートメントを通じてスクロール可能なカーソルをサポートしているためです。 これは直接を決定できなかったため、基になる SQL サポート、ただし、スクロール可能なカーソルがサポートされていない、SQL 92 中級者向けのレベル – 準拠するドライバーに対しても。  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 ドライバーでサポートされている静的カーソルの属性を記述する SQLUINTEGER ビットマスクです。 このビットマスクには、属性の 2 つ目のサブセットが含まれています。最初のサブセット SQL_STATIC_CURSOR_ATTRIBUTES1 を参照してください。  
  
 以下のビットマスクを使用して、どの属性がサポートされているを調べます。  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 これらのビットマスクの説明については、SQL_DYNAMIC_CURSOR_ATTRIBUTES2 を参照してください (と説明に示される「動的カーソル」を"静的 cursor"に置き換える)。  
  
 SQL_STRING_FUNCTIONS (ODBC 1.0)  
 注: 情報の種類が ODBC 1.0; で導入されました。各ビットマスクには、導入されたバージョンが付いています。  
  
 ドライバーと関連付けられているデータ ソースでサポートされているスカラー文字列関数を列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを使用してがサポートする文字列関数を調べます。  
  
 SQL_FN_STR_ASCII (ODBC 1.0) SQL_FN_STR_BIT_LENGTH (ODBC 3.0) SQL_FN_STR_CHAR (ODBC 1.0) SQL_FN_STR_CHAR_LENGTH (ODBC 3.0) SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0) SQL_FN_STR_CONCAT (ODBC 1.0) SQL_FN_STR_DIFFERENCE (ODBC 2.0) SQL_FN_STR_INSERT (ODBC1.0) SQL_FN_STR_LCASE (ODBC 1.0) SQL_FN_STR_LEFT (ODBC 1.0) SQL_FN_STR_LENGTH (ODBC 1.0) SQL_FN_STR_LOCATE (ODBC 1.0) SQL_FN_STR_LTRIM (ODBC 1.0) SQL_FN_STR_OCTET_LENGTH (ODBC 3.0) SQL_FN_STR_POSITION (ODBC 3.0) SQL_FN_STR_REPEAT (ODBC 1.0) SQL_FN_(ODBC 1.0) できるような SQL_FN_STR_RIGHT (ODBC 1.0) SQL_FN_STR_RTRIM (ODBC 1.0) SQL_FN_STR_SOUNDEX (ODBC 2.0) SQL_FN_STR_SPACE (ODBC 2.0)、(ODBC 1.0) SQL_FN_STR_SUBSTRING、SQL_FN_STR_UCASE (ODBC 1.0)  
  
 アプリケーションが呼び出すことができる場合、**を見つける**を持つスカラー関数、 *string_exp1*、 *string_exp2*、および*開始*引数、ドライバーSQL_FN_STR_LOCATE ビットマスクを返します。 アプリケーションでのみを持つ 検索のスカラー関数を呼び出すことができる場合、 *string_exp1*と*string_exp2*引数、ドライバーは SQL_FN_STR_LOCATE_2 ビットマスクを返します。 完全にサポートするドライバー、 **LOCATE**スカラー関数は、両方のビットマスクを返します。  
  
 (詳細については、次を参照してください[文字列関数](../../../odbc/reference/appendixes/string-functions.md)、付録 e"スカラー関数です。")。  
  
 SQL_SUBQUERIES (ODBC 2.0)  
 サブクエリをサポートする述語を列挙する SQLUINTEGER ビットマスク。  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 SQL_SQ_CORRELATED_SUBQUERIES ビットマスクは、サブクエリをサポートするすべての述語が相関サブクエリをサポートすることを示します。  
  
 SQL 92 エントリのレベル – 準拠ドライバーでは、すべてのこれらのビットが設定されているビットマスクは常に返します。  
  
 SQL_SYSTEM_FUNCTIONS (ODBC 1.0)  
 ドライバーと関連付けられているデータ ソースでサポートされているスカラー システム関数を列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを使用してがサポートするシステム関数を調べます。  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM (ODBC 1.0)  
 テーブルのデータ ソースの仕入先の名前を持つ文字の文字列たとえば、"table"または"file"です。  
  
 この文字の文字列は、上部、下部、または大文字と小文字で指定できます。  
  
 SQL 92 エントリのレベル – 準拠するドライバーは、"table"常に戻ります。  
  
 SQL_TIMEDATE_ADD_INTERVALS (ODBC 2.0)  
 ドライバーおよび TIMESTAMPADD スカラー関数の場合、関連付けられたデータ ソースによってサポートされるタイムスタンプの間隔を列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを使用して、サポートされている間隔を調べます。  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 FIPS 過渡期のレベル – 準拠ドライバーでは、すべてのこれらのビットが設定されているビットマスクは常に返します。  
  
 SQL_TIMEDATE_DIFF_INTERVALS (ODBC 2.0)  
 ドライバーおよび TIMESTAMPDIFF スカラー関数の場合、関連付けられたデータ ソースによってサポートされるタイムスタンプの間隔を列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを使用して、サポートされている間隔を調べます。  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 FIPS 過渡期のレベル – 準拠ドライバーでは、すべてのこれらのビットが設定されているビットマスクは常に返します。  
  
 SQL_TIMEDATE_FUNCTIONS (ODBC 1.0)  
 注: 情報の種類が ODBC 1.0; で導入されました。各ビットマスクには、導入されたバージョンが付いています。  
  
 スカラーの日付と時刻の関数が、ドライバーと関連付けられたデータ ソースによってサポートされているを列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを使用してがサポートする日付と時刻の関数を調べます。  
  
 SQL_FN_TD_CURRENT_DATE ODBC 3.0) SQL_FN_TD_CURRENT_TIME (ODBC 3.0) SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0) SQL_FN_TD_CURDATE (ODBC 1.0) SQL_FN_TD_CURTIME (ODBC 1.0) SQL_FN_TD_DAYNAME (ODBC 2.0) SQL_FN_TD_DAYOFMONTH (ODBC 1.0) SQL_FN_TD_DAYOFWEEK (ODBC 1.0) SQL_FN_TD_DAYOFYEAR (ODBC 1.0) SQL_FN_TD_EXTRACT (ODBC 3.0) SQL_FN_TD_HOUR (ODBC 1.0) SQL_FN_TD_MINUTE (ODBC 1.0) SQL_FN_TD_MONTH (ODBC 1.0) SQL_FN_TD_MONTHNAME (ODBC 2.0) SQL_FN_TD_NOW (ODBC 1.0) SQL_FN_TD_QUARTER (ODBC 1.0) SQL_FN_TD_2 番目 (ODBC 1.0) SQL_FN_TD_TIMESTAMPADD (ODBC 2.0) SQL_FN_TD_TIMESTAMPDIFF (ODBC 2.0)、(ODBC 1.0) SQL_FN_TD_WEEK、SQL_FN_TD_YEAR (ODBC 1.0)  
  
 SQL_TXN_CAPABLE (ODBC 1.0)  
 注: 情報の種類が ODBC 1.0; で導入されました。戻り値の各値には、導入されたバージョンが付いています。  
  
 ドライバーまたはデータ ソースでサポートされるトランザクションを記述する SQLUSMALLINT 値:  
  
 SQL_TC_NONE = トランザクションはサポートされていません。 (ODBC 1.0)  
  
 SQL_TC_DML = トランザクションは、データ操作言語 (DML) ステートメントのみを含めることができます (**選択**、**挿入**、**更新**、**削除**). データ定義言語 (DDL) ステートメントのトランザクションの原因でエラーが発生しました。 (ODBC 1.0)  
  
 SQL_TC_DDL_COMMIT = トランザクションは、DML ステートメントのみを含めることができます。 DDL ステートメント (**CREATE TABLE**、 **DROP INDEX**など)、トランザクションをコミットするトランザクションの原因で発生しました。 (ODBC 2.0)  
  
 SQL_TC_DDL_IGNORE = トランザクションは、DML ステートメントのみを含めることができます。 トランザクションで発生した DDL ステートメントは無視されます。 (ODBC 2.0)  
  
 SQL_TC_ALL = トランザクションは、DDL ステートメントおよび任意の順序での DML ステートメントを含めることができます。 (ODBC 1.0)  
  
 (トランザクションのサポートは、sql-92 で必須であるため、sql-92 に準拠するドライバー [任意のレベル] を返さない SQL_TC_NONE。)  
  
 SQL_TXN_ISOLATION_OPTION (ODBC 1.0)  
 ドライバーまたはデータ ソースから使用可能なトランザクション分離レベルを列挙する SQLUINTEGER ビットマスクです。  
  
 以下のビットマスクを決定するオプションがサポートされているフラグと共に使用されます。  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 これらの分離レベルの詳細については、SQL_DEFAULT_TXN_ISOLATION の説明を参照してください。  
  
 トランザクション分離レベルを設定するアプリケーションを呼び出す**SQLSetConnectAttr** SQL_ATTR_TXN_ISOLATION 属性を設定します。 詳細については、次を参照してください。 [SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)です。  
  
 SQL 92 エントリのレベル – 準拠ドライバーでは、サポートされている、SQL_TXN_SERIALIZABLE は常に返します。 FIPS 過渡期のレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。  
  
 SQL_UNION (ODBC 2.0)  
 サポートを列挙する SQLUINTEGER ビットマスク、**共用体**句。  
  
 SQL_U_UNION =、データ ソースがサポートする、**共用体**句。  
  
 SQL_U_UNION_ALL =、データ ソースがサポートする、**すべて**キーワード、**共用体**句。 (**SQLGetInfo**と両方を返します SQL_U_UNION、SQL_U_UNION_ALL ここでします)。  
  
 SQL 92 エントリのレベル – 準拠するドライバーは常に返しますこれらのオプションの両方のサポートされています。  
  
 SQL_USER_NAME (ODBC 1.0)  
 ログイン名と異なる可能性がある特定のデータベースで使用される名前を持つ文字列を返します。  
  
 SQL_XOPEN_CLI_YEAR (ODBC 3.0)  
 使用するバージョンの ODBC ドライバー マネージャーが完全に準拠して、Open Group 仕様のパブリケーションの年を示す文字列。  
  
 SQL_ACCESSIBLE_PROCEDURES (ODBC 1.0)  
 文字の文字列:"Y"、ユーザーは、によって返されるすべてのプロシージャを実行できる場合**SQLProcedures**です。"N"プロシージャがある場合は、ユーザーが実行できないことを返されます。  
  
 SQL_ACCESSIBLE_TABLES (ODBC 1.0)  
 文字の文字列:"Y"、ユーザーが保証される場合**選択**によって返されるすべてのテーブル特権**SQLTables**です。"N"のテーブルがある場合に、ユーザーがアクセスできないことが返されます。  
  
 SQL_ACTIVE_ENVIRONMENTS (ODBC 3.0)  
 ドライバーをサポートできるアクティブな環境の最大数を指定する SQLUSMALLINT 値です。 指定された制限がないか、上限が不明な場合、この値は 0 に設定します。  
  
 SQL_AGGREGATE_FUNCTIONS (ODBC 3.0)  
 集計関数のサポートを列挙する SQLUINTEGER ビットマスク。  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 SQL 92 エントリのレベル – 準拠するドライバーは常に返しますすべてこれらのオプションのサポートされています。  
  
 SQL_ALTER_DOMAIN (ODBC 3.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、 **ALTER ドメイン**ステートメントでは、データ ソースでサポートされている、sql-92 で定義されています。 SQL 92 完全レベルに準拠したドライバーすべて、ビットマスクは常に返します。 「0」の戻り値は、つまり、 **ALTER ドメイン**ステートメントはサポートされていません。  
  
 この機能をサポートする必要があります、sql-92 または FIPS 準拠のレベルが各ビットマスクの横にあるかっこ内に表示されます。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT ドメイン制約がサポートされている追加の = (フル レベル)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT =\<ドメインを alter > \<set ドメイン既定句 > はサポートされて (フル レベル)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION =\<制約定義名句 > ドメイン制約 (中間レベル) の名前付けのサポート  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT = \<drop ドメイン制約句 > はサポートされて (フル レベル)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT =\<ドメインを alter > \<drop ドメイン既定句 > はサポートされて (フル レベル)  
  
 次のビットをサポートされている指定\<制約属性 > 場合\<ドメイン制約の追加 > はサポートされて (SQL_AD_ADD_DOMAIN_CONSTRAINT ビットが設定されます)。  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (完全レベル) SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE (完全レベル) SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED (完全レベル) SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE (完全レベル)  
  
 SQL_ALTER_TABLE (ODBC 2.0)  
 内の句を列挙する SQLUINTEGER ビットマスク、 **ALTER TABLE**ステートメント、データ ソースによってサポートされています。  
  
 この機能をサポートする必要があります、sql-92 または FIPS 準拠のレベルが各ビットマスクの横にあるかっこ内に表示されます。  
  
 以下のビットマスクを使用して、どの句がサポートされてを調べます。  
  
 SQL_AT_ADD_COLUMN_COLLATION =\<列の追加 > 句はサポートされて、列の照合順序 (完全レベル) を指定する機能を使用 (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT =\<列の追加 > 句はサポートされて、列の既定値 (FIPS 過渡期レベル) を指定する機能を使用 (ODBC 3.0)  
  
 Sql_at_add_column_single、=\<列の追加 > は (FIPS 過渡期レベル) のサポート (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT =\<列の追加 > 句はサポートされて、列の制約 (FIPS 過渡期レベル) を指定する機能を使用 (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT =\<テーブル制約の追加 > 句がサポートされている (FIPS 過渡期レベル) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION =\<制約名の定義 > は列とテーブルの制約 (中間レベル) の名前付けのサポート (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_CASCADE =\<ドロップ列 > CASCADE がサポートされている (FIPS 過渡期レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT =\<列を alter > \<drop 列の既定の句 > は (中間レベル) のサポート (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT =\<ドロップ列 > 制限がサポートされている (FIPS 過渡期レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT =\<ドロップ列 > 制限がサポートされている (FIPS 過渡期レベル) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT =\<列を alter >\<セット列の default 句 > は (中間レベル) をサポート (ODBC 3.0)  
  
 次のビットのサポートを指定する\<制約属性 > の列またはテーブルの制約の指定がサポートされている場合 (SQL_AT_ADD_CONSTRAINT ビットが設定されます)。  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (完全レベル) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (完全レベル) (ODBC 3.0) SQL_AT_CONSTRAINT_DEFERRABLE (完全レベル) (ODBC 3.0) SQL_AT_CONSTRAINT_NON_DEFERRABLE (完全レベル) (ODBC 3.0)  
  
 SQL_ASYNC_MODE (ODBC 3.0)  
 ドライバーでの非同期のサポートのレベルを示す SQLUINTEGER 値:  
  
 SQL_AM_CONNECTION = 接続レベルの非同期実行をサポートします。 か、指定された接続ハンドルに関連付けられたすべてのステートメント ハンドルは非同期モードで、または同期モードではすべて。 接続のステートメント ハンドルは、同じ接続上の別のステートメント ハンドルが同期モードでは、その逆で非同期モードですることはできません。  
  
 SQL_AM_STATEMENT = ステートメント レベルの非同期実行がサポートされています。 同じ接続で他のステートメント ハンドルを同期モードで、接続ハンドルに関連付けられているいくつかのステートメント ハンドルは非同期モードで指定できます。  
  
 SQL_AM_NONE = 非同期モードはサポートされていません。  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 行の可用性に対するドライバーの動作を列挙する SQLUINTEGER ビットマスクをカウントします。 以下のビットマスクは、情報の種類と共に使用されます。  
  
 SQL_BRC_ROLLED_UP = 行数は、連続する INSERT、DELETE、または UPDATE ステートメントを 1 つにロールアップします。 このビットが設定されていない場合は、各ステートメントに対して行カウントがあります。  
  
 SQL_BRC_PROCEDURES = ストアド プロシージャのバッチを実行すると、いずれかが使用可能な場合、行カウントします。 行数が使用可能な場合は、上または SQL_BRC_ROLLED_UP ビットによって、個別に使用できる、ロールできます。  
  
 SQL_BRC_EXPLICIT バッチを呼び出すことによって直接実行すると、いずれかが使用可能な場合は、行のカウントを = **SQLExecute**または**SQLExecDirect**です。 行数が使用可能な場合は、上または SQL_BRC_ROLLED_UP ビットによって、個別に使用できる、ロールできます。  
  
## <a name="example"></a>例  
 **SQLGetInfo** 、SQLUINTEGER ビットマスクでとしてサポートされているオプションの一覧を返します **InfoValuePtr*です。 各オプションのビットマスクは、オプションはサポートされているかどうかを決定するフラグと共に使用されます。  
  
 など、アプリケーションでは、部分文字列のスカラー関数は、接続に関連付けられているドライバーでサポートされているかどうかを決定するのに、次のコードを使用できます。  
  
 使用する別の例について**SQLGetInfo**を参照してください[SQLTables 関数](../../../odbc/reference/syntax/sqltables-function.md)です。  
  
```  
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
 接続属性の設定値を返す  
 [SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)  
  
 ドライバーが関数をサポートしているかどうかを決定します。  
 [SQLGetFunctions 関数](../../../odbc/reference/syntax/sqlgetfunctions-function.md)  
  
 ステートメント属性の設定値を返す  
 [SQLGetStmtAttr 関数](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)  
  
 データ ソースのデータ型に関する情報を返す  
 [SQLGetTypeInfo 関数](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

