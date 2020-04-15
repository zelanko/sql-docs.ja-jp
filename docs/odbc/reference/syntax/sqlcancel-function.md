---
title: 関数のキャンセル |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fcc2afce495a1481692ba1f20162a2df5d9a9458
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301312"
---
# <a name="sqlcancel-function"></a>SQLCancel 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLCancel ステートメント**の処理をキャンセルします。  
  
 接続またはステートメントの処理を取り消すには、 [SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)を使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLCancel(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLCancel**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、関連付けられた SQLSTATE 値を取得するには、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*を*指定*して**SQLGetDiagRec**を呼び出します。 次の表は **、SQLCancel**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 *引数\*MessageText*バッファー内の[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)によって返されるエラー メッセージは、エラーとその原因を記述します。|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLCancel**関数が呼び出されたときに実行されていました。<br /><br /> *(DM) ステートメント ハンドル*に関連付けられている接続ハンドルで非同期操作が進行中であるため、操作をキャンセルできませんでした。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY018|サーバーはキャンセル要求を拒否しました|サーバーはキャンセル要求を拒否しました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 **SQLCancel は**、ステートメントに対して以下のタイプの処理を取り消すことができます。  
  
-   ステートメントで非同期に実行される関数。  
  
-   データを必要とするステートメントの関数。  
  
-   別のスレッド上のステートメントで実行されている関数。  
  
 ODBC 2 で。*x*、 ステートメントで処理が行われていないときにアプリケーションが**SQLCancel**を呼び出すと **、SQLCancel**は**sqlFreeStmt**と同じSQL_CLOSEオプションを使用して実行されます。この動作は完全性のために定義され、アプリケーションはカーソルをクローズするために**SQLFreeStmt**または**SQLCloseCursor**を呼び出す必要があります。  
  
 **SQLCancel**が呼び出されて、ステートメント内で非同期に実行されている関数、またはデータを必要とするステートメント上の関数をキャンセルすると、取り消された関数によってポストされた診断レコードがクリアされ **、SQLCancel**は自身の診断レコードをポストします。しかし、別のスレッド上のステートメントで実行されている関数を取り消すために**SQLCancel**が呼び出された場合、取り消された関数の診断レコードはクリアされず、それ自体の診断レコードはポストされません。  
  
## <a name="canceling-asynchronous-processing"></a>非同期処理のキャンセル  
 アプリケーションは、関数を非同期に呼び出した後、繰り返し関数を呼び出して、処理が終了したかどうかを判断します。 関数がまだ処理中の場合は、SQL_STILL_EXECUTING返します。 関数の処理が終了した場合は、別のコードを返します。  
  
 SQL_STILL_EXECUTINGを返す関数を呼び出した後、アプリケーションは**SQLCancel**を呼び出して関数をキャンセルできます。 キャンセル要求が成功した場合、ドライバーはSQL_SUCCESSを返します。 このメッセージは、関数が実際に取り消されたことを示すものではありません。キャンセル要求が処理されたことを示します。 関数が実際に取り消された場合、またはキャンセルされた場合は、ドライバーに依存し、データ ソースに依存します。 戻りコードがSQL_STILL_EXECUTINGされないまで、アプリケーションは元の関数を呼び出し続ける必要があります。 関数が正常に取り消された場合、戻りコードはSQL_ERRORされ、SQLSTATE HY008 (操作は取り消されました) になります。 関数が通常の処理を完了した場合、戻りコードは、関数が成功したか、またはSQL_ERRORした場合はSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOされ、関数が失敗した場合は HY008 以外の SQLSTATE (操作は取り消されました) になります。  
  
> [!NOTE]  
>  ODBC 3.5 では、ステートメントで処理が行われていない場合の**SQLCancel の**呼び出しは、sqlFreeStmt として扱われ、SQL_CLOSEオプションは使用されませんが、何の効果もありません。 **SQLFreeStmt** カーソルを閉じるには、アプリケーションは SQL**キャンセル**ではなく**SQLCloseCursor**を呼び出す必要があります。  
  
 非同期処理の詳細については、「[非同期実行](../../../odbc/reference/develop-app/asynchronous-execution-polling-method.md)」を参照してください。  
  
## <a name="canceling-functions-that-need-data"></a>データを必要とする関数のキャンセル  
 **SQLExecute**または**SQLExecDirect**がSQL_NEED_DATAを返した後、実行時にデータのすべてのパラメーターに対してデータが送信される前に、アプリケーションは**SQLCancel**を呼び出してステートメントの実行をキャンセルできます。 ステートメントが取り消された後、アプリケーションは再び**SQLExecute**または**SQLExecDirect を**呼び出すことができます。 詳細については[、「SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)」を参照してください。  
  
 **SQLBulkOperations**または**SQLSetPos**がSQL_NEED_DATAを返した後、実行データ列のすべてのデータが送信される前に、アプリケーションは**SQLCancel**を呼び出して操作をキャンセルできます。 操作が取り消された後、アプリケーションは再び**SQLBulk オペレーション**または**SQLSetPos**を呼び出すことができます。キャンセルしても、カーソル状態や現在のカーソル位置には影響しません。 詳細については、「 [SQL 一括処理](../../../odbc/reference/syntax/sqlbulkoperations-function.md)または[SQL セットポス](../../../odbc/reference/syntax/sqlsetpos-function.md)」を参照してください。  
  
## <a name="canceling-functions-executing-on-another-thread"></a>別のスレッドで実行されている関数のキャンセル  
 マルチスレッド アプリケーションでは、アプリケーションは、別のスレッドで実行されている関数を取り消すことができます。 この関数を取り消すために、アプリケーションは、ターゲット関数で使用されるステートメント ハンドルと同じステートメント ハンドルを使用して**SQLCancel**を呼び出しますが、別のスレッドで呼び出します。 機能の取り消し方法は、ドライバとオペレーティング システムによって異なります。 非同期に実行されている関数をキャンセルする場合と同様に **、SQLCancel**の戻りコードは、ドライバーが要求を正常に処理したかどうかのみを示します。 SQL_SUCCESSまたはSQL_ERRORのみを返すことができます。診断情報は返されません。 元の関数が取り消されると、SQL_ERRORと SQLSTATE HY008 (操作は取り消されました) が返されます。  
  
 ステートメントの実行をキャンセルするために別のスレッドで**SQLCancel**が呼び出されたときに SQL ステートメントが実行されている場合、その実行が成功し、SQL_SUCCESSが返される可能性があります。 この場合、ドライバー マネージャーは、ステートメントの実行によって開かれたカーソルがキャンセルによって閉じられていることを前提とするため、アプリケーションはカーソルを使用できません。  
  
 スレッド処理の詳細については、「[マルチスレッド](../../../odbc/reference/develop-app/multithreading.md)」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|バッファーをパラメーターにバインドする|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|一括挿入または更新操作の実行|[SQLBulkOperations 関数](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|  
|**SQLCancel**の機能に加えて、接続ハンドルで非同期に実行されている関数をキャンセルします。|[SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|  
|SQL ステートメントの実行|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|ステートメント ハンドルの解放|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|  
|診断レコードのフィールドまたは診断ヘッダーのフィールドの取得|[SQLGetDiagField 関数](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|  
|診断データ構造の複数のフィールドの取得|[SQLGetDiagRec 関数](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|  
|データを送信する次のパラメータを返す|[SQLParamData 関数](../../../odbc/reference/syntax/sqlparamdata-function.md)|  
|実行時にパラメータデータを送信する|[SQLPutData 関数](../../../odbc/reference/syntax/sqlputdata-function.md)|  
|行セット内にカーソルを配置する、行セット内のデータを更新する、または結果セット内のデータを更新または削除する|[SQLSetPos 関数](../../../odbc/reference/syntax/sqlsetpos-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
