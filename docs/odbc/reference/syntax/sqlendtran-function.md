---
title: "SQLEndTran 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLEndTran
apilocation: sqlsrv32.dll
apitype: dllExport
f1_keywords: SQLEndTran
helpviewer_keywords: SQLEndTran function [ODBC]
ms.assetid: ff375ce1-eb50-4693-b1e6-70181a6dbf9f
caps.latest.revision: "29"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 15ba9ff7d28101201842071929b34dfa7ec1d455
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlendtran-function"></a>SQLEndTran 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLEndTran**接続に関連付けられているすべてのステートメントにアクティブなすべての操作をコミットまたはロールバック操作を要求します。 **SQLEndTran**環境に関連付けられているすべての接続のコミットまたはロールバック操作を実行することが要求もできます。  
  
> [!NOTE]  
>  どのようなドライバー マネージャーの詳細と ODBC 3 には、この関数にマップします。*x* ODBC 2 を利用するアプリケーション*。x*ドライバーを参照してください[アプリケーションの旧バージョンと互換性を保つのための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLEndTran(  
     SQLSMALLINT   HandleType,  
     SQLHANDLE     Handle,  
     SQLSMALLINT   CompletionType);  
```  
  
## <a name="arguments"></a>引数  
 *HandleType*  
 [入力]ハンドル型の識別子。 いずれかの sql_handle_env として含まれています (場合*処理*環境ハンドルは、) または sql_handle_dbc として (場合*処理*接続ハンドル)。  
  
 *Handle*  
 [入力]によって示される型のハンドル、 *HandleType*トランザクションのスコープを示すです。 詳細については、「コメント」を参照してください。  
  
 *CompletionType*  
 [入力]次の 2 つの値のいずれか。  
  
 指定して SQL_ROLLBACK  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、または SQL_STILL_EXECUTING です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLEndTran** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得される可能性があります**SQLGetDiagRec**と適切な*HandleType*と*処理*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLEndTran**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08003|接続は開いていません|(DM)、 *HandleType*が sql_handle_dbc として、および*処理*接続状態ではありませんでした。|  
|08007|トランザクションの実行中の接続エラー|*HandleType*を sql_handle_dbc として、接続に関連付けられている、*処理*、関数の実行中に失敗し、そのことはできないかどうかを確認要求された**コミット**または**ロールバック**障害発生前に発生します。|  
|25S01|トランザクション状態が不明です。|1 つ以上では、接続の*処理*を指定すると、結果を持つトランザクションを完了できませんでしたし、結果は不明です。|  
|25S02|トランザクションがアクティブなままです。|ドライバーはアトミックに、グローバル トランザクション内のすべての作業を完了できませんできますされ、トランザクションがアクティブであることを保証できませんでした。|  
|25S03|トランザクションはロールバックします。|ドライバーをできなかったことを保証原子的に、グローバル トランザクション内のすべての作業を完了できませんでした アクティブなトランザクションですべての作業*処理*はロールバックされました。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックによりロールバックされました。|  
|40002|整合性制約の違反|*CompletionType*を指定して、変更のコミットには、整合性制約違反が発生しました。 その結果、トランザクションがロールバックされます。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*szMessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *ConnectionHandle*です。 関数が呼び出され、実行前に完了[SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)で呼び出されましたが、 *ConnectionHandle*です。 関数が再度呼び出されたし、 *ConnectionHandle*です。<br /><br /> 関数が呼び出され、実行前に完了**SQLCancelHandle**で呼び出されましたが、 *ConnectionHandle*マルチ スレッド アプリケーションで別のスレッドからです。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたステートメント ハンドルに関連付けられているため、 *ConnectionHandle*ときに実行されていると**SQLEndTran**が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *ConnectionHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**ステートメント ハンドルに関連付けられているために呼び出されますが、*ConnectionHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、*処理*で*HandleType* sql_handle_dbc としてに設定され、この関数が呼び出されたときに実行されています。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に関連付けられているステートメント ハンドルのいずれかが呼び出された*処理*と返される SQL_PARAM_DATA_AVAILABLE です。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY012|無効なトランザクション操作コード|(DM) 引数の値が指定された*CompletionType*指定しても SQL_ROLLBACK されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY092|無効な属性またはオプション識別子|(DM) 引数の値が指定された*HandleType* sql_handle_env としても sql_handle_dbc としてされました。|  
|HY115|非同期関数の実行が有効になっていると、接続が含まれている環境の SQLEndTran は許可されません。|(DM) *HandleType*環境での接続の接続の機能の非同期実行が有効になっている場合、SQL_HANDLE_ENV に設定することはできません。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、このトピックのコメント セクションを参照してください。|  
|HYC00|省略可能な機能が実装されていません|ドライバーまたはデータ ソースがサポートしない、**ロールバック**操作します。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *ConnectionHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 ODBC 3 の場合。*x*ドライバー場合*HandleType* sql_handle_env としてと*処理*ドライバー マネージャーを呼び出すが、有効な環境ハンドルが**SQLEndTran**環境に関連付けられている各ドライバーでします。 *処理*ドライバーへの呼び出しの引数は、ドライバーの環境ハンドルになります。 ODBC 2 の場合。*x*ドライバー場合*HandleType* sql_handle_env としてと*処理*、有効な環境ハンドルは、その環境内で接続状態で複数の接続があります。ドライバー マネージャーが呼び出して**SQLTransact**環境で、接続状態の接続ごとに 1 回、ドライバーでします。 *処理*の各呼び出しの引数は、接続ハンドルになります。 どちらの場合に、ドライバーがコミットまたはロールバックの値に応じて、トランザクションを試みます*CompletionType*、その環境で接続されている状態にあるすべての接続でします。 非アクティブな接続では、トランザクションは影響しません。  
  
> [!NOTE]  
>  **SQLEndTran**コミットするか、共有環境でトランザクションをロールバックするのには使用できません。 SQLSTATE HY092 場合 (無効な属性またはオプション識別子) が返されます**SQLEndTran**で呼び出された*処理*共有環境のいずれかのハンドルまたは共有上の接続のハンドルに設定環境。  
  
 接続ごとに関係なく SQL_SUCCESS を受信した場合にのみ、ドライバー マネージャーは関係なく SQL_SUCCESS を返します。 ドライバー マネージャーは、1 つまたは複数の接続で SQL_ERROR を受信する場合は、アプリケーションに SQL_ERROR を返し、診断情報は、環境の診断データの構造に配置されます。 コミットまたはロールバック操作中にどの接続または接続が失敗したためには、アプリケーションが呼び出すことができます**SQLGetDiagRec**接続ごとにします。  
  
> [!NOTE]  
>  ドライバー マネージャーは、すべての接続をグローバル トランザクションはシミュレートせず、2 フェーズ コミット プロトコルを使用できません。  
  
 場合*CompletionType*は指定して、 **SQLEndTran**影響を受ける接続に関連付けられた任意のステートメントですべてのアクティブな操作のコミット要求を発行します。 場合*CompletionType*は SQL_ROLLBACK、 **SQLEndTran**影響を受ける接続に関連付けられた任意のステートメントですべてのアクティブな操作のロールバック要求を発行します。 アクティブな場合は、トランザクションがない場合**SQLEndTran**のどのデータ ソースに影響しないと関係なく SQL_SUCCESS を返します。 詳細については、次を参照してください。 [Committing とトランザクションのロールバック](../../../odbc/reference/develop-app/committing-and-rolling-back-transactions.md)です。  
  
 ドライバーが手動コミット モードの場合 (を呼び出して**SQLSetConnectAttr** SQL_ATTR_AUTOCOMMIT を SQL_AUTOCOMMIT_OFF にセットを属性)、SQL ステートメント内で格納できる場合に、新しいトランザクションが開始暗黙的には、トランザクションは、現在のデータ ソースに対して実行されます。 詳細については、次を参照してください。[コミット モード](../../../odbc/reference/develop-app/commit-mode.md)です。  
  
 カーソルのトランザクション操作の影響を確認するのにアプリケーションを呼び出す**SQLGetInfo** SQL_CURSOR_ROLLBACK_BEHAVIOR と SQL_CURSOR_COMMIT_BEHAVIOR オプションを使用します。 詳細については、次の段落を参照してください。 とも参照してください[カーソルおよび準備されたステートメントでトランザクションの効果](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)です。  
  
 場合は、SQL_CURSOR_ROLLBACK_BEHAVIOR または SQL_CURSOR_COMMIT_BEHAVIOR 値に等しい SQL_CB_DELETE、 **SQLEndTran**を閉じ、接続に関連付けられているすべてのステートメントですべての開いているカーソルの削除、保留中のすべての結果を破棄します。 **SQLEndTran**割り当て済みの (準備解除) 状態である任意のステートメントのまま、アプリケーションが SQL の後続の要求の再利用できる、または呼び出すことができます**SQLFreeStmt**または**SQLFreeHandle***HandleType* sql_handle_stmt としてそれらの割り当てを解除するのです。  
  
 場合は、SQL_CURSOR_ROLLBACK_BEHAVIOR または SQL_CURSOR_COMMIT_BEHAVIOR 値に等しい SQL_CB_CLOSE、 **SQLEndTran**接続に関連付けられているすべてのステートメントにすべての開いているカーソルを閉じます。 **SQLEndTran**準備された状態にある任意のステートメントのまま、アプリケーションを呼び出すことができます**SQLExecute**最初呼び出さずに、接続に関連付けられているステートメントの**SQLPrepare**.  
  
 場合は、SQL_CURSOR_ROLLBACK_BEHAVIOR または SQL_CURSOR_COMMIT_BEHAVIOR 値に等しい SQL_CB_PRESERVE、 **SQLEndTran**接続に関連付けられた開いているカーソルには影響しません。 呼び出す前に、示される行にカーソルをまま**SQLEndTran**です。  
  
 呼び出し、トランザクションをサポートするドライバーとデータ ソースの**SQLEndTran**で指定して、または SQL_ROLLBACK アクティブなトランザクションがないとき SQL_SUCCESS を返します (コミットまたはロールバックする作業がないことを示す)データ ソースへの影響を与えません。  
  
 ドライバーは、自動コミット モードでは、ときに、ドライバー マネージャーを呼び出しません**SQLEndTran**ドライバーにします。 **SQLEndTran**で呼び出されたかどうかに関係なく常に関係なく SQL_SUCCESS を返します、 *CompletionType*指定してまたは SQL_ROLLBACK のです。  
  
 トランザクションをサポートしていないドライバーまたはデータ ソース (**SQLGetInfo** *オプション*SQL_TXN_CAPABLE は SQL_TC_NONE) 常に効果的に自動コミット モードでは、したがって常に関係なく SQL_SUCCESS を返します**SQLEndTran**で呼び出されるかどうか、 *CompletionType*指定してまたは SQL_ROLLBACK のです。 このようなドライバーとデータ ソースと実際にはロールバックしないするように要求されたときに、トランザクションです。  
  
## <a name="suspended-state"></a>中断状態  
 Windows 7 以前にリリースされたドライバー マネージャーでは、トランザクションがアクティブな場合は**SQLEndTran**ドライバーから SQL_ERROR が返されます。 ただし、そのトランザクションは、サーバーで、正常にコミットされていたが、(たとえば、ネットワーク エラーが発生しました) ため、クライアント上のドライバーが通知いませんでした。 これは状態のままに、接続が正しくありません。 以降、Windows 7 でとき**SQLEndTran** SQL_ERROR、接続を返しますが、中断状態になる可能性があります。 中断状態は、読み取り専用の関数を呼び出します。 アプリケーションが最終的には、呼び出す必要があります**SQLDisconnect**リソースを解放する中断されている接続でします。  
  
 次の条件がすべて当てはまる場合、接続が中断状態に配置されます。  
  
-   ドライバーはから SQL_ERROR を返します**SQLEndTran**です。  
  
-   ドライバーは、ODBC 3.8、またはそれ以降のバージョンです。  
  
-   アプリケーションのバージョンは、3.8 以降です。または、再コンパイルされた ODBC 2.x アプリケーションまたは 3.x アプリケーションが正常にキャンセル、 **SQLEndTran**を通して機能**SQLCancelHandle**です。  
  
-   ドライバーでは、次のメッセージは、トランザクションが完了しなかったことを確認の 1 つ返されませんでした。  
  
    -   25S03: トランザクションがロールバック  
  
    -   40001: シリアル化のエラー  
  
    -   40002: 整合性制約  
  
    -   HYC00: 省略可能な機能が実装されていません  
  
 場合**SQLEndTran**が呼び出された環境ハンドルと接続のいずれかを満たすを上記の条件、同じドライバーに接続するすべての接続が中断状態に配置されます。  
  
 アプリケーションが呼び出す後**SQLDisconnect**中断されている接続では接続を使用して別のデータ ソースや、同じデータ ソースへの再接続をします。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|接続ハンドルで非同期的に実行されている関数は取り消されます。|[SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|ドライバーまたはデータ ソースに関する情報を返す|[SQLGetInfo 関数](../../../odbc/reference/syntax/sqlgetinfo-function.md)|  
|ハンドルを解放します。|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|ステートメント ハンドルを解放します。|[SQLFreeStmt 関数](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [非同期実行 (ポーリング メソッド)](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)
