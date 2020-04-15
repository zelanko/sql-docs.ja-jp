---
title: 関数の表示 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLMoreResults
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLMoreResults
helpviewer_keywords:
- SQLMoreResults function [ODBC]
ms.assetid: bf169ed5-4d55-412c-b184-12065a726e89
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 78bbb277e4b783eb46c79f59939a1080feae2b60
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304743"
---
# <a name="sqlmoreresults-function"></a>SQLMoreResults 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: ODBC  
  
 **まとめ**  
 **SQLMoreResults**は **、SELECT、UPDATE、****挿入**、または DELETE**UPDATE**ステートメントを含む**DELETE**ステートメントで、さらに結果を使用できるかどうかを判断し、その場合は、それらの結果の処理を初期化します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLMoreResults(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_NO_DATA、SQL_ERROR、SQL_INVALID_HANDLE、またはSQL_PARAM_DATA_AVAILABLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLMoreResults**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLMoreResults**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01S02|オプション値が変更されました|バッチの処理中に変更されたステートメント属性の値。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|40001|シリアル化の失敗|別のトランザクションでリソースがデッドロックしたため、トランザクションがロールバックされました。|  
|40003|ステートメントの完了が不明です|この関数の実行中に関連付けられた接続が失敗し、トランザクションの状態を判別できません。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作がキャンセルされました|*ステートメント ハンドル*に対して非同期処理が有効になりました。 **関数**が呼び出され、実行が完了する前にステートメント*ハンドル*で**SQL キャンセル**または SQL**キャンセル ハンドル**が呼び出されました。 その後、*ステートメント ハンドル*で**SQLMoreResults**関数が再び呼び出されました。<br /><br /> **SQLMoreResults**関数が呼び出され、実行が完了する前に、マルチスレッド アプリケーションの別のスレッドからステートメント ハンドルに対して**SQLCancel**または**SQLCancelHandle**が呼び出されました。 *StatementHandle*|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLMoreResults**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
|IM017|非同期通知モードではポーリングが無効になっています|通知モデルを使用すると、ポーリングは無効になります。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するために呼び出されていません。|ハンドルの前の関数呼び出しがSQL_STILL_EXECUTINGを返し、通知モードが有効な場合、後処理を実行して操作を完了するために、ハンドルで**SQLCompleteAsync**を呼び出す必要があります。|  
  
## <a name="comments"></a>説明  
 **SELECT**ステートメントは結果セットを返します。 **UPDATE**、**挿入**、および**DELETE**ステートメントは、影響を受ける行のカウントを返します。 これらのステートメントのいずれかがバッチ処理され、パラメーターの配列 (パラメーターの配列で番号が増え、バッチに出現する順序で番号が付けられている) またはプロシージャで送信された場合、複数の結果セットまたは行カウントを返すことができます。 ステートメントのバッチとパラメーターの配列については、「 [SQL ステートメントのバッチ](../../../odbc/reference/develop-app/batches-of-sql-statements.md)」および「[パラメーター値の配列](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)」を参照してください。  
  
 バッチを実行すると、アプリケーションは最初の結果セットに配置されます。 アプリケーションは、1 つの結果セットがある場合と同様に、最初または後の結果セットで **、SQLBindCol** **、SQLBulkOperations**、SQLFetch、SQLGetData、SQLFetchScroll、SQLSetPos、およびすべてのメタデータ関数を呼び出すことができます。 **SQLFetch** **SQLGetData** **SQLFetchScroll** **SQLSetPos** 最初の結果セットで実行すると、アプリケーションは**SQLMoreResults**を呼び出して次の結果セットに移動します。 別の結果セットまたはカウントが使用可能な場合 **、SQLMoreResults**はSQL_SUCCESSを返し、追加の処理のために結果セットまたはカウントを初期化します。 結果セット生成ステートメントの間に行数生成ステートメントが出現する場合は、 **SQLMoreResults**を呼び出してステップ オーバーできます。**更新**、**挿入**、または**削除**ステートメントの**SQLMoreResults**を呼び出した後、アプリケーションは**SQLRowCount**を呼び出すことができます。  
  
 フェッチされていない行を持つ現在の結果セットがあった場合 **、SQLMoreResults**はその結果セットを破棄し、次の結果セットまたはカウントを使用可能にします。 すべての結果が処理されている**場合は**、SQL_NO_DATA返します。 一部のドライバーでは、すべての結果セットと行カウントが処理されるまで、出力パラメーターと戻り値は使用できません。 このようなドライバーの場合は、出力パラメーターと戻り値は **、SQLMoreResults**がSQL_NO_DATAを返したときに使用できるようになります。  
  
 前の結果セットに対して確立されたバインディングは、引き続き有効です。 列構造がこの結果セットで異なる場合 **、SQLFetch**または**SQLFetchScroll**を呼び出すと、エラーまたは切り捨てが発生する可能性があります。 これを防ぐために、アプリケーションは**SQLBindCol**を呼び出して、必要に応じて明示的に再バインドする必要があります (または記述子フィールドを設定して再バインドする必要があります)。 または、アプリケーションは、すべての列バッファーをアンバインドする*オプション*をSQL_UNBINDを指定して**SQLFreeStmt**を呼び出すことができます。  
  
 **SQLMoreResults**の呼び出しによってアプリケーションがバッチ内を移動する場合、カーソルの種類、カーソルの同時実行性、キーセット のサイズ、最大長などのステートメント属性の値が変更される場合があります。 この場合 **、SQLMoreResults**はSQL_SUCCESS_WITH_INFOを返し、SQLSTATE 01S02 (オプション値が変更されました) を返します。  
  
 オプションを*SQL_CLOSE*で指定して**SQLCloseCursor**または**SQLFreeStmt**を呼び出すと、バッチの実行の結果として使用できるすべての結果セットと行カウントが破棄されます。 ステートメント・ハンドルは、割り振り状態または準備済み状態のいずれかに戻ります。 バッチが実行され、ステートメント ハンドルが実行、カーソル位置、または非同期状態にある場合に、非同期実行関数をキャンセルする**SQLCancel**を呼び出すと、バッチが生成したすべての結果セットと行数が、キャンセル呼び出しが成功した場合に破棄されます。 その後、ステートメントは準備済みまたは割り当て済みの状態に戻ります。  
  
 ステートメントのバッチまたはプロシージャーが **、他**の SQL ステートメントと SELECT、 **UPDATE**、**挿入**、**および DELETE**ステートメントを混在させる場合、これらの他のステートメントは**SQLMoreResults**に影響を与えないでください。  
  
 詳細については、「[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)」を参照してください。  
  
 ステートメントのバッチ内の検索された更新、挿入、または削除ステートメントがデータ ソースの行に影響しない場合 **、SQLMoreResults**はSQL_SUCCESSを返します。 これは **、SQLExecDirect** **、SQLExecute、** または**SQLParamData**を使用して実行される検索された更新、挿入、または削除ステートメントの場合とは異なり、データ ソースの行に影響がない場合はSQL_NO_DATAを返します。 アプリケーションが**SQLRowCount**を呼び出して **、SQLMoreResults**の呼び出しがどの行にも影響を与えていない場合に、行数を取得すると **、SQLRowCount**はSQL_NO_DATA返します。  
  
 結果処理関数の有効なシーケンスの詳細については、「 付録 B : [ODBC 状態遷移テーブル](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)」を参照してください。  
  
 SQL_PARAM_DATA_AVAILABLEおよびストリーム出力パラメーターの詳細については、「 [SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)」を参照してください。  
  
## <a name="availability-of-row-counts"></a>行数の可用性  
 バッチに複数の連続した行カウント生成ステートメントが含まれている場合、これらの行カウントは 1 つの行カウントにロールアップされる可能性があります。 たとえば、バッチに 5 つの insert ステートメントがある場合、特定のデータ ソースは 5 つの個別の行カウントを返すことができます。 他のデータ ソースでは、5 つの個別の行カウントの合計を表す 1 つの行カウントのみが返されます。  
  
 バッチに結果セット生成ステートメントと行カウント生成ステートメントの組み合わせが含まれている場合、行数がまったく使用できる場合と使用できない場合があります。 行数の可用性に関するドライバーの動作は **、SQLGetInfo**の呼び出しを通じて利用できるSQL_BATCH_ROW_COUNT情報の種類で列挙されます。 たとえば、バッチに**SELECT**が含まれ、その後に 2 つの**INSERT**ともう 1 つの**SELECT**が含まれているとします。 その場合、次のケースが考えられます。  
  
-   2 つの**INSERT**ステートメントに対応する行カウントは、まったく使用できません。 **SQLMoreResults**の最初の呼び出しは、2 番目の**SELECT**ステートメントの結果セットに位置します。  
  
-   2 つの**INSERT**ステートメントに対応する行カウントは個別に使用できます。 **(SQLGetInfo**の呼び出しでは、SQL_BATCH_ROW_COUNT情報の種類のSQL_BRC_ROLLED_UP ビットは返されません。**SQLMoreResults**の最初の呼び出しは、最初の**INSERT**の行カウントに位置し、2 番目の呼び出しでは、2 番目の**INSERT**の行カウントに位置します。 3 回目の**呼**び出しでは、2 番目の**SELECT**ステートメントの結果セットに配置されます。  
  
-   2 つの**INSERT**に対応する行カウントは、使用可能な 1 つの行カウントにロールアップされます。 **(SQLGetInfo**の呼び出しは、SQL_BATCH_ROW_COUNT情報の種類のSQL_BRC_ROLLED_UP ビットを返します。**SQLMoreResults**の最初の呼び出しは、ロールアップされた行カウントに位置し **、SQLMoreResults**への 2 回目の呼び出しは 2 番目の**SELECT**の結果セットに配置されます。  
  
 一部のドライバーは、明示的なバッチでのみ行数を使用できるようにし、ストアド プロシージャには使用できません。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|データブロックのフェッチまたは結果セットのスクロール|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|単一行またはデータブロックを順方向方向にフェッチする|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データ列の一部または全部をフェッチする|[SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [SQLGetData を使用した出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)
