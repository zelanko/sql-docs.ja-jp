---
title: "SQLGetConnectAttr 関数 |Microsoft ドキュメント"
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
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectAttr
helpviewer_keywords:
- SQLGetConnectAttr function [ODBC]
ms.assetid: 2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33
caps.latest.revision: 32
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: fc8f754301b5b0c0d5259cd7613bacdf302a06e7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetconnectattr-function"></a>SQLGetConnectAttr 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLGetConnectAttr**接続属性の現在の設定を返します。  
  
> [!NOTE]  
>  詳細については、どのようなドライバー マネージャーは、この関数にする際にマップ ODBC 3*.x* ODBC 2 を利用するアプリケーション*.x*ドライバーを参照してください[後方の置換関数のマッピングアプリケーションの互換性を](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLGetConnectAttr(  
     SQLHDBC        ConnectionHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *ConnectionHandle*  
 [入力]接続ハンドルです。  
  
 *属性*  
 [入力]取得する属性。  
  
 *ValuePtr*  
 [出力]指定された属性の現在の値を返すメモリへのポインター*属性*です。 整数型の属性の一部のドライバーのみ書き込むことが、下位 32 ビットまたは 16 ビットのバッファーとのままにして、上位ビットがそのままです。 そのため、アプリケーションは SQLULEN のバッファーを使用し、この関数を呼び出す前に、値を 0 を初期化する必要があります。  
  
 場合*ValuePtr* null、 *StringLengthPtr*バイト (文字データの null 終端文字を除く) の合計数を返すはまだが指すバッファーに返される使用可能な*ValuePtr*です。  
  
 *BufferLength*  
 [入力]場合*属性*ODBC で定義された属性と*ValuePtr*文字の文字列またはバイナリ バッファーへのポインター、この引数の長さにする必要があります\* *ValuePtr*. 場合*属性*ODBC で定義された属性と\* *ValuePtr*整数*BufferLength*は無視されます。 場合の値* \*ValuePtr* Unicode 文字列です (呼び出し時に**SQLGetConnectAttrW**) では、 *BufferLength*引数は偶数である必要があります。  
  
 場合*属性*ドライバーの定義済みの属性は、アプリケーション、ドライバー マネージャーに属性の性質を示す設定、 *BufferLength*引数。 *BufferLength*次の値を持つことができます。  
  
-   場合* \*ValuePtr*文字の文字列を指すポインター *BufferLength*文字列の長さです。  
  
-   場合* \*ValuePtr*バイナリのバッファー、アプリケーションの場所へのポインター、SQL_LEN_BINARY_ATTR の結果である (*長さ*) マクロで*BufferLength*です。 これにより、配置に負の値*BufferLength*です。  
  
-   場合* \*ValuePtr*文字の文字列またはバイナリ文字列以外の値を指すポインター *BufferLength* SQL_IS_POINTER 値でなければなりません。  
  
-   場合* \*ValuePtr* 、固定長データ型を含む*BufferLength*は SQL_IS_INTEGER か SQL_IS_UINTEGER、必要に応じて。  
  
 *StringLengthPtr*  
 [出力]合計バイト数 (null 終了文字を除く) を返すバッファーへのポインターで返される使用可能な\* *ValuePtr*です。 場合\* *ValuePtr* null ポインターでは、長さは返されません。 属性値、文字の文字列であり、使用できるバイト数を返すよりも大きい場合*BufferLength* null 終端文字、内のデータの長さマイナス* \*ValuePtr*に切り捨てられます*BufferLength* null 終端文字の長さマイナスはドライバーによって null で終わるとします。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetConnectAttr** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますは、呼び出すことにより、診断データの構造から取得できます**SQLGetDiagRec** 、で*。HandleType* sql_handle_dbc としての*処理*の*ConnectionHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLGetConnectAttr**ですこの関数のコンテキストでは、各フォルダーについて説明しますと表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。. SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|返されるデータ\* *ValuePtr*に切り詰められました*BufferLength* null 終端文字の長さマイナスです。 切り詰められていない文字列値の長さが返される **StringLengthPtr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|08003|接続は開いていません|(DM)、*属性*接続を開くために必要な値が指定されました。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 引数で診断データの構造からエラー メッセージが返される*MessageText*で**SQLGetDiagField**エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM) **SQLBrowseConnect**で呼び出され、 *ConnectionHandle* SQL_NEED_DATA が返されます。 この関数が呼び出されました**SQLBrowseConnect** SQL_SUCCESS_WITH_INFO または SQL_SUCCESS が返されます。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、または**SQLMoreResults**で呼び出され、 *ConnectionHandle*し SQL_PARAM_DATA_ が返されました使用できます。 ストリーミングのすべてのパラメーターのデータが取得される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM) * \*ValuePtr*文字の文字列、および BufferLength は SQL_NTS に等しくないが、0 より小さい。|  
|HY092|無効な属性またはオプション識別子|引数が指定された値*属性*が ODBC ドライバーでサポートされているのバージョンは無効です。|  
|HY114|ドライバーは接続レベルの非同期関数の実行をサポートしていません|(DM) アプリケーションは、非同期の接続操作をサポートしていないドライバーの SQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLE で非同期関数の実行を有効にしようとしました。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|引数が指定された値*属性*有効な ODBC 接続属性であった ODBC のバージョンは、ドライバーでサポートされていますが、ドライバーによってサポートされていませんでした。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に対応するドライバー、 *ConnectionHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 一般的な接続属性については、次を参照してください。[接続属性](../../../odbc/reference/develop-app/connection-attributes.md)です。  
  
 設定可能な属性の一覧は、次を参照してください。 [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)です。 場合に注意してください*属性*、文字列を返す属性を指定します*ValuePtr*の文字列バッファーへのポインターにする必要があります。 Null 終了文字を含む、返される文字列の最大長になります*BufferLength*バイトです。  
  
 属性によって、アプリケーションが呼び出す前に、接続を確立するために**SQLGetConnectAttr**です。 ただし場合、 **SQLGetConnectAttr**が呼び出された指定された属性が、既定値はありませんし、前回の呼び出しが設定されていないと**SQLSetConnectAttr**、 **SQLGetConnectAttr**SQL_NO_DATA が返されます。  
  
 場合*属性*SQL_ATTR トレースまたは SQL_ATTR TRACEFILE *ConnectionHandle*が無効になると**SQLGetConnectAttr** SQL_ERROR または sql _ は返されませんINVALID_HANDLE 場合*ConnectionHandle*が無効です。 これらの属性は、すべての接続に適用されます。 **SQLGetConnectAttr**別の引数が有効でない場合、SQL_ERROR または SQL_INVALID_HANDLE を返します。  
  
 使用してステートメント属性を設定できますが、アプリケーション**SQLSetConnectAttr**、アプリケーションで使用できない**SQLGetConnectAttr**ステートメント属性を取得する値ですこれを呼び出す必要があります**。SQLGetStmtAttr**ステートメント属性の設定を取得します。  
  
 呼び出しによって返される SQL_ATTR_AUTO_IPD と SQL_ATTR_CONNECTION_DEAD の両方の接続属性**SQLGetConnectAttr**への呼び出しで設定することはできませんが、 **SQLSetConnectAttr**です。  
  
> [!NOTE]  
>  非同期のサポートされていません**SQLGetConnectAttr**です。 実装するときに**SQLGetConnectAttr**ドライバーの情報が送信されるか、サーバーから要求する回数を最小限に抑え、パフォーマンスが向上します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|ステートメント属性の設定値を返す|[SQLGetStmtAttr 関数](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|環境属性を設定|[SQLSetEnvAttr 関数](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
