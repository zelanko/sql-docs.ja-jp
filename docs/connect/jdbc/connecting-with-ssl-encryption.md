---
title: "SSL 暗号化を使用した接続 |Microsoft ドキュメント"
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
ms.assetid: ec91fa8a-ab7e-4c1e-a05a-d7951ddf33b1
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4fdb56715660ca32f8c41ff6356be3ec3c6a64af
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="connecting-with-ssl-encryption"></a>SSL 暗号化を使用した接続
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  このトピックの例では、Java アプリケーションで SSL (Secure Sockets Layer) 暗号化を使用できるようにする接続文字列プロパティの使用方法について説明します。 これらの新しい接続の詳細については、文字列などのプロパティ**暗号化**、 **trustServerCertificate**、 **trustStore**、 **trustStorePassword**、および**hostNameInCertificate**を参照してください[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)です。  
  
 ときに、**暗号化**プロパティに設定されている**true**と**trustServerCertificate**プロパティに設定されている**true**、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]検証されません、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL 証明書。 これは通常、場所など、テスト環境での接続を許可する必要、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]インスタンスには、自己署名証明書のみです。  
  
 次のコード例は、設定する方法を示します、 **trustServerCertificate**接続文字列内のプロパティ。  
  
```  
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true;trustServerCertificate=true";  
```  
  
 ときに、**暗号化**プロパティに設定されている**true**と**trustServerCertificate**プロパティに設定されている**false**、 [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]検証は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL 証明書。 サーバー証明書の検証は、SSL ハンドシェイクの一部であり、接続先のサーバーが適切なサーバーであることを保証します。 サーバー証明書を検証するために使用するか、接続時にトラスト マテリアルを指定する必要があります**trustStore**と**trustStorePassword**接続のプロパティを明示的にまたはを使用して基になる Java 仮想マシン (JVM) の既定の信頼は、暗黙的に格納されます。  
  
 **TrustStore**プロパティは、クライアントが信頼する証明書のリストを含む証明書の trustStore ファイルへ (ファイル名を含む) のパスを指定します。 **TrustStorePassword**プロパティは trustStore データの整合性を確認するためのパスワードを指定します。 JVM の既定のトラスト ストアを使用する方法については、次を参照してください。、 [SSL 暗号化用のクライアントを構成する](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md)です。  
  
 次のコード例は、設定する方法を示します、 **trustStore**と**trustStorePassword**接続文字列のプロパティ。  
  
```  
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword";  
```  
  
 JDBC Driver は、追加のプロパティ**hostNameInCertificate**サーバーのホストの名前を指定します。 このプロパティの値は、証明書の subject プロパティと一致する必要があります。  
  
 次のコード例を使用する方法を示しています、 **hostNameInCertificate**接続文字列内のプロパティ。  
  
```  
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword" +  
     "hostNameInCertificate=hostName";  
```  
  
> [!NOTE]  
>  適切なを使用して接続のプロパティの値を設定する代わりに、 **set アクセス操作子**によって提供されるメソッド、 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)クラスです。  
  
 場合、**暗号化**プロパティに設定されている**true**と**trustServerCertificate**プロパティに設定されている**false**場合で、サーバーの名前と、接続文字列が内のサーバー名と一致しません、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] SSL 証明書を次のエラーが発行されます: ドライバーは、安全な接続を確立できませんでした[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]安全な Sockets Layer (SSL) 暗号化を使用しています。 エラー: "java.security.cert.CertificateException: SSL (Secure Sockets Layer) の初期化中に、証明書内のサーバー名の検証が失敗しました。"  
  
## <a name="see-also"></a>参照  
 [SSL 暗号化を使用します。](../../connect/jdbc/using-ssl-encryption.md)   
 [JDBC ドライバー アプリケーションをセキュリティで保護します。](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  

