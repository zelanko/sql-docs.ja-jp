---
title: SQLCloseCursor 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCloseCursor
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLCloseCursor
helpviewer_keywords:
- SQLCloseCursor function [ODBC]
ms.assetid: 05b0a054-e28d-4e16-b5b0-07418486b372
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2cf998ada7b0e6835265c8e58bfcab855d9c2361
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65537668"
---
# <a name="sqlclosecursor-function"></a>SQLCloseCursor 関数
**準拠**  
 バージョンが導入されました。ODBC 3.0 規格に準拠します。ISO 92  
  
 **まとめ**  
 **SQLCloseCursor**でステートメントが開かれたし、保留中の結果を破棄するカーソルを閉じます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLCloseCursor(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLCloseCursor** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得される可能性があります**SQLGetDiagRec**で、 *HandleType* SQL の_HANDLE_STMT と*処理*の*StatementHandle*します。 次の表に、一般的にによって返される SQLSTATE 値**SQLCloseCursor** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|24000|カーソル状態が無効|開いているカーソルがなかった、 *StatementHandle*します。 (これは、ODBC 3 のみが返されます。*x*ドライバー)。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM) に関連付けられている接続ハンドルの非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) を非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**に対して呼び出された、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 **SQLCloseCursor**カーソルが開いていない場合は、SQLSTATE 24000 (無効なカーソル状態) を返します。 呼び出す**SQLCloseCursor**呼び出しと同じですが**SQLFreeStmt** SQL_CLOSE オプションでは、例外を使用する**SQLFreeStmt** SQL_CLOSE にも何も起こりません、アプリケーションのステートメントで開いているカーソルがない場合は、while **SQLCloseCursor** SQLSTATE 24000 (無効なカーソル状態) を返します。  
  
> [!NOTE]  
>  ODBC 3 場合。*x* ODBC 2 を使用するアプリケーション *。x*ドライバー呼び出し**SQLCloseCursor**カーソルが開いていないときに、ドライバー マネージャーがマップされるため、SQLSTATE 24000 (無効なカーソル状態) は返されませんが**SQLCloseCursor** に**SQLFreeStmt** SQL_CLOSE とします。  
  
 詳細については、次を参照してください。[カーソルを閉じる](../../../odbc/reference/develop-app/closing-the-cursor.md)します。  
  
## <a name="code-example"></a>コード例  
 参照してください[SQLBrowseConnect 関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)と[SQLConnect 関数](../../../odbc/reference/syntax/sqlconnect-function.md)します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ステートメントの処理をキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|ハンドルの解放|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|複数の結果セットの処理|[SQLMoreResults 関数](../../../odbc/reference/syntax/sqlmoreresults-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
