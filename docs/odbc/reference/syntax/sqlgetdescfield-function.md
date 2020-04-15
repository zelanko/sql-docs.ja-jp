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
- SQLGetDescField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDescField
helpviewer_keywords:
- SQLGetDescField function [ODBC]
ms.assetid: f09ff660-1e4a-4370-be85-90d4da0487d3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 89972d7f36b436868cc8e243b03827f095b90492
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285477"
---
# <a name="sqlgetdescfield-function"></a>SQLGetDescField 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **記述子**レコードの単一フィールドの現在の設定値または値を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLGetDescField(  
     SQLHDESC        DescriptorHandle,  
     SQLSMALLINT     RecNumber,  
     SQLSMALLINT     FieldIdentifier,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *DescriptorHandle*  
 [入力]記述子ハンドル。  
  
 *RecNumber*  
 [入力]アプリケーションが情報を探す記述子レコードを示します。 記述子レコードには 0 から番号が付けられ、レコード番号 0 はブックマーク・レコードになります。 *引数が*ヘッダー フィールドを示す場合 *、RecNumber*は無視されます。 *RecNumber*がSQL_DESC_COUNT以下であるが、行に列またはパラメーターのデータが含まれていない場合 **、SQLGetDescField**の呼び出しはフィールドの既定値を返します。 (詳細については[、SQLSetDesc フィールド](../../../odbc/reference/syntax/sqlsetdescfield-function.md)の「記述子フィールドの初期化」を参照してください。  
  
 *FieldIdentifier*  
 [入力]値を返す記述子のフィールドを示します。 詳細については、 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)の「*フィールド識別子*の引数」を参照してください。  
  
 *ValuePtr*  
 [出力]記述子情報を返すバッファーへのポインター。 データ型は *、 FieldIdentifier*の値によって異なります。  
  
 *ValuePtr*が整数型の場合、一部のドライバーは、バッファーの下位 32 ビットまたは 16 ビットのみを書き込み、高い順序のビットを変更せずに残す場合があるため、アプリケーションは SQLULEN のバッファーを使用し、この関数を呼び出す前に値を 0 に初期化する必要があります。  
  
 *ValuePtr*が NULL の場合 *、StringLengthPtr*は*ValuePtr*が指すバッファに返されるバイトの総数 (文字データの NULL 終端文字を除く) を返します。  
  
 *BufferLength*  
 [入力]*フィールド識別子*が ODBC で定義されたフィールド*で、ValuePtr*が文字列またはバイナリ バッファを指している場合、この引数は\* *ValuePtr*の長さになります。 *フィールド識別子*が ODBC で定義されたフィールド\*で *、ValuePtr*が整数の場合、*バッファー長*は無視されます。 * \*ValuePtr*の値が Unicode データ型の場合 **(SQLGetDescFieldW**を呼び出すとき)、BufferLength 引数は偶数でなければなりません。 *BufferLength*  
  
 *FieldIdentifier*がドライバー定義フィールドの場合、アプリケーションは *、BufferLength*引数を設定してドライバー マネージャーにフィールドの性質を示します。 *バッファー長*には、次の値を指定できます。  
  
-   * \*ValuePtr*が文字列へのポインタである場合 *、BufferLength*は文字列またはSQL_NTSの長さです。  
  
-   * \*ValuePtr*がバイナリ バッファへのポインタである場合、アプリケーションは*bufferLength*に SQL_LEN_BINARY_ATTR(*長さ*) マクロの結果を格納します。 この場合は、負の値を*BufferLength*に配置します。  
  
-   * \*ValuePtr*が文字列またはバイナリ文字列以外の値へのポインターである場合 *、BufferLength*には値がSQL_IS_POINTER。  
  
-   * \*ValuePtr*に固定長データ型が含まれている場合 *、BufferLength*は、必要に応じて、SQL_IS_INTEGER、SQL_IS_UINTEGER、SQL_IS_SMALLINT、またはSQL_IS_USMALLINTのいずれかになります。  
  
 *文字列を長くします。*  
 [出力]**ValuePtr*で返されるバイトの総数 (NULL 終了文字に必要なバイト数を除く) を返すバッファーへのポインター。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_NO_DATA、またはSQL_INVALID_HANDLE。  
  
 *RecNumber*が現在の記述子レコード数より大きい場合は、SQL_NO_DATAが返されます。  
  
 *SQL_NO_DATAは、DescriptorHandle*が IRD ハンドルであり、ステートメントが準備済みまたは実行済みの状態にあるが、それに関連するオープン・カーソルが存在しない場合に戻されます。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetDescField**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_STMTの*ハンドル型*と*ステートメント ハンドル*ハンドルを指定して**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLGetDescField**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|バッファー \* *ValuePtr*は記述子フィールド全体を戻すのに十分な大きさではなかったため、フィールドは切り捨てられました。 切り捨てられていない記述子フィールドの長さは、 **StringLengthPtr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07009|記述子インデックスが無効です|(DM)*引数*が 0 に等しく、SQL_ATTR_USE_BOOKMARKステートメント属性がSQL_UB_OFFされ、*引数 DescriptorHandle*が IRD ハンドルでした。 (このエラーは、記述子がステートメント・ハンドルに関連付けられている場合にのみ、明示的に割り振られる記述子に対して戻されます。<br /><br /> 引数*は*レコード フィールド *、RecNumber*引数は 0、引数*は*IPD ハンドルでした。<br /><br /> *引数が*0 未満でした。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY007|関連付けられたステートメントは準備されていません|*記述子ハンドル*は *、IRD*としてステートメント ハンドルに関連付けられており、関連付けられているステートメント ハンドルが準備または実行されていません。|  
|HY010|関数シーケンス エラー|(DM) *DescriptorHandle*は、非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていた*ステートメント ハンドル*に関連付けられていた。<br /><br /> (DM)*記述子ハンドル*は **、SQL 実行、SQLExecDirect、SQLBulkOperations** **SQLBulkOperations**、または**SQLSetPos**が呼び出され、SQL_NEED_DATA返された*ステートメント ハンドル*に関連付けられました。 **SQLExecDirect** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM)*記述子ハンドル*に関連付けられている接続ハンドルに対して非同期に実行する関数が呼び出されました。 この非同期関数は **、SQLGetDescField**関数が呼び出されたときに実行されていました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY021|記述子情報の不一致|SQL_DESC_TYPEフィールドとSQL_DESC_DATETIME_INTERVAL_CODEフィールドは、有効な ODBC SQL タイプ、有効なドライバ固有の SQL タイプ (IPD の場合)、または有効な ODBC C タイプ (APK または ARD の場合) を形成しません。|  
|HY090|無効な文字列またはバッファ長|(DM) * \*ValuePtr*は文字列であり、*バッファ長*は 0 未満でした。|  
|HY091|記述子フィールド ID が無効です|*フィールド識別子*は ODBC で定義されたフィールドではなく、実装で定義された値ではありませんでした。<br /><br /> *フィールド識別子*は*記述子ハンドル*に対して定義されていませんでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*記述子ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 アプリケーションは、記述子レコードの単一フィールドの値を返すために**SQLGetDescField**を呼び出すことができます。 **SQLGetDescField**の呼び出しは、ヘッダー フィールド、レコード フィールド、およびブックマーク フィールドを含む、任意の記述子型の任意のフィールドの設定を返すことができます。 アプリケーションは**SQLGetDescField**を繰り返し呼び出すことによって、同じ記述子または異なる記述子内の複数のフィールドの設定を任意の順序で取得できます。 **SQLGetDescフィールド**は、ドライバー定義の記述子フィールドを返すために呼び出すこともできます。  
  
 パフォーマンス上の理由から、アプリケーションはステートメントを実行する前に、IRD の**SQLGetDescField**を呼び出す必要があります。  
  
 列またはパラメーター のデータの名前、データ型、およびストレージを記述する複数のフィールドの設定は、 **SQLGetDescRec**への 1 回の呼び出しでも取得できます。 **SQLGetStmtAttr**を呼び出して、ステートメント属性でもある記述子ヘッダー内の単一フィールドの設定を返すことができます。 **SQLCol 属性** **、SQLDescribeCol**、および**SQLDescribeParam**はレコードまたはブックマーク フィールドを返します。  
  
 アプリケーションが特定の記述子型に対して未定義のフィールドの値を取得するために**SQLGetDescField**を呼び出すと、関数はSQL_SUCCESSを返しますが、フィールドに対して返される値は未定義です。 たとえば、APD または ARD のSQL_DESC_NAMEまたはSQL_DESC_NULLABLEフィールドに対して**SQLGetDescField**を呼び出すと、フィールドのSQL_SUCCESSが未定義の値を返します。  
  
 アプリケーションが**SQLGetDescField**を呼び出して、特定の記述子型に対して定義されているが、まだ設定されていないフィールドの値を取得すると、関数はSQL_SUCCESS返されますが、フィールドに返される値は未定義です。 記述子フィールドの初期化とフィールドの説明の詳細については、 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)の「記述子フィールドの初期化」を参照してください。 記述子の詳細については、[記述子](../../../odbc/reference/develop-app/descriptors.md)を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|複数の記述子フィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|単一の記述子フィールドの設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|複数の記述子フィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
