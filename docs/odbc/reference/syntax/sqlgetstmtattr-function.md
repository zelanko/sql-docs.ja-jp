---
title: SQLGetStmtAttr 関数 |Microsoft ドキュメント
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
- SQLGetStmtAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetStmtAttr
helpviewer_keywords:
- SQLGetStmtAttr function [ODBC]
ms.assetid: e321d460-e997-4527-aee6-207cf5a498e9
caps.latest.revision: 25
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 10ef63cf77fc4668d9f9f80daaff8ab483d1876b
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="sqlgetstmtattr-function"></a>SQLGetStmtAttr 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLGetStmtAttr**ステートメント属性の現在の設定を返します。  
  
> [!NOTE]  
>  どのようなドライバー マネージャーの詳細と ODBC 3 には、この関数にマップします。*x* ODBC 2 を利用するアプリケーション*。x*ドライバーを参照してください[アプリケーションの旧バージョンと互換性を保つのための置換関数のマッピング](../../../odbc/reference/develop-app/mapping-replacement-functions-for-backward-compatibility-of-applications.md)です。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLGetStmtAttr(  
     SQLHSTMT        StatementHandle,  
     SQLINTEGER      Attribute,  
     SQLPOINTER      ValuePtr,  
     SQLINTEGER      BufferLength,  
     SQLINTEGER *    StringLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *StatementHandle*  
 [入力]ステートメント ハンドルです。  
  
 *属性*  
 [入力]取得する属性。  
  
 *ValuePtr*  
 [出力]指定された属性の値を返すバッファーへのポインター*属性*です。  
  
 場合*ValuePtr* null、 *StringLengthPtr*バイト (文字データの null 終端文字を除く) の合計数を返すはまだが指すバッファーに返される使用可能な*ValuePtr*です。  
  
 *BufferLength*  
 [入力]場合*属性*ODBC で定義された属性と*ValuePtr*文字の文字列またはバイナリ バッファーへのポインター、この引数の長さにする必要があります\* *ValuePtr*. 場合*属性*ODBC で定義された属性と\* *ValuePtr*整数*BufferLength*は無視されます。 値が返される場合 *\*ValuePtr* Unicode 文字列です (呼び出し時に**SQLGetStmtAttrW**) では、 *BufferLength*引数は偶数である必要があります。  
  
 場合*属性*ドライバーの定義済みの属性は、アプリケーション、ドライバー マネージャーに属性の性質を示す設定、 *BufferLength*引数。 *BufferLength*次の値を持つことができます。  
  
-   場合 *\*ValuePtr*文字の文字列へのポインターが*BufferLength* SQL_NTS または文字列の長さです。  
  
-   場合 *\*ValuePtr*アプリケーションが、SQL_LEN_BINARY_ATTR の結果を配置し、バイナリのバッファーへのポインターは、(*長さ*) マクロで*BufferLength*です。 これにより、配置に負の値*BufferLength*です。  
  
-   場合 *\*ValuePtr*文字の文字列またはバイナリ文字列以外の値へのポインターが*BufferLength* SQL_IS_POINTER 値でなければなりません。  
  
-   場合 *\*ValuePtr*はし、固定長のデータ型を含む*BufferLength*は SQL_IS_INTEGER か SQL_IS_UINTEGER、必要に応じて。  
  
 *StringLengthPtr*  
 [出力]合計バイト数 (null 終了文字を除く) を返すバッファーへのポインターで返される使用可能な *\*ValuePtr*です。 場合*ValuePtr* null ポインターでは、長さは返されません。 属性値が文字の文字列と、使用できるバイト数を返すより大きいまたは等しい*BufferLength*、内のデータ *\*ValuePtr* に切り捨てられます*BufferLength* null 終端文字の長さマイナスはドライバーによって null で終わるとします。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetStmtAttr** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得される可能性があります**SQLGetDiagRec**で、 *HandleType* SQL の_HANDLE_STMT と*処理*の*StatementHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLGetStmtAttr**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|返されるデータ *\*ValuePtr*に切り詰められました*BufferLength* null 終端文字の長さマイナスです。 切り詰められていない文字列値の長さが返される **StringLengthPtr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|24000|カーソル状態が無効|引数*属性*SQL_ATTR_ROW_NUMBER が、カーソルが開いて、いなかったやまたは結果セットの終了後に結果セットの開始前に、カーソルが置かれています。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**引数で*MessageText*エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM)、非同期的に実行されている関数が呼び出されたため、接続ハンドルに関連付けられている、 *StatementHandle*です。 この非同期関数がまだ実行したときに、 **SQLGetStmtAttr**関数が呼び出されました。<br /><br /> (DM) の非同期的に実行中の関数が呼び出された、 *StatementHandle*この関数が呼び出されたときに実行されているとします。<br /><br /> (DM) **SQLExecute**、 **SQLExecDirect**、 **SQLBulkOperations**、または**SQLSetPos**で呼び出され、 *StatementHandle* SQL_NEED_DATA が返されます。 すべての実行時データ パラメーターまたは列に対してデータが送信される前に、この関数が呼び出されました。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY090|文字列またはバッファーの長さが無効です。|*(DM) \*ValuePtr*文字の文字列、および BufferLength は SQL_NTS に等しくないが、0 より小さいをでした。|  
|HY092|無効な属性またはオプション識別子|引数が指定された値*属性*が ODBC ドライバーでサポートされているのバージョンは無効です。|  
|HY109|無効なカーソルの位置|*属性*引数 SQL_ATTR_ROW_NUMBER れ、行が削除されたかをフェッチできませんでした。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|引数が指定された値*属性*有効な ODBC ステートメント属性が ODBC のバージョンは、ドライバーでサポートされていますが、ドライバーによってサポートされていませんでした。|  
|HYT01|接続がタイムアウトしました|データ ソースが要求に応答する前に、接続タイムアウト期間が期限切れです。 によって、接続タイムアウト期間が設定されている**SQLSetConnectAttr**、SQL_ATTR_CONNECTION_TIMEOUT です。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に対応するドライバー、 *StatementHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 ステートメント属性に関する概要については、次を参照してください。[ステートメント属性](../../../odbc/reference/develop-app/statement-attributes.md)です。  
  
 呼び出し**SQLGetStmtAttr**で返します *\*ValuePtr*で指定されたステートメント属性の値*属性*です。 SQLULEN 値または null で終わる文字の文字列、その値を指定するか、できます。 SQLULEN 値の場合、一部のドライバーのみ書き込むことが、下位 32 ビットまたは 16 ビットのバッファーとのままにして、上位ビットがそのままです。 そのため、アプリケーションは SQLULEN のバッファーを使用し、この関数を呼び出す前に、値を 0 を初期化する必要があります。 また、 *BufferLength*と*StringLengthPtr*引数は使用されません。 アプリケーションがその文字列内で最大長を指定する値が null で終わる文字列の場合は、 *BufferLength*引数、およびドライバーでは、その文字列の長さを返します、  *\*StringLengthPtr*バッファー。  
  
 呼び出すアプリケーションを許可する**SQLGetStmtAttr** ODBC 2 を使用する*。x*ドライバーへの呼び出し**SQLGetStmtAttr**をドライバー マネージャーではマップ**SQLGetStmtOption**です。  
  
 次のステートメント属性は読み取り専用を取得できるように**SQLGetStmtAttr**では設定されませんが、 **SQLSetStmtAttr**:  
  
-   SQL_ATTR_IMP_PARAM_DESC  
  
-   SQL_ATTR_IMP_ROW_DESC  
  
-   SQL_ATTR_ROW_NUMBER  
  
 設定および取得が可能な属性の一覧は、次を参照してください。 [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|接続属性の設定値を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
