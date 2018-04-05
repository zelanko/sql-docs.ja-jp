---
title: SQLGetDescField 関数 |Microsoft ドキュメント
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
- SQLGetDescField
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetDescField
helpviewer_keywords:
- SQLGetDescField function [ODBC]
ms.assetid: f09ff660-1e4a-4370-be85-90d4da0487d3
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 091703d14644fe24bef88c939ac4b45087113bd7
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetdescfield-function"></a>SQLGetDescField 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **Sqlgetdescfield による**現在の設定または記述子レコードの 1 つのフィールドの値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
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
 [入力]記述子ハンドルです。  
  
 *RecNumber*  
 [入力]アプリケーションが情報をシークする記述子レコードを示します。 記述子レコードは、レコード番号 0 のブックマーク レコードの中で、0 から番号が付けられます。 場合、 *FieldIdentifier*引数が、ヘッダー フィールドを示す*RecNumber*は無視されます。 場合*RecNumber* SQL_DESC_COUNT 小さいですが、行がデータの列またはパラメーターへの呼び出しを含まない**SQLGetDescField**はフィールドの既定値を返します。 (詳細についてを参照してください「の初期化の記述子フィールド」 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md))。  
  
 *FieldIdentifier*  
 [入力]値が返される記述子のフィールドを示します。 詳細については、次を参照してください。、"*FieldIdentifier*引数"」の「 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)です。  
  
 *ValuePtr*  
 [出力]記述子の情報を返すバッファーへのポインター。 データ型は、の値によって異なります。 *FieldIdentifier*です。  
  
 場合*ValuePtr*整数型には、アプリケーションは SQLULEN のバッファーを使用する必要がありますドライバーによって、この関数を呼び出す前に初期化値を 0 に可能性がありますのみ作成し、下位 32 ビットまたは 16 ビット、バッファーの上位ビットのままに変更されません。  
  
 場合*ValuePtr* null、 *StringLengthPtr*バイト (文字データの null 終端文字を除く) の合計数を返すはまだが指すバッファーに返される使用可能な*ValuePtr*です。  
  
 *BufferLength*  
 [入力]場合*FieldIdentifier* ODBC で定義されたフィールドと*ValuePtr*文字の文字列またはバイナリ バッファーへのポインター、この引数の長さにする必要があります\* *ValuePtr*. 場合*FieldIdentifier* ODBC で定義されたフィールドと\* *ValuePtr*整数*BufferLength*は無視されます。 場合の値 *\*ValuePtr*が Unicode データ型 (呼び出し時に**SQLGetDescFieldW**) では、 *BufferLength*引数は偶数である必要があります。  
  
 場合*FieldIdentifier*ドライバーの定義済みのフィールドでは、アプリケーション、ドライバー マネージャーに、フィールドの性質を示す設定、 *BufferLength*引数。 *BufferLength*次の値を持つことができます。  
  
-   場合 *\*ValuePtr*文字の文字列へのポインターが*BufferLength* SQL_NTS または文字列の長さです。  
  
-   場合 *\*ValuePtr*アプリケーションが、SQL_LEN_BINARY_ATTR の結果を配置し、バイナリのバッファーへのポインターは、(*長さ*) マクロで*BufferLength*です。 これにより、配置に負の値*BufferLength*です。  
  
-   場合 *\*ValuePtr*文字の文字列またはバイナリ文字列以外の値へのポインターが*BufferLength* SQL_IS_POINTER 値でなければなりません。  
  
-   場合 *\*ValuePtr*はし、固定長のデータ型を含む*BufferLength*は必要に応じて SQL_IS_INTEGER、SQL_IS_UINTEGER、SQL_IS_SMALLINT、または SQL_IS_USMALLINT のいずれか。  
  
 *StringLengthPtr*  
 [出力]合計バイト数 (null 終端文字のために必要なバイト数を除く) を返すバッファーへのポインターで返される使用可能な **ValuePtr*です。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、SQL_NO_DATA、または SQL_INVALID_HANDLE です。  
  
 場合は、SQL_NO_DATA が返されます。 *RecNumber*記述子レコードの現在の数よりも大きいです。  
  
 場合は、SQL_NO_DATA が返されます。 *DescriptorHandle* IRD ハンドルと、ステートメントが準備または実行された状態ではそれに関連付けられた開いているカーソルはありませんでした。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetDescField** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType*のSQL_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLGetDescField**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|バッファー \* *ValuePtr*全体の記述子フィールドを返すフィールドが切り捨てられましたため大きさがありません。 切り詰められていない記述子フィールドの長さが返される **StringLengthPtr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|07009|無効な記述子のインデックス|(DM)、 *RecNumber*引数が 0 に等しい、SQL_ATTR_USE_BOOKMARK ステートメント属性が SQL_UB_OFF、および*DescriptorHandle*引数は、IRD のハンドル。 (このエラーに対応する明示的に割り当てられた記述子記述子は、ステートメント ハンドルに関連付けられている場合にのみ。)<br /><br /> *FieldIdentifier*引数がレコードのフィールド、 *RecNumber*引数が 0 の場合、 *DescriptorHandle*引数は、IPD ハンドル。<br /><br /> *RecNumber*引数が 0 未満です。|  
|08S01|通信リンクが失敗しました|関数は完了しました処理する前に、ドライバーとドライバーが接続されているデータ ソース間の通信リンクが失敗しました。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY007|関連付けられたステートメントが準備されていません|*DescriptorHandle*が関連付けられて、 *StatementHandle* IRD と関連付けられているステートメント ハンドルがないされて準備または実行されます。|  
|HY010|関数のシーケンス エラー|(DM) *DescriptorHandle*が関連付けられて、 *StatementHandle*非同期的に実行中の関数 (いないこの 1 つ) が呼び出されたおよびこの関数が呼び出されたときに実行されています。<br /><br /> (DM) *DescriptorHandle*が関連付けられて、 *StatementHandle*を**SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**が呼び出され、SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。<br /><br /> (DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *DescriptorHandle*です。 この非同期関数がまだ実行したときに、 **SQLGetDescField**関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY021|不整合な記述子情報|SQL_DESC_TYPE と SQL_DESC_DATETIME_INTERVAL_CODE フィールドが形成されていません、有効な ODBC SQL 型、有効な個々 のドライバーの SQL 型 (Ipd)、または有効な ODBC C 型 (Apd の標準)。|  
|HY090|文字列またはバッファーの長さが無効です。|(DM)  *\*ValuePtr*された文字の文字列と*BufferLength*が 0 未満です。|  
|HY091|無効な記述子フィールド識別子|*FieldIdentifier*でした、ODBC で定義されたフィールドと、実装定義の値ではありません。<br /><br /> *FieldIdentifier*に対して定義されていないが、 *DescriptorHandle*です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に、ドライバーが関連付けられている、 *DescriptorHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 アプリケーションが呼び出すことができます**SQLGetDescField**記述子レコードの 1 つのフィールドの値を取得します。 呼び出し**SQLGetDescField**ヘッダー フィールド、レコードのフィールド、およびブックマークのフィールドを含む、記述子の型のいずれかのフィールドの設定値を返すことができます。 アプリケーションは、何度も呼び出すことで、同じまたは異なる記述子に、任意の順序で複数のフィールドの設定を取得する**SQLGetDescField**です。 **Sqlgetdescfield による**ドライバーの定義済みの記述子フィールドを返すには呼び出すこともできます。  
  
 パフォーマンス上の理由から、アプリケーションを呼び出す必要がありますいない**SQLGetDescField**ステートメントを実行する前に、IRD のです。  
  
 名前、データ型、および列またはパラメーターのデータの記憶域を記述する複数のフィールドの設定は、1 回の呼び出しでも取得できます**SQLGetDescRec**です。 **SQLGetStmtAttr**ステートメント属性になっている記述子のヘッダーにフィールドを 1 つの設定値を返すを呼び出すことができます。 **SQLColAttribute**、 **SQLDescribeCol**、および**SQLDescribeParam**ブックマークのレコードまたはフィールドを取得します。  
  
 アプリケーションを呼び出すと**SQLGetDescField**特定記述子の型に対して定義されるフィールドの値を取得する関数は関係なく SQL_SUCCESS を返しますが、フィールドに返される値は未定義です。 たとえば、呼び出し**SQLGetDescField** APD または ARD の SQL_DESC_NAME または SQL_DESC_NULLABLE フィールドについては、SQL_SUCCESS が未定義のフィールドの値は返します。  
  
 アプリケーションを呼び出すと**SQLGetDescField**特定記述子の型に対して定義されているが、既定値を持たないをまだ設定されていないフィールドの値を取得する、関数を返しますが、SQL_SUCCESS、値が返されますフィールドに対して定義されていません。 記述子フィールドとフィールドの説明の初期化の詳細についてを参照してください「の初期化の記述子フィールド」 [SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)です。 記述子の詳細については、次を参照してください。[記述子](../../../odbc/reference/develop-app/descriptors.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|複数の記述子フィールドの取得|[SQLGetDescRec 関数](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|  
|1 つの記述子フィールドの設定|[SQLSetDescField 関数](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|  
|複数の記述子フィールドの設定|[SQLSetDescRec 関数](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
