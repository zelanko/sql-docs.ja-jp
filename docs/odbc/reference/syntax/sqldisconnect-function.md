---
title: "SQLDisconnect 関数 |Microsoft ドキュメント"
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
- SQLDisconnect
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDisconnect
helpviewer_keywords:
- SQLDisconnect function [ODBC]
ms.assetid: 9e84a58e-db48-4821-a0cd-5c711fcbe36b
caps.latest.revision: 31
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: af65dee0cfa0efcb4b4daffa55e02dfbebff8473
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqldisconnect-function"></a>SQLDisconnect 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLDisconnect**特定の接続ハンドルに関連付けられた接続を閉じます。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLDisconnect(  
     SQLHDBC     ConnectionHandle);  
```  
  
## <a name="arguments"></a>引数  
 *ConnectionHandle*  
 [入力]接続ハンドルです。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、または SQL_STILL_EXECUTING です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLDisconnect** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得される可能性があります**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_DBC と*処理*の*ConnectionHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLDisconnect**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01002|エラーを切断します。|切断中にエラーが発生しました。 ただし、接続解除が成功しました。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08003|接続は開いていません|(DM) 接続は、引数で指定された*ConnectionHandle*が開いていませんでした。|  
|25000|トランザクション状態が無効|引数で指定された接続上のプロセス内のトランザクションにありました*ConnectionHandle*です。 トランザクションは、アクティブなままです。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、 * \*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *ConnectionHandle*です。 関数が呼び出された、およびを実行する前に[SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)で呼び出されましたが、 *ConnectionHandle*です。 関数が再度呼び出されたし、 *ConnectionHandle*です。<br /><br /> 関数が呼び出され、実行前に完了**SQLCancelHandle**で呼び出されましたが、 *ConnectionHandle*マルチ スレッド アプリケーションで別のスレッドからです。|  
|HY010|関数のシーケンス エラー|(DM) の非同期的に実行中の関数が呼び出された、 *StatementHandle*に関連付けられている、 *ConnectionHandle*ときに実行されていると**SQLDisconnect**されましたと呼ばれる。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *ConnectionHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle*に関連付けられている、 *ConnectionHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが、要求に応答して、接続がアクティブなまま前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *ConnectionHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 アプリケーションを呼び出す場合**SQLDisconnect**後**SQLBrowseConnect** SQL_NEED_DATA を返しますと、さまざまなリターン コードを返す前に、ドライバー プロセスを参照する接続を取り消しますを返します。未接続状態への接続。  
  
 アプリケーションを呼び出す場合**SQLDisconnect**接続ハンドルに関連付けられている不完全なトランザクションがあるときに、ドライバーは SQLSTATE 25000 (無効なトランザクションの状態)、トランザクションが変更されていないことを示すを返します接続が開かれています。 不完全なトランザクションはコミットまたはロールバックされたいない**SQLEndTran**です。  
  
 アプリケーションを呼び出す場合**SQLDisconnect**接続に関連付けられているすべてのステートメントが解放されて、前に、ドライバー、データ ソースから正常に接続を切断後にこれらのステートメントと解放されているすべての記述子接続で明示的に割り当てられます。 ただし、1 つ以上の場合、接続に関連付けられたステートメントがまだ実行中、非同期的に**SQLDisconnect** HY010 の SQLSTATE 値は、SQL_ERROR が返されます (関数のシーケンス エラーです)。 また、 **SQLDisconnect**関連付けられているすべてのステートメントとが明示的に割り当てられた接続で接続が中断状態の場合、または場合すべての記述子に空きが**SQLDisconnect**されました正常に取り消しました**SQLCancelHandle**です。  
  
 アプリケーションが使用する方法に関する情報の**SQLDisconnect**を参照してください[データ ソースまたはドライバーからの切断](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md)です。  
  
## <a name="disconnecting-from-a-pooled-connection"></a>プールされた接続からの切断  
 共有環境の接続プールが有効になっているし、アプリケーションを呼び出すかどうか**SQLDisconnect**環境で、接続で接続が接続プールに返されますが使用可能でを使用して他のコンポーネント同じ共有環境です。  
  
## <a name="code-example"></a>コード例  
 参照してください[ODBC プログラムのサンプル](../../../odbc/reference/sample-odbc-program.md)、 [SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)、および[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ハンドルの割り当てください。|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|データ ソースへの接続|[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|接続文字列やダイアログ ボックスを使用してデータ ソースに接続します。|[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|コミットまたはロールバック操作を実行します。|[SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|接続ハンドルを解放します。|[SQLFreeConnect 関数](../../../odbc/reference/syntax/sqlfreeconnect-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
