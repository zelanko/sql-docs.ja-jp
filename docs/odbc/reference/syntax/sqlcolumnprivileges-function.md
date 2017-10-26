---
title: "SQLColumnPrivileges 関数 |Microsoft ドキュメント"
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
- SQLColumnPrivileges
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLColumnPrivileges
helpviewer_keywords:
- SQLColumnPrivileges function [ODBC]
ms.assetid: ef233d9a-6ed5-4986-9d42-5e0b1a79fb6e
caps.latest.revision: 20
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b9fa1af8ad7cc84b69f3e54e7f1f7f911880bb25
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlcolumnprivileges-function"></a>SQLColumnPrivileges 関数
**準拠**  
 バージョンが導入されています ODBC 1.0 標準への準拠: ODBC。  
  
 **概要**  
 **SQLColumnPrivileges**列と、指定したテーブルの関連する権限の一覧を返します。 ドライバーは結果セットとして指定した情報を返します*StatementHandle*です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLColumnPrivileges(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     TableName,  
     SQLSMALLINT   NameLength3,  
     SQLCHAR *     ColumnName,  
     SQLSMALLINT   NameLength4);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *カタログ名*  
 [入力]カタログの名前。 ドライバー、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他が、一部のカタログ名をサポートする場合 ("") の名前を持たないこれらのカタログを表します。 *CatalogName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*CatalogName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *CatalogName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。 詳細については、次を参照してください。[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)です。  
  
 *NameLength1*  
 [入力]文字の長さ **CatalogName*です。  
  
 *スキーマ名*  
 [入力]スキーマ名です。 ドライバーは、いくつかのテーブルは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のスキーマをサポートしている場合 ("") のスキーマはありません。 それらのテーブルを表します。 *SchemaName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*SchemaName*は識別子として扱われます。 場合は SQL_FALSE、 *SchemaName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength2*  
 [入力]文字の長さ **SchemaName*です。  
  
 *テーブル名*  
 [入力]テーブル名です。 この引数は、null ポインターにすることはできません。 *TableName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*TableName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *TableName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength3*  
 [入力]文字の長さ **TableName*です。  
  
 *ColumnName*  
 [入力]列名の文字列の検索パターン。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*ColumnName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *ColumnName*パターン引数の値は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength4*  
 [入力]文字の長さ **ColumnName*です。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLColumnPrivileges** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得される可能性があります**SQLGetDiagRec**で、 *HandleType*sql_handle_stmt としての*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLColumnPrivileges**ですこの関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバーによって返される SQLSTATEs の説明。マネージャーです。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|24000|カーソル状態が無効|カーソルが開いて、 *StatementHandle、*と**SQLFetch**または**SQLFetchScroll**が呼び出されました。 このエラーが返されます、ドライバー マネージャーによって**SQLFetch**または**SQLFetchScroll** 、SQL_NO_DATA が返されなかったと場合、ドライバーによって返される**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されました。<br /><br /> カーソルが開いて、 *StatementHandle*が**SQLFetch**または**SQLFetchScroll**が呼び出されていません。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックによりロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、 * \*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY009|無効な null ポインターの使用|*TableName*引数が null ポインターでした。<br /><br /> SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定された、 *CatalogName*引数が null ポインターの場合と、SQL_CATALOG_NAME*情報の種類*カタログ名を返しますがサポートされています。<br /><br /> (DM) SQL_ATTR_METADATA_ID ステートメント属性が SQL_TRUE に設定、および*SchemaName*または*ColumnName*引数が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期機能がまだこの関数が呼び出されたときに実行します。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) 名長の引数のいずれかの値が 0 より小さい値は SQL_NTS に等しくありません。|  
|||名前の長さの引数のいずれかの値には、対応する名前の最大長の値を超えています。 (「コメント」を参照してください)|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|カタログ名が指定あり、ドライバーまたはデータ ソースがカタログをサポートしていません。<br /><br /> スキーマ名が指定された、およびドライバーまたはデータ ソースがスキーマをサポートしていません。<br /><br /> 列名の文字列の検索パターンが指定され、データ ソースがその引数の検索パターンをサポートしていません。<br /><br /> SQL_CONCURRENCY と SQL_CURSOR_TYPE ステートメント属性の現在の設定の組み合わせが、ドライバーまたはデータ ソースではサポートされていません。<br /><br /> SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されており、SQL_ATTR_CURSOR_TYPE ステートメント属性は、ドライバーがブックマークにできないカーソルの種類に設定されました。|  
|HYT00|タイムアウトが発生しました|クエリのタイムアウト時間は、データ ソースには、結果セットが返される前に期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtAttr**、SQL_ATTR_QUERY_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 **SQLColumnPrivileges** TABLE_CAT、TABLE_SCHEM、TABLE_NAME、COLUMN_NAME、および特権順に並べ、標準的な結果セットとして結果を返します。  
  
> [!NOTE]  
>  **SQLColumnPrivileges**すべての列に対して権限を返さない可能性があります。 たとえば、ドライバーは、Oracle ROWID などの擬似列の権限に関する情報を返さない可能性があります。 アプリケーションは、によって返されるかどうかにかかわらず、任意の有効な列を使用できます**SQLColumnPrivileges**です。  
  
 Varchar 型の列の長さは、テーブルには表示されません。実際の長さは、データ ソースに依存します。 CATALOG_NAME、SCHEMA_NAME、TABLE_NAME、COLUMN_NAME、列の実際の長さを決定するには、アプリケーションが呼び出すことができます**SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、SQL_MAX_TABLE_NAME_ とLEN、および SQL_MAX_COLUMN_NAME_LEN オプション。  
  
> [!NOTE]  
>  一般的な使用、引数、および ODBC カタログ関数の返されたデータの詳細については、次を参照してください。[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)です。  
  
 次の列は、ODBC 3 の名前変更されています。*x*です。 列名の変更では、列番号により、アプリケーション バインドのための下位互換性は影響しません。  
  
|ODBC 2.0 列|ODBC 3 です。*x*列|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 次の表には、結果セット内の列が一覧表示します。 ドライバーでは、8 (IS_GRANTABLE) の列を超える追加の列を定義できます。 アプリケーションでは、明示的な位置を表す序数を指定するのではなく、結果セットの末尾からカウント ダウンによって、ドライバー固有の列へのアクセスを得る必要があります。 詳細については、次を参照してください。[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)です。  
  
|列名|列番号|データ型|コメント|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|カタログの識別子です。データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどにいくつかのテーブルが、他のカタログをサポートする場合 ("")、それらのテーブルのカタログがないです。|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|スキーマの識別子。データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどにいくつかのテーブルが、他のスキーマをサポートする場合 ("")、それらのテーブルのスキーマがないです。|  
|TABLE_NAME (ODBC 1.0)|3|NULL でない Varchar|テーブルの識別子です。|  
|COLUMN_NAME (ODBC 1.0)|4|NULL でない Varchar|列名 ドライバーでは、名前がない列の空の文字列を返します。|  
|権限の許可者 (ODBC 1.0)|5|Varchar|特権を付与したユーザーの名前データ ソースに適用されない場合は NULL です。<br /><br /> すべての行の権限付与対象ユーザーの列の値のオブジェクトの所有者、GRANTOR 列を「(_s)」となります。|  
|権限付与対象ユーザー (ODBC 1.0)|6|NULL でない Varchar|ユーザーに権限を与えられたユーザーの名前です。|  
|権限 (ODBC 1.0)|7|NULL でない Varchar|この列の特権を識別します。 次のいずれかの可能性があります (ソース データでサポートされている他のユーザーまたは実装定義)。<br /><br /> 選択します。 列のデータを取得する、権限付与対象ユーザーが許可されています。<br /><br /> 挿入します。 関連付けられているテーブルに挿入される新しい行の列のデータを提供する、権限付与対象ユーザーが許可されています。<br /><br /> 更新: 権限付与対象ユーザーは、列のデータを更新する許可します。<br /><br /> 参照: 制約中で列を参照する、権限付与対象ユーザーが許可されている (たとえば、一意、参照、またはテーブルが check 制約) です。|  
|IS_GRANTABLE (ODBC 1.0)|8|Varchar|他のユーザーに、特権を付与する、権限付与対象ユーザーが許可されているかどうかを示します"YES"、"NO"、または不明であるか、またはデータ ソースに適用されない場合は"NULL"です。<br /><br /> 特権は、譲与可能なまたはいない譲与可能な両方は必要ありません。 によって返される結果セット**SQLColumnPrivileges** IS_GRANTABLE 列を除くすべての列が、同じ値を含んでいる 2 つの行が含まれません。|  
  
## <a name="code-example"></a>コード例  
 同様の関数のコード例では、次を参照してください。 [SQLColumns 関数](../../../odbc/reference/syntax/sqlcolumns-function.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|テーブルまたはテーブル内の列を返す|[SQLColumns 関数](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|複数行のデータのフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|テーブルまたはテーブルに対する権限を返す|[SQLTablePrivileges 関数](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
|データ ソース内のテーブルの一覧を返す|[SQLTables 関数](../../../odbc/reference/syntax/sqltables-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

