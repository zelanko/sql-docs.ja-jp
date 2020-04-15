---
title: 関数を閉じる |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLCloseCursor
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLCloseCursor
helpviewer_keywords:
- SQLCloseCursor function [ODBC]
ms.assetid: 05b0a054-e28d-4e16-b5b0-07418486b372
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f2703af46e6043fbadb7d3ceb5c00c565c1f6777
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301302"
---
# <a name="sqlclosecursor-function"></a>SQLCloseCursor 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLCloseCursor ステートメント**で開かれたカーソルを閉じ、保留中の結果を破棄します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLCloseCursor(  
     SQLHSTMT     StatementHandle);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLCloseCursor が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときに、関連付けられた SQLSTATE 値を取得するには、SQL_HANDLE_STMT*のハンドル型*と*ステートメント ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出します。 次の表は **、SQLCloseCursor**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|24000|カーソル状態が無効|ステートメント ハンドルでカーソルが開*かれなかった*。 (これは ODBC 3 によってのみ返されます。*x*ドライバ。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM) 非同期に実行される関数が *、 StatementHandle*に関連付けられた接続ハンドルに対して呼び出され、この関数が呼び出されたときにまだ実行されていました。<br /><br /> (DM) 非同期に実行される関数が呼び出されました、 *StatementHandle、* この関数が呼び出されたときに実行されています。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 **カーソルがオープンされていない場合、SQLCloseCursor**は SQLSTATE 24000 (無効なカーソル状態) を返します。 **SQLCloseCursor**を呼び出すことは、SQL_CLOSE オプションを指定して**SQLFreeStmt**を呼び出すのと同じですが、ステートメントでカーソルが開かなければ、SQL_CLOSEを指定した**SQLFreeStmt**はアプリケーションに影響を与えなく **、SQLCloseCursor**は SQLSTATE 24000 (無効なカーソル状態) を返します。  
  
> [!NOTE]  
>  ODBC 3 の場合。*x*アプリケーションは ODBC 2 で動作します。*x*ドライバーは、カーソルが開いていないときに**SQLCloseCursor**を呼び出します、SQLSTATE 24000 (無効なカーソルの状態) は返されません、ドライバー マネージャーは、SQL_CLOSEを使用して**SQLCloseCursor**を**SQLFreeStmt**にマップするため。  
  
 詳細については、「[カーソルを閉じる」を](../../../odbc/reference/develop-app/closing-the-cursor.md)参照してください。  
  
## <a name="code-example"></a>コード例  
 [「SQL ブラウズ接続関数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)」および[「SQL 接続関数](../../../odbc/reference/syntax/sqlconnect-function.md)」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ステートメント処理のキャンセル|[SQLCancel 関数](../../../odbc/reference/syntax/sqlcancel-function.md)|  
|ハンドルを解放する|[SQLFreeHandle 関数](../../../odbc/reference/syntax/sqlfreehandle-function.md)|  
|複数の結果セットの処理|[SQLMoreResults 関数](../../../odbc/reference/syntax/sqlmoreresults-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
