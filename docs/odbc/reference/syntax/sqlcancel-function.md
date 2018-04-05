---
title: SQLCancel 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLCancel
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCancel
helpviewer_keywords:
- SQLCancel function [ODBC]
ms.assetid: ac0b5972-627f-4440-8c5a-0e8da728726d
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e7adc83a958667e963749e390518bfc792c7cd85
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlcancel-function"></a>SQLCancel 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLCancel**ステートメントで処理をキャンセルします。  
  
 接続やステートメントの処理を取り消す場合に、次のように使用します。 [SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLCancel(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLCancel** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLCancel**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)引数で *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLCancel**関数が呼び出されました。<br /><br /> (DM) に関連付けられている接続ハンドル上で進行中は、非同期操作が失敗しました。 操作を取り消す*StatementHandle*です。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY018|キャンセル要求を拒否されました。 サーバー|サーバーには、キャンセル要求が拒否されました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 **SQLCancel**次の種類のステートメントで処理を取り消すことができます。  
  
-   ステートメントで非同期的に実行されている関数です。  
  
-   データを必要があるステートメントの関数。  
  
-   別のスレッドでステートメントで実行されている関数です。  
  
 ODBC 2 です。*x*アプリケーションを呼び出す場合は、 **SQLCancel** 、ステートメントの処理が行われない場合に**SQLCancel**と同じ効果を持つ**SQLFreeStmt** SQL_CLOSE オプションと共にこの動作は、完全を期すのためだけに定義し、アプリケーションを呼び出す必要があります**SQLFreeStmt**または**SQLCloseCursor**カーソルを閉じます。  
  
 ときに**SQLCancel**ニーズ データ、取り消されること、関数によって投稿された診断レコードがオフになっているステートメントのステートメントまたは関数に非同期的に実行して関数を取り消すために呼び出されると**SQLCancel** 、独自の診断レコードの送信以外の場合**SQLCancel**取り消すには、別のスレッドのステートメントで実行されている関数、ただし、これはクリアされません診断が呼び出された関数とがないキャンセル中のレコード独自の診断レコードを投稿します。  
  
## <a name="canceling-asynchronous-processing"></a>非同期処理を取り消す  
 アプリケーションでは、非同期的に関数を呼び出して、処理が完了するかどうかを判断するには、繰り返し関数を呼び出します。 関数がまだ処理して、SQL_STILL_EXECUTING が返されます。 場合は、関数には、処理が完了したら、別のコードを返します。  
  
 すべての呼び出しを SQL_STILL_EXECUTING を返す関数には、アプリケーションを呼び出すことが**SQLCancel**関数をキャンセルします。 取り消し要求が成功した場合、ドライバーは SQL_SUCCESS を返します。 このメッセージを示しません関数が実際に取り消されたことです。これは、キャンセル要求が処理されたことを示します。 ときに、または関数が実際に取り消されたかどうかは、ドライバーに依存し、データ ソースに依存します。 リターン コードが SQL_STILL_EXECUTING されるまで、元の関数を呼び出すアプリケーションを続行する必要があります。 関数が正常に取り消された場合、戻り値のコードは SQL_ERROR と SQLSTATE HY008 (操作が取り消されました)。 関数では、通常の処理が完了した、リターン コードが SQL_SUCCESS や関数が成功した場合、SQL_SUCCESS_WITH_INFO または SQL_ERROR HY008 以外 SQLSTATE (操作が取り消されました) 場合は、関数が失敗しました。  
  
> [!NOTE]  
>  ODBC 3.5 への呼び出しで**SQLCancel**と処理が行われないステートメントでとして扱われません**SQLFreeStmt** SQL_CLOSE オプションが持つは何も起こりませんまったくです。 カーソルが閉じ、アプリケーションを呼び出す必要があります**SQLCloseCursor**ではなく、 **SQLCancel**です。  
  
 非同期処理の詳細については、次を参照してください。[非同期実行](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)です。  
  
## <a name="canceling-functions-that-need-data"></a>データを必要とする関数のキャンセル  
 後に**SQLExecute**または**SQLExecDirect** SQL_NEED_DATA を返しますのすべての実行時データ パラメーターは、データが送信されて、前に、アプリケーションが呼び出すことができます、 **SQLCancel**ステートメントの実行をキャンセルします。 ステートメントが取り消されると、アプリケーションを呼び出すことが**SQLExecute**または**SQLExecDirect**もう一度です。 詳細については、次を参照してください。 [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)です。  
  
 後に**SQLBulkOperations**または**SQLSetPos** SQL_NEED_DATA を返しますのすべての実行時データ列のデータが送信された前に、アプリケーションが呼び出すことができます、 **SQLCancel**操作をキャンセルします。 操作が取り消されると、アプリケーションを呼び出すことが**SQLBulkOperations**または**SQLSetPos**再度を取り消すには影響しません、カーソルの状態または現在のカーソル位置。 詳細については、次を参照してください。 [SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)または[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)です。  
  
## <a name="canceling-functions-executing-on-another-thread"></a>別のスレッドで実行されている関数のキャンセル  
 マルチ スレッド アプリケーションで、アプリケーションは、別のスレッドで実行されている関数を取り消すことができます。 関数では、アプリケーションの呼び出しをキャンセルする**SQLCancel**では、対象の関数が別のスレッドで使用されるものと同じ、ステートメント ハンドルを使用します。 関数が取り消される方法は、ドライバーと、オペレーティング システムによって異なります。 リターン コードを非同期的に実行されている関数の取り消しと同様に、 **SQLCancel**のみのドライバーが正常に要求を処理するかどうかを示します。 SQL_SUCCESS や SQL_ERROR のみが返されることができます。診断情報は返されません。 元の関数が取り消されると場合、SQL_ERROR と SQLSTATE HY008 を返します (操作が取り消されました)。  
  
 SQL ステートメントの中の場合実行すると実行**SQLCancel**ステートメントの実行をキャンセルする別のスレッドで呼び出されると、可能であれば、実行を完了、キャンセル中に戻り値に関係なく SQL_SUCCESS も成功します。 この場合、ドライバー マネージャーでは、ので、アプリケーションは、カーソルを使用できません、キャンセル、ステートメントの実行によって開かれたカーソルが閉じられた前提としています。  
  
 スレッド処理の詳細については、次を参照してください。[マルチ スレッド](../../../odbc/reference/develop-app/multithreading.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|パラメーターへのバッファーのバインド|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|実行の一括挿入または更新操作|[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|関数を実行して非同期的に、接続ハンドルのさらの機能にキャンセル**SQLCancel**です。|[SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|ステートメント ハンドルを解放します。|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|診断レコードのフィールドまたは診断のヘッダーのフィールドを取得します。|[SQLGetDiagField 関数](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
|診断データの構造体の複数のフィールドを取得します。|[SQLGetDiagRec 関数](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|  
|データを送信する次のパラメーターを返す|[SQLParamData 関数](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|実行時にパラメーターのデータを送信します。|[SQLPutData 関数](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|カーソルを行セットや、行セット内のデータを更新する、更新、または結果セット内のデータを削除します。|[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
