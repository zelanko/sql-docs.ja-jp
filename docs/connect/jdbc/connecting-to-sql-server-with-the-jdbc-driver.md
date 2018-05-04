---
title: JDBC ドライバーで SQL Server への接続 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 94bcfbe3-f00e-4774-bda8-bb7577518fec
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6af836edb1585a07d54fb0742b73ac10a4852d8a
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="connecting-to-sql-server-with-the-jdbc-driver"></a>JDBC ドライバーによる SQL Server への接続
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  行う最も基本的な機能の 1 つ、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]への接続を行うには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 使用するデータベースとすべてのやり取りが行われる、 [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md)オブジェクト、注目に値するほとんどすべての動作が、SQLServerConnection オブジェクトを関連 JDBC ドライバーには、このようなフラットなアーキテクチャがあるためです。  
  
 場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]はへの接続に IPv4 ではなく IPv6 を使用するかどうかを確認するために java.net.preferIPv6Addresses システム プロパティを設定、IPv6 のポートでリッスンしている、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]:  
  
```  
System.setProperty("java.net.preferIPv6Addresses", "true");  
```  
  
 このセクションのトピックを作成してへの接続を使用する方法について説明、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[接続 URL の構築](../../connect/jdbc/building-the-connection-url.md)|接続するため、接続 URL を構築する方法について説明、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 名前付きインスタンスへの接続についても説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。|  
|[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)|さまざまな接続プロパティと、利用する方法に接続する場合について説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。|  
|[データ ソースのプロパティの設定](../../connect/jdbc/setting-the-data-source-properties.md)|Java Platform, Enterprise Edition (Java EE) 環境でデータ ソースを使用する方法について説明します。|  
|[接続の操作](../../connect/jdbc/working-with-a-connection.md)|接続のインスタンスを作成するためのさまざまな方法について説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。|  
|[接続プールの使用](../../connect/jdbc/using-connection-pooling.md)|JDBC ドライバーが接続プールをサポートするしくみについて説明します。|  
|[データベース ミラーリングを使用して&#40;JDBC&#41;](../../connect/jdbc/using-database-mirroring-jdbc.md)|JDBC ドライバーがデータベース ミラーリングの使用をサポートするしくみについて説明します。|  
|[高可用性、ディザスター リカバリーのための JDBC Driver のサポート](../../connect/jdbc/jdbc-driver-support-for-high-availability-disaster-recovery.md)|AlwaysOn 可用性グループに接続するアプリケーションの開発方法について説明します。|  
|[Kerberos 統合認証による SQL Server への接続](../../connect/jdbc/using-kerberos-integrated-authentication-to-connect-to-sql-server.md)|接続するアプリケーションの Java 実装について説明、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベースの Kerberos 統合認証を使用します。|  
|[Azure SQL Database への接続](../../connect/jdbc/connecting-to-an-azure-sql-database.md)|SQL Azure 上のデータベースに対する接続の問題について説明します。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーの概要](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  
