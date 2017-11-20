---
title: "SQLMoreResults 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 772bfd3d05d620840ea43c9f1313b4d94add10de
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlmoreresults-function"></a>SQLMoreResults 関数
**準拠**  
 バージョンが導入されています ODBC 1.0 標準への準拠: ODBC。  
  
 **概要**  
 **SQLMoreResults**より多くの結果を含むステートメントで使用できるかどうかを判断**選択**、**更新**、**挿入**、または**削除**ステートメントと、初期化がそれらの結果の処理があれば、します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLMoreResults(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_STILL_EXECUTING、SQL_NO_DATA、SQL_ERROR、SQL_INVALID_HANDLE、または SQL_PARAM_DATA_AVAILABLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLMoreResults** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* SQL の_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLMoreResults**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01S02|オプションの値が変更されました。|バッチとして変更ステートメント属性の値が処理されていた。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックによりロールバックされました。|  
|40003|不明なステートメント入力候補|この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 **SQLMoreResults**関数が呼び出され、実行を完了する前に**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*. 続いて、 **SQLMoreResults**関数がもう一度、 *StatementHandle*です。<br /><br /> **SQLMoreResults**関数が呼び出され、実行を完了する前に**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*マルチ スレッド アプリケーションで別のスレッドからです。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLMoreResults**関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
## <a name="comments"></a>コメント  
 **選択**ステートメントが結果セットを返します。 **更新**、**挿入**、および**削除**ステートメントが影響を受けた行の数を返します。 次のステートメントはバッチ、プロシージャ、または () の番号、バッチに出現する順序で、パラメーターの順序を増やすことで、パラメーターの配列で送信された場合は、複数の結果セットを返すことがまたは行をカウントします。 ステートメントのバッチおよびパラメーターの配列については、次を参照してください。 [SQL ステートメントのバッチ](../../../odbc/reference/develop-app/batches-of-sql-statements.md)と[パラメーター値の配列](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)です。  
  
 バッチを実行すると、アプリケーションは最初の結果セットに位置付けられます。 アプリケーションが呼び出すことができます**SQLBindCol**、 **SQLBulkOperations**、 **SQLFetch**、 **SQLGetData**、 **SQLFetchScroll**、 **SQLSetPos**、および最初またはそれ以降の結果セットを 1 つの結果セットだけがあった場合と同様に、すべてのメタデータ関数。 完了後に、最初の結果セットと、アプリケーションが呼び出す**SQLMoreResults**次の結果セットに移動します。 別の結果セットまたはカウントがある場合、 **SQLMoreResults** SQL_SUCCESS を返し、結果セットまたは追加の処理の数を初期化します。 行カウント: 生成するステートメントが間に表示されない場合は – セットを生成するステートメントの結果をキーを呼び出す場所を空けるステップを実行できる**SQLMoreResults**です。呼び出した後**SQLMoreResults**の**更新**、**挿入**、または**削除**ステートメント、アプリケーションはを呼び出すことができます**SQLRowCount**です。  
  
 現在結果セットには、まだ行があった場合**SQLMoreResults**その結果セットを破棄し、次の結果セットまたは使用可能なカウントは、します。 すべての結果が処理された場合**SQLMoreResults** SQL_NO_DATA が返されます。 一部のドライバーでは、出力パラメーターと戻り値は使用できませんすべての結果セットと行カウントが処理されるまでです。 このようなドライバーの場合は、出力パラメーターと戻り値のときに使用可能になる**SQLMoreResults** SQL_NO_DATA が返されます。  
  
 上記の結果をまだ設定の確立されたバインディングは、有効なままです。 列の構造体がこの結果セットのさまざまな場合は、呼び出すことで、 **SQLFetch**または**SQLFetchScroll**エラーまたは切り捨てが発生する可能性があります。 これを防ぐためには、アプリケーションが呼び出す、 **SQLBindCol**を明示的に適切な再バインド (または記述子フィールドを設定してように) します。 また、アプリケーションが呼び出すことができます**SQLFreeStmt**で、*オプション*SQL_UNBIND 列のすべてのバッファーをバインド解除するのです。  
  
 呼び出しによってバッチから、アプリケーションが移動したときに、カーソルの種類、カーソルの同時実行、キーセットのサイズまたは長さが最大値などのステートメント属性の値を変更する可能性があります**SQLMoreResults**です。 この場合、 **SQLMoreResults** SQL_SUCCESS_WITH_INFO と SQLSTATE 01S02 が返されます (オプションの値が変更されました)。  
  
 呼び出す**SQLCloseCursor**、または**SQLFreeStmt**で、*オプション*SQL_CLOSE のすべての結果セットとの実行の結果として使用可能になった行カウントが破棄バッチです。 ステートメント ハンドルを割り当てまたは準備された状態のいずれかを返します。 呼び出す**SQLCancel**とときに、バッチが実行されたステートメント ハンドルは、実行済みで、カーソル、または非同期状態になるすべての結果セット行をカウントに非同期的に実行中の関数をキャンセルするには[キャンセル] 呼び出しが成功した場合は破棄されているバッチによって生成されます。 次に、ステートメントは、準備済みまたは割り当て済みの状態に戻ります。  
  
 ステートメントまたはプロシージャのバッチとその他の SQL ステートメントと混合かどうか**選択**、**更新**、**挿入**、および**削除**ステートメント、これらの他のステートメントには影響しません**SQLMoreResults**です。  
  
 詳細については、次を参照してください。[複数の結果](../../../odbc/reference/develop-app/multiple-results.md)です。  
  
 ステートメントのバッチがデータ ソースで行に影響を与えない場合は、検索結果を更新、挿入、または delete ステートメントで**SQLMoreResults** SQL_SUCCESS を返します。 これとは異なる検索の更新の場合、挿入、または delete ステートメントで実行される**SQLExecDirect**、 **SQLExecute**、または**SQLParamData**、SQL_NO_DATA が返される場合は、データ ソースのすべての行には影響しません。 アプリケーションを呼び出す場合**SQLRowCount**呼び出しの後に、行の数を取得する**SQLMoreResults** 、どの行が影響を受けません**SQLRowCount** SQL_NO_DATA が返されます。  
  
 結果の処理関数のうち、有効なシーケンス処理に関する詳細については、次を参照してください。[付録 b: ODBC 状態遷移表](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)です。  
  
 SQL_PARAM_DATA_AVAILABLE とストリーム出力パラメーターの詳細については、次を参照してください。 [SQLGetData を使用して出力パラメーターを取得する](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)です。  
  
## <a name="availability-of-row-counts"></a>行の数の可用性  
 バッチに複数の連続する行のカウント – を生成するステートメントが含まれている場合、これらの行カウントが 1 つの行の数に重ねはことができます。 たとえば、バッチがある場合 5 insert ステートメント、特定のデータ ソースが 5 つの個別の行カウントを返すことができます。 その他の特定のデータ ソースは、5 つの個別の行カウントの合計を表す 1 つだけの行の数を返します。  
  
 時に、バッチには、結果セット: 生成して行のカウント – を生成するステートメントの組み合わせが含まれている、行数もできない場合がありますすべてのです。 呼び出すことによって SQL_BATCH_ROW_COUNT 情報の種類に行の数の可用性に対するドライバーの動作が列挙された**SQLGetInfo**です。 たとえば、バッチが含まれている、**選択**、その後に 2 つ**挿入**s と別**選択**です。 次の場合が考えられます。  
  
-   2 つに対応する行をカウント**挿入**ステートメントは使用できませんまったくです。 最初に呼び出す**SQLMoreResults** 、2 つ目の結果セットに位置する**選択**ステートメントです。  
  
-   2 つに対応する行をカウント**挿入**ステートメントは個別に使用できます。 (への呼び出し**SQLGetInfo** SQL_BATCH_ROW_COUNT 情報の種類の SQL_BRC_ROLLED_UP ビットは返しません)。最初の呼び出し**SQLMoreResults**最初の行の数に位置する**挿入**、2 番目の呼び出しの位置で 2 番目の行の数と**挿入**です。 3 番目の呼び出し**SQLMoreResults** 、2 つ目の結果セットに位置する**選択**ステートメントです。  
  
-   2 つに対応する行をカウント**挿入**使用可能な 1 つの単一行の数にロール アップします。 (への呼び出し**SQLGetInfo** SQL_BATCH_ROW_COUNT 情報の種類のビット SQL_BRC_ROLLED_UP が返されます)。最初に呼び出す**SQLMoreResults**重ね行の数と 2 番目の呼び出しに位置する**SQLMoreResults** 、2 つ目の結果セットに位置する**選択**.  
  
 特定のドライバーは、明示的なバッチやストアド プロシージャではなく行カウントを作成します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|データのブロックをフェッチまたは結果をスクロール設定|[SQLFetchScroll 関数](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|  
|1 つの行または順方向専用の方向にデータのブロックをフェッチ|[SQLFetch 関数](../../../odbc/reference/syntax/sqlfetch-function.md)|  
|データの列の一部またはすべてのフェッチ|[SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [SQLGetData を使用して出力パラメーターを取得します。](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)

