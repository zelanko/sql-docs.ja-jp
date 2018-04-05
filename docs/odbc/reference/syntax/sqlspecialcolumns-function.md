---
title: SQLSpecialColumns 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
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
- SQLSpecialColumns
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSpecialColumns
helpviewer_keywords:
- SQLSpecialColumns function [ODBC]
ms.assetid: bb2d9f21-bda0-4e50-a8be-f710db660034
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 80afdd42ee17c77a44035854207812ecac3afb46
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlspecialcolumns-function"></a>SQLSpecialColumns 関数
**準拠**  
 バージョンが導入されています ODBC 1.0 標準への準拠: グループを開く。  
  
 **概要**  
 **SQLSpecialColumns**指定されたテーブル内の列に関する次の情報を取得します。  
  
-   テーブル内の行を一意に識別する最適な列のセット。  
  
-   トランザクションによって行の任意の値が更新されたときに自動的に更新される列。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLSpecialColumns(  
     SQLHSTMT      StatementHandle,  
     SQLSMALLINT   IdentifierType,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     TableName,  
     SQLSMALLINT   NameLength3,  
     SQLSMALLINT   Scope,  
     SQLSMALLINT   Nullable);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *IdentifierType*  
 [入力]返される列の型。 次の値のいずれかを指定する必要があります。  
  
 SQL_BEST_ROWID: は、最適な列またはことによって、または複数の列から値を取得する任意の行を一意に識別する指定されたテーブルで列のセットを返します。 列には、この目的 (Oracle ROWID または Ingres TID) と同じ列またはテーブルの一意のインデックスの列用に設計された疑似列を指定できます。  
  
 SQL_ROWVER: を返しますまたは複数の列、指定したテーブルに存在する場合、(SQLBase ROWID または Sybase タイムスタンプ) と同じトランザクションによって行の任意の値が更新されたときに、データ ソースによって自動的に更新されます。  
  
 *カタログ名*  
 [入力]テーブルのカタログ名。 ドライバーは、いくつかのテーブルは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のカタログをサポートしている場合 ("") のカタログがないテーブルを表します。 *CatalogName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*CatalogName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *CatalogName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。 詳細については、次を参照してください。[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)です。  
  
 *NameLength1*  
 [入力]文字の長さ **CatalogName*です。  
  
 *スキーマ名*  
 [入力]テーブルのスキーマ名です。 ドライバーは、いくつかのテーブルは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のスキーマをサポートしている場合 ("") のスキーマはありません。 それらのテーブルを表します。 *SchemaName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*SchemaName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *SchemaName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength2*  
 [入力]文字の長さ **SchemaName*です。  
  
 *テーブル名*  
 [入力]テーブル名です。 この引数は、null ポインターにすることはできません。 *TableName*検索パターンに文字列を含めることはできません。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合*TableName*識別子として処理し、そのケースは重要ではありません。 場合は SQL_FALSE、 *TableName*通常の引数は、以外の場合は文字どおり、扱われ、大文字と小文字が重要です。  
  
 *NameLength3*  
 [入力]文字の長さ **TableName*です。  
  
 *スコープ*  
 [入力]Rowid の最低限必要な範囲です。 大きいスコープの返された rowid があります。 次のいずれかを指定する必要があります。  
  
 SQL_SCOPE_CURROW: rowid がその行に配置されている間のみ有効である保証されます。 Rowid を使用して、後で再度選択行が更新または別のトランザクションによって削除された行は返されません可能性があります。  
  
 SQL_SCOPE_TRANSACTION: 現在のトランザクションの間有効である、rowid が保証されます。  
  
 SQL_SCOPE_SESSION: する有効なセッションの間の (トランザクションが変わって) は、rowid が保証されます。  
  
 *[可]*  
 [入力]NULL 値を持つことができる特別な列を返すかどうかを判断します。 次のいずれかを指定する必要があります。  
  
 SQL_NO_NULLS: は、NULL 値を持つことができる特別な列を除外します。 一部のドライバーが SQL_NO_NULLS をサポートできないし、これらのドライバーが空の結果セット SQL_NO_NULLS が指定されている場合を返します。 どうしても必要な場合にのみ、このケースと要求 SQL_NO_NULLS のアプリケーションを準備する必要があります。  
  
 SQL_NULLABLE: は、NULL 値を持っている場合でも、特別な列を返します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLSpecialColumns** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得される可能性があります**SQLGetDiagRec**で、 *HandleType*のSQL_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLSpecialColumns**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|24000|カーソル状態が無効|カーソルが開いて、 *StatementHandle*、および**SQLFetch**または**SQLFetchScroll**が呼び出されました。 このエラーが返されます、ドライバー マネージャーによって**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されなかったと場合、ドライバーによって返される**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されました。<br /><br /> カーソルが開いて、 *StatementHandle*が**SQLFetch**または**SQLFetchScroll**が呼び出されていません。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックによりロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY009|無効な null ポインターの使用|*TableName*引数が null ポインターでした。<br /><br /> SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定された、 *CatalogName*引数が null ポインターの場合と、SQL_CATALOG_NAME*情報の種類*カタログ名を返しますがサポートされています。<br /><br /> (DM) SQL_ATTR_METADATA_ID ステートメント属性が SQL_TRUE に設定、および*SchemaName*引数が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この関数ではときに実行されている**SQLSpecialColumns**が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) 長の引数のいずれかの値が 0 より小さい値は SQL_NTS に等しくありません。<br /><br /> 長の引数のいずれかの値には、対応する名前の最大長の値を超えています。 それぞれの名前の最大長を呼び出すことによって取得できます**SQLGetInfo**で、*情報の種類*値: SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、または SQL_MAX_TABLE_NAME_LEN です。|  
|HY097|範囲外の列の型|(DM) に無効な*IdentifierType*値が指定されました。|  
|HY098|範囲外のスコープの種類|(DM) に無効な*スコープ*値が指定されました。|  
|HY099|範囲外の null 許容型|(DM) に無効な*Nullable*値が指定されました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|カタログが指定されていると、ドライバーまたはデータ ソースがカタログをサポートしていません。<br /><br /> スキーマが指定し、ドライバーまたはデータ ソースがスキーマをサポートしていません。<br /><br /> ドライバーまたはデータ ソースによっては、SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE ステートメント属性の現在の設定の組み合わせはサポートされていません。<br /><br /> SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されており、SQL_ATTR_CURSOR_TYPE ステートメント属性は、ドライバーがブックマークにできないカーソルの種類に設定されました。|  
|HYT00|タイムアウトが発生しました|要求された結果セットが返されるデータ ソースの前に、クエリのタイムアウト期間が期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtAttr**、SQL_ATTR_QUERY_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 ときに、 *IdentifierType*引数は SQL_BEST_ROWID、 **SQLSpecialColumns**列またはテーブル内の各行を一意に識別する列を返します。 これらの列で常に使用できる、*選択リスト*または**場所**句。 **SQLColumns**テーブルの列にさまざまな情報を返すために使用するとは限りません返さない、各行を一意に識別する列、またはによって行の値のいずれかのときに自動的に更新される列を更新します。トランザクションです。 たとえば、 **SQLColumns** Oracle 疑似列 ROWID を返さない可能性があります。 その理由は**SQLSpecialColumns**これらの列を返すために使用します。 詳細については、次を参照してください。[カタログ データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)です。  
  
> [!NOTE]  
>  一般的な使用、引数、および ODBC カタログ関数の返されたデータの詳細については、次を参照してください。[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)です。  
  
 テーブル内の各行を一意に識別する列が存在しない場合**SQLSpecialColumns**行の存在しない行セットが返されます後続の呼び出しに**SQLFetch**または**SQLFetchScroll**。ステートメントで SQL_NO_DATA が返されます。  
  
 場合、 *IdentifierType*、*スコープ*、または*Nullable*引数を指定、データ ソースによってサポートされていない特性**SQLSpecialColumns**は空の結果セットを返します。  
  
 SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定されている場合、 *CatalogName*、 *SchemaName*、および*TableName*のための引数は、識別子として扱われます、特定の状況での null ポインターを設定することはできません。 (詳細については、次を参照してください[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)。)。  
  
 **SQLSpecialColumns**結果のスコープによって順序付け、標準的な結果セットとして返します。  
  
 ODBC 3 の名前を変更した次の列*.x*です。 列名の変更では、列番号により、アプリケーション バインドのための下位互換性は影響しません。  
  
|ODBC 2.0 列|ODBC 3*.x*列|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
  
 COLUMN_NAME 列の実際の長さを決定するには、アプリケーションが呼び出すことができます**SQLGetInfo** SQL_MAX_COLUMN_NAME_LEN オプションを使用します。  
  
 次の表には、結果セット内の列が一覧表示します。 ドライバーでは、8 (PSEUDO_COLUMN) の列を超える追加の列を定義できます。 アプリケーションでは、明示的な位置を表す序数を指定するのではなく、結果セットの末尾からカウント ダウンによって、ドライバー固有の列へのアクセスを得る必要があります。 詳細については、次を参照してください。[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)です。  
  
|列名|列番号|データ型|コメント|  
|-----------------|-------------------|---------------|--------------|  
|スコープ (ODBC 1.0)|@shouldalert|Smallint|Rowid の実際の範囲です。 次の値のいずれかが含まれます。<br /><br /> SQL_SCOPE_CURROW SQL_SCOPE_TRANSACTION SQL_SCOPE_SESSION<br /><br /> NULL が返されます*IdentifierType* SQL_ROWVER がします。 各値については、の説明を参照してください。*スコープ*構文では"、"このセクションでします。|  
|COLUMN_NAME (ODBC 1.0)|2|NULL でない Varchar|列名 ドライバーでは、名前がない列の空の文字列を返します。|  
|DATA_TYPE (ODBC 1.0)|3|Smallint (NULL 以外)|SQL データ型です。 これには、ODBC SQL データ型またはドライバー固有の SQL データ型を指定できます。 有効な ODBC SQL データ型の一覧は、次を参照してください。 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)です。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。|  
|TYPE_NAME (ODBC 1.0)|4|NULL でない Varchar|データ ソースに依存するデータ型の名前です。たとえば、"CHAR"、"VARCHAR"、"MONEY"、"LONG VARBINARY"、または「CHAR () FOR BIT DATA」です。|  
|COLUMN_SIZE (ODBC 1.0)|5|Integer|データ ソースの列のサイズ。 列のサイズに関する詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)です。|  
|BUFFER_LENGTH 列 (ODBC 1.0)|6|Integer|転送されるデータの長さ (バイト単位)、 **SQLGetData**または**SQLFetch** SQL_C_DEFAULT が指定されている場合に操作します。 数値データは、このサイズは、データ ソースに格納されているデータのサイズとは異なる可能性があります。 この値は、文字またはバイナリ データの COLUMN_SIZE 列と同じです。 詳細については、次を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)です。|  
|DECIMAL_DIGITS (ODBC 1.0)|7|Smallint|データ ソース上の列の 10 進数字。 小数点以下桁数は適用されないデータ型に対して NULL を返します。 詳細については小数点以下桁数を参照してください。[列のサイズ、小数点以下桁数、転送オクテット長さ、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)です。|  
|PSEUDO_COLUMN (ODBC 2.0)|8|Smallint|列が Oracle ROWID などの擬似列であるかどうかを示します。<br /><br /> SQL_PC_UNKNOWN SQL_PC_NOT_PSEUDO SQL_PC_PSEUDO**注:**相互運用性を最大にするため、擬似列必要がありますいないする引用符で囲まれた識別子を持つ、引用符文字によって返される**SQLGetInfo**です。|  
  
 アプリケーションは、SQL_BEST_ROWID の値を取得後、アプリケーションに定義されたスコープ内でその行を再度選択してこれらの値を使用できます。 **選択**ステートメントが行の存在しないか、1 つの行を返すことが保証されます。  
  
 アプリケーションは、rowid 列に基づいて行を reselects、行が見つからなかった場合は、アプリケーションは、行が削除されたか、rowid 列が変更されたことを想定できます。 その反対は該当しません: rowid が変更されていない場合でも、行の他の列が変更されます。  
  
 SQL_BEST_ROWID は前方スクロールする必要があるアプリケーションと一連の行から最新のデータの取得に結果セット内に戻します便利です。 列の型に対して返される列です。 または、rowid の複数の列は、その行に位置している間に変更しないように保証されます。  
  
 列、rowid の残る可能性がある有効な行にカーソルが配置されていない場合でもアプリケーションは、結果セットのスコープ 列をチェックしてこれを特定できます。  
  
 SQL_ROWVER は rowid を使用して、行が再度選択されるときに、特定の行の任意の列が更新されたかどうかをチェックする機能を必要とするアプリケーションに役立つ列型に対して返される列です。 たとえば、rowid を使用して行を再度選択した後、アプリケーションは SQL_ROWVER 列をフェッチしたものでは、以前の値を比較できます。 SQL_ROWVER 列の値と異なる場合、以前の値、アプリケーションは、画面上のデータが変更されたユーザーに警告できます。  
  
## <a name="code-example"></a>コード例  
 同様の関数のコード例では、次を参照してください。 [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|テーブルまたはテーブル内の列を返す|[SQLColumns 関数](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|1 つの行または順方向専用の方向にデータのブロックをフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|主キーの列値を返す|[SQLPrimaryKeys 関数](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
