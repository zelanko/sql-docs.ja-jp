---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCopyDesc
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLCopyDesc
helpviewer_keywords:
- SQLCopyDesc function [ODBC]
ms.assetid: d5450895-3824-44c4-8aa4-d4f9752a9602
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ef1fa5b319e8d72d5b70e6f2010e493eec6f844a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301229"
---
# <a name="sqlcopydesc-function"></a>SQLCopyDesc 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLCopyDesc は**、記述子情報をある記述子ハンドルから別の記述子ハンドルにコピーします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLCopyDesc(  
     SQLHDESC     SourceDescHandle,  
     SQLHDESC     TargetDescHandle);  
```  
  
## <a name="arguments"></a>引数  
 *ソースデスハンドル*  
 [入力]ソース記述子ハンドル。  
  
 *ターゲット・デスハンドル*  
 [入力]ターゲット記述子ハンドル。 引数*は*、アプリケーション記述子または IPD へのハンドルを指定できます。 *IRD*へのハンドルに対してターゲットのハンドルを設定できないか **、SQLCopyDesc**が SQLSTATE HY016 を返します (実装行記述子を変更できません)。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLCopyDesc が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_DESCの*ハンドル型*と*TargetDescHandle*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE 値を取得できます。 呼び出しで無効な*SourceDescHandle*が渡された場合、SQL_INVALID_HANDLEが返されますが、SQLSTATE は返されません。 次の表は **、SQLCopyDesc**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
 エラーが返されると **、SQLCopyDesc**の呼び出しは直ちに中止され *、TargetDescHandle*記述子のフィールドの内容は未定義になります。  
  
 **SQLCopyDesc**は**SQLGetDesc フィールド**と**SQLSetDesc フィールド**を呼び出すことによって実装される可能性があるため **、SQLCopyDesc**は**SQLGetDesc フィールド**または**SQLSetDescField**によって返される SQLSTATEEs を返す可能性があります。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY007|関連付けられたステートメントは準備されていません|*SourceDescHandle*は IRD に関連付けられており、関連付けられたステートメント ハンドルが準備済みまたは実行済みの状態ではありませんでした。|  
|HY010|関数シーケンス エラー|(DM) *SourceDescHandle*または*TargetDescHandle*の記述子ハンドルは、非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていた*ステートメント ハンドル*に関連付けられていた。<br /><br /> *TargetDescHandle* (DM)*記述子*ハンドルは、SQLExecute、SQLExecDirect、SQLBulkOperations 、または**SQLExecDirect****SQLBulkOperations****SQLSetPos**が呼び出され、SQL_NEED_DATA返された*ステートメント ハンドル*に関連付けられていた。 **SQLExecute** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM)*非同期*に実行される関数が呼び出されました。 *TargetDescHandle* この非同期関数は **、SQLCopyDesc**関数が呼び出されたときに実行されていました。<br /><br /> (DM) **SQL 実行****、SQLExecDirect**、または**SQLMoreResults**が、*ソースデスキューハンドル*または*ターゲットデスハンドル*に関連付けられたステートメントハンドルの 1 つに対して呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY016|実装行記述子を変更できません|*IRD に*関連付けられていた。|  
|HY021|記述子情報の不一致|整合性チェック中にチェックされた記述子情報が一貫していません。 詳細については、 **SQLSetDescField**の「整合性チェック」を参照してください。|  
|HY092|属性/オプション識別子が無効です|**SQLCopyDesc**の呼び出しは **、呼**び出しを要求しますが*\*、ValuePtr*は *、ターゲットの識別子**の引数*に対して有効ではありませんでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM) ソースに関連付けられているドライバー *、 ソースを*処理または*ターゲットをサポート*していません。|  
  
## <a name="comments"></a>説明  
 **SQLCopyDesc**の呼び出しは、ソース記述子ハンドルのフィールドをターゲット記述子ハンドルにコピーします。 フィールドは、アプリケーション記述子または IPD にのみコピーできますが、IRD にはコピーできません。 フィールドは、アプリケーションまたは実装記述子からコピーできます。  
  
 IRD からフィールドをコピーできるのは、ステートメント ハンドルが準備済みまたは実行状態の場合だけです。それ以外の場合、関数は SQLSTATE HY007 を返します (関連付けられたステートメントは準備されません)。  
  
 ステートメントが準備されているかどうかにかかわらず、フィールドを IPD からコピーすることができます。 動的パラメーターを持つ SQL ステートメントが準備され、IPD の自動作成がサポートされ、有効になっている場合、IPD はドライバーによって設定されます。 IPD を使用して**SQLCopyDesc**を*呼*び出すと、入力されたフィールドがコピーされます。 IPD がドライバによって設定されていない場合は、IPD の元のフィールドの内容がコピーされます。  
  
 SQL_DESC_ALLOC_TYPEを除くすべての記述子フィールド (記述子ハンドルが自動的に割り当てられたか明示的に割り振られたかを指定します) は、そのフィールドが宛先記述子に対して定義されているかどうかにかかわらずコピーされます。 コピーされたフィールドは、既存のフィールドを上書きします。  
  
 *SourceDescHandle*と*TargetDescHandle*引数が同じドライバーに関連付けられている場合、ドライバーは、2 つの異なる接続または環境上にある場合でも、すべての記述子フィールドをコピーします。 *SourceDescHandle*と*TargetDescHandle*引数が異なるドライバーに関連付けられている場合、ドライバー マネージャーは ODBC で定義されたフィールドをコピーしますが、記述子の種類に対して ODBC で定義されていないドライバー定義フィールドまたはフィールドはコピーしません。  
  
 エラーが発生すると **、SQLCopyDesc**の呼び出しは直ちに中止されます。  
  
 SQL_DESC_DATA_PTRフィールドがコピーされると、ターゲット記述子に対して整合性チェックが実行されます。 整合性チェックが失敗すると、SQLSTATE HY021 (整合性のない記述子情報) が返され **、SQLCopyDesc**の呼び出しは直ちに中止されます。 整合性チェックの詳細については、 [SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)の「整合性チェック」を参照してください。  
  
 記述子ハンドルは、接続が異なる環境にある場合でも、接続間でコピーできます。 ドライバー マネージャーは、ソースと宛先記述子ハンドルが同じ接続に属していないことを検出し、2 つの接続は、別々のドライバーに属している場合は **、SQLGetDescフィールド**と**SQLSetDesc フィールド**を使用してフィールドごとのコピーを実行することによって**SQLCopyDesc**を実装します。  
  
 **ある**ドライバーで*ソースを*呼び出し、別のドライバーで *、ターゲットを呼び出*すと、エラー キューがクリアされます *。* この場合 **、SQLCopyDesc**は**SQLGetDesc フィールドおよび SQLSetDescField**への呼び出しによって実装されているため**に発生します**。  
  
> [!NOTE]  
>  アプリケーションは **、SQLCopyDesc**を呼び出してある記述子から別の記述子にフィールドをコピーするのではなく、明示的に割り当てられた記述子ハンドルを*StatementHandle*に関連付けることができます。 明示的に割り当てられた記述子は、SQL_ATTR_APP_ROW_DESCまたはSQL_ATTR_APP_PARAM_DESCステートメント属性を明示的に割り当てられた記述子のハンドルに設定することで、同じ*ConnectionHandle*上の別の*ステートメント ハンドル*に関連付けることができます。 この処理が行われると、記述子フィールド値をある記述子から別の記述子にコピーするために**SQLCopyDesc**を呼び出す必要はありません。 ただし、記述子ハンドルを別の*ConnectionHandle*上のステートメント*ハンドル*に関連付けることはできません。ステートメント*の同*じ記述子フィールド値を使用する別の*接続ハンドルのハンドル***、SQLCopyDesc**を呼び出す必要があります。  
  
 記述子ヘッダーまたはレコードのフィールドの説明については、 [SQLSetDesc フィールド関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)を参照してください。 記述子の詳細については、[記述子](../../../odbc/reference/develop-app/descriptors.md)を参照してください。  
  
## <a name="copying-rows-between-tables"></a>テーブル間の行のコピー  
 アプリケーションは、アプリケーション レベルでデータをコピーせずに、あるテーブルから別のテーブルにデータをコピーできます。 これを行うために、アプリケーションは、データをフェッチするステートメントと、データをコピーに挿入するステートメントに、同じデータ バッファーと記述子情報をバインドします。 これは、アプリケーション記述子を共有する (ARD として明示的に割り当てられた記述子を 1 つのステートメントに、APD を別のステートメントにバインドする) か **、または SQLCopyDesc**を使用して、ARD と 2 つのステートメントの APD 間のバインディングをコピーすることによって行うことができます。 ステートメントが異なる接続にある場合は **、SQLCopyDesc を**使用する必要があります。 さらに、2 つのステートメントの IRD と IPD の間のバインディングをコピーするために **、SQLCopyDesc**を呼び出す必要があります。 同じ接続上のステートメント間でコピーする場合、この操作を成功させるには、ドライバーが**SQLGetInfo**を呼び出すためにドライバーから返されるSQL_ACTIVE_STATEMENTS情報の種類が 1 より大きい必要があります。 (これは、複数の接続をコピーする場合には当てはまらない)。  
  
### <a name="code-example"></a>コード例  
 次の例では、記述子操作を使用して、PartsSource テーブルのフィールドを PartsCopy テーブルにコピーします。 PartsSource テーブルの内容は *、hstmt0*の行セット バッファにフェッチされます。 これらの値は、PartCopy テーブルの列を設定するために *、hstmt1*上の INSERT ステートメントのパラメーターとして使用されます。 そのために *、hstmt0*の IRD のフィールドは *、hstmt1*の IPD のフィールドにコピーされ *、hstmt0*の ARD のフィールドが*hstmt1*の APD のフィールドにコピーされます。 出力パラメーターを持つステートメントから入力パラメーターである IPD フィールドに IRD フィールドをコピーするときに、IPD のSQL_DESC_PARAMETER_TYPE属性を SQL_PARAM_INPUT に設定するには **、SQLSetDescField**を使用します。  
  
```cpp  
#define ROWS 100  
#define DESC_LEN 50  
#define SQL_SUCCEEDED(rc) (rc == SQL_SUCCESS || rc == SQL_SUCCESS_WITH_INFO)  
  
// Template for a row  
typedef struct {  
   SQLINTEGER   sPartID;  
   SQLINTEGER   cbPartID;  
   SQLUCHAR     szDescription[DESC_LENGTH];  
   SQLINTEGER   cbDescription;  
   REAL         sPrice;  
   SQLINTEGER   cbPrice;  
} PartsSource;  
  
PartsSource    rget[ROWS];          // rowset buffer  
SQLUSMALLINT   sts_ptr[ROWS];       // status pointer  
SQLHSTMT       hstmt0, hstmt1;  
SQLHDESC       hArd0, hIrd0, hApd1, hIpd1;  
  
// ARD and IRD of hstmt0  
SQLGetStmtAttr(hstmt0, SQL_ATTR_APP_ROW_DESC, &hArd0, 0, NULL);  
SQLGetStmtAttr(hstmt0, SQL_ATTR_IMP_ROW_DESC, &hIrd0, 0, NULL);  
  
// APD and IPD of hstmt1  
SQLGetStmtAttr(hstmt1, SQL_ATTR_APP_PARAM_DESC, &hApd1, 0, NULL);  
SQLGetStmtAttr(hstmt1, SQL_ATTR_IMP_PARAM_DESC, &hIpd1, 0, NULL);  
  
// Use row-wise binding on hstmt0 to fetch rows  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_BIND_TYPE, (SQLPOINTER) sizeof(PartsSource), 0);  
  
// Set rowset size for hstmt0  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER) ROWS, 0);  
  
// Execute a select statement  
SQLExecDirect(hstmt0, "SELECT PARTID, DESCRIPTION, PRICE FROM PARTS ORDER BY 3, 1, 2"",  
               SQL_NTS);  
  
// Bind  
SQLBindCol(hstmt0, 1, SQL_C_SLONG, rget[0].sPartID, 0,   
   &rget[0].cbPartID);  
SQLBindCol(hstmt0, 2, SQL_C_CHAR, &rget[0].szDescription, DESC_LEN,   
   &rget[0].cbDescription);  
SQLBindCol(hstmt0, 3, SQL_C_FLOAT, rget[0].sPrice,   
   0, &rget[0].cbPrice);  
  
// Perform parameter bindings on hstmt1.   
SQLCopyDesc(hArd0, hApd1);  
SQLCopyDesc(hIrd0, hIpd1);  
  
// Set the array status pointer of IRD  
SQLSetStmtAttr(hstmt0, SQL_ATTR_ROW_STATUS_PTR, sts_ptr, SQL_IS_POINTER);  
  
// Set the ARRAY_STATUS_PTR field of APD to be the same  
// as that in IRD.  
SQLSetStmtAttr(hstmt1, SQL_ATTR_PARAM_OPERATION_PTR, sts_ptr, SQL_IS_POINTER);  
  
// Set the hIpd1 records as input parameters  
rc = SQLSetDescField(hIpd1, 1, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
rc = SQLSetDescField(hIpd1, 2, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
rc = SQLSetDescField(hIpd1, 3, SQL_DESC_PARAMETER_TYPE, (SQLPOINTER)SQL_PARAM_INPUT, SQL_IS_INTEGER);  
  
// Prepare an insert statement on hstmt1. PartsCopy is a copy of  
// PartsSource  
SQLPrepare(hstmt1, "INSERT INTO PARTS_COPY VALUES (?, ?, ?)", SQL_NTS);  
  
// In a loop, fetch a rowset, and copy the fetched rowset to PARTS_COPY  
  
rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);  
while (SQL_SUCCEEDED(rc)) {  
  
   // After the call to SQLFetchScroll, the status array has row   
   // statuses. This array is used as input status in the APD  
   // and hence determines which elements of the rowset buffer  
   // are inserted.  
   SQLExecute(hstmt1);  
  
   rc = SQLFetchScroll(hstmt0, SQL_FETCH_NEXT, 0);  
} // while  
```  
  
### <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|複数の記述子フィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|単一の記述子フィールドの設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|複数の記述子フィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
