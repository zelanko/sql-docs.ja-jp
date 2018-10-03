---
title: SQLRowCount 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRowCount
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRowCount
helpviewer_keywords:
- SQLRowCount function [ODBC]
ms.assetid: 61e00a8a-9b3b-45b9-b397-7fe818822416
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc2ab4b2e97b9e1a83e0b00404010195b08f0dc0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654930"
---
# <a name="sqlrowcount-function"></a>SQLRowCount 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLRowCount**によって影響を受ける行の数を返します、 **UPDATE**、**挿入**、または**削除**ステートメントでは、SQL_ADD、SQL_UPDATE_BY_BOOKMARK、または sql _DELETE_BY_BOOKMARK 操作**SQLBulkOperations**; SQL_UPDATE または SQL_DELETE 操作または**SQLSetPos**します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLRowCount(  
      SQLHSTMT   StatementHandle,  
      SQLLEN *   RowCountPtr);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *RowCountPtr*  
 [出力]行の数を返すバッファーへのポインター。 **更新**、**挿入**、および**削除**SQL_ADD、SQL_UPDATE_BY_BOOKMARK、および SQL_DELETE_BY_BOOKMARK 操作のステートメント、 **SQLBulkOperations**、およびで SQL_UPDATE または SQL_DELETE 操作**SQLSetPos**で返される値 **RowCountPtr*か影響を受ける行の数が、要求または影響を受けた行の数がない場合は-1。  
  
 ときに**SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、 **SQLSetPos、または SQLMoreResults**が呼び出され、SQL_DIAG_ROW_COUNT診断データの構造体のフィールドが行の数に設定され、行の数が、実装に依存する方法にキャッシュされます。 **SQLRowCount**キャッシュされた行の数の値を返します。 キャッシュされた行の数の値が有効では、ステートメント ハンドルが 準備済みまたは割り当て済みの状態になるまで、ステートメントを再実行または**SQLCloseCursor**が呼び出されます。 SQL_DIAG_ROW_COUNT フィールドが設定されているため、関数が呼び出された場合、によって値を返すに注意してください**SQLRowCount** SQL_DIAG_ROW_COUNT フィールドをリセットするために SQL_DIAG_ROW_COUNT フィールドの値と異なる可能性があります。任意の関数呼び出しで 0 に設定します。  
  
 その他のステートメントと関数を使用して、ドライバーに返される値を定義できます\* *RowCountPtr*します。 たとえば、一部のデータ ソースがによって返される行の数を取得できる可能性があります、**選択**ステートメントまたは行をフェッチする前に、カタログ関数。  
  
> [!NOTE]  
>  多くのデータ ソースは、結果にはフェッチする前にセットの行の数を返すことはできません。最大の相互運用性、アプリケーションはこの動作に依存しない必要があります。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE します。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLRowCount** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得できる**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*します。 次の表に、一般的にによって返される SQLSTATE 値**SQLRowCount** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM) を非同期的に実行中の関数が呼び出された接続ハンドルに関連付けられているため、 *StatementHandle*します。 この非同期関数ではときに実行されている、 **SQLRowCount**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**に対して呼び出された、 *StatementHandle* SQL_PARAM_DATA_ を返されます。ご利用いただけます。 ストリームのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) 関数が呼び出す前に呼び出された**SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos** の*StatementHandle*します。<br /><br /> (DM) を非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**に対して呼び出された、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列のデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続のタイムアウト期間が終了しました。 によって、接続タイムアウト期間が設定されます**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT します。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 ステートメント ハンドルで実行された最後の SQL ステートメントがなかったかどうか、 **UPDATE**、**挿入**、または**削除**ステートメントまたは場合、*操作*前の呼び出しで引数**SQLBulkOperations** SQL_ADD、SQL_UPDATE_BY_BOOKMARK、または SQL_DELETE_BY_BOOKMARK、なかった場合は、*操作*を前の呼び出しで引数**SQLSetPos** SQL_UPDATE または SQL_DELETE の値が **RowCountPtr*ドライバーで定義されます。 詳細については、次を参照してください。[の影響を受ける行の数を決定する](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
