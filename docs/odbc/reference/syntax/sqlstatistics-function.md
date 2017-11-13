---
title: "SQLStatistics 関数 |Microsoft ドキュメント"
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
- SQLStatistics
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLStatistics
helpviewer_keywords:
- SQLStatistics function [ODBC]
ms.assetid: 45210682-cfea-4e5d-9951-bcf1cbe10f41
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 664c3c439eacc7bfa5b5b1d59b8421f8067c3376
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlstatistics-function"></a>SQLStatistics 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLStatistics** 1 つのテーブルとテーブルに関連付けられているインデックスに関する統計情報の一覧を取得します。 ドライバーは、情報の結果セットとしてを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLStatistics(  
     SQLHSTMT        StatementHandle,  
     SQLCHAR *       CatalogName,  
     SQLSMALLINT     NameLength1,  
     SQLCHAR *       SchemaName,  
     SQLSMALLINT     NameLength2,  
     SQLCHAR *       TableName,  
     SQLSMALLINT     NameLength3,  
     SQLUSMALLINT    Unique,  
     SQLUSMALLINT    Reserved);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *カタログ名*  
 [入力]カタログの名前。 ドライバーは、いくつかのテーブルは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のカタログをサポートしている場合 ("") これらのテーブルのカタログがないことを示します。 *CatalogName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*CatalogName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *CatalogName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。 詳細については、次を参照してください。[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)です。  
  
 *NameLength1*  
 [入力]文字の長さ **CatalogName*です。  
  
 *スキーマ名*  
 [入力]スキーマ名です。 ドライバーは、いくつかのテーブルは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のスキーマをサポートしている場合 ("") これらのテーブルのスキーマがないことを示します。 *SchemaName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*SchemaName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *SchemaName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength2*  
 [入力]文字の長さ **SchemaName*です。  
  
 *テーブル名*  
 [入力]テーブル名です。 この引数は、null ポインターにすることはできません。 *SchemaName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*TableName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *TableName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength3*  
 [入力]文字の長さ **TableName*です。  
  
 *[一意]*  
 [入力]インデックスの種類: SQL_INDEX_UNIQUE または SQL_INDEX_ALL です。  
  
 *予約されています*  
 [入力]結果セットの基数およびページの列の重要度を示します。 次のオプションに影響を与える基数およびページの列のみです。 戻り値基数およびページは返されません場合でも、インデックスの情報が返されます。  
  
 SQL_ENSURE では、ドライバーが統計を無条件に取得することを要求します。 (ドライバーのみ、Open Group 標準に準拠しているし、ODBC 拡張機能をサポートしていませんができなく SQL_ENSURE をサポートするためにします。)  
  
 SQL_QUICK では、サーバーからすぐに使用できる場合に、ドライバーで基数とページを取得するを要求します。 この場合、ドライバーで取得される値が最新であるかどうかは保証されません。 (ODBC 3 から SQL_QUICK 動作を常に取得は、Open Group 標準に記述されたアプリケーションを*.x*-準拠のドライバーです)。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLStatistics** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLStatistics**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|24000|カーソル状態が無効|カーソルが開いて、 *StatementHandle*、および**SQLFetch**または**SQLFetchScroll**が呼び出されました。 このエラーが返されます、ドライバー マネージャーによって**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されなかったと場合、ドライバーによって返される**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されました。<br /><br /> カーソルが開いて、 *StatementHandle*が**SQLFetch**または**SQLFetchScroll**が呼び出されていません。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックが原因ロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*関数が呼び出されたし、再度、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY009|無効な null ポインターの使用|*TableName*引数が null ポインターでした。<br /><br /> SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定された、 *CatalogName*引数が null ポインターの場合と、SQL_CATALOG_NAME*情報の種類*カタログ名を返しますがサポートされています。<br /><br /> (DM) SQL_ATTR_METADATA_ID ステートメント属性が SQL_TRUE に設定、および*SchemaName*引数が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLStatistics**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) 名長の引数のいずれかの値が 0 より小さい値は SQL_NTS に等しくありません。<br /><br /> 名前の長さの引数のいずれかの値には、対応する名前の最大長の値を超えています。|  
|HY100|一意オプションの範囲外の型|(DM) に無効な*Unique*値が指定されました。|  
|HY101|範囲外の正確度オプションの型|(DM) に無効な*占有*値が指定されました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|カタログが指定されていると、ドライバーまたはデータ ソースがカタログをサポートしていません。<br /><br /> スキーマが指定し、ドライバーまたはデータ ソースがスキーマをサポートしていません。<br /><br /> ドライバーまたはデータ ソースによっては、SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE ステートメント属性の現在の設定の組み合わせはサポートされていません。<br /><br /> SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されており、SQL_ATTR_CURSOR_TYPE ステートメント属性は、ドライバーがブックマークにできないカーソルの種類に設定されました。|  
|HYT00|タイムアウトが発生しました|要求された結果セットが返されるデータ ソースの前に、クエリのタイムアウト期間が期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtAttr**、SQL_ATTR_QUERY_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 **SQLStatistics** NON_UNIQUE、種類、INDEX_QUALIFIER、INDEX_NAME、ORDINAL_POSITION によって順序付け、標準的な結果セットとして 1 つのテーブルに関する情報を返します。 結果セットは、統計情報 (結果セットの基数およびページの列) 内のテーブルの各インデックスに関する情報を結合します。 この情報の使用方法については、次を参照してください。[カタログ データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)です。  
  
 TABLE_CAT、TABLE_SCHEM、TABLE_NAME、COLUMN_NAME の各列の実際の長さを決定するには、アプリケーションが呼び出すことができます**SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、SQL_MAX_TABLE_NAME_LEN、および SQL_MAX_COLUMN_NAME_LEN オプション。  
  
> [!NOTE]  
>  一般的な使用、引数、および ODBC カタログ関数の返されたデータの詳細については、次を参照してください。[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)です。  
  
 ODBC 3 の名前を変更した次の列*.x*です。 列名の変更では、列番号により、アプリケーション バインドのための下位互換性は影響しません。  
  
|ODBC 2.0 列|ODBC 3*.x*列|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|SEQ_IN_INDEX|ORDINAL_POSITION|  
|COLLATION|ASC_OR_DESC|  
  
 次の表には、結果セット内の列が一覧表示します。 ドライバーでは、列 (FILTER_CONDITION) 13 を超える追加の列を定義できます。 アプリケーションは、結果の明示的な位置を表す序数を指定する代わりにセットの末尾からカウント ダウンしてドライバー固有の列へのアクセスを得る必要があります。 詳細については、次を参照してください。[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)です。  
  
|列名|列番号|データ型|コメント|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|統計またはインデックスを適用する; テーブルのカタログ名データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどにいくつかのテーブルが、他のカタログをサポートする場合 ("")、それらのテーブルのカタログがないです。|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|統計またはインデックスを適用する; テーブルのスキーマ名データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどにいくつかのテーブルが、他のスキーマをサポートする場合 ("")、それらのテーブルのスキーマがないです。|  
|TABLE_NAME (ODBC 1.0)|3|NULL でない Varchar|統計またはインデックスを適用するテーブルのテーブル名です。|  
|NON_UNIQUE (ODBC 1.0)|4|Smallint|インデックスでは重複する値が許可されないかどうかを示します。<br /><br /> SQL_TRUE 場合は、インデックス値が一意でなくなることができます。<br /><br /> SQL_FALSE 場合は、インデックス値を一意にする必要があります。<br /><br /> 型が SQL_TABLE_STAT の場合は、NULL が返されます。|  
|INDEX_QUALIFIER (ODBC 1.0)|5|Varchar|インデックスを修飾するために使用されている識別子という名前を行うと、 **DROP INDEX**です。インデックス修飾子は、データ ソースによってサポートされていない場合、または型が SQL_TABLE_STAT の場合は、NULL が返されます。 この列に null 以外の値が返される場合はインデックス名を修飾するために使用する必要があります、 **DROP INDEX**ステートメントです。 それ以外の場合、TABLE_SCHEM はインデックス名を修飾するために使用必要があります。|  
|INDEX_NAME (ODBC 1.0)|6|Varchar|インデックスの名前です。型が SQL_TABLE_STAT の場合は、NULL が返されます。|  
|型 (ODBC 1.0)|7|Smallint (NULL 以外)|返される情報の種類です。<br /><br /> SQL_TABLE_STAT では、(基数やページの列) のテーブルの統計情報を示します。<br /><br /> SQL_INDEX_BTREE では、B ツリー インデックスを示します。<br /><br /> SQL_INDEX_CLUSTERED では、クラスター化インデックスを示します。<br /><br /> SQL_INDEX_CONTENT では、コンテンツ インデックスを示します。<br /><br /> SQL_INDEX_HASHED では、ハッシュ インデックスを示します。<br /><br /> SQL_INDEX_OTHER では、別の種類のインデックスを示します。|  
|ORDINAL_POSITION (ODBC 1.0)|8|Smallint|(1 から始まります)。 インデックス内の列のシーケンス番号型が SQL_TABLE_STAT の場合は、NULL が返されます。|  
|COLUMN_NAME (ODBC 1.0)|9|Varchar|列名 列が式に基づいている場合など、給与 + 利点、式が返されます。式が決定できない場合は、空の文字列が返されます。 型が SQL_TABLE_STAT の場合は、NULL が返されます。|  
|ASC_OR_DESC (ODBC 1.0)|10|Char (1)|列のシーケンスを並べ替える: 昇順; の"A"降順以外の場合に、"D"列の並べ替え順序が、データ ソースによってサポートされていない場合、または型が SQL_TABLE_STAT の場合は、NULL が返されます。|  
|基数 (ODBC 1.0)|11|Integer|テーブルまたはインデックスの基数型が SQL_TABLE_STAT 以外の場合、テーブル内の行の数型は SQL_TABLE_STAT; がない場合、インデックスの一意の値の数データ ソースから値が使用できない場合は、NULL が返されます。|  
|ページ (ODBC 1.0)|12|Integer|インデックスまたはテーブルを格納するために使用ページ数種類は SQL_TABLE_STAT; 場合、テーブルのページ数型は SQL_TABLE_STAT; がない場合、インデックスのページ数データ ソースから値が使用できない場合、またはデータ ソースに適用されない場合は、NULL が返されます。|  
|FILTER_CONDITION (ODBC 2.0)|13|Varchar|これは、フィルター条件の給与など、インデックスがフィルター選択されたインデックスの場合は、> 30000 です。フィルター条件を特定できない場合、空の文字列です。<br /><br /> インデックスは、フィルター選択されたインデックスではない場合は、NULL、確認できないかどうか、インデックスがフィルター選択されたインデックス、または型が SQL_TABLE_STAT です。|  
  
 結果セット内の行は、テーブルに対応している場合、ドライバーは SQL_TABLE_STAT の種類を設定し、NON_UNIQUE、INDEX_QUALIFIER、INDEX_NAME、ORDINAL_POSITION、COLUMN_NAME、および ASC_OR_DESC を NULL に設定します。 基数やページ利用できない場合、データ ソースから、ドライバーはそれらを NULL に設定します。  
  
## <a name="code-example"></a>コード例  
 同様の関数のコード例では、次を参照してください。 [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|1 つの行または順方向専用の方向にデータのブロックをフェッチしています。|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|外部キーの列値を返す|[SQLForeignKeys 関数](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|  
|主キーの列値を返す|[SQLPrimaryKeys 関数](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

