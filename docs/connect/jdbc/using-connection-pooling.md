---
title: 接続プールを使用して |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 699d4e8a-34bf-4c60-b0d5-4a10dad6084a
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: af73ee2a721ccd8da4a77b7d294460cf1d4da75b
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="using-connection-pooling"></a>接続プールの使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]使用できるように、Java Platform, Enterprise Edition (Java EE) の接続プールします。 JDBC ドライバーは、ミドルウェア ベンダーが提供し JDBC 3.0 に準拠する接続プールの実装に参加できるように、JDBC 3.0 に必要なインターフェイスを実装しています。 Java EE アプリケーション サーバーのようなミドルウェアの多くは、準拠した接続プール機能を備えています。 JDBC ドライバーは、これらの環境でプールされた接続に参加します。  
  
> [!NOTE]  
>  JDBC ドライバーは Java EE 接続プールをサポートしますが、独自のプール実装は提供しません。 このドライバーでは、接続の管理をサードパーティの Java アプリケーション サーバーに依存しています。  
  
## <a name="remarks"></a>解説  
 接続プールを実装するためのクラスは次のとおりです。  
  
|クラス|実装|Description|  
|-----------|----------------|-----------------|  
|com.microsoft.sqlserver.jdbc です。 SQLServerXADataSource|javax.sql.ConnectionPoolDataSource および javax.sql.XADataSource|使用することをお勧め、 [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md)クラス、Java EE サーバーはすべての必要がある、すべての JDBC 3.0 プールおよび XA インターフェイスを実装するためです。|  
|com.microsoft.sqlserver.jdbc です。 SQLServerConnectionPoolDataSource|javax.sql.ConnectionPoolDataSource|このクラスは、Java EE アプリケーション サーバーが物理接続による接続プールを作成するための接続ファクトリです。 Java EE ベンダーの構成は、javax.sql.ConnectionPoolDataSource を実装するクラスを必要とする場合とクラス名を指定します。 [SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md)です。 一般的に使用することをお勧め、 [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md)のためと、プールの両方を実装し、XA インターフェイス、クラスの代わりに、多くの Java EE サーバー構成で検証されているとします。|  
  
 JDBC のアプリケーション コードでは、プールの利点を最大限に活かすため、常に接続を明示的に閉じる必要があります。 アプリケーションが接続を明示的に閉じると、プール実装は直ちに接続を再利用することができます。 接続が開いたままの場合、他のアプリケーションはその接続を再利用することができません。 アプリケーションを使用して、`finally`コンストラクトを例外が発生した場合でも、プールされた接続が閉じられたことを確認してください。  
  
> [!NOTE]  
>  現在 JDBC ドライバーは、接続をプールに返すとき sp_reset_connection ストアド プロシージャを呼び出しません。 ただし、接続を元の状態に戻すときは、サードパーティの Java アプリケーション サーバーに依存します。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによる SQL Server への接続](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
  
  
