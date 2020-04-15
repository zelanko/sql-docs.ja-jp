---
title: ODBC サービス プロバイダ インターフェイス (SPI) のリファレンス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cdeffb4a-f344-4abe-97f3-be2ede1c8e59
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e9739abd13bf2c4bed1b1b3a31c18c683594705a
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298910"
---
# <a name="odbc-service-provider-interface-spi-reference"></a>ODBC サービス プロバイダー インターフェイス (SPI) リファレンス
従来、ODBC はアプリケーション プログラミング インターフェイス (API) を定義しました。 API の関数はアプリケーションから呼び出すことができますし、ドライバー マネージャーとドライバーの両方の内部で実装する必要があります。  
  
 ドライバー対応接続プール機能が追加された ODBC では、サービス プロバイダー インターフェイス (SPI) が導入されています。 SPI の関数は、ドライバー マネージャーとドライバーの間の通信に使用されます。 SPI 関数はドライバによって実装されます。ドライバー マネージャーは、アプリケーションに SPI 関数を公開しません。 アプリケーションは、これらの関数を直接呼び出さないでください。  
  
 ODBC ドライバ開発用に sqlspi.h を含めます。  
  
 このセクションでは、以下のトピックについて説明します。  
  
-   [接続プール ID](../../../odbc/reference/syntax/sqlcleanupconnectionpoolid-function.md)  
  
-   [を使用します。](../../../odbc/reference/syntax/sqlgetpoolid-function.md)  
  
-   [コネクト](../../../odbc/reference/syntax/sqlpoolconnect-function.md)  
  
-   [接続](../../../odbc/reference/syntax/sqlrateconnection-function.md)  
  
-   [を使用します。](../../../odbc/reference/syntax/sqlsetconnectattrfordbcinfo-function.md)  
  
-   [接続情報](../../../odbc/reference/syntax/sqlsetconnectinfo-function.md)  
  
-   [接続情報](../../../odbc/reference/syntax/installation-and-configuration-wwi-oltp.md)  
  
## <a name="see-also"></a>参照  
 [ODBC ドライバーの開発](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)   
 [ODBC ドライバーでの接続プール認識の開発](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md)   
 [ドライバー マネージャーの接続プール](../../../odbc/reference/develop-app/driver-manager-connection-pooling.md)
