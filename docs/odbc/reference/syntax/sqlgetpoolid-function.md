---
title: 関数を取得する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetPoolID function [ODBC]
ms.assetid: 95a8666a-ad68-4d89-bf65-f2cc797f8820
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 32cc973f4dab5bde7bcedade0365d233987dda72
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303319"
---
# <a name="sqlgetpoolid-function"></a>SQLGetPoolID 関数
**適合 性**  
 バージョン導入: ODBC 3.81 標準準拠: ODBC  
  
 **まとめ**  
 **プール ID**を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
  
SQLRETURN  SQLGetPoolID (  
                SQLHDBC_INFO_TOKEN    hDbcInfoToken,  
                POOLID *              pPoolID );  
```  
  
## <a name="arguments"></a>引数  
 *トークン*  
 [入力]すべての接続情報を含むトークン ハンドル。  
  
 *を使用します。*  
 [出力]プール ID は、交換可能に使用できる接続のセットを識別するために使用されます (場合によっては、追加のリセットが必要)。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、またはSQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 **SQLGetPoolID**がSQL_ERRORまたはSQL_SUCCESS_WITH_INFOを返すとき、ドライバー マネージャーは、SQL_HANDLE_DBC_INFO_TOKENの**ハンドル型**と*hDbcInfoToken*の**ハンドル**を使用します。  
  
## <a name="remarks"></a>解説  
 **一**連の接続情報を指定してプール ID を取得するために使用されます (**一**連の接続情報から、SQL セット ドライバー接続情報 、および**SQLSetConnectInfo**から)。 **SQLSetConnectInfo** このプール ID は、交換可能に使用できる接続のセットを識別するために使用されます (場合によっては、追加のリセットが必要です)。 プール ID は、その接続グループの接続プールを識別するために使用されます。  
  
 ドライバーがSQL_ERRORまたはSQL_INVALID_HANDLEを返すたびに、ドライバー マネージャーはエラーをアプリケーションに返します[(SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)または[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)で)。  
  
 ドライバーがSQL_SUCCESS_WITH_INFOを返すたびに、ドライバー マネージャーは*hDbcInfoToken*から診断情報を取得し[、SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)と[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)でアプリケーションにSQL_SUCCESS_WITH_INFOを返します。  
  
 アプリケーションはこの関数を直接呼び出さないでください。 ドライバー対応接続プールをサポートする ODBC ドライバーは、この関数を実装する必要があります。  
  
 ODBC ドライバ開発用に sqlspi.h を含めます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
