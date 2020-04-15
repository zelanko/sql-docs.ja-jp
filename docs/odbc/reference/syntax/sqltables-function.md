---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTables
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTables
helpviewer_keywords:
- SQLTables function [ODBC]
ms.assetid: 60d5068a-7d7c-447c-acc6-f3f2cf73440c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae52e6431679ed0f260e6885090ac38363b4ef3d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287132"
---
# <a name="sqltables-function"></a>SQLTables 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: オープングループ  
  
 **まとめ**  
 **SQLTables は**、特定のデータ ソースに格納されているテーブル、カタログ、またはスキーマ名、およびテーブルの種類の一覧を返します。 ドライバーは、結果セットとして情報を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLTables(  
     SQLHSTMT       StatementHandle,  
     SQLCHAR *      CatalogName,  
     SQLSMALLINT    NameLength1,  
     SQLCHAR *      SchemaName,  
     SQLSMALLINT    NameLength2,  
     SQLCHAR *      TableName,  
     SQLSMALLINT    NameLength3,  
     SQLCHAR *      TableType,  
     SQLSMALLINT    NameLength4);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]取得した結果のステートメント ハンドル。  
  
 *カタログ名*  
 [入力]カタログ名。 *引数 CatalogName*は、SQL_ODBC_VERSION環境属性がSQL_OV_ODBC3場合は検索パターンを受け入れます。SQL_OV_ODBC2が設定されている場合、検索パターンは受け入れません。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしているドライバーでは、空の文字列 ("" ) は、カタログを持たないテーブルを示します。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、CatalogName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合 *、CatalogName*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。 詳細については、「[カタログ関数の引数](../../../odbc/reference/develop-app/arguments-in-catalog-functions.md)」を参照してください。  
  
 *NameLength1*  
 [入力]* カタログ*名*の文字での長さ。  
  
 *Schemaname*  
 [入力]スキーマ名の文字列検索パターン。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、スキーマを持たないテーブルを示す空の文字列 (") が表示されます。  
  
 SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定されている場合 *、SchemaName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合、*スキーマ名*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 2*  
 [入力]**スキーマ名*の文字での長さ。  
  
 *TableName*  
 [入力]テーブル名の文字列検索パターン。  
  
 SQL_ATTR_METADATA_IDステートメント属性が SQL_TRUE に設定されている場合 *、TableName*は識別子として扱われ、大文字と小文字は意味がありません。 SQL_FALSE場合 *、TableName*はパターン値の引数です。それは文字通り扱われ、そのケースは重要です。  
  
 *名前の長さ 3*  
 [入力]**テーブル名*の文字での長さ。  
  
 *テーブルタイプ*  
 [入力]一致するテーブルの種類のリスト。  
  
 SQL_ATTR_METADATA_IDステートメント属性は *、引数 TableType*には影響しません。 *テーブルタイプ*は、SQL_ATTR_METADATA_IDの設定に関係なく、値リストの引数です。  
  
 *名前の長さ4*  
 [入力]**テーブル型*の文字での長さ。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLTables**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、関連付けられた SQLSTATE 値を取得するには *、SQL_HANDLE_STMTのハンドル型*と*ステートメント ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出します。 次の表は、SQLTables によって返される**SQLSTATE**値の一覧と、この関数のコンテキストでの各値の説明です。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
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
|HY009|無効な null ポインターの使用|SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、*引数 CatalogName*が null ポインターであり、SQL_CATALOG_NAME *InfoType*はカタログ名がサポートされていることを返します。<br /><br /> (DM) SQL_ATTR_METADATA_IDステートメント属性がSQL_TRUEに設定され、引数*SchemaName*または*TableName*が null ポインターでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は、SQLTables が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 長さの引数の 1 つの値が 0 より小さいが、SQL_NTSと等しくない。<br /><br /> 名前長引数の 1 つの値が、対応する名前の最大長の値を超えました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|カタログが指定され、ドライバまたはデータ ソースがカタログをサポートしていません。<br /><br /> スキーマが指定され、ドライバーまたはデータ ソースがスキーマをサポートしていません。<br /><br /> カタログ名、テーブル スキーマ、またはテーブル名に文字列検索パターンが指定されていますが、データ ソースは、これらの引数の 1 つ以上の検索パターンをサポートしていません。<br /><br /> SQL_ATTR_CONCURRENCYの現在の設定とSQL_ATTR_CURSOR_TYPEステートメント属性の組み合わせは、ドライバーまたはデータ ソースでサポートされていません。<br /><br /> SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_VARIABLE に設定され、SQL_ATTR_CURSOR_TYPE ステートメント属性が、ドライバーがブックマークをサポートしていないカーソルの種類に設定されました。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが要求された結果セットを返しました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUT**を**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 **SQLTables は**、要求された範囲内のすべてのテーブルを一覧表示します。 ユーザーは、これらのテーブルに対する SELECT 権限を持つ場合と持たない場合があります。 アクセシビリティを確認するために、アプリケーションは次の操作を実行できます。  
  
-   **SQLGetInfo を**呼び出し、SQL_ACCESSIBLE_TABLES情報の種類を確認します。  
  
-   各テーブルの特権をチェックするには **、SQLTablePrivileges**を呼び出します。  
  
 それ以外の場合、アプリケーションは、ユーザーが**SELECT**特権が付与されていない表を選択する状況を処理できる必要があります。  
  
 *スキーマ名*と*テーブル名*の引数は、検索パターンを受け入れます。 *引数 CatalogName*は、SQL_ODBC_VERSION環境属性がSQL_OV_ODBC3場合は検索パターンを受け入れます。SQL_OV_ODBC2が設定されている場合、検索パターンは受け入れません。 SQL_OV_ODBC3設定されている場合、ODBC 3 *.x*ドライバは *、引数 CatalogName*のワイルドカード文字をエスケープして、文字どおり扱う必要があります。 有効な検索パターンの詳細については、「[パターン値の引数](../../../odbc/reference/develop-app/pattern-value-arguments.md)」を参照してください。  
  
> [!NOTE]  
>  ODBC カタログ関数の一般的な使用、引数、および返されるデータの詳細については、「[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)」を参照してください。  
  
 カタログ、スキーマ、およびテーブル型の列挙をサポートするために **、SQLTable**の*カタログ名*、*スキーマ名*、*テーブル名*、および*TableType*の引数に対して次の特別なセマンティクスが定義されています。  
  
-   *CatalogName*がSQL_ALL_CATALOGSされ、*スキーマ名*と*テーブル名*が空の文字列である場合、結果セットにはデータ ソースの有効なカタログの一覧が含まれます。 (TABLE_CAT列以外のすべての列には、ヌルが含まれています。  
  
-   *スキーマ名*がSQL_ALL_SCHEMASされ、*カタログ名*と*テーブル名*が空の文字列である場合、結果セットにはデータ ソースの有効なスキーマの一覧が含まれます。 (TABLE_SCHEM列以外のすべての列には、ヌルが含まれています。  
  
-   *TableType*がSQL_ALL_TABLE_TYPESで、*カタログ名*、*スキーマ名*、および*テーブル名*が空の文字列である場合、結果セットにはデータ ソースに有効なテーブル型の一覧が含まれます。 (TABLE_TYPE列以外のすべての列には、ヌルが含まれています。  
  
 *TableType*が空の文字列でない場合は、対象の型のコンマ区切り値のリストを含める必要があります。各値は、単一引用符 (') または引用符なし ('TABLE'、'VIEW'、または TABLE、VIEW) で囲むことができます。 アプリケーションでは、常にテーブルの種類を大文字で指定する必要があります。ドライバーは、データ ソースで必要な大文字と小文字を表の種類に変換する必要があります。 データ ソースが指定されたテーブル型をサポートしていない場合 **、SQLTables**はその型の結果を返しません。  
  
 **SQLTables は**、結果を標準の結果セットとして、TABLE_TYPE、TABLE_CAT、TABLE_SCHEM、およびTABLE_NAME順に並べ替えて返します。 この情報の使用方法については、「[カタログ データの使用](../../../odbc/reference/develop-app/uses-of-catalog-data.md)」を参照してください。  
  
 TABLE_CAT、TABLE_SCHEM、およびTABLE_NAME列の実際の長さを決定するために、アプリケーションは、SQL_MAX_CATALOG_NAME_LEN、SQL_MAX_SCHEMA_NAME_LEN、およびSQL_MAX_TABLE_NAME_LENの情報型を使用して**SQLGetInfo**を呼び出すことができます。  
  
 次の列は、ODBC 3 *.x*の名前が変更されました。 列名の変更は、アプリケーションが列番号でバインドするため、下位互換性には影響しません。  
  
|ODBC 2.0 列|ODBC 3 *.x*列|  
|---------------------|-----------------------|  
|TABLE_QUALIFIER|TABLE_CAT|  
|TABLE_OWNER|TABLE_SCHEM|  
  
 次の表は、結果セット内の列の一覧です。 5 列 (REMARKS) を超える追加の列は、ドライバーによって定義できます。 アプリケーションは、明示的な序数の位置を指定するのではなく、結果セットの末尾からカウントダウンして、ドライバー固有の列にアクセスする必要があります。 詳細については、「[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)」を参照してください。  
  
|列名|列番号|データ型|説明|  
|-----------------|-------------------|---------------|--------------|  
|TABLE_CAT (ODBC 1.0)|1|Varchar|カタログ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのカタログをサポートしているが、他のテーブルについてはサポートしない場合は、カタログを持たないテーブルの空の文字列 ("" ) を返します。|  
|TABLE_SCHEM (ODBC 1.0)|2|Varchar|スキーマ名。データ ソースに適用できない場合は NULL。 ドライバーが異なる DBMS からデータを取得する場合など、一部のテーブルのスキーマをサポートしているドライバーは、スキーマを持たないテーブルの空の文字列 ("" ) を返します。|  
|TABLE_NAME (ODBC 1.0)|3|Varchar|テーブル名。|  
|TABLE_TYPE (ODBC 1.0)|4|Varchar|テーブル型名。次の 1 つ: "テーブル"、"表示"、"システム テーブル"、"グローバル一時"、"LOCAL 一時"、"ALIAS"、"シノニム"、またはデータ ソース固有の型名。<br /><br /> "ALIAS" と "SYNONYM" の意味は、ドライバー固有です。|  
|注釈 (ODBC 1.0)|5|Varchar|テーブルの説明。|  
  
## <a name="example"></a>例  
 次のサンプル コードでは、ハンドルと接続を解放しません。 ハンドルとステートメントを解放するコード サンプルについては[、SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)および[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)を参照してください。  
  
```cpp  
// SQLTables.cpp  
// compile with: user32.lib odbc32.lib  
#include <windows.h>  
#include <sqlext.h>  
#include <strsafe.h>  
  
// simple helper functions  
int MySQLSuccess(SQLRETURN rc) {  
   return (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO);  
}  
  
struct DataBinding {  
   SQLSMALLINT TargetType;  
   SQLPOINTER TargetValuePtr;  
   SQLINTEGER BufferLength;  
   SQLLEN StrLen_or_Ind;  
};  
  
void printCatalog(const struct DataBinding* catalogResult) {  
   if (catalogResult[0].StrLen_or_Ind != SQL_NULL_DATA)   
      printf("Catalog Name = %s\n", (char *)catalogResult[0].TargetValuePtr);  
}  
  
// remember to disconnect and free memory, and free statements and handles  
int main() {  
   int bufferSize = 1024, i, numCols = 5;  
   struct DataBinding* catalogResult = (struct DataBinding*) malloc( numCols * sizeof(struct DataBinding) );  
   wchar_t* dbName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
   wchar_t* userName = (wchar_t *)malloc( sizeof(wchar_t)*bufferSize );  
  
   // declare and initialize the environment, connection, statement handles  
   SQLHENV henv = NULL;   // Environment     
   SQLHDBC hdbc = NULL;   // Connection handle  
   SQLHSTMT hstmt = NULL;   // Statement handle  
  
   SQLRETURN retCode;  
   HWND desktopHandle = GetDesktopWindow();   // desktop's window handle  
   SQLWCHAR connStrbuffer[1024];  
   SQLSMALLINT connStrBufferLen;  
  
   retCode = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv);  
   retCode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (void*)SQL_OV_ODBC3, -1);  
   retCode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc);  
   retCode = SQLSetConnectAttr(hdbc, SQL_LOGIN_TIMEOUT, (SQLPOINTER)10, 0);  
   retCode = SQLDriverConnect(hdbc, desktopHandle, (SQLCHAR*)"Driver={SQL Server}", SQL_NTS, (SQLCHAR*)connStrbuffer, 1024 + 1, &connStrBufferLen, SQL_DRIVER_PROMPT);  
   retCode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt);  
   retCode = SQLGetInfo(hdbc, SQL_DATABASE_NAME, dbName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferSize);  
   retCode = SQLGetInfo(hdbc, SQL_USER_NAME, userName, (SQLSMALLINT)bufferSize, (SQLSMALLINT *)&bufferSize);  
  
   bufferSize = 1024;  
  
   // allocate memory for the binding  
   // free this memory when done  
   for ( i = 0 ; i < numCols ; i++ ) {  
      catalogResult[i].TargetType = SQL_C_CHAR;  
      catalogResult[i].BufferLength = (bufferSize + 1);  
      catalogResult[i].TargetValuePtr = malloc( sizeof(unsigned char)*catalogResult[i].BufferLength );  
   }  
  
   // setup the binding (can be used even if the statement is closed by closeStatementHandle)  
   for ( i = 0 ; i < numCols ; i++ )  
      retCode = SQLBindCol(hstmt, (SQLUSMALLINT)i + 1, catalogResult[i].TargetType, catalogResult[i].TargetValuePtr, catalogResult[i].BufferLength, &(catalogResult[i].StrLen_or_Ind));  
  
   // all catalogs query  
   printf( "A list of names of all catalogs\n" );  
   retCode = SQLTables( hstmt, (SQLCHAR*)SQL_ALL_CATALOGS, SQL_NTS, (SQLCHAR*)"", SQL_NTS, (SQLCHAR*)"", SQL_NTS, (SQLCHAR*)"", SQL_NTS );  
   for ( retCode = SQLFetch(hstmt) ;  MySQLSuccess(retCode) ; retCode = SQLFetch(hstmt) )  
      printCatalog( catalogResult );  
}  
```  
  
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
|表の特権の戻り|[SQLTablePrivileges 関数](../../../odbc/reference/syntax/sqltableprivileges-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
