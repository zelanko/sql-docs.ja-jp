---
title: SQLCopyDesc 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e165ca48af3b634f1dcbe80c05c83f2c872d1b01
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47642780"
---
# <a name="sqlcopydesc-function"></a>SQLCopyDesc 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLCopyDesc**記述子の情報の 1 つの記述子ハンドルのコピーします。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLCopyDesc(  
     SQLHDESC     SourceDescHandle,  
     SQLHDESC     TargetDescHandle);  
```  
  
## <a name="arguments"></a>引数  
 *SourceDescHandle*  
 [入力]ソース記述子ハンドル。  
  
 *TargetDescHandle*  
 [入力]ターゲットの記述子ハンドル。 *TargetDescHandle*引数は、アプリケーション記述子を IPD へのハンドルを指定できます。 *TargetDescHandle* 、IRD へのハンドルに設定することはできませんまたは**SQLCopyDesc** SQLSTATE HY016 が (実装行記述子は変更できません) が返されます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLCopyDesc** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得できる**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_DESC と*処理*の*TargetDescHandle*します。 場合、無効な*SourceDescHandle*渡された呼び出しで SQL_INVALID_HANDLE が返されますが、SQLSTATE は返されません。 次の表に、一般的にによって返される SQLSTATE 値**SQLCopyDesc** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
 エラーが返される場合、呼び出し**SQLCopyDesc**がすぐに中止されたと内のフィールドの内容、 *TargetDescHandle*記述子が定義されていません。  
  
 **SQLCopyDesc**呼び出すことによって実装される場合があります**SQLGetDescField**と**SQLSetDescField**、 **SQLCopyDesc**返す可能性がありますによって返される SQLSTATEs **SQLGetDescField**または**SQLSetDescField**します。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンク エラー|関数が完了した処理の前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクに失敗しました。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY007|関連付けられているステートメントが準備されていません|*SourceDescHandle*は、IRD の関連付けと関連付けられているステートメント ハンドルは、準備または実行された状態ではありませんでした。|  
|HY010|関数のシーケンス エラー|記述子ハンドルが (DM) *SourceDescHandle*または*TargetDescHandle*に関連付けられているが、 *StatementHandle*を非同期的に実行中の関数 (notこの 1 つ) が呼び出された、この関数が呼び出されたときに実行されています。<br /><br /> 記述子ハンドルが (DM) *SourceDescHandle*または*TargetDescHandle*に関連付けられているが、 *StatementHandle*を**SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**が呼び出され、SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) を非同期的に実行中の関数が呼び出された接続ハンドルに関連付けられているため、 *SourceDescHandle*または*TargetDescHandle*します。 この非同期関数ではときに実行されている、 **SQLCopyDesc**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に関連付けられているステートメント ハンドルのいずれかが呼び出された、 *SourceDescHandle*または*TargetDescHandle* SQL_PARAM_DATA_AVAILABLE が返されます。 ストリームのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY016|実装行記述子は変更できません。|*TargetDescHandle* IRD に関連付けられていた。|  
|HY021|不整合な記述子情報|整合性チェック中にチェックする記述子の情報は、一貫性のあるでした。 詳細についてを参照してください「整合性チェック」 **SQLSetDescField**します。|  
|HY092|無効な属性またはオプション識別子|呼び出し**SQLCopyDesc**への呼び出しの入力を求め**SQLSetDescField**が *\*ValuePtr*は無効です、 *FieldIdentifier*引数*TargetDescHandle*します。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *SourceDescHandle*または*TargetDescHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 呼び出し**SQLCopyDesc**ソース記述子のフィールドを処理対象の記述子ハンドルをコピーします。 フィールドは、IRD ではなく、アプリケーション記述子をまたは、IPD にのみコピーできます。 フィールドは、アプリケーションまたは実装記述子からコピーできます。  
  
 フィールドは、ステートメント ハンドルが、準備または実行された状態である場合にのみ、IRD からコピーできます。SQLSTATE HY007 を返しますそれ以外の場合、(関連付けられているステートメントが準備されていません)。  
  
 ステートメントは準備ができているかどうかを示す、フィールドは、IPD からコピーできます。 動的パラメーターを含む SQL ステートメントが準備されて、IPD の自動作成がサポートされ、有効な場合は、ドライバーによって、IPD が設定されます。 ときに**SQLCopyDesc**として IPD を呼び出すと、 *SourceDescHandle*、設定されたフィールドがコピーされます。 ドライバーによって、IPD が設定されていない場合は、IPD で最初のフィールドの内容がコピーされます。  
  
 (元の記述子ハンドルが自動的にまたは明示的に割り当てられたアドレスを指定) SQL_DESC_ALLOC_TYPE を除く、記述子のすべてのフィールドは、変換先の記述子フィールドが定義されているかどうかにコピーされます。 コピーしたフィールドは、既存のフィールドを上書きします。  
  
 場合、ドライバーがすべての記述子フィールドをコピー、 *SourceDescHandle*と*TargetDescHandle*引数は、2 つの異なる接続でのドライバーがある場合でも同じのドライバーに関連付けられたまたは環境。 場合、 *SourceDescHandle*と*TargetDescHandle*引数は、さまざまなドライバーに関連付けられた、ドライバー マネージャー、ODBC で定義されたフィールドをコピーしますがドライバーで定義されたフィールドをコピーしませんまたはフィールド型記述子の odbc は定義されません。  
  
 呼び出し**SQLCopyDesc**エラーが発生した場合はすぐに中止します。  
  
 SQL_DESC_DATA_PTR フィールドがコピーされるターゲット記述子の整合性チェックが実行されます。 整合性チェックが失敗した場合は、SQLSTATE HY021 (不整合な記述子情報) が返されるとへの呼び出し**SQLCopyDesc**はすぐに中止されます。 整合性チェックの詳細についてを参照してください「整合性チェック」 [SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)します。  
  
 記述子ハンドルは、さまざまな環境での接続がある場合でも、接続間でコピーできます。 ドライバー マネージャーは、ソースと宛先記述子ハンドルは、同じ接続と 2 つの接続には属していないドライバーの分離に属している、実装することが検出された場合**SQLCopyDesc**フィールドごとのフィールドを実行することによって使用してコピー **SQLGetDescField**と**SQLSetDescField**します。  
  
 ときに**SQLCopyDesc**を呼び出すと、 *SourceDescHandle*で 1 つのドライバーと*TargetDescHandle*別のドライバーのエラー キューで、 *SourceDescHandle*がオフになっています。 これは、 **SQLCopyDesc**への呼び出しによってこのケースでは実装されて**SQLGetDescField**と**SQLSetDescField**します。  
  
> [!NOTE]  
>  アプリケーションは、明示的に割り当てられた記述子ハンドルとを関連付けることができる可能性があります、 *StatementHandle*、呼び出し元ではなく**SQLCopyDesc**記述子が 1 つからフィールドをコピーします。 明示的に割り当てられた記述子を別に関連付けることができます*StatementHandle*同じ*ConnectionHandle* SQL_ATTR_APP_ROW_DESC または SQL_ATTR_APP_PARAM_DESC ステートメントの設定属性の明示的に割り当てられた記述子ハンドルをします。 これが完了したら、 **SQLCopyDesc**間の記述子が 1 つの記述子フィールドの値をコピーするために呼び出すことはありません。 記述子ハンドルが関連付けられることはできません、 *StatementHandle*別*ConnectionHandle*、ただし; で同じの記述子フィールドの値を使用する*StatementHandles*で異なる*ConnectionHandles*、 **SQLCopyDesc**呼び出す必要があります。  
  
 記述子のヘッダーまたはレコードのフィールドの説明は、次を参照してください。 [SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)します。 記述子の詳細については、次を参照してください。[記述子](../../../odbc/reference/develop-app/descriptors.md)します。  
  
## <a name="copying-rows-between-tables"></a>テーブル間の行のコピー  
 アプリケーションがからデータをコピー 1 つのテーブル間アプリケーション レベルでデータをコピーせず。 これを行うには、アプリケーションは、データをフェッチするステートメントとコピーにデータを挿入するステートメントに、同じデータ バッファーと記述子の情報をバインドします。 (を明示的に割り当てられた記述子を 1 つのステートメントに ARD と別の APD の両方としてバインディング) アプリケーション記述子を共有することで、またはを使用してこれを実現することができます**SQLCopyDesc** ARD 間のバインディングをコピーして2 つのステートメントの APD します。 場合、ステートメントは、異なる接続で**SQLCopyDesc**使用する必要があります。 さらに、 **SQLCopyDesc** IRD と IPD 2 つのステートメントの間のバインドのコピーを呼び出す必要があります。 SQL_ACTIVE_STATEMENTS 情報の種類がへの呼び出し用のドライバーによって返される、同じ接続でステートメントの間でデータをコピーするとき**SQLGetInfo**を成功させるのには、この操作を 1 より大きい必要があります。 (このそうでない接続間でコピーするときにします。)  
  
### <a name="code-example"></a>コード例  
 次の例では、記述子の操作は PartsSource テーブルのフィールドを PartsCopy テーブルにコピーに使用されます。 PartsSource テーブルの内容は、行セットのバッファーにフェッチされて*hstmt0*します。 これらの値がで INSERT ステートメントのパラメーターとして使用される*hstmt1* PartsCopy テーブルの列の設定にします。 そのための ird フィールドに*hstmt0*の IPD フィールドにコピーされます*hstmt1*の ARD のフィールドと*hstmt0* のAPDのフィールドにコピーされます*hstmt1*します。 使用**SQLSetDescField** IRD フィールドを出力パラメーターを持つステートメントからは入力パラメーターとして指定する必要がある IPD フィールドにコピーする場合に SQL_PARAM_INPUT IPD の SQL_DESC_PARAMETER_TYPE 属性を設定します。  
  
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
