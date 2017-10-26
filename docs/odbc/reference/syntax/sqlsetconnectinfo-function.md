---
title: "SQLSetConnectInfo 関数 |Microsoft ドキュメント"
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
- SQLSetConnectInfo function [ODBC]
ms.assetid: 0782a1c3-c5d1-499b-a8ba-134162db9990
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6e4c974a8cf4bb46f955ec8f2bae0a766f58f692
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectinfo-function"></a>SQLSetConnectInfo 関数
**準拠**  
 のバージョンで導入されました ODBC 3.81 規格に準拠: ODBC。  
  
 **概要**  
 **SQLSetConnectInfo**アプリケーションのためのトークンの接続情報に、データ ソース、ユーザー ID とパスワードを設定に使用される[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)呼び出します。  
  
## <a name="syntax"></a>構文  
  
```  
SQLRETURN  SQLSetConnectInfo(  
                SQLHDBC_INFO_TOKEN   TokenHandle,  
                WCHAR *              ServerName,  
                SQLSMALLINT          NameLength1,  
                WCHAR *              UserName,  
                SQLSMALLINT          NameLength2,  
                WCHAR *              Authentication,  
                SQLSMALLINT          NameLength3 );  
```  
  
## <a name="arguments"></a>引数  
 *TokenHandle*  
 [入力]トークンのハンドル。  
  
 *ServerName*  
 [入力]データ ソースの名前。 データをプログラムと同じコンピューター上またはネットワーク上のどこか別のコンピューター上にあることがあります。 アプリケーションがデータ ソースを選択する方法については、次を参照してください。[データ ソースまたはドライバーを選択する](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)です。  
  
 *NameLength1*  
 [入力]長さ **ServerName*文字です。  
  
 *UserName*  
 [入力]ユーザーの識別子です。  
  
 *NameLength2*  
 [入力]長さ **UserName*文字です。  
  
 *[認証]*  
 [入力]認証の文字列 (通常はパスワード)。  
  
 *NameLength3*  
 [入力]長さ **認証*文字です。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 同じ[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)のドライバー マネージャーを使用する点を除いて、検証エラーを入力、 **HandleType** SQL_HANDLE_DBC_INFO_TOKEN のおよび**処理**の*hDbcInfoToken*です。  
  
## <a name="remarks"></a>解説  
 ドライバーには、SQL_ERROR または SQL_INVALID_HANDLE が返されます、されるたびに、ドライバー マネージャーはアプリケーションに、エラーを返します (で[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)または[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md))。  
  
 ドライバーでは、sql_success_with_info が返されます、されるたびに、ドライバー マネージャーは、診断情報を取得から*hDbcInfoToken*でのアプリケーションに SQL_SUCCESS_WITH_INFO を返すと[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)と[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)です。  
  
 アプリケーションでは、この関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーでは、この関数を実装する必要があります。  
  
 ODBC ドライバーの開発の sqlspi.h が含まれます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)

