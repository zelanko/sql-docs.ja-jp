---
title: "アプリケーションのセキュリティ |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 940879b4-aa0f-41ce-a369-6cfc0e78e01d
caps.latest.revision: 23
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e608d2181520284be87dbdaa078ff261a2a7d878
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="application-security"></a>アプリケーション セキュリティ
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  使用すると、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]をアプリケーションのセキュリティを確保する予防措置を講じることが重要です。 以下のセクションでは、アプリケーションをセキュリティ保護するために実行できる手順に関する情報を提供します。  
  
## <a name="using-java-policy-permissions"></a>Java のポリシー アクセス許可の使用  
 使用すると、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]、JDBC ドライバーで必要な Java ポリシーの必須のアクセス許可を指定することが重要です。 Java ランタイム環境 (JRE) には、スレッドがリソースにアクセスできるかどうかを判断するために実行時に使用できる拡張セキュリティ モデルがあります。 セキュリティ ポリシー ファイルでこのアクセスを制御することができます。 ポリシー ファイル自体は開発者およびコンテナーのシステム管理者が管理しますが、このトピックで挙げるアクセス許可は JDBC ドライバーの機能に影響します。  
  
 ポリシー ファイルの一般的なアクセス許可は、次のようになっています。  
  
```  
// Example policy file entry.  
grant [signedBy <signer>,] [codeBase <code source>] {  
   permission  <class>  [<name> [, <action list>]];  
};  
```  
  
 特権の付与を最小限に留めるために、次のコードベースは JDBC ドライバーのコードベースに限定してください。  
  
```  
grant codeBase "file:/install_dir/lib/-" {  
  
// Grant access to data source.  
permission java.util.PropertyPermission "java.naming.*", "read,write";  
  
// Specify which hosts can be connected to.  
permission java.net.socketPermission "host:port", "connect";  
  
// Logger permission to take advantage of logging.  
permission java.util.logging.LoggingPermission;  
  
// Grant listen/connect/accept permissions to the driver if   
// connecting to a named instance as the client driver.   
// This connects to a udp service and listens for a response.  
permission java.net.SocketPermission "*", "listen, connect, accept";   
};   
```  
  
> [!NOTE]  
>  コード "file:/install_dir/lib/-" は、JDBC ドライバーのインストール ディレクトリを指します。  
  
## <a name="protecting-server-communication"></a>サーバーとの通信の保護  
 通信するために、JDBC ドライバーを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース、インターネット プロトコル セキュリティ (IPSEC) または安全な Sockets Layer (SSL); のいずれかを使用して通信チャネルを保護することができます、または両方を使用することができます。  
  
 SSL のサポートは、IPSec 以外の追加の保護レベルを提供するために使用できます。 SSL の使用に関する詳細については、次を参照してください。 [SSL 暗号化を使用して](../../connect/jdbc/using-ssl-encryption.md)です。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバー アプリケーションをセキュリティで保護します。](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  

