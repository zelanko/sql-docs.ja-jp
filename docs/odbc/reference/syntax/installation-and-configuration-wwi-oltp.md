---
title: SQLSetDriverConnectInfo 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLSetDriverConnectInfo function [ODBC]
ms.assetid: bfd4dfc2-fbca-4ef3-81e5-2706f2389256
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e6869e1f4be42bfc88b3fb1f38cb605c0ad5a20
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlsetdriverconnectinfo-function"></a>SQLSetDriverConnectInfo 関数
**準拠**  
 のバージョンで導入されました ODBC 3.81 規格に準拠: ODBC。  
  
 **概要**  
 **SQLSetDriverConnectInfo**アプリケーションのためのトークンの接続情報に、接続文字列を設定に使用される**SQLDriverConnect**呼び出します。  
  
## <a name="syntax"></a>構文  
  
```  
SQLRETURN SQLSetDriverConnectInfo(  
                SQLHDBC_INFO_TOKEN   hDbcInfoToken,  
                WCHAR *              InConnectionString,  
                SQLSMALLINT          StringLength1 );  
```  
  
## <a name="arguments"></a>引数  
 *TokenHandle*  
 [入力]トークンのハンドル。  
  
 *InConnectionString*  
 [入力]完全な接続文字列 (「コメント」内の構文を参照してください[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md))、部分的な接続文字列、または空の文字列。  
  
 *StringLength1*  
 [入力]長さ **InConnectionString*、文字の文字列の場合、Unicode、またはバイトの文字列は ANSI または DBCS 場合。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 同じ[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)ドライバー マネージャーを使用する点を除いて、任意の入力の検証エラーに関連する、 **HandleType** SQL_HANDLE_DBC_INFO_TOKEN のおよび**処理**の*hDbcInfoToken*です。  
  
## <a name="remarks"></a>解説  
 ドライバーには、SQL_ERROR または SQL_INVALID_HANDLE が返されます、されるたびに、ドライバー マネージャーはアプリケーションに、エラーを返します (で[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)または[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md))。  
  
 ドライバーでは、sql_success_with_info が返されます、されるたびに、ドライバー マネージャーは、診断情報を取得から*hDbcInfoToken*でのアプリケーションに SQL_SUCCESS_WITH_INFO を返すと[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)と[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)です。  
  
 アプリケーションでは、この関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーでは、この関数を実装する必要があります。  
  
 ODBC ドライバーの開発の sqlspi.h が含まれます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
