---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLNativeSql
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLNativeSql
helpviewer_keywords:
- SQLNativeSql function [ODBC]
ms.assetid: b8efc247-27ab-4a00-92b6-1400785783fe
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9666bc767affb3b6bb624c416614079193d4b921
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304723"
---
# <a name="sqlnativesql-function"></a>SQLNativeSql 関数
**適合 性**  
 バージョン導入: ODBC 1.0 標準準拠: ODBC  
  
 **まとめ**  
 **ドライバーによって**変更された SQL 文字列を返します。 **SQL ステートメント**は実行されません。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLNativeSql(  
     SQLHDBC        ConnectionHandle,  
     SQLCHAR *      InStatementText,  
     SQLINTEGER     TextLength1,  
     SQLCHAR *      OutStatementText,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   TextLength2Ptr);  
```  
  
## <a name="arguments"></a>引数  
 *接続ハンドル*  
 [入力] 接続ハンドル。  
  
 *ステートメントテキスト*  
 [入力]変換する SQL テキスト文字列。  
  
 *テキスト長さ1*  
 [入力]**InStatementText テキスト*文字列の文字数で表された長さ。  
  
 *ステートメントテキスト*  
 [出力]変換された SQL 文字列を返すバッファーへのポインター。  
  
 *場合は*、Null の*場合、TextLength2Ptr*は、引き続き返される文字列の合計数 (文字データの null 終端文字を除く) を返*します。*  
  
 *BufferLength*  
 [入力]\**バッファ内*の文字数。 で返される値が Unicode 文字列である場合 **(SQLNativeSqlW**を呼び出すとき *)、BufferLength*引数は偶数でなければなりません。 * \**  
  
 *テキスト長2Ptr*  
 [出力]\**返*される文字の合計数 (Null 終端を除く) を返すバッファーへのポインター。 返される文字の数が*BufferLength*以上の場合、\**変換*された SQL 文字列は *、BufferLength*から NULL 終端文字の長さを引いた値に切り捨てられます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLNativeSql**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_DBCの*ハンドル型*と*接続ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLNativeSql**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|バッファー \* *OutStatementText*は SQL 文字列全体を返すのに十分な大きさではなかったので、SQL 文字列が切り捨てられました。 切り捨てられていない SQL 文字列の長さは、 **TextLength2Ptr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08003|接続が開かない|*接続ハンドル*は接続状態ではありませんでした。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|22007|日付/時刻形式が無効です|**InStatementText には*、無効な日付、時刻、またはタイムスタンプ値を持つエスケープ句が含まれていました。|  
|24000|カーソル状態が無効|ステートメントで参照されるカーソルは、結果セットの開始前、または結果セットの終了後に位置付けされました。 このエラーは、ネイティブ DBMS カーソルの実装を持つドライバーによって返されない可能性があります。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY009|無効な null ポインターの使用|(DM) **InStatementText*は null ポインターでした。|  
|HY010|関数シーケンス エラー|(DM) 非同期に実行される関数が呼び出されました、 *ConnectionHandle、* この関数が呼び出されたときに実行されています。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) 引数*TextLength1*が 0 未満でしたが、SQL_NTSと等しくありません。|  
|||(DM) 引数*BufferLength*が 0 より小さく、引数*OutStatementText*が null ポインターではありませんでした。|  
|HY109|カーソル位置が無効です|カーソルの現在の行が削除されたか、フェッチされていません。 このエラーは、ネイティブ DBMS カーソルの実装を持つドライバーによって返されない可能性があります。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM) に関連付けられているドライバー、 *ConnectionHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 次に示す例は、スカラー関数 CONVERT を含む次の入力 SQL 文字列に対して**SQLNativeSql**が返す可能性がある例です。 列の empid がデータ ソース内の INTEGER 型であるとします。  
  
```sql  
SELECT { fn CONVERT (empid, SQL_SMALLINT) } FROM employee  
```  
  
 SQL Server のドライバーは、次の変換された SQL 文字列を返す可能性があります。  
  
```sql  
SELECT convert (smallint, empid) FROM employee  
```  
  
 ORACLE サーバーのドライバーは、次の変換された SQL 文字列を返す可能性があります。  
  
```sql  
SELECT to_number (empid) FROM employee  
```  
  
 Ingres のドライバーは、次の変換された SQL 文字列を返す可能性があります。  
  
```sql  
SELECT int2 (empid) FROM employee  
```  
  
 詳細については、「[直接実行](../../../odbc/reference/develop-app/direct-execution-odbc.md)と[準備実行](../../../odbc/reference/develop-app/prepared-execution-odbc.md)」を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
 なし。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
