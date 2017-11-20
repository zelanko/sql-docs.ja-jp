---
title: "SQLForeignKeys 関数 |Microsoft ドキュメント"
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
- SQLForeignKeys
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLForeignKeys
helpviewer_keywords:
- SQLForeignKeys function [ODBC]
ms.assetid: 07f3f645-f643-4d39-9a10-70a72f24e608
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0d56fd87c4c9612fb520b1a54b9d0c2cab645223
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlforeignkeys-function"></a>SQLForeignKeys 関数
**準拠**  
 バージョンが導入されています ODBC 1.0 標準への準拠: ODBC。  
  
 **概要**  
 **SQLForeignKeys**返すことができます。  
  
-   指定されたテーブル (列指定されたテーブル内の他のテーブルの主キーを参照している) の外部キーの一覧。  
  
-   指定されたテーブルの主キーを参照している他のテーブルの外部キーの一覧。  
  
 ドライバーでは、結果セットとして指定されたステートメントにそれぞれのリストを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLForeignKeys(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      PKCatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      PKSchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      PKTableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      FKCatalogName,  
     SQLSMALLINT    NameLength4,  
     SQLCHAR *      FKSchemaName,  
     SQLSMALLINT    NameLength5,  
     SQLCHAR *      FKTableName,  
     SQLSMALLINT    NameLength6);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *PKCatalogName*  
 [入力]主キー テーブルのカタログ名。 ドライバーは、いくつかのテーブルは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のカタログをサポートしている場合 ("") のカタログがないテーブルを表します。 *PKCatalogName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*PKCatalogName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *PKCatalogName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。 詳細については、次を参照してください。[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)です。  
  
 *NameLength1*  
 [入力]長さ **PKCatalogName*、文字数。  
  
 *PKSchemaName*  
 [入力]主キー テーブルのスキーマ名です。 ドライバーは、いくつかのテーブルは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のスキーマをサポートしている場合 ("") のスキーマはありません。 それらのテーブルを表します。 *PKSchemaName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*PKSchemaName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *PKSchemaName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength2*  
 [入力]長さ **PKSchemaName*、文字数。  
  
 *PKTableName*  
 [入力]主キー テーブルの名前です。 *PKTableName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*PKTableName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *PKTableName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength3*  
 [入力]長さ **PKTableName*、文字数。  
  
 *FKCatalogName*  
 [入力]外部キー テーブルのカタログ名。 ドライバーは、いくつかのテーブルは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のカタログをサポートしている場合 ("") のカタログがないテーブルを表します。 *FKCatalogName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*FKCatalogName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *FKCatalogName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength4*  
 [入力]長さ **FKCatalogName*、文字数。  
  
 *FKSchemaName*  
 [入力]外部キー テーブルのスキーマ名です。 ドライバーは、いくつかのテーブルは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のスキーマをサポートしている場合 ("") のスキーマはありません。 それらのテーブルを表します。 *FKSchemaName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*FKSchemaName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *FKSchemaName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength5*  
 [入力]長さ **FKSchemaName*、文字数。  
  
 *FKTableName*  
 [入力]外部キー テーブルの名前です。 *FKTableName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*FKTableName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *FKTableName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength6*  
 [入力]長さ **FKTableName*、文字数。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLForeignKeys** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* SQL の_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLForeignKeys**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|24000|カーソル状態が無効|カーソルが開いて、 *StatementHandle*、および**SQLFetch**または**SQLFetchScroll**が呼び出されました。 このエラーが返されます、ドライバー マネージャーによって**SQLFetch**または**SQLFetchScroll** 、SQL_NO_DATA が返されなかったと場合、ドライバーによって返される**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されました。<br /><br /> カーソルが開いて、 *StatementHandle*が**SQLFetch**または**SQLFetchScroll**が呼び出されていません。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックが原因ロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*関数が呼び出されたし、再度、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY009|無効な null ポインターの使用|(DM) 引数*PKTableName*と*FKTableName*が両方とも null ポインターです。<br /><br /> SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定された、 *FKCatalogName*または*PKCatalogName*引数が null ポインターの場合と、SQL_CATALOG_NAME*情報の種類*カタログ名を返しますがサポートされています。<br /><br /> (DM) SQL_ATTR_METADATA_ID ステートメント属性が SQL_TRUE に設定、および*FKSchemaName*、 *PKSchemaName*、 *FKTableName*、または*PKTableName*引数が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 SQLForeignKeys 関数が呼び出されたときに、この非同期関数が実行されています。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) 名長の引数のいずれかの値が 0 より小さい値は SQL_NTS に等しくありません。|  
|||名前の長さの引数のいずれかの値には、対応する名前の最大長の値を超えています。 (「コメント」を参照してください)|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|カタログ名が指定あり、ドライバーまたはデータ ソースがカタログをサポートしていません。<br /><br /> スキーマ名が指定された、およびドライバーまたはデータ ソースがスキーマをサポートしていません。|  
|||ドライバーまたはデータ ソースによっては、SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE ステートメント属性の現在の設定の組み合わせはサポートされていません。<br /><br /> SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されており、SQL_ATTR_CURSOR_TYPE ステートメント属性は、ドライバーがブックマークにできないカーソルの種類に設定されました。|  
|HYT00|タイムアウトが発生しました|クエリのタイムアウト時間は、データ ソースには、結果セットが返される前に期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtAttr**、SQL_ATTR_QUERY_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 この関数によって返される情報を使用する方法については、次を参照してください。[カタログ データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)です。  
  
 場合\* *PKTableName*テーブル名を含む**SQLForeignKeys**指定したテーブルの主キーとそれを参照するすべての外部キーを含む結果セットを返します。 その他のテーブルの外部キーの一覧では、指定されたテーブルでの unique 制約をポイントする外部キーは含まれません。  
  
 場合\* *FKTableName*テーブル名を含む**SQLForeignKeys**を他のテーブルの主キーを指す指定のテーブル内のすべての外部キーを含む結果セットを返すと、他の参照先のテーブルの主キー。 指定したテーブルの外部キーの一覧には、他のテーブルで unique 制約を参照する外部キーがありません。  
  
 両方\* *PKTableName*と\* *FKTableName*テーブル名を含む**SQLForeignKeys**指定されたテーブルで外部キーを返します\* *FKTableName*で指定されたテーブルの主キーを参照する **PKTableName*です。 1 つのキーは、最大でこのする必要があります。  
  
> [!NOTE]  
>  一般的な使用、引数、および ODBC カタログ関数の返されたデータの詳細については、次を参照してください。[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)です。  
  
 **SQLForeignKeys**結果の標準的な結果セットとして返します。 主キーに関連付けられている外部キーが要求される場合、結果セットは FKTABLE_CAT、FKTABLE_SCHEM、FKTABLE_NAME、KEY_SEQ して並んでいます。 外部キーに関連付けられている主キーが要求される場合、結果セットは PKTABLE_CAT、PKTABLE_SCHEM、PKTABLE_NAME、および KEY_SEQ によって並べ替えられます。 次の表には、結果セット内の列が一覧表示します。  
  
 Varchar 型の列の長さは、テーブルには表示されません。実際の長さは、データ ソースに依存します。 PKTABLE_CAT または FKTABLE_CAT、PKTABLE_SCHEM または FKTABLE_SCHEM の実際の長さを確認するのに PKTABLE_NAME または FKTABLE_NAME、および PKCOLUMN_NAME FKCOLUMN_NAME 列では、アプリケーションが呼び出して**SQLGetInfo** SQL_MAX_ とCATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、SQL_MAX_TABLE_NAME_LEN、および SQL_MAX_COLUMN_NAME_LEN オプションです。  
  
 ODBC 3 の名前を変更した次の列*。 x。* 列名の変更では、列番号により、アプリケーション バインドのための下位互換性は影響しません。  
  
|ODBC 2.0 列|ODBC 3*.x*列|  
|---------------------|-----------------------|  
|PKTABLE_QUALIFIER|PKTABLE_CAT|  
|PKTABLE_OWNER|PKTABLE_SCHEM|  
|FKTABLE_QUALIFIER|FK_TABLE_CAT|  
|FKTABLE_OWNER|FKTABLE_SCHEM|  
  
 次の表には、結果セット内の列が一覧表示します。 ドライバーでは、列 14 (注釈) を超える追加の列を定義できます。 アプリケーションは、結果の明示的な位置を表す序数を指定する代わりにセットの末尾からカウント ダウンしてドライバー固有の列へのアクセスを得る必要があります。 詳細については、次を参照してください。[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)です。  
  
|列名|列番号|データ型|コメント|  
|-----------------|-------------------|---------------|--------------|  
|PKTABLE_CAT (ODBC 1.0)|1|Varchar|主キー テーブルのカタログ名です。データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどにいくつかのテーブルが、他のカタログをサポートする場合 ("")、それらのテーブルのカタログがないです。|  
|PKTABLE_SCHEM (ODBC 1.0)|2|Varchar|主キー テーブルのスキーマ名です。データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどにいくつかのテーブルが、他のスキーマをサポートする場合 ("")、それらのテーブルのスキーマがないです。|  
|PKTABLE_NAME (ODBC 1.0)|3|NULL でない Varchar|主キー テーブルの名前です。|  
|PKCOLUMN_NAME (ODBC 1.0)|4|NULL でない Varchar|主キー列の名前です。 ドライバーでは、名前がない列の空の文字列を返します。|  
|FKTABLE_CAT (ODBC 1.0)|5|Varchar|外部キー テーブルのカタログ名です。データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどにいくつかのテーブルが、他のカタログをサポートする場合 ("")、それらのテーブルのカタログがないです。|  
|FKTABLE_SCHEM (ODBC 1.0)|6|Varchar|外部キー テーブルのスキーマ名です。データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどにいくつかのテーブルが、他のスキーマをサポートする場合 ("")、それらのテーブルのスキーマがないです。|  
|FKTABLE_NAME (ODBC 1.0)|7|NULL でない Varchar|外部キー テーブルの名前です。|  
|FKCOLUMN_NAME (ODBC 1.0)|8|NULL でない Varchar|外部キー列の名前です。 ドライバーでは、名前がない列の空の文字列を返します。|  
|KEY_SEQ (ODBC 1.0)|9|Smallint (NULL 以外)|(1 から始まる) キーの列のシーケンス番号。|  
|句 (ODBC 1.0)|10|Smallint|SQL の操作時に、外部キーに適用されるアクション**更新**です。 次の値のいずれかのことができます。 (参照先のテーブルが主キーを持つテーブル以外の場合は、参照元テーブルが外部キーを持つテーブルです。)<br /><br /> SQL_CASCADE: 参照先のテーブルの主キーが更新されると、参照元のテーブルの外部キーも更新されます。<br /><br /> SQL_NO_ACTION: 場合の主キーの更新プログラム、参照先のテーブル参照が発生する、"未解決"参照テーブル (つまり、参照元のテーブル内の行がないための対応する参照先のテーブルで)、更新が拒否されました。 参照元のテーブルの外部キーの更新プログラムは、参照先のテーブルの主キーの値として存在しない値を発生させることは、更新プログラムは拒否されます。 (この操作は、ODBC 2 で SQL_RESTRICT アクションと同じ*.x*)。<br /><br /> SQL_SET_NULL: 主キーの 1 つまたは複数のコンポーネントが変更されているように、参照されるテーブルの 1 つまたは複数の行が更新されると、コンポーネント、外部キー参照テーブルの主キーの変更されたコンポーネントに対応する設定します。参照元のテーブルのすべての一致する行で NULL にします。<br /><br /> SQL_SET_DEFAULT: 主キーの 1 つまたは複数のコンポーネントが変更されているように、参照されるテーブルの 1 つまたは複数の行が更新されると、主キーの変更されたコンポーネントに対応する参照テーブルの外部キーのコンポーネントは、します。参照元のテーブルのすべての一致する行の該当する既定値に設定します。<br /><br /> データ ソースに適用されない場合は NULL です。|  
|DELETE_RULE (ODBC 1.0)|11|Smallint|SQL の操作時に、外部キーに適用されるアクション**削除**です。 次の値のいずれかのことができます。 (参照先のテーブルが主キーを持つテーブル以外の場合は、参照元テーブルが外部キーを持つテーブルです。)<br /><br /> SQL_CASCADE: 参照先のテーブル内の行が削除されると、参照元テーブル内のすべての一致する行も削除されます。<br /><br /> SQL_NO_ACTION: 場合内の行を削除してから参照先のテーブル参照が発生する、"未解決"参照テーブル (つまり、参照元のテーブル内の行がないための対応する参照先のテーブルで)、更新が拒否されました。 (この操作は、ODBC 2 で SQL_RESTRICT アクションと同じ*.x*)。<br /><br /> SQL_SET_NULL: 参照先のテーブル内の 1 つまたは複数の行が削除されると、参照元のテーブルの外部キーの各コンポーネントが NULL に設定、参照元テーブルのすべての一致する行の。<br /><br /> SQL_SET_DEFAULT: 参照先のテーブル内の 1 つまたは複数の行が削除されると、参照元のテーブルの外部キーの各コンポーネントは参照元のテーブルのすべての一致する行の該当する既定値に設定します。<br /><br /> データ ソースに適用されない場合は NULL です。|  
|FK_NAME (ODBC 2.0)|12|Varchar|外部キーの名前。 データ ソースに適用されない場合は NULL です。|  
|PK_NAME (ODBC 2.0)|13|Varchar|主キーの名前。 データ ソースに適用されない場合は NULL です。|  
|DEFERRABILITY (ODBC 3.0)|14|Smallint|度を SQL_NOT_DEFERRABLE です。|  
  
## <a name="code-example"></a>コード例  
 次の表にあるよう、この例は、注文、線、および顧客をという名前の 3 つのテーブルを使用します。  
  
|ORDERS|行|顧客|  
|------------|-----------|---------------|  
|ORDERID|ORDERID|CUSTID|  
|CUSTID|行|NAME|  
|OPENDATE|PARTID|アドレス|  
|販売員|数量|電話|  
|STATUS|||  
  
 ORDERS テーブルでは、CUSTID は、先に、販売が行われていない顧客を識別します。 CUSTOMERS テーブル内の CUSTID を参照する外部キーです。  
  
 行の表では、ORDERID は、行項目が関連付けられている販売注文を識別します。 これは、ORDERS テーブルの ORDERID に参照する外部キーです。  
  
 この例では**SQLPrimaryKeys** ORDERS テーブルの主キーを取得します。 結果セットが 1 つの行には重要な列は、次の表に表示されます。  
  
|TABLE_NAME|COLUMN_NAME|KEY_SEQ|  
|-----------------|------------------|--------------|  
|ORDERS|ORDERID|1|  
  
 この例では次に、 **SQLForeignKeys** ORDERS テーブルの主キーを参照する他のテーブル内の外部キーを取得します。 結果セットが 1 つの行には重要な列は、次の表に表示されます。  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|ORDERS|CUSTID|行|CUSTID|1|  
  
 この例では最後に、 **SQLForeignKeys**を他のテーブルの主キーを参照する ORDERS テーブルの外部キーを取得します。 結果セットが 1 つの行には重要な列は、次の表に表示されます。  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|顧客|CUSTID|ORDERS|CUSTID|1|  
  
```  
#define TAB_LEN SQL_MAX_TABLE_NAME_LEN + 1  
#define COL_LEN SQL_MAX_COLUMN_NAME_LEN + 1  
  
LPSTR   szTable;              /* Table to display */  
  
UCHAR szPkTable[TAB_LEN];   /* Primary key table name */  
UCHAR szFkTable[TAB_LEN];   /* Foreign key table name */  
UCHAR szPkCol[COL_LEN];     /* Primary key column */  
UCHAR szFkCol[COL_LEN];     /* Foreign key column */  
  
SQLHSTMT      hstmt;  
SQLINTEGER    cbPkTable, cbPkCol, cbFkTable, cbFkCol, cbKeySeq;  
SQLSMALLINT   iKeySeq;  
SQLRETURN     retcode;  
  
// Bind the columns that describe the primary and foreign keys.  
// Ignore the table schema, name, and catalog for this example.  
  
SQLBindCol(hstmt, 3, SQL_C_CHAR, szPkTable, TAB_LEN, &cbPkTable);  
SQLBindCol(hstmt, 4, SQL_C_CHAR, szPkCol, COL_LEN, &cbPkCol);  
SQLBindCol(hstmt, 5, SQL_C_SSHORT, &iKeySeq, TAB_LEN, &cbKeySeq);  
SQLBindCol(hstmt, 7, SQL_C_CHAR, szFkTable, TAB_LEN, &cbFkTable);  
SQLBindCol(hstmt, 8, SQL_C_CHAR, szFkCol, COL_LEN, &cbFkCol);  
  
strcpy_s(szTable, sizeof(szTable), "ORDERS");  
  
/* Get the names of the columns in the primary key. */  
  
retcode = SQLPrimaryKeys(hstmt,  
         NULL, 0,             /* Catalog name */  
         NULL, 0,             /* Schema name */  
         szTable, SQL_NTS);   /* Table name */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL SUCCESS_WITH_INFO)) {  
  
   /* Fetch and display the result set. This will be a list of the */  
   /* columns in the primary key of the ORDERS table. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "Table: %s Column: %s Key Seq: %hd \n", szPkTable, szPkCol,  
      iKeySeq);  
}  
  
/* Close the cursor (the hstmt is still allocated). */  
  
SQLFreeStmt(hstmt, SQL_CLOSE);  
  
/* Get all the foreign keys that refer to ORDERS primary key.*/   
  
retcode = SQLForeignKeys(hstmt,  
         NULL, 0,            /* Primary catalog */  
         NULL, 0,            /* Primary schema */  
         szTable, SQL_NTS,   /* Primary table */  
         NULL, 0,            /* Foreign catalog */  
         NULL, 0,            /* Foreign schema */  
         NULL, 0);           /* Foreign table */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {  
  
/* Fetch and display the result set. This will be all of the */  
/* foreign keys in other tables that refer to the ORDERS */  
/* primary key. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "%-s ( %-s ) <-- %-s ( %-s )\n", szPkTable,  
               szPkCol, szFkTable, szFkCol);  
}  
  
/* Close the cursor (the hstmt is still allocated). */  
  
SQLFreeStmt(hstmt, SQL_CLOSE);  
  
/* Get all the foreign keys in the ORDERS table. */  
  
retcode = SQLForeignKeys(hstmt,  
         NULL, 0,             /* Primary catalog */  
         NULL, 0,             /* Primary schema */  
         NULL, 0,             /* Primary table */  
         NULL, 0,             /* Foreign catalog */  
         NULL, 0,             /* Foreign schema */  
         szTable, SQL_NTS);   /* Foreign table */  
  
while ((retcode == SQL_SUCCESS) || (retcode == SQL_SUCCESS_WITH_INFO)) {  
  
/* Fetch and display the result set. This will be all of the */  
/* primary keys in other tables that are referred to by foreign */  
/* keys in the ORDERS table. */  
  
   retcode = SQLFetch(hstmt);  
   if (retcode == SQL_SUCCESS || retcode == SQL_SUCCESS_WITH_INFO)  
      fprintf(out, "%-s ( %-s )--> %-s ( %-s )\n", szFkTable, szFkCol, szPkTable, szPkCol);  
}  
  
/* Free the hstmt. */  
SQLFreeStmt(hstmt, SQL_DROP);  
```  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|1 つの行または順方向専用の方向にデータのブロックをフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|主キーの列値を返す|[SQLPrimaryKeys 関数](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
|テーブルの統計情報とインデックスを返す|[SQLStatistics 関数](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

