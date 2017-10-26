---
title: "SQLParamData 関数 |Microsoft ドキュメント"
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
- SQLParamData
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLParamData
helpviewer_keywords:
- SQLParamData function [ODBC]
ms.assetid: 68fe010d-9539-4e5b-a260-c8d32423b1db
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 019b15aa5a4bd27bd96261d016fbaaebe0fc366c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlparamdata-function"></a>SQLParamData 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLParamData**と共に使用する**SQLPutData**を使用して、ステートメント実行時にパラメーター データを指定する**SQLGetData**ストリーミングされる出力パラメーターのデータを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLParamData(  
     SQLHSTMT       StatementHandle,  
     SQLPOINTER *   ValuePtrPtr);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *ValuePtrPtr*  
 [出力]アドレスを取得するためのバッファーへのポインター、 *ParameterValuePtr*で指定されたバッファー **SQLBindParameter** (のパラメーターのデータ) のアドレス、または、 *TargetValuePtr*で指定されたバッファー **SQLBindCol** (列、データの) SQL_DESC_DATA_PTR 記述子レコード フィールドに含まれているとします。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NEED_DATA、SQL_NO_DATA、SQL_STILL_EXECUTING、SQL_ERROR、SQL_INVALID_HANDLE、または SQL_PARAM_DATA_AVAILABLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLParamData** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLParamData**です。 この関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07006|制限付きのデータ型の属性違反|識別されるデータ値、 *ValueType*引数**SQLBindParameter**で識別されるデータ型にバインドされたパラメーターを変換できませんでしたの*ParameterType*引数**SQLBindParameter**です。<br /><br /> SQL_PARAM_INPUT_OUTPUT または SQL_PARAM_OUTPUT で識別されるデータ型に変換できませんとしてバインドされたパラメーターのデータ値が返されます、 *ValueType*引数**SQLBindParameter**です。<br /><br /> (1 つまたは複数の行のデータ値を変換できませんでした、1 つまたは複数の行が正常に返される場合は、この関数 sql_success_with_info が返されます。)|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|22026|文字列データの長さが合致しません|SQL_NEED_LONG_DATA_LEN 情報の種類で**SQLGetInfo** "Y"、指定された数より長いパラメーターの (データ型は、SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長い形式のデータ ソース固有のデータ型をいました) の低いデータが送信されました*StrLen_or_IndPtr*引数**SQLBindParameter**です。<br /><br /> SQL_NEED_LONG_DATA_LEN 情報の種類で**SQLGetInfo** "Y"で指定されたよりも長い列 (データ型は、SQL_LONGVARCHAR、SQL_LONGVARBINARY、または長い形式のデータ ソース固有のデータ型をいました) の低いデータが送信された、追加または更新されたデータの行の列に対応する長バッファー **SQLBulkOperations**またはで更新された**SQLSetPos**です。|  
|40001|シリアル化のエラー|トランザクションが別のトランザクションでリソース デッドロックが原因ロールバックされました。|  
|40003|不明なステートメント入力候補|、この関数の実行中に、関連付けられた接続が失敗し、トランザクションの状態を判断することはできません。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、 * \*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY008|操作が取り消されました|非同期処理が有効で、 *StatementHandle*です。 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*; で、関数が再度呼び出さし、*StatementHandle*です。<br /><br /> 関数が呼び出され、前に、実行を完了**SQLCancel**または**SQLCancelHandle**で呼び出されましたが、 *StatementHandle*の別のスレッドから、マルチ スレッド アプリケーションです。|  
|HY010|関数のシーケンス エラー|(DM) 前の関数呼び出しがへの呼び出し**SQLExecDirect**、 **SQLExecute**、 **SQLBulkOperations**、または**SQLSetPos**ここで、コードは SQL_NEED_DATA、または前の関数呼び出しがへの呼び出しを返す**SQLPutData**です。<br /><br /> 前の関数呼び出しがへの呼び出し**SQLParamData**です。<br /><br /> (DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLParamData**関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数 (いないこの 1 つ) が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle*SQL_NEED_DATA が返される。 **SQLCancel**がすべての実行時データ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に対応するドライバー、 *StatementHandle*関数をサポートしていません。|  
|IM017|非同期通知モードでのポーリングが無効になっています|通知のモデルを使用するとは、ポーリングは無効です。|  
|IM018|**SQLCompleteAsync**このハンドルに対する前の非同期操作を完了するが呼び出されていません。|ハンドルに対する前の関数呼び出しに SQL_STILL_EXECUTING が返された場合、および通知モードが有効になっている**SQLCompleteAsync**ハンドルの後処理を行い、操作を完了するに呼び出せる必要があります。|  
  
 場合**SQLParamData**が呼び出された SQL ステートメントにパラメーターのデータを送信中に、ステートメントを実行すると呼ばれる、関数によって返される任意の SQLSTATE を返すこと (**SQLExecute**または**SQLExecDirect**)。 列のデータを送信中に呼び出されると更新または追加された**SQLBulkOperations**で更新されているまたは**SQLSetPos**、によって返される任意の SQLSTATE を返すことができます**SQLBulkOperations**または**SQLSetPos**です。  
  
## <a name="comments"></a>コメント  
 **SQLParamData** 2 つの用途の実行時データのデータを指定するに呼び出せる: パラメーターのデータへの呼び出しで使用される**SQLExecute**または**SQLExecDirect**、または使用される列のデータ行が更新またはへの呼び出しによって追加されたときに**SQLBulkOperations**への呼び出しによって更新または**SQLSetPos**です。 実行時に、 **SQLParamData**のどのデータを示すインジケーターが必要になるアプリケーションに返します。  
  
 アプリケーションを呼び出すと**SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**ドライバーは SQL_NEED_ を返します実行時データのデータが必要がある場合は、データ。 その後、アプリケーションを呼び出す**SQLParamData**を送信するデータを決定します。 ドライバーは、パラメーターのデータを必要とする場合、ドライバーを返します、 * \*ValuePtrPtr*出力バッファーの行セットのバッファーでアプリケーションを配置する値。 アプリケーションでは、この値を使用して、ドライバーが要求しているパラメーター データを決定します。 ドライバーは、列のデータを必要とする場合、ドライバーを返します、 * \*ValuePtrPtr*バッファーの列が最初にバインドされている、次のように、アドレス。  
  
 *アドレスをバインド* + *オフセットをバインド*+ ((*行数*– 1) x*要素サイズ*)  
  
 変数が定義されている次の表に示すようにします。  
  
|変数|Description|  
|--------------|-----------------|  
|*アドレスをバインドします。*|指定されたアドレス、 *TargetValuePtr*引数**SQLBindCol**です。|  
|*オフセットのバインド*|SQL_ATTR_ROW_BIND_OFFSET_PTR ステートメント属性で指定されたアドレスに格納された値。|  
|*行番号*|1 から始まる行セットの行の数。 単一行のフェッチは、既定値は、これは 1 です。|  
|*要素のサイズ*|両方のデータと長さ/インジケーター バッファーの SQL_ATTR_ROW_BIND_TYPE ステートメント属性の値。|  
  
 また、これを呼び出して、アプリケーションにインジケーターは SQL_NEED_DATA を返します**SQLPutData**データを送信します。  
  
 アプリケーションの呼び出し**SQLPutData**列またはパラメーターの実行時データのデータを送信するために必要な回数だけです。 列またはパラメーターのすべてのデータが送信された後、アプリケーションを呼び出す**SQLParamData**もう一度です。 場合**SQLParamData** SQL_NEED_DATA を返しますが別のパラメーターまたは列のデータを送信する必要があります。 そのため、アプリケーションを再度呼び出す**SQLPutData**です。 実行時データのすべてのデータがすべてのパラメーターまたは列の送信された場合**SQLParamData** SQL_SUCCESS または SQL_SUCCESS_WITH_INFO の値を返します* \*ValuePtrPtr*が定義されていませんSQL ステートメントを実行して、または**SQLBulkOperations**または**SQLSetPos**呼び出しを処理することができます。  
  
 場合**SQLParamData**な検索の提供パラメーターのデータを更新または delete ステートメント、データ ソースへの呼び出しですべての行は影響しない**SQLParamData** SQL_NO_DATA が返されます。  
  
 方法の実行時データ パラメーターのデータの詳細については、ステートメントの実行時に渡されたを参照してください「パラメーターの値の引き渡し」 [SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)と[長い形式のデータを送信する](../../../odbc/reference/develop-app/sending-long-data.md)です。 更新や追加方法 - 実行時データ列のデータに関する詳細についてを参照してください"を使用して SQLSetPos"で[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)、「を実行する一括更新プログラムを使用してブックマーク」で[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)、および[長い形式のデータおよび SQLSetPos SQLBulkOperations](../../../odbc/reference/develop-app/long-data-and-sqlsetpos-and-sqlbulkoperations.md)です。  
  
 **SQLParamData**ストリーミングされる出力パラメーターを取得すると呼ばれることができます。 ときに**SQLMoreResults**、 **SQLExecute**、 **SQLGetData**、または**SQLExecDirect**返します SQL_PARAM_DATA_AVAILABLE、呼び出す**SQLParamData**パラメーターが使用可能な値を判別します。 SQL_PARAM_DATA_AVAILABLE とストリーム出力パラメーターの詳細については、次を参照してください。 [SQLGetData を使用して出力パラメーターを取得する](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)です。  
  
## <a name="code-example"></a>コード例  
 参照してください[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|パラメーターへのバッファーのバインド|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|ステートメントの処理を取り消す|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|ステートメント内のパラメーターに関する情報を返す|[SQLDescribeParam 関数](../../../odbc/reference/syntax/sqldescribeparam-function.md)|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|実行時にパラメーターのデータを送信します。|[SQLPutData 関数](../../../odbc/reference/syntax/sqlputdata-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)   
 [SQLGetData を使用して出力パラメーターを取得します。](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)

