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
- SQLSetDriverConnectInfo function [ODBC]
ms.assetid: bfd4dfc2-fbca-4ef3-81e5-2706f2389256
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10336475e39598161126c13771ad822de0d5f7d8
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298803"
---
# <a name="sqlsetdriverconnectinfo-function"></a>SQLSetDriverConnectInfo 関数
**適合 性**  
 バージョン導入: ODBC 3.81 標準準拠: ODBC  
  
 **まとめ**  
 **アプリケーションの SQLDriverConnect**呼び出しの接続文字列を接続情報トークンに設定するために使用されます**SQLDriverConnect**。  
  
## <a name="syntax"></a>構文  
  
```cpp
  
SQLRETURN SQLSetDriverConnectInfo(  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              InConnectionString,  
                SQLSMALLINT          StringLength1 );  
```  
  
## <a name="arguments"></a>引数  
 *トークンハンドル*  
 [入力]トークン ハンドル。  
  
 *インコネクションストリング*  
 [入力]完全な接続文字列[(SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)の「コメント」の構文を参照)、部分的な接続文字列、または空の文字列。  
  
 *文字列長1*  
 [入力]文字列が Unicode の場合は文字で表された **InConnectionString*の長さ、または文字列が ANSI または DBCS の場合はバイト数。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 入力検証エラーに関連する[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)と同じですが、ドライバー マネージャーは、SQL_HANDLE_DBC_INFO_TOKENの**ハンドルの種類**と*hDbcInfoToken*の**ハンドル**を使用する点を除きます。  
  
## <a name="remarks"></a>解説  
 ドライバーがSQL_ERRORまたはSQL_INVALID_HANDLEを返すたびに、ドライバー マネージャーはエラーをアプリケーションに返します[(SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)または[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)で)。  
  
 ドライバーがSQL_SUCCESS_WITH_INFOを返すたびに、ドライバー マネージャーは*hDbcInfoToken*から診断情報を取得し[、SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)と[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)でアプリケーションにSQL_SUCCESS_WITH_INFOを返します。  
  
 アプリケーションはこの関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーは、この関数を実装する必要があります。  
  
 ODBC ドライバ開発用に sqlspi.h を含めます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
