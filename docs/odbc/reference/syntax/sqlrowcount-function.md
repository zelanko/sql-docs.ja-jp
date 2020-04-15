---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRowCount
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLRowCount
helpviewer_keywords:
- SQLRowCount function [ODBC]
ms.assetid: 61e00a8a-9b3b-45b9-b397-7fe818822416
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2cbca03e7c3e381b803196a1bf7bb227ebeea03b
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81293372"
---
# <a name="sqlrowcount-function"></a>SQLRowCount 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLRowCount は****、UPDATE**、**挿入**、または**DELETE**ステートメントによって影響を受ける行の数を返します。**SQLBulk オペレーション**のSQL_ADD、SQL_UPDATE_BY_BOOKMARK、またはSQL_DELETE_BY_BOOKMARK操作。または **、SQLSetPos**のSQL_UPDATEまたはSQL_DELETE操作を行います。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLRowCount(  
      SQLHSTMT   StatementHandle,  
      SQLLEN *   RowCountPtr);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *行カウントプター*  
 [出力]行数を返すバッファーへのポイント。 **UPDATE、INSERT、** および**DELETE**ステートメントの場合は、 **SQLBulkOperations**のSQL_ADD、SQL_UPDATE_BY_BOOKMARK、およびSQL_DELETE_BY_BOOKMARK操作、および**SQLSetPos**のSQL_UPDATEまたはSQL_DELETE操作の場合、 **RowCountPtr*で返される値は、要求の影響を受ける行数のいずれかです。 **INSERT**  
  
 **SQL 実行****、SQLExecDirect** **、SQLBulkOperations** **、SQLSetPos、または SQLMoreResults**が呼び出されると、診断データ構造体のSQL_DIAG_ROW_COUNT フィールドが行数に設定され、行数が実装に依存する方法でキャッシュされます。 **SQLRowCount は**、キャッシュされた行カウント値を返します。 キャッシュされた行カウント値は、ステートメント ハンドルが準備済みまたは割り当て済みの状態に戻るまで、ステートメントが再実行されるか、**または SQLCloseCursor**が呼び出されるまで有効です。 SQL_DIAG_ROW_COUNTフィールドが設定された後に関数が呼び出された場合、SQL_DIAG_ROW_COUNTフィールドは関数呼び出しによって 0 にリセットされるため **、SQLRowCount**によって返される値がSQL_DIAG_ROW_COUNTフィールドの値と異なる可能性があることに注意してください。  
  
 その他のステートメントや関数の場合、ドライバーは\**RowCountPtr*で返される値を定義できます。 たとえば、データ ソースによっては **、SELECT**ステートメントまたはカタログ関数が行をフェッチする前に返す行数を返すことができる場合があります。  
  
> [!NOTE]  
>  多くのデータ ソースは、フェッチする前に結果セット内の行数を返すことができません。相互運用性を最大限に高めるには、アプリケーションはこの動作に依存しないようにしてください。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLRowCount**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返す場合、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLRowCount**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLRowCount**関数が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM) 関数は、*ステートメント ハンドル*に対して**SQL 実行****、SQLExecDirect、SQLBulkOperations**、または**SQLBulkOperations****SQLSetPos**を呼び出す前に呼び出されました。<br /><br /> (DM) 非同期に実行される関数が呼び出されました、 *StatementHandle、* この関数が呼び出されたときに実行されています。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 ステートメント ハンドルで最後に実行された SQL ステートメントが**UPDATE、INSERT、** または**DELETE**ステートメントでない場合、または**SQLBulkOperations**への前回の呼び出しで*Operation*引数がSQL_ADD、SQL_UPDATE_BY_BOOKMARK、またはSQL_DELETE_BY_BOOKMARKされていない場合、または前の**SQLSetPos**の呼び出しの*Operation*引数がSQL_UPDATEまたはSQL_DELETEされていない場合、**RowCountPtr*の値はドライバー定義です。 **INSERT** 詳細については、「[影響を受ける行の数の決定](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|SQL ステートメントの実行|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
