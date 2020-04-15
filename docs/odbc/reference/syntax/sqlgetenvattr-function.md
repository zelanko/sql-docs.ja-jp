---
title: 関数 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetEnvAttr
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLGetEnvAttr
helpviewer_keywords:
- SQLGetEnvAttr function [ODBC]
ms.assetid: 01f4590f-427a-4280-a1c3-18de9f7d86c1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 77cd24386a8eea6769aee59f3674b681c516d9ed
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285312"
---
# <a name="sqlgetenvattr-function"></a>SQLGetEnvAttr 関数
**適合 性**  
 バージョン導入: ODBC 3.0 規格準拠: ISO 92  
  
 **まとめ**  
 **環境**属性の現在の設定を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
SQLRETURN SQLGetEnvAttr(  
     SQLHENV        EnvironmentHandle,  
     SQLINTEGER     Attribute,  
     SQLPOINTER     ValuePtr,  
     SQLINTEGER     BufferLength,  
     SQLINTEGER *   StringLengthPtr);  
```  
  
## <a name="arguments"></a>引数  
 *環境ハンドル*  
 [入力]環境ハンドル。  
  
 *属性*  
 [入力]取得する属性。  
  
 *ValuePtr*  
 [出力]*Attribute*で指定された属性の現在の値を返すバッファーへのポインター。  
  
 *ValuePtr*が NULL の場合 *、StringLengthPtr*は*ValuePtr*が指すバッファに返されるバイトの総数 (文字データの NULL 終端文字を除く) を返します。  
  
 *BufferLength*  
 [入力]*ValuePtr*が文字列を指している場合、この引数は\**ValuePtr*の長さになります。 \* *ValuePtr*が整数の場合、*バッファー長*は無視されます。 * \*ValuePtr*が Unicode 文字列の場合 **(SQLGetEnvAttrW**を呼び出す場合)、BufferLength 引数は偶数でなければなりません。 *BufferLength* 属性値が文字列でない場合は *、BufferLength*は使用されません。  
  
 *文字列を長くします。*  
 [出力]ValuePtr で返されるバイトの総数 (NULL 終端文字を除く) を返すバッファーへのポインター。 * \** *ValuePtr*が null ポインターの場合、長さは返されません。 属性値が文字列で、返されるバイト数が*BufferLength*以上の場合\**、ValuePtr*のデータは*BufferLength*から null 終端文字の長さを引いた値に切り捨てられ、ドライバーによって NULL で終了します。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_NO_DATA、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetEnvAttr**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すときは、SQL_HANDLE_ENVの*ハンドル型*と*環境ハンドル*ハンドルを指定して**SQLGetDiagRec**を*Handle*呼び出すことによって、関連付けられた SQLSTATE 値を取得できます。 次の表は **、SQLGetEnvAttr**によって一般的に返される SQLSTATE 値を示し、この関数のコンテキストで各値を説明しています。「(DM)」という表記は、ドライバ マネージャによって返される SQLSTATEs の説明の前に記述されます。 特に注記がない限り、各 SQLSTATE 値に関連付けられた戻りコードはSQL_ERROR。  
  
|SQLSTATE|エラー|説明|  
|--------------|-----------|-----------------|  
|01000|一般的な警告|ドライバー固有の情報メッセージ。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|01004|文字列データ(右切り捨て)|\* *ValuePtr*に返されたデータは *、BufferLength*から NULL 終了文字を引いた値に切り捨てられました。 切り捨てられていない文字列値の長さは、 **StringLengthPtr*に返されます。 (関数はSQL_SUCCESS_WITH_INFOを返します。|  
|HY000|一般的なエラー|特定の SQLSTATE がなく、実装固有の SQLSTATE が定義されていないエラーが発生しました。 メッセージ テキスト バッファー内の**SQLGetDiagRec**によって返されるエラー メッセージは、エラーとその原因を記述します。 * \**|  
|HY001|メモリ割り当てエラー|ドライバは、関数の実行または完了をサポートするために必要なメモリを割り当てることができませんでした。|  
|HY010|関数シーケンス エラー|(DM) **SQL_ATTR_ODBC_VERSION**は**SQLSetEnvAttr**を介してまだ設定されていません。 **SQLAllocHandleStd**を使用している場合は **、SQL_ATTR_ODBC_VERSION**を明示的に設定する必要はありません。|  
|HY013|メモリ管理エラー|メモリ不足の状態が原因で、基になるメモリ オブジェクトにアクセスできなかったため、関数呼び出しを処理できませんでした。|  
|HY092|属性/オプション識別子が無効です|引数*Attribute*に指定された値は、ドライバーでサポートされている ODBC のバージョンに対して無効です。|  
|HY117|不明なトランザクション状態のため、接続が中断されました。 切断と読み取り専用の機能のみが許可されます。|(DM) 中断状態の詳細については[、SQLEndTran 関数](../../../odbc/reference/syntax/sqlendtran-function.md)を参照してください。|  
|ハイク00|オプション機能が実装されていません|引数*Attribute*に指定された値は、ドライバでサポートされている ODBC のバージョンに対する有効な ODBC 環境属性でしたが、ドライバではサポートされていませんでした。|  
|IM001|ドライバはこの機能をサポートしていません|(DM) に対応するドライバー *、 環境ハンドル*は、関数をサポートしていません。|  
  
## <a name="comments"></a>説明  
 属性の一覧については、「 [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)」を参照してください。 ドライバー固有の環境属性はありません。 *属性*が文字列を返す属性を指定する場合 *、ValuePtr*は文字列を返すバッファーへのポインターである必要があります。 null 終了バイトを含む文字列の最大長は*BufferLength*バイトになります。  
  
 **SQLGetEnvAttr**は、割り当てと環境ハンドルの解放の間の任意の時点で呼び出すことができます。 アプリケーションによって環境に対して正常に設定されたすべての環境属性は、*ハンドル型*の SQL_HANDLE_ENV を使用して**SQLFreeHandle**が*環境ハンドル*で呼び出されるまで保持されます。 ODBC 3 *.x*では、複数の環境ハンドルを同時に割り当てることができます。 ある環境の環境属性は、別の環境が割り振られた場合には影響を受けません。  
  
> [!NOTE]
>  SQL_ATTR_OUTPUT_NTS環境属性は、標準に準拠したアプリケーションでサポートされています。 **SQLGetEnvAttr**が呼び出されると、ODBC 3 *.x*ドライバー マネージャーは常にこの属性のSQL_TRUEを返します。 SQL_ATTR_OUTPUT_NTSは **、SQLSetEnvAttr**の呼び出しによってのみSQL_TRUEに設定できます。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|接続属性の設定を返す|[SQLGetConnectAttr 関数](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|  
|ステートメント属性の設定を返す|[SQLGetStmtAttr 関数](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|  
|接続属性の設定|[SQLSetConnectAttr 関数](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)|  
|環境属性の設定|[SQLSetEnvAttr 関数](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|  
|ステートメント属性の設定|[SQLSetStmtAttr 関数](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
