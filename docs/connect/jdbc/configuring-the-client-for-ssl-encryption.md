---
title: "SSL 暗号化用のクライアントの構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae34cd1f-3569-4759-80c7-7c9b33b3e9eb
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: a5c395fcd8ae12a91db5dcd7bf26f8d81589d2f6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="configuring-the-client-for-ssl-encryption"></a>SSL 暗号化のためのクライアントの構成
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]またはクライアントでは、サーバーは、正しいサーバーと、その証明書がクライアントが信頼する証明機関によって発行されたことを検証します。 サーバー証明書を検証するためには、接続時にトラスト マテリアルを指定する必要があります。 また、サーバー証明書の発行者が、クライアントによって信頼されている証明機関である必要があります。  
  
 このトピックでは、まず、クライアント コンピューターのトラスト マテリアルを提供する方法を説明します。 次に、SQL Server のインスタンスの SSL (Secure Sockets Layer) 証明書が民間の証明機関によって発行されている場合にサーバー証明書をクライアント コンピューターのトラスト ストアにインポートする方法を説明します。  
  
 サーバー証明書の検証の詳細については、サーバー SSL 証明書の検証」セクションを参照してください。[について SSL サポート](../../connect/jdbc/understanding-ssl-support.md)です。  
  
## <a name="configuring-the-client-trust-store"></a>クライアントのトラスト ストアの構成  
 サーバー証明書を検証する必要がありますを使用するか、接続時にトラスト マテリアルを指定する必要があります**trustStore**と**trustStorePassword**接続のプロパティに明示的に、または基になる Java 仮想マシン (JVM) の既定のトラスト ストアを暗黙的に使用します。 設定する方法について、 **trustStore**と**trustStorePassword** 、接続文字列のプロパティを参照してください[SSL 暗号化を使用した接続](../../connect/jdbc/connecting-with-ssl-encryption.md)です。  
  
 場合、 **trustStore**プロパティが未定義または null に設定を[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]は基になる JVM のセキュリティ プロバイダー Java Secure Socket Extension (sunjsse を信頼) に依存します。 によって提供既定 TrustManager、これは、トラスト ストアで提供されるトラスト マテリアルに対して SQL Server によって返される X.509 証明書の検証に使用します。  
  
 TrustManager は、次の検索順序内での既定の trustStore の検索を試みます。  
  
-   "Javax.net.ssl.trustStore"システム プロパティが定義されている場合、TrustManager は、そのシステム プロパティによって指定されたファイル名を使用して、既定の trustStore ファイルを見つけようと試みます。  
  
-   "Javax.net.ssl.trustStore"システム プロパティが指定されていない場合、ファイル"\<java ホーム >/ライブラリ/セキュリティ/jssecacerts"が存在する場合、そのファイルを使用します。  
  
-   場合、ファイル"\<java ホーム >/ライブラリ/セキュリティ/cacerts"が存在する場合、そのファイルを使用します。  
  
 詳細については、Sun Microsystems の Web サイトで SunX509 TrustManager Interface についてのドキュメントを参照してください。  
  
 Java ランタイム環境では、次のようにしてシステム プロパティ trustStore および trustStorePassword を設定できます。  
  
```  
java -Djavax.net.ssl.trustStore=C:\MyCertificates\storeName  
java -Djavax.net.ssl.trustStorePassword=storePassword  
```  
  
 この場合、この JVM 上で実行されるすべてのアプリケーションが既定でこれらの設定を使用します。 アプリケーションの既定の設定をオーバーライドするために設定する必要があります、 **trustStore**と**trustStorePassword**接続文字列にするか、適切な接続のプロパティset アクセス操作子メソッド、 [SQLServerDataSource](../../connect/jdbc/reference/sqlserverdatasource-class.md)クラスです。  
  
 さらに、構成し、既定のトラスト ストア ファイルなどの管理"\<java ホーム >/ライブラリ/セキュリティ/jssecacerts"と"\<java ホーム >/ライブラリ/セキュリティ/cacerts"です。 そのためには、JRE (Java ランタイム環境) と共にインストールされる JAVA "keytool" ユーティリティを使用します。 "keytool" ユーティリティの詳細については、Sun Microsystems の Web サイトで keytool についてのドキュメントを参照してください。  
  
### <a name="importing-the-server-certificate-to-trust-store"></a>トラスト ストアへのサーバー証明書のインポート  
 サーバーは、SSL ハンドシェイクの際にクライアントに公開キー証明書を送信します。 公開キー証明書の発行者は証明機関 (CA) と呼ばれます。 クライアントは、その証明機関が信頼されている証明機関であることを確認する必要があります。 この確認は、信頼されている CA の公開キーを事前に把握しておくことによって行われます。 通常、JVM では、一連の信頼されている証明機関があらかじめ定義されています。  
  
 SQL Server のインスタンスの SSL 証明書が私的な証明機関によって発行されている場合は、クライアント コンピューターのトラスト ストアの信頼された証明書の一覧にその証明機関の証明書を追加する必要があります。  
  
 そのためには、JRE (Java ランタイム環境) と共にインストールされる JAVA"keytool"ユーティリティを使用します。 次のコマンド プロンプトは、"keytool" ユーティリティを使用してファイルから証明書をインポートする方法を示しています。  
  
```  
keytool -import -v -trustcacerts -alias myServer -file caCert.cer -keystore truststore.ks  
```  
  
 この例では、"caCert.cer" というファイルが証明書ファイルとして使用されています。 この証明書ファイルをサーバーから入手する必要があります。 次の手順は、サーバー証明書をファイルにエクスポートする方法を示しています。  
  
1.  [スタート] ボタンをクリックし、[ファイル名を指定して実行] をクリックして「MMC」と入力します  (MMC は Microsoft 管理コンソールの略称です)。  
  
2.  MMC で、[証明書] を開きます。  
  
3.  [個人用] を展開し、[証明書] を展開します。  
  
4.  サーバー証明書を右クリックし、[すべてのタスク] をポイントして、[エクスポート] をクリックします。  
  
5.  証明書のエクスポート ウィザードの [ようこそ] ダイアログ ボックスで、[次へ] をクリックして次のページに進みます。  
  
6.  [いいえ、秘密キーをエクスポートしません] が選択されていることを確認して、[次へ] をクリックします。  
  
7.  [DER encoded binary X.509 (.CER)] または [Base-64 encoded X.509 (.CER)] が選択されていることを確認して、[次へ] をクリックします。  
  
8.  エクスポート ファイルの名前を入力します。  
  
9. [次へ] をクリックし、[完了] をクリックすると、証明書がエクスポートされます。  
  
## <a name="see-also"></a>参照  
 [SSL 暗号化を使用します。](../../connect/jdbc/using-ssl-encryption.md)   
 [JDBC ドライバー アプリケーションをセキュリティで保護します。](../../connect/jdbc/securing-jdbc-driver-applications.md)  
  
  

