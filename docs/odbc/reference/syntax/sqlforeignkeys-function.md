---
title: SQL 外来キー機能 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5f2769fb378a5ee989fb6a0351537edb3de03469
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285862"
---
# <a name="sqlforeignkeys-function"></a>SQLForeignKeys 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: ODBC  
  
 **まとめ**  
 **SQL 外部キーは**次を返すことができます。  
  
-   指定されたテーブル (他のテーブルの主キーを参照する指定されたテーブルの列) の外部キーのリスト。  
  
-   指定されたテーブルの主キーを参照する他のテーブルの外部キーのリスト。  
  
 ドライバーは、指定されたステートメントの結果セットとして各リストを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
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
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *カタログ名*  
 [入力]主キー テーブル カタログ名。 ドライバーが、異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしている場合、空の文字列 (") は、カタログを持たないテーブルを表します。 *PKCatalogName に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、PKCatalogName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSEの場合 *、PKカタログ名*は通常の引数です。それは文字通り扱われ、そのケースは重要です。 詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。  
  
 *NameLength1*  
 [入力]文字での **PKカタログ名*の長さ。  
  
 *スキーマ名*  
 [入力]主キー テーブルのスキーマ名。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、"" はスキーマを持たないテーブルを表します。 *文字列検索*パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、PKSchemaName*は識別子として扱われ、その大文字と小文字は意味がありません。 SQL_FALSE場合 *、PKSchemaName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 2*  
 [入力]文字での **PKスキーマ名*の長さ。  
  
 *テーブル名*  
 [入力]主キー テーブル名。 *文字列検索*パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性が SQL_TRUE に設定されている場合 *、PKTableName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合 *、PKTableName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 3*  
 [入力]文字での **PKテーブル名*の長さ。  
  
 *FKカタログ名*  
 [入力]外部キー テーブル カタログ名。 ドライバーが、異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしている場合、空の文字列 (") は、カタログを持たないテーブルを表します。 *FKCatalogName に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、FKCatalogName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSEの場合 *、FKCatalogName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ4*  
 [入力]文字での ** FK カタログ名*の長さ。  
  
 *名を指定します。*  
 [入力]外部キー テーブル スキーマ名。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、"" はスキーマを持たないテーブルを表します。 *FKSchemaName に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、FKSchemaName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSEの場合 *、FKSchemaName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前長5*  
 [入力]文字での ** FK スキーマ名*の長さ。  
  
 *FK テーブル名*  
 [入力]外部キー テーブル名。 *FKTableName に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性が SQL_TRUE に設定されている場合 *、FKTableName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合 *、FKTableName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ6*  
 [入力]文字での ** FK テーブル名*の長さ。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLForeignKeys が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は、通常 **、SQLForeignKeys**によって返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*でカーソルが開かれていたし **、SQL フェッチ**または SQL**フェッチスクロール**が呼び出されました。 このエラーは、ドライバー マネージャーが返す SQLFetch または**SQLFetchScrollSQL_NO_DATA**返されていない場合、ドライバー ドライバー マネージャーが返す **、SQL_NO_DATA****返された**場合は、ドライバーによって返されます。 **SQLFetch**<br /><br /> *ステートメント ハンドル*でカーソルが開かれていたが **、SQLFetch**または**SQLFetchScroll が**呼び出されていませんでした。|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、ステートメント ハンドルで**SQLCancel**または**SQLCancelHandle**が呼び出された後、*ステートメント ハンドル*で関数が再度呼び出されました。 *StatementHandle*<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY009|無効な null ポインターの使用|(DM) 引数*PK テーブル名*と*FK テーブル名*はどちらも null ポインターでした。<br /><br /> SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、引数*FKCatalogName*または*PKCatalogName*が null ポインターであり、SQL_CATALOG_NAME *InfoType*はカタログ名がサポートされていることを返します。<br /><br /> (DM) SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、*引数 FKSchemaName、PK**スキーマ名**、FK テーブル名*、または*PKTableName*引数が null ポインターでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は、SQLForeignKeys 関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 名前長引数の 1 つの値が 0 より小さいが、SQL_NTSと等しくない。|  
|||名前長引数の 1 つの値が、対応する名前の最大長の値を超えました。 (「コメント」を参照してください。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|カタログ名が指定され、ドライバまたはデータ ソースがカタログをサポートしていません。<br /><br /> スキーマ名が指定され、ドライバーまたはデータ ソースがスキーマをサポートしていません。|  
|||SQL_ATTR_CONCURRENCYの現在の設定とSQL_ATTR_CURSOR_TYPEステートメント属性の組み合わせは、ドライバーまたはデータ ソースでサポートされていません。<br /><br /> SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_VARIABLE に設定され、SQL_ATTR_CURSOR_TYPE ステートメント属性が、ドライバーがブックマークをサポートしていないカーソルの種類に設定されました。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが結果セットを返しました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUT**を**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 この関数によって返される情報の使用方法については、[カタログ データの使用を参照](../../../odbc/reference/develop-app/uses-of-catalog-data.md)してください。  
  
 \* *PKTableName に*テーブル名が含まれている場合、**指定**したテーブルの主キーと、それを参照するすべての外部キーを含む結果セットが返されます。 他のテーブルの外部キーのリストには、指定されたテーブルの一意制約を指す外部キーは含まれません。  
  
 \* *FKTableName に*テーブル名が含まれている場合 **、SQLForeignKeys は**、他のテーブルの主キーを指す、指定されたテーブル内のすべての外部キー、および参照先の他のテーブルの主キーを含む結果セットを返します。 指定されたテーブルの外部キーのリストには、他のテーブルの一意制約を参照する外部キーが含まれていません。  
  
 両方の\* *PK テーブル名*と\* *FK テーブル名*にテーブル名が含まれている**場合は、** * \**PKTableName*で指定されたテーブルの主キーを参照する*FKTableName*で指定されたテーブルの外部キーを返します。 これは、最も 1 つのキーである必要があります。  
  
> [!NOTE]  
>  ODBC カタログ関数の一般的な使用、引数、および返されるデータの詳細については、「[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)」を参照してください。  
  
 **結果は**標準の結果セットとして返されます。 主キーに関連付けられた外部キーが要求された場合、結果セットはFKTABLE_CAT、FKTABLE_SCHEM、FKTABLE_NAME、およびKEY_SEQ順に並べられます。 外部キーに関連付けられた主キーが要求された場合、結果セットはPKTABLE_CAT、PKTABLE_SCHEM、PKTABLE_NAME、およびKEY_SEQ順に並べられます。 次の表は、結果セット内の列の一覧です。  
  
 VARCHAR 列の長さは表に示されていません。実際の長さはデータ ソースによって異なります。 PKTABLE_CATまたはFKTABLE_CAT、PKTABLE_SCHEMまたはFKTABLE_SCHEM、PKTABLE_NAME、FKTABLE_NAME、PKCOLUMN_NAME列またはFKCOLUMN_NAME列の実際の長さを決定するために、アプリケーションは**SQLGetInfo**を呼び出して、SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、SQL_MAX_TABLE_NAME_LEN、およびSQL_MAX_COLUMN_NAME_LENオプションを指定できます。  
  
 次の列は、ODBC 3 *.x*の名前が変更されました。 列名の変更は、アプリケーションが列番号でバインドするため、下位互換性には影響しません。  
  
|ODBC 2.0 列|ODBC 3 *.x*列|  
|---------------------|-----------------------|  
|PKTABLE_QUALIFIER|PKTABLE_CAT|  
|PKTABLE_OWNER|PKTABLE_SCHEM|  
|FKTABLE_QUALIFIER|FK_TABLE_CAT|  
|FKTABLE_OWNER|FKTABLE_SCHEM|  
  
 次の表は、結果セット内の列の一覧です。 列 14 (REMARKS) を超える追加の列は、ドライバーによって定義できます。 アプリケーションは、明示的な序数の位置を指定するのではなく、結果セットの末尾からカウントダウンして、ドライバー固有の列にアクセスする必要があります。 詳細については、「[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)」を参照してください。  
  
|列名|列番号|データ型|説明|  
|-----------------|-------------------|---------------|--------------|  
|PKTABLE_CAT (ODBC 1.0)|1|Varchar|主キー テーブル カタログ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしているが、他のテーブルについてはサポートしない場合は、カタログを持たないテーブルの空の文字列 ("" ) を返します。|  
|PKTABLE_SCHEM (ODBC 1.0)|2|Varchar|主キー テーブルのスキーマ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、スキーマを持たないテーブルの空の文字列 ("" ) を返します。|  
|PKTABLE_NAME (ODBC 1.0)|3|NULL ではないヴァルチャー|主キー テーブル名。|  
|PKCOLUMN_NAME (ODBC 1.0)|4|NULL ではないヴァルチャー|主キー列名。 ドライバーは、名前を持たない列の空の文字列を返します。|  
|FKTABLE_CAT (ODBC 1.0)|5|Varchar|外部キー テーブル カタログ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしているが、他のテーブルについてはサポートしない場合は、カタログを持たないテーブルの空の文字列 ("" ) を返します。|  
|FKTABLE_SCHEM (ODBC 1.0)|6|Varchar|外部キー テーブル スキーマ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、スキーマを持たないテーブルの空の文字列 ("" ) を返します。|  
|FKTABLE_NAME (ODBC 1.0)|7|NULL ではないヴァルチャー|外部キー テーブル名。|  
|FKCOLUMN_NAME (ODBC 1.0)|8|NULL ではないヴァルチャー|外部キー列名。 ドライバーは、名前を持たない列の空の文字列を返します。|  
|KEY_SEQ (ODBC 1.0)|9|Smallint (NULL 以外)|キーの列シーケンス番号 (1 から始まる)|  
|UPDATE_RULE (ODBC 1.0)|10|Smallint|SQL 操作が**UPDATE**の場合に外部キーに適用されるアクション。 次のいずれかの値を指定できます。 (参照されるテーブルは主キーを持つテーブルで、参照元のテーブルは外部キーを持つテーブルです)。<br /><br /> SQL_CASCADE: 参照先テーブルの主キーが更新されると、参照元テーブルの外部キーも更新されます。<br /><br /> SQL_NO_ACTION: 参照先テーブルの主キーの更新によって参照元テーブル内の "ダングリング参照" が発生する場合 (つまり、参照元テーブルの行には、参照先テーブル内の対応する行がない場合)、更新は拒否されます。 参照元テーブルの外部キーの更新によって、参照先テーブルの主キーの値として存在しない値が発生する場合、更新は拒否されます。 (このアクションは、ODBC 2 *.x*のSQL_RESTRICTアクションと同じです。<br /><br /> SQL_SET_NULL: 主キーの 1 つ以上のコンポーネントが変更されるように参照テーブル内の 1 つまたは複数の行が更新されると、参照元テーブルの変更されたコンポーネントに対応する参照テーブルの外部キーのコンポーネントは、参照元テーブルのすべての一致する行で NULL に設定されます。<br /><br /> SQL_SET_DEFAULT: 主キーの 1 つ以上のコンポーネントが変更されるように、参照テーブル内の 1 つまたは複数の行が更新されると、主キーの変更されたコンポーネントに対応する参照テーブルの外部キーのコンポーネントは、参照元テーブルのすべての一致する行の該当する既定値に設定されます。<br /><br /> データ ソースに適用できない場合は NULL。|  
|DELETE_RULE (ODBC 1.0)|11|Smallint|SQL 操作が**DELETE**の場合に外部キーに適用されるアクション。 次のいずれかの値を指定できます。 (参照されるテーブルは主キーを持つテーブルで、参照元のテーブルは外部キーを持つテーブルです)。<br /><br /> SQL_CASCADE: 参照先テーブルの行が削除されると、参照元テーブル内の一致する行もすべて削除されます。<br /><br /> SQL_NO_ACTION: 参照先のテーブルの行を削除すると、参照元テーブルで "ダングリング参照" が発生する (つまり、参照元テーブルの行に対応する行がない) 場合、更新は拒否されます。 (このアクションは、ODBC 2 *.x*のSQL_RESTRICTアクションと同じです。<br /><br /> SQL_SET_NULL: 参照先テーブルの 1 つまたは複数の行が削除されると、参照元テーブルの外部キーの各コンポーネントは、参照元テーブルのすべての一致する行で NULL に設定されます。<br /><br /> SQL_SET_DEFAULT: 参照先テーブルの 1 つまたは複数の行が削除されると、参照元テーブルの外部キーの各コンポーネントは、参照元テーブルのすべての一致する行で適用可能な既定値に設定されます。<br /><br /> データ ソースに適用できない場合は NULL。|  
|FK_NAME (ODBC 2.0)|12|Varchar|外部キー名。 データ ソースに適用できない場合は NULL。|  
|PK_NAME (ODBC 2.0)|13|Varchar|主キー名。 データ ソースに適用できない場合は NULL。|  
|デフェレーション (ODBC 3.0)|14|Smallint|SQL_INITIALLY_DEFERRED、SQL_INITIALLY_IMMEDIATE、SQL_NOT_DEFERRABLE。|  
  
## <a name="code-example"></a>コード例  
 次の表に示すように、この例では ORDERS、LINES、および CUSTOMERS という名前の 3 つのテーブルを使用します。  
  
|ORDERS|行|顧客|  
|------------|-----------|---------------|  
|Orderid|Orderid|CUSTID|  
|CUSTID|行|NAME|  
|オープンデイト|パートID|アドレス|  
|営業 担当者|量|電話|  
|状態|||  
  
 ORDERS テーブルでは、CUSTID は、販売が行われた顧客を識別します。 これは、CUSTOMERS テーブル内の CUSTID を参照する外部キーです。  
  
 LINES テーブルでは、ORDERID は、品目が関連付けられている販売注文を識別します。 これは、ORDERS テーブルの ORDERID を参照する外部キーです。  
  
 この例では **、SQLPrimaryKeys**を呼び出して、ORDERS テーブルの主キーを取得します。 結果セットには 1 行が含まれ、結果セットには 1 行が含まれ、結果セットには 1 行の行が重要な列を次の表に示します。  
  
|TABLE_NAME|COLUMN_NAME|KEY_SEQ|  
|-----------------|------------------|--------------|  
|ORDERS|Orderid|1|  
  
 次に、この例では **、SQLForeignKeys**を呼び出して、ORDERS テーブルの主キーを参照する他のテーブルの外部キーを取得します。 結果セットには 1 行が含まれ、結果セットには 1 行が含まれ、結果セットには 1 行の行が重要な列を次の表に示します。  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|ORDERS|CUSTID|行|CUSTID|1|  
  
 最後に、この例では **、SQLForeignKeys**を呼び出して、他のテーブルの主キーを参照する ORDERS テーブルの外部キーを取得します。 結果セットには 1 行が含まれ、結果セットには 1 行が含まれ、結果セットには 1 行の行が重要な列を次の表に示します。  
  
|PKTABLE_NAME|PKCOLUMN_NAME|FKTABLE_NAME|FKCOLUMN_NAME|KEY_SEQ|  
|-------------------|--------------------|-------------------|--------------------|--------------|  
|顧客|CUSTID|ORDERS|CUSTID|1|  
  
```cpp  
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
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|単一行またはデータブロックを順方向方向にフェッチする|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|主キーの列を返す|[SQLPrimaryKeys 関数](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
|テーブルの統計とインデックスを返す|[SQLStatistics 関数](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
