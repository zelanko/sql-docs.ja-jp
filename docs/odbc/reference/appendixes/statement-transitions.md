---
title: "ステートメントの遷移 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transitioning states [ODBC], statement
- state transitions [ODBC], statement
- statement transitions [ODBC]
ms.assetid: 3d70e0e3-fe83-4b4d-beac-42c82495a05b
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 328529660d13c324e0d69749285c9e0022a04405
ms.sourcegitcommit: 50e9ac6ae10bfeb8ee718c96c0eeb4b95481b892
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2017
---
# <a name="statement-transitions"></a>ステートメントの遷移
ODBC ステートメントでは、次の状態があります。  
  
|状態|Description|  
|-----------|-----------------|  
|S0|未割り当てのステートメント。 (接続の状態は、C4、C5、または C6 にする必要があります。 詳細については、次を参照してください[接続遷移](../../../odbc/reference/appendixes/connection-transitions.md)。)。|  
|S1|割り当てられているステートメントです。|  
|S2|準備されたステートメント。 結果セットは作成されません。|  
|S3|準備されたステートメント。 (おそらく空の) 結果セットが作成されます。|  
|S4|実行されるステートメントの結果セットがありませんが作成されたとします。|  
|S5|実行されるステートメントを (おそらく空の) 結果セットが作成されたとします。 カーソルは、開いていると、結果セットの最初の行の前に配置されているがします。|  
|S6|カーソルを置いた状態**SQLFetch**または**SQLFetchScroll**です。|  
|S7|カーソルを置いた状態**SQLExtendedFetch**です。|  
|S8|関数には、データが必要があります。 **SQLParamData**が呼び出されていません。|  
|S9|関数には、データが必要があります。 **SQLPutData**が呼び出されていません。|  
|S10|関数には、データが必要があります。 **SQLPutData**が呼び出されています。|  
|S11|まだ実行中です。 非同期的に実行される関数に SQL_STILL_EXECUTING が返された後に、ステートメントはこの状態のままです。 ステートメントを受け付けるために、ステートメント ハンドルを実行する任意の関数の中にこの状態は一時的にします。 S11 がの状態テーブル以外の状態テーブルに表示されていない状態で一時居住**SQLCancel**です。 関数を呼び出すことによってキャンセルできますステートメントは、状態 S11 で一時的には、 **SQLCancel**別のスレッドからです。|  
|S12|非同期の実行が取り消されました。 S12、メンバー SQL_STILL_EXECUTING 以外の値が返されるまでに、アプリケーションで処理が取り消されました関数を呼び出す必要があります。 SQL_ERROR と SQLSTATE HY008 関数が返す場合にのみ、関数が正常に取り消されました (操作が取り消されました)。 場合は SQL_SUCCESS、取り消し操作は失敗と通常実行される関数など、他の任意の値を返します。|  
  
 カーソルの状態、必要データの状態として S10 を通じて S8 の状態、および非同期の遷移の状態の S11 と S12 S7 を通じて S5 を示す状態 S2、S3 は準備済みの状態と呼ばれます。 これらのグループの各遷移は個別に表示が異なるグループ内の各状態の場合にのみほとんどの場合、各遷移状態の各グループが同じです。  
  
 次の表では、各 ODBC 関数がステートメントの状態に与える影響を示しています。  
  
## <a name="sqlallochandle"></a>SQLAllocHandle  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1], [5], [6]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[2], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|S1 [3]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
|--[4], [5]|--[5]|--[5]|--[5]|--[5]|--[5]|--[5]|  
  
 [1] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_ENV をがします。  
  
 [2] この行は、移行を示しています。 ときに*HandleType* sql_handle_dbc としてをがします。  
  
 [3] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_STMT をがします。  
  
 [4] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_DESC をがします。  
  
 [5] 通話**SQLAllocHandle**で*OutputHandlePtr*を以前の内容を処理し、ODBC ドライバーの問題が発生する可能性がありますに関係なく、そのハンドルを上書き有効なハンドルを指すです。 呼び出す ODBC アプリケーション プログラミングを不適切なである**SQLAllocHandle**に対して定義されている同じアプリケーションの変数を 2 回 *\*OutputHandlePtr*呼び出さず**SQLFreeHandle**にそれを再割り当てする前に、ハンドルを解放します。 ODBC を上書きするようにハンドルを動作の一貫性がや部分の ODBC ドライバー エラーにつながる可能性があります。  
  
## <a name="sqlbindcol"></a>SQLBindCol  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbindparameter"></a>SQLBindParameter  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|--|--|--|--|HY010|HY010|  
  
## <a name="sqlbrowseconnect-sqlconnect-and-sqldriverconnect"></a>SQLBrowseConnect、SQLConnect、および SQLDriverConnect  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|08002|08002|08002|08002|08002|08002|08002|  
  
## <a name="sqlbulkoperations"></a>SQLBulkOperations  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|HY010|HY010|24000|次の表を参照してください。|HY010|NS [c] HY010 o|  
  
## <a name="sqlbulkoperations-cursor-states"></a>SQLBulkOperations (カーソルの状態)  
  
|S5<br /><br /> 開く|S6<br /><br /> SQLFetch または SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|-[s] S8 [d] S11 [x]|-[s] S8 [d] S11 [x]|HY010|  
  
## <a name="sqlcancel"></a>SQLCancel  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|--|--|--|--|S1 [1] S2 [nr] と [2] S3 [r] および [2] の S5 [3] と [5] S6 ([3] または [4]) し、[6] S7 [4] [7]、|次の表を参照してください。|  
  
 [1] **SQLExecDirect** SQL_NEED_DATA が返されます。  
  
 [2] **SQLExecute** SQL_NEED_DATA が返されます。  
  
 [3] **SQLBulkOperations** SQL_NEED_DATA が返されます。  
  
 [4] **SQLSetPos** SQL_NEED_DATA が返されます。  
  
 [5] **SQLFetch**、 **SQLFetchScroll**、または**SQLExtendedFetch**が呼び出されていません。  
  
 [6] **SQLFetch**または**SQLFetchScroll**が呼び出されました。  
  
 [7] **SQLExtendedFetch**が呼び出されました。  
  
## <a name="sqlcancel-asynchronous-states"></a>SQLCancel (非同期状態)  
  
|S11<br /><br /> まだ実行中|S12<br /><br /> 非同期のキャンセル|  
|-----------------------------|-----------------------------|  
|[1] NS S12 [2]|S12|  
  
 [1] で、ステートメントは、関数の実行中に状態 S11 で一時的にしました。 **SQLCancel**が別のスレッドから呼び出されました。  
  
 [2] のステートメントは、非同期的に呼び出される関数には、SQL_STILL_EXECUTING が返されたために、状態 S11 だった。  
  
## <a name="sqlclosecursor"></a>SQLCloseCursor  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|24000|24000|24000|S1 np 受信 S3 [p]|HY010|HY010|  
  
## <a name="sqlcolattribute"></a>SQLColAttribute  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|HY010|次の表を参照してください。|24000|-[s] S11 [x]|HY010|NS [c] HY010 o|  
  
## <a name="sqlcolattribute-prepared-states"></a>SQLColAttribute (準備された状態)  
  
|S2<br /><br /> 結果はありません。|S3<br /><br /> [結果]|  
|-----------------------|--------------------|  
|--[1] 07005[2]|-[s] S11 x|  
  
 [1] *FieldIdentifier* SQL_DESC_COUNT がします。  
  
 [2] *FieldIdentifier* SQL_DESC_COUNT でした。  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables"></a>SQLColumnPrivileges、SQLColumns、SQLForeignKeys、SQLGetTypeInfo、SQLPrimaryKeys、SQLProcedureColumns、SQLProcedures、SQLSpecialColumns、SQLStatistics、SQLTablePrivileges、および SQLTables  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(組み込み)|S5 [s] S11 [x]|S1 [e] S5 [s] S11 [x]|S1 [e] と [1] S5 [s] および [1] S11 [x] と [1] 24000 [2]|次の表を参照してください。|HY010|NS [c] HY010 o|  
  
 [1] で、現在の結果は、last、または結果だけ、または現在の結果はありません。 複数の結果の詳細については、次を参照してください。[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)です。  
  
 [2] で、現在の結果は、最後の結果ではありません。  
  
## <a name="sqlcolumnprivileges-sqlcolumns-sqlforeignkeys-sqlgettypeinfo-sqlprimarykeys-sqlprocedurecolumns-sqlprocedures-sqlspecialcolumns-sqlstatistics-sqltableprivileges-and-sqltables-cursor-states"></a>SQLColumnPrivileges、SQLColumns、SQLForeignKeys、SQLGetTypeInfo、SQLPrimaryKeys、SQLProcedureColumns、SQLProcedures、SQLSpecialColumns、SQLStatistics、SQLTablePrivileges、および SQLTables (カーソルの状態)  
  
|S5<br /><br /> 開く|S6<br /><br /> SQLFetch または SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|24000[1]|24000|  
  
 [1] このエラーが返されます、ドライバー マネージャーによって**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されなかったと場合、ドライバーによって返される**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されました。  
  
## <a name="sqlcopydesc"></a>SQLCopyDesc  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み [1]|--|--|--|--|HY010|NS [c] と [3] HY010 [o] または [4]|  
|組み込み [2]|HY010|次の表を参照してください。|24000|-[s] S11 x|HY010|NS [c] と [3] HY010 [o] または [4]|  
  
 [1] この行は、移行を示しています。 ときに、 *SourceDescHandle*因数が ARD、APD、または IPD でした。  
  
 [2] この行は、移行を示しています。 ときに、 *SourceDescHandle*引数は、IRD のでした。  
  
 [3]、 *SourceDescHandle*と*TargetDescHandle*の場合と同じ引数が、 **SQLCopyDesc**が非同期的に実行されている関数です。  
  
 [4] するか、 *SourceDescHandle*引数または*TargetDescHandle*引数 (または両方) と異なりますが、 **SQLCopyDesc**が実行されている関数非同期的にします。  
  
## <a name="sqlcopydesc-prepared-states"></a>SQLCopyDesc (準備された状態)  
  
|S2<br /><br /> 結果はありません。|S3<br /><br /> [結果]|  
|-----------------------|--------------------|  
|24000[1]|-[s] S11 [x]|  
  
 [1]この行は、移行を示しています。 ときに、 *SourceDescHandle*引数は、IRD のでした。  
  
## <a name="sqldatasources-and-sqldrivers"></a>SQLDataSources と SQLDrivers  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqldescribecol"></a>SQLDescribeCol  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|HY010|次の表を参照してください。|24000|-[s] S11 [x]|HY010|NS [c] HY010 o|  
  
## <a name="sqldescribecol-prepared-states"></a>SQLDescribeCol (準備された状態)  
  
|S2<br /><br /> 結果はありません。|S3<br /><br /> [結果]|  
|-----------------------|--------------------|  
|07005|-[s] S11 [x]|  
  
## <a name="sqldescribeparam"></a>SQLDescribeParam  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|HY010|-[s] S11 [x]|HY010|HY010|HY010|NS [c] HY010 [o]|  
  
## <a name="sqldisconnect"></a>SQLDisconnect  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|S0 [1]|S0 [1]|S0 [1]|S0 [1]|(HY010)|(HY010)|  
  
 [1] 通話**SQLDisconnect**接続に関連付けられているすべてのステートメントを解放します。 接続状態が返されます C2; にさらに、ステートメントの状態は、S0 前に、接続状態は C4 をする必要があります。  
  
## <a name="sqlendtran"></a>SQLEndTran  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|-[2] [3] S1 または [1]|--S1 [np] [3] と [1] ([2]) S1 [p] と [1] S2 [p] および [2]|--S1 [np] [3] と [1] ([2]) S1 [p] と [1] S3 [p] および [2]|(HY010)|(HY010)|  
  
 [1] が*CompletionType*引数が指定して、 **SQLGetInfo** SQL_CB_DELETE SQL_CURSOR_COMMIT_BEHAVIOR 情報の種類のデータを返しますまたは、 *CompletionType*引数は SQL_ROLLBACK と**SQLGetInfo** SQL_CB_DELETE SQL_CURSOR_ROLLBACK_BEHAVIOR 情報の種類のデータを返します。  
  
 [2]、 *CompletionType*引数が指定して、 **SQLGetInfo** SQL_CB_CLOSE SQL_CURSOR_COMMIT_BEHAVIOR 情報の種類のデータを返しますまたは*CompletionType*引数は SQL_ROLLBACK と**SQLGetInfo** SQL_CB_CLOSE SQL_CURSOR_ROLLBACK_BEHAVIOR 情報の種類のデータを返します。  
  
 [3]、 *CompletionType*引数が指定して、 **SQLGetInfo** SQL_CB_PRESERVE SQL_CURSOR_COMMIT_BEHAVIOR 情報の種類のデータを返しますまたは、 *CompletionType*引数は SQL_ROLLBACK と**SQLGetInfo** SQL_CB_PRESERVE SQL_CURSOR_ROLLBACK_BEHAVIOR 情報の種類のデータを返します。  
  
## <a name="sqlexecdirect"></a>SQLExecDirect  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(組み込み)|S4 [s] と [nr] S5 [s] と [r] [d] S8 S11 [x]|-[e] と [1] S1 [e] S4 [2] [s] および [nr] S5 [s] と [r] [d] S8 S11 [x]|--[e]、[1] と [3] S1 [e]、[2]、および S4 [3] [s] [nr] と [3] S5 [s] [r] S8 [3] [d] と [3] S11 [x] と [3] 24000 [4]|次の表を参照してください。|HY010|NS [c] HY010 [o]|  
  
 [ドライバー マネージャーでは、1]、エラーが返されました。  
  
 [2] のエラーでは、ドライバー マネージャーでは返されませんでした。  
  
 [3] で、現在の結果は、last、または結果だけ、または現在の結果はありません。 複数の結果の詳細については、次を参照してください。[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)です。  
  
 [4] の現在の結果は、最後の結果ではありません。  
  
## <a name="sqlexecdirect-cursor-states"></a>SQLExecDirect (カーソルの状態)  
  
|S5<br /><br /> 開く|S6<br /><br /> SQLFetch または SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|24000 [1]|24000|  
  
 [1] このエラーが返されます、ドライバー マネージャーによって**SQLFetch**または**SQLFetchScroll** 、SQL_NO_DATA が返されなかったと場合、ドライバーによって返される**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されました。  
  
## <a name="sqlexecute"></a>SQLExecute  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(組み込み)|(HY010)|次の表を参照してください。|S2 [e]、p、および [1] S4 [s]、[p] [nr] S5 は [1] [s]、[p] [r] S8 [d] [p] は [1] S11 は [1] [x]、[p]、[1] 24000 [p] と [2] HY010 [np]|カーソルの状態テーブルを参照してください。|HY010|NS [c] HY010 [o]|  
  
 [1] で、現在の結果は、last、または結果だけ、または現在の結果はありません。 複数の結果の詳細については、次を参照してください。[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)です。  
  
 [2] で、現在の結果は、最後の結果ではありません。  
  
## <a name="sqlexecute-prepared-states"></a>SQLExecute (準備された状態)  
  
|S2<br /><br /> 結果はありません。|S3<br /><br /> [結果]|  
|-----------------------|--------------------|  
|S4 [s] [d] S8 S11 [x]|S5 [s] [d] S8 S11 [x]|  
  
## <a name="sqlexecute-cursor-states"></a>SQLExecute (カーソルの状態)  
  
|S5<br /><br /> 開く|S6<br /><br /> SQLFetch または SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000 [p] HY010 [np]|24000 [p]、[1] HY010 [np]|24000 [p] HY010 [np]|  
  
 [1] このエラーが返されます、ドライバー マネージャーによって**SQLFetch**または**SQLFetchScroll** 、SQL_NO_DATA が返されなかったと場合、ドライバーによって返される**SQLFetch**または**SQLFetchScroll** SQL_NO_DATA が返されました。  
  
## <a name="sqlextendedfetch"></a>SQLExtendedFetch  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|S1010|S1010|24000|次の表を参照してください。|S1010|NS [c] S1010 [o]|  
  
## <a name="sqlextendedfetch-cursor-states"></a>SQLExtendedFetch (カーソルの状態)  
  
|S5<br /><br /> 開く|S6<br /><br /> SQLFetch または SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|S7 [s] または [%nf] S11 [x]|S1010|-[s] または [%nf] S11 [x]|  
  
## <a name="sqlfetch-and-sqlfetchscroll"></a>SQLFetch と SQLFetchScroll  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|HY010|HY010|24000|次の表を参照してください。|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlfetch-and-sqlfetchscroll-cursor-states"></a>SQLFetch と SQLFetchScroll (カーソルの状態)  
  
|S5<br /><br /> 開く|S6<br /><br /> SQLFetch または SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|S6 [s] または [%nf] S11 [x]|-[s] または [%nf] S11 [x]|HY010|  
  
## <a name="sqlfreehandle"></a>SQLFreeHandle  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|-- [1]|HY010|HY010|HY010|HY010|HY010|HY010|  
|組み込み [2]|S0|S0|S0|S0|HY010|HY010|  
|-- [3]|--|--|--|--|--|--|  
  
 [1] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_ENV または sql_handle_dbc として。  
  
 [2] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_STMT をがします。  
  
 [3] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_DESC、記述子が明示的に割り当てられます。  
  
## <a name="sqlfreestmt"></a>SQLFreeStmt  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み [1]|--|--|S1 np 受信 S2 [p]|S1 np 受信 S3 [p]|HY010|HY010|  
|組み込み [2]|--|--|--|--|HY010|HY010|  
  
 [1] この行は、移行を示しています。 ときに*オプション*SQL_CLOSE をがします。  
  
 [2] この行は、移行を示しています。 ときに*オプション*SQL_UNBIND または SQL_RESET_PARAMS をがします。 場合、*オプション*引数 SQL_DROP れ、基になるドライバーは ODBC 3*.x*ドライバー、ドライバー マネージャーは、これにマップへの呼び出し**SQLFreeHandle**で*HandleType* SQL_HANDLE_STMT を設定します。 詳細については、移行テーブルを参照してください。 [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)です。  
  
## <a name="sqlgetconnectattr"></a>SQLGetConnectAttr  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetcursorname"></a>SQLGetCursorName  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|--|--|--|--|HY010|HY010|  
  
## <a name="sqlgetdata"></a>SQLGetData  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|HY010|HY010|24000|次の表を参照してください。|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlgetdata-cursor-states"></a>SQLGetData (カーソルの状態)  
  
|S5<br /><br /> 開く|S6<br /><br /> SQLFetch または SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|-[s] または [%nf] [x] 24000 [b] HY109 S11 [i]|-[s] または [%nf] [x] 24000 [b] HY109 S11 [i]|  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec"></a>SQLGetDescField と SQLGetDescRec  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|-[1] または [2] HY010 [3]|次の表を参照してください。|-[1]、または 24000 [2] [3]|-[1]、[2]、または S11 [3] [3] と [x]|HY010|NS [c] または [4] HY010 [o] と [5]|  
  
 [1] が*DescriptorHandle*因数が APD または ARD でした。  
  
 [2]、 *DescriptorHandle*引数は、IPD です。  
  
 [3]、 *DescriptorHandle*引数は、IRD のでした。  
  
 [4]、 *DescriptorHandle*と同じ引数が、 *DescriptorHandle*の引数、 **SQLGetDescField**または**SQLGetDescRec**非同期的に実行されている関数です。  
  
 [5]、 *DescriptorHandle*引数が異なる、 *DescriptorHandle*の引数、 **SQLGetDescField**または**SQLGetDescRec**が非同期的に実行されている関数です。  
  
## <a name="sqlgetdescfield-and-sqlgetdescrec-prepared-states"></a>SQLGetDescField と SQLGetDescRec (準備された状態)  
  
|S2<br /><br /> 結果はありません。|S3<br /><br /> [結果]|  
|-----------------------|--------------------|  
|-[1]、[2]、または S11 [2] [3] と [x]|-[1]、[2]、または [3] S11 [x]|  
  
 [1] が*DescriptorHandle*因数が APD または ARD でした。  
  
 [2]、 *DescriptorHandle*引数は、IPD です。  
  
 [3]、 *DescriptorHandle*引数は、IRD のでした。 これらの関数は、状態 S2 SQL_NO_DATA を常に返すときに*DescriptorHandle* IRD のされました。  
  
## <a name="sqlgetdiagfield-and-sqlgetdiagrec"></a>SQLGetDiagField と SQLGetDiagRec  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--|--|--|  
|組み込み [2]|--[3]|--[3]|--|--|--[3]|--[3]|  
  
 [1] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_ENV、sql_handle_dbc として、または SQL_HANDLE_DESC でした。  
  
 [2] この行は、移行を示しています。 ときに*HandleType* SQL_HANDLE_STMT をがします。  
  
 [3] **SQLGetDiagField**常にこのエラーを返します状態*DiagIdentifier* SQL_DIAG_ROW_COUNT がします。  
  
## <a name="sqlgetenvattr"></a>SQLGetEnvAttr  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetfunctions"></a>SQLGetFunctions  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetinfo"></a>SQLGetInfo  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlgetstmtattr"></a>SQLGetStmtAttr  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|--[1] 24000[2]|--[1] 24000[2]|--[1] 24000[2]|次の表を参照してください。|HY010|HY010|  
  
 [1] で、ステートメント属性でした SQL_ATTR_ROW_NUMBER です。  
  
 [2] のステートメント属性は、SQL_ATTR_ROW_NUMBER をでした。  
  
## <a name="sqlgetstmtattr-cursor-states"></a>SQLGetStmtAttr (カーソルの状態)  
  
|S5<br /><br /> 開く|S6<br /><br /> SQLFetch または SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|--[1] 24000[2]|--または [1] ([v] と [2]) 24000 [b] および [2] HY109 [i] および [2]|--または [i] ([v] と [2]) 24000 [b] および [2] HY109 [1] と [2]|  
  
 [1] が*属性*引数 SQL_ATTR_ROW_NUMBER がありませんでした。  
  
 [2]、*属性*引数が SQL_ATTR_ROW_NUMBER です。  
  
## <a name="sqlmoreresults"></a>SQLMoreResults  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(組み込み)|--[1]|--[1]|--[s] と [2] S1 [%nf]、[np] および [4] S2 [%nf] [p] および [4] S5 [s] と [3] S11 [x]|S1 [%nf] [np] および [4] S3 [%nf] [p] および [4] S4 [s] と [2] S5 [s] と [3] S11 [x]|HY010|NS [c] HY010 [o]|  
  
 [1]、関数は、この状態では SQL_NO_DATA を常に返します。  
  
 [2] で、次の結果は、行の数です。  
  
 [3] で、次の結果は、結果セットです。  
  
 [4] の現在の結果は、最後の結果です。  
  
## <a name="sqlnativesql"></a>SQLNativeSql  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--|--|--|--|--|--|--|  
  
## <a name="sqlnumparams"></a>SQLNumParams  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|HY010|-[s] S11 [x]|-[s] S11 [x]|-[s] S11 [x]|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlnumresultcols"></a>SQLNumResultCols  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|HY010|-[s] S11 [x]|-[s] S11 [x]|-[s] S11 [x]|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlparamdata"></a>SQLParamData  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|HY010|HY010|HY010|HY010|次の表を参照してください。|NS [c] HY010 [o]|  
  
## <a name="sqlparamdata-need-data-states"></a>SQLParamData (必要状態のデータ)  
  
|S8<br /><br /> データが必要|S9<br /><br /> 配置する必要があります。|S10<br /><br /> 配置できます。|  
|----------------------|---------------------|---------------------|  
|S1 [e] と S2 [1] [e] [nr]、および S3 [2] [e] [r] と [2] S5 [e] および [4] S6 [e] と [5] S7 [e] と S9 [3] [d] S11 [x]|HY010|S1 [e] と S2 [1] [e] [nr]、および S3 [2] [e] [r] と [2] S4 [s] [nr] と ([1] または [2]) S5 [s] [r] と ([1] または [2]) S5 ([s] または [e]) し、[4] S6 ([s] または [e]) と [5] S7 ([s] または [e]) と S9 [3] [d] S11 [x]|  
  
 [1] **SQLExecDirect** SQL_NEED_DATA が返されます。  
  
 [2] **SQLExecute** SQL_NEED_DATA が返されます。  
  
 [3] **SQLSetPos**状態 S7 から呼び出されるされ、SQL_NEED_DATA が返されます。  
  
 [4] **SQLBulkOperations**状態 S5 から呼び出されるされ、SQL_NEED_DATA が返されます。  
  
 [5] **SQLSetPos**または**SQLBulkOperations**状態 S6 から呼び出されるされ、SQL_NEED_DATA が返されます。  
  
## <a name="sqlprepare"></a>SQLPrepare  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(組み込み)|S2 [s] と [nr] S3 [s] と [r] S11 [x]|--または [s] ([e] と [1]) S1 [e] と [2] S11 [x]|S1 [e] と [3] S2 [s]、[nr] と [3] S3 [s] [r] と [3] S11 [x] と [3] 24000 [4]|次の表を参照してください。|HY010|NS [c] HY010 [o]|  
  
 [1] で、準備は、ステートメントを検証する以外の理由が失敗した (SQLSTATE が HY009 [無効な引数の値] HY090 または [無効な文字列長またはバッファー長])。  
  
 [2] の準備は、ステートメントの検証中に失敗した (SQLSTATE は HY009 でした。 [無効な引数の値] HY090 または [無効な文字列長またはバッファー長])。  
  
 [3] で、現在の結果は、last、または結果だけ、または現在の結果はありません。 複数の結果の詳細については、次を参照してください。[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)です。  
  
 [4] の現在の結果は、最後の結果ではありません。  
  
## <a name="sqlprepare-cursor-states"></a>SQLPrepare (カーソルの状態)  
  
|S5<br /><br /> 開く|S6<br /><br /> SQLFetch または SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|24000|24000|  
  
## <a name="sqlputdata"></a>SQLPutData  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|HY010|HY010|HY010|HY010|次の表を参照してください。|NS [c] HY010 [o]|  
  
## <a name="sqlputdata-need-data-states"></a>SQLPutData (必要状態のデータ)  
  
|S8<br /><br /> データが必要|S9<br /><br /> 配置する必要があります。|S10<br /><br /> 配置できます。|  
|----------------------|---------------------|---------------------|  
|HY010|S1 [e] と S2 [1] [e] [nr]、および S3 [2] [e] [r] と [2] S5 [e] および [4] S6 [e] と [5] S7 [e] と S10 [3] [s] S11 [x]|--[s] S1 [e] と [1] S2 [e] [nr]、および S3 [2] [e] [r] と [2] S5 [e] および [4] S6 [e] と [5] S7 [e] と S11 [3] [x] HY011 [6]|  
  
 [1] **SQLExecDirect** SQL_NEED_DATA が返されます。  
  
 [2] **SQLExecute** SQL_NEED_DATA が返されます。  
  
 [3] **SQLSetPos**状態 S7 から呼び出されるされ、SQL_NEED_DATA が返されます。  
  
 [4] **SQLBulkOperations**状態 S5 から呼び出されるされ、SQL_NEED_DATA が返されます。  
  
 [5] **SQLSetPos**または**SQLBulkOperations**状態 S6 から呼び出されるされ、SQL_NEED_DATA が返されます。  
  
 [6] 1 つまたは複数の呼び出し**SQLPutData** SQL_SUCCESS、しを呼び出すと、1 つのパラメーターが返されたについて**SQLPutData**が同じパラメーターに行われた*StrLen_or_Ind*設定SQL_NULL_DATA です。  
  
## <a name="sqlrowcount"></a>SQLRowCount  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|(組み込み)|(HY010)|(HY010)|--|--|(HY010)|(HY010)|  
  
## <a name="sqlsetconnectattr"></a>SQLSetConnectAttr  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|--[1]|--|--|--|--[2] 24000[3]|HY010|HY010|  
  
 [1] この行は、移行を示しています。 ときに*属性*接続属性であった。 移行時に*属性*はステートメントだった属性については、ステートメントの遷移表を参照してください**SQLSetStmtAttr**です。  
  
 [2]、*属性*引数 SQL_ATTR_CURRENT_CATALOG がありませんでした。  
  
 [3]、*属性*引数が SQL_ATTR_CURRENT_CATALOG です。  
  
## <a name="sqlsetcursorname"></a>SQLSetCursorName  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|--|--|24000|24000|HY010|HY010|  
  
## <a name="sqlsetdescfield-and-sqlsetdescrec"></a>Sqlsetdescfield によると SQLSetDescRec  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み [1]|--|--|--|--|HY010|HY010|  
  
 [1] この行は、移行を示していますここで、 *DescriptorHandle*引数が ARD、APD、IPD、または (の**SQLSetDescField**)、IRD ときに、 *FieldIdentifier*引数が sql _。DESC_ARRAY_STATUS_PTR または SQL_DESC_ROWS_PROCESSED_PTR します。 呼び出すとエラーは**SQLSetDescField** 、IRD のときに*FieldIdentifier*は、その他の値。  
  
## <a name="sqlsetenvattr"></a>SQLSetEnvAttr  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|HY011|HY011|HY011|HY011|Y011|HY01|HY011|  
  
## <a name="sqlsetpos"></a>SQLSetPos  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|HY010|HY010|24000|次の表を参照してください。|HY010|NS [c] HY010 [o]|  
  
## <a name="sqlsetpos-cursor-states"></a>SQLSetPos (カーソルの状態)  
  
|S5<br /><br /> 開く|S6<br /><br /> SQLFetch または SQLFetchScroll|S7<br /><br /> SQLExtendedFetch|  
|-------------------|---------------------------------------|-----------------------------|  
|24000|-[s] S8 [d] [x] 24000 [b] HY109 S11 [i]|-[s] S8 [d] [x] 24000 [b] HY109 S11 [i]|  
  
## <a name="sqlsetstmtattr"></a>SQLSetStmtAttr  
  
|S0<br /><br /> 未割り当て|S1<br /><br /> 割り当てられています。|S2 – S3<br /><br /> Prepared|S4<br /><br /> 実行|S5 – S7<br /><br /> カーソル|S8 – S10<br /><br /> データが必要|S11 – S12<br /><br /> 非同期|  
|------------------------|----------------------|------------------------|---------------------|----------------------|--------------------------|-----------------------|  
|組み込み|--|-[1] HY011 [2]|--[1] 24000[2]|--[1] 24000[2]|HY010 [np] または [1] HY011 [p] と [2]|HY010 [np] または [1] HY011 [p] と [2]|  
  
 [1] が*属性*SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE、SQL_ATTR_SIMULATE_CURSOR、SQL_ATTR_USE_BOOKMARKS、SQL_ATTR_CURSOR_SCROLLABLE、または SQL_ATTR_CURSOR_SENSITIVITY、引数がありません。  
  
 [2]、*属性*因数が SQL_ATTR_CONCURRENCY、SQL_ATTR_CURSOR_TYPE、SQL_ATTR_SIMULATE_CURSOR、SQL_ATTR_USE_BOOKMARKS、SQL_ATTR_CURSOR_SCROLLABLE、または SQL_ATTR_CURSOR_SENSITIVITY でした。
