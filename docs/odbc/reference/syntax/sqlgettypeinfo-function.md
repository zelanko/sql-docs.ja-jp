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
- SQLGetTypeInfo
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetTypeInfo
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC]
ms.assetid: bdedb044-8924-4ca4-85f3-8b37578e0257
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 47273c75a005f11b33e9929977b57607b36898de
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303263"
---
# <a name="sqlgettypeinfo-function"></a>SQLGetTypeInfo 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **データ**ソースでサポートされているデータ型に関する情報を返します。 ドライバーは、SQL 結果セットの形式で情報を返します。 データ型は、データ定義言語 (DDL) ステートメントで使用するためのデータ型です。  
  
> [!IMPORTANT]  
>  アプリケーションでは **、ALTER TABLE**ステートメントおよび**CREATE** TABLE ステートメントで**SQLGetTypeInfo**結果セットの TYPE_NAME 列に返される型名を使用する必要があります。 **DATA_TYPE列に**同じ値を持つ複数の行が返される場合があります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLGetTypeInfo(  
     SQLHSTMT      StatementHandle,  
     SQLSMALLINT   DataType);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]結果セットのステートメント ハンドル。  
  
 *DataType*  
 [入力]SQL データ型。 これは、「付録 D:[データ型」の「SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)」セクションの値のいずれか、またはドライバー固有の SQL データ型である必要があります。 SQL_ALL_TYPESすべてのデータ型に関する情報を返す必要があることを指定します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetTypeInfo**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLGetTypeInfo**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S02|オプション値が変更されました|指定されたステートメント属性は、実装の動作条件のために無効であったため、同様の値が一時的に置換されました。 (一時的に置換された値を決定するために**SQLGetStmtAttr**を呼び出します。代替値は、カーソルが閉じられるまで*ステートメント ハンドル*に対して有効です。 変更できるステートメント属性は、SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE、SQL_ATTR_KEYSET_SIZE、SQL_ATTR_MAX_LENGTH、SQL_ATTR_MAX_ROWS、SQL_ATTR_QUERY_TIMEOUT、およびSQL_ATTR_SIMULATE_CURSORです。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|24000|カーソル状態が無効|*ステートメントハンドル*でカーソルが開いていて **、SQLFetch または SQLFetchScroll** **が**呼び出されました。 このエラーは、ドライバー マネージャーが返す SQLFetch または**SQLFetchScrollSQL_NO_DATA**返されていない場合、ドライバー ドライバー マネージャーが返す **、SQL_NO_DATA****返された**場合は、ドライバーによって返されます。 **SQLFetch**<br /><br /> ステートメント*ハンドル*で結果セットが開かれていたが **、SQLFetch**または**SQLFetchScroll が**呼び出されていなかった。|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY004|無効な SQL データ型|*引数 DataType*に指定された値は、有効な ODBC SQL データ型識別子でも、ドライバがサポートするドライバ固有のデータ型識別子でもありませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効にされた後、関数が呼び出され、実行が完了する前にステートメント*ハンドル*で**SQLCancel**または**SQLCancelHandle**が呼び出されました。 その後、関数は*ステートメント ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLGetTypeInfo**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|SQL_ATTR_CONCURRENCYの現在の設定とSQL_ATTR_CURSOR_TYPEステートメント属性の組み合わせは、ドライバーまたはデータ ソースでサポートされていません。<br /><br /> SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_VARIABLE に設定され、SQL_ATTR_CURSOR_TYPE ステートメント属性が、ドライバーがブックマークをサポートしていないカーソルの種類に設定されました。|  
|ヒュット00|タイムアウトに達しました|クエリのタイムアウト期間が経過した後、データ ソースが結果セットを返しました。 タイムアウト期間は、SQL_ATTR_QUERY_TIMEOUT**を**使用して設定されます。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に対応するドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 **SQLGetTypeInfo は**、結果を標準の結果セットとして、DATA_TYPE順に並べ替え、データ型が対応する ODBC SQL データ型にどれだけ近い値でマップするかを返します。 データ ソースによって定義されたデータ型は、ユーザー定義のデータ型よりも優先されます。 したがって、ソート順は必ずしも一貫していませんが、最初にDATA_TYPE、続いてTYPE_NAME、両方の昇順として一般化できます。 たとえば、データ ソースで INTEGER および COUNTER データ型が定義されており、COUNTER が自動インクリメントされ、ユーザー定義データ型のデータ型が WHOLENUM も定義されているとします。 これらの値は整数、整数、およびカウンタの順序で返されます、整数は ODBC SQL データ型に密接にマップSQL_INTEGER、データ ソースでサポートされている場合でも、自動インクリメントデータ型は ODBC SQL データ型に密接にマップされません。 この情報の使用方法については[、DDL ステートメント](../../../odbc/reference/develop-app/ddl-statements.md)を参照してください。  
  
 *DataType*引数に、ドライバでサポートされている ODBC のバージョンに対して有効なデータ型が指定されているが、ドライバでサポートされていない場合、空の結果セットが返されます。  
  
> [!NOTE]  
>  ODBC カタログ関数の一般的な使用、引数、および返されるデータの詳細については、「[カタログ関数](../../../odbc/reference/develop-app/catalog-functions.md)」を参照してください。  
  
 次の列は、ODBC 3 の名前が変更されました。*x .* 列名の変更は、アプリケーションが列番号でバインドするため、下位互換性には影響しません。  
  
|ODBC 2.0 列|ODBC 3.*x*列|  
|---------------------|-----------------------|  
|PRECISION|COLUMN_SIZE|  
|MONEY|FIXED_PREC_SCALE|  
|AUTO_INCREMENT|AUTO_UNIQUE_VALUE|  
  
 ODBC 3 の**SQLGetTypeInfo**によって返される結果セットに、次の列が追加されました。*x*:  
  
-   SQL_DATA_TYPE  
  
-   INTERVAL_PRECISION  
  
-   SQL_DATETIME_SUB  
  
-   NUM_PREC_RADIX  
  
 次の表は、結果セット内の列の一覧です。 列 19 (INTERVAL_PRECISION) を超える追加の列は、ドライバーによって定義できます。 アプリケーションは、明示的な序数の位置を指定するのではなく、結果セットの末尾からカウントダウンして、ドライバー固有の列にアクセスする必要があります。 詳細については、「[カタログ関数によって返されるデータ](../../../odbc/reference/develop-app/data-returned-by-catalog-functions.md)」を参照してください。  
  
> [!NOTE]  
>  **一方、データ型**が返されない場合があります。 たとえば、ドライバーは、ユーザー定義のデータ型を返さない可能性があります。 **アプリケーションは、SQLGetTypeInfo**によって返されるかどうかにかかわらず、任意の有効なデータ型を使用できます。 **SQLGetTypeInfo**によって返されるデータ型は、データ ソースでサポートされるデータ型です。 これらは、データ定義言語 (DDL) ステートメントで使用するためのものではありません。 ドライバーは **、SQLGetTypeInfo**によって返される型以外のデータ型を使用して結果セット データを返すことができます。 カタログ関数の結果セットを作成する際、ドライバーは、データ ソースでサポートされていないデータ型を使用する可能性があります。  
  
|列名|列<br /><br /> number|データ型|説明|  
|-----------------|-----------------------|---------------|--------------|  
|TYPE_NAME (ODBC 2.0)|1|NULL ではないヴァルチャー|データ ソース依存のデータ型名。たとえば、"CHAR()"、"VARCHAR()"、"マネー"、"ロングVARBINARY"、またはビットデータの場合は「CHAR 」()、または"CHAR ( )"。 アプリケーションは **、CREATE TABLE**ステートメントおよび**ALTER TABLE**ステートメントでこの名前を使用する必要があります。|  
|DATA_TYPE (ODBC 2.0)|2|Smallint (NULL 以外)|SQL データ型。 これは、ODBC SQL データ型またはドライバー固有の SQL データ型です。 日時型または間隔データ型の場合、この列は簡潔なデータ型 (SQL_TYPE_TIME、SQL_INTERVAL_YEAR_TO_MONTHなど) を返します。 有効な ODBC SQL データ型の一覧については、「付録 D: データ型」の[SQL データ型](../../../odbc/reference/appendixes/sql-data-types.md)を参照してください。 ドライバー固有の SQL データ型については、ドライバーのドキュメントを参照してください。|  
|COLUMN_SIZE (ODBC 2.0)|3|Integer|このデータ型に対してサーバーがサポートする列の最大サイズ。 数値データの場合、これは最大精度です。 文字列データの場合、これは文字数の長さです。 datetime データ型の場合、これは文字列表現の文字数の長さです (秒の小数部の要素の最大許容精度を想定)。 列サイズが適用されないデータ型に対して NULL が返されます。 間隔データ型の場合、これは間隔リテラルの文字表現の文字数です (間隔の先行精度で定義されているとおり、付録 D: データ[型の「間隔データ型の長さ](../../../odbc/reference/appendixes/interval-data-type-length.md)」を参照)。<br /><br /> 列サイズの詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長、および表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|LITERAL_PREFIX (ODBC 2.0)|4|Varchar|リテラルの先頭に使用される 1 つまたは 1 つの文字。たとえば、文字データ型の場合は単一引用符 (')、バイナリ データ型の場合は 0x、バイナリ データ型の場合は 0x、文字データ型の場合は 0x、2 進データ型の場合は 0 を指定します。リテラルプレフィックスが適用されないデータ型に対して NULL が返されます。|  
|LITERAL_SUFFIX (ODBC 2.0)|5|Varchar|リテラルを終了するために使用される 1 つまたは 1 つの文字。たとえば、文字データ型の単一引用符 (') を指定します。リテラルサフィックスが適用されないデータ型に対して NULL が返されます。|  
|CREATE_PARAMS (ODBC 2.0)|6|Varchar|TYPE_NAME フィールドに返される名前を使用する場合に、アプリケーションがかっこで囲んで指定できる各パラメーターに対応する、コンマで区切られたキーワードのリスト。 リスト内のキーワードには、長さ、精度、または位取りのいずれかのキーワードを指定できます。 これらは、構文の使用が必要な順序で表示されます。 たとえば、DECIMAL のCREATE_PARAMSは"精度、小数点以下桁数"です。varchar のCREATE_PARAMSは"長さ"に等しくなります。 データ型定義にパラメーターがない場合は NULL が返されます。たとえば、整数型の整数型の値を指定します。<br /><br /> ドライバーは、使用する国/地域の言語でCREATE_PARAMSテキストを提供します。|  
|NULL 可能 (ODBC 2.0)|7|Smallint (NULL 以外)|データ型が NULL 値を受け入れるかどうか。<br /><br /> データ型が NULL 値を受け入れない場合はSQL_NO_NULLS。<br /><br /> データ型が NULL 値を受け入れる場合にSQL_NULLABLEします。<br /><br /> 列が NULL 値を受け入れるかどうかが不明な場合はSQL_NULLABLE_UNKNOWNします。|  
|CASE_SENSITIVE (ODBC 2.0)|8|Smallint (NULL 以外)|照合順序と比較で文字データ型の大文字と小文字が区別されるかどうか:<br /><br /> SQL_TRUEデータ型が文字データ型であり、大文字と小文字が区別される場合です。<br /><br /> SQL_FALSEデータ型が文字データ型でないか、大文字と小文字が区別されない場合です。|  
|検索可能 (ODBC 2.0)|9|Smallint (NULL 以外)|**WHERE**句でのデータ型の使用方法:<br /><br /> 列を**WHERE**句で使用できない場合はSQL_PRED_NONEします。 (これは、ODBC 2 のSQL_UNSEARCHABLE値と同じです。*x.*<br /><br /> SQL_PRED_CHAR、列を**WHERE**句で使用できますが **、LIKE**述語でのみ使用できる場合。 (これは、ODBC 2 のSQL_LIKE_ONLY値と同じです。*x.*<br /><br /> LIKE**を除くすべての**比較演算子 (比較、定量化比較 **、BETWEEN** **、DISTINCT** **、IN** **、MATCH**、**および UNIQUE)** を含む**WHERE**句で列を使用できる場合SQL_PRED_BASIC。 (これは ODBC 2 のSQL_ALL_EXCEPT_LIKE値と同じです。*x.*<br /><br /> SQL_SEARCHABLE、任意の比較演算子を使用して**WHERE**句で列を使用できる場合。|  
|UNSIGNED_ATTRIBUTE (ODBC 2.0)|10|Smallint|データ型が符号なしかどうか:<br /><br /> データ型が符号なしの場合にSQL_TRUEします。<br /><br /> データ型が署名されている場合にSQL_FALSEします。<br /><br /> 属性がデータ型に適用できない場合、またはデータ型が数値でない場合は NULL が返されます。|  
|FIXED_PREC_SCALE (ODBC 2.0)|11|Smallint (NULL 以外)|データ型に、固定精度と小数点以下桁数 (データ ソース固有) が事前定義されているかどうか(money データ型など)。<br /><br /> SQL_TRUE固定精度と小数点次桁数が事前定義されている場合。<br /><br /> SQL_FALSE定義済みの固定精度と小数点次桁数がない場合に使用します。|  
|AUTO_UNIQUE_VALUE (ODBC 2.0)|12|Smallint|データタイプが自動増分されているかどうか:<br /><br /> データ型が自動増分の場合にSQL_TRUEします。<br /><br /> データ型が自動増分でない場合にSQL_FALSEします。<br /><br /> 属性がデータ型に適用できない場合、またはデータ型が数値でない場合は NULL が返されます。<br /><br /> アプリケーションは、この属性を持つ列に値を挿入できますが、通常は列の値を更新することはできません。<br /><br /> 挿入が自動インクリメント列に作成されると、挿入時に一意の値が列に挿入されます。 増分は定義されていませんが、データ ソース固有です。 アプリケーションでは、自動インクリメント列が特定のポイントで開始されるか、特定の値で増分されると想定しないでください。|  
|LOCAL_TYPE_NAME (ODBC 2.0)|13|Varchar|データ 型のデータ ソース依存名のローカライズバージョン。 ローカライズされた名前がそのデータ ソースによってサポートされない場合は NULL が返されます。 この名前は、ダイアログ ボックスなどでの表示のみを目的としています。|  
|MINIMUM_SCALE (ODBC 2.0)|14|Smallint|データ ソースのデータ型の最小縮尺。 データ型の小数点以下桁数が固定されている場合は、MINIMUM_SCALE 列および MAXIMUM_SCALE 列の両方にこの値が入ります。 たとえば、SQL_TYPE_TIMESTAMP列には、秒数の小数部の固定小数点以下桁数が含まれている場合があります。 スケールが適用されない場合は NULL が返されます。 詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長さ」および「表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|MAXIMUM_SCALE (ODBC 2.0)|15|Smallint|データ ソースのデータ型の最大スケール。 スケールが適用されない場合は NULL が返されます。 最大スケールがデータ ソースで個別に定義されていないが、その代わりに最大精度と同じとして定義されている場合、この列にはCOLUMN_SIZE列と同じ値が含まれます。 詳細については、「付録 D: データ型」の[「列サイズ、10 進数、転送オクテット長さ」および「表示サイズ](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)」を参照してください。|  
|SQL_DATA_TYPE (ODBC 3.0)|16|NULL でない Smallint|記述子のSQL_DESC_TYPE フィールドに表示される SQL データ型の値。 この列は、間隔および日時のデータ型を除き、DATA_TYPE列と同じです。<br /><br /> 間隔データ型および日時データ型の場合、結果セットのSQL_DATA_TYPEフィールドはSQL_INTERVALまたはSQL_DATETIMEを返し、SQL_DATETIME_SUBフィールドは特定の間隔または日時データ型のサブコードを返します。 ([付録 D: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)を参照してください。|  
|SQL_DATETIME_SUB (ODBC 3.0)|17|Smallint|SQL_DATA_TYPEの値がSQL_DATETIMEまたはSQL_INTERVALの場合、この列には日時/間隔サブコードが含まれます。 日時および間隔以外のデータ・タイプの場合、このフィールドは NULL です。<br /><br /> 間隔または日時のデータ型の場合、結果セットのSQL_DATA_TYPE フィールドはSQL_INTERVALまたはSQL_DATETIMEを返し、SQL_DATETIME_SUB フィールドは特定の間隔または日時データ型のサブコードを返します。 ([付録 D: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)を参照してください。|  
|NUM_PREC_RADIX (ODBC 3.0)|18|Integer|データ型が概数値型の場合、この列には、COLUMN_SIZEビット数を指定することを示す値 2 が含まれます。 正確な数値型の場合、この列には、COLUMN_SIZEが 10 進数の桁数を指定することを示す値 10 が含まれます。 その他の場合、この列は NULL になります。|  
|INTERVAL_PRECISION (ODBC 3.0)|19|Smallint|データ・タイプが間隔データ・タイプの場合、この列には、間隔先行精度の値が入ります。 (付録 D:[データ型の「間隔データ型の精度](../../../odbc/reference/appendixes/interval-data-type-precision.md)」を参照してください。それ以外の場合、この列は NULL です。|  
  
 属性情報は、データ型または結果セット内の特定の列に適用できます。 **データ型に**関連付けられた属性に関する情報を返します。**結果**セット内の列に関連付けられた属性に関する情報を返します。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|結果セット内の列へのバッファーのバインディング|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|結果セット内の列に関する情報を返す|[SQLColAttribute 関数](../../../odbc/reference/syntax/sqlcolattribute-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|単一行またはデータブロックを順方向方向にフェッチする|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|ドライバーまたはデータ ソースに関する情報を返す|[SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
