---
title: SQLProcedures 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLProcedures
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLProcedures
helpviewer_keywords:
- SQLProcedures function [ODBC]
ms.assetid: d0d9ef10-2fd4-44a5-9334-649f186f4ba0
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: daec499cca74ef63978b3eede0216e192435bdaa
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlprocedures-function"></a>SQLProcedures 関数
**準拠**  
 バージョンが導入されています ODBC 1.0 標準への準拠: ODBC。  
  
 **概要**  
 **SQLProcedures**特定のデータ ソースに格納されているプロシージャ名の一覧を返します。 *プロシージャ*記述に使用される一般的な用語は、*実行可能オブジェクト*、または名前付きエンティティであり、入力と出力パラメーターを使用して呼び出すことができます。 プロシージャの詳細については、次を参照してください。、[プロシージャ](../../../odbc/reference/develop-app/procedures-odbc.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLProcedures(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      ProcName,  
     SQLSMALLINT    NameLength3);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *カタログ名*  
 [入力]プロシージャのカタログです。 ドライバーは、いくつかのテーブルは、ドライバーがさまざまな Dbms、空の文字列からデータを取得するときなど、他のカタログをサポートしている場合 ("") のカタログがないテーブルを表します。 *CatalogName*検索パターンに文字列を含めることはできません。  
  
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
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLProcedures** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLProcedures**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|24000|カーソル状態が無効|カーソルが開いて、 *StatementHandle*、および**SQLFetch**または**SQLFetchScroll**が呼び出されました。 このエラーが返されます、ドライバー マネージャーによって**SQLFetch**または**SQLFetchScroll** 、SQL_NO_DATA が返されなかったと場合、ドライバーによって返される**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されました。<br /><br /> カーソルが開いて、 *StatementHandle*が**SQLFetch**または**SQLFetchScroll**が呼び出されていません。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックによりロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*です。 関数が再度呼び出されたし、 *StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY009|無効な null ポインターの使用|SQL_ATTR_METADATA_ID ステートメント属性は、SQL_TRUE に設定された、 *CatalogName*引数が null ポインターの場合と、SQL_CATALOG_NAME*情報の種類*カタログ名を返しますがサポートされています。<br /><br /> (DM) SQL_ATTR_METADATA_ID ステートメント属性が SQL_TRUE に設定、および*SchemaName*または*ProcName*引数が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期機能がまだこの関数が呼び出されたときに実行します。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) 名長の引数のいずれかの値が 0 より小さい値は SQL_NTS に等しくありません。<br /><br /> 名前の長さの引数のいずれかの値には、対応する名前の最大長の値を超えています。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|プロシージャのカタログが指定されていると、ドライバーまたはデータ ソースがカタログをサポートしていません。<br /><br /> プロシージャのスキーマが指定されました、ドライバーまたはデータ ソースがスキーマをサポートしていません。<br /><br /> プロシージャのスキーマまたはプロシージャ名、文字列、検索パターンが指定され、データ ソースがこれらの引数の 1 つ以上の検索パターンをサポートしていません。<br /><br /> ドライバーまたはデータ ソースによっては、SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE ステートメント属性の現在の設定の組み合わせはサポートされていません。<br /><br /> SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメント属性が設定されており、SQL_ATTR_CURSOR_TYPE ステートメント属性は、ドライバーがブックマークにできないカーソルの種類に設定されました。|  
|HYT00|タイムアウトが発生しました|要求された結果セットが返されるデータ ソースの前に、クエリのタイムアウト期間が期限切れです。 によって、タイムアウト期間が設定されている**SQLSetStmtAttr**、SQL_ATTR_QUERY_TIMEOUT です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*この関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 **SQLProcedures**要求された範囲内のすべてのプロシージャを一覧表示します。 ユーザーは、可能性があります。 またはいずれかの手順を実行する権限がない可能性があります。 確認するにはユーザー補助アプリケーションが呼び出すことができます**SQLGetInfo** SQL_ACCESSIBLE_PROCEDURES 情報値を確認します。 それ以外の場合、アプリケーションは、ユーザーがプロシージャを実行できないことを選択した状況を処理できる必要があります。 この情報の使用方法については、次を参照してください。[プロシージャ](../../../odbc/reference/develop-app/procedures-odbc.md)です。  
  
> [!NOTE]  
>  一般的な使用、引数、および ODBC カタログ関数の返されたデータの詳細については、次を参照してください。[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)です。  
  
 **SQLProcedures** PROCEDURE_CAT、PROCEDURE_SCHEMA、PROCEDURE_NAME、順序付け、標準的な結果セットとして結果を返します。  
  
> [!NOTE]  
>  **SQLProcedures**のすべてのプロシージャを返さない可能性があります。 アプリケーションは、によって返されるかどうかに関係なく、任意の有効なプロシージャを使用して**SQLProcedures**です。  
  
 ODBC 3 の名前を変更した次の列 *.x*です。 列名の変更では、列番号により、アプリケーション バインドのための下位互換性は影響しません。  
  
|ODBC 2.0 列|ODBC 3 *.x*列|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|プロシージャ _OWNER|プロシージャ _SCHEM|  
  
 PROCEDURE_CAT、PROCEDURE_SCHEM、PROCEDURE_NAME の各列の実際の長さを決定するには、アプリケーションが呼び出すことができます**SQLGetInfo** SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、SQL_MAX_PROCEDURE_ とNAME_LEN オプションです。  
  
 次の表には、結果セット内の列が一覧表示します。 ドライバーでは、8 (PROCEDURE_TYPE) の列を超える追加の列を定義できます。 アプリケーションでは、明示的な位置を表す序数を指定するのではなく、結果セットの末尾からカウント ダウンによって、ドライバー固有の列へのアクセスを得る必要があります。 詳細については、次を参照してください。[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)です。  
  
|列名|列番号|データ型|コメント|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2.0)|1|Varchar|プロシージャのカタログの識別子です。データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどに一部のプロシージャが、他のカタログをサポートする場合 ("") のカタログはありません。 それらの手順をします。|  
|PROCEDURE_SCHEM (ODBC 2.0)|2|Varchar|プロシージャのスキーマの識別子です。データ ソースに適用されない場合は NULL です。 ドライバーの空の文字列を返します、ドライバーは、さまざまな Dbms からデータを取得、するときなどに一部のプロシージャが、他のスキーマをサポートする場合 ("") のスキーマはありません。 それらの手順です。|  
|PROCEDURE_NAME (ODBC 2.0)|3|NULL でない Varchar|プロシージャの識別子です。|  
|NUM_INPUT_PARAMS (ODBC 2.0)|4|なし|将来の使用のために予約されています。 これらの結果の列に返されるデータには、アプリケーションは保証はありません。|  
|NUM_OUTPUT_PARAMS (ODBC 2.0)|5|なし|将来の使用のために予約されています。 これらの結果の列に返されるデータには、アプリケーションは保証はありません。|  
|NUM_RESULT_SETS (ODBC 2.0)|6|なし|将来の使用のために予約されています。 これらの結果の列に返されるデータには、アプリケーションは保証はありません。|  
|「解説」(ODBC 2.0)|7|Varchar|プロシージャの説明です。|  
|PROCEDURE_TYPE (ODBC 2.0)|8|Smallint|プロシージャの型を定義します。<br /><br /> SQL_PT_UNKNOWN: 確認できないかどうか、プロシージャが値を返します。<br /><br /> SQL_PT_PROCEDURE: 返されたオブジェクトは、プロシージャです。つまり、戻り値はありません。<br /><br /> : は、返されたオブジェクトは関数です。つまり、戻り値があります。|  
  
 *SchemaName*と*ProcName*引数には、検索パターンがそのまま使用します。 有効な検索パターンの詳細については、次を参照してください。[パターン値の引数](../../../odbc/reference/develop-app/pattern-value-arguments.md)です。  
  
## <a name="code-example"></a>コード例  
 参照してください[プロシージャ呼び出し](../../../odbc/reference/develop-app/procedure-calls.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|1 つの行または順方向専用の方向にデータのブロックをフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|ドライバーまたはデータ ソースに関する情報を返す|[SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|プロシージャの列を設定するパラメーターと結果を返す|[SQLProcedureColumns 関数](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|  
|ストアド プロシージャを呼び出すための構文|[ステートメントの実行](../../../odbc/reference/develop-app/executing-statements-odbc.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
