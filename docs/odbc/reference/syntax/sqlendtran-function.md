---
title: SQLEndTran 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLEndTran
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLEndTran
helpviewer_keywords:
- SQLEndTran function [ODBC]
ms.assetid: ff375ce1-eb50-4693-b1e6-70181a6dbf9f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa1b2afec38116bef3ae90d75607d21c9a92cd80
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53204561"
---
# <a name="sqlendtran-function"></a>SQLEndTran 関数
**準拠**  
 バージョンが導入されました。ODBC 3.0 規格に準拠します。ISO 92  
  
 **まとめ**  
 **SQLEndTran**接続に関連付けられているすべてのステートメントにアクティブなすべての操作をコミットまたはロールバック操作を要求します。 **SQLEndTran**環境に関連付けられているすべての接続のコミットまたはロールバック操作を実行することが要求もできます。  
  
> [!NOTE]  
>  詳細についてはどのようなドライバー マネージャーのときに、ODBC 3 には、この関数にマップします。*x* ODBC 2 を利用するアプリケーション *。x*ドライバーを参照してください[アプリケーションの旧バージョンと互換性のマッピング置換関数](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLEndTran(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle,  
     SQLSMALLINT   CompletionType);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]ハンドル型の識別子。 いずれかの sql_handle_env として含まれています (場合*処理*環境ハンドルは、) または sql_handle_dbc として (場合*処理*接続ハンドルです)。  
  
 *Handle*  
 [入力]示される型のハンドル、 *HandleType*トランザクションのスコープを示します。 詳細については、「コメント」を参照してください。  
  
 *CompletionType*  
 [入力]次の 2 つの値のいずれか:  
  
 指定して SQL_ROLLBACK  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、または SQL_STILL_EXECUTING します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLEndTran** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得される可能性があります**SQLGetDiagRec**と適切な*HandleType*と*処理*します。 次の表に、一般的にによって返される SQLSTATE 値**SQLEndTran** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08003|接続は開いていません|(DM)、 *HandleType*が sql_handle_dbc として、および*処理*接続状態ではありませんでした。|  
|08007|トランザクション中に、接続エラー|*HandleType*を sql_handle_dbc として、接続に関連付けられている、*処理*、関数の実行に失敗したし、することはできないかどうかを確認、要求された**コミット**または**ロールバック**障害発生前に発生します。|  
|25S01|トランザクションの状態が不明です。|1 つまたは複数の接続の*処理*を指定すると、結果を持つトランザクションを完了できませんでしたし、結果は不明です。|  
|25S02|トランザクションがアクティブなままです。|ドライバーは、グローバル トランザクションのすべての処理が自動的に完了して、トランザクションがアクティブなままのことを保証するためにできませんでした。|  
|25S03|トランザクションをロールバックします。|ドライバーは、グローバル トランザクションのすべての処理が自動的に完了してすべてのアクティブなトランザクションの処理のことを保証するためにできませんでした*処理*はロールバックされました。|  
|40001|シリアル化エラー|トランザクションが別のトランザクションでリソース デッドロックによりロールバックされました。|  
|40002|整合性制約違反|*CompletionType*した状態で、変更のコミットには、整合性制約違反が発生しました。 その結果、トランザクション ロールバックされました。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*szMessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効に、 *ConnectionHandle*します。 関数が呼び出された、および実行する前に完了[SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)が呼び出されて、 *ConnectionHandle*します。 後でもう一度関数が呼び出された、 *ConnectionHandle*します。<br /><br /> 関数が呼び出された、および実行する前に完了**SQLCancelHandle**が呼び出されて、 *ConnectionHandle*マルチ スレッド アプリケーションで別のスレッドから。|  
|HY010|関数のシーケンス エラー|(DM) を非同期的に実行中の関数が呼び出されたステートメント ハンドルに関連付けられている、 *ConnectionHandle*ときに実行されていると**SQLEndTran**が呼び出されました。<br /><br /> (DM) を非同期的に実行中の関数 (いないこの"1") が呼び出された、 *ConnectionHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**ステートメント ハンドルに関連付けられているために呼び出されますが、*ConnectionHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) を非同期的に実行中の関数 (いないこの"1") が呼び出された、*処理*で*HandleType* sql_handle_dbc として設定し、この関数が呼び出されたときに実行されています。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に関連付けられているステートメント ハンドルのいずれかが呼び出された*処理*と返された SQL_PARAM_DATA_AVAILABLE します。 ストリームのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY012|無効なトランザクション操作コード|引数に指定された値 (DM) *CompletionType*した状態でも SQL_ROLLBACK でした。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY092|無効な属性またはオプション識別子|引数に指定された値 (DM) *HandleType* sql_handle_env としても sql_handle_dbc としてでした。|  
|HY115|非同期関数の実行が有効になっていると、接続が存在する環境に SQLEndTran が許可されていません|(DM) *HandleType*環境での接続の接続の機能の非同期実行が有効になっている場合、sql_handle_env としてに設定することはできません。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、このトピックのコメント セクションを参照してください。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースはサポートしていません、**ロールバック**操作。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *ConnectionHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングは無効です。|通知のモデルを使用すると、常にポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了が呼び出されていません。|通知モードが有効になっている場合、ハンドルでは、前の関数呼び出しに SQL_STILL_EXECUTING が返された場合と**SQLCompleteAsync**後処理を行い、操作を完了するハンドルで呼び出す必要があります。|  
  
## <a name="comments"></a>コメント  
 ODBC 3 の場合。*x*ドライバー場合*HandleType* sql_handle_env としてと*処理*ドライバー マネージャーを呼び出すが、有効な環境ハンドルが**SQLEndTran**環境に関連付けられている各ドライバーでします。 *処理*ドライバーへの呼び出しの引数が、ドライバーの環境ハンドルになります。 ODBC 2 の場合。*x*ドライバー場合*HandleType* sql_handle_env としてと*処理*、有効な環境ハンドルであり、その環境での接続状態で複数の接続があります。ドライバー マネージャーが呼び出す**SQLTransact**ドライバー、その環境での接続状態の接続ごとに 1 回です。 *処理*各呼び出しで引数が、接続のハンドルになります。 どちらの場合、ドライバーはしようとするとコミットするかの値に応じて、トランザクションはロールバック*CompletionType*、その環境に接続されている状態にあるすべての接続。 非アクティブな接続では、トランザクションは影響しません。  
  
> [!NOTE]  
>  **SQLEndTran**コミットするか、共有環境でトランザクションをロールバックするのには使用できません。 SQLSTATE HY092 場合 (無効な属性またはオプション識別子) が返される**SQLEndTran**を使用して呼び出した*処理*共有環境のいずれかのハンドルまたは共有上の接続のハンドルに設定環境。  
  
 接続ごとに関係なく SQL_SUCCESS を受信した場合にのみ、ドライバー マネージャーは関係なく SQL_SUCCESS を返します。 ドライバー マネージャーは、1 つまたは複数の接続で SQL_ERROR を受信する場合は、アプリケーションに SQL_ERROR を返し、診断情報は、環境の診断データの構造に配置されます。 アプリケーションを呼び出して、コミットまたはロールバック操作中にどの接続または接続の失敗を判断する**SQLGetDiagRec**接続ごとにします。  
  
> [!NOTE]  
>  ドライバー マネージャーは、すべての接続はグローバル トランザクションをシミュレートせず、2 フェーズ コミット プロトコルを使用しません。  
  
 場合*CompletionType*は指定して、 **SQLEndTran**影響を受ける接続に関連付けられた任意のステートメントですべてのアクティブな操作をコミット要求を発行します。 場合*CompletionType*は SQL_ROLLBACK、 **SQLEndTran**影響を受ける接続に関連付けられた任意のステートメントですべてのアクティブな操作のロールバック要求を発行します。 アクティブな場合は、トランザクションがない場合**SQLEndTran**で任意のデータ ソースに影響しない SQL_SUCCESS を返します。 詳細については、次を参照してください。 [Committing とトランザクションのロールバック](../../../odbc/reference/develop-app/committing-and-rolling-back-transactions.md)します。  
  
 ドライバーが手動コミット モードの場合 (呼び出して**SQLSetConnectAttr** SQL_ATTR_AUTOCOMMIT を SQL_AUTOCOMMIT_OFF にセットを属性) と内で格納できる SQL ステートメント、に暗黙的に、新しいトランザクションが開始します。トランザクションは、現在のデータ ソースに対して実行されます。 詳細については、次を参照してください。[コミット モード](../../../odbc/reference/develop-app/commit-mode.md)します。  
  
 カーソルのトランザクション操作の影響を確認するアプリケーションを呼び出す**SQLGetInfo** SQL_CURSOR_ROLLBACK_BEHAVIOR および SQL_CURSOR_COMMIT_BEHAVIOR のオプションを使用します。 詳細については、次の段落を参照してくださいし、も参照してください[カーソルと準備されたステートメントでトランザクションの効果](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)します。  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR または SQL_CURSOR_COMMIT_BEHAVIOR 値に等しい SQL_CB_DELETE 場合、 **SQLEndTran**閉じますと、接続に関連付けられたすべてのステートメントにすべての開いているカーソルを削除し、保留中のすべての結果を破棄します。 **SQLEndTran** (準備されていない) 割り当て済みの状態で存在する任意のステートメントを離れるアプリケーションは、後続の SQL 要求の再利用できるか、呼び出すことができます**SQLFreeStmt**または**SQLFreeHandle**で*HandleType*の sql_handle_stmt としてその割り当てを解除します。  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR または SQL_CURSOR_COMMIT_BEHAVIOR 値に等しい SQL_CB_CLOSE 場合、 **SQLEndTran**接続に関連付けられたすべてのステートメントにすべての開いているカーソルを閉じます。 **SQLEndTran**準備された状態で存在する任意のステートメントのまま、アプリケーションが呼び出すことができます**SQLExecute** 、接続先に呼び出さずに関連付けられているステートメントの**SQLPrepare**します。  
  
 SQL_CURSOR_ROLLBACK_BEHAVIOR または SQL_CURSOR_COMMIT_BEHAVIOR 値に等しい SQL_CB_PRESERVE 場合、 **SQLEndTran**接続に関連付けられた開いているカーソルには影響しません。 呼び出す前に、示される行にカーソルをまま**SQLEndTran**します。  
  
 呼び出し、トランザクションをサポートするドライバーとデータのソースで**SQLEndTran**した状態または SQL_ROLLBACK のいずれかでアクティブなトランザクションがないときに SQL_SUCCESS を返します (コミットまたはロールバックする作業がないことを示す)あり、データ ソースへの影響はありません。  
  
 ドライバーは、自動コミット モードでは、ドライバー マネージャーは呼び出されません**SQLEndTran**ドライバー。 **SQLEndTran**常に使用して呼び出したかどうかに関係なく SQL_SUCCESS を返します、 *CompletionType*した状態または SQL_ROLLBACK の。  
  
 トランザクションをサポートしていないドライバーまたはデータ ソース (**SQLGetInfo** *オプション*SQL_TXN_CAPABLE は SQL_TC_NONE)、常に効果的に自動コミット モードにし、したがって常に関係なく SQL_SUCCESS を返します**SQLEndTran**で呼び出されるかどうかを*CompletionType*した状態または SQL_ROLLBACK の。 このようなドライバーとデータ ソース実際にはロールバックしないするよう要求されたときに、トランザクション。  
  
## <a name="suspended-state"></a>中断状態  
 Windows 7 より前にリリースされたドライバー マネージャーでは、トランザクションがアクティブな場合は**SQLEndTran**ドライバーから SQL_ERROR が返されます。 ただし、トランザクションは、サーバーで、正常にコミットされたいたも、(たとえば、ネットワーク エラーが発生しました) ため、クライアント上のドライバーが通知いませんでした。 異常な状態にこれ接続のままになります。 Windows 7 以降、ときに**SQLEndTran**中断状態で返します SQL_ERROR、接続があります。 中断状態の場合を読み取り専用の関数を呼び出すことです。 最終的には、アプリケーションを呼び出す必要があります**SQLDisconnect**リソースを解放する中断されている接続でします。  
  
 次の条件がすべて当てはまる場合、接続が中断状態に格納されます。  
  
-   ドライバーはから SQL_ERROR を返します**SQLEndTran**します。  
  
-   ドライバーは、ODBC 3.8、またはそれ以降のバージョンです。  
  
-   アプリケーションのバージョンは 3.8 以降です。再コンパイルされた ODBC 2.x または 3.x アプリケーションが正常にキャンセルするか、 **SQLEndTran**を通過して機能**SQLCancelHandle**します。  
  
-   ドライバーでは、次のメッセージは、トランザクションが完了しなかったことを確認の 1 つ返されませんでした。  
  
    -   25S03:トランザクションをロールバックします。  
  
    -   40001:シリアル化エラー  
  
    -   40002:整合性制約  
  
    -   HYC00:省略可能な機能が実装されていません  
  
 場合**SQLEndTran**が呼び出された環境でハンドルとその接続のいずれかで、上記の条件が満たさ、同じドライバーに接続するすべての接続は中断状態に格納されます。  
  
 アプリケーションから**SQLDisconnect**接続の中断された、接続を別のデータ ソースまたは同じデータ ソースへの再接続を使用できます。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|接続ハンドルで非同期的に実行されている関数を取り消しています。|[SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|ドライバーまたはデータ ソースに関する情報を返す|[SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|ハンドルの解放|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|ステートメント ハンドルの解放|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
