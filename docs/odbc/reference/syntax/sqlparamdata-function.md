---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLParamData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLParamData
helpviewer_keywords:
- SQLParamData function [ODBC]
ms.assetid: 68fe010d-9539-4e5b-a260-c8d32423b1db
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 8ed149e125e3231d670c6ddbd4569ff5ccee5c15
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306923"
---
# <a name="sqlparamdata-function"></a>SQLParamData 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLParamData**は、ステートメント実行時にパラメーター データを提供するために**SQLPutData**と共に使用され、ストリーミング出力パラメーター データを取得するために**SQLGetData**と共に使用されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLParamData(  
     SQLHSTMT       StatementHandle,  
     SQLPOINTER *   ValuePtrPtr);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *値を設定します。*  
 [出力]**sqlBindParameter** (パラメーター データの場合) で指定された*パラメーター値Ptr*バッファーのアドレスを返すバッファーへのポインターまたは**SQLBindCol**で指定された*ターゲット値Ptr*バッファーのアドレス (列データ) SQL_DESC_DATA_PTR記述子レコード フィールドに含まれている。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NEED_DATA、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、SQL_INVALID_HANDLE、またはSQL_PARAM_DATA_AVAILABLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLParamData**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLParamData**によって返される SQLSTATE 値を一覧し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07006|制限付きデータ型属性違反|バインドされたパラメーターの**SQLBindParameter**の*値型*引数で識別されるデータ値を **、SQLBindParameter**の*引数 ParameterType*で識別されるデータ型に変換できませんでした。<br /><br /> SQL_PARAM_INPUT_OUTPUTまたはSQL_PARAM_OUTPUTとしてバインドされたパラメーターに対して返されたデータ値は **、SQLBindParameter**の引数*ValueType*で識別されるデータ型に変換できませんでした。<br /><br /> (1 つ以上の行のデータ値を変換できなかったが、1 つ以上の行が正常に返された場合、この関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|22026|文字列データの長さが合致しません|**SQLGetInfo**のSQL_NEED_LONG_DATA_LEN情報型は "Y" で **、SQLBindParameter**で*StrLen_or_IndPtr*引数を指定した場合よりも長いパラメーター (データ型がSQL_LONGVARCHAR、SQL_LONGVARBINARY、または長いデータ ソース固有のデータ型) に対して送信されるデータが少なかった場合。<br /><br /> **SQLGetInfo**のSQL_NEED_LONG_DATA_LEN情報の種類は "Y" で **、SQLBulkOperations で**追加または更新されたデータ行の列に対応する長さバッファーに指定された長さバッファーに指定された長さバッファーに指定された長い列 (データ型がSQL_LONGVARCHAR、SQL_LONGVARBINARY、または長いデータ ソース固有のデータ型) に送信されるデータが少**なかった場合があります**。|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 関数が呼び出され、実行が完了する前にステートメント*ハンドル*に対して**SQLCancel**または**SQLCancelHandle**が呼び出されました。その後、関数は ステートメント*ハンドル*で再度呼び出されました。<br /><br /> 関数が呼び出され、実行が完了する前に **、SQLCancel**または**SQLCancelHandle**がマルチスレッド アプリケーションの別のスレッドから*ステートメント ハンドル*で呼び出されました。|  
|HY010|関数シーケンス エラー|(DM) 以前の関数呼び出しは、戻りコードがSQL_NEED_DATAされた SQLExecDirect、SQLExecute、SQLBulkOperations、または**SQLSetPos**への呼び出しではなかったか、以前の関数呼び出しが**SQLExecDirect** **SQLPutData**を呼び出した場合でした。 **SQLExecute** **SQLBulkOperations**<br /><br /> 前の関数呼び出しは **、SQLParamData**への呼び出しでした。<br /><br /> (DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLParamData**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> **ステートメント***ハンドル*に対**して**呼**SQLBulkOperations**び**出され**、SQL_NEED_DATA返されました。 **SQLCancel**は、すべての実行時データ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に対応するドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
 SQL ステートメント内のパラメーターのデータを送信中に**SQLParamData**が呼び出された場合は、ステートメントを実行するために呼び出される関数によって返される SQLSTATE を返すことができます (**SQLExecute**または**SQLExecDirect**) 。 更新または追加される列のデータを送信中に呼び出された場合、または**SQLSetPos**で更新されている列のデータを呼び出す場合は **、SQLBulkOperations**または**SQLSetPos**によって返される可能性のある SQLSTATE を返すことができます。 **SQLSetPos**  
  
## <a name="comments"></a>説明  
 **SQLParamData**を呼び出して **、2**つの用途に対して実行時データを提供**できます。** **SQLExecDirect** **SQLBulkOperations** 実行時に **、SQLParamData は**、ドライバーが必要とするデータのインジケーターをアプリケーションに返します。  
  
 アプリケーションが呼び出すと **、SQL実行****、SQLExecDirect** **、SQLBulkOperations**、または**SQLSetPos、** ドライバーは実行時のデータが必要な場合はSQL_NEED_DATAを返します。 アプリケーションは、送信するデータを決定する**SQLParamData**を呼び出します。 ドライバーは、パラメーターデータを必要とする場合、ドライバーは*\*、ValuePtrPtr*出力バッファーにアプリケーションが行セット バッファーに入れた値を返します。 アプリケーションは、この値を使用して、ドライバーが要求しているパラメーター データを決定できます。 ドライバーは、列のデータを必要とする場合、ドライバーは*\*、ValuePtrPtr*バッファーに列が最初にバインドされたアドレスを返します。  
  
 *バインド アドレス* + *バインド オフセット*+ (*行番号*- 1) x*要素サイズ*)  
  
 ここで、変数は次の表に示すように定義されます。  
  
|変数|説明|  
|--------------|-----------------|  
|*バインド アドレス*|**引数**で指定されたアドレス*TargetValuePtr*です。|  
|*バインド オフセット*|SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性で指定されたアドレスに格納される値。|  
|*Row Number*|行セット内の行の 1 から数を返します。 単一行フェッチ (デフォルト) の場合、これは 1 です。|  
|*要素サイズ*|データバッファーと長さ/インジケーター・バッファーの両方に対するSQL_ATTR_ROW_BIND_TYPEステートメント属性の値。|  
  
 また、SQL_NEED_DATA返すのもアプリケーションに示す指標であり、データを送信するために**SQLPutData**を呼び出す必要があります。  
  
 アプリケーションは、列またはパラメーターの実行時データを送信するために必要な回数**だけ SQLPutData**を呼び出します。 列またはパラメーターのすべてのデータが送信された後、アプリケーションは**SQLParamData**を再度呼び出します。 **SQLParamData が**再びSQL_NEED_DATAを返す場合は、別のパラメーターまたは列に対してデータを送信する必要があります。 したがって、アプリケーションは再び**SQLPutData**を呼び出します。 すべてのパラメータまたは列に対して実行データデータがすべて送信されている場合 **、SQLParamData**はSQL_SUCCESSまたはSQL_SUCCESS_WITH_INFOを返し*\*、ValuePtrPtr*の値は未定義であり、SQL ステートメントを実行するか **、SQLBulkOperations**または**SQLSetPos**呼び出しを処理できます。  
  
 検索された更新ステートメントまたは削除ステートメントに対して、データ ソースの行に影響を与えないパラメーター データが**SQLParamData**から提供される場合 **、SQLParamData**の呼び出しはSQL_NO_DATAを返します。  
  
 ステートメント実行時に実行時データパラメーター・データを渡す方法の詳細については、 [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)の「パラメーター値の引き渡し」および[「長いデータの送信](../../../odbc/reference/develop-app/sending-long-data.md)」を参照してください。 実行時のデータ列データの更新または追加方法の詳細については[、SQLSetPos の「SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)の使用[」、SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)の「ブックマークを使用した一括更新の実行」、および[長いデータと SQLSetPos および SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)を参照してください。  
  
 **ストリーミング**出力パラメータを取得するために呼び出すことができます。 **SQLMoreResults** **、SQLExecute** **、SQLGetData、** または**SQLExecDirect**がSQL_PARAM_DATA_AVAILABLEを返す場合は **、SQLParamData**を呼び出して、どのパラメーターに使用可能な値があるかを判断します。 SQL_PARAM_DATA_AVAILABLEおよびストリーム出力パラメーターの詳細については、「 [SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)」を参照してください。  
  
## <a name="code-example"></a>コード例  
 [「SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|バッファーをパラメーターにバインドする|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|ステートメント内のパラメーターに関する情報を返す|[SQLDescribeParam 関数](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|SQL ステートメントの実行|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|実行時にパラメータデータを送信する|[SQLPutData 関数](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
