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
- SQLGetStmtAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetStmtAttr
helpviewer_keywords:
- SQLGetStmtAttr function [ODBC]
ms.assetid: e321d460-e997-4527-aee6-207cf5a498e9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89e7c75b412a6358806017102915989a8370dd43
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303306"
---
# <a name="sqlgetstmtattr-function"></a>SQLGetStmtAttr 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **ステートメント**属性の現在の設定値を返します。  
  
> [!NOTE]  
>  ドライバー マネージャーは、ODBC 3 のときにこの関数をマップする方法の詳細について。*x*アプリケーションは ODBC 2 で動作しています。*x*ドライバについては、「[アプリケーションの下位互換性のための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLGetStmtAttr(  
     SQLHSTMT        StatementHandle,  
     SQLINTEGER      Attribute,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *ステートメントハンドル*  
 [入力]ステートメント ハンドル。  
  
 *属性*  
 [入力]取得する属性。  
  
 *ValuePtr*  
 [出力]*Attribute*で指定された属性の値を返すバッファーへのポインター。  
  
 *ValuePtr*が NULL の場合 *、StringLengthPtr*は*ValuePtr*が指すバッファに返されるバイトの総数 (文字データの NULL 終端文字を除く) を返します。  
  
 *BufferLength*  
 [入力]*属性*が ODBC で定義された属性で *、ValuePtr*が文字列またはバイナリ バッファを指している場合、この引数は\* *ValuePtr*の長さになります。 *属性*が ODBC で定義された属性\*で *、ValuePtr*が整数の場合、*バッファー長*は無視されます。 * \*ValuePtr*に返される値が Unicode 文字列の場合 **(SQLGetStmtAttrW**を呼び出すとき)、BufferLength 引数は偶数でなければなりません。 *BufferLength*  
  
 *属性*がドライバー定義の属性である場合、アプリケーションは *、BufferLength*引数を設定することによってドライバー マネージャーに属性の性質を示します。 *バッファー長*には、次の値を指定できます。  
  
-   * \*ValuePtr*が文字列へのポインタである場合 *、BufferLength*は文字列またはSQL_NTSの長さです。  
  
-   * \*ValuePtr*がバイナリ バッファへのポインタである場合、アプリケーションは*bufferLength*に SQL_LEN_BINARY_ATTR(*長さ*) マクロの結果を格納します。 この場合は、負の値を*BufferLength*に配置します。  
  
-   * \*ValuePtr*が文字列またはバイナリ文字列以外の値へのポインターである場合 *、BufferLength*には値がSQL_IS_POINTER。  
  
-   * \*ValuePtr*に固定長データ型が含まれている場合 *、BufferLength*は、必要に応じてSQL_IS_INTEGERまたはSQL_IS_UINTEGERです。  
  
 *文字列を長くします。*  
 [出力]ValuePtr で返されるバイトの総数 (NULL 終端文字を除く) を返すバッファーへのポインター。 * \** *ValuePtr*が null ポインターの場合、長さは返されません。 属性値が文字列で、返されるバイト数が*BufferLength*以上の場合*\*、ValuePtr*のデータは*BufferLength*から null 終端文字の長さを引いた値に切り捨てられ、ドライバーによって NULL で終了します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetStmtAttr**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときに、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLGetStmtAttr**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストでそれぞれについて説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|* \*ValuePtr*に返されたデータは *、BufferLength*から NULL 終端文字の長さを引いた値に切り捨てられました。 切り捨てられていない文字列値の長さは、 **StringLengthPtr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|24000|カーソル状態が無効|引数*Attribute*がSQL_ATTR_ROW_NUMBERされ、カーソルがオープンされていないか、カーソルが結果セットの開始前または結果セットの終了後に位置付けされています。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 引数*MessageText*で**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を説明します。|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM)*ステートメント ハンドル*に関連付けられている接続ハンドルに対して非同期に実行される関数が呼び出されました。 この非同期関数は **、SQLGetStmtAttr**関数が呼び出されたときに実行されていました。<br /><br /> (DM) 非同期に実行される関数が呼び出されました、 *StatementHandle、* この関数が呼び出されたときに実行されています。<br /><br /> (DM)**ステートメント***ハンドル*に対**して**呼び**出され**、SQL_NEED_DATA返されました。 **SQLBulkOperations** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY090|無効な文字列またはバッファ長|*(DM) \*ValuePtr*は文字列であり、BufferLength はゼロより小さく、SQL_NTSと等しくありません。|  
|HY092|属性/オプション識別子が無効です|引数*Attribute*に指定された値は、ドライバーでサポートされている ODBC のバージョンに対して無効です。|  
|HY109|カーソル位置が無効です|*Attribute*引数がSQL_ATTR_ROW_NUMBERされ、行が削除されたか、またはフェッチできませんでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|引数*Attribute*に指定された値は、ドライバーでサポートされている ODBC のバージョンの有効な ODBC ステートメント属性でしたが、ドライバーでサポートされていませんでした。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*ステートメント ハンドル*に対応するドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 ステートメント属性の一般情報については、[ステートメント属性](../../../odbc/reference/develop-app/statement-attributes.md)を参照してください。  
  
 **呼**び出しは*\*、ValuePtr*に*属性*で指定されたステートメント属性の値を返します。 この値は、SQLULEN 値または NULL で終わる文字ストリングのいずれかです。 値が SQLULEN 値の場合、一部のドライバーは、バッファーの下位 32 ビットまたは 16 ビットのみを書き込み、上位ビットを変更しないままにします。 したがって、アプリケーションは SQLULEN のバッファーを使用し、この関数を呼び出す前に値を 0 に初期化する必要があります。 また、*バッファー長*と*文字列の長さの引数*は使用されません。 値が null で終わる文字列の場合、アプリケーションは *、その*文字列の最大長を指定、 BufferLength引数、ドライバー*\*は、StringLengthPtr*バッファー内のその文字列の長さを返します。  
  
 **SQLGetStmtAttr**を呼び出すアプリケーションが ODBC 2 で動作することを許可します。*x*ドライバー、**への**呼び出しは、ドライバー マネージャーで**SQLGetStmt オプション**にマップされます。  
  
 次のステートメント属性は読み取り専用であるため **、SQLGetStmtAttr**で取得できますが **、SQLSetStmtAttr**では設定できません。  
  
-   SQL_ATTR_IMP_PARAM_DESC  
  
-   SQL_ATTR_IMP_ROW_DESC  
  
-   SQL_ATTR_ROW_NUMBER  
  
 設定および取得できる属性の一覧については、 [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|接続属性の設定を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|ステートメント属性の設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
