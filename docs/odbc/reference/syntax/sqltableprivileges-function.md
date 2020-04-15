---
title: 関数を使用する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTablePrivileges
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTablePrivileges
helpviewer_keywords:
- SQLTablePrivileges function [ODBC]
ms.assetid: 8cfdb64f-64c5-47e6-ad57-0533ac630afa
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2d8260dd285fb3f5bbb9fcdaeaaebf1586090179
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282922"
---
# <a name="sqltableprivileges-function"></a>SQLTablePrivileges 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: ODBC  
  
 **まとめ**  
 **テーブル**のリストと、各テーブルに関連付けられた特権を返します。 ドライバーは、指定されたステートメントの結果セットとして情報を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLTablePrivileges(  
     SQLHSTMT      StatementHandle,  
     SQLCHAR *     CatalogName,  
     SQLSMALLINT   NameLength1,  
     SQLCHAR *     SchemaName,  
     SQLSMALLINT   NameLength2,  
     SQLCHAR *     TableName,  
     SQLSMALLINT   NameLength3);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *カタログ名*  
 [入力]テーブル カタログ。 ドライバーが、異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしている場合、空の文字列 (") は、カタログを持たないテーブルを表します。 *カタログ名に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、CatalogName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合 *、CatalogName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。 詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。  
  
 *NameLength1*  
 [入力]* カタログ*名*の文字での長さ。  
  
 *Schemaname*  
 [入力]スキーマ名の文字列検索パターン。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、"" はスキーマを持たないテーブルを表します。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、SchemaName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合、*スキーマ名*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 2*  
 [入力]**スキーマ名*の文字での長さ。  
  
 *TableName*  
 [入力]テーブル名の文字列検索パターン。  
  
 SQL_ATTR_METADATA_IDステートメント属性が SQL_TRUE に設定されている場合 *、TableName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合 *、TableName*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 3*  
 [入力]**テーブル名*の文字での長さ。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLTablePrivileges が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときに、関連付けられた SQLSTATE 値を取得するには、SQL_HANDLE_STMT*のハンドル型*と*ステートメント ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出します。 次の表は **、SQLTablePrivileges**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*でカーソルが開かれていたし **、SQL フェッチ**または SQL**フェッチスクロール**が呼び出されました。 このエラーは、ドライバー マネージャーが返す SQLFetch または**SQLFetchScroll**がSQL_NO_DATA返されていない場合は**SQLFetchScroll****、ドライバー**マネージャーが返す、ドライバーによって返されますSQL_NO_DATA返された場合は、**ドライバー**によって返されます。<br /><br /> *ステートメント ハンドル*でカーソルが開かれていたが **、SQLFetch**または**SQLFetchScroll が**呼び出されていませんでした。|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数**が**呼び出され、実行が完了する前に、**ステートメント***ハンドル*で SQL キャンセルまたは SQL**キャンセル ハンドル**が呼び出されました。 その後、ステートメント*ハンドル*で**関数**が再び呼び出されました。<br /><br /> **関数**が呼び出され、実行が完了する前に、マルチスレッド アプリケーションの別のスレッドからステートメント ハンドルに対して**SQLCancel**または*StatementHandle***SQLCancelHandle**が呼び出されました。|  
|HY009|無効な null ポインターの使用|SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、*引数 CatalogName*が null ポインターであり、SQL_CATALOG_NAME *InfoType*はカタログ名がサポートされていることを返します。<br /><br /> (DM) SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、引数*SchemaName*または*TableName*が null ポインターでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は、**関数**が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 名前長引数の 1 つの値が 0 より小さいが、SQL_NTSと等しくない。<br /><br /> 名前の長さ引数の 1 つの値が、対応する修飾子または名前の最大長の値を超えました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|カタログが指定され、ドライバまたはデータ ソースがカタログをサポートしていません。<br /><br /> スキーマが指定され、ドライバーまたはデータ ソースがスキーマをサポートしていません。<br /><br /> テーブル スキーマ、テーブル名、または列名に文字列検索パターンが指定されていますが、データ ソースは、これらの引数の 1 つ以上の検索パターンをサポートしていません。<br /><br /> SQL_ATTR_CONCURRENCYの現在の設定とSQL_ATTR_CURSOR_TYPEステートメント属性の組み合わせは、ドライバーまたはデータ ソースでサポートされていません。<br /><br /> SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_VARIABLE に設定され、SQL_ATTR_CURSOR_TYPE ステートメント属性が、ドライバーがブックマークをサポートしていないカーソルの種類に設定されました。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが結果セットを返しました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUT**を**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 *スキーマ名*と*テーブル名*の引数は、検索パターンを受け入れます。 有効な検索パターンの詳細については、「[パターン値の引数](../../../odbc/reference/develop-app/pattern-value-arguments.md)」を参照してください。  
  
 **結果**は、TABLE_CAT、TABLE_SCHEM、TABLE_NAME、特権、および GRANTEE の順に並べられた標準結果セットとして返されます。  
  
 TABLE_CAT、TABLE_SCHEM、およびTABLE_NAME列の実際の長さを決定するために、アプリケーションは、SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、およびSQL_MAX_TABLE_NAME_LENのオプションを指定して**SQLGetInfo**を呼び出すことができます。  
  
> [!NOTE]  
>  ODBC カタログ関数の一般的な使用、引数、および返されるデータの詳細については、「[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)」を参照してください。  
  
 次の列は、ODBC *3.x*の名前が変更されました。 列名の変更は、アプリケーションが列番号でバインドするため、下位互換性には影響しません。  
  
|ODBC 2.0 列|ODBC *3.x*列|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 次の表は、結果セット内の列の一覧です。 列 7 (IS_GRANTABLE) を超える追加の列は、ドライバーによって定義できます。 アプリケーションは、明示的な序数の位置を指定するのではなく、結果セットの末尾からカウントダウンして、ドライバー固有の列にアクセスする必要があります。 詳細については、「[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)」を参照してください。  
  
|列名|列番号|データ型|説明|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|カタログ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしているが、他のテーブルについてはサポートしない場合は、カタログを持たないテーブルの空の文字列 ("" ) を返します。|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|スキーマ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、スキーマを持たないテーブルの空の文字列 ("" ) を返します。|  
|TABLE_NAME (ODBC 1.0)|3|NULL ではないヴァルチャー|テーブル名。|  
|グランター (ODBC 1.0)|4|Varchar|特権を付与したユーザーの名前。データ ソースに適用できない場合は NULL。<br /><br /> GRANTEE 列の値がオブジェクトの所有者であるすべての行に対して、GRANTOR 列は 「_SYSTEM」 になります。|  
|グラントイー (ODBC 1.0)|5|NULL ではないヴァルチャー|特権が付与されたユーザーの名前。|  
|特権 (ODBC 1.0)|6|NULL ではないヴァルチャー|テーブルの特権。 次のいずれかまたはデータ ソース固有の特権があります。<br /><br /> SELECT: 権限付与対象ユーザーは、テーブルの 1 つ以上の列のデータを取得できます。<br /><br /> INSERT: 権限付与対象ユーザーは、1 つ以上の列のデータを含む新しい行を表に挿入できます。<br /><br /> 更新: 権限付与対象ユーザーは、テーブルの 1 つ以上の列のデータを更新できます。<br /><br /> DELETE: 権限付与対象ユーザーは、テーブルからデータの行を削除できます。<br /><br /> 参照: 権限付与対象者は、制約内の表の 1 つ以上の列 (例えば、固有、参照、または表検査制約) を参照することが許可されます。<br /><br /> 特定のテーブル特権によって被付与者に許可されたアクションの範囲は、データ・ソースに依存します。 たとえば、UPDATE 特権を使用すると、権限付与対象ユーザーは、あるデータ ソースのテーブルのすべての列を更新でき、付与者が別のデータ ソースに対して UPDATE 特権を持つ列のみを更新できます。|  
|IS_GRANTABLE (ODBC 1.0)|7|Varchar|権限付与対象ユーザーが特権を他のユーザーに付与できるかどうかを示します。"YES"、"NO"、または NULL (不明な場合、またはデータ ソースに適用されない場合)。<br /><br /> 特権は付与可能であるか、付与できないかのどちらかですが、両方は付与されません。 **SQLColumnPrivileges**によって返される結果セットには、IS_GRANTABLE列以外のすべての列に同じ値が含まれる 2 つの行が含まれることはありません。|  
  
## <a name="code-example"></a>コード例  
 同様の関数のコード例については、「 [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|列の特権の取得|[SQLColumnPrivileges 関数](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)|  
|テーブル内の列を返す|[SQLColumns 関数](../../../odbc/reference/syntax/sqlcolumns-function.md)|  
|単一行またはデータブロックを順方向方向にフェッチする|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|テーブルの統計とインデックスを返す|[SQLStatistics 関数](../../../odbc/reference/syntax/sqlstatistics-function.md)|  
|データ ソース内のテーブルの一覧を返す|[SQLTables 関数](../../../odbc/reference/syntax/sqltables-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
