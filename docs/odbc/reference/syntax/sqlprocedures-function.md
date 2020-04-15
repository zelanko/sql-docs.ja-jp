---
title: SQL プロシージャ関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4c8b8a9f22f6005d1af811e56485299bad3a425
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306843"
---
# <a name="sqlprocedures-function"></a>SQLProcedures 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: ODBC  
  
 **まとめ**  
 **SQLProcedures は**、特定のデータ ソースに格納されているプロシージャ名の一覧を返します。 *プロシージャ*は、*実行可能オブジェクト*を記述するために使用される総称、または入力および出力パラメーターを使用して呼び出すことができる名前付きエンティティです。 手順の詳細については、[の手順](../../../odbc/reference/develop-app/procedures-odbc.md)を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
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
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *カタログ名*  
 [入力]プロシージャ カタログ。 ドライバーが、異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしている場合、空の文字列 (") は、カタログを持たないテーブルを表します。 *カタログ名に*文字列検索パターンを含めることはできません。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、CatalogName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合 *、CatalogName*は通常の引数です。それは文字通り扱われ、そのケースは重要です。 詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。  
  
 *NameLength1*  
 [入力]* カタログ*名*の文字での長さ。  
  
 *Schemaname*  
 [入力]プロシージャ スキーマ名の文字列検索パターン。 ドライバーが異なる DBMS からデータを取得する場合など、一部のプロシージャのスキーマをサポートしているドライバーの場合は、空の文字列 (") は、スキーマを持たないプロシージャを表します。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、SchemaName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合、*スキーマ名*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 2*  
 [入力]**スキーマ名*の文字での長さ。  
  
 *プロク名*  
 [入力]プロシージャ名の文字列検索パターン。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、ProcName*は識別子として扱われ、その大文字と小文字は意味がありません。 SQL_FALSE場合 *、ProcName*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 3*  
 [入力]* の文字での長*さ*です。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLProcedures が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec** *を呼*び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLProcedures によって**一般的に返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|24000|カーソル状態が無効|*ステートメント ハンドル*でカーソルが開かれていたし **、SQL フェッチ**または SQL**フェッチスクロール**が呼び出されました。 このエラーは、ドライバー マネージャーが返す SQLFetch または**SQLFetchScrollSQL_NO_DATA**返されていない場合、ドライバー ドライバー マネージャーが返す **、SQL_NO_DATA****返された**場合は、ドライバーによって返されます。 **SQLFetch**<br /><br /> *ステートメント ハンドル*でカーソルが開かれていたが **、SQLFetch**または**SQLFetchScroll が**呼び出されていませんでした。|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前に、*ステートメント ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、関数は*ステートメント ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY009|無効な null ポインターの使用|SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、*引数 CatalogName*が null ポインターであり、SQL_CATALOG_NAME *InfoType*はカタログ名がサポートされていることを返します。<br /><br /> (DM) SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、引数*の引数*が*ProcName*null ポインターでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は、この関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 名前長引数の 1 つの値が 0 より小さいが、SQL_NTSと等しくない。<br /><br /> 名前長引数の 1 つの値が、対応する名前の最大長の値を超えました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|プロシージャ カタログが指定され、ドライバまたはデータ ソースがカタログをサポートしていません。<br /><br /> プロシージャ スキーマが指定され、ドライバまたはデータ ソースがスキーマをサポートしていません。<br /><br /> プロシージャ スキーマまたはプロシージャ名に文字列検索パターンが指定されており、データ ソースは、これらの引数の 1 つ以上の検索パターンをサポートしていません。<br /><br /> SQL_ATTR_CONCURRENCYの現在の設定とSQL_ATTR_CURSOR_TYPEステートメント属性の組み合わせは、ドライバーまたはデータ ソースでサポートされていません。<br /><br /> SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_VARIABLE に設定され、SQL_ATTR_CURSOR_TYPE ステートメント属性が、ドライバーがブックマークをサポートしていないカーソルの種類に設定されました。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが要求された結果セットを返しました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUT**を**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、この関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 **SQLProcedures は**、要求された範囲内のすべてのプロシージャーをリストします。 ユーザーは、これらのプロシージャを実行する権限を持っている場合と、権限を持たない場合があります。 アクセシビリティを確認するために、アプリケーションは**SQLGetInfo**を呼び出し、SQL_ACCESSIBLE_PROCEDURES情報値を確認できます。 それ以外の場合、アプリケーションは、ユーザーが実行できないプロシージャを選択する状況を処理できる必要があります。 この情報の使用方法については、「[手順](../../../odbc/reference/develop-app/procedures-odbc.md)」を参照してください。  
  
> [!NOTE]  
>  ODBC カタログ関数の一般的な使用、引数、および返されるデータの詳細については、「[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)」を参照してください。  
  
 **SQLProcedures は**、結果を標準の結果セットとして、PROCEDURE_CAT、PROCEDURE_SCHEMA、およびPROCEDURE_NAME順に並べ替えて返します。  
  
> [!NOTE]  
>  **SQL プロシージャーがすべてのプロシージャーを**戻すわけではありません。 アプリケーションは、 **SQLProcedures**によって返されるかどうかにかかわらず、有効なプロシージャを使用できます。  
  
 次の列は、ODBC 3 *.x*の名前が変更されました。 列名の変更は、アプリケーションが列番号でバインドするため、下位互換性には影響しません。  
  
|ODBC 2.0 列|ODBC 3 *.x*列|  
|---------------------|-----------------------|  
|PROCEDURE_QUALIFIER|PROCEDURE_CAT|  
|手順_OWNER|手順_SCHEM|  
  
 PROCEDURE_CAT、PROCEDURE_SCHEM、およびPROCEDURE_NAME列の実際の長さを決定するために、アプリケーションは、SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、およびSQL_MAX_PROCEDURE_NAME_LENのオプションを指定して**SQLGetInfo**を呼び出すことができます。  
  
 次の表は、結果セット内の列の一覧です。 列 8 (PROCEDURE_TYPE) を超える追加の列は、ドライバーによって定義できます。 アプリケーションは、明示的な序数の位置を指定するのではなく、結果セットの末尾からカウントダウンして、ドライバー固有の列にアクセスする必要があります。 詳細については、「[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)」を参照してください。  
  
|列名|列番号|データ型|説明|  
|-----------------|-------------------|---------------|--------------|  
|PROCEDURE_CAT (ODBC 2.0)|1|Varchar|プロシージャ カタログ識別子。データ ソースに適用できない場合は NULL。 ドライバーが異なる Dbms からデータを取得する場合など、一部のプロシージャのカタログをサポートしている場合、ドライバーは、カタログを持たないプロシージャの空の文字列 ("" ) を返します。|  
|PROCEDURE_SCHEM (ODBC 2.0)|2|Varchar|プロシージャ スキーマ識別子。データ ソースに適用できない場合は NULL。 ドライバーが異なる Dbms からデータを取得する場合など、一部のプロシージャのスキーマをサポートしているドライバーは、スキーマを持たないプロシージャの空の文字列 ("" ) を返します。|  
|PROCEDURE_NAME (ODBC 2.0)|3|NULL ではないヴァルチャー|プロシージャ識別子。|  
|NUM_INPUT_PARAMS (ODBC 2.0)|4|該当なし|将来利用するために予約されています。 アプリケーションは、これらの結果列で返されるデータに依存しないでください。|  
|NUM_OUTPUT_PARAMS (ODBC 2.0)|5|該当なし|将来利用するために予約されています。 アプリケーションは、これらの結果列で返されるデータに依存しないでください。|  
|NUM_RESULT_SETS (ODBC 2.0)|6|該当なし|将来利用するために予約されています。 アプリケーションは、これらの結果列で返されるデータに依存しないでください。|  
|注釈 (ODBC 2.0)|7|Varchar|プロシージャの説明。|  
|PROCEDURE_TYPE (ODBC 2.0)|8|Smallint|プロシージャの種類を定義します。<br /><br /> SQL_PT_UNKNOWN: プロシージャが値を返すかどうかを判断できません。<br /><br /> SQL_PT_PROCEDURE: 返されるオブジェクトはプロシージャです。つまり、戻り値はありません。<br /><br /> SQL_PT_FUNCTION: 返されるオブジェクトは関数です。つまり、戻り値を持ちます。|  
  
 *引数*は、検索*パターンを受*け入れます。 有効な検索パターンの詳細については、「[パターン値の引数](../../../odbc/reference/develop-app/pattern-value-arguments.md)」を参照してください。  
  
## <a name="code-example"></a>コード例  
 [「プロシージャ コール」を](../../../odbc/reference/develop-app/procedure-calls.md)参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|単一行またはデータブロックを順方向方向にフェッチする|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|ドライバーまたはデータ ソースに関する情報を返す|[SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|プロシージャのパラメータおよび結果セット列を返す|[SQLProcedureColumns 関数](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|  
|ストアド プロシージャを呼び出すための構文|[ステートメントの実行](../../../odbc/reference/develop-app/executing-statements-odbc.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
