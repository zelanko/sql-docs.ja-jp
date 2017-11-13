---
title: "SQLGetDescRec 関数 |Microsoft ドキュメント"
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
- SQLGetDescRec
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDescRec
helpviewer_keywords:
- SQLGetDescRec function [ODBC]
ms.assetid: 325e0907-8e87-44e8-a111-f39e636a9cbc
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c40e0e26ada07854f6772389ed09fc39e092952e
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetdescrec-function"></a>SQLGetDescRec 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLGetDescRec**現在の設定または記述子レコードの複数のフィールドの値を返します。 返されるフィールドは、名前、データ型、および列またはパラメーターのデータの格納について説明します。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 [入力]記述子ハンドルです。  
  
 *RecNumber*  
 [入力]アプリケーションが情報をシークする記述子レコードを示します。 記述子レコードは、レコード番号 0 のブックマーク レコードの中で、1 から番号が付けられます。 *RecNumber*引数は SQL_DESC_COUNT の値以下である必要があります。 場合*RecNumber* SQL_DESC_COUNT 小さいですが、行がデータの列またはパラメーターへの呼び出しを含まない**SQLGetDescRec**はフィールドの既定値を返します。 (詳細についてを参照してください「の初期化の記述子フィールド」 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md))。  
  
 *名前*  
 [出力]記述子レコードの SQL_DESC_NAME フィールドを返すバッファーへのポインター。  
  
 場合*名前*null、 *StringLengthPtr*文字 (文字データの null 終端文字を除く) の合計数を返すはまだが指すバッファーに返される使用可能な*名前*です。  
  
 *BufferLength*  
 [入力]長さ、**名前*文字バッファー。  
  
 *StringLengthPtr*  
 [出力]返される使用可能なデータの文字数を返すバッファーへのポインター、 \**名前*バッファー、null 終端文字を除外します。 文字の数がより大きいかに等しいかどうか*BufferLength*、内のデータ\**名前*に切り捨てられます*BufferLength*の長さマイナス、null 終了文字は、ドライバーが null で終わるとします。  
  
 *TypePtr*  
 [出力]記述子レコードの SQL_DESC_TYPE フィールドの値を返すバッファーへのポインター。  
  
 *SubTypePtr*  
 [出力]型を持つが SQL_DATETIME または SQL_INTERVAL のレコード、これは SQL_DESC_DATETIME_INTERVAL_CODE フィールドの値を返すバッファーへのポインターです。  
  
 *LengthPtr*  
 [出力]記述子レコードの SQL_DESC_OCTET_LENGTH フィールドの値を返すバッファーへのポインター。  
  
 *PrecisionPtr*  
 [出力]記述子レコードの SQL_DESC_PRECISION フィールドの値を返すバッファーへのポインター。  
  
 *ScalePtr*  
 [出力]記述子レコードの SQL_DESC_SCALE フィールドの値を返すバッファーへのポインター。  
  
 *NullablePtr*  
 [出力]記述子レコードの SQL_DESC_NULLABLE フィールドの値を返すバッファーへのポインター。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_NO_DATA、または SQL_INVALID_HANDLE です。  
  
 場合は、SQL_NO_DATA が返されます。 *RecNumber*記述子レコードの現在の数よりも大きいです。  
  
 場合は、SQL_NO_DATA が返されます。 *DescriptorHandle* IRD ハンドルと、ステートメントが準備または実行された状態ではそれに関連付けられた開いているカーソルはありませんでした。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetDescRec** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_DESC と*処理*の*DescriptorHandle*です。 次の表に、によって通常返される SQLSTATE 値**SQLGetDescRec**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|バッファー \**名前*を全体の記述子フィールドを返すのに十分な大きさがありません。 そのため、フィールドが切り捨てられました。 切り詰められていない記述子フィールドの長さが返される **StringLengthPtr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07009|無効な記述子のインデックス|*FieldIdentifier*引数がレコードのフィールド、 *RecNumber*引数が 0 に設定して、 *DescriptorHandle*引数は、IPD ハンドル。<br /><br /> (DM)、 *RecNumber*引数が 0 に設定された、SQL_ATTR_USE_BOOKMARKS ステートメント属性が SQL_UB_OFF に設定され、 *DescriptorHandle*引数は、IRD のハンドル。<br /><br /> *RecNumber*引数が 0 未満です。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY007|関連付けられたステートメントが準備されていません|*DescriptorHandle* IRD では、関連付けられていたし、関連付けられているステートメント ハンドルは、準備または実行された状態ではありませんでした。|  
|HY010|関数のシーケンス エラー|(DM) *DescriptorHandle*が関連付けられて、 *StatementHandle*非同期的に実行中の関数 (いないこの 1 つ) が呼び出されたおよびこの関数が呼び出されたときに実行されています。<br /><br /> (DM) *DescriptorHandle*が関連付けられて、 *StatementHandle*を**SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**が呼び出され、SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *DescriptorHandle*です。 この非同期関数ではときに実行されている**SQLGetDescRec**が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている*DescriptorHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 アプリケーションが呼び出すことができます**SQLGetDescRec**次の記述子フィールドを 1 つの列またはパラメーターの値を取得します。  
  
-   SQL_DESC_NAME  
  
-   SQL_DESC_TYPE  
  
-   SQL_DESC_DATETIME_INTERVAL_CODE (の型を持つが SQL_DATETIME または SQL_INTERVAL レコード)  
  
-   SQL_DESC_OCTET_LENGTH  
  
-   SQL_DESC_PRECISION  
  
-   SQL_DESC_SCALE  
  
-   SQL_DESC_NULLABLE  
  
 **SQLGetDescRec**ヘッダー フィールドの値を取得しません。  
  
 アプリケーションでは、null ポインターをフィールドに対応する引数を設定して、フィールドの設定値を返すを防ぐことができます。  
  
 アプリケーションを呼び出すと**SQLGetDescRec**特定記述子の型に対して定義されるフィールドの値を取得する関数は関係なく SQL_SUCCESS を返しますが、フィールドに返される値は未定義です。 たとえば、呼び出し**SQLGetDescRec** APD または ARD の SQL_DESC_NAME または SQL_DESC_NULLABLE フィールドについては、SQL_SUCCESS が未定義のフィールドの値は返します。  
  
 アプリケーションを呼び出すと**SQLGetDescRec**特定記述子の型に対して定義されているが、既定値を持たないをまだ設定されていないフィールドの値を取得する関数は関係なく SQL_SUCCESS を返しますが、返される値フィールドが定義されていません。 詳細についてを参照してください「の初期化の記述子フィールド」 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)です。  
  
 フィールドの値も取得できる個別にへの呼び出しによって**SQLGetDescField**です。 記述子のヘッダーまたはレコードのフィールドの説明は、次を参照してください。 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)です。 記述子の詳細については、次を参照してください。[記述子](../../../odbc/reference/develop-app/descriptors.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|列のバインド|[SQLBindCol 関数](../../../odbc/reference/syntax/sqlbindcol-function.md)|  
|パラメーターのバインド|[SQLBindParameter 関数](../../../odbc/reference/syntax/sqlbindparameter-function.md)|  
|記述子フィールドの取得|[SQLGetDescField 関数](../../../odbc/reference/syntax/sqlgetdescfield-function.md)|  
|複数の記述子フィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

