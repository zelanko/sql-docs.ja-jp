---
title: 関数の特殊な列 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 826630e1d344322268a2f2638310b3a1e182de6d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287172"
---
# <a name="sqlspecialcolumns-function"></a>SQLSpecialColumns 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: オープングループ  
  
 **まとめ**  
 **SQLSpecialColumns は**、指定されたテーブル内の列に関する次の情報を取得します。  
  
-   テーブル内の行を一意に識別する列の最適なセット。  
  
-   トランザクションによって行の値が更新されたときに自動的に更新される列。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
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
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *識別子タイプ*  
 [入力]返す列の型。 次のいずれかの値を指定する必要があります。  
  
 SQL_BEST_ROWID: 列から値を取得することによって、指定されたテーブル内の任意の行を一意に識別できる最適な列または列セットを返します。 列は、この目的のために特別に設計された疑似列 (Oracle ROWID または Ingres TID のように) か、表の一意索引の列のいずれかです。  
  
 SQL_ROWVER: 行の値がトランザクションによって更新されたときにデータ ソースによって自動的に更新される、指定されたテーブルの列 (存在する場合) を返します (SQLBase ROWID または Sybase TIMESTAMP のように)。  
  
 *カタログ名*  
 [入力]テーブルのカタログ名。 ドライバーが、異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしている場合、空の文字列 (") は、カタログを持たないテーブルを表します。 *カタログ名に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、CatalogName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合 *、CatalogName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。 詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。  
  
 *NameLength1*  
 [入力]* カタログ*名*の文字での長さ。  
  
 *Schemaname*  
 [入力]テーブルのスキーマ名。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、"" はスキーマを持たないテーブルを表します。 *スキーマ名に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、SchemaName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合、*スキーマ名*は通常の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 2*  
 [入力]**スキーマ名*の文字での長さ。  
  
 *TableName*  
 [入力]テーブル名。 この引数を NULL ポインターにすることはできません。 *TableName に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性が SQL_TRUE に設定されている場合 *、TableName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合は *、TableName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 3*  
 [入力]**テーブル名*の文字での長さ。  
  
 *Scope*  
 [入力]rowid の最小必要範囲。 返される rowid のスコープが大きい場合があります。 次のいずれかである必要があります。  
  
 SQL_SCOPE_CURROW: rowid は、その行に位置している間のみ有効であることが保証されます。 rowid を使用して後で再選択した場合、その行が別のトランザクションによって更新または削除された場合、行が返されないことがあります。  
  
 SQL_SCOPE_TRANSACTION: rowid は、現在のトランザクションの間有効であることが保証されます。  
  
 SQL_SCOPE_SESSION: rowid は、セッションの間 (トランザクション境界を越えて) 有効であることが保証されます。  
  
 *NULL 値の使用*  
 [入力]NULL 値を持つ特殊な列を返すかどうかを決定します。 次のいずれかである必要があります。  
  
 SQL_NO_NULLS: NULL 値を持つ可能性がある特殊な列を除外します。 一部のドライバーはSQL_NO_NULLSをサポートできず、これらのドライバーは、SQL_NO_NULLSが指定された場合、空の結果セットを返します。 アプリケーションは、この場合に備えて、それが絶対に必要な場合にのみSQL_NO_NULLSを要求する必要があります。  
  
 SQL_NULLABLE: NULL 値を持つ場合でも、特殊な列を返します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLSpecialColumns が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときに、関連付けられた SQLSTATE 値を取得するには、SQL_HANDLE_STMT*のハンドル型*と*ステートメント ハンドル*を*指定*して**SQLGetDiagRec**を呼び出します。 次の表は **、SQLSpecialColumns**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*でカーソルが開かれていたし **、SQL フェッチ**または SQL**フェッチスクロール**が呼び出されました。 このエラーは、ドライバー マネージャーが返す SQLFetch または**SQLFetchScroll**がSQL_NO_DATA返されていない場合は**SQLFetchScroll****、ドライバー**マネージャーが返す、ドライバーによって返されますSQL_NO_DATA返された場合は、**ドライバー**によって返されます。<br /><br /> *ステートメント ハンドル*でカーソルが開かれていたが **、SQLFetch**または**SQLFetchScroll が**呼び出されていませんでした。|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、*ステートメント ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、関数は*ステートメント ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY009|無効な null ポインターの使用|*引数が*null ポインターでした。<br /><br /> SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、*引数 CatalogName*が null ポインターであり、SQL_CATALOG_NAME *InfoType*はカタログ名がサポートされていることを返します。<br /><br /> (DM) SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、引数*SchemaName*が null ポインターでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この関数は **、SQLSpecialColumns が**呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 長さの引数の 1 つの値が 0 より小さいが、SQL_NTSと等しくない。<br /><br /> 長さ引数の 1 つの値が、対応する名前の最大長の値を超えました。 各名前の最大長は、SQL_MAX_TABLE_NAME_LEN SQL_MAX_SCHEMA_NAME_LEN SQL_MAX_CATALOG_NAME_LEN*情報の種類*の値を使用して**SQLGetInfo**を呼び出すことによって得ることができます。|  
|HY097|列の種類が範囲外です|(DM) 無効な*識別子の種類の*値が指定されました。|  
|HY098|スコープの種類が範囲外です|(DM) 無効な*スコープ*値が指定されました。|  
|HY099|Null 許容型が範囲外です|(DM) 無効な*Null 許容*値が指定されました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|カタログが指定され、ドライバまたはデータ ソースがカタログをサポートしていません。<br /><br /> スキーマが指定され、ドライバーまたはデータ ソースがスキーマをサポートしていません。<br /><br /> SQL_ATTR_CONCURRENCYの現在の設定とSQL_ATTR_CURSOR_TYPEステートメント属性の組み合わせは、ドライバーまたはデータ ソースでサポートされていません。<br /><br /> SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_VARIABLE に設定され、SQL_ATTR_CURSOR_TYPE ステートメント属性が、ドライバーがブックマークをサポートしていないカーソルの種類に設定されました。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが要求された結果セットを返しました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUT**を**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 *引数が*SQL_BEST_ROWIDされると、**テーブル**内の各行を一意に識別する列が返されます。 これらの列は、選択*リスト*または**WHERE**句で常に使用できます。 **SQLColumns**は、テーブルの列に関するさまざまな情報を返すために使用され、各行を一意に識別する列や、トランザクションによって行内の値が更新されたときに自動的に更新される列を返すわけではありません。 たとえば **、SQLColumns は**、Oracle の疑似列 ROWID を返さない場合があります。 このため、これらの列を返すために**SQLSpecialColumns**が使用されます。 詳細については、「カタログ[データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)」を参照してください。  
  
> [!NOTE]  
>  ODBC カタログ関数の一般的な使用、引数、および返されるデータの詳細については、「[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)」を参照してください。  
  
 テーブル内の各行を一意に識別する列がない**場合は、** 行なしの行セットが返されます。ステートメントの SQLFetch または**SQLFetchScroll**への後続の呼び出しは、SQL_NO_DATAを返します。 **SQLFetchScroll**  
  
 *識別子型*、*スコープ*、または*Null 許容の*引数で、データ ソースでサポートされていない特性が指定されている場合 **、SQLSpecialColumns は**空の結果セットを返します。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、CatalogName、SchemaName、* および*TableName*の各引数は識別子として扱われるため、特定の状況では null ポインターに設定することはできません。 *SchemaName* (詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。  
  
 **結果は**、SCOPE の順序で並べ替えられた標準の結果セットとして返されます。  
  
 次の列は、ODBC *3.x*の名前が変更されました。 列名の変更は、アプリケーションが列番号でバインドするため、下位互換性には影響しません。  
  
|ODBC 2.0 列|ODBC *3.x*列|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|LENGTH|BUFFER_LENGTH|  
|SCALE|DECIMAL_DIGITS|  
  
 COLUMN_NAME列の実際の長さを決定するために、アプリケーションは SQL_MAX_COLUMN_NAME_LEN オプションを指定して**SQLGetInfo**を呼び出すことができます。  
  
 次の表は、結果セット内の列の一覧です。 列 8 (PSEUDO_COLUMN) を超える追加の列は、ドライバーによって定義できます。 アプリケーションは、明示的な序数の位置を指定するのではなく、結果セットの末尾からカウントダウンして、ドライバー固有の列にアクセスする必要があります。 詳細については、「[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)」を参照してください。  
  
|列名|列番号|データ型|説明|  
|-----------------|-------------------|---------------|--------------|  
|スコープ (ODBC 1.0)|1|Smallint|rowid の実際のスコープ。 次のいずれかの値が含まれます。<br /><br /> SQL_SCOPE_TRANSACTIONSQL_SCOPE_SESSIONSQL_SCOPE_CURROW<br /><br /> *識別子の種類*がSQL_ROWVER場合は NULL が返されます。 各値の説明については、このセクションの「構文」の*スコープ*の説明を参照してください。|  
|COLUMN_NAME (ODBC 1.0)|2|NULL ではないヴァルチャー|列名。 ドライバーは、名前を持たない列の空の文字列を返します。|  
|DATA_TYPE (ODBC 1.0)|3|Smallint (NULL 以外)|SQL データ型。 これは、ODBC SQL データ型またはドライバー固有の SQL データ型です。 有効な ODBC SQL データ型の一覧については、「 [SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)」を参照してください。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。|  
|TYPE_NAME (ODBC 1.0)|4|NULL ではないヴァルチャー|データ ソース依存のデータ型名。たとえば、"CHAR" "VARCHAR" "VARCHAR" "、"MONEY"、"ロング VARBINARY"、または "CHAR ( ) (ビット データ" の場合) などです。|  
|COLUMN_SIZE (ODBC 1.0)|5|Integer|データ ソースの列のサイズ。 列サイズの詳細については、「[列サイズ、10 進数、オクテットの長さの転送、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|BUFFER_LENGTH (ODBC 1.0)|6|Integer|SQL_C_DEFAULT指定されている場合に **、SQLGetData**または**SQLFetch**操作で転送されるデータのバイト数です。 数値データの場合、このサイズはデータ ソースに格納されているデータのサイズと異なる場合があります。 この値は、文字データまたはバイナリー・データのCOLUMN_SIZE列と同じです。 詳細については、「[列サイズ、10 進数、オクテット長の転送、および表示サイズ」を参照してください](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)。|  
|DECIMAL_DIGITS (ODBC 1.0)|7|Smallint|データ ソースの列の 10 進数の数字。 10 進数が適用できないデータ・タイプの場合は、NULL が戻されます。 10 進数の桁数の詳細については、「[列サイズ、10 進数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|PSEUDO_COLUMN (ODBC 2.0)|8|Smallint|列が疑似列であるかどうかを示します (Oracle ROWID など)。<br /><br /> SQL_PC_UNKNOWN SQL_PC_NOT_PSEUDO SQL_PC_PSEUDO**注意:** 相互運用性を最大限に高めるには、 **SQLGetInfo**によって返される識別子の引用符で疑似列を引用符で囲む必要はありません。|  
  
 アプリケーションがSQL_BEST_ROWIDの値を取得した後、アプリケーションはこれらの値を使用して、定義されたスコープ内でその行を再選択できます。 **SELECT ステートメント**は、行も 1 行も返さないと保証されます。  
  
 アプリケーションが rowid 列に基づいて行を再選択し、その行が見つからない場合、アプリケーションは行が削除されたか、rowid 列が変更されたと見なすことができます。 その逆は、rowid が変更されていない場合でも、行の他の列が変更されている可能性があります。  
  
 列型SQL_BEST_ROWIDに対して返される列は、結果セット内で前後にスクロールして、行セットから最新のデータを取得する必要があるアプリケーションに役立ちます。 rowid の列は、その行に位置付けされている間は変更されないことが保証されます。  
  
 rowid の列は、カーソルが行に配置されていない場合でも有効なままである場合があります。アプリケーションは、結果セット内の SCOPE 列をチェックすることによって、これを判別できます。  
  
 列タイプSQL_ROWVERに返される列は、rowid を使用して行が再選択されている間に、特定の行の列が更新されたかどうかを確認する機能を必要とするアプリケーションに役立ちます。 たとえば、rowid を使用して行を再選択した後、アプリケーションは、SQL_ROWVER列の前の値をフェッチした値と比較できます。 SQL_ROWVER列の値が以前の値と異なる場合、アプリケーションは、表示上のデータが変更されたことをユーザーに警告できます。  
  
## <a name="code-example"></a>コード例  
 同様の関数のコード例については、「 [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|テーブル内の列を返す|[SQLColumns 関数](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|単一行またはデータブロックを順方向方向にフェッチする|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|主キーの列を返す|[SQLPrimaryKeys 関数](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
