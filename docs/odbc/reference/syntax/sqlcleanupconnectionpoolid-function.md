---
title: SQLCleanupConnectionPoolID 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLCleanupConnectionPoolID function [ODBC]
ms.assetid: 1fc61908-e003-4587-b91a-32f40569fb99
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ee8f9b9879a3533e8196bbc89f8ae0b0a132293a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68036089"
---
# <a name="sqlcleanupconnectionpoolid-function"></a>SQLCleanupConnectionPoolID 関数
**互換性**  
 導入されたバージョン: ODBC 3.81 標準準拠: ODBC  
  
 **まとめ**  
 **SQLCleanupConnectionPoolID**は、プール ID がタイムアウトしたことをドライバーに通知します。プール ID は、そのプール ID に関連付けられているプール内のすべての接続がタイムアウトしたときにタイムアウトすることがあります。接続タイムアウトの詳細については[、「Microsoft Data Access コンポーネントでのプーリング](https://msdn.microsoft.com/library/ms810829.aspx)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```cpp
  
SQLRETURN  SQLCleanupConnectionPoolID (  
                SQLHENV    EnvironmentHandle  
                SQLPOOLID  PoolID );  
```  
  
## <a name="arguments"></a>引数  
 *EnvironmentHandle*  
 代入プールの環境ハンドル。  
  
 *PoolID*  
 代入タイムアウトしたプール ID に関連付けられているプール。  
  
## <a name="returns"></a>戻り値  
 SQL_SUCCESS、SQL_SUCCESS_WITH_INFO、SQL_ERROR、または SQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>診断  
 ドライバーマネージャーは、 **SQLCleanupConnectionPoolID**から返された診断情報を処理しません。  
  
 アプリケーションは、ドライバーによって返されたエラーメッセージを受信できません。  
  
## <a name="remarks"></a>解説  
 **SQLCleanupConnectionPoolID**はいつでも呼び出すことができますが、ドライバーマネージャーは、他のスレッドが同時に**SQLGetPoolID**を呼び出していないことを保証します。また、そのプール ID で割り当てられた接続情報トークンを使用して、他のスレッドが**SQLRateConnection**と**sqlpoolconnect**を同時に呼び出すことはありません。 そのため、ドライバーは、この機能がスレッドセーフであることを確認する必要があります。  
  
 ドライバーは、プール ID に関連付けられているリソースをクリーンアップできます。  
  
 アプリケーションでは、この関数を直接呼び出すことはできません。 ドライバー対応接続プールをサポートする ODBC ドライバーでは、この関数を実装する必要があります。  
  
 ODBC ドライバーの開発には sqlspi. h を含めます。  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ドライバー対応接続プール](../../../odbc/reference/develop-app/driver-aware-connection-pooling.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)
