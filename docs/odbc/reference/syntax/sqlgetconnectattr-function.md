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
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectAttr
helpviewer_keywords:
- SQLGetConnectAttr function [ODBC]
ms.assetid: 2cb4ffa8-19d3-4664-8c2f-6682cdcc3f33
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e6076f14ff0c33fec38b99e9c43b8a688970a7a9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285632"
---
# <a name="sqlgetconnectattr-function"></a>SQLGetConnectAttr 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **接続**属性の現在の設定を返します。  
  
> [!NOTE]
>  ODBC 3 *.x*アプリケーションが ODBC 2 *.x*ドライバーを使用して動作している場合にドライバー マネージャーがこの関数をマップする方法の詳細については、「[アプリケーションの下位互換性を確保するための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLGetConnectAttr(  
     SQLHDBC        ConnectionHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *接続ハンドル*  
 [入力] 接続ハンドル。  
  
 *属性*  
 [入力]取得する属性。  
  
 *ValuePtr*  
 [出力]*Attribute*で指定された属性の現在の値を返すメモリへのポインター。 整数型の属性の場合、一部のドライバーは、バッファーの下位 32 ビットまたは 16 ビットのみを書き込み、上位ビットを変更しないままにします。 したがって、アプリケーションは SQLULEN のバッファーを使用し、この関数を呼び出す前に値を 0 に初期化する必要があります。  
  
 *ValuePtr*が NULL の場合 *、StringLengthPtr*は*ValuePtr*が指すバッファに返されるバイトの総数 (文字データの NULL 終端文字を除く) を返します。  
  
 *BufferLength*  
 [入力]*属性*が ODBC で定義された属性で *、ValuePtr*が文字列またはバイナリ バッファを指している場合、この引数は\* *ValuePtr*の長さになります。 *属性*が ODBC で定義された属性\*で *、ValuePtr*が整数の場合、*バッファー長*は無視されます。 * \*ValuePtr*の値が Unicode 文字列の場合 **(SQLGetConnectAttrW**を呼び出すとき *)、BufferLength*引数は偶数でなければなりません。  
  
 *属性*がドライバー定義の属性である場合、アプリケーションは *、BufferLength*引数を設定することによってドライバー マネージャーに属性の性質を示します。 *バッファー長*には、次の値を指定できます。  
  
-   * \*ValuePtr*が文字列へのポインタである場合 *、BufferLength*は文字列の長さです。  
  
-   * \*ValuePtr*がバイナリ バッファへのポインタである場合、アプリケーションは SQL_LEN_BINARY_ATTR(*長さ*) マクロの結果を*BufferLength*に格納します。 この場合は、負の値を*BufferLength*に配置します。  
  
-   * \*ValuePtr*が文字列またはバイナリ文字列以外の値へのポインターである場合 *、BufferLength*はSQL_IS_POINTER値を持つ必要があります。  
  
-   * \*ValuePtr*に固定長データ型が含まれている場合 *、BufferLength*はSQL_IS_INTEGERまたはSQL_IS_UINTEGERのいずれかになります。  
  
 *文字列を長くします。*  
 [出力]\* *ValuePtr*で返されるバイトの総数 (NULL 終端文字を除く) を返すバッファーへのポインター。 \* *ValuePtr*が null ポインターの場合、長さは返されません。 属性値が文字列で、返されるバイト数が*BufferLength*から NULL 終端文字の長さを引いた値より大きい場合*\*、ValuePtr*のデータは*BufferLength*から NULL 終端文字の長さを引いた値に切り捨てられ、ドライバーによって NULL で終了します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetConnectAttr**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_DBCの*ハンドル型*と*接続ハンドル*の*ハンドル*を指定して**SQLGetDiagRec**を呼び出すことによって、診断データ構造から関連付けられた SQLSTATE 値を取得できます。 次の表は、通常**は SQLGetConnectAttr**によって返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|\* *ValuePtr*に返されたデータは *、BufferLength*から NULL 終端文字の長さを引いた値に切り捨てられました。 切り捨てられていない文字列値の長さは、 **StringLengthPtr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|08003|接続が開かない|(DM) オープン接続を必要とする*属性*値が指定されました。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 **SQLGetDiagField**の引数*MessageText*によって診断データ構造体から返されるエラー メッセージは、エラーとその原因を説明します。|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM) **SQLBrowseConnect**が*接続ハンドル*に対して呼び出され、SQL_NEED_DATA返されました。 この関数は **、SQLBrowseConnect**がSQL_SUCCESS_WITH_INFOまたはSQL_SUCCESSを返す前に呼び出されました。<br /><br /> (DM) 接続*ハンドル*に対して SQL**実行****、SQLExecDirect、** または**SQLMoreResults**が呼び出され、SQL_PARAM_DATA_AVAILABLE返されました。 この関数は、ストリームされたすべてのパラメーターに対してデータが取得される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|(DM) * \*ValuePtr*は文字列であり、BufferLength はゼロ未満でしたが、SQL_NTSと等しくありません。|  
|HY092|属性/オプション識別子が無効です|引数*Attribute*に指定された値は、ドライバーでサポートされている ODBC のバージョンに対して無効です。|  
|HY114|ドライバは接続レベルの非同期関数の実行をサポートしていません|(DM) アプリケーションは、非同期接続操作をサポートしていないドライバーのSQL_ATTR_ASYNC_DBC_FUNCTIONS_ENABLEで非同期関数の実行を有効にしようとしました。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|引数*Attribute*に指定された値は、ドライバーでサポートされている ODBC のバージョンの有効な ODBC 接続属性でしたが、ドライバーでサポートされていませんでした。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM) に対応するドライバー、*接続ハンドル*は、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 接続属性の一般情報については、[接続属性](../../../odbc/reference/develop-app/connection-attributes.md)を参照してください。  
  
 設定できる属性のリストについては、 [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)を参照してください。 *属性*が文字列を返す属性を指定する場合 *、ValuePtr*は文字列のバッファーへのポインターである必要があります。 返される文字列の最大長 (null 終端文字を含む) は*BufferLength*バイトになります。  
  
 属性によっては、アプリケーションは**SQLGetConnectAttr**を呼び出す前に接続を確立する必要はありません。 ただし、**指定**した属性が既定値を持っておらず **、SQLSetConnectAttr**への以前の呼び出しによって設定されていない場合は **、sqlGetConnectAttr**はSQL_NO_DATA返します。  
  
 *属性*がトレースまたは SQL_ATTR_ TRACEFILE SQL_ATTR_場合、*接続ハンドル*は有効である必要 SQL_INVALID_HANDLE SQL_ERROR**はありません。** *ConnectionHandle* これらの属性はすべての接続に適用されます。 別**の**引数が無効な場合は、SQL_ERRORまたはSQL_INVALID_HANDLEを返します。  
  
 アプリケーションは**SQLSetConnectAttr**を使用してステートメント属性を設定できますが、アプリケーションは**SQLGetConnectAttr**を使用してステートメント属性値を取得することはできません。ステートメント属性の設定を取得するには **、SQLGetStmtAttr**を呼び出す必要があります。  
  
 SQL_ATTR_AUTO_IPDとSQL_ATTR_CONNECTION_DEAD接続属性の両方は **、SQLGetConnectAttr**の呼び出しによって返すことができますが **、SQLSetConnectAttr**の呼び出しでは設定できません。  
  
> [!NOTE]  
>  **非同期**サポートはありません。 **SQLGetConnectAttr**を実装する場合、ドライバーは、サーバーから情報が送信または要求される回数を最小限に抑えることによって、パフォーマンスを向上させることができます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ステートメント属性の設定を返す|[SQLGetStmtAttr 関数](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|環境属性の設定|[SQLSetEnvAttr 関数](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|ステートメント属性の設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
