---
title: "SQLPoolConnect 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLPoolConnect function [ODBC]
ms.assetid: 41322737-890d-4a81-aed2-06cc3d546962
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8c0a82eecc733223442bc1cebf6da111397bca99
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlpoolconnect-function"></a>SQLPoolConnect 関数
**準拠**  
 バージョンで導入されました ODBC 3.8 Standards 準拠: ODBC。  
  
 **概要**  
 **SQLPoolConnect**プール内の接続を再利用できるない場合は、新しい接続を作成するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
SQLRETURN  SQLPoolConnect(  
                SQLHDBC              hDbc,  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              wszOutConnectString,  
                SQLSMALLINT          cchConnectStringBuffer,  
                SQLSMALLINT *        cchConnectStringLen );  
```  
  
## <a name="arguments"></a>引数  
 *hDbc*  
 [入力]接続のハンドルです。  
  
 *hDbcInfoToken*  
 [入力]新しいアプリケーション接続要求のトークンのハンドルです。  
  
 *wszOutConnectString*  
 [出力]完全な接続文字列のバッファーへのポインター。 ターゲット データ ソースへの接続に成功したときに、このバッファーには、完全な接続文字列が含まれています。 アプリケーションは、このバッファーの少なくとも 1,024 文字を割り当てる必要があります。  
  
 場合*wszOutConnectString* null、 *cchConnectStringLen*はまだ文字 (文字データの null 終端文字を除く) の合計数を返しますで返される使用可能なバッファーを指す*wszOutConnectString*です。  
  
 *cchConnectStringBuffer*  
 [入力]長さ、**wszOutConnectString*文字バッファー。  
  
 *cchConnectStringLen*  
 [出力]文字 (null 終了文字を除く) の合計数を返すバッファーへのポインターで返される使用可能な\* *wszOutConnectString*です。 返される文字数がより大きいかに等しい場合*cchConnectStringBuffer*、内の接続文字列を完了した\* *wszOutConnectString* に切り捨てられます*cchConnectStringBuffer* null 終端文字の長さマイナスです。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ような[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)ドライバー マネージャーを使用する点を除いて、任意の入力の検証エラーを**HandleType** SQL_HANDLE_DBC_INFO_TOKEN のおよび**処理**の*hDbcInfoToken*です。  
  
## <a name="remarks"></a>解説  
 ドライバー マネージャーは、保証のハンドルを HENV 親*hDbc*と*hDbcInfoToken*は同じです。  
  
 異なり[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)、あるありません*DriverCompletion*接続情報の入力を求めるに渡す引数。 プロンプトを表示するダイアログは、プールのシナリオでは許可されていません。  
  
 アプリケーションでは、この関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーでは、この関数を実装する必要があります。  
  
 ドライバーには、SQL_ERROR または SQL_INVALID_HANDLE が返されます、されるたびに、ドライバー マネージャーはアプリケーションに、エラーを返します (で[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)または[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md))。  
  
 ドライバーでは、sql_success_with_info が返されます、されるたびに、ドライバー マネージャーは、診断情報を取得から*hDbcInfoToken*でのアプリケーションに SQL_SUCCESS_WITH_INFO を返すと[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)と[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)です。  
  
 アプリケーションを使用する場合[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)、 *wszOutConnectString* (最後の 3 つのパラメーターすべてに設定されます NULL、0、NULL) バッファーは、NULL になります。 それ以外の場合、ドライバーがアプリケーションに返されます、出力の接続文字列を返す必要があります[SQLDriverConnect 関数](../../../odbc/reference/syntax/sqldriverconnect-function.md)呼び出します。  
  
 ODBC ドライバーの開発の sqlspi.h が含まれます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
