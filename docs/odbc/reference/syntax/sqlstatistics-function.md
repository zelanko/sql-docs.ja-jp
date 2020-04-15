---
title: 統計関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c2a5ef0b0e54e17a2dc091a98efc972fa608ef15
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302946"
---
# <a name="sqlstatistics-function"></a>SQLStatistics 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLStatistics は**、単一のテーブルと、そのテーブルに関連付けられたインデックスに関する統計のリストを取得します。 ドライバーは、結果セットとして情報を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
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
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *カタログ名*  
 [入力]カタログ名。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしているが、他のテーブルについてはサポートされていない場合は、空の文字列 (") は、カタログを持たないテーブルを示します。 *カタログ名に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、CatalogName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合 *、CatalogName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。 詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。  
  
 *NameLength1*  
 [入力]* カタログ*名*の文字での長さ。  
  
 *Schemaname*  
 [入力]スキーマ名。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、スキーマを持たないテーブルを示す空の文字列 (") が表示されます。 *スキーマ名に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、SchemaName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合、*スキーマ名*は通常の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 2*  
 [入力]**スキーマ名*の文字での長さ。  
  
 *TableName*  
 [入力]テーブル名。 この引数を NULL ポインターにすることはできません。 *スキーマ名に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性が SQL_TRUE に設定されている場合 *、TableName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合は *、TableName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 3*  
 [入力]**テーブル名*の文字での長さ。  
  
 *一意*  
 [入力]インデックスの種類: SQL_INDEX_UNIQUEまたはSQL_INDEX_ALL。  
  
 *予約済み*  
 [入力]結果セット内のカーディナリティ列と PAGES 列の重要性を示します。 次のオプションは、カーディナリティ列と PAGES 列の戻り値にのみ影響します。カーディナリティと PAGES が返されない場合でも、インデックス情報が返されます。  
  
 SQL_ENSURE、ドライバが統計を無条件で取得することを要求します。 (オープングループ標準に準拠し、ODBC 拡張をサポートしないドライバは、SQL_ENSUREをサポートできません)。  
  
 SQL_QUICK、ドライバがサーバからすぐに利用できる場合にのみ、CARDINALITY と PAGES を取得することを要求します。 この場合、ドライバーで取得される値が最新であるかどうかは保証されません。 (オープングループ標準に書かれたアプリケーションは、ODBC *3.x*準拠ドライバからSQL_QUICK動作を常に受け取ります)。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLStatistics**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は、通常 **、SQLStatistics**によって返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*でカーソルが開かれていたし **、SQL フェッチ**または SQL**フェッチスクロール**が呼び出されました。 このエラーは、ドライバー マネージャーが返す SQLFetch または**SQLFetchScroll**がSQL_NO_DATA返されていない場合は**SQLFetchScroll****、ドライバー**マネージャーが返す、ドライバーによって返されますSQL_NO_DATA返された場合は、**ドライバー**によって返されます。<br /><br /> *ステートメント ハンドル*でカーソルが開かれていたが **、SQLFetch**または**SQLFetchScroll が**呼び出されていませんでした。|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、ステートメント ハンドルで**SQLCancel**または**SQLCancelHandle**が呼び出された後、*ステートメント ハンドル*で関数が再度呼び出されました。 *StatementHandle*<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY009|無効な null ポインターの使用|*引数が*null ポインターでした。<br /><br /> SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、*引数 CatalogName*が null ポインターであり、SQL_CATALOG_NAME *InfoType*はカタログ名がサポートされていることを返します。<br /><br /> (DM) SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、引数*SchemaName*が null ポインターでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLStatistics**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 名前長引数の 1 つの値が 0 より小さいが、SQL_NTSと等しくない。<br /><br /> 名前長引数の 1 つの値が、対応する名前の最大長の値を超えました。|  
|HY100|一意性オプションの種類が範囲外です|(DM) 無効な*固有*値が指定されました。|  
|HY101|精度オプションの種類が範囲外です|(DM) 無効な*予約値*が指定されました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|カタログが指定され、ドライバまたはデータ ソースがカタログをサポートしていません。<br /><br /> スキーマが指定され、ドライバーまたはデータ ソースがスキーマをサポートしていません。<br /><br /> SQL_ATTR_CONCURRENCYの現在の設定とSQL_ATTR_CURSOR_TYPEステートメント属性の組み合わせは、ドライバーまたはデータ ソースでサポートされていません。<br /><br /> SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_VARIABLE に設定され、SQL_ATTR_CURSOR_TYPE ステートメント属性が、ドライバーがブックマークをサポートしていないカーソルの種類に設定されました。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが要求された結果セットを返しました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUT**を**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 **SQLStatistics は、** 単一のテーブルに関する情報を、NON_UNIQUE、TYPE、INDEX_QUALIFIER、INDEX_NAME、およびORDINAL_POSITION順に並べられた標準結果セットとして返します。 結果セットは、各インデックスに関する情報とテーブルの (結果セットの CARDINALITY 列および PAGES 列の) 統計情報を結合します。 この情報の使用方法については、「[カタログ データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)」を参照してください。  
  
 TABLE_CAT、TABLE_SCHEM、TABLE_NAME、およびCOLUMN_NAME列の実際の長さを決定するために、アプリケーションは**SQLGetInfo**を呼び出して、SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、SQL_MAX_TABLE_NAME_LEN、およびSQL_MAX_COLUMN_NAME_LENオプションを指定できます。  
  
> [!NOTE]  
>  ODBC カタログ関数の一般的な使用、引数、および返されるデータの詳細については、「[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)」を参照してください。  
  
 次の列は、ODBC *3.x*の名前が変更されました。 列名の変更は、アプリケーションが列番号でバインドするため、下位互換性には影響しません。  
  
|ODBC 2.0 列|ODBC *3.x*列|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
|SEQ_IN_INDEX|ORDINAL_POSITION|  
|COLLATION|ASC_OR_DESC|  
  
 次の表は、結果セット内の列の一覧です。 列 13 (FILTER_CONDITION) を超える追加の列は、ドライバーによって定義できます。 アプリケーションは、明示的な序数の位置を指定するのではなく、結果セットの末尾からカウントダウンして、ドライバー固有の列にアクセスする必要があります。 詳細については、「[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)」を参照してください。  
  
|列名|列番号|データ型|説明|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|統計または索引が適用される表のカタログ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしているが、他のテーブルについてはサポートしない場合は、カタログを持たないテーブルの空の文字列 ("" ) を返します。|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|統計または索引が適用される表のスキーマ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、スキーマを持たないテーブルの空の文字列 ("" ) を返します。|  
|TABLE_NAME (ODBC 1.0)|3|NULL ではないヴァルチャー|統計または索引が適用される表の名前。|  
|NON_UNIQUE (ODBC 1.0)|4|Smallint|インデックスで重複する値が許可されないかどうかを示します。<br /><br /> インデックス値が一意でない場合にSQL_TRUEします。<br /><br /> インデックス値が一意である必要がある場合にSQL_FALSEします。<br /><br /> TYPE がSQL_TABLE_STATの場合は NULL が返されます。|  
|INDEX_QUALIFIER (ODBC 1.0)|5|Varchar|インデックス名を修飾するために使用される識別子で **、DROP INDEX**を実行します。データ ソースでインデックス修飾子がサポートされていない場合、または TYPE がSQL_TABLE_STATの場合は、NULL が返されます。 この列に NULL 以外の値が戻される場合は **、DROP INDEX**ステートメントでインデックス名を修飾するために使用する必要があります。それ以外の場合は、インデックス名を修飾するためにTABLE_SCHEMを使用する必要があります。|  
|INDEX_NAME (ODBC 1.0)|6|Varchar|インデックス名。TYPE がSQL_TABLE_STATの場合は NULL が返されます。|  
|タイプ (ODBC 1.0)|7|Smallint (NULL 以外)|返される情報の種類:<br /><br /> SQL_TABLE_STATは、テーブルの統計 (カーディナリティ列または PAGES 列) を示します。<br /><br /> SQL_INDEX_BTREEは、B ツリー インデックスを示します。<br /><br /> SQL_INDEX_CLUSTEREDは、クラスタ化インデックスを示します。<br /><br /> SQL_INDEX_CONTENTはコンテンツ インデックスを示します。<br /><br /> SQL_INDEX_HASHEDハッシュされたインデックスを示します。<br /><br /> SQL_INDEX_OTHERは、別の種類のインデックスを示します。|  
|ORDINAL_POSITION (ODBC 1.0)|8|Smallint|インデックス内の列シーケンス番号 (1 から始まる)TYPE がSQL_TABLE_STATの場合は NULL が返されます。|  
|COLUMN_NAME (ODBC 1.0)|9|Varchar|列名。 列が SALARY + BENEFITS などの式に基づいている場合は、式が戻されます。式を判別できない場合は、空の文字列が返されます。 TYPE がSQL_TABLE_STATの場合は NULL が返されます。|  
|ASC_OR_DESC (ODBC 1.0)|10|Char(1)|列の並べ替え順序: 昇順の場合は "A" です。降下のための"D";列の並べ替え順序がデータ ソースでサポートされていない場合、または TYPE がSQL_TABLE_STAT場合は、NULL が返されます。|  
|カーディナリティ (ODBC 1.0)|11|Integer|テーブルまたはインデックスのカーディナリティー。TYPE がSQL_TABLE_STATの場合、テーブル内の行数。TYPE がSQL_TABLE_STATされていない場合、インデックス内の一意の値の数。値がデータ ソースから使用できない場合は NULL が返されます。|  
|ページ (ODBC 1.0)|12|Integer|インデックスまたはテーブルを格納するために使用するページ数。TYPE がSQL_TABLE_STAT場合は、テーブルのページ数。TYPE がSQL_TABLE_STATされていない場合は、インデックスのページ数。値がデータ ソースから使用できない場合、またはデータ ソースに適用できない場合は、NULL が返されます。|  
|FILTER_CONDITION (ODBC 2.0)|13|Varchar|索引がフィルター・インデックスの場合、これは、SALARY > 30000 などのフィルター条件です。フィルタ条件を判別できない場合、これは空の文字列です。<br /><br /> インデックスがフィルタされたインデックスでない場合は NULL、インデックスがフィルタされたインデックスであるか、TYPE がSQL_TABLE_STATかどうかを判断できません。|  
  
 結果セットの行がテーブルに対応する場合、ドライバは TYPE を SQL_TABLE_STAT に設定し、NON_UNIQUE、INDEX_QUALIFIER、INDEX_NAME、ORDINAL_POSITION、COLUMN_NAME、およびASC_OR_DESCを NULL に設定します。 データ ソースからカーディナリティまたは PAGES を使用できない場合、ドライバーは NULL に設定します。  
  
## <a name="code-example"></a>コード例  
 同様の関数のコード例については、「 [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|単一行またはデータブロックを順方向方向にフェッチする。|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|外部キーの列を返す|[SQLForeignKeys 関数](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|  
|主キーの列を返す|[SQLPrimaryKeys 関数](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
