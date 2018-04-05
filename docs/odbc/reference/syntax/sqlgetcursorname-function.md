---
title: SQLGetCursorName 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLGetCursorName
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetCursorName
helpviewer_keywords:
- SQLGetCursorName function [ODBC]
ms.assetid: e6e92199-7bb6-447c-8987-049a4c6ce05d
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 69a0da5196c5724284c2da75dc6c7deb3c3cedcd
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetcursorname-function"></a>SQLGetCursorName 関数
**準拠**  
 バージョンで導入されました ODBC 1.0 標準準拠: ISO 92。  
  
 **概要**  
 **SQLGetCursorName**指定されたステートメントに関連付けられているカーソル名を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLGetCursorName(  
     SQLHSTMT        StatementHandle,  
     SQLCHAR *       CursorName,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   NameLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *カーソル名*  
 [出力]カーソル名を返されるバッファーへのポインター。  
  
 場合*カーソル名*null、 *NameLengthPtr*はまだ文字 (文字データの null 終端文字を除く) の合計数を返しますが指すバッファーに返される使用可能な*カーソル名*です。  
  
 *BufferLength*  
 [入力]長さ\**カーソル名*、文字数。 場合の値*\*カーソル名*Unicode 文字列です (呼び出し時に**SQLGetCursorNameW**) では、 *BufferLength*引数は偶数である必要があります。  
  
 *NameLengthPtr*  
 [出力]文字 (null 終了文字を除く) の合計数を返すメモリへのポインターで返される使用可能な\**カーソル名*です。 返される文字数がより大きいかに等しい場合*BufferLength*、内のカーソル名\**カーソル名*に切り捨てられます*BufferLength*null 終端文字の長さマイナスです。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetCursorName** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる**SQLGetDiagRec**で、 *HandleType*sql_handle_stmt としての*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLGetCursorName**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|バッファー \**カーソル名*全体のカーソルの名前を返す、カーソル名は切り詰められましたために大きさが不十分です。 切り詰められていないカーソル名の長さが返される **NameLengthPtr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLGetCursorName**関数が呼び出されました。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *StatementHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY015|使用可能なカーソル名|(DM) ドライバーは ODBC 2*.x*ドライバーのステートメントで開いているカーソルがなかったおよびでカーソル名が設定されていません**SQLSetCursorName**です。|  
|HY090|文字列またはバッファーの長さが無効です。|引数に指定された値 (DM) *BufferLength*が 0 未満です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 カーソル名が位置指定更新でのみ使用および delete ステートメント (たとえば、**更新***テーブル名*.**WHERE CURRENT OF** *カーソル名*)。 詳細については、次を参照してください。[位置指定の Update ステートメントとステートメントの削除](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)です。 アプリケーションが要求されていない場合**SQLSetCursorName**カーソル名を定義するには、ドライバーには名前が生成されます。 この名前は、アルファベット SQL_CUR で始まります。  
  
> [!NOTE]  
>  ODBC 2 で*.x*開いているカーソルが入っていなかったし、への呼び出しで名前が設定されていません、 **SQLSetCursorName**への呼び出し**SQLGetCursorName** SQLSTATE HY015 が返されます (カーソル名がないです。使用可能)。 ODBC 3*.x*、これが true であるのどの段階で不要になった**SQLGetCursorName**が呼び出されると、ドライバーは、カーソル名を返します。  
  
 **SQLGetCursorName**明示的または暗黙的に名前が作成されたかどうか、カーソルの名前を返します。 場合、カーソル名が暗黙的に生成された**SQLSetCursorName**は呼び出されません。 **SQLSetCursorName**カーソルが割り当てられているまたは準備された状態である限り、ステートメントのカーソルの名前を変更するに呼び出せることができます。  
  
 設定されるまでは、明示的または暗黙的に設定されているカーソル名、 *StatementHandle*関連付けられているを使用して削除**SQLFreeHandle**で、 *HandleType* SQL_HANDLE_STMT のです。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|SQL ステートメントを実行します。|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントを実行します。|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|実行のためのステートメントを準備します。|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|カーソル名の設定|[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
