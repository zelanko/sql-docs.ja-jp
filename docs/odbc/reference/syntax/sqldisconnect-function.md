---
title: SQLDisconnect 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 61e32c11aafeaf693188a96b48ddd60728ba5bc4
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53203951"
---
# <a name="sqldisconnect-function"></a>SQLDisconnect 関数
**準拠**  
 バージョンが導入されました。ODBC 1.0 規格に準拠します。ISO 92  
  
 **まとめ**  
 **SQLDisconnect**特定の接続ハンドルに関連付けられた接続を閉じます。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLDisconnect(  
     SQLHDBC     ConnectionHandle);  
```  
  
## <a name="arguments"></a>引数  
 *ConnectionHandle*  
 [入力]接続ハンドルです。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_INVALID_HANDLE、または SQL_STILL_EXECUTING します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLDisconnect** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得される可能性があります**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_DBC と*処理*の*ConnectionHandle*します。 次の表に、一般的にによって返される SQLSTATE 値**SQLDisconnect** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01002|切断エラー|切断中にエラーが発生しました。 ただし、切断に成功しました。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08003|接続は開いていません|(DM)、接続は、引数で指定された*ConnectionHandle*開かれていませんでした。|  
|25000|トランザクション状態が無効|引数で指定された接続上のプロセスでのトランザクションが*ConnectionHandle*します。 トランザクションはアクティブなままにします。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効に、 *ConnectionHandle*します。 関数が呼び出されるを実行する前に、 [SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)が呼び出されて、 *ConnectionHandle*します。 後でもう一度関数が呼び出された、 *ConnectionHandle*します。<br /><br /> 関数が呼び出された、および実行する前に完了**SQLCancelHandle**が呼び出されて、 *ConnectionHandle*マルチ スレッド アプリケーションで別のスレッドから。|  
|HY010|関数のシーケンス エラー|(DM) を非同期的に実行中の関数が呼び出された、 *StatementHandle*に関連付けられている、 *ConnectionHandle*ときに実行されていると**SQLDisconnect**されましたと呼ばれる。<br /><br /> (DM) を非同期的に実行中の関数 (いないこの"1") が呼び出された、 *ConnectionHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**に対して呼び出された、 *StatementHandle*に関連付けられている、 *ConnectionHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、[SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|HYT01|接続がタイムアウトしました|データ ソースが、要求に応答し、接続がまだアクティブにする前に、接続タイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *ConnectionHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングは無効です。|通知のモデルを使用すると、常にポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了が呼び出されていません。|通知モードが有効になっている場合、ハンドルでは、前の関数呼び出しに SQL_STILL_EXECUTING が返された場合と**SQLCompleteAsync**後処理を行い、操作を完了するハンドルで呼び出す必要があります。|  
  
## <a name="comments"></a>コメント  
 アプリケーションを呼び出す場合**SQLDisconnect**後**SQLBrowseConnect** SQL_NEED_DATA を返しますにさまざまなリターン コードを返す前に、ドライバーがプロセスを参照する接続を取り消しますされ返されます接続されていない状態に接続します。  
  
 アプリケーションを呼び出す場合**SQLDisconnect**接続ハンドルに関連付けられた、未完了のトランザクションは、ドライバーは SQLSTATE 25000 (無効なトランザクションの状態)、トランザクションが変更されていないことを示すを返しますされ、接続が開きます。 未完了のトランザクションがコミットまたはロールバックされたしないもの**SQLEndTran**します。  
  
 アプリケーションを呼び出す場合**SQLDisconnect**ことが、接続に関連付けられたすべてのステートメントを解放して、前に、ドライバー、データ ソースから正常に切断した後にこれらのステートメントと解放されているすべての記述子接続で明示的に割り当てられます。 ただし、1 つ以上の場合、接続に関連付けられたステートメントがまだ実行中、非同期的に**SQLDisconnect** HY010 の SQLSTATE 値 SQL_ERROR を返します (関数のシーケンス エラーです)。 また、 **SQLDisconnect**は関連付けられているすべてのステートメントと明示的に割り当てられた、接続で接続が中断状態の場合、または場合すべての記述子を解放**SQLDisconnect**されました正常に取り消しました**SQLCancelHandle**します。  
  
 アプリケーションでの使用方法については**SQLDisconnect**を参照してください[データ ソースまたはドライバーからの切断](../../../odbc/reference/develop-app/disconnecting-from-a-data-source-or-driver.md)します。  
  
## <a name="disconnecting-from-a-pooled-connection"></a>プールされた接続から切断しています  
 共有環境の接続プールが有効になっているし、アプリケーションを呼び出すかどうか**SQLDisconnect**その環境で、接続で、接続が接続プールに返されを使用して他のコンポーネントを引き続き使用できます同じ共有環境です。  
  
## <a name="code-example"></a>コード例  
 参照してください[サンプル ODBC プログラム](../../../odbc/reference/sample-odbc-program.md)、 [SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)、および[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ハンドルの割り当てください。|[SQLAllocHandle 関数](../../../odbc/reference/syntax/sqlallochandle-function.md)|  
|データ ソースへの接続|[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|接続文字列またはダイアログ ボックスを使用してデータ ソースへの接続|[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
|コミットまたはロールバック操作を実行します。|[SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)|  
|接続ハンドルの解放|[SQLFreeConnect 関数](../../../odbc/reference/syntax/sqlfreeconnect-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
