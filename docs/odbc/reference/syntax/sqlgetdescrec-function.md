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
- SQLGetDescRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDescRec
helpviewer_keywords:
- SQLGetDescRec function [ODBC]
ms.assetid: 325e0907-8e87-44e8-a111-f39e636a9cbc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 87d7b971b379f19f8451e924932a5e699e9b9983
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285487"
---
# <a name="sqlgetdescrec-function"></a>SQLGetDescRec 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **SQLGetDescRec は**、記述子レコードの複数のフィールドの現在の設定または値を返します。 返されるフィールドには、列またはパラメーター のデータの名前、データ型、および格納場所が記述されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLGetDescRec(  
      SQLHDESC        DescriptorHandle,  
      SQLSMALLINT     RecNumber,  
      SQLCHAR *       Name,  
      SQLSMALLINT     BufferLength,  
      SQLSMALLINT *   StringLengthPtr,  
      SQLSMALLINT *   TypePtr,  
      SQLSMALLINT *   SubTypePtr,  
      SQLLEN *        LengthPtr,  
      SQLSMALLINT *   PrecisionPtr,  
      SQLSMALLINT *   ScalePtr,  
      SQLSMALLINT *   NullablePtr);  
```  
  
## <a name="arguments"></a>引数  
 *DescriptorHandle*  
 [入力]記述子ハンドル。  
  
 *RecNumber*  
 [入力]アプリケーションが情報を探す記述子レコードを示します。 記述子レコードは 1 から番号が付けられ、レコード番号 0 はブックマーク・レコードになります。 *引数 RecNumber*は、SQL_DESC_COUNTの値以下である必要があります。 *RecNumber*がSQL_DESC_COUNT以下であるが、行に列またはパラメーターのデータが含まれていない場合 **、SQLGetDescRec**の呼び出しはフィールドの既定値を返します。 (詳細については[、SQLSetDesc フィールド](../../../odbc/reference/syntax/sqlsetdescfield-function.md)の「記述子フィールドの初期化」を参照してください。  
  
 *名前*  
 [出力]記述子レコードのSQL_DESC_NAMEフィールドを返すバッファーへのポインター。  
  
 *名前*が NULL の場合 *、StringLengthPtr*は*Name*が指すバッファで返される文字の総数 (文字データの NULL 終端文字を除く) を返します。  
  
 *BufferLength*  
 [入力]**Name*バッファの長さ (文字数)。  
  
 *文字列を長くします。*  
 [出力]\* *Name*バッファーに戻すために使用できるデータの文字数を返すバッファーへのポインター。 文字数が*BufferLength*以上の場合\**、Name*のデータは*BufferLength*から null 終端文字の長さを引いた値に切り捨てられ、ドライバーによって null で終了します。  
  
 *タイププター*  
 [出力]記述子レコードのSQL_DESC_TYPEフィールドの値を戻すバッファーへのポインター。  
  
 *サブタイププター*  
 [出力]型がSQL_DATETIMEまたはSQL_INTERVALのレコードの場合、これはSQL_DESC_DATETIME_INTERVAL_CODE フィールドの値を返すバッファーへのポインターです。  
  
 *長さPtr*  
 [出力]記述子レコードのSQL_DESC_OCTET_LENGTHフィールドの値を戻すバッファーへのポインター。  
  
 *プレシジョンプター*  
 [出力]記述子レコードのSQL_DESC_PRECISIONフィールドの値を戻すバッファーへのポインター。  
  
 *スケールプター*  
 [出力]記述子レコードのSQL_DESC_SCALEフィールドの値を戻すバッファーへのポインター。  
  
 *Null 可能なPtr*  
 [出力]記述子レコードのSQL_DESC_NULLABLEフィールドの値を戻すバッファーへのポインター。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_NO_DATA、またはSQL_INVALID_HANDLE。  
  
 *RecNumber*が現在の記述子レコード数より大きい場合は、SQL_NO_DATAが返されます。  
  
 *SQL_NO_DATAは、DescriptorHandle*が IRD ハンドルであり、ステートメントが準備済みまたは実行済みの状態にあるが、それに関連するオープン・カーソルが存在しない場合に戻されます。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetDescRec**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_DESCの*ハンドル型*と*記述子ハンドル*を持つ**SQLGetDiagRec**を呼び出すことによって、関連付けられた SQLSTATE*値を取得*できます。 次の表は **、SQLGetDescRec**によって返される SQLSTATE 値を一覧し、この関数のコンテキストで各値を説明します。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|バッファー\**名*が、記述子フィールド全体を戻すのに十分な大きさではありませんでした。 したがって、フィールドは切り捨てられました。 切り捨てられていない記述子フィールドの長さは、 **StringLengthPtr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|07009|記述子インデックスが無効です|引数*は*レコード フィールド *、RecNumber*引数は 0 に設定され、*引数は*IPD ハンドルでした。<br /><br /> (DM)*引数 RecNumber*が 0 に設定され、SQL_ATTR_USE_BOOKMARKSステートメント属性が SQL_UB_OFF に設定され、*引数 DescriptorHandle*が IRD ハンドルでした。<br /><br /> *引数が*0 未満でした。|  
|08S01|通信リンクの障害|ドライバとドライバが接続されているデータ ソースとの間の通信リンクが、関数の処理を完了する前に失敗しました。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY007|関連付けられたステートメントは準備されていません|*記述子ハンドル*は、IRD に関連付けられており、関連付けられているステートメント ハンドルが準備済みまたは実行状態ではありませんでした。|  
|HY010|関数シーケンス エラー|(DM) *DescriptorHandle*は、非同期に実行される関数 (この関数ではない) が呼び出され、この関数が呼び出されたときにまだ実行されていた*ステートメント ハンドル*に関連付けられていた。<br /><br /> (DM)*記述子ハンドル*は **、SQL 実行、SQLExecDirect、SQLBulkOperations** **SQLBulkOperations**、または**SQLSetPos**が呼び出され、SQL_NEED_DATA返された*ステートメント ハンドル*に関連付けられました。 **SQLExecDirect** この関数は、実行時のすべてのデータ パラメーターまたは列に対してデータが送信される前に呼び出されました。<br /><br /> (DM)*記述子ハンドル*に関連付けられている接続ハンドルに対して非同期に実行する関数が呼び出されました。 この非同期関数は **、SQLGetDescRec**が呼び出されたときに実行されていました。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ヒュットー1|接続のタイムアウトが期限切れになりました|データ ソースが要求に応答する前に、接続タイムアウト期間が切れました。 接続タイムアウト期間は **、SQL_ATTR_CONNECTION_TIMEOUT SQLSetConnectAttr**を使用して設定されます。|  
|IM001|ドライバはこの機能をサポートしていません|(DM)*記述子ハンドル*に関連付けられているドライバーは、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 アプリケーションは **、SQLGetDescRec**を呼び出して、単一の列またはパラメーターに対して次の記述子フィールドの値を取得できます。  
  
-   SQL_DESC_NAME  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (タイプがSQL_DATETIMEまたはSQL_INTERVALのレコードの場合)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_NULLABLE  
  
 **SQLGetDescRec**は、ヘッダー フィールドの値を取得しません。  
  
 アプリケーションは、フィールドに対応する引数を null ポインターに設定することで、フィールドの設定の戻り値を防ぐことができます。  
  
 アプリケーションが**SQLGetDescRec**を呼び出して、特定の記述子型に対して未定義のフィールドの値を取得すると、関数はSQL_SUCCESSを返しますが、そのフィールドに対して返される値は未定義です。 たとえば、APD または ARD のSQL_DESC_NAMEまたはSQL_DESC_NULLABLE フィールドに対して**SQLGetDescRec**を呼び出すと、SQL_SUCCESSが、フィールドに未定義の値が返されます。  
  
 アプリケーションが**SQLGetDescRec**を呼び出して、特定の記述子型に対して定義されているが、まだ既定値が設定されていないフィールドの値を取得すると、関数はSQL_SUCCESS返されますが、フィールドに返される値は未定義です。 詳細については、 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)の「記述子フィールドの初期化」を参照してください。  
  
 フィールドの値は、 **SQLGetDescField**の呼び出しによって個別に取得することもできます。 記述子ヘッダーまたはレコードのフィールドの説明については、 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)を参照してください。 記述子の詳細については、[記述子](../../../odbc/reference/develop-app/descriptors.md)を参照してください。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|列のバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|パラメーターのバインド|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|記述子フィールドの取得|[SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|複数の記述子フィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
