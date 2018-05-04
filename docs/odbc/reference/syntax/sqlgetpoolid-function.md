---
title: SQLGetPoolID 関数 |Microsoft ドキュメント
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
- SQLGetPoolID function [ODBC]
ms.assetid: 95a8666a-ad68-4d89-bf65-f2cc797f8820
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc9cb230a0e55c216d92209e8a42d9f6759973ba
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sqlgetpoolid-function"></a>SQLGetPoolID 関数
**準拠**  
 のバージョンで導入されました ODBC 3.81 規格に準拠: ODBC。  
  
 **概要**  
 **SQLGetPoolID**プール ID を取得します  
  
## <a name="syntax"></a>構文  
  
```  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>引数  
 *hDbcInfoToken*  
 [入力]すべての接続情報を含むトークンのハンドルです。  
  
 *pPoolID*  
 [出力]プール ID は、同じ意味で使用できる接続のセットを識別するために使用する (追加のリセットを必要とする可能性があります)。  
  
## <a name="returns"></a>返します。  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE です。  
  
## <a name="diagnostics"></a>診断  
 ときに**SQLGetPoolID**返します SQL_ERROR または SQL_SUCCESS_WITH_INFO、ドライバー マネージャーを使用して、 **HandleType** SQL_HANDLE_DBC_INFO_TOKEN のおよび**処理**の*hDbcInfoToken*です。  
  
## <a name="remarks"></a>解説  
 **SQLGetPoolID**接続情報のセットが与えられてプール ID を取得するために使用 (から**SQLSetConnectAttrForDbcInfo**、 **SQLSetDriverConnectInfo**、および**SQLSetConnectInfo**)。 このプールを置き換えて使用できる接続のセットを識別する ID が使用する (追加のリセットを必要とする可能性があります)。 プール ID は、接続のグループに対して、接続プールの識別に使用されます。  
  
 ドライバーには、SQL_ERROR または SQL_INVALID_HANDLE が返されます、されるたびに、ドライバー マネージャーはアプリケーションに、エラーを返します (で[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)または[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md))。  
  
 ドライバーでは、sql_success_with_info が返されます、されるたびに、ドライバー マネージャーは、診断情報を取得から*hDbcInfoToken*でのアプリケーションに SQL_SUCCESS_WITH_INFO を返すと[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)と[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)です。  
  
 アプリケーションでは、この関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーでは、この関数を実装する必要があります。  
  
 ODBC ドライバーの開発の sqlspi.h が含まれます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
