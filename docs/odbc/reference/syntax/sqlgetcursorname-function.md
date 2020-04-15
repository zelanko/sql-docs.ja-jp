---
title: 関数を取得する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d3ac65dc07897ddc789ee03b06b1bc1f71d37c3c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285550"
---
# <a name="sqlgetcursorname-function"></a>SQLGetCursorName 関数
**適合 性**  
 バージョン導入: ODBC 1.0 規格準拠: ISO 92  
  
 **まとめ**  
 **指定**したステートメントに関連付けられたカーソル名を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLGetCursorName(  
     SQLHSTMT        StatementHandle,  
     SQLCHAR *       CursorName,  
     SQLSMALLINT     BufferLength,  
     SQLSMALLINT *   NameLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *カーソル名*  
 [出力]カーソル名を返すバッファーへのポインター。  
  
 *カーソル名*が NULL の場合 *、NameLengthPtr*は*CursorName*が指すバッファーで返される文字の合計数 (文字データの NULL 終端文字を除く) を返します。  
  
 *BufferLength*  
 [入力]\**カーソル名*の長さ (文字数)。 *\*カーソル名*の値が Unicode 文字列の場合 **(SQLGetCursorNameW**を呼び出すとき)、BufferLength 引数は偶数でなければなりません。 *BufferLength*  
  
 *名前の長さプター*  
 [出力]\* *CursorName*で返される文字の合計数 (NULL 終端文字を除く) を返すメモリへのポインター。 戻り値の文字数が*BufferLength*以上の場合、\**カーソル名*のカーソル名は*BufferLength*から NULL 終端文字の長さを引いた値に切り捨てられます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetCursorName が**SQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返す場合は、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLGetCursorName**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|カーソル名\*全体を返すほど大きなバッファ*CursorName*がなかったので、カーソル名が切り捨てられました。 切り捨てられていないカーソル名の長さは、 **NameLengthPtr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は、**関数**が呼び出されたときに実行されていました。<br /><br /> (DM)*ステートメント ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。<br /><br /> (DM) 非同期に実行される関数が呼び出されました、 *StatementHandle、* この関数が呼び出されたときに実行されています。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY015|カーソル名がありません|(DM) ドライバは ODBC 2 *.x*ドライバで、ステートメントにカーソルが開かれていたり **、SQLSetCursorName**でカーソル名が設定されていなかったりしました。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*BufferLength*で指定された値が 0 未満でした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 カーソル名は、位置指定更新および削除ステートメント (たとえば **、UPDATE** _table-name_ .**カーソル名の現在**_の_場所 。 詳細については、「[位置指定更新ステートメントとステートメントの削除](../../../odbc/reference/develop-app/positioned-update-and-delete-statements.md)」を参照してください。 アプリケーションがカーソル名を定義するために**SQLSetCursorName**を呼び出さない場合、ドライバーは名前を生成します。 この名前は、SQL_CUR文字で始まります。  
  
> [!NOTE]
>  ODBC 2 *.x*では、オープン・カーソルがなく、 **SQLSetCursorName**の呼び出しによって名前が設定されていなかった場合、 **SQLGetCursorName**の呼び出しは SQLSTATE HY015 を返しました (カーソル名は使用できません)。 ODBC 3 *.x*では、これはもはや当てはまりません。**SQLGetCursorName**が呼び出されたときに、ドライバーは、カーソル名を返します。  
  
 **SQLGetCursorName は**、名前が明示的に作成されたか暗黙的に作成されたか否かにかかわらず、カーソルの名前を返します。 カーソル名は **、SQLSetCursorName**が呼び出されない場合に暗黙的に生成されます。 **SQLSetCursorName**は、カーソルが割り振りまたは準備された状態である限り、ステートメント上のカーソルの名前を変更するために呼び出すことができます。  
  
 明示的または暗黙的に設定されたカーソル名は、関連付けられている*ステートメント ハンドル*が削除されるまで、SQL_HANDLE_STMTの*HandleType*を指定した**SQLFreeHandle**を使用して設定されたままになります。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|SQL ステートメントの実行|[SQLExecDirect 関数](../../../odbc/reference/syntax/sqlexecdirect-function.md)|  
|準備された SQL ステートメントの実行|[SQLExecute 関数](../../../odbc/reference/syntax/sqlexecute-function.md)|  
|実行のためのステートメントの準備|[SQLPrepare 関数](../../../odbc/reference/syntax/sqlprepare-function.md)|  
|カーソル名の設定|[SQLSetCursorName 関数](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
