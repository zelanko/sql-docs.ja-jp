---
title: "SSL 暗号化を使用して |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8e566243-2f93-4b21-8065-3c8336649309
caps.latest.revision: "32"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 2ca2c1c7b566b70b82a70b939c5495e76ce4612a
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="using-ssl-encryption"></a>SSL 暗号化の使用
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  インスタンス間のネットワーク間で secure Sockets Layer (SSL) 暗号化により、暗号化されたデータの送信[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]とクライアント アプリケーション。  
  
 SSL は、ネットワークやその他のインターネット通信において、重要な情報や機密情報の傍受を防ぐ安全な通信チャネルを確立するためのプロトコルです。 SSL を使用すると、クライアントとサーバーは互いの ID を認証することができます。 参加者の認証が完了すると、SSL は安全なメッセージ送信のための暗号化された接続を参加者間で提供します。  
  
 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]インフラストラクチャを有効にして、指定されたユーザーに基づいて、特定の接続の暗号化を無効にするのには、接続のプロパティと、サーバーおよびクライアント設定します。 ユーザーは、証明書ストアの場所とパスワード、証明書の検証に使用するホスト名、および通信チャネルを暗号化するタイミングを指定できます。  
  
 SSL 暗号化を有効にすると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] のインスタンスとアプリケーションの間でネットワークを経由して転送されるデータのセキュリティが強化されます。 ただし、暗号化を有効にすると、パフォーマンスが低下します。  
  
 このセクションのトピックで説明する方法、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]バージョンは、新しい接続のプロパティ、およびクライアント側でトラスト ストアを構成する方法を含む、SSL 暗号化をサポートしています。  
  
> [!NOTE]  
>  **HostNameInCertificate**接続プロパティは、SSL 証明書を検証することをお勧めします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[SSL のサポートについて](../../connect/jdbc/understanding-ssl-support.md)|について説明しますが、どのように[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]SSL 暗号化をサポートします。|  
|[SSL 暗号化を使用した接続](../../connect/jdbc/connecting-with-ssl-encryption.md)|接続する方法について説明します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]新しい SSL 固有の接続プロパティを使用してデータベース。|  
|[SSL 暗号化のためのクライアントの構成](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md)|クライアント側で既定のトラスト ストアを構成する方法と、クライアント コンピューターのトラスト ストアにプライベート証明書をインポートする方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバー アプリケーションのセキュリティ保護](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
