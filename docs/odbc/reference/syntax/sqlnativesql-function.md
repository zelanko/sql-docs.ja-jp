---
title: "SQLNativeSql 関数 |Microsoft ドキュメント"
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
- SQLNativeSql
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLNativeSql
helpviewer_keywords:
- SQLNativeSql function [ODBC]
ms.assetid: b8efc247-27ab-4a00-92b6-1400785783fe
caps.latest.revision: 24
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1672e4c1f21d223ed326c0e0649fc7cbb2376f74
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlnativesql-function"></a>SQLNativeSql 関数
**準拠**  
 バージョンが導入されています ODBC 1.0 標準への準拠: ODBC。  
  
 **概要**  
 **SQLNativeSql**ドライバーによって変更された、SQL 文字列を返します。 **SQLNativeSql** SQL ステートメントは実行されません。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLNativeSql(  
     SQLHDBC        ConnectionHandle,  
     SQLCHAR *      InStatementText,  
     SQLINTEGER     TextLength1,  
     SQLCHAR *      OutStatementText,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   TextLength2Ptr);  
```  
  
## <a name="arguments"></a>引数  
 *ConnectionHandle*  
 [入力]接続ハンドルです。  
  
 *InStatementText*  
 [入力]変換する SQL テキスト文字列です。  
  
 *TextLength1*  
 [入力]文字の長さ **InStatementText*テキスト文字列。  
  
 *OutStatementText*  
 [出力]翻訳済みの SQL 文字列を返すバッファーへのポインター。  
  
 場合*OutStatementText* null、 *TextLength2Ptr*は文字 (文字データの null 終端文字を除く) の合計数を返しますが、バッファーに返される使用可能なによって示される*OutStatementText*です。  
  
 *BufferLength*  
 [入力]内の文字数、 \* *OutStatementText*バッファー。 値が返される場合 *\*InStatementText* Unicode 文字列です (呼び出し時に**SQLNativeSqlW**) では、 *BufferLength*引数は偶数である必要があります。  
  
 *TextLength2Ptr*  
 [出力]文字 (除外 null 終了あり) で返される使用可能な数の合計を返すバッファーへのポインター \* *OutStatementText*です。 返される文字数がより大きいかに等しい場合*BufferLength*では、SQL 文字列を翻訳\* *OutStatementText*に切り捨てられます*BufferLength* null 終端文字の長さマイナスです。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLNativeSql** SQL_ERROR または SQL_SUCCESS_WITH_INFO のいずれかを返します呼び出すことによって、関連付けられた SQLSTATE 値を取得できる**SQLGetDiagRec**で、 *HandleType*sql_handle_dbc としての*処理*の*ConnectionHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLNativeSql**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|バッファー \* *OutStatementText* SQL 文字列が全体を返す SQL 文字列が切り捨てられましたため大きさがありません。 切り詰められていない SQL 文字列の長さが返される **TextLength2Ptr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08003|接続は開いていません|*ConnectionHandle*接続状態ではありませんでした。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|22007|無効な datetime 形式|**InStatementText*値が無効な日付、時刻、またはタイムスタンプ escape 句が含まれています。|  
|24000|カーソル状態が無効|または、結果セットの終了後に結果セットの開始前に、ステートメントで参照されるカーソルが配置されました。 このエラーをネイティブ DBMS カーソルの実装を持つドライバーによって返されないことができます。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY009|無効な null ポインターの使用|(DM) **InStatementText*が null ポインターでした。|  
|HY010|関数のシーケンス エラー|(DM) の非同期的に実行中の関数が呼び出された、 *ConnectionHandle*この関数が呼び出されたときに実行されているとします。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) 引数*TextLength1* SQL_NTS に等しくないが、0 より小さいをでした。|  
|||(DM) 引数*BufferLength*が 0 との引数よりも小さい*OutStatementText*が null ポインターではありません。|  
|HY109|無効なカーソルの位置|カーソルの現在の行が削除されたかがまだフェッチされていません。 このエラーをネイティブ DBMS カーソルの実装を持つドライバーによって返されないことができます。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *ConnectionHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 新機能の例を次に**SQLNativeSql**スカラー関数の変換を含む次の入力 SQL 文字列を返す場合があります。 データ ソース内の整数型の列 empid があると仮定します。  
  
```  
SELECT { fn CONVERT (empid, SQL_SMALLINT) } FROM employee  
```  
  
 Microsoft SQL Server 用のドライバーには、次の翻訳済みの SQL 文字列が返されます。  
  
```  
SELECT convert (smallint, empid) FROM employee  
```  
  
 ORACLE サーバー用のドライバーは、次の翻訳済みの SQL 文字列を返す場合があります。  
  
```  
SELECT to_number (empid) FROM employee  
```  
  
 Ingres 用のドライバーは、次の翻訳済みの SQL 文字列を返す場合があります。  
  
```  
SELECT int2 (empid) FROM employee  
```  
  
 詳細については、次を参照してください。[直接実行](../../../odbc/reference/develop-app/direct-execution-odbc.md)と[準備された実行](../../../odbc/reference/develop-app/prepared-execution-odbc.md)です。  
  
## <a name="related-functions"></a>関連する関数  
 [なし] :  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

