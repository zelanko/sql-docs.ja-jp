---
title: ODBC サービス プロバイダー インターフェイス (SPI) リファレンス |Microsoft ドキュメント
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
ms.topic: article
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 1bd481d7344345578f830374f7049a917e60eb68
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-service-provider-interface-spi-reference"></a>ODBC サービス プロバイダー インターフェイス (SPI) のリファレンス
従来、ODBC では、アプリケーション プログラミング インターフェイス (API) が定義されています。 アプリケーションによって API の関数を呼び出すことができ、ドライバー マネージャーとドライバーの両方の内部実装すべきです。  
  
 ドライバー対応接続プール機能の追加により、ODBC では、サービス プロバイダー インターフェイス (SPI) が導入されています。 SPI 内の関数は、ドライバー マネージャーとドライバーの間の通信に使用されます。 SPI 関数は、ドライバーによって実装されます。ドライバー マネージャーは、アプリケーションに SPI 関数を公開しません。 アプリケーションでは、これらの関数を直接呼び出さないでください。  
  
 ODBC ドライバーの開発の sqlspi.h が含まれます。  
  
 このセクションには、次のトピックが含まれています。  
  
-   [SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [SQLGetPoolID](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [SQLPoolConnect](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [SQLRateConnection](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [SQLSetConnectInfo](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [SQLSetDriverConnectInfo](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ODBC ドライバー対応接続プールの開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [ドライバー マネージャーの接続プール](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
