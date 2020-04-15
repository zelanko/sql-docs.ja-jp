---
title: 機能を接続する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPoolConnect function [ODBC]
ms.assetid: 41322737-890d-4a81-aed2-06cc3d546962
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5045fe47683529f858b01e69f6af696e2821ca4c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306903"
---
# <a name="sqlpoolconnect-function"></a>SQLPoolConnect 関数
**適合 性**  
 バージョン導入: ODBC 3.8 標準準拠: ODBC  
  
 **まとめ**  
 プール内の接続を再利用できない場合は **、SQLPoolConnect**を使用して新しい接続を作成します。  
  
## <a name="syntax"></a>構文  
  
```cpp
  
SQLRETURN  SQLPoolConnect(  
                SQLHDBC              hDbc,  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              wszOutConnectString,  
                SQLSMALLINT          cchConnectStringBuffer,  
                SQLSMALLINT *        cchConnectStringLen );  
```  
  
## <a name="arguments"></a>引数  
 *Hdbc*  
 [入力]接続ハンドル。  
  
 *トークン*  
 [入力]新しいアプリケーション接続要求のトークン ハンドル。  
  
 *文字列*  
 [出力]完了した接続文字列のバッファーへのポインター。 ターゲット データ ソースへの接続が成功すると、このバッファーには、完了した接続文字列が格納されます。 アプリケーションでは、このバッファーに少なくとも 1,024 文字を割り当てる必要があります。  
  
 *wszOutConnectString*が NULL の場合 *、cchConnectStringLen*は *、wszOutConnectString*が指すバッファで返す可能性がある文字の総数 (文字データの NULL 終端文字を除く) を返します。  
  
 *をクリックします。*  
 [入力]文字で表した **wszOutConnect 文字列*バッファーの長さ。  
  
 *クチコネクトストリングレン*  
 [出力]\* *wszOutConnectString*で返される文字の合計数 (NULL 終端文字を除く) を返すバッファーへのポインター。 返される文字の数が*cchConnectStringBuffer*以上の場合\**、wszOutConnectString*内の完了した接続文字列は *、cchConnectStringBuffer*から null 終了文字の長さを引いた長さに切り捨てられます。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 入力検証エラーの[SQLDriverConnect と](../../../odbc/reference/syntax/sqldriverconnect-function.md)同様に、ドライバー マネージャーがSQL_HANDLE_DBC_INFO_TOKENの**ハンドル型**と*hDbcInfoToken*の**ハンドル**を使用する点を除いて。  
  
## <a name="remarks"></a>解説  
 ドライバー マネージャーは *、hDbc*と*hDbcInfoToken*の親 HENV ハンドルが同じであることを保証します。  
  
 [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)とは異なり、接続情報を入力するようにユーザーに要求する*DriverCompletion*引数はありません。 プールのシナリオでは、プロンプト ダイアログは許可されません。  
  
 アプリケーションはこの関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーは、この関数を実装する必要があります。  
  
 ドライバーがSQL_ERRORまたはSQL_INVALID_HANDLEを返すたびに、ドライバー マネージャーはエラーをアプリケーションに返します[(SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)または[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)で)。  
  
 ドライバーがSQL_SUCCESS_WITH_INFOを返すたびに、ドライバー マネージャーは*hDbcInfoToken*から診断情報を取得し[、SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)と[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)でアプリケーションにSQL_SUCCESS_WITH_INFOを返します。  
  
 アプリケーションが[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)を使用する場合 *、wszOutConnect 文字列*は NULL バッファになります (最後の 3 つのパラメータはすべて NULL、0、NULL に設定されます)。 それ以外の場合、ドライバーは、アプリケーションの[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)呼び出しに返される出力接続文字列を返す必要があります。  
  
 ODBC ドライバ開発用に sqlspi.h を含めます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
