---
title: SSL 暗号化を使用した接続 |Microsoft Docs
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ec91fa8a-ab7e-4c1e-a05a-d7951ddf33b1
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d47c4234482c879e2ee564f8035c9e2033a469f3
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 08/14/2018
ms.locfileid: "42785516"
---
# <a name="connecting-with-ssl-encryption"></a>SSL 暗号化を使用した接続
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  この記事の例では、Java アプリケーションで SSL (Secure Sockets Layer) 暗号化を使用できるようにする接続文字列プロパティの使用方法について説明します。 これらの新しい接続文字列プロパティ (**encrypt**、**trustServerCertificate**、**trustStore**、**trustStorePassword**、**hostNameInCertificate** など) の詳細については、「[接続プロパティの設定](../../connect/jdbc/setting-the-connection-properties.md)」を参照してください。  
  
 **encrypt** プロパティが **true** に設定され、**trustServerCertificate** プロパティが **true** に設定されている場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の SSL 証明書を検証しません。 これは、通常、テスト環境 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが自己署名入りの証明書しか備えていない環境など) で接続を許可する場合に必要になります。  
  
 次のコード例では、接続文字列内に **trustServerCertificate** プロパティを設定する方法を示します。  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true;trustServerCertificate=true";  
```  
  
 **encrypt** プロパティが **true** に設定され、**trustServerCertificate** プロパティが **false** に設定されている場合、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の SSL 証明書を検証しません。 サーバー証明書の検証は、SSL ハンドシェイクの一部であり、接続先のサーバーが適切なサーバーであることを保証します。 サーバー証明書を検証するには、**trustStore** 接続プロパティと **trustStorePassword** 接続プロパティを明示的に使用するか、または基になる Java 仮想マシン (JVM) のトラスト ストアを暗黙的に使用して、接続時にトラスト マテリアルを提供する必要があります。  
  
 **trustStore** プロパティでは、証明書の trustStore ファイルへのパス (ファイル名を含む) を指定します。このファイルには、クライアントが信頼する証明書の一覧が含まれています。 **trustStorePassword** プロパティでは、trustStore データの整合性の確認に使用するパスワードを指定します。 JVM の既定のトラスト ストアの使用に関する詳細については、次を参照してください。、 [SSL 暗号化用のクライアントを構成する](../../connect/jdbc/configuring-the-client-for-ssl-encryption.md)します。  
  
 次のコード例では、接続文字列内に **trustStore** プロパティと **trustStorePassword** プロパティを設定する方法を示します。  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword";  
```  
  
 JDBC Driver には、サーバーのホスト名を指定するための追加プロパティである **hostNameInCertificate** が用意されています。 このプロパティの値は、証明書の subject プロパティと一致する必要があります。  
  
 次のコード例では、接続文字列内で **hostNameInCertificate** プロパティを使用する方法を示します。  
  
```java
String connectionUrl =   
    "jdbc:sqlserver://localhost:1433;" +  
     "databaseName=AdventureWorks;integratedSecurity=true;" +  
     "encrypt=true; trustServerCertificate=false;" +  
     "trustStore=storeName;trustStorePassword=storePassword" +  
     "hostNameInCertificate=hostName";  
```  
  
> [!NOTE]  
>  または、[SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md) クラスによって提供される適切な **setter** メソッドを使用して、接続プロパティの値を設定することもできます。  
  
 **encrypt** プロパティが **true** に設定され、**trustServerCertificate** プロパティが **false** に設定され、接続文字列のサーバー名が [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SSL 証明書のサーバー名に一致しない場合は、次のエラーが発行されます: ドライバーは SSL (Secure Sockets Layer) 暗号化を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への安全な接続を確立できませんでした。 エラー: "java.security.cert.CertificateException: SSL (Secure Sockets Layer) の初期化中に、証明書内のサーバー名の検証が失敗しました。"  
  
## <a name="see-also"></a>参照  
 [SSL 暗号化の使用](../../connect/jdbc/using-ssl-encryption.md)   
 [JDBC ドライバー アプリケーションのセキュリティ保護](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  
