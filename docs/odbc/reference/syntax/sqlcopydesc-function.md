---
title: "SQLCopyDesc 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLCopyDesc
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCopyDesc
helpviewer_keywords:
- SQLCopyDesc function [ODBC]
ms.assetid: d5450895-3824-44c4-8aa4-d4f9752a9602
caps.latest.revision: 19
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e8e7383a16b40a966612784e864594588cc37199
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlcopydesc-function"></a>SQLCopyDesc 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLCopyDesc**記述子が 1 つのハンドルから記述子情報をコピーします。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLCopyDesc(  
     SQLHDESC     SourceDescHandle,  
     SQLHDESC     TargetDescHandle);  
```  
  
## <a name="arguments"></a>引数  
 *SourceDescHandle*  
 [入力]ソース記述子ハンドルです。  
  
 *TargetDescHandle*  
 [入力]ターゲット記述子ハンドルです。 *TargetDescHandle*引数は、IPD アプリケーション記述子へのハンドルを指定できます。 *TargetDescHandle* 、IRD へのハンドルに設定することはできませんまたは**SQLCopyDesc** SQLSTATE HY016 (実装行記述子は修正できません) が返されます。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLCopyDesc** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_DESC と*処理*の*TargetDescHandle*です。 場合、無効な*SourceDescHandle*渡されたの呼び出しで SQL_INVALID_HANDLE が返されますが、SQLSTATE は返されません。 次の表に、一般的にによって返される SQLSTATE 値**SQLCopyDesc**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
 エラーが返される場合、呼び出し**SQLCopyDesc**すぐに中止されると、および内のフィールドの内容、 *TargetDescHandle*記述子が定義されていません。  
  
 **SQLCopyDesc**呼び出すことによって実装される場合があります**SQLGetDescField**と**SQLSetDescField**、 **SQLCopyDesc**返す可能性がありますによって返される SQLSTATEs **SQLGetDescField**または**SQLSetDescField**です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、 * \*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY007|関連付けられたステートメントが準備されていません|*SourceDescHandle* IRD では、関連付けられていたし、関連付けられているステートメント ハンドルは、準備または実行された状態ではありませんでした。|  
|HY010|関数のシーケンス エラー|(DM) では、記述子の処理*SourceDescHandle*または*TargetDescHandle*が関連付けられて、 *StatementHandle*を非同期的に実行中の関数 (notこの 1 つ) が呼び出され、この関数が呼び出されたときに実行されています。<br /><br /> (DM) では、記述子の処理*SourceDescHandle*または*TargetDescHandle*が関連付けられて、 *StatementHandle*を**SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**が呼び出され、SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *SourceDescHandle*または*TargetDescHandle*です。 この非同期関数がまだ実行したときに、 **SQLCopyDesc**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に関連付けられているステートメント ハンドルのいずれかで呼び出され、 *SourceDescHandle*または*TargetDescHandle* SQL_PARAM_DATA_AVAILABLE を返されるとします。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY016|実装行記述子は変更できません。|*TargetDescHandle* IRD に関連付けました。|  
|HY021|不整合な記述子情報|整合性チェック中にチェック記述子の情報が一致していません。 詳細についてを参照してください「整合性チェック」 **SQLSetDescField**です。|  
|HY092|無効な属性またはオプション識別子|呼び出し**SQLCopyDesc**への呼び出しの入力を求め**SQLSetDescField**が* \*ValuePtr*が、無効、 *FieldIdentifier*の引数で*TargetDescHandle*です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *SourceDescHandle*または*TargetDescHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 呼び出し**SQLCopyDesc**ソース記述子のフィールドを処理対象の記述子ハンドルをコピーします。 フィールドは、IRD ではなく、アプリケーション記述子または、IPD にのみコピーできます。 フィールドは、アプリケーションまたは実装記述子からコピーすることができます。  
  
 フィールドは、ステートメント ハンドルが準備または実行された状態である場合にのみ、IRD からコピーできます。SQLSTATE HY007 を返しますそれ以外の場合 (関連付けられたステートメントが準備されていません)。  
  
 フィールドは、ステートメントが準備されているかどうか、IPD からコピーすることができます。 動的パラメーターを含む SQL ステートメントが準備され、IPD の自動作成がサポートされていて有効になっているの場合は、ドライバーによって、IPD が設定されます。 ときに**SQLCopyDesc**として IPD してを呼び出すと、 *SourceDescHandle*、設定されたフィールドをコピーします。 ドライバーによって、IPD が設定されていない場合、IPD で最初のフィールドの内容がコピーされます。  
  
 (を指定するかどうか記述子ハンドルが自動的にまたは明示的に割り当てられた) SQL_DESC_ALLOC_TYPE を除く、記述子のすべてのフィールドは、宛先記述子フィールドが定義されているかどうかにコピーされます。 コピーしたフィールドは、既存のフィールドを上書きします。  
  
 場合、ドライバーがすべての記述子フィールドをコピー、 *SourceDescHandle*と*TargetDescHandle*引数に割り当てられた同じドライバーをドライバーが 2 つの接続上にある場合でも、または環境。 場合、 *SourceDescHandle*と*TargetDescHandle*引数が別のドライバーに関連付けられた、ドライバー マネージャー、ODBC で定義されたフィールドのコピーは、ドライバー定義のフィールドをコピーしませんまたはフィールド型記述子の ODBC で定義されているはありません。  
  
 呼び出し**SQLCopyDesc**エラーが発生した場合はすぐに中止されます。  
  
 SQL_DESC_DATA_PTR フィールドをコピーすると、ターゲット記述子の一貫性チェックが実行されます。 整合性チェックが失敗した場合は、SQLSTATE HY021 (不整合な記述子情報) が返されますを呼び出すと**SQLCopyDesc**はすぐに中止します。 整合性チェックの詳細についてを参照してください「整合性チェック」 [SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)です。  
  
 記述子ハンドルは、接続がさまざまな環境下にある場合でも接続間でコピーできます。 ドライバー マネージャーは、ソースと、移行先記述子ハンドルは、同じ接続と 2 つの接続には属していないドライバーを個別に属している、実装することが検出された場合**SQLCopyDesc**フィールドごとのフィールドを実行することによって使用してコピー **SQLGetDescField**と**SQLSetDescField**です。  
  
 ときに**SQLCopyDesc**してを呼び出すと、 *SourceDescHandle*で 1 つのドライバーと*TargetDescHandle*別のドライバーのエラーのキューに、 *SourceDescHandle*がオフになっています。 これは、ために発生**SQLCopyDesc**への呼び出しによってここでは実装されて**SQLGetDescField**と**SQLSetDescField**です。  
  
> [!NOTE]  
>  アプリケーションは、使用して、明示的に割り当てられた記述子ハンドルを関連付けることができる可能性があります、 *StatementHandle*、呼び出し元ではなく**SQLCopyDesc**フィールドを別の記述子が 1 つにコピーします。 明示的に割り当てられた記述子は別に関連付けられる*StatementHandle*同じ*ConnectionHandle* SQL_ATTR_APP_ROW_DESC または SQL_ATTR_APP_PARAM_DESC ステートメントを設定して属性の明示的に割り当てられた記述子ハンドルにします。 これが完了したら、 **SQLCopyDesc**記述子が 1 つの記述子フィールドの値をコピーするに呼び出せる必要はありません。 記述子ハンドルが関連付けられることはできません、 *StatementHandle*別の*ConnectionHandle*、ただし; で同じ記述子フィールドの値を使用する*StatementHandles*別に*ConnectionHandles*、 **SQLCopyDesc**が呼び出されます。  
  
 記述子のヘッダーまたはレコードのフィールドの説明は、次を参照してください。 [SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)です。 記述子の詳細については、次を参照してください。[記述子](../../../odbc/reference/develop-app/descriptors.md)です。  
  
## <a name="copying-rows-between-tables"></a>テーブル間の行のコピー  
 アプリケーションは、可能性がありますデータ 1 つのテーブルからにコピー別、アプリケーション レベルでデータをコピーせずします。 これを行うには、アプリケーションは、データをフェッチするステートメントとコピーにデータを挿入するステートメントを同じデータ バッファーと記述子の情報をバインドします。 これには、(1 つのステートメントに ARD と別の APD の両方として明示的に割り当てられた記述子のバインド) アプリケーション記述子を共有することで、またはを使用して**SQLCopyDesc** ARD 間のバインディングをコピーし、2 つのステートメントの APD です。 ステートメントが別の接続にある場合**SQLCopyDesc**使用する必要があります。 さらに、 **SQLCopyDesc**は、IRD と IPD 2 つのステートメントの間のバインディングをコピーするに呼び出せるようにします。 同じ接続でステートメントの間でコピーへの呼び出しのドライバーで SQL_ACTIVE_STATEMENTS 情報の種類が返されます。 **SQLGetInfo**を成功させるには、この操作を 1 より大きい必要があります。 (これはない場合の接続間でコピーするときにします。)  
  
### <a name="code-example"></a>コード例  
 次の例では、記述子の操作は PartsCopy テーブル PartsSource テーブルのフィールドにコピーに使用されます。 PartsSource テーブルの内容が内の行セットのバッファーにフェッチされて*hstmt0*です。 これらの値は、INSERT ステートメントのパラメーターとして使用される*hstmt1* PartsCopy テーブルの列の設定にします。 表示するには、IRD のフィールド*hstmt0*の IPD のフィールドにコピーされます*hstmt1*のフィールドと、フィールドの ARD *hstmt0* のAPDのフィールドにコピーされます*hstmt1*です。 使用して**SQLSetDescField** IRD フィールドを出力パラメーターを持つステートメントからの入力パラメーターを指定する必要がある IPD フィールドにコピーするときに SQL_PARAM_INPUT を IPD の SQL_DESC_PARAMETER_TYPE 属性を設定します。  
  
```  
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
  
|詳細|参照先|  
|---------------------------|---------|  
|複数の記述子フィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|1 つの記述子フィールドの設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|複数の記述子フィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
