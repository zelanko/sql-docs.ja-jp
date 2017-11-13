---
title: "SQLGetEnvAttr 関数 |Microsoft ドキュメント"
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
- SQLGetEnvAttr
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetEnvAttr
helpviewer_keywords:
- SQLGetEnvAttr function [ODBC]
ms.assetid: 01f4590f-427a-4280-a1c3-18de9f7d86c1
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a7e353d41c1065f8d65a70c6633901ef22547a61
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlgetenvattr-function"></a>SQLGetEnvAttr 関数
**準拠**  
 バージョンで導入されました ODBC 3.0 Standards 準拠: ISO 92。  
  
 **概要**  
 **SQLGetEnvAttr**環境属性の現在の設定を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
SQLRETURN SQLGetEnvAttr(  
     SQLHENV        EnvironmentHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *EnvironmentHandle*  
 [入力]環境ハンドルです。  
  
 *属性*  
 [入力]取得する属性。  
  
 *ValuePtr*  
 [出力]指定された属性の現在の値を返すバッファーへのポインター*属性*です。  
  
 場合*ValuePtr* null、 *StringLengthPtr*バイト (文字データの null 終端文字を除く) の合計数を返すはまだが指すバッファーに返される使用可能な*ValuePtr*です。  
  
 *BufferLength*  
 [入力]場合*ValuePtr*文字の文字列へのポインター、この引数の長さにする必要があります\* *ValuePtr*です。 場合\* *ValuePtr*整数*BufferLength*は無視されます。 場合 *\*ValuePtr* Unicode 文字列です (呼び出し時に**SQLGetEnvAttrW**) では、 *BufferLength*引数は偶数である必要があります。 属性値が文字の文字列ではない場合*BufferLength*は使用されません。  
  
 *StringLengthPtr*  
 [出力]合計バイト数 (null 終了文字を除く) を返すバッファーへのポインターで返される使用可能な *\*ValuePtr*です。 場合*ValuePtr* null ポインターでは、長さは返されません。 属性値、文字の文字列であり、使用できるバイト数を返すより大きいかに等しい場合*BufferLength*、内のデータ\* *ValuePtr*に切り捨てられます*BufferLength* null 終端文字の長さマイナスはドライバーによって null で終わるとします。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetEnvAttr** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられた SQLSTATE 値を返しますを呼び出すことによって取得できます**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_ENV と*処理*の*EnvironmentHandle*です。 次の表に、一般的にによって返される SQLSTATE 値**SQLGetEnvAttr**とコンテキストでこの関数のいずれかを説明します。 表記"(DM)"の前に、ドライバー マネージャーによって返される SQLSTATEs の説明。 SQLSTATE 値ごとに関連付けられている戻り値のコードは、特に明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|Description|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|返されるデータ\* *ValuePtr*に切り詰められました*BufferLength*マイナス、null 終端文字です。 切り詰められていない文字列値の長さが返される **StringLengthPtr*です。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|存在しなかった固有の SQLSTATE となる実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリ割り当てエラー|ドライバーは、実行や、関数の終了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM)**また**経由で設定されていない**SQLSetEnvAttr**です。 設定する必要はありません**また**を使用している場合は明示的に**SQLAllocHandleStd**です。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、可能性のあるメモリ不足の状況が原因であるために、関数呼び出しを処理できませんでした。|  
|HY092|無効な属性またはオプション識別子|引数が指定された値*属性*が ODBC ドライバーでサポートされているのバージョンは無効です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)です。|  
|HYC00|省略可能な機能が実装されていません|引数が指定された値*属性*ODBC 環境の有効な属性が ODBC のバージョンは、ドライバーでサポートされていますが、ドライバーによってサポートされていませんでした。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に対応するドライバー、 *EnvironmentHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 属性の一覧は、次を参照してください。 [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)です。 ドライバー固有の環境属性はありません。 場合*属性*、文字列を返す属性を指定します*ValuePtr*を文字列を返すバッファーへのポインターにする必要があります。 Null 終了バイトを含む文字列の最大長*BufferLength*バイトです。  
  
 **SQLGetEnvAttr**割り当てと開放環境ハンドルの間でいつでも呼び出すことができます。 環境のアプリケーションによって設定が正常にすべての環境属性がまで保持**SQLFreeHandle**で呼び出されると、 *EnvironmentHandle*で、 *HandleType*SQL_HANDLE_ENV のです。 ODBC 3 に、1 つ以上の環境ハンドルを同時に割り当てることができる*.x*です。 別の環境が割り当てられたときに、1 つの環境の環境属性は影響はありません。  
  
> [!NOTE]  
>  SQL_ATTR_OUTPUT_NTS 環境属性は、標準に準拠したアプリケーションでサポートされています。 ときに**SQLGetEnvAttr**が呼び出されると、ODBC 3*.x*ドライバー マネージャーは常にこの属性を SQL_TRUE を返します。 呼び出しによってのみ SQL_ATTR_OUTPUT_NTS SQL_TRUE に設定できます**SQLSetEnvAttr**です。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|接続属性の設定値を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|ステートメント属性の設定値を返す|[SQLGetStmtAttr 関数](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|環境属性を設定|[SQLSetEnvAttr 関数](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)

