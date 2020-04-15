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
- SQLEndTran
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLEndTran
helpviewer_keywords:
- SQLEndTran function [ODBC]
ms.assetid: ff375ce1-eb50-4693-b1e6-70181a6dbf9f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cce7792e52fce4984f3da41e11d79c34b6b79e53
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302743"
---
# <a name="sqlendtran-function"></a>SQLEndTran 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLEndTran は**、接続に関連付けられたすべてのステートメントに対して、すべてのアクティブ操作に対してコミット操作またはロールバック操作を要求します。 **SQLEndTran**は、環境に関連付けられたすべての接続に対してコミット操作またはロールバック操作を実行することを要求することもできます。  
  
> [!NOTE]  
>  ドライバー マネージャーは、ODBC 3 のときにこの関数をマップする方法の詳細について。*x*アプリケーションは ODBC 2 で動作しています。*x*ドライバについては、「[アプリケーションの下位互換性のための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLEndTran(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle,  
     SQLSMALLINT   CompletionType);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]型識別子を処理します。 SQL_HANDLE_ENV (*ハンドル*が環境ハンドルの場合) またはSQL_HANDLE_DBC *(Handle*が接続ハンドルの場合) を含みます。  
  
 *Handle*  
 [入力]HandleType で示される型の*HandleType*ハンドルで、トランザクションのスコープを示します。 詳細については、「コメント」を参照してください。  
  
 *コンプリートタイプ*  
 [入力]次の 2 つの値のいずれか。  
  
 SQL_COMMIT SQL_ROLLBACK  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、またはSQL_STILL_EXECUTING。  
  
## <a name="diagnostics"></a>診断  
 **SQLEndTran が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときに、関連付けられた SQLSTATE 値を取得するには、適切な*ハンドル型*と*ハンドル*を指定して**SQLGetDiagRec**を呼び出します。 次の表は **、SQLEndTran**によって一般的に返される SQLSTATE 値をリストし、この関数のコンテキストでそれぞれの値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08003|接続が開かない|(DM)*ハンドルタイプ*がSQL_HANDLE_DBCされ、*ハンドル*が接続状態ではありませんでした。|  
|08007|トランザクション中の接続エラー|*HandleType*がSQL_HANDLE_DBCされ、*ハンドル*に関連付けられた接続が関数の実行中に失敗し、要求された**COMMIT**または**ROLLBACK**が失敗の前に発生したかどうかを判断できません。|  
|25S01|トランザクション状態が不明です|*Handle*の 1 つ以上の接続が、指定された結果でトランザクションを完了できませんでした。|  
|25S02|トランザクションはアクティブです|ドライバーは、グローバル トランザクション内のすべての作業がアトミックに完了できることを保証できませんでした。|  
|25S03|トランザクションがロールバックされる|ドライバーは、グローバル トランザクション内のすべての作業がアトミックに完了できることを保証できませんでした。 *Handle*|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40002|整合性制約違反|*完了タイプ*がSQL_COMMITされ、変更のコミットメントが原因で整合性制約違反が発生しました。 その結果、トランザクションはロールバックされました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 *\*バッファー内*の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を説明します。|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|非同期処理が*有効*にされました。 関数が呼び出され、実行が完了する前に[、SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)が*呼*び出されました。 その後、関数は *、接続ハンドル*で再び呼び出されました。<br /><br /> 関数が呼び出され **、SQLCancelHandle**の実行が完了する前に、マルチスレッド アプリケーションの別のスレッドから*ConnectionHandle*で呼び出されました。|  
|HY010|関数シーケンス エラー|(DM) 非同期に実行される関数は *、ConnectionHandle*に関連付けられたステートメント ハンドルに対して呼び出され **、SQLEndTran**が呼び出されたときにまだ実行されていました。<br /><br /> (DM) 非同期実行関数 (この関数ではない) は *、ConnectionHandle*に対して呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**接続***ハンドル***に**関連付けられた**SQLBulkOperations**ステートメント ハンドルに対して呼び**出され**、SQL_NEED_DATA返されました。 この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM) 非同期実行関数 (この関数ではない) は *、HandleType*が SQL_HANDLE_DBC に設定された*ハンドル*に対して呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM) ハンドルに関連*付けられているステートメント*ハンドルの 1 つに対して **、SQL 実行** **、SQLExecDirect**、または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。|  
|HY012|トランザクション操作コードが無効です|(DM) 引数*CompletionType*に指定された値は、SQL_COMMITもSQL_ROLLBACKでもありませんでした。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY092|属性/オプション識別子が無効です|(DM) 引数*HandleType*に指定された値は、SQL_HANDLE_ENVもSQL_HANDLE_DBCでもありませんでした。|  
|HY115|SQLEndTran は、非同期関数実行が有効になっている接続を含む環境では許可されていません。|(DM) 環境内の接続に対して接続関数の非同期実行が有効になっている場合 *、HandleType*をSQL_HANDLE_ENVに設定することはできません。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については、このトピックの「コメント」セクションを参照してください。|  
|ハイク00|オプション機能が実装されていません|ドライバまたはデータ ソースは **、ROLLBACK**操作をサポートしていません。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM) に関連付けられているドライバー、 *ConnectionHandle*関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 ODBC 3 の場合。*x*ドライバー *、HandleType*がSQL_HANDLE_ENVされ、*ハンドル*が有効な環境ハンドルである場合、ドライバー マネージャーは、環境に関連付けられている各ドライバーで**SQLEndTran**を呼び出します。 ドライバーの呼び出しの*引数 Handle*は、ドライバーの環境ハンドルになります。 ODBC 2 の場合。*x*ドライバー *、HandleType*がSQL_HANDLE_ENVされ、*ハンドル*が有効な環境ハンドルであり、その環境で接続状態で複数の接続がある場合、ドライバー マネージャーは、その環境で接続状態の接続ごとに、ドライバーで**SQLTransact**を呼び出します。 各呼び出しの*ハンドル*引数は、接続のハンドルになります。 どちらの場合も、ドライバは、その環境で接続状態にあるすべての接続で *、CompletionType*の値に応じてトランザクションをコミットまたはロールバックしようとします。 アクティブでない接続は、トランザクションに影響を与えない。  
  
> [!NOTE]  
>  **SQLEndTran**を使用して、共有環境でトランザクションをコミットまたはロールバックすることはできません。 *ハンドル*が共有環境のハンドルまたは共用環境上の接続ハンドルに設定された状態で**SQLEndTran**が呼び出された場合、SQLSTATE HY092 (無効な属性/オプション ID) が戻されます。  
  
 ドライバー マネージャーは、接続ごとにSQL_SUCCESSを受け取った場合にのみSQL_SUCCESSを返します。 ドライバー マネージャーは、1 つまたは複数の接続でSQL_ERRORを受信した場合、アプリケーションにSQL_ERRORを返し、診断情報は、環境の診断データ構造に配置されます。 コミット操作またはロールバック操作中に失敗した接続を特定するために、アプリケーションは各接続に対して**SQLGetDiagRec**を呼び出すことができます。  
  
> [!NOTE]  
>  ドライバー マネージャーは、すべての接続でグローバル トランザクションをシミュレートしないため、2 フェーズ コミット プロトコルを使用しません。  
  
 *CompletionType*がSQL_COMMIT場合 **、SQLEndTran**は、影響を受ける接続に関連付けられた任意のステートメントに対して、すべてのアクティブな操作に対してコミット要求を発行します。 *CompletionType*がSQL_ROLLBACKされている場合 **、SQLEndTran**は、影響を受ける接続に関連付けられているすべてのステートメントですべてのアクティブな操作のロールバック要求を発行します。 アクティブなトランザクションがない場合 **、SQLEndTran**は、どのデータ・ソースにも影響を与えないSQL_SUCCESSを戻します。 詳細については、「[トランザクションのコミットとロールバック](../../../odbc/reference/develop-app/committing-and-rolling-back-transactions.md)」を参照してください。  
  
 ドライバーが手動コミット モードの場合 (SQL_ATTR_AUTOCOMMIT属性を SQL_AUTOCOMMIT_OFF に設定して**SQLSetConnectAttr**を呼び出すことによって)、トランザクション内に含まれる SQL ステートメントが現在のデータ ソースに対して実行されると、新しいトランザクションが暗黙的に開始されます。 詳細については、「コミット[モード](../../../odbc/reference/develop-app/commit-mode.md)」を参照してください。  
  
 トランザクション操作がカーソルに与える影響を判断するために、アプリケーションは**sqlGetInfo**をSQL_CURSOR_ROLLBACK_BEHAVIORおよびSQL_CURSOR_COMMIT_BEHAVIORオプションで呼び出します。 詳細については、以下の段落を参照し、「カーソルに[対するトランザクションの影響」および「プリペアドステートメント](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)」を参照してください。  
  
 SQL_CURSOR_ROLLBACK_BEHAVIORまたはSQL_CURSOR_COMMIT_BEHAVIOR値がSQL_CB_DELETEに等しい場合 **、SQLEndTran**は接続に関連付けられたすべてのステートメントで開いているすべてのカーソルをクローズして削除し、保留されているすべての結果を破棄します。 **SQLEndTran は**、割り当てられた (準備されていない) 状態のステートメントを残します。アプリケーションは、後続の SQL 要求に再利用したり、ハンドル*型*のSQL_HANDLE_STMTを使用して**SQLFreeStmt**または**SQLFreeHandle**を呼び出して割り当てを解除したりできます。  
  
 SQL_CURSOR_ROLLBACK_BEHAVIORまたはSQL_CURSOR_COMMIT_BEHAVIOR値がSQL_CB_CLOSEに等しい場合 **、SQLEndTran**は接続に関連付けられているすべてのステートメントで開いているすべてのカーソルを閉じます。 **SQLEndTran は**、存在するステートメントを準備済み状態のままにします。アプリケーションは、最初に**SQLPrepare**を呼び出さずに、接続に関連付けられたステートメントに対して**SQLExecute を**呼び出すことができます。  
  
 SQL_CURSOR_ROLLBACK_BEHAVIORまたはSQL_CURSOR_COMMIT_BEHAVIOR値がSQL_CB_PRESERVEに等しい場合 **、SQLEndTran**は接続に関連付けられたオープン・カーソルに影響を与えません。 カーソルは**SQLEndTran**を呼び出す前に指していた行に残ります。  
  
 トランザクションをサポートするドライバーおよびデータ ソースの場合、トランザクションがアクティブでない場合に SQL_COMMIT または SQL_ROLLBACK を指定して**SQLEndTran**を呼び出すと、SQL_SUCCESS (コミットまたはロールバックする作業がないことを示す) が返され、データ ソースには影響しません。  
  
 ドライバーが自動コミット モードの場合、ドライバー マネージャーは、ドライバーで**SQLEndTran**を呼び出しません。 **SQLEndTran は**、*完了型*が SQL_COMMIT またはSQL_ROLLBACKのどちらで呼び出されたかに関係なく、常にSQL_SUCCESSを返します。  
  
 トランザクションをサポートしないドライバーまたはデータ ソース **(SQL_TXN_CAPABLE***option*がSQL_TC_NONE) は、常に常に自動コミット モードであるため、SQL_COMMITまたはSQL_ROLLBACKの*CompletionType*で呼び出されるかどうかにかかわらず、常に**SQLEndTran**のSQL_SUCCESSを返します。 このようなドライバーとデータ ソースは、要求されたときにトランザクションを実際にはロールバックしません。  
  
## <a name="suspended-state"></a>中断状態  
 Windows 7 より前にリリースされたドライバー マネージャーでは **、SQLEndTran**がドライバーからSQL_ERRORを返した場合、トランザクションがアクティブでした。 ただし、トランザクションがサーバーで正常にコミットされたが、クライアント上のドライバーが通知されなかった可能性があります (たとえば、ネットワーク エラーが発生したため)。 これにより、接続が悪い状態になります。 Windows 7 以降 **、SQLEndTran**がSQL_ERRORを返すときに、接続が中断状態になる可能性があります。 中断状態では、読み取り専用関数を呼び出すことができます。 最終的には、アプリケーションは中断された接続で**SQLDisconnect**を呼び出してリソースを解放する必要があります。  
  
 次の条件がすべて満たされると、接続は中断状態になります。  
  
-   ドライバは**SQLEndTran**からSQL_ERRORを返します。  
  
-   ドライバは ODBC バージョン 3.8 以降です。  
  
-   アプリケーションのバージョンは 3.8 以降です。または、再コンパイルされた ODBC 2.x または 3.x アプリケーションは **、SQLEndTran**関数を**SQLCancelHandle**を使用して正常にキャンセルします。  
  
-   ドライバは、トランザクションが完了しなかったことを確認する次のメッセージを返しませんでした。  
  
    -   25S03: トランザクションがロールバックされました  
  
    -   40001: シリアル化エラー  
  
    -   40002: 整合性制約  
  
    -   HYC00: オプション機能が実装されていません  
  
 環境ハンドルで**SQLEndTran**が呼び出され、その接続の 1 つが上記の条件を満たしている場合、同じドライバーに接続するすべての接続は中断状態になります。  
  
 アプリケーションが中断された接続で**SQLDisconnect**を呼び出した後、接続を使用して別のデータ ソースまたは同じデータ ソースに再接続できます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|接続ハンドルで非同期に実行されている関数をキャンセルします。|[SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|ドライバーまたはデータ ソースに関する情報を返す|[SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|ハンドルを解放する|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|ステートメント ハンドルの解放|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
