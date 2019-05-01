---
title: SQLGetEnvAttr 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 70fe1ca95f5160f801eaf3528e625116705eda6d
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63258841"
---
# <a name="sqlgetenvattr-function"></a>SQLGetEnvAttr 関数
**準拠**  
 バージョンが導入されました。ODBC 3.0 規格に準拠します。ISO 92  
  
 **まとめ**  
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
 [入力]環境ハンドル。  
  
 *属性*  
 [入力]取得する属性。  
  
 *ValuePtr*  
 [出力]指定された属性の現在の値を返すバッファーへのポインター*属性*します。  
  
 場合*ValuePtr*が null の場合、 *StringLengthPtr*バイト (文字データの null 終端文字を除く) の合計数を返すはまだが指すバッファーに返される使用可能な*ValuePtr*します。  
  
 *BufferLength*  
 [入力]場合*ValuePtr*文字の文字列をポイントして、この引数の長さである必要があります\* *ValuePtr*します。 場合\* *ValuePtr*整数*BufferLength*は無視されます。 場合 *\*ValuePtr*は Unicode 文字列です (呼び出し時に**SQLGetEnvAttrW**)、 *BufferLength*引数は偶数である必要があります。 属性値が文字の文字列でない場合*BufferLength*は使用されません。  
  
 *StringLengthPtr*  
 [出力](Null 終了文字を除く) バイトの合計数を返すバッファーへのポインターで返される使用可能な *\*ValuePtr*します。 場合*ValuePtr* null ポインターの場合は、長さは返されません。 属性値が文字の文字列と、返される使用可能なバイト数がより大きいまたは等しい場合*BufferLength*、内のデータ\* *ValuePtr*に切り捨てられます*BufferLength* null 終了文字の長さマイナスはドライバーによって null で終わるとします。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_ERROR、または SQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetEnvAttr** SQL_ERROR または SQL_SUCCESS_WITH_INFO、関連付けられている SQLSTATE 値を返しますを呼び出すことによって取得できる**SQLGetDiagRec**で、 *HandleType* sql _ のHANDLE_ENV と*処理*の*EnvironmentHandle*します。 次の表に、一般的にによって返される SQLSTATE 値**SQLGetEnvAttr** ; この関数のコンテキストでそれぞれについて説明しますと表記"(DM)"の前にドライバー マネージャーによって返されるについての説明。 SQLSTATE 値ごとに関連付けられているリターン コードは明記しない限り、SQL_ERROR です。  
  
|SQLSTATE|[エラー]|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージです。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|01004|文字列データで、右側が切り捨てられました|返されるデータ\* *ValuePtr*に切り詰められました*BufferLength*マイナス、null 終了文字。 切り詰められていない文字列値の長さが返される **StringLengthPtr*します。 (関数は、SQL_SUCCESS_WITH_INFO を返します)。|  
|HY000|一般的なエラー|これがなかった固有の SQLSTATE とする実装に固有の SQLSTATE が定義されていない、エラーが発生しました。 によって返されるエラー メッセージ**SQLGetDiagRec**で、  *\*MessageText*バッファーは、エラーとその原因について説明します。|  
|HY001|メモリの割り当てエラー|ドライバーは、実行または関数の完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数のシーケンス エラー|(DM) **SQL_ATTR_ODBC_VERSION**経由で設定されていない**SQLSetEnvAttr**します。 設定する必要はありません**SQL_ATTR_ODBC_VERSION**を使用する場合は明示的に**SQLAllocHandleStd**します。|  
|HY013|メモリ管理エラー|基になるメモリ オブジェクトにアクセスできませんでした、場合によってメモリ不足が原因であるために、関数呼び出しを処理できませんでした。|  
|HY092|無効な属性またはオプション識別子|引数が指定された値*属性*ODBC ドライバーでサポートされているのバージョンには無効です。|  
|HY117|不明なトランザクションの状態のため、接続が中断されます。 のみを切断して、読み取り専用の関数が許可されます。|(DM) 中断状態の詳細については、次を参照してください。 [SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)します。|  
|HYC00|省略可能な機能が実装されていません|引数が指定された値*属性*有効な ODBC 環境属性が ODBC のバージョンのドライバーでサポートされているが、ドライバーによってサポートされていませんでした。|  
|IM001|ドライバーでは、この関数はサポートされていません|(DM) に対応するドライバー、 *EnvironmentHandle*関数をサポートしていません。|  
  
## <a name="comments"></a>コメント  
 属性の一覧は、次を参照してください。 [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)します。 ドライバー固有の環境属性はありません。 場合*属性*、文字列を返す属性を指定します*ValuePtr*を文字列を返すバッファーへのポインターである必要があります。 Null 終了のバイトを含む文字列の最大長*BufferLength*バイト。  
  
 **SQLGetEnvAttr**割り当てと、環境ハンドルの解放の間でいつでも呼び出すことができます。 環境のアプリケーションの設定が正常にすべての環境属性がされるまで保持**SQLFreeHandle**で呼び出される、 *EnvironmentHandle*で、 *HandleType*sql_handle_env としての。 ODBC 3 では、複数の環境ハンドルを同時に割り当てることが *.x*します。 別の環境が割り当てられているときに、1 つの環境の環境属性は影響しません。  
  
> [!NOTE]
>  SQL_ATTR_OUTPUT_NTS 環境属性は、標準に準拠したアプリケーションでサポートされています。 ときに**SQLGetEnvAttr**を呼び出すと、ODBC 3 *.x*ドライバー マネージャーは常にこの属性を SQL_TRUE を返します。 呼び出しでのみ SQL_ATTR_OUTPUT_NTS が SQL_TRUE に設定することができます**SQLSetEnvAttr**します。  
  
## <a name="related-functions"></a>関連する関数  
  
|詳細|参照先|  
|---------------------------|---------|  
|接続属性の設定を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|ステートメント属性の設定を返す|[SQLGetStmtAttr 関数](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|環境属性を設定|[SQLSetEnvAttr 関数](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|ステートメント属性を設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
