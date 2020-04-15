---
title: 関数を接続する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetConnectInfo function [ODBC]
ms.assetid: 0782a1c3-c5d1-499b-a8ba-134162db9990
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b575e0d09f87ad21e1190b8081b6604349a98263
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301853"
---
# <a name="sqlsetconnectinfo-function"></a>SQLSetConnectInfo 関数
**適合 性**  
 バージョン導入: ODBC 3.81 標準準拠: ODBC  
  
 **まとめ**  
 **SQLSetConnectInfo**は、アプリケーションの[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)呼び出しの接続情報トークンにデータ ソース、ユーザー ID、およびパスワードを設定するために使用されます。  
  
## <a name="syntax"></a>構文  
  
```cpp
  
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
 *トークンハンドル*  
 [入力]トークン ハンドル。  
  
 *ServerName*  
 [入力]データ ソース名。 データは、プログラムと同じコンピューター上に置くか、ネットワーク上の別のコンピューター上に配置されている可能性があります。 アプリケーションでデータ ソースを選択する方法については、「データ[ソースまたはドライバの選択](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)」を参照してください。  
  
 *NameLength1*  
 [入力]**文字でのサーバー名*の長さ。  
  
 *名*  
 [入力]ユーザー識別子。  
  
 *名前の長さ 2*  
 [入力]**文字数でのユーザー名*の長さ。  
  
 *認証*  
 [入力]認証文字列 (通常はパスワード)。  
  
 *名前の長さ 3*  
 [入力]**文字での認証*の長さ。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 入力検証エラーの[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)と同じですが、ドライバー マネージャーはハンドル**型**のSQL_HANDLE_DBC_INFO_TOKENと*hDbcInfoToken*の**ハンドル**を使用する点を除いて。  
  
## <a name="remarks"></a>解説  
 ドライバーがSQL_ERRORまたはSQL_INVALID_HANDLEを返すたびに、ドライバー マネージャーはエラーをアプリケーションに返します[(SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)または[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)で)。  
  
 ドライバーがSQL_SUCCESS_WITH_INFOを返すたびに、ドライバー マネージャーは*hDbcInfoToken*から診断情報を取得し[、SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)と[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)でアプリケーションにSQL_SUCCESS_WITH_INFOを返します。  
  
 アプリケーションはこの関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーは、この関数を実装する必要があります。  
  
 ODBC ドライバ開発用に sqlspi.h を含めます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
