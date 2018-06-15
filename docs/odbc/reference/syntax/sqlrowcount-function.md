---
title: Sqlrowcount |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
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
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f9ad642032c2bee346381bd74a2dc5db46bb3d0f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32920177"
---
# <a name="sqlrowcount-function"></a>SQLRowCount 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLRowCount**影響を受ける行の数を返します、**更新**、**挿入**、または**削除**ステートメントは、SQL_ADD SQL_UPDATE_BY_BOOKMARK、または sql _。DELETE_BY_BOOKMARK 操作**SQLBulkOperations**; または SQL_UPDATE または SQL_DELETE 操作**SQLSetPos**です。  
  
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
 [出力]行の数を返すバッファーへのポインター。 **更新**、**挿入**、および**削除**内 SQL_ADD、SQL_UPDATE_BY_BOOKMARK、および SQL_DELETE_BY_BOOKMARK の操作用のステートメント**SQLBulkOperations**とで SQL_UPDATE または SQL_DELETE 操作の**SQLSetPos**で返される値 **RowCountPtr*が影響を受ける行数、要求または影響を受けた行の数が使用可能な場合は – 1。  
  
 ときに**SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、 **SQLSetPos、または SQLMoreResults**が呼び出されたが、SQL_DIAG_ROW_COUNT行の数に診断データの構造体のフィールドが設定されているし、行の数が実装に依存するようにキャッシュします。 **SQLRowCount**キャッシュされた行のカウント値を返します。 キャッシュされた行の数の値が有効では、ステートメント ハンドルが準備または割り当て済みの状態に戻す設定されるまで、ステートメントを再実行または**SQLCloseCursor**と呼びます。 場合は、関数が呼び出されて、SQL_DIAG_ROW_COUNT フィールドが設定されているため、値が返されますによって**SQLRowCount** SQL_DIAG_ROW_COUNT フィールドにリセットため SQL_DIAG_ROW_COUNT フィールドの値と異なる場合があります関数呼び出しでは 0 です。  
  
 ドライバーの他のステートメントおよび関数を使用してで返される値を定義できます\* *RowCountPtr*です。 たとえば、一部のデータ ソースがありますによって返される行の数を返す、**選択**ステートメントまたは行をフェッチする前に、カタログ関数。  
  
> [!NOTE]  
>  多くのデータ ソースは、結果をフェッチする前にセットの行の数を返すことはできません。相互運用性を最大にするため、アプリケーションはこの動作に保証はありません。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLRowCount** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLRowCount**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLRowCount**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM)、関数が呼び出された呼び出しの前に**SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos** の*StatementHandle*です。<br /><br /> (DM) の非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 ステートメント ハンドルで実行された最後の SQL ステートメントがなかったかどうか、**更新**、**挿入**、または**削除**ステートメントまたは場合、*操作*前の呼び出しで引数**SQLBulkOperations** SQL_ADD、SQL_UPDATE_BY_BOOKMARK、または SQL_DELETE_BY_BOOKMARK、できなかった場合、または、*操作*を前の呼び出しで引数**SQLSetPos** SQL_UPDATE または SQL_DELETE の値が **RowCountPtr*ドライバーで定義されます。 詳細については、次を参照してください。[の影響を受ける行の数を決定する](../../../odbc/reference/develop-app/determining-the-number-of-affected-rows.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
