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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303344"
---
# <a name="sqlgetinfo-function"></a>SQLGetInfo 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLGetInfo**は、接続に関連付けられているドライバーとデータ ソースに関する一般的な情報を返します。  
  
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
 *接続ハンドル*  
 [入力] 接続ハンドル。  
  
 *Infotype*  
 [入力]情報の種類。  
  
 *インフォバリュープター*  
 [出力]情報を返すバッファーへのポインター。 要求された*インフォタイプ*に応じて、返される情報は、NULL で終わる文字列、SQLUSMALLINT 値、SQLUINTEGER ビットマスク、SQLUINTEGER フラグ、SQLUINTEGER バイナリ値、または SQLULEN 値のいずれかになります。  
  
 *引数が*SQL_DRIVER_HDESCまたはSQL_DRIVER_HSTMT場合 *、InfoValuePtr*引数は入力と出力の両方になります。 (詳細については、この関数の説明の後半のSQL_DRIVER_HDESCまたはSQL_DRIVER_HSTMT記述子を参照してください。  
  
 *InfoValuePtr*が NULL の場合 *、StringLengthPtr*は*InfoValuePtr*が指すバッファーで返すバイトの合計数 (文字データの null 終端文字を除く) を返します。  
  
 *BufferLength*  
 [入力]\* *InfoValuePtr*バッファーの長さ。 * \*InfoValuePtr*の値が文字列でない場合、または*InfoValuePtr*が null ポインターの場合は *、BufferLength*引数は無視されます。 ドライバは、インフォタイプに基づいて*\*、インフォバリュープラー*のサイズが SQLUSMALLINT または SQLUINTEGER であると想定*しています*。 * \*InfoValuePtr*が Unicode 文字列の場合 **(SQLGetInfoW**を呼び出すとき)、BufferLength 引数は偶数でなければなりません。 *BufferLength*ない場合は、SQLSTATE HY090 (無効なストリングまたはバッファー長) が戻されます。  
  
 *文字列を長くします。*  
 [出力]**InfoValuePtr*で返されるバイトの総数 (文字データの NULL 終端文字を除く) を返すバッファーへのポインター。  
  
 文字データの場合、返されるバイト数が*BufferLength*より大きいか等しい場合\**、InfoValuePtr*の情報は*BufferLength*バイトから null 終端文字の長さを引いた値に切り捨てられ、ドライバーによって null で終了します。  
  
 その他のすべてのデータ型の場合 *、BufferLength*の値は無視され、ドライバーは\**InfoValuePtr*のサイズが情報*の種類*に応じて SQLUSMALLINT または SQLUINTEGER であると想定します。  
  
## <a name="return-value"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetInfo**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_DBCの*ハンドル型*と*接続ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLGetInfo**によって返される SQLSTATE 値を一覧し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|バッファ\* *InfoValuePtr*は、要求されたすべての情報を返すのに十分な大きさではありませんでした。 したがって、情報は切り捨てられました。 要求された情報の長さは、その切り捨てられていない形式で **StringLengthPtr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08003|接続が開かない|(DM)*インフォタイプ*で要求された情報の種類には、接続が開いている必要があります。 ODBC によって予約されている情報の種類のうち、接続を開いたままで返すことができるのはSQL_ODBC_VERのみです。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY024|属性値が無効です|(DM)*引数が*SQL_DRIVER_HSTMTされ *、InfoValuePtr*が指す値が有効なステートメント ハンドルではありませんでした。<br /><br /> (DM)*引数が*SQL_DRIVER_HDESCされ *、InfoValuePtr*が指す値が有効な記述子ハンドルではありませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*BufferLength*に指定された値が 0 より小さかった。<br /><br /> (DM) *BufferLength*に指定された値は奇数で*\*、InfoValuePtr*は Unicode データ型です。|  
|HY096|情報の種類が範囲外です|*引数 InfoType*に指定された値は、ドライバーでサポートされている ODBC のバージョンに対して無効です。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプションのフィールドが実装されていません|*引数 InfoType*に指定された値は、ドライバーによってサポートされていないドライバー固有の値でした。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM) に対応するドライバー、*接続ハンドル*は、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 現在定義されている情報の種類については、このセクションの後半の「情報の種類」に示します。さまざまなデータ ソースを利用するために、さらに多くのデータ ソースを定義することが期待されます。 情報型の範囲は ODBC によって予約されています。ドライバー開発者は、Open Group から独自のドライバー固有の使用の値を予約する必要があります。 **SQLGetInfo**は、ドライバー定義*のインフォタイプ*に対して、ユニコード変換または*サンクを*実行しません (ODBC*プログラマ リファレンス*の[「付録 A: ODBC エラー コード](../../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md)」を参照)。 詳細については、「[ドライバ固有のデータ型、記述子の型、情報の種類、診断の種類、および属性](../../../odbc/reference/develop-app/driver-specific-data-types-descriptor-information-diagnostic.md)」を参照してください。 \* *InfoValuePtr*で返される情報の形式は、要求された*インフォタイプ*によって異なります。 **SQLGetInfo**は、次の 5 つの異なる形式のいずれかで情報を返します。  
  
-   NULL で終わる文字列  
  
-   値  
  
-   SQLUINTEGER ビットマスク  
  
-   整数の値  
  
-   2 進整数のバイナリ値  
  
 以下の各情報タイプの形式は、タイプの説明に記載されています。 アプリケーションは、 **InfoValuePtr*に返される値をそれに応じてキャストする必要があります。 アプリケーションが SQLUINTEGER ビットマスクからデータを取得する方法の例については、「コード例」を参照してください。  
  
 ドライバーは、次の表で定義されている各情報の種類の値を返す必要があります。 情報の種類がドライバーまたはデータ ソースに適用されない場合、ドライバーは、次の表に示す値のいずれかを返します。  
  
 文字列 ("Y" または "N" )  
 "N"  
  
 文字列 ("Y" や "N" ではない)  
 空の文字列  
  
 スモートフィント  
 0  
  
 ビットマスクまたは SQLUINTEGER 2 進数値  
 0L  
  
 たとえば、データ ソースがプロシージャをサポートしていない場合 **、SQLGetInfo**は、プロシージャに関連する*InfoType*の値について、次の表に示す値を返します。  
  
 SQL_PROCEDURES  
 "N"  
  
 SQL_ACCESSIBLE_PROCEDURES  
 "N"  
  
 SQL_MAX_PROCEDURE_NAME_LEN  
 0  
  
 SQL_PROCEDURE_TERM  
 空の文字列  
  
 **SQLGetInfo**は、ODBC で使用するために予約されているが、ドライバーでサポートされている ODBC のバージョンで定義されていない*情報型*の値に対して SQLSTATE HY096 (無効な引数値) を返します。 ODBC ドライバーのどのバージョンに準拠しているかを確認するには、アプリケーションは、SQL_DRIVER_ODBC_VER情報の種類を使用して**SQLGetInfo**を呼び出します。 **SQLGetInfo**は、ドライバー固有の使用のために予約されているが、ドライバーでサポートされていない情報の種類の範囲内にある*InfoType*の値の SQLSTATE HYC00 (実装されていないオプションの機能) を返します。  
  
 **SQLGetInfo**へのすべての呼び出しは、ドライバー マネージャーのバージョンを返す *、情報の種類*がSQL_ODBC_VER場合を除き、開いている接続を必要とします。  
  
## <a name="information-types"></a>情報の種類  
 このセクションでは、 **SQLGetInfo**でサポートされる情報の種類を示します。 情報タイプは、カテゴリ別にグループ化され、アルファベット順にリストされます。 ODBC 3 *.x*用に追加または名前変更された情報の種類も一覧表示されます。  
  
## <a name="driver-information"></a>ドライバ情報  
 *InfoType*引数の次の値は、ODBC ドライバーに関する情報を返します。  
  
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
>  **SQLGetInfo**を実装する場合、ドライバーは、サーバーから情報が送信または要求される回数を最小限に抑えることによってパフォーマンスを向上させることができます。  
  
## <a name="dbms-product-information"></a>DBMS 製品情報  
 *InfoType*引数の次の値は、DBMS の名前やバージョンなどの DBMS 製品に関する情報を返します。  
  
 SQL_DATABASE_NAMESQL_DBMS_NAMESQL_DBMS_VER  
  
## <a name="data-source-information"></a>データ ソース情報  
 *InfoType*引数の次の値は、カーソルの特性やトランザクション機能など、データ ソースに関する情報を返します。  
  
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
 *InfoType*引数の次の値は、データ ソースでサポートされている SQL ステートメントに関する情報を返します。 これらの情報タイプで記述される各機能の SQL 構文は、SQL-92 構文です。 これらの情報型は、SQL-92 文法全体を完全には記述しません。 代わりに、データ ソースが通常異なるレベルのサポートを提供する文法のこれらの部分を記述します。 具体的には、SQL-92 の DDL ステートメントの大部分をカバーしています。  
  
 アプリケーションでは、サポートされている文法の一般的なレベルをSQL_SQL_CONFORMANCE情報の種類から判断し、その他の情報の種類を使用して、記載されている標準準拠レベルとの違いを判断する必要があります。  
  
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
 *InfoType*引数の次の値は、SQL ステートメントの識別子と句に適用される制限に関する情報を返します。 ドライバーまたはデータ ソースによって制限を課すことができます。  
  
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
  
## <a name="scalar-function-information"></a>スカラー関数情報  
 *InfoType*引数の次の値は、データ ソースとドライバーでサポートされているスカラー関数に関する情報を返します。 スカラー関数の詳細については、「[付録 E : スカラー関数](../../../odbc/reference/appendixes/appendix-e-scalar-functions.md)」を参照してください。  
  
|||  
|-|-|  
|SQL_CONVERT_FUNCTIONS|SQL_TIMEDATE_ADD_INTERVALS|  
|SQL_NUMERIC_FUNCTIONS|SQL_TIMEDATE_DIFF_INTERVALS|  
|SQL_STRING_FUNCTIONS|SQL_TIMEDATE_FUNCTIONS|  
|SQL_SYSTEM_FUNCTIONS||  
  
## <a name="conversion-information"></a>変換情報  
 *InfoType*引数の次の値は **、CONVERT**スカラー関数を使用して指定した SQL データ型を変換できる SQL データ型のリストを返します。  
  
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
  
## <a name="information-types-added-for-odbc-3x"></a>ODBC 3.x 用に追加された情報型  
 ODBC 3 *.x*に*対して、次のインフォタイプ*引数の値が追加されました。  
  
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
  
## <a name="information-types-renamed-for-odbc-3x"></a>ODBC 3.x 用に名前が変更された情報型  
 次の*InfoType*引数の値は、ODBC 3 *.x*の名前が変更されました。  
  
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
  
## <a name="information-types-deprecated-in-odbc-3x"></a>ODBC 3.x で情報型が使用されなくなった  
 以下の*InfoType*引数の値は、ODBC 3 *.x*で非推奨になりました。 ODBC 3 *.x*ドライバは、ODBC 2 *.x*アプリケーションとの下位互換性を維持するために、これらの情報型を引き続きサポートする必要があります。 これらの型の詳細については、「付録 G: 下位互換性のためのドライバーのガイドライン」の[SQLGetInfo サポート](../../../odbc/reference/appendixes/sqlgetinfo-support.md)を参照してください。  
  
|||  
|-|-|  
|SQL_FETCH_DIRECTION|SQL_POS_OPERATIONS|  
|SQL_LOCK_TYPES|SQL_POSITIONED_STATEMENTS|  
|SQL_ODBC_API_CONFORMANCE|SQL_SCROLL_CONCURRENCY|  
|SQL_ODBC_SQL_CONFORMANCE|SQL_STATIC_SENSITIVITY|  
  
## <a name="information-type-descriptions"></a>情報の種類 説明  
 次の表は、各情報の種類、導入された ODBC のバージョン、およびその説明をアルファベット順に一覧表示します。  
  
 SQL_ACCESSIBLE_PROCEDURES(ODBC 1.0)  
 ユーザーが**SQLProcedures によって**返されるすべてのプロシージャを実行できる場合は、"Y" という文字列を指定します。ユーザーが実行できないプロシージャが返される可能性がある場合は"N"。  
  
 SQL_ACCESSIBLE_TABLES(ODBC 1.0)  
 **SQLTables**によって返されるすべてのテーブルに対する**SELECT**権限がユーザーに保証されている場合は、"Y" という文字列を指定します。ユーザーがアクセスできないテーブルが返される可能性がある場合は"N"。  
  
 SQL_ACTIVE_ENVIRONMENTS(ODBC 3.0)  
 ドライバーがサポートできるアクティブな環境の最大数を指定する SQLUSMALLINT 値。 指定された制限がない場合、または制限が不明な場合、この値はゼロに設定されます。  
  
 SQL_AGGREGATE_FUNCTIONS(ODBC 3.0)  
 SQLUINTEGER ビットマスクの列挙関数のサポート:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 SQL-92 エントリ レベル準拠ドライバーは、常にサポートされているこれらのオプションのすべてを返します。  
  
 SQL_ALTER_DOMAIN(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**ALTER DOMAIN**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。 SQL-92 完全レベル準拠のドライバーは、常にすべてのビットマスクを返します。 "0" の戻り値は **、ALTER DOMAIN**ステートメントがサポートされないことを意味します。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの隣に括弧で囲んで示されています。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = ドメイン制約の追加がサポートされています (フル レベル)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT \<= ドメイン\<>設定ドメインのデフォルト節>変更がサポートされています (フルレベル)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION \<= 制約名定義句>命名ドメイン制約 (中間レベル) に対してサポートされています。  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT \<= ドメイン制約句>削除>サポート (フル レベル)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT \<= ドメイン\<>ドロップ ドメインのデフォルト句>変更>サポートされています (フル レベル)  
  
 次のビットは、ドメイン\<制約>の追加\<がサポートされている場合>サポートされる制約属性を指定します (SQL_AD_ADD_DOMAIN_CONSTRAINT ビットが設定されています)。  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (フルレベル)SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE(フルレベル)SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED(フルレベル)SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE(フルレベル)  
  
 SQL_ALTER_TABLE(ODBC 2.0)  
 データ ソースでサポートされている**ALTER TABLE**ステートメント内の句を列挙した SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの隣に括弧で囲んで示されています。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_AT_ADD_COLUMN_COLLATION \<= 列>の追加句がサポートされており、列照合順序 (フル レベル) を指定する機能 (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT \<= 列>節の追加がサポートされ、列のデフォルト (FIPS 移行レベル) を指定する機能 (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE \<= 列>の追加がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT \<= 列>節の追加がサポートされ、列制約 (FIPS 移行レベル) を指定する機能 (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT \<= テーブル制約>追加句がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION \<= 制約名定義>列およびテーブルの制約の命名 (中間レベル) (ODBC 3.0) でサポートされています。  
  
 SQL_AT_DROP_COLUMN_CASCADE \<= カスケード>ドロップ列がサポートされている (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT \<= 列\<>変更>列のデフォルト節がサポートされます (中間レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT \<= RESTRICT>ドロップ列がサポートされている (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT \<= RESTRICT>ドロップ列がサポートされている (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT \<= 列\<の変更>列のデフォルト節>がサポートされている (中間レベル) (ODBC 3.0)  
  
 次のビットは、列\<制約またはテーブル制約の指定がサポートされている場合 (SQL_AT_ADD_CONSTRAINTビットが設定されている) 場合に>サポート制約属性を指定します。  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (フル レベル) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (フル レベル) (ODBC 3.0)SQL_AT_CONSTRAINT_DEFERRABLE (フル レベル) (ODBC 3.0)SQL_AT_CONSTRAINT_NON_DEFERRABLE (フル レベル) (ODBC 3.0) (ODBC 3.0)  
  
 SQL_ASYNC_DBC_FUNCTIONS (ODBC 3.8)  
 ドライバーが接続ハンドルで非同期に関数を実行できるかどうかを示す SQLUINTEGER 値。  
  
 SQL_ASYNC_DBC_CAPABLE = ドライバーは、接続関数を非同期に実行できます。  
  
 SQL_ASYNC_DBC_NOT_CAPABLE = ドライバは接続関数を非同期に実行できません。  
  
 SQL_ASYNC_MODE(ODBC 3.0)  
 ドライバーでの非同期サポートのレベルを示す SQLUINTEGER 値:  
  
 SQL_AM_CONNECTION = 接続レベルの非同期実行がサポートされています。 指定された接続ハンドルに関連付けられているすべてのステートメント ハンドルが非同期モードであるか、すべて同期モードです。 同じ接続の別のステートメント ハンドルが同期モードである間は、接続のステートメント ハンドルを非同期モードにすることはできません。  
  
 SQL_AM_STATEMENT = ステートメント レベルの非同期実行がサポートされています。 接続ハンドルに関連付けられたステートメント ハンドルの中には、非同期モードに設定できるものもありますが、同じ接続の他のステートメント ハンドルは同期モードです。  
  
 SQL_AM_NONE = 非同期モードはサポートされていません。  
  
 SQL_ASYNC_NOTIFICATION  
 ドライバーが非同期通知をサポートするかどうかを示す SQLUINTEGER 値:  
  
-   **SQL_ASYNC_NOTIFICATION_CAPABLE**非同期実行通知は、ドライバーでサポートされています。  
  
-   **SQL_ASYNC_NOTIFICATION_NOT_CAPABLE**非同期実行通知は、ドライバーではサポートされていません。  
  
 ODBC 非同期操作には、接続レベルの非同期操作とステートメント レベルの非同期操作の 2 つのカテゴリがあります。  ドライバーがSQL_ASYNC_NOTIFICATION_CAPABLEを返す場合は、非同期で実行できるすべての API の通知をサポートする必要があります。  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 行数の可用性に関するドライバーの動作を列挙する SQLUINTEGER ビットマスク。 以下のビットマスクは、情報タイプと共に使用されます。  
  
 SQL_BRC_ROLLED_UP = 連続する INSERT、DELETE、または UPDATE ステートメントの行カウントは、1 つにロールアップされます。 このビットが設定されていない場合、各ステートメントに対して行数が使用可能になります。  
  
 SQL_BRC_PROCEDURES = 行数がある場合は、ストアド プロシージャでバッチが実行されるときに使用できます。 行数が使用可能な場合は、SQL_BRC_ROLLED_UPビットに応じて、行数をロールアップしたり個別に使用したりできます。  
  
 SQL_BRC_EXPLICIT = 行数がある場合は、 **SQLExecute**または**SQLExecDirect**を呼び出してバッチを直接実行するときに使用できます。 行数が使用可能な場合は、SQL_BRC_ROLLED_UPビットに応じて、行数をロールアップしたり個別に使用したりできます。  
  
 SQL_BATCH_SUPPORT (ODBC 3.0)  
 バッチのドライバーのサポートを列挙する SQLUINTEGER ビットマスク。 サポートされているレベルを決定するには、次のビットマスクを使用します。  
  
 SQL_BS_SELECT_EXPLICIT = ドライバーは、結果セット生成ステートメントを持つことができる明示的なバッチをサポートしています。  
  
 SQL_BS_ROW_COUNT_EXPLICIT = ドライバーは、行数生成ステートメントを持つことができる明示的なバッチをサポートしています。  
  
 SQL_BS_SELECT_PROC = ドライバーは、結果セット生成ステートメントを持つことができる明示的なプロシージャをサポートしています。  
  
 SQL_BS_ROW_COUNT_PROC = ドライバーは、行数生成ステートメントを持つことができる明示的なプロシージャをサポートします。  
  
 SQL_BOOKMARK_PERSISTENCE(ODBC 2.0)  
 ブックマークが永続化される操作を列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクは、ブックマークがどのオプションを保持するかを決定するためにフラグと共に使用されます。  
  
 SQL_BP_CLOSE = ブックマークは、アプリケーションが SQL_CLOSE オプションを指定して**SQLFreeStmt**を呼び出した後、または**SQLCloseCursor が**ステートメントに関連付けられたカーソルをクローズした後に有効です。  
  
 SQL_BP_DELETE = その行が削除された後、その行のブックマークは有効です。  
  
 SQL_BP_DROP = ブックマークは、アプリケーションがステートメントを削除するハンドル*型*のSQL_HANDLE_STMTを使用して**SQLFreeHandle**を呼び出した後に有効です。  
  
 SQL_BP_TRANSACTION = ブックマークは、アプリケーションがトランザクションをコミットまたはロールバックした後に有効です。  
  
 SQL_BP_UPDATE = キー列を含む、その行の任意の列が更新された後に、行のブックマークが有効になります。  
  
 SQL_BP_OTHER_HSTMT = ある文に関連付けられたブックマークを別の文と共に使用できます。 SQL_BP_CLOSEまたはSQL_BP_DROPを指定しない限り、最初のステートメントのカーソルはオープンでなければなりません。  
  
 SQL_CATALOG_LOCATION(ODBC 2.0)  
 修飾表名のカタログの位置を示す SQLUSMALLINT 値。  
  
 SQL_CL_STARTSQL_CL_END  
  
 たとえば、Xbase ドライバは、\EMPDATA\EMP のように、ディレクトリ (カタログ) 名がテーブル名の先頭にあるため、SQL_CL_STARTを返します。Dbf。 ORACLE サーバー ドライバは、カタログがテーブル名の末尾にあるため、SQL_CL_ENDを返しますADMIN.EMP@EMPDATA。  
  
 SQL-92 完全なレベル準拠ドライバーは、常にSQL_CL_START返します。 カタログがデータ ソースでサポートされていない場合は、値 0 が返されます。 カタログがサポートされているかどうかを確認するために、アプリケーションは、SQL_CATALOG_NAME情報の種類を指定して**SQLGetInfo**を呼び出します。  
  
 この*インフォタイプ*は、ODBC 2.0 インフォタイプ SQL_QUALIFIER_LOCATIONから ODBC 3.0*の名前*が変更されました。  
  
 SQL_CATALOG_NAME(ODBC 3.0)  
 サーバーがカタログ名をサポートする場合は "Y" 、サポートされていない場合は "N" という文字列を指定します。  
  
 SQL-92 完全レベル準拠ドライバーは、常に "Y" を返します。  
  
 SQL_CATALOG_NAME_SEPARATOR(ODBC 1.0)  
 文字ストリング: データ・ソースがカタログ名と、その後または前に続く修飾名エレメントの間の区切り文字として定義する文字。  
  
 カタログがデータ ソースでサポートされていない場合は、空の文字列が返されます。 カタログがサポートされているかどうかを確認するために、アプリケーションは、SQL_CATALOG_NAME情報の種類を指定して**SQLGetInfo**を呼び出します。 SQL-92 完全なレベル準拠ドライバーは、常に "." を返します。  
  
 この*インフォタイプ*は ODBC 2.0 インフォタイプ SQL_QUALIFIER_NAME_SEPARATORから ODBC 3.0*の名前*が変更されました。  
  
 SQL_CATALOG_TERM(ODBC 1.0)  
 カタログのデータ ソース ベンダーの名前を含む文字列。たとえば、「データベース」や「ディレクトリ」などです。 この文字列は、大文字、小文字、または混合の大文字と小文字で指定できます。  
  
 カタログがデータ ソースでサポートされていない場合は、空の文字列が返されます。 カタログがサポートされているかどうかを確認するために、アプリケーションは、SQL_CATALOG_NAME情報の種類を指定して**SQLGetInfo**を呼び出します。 SQL-92 完全なレベル準拠ドライバーは、常に"カタログ"を返します。  
  
 この*インフォタイプ*は、ODBC 2.0 インフォタイプSQL_QUALIFIER_TERMから ODBC 3.0*の名前*が変更されました。  
  
 SQL_CATALOG_USAGE(ODBC 2.0)  
 カタログを使用できるステートメントを列挙する SQLUINTEGER ビットマスク。  
  
 カタログを使用できる場所を決定するには、次のビットマスクを使用します。  
  
 SQL_CU_DML_STATEMENTS = カタログは、すべてのデータ操作言語ステートメントでサポートされます: **SELECT、****挿入**、**更新**、**削除**、およびサポートされている場合は **、更新および**位置指定更新および削除ステートメントを選択します。  
  
 SQL_CU_PROCEDURE_INVOCATION = カタログは、ODBC プロシージャー呼び出しステートメントでサポートされます。  
  
 SQL_CU_TABLE_DEFINITION = カタログは、テーブルの作成、 **CREATE** **VIEW**、**テーブルの変更**、**テーブルの削除**、および DROP **VIEW**などのすべての表定義ステートメントでサポートされます。  
  
 SQL_CU_INDEX_DEFINITION = カタログは、すべての索引定義ステートメントでサポートされます: **CREATE INDEX**および**DROP INDEX**。  
  
 SQL_CU_PRIVILEGE_DEFINITION = カタログは **、GRANT**および**REVOKE**のすべての特権定義ステートメントでサポートされます。  
  
 カタログがデータ ソースでサポートされていない場合は、値 0 が返されます。 カタログがサポートされているかどうかを確認するために、アプリケーションは、SQL_CATALOG_NAME情報の種類を指定して**SQLGetInfo**を呼び出します。 SQL-92 完全レベル準拠ドライバーは、常にこれらのビットセットのビットマスクを返します。  
  
 この*インフォタイプ*は、ODBC 2.0 インフォタイプSQL_QUALIFIER_USAGEから ODBC 3.0*の名前*が変更されました。  
  
 SQL_COLLATION_SEQ(ODBC 3.0)  
 照合順序の名前。 これは、このサーバーのデフォルト文字セット (例えば、「ISO 8859-1」や EBCDIC) のデフォルトの照合順序の名前を示す文字ストリングです。 これが不明な場合は、空の文字列が返されます。 SQL-92 完全なレベル準拠ドライバーは、常に空でない文字列を返します。  
  
 SQL_COLUMN_ALIAS(ODBC 2.0)  
 データ ソースが列の別名をサポートしている場合は、"Y" という文字列を指定します。それ以外の場合は"N"。  
  
 列別名は、AS 節を使用して選択リスト内の列に対して指定できる代替名です。 SQL-92 エントリ レベル準拠ドライバーは常に "Y" を返します。  
  
 SQL_CONCAT_NULL_BEHAVIOR(ODBC 1.0)  
 データ ソースが NULL 値を持たない文字型のデータ型列の連結を処理する方法を示す SQLUSMALLINT 値。  
  
 SQL_CB_NULL = 結果は NULL 値です。  
  
 SQL_CB_NON_NULL = 結果は NULL 以外の値を持つ列または列を連結したものです。  
  
 SQL-92 エントリ レベル準拠ドライバーは常にSQL_CB_NULL返します。  
  
 SQL_CONVERT_BIGINTSQL_CONVERT_BINARYSQL_CONVERT_BIT SQL_CONVERT_CHAR SQL_CONVERT_GUIDSQL_CONVERT_DATESQL_CONVERT_DECIMALSQL_CONVERT_DOUBLESQL_CONVERT_FLOATSQL_CONVERT_INTEGERSQL_CONVERT_INTERVAL_YEAR_MONTHSQL_CONVERT_INTERVAL_DAY_TIMESQL_CONVERT_LONGVARBINARYSQL_CONVERT_LONGVARCHARSQL_CONVERT_NUMERICSQL_CONVERT_REALSQL_CONVERT_SMALLINTSQL_CONVERT_TIMESQL_CONVERT_TIMESTAMPSQL_CONVERT_TINYINTSQL_CONVERT_VARBINARYSQL_CONVERT_VARCHAR (ODBC 1.0)  
 SQLSqlINTEGER ビットマスク。 ビットマスクは、データ ソースが*InfoType*で指定した型のデータに対する**CONVERT**スカラー関数を使用してサポートする変換を示します。 ビットマスクが 0 の場合、データ ソースは、同じデータ型への変換を含む、名前付きの型のデータからの変換をサポートしません。  
  
 たとえば、データ ソースがSQL_INTEGERデータのSQL_BIGINTデータ型への変換をサポートしているかどうかを判断するには、アプリケーションは SQL_CONVERT_INTEGERの*InfoType*を指定して**SQLGetInfo**を呼び出します。 アプリケーションは、返されたビットマスクとSQL_CVT_BIGINTを使用して**AND**演算を実行します。 結果の値が 0 以外の場合は、変換がサポートされます。  
  
 サポートされている変換を決定するには、次のビットマスクを使用します。  
  
 SQL_CVT_BIGINT (ODBC 1.0) SQL_CVT_BINARY (ODBC 1.0) SQL_CVT_BIT (ODBC 1.0) SQL_CVT_GUID (ODBC 3.5) SQL_CVT_CHAR (ODBC 1.0) SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DECIMAL SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DATE (ODBC 1.0)SQL_CVT_DOUBLE (ODBC 1.0)SQL_CVT_FLOAT (ODBC 1.0)SQL_CVT_INTEGER (ODBC 1.0)SQL_CVT_INTERVAL_YEAR_MONTH (ODBC 3.0)SQL_CVT_INTERVAL_DAY_TIME (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.SQL_CVT_LONGVARCHAR 0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.SQL_ 0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_GUID (ODBC 1.0) SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DOUBLE (ODBC 1.0)SQL_CVT_FLOAT (ODBC 1.0)SQL_CVT_INTEGER (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)SQL_CVT_LONGVARBINARY (ODBC 1.0)(ODBC 1.0)、odbc 1.0 (ODBC 1 SQL_CVT_NUMERIC.0)、odbc 1.0)SQL_CVT_DATE (ODBC 1.0) SQL_CVT_DOUBLE (ODBC 1.0) SQL_CVT_FLOAT (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) (ODBC 1.0) (ODBC 1.0ODBC 1.0) SQL_CVT_SMALLINT (ODBC 1.0) SQL_CVT_TIME (ODBC 1.0) SQL_CVT_TIMESTAMP (ODBC 1.0) SQL_CVT_TINYINT (ODBC 1.0) SQL_CVT_VARBINARY (ODBC 1.0) SQL_CVT_VARCHAR (ODBC 1.0) (ODBC 1.0) をCVT_REALします。  
  
 SQL_CONVERT_FUNCTIONS(ODBC 1.0)  
 ドライバーと関連データ ソースでサポートされているスカラー変換関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされている変換関数を決定するには、次のビットマスクを使用します。  
  
 SQL_FN_CVT_CASTSQL_FN_CVT_CONVERT  
  
 SQL_CORRELATION_NAME(ODBC 1.0)  
 テーブルの相関名がサポートされるかどうかを示す SQLUSMALLINT 値。  
  
 SQL_CN_NONE = 相関名はサポートされていません。  
  
 SQL_CN_DIFFERENT = 相関名はサポートされますが、それらが表すテーブルの名前とは異なる名前でなければなりません。  
  
 SQL_CN_ANY = 相関名はサポートされており、任意の有効なユーザー定義名を指定できます。  
  
 SQL-92 エントリ レベル準拠ドライバーは常にSQL_CN_ANY返します。  
  
 SQL_CREATE_ASSERTION(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**CREATE アサーション**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_CA_CREATE_ASSERTION  
  
 次のビットは、制約属性を明示的に指定する機能がサポートされている場合に、サポートされている制約属性を指定します (SQL_ALTER_TABLEおよびSQL_CREATE_TABLE情報の種類を参照)。  
  
 SQL_CA_CONSTRAINT_INITIALLY_DEFERREDSQL_CA_CONSTRAINT_INITIALLY_IMMEDIATESQL_CA_CONSTRAINT_DEFERRABLESQL_CA_CONSTRAINT_NON_DEFERRABLE  
  
 SQL-92 完全なレベル準拠ドライバーは、サポートされているとおり、常にこれらのオプションのすべてを返します。 戻り値 "0" は **、CREATE アサーション**ステートメントがサポートされないことを意味します。  
  
 SQL_CREATE_CHARACTER_SET(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**CREATE CHARACTER SET**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_CCS_CREATE_CHARACTER_SETSQL_CCS_COLLATE_CLAUSESQL_CCS_LIMITED_COLLATION  
  
 SQL-92 完全なレベル準拠ドライバーは、サポートされているとおり、常にこれらのオプションのすべてを返します。 戻り値 "0" は **、CREATE CHARACTER SET**ステートメントがサポートされないことを意味します。  
  
 SQL_CREATE_COLLATION(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**CREATE COLLATION**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクを使用して、サポートされる句を決定します。  
  
 SQL_CCOL_CREATE_COLLATION  
  
 SQL-92 完全なレベル準拠ドライバーは、サポートされているとおりに常にこのオプションを返します。 "0" の戻り値は **、CREATE COLLATION**ステートメントがサポートされないことを意味します。  
  
 SQL_CREATE_DOMAIN(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**CREATE DOMAIN**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_CDO_CREATE_DOMAIN = CREATE DOMAIN ステートメントがサポートされています (中間レベル)。  
  
 SQL_CDO_CONSTRAINT_NAME_DEFINITION \<= 制約名定義>は、名前付けドメインの制約 (中間レベル) でサポートされています。  
  
 次のビットは、列の制約を作成する機能を指定します:SQL_CDO_DEFAULT = ドメイン制約の指定がサポートされています (中間レベル)SQL_CDO_CONSTRAINT = ドメインのデフォルトの指定がサポートされています (中間レベル)SQL_CDO_COLLATION = ドメイン照合の指定がサポートされています (フルレベル)  
  
 次のビットは、ドメイン制約の指定がサポートされている場合 (SQL_CDO_DEFAULTが設定されている場合)、サポートされる制約属性を指定します。  
  
 SQL_CDO_CONSTRAINT_INITIALLY_DEFERRED (フルレベル)SQL_CDO_CONSTRAINT_INITIALLY_IMMEDIATE(フルレベル)SQL_CDO_CONSTRAINT_DEFERRABLE(フルレベル)SQL_CDO_CONSTRAINT_NON_DEFERRABLE(フルレベル)  
  
 "0" の戻り値は **、CREATE DOMAIN**ステートメントがサポートされないことを意味します。  
  
 SQL_CREATE_SCHEMA(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている CREATE **SCHEMA**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_CS_CREATE_SCHEMASQL_CS_AUTHORIZATIONSQL_CS_DEFAULT_CHARACTER_SET  
  
 SQL-92 中間レベル準拠ドライバーは、サポートされているSQL_CS_CREATE_SCHEMAとSQL_CS_AUTHORIZATIONオプションを常に返します。 これらのステートメントは、SQL-92 のエントリ レベルでもサポートされている必要がありますが、SQL ステートメントとしてはサポートされません。 SQL-92 完全なレベル準拠ドライバーは、サポートされているとおり、常にこれらのオプションのすべてを返します。  
  
 SQL_CREATE_TABLE(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている CREATE **TABLE**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの隣に括弧で囲んで示されています。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_CT_CREATE_TABLE = CREATE TABLE ステートメントがサポートされています。 (エントリーレベル)  
  
 SQL_CT_TABLE_CONSTRAINT = テーブル制約の指定がサポートされています (FIPS 移行レベル)  
  
 SQL_CT_CONSTRAINT_NAME_DEFINITION =\<制約名定義>句は、列制約およびテーブル制約の命名に対してサポートされています (中間レベル)  
  
 次のビットは、一時テーブルを作成する機能を指定します。  
  
 SQL_CT_COMMIT_PRESERVE = 削除された行はコミット時に保持されます。 (フルレベル)SQL_CT_COMMIT_DELETE = 削除された行はコミット時に削除されます。 (フルレベル)SQL_CT_GLOBAL_TEMPORARY = グローバル一時テーブルを作成できます。 (フルレベル)SQL_CT_LOCAL_TEMPORARY = ローカル一時テーブルを作成できます。 (フルレベル)  
  
 次のビットは、列制約を作成する機能を指定します。  
  
 SQL_CT_COLUMN_CONSTRAINT = 列制約の指定がサポートされています (FIPS 移行レベル) SQL_CT_COLUMN_DEFAULT = 列のデフォルトの指定がサポートされています (FIPS 移行レベル)SQL_CT_COLUMN_COLLATION = 列照合の指定がサポートされています (フルレベル)  
  
 次のビットは、列制約またはテーブル制約の指定がサポートされている場合に、サポートされる制約属性を指定します。  
  
 SQL_CT_CONSTRAINT_INITIALLY_DEFERRED (フルレベル)SQL_CT_CONSTRAINT_INITIALLY_IMMEDIATE(フルレベル)SQL_CT_CONSTRAINT_DEFERRABLE(フルレベル)SQL_CT_CONSTRAINT_NON_DEFERRABLE(フルレベル)  
  
 SQL_CREATE_TRANSLATION(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**CREATE 変換**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクを使用して、サポートされる句を決定します。  
  
 SQL_CTR_CREATE_TRANSLATION  
  
 SQL-92 完全なレベル準拠ドライバーは、サポートされているとおり、常にこれらのオプションを返します。 戻り値 "0" は **、CREATE TRANSLATION**ステートメントがサポートされないことを意味します。  
  
 SQL_CREATE_VIEW(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**CREATE VIEW**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_CV_CREATE_VIEWSQL_CV_CHECK_OPTIONSQL_CV_CASCADEDSQL_CV_LOCAL  
  
 戻り値 "0" は **、CREATE VIEW**ステートメントがサポートされないことを意味します。  
  
 SQL-92 エントリ レベル準拠ドライバーは、常にサポートされているとおりにSQL_CV_CREATE_VIEWとSQL_CV_CHECK_OPTIONのオプションを返します。  
  
 SQL-92 完全なレベル準拠ドライバーは、サポートされているとおり、常にこれらのオプションのすべてを返します。  
  
 SQL_CURSOR_COMMIT_BEHAVIOR(ODBC 1.0)  
 **COMMIT**操作がデータ・ソース内のカーソルおよび準備済みステートメントに与える影響 (トランザクションをコミットするときのデータ・ソースの動作) を示す SQLUSMALLINT 値。  
  
 この属性の値は、次の設定の現在の状態を反映SQL_COPT_SS_PRESERVE_CURSORS。  
  
 SQL_CB_DELETE = カーソルをクローズし、準備済みステートメントを削除します。 カーソルを再び使用するには、アプリケーションは、ステートメントを再準備し、再実行する必要があります。  
  
 SQL_CB_CLOSE = カーソルを閉じます。 準備済みステートメントの場合、アプリケーションは **、SQLPrepare**を再度呼び出すことなく、ステートメントで**SQLExecute**を呼び出すことができます。 SQL ODBC ドライバのデフォルトはSQL_CB_CLOSEです。 つまり、トランザクションをコミットすると、SQL ODBC ドライバがカーソルを閉じます。  
  
 SQL_CB_PRESERVE = **COMMIT**操作の前と同じ位置にあるカーソルを保持します。 アプリケーションは、データのフェッチを続行するか、またはカーソルをクローズして、再準備せずにステートメントを再実行できます。  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR(ODBC 1.0)  
 **ROLLBACK**操作がデータ・ソース内のカーソルおよび準備済みステートメントに与える影響を示す SQLUSMALLINT 値。  
  
 SQL_CB_DELETE = カーソルをクローズし、準備済みステートメントを削除します。 カーソルを再び使用するには、アプリケーションは、ステートメントを再準備し、再実行する必要があります。  
  
 SQL_CB_CLOSE = カーソルを閉じます。 準備済みステートメントの場合、アプリケーションは **、SQLPrepare**を再度呼び出すことなく、ステートメントで**SQLExecute**を呼び出すことができます。  
  
 SQL_CB_PRESERVE = **ROLLBACK**操作の前と同じ位置にあるカーソルを保持します。 アプリケーションは、データをフェッチし続けるか、またはカーソルをクローズして、再準備せずにステートメントを再実行できます。  
  
 SQL_CURSOR_SENSITIVITY (ODBC 3.0)  
 カーソルの秘密度のサポートを示す SQLUINTEGER 値。  
  
 SQL_INSENSITIVE = ステートメント・ハンドルのすべてのカーソルは、同じトランザクション内の他のカーソルによって行われた変更を反映せずに結果セットを表示します。  
  
 SQL_UNSPECIFIED = ステートメント・ハンドル上のカーソルが、同じトランザクション内の別のカーソルによって結果セットに加えられた変更を可視にするかどうかは未規定です。 ステートメント ハンドル上のカーソルは、表示されない、一部、またはすべての変更を行うことができます。  
  
 SQL_SENSITIVE = カーソルは、同じトランザクション内の他のカーソルによって行われた変更に影響を与えます。  
  
 SQL-92 エントリ レベル準拠ドライバーは、サポートされているSQL_UNSPECIFIEDオプションを常に返します。  
  
 SQL-92 完全なレベル準拠ドライバーは、サポートされているSQL_INSENSITIVEオプションを常に返します。  
  
 SQL_DATA_SOURCE_NAME(ODBC 1.0)  
 接続中に使用されたデータ ソース名を持つ文字列。 アプリケーションが**SQLConnect**と呼ばれている場合、これは*szDSN*引数の値です。 アプリケーションが**SQLDriverConnect**または**SQLBrowseConnect**と呼ばれる場合、これはドライバーに渡される接続文字列の DSN キーワードの値です。 接続文字列に**DSN**キーワードが含まれていない場合 **(DRIVER**キーワードが含まれている場合など)、これは空の文字列です。  
  
 SQL_DATA_SOURCE_READ_ONLY(ODBC 1.0)  
 文字列。 データ ソースが読み取り専用モードに設定されている場合は "Y" 、それ以外の場合は "N" に設定します。  
  
 この特性は、データ ソース自体にのみ関連します。データ ソースへのアクセスを有効にするドライバーの特性ではありません。 読み取り/書き込み可能なドライバーは、読み取り専用のデータ ソースで使用できます。 ドライバーが読み取り専用の場合、そのすべてのデータ ソースは読み取り専用である必要があり、SQL_DATA_SOURCE_READ_ONLY返す必要があります。  
  
 SQL_DATABASE_NAME(ODBC 1.0)  
 データ ソースが "database" という名前のオブジェクトを定義している場合、現在使用中のデータベースの名前を持つ文字列。  
  
> [!NOTE]
>  ODBC 3 *.x*では、この*インフォタイプ*に返される値は、SQL_ATTR_CURRENT_CATALOGの*属性*引数を指定して**SQLGetConnectAttr**を呼び出すことによっても返すことができます。  
  
 SQL_DATETIME_LITERALS(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 の日時リテラルを列挙する SQLUINTEGER ビットマスク。 これらは、SQL-92 仕様に記載されている日時リテラルであり、ODBC で定義された日時リテラルのエスケープ句とは別のリテラルであることに注意してください。 ODBC 日時リテラルエスケープ句の詳細については、「[日付、時刻、およびタイムスタンプリテラル](../../../odbc/reference/develop-app/date-time-and-timestamp-literals.md)」を参照してください。  
  
 FIPS 移行レベル準拠ドライバーは、常に、次のリストのビットのビットマスクに"1"値を返します。 値 "0" は、SQL-92 の日時リテラルがサポートされないことを意味します。  
  
 サポートされるリテラルを判別するには、次のビットマスクを使用します。  
  
 SQL_DL_SQL92_DATESQL_DL_SQL92_TIMESQL_DL_SQL92_TIMESTAMPSQL_DL_SQL92_INTERVAL_YEARSQL_DL_SQL92_INTERVAL_MONTHSQL_DL_SQL92_INTERVAL_DAYSQL_DL_SQL92_INTERVAL_HOURSQL_DL_SQL92_INTERVAL_MINUTESQL_DL_SQL92_INTERVAL_SECONDSQL_DL_SQL92_INTERVAL_YEAR_TO_MONTHSQL_DL_SQL92_INTERVAL_DAY_TO_HOUR  
  
 SQL_DL_SQL92_INTERVAL_DAY_TO_MINUTESQL_DL_SQL92_INTERVAL_DAY_TO_SECONDSQL_DL_SQL92_INTERVAL_HOUR_TO_MINUTESQL_DL_SQL92_INTERVAL_HOUR_TO_SECONDSQL_DL_SQL92_INTERVAL_MINUTE_TO_SECOND  
  
 SQL_DBMS_NAME(ODBC 1.0)  
 ドライバーがアクセスする DBMS 製品の名前を含む文字列。  
  
 SQL_DBMS_VER(ODBC 1.0)  
 ドライバーがアクセスする DBMS 製品のバージョンを示す文字列。 バージョンは ##.###############という形式で、最初の 2 桁はメジャー バージョン、次の 2 桁はマイナー バージョン、最後の 4 桁はリリース バージョンです。 ドライバーは、この形式で DBMS 製品のバージョンをレンダリングする必要がありますが、DBMS 製品固有のバージョンを追加することもできます。 たとえば、"04.01.0000 Rdb 4.1" とします。  
  
 SQL_DDL_INDEX(ODBC 3.0)  
 インデックスの作成と削除のサポートを示す SQLUINTEGER 値:  
  
 SQL_DI_CREATE_INDEXSQL_DI_DROP_INDEX  
  
 SQL_DEFAULT_TXN_ISOLATION(ODBC 1.0)  
 ドライバーまたはデータ ソースでサポートされる既定のトランザクション分離レベルを示す SQLUINTEGER 値。 トランザクション分離レベルを定義するには、次の用語を使用します。  
  
 **汚い読み取り**トランザクション 1 は行を変更します。 トランザクション 2 は、トランザクション 1 が変更をコミットする前に変更された行を読み取ります。 トランザクション 1 が変更をロールバックすると、トランザクション 2 は、存在しなかった行を読み取ります。  
  
 **繰り返し不可能な読み取り**トランザクション 1 は行を読み取ります。 トランザクション 2 は、その行を更新または削除し、この変更をコミットします。 トランザクション 1 が行を再読み取りしようとすると、別の行値を受け取るか、行が削除されたことを検出します。  
  
 **ファントム**トランザクション 1 は、いくつかの検索条件を満たす行のセットを読み取ります。 トランザクション 2 は、検索条件に一致する 1 つ以上の行を (挿入または更新を通じて) 生成します。 トランザクション 1 が、行を読み取るステートメントを再実行すると、異なる行セットを受け取ります。  
  
 データ ソースがトランザクションをサポートしている場合、ドライバーは、次のビットマスクのいずれかを返します。  
  
 SQL_TXN_READ_UNCOMMITTED = ダーティ読み取り、反復不能読み取り、およびファントムが可能です。  
  
 SQL_TXN_READ_COMMITTED = ダーティ読み取りはできません。 反復不能読み取りとファントムが可能です。  
  
 SQL_TXN_REPEATABLE_READ = ダーティ読み取りと繰り返し不可能な読み取りはできません。 ファントムが可能です。  
  
 SQL_TXN_SERIALIZABLE = トランザクションはシリアル化可能です。 シリアル化可能なトランザクションでは、ダーティ読み取り、繰り返し不可能な読み取り、またはファントムは許可されません。  
  
 SQL_DESCRIBE_PARAMETER(ODBC 3.0)  
 パラメータを記述できる場合は"Y"という文字列。「N」でなければ。  
  
 SQL-92 完全レベル準拠ドライバーは **、DESCRIBE INPUT**ステートメントをサポートするため、通常は "Y" を返します。 これは基になる SQL サポートを直接指定するわけではないので、SQL-92 の完全なレベル準拠ドライバーでも、パラメーターの記述はサポートされない場合があります。  
  
 SQL_DM_VER(ODBC 3.0)  
 ドライバー マネージャーのバージョンを含む文字列。 バージョンは###############という形式です。  
  
 2 桁の最初のセットは、定数SQL_SPEC_MAJORで指定された主要な ODBC バージョンです。  
  
 2 桁の 2 番目のセットは、定数 SQL_SPEC_MINORで指定されたマイナー ODBC バージョンです。  
  
 4 桁の 3 番目のセットは、ドライバー マネージャーのメジャー ビルド番号です。  
  
 4 桁の最後のセットは、ドライバー マネージャーのマイナー ビルド番号です。  
  
 Windows 7 ドライバー マネージャーのバージョンは 03.80 です。 Windows 8 ドライバー マネージャーのバージョンは 03.81 です。  
  
 SQL_DRIVER_AWARE_POOLING_SUPPORTED (ODBC 3.8)  
 ドライバー対応のプールをサポートするかどうか示す SQLUINTEGER 値。 (詳細については、「[ドライバ対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)」を参照してください。  
  
 SQL_DRIVER_AWARE_POOLING_CAPABLEは、ドライバーがドライバー対応のプールメカニズムをサポートできることを示します。  
  
 SQL_DRIVER_AWARE_POOLING_NOT_CAPABLEは、ドライバーがドライバー対応のプールメカニズムをサポートできないことを示します。  
  
 ドライバーはSQL_DRIVER_AWARE_POOLING_SUPPORTEDを実装する必要はありませんし、ドライバー マネージャーは、ドライバーの戻り値を受け入れません。  
  
 SQL_DRIVER_HDBCSQL_DRIVER_HENV(ODBC 1.0)  
 SQLULEN 値、ドライバーの環境ハンドルまたは接続ハンドルは、引数*InfoType*によって決定されます。  
  
 これらの情報の種類は、ドライバー マネージャーだけで実装されます。  
  
 SQL_DRIVER_HDESC(ODBC 3.0)  
 SQLULEN 値は、ドライバー マネージャーの記述子ハンドルによって決定されるドライバーの記述子ハンドル、アプリケーションから\**InfoValuePtr*で入力に渡す必要があります。 この場合 *、InfoValuePtr*は入力引数と出力引数の両方です。 \* *InfoValuePtr*で渡される入力記述子ハンドルは *、ConnectionHandle*で明示的または暗黙的に割り当てられている必要があります。  
  
 アプリケーションは、出力でハンドルが上書きされないように、この情報の種類を**使用して SQLGetInfo**を呼び出す前に、ドライバー マネージャーの記述子ハンドルのコピーを作成する必要があります。  
  
 この情報の種類は、ドライバー マネージャーだけで実装されます。  
  
 SQL_DRIVER_HLIB(ODBC 2.0)  
 SQLULEN 値、読み込みライブラリからの*ヒンスト*は、Microsoft Windows オペレーティング システム、または別のオペレーティング システム上で同等のドライバー DLL を読み込んだときにドライバー マネージャーに返されます。 このハンドルは、 **SQLGetInfo**の呼び出しで指定された接続ハンドルに対してのみ有効です。  
  
 この情報の種類は、ドライバー マネージャーだけで実装されます。  
  
 SQL_DRIVER_HSTMT(ODBC 1.0)  
 SQLULEN 値は、ドライバー マネージャーステートメント ハンドルによって決定されるドライバーのステートメント ハンドル、アプリケーションから\**InfoValuePtr*で入力に渡す必要があります。 この場合 *、InfoValuePtr*は入力引数と出力引数の両方です。 \* *InfoValuePtr*で渡された入力ステートメント ハンドルは、引数*ConnectionHandle*に割り当てられている必要があります。  
  
 アプリケーションは、出力でハンドルが上書きされないように、この情報の種類を**使用して SQLGetInfo**を呼び出す前に、ドライバー マネージャーのステートメント ハンドルのコピーを作成する必要があります。  
  
 この情報の種類は、ドライバー マネージャーだけで実装されます。  
  
 SQL_DRIVER_NAME(ODBC 1.0)  
 データ ソースへのアクセスに使用するドライバーのファイル名を含む文字列。  
  
 SQL_DRIVER_ODBC_VER(ODBC 2.0)  
 ドライバーがサポートする ODBC のバージョンを含む文字列。 バージョンは ##.##という形式で、最初の 2 桁はメジャー バージョンで、次の 2 桁はマイナー バージョンです。 SQL_SPEC_MAJORとSQL_SPEC_MINORは、メジャーバージョン番号とマイナー バージョン番号を定義します。 このマニュアルで説明する ODBC のバージョンでは、これらは 3 と 0 であり、ドライバーは "03.00" を返す必要があります。  
  
 ODBC ドライバー マネージャーは、既存のアプリケーションの下位互換性を維持するために SQLGetInfo(SQL_DRIVER_ODBC_VER) の戻り値を変更しません。 ドライバーは、返される値を指定します。 ただし、C データ型の機能拡張をサポートするドライバーは、アプリケーションが 3.8 に設定する**SQL_ATTR_ODBC_VERSIONを設定する SQLSetEnvAttr**を呼び出すときに 3.8 (またはそれ以降) を返す必要があります。 詳細については[、「ODBC での C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)」を参照してください。  
  
 SQL_DRIVER_VER(ODBC 1.0)  
 ドライバーのバージョンとオプションで、ドライバーの説明を含む文字列。 バージョンは少なくとも ##.###########という形式で、最初の 2 桁はメジャー バージョン、次の 2 桁はマイナー バージョン、最後の 4 桁はリリース バージョンです。  
  
 SQL_DROP_ASSERTION(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**DROP アサーション**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクを使用して、サポートされる句を決定します。  
  
 SQL_DA_DROP_ASSERTION  
  
 SQL-92 完全なレベル準拠ドライバーは、サポートされているとおりに常にこのオプションを返します。  
  
 SQL_DROP_CHARACTER_SET(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**DROP CHARACTER SET**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクを使用して、サポートされる句を決定します。  
  
 SQL_DCS_DROP_CHARACTER_SET  
  
 SQL-92 完全なレベル準拠ドライバーは、サポートされているとおりに常にこのオプションを返します。  
  
 SQL_DROP_COLLATION(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている **、DROP COLLATION**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクを使用して、サポートされる句を決定します。  
  
 SQL_DC_DROP_COLLATION  
  
 SQL-92 完全なレベル準拠ドライバーは、サポートされているとおりに常にこのオプションを返します。  
  
 SQL_DROP_DOMAIN(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**DROP DOMAIN**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_DD_DROP_DOMAINSQL_DD_CASCADESQL_DD_RESTRICT  
  
 SQL-92 中間レベル準拠ドライバーは、常にサポートされているこれらのオプションのすべてを返します。  
  
 SQL_DROP_SCHEMA(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**DROP SCHEMA**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_DS_DROP_SCHEMASQL_DS_CASCADESQL_DS_RESTRICT  
  
 SQL-92 中間レベル準拠ドライバーは、常にサポートされているこれらのオプションのすべてを返します。  
  
 SQL_DROP_TABLE(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**DROP TABLE**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_DT_DROP_TABLESQL_DT_CASCADESQL_DT_RESTRICT  
  
 FIPS 移行レベル準拠ドライバーは、常にサポートされているこれらのオプションのすべてを返します。  
  
 SQL_DROP_TRANSLATION(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**DROP 変換**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクを使用して、サポートされる句を決定します。  
  
 SQL_DTR_DROP_TRANSLATION  
  
 SQL-92 完全なレベル準拠ドライバーは、サポートされているとおりに常にこのオプションを返します。  
  
 SQL_DROP_VIEW(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**DROP VIEW**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_DV_DROP_VIEWSQL_DV_CASCADESQL_DV_RESTRICT  
  
 FIPS 移行レベル準拠ドライバーは、常にサポートされているこれらのオプションのすべてを返します。  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 ドライバーでサポートされている動的カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の最初のサブセットが含まれています。2 番目のサブセットについては、「SQL_DYNAMIC_CURSOR_ATTRIBUTES2」を参照してください。  
  
 サポートされる属性を決定するには、次のビットマスクを使用します。  
  
 SQL_CA1_NEXT = SQL_FETCH_NEXTの*フェッチオリエンテーション*引数は、カーソルが動的カーソルの場合に**SQLFetchScroll**の呼び出しでサポートされます。  
  
 SQL_CA1_ABSOLUTE = SQL_FETCH_FIRST、SQL_FETCH_LAST、およびSQL_FETCH_ABSOLUTEの*FetchOrientation*引数は、カーソルが動的カーソルの場合に**SQLFetchScroll**の呼び出しでサポートされます。 (フェッチされる行セットは、現在のカーソル位置とは無関係です。  
  
 SQL_CA1_RELATIVE = SQL_FETCH_PRIORおよびSQL_FETCH_RELATIVEの*FetchOrientation*引数は、カーソルが動的カーソルの場合に**SQLFetchScroll**の呼び出しでサポートされます。 (取り出される行セットは、現在のカーソル位置によって異なります。 前方専用カーソルでは、SQL_FETCH_NEXTだけがサポートされるため、これはSQL_FETCH_NEXTから分離されています。  
  
 SQL_CA1_BOOKMARK = カーソルが動的カーソルの場合 **、SQLFetchScroll**の呼び出しでは、SQL_FETCH_BOOKMARKの*フェッチオリエンテーション*引数がサポートされます。  
  
 SQL_CA1_LOCK_EXCLUSIVE = SQL_LOCK_EXCLUSIVEの*LockType*引数は、カーソルが動的カーソルの場合に**SQLSetPos**の呼び出しでサポートされます。  
  
 SQL_CA1_LOCK_NO_CHANGE = SQL_LOCK_NO_CHANGEの*LockType*引数は、カーソルが動的カーソルの場合に**SQLSetPos**の呼び出しでサポートされます。  
  
 SQL_CA1_LOCK_UNLOCK = カーソルが動的カーソルの場合、SQL_LOCK_UNLOCKの*LockType*引数は**SQLSetPos**の呼び出しでサポートされます。  
  
 SQL_CA1_POS_POSITION = カーソルが動的カーソルの場合 **、SQLSetPos**の呼び出しでは、SQL_POSITIONの*操作*引数がサポートされます。  
  
 SQL_CA1_POS_UPDATE = SQL_UPDATE の*操作*引数は、カーソルが動的カーソルの場合に**SQLSetPos**の呼び出しでサポートされます。  
  
 SQL_CA1_POS_DELETE = カーソルが動的カーソルの場合 **、SQLSetPos**の呼び出しでは、SQL_DELETEの*操作*引数がサポートされます。  
  
 SQL_CA1_POS_REFRESH = カーソルが動的カーソルの場合 **、sqlSetPos**の呼び出しでは、SQL_REFRESHの*操作*引数がサポートされます。  
  
 SQL_CA1_POSITIONED_UPDATE = カーソルが動的カーソルの場合は、SQL ステートメントの現在の UPDATE がサポートされます。 (SQL-92 エントリ レベル準拠ドライバーは、常にサポートされているとして、このオプションを返します。  
  
 SQL_CA1_POSITIONED_DELETE = カーソルが動的カーソルである場合は、SQL ステートメントの DELETE WHERE CURRENT OF ステートメントがサポートされます。 (SQL-92 エントリ レベル準拠ドライバーは、常にサポートされているとして、このオプションを返します。  
  
 SQL_CA1_SELECT_FOR_UPDATE = カーソルが動的カーソルの場合は、SELECT FOR UPDATE SQL ステートメントがサポートされます。 (SQL-92 エントリ レベル準拠ドライバーは、常にサポートされているとして、このオプションを返します。  
  
 SQL_CA1_BULK_ADD = SQL_ADD の*操作*引数は、カーソルが動的カーソルの場合に**SQLBulkOperations**の呼び出しでサポートされます。  
  
 SQL_CA1_BULK_UPDATE_BY_BOOKMARK = SQL_UPDATE_BY_BOOKMARK の*操作*引数は、カーソルが動的カーソルの場合に**SQLBulkOperations**の呼び出しでサポートされます。  
  
 SQL_CA1_BULK_DELETE_BY_BOOKMARK = SQL_DELETE_BY_BOOKMARK の*操作*引数は、カーソルが動的カーソルの場合に**SQLBulkOperations**の呼び出しでサポートされます。  
  
 SQL_CA1_BULK_FETCH_BY_BOOKMARK = SQL_FETCH_BY_BOOKMARK の*操作*引数は、カーソルが動的カーソルの場合に**SQLBulkOperations**の呼び出しでサポートされます。  
  
 SQL-92 中間レベル適合ドライバーは、通常、SQL_CA1_NEXT、SQL_CA1_ABSOLUTE、およびSQL_CA1_RELATIVEオプションをサポートするために、組み込みの SQL FETCH ステートメントを介してスクロール可能なカーソルをサポートするため、サポートされているとして返します。 これは基になる SQL サポートを直接決定しないため、ただし、SQL-92 中間レベル準拠ドライバーであっても、スクロール可能なカーソルはサポートされない場合があります。  
  
 SQL_DYNAMIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 ドライバーでサポートされている動的カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の 2 番目のサブセットが含まれています。最初のサブセットについては、「SQL_DYNAMIC_CURSOR_ATTRIBUTES1」を参照してください。  
  
 サポートされる属性を決定するには、次のビットマスクを使用します。  
  
 SQL_CA2_READ_ONLY_CONCURRENCY = 更新が許可されていない読み取り専用の動的カーソルがサポートされています。 (SQL_ATTR_CONCURRENCYステートメント属性は、動的カーソルにSQL_CONCUR_READ_ONLYできます。  
  
 SQL_CA2_LOCK_CONCURRENCY = 行を更新できる状態にする場合に十分な最低レベルのロックを使用する動的カーソルがサポートされます。 (SQL_ATTR_CONCURRENCY ステートメント属性は、動的カーソルにSQL_CONCUR_LOCKできます。これらのロックは、SQL_ATTR_TXN_ISOLATION接続属性によって設定されたトランザクション分離レベルと一致している必要があります。  
  
 SQL_CA2_OPT_ROWVER_CONCURRENCY = 行バージョンを比較するオプティミスティック同時実行制御を使用する動的カーソルがサポートされています。 (SQL_ATTR_CONCURRENCYステートメント属性は、動的カーソルにSQL_CONCUR_ROWVERできます。  
  
 SQL_CA2_OPT_VALUES_CONCURRENCY = 値を比較するオプティミスティック同時実行制御を使用する動的カーソルがサポートされています。 (SQL_ATTR_CONCURRENCYステートメント属性は、動的カーソルにSQL_CONCUR_VALUESできます。  
  
 SQL_CA2_SENSITIVITY_ADDITIONS = 追加された行は動的カーソルから見えます。カーソルは、それらの行までスクロールできます。 (これらの行がカーソルに追加される場所は、ドライバーに依存します)。  
  
 SQL_CA2_SENSITIVITY_DELETIONS = 削除された行は動的カーソルからは使用できなくなり、結果セットに「穴」を残しません。削除された行から動的カーソルをスクロールした後、その行に戻ることはできません。  
  
 SQL_CA2_SENSITIVITY_UPDATES = 行の更新は動的カーソルから参照できます。動的カーソルがからスクロールして更新された行に戻る場合、カーソルによって返されるデータは更新されたデータであり、元のデータではありません。  
  
 SQL_CA2_MAX_ROWS_SELECT = SQL_ATTR_MAX_ROWS ステートメント属性は、カーソルが動的カーソルの場合に**SELECT**ステートメントに影響を与えます。  
  
 SQL_CA2_MAX_ROWS_INSERT = SQL_ATTR_MAX_ROWS ステートメント属性は、カーソルが動的カーソルの場合に**INSERT**ステートメントに影響します。  
  
 SQL_CA2_MAX_ROWS_DELETE = SQL_ATTR_MAX_ROWS ステートメント属性は、カーソルが動的カーソルの場合に**DELETE**ステートメントに影響します。  
  
 SQL_CA2_MAX_ROWS_UPDATE = SQL_ATTR_MAX_ROWS ステートメント属性は、カーソルが動的カーソルである場合に**UPDATE**ステートメントに影響します。  
  
 SQL_CA2_MAX_ROWS_CATALOG = カーソルが動的カーソルである場合、SQL_ATTR_MAX_ROWSステートメント属性は**CATALOG**結果セットに影響します。  
  
 SQL_CA2_MAX_ROWS_AFFECTS_ALL = SQL_ATTR_MAX_ROWS ステートメント属性は、カーソルが動的カーソル**UPDATE**の場合、SELECT、INSERT、DELETE、および UPDATE ステートメント、および**CATALOG**結果セットに影響します。 **SELECT** **INSERT** **DELETE**  
  
 SQL_CA2_CRC_EXACT = カーソルが動的カーソルの場合、SQL_DIAG_CURSOR_ROW_COUNT診断フィールドで正確な行数を使用できます。  
  
 SQL_CA2_CRC_APPROXIMATE = カーソルが動的カーソルの場合、SQL_DIAG_CURSOR_ROW_COUNT診断フィールドでおよその行数を使用できます。  
  
 SQL_CA2_SIMULATE_NON_UNIQUE = ドライバーは、カーソルが動的カーソルの場合、シミュレートされた位置指定更新または削除ステートメントが 1 つの行にのみ影響することを保証しません。これを保証するのはアプリケーションの責任です。 (ステートメントが複数の行に影響を与える場合 **、SQLExecute**または**SQLExecDirect**は SQLSTATE 01001 [カーソル操作の競合]を返します。この動作を設定するには、アプリケーションは、SQL_ATTR_SIMULATE_CURSOR属性をSQL_SC_NON_UNIQUEに設定して**SQLSetStmtAttr**を呼び出します。  
  
 SQL_CA2_SIMULATE_TRY_UNIQUE = ドライバーは、カーソルが動的カーソルの場合、シミュレートされた位置指定更新または削除ステートメントが 1 つの行にのみ影響することを保証しようとします。 ドライバーは、一意のキーがない場合など、複数の行に影響する可能性がある場合でも、常にこのようなステートメントを実行します。 (ステートメントが複数の行に影響を与える場合 **、SQLExecute**または**SQLExecDirect**は SQLSTATE 01001 [カーソル操作の競合]を返します。この動作を設定するには、アプリケーションは、SQL_ATTR_SIMULATE_CURSOR属性をSQL_SC_TRY_UNIQUEに設定して**SQLSetStmtAttr**を呼び出します。  
  
 SQL_CA2_SIMULATE_UNIQUE = ドライバーは、カーソルが動的カーソルの場合、シミュレートされた位置指定更新または削除ステートメントが 1 つの行にのみ影響することを保証します。 ドライバーが指定されたステートメントに対してこれを保証できない場合 **、SQLExecDirect**または**SQLPrepare**は SQLSTATE 01001 (カーソル操作の競合) を返します。 この動作を設定するには、アプリケーションは SQL_ATTR_SIMULATE_CURSOR 属性を SQL_SC_UNIQUE に設定して**SQLSetStmtAttr**を呼び出します。  
  
 SQL_EXPRESSIONS_IN_ORDERBY(ODBC 1.0)  
 データ ソースが**ORDER BY**リスト内の式をサポートしている場合は、"Y" という文字列を指定します。「N」が表示されない場合。  
  
 SQL_FILE_USAGE(ODBC 2.0)  
 単一層ドライバーがデータ ソース内のファイルを直接処理する方法を示す SQLUSMALLINT 値。  
  
 SQL_FILE_NOT_SUPPORTED = ドライバーは単一層ドライバーではありません。 たとえば、ORACLE ドライバーは 2 層ドライバーです。  
  
 SQL_FILE_TABLE = 単一層ドライバーは、データ ソース内のファイルをテーブルとして扱います。 たとえば、Xbase ドライバは、各 Xbase ファイルをテーブルとして扱います。  
  
 SQL_FILE_CATALOG = 単一層ドライバーは、データ ソース内のファイルをカタログとして扱います。 たとえば、Access ドライバは、各 Access ファイルを完全なデータベースとして扱います。  
  
 アプリケーションでは、これを使用して、ユーザーがデータを選択する方法を決定できます。 たとえば、Xbase ユーザーはデータをファイルに格納すると考えることがよくありますが、ORACLE および Access ユーザーは通常、データをテーブルに格納すると考えます。  
  
 ユーザーが Xbase データ ソースを選択すると、アプリケーションに [Windows**ファイルを開く]** コモン ダイアログ ボックスが表示されます。ユーザーが Access または ORACLE データ ソースを選択すると、アプリケーションにカスタム**の [テーブルの選択**] ダイアログ ボックスが表示される場合があります。  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 ドライバーでサポートされている前方専用カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の最初のサブセットが含まれています。2 番目のサブセットについては、「SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2」を参照してください。  
  
 サポートされる属性を決定するには、次のビットマスクを使用します。  
  
 SQL_CA1_NEXTSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 これらのビットマスクの説明については、SQL_DYNAMIC_CURSOR_ATTRIBUTES1を参照してください (および説明の「動的カーソル」の「前方専用カーソル」を置き換えてください)。  
  
 SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 ドライバーでサポートされている前方専用カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の 2 番目のサブセットが含まれています。最初のサブセットについては、「SQL_FORWARD_ONLY_CURSOR_ATTRIBUTES1」を参照してください。  
  
 サポートされる属性を決定するには、次のビットマスクを使用します。  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 これらのビットマスクの説明については、SQL_DYNAMIC_CURSOR_ATTRIBUTES2 (および説明の「動的カーソル」の「前方専用カーソル」の代わりに使用する)を参照してください。  
  
 SQL_GETDATA_EXTENSIONS(ODBC 2.0)  
 SQLGetData への拡張機能を列挙する**SQLUINTEGER**ビットマスク。  
  
 次のビットマスクは **、SQLGetData**のドライバーがサポートする一般的な拡張機能を決定するフラグと共に使用されます。  
  
 SQL_GD_ANY_COLUMN = **SQLGetData**は、最後にバインドされた列の前の列を含め、バインドされていない列に対して呼び出すことができます。 SQL_GD_ANY_ORDERも返されない限り、列は昇順で呼び出す必要があることに注意してください。  
  
 SQL_GD_ANY_ORDER = **SQLGetData**は、任意の順序で非バインド列に対して呼び出すことができます。 **SQLGetData**は、SQL_GD_ANY_COLUMNも返されない限り、最後にバインドされた列の後の列に対してのみ呼び出すことができます。  
  
 SQL_GD_BLOCK = **SQLGetData は、SQLSetPos**でその行に位置指定した後、ブロック内の任意の行 (行セットサイズが 1 より大**SQLSetPos**きい行) のデータに対して非連結列を呼び出すことができます。  
  
 SQL_GD_BOUND = バインドされていない列に加えて、バインドされた列に対して**SQLGetData**を呼び出すことができます。 ドライバーもSQL_GD_ANY_COLUMNを返す場合を除き、この値を返すことはできません。  
  
 SQL_GD_OUTPUT_PARAMS = **SQLGetData**を呼び出して、出力パラメーター値を返すことができます。 詳細については、「 [SQLGetData を使用した出力パラメータの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)」を参照してください。  
  
 **SQLGetData**は、最後にバインドされた列の後に出現する非連結列からのみデータを返す必要があり、列番号が増える順に呼び出され、行ブロック内の行には含まれません。  
  
 ドライバーは、ブックマークをサポートしている場合 (固定長または可変長) 列 0 で**の SQLGetData**の呼び出しをサポートする必要があります。 このサポートは、ドライバが情報型を使用して**SQLGetInfo**を呼び出すために返すものに関係なく必要*SQL_GETDATA_EXTENSIONS。*  
  
 SQL_GROUP_BY(ODBC 2.0)  
 **GROUP BY**句の列と選択リストの非集計列との関係を指定する SQLUSMALLINT 値。  
  
 SQL_GB_COLLATE = **COLLATE**句は、各グループ化列の末尾に指定できます。 (ODBC 3.0)  
  
 SQL_GB_NOT_SUPPORTED = **GROUP BY**句はサポートされていません。 (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_EQUALS_SELECT = **GROUP BY**句には、選択リスト内のすべての非集約列が含まれている必要があります。 他の列を含めることはできません。 たとえば、**従業員グループから DEPT、 MAX (給与) を 選択**します。 (ODBC 2.0)  
  
 SQL_GB_GROUP_BY_CONTAINS_SELECT = **GROUP BY**句には、選択リスト内のすべての非集約列が含まれている必要があります。 選択リストにない列を含めることができます。 たとえば、[従業員グループ ]**から [DEPT, MAX(給与)]** を選択します。 (ODBC 2.0)  
  
 SQL_GB_NO_RELATION = GROUP **BY**句の列と選択リストは関連付けされません。 選択リスト内のグループ化されていない非集計列の意味は、データ ソースに依存します。 たとえば、[ **DEPT, 従業員グループから給与**] を選択します 。 (ODBC 2.0)  
  
 SQL-92 エントリ レベル準拠ドライバーは、サポートされているとおりに常にSQL_GB_GROUP_BY_EQUALS_SELECTオプションを返します。 SQL-92 完全レベル準拠ドライバーは、常にサポートされているSQL_GB_COLLATEオプションを返します。 いずれのオプションもサポートされていない場合 **、GROUP BY**句はデータ ソースでサポートされません。  
  
 SQL_IDENTIFIER_CASE(ODBC 1.0)  
 次のような SQLSmallINT 値。  
  
 SQL_IC_UPPER = SQL の識別子は大文字と小文字を区別せず、システム カタログに大文字で格納されます。  
  
 SQL_IC_LOWER = SQL の識別子は大文字と小文字を区別せず、システム カタログに小文字で格納されます。  
  
 SQL_IC_SENSITIVE = SQL の識別子は大文字と小文字が区別され、システム カタログに大文字と小文字が混在して格納されます。  
  
 SQL_IC_MIXED = SQL の識別子は大文字と小文字を区別せず、システム カタログ内で大文字と小文字が混在して格納されます。  
  
 SQL-92 の識別子では、大文字と小文字が区別されないため、SQL-92 (任意のレベル) に厳密に準拠しているドライバーは、サポートされているとおりにSQL_IC_SENSITIVEオプションを返すことはありません。  
  
 SQL_IDENTIFIER_QUOTE_CHAR(ODBC 1.0)  
 SQL ステートメント内の引用符で囲まれた (区切り記号付き) 識別子の開始区切り文字と終了区切り文字として使用される文字ストリング。 (ODBC 関数に引数として渡される識別子は、引用符で囲む必要はありません。データ ソースが引用符で囲まれた識別子をサポートしていない場合は、空白が返されます。  
  
 この文字列は、接続属性SQL_ATTR_METADATA_IDが SQL_TRUE に設定されている場合に、カタログ関数の引数を引用するためにも使用できます。  
  
 SQL-92 の識別子の引用符文字は二重引用符 (") であるため、SQL-92 に厳密に準拠するドライバーは常に二重引用符文字を返します。  
  
 SQL_INDEX_KEYWORDS(ODBC 3.0)  
 ドライバーでサポートされている CREATE INDEX ステートメント内のキーワードを列挙する SQLUINTEGER ビットマスク:  
  
 SQL_IK_NONE = どのキーワードもサポートされていません。  
  
 SQL_IK_ASC = ASC キーワードがサポートされています。  
  
 SQL_IK_DESC = DESC キーワードがサポートされています。  
  
 SQL_IK_ALL = すべてのキーワードがサポートされています。  
  
 CREATE INDEX ステートメントがサポートされているかどうかを確認するために、アプリケーションはSQL_DLL_INDEX情報型を指定して**SQLGetInfo**を呼び出します。  
  
 SQL_INFO_SCHEMA_VIEWS(ODBC 3.0)  
 ドライバーでサポートされているINFORMATION_SCHEMA内のビューを列挙する SQLUINTEGER ビットマスク。 INFORMATION_SCHEMA内のビューと内容は、SQL-92 で定義されているとおりです。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの隣に括弧で囲んで示されています。  
  
 サポートされているビューを決定するには、次のビットマスクを使用します。  
  
 SQL_ISV_ASSERTIONS = 特定のユーザーが所有するカタログのアサーションを識別します。 (フルレベル)  
  
 SQL_ISV_CHARACTER_SETS = 特定のユーザーがアクセスできるカタログの文字セットを識別します。 (中級レベル)  
  
 SQL_ISV_CHECK_CONSTRAINTS = 特定のユーザーが所有する CHECK 制約を識別します。 (中級レベル)  
  
 SQL_ISV_COLLATIONS = 特定のユーザーがアクセスできるカタログの文字照合順序を識別します。 (フルレベル)  
  
 SQL_ISV_COLUMN_DOMAIN_USAGE = カタログに定義されているドメインに依存し、特定のユーザーが所有するカタログの列を識別します。 (中級レベル)  
  
 SQL_ISV_COLUMN_PRIVILEGES = 特定のユーザーが使用できる、または与えられた永続表の列に対する特権を識別します。 (FIPS移行レベル)  
  
 SQL_ISV_COLUMNS = 特定のユーザーがアクセスできる永続テーブルの列を識別します。 (FIPS移行レベル)  
  
 SQL_ISV_CONSTRAINT_COLUMN_USAGE = CONSTRAINT_TABLE_USAGEビューと同様に、特定のユーザーが所有するさまざまな制約に対して列が識別されます。 (中級レベル)  
  
 SQL_ISV_CONSTRAINT_TABLE_USAGE = 制約によって使用されるテーブル (参照、一意、アサーション) を識別し、特定のユーザーが所有します。 (中級レベル)  
  
 SQL_ISV_DOMAIN_CONSTRAINTS = 特定のユーザーがアクセスできるドメイン制約 (カタログ内のドメイン) を識別します。 (中級レベル)  
  
 SQL_ISV_DOMAINS = ユーザーがアクセスできるカタログに定義されているドメインを識別します。 (中級レベル)  
  
 SQL_ISV_KEY_COLUMN_USAGE = 特定のユーザーによってキーとして制約される、カタログで定義されている列を識別します。 (中級レベル)  
  
 SQL_ISV_REFERENTIAL_CONSTRAINTS = 特定のユーザーが所有する参照制約を識別します。 (中級レベル)  
  
 SQL_ISV_SCHEMATA = 特定のユーザーが所有するスキーマを識別します。 (中級レベル)  
  
 SQL_ISV_SQL_LANGUAGES = SQL 実装でサポートされる SQL 準拠レベル、オプション、および言語を識別します。 (中級レベル)  
  
 SQL_ISV_TABLE_CONSTRAINTS = 特定のユーザーが所有するテーブル制約を識別します。 (中級レベル)  
  
 SQL_ISV_TABLE_PRIVILEGES = 特定のユーザーが使用できる、または与えられた永続表に対する特権を識別します。 (FIPS移行レベル)  
  
 SQL_ISV_TABLES = 特定のユーザーがアクセスできるカタログに定義されている永続テーブルを識別します。 (FIPS移行レベル)  
  
 SQL_ISV_TRANSLATIONS = 特定のユーザーがアクセスできるカタログの文字変換を識別します。 (フルレベル)  
  
 SQL_ISV_USAGE_PRIVILEGES = 特定のユーザーが使用できる、または所有しているカタログ・オブジェクトに対する USAGE 特権を識別します。 (FIPS移行レベル)  
  
 SQL_ISV_VIEW_COLUMN_USAGE = 特定のユーザーが所有するカタログのビューが依存している列を識別します。 (中級レベル)  
  
 SQL_ISV_VIEW_TABLE_USAGE = 特定のユーザーが所有するカタログのビューが従属しているテーブルを識別します。 (中級レベル)  
  
 SQL_ISV_VIEWS = このカタログで定義されている、特定のユーザーがアクセスできる表示テーブルを識別します。 (FIPS移行レベル)  
  
 SQL_INSERT_STATEMENT(ODBC 3.0)  
 **INSERT**ステートメントのサポートを示す SQLUINTEGER ビットマスク。  
  
 SQL_IS_INSERT_LITERALS  
  
 SQL_IS_INSERT_SEARCHED  
  
 SQL_IS_SELECT_INTO  
  
 SQL-92 エントリ レベル準拠ドライバーは、常にサポートされているこれらのオプションのすべてを返します。  
  
 SQL_INTEGRITY(ODBC 1.0)  
 データ・ソースが保全性拡張機能をサポートする場合は、文字ストリング「Y」。「N」が表示されない場合。  
  
 この*インフォタイプ*は、ODBC 2.0 インフォタイプSQL_ODBC_SQL_OPT_IEFから ODBC 3.0*の名前*が変更されました。  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 ドライバーでサポートされているキーセット カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の最初のサブセットが含まれています。2 番目のサブセットについては、「SQL_KEYSET_CURSOR_ATTRIBUTES2」を参照してください。  
  
 サポートされる属性を決定するには、次のビットマスクを使用します。  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 これらのビットマスクの説明については、SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (および説明の「動的カーソル」の「キーセット駆動カーソル」の代用)を参照してください。  
  
 SQL-92 中間レベル適合ドライバーは、通常、サポートされているSQL_CA1_NEXT、SQL_CA1_ABSOLUTE、およびSQL_CA1_RELATIVEオプションを返します。 これは基になる SQL サポートを直接決定しないため、ただし、SQL-92 中間レベル準拠ドライバーであっても、スクロール可能なカーソルはサポートされない場合があります。  
  
 SQL_KEYSET_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 ドライバーでサポートされているキーセット カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の 2 番目のサブセットが含まれています。最初のサブセットについては、「SQL_KEYSET_CURSOR_ATTRIBUTES1」を参照してください。  
  
 サポートされる属性を決定するには、次のビットマスクを使用します。  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 これらのビットマスクの説明については、SQL_DYNAMIC_CURSOR_ATTRIBUTES1 (および説明の「動的カーソル」の「キーセット駆動カーソル」の代用)を参照してください。  
  
 SQL_KEYWORDS(ODBC 2.0)  
 すべてのデータ ソース固有のキーワードのコンマ区切りリストを含む文字列。 このリストには、ODBC に固有のキーワードや、データ ソースと ODBC の両方で使用されるキーワードは含まれません。 このリストは、すべての予約済みキーワードを表します。相互運用可能なアプリケーションでは、オブジェクト名にこれらの単語を使用しないでください。  
  
 ODBC キーワードの一覧については、「 付録 C [: SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)」の[「予約キーワード](../../../odbc/reference/appendixes/reserved-keywords.md)」を参照してください。 **#define**値SQL_ODBC_KEYWORDSには、ODBC キーワードのコンマ区切りリストが含まれています。  
  
 付録 C: SQL 文法  
  
 SQL_LIKE_ESCAPE_CLAUSE(ODBC 2.0)  
 データ ソースがパーセント文字のエスケープ文字をサポートする場合は、文字列 "Y" (パーセント)**LIKE**述語のアンダースコア文字 (_) とドライバーは **、LIKE**述語のエスケープ文字を定義するための ODBC 構文をサポートします。それ以外の場合は"N"。  
  
 SQL_MAX_ASYNC_CONCURRENT_STATEMENTS(ODBC 3.0)  
 非同期モードでの、ドライバーが特定の接続でサポートできるアクティブな同時実行ステートメントの最大数を指定する SQLUINTEGER 値。 特定の制限がない場合、または制限が不明な場合、この値はゼロです。  
  
 SQL_MAX_BINARY_LITERAL_LEN(ODBC 2.0)  
 SQL ステートメント内のバイナリ リテラルの最大長 **(SQLGetTypeInfo**によって返されるリテラル プレフィックスとサフィックスを除く 16 進文字の数) を指定する SQLUINTEGER 値。 たとえば、バイナリリテラル 0xFFAA の長さは 4 です。 最大長がない場合、または長さが不明の場合、この値はゼロに設定されます。  
  
 SQL_MAX_CATALOG_NAME_LEN(ODBC 1.0)  
 データ・ソース内のカタログ名の最大長を指定する SQLUSMALLINT 値。 最大長がない場合、または長さが不明の場合、この値はゼロに設定されます。  
  
 FIPS の完全なレベルに準拠したドライバーは、少なくとも 128 を返します。  
  
 この*インフォタイプ*は、ODBC 2.0 インフォタイプ SQL_MAX_QUALIFIER_NAME_LENから ODBC 3.0*の名前*が変更されました。  
  
 SQL_MAX_CHAR_LITERAL_LEN(ODBC 2.0)  
 SQL ステートメント内の文字リテラルの最大長 **(SQLGetTypeInfo**によって戻されるリテラル接頭部および接尾辞を除く文字数) を指定する SQLUINTEGER 値。 最大長がない場合、または長さが不明の場合、この値はゼロに設定されます。  
  
 SQL_MAX_COLUMN_NAME_LEN(ODBC 1.0)  
 データ・ソース内の列名の最大長を指定する SQLUSMALLINT 値。 最大長がない場合、または長さが不明の場合、この値はゼロに設定されます。  
  
 FIPS エントリ レベル準拠ドライバーは、少なくとも 18 を返します。 FIPS 中間レベル準拠ドライバーは、少なくとも 128 を返します。  
  
 SQL_MAX_COLUMNS_IN_GROUP_BY(ODBC 2.0)  
 **グループ BY**句で使用できる列の最大数を指定する SQLUSMALLINT 値。 指定された制限がない場合、または制限が不明な場合、この値はゼロに設定されます。  
  
 FIPS エントリ レベル準拠ドライバーは、少なくとも 6 を返します。 FIPS 中間レベル準拠ドライバーは、少なくとも 15 を返します。  
  
 SQL_MAX_COLUMNS_IN_INDEX(ODBC 2.0)  
 インデックスで使用できる列の最大数を指定する SQLUSMALLINT 値。 指定された制限がない場合、または制限が不明な場合、この値はゼロに設定されます。  
  
 SQL_MAX_COLUMNS_IN_ORDER_BY(ODBC 2.0)  
 **ORDER BY**句で使用できる最大列数を指定する SQLUSMALLINT 値。 指定された制限がない場合、または制限が不明な場合、この値はゼロに設定されます。  
  
 FIPS エントリ レベル準拠ドライバーは、少なくとも 6 を返します。 FIPS 中間レベル準拠ドライバーは、少なくとも 15 を返します。  
  
 SQL_MAX_COLUMNS_IN_SELECT(ODBC 2.0)  
 選択リストで使用できる最大列数を指定する SQLUSMALLINT 値。 指定された制限がない場合、または制限が不明な場合、この値はゼロに設定されます。  
  
 FIPS エントリ レベル準拠ドライバーは、少なくとも 100 を返します。 FIPS 中間レベル準拠ドライバーは、少なくとも 250 を返します。  
  
 SQL_MAX_COLUMNS_IN_TABLE(ODBC 2.0)  
 テーブルで使用できる列の最大数を指定する SQLUSMALLINT 値。 指定された制限がない場合、または制限が不明な場合、この値はゼロに設定されます。  
  
 FIPS エントリ レベル準拠ドライバーは、少なくとも 100 を返します。 FIPS 中間レベル準拠ドライバーは、少なくとも 250 を返します。  
  
 SQL_MAX_CONCURRENT_ACTIVITIES(ODBC 1.0)  
 ドライバーが接続をサポートできるアクティブなステートメントの最大数を指定する SQLUSMALLINT 値。 ステートメントは、結果が保留状態である場合、SELECT**操作の**行、または INSERT、UPDATE、または**DELETE**操作 (**INSERT**行カウント**UPDATE**など) によって影響を受ける行を意味する、結果として定義 NEED_DATAされます。 この値は、ドライバーまたはデータ ソースによって課される制限を反映できます。 指定された制限がない場合、または制限が不明な場合、この値はゼロに設定されます。  
  
 この*インフォタイプ*は、ODBC 2.0 インフォタイプ SQL_ACTIVE_STATEMENTSから ODBC 3.0*の名前*が変更されました。  
  
 SQL_MAX_CURSOR_NAME_LEN(ODBC 1.0)  
 データ・ソース内のカーソル名の最大長を指定する SQLUSMALLINT 値。 最大長がない場合、または長さが不明の場合、この値はゼロに設定されます。  
  
 FIPS エントリ レベル準拠ドライバーは、少なくとも 18 を返します。 FIPS 中間レベル準拠ドライバーは、少なくとも 128 を返します。  
  
 SQL_MAX_DRIVER_CONNECTIONS(ODBC 1.0)  
 ドライバーが環境をサポートできるアクティブな接続の最大数を指定する SQLUSMALLINT 値。 この値は、ドライバーまたはデータ ソースによって課される制限を反映できます。 指定された制限がない場合、または制限が不明な場合、この値はゼロに設定されます。  
  
 この*インフォタイプ*は、ODBC 2.0 インフォタイプSQL_ACTIVE_CONNECTIONSから ODBC 3.0*の名前*が変更されました。  
  
 SQL_MAX_IDENTIFIER_LEN(ODBC 3.0)  
 データ ソースがユーザー定義名に対してサポートする最大サイズを文字数で示す SQLUSMALLINT。  
  
 FIPS エントリ レベル準拠ドライバーは、少なくとも 18 を返します。 FIPS 中間レベル準拠ドライバーは、少なくとも 128 を返します。  
  
 SQL_MAX_INDEX_SIZE(ODBC 2.0)  
 インデックスの結合されたフィールドで許容される最大バイト数を指定する SQLUINTEGER 値。 指定された制限がない場合、または制限が不明な場合、この値はゼロに設定されます。  
  
 SQL_MAX_PROCEDURE_NAME_LEN(ODBC 1.0)  
 データ・ソース内のプロシージャー名の最大長を指定する SQLUSMALLINT 値。 最大長がない場合、または長さが不明の場合、この値はゼロに設定されます。  
  
 SQL_MAX_ROW_SIZE(ODBC 2.0)  
 テーブル内の 1 行の最大長を指定する SQLUINTEGER 値。 指定された制限がない場合、または制限が不明な場合、この値はゼロに設定されます。  
  
 FIPS エントリ レベル準拠ドライバーは、少なくとも 2,000 を返します。 FIPS 中間レベル準拠ドライバーは、少なくとも 8,000 を返します。  
  
 SQL_MAX_ROW_SIZE_INCLUDES_LONG(ODBC 3.0)  
 SQL_MAX_ROW_SIZE情報タイプに対して返される最大行サイズに、行内のすべてのSQL_LONGVARCHAR列とSQL_LONGVARBINARY列の長さが含まれている場合は、文字列"Y"。;それ以外の場合は"N"。  
  
 SQL_MAX_SCHEMA_NAME_LEN(ODBC 1.0)  
 データ ソース内のスキーマ名の最大長を指定する SQLUSMALLINT 値。 最大長がない場合、または長さが不明の場合、この値はゼロに設定されます。  
  
 FIPS エントリ レベル準拠ドライバーは、少なくとも 18 を返します。 FIPS 中間レベル準拠ドライバーは、少なくとも 128 を返します。  
  
 この*インフォタイプ*は、ODBC 2.0 インフォタイプSQL_MAX_OWNER_NAME_LENから ODBC 3.0*の名前*が変更されました。  
  
 SQL_MAX_STATEMENT_LEN(ODBC 2.0)  
 SQL ステートメントの最大長 (空白文字を含む) を指定する SQLUINTEGER 値。 最大長がない場合、または長さが不明の場合、この値はゼロに設定されます。  
  
 SQL_MAX_TABLE_NAME_LEN(ODBC 1.0)  
 データ ソース内のテーブル名の最大長を指定する SQLUSMALLINT 値。 最大長がない場合、または長さが不明の場合、この値はゼロに設定されます。  
  
 FIPS エントリ レベル準拠ドライバーは、少なくとも 18 を返します。 FIPS 中間レベル準拠ドライバーは、少なくとも 128 を返します。  
  
 SQL_MAX_TABLES_IN_SELECT(ODBC 2.0)  
 **SELECT**ステートメントの**FROM**句で使用できるテーブルの最大数を指定する SQLUSMALLINT 値。 指定された制限がない場合、または制限が不明な場合、この値はゼロに設定されます。  
  
 FIPS エントリ レベル準拠ドライバーは、少なくとも 15 を返します。 FIPS 中間レベル準拠ドライバーは、少なくとも 50 を返します。  
  
 SQL_MAX_USER_NAME_LEN(ODBC 2.0)  
 データ・ソース内のユーザー名の最大長を指定する SQLUSMALLINT 値。 最大長がない場合、または長さが不明の場合、この値はゼロに設定されます。  
  
 SQL_MULT_RESULT_SETS(ODBC 1.0)  
 データ ソースが複数の結果セットをサポートする場合は "Y" を、サポートしていない場合は "N" を指定します。  
  
 複数の結果セットの詳細については、「[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)」を参照してください。  
  
 SQL_MULTIPLE_ACTIVE_TXN(ODBC 1.0)  
 一方、文字列: "Y" は、ドライバーが同時に複数のアクティブなトランザクションをサポートする場合は "N" を、同時に 1 つのトランザクションしかアクティブにできない場合は "N" です。  
  
 この情報タイプに対して返される情報は、分散トランザクションの場合には適用されません。  
  
 SQL_NEED_LONG_DATA_LEN(ODBC 2.0)  
 データ ソースが長いデータ値の長さ (データ型がSQL_LONGVARCHAR、SQL_LONGVARBINARY、または長いデータ ソース固有のデータ型) を必要とする場合は、文字列 "Y" を指定します。 詳細については、「 [SQLBind パラメーター関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)および[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)」を参照してください。  
  
 SQL_NON_NULLABLE_COLUMNS(ODBC 1.0)  
 データ ソースが列で NOT NULL をサポートするかどうかを指定する SQLUSMALLINT 値。  
  
 SQL_NNC_NULL = すべての列は NULL 可能でなければなりません。  
  
 SQL_NNC_NON_NULL = 列を NULL 可能にすることはできません。 (データ ソースは **、CREATE TABLE**ステートメントで**NOT NULL**列制約をサポートしています。  
  
 SQL-92 エントリ レベル準拠ドライバーはSQL_NNC_NON_NULL返します。  
  
 SQL_NULL_COLLATION(ODBC 2.0)  
 ヌルが結果セット内でソートされる場所を指定する SQLUSMALLINT 値:  
  
 SQL_NC_END = ヌルは、ASC キーワードや DESC キーワードに関係なく、結果セットの末尾で並べ替えられます。  
  
 SQL_NC_HIGH = ヌルは、ASC または DESC キーワードに応じて、結果セットの上限でソートされます。  
  
 SQL_NC_LOW = ヌルは、ASC または DESC キーワードに応じて、結果セットの下限でソートされます。  
  
 SQL_NC_START = ヌルは、ASC キーワードや DESC キーワードに関係なく、結果セットの先頭でソートされます。  
  
 SQL_NUMERIC_FUNCTIONS(ODBC 1.0)  
 注: 情報タイプは ODBC 1.0 で導入されました。各ビットマスクには、導入されたバージョンがラベル付けされています。  
  
 ドライバーと関連データ ソースでサポートされているスカラー数値関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる数値関数を決定するには、次のビットマスクを使用します。  
  
 SQL_FN_NUM_ABS (ODBC 1.0)SQL_FN_NUM_ACOS (ODBC 1.0) SQL_FN_NUM_ASIN (ODBC 1.0) SQL_FN_NUM_ASIN (ODBC 1.0) SQL_FN_NUM_ATAN (ODBC 1.0) SQL_FN_NUM_ATAN2 (ODBC 1.0) SQL_FN_NUM_CEILING (ODBC 1.0) SQL_FN_NUM_COS (ODBC 1.0) SQL_FN_NUM_COS (ODBC 1.0 SQL_FN_NUM_COT) SQL_FN_NUM_COS (ODBC 1.0) SQL_FN_NUM_DEGREES (ODBC 2.0)SQL_FN_NUM_EXP (ODBC 1.0)SQL_FN_NUM_FLOOR (ODBC 1.0)SQL_FN_NUM_LOG (ODBC 1.0)SQL_FN_NUM_LOG10 (ODBC 1.0)SQL_FN_NUM_LOG10 (ODBC 1.0)SQL_FN_ (ODBC 1.0)SQL_FN_NUM_LOG10 (ODBC 1.0)SQL_FN_ (ODBC 1.0)SQL_FN_NUM_LOG10 (ODBC 1.0)SQL_FN_NUM_LOG10 (ODBC 1.0)SQL_FN_NUM_LOG10 (ODBC 1.0)SQL_FN_ (ODBC 1.0)SQL_FN_NUM_LOG10 (ODBC 1.0)SQL_FN_NUM_LOG10 (ODBC 1.0)SQL_FN_ (ODBC 1.0)NUM_MOD (ODBC 1.0) SQL_FN_NUM_PI (ODBC 1.0) SQL_FN_NUM_POWER (ODBC 1.0) SQL_FN_NUM_POWER (ODBC 2.0) SQL_FN_NUM_RADIANS (ODBC 2.0) SQL_FN_NUM_RAND (ODBC 1.0) SQL_FN_NUM_ROUND (ODBC 2.0) SQL_FN_NUM_SIGN (ODBC 1.0) SQL_FN_NUM_SIN (ODBC 1.0) SQL_FN_NUM_SQRT (ODBC 1.0) SQL_FN_NUM_TAN (ODBC 1.0) SQL_FN_NUM_TRUNCATE (ODBC 2.0)  
  
 SQL_ODBC_INTERFACE_CONFORMANCE(ODBC 3.0)  
 ドライバーが準拠する ODBC 3 *.x*インターフェイスのレベルを示す SQLUINTEGER 値。  
  
 SQL_OIC_CORE: すべての ODBC ドライバーが準拠することが期待される最小レベル。 このレベルには、接続関数、SQL ステートメントを準備および実行するための関数、基本結果セットのメタデータ関数、基本カタログ関数などの基本的なインタフェース要素が含まれます。  
  
 SQL_OIC_LEVEL1: コア標準準拠レベル機能、およびスクロール可能なカーソル、ブックマーク、位置指定更新と削除などのレベル。  
  
 SQL_OIC_LEVEL2: レベル 1 標準準拠レベル機能、および機密性の高いカーソルなどの高度な機能を含むレベル。ブックマークによる更新、削除、および更新。ストアド プロシージャのサポート;主キーと外部キーのカタログ関数。マルチカタログのサポート。などなど。  
  
 詳細については、「[インターフェイス準拠レベル](../../../odbc/reference/develop-app/interface-conformance-levels.md)」を参照してください。  
  
 SQL_ODBC_VER(ODBC 1.0)  
 ドライバー マネージャーが準拠する ODBC のバージョンを持つ文字列。 バージョンは ##.###.0000 形式で、最初の 2 桁はメジャー バージョンで、次の 2 桁はマイナー バージョンです。 これは、ドライバー マネージャーでのみ実装されます。  
  
 SQL_OJ_CAPABILITIES(ODBC 2.01)  
 ドライバーとデータ ソースでサポートされる外部結合の型を列挙する SQLUINTEGER ビットマスク。 サポートされている型を決定するには、次のビットマスクを使用します。  
  
 SQL_OJ_LEFT = 左外部結合がサポートされています。  
  
 SQL_OJ_RIGHT = 右外部結合がサポートされています。  
  
 SQL_OJ_FULL = 完全外部結合がサポートされています。  
  
 SQL_OJ_NESTED = ネストされた外部結合がサポートされます。  
  
 SQL_OJ_NOT_ORDERED = 外部結合の ON 句の列名は **、OUTER JOIN**句のそれぞれのテーブル名と同じ順序である必要はありません。  
  
 SQL_OJ_INNER = 内部結合 (左外部結合の右テーブル、または右外部結合の左テーブル) も内部結合で使用できます。 これは、内部テーブルを持たない完全外部結合には適用されません。  
  
 SQL_OJ_ALL_COMPARISON_OPS = ON 句の比較演算子は、ODBC 比較演算子のいずれかです。 このビットが設定されていない場合は、外部結合で等号 (=) 比較演算子のみを使用できます。  
  
 サポートされているオプションがいずれも返されない場合は、外部結合句はサポートされません。  
  
 SQL-92 で定義されている SELECT ステートメントでの関係結合演算子のサポートについては、「SQL_SQL92_RELATIONAL_JOIN_OPERATORS」を参照してください。  
  
 SQL_ORDER_BY_COLUMNS_IN_SELECT(ODBC 2.0)  
 **ORDER BY**句の列が選択リストに含まれなければならない場合は、"Y" という文字列を指定します。それ以外の場合は"N"。  
  
 SQL_PARAM_ARRAY_ROW_COUNTS(ODBC 3.0)  
 パラメーター化された実行で行数が使用できるかどうかに関するドライバーのプロパティを列挙する SQLUINTEGER です。 次の値を持ちます。  
  
 SQL_PARC_BATCH = 個々の行数は、パラメーターのセットごとに使用できます。 これは概念的には、配列に設定された各パラメーターに対して 1 つずつ、SQL ステートメントのバッチを生成するドライバーと同じです。 拡張エラー情報は、SQL_PARAM_STATUS_PTR記述子フィールドを使用して取得できます。  
  
 SQL_PARC_NO_BATCH = 使用可能な行数は 1 つのみで、これはパラメーターの配列全体に対するステートメントの実行から生じる累積行数です。 これは概念的には、完全なパラメーター配列を 1 つのアトミック単位としてステートメントを扱うのと同じです。 エラーは、1 つのステートメントが実行された場合と同じように処理されます。  
  
 SQL_PARAM_ARRAY_SELECTS(ODBC 3.0)  
 パラメーター化された実行での結果セットの可用性に関するドライバーのプロパティを列挙する SQLUINTEGER です。 次の値を持ちます。  
  
 SQL_PAS_BATCH = パラメータのセットごとに 1 つの結果セットを使用できます。 これは概念的には、配列に設定された各パラメーターに対して 1 つずつ、SQL ステートメントのバッチを生成するドライバーと同じです。  
  
 SQL_PAS_NO_BATCH = 使用可能な結果セットは 1 つだけで、パラメーターの完全な配列に対するステートメントの実行から得られた累積結果セットを表します。 これは概念的には、完全なパラメーター配列を 1 つのアトミック単位としてステートメントを扱うのと同じです。  
  
 SQL_PAS_NO_SELECT = ドライバーは、パラメーターの配列を使用して結果セット生成ステートメントを実行することはできません。  
  
 SQL_PROCEDURE_TERM(ODBC 1.0)  
 プロシージャのデータ ソース ベンダーの名前を含む文字列。たとえば、"データベース プロシージャ"、"ストアド プロシージャ"、"プロシージャ"、"パッケージ"、または "ストアド クエリ" です。  
  
 SQL_PROCEDURES(ODBC 1.0)  
 データ ソースがプロシージャをサポートし、ドライバーが ODBC プロシージャ呼び出し構文をサポートしている場合は、"Y" という文字列を指定します。それ以外の場合は"N"。  
  
 SQL_POS_OPERATIONS(ODBC 2.0)  
 SQLINTEGER ビットマスクで **、SQLSetPos**でのサポート操作を列挙します。  
  
 以下のビットマスクは、どのオプションがサポートされているかを決定するためにフラグと共に使用されます。  
  
 SQL_POS_POSITION (ODBC 2.0) SQL_POS_REFRESH (ODBC 2.0) SQL_POS_UPDATE (ODBC 2.0) SQL_POS_DELETE (ODBC 2.0) SQL_POS_ADD (ODBC 2.0)  
  
 SQL_QUOTED_IDENTIFIER_CASE(ODBC 2.0)  
 次のような SQLSmallINT 値。  
  
 SQL_IC_UPPER = SQL で引用符で囲まれた識別子は大文字と小文字を区別せず、システム カタログに大文字で格納されます。  
  
 SQL_IC_LOWER = SQL で引用符で囲まれた識別子は大文字と小文字を区別せず、システム カタログに小文字で格納されます。  
  
 SQL_IC_SENSITIVE = SQL で引用符で囲まれた識別子は大文字と小文字を区別し、システム カタログに大文字と小文字が混在して格納されます。 (SQL-92 準拠のデータベースでは、引用符で囲まれた識別子は常に大文字と小文字を区別します。  
  
 SQL_IC_MIXED = SQL で引用符で囲まれた識別子は大文字と小文字を区別せず、システム カタログに大文字と小文字が混在して格納されます。  
  
 SQL-92 エントリ レベル準拠ドライバーは常にSQL_IC_SENSITIVE返します。  
  
 SQL_ROW_UPDATES(ODBC 1.0)  
 キーセットドリブンカーソルまたは混合カーソルが、フェッチされたすべての行の行バージョンまたは値を維持し、行が最後にフェッチされた後に行に対して行われた更新を検出できる場合は、文字列 "Y" を指定します。 (これは更新にのみ適用され、削除や挿入には適用されません)。ドライバーは **、SQLFetchScroll**が呼び出されたときに行の状態配列にSQL_ROW_UPDATEDフラグを返すことができます。 それ以外の場合は"N"。  
  
 SQL_SCHEMA_TERM(ODBC 1.0)  
 スキーマのデータ ソース ベンダーの名前を持つ文字列。たとえば、"所有者"、"承認 ID"、または "スキーマ" です。  
  
 文字ストリングは、大文字、小文字、または混合大文字小文字で返すことができます。  
  
 SQL-92 エントリ レベル準拠ドライバーは、常に "スキーマ" を返します。  
  
 この*インフォタイプ*は、ODBC 2.0 インフォタイプSQL_OWNER_TERMから ODBC 3.0*の名前*が変更されました。  
  
 SQL_SCHEMA_USAGE(ODBC 2.0)  
 スキーマを使用できるステートメントを列挙する SQLUINTEGER ビットマスク。  
  
 SQL_SU_DML_STATEMENTS = スキーマは、すべてのデータ操作言語ステートメントでサポートされます: **SELECT、****挿入**、**更新**、**削除**、およびサポートされている場合は **、更新および**位置指定更新および削除ステートメントを選択します。  
  
 SQL_SU_PROCEDURE_INVOCATION = スキーマは、ODBC プロシージャー呼び出しステートメントでサポートされます。  
  
 SQL_SU_TABLE_DEFINITION = スキーマは、すべてのテーブル定義ステートメントでサポートされます:**テーブルの作成**、 **CREATE VIEW**、**テーブルの変更**、**テーブルの削除**、およびビューの**削除**。  
  
 SQL_SU_INDEX_DEFINITION = スキーマは、すべてのインデックス定義ステートメントでサポートされます: **CREATE INDEX**と**DROP INDEX**。  
  
 SQL_SU_PRIVILEGE_DEFINITION = スキーマは **、GRANT**と**REVOKE**のすべての特権定義ステートメントでサポートされます。  
  
 SQL-92 エントリ レベル準拠ドライバーは、サポートされているとおり、常にSQL_SU_DML_STATEMENTS、SQL_SU_TABLE_DEFINITION、およびSQL_SU_PRIVILEGE_DEFINITIONのオプションを返します。  
  
 この*インフォタイプ*は ODBC 2.0 インフォタイプ SQL_OWNER_USAGEから ODBC 3.0*の名前*が変更されました。  
  
 SQL_SCROLL_OPTIONS(ODBC 1.0)  
 注: 情報タイプは ODBC 1.0 で導入されました。各ビットマスクには、導入されたバージョンがラベル付けされています。  
  
 スクロール可能なカーソルでサポートされるスクロール オプションを列挙する SQLUINTEGER ビットマスク。  
  
 サポートされるオプションを決定するには、次のビットマスクを使用します。  
  
 SQL_SO_FORWARD_ONLY = カーソルは前方にのみスクロールします。 (ODBC 1.0)  
  
 SQL_SO_STATIC = 結果セット内のデータは静的です。 (ODBC 2.0)  
  
 SQL_SO_KEYSET_DRIVEN = ドライバーは、結果セット内のすべての行のキーを保存して使用します。 (ODBC 1.0)  
  
 SQL_SO_DYNAMIC = ドライバーは、行セット内のすべての行のキーを保持します (キーセットのサイズは行セットのサイズと同じです)。 (ODBC 1.0)  
  
 SQL_SO_MIXED = ドライバーはキーセット内のすべての行のキーを保持し、キーセットのサイズが行セットのサイズより大きくなっています。 カーソルはキーセット内でキーセット駆動され、キーセットの外側では動的です。 (ODBC 1.0)  
  
 スクロール可能なカーソルについては、「[スクロール可能なカーソル](../../../odbc/reference/develop-app/scrollable-cursors.md)」を参照してください。  
  
 SQL_SEARCH_PATTERN_ESCAPE(ODBC 1.0)  
 パターンマッチメタ文字アンダースコア (_) とパーセント記号 (%)検索パターンで有効な文字として使用します。 このエスケープ文字は、検索文字列をサポートするカタログ関数の引数にのみ適用されます。 この文字列が空の場合、ドライバーは検索パターンエスケープ文字をサポートしません。  
  
 この情報型は**LIKE**述部のエスケープ文字の一般的なサポートを示すものではないため、SQL-92 にはこの文字ストリングの要件は含まれません。  
  
 この*インフォタイプ*は、カタログ機能に限定されています。 検索パターン文字列でのエスケープ文字の使用については、「[パターン値引数](../../../odbc/reference/develop-app/pattern-value-arguments.md)」を参照してください。  
  
 SQL_SERVER_NAME(ODBC 1.0)  
 実際のデータ ソース固有のサーバー名を持つ文字列。データ ソース名が**SQLConnect** **、SQL ドライバ接続**、および**SQL ブラウズ接続**の間に使用される場合に役立ちます。  
  
 SQL_SPECIAL_CHARACTERS(ODBC 2.0)  
 データ ソース上の識別子名 (テーブル名、列名、インデックス名など) で使用できるすべての特殊文字 (a ~ z、A ~ Z、0 ~ 9、およびアンダースコアを除くすべての文字) を含む文字列。 たとえば、"#$^" とします。 識別子にこれらの文字が 1 つ以上含まれている場合、その識別子は区切り識別子である必要があります。  
  
 SQL_SQL_CONFORMANCE(ODBC 3.0)  
 ドライバーでサポートされている SQL-92 のレベルを示す SQLUINTEGER 値:  
  
 SQL_SC_SQL92_ENTRY = エントリ レベル SQL-92 に準拠しています。  
  
 SQL_SC_FIPS127_2_TRANSITIONAL = FIPS 127-2 移行レベルに準拠しています。  
  
 SQL_SC_SQL92_FULL = フル レベル SQL-92 準拠。  
  
 SQL_SC_ SQL92_INTERMEDIATE = 中間レベル SQL-92 に準拠しています。  
  
 SQL_SQL92_DATETIME_FUNCTIONS(ODBC 3.0)  
 SQL-92 で定義されている、ドライバーと関連データ ソースでサポートされている日時スカラー関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる日時関数を決定するには、次のビットマスクを使用します。  
  
 SQL_SDF_CURRENT_DATESQL_SDF_CURRENT_TIMESQL_SDF_CURRENT_TIMESTAMP  
  
 SQL_SQL92_FOREIGN_KEY_DELETE_RULE(ODBC 3.0)  
 SQL-92 で定義されている **、DELETE**ステートメントで外部キーに対してサポートされる規則を列挙する SQLUINTEGER ビットマスク。  
  
 データ ソースでサポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_SFKD_CASCADESQL_SFKD_NO_ACTIONSQL_SFKD_SET_DEFAULTSQL_SFKD_SET_NULL  
  
 FIPS 移行レベル準拠ドライバーは、常にサポートされているこれらのオプションのすべてを返します。  
  
 SQL_SQL92_FOREIGN_KEY_UPDATE_RULE(ODBC 3.0)  
 SQL-92 で定義されている UPDATE ステートメントで、外部キーに対**UPDATE**してサポートされる規則を列挙する SQLUINTEGER ビットマスク。  
  
 データ ソースでサポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_SFKU_CASCADESQL_SFKU_NO_ACTIONSQL_SFKU_SET_DEFAULTSQL_SFKU_SET_NULL  
  
 SQL-92 完全なレベル準拠ドライバーは、サポートされているとおり、常にこれらのオプションのすべてを返します。  
  
 SQL_SQL92_GRANT(ODBC 3.0)  
 SQL-92 で定義されている**GRANT**ステートメントでサポートされる句を列挙する SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの隣に括弧で囲んで示されています。  
  
 データ ソースでサポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_SG_DELETE_TABLE (エントリーレベル)SQL_SG_INSERT_COLUMN(中間レベル)SQL_SG_INSERT_TABLE(エントリーレベル)SQL_SG_REFERENCES_TABLE(エントリーレベル)SQL_SG_REFERENCES_COLUMN(エントリーレベル)SQL_SG_SELECT_TABLE(エントリーレベル)SQL_SG_UPDATE_COLUMN(エントリーレベル)SQL_SG_UPDATE_TABLE(エントリーレベル)SQL_SG_USAGE_ON_DOMAIN(FIPS移行レベル)SQL_SG_USAGE_ON_CHARACTER_SET(FIPS移行レベル)SQL_SG_USAGE_ON_COLLATION(FIPS移行レベル)SQL_SG_USAGE_ON_TRANSLATION(FIPS移行レベル)レベル)SQL_SG_WITH_GRANT_OPTION(エントリーレベル)  
  
 SQL_SQL92_NUMERIC_VALUE_FUNCTIONS(ODBC 3.0)  
 SQL-92 で定義されているドライバーと関連データ ソースでサポートされている数値スカラー関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる数値関数を決定するには、次のビットマスクを使用します。  
  
 SQL_SNVF_BIT_LENGTHSQL_SNVF_CHAR_LENGTHSQL_SNVF_CHARACTER_LENGTHSQL_SNVF_EXTRACTSQL_SNVF_OCTET_LENGTHSQL_SNVF_POSITION  
  
 SQL_SQL92_PREDICATES(ODBC 3.0)  
 **SELECT**ステートメントでサポートされている述語を列挙する SQLUINTEGER ビットマスクです。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの隣に括弧で囲んで示されています。  
  
 次のビットマスクを使用して、データ ソースでサポートされるオプションを決定します。  
  
 SQL_SP_BETWEEN (エントリーレベル)SQL_SP_COMPARISON(エントリーレベル)SQL_SP_COMPARISON(エントリーレベル)SQL_SP_EXISTS(エントリーレベル)SQL_SP_IN(エントリーレベル)SQL_SP_ISNOTNULL(エントリーレベル)SQL_SP_ISNULL(エントリーレベル)SQL_SP_LIKE(エントリーレベル)SQL_SP_MATCH_FULL(フルレベル)SQL_SP_MATCH_PARTIAL(フルレベル)SQL_SP_MATCH_UNIQUE_FULL(フルレベル)SQL_SP_MATCH_UNIQUE_PARTIAL(全レベル)SQL_SP_OVERLAPS(FIPS移行レベル)SQL_SP_QUANTIFIED_COMPARISON(エントリーレベル)SQL_SP_UNIQUE(エントリーレベル)  
  
 SQL_SQL92_RELATIONAL_JOIN_OPERATORS(ODBC 3.0)  
 SQL-92 で定義されている**SELECT**ステートメントでサポートされているリレーショナル結合演算子を列挙する SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの隣に括弧で囲んで示されています。  
  
 次のビットマスクを使用して、データ ソースでサポートされるオプションを決定します。  
  
 SQL_SRJO_CORRESPONDING_CLAUSE (中間レベル)SQL_SRJO_CROSS_JOIN (フルレベル)SQL_SRJO_EXCEPT_JOIN (中間レベル)SQL_SRJO_FULL_OUTER_JOIN (中間レベル) SQL_SRJO_INNER_JOIN (FIPS 移行レベル)SQL_SRJO_INTERSECT_JOIN (中間レベル)SQL_SRJO_LEFT_OUTER_JOIN (FIPS 移行レベル)SQL_SRJO_NATURAL_JOIN (FIPS 移行レベル)SQL_SRJO_RIGHT_OUTER_JOIN (FIPS 移行レベル)SQL_SRJO_UNION_JOIN (フルレベル)  
  
 SQL_SRJO_INNER_JOINは、**内部結合機能ではなく、INNER JOIN**構文をサポートする場合を示します。 **内部結合**構文のサポートは FIPS 移行であり、内部結合機能のサポートは**ENTRY**です。  
  
 SQL_SQL92_REVOKE(ODBC 3.0)  
 データ ソースでサポートされている **、REVOKE**ステートメントでサポートされる句を列挙する SQLUINTEGER ビットマスクです。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの隣に括弧で囲んで示されています。  
  
 データ ソースでサポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_SR_CASCADE (FIPS 移行レベル) SQL_SR_DELETE_TABLE (エントリレベル)SQL_SR_GRANT_OPTION_FOR (中間レベル) SQL_SR_INSERT_COLUMN (中間レベル)SQL_SR_INSERT_TABLE (エントリレベル) SQL_SR_REFERENCES_COLUMN (エントリーレベル)SQL_SR_REFERENCES_TABLE(エントリーレベル)SQL_SR_RESTRICT(FIPS 移行レベル)SQL_SR_SELECT_TABLE(エントリーレベル)SQL_SR_UPDATE_COLUMN(エントリーレベル)SQL_SR_UPDATE_TABLE(エントリーレベル)SQL_SR_USAGE_ON_DOMAIN (FIPS 移行レベル)SQL_SR_USAGE_ON_CHARACTER_セット (FIPS 移行レベル)SQL_SR_USAGE_ON_COLLATION (FIPS 移行レベル)SQL_SR_USAGE_ON_TRANSLATION (FIPS 移行レベル)  
  
 SQL_SQL92_ROW_VALUE_CONSTRUCTOR(ODBC 3.0)  
 **SELECT**ステートメントでサポートされている行値コンストラクター式を列挙する SQLUINTEGER ビットマスクです。 次のビットマスクを使用して、データ ソースでサポートされるオプションを決定します。  
  
 SQL_SRVC_NULLSQL_SRVC_DEFAULTSQL_SRVC_ROW_SUBQUERYSQL_SRVC_VALUE_EXPRESSION  
  
 SQL_SQL92_STRING_FUNCTIONS(ODBC 3.0)  
 SQL-92 で定義されている、ドライバーと関連データ ソースでサポートされている文字列スカラー関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる文字列関数を決定するには、次のビットマスクを使用します。  
  
 SQL_SSF_CONVERTSQL_SSF_LOWERSQL_SSF_UPPERSQL_SSF_SUBSTRINGSQL_SSF_TRANSLATESQL_SSF_TRIM_BOTHSQL_SSF_TRIM_LEADINGSQL_SSF_TRIM_TRAILING  
  
 SQL_SQL92_VALUE_EXPRESSIONS(ODBC 3.0)  
 SQL-92 で定義されている、サポートされている値式を列挙する SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの隣に括弧で囲んで示されています。  
  
 次のビットマスクを使用して、データ ソースでサポートされるオプションを決定します。  
  
 SQL_SVE_CASE (中間レベル)SQL_SVE_CAST (FIPS 移行レベル)SQL_SVE_COALESCE (中間レベル)SQL_SVE_NULLIF (中間レベル)  
  
 SQL_STANDARD_CLI_CONFORMANCE(ODBC 3.0)  
 ドライバーが準拠する CLI 標準を列挙する SQLUINTEGER ビットマスク。 次のビットマスクは、ドライバがどのレベルに準拠しているかを判断するために使用されます。  
  
 SQL_SCC_XOPEN_CLI_VERSION1: ドライバーは、オープン グループ CLI バージョン 1 に準拠しています。  
  
 SQL_SCC_ISO92_CLI: ドライバは ISO 92 CLI に準拠しています。  
  
 SQL_STATIC_CURSOR_ATTRIBUTES1(ODBC 3.0)  
 ドライバーでサポートされている静的カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の最初のサブセットが含まれています。2 番目のサブセットについては、「SQL_STATIC_CURSOR_ATTRIBUTES2」を参照してください。  
  
 サポートされる属性を決定するには、次のビットマスクを使用します。  
  
 SQL_CA1_NEXTSQL_CA1_ABSOLUTESQL_CA1_RELATIVESQL_CA1_BOOKMARKSQL_CA1_LOCK_NO_CHANGESQL_CA1_LOCK_EXCLUSIVESQL_CA1_LOCK_UNLOCKSQL_CA1_POS_POSITIONSQL_CA1_POS_UPDATESQL_CA1_POS_DELETESQL_CA1_POS_REFRESHSQL_CA1_POSITIONED_UPDATESQL_CA1_POSITIONED_DELETESQL_CA1_SELECT_FOR_UPDATESQL_CA1_BULK_ADDSQL_CA1_BULK_UPDATE_BY_BOOKMARKSQL_CA1_BULK_DELETE_BY_BOOKMARKSQL_CA1_BULK_FETCH_BY_BOOKMARK  
  
 これらのビットマスクの説明については、SQL_DYNAMIC_CURSOR_ATTRIBUTES1(および説明の「動的カーソル」の「静的カーソル」の代わりに)を参照してください。  
  
 SQL-92 中間レベル適合ドライバーは、通常、サポートされているSQL_CA1_NEXT、SQL_CA1_ABSOLUTE、およびSQL_CA1_RELATIVEオプションを返します。 これは基になる SQL サポートを直接決定しないため、ただし、SQL-92 中間レベル準拠ドライバーであっても、スクロール可能なカーソルはサポートされない場合があります。  
  
 SQL_STATIC_CURSOR_ATTRIBUTES2(ODBC 3.0)  
 ドライバーでサポートされている静的カーソルの属性を記述する SQLUINTEGER ビットマスク。 このビットマスクには、属性の 2 番目のサブセットが含まれています。最初のサブセットについては、「SQL_STATIC_CURSOR_ATTRIBUTES1」を参照してください。  
  
 サポートされる属性を決定するには、次のビットマスクを使用します。  
  
 SQL_CA2_READ_ONLY_CONCURRENCYSQL_CA2_LOCK_CONCURRENCYSQL_CA2_OPT_ROWVER_CONCURRENCYSQL_CA2_OPT_VALUES_CONCURRENCYSQL_CA2_SENSITIVITY_ADDITIONSSQL_CA2_SENSITIVITY_DELETIONSSQL_CA2_SENSITIVITY_UPDATESSQL_CA2_MAX_ROWS_SELECTSQL_CA2_MAX_ROWS_INSERTSQL_CA2_MAX_ROWS_DELETESQL_CA2_MAX_ROWS_UPDATESQL_CA2_MAX_ROWS_CATALOGSQL_CA2_MAX_ROWS_AFFECTS_ALLSQL_CA2_CRC_EXACTSQL_CA2_CRC_APPROXIMATESQL_CA2_SIMULATE_NON_UNIQUESQL_CA2_SIMULATE_TRY_UNIQUESQL_CA2_SIMULATE_UNIQUE  
  
 これらのビットマスクの説明については、SQL_DYNAMIC_CURSOR_ATTRIBUTES2を参照してください (および説明の「動的カーソル」の「静的カーソル」を置き換えてください)。  
  
 SQL_STRING_FUNCTIONS(ODBC 1.0)  
 注: 情報タイプは ODBC 1.0 で導入されました。各ビットマスクには、導入されたバージョンがラベル付けされています。  
  
 ドライバーと関連データ ソースでサポートされているスカラー文字列関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる文字列関数を決定するには、次のビットマスクを使用します。  
  
 SQL_FN_STR_ASCII (ODBC 1.0)SQL_FN_STR_BIT_LENGTH (ODBC 3.0) SQL_FN_STR_CHAR (ODBC 1.0) SQL_FN_STR_CHAR (ODBC 3.0) SQL_FN_STR_CHAR_LENGTH (ODBC 3.0) SQL_FN_STR_CHARACTER_LENGTH (ODBC 3.0) SQL_FN_STR_CONCAT (ODBC 1.0) SQL_FN_STR_DIFFERENCE (ODBC 2.0)SQL_FN_STR_INSERT (ODBC 1.0)SQL_FN_STR_LCASE (ODBC 1.0)SQL_FN_STR_LEFT (ODBC 1.0)SQL_FN_STR_LENGTH (ODBC 1.0)SQL_FN_STR_LENGTH (ODBC 1.0)SQL_FN_STR_LOCATE (ODBC 1.0) SQL_FN_STR_LTRIM (ODBC 1.0) (ODBC 1.0) SQL_FN_STR_LTRIM (ODBC 1.0)1.0) SQL_FN_STR_OCTET_LENGTH (ODBC 3.0) SQL_FN_STR_POSITION (ODBC 3.0) SQL_FN_STR_POSITION (ODBC 3.0) SQL_FN_STR_REPEAT (ODBC 1.0) SQL_FN_STR_REPLACE (ODBC 1.0) SQL_FN_STR_RIGHT (ODBC 1.0)SQL_FN_STR_RTRIM (ODBC 1.0)SQL_FN_STR_SOUNDEX (ODBC 2.0)SQL_FN_STR_SPACE (ODBC 2.0) SQL_FN_STR_SUBSTRING (ODBC 1.0) SQL_FN_STR_UCASE (ODBC 1.0) SQL_FN_STR_UCASE (ODBC 1.0)  
  
 アプリケーションが*string_exp1、* string_exp2 、 string_exp2 、*および**開始*引数を指定して**LOCATE**スカラー関数を呼び出すことができる場合、ドライバーはSQL_FN_STR_LOCATEビットマスクを返します。 アプリケーションが *、string_exp1*と*string_exp2*引数のみを指定して LOCATE スカラー関数を呼び出すことができる場合、ドライバーはSQL_FN_STR_LOCATE_2ビットマスクを返します。 **LOCATE**スカラー関数を完全にサポートしているドライバは、両方のビットマスクを返します。  
  
 (詳細については、「付録 E スカラー関数」の[文字列](../../../odbc/reference/appendixes/string-functions.md)関数を参照してください。  
  
 SQL_SUBQUERIES(ODBC 2.0)  
 サブクエリをサポートする述部を列挙する SQLUINTEGER ビットマスク。  
  
 SQL_SQ_CORRELATED_SUBQUERIESSQL_SQ_COMPARISONSQL_SQ_EXISTSSQL_SQ_INSQL_SQ_QUANTIFIED  
  
 SQL_SQ_CORRELATED_SUBQUERIESビットマスクは、サブクエリをサポートするすべての述部が相関サブクエリをサポートすることを示します。  
  
 SQL-92 エントリ レベル準拠ドライバーは、常にビットマスクを返し、これらのビットがすべて設定されます。  
  
 SQL_SYSTEM_FUNCTIONS(ODBC 1.0)  
 ドライバーと関連データ ソースでサポートされているスカラー システム関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされるシステム関数を決定するには、次のビットマスクを使用します。  
  
 SQL_FN_SYS_DBNAMESQL_FN_SYS_IFNULLSQL_FN_SYS_USERNAME  
  
 SQL_TABLE_TERM(ODBC 1.0)  
 テーブルのデータ ソース ベンダーの名前を含む文字列。たとえば、「テーブル」や「ファイル」などです。  
  
 この文字ストリングは、大文字、小文字、または混合の大文字小文字を使用できます。  
  
 SQL-92 エントリ レベル準拠ドライバーは常に "テーブル" を返します。  
  
 SQL_TIMEDATE_ADD_INTERVALS(ODBC 2.0)  
 ドライバーと、関連付けられたデータ ソースによってサポートされているタイムスタンプ間隔を列挙する SQLUINTEGER ビットマスク、 TIMESTAMPADD スカラー関数。  
  
 サポートされる間隔を決定するには、次のビットマスクを使用します。  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 FIPS 移行レベル準拠ドライバーは、常にこれらのビットがすべて設定されているビットマスクを返します。  
  
 SQL_TIMEDATE_DIFF_INTERVALS(ODBC 2.0)  
 TIMESTAMPDIFF スカラー関数のドライバーと関連データ ソースでサポートされているタイムスタンプ間隔を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる間隔を決定するには、次のビットマスクを使用します。  
  
 SQL_FN_TSI_FRAC_SECONDSQL_FN_TSI_SECONDSQL_FN_TSI_MINUTESQL_FN_TSI_HOURSQL_FN_TSI_DAYSQL_FN_TSI_WEEKSQL_FN_TSI_MONTHSQL_FN_TSI_QUARTERSQL_FN_TSI_YEAR  
  
 FIPS 移行レベル準拠ドライバーは、常にこれらのビットがすべて設定されているビットマスクを返します。  
  
 SQL_TIMEDATE_FUNCTIONS(ODBC 1.0)  
 注: 情報タイプは ODBC 1.0 で導入されました。各ビットマスクには、導入されたバージョンがラベル付けされています。  
  
 ドライバーと関連データ ソースでサポートされているスカラーの日付と時刻の関数を列挙する SQLUINTEGER ビットマスク。  
  
 サポートされる日付と時刻の関数を決定するには、次のビットマスクを使用します。  
  
 SQL_FN_TD_CURRENT_DATE odbc 3.0)SQL_FN_TD_CURRENT_TIME (ODBC 3.0) SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0 SQL_FN_TD_CURTIME) SQL_FN_TD_CURRENT_TIMESTAMP (ODBC 3.0) SQL_FN_TD_CURDATE (ODBC 1.0) SQL_FN_TD_CURDATE (ODBC 1.0) SQL_FN_TD_DAYNAME (ODBC 2.0) SQL_FN_TD_DAYOFMONTH (ODBC 1.0) SQL_FN_TD_DAYOFWEEK (ODBC 1.0) SQL_FN_TD_DAYOFWEEK (ODBC 1.0) SQL_FN_TD_DAYOFYEAR (ODBC 1.0) SQL_FN_TD_EXTRACT SQL_FN_TD_HOUR (ODBC 3.SQL_FN_TD_MINUTE 0) SQL_FN_TD_HOUR (ODBC 3.0) SQL_FN_TD_HOUR (ODBC 1.0) SQL_FN_TD_HOUR (ODBC 1.0) SQL_FN_TD_HOUR (ODBC 1.0)SQL_FN_TD_MONTH (ODBC 1.0) (ODBC SQL_FN_TD_MONTH1.0)SQL_FN_TD_MONTHNAME (ODBC 2.0) SQL_FN_TD_NOW (ODBC 1.0) SQL_FN_TD_QUARTER (ODBC 1.0) SQL_FN_TD_SECOND (ODBC 1.0) SQL_FN_TD_SECOND (ODBC 1.0) SQL_FN_TD_TIMESTAMPADD (ODBC 2.0) SQL_FN_TD_TIMESTAMPDIFF (ODBC 2.0) SQL_FN_TD_WEEK (ODBC 1.0) SQL_FN_TD_YEAR (ODBC 1.0)  
  
 SQL_TXN_CAPABLE(ODBC 1.0)  
 注: 情報タイプは ODBC 1.0 で導入されました。各戻り値には、それが導入されたバージョンが付いています。  
  
 ドライバーまたはデータ ソースでのトランザクション サポートを記述する SQLUSMALLINT 値:  
  
 SQL_TC_NONE = トランザクションはサポートされていません。 (ODBC 1.0)  
  
 SQL_TC_DML = トランザクションには、データ操作言語 (DML) ステートメント (**SELECT**、**挿入**、**更新**、**削除**) のみを含めることができます。 トランザクションでデータ定義言語 (DDL) ステートメントが発生すると、エラーが発生します。 (ODBC 1.0)  
  
 SQL_TC_DDL_COMMIT = トランザクションには DML ステートメントのみを含めることができます。 DDL ステートメント (**CREATE TABLE**、 **DROP INDEX**など ) がトランザクションで発生すると、トランザクションがコミットされます。 (ODBC 2.0)  
  
 SQL_TC_DDL_IGNORE = トランザクションには DML ステートメントのみを含めることができます。 トランザクションで DDL ステートメントが検出された場合は無視されます。 (ODBC 2.0)  
  
 SQL_TC_ALL = トランザクションには、DDL ステートメントと DML ステートメントを任意の順序で含めることができます。 (ODBC 1.0)  
  
 (SQL-92 ではトランザクションのサポートが必須であるため、SQL-92 準拠ドライバー (任意のレベル) はSQL_TC_NONE返しません。  
  
 SQL_TXN_ISOLATION_OPTION(ODBC 1.0)  
 ドライバーまたはデータ ソースから使用できるトランザクション分離レベルを列挙する SQLUINTEGER ビットマスク。  
  
 次のビットマスクをフラグと共に使用して、どのオプションがサポートされているかを決定します。  
  
 SQL_TXN_READ_UNCOMMITTEDSQL_TXN_READ_COMMITTEDSQL_TXN_REPEATABLE_READSQL_TXN_SERIALIZABLE  
  
 これらの分離レベルの説明については、SQL_DEFAULT_TXN_ISOLATIONの説明を参照してください。  
  
 トランザクション分離レベルを設定するために、アプリケーションは**SQLSetConnectAttr**を呼び出してSQL_ATTR_TXN_ISOLATION属性を設定します。 詳細については、「 [SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)」を参照してください。  
  
 SQL-92 エントリ レベル準拠ドライバーは、常にサポートされているSQL_TXN_SERIALIZABLE返します。 FIPS 移行レベル準拠ドライバーは、常にサポートされているこれらのオプションのすべてを返します。  
  
 SQL_UNION(ODBC 2.0)  
 **UNION**句のサポートを列挙する SQLUINTEGER ビットマスク:  
  
 SQL_U_UNION = データ ソースは**UNION**句をサポートします。  
  
 SQL_U_UNION_ALL = データ・ソースは**UNION**句の中で**ALL**キーワードをサポートします。 (**この場合は**、SQL_U_UNIONとSQL_U_UNION_ALLの両方が返されます。  
  
 SQL-92 エントリ レベル準拠ドライバーは、サポートされているこれらのオプションの両方を常に返します。  
  
 SQL_USER_NAME(ODBC 1.0)  
 特定のデータベースで使用される名前を持つ文字列。  
  
 SQL_XOPEN_CLI_YEAR(ODBC 3.0)  
 ODBC ドライバー マネージャーのバージョンが完全に準拠しているオープン グループ仕様の公開年を示す文字列。  
  
 SQL_ACCESSIBLE_PROCEDURES(ODBC 1.0)  
 ユーザーが**SQLProcedures によって**返されるすべてのプロシージャを実行できる場合は、"Y" という文字列を指定します。ユーザーが実行できないプロシージャが返される可能性がある場合は"N"。  
  
 SQL_ACCESSIBLE_TABLES(ODBC 1.0)  
 **SQLTables**によって返されるすべてのテーブルに対する**SELECT**権限がユーザーに保証されている場合は、"Y" という文字列を指定します。ユーザーがアクセスできないテーブルが返される可能性がある場合は"N"。  
  
 SQL_ACTIVE_ENVIRONMENTS(ODBC 3.0)  
 ドライバーがサポートできるアクティブな環境の最大数を指定する SQLUSMALLINT 値。 指定された制限がない場合、または制限が不明な場合、この値はゼロに設定されます。  
  
 SQL_AGGREGATE_FUNCTIONS(ODBC 3.0)  
 SQLUINTEGER ビットマスクの列挙関数のサポート:  
  
 SQL_AF_ALLSQL_AF_AVGSQL_AF_COUNTSQL_AF_DISTINCTSQL_AF_MAXSQL_AF_MINSQL_AF_SUM  
  
 SQL-92 エントリ レベル準拠ドライバーは、常にサポートされているこれらのオプションのすべてを返します。  
  
 SQL_ALTER_DOMAIN(ODBC 3.0)  
 データ ソースでサポートされている SQL-92 で定義されている**ALTER DOMAIN**ステートメント内の句を列挙する SQLUINTEGER ビットマスク。 SQL-92 完全レベル準拠のドライバーは常にすべてのビットマスクを返します。 "0" の戻り値は **、ALTER DOMAIN**ステートメントがサポートされないことを意味します。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの隣に括弧で囲んで示されています。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_AD_ADD_DOMAIN_CONSTRAINT = ドメイン制約の追加がサポートされています (フル レベル)  
  
 SQL_AD_ADD_DOMAIN_DEFAULT \<= ドメイン\<>設定ドメインのデフォルト節>変更がサポートされています (フルレベル)  
  
 SQL_AD_CONSTRAINT_NAME_DEFINITION \<= 制約名定義句>命名ドメイン制約 (中間レベル) に対してサポートされています。  
  
 SQL_AD_DROP_DOMAIN_CONSTRAINT \<= ドメイン制約句>削除>サポート (フル レベル)  
  
 SQL_AD_DROP_DOMAIN_DEFAULT \<= ドメイン\<>ドロップ ドメインのデフォルト句>変更>サポートされています (フル レベル)  
  
 次のビットは、ドメイン\<制約>の追加\<がサポートされている場合>サポートされる制約属性を指定します (SQL_AD_ADD_DOMAIN_CONSTRAINT ビットが設定されています)。  
  
 SQL_AD_ADD_CONSTRAINT_DEFERRABLE (フルレベル)SQL_AD_ADD_CONSTRAINT_NON_DEFERRABLE(フルレベル)SQL_AD_ADD_CONSTRAINT_INITIALLY_DEFERRED(フルレベル)SQL_AD_ADD_CONSTRAINT_INITIALLY_IMMEDIATE(フルレベル)  
  
 SQL_ALTER_TABLE(ODBC 2.0)  
 データ ソースでサポートされている**ALTER TABLE**ステートメント内の句を列挙した SQLUINTEGER ビットマスク。  
  
 この機能をサポートする必要がある SQL-92 または FIPS 準拠レベルは、各ビットマスクの隣に括弧で囲んで示されています。  
  
 サポートされる句を決定するには、次のビットマスクを使用します。  
  
 SQL_AT_ADD_COLUMN_COLLATION \<= 列>の追加句がサポートされており、列照合順序 (フル レベル) を指定する機能 (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_DEFAULT \<= 列>節の追加がサポートされ、列のデフォルト (FIPS 移行レベル) を指定する機能 (ODBC 3.0)  
  
 SQL_AT_ADD_COLUMN_SINGLE \<= 列>の追加がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_ADD_CONSTRAINT \<= 列>節の追加がサポートされ、列制約 (FIPS 移行レベル) を指定する機能 (ODBC 3.0)  
  
 SQL_AT_ADD_TABLE_CONSTRAINT \<= テーブル制約>追加句がサポートされています (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_CONSTRAINT_NAME_DEFINITION \<= 制約名定義>列およびテーブルの制約の命名 (中間レベル) (ODBC 3.0) でサポートされています。  
  
 SQL_AT_DROP_COLUMN_CASCADE \<= カスケード>ドロップ列がサポートされている (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_DEFAULT \<= 列\<>変更>列のデフォルト節がサポートされます (中間レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_COLUMN_RESTRICT \<= RESTRICT>ドロップ列がサポートされている (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_CASCADE (ODBC 3.0)  
  
 SQL_AT_DROP_TABLE_CONSTRAINT_RESTRICT \<= RESTRICT>ドロップ列がサポートされている (FIPS 移行レベル) (ODBC 3.0)  
  
 SQL_AT_SET_COLUMN_DEFAULT \<= 列\<の変更>列のデフォルト節>がサポートされている (中間レベル) (ODBC 3.0)  
  
 次のビットは、列\<制約またはテーブル制約の指定がサポートされている場合 (SQL_AT_ADD_CONSTRAINTビットが設定されている) 場合に>サポート制約属性を指定します。  
  
 SQL_AT_CONSTRAINT_INITIALLY_DEFERRED (フル レベル) (ODBC 3.0) SQL_AT_CONSTRAINT_INITIALLY_IMMEDIATE (フル レベル) (ODBC 3.0)SQL_AT_CONSTRAINT_DEFERRABLE (フル レベル) (ODBC 3.0)SQL_AT_CONSTRAINT_NON_DEFERRABLE (フル レベル) (ODBC 3.0) (ODBC 3.0)  
  
 SQL_ASYNC_MODE(ODBC 3.0)  
 ドライバーでの非同期サポートのレベルを示す SQLUINTEGER 値:  
  
 SQL_AM_CONNECTION = 接続レベルの非同期実行がサポートされています。 指定された接続ハンドルに関連付けられているすべてのステートメント ハンドルが非同期モードであるか、すべて同期モードです。 同じ接続の別のステートメント ハンドルが同期モードである間は、接続のステートメント ハンドルを非同期モードにすることはできません。  
  
 SQL_AM_STATEMENT = ステートメント レベルの非同期実行がサポートされています。 接続ハンドルに関連付けられているステートメント ハンドルの中には、非同期モードにできるものもありますが、同じ接続の他のステートメント ハンドルは同期モードです。  
  
 SQL_AM_NONE = 非同期モードはサポートされていません。  
  
 SQL_BATCH_ROW_COUNT (ODBC 3.0)  
 行数の可用性に関するドライバーの動作を列挙する SQLUINTEGER ビットマスク。 以下のビットマスクは、情報タイプと共に使用されます。  
  
 SQL_BRC_ROLLED_UP = 連続する INSERT、DELETE、または UPDATE ステートメントの行カウントは、1 つにロールアップされます。 このビットが設定されていない場合、各ステートメントに対して行数が使用可能になります。  
  
 SQL_BRC_PROCEDURES = 行数がある場合は、ストアド プロシージャでバッチが実行されるときに使用できます。 行数が使用可能な場合は、SQL_BRC_ROLLED_UPビットに応じて、行数をロールアップしたり個別に使用したりできます。  
  
 SQL_BRC_EXPLICIT = 行数がある場合は、 **SQLExecute**または**SQLExecDirect**を呼び出してバッチを直接実行するときに使用できます。 行数が使用可能な場合は、SQL_BRC_ROLLED_UPビットに応じて、行数をロールアップしたり個別に使用したりできます。  
  
## <a name="example"></a>例  
 **サポート**されているオプションの一覧を SQLUINTEGER ビットマスクとして **InfoValuePtr*で返します。 各オプションのビットマスクは、オプションがサポートされているかどうかを判断するためにフラグと共に使用されます。  
  
 たとえば、アプリケーションは、次のコードを使用して、接続に関連付けられているドライバーで SUBSTRING スカラー関数がサポートされているかどうかを判断できます。  
  
 **SQLGetInfo**を使用する別の例については、「 [SQLTables 関数](../../../odbc/reference/syntax/sqltables-function.md)」を参照してください。  
  
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
  
 データ ソースのデータ型に関する情報を返す  
 [SQLGetTypeInfo 関数](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
