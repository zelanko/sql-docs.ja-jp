---
title: SQL Server への接続 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data source names
- connection string keywords
- DSNs
ms.assetid: f95cdbce-e7c2-4e56-a9f7-8fa3a920a125
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: db4df94d04a27df5715abe4bf5e4947850c687e4
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54125842"
---
# <a name="connecting-to-sql-server"></a>SQL Server への接続
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

このトピックでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースへの接続を作成する方法について説明します。  
  
## <a name="connection-properties"></a>接続プロパティ  

参照してください[DSN と接続文字列キーワード、および属性](../../../connect/odbc/dsn-connection-string-attribute.md)のすべての接続文字列キーワードと Linux および Mac でサポートされる属性

> [!IMPORTANT]  
> データベース ミラーリングを使用する (フェールオーバー パートナーがある) データベースに接続する場合は、接続文字列にデータベース名を指定しないでください。 代わりに、**use** <_データベース名_> コマンドを送信してデータベースに接続してから、クエリを実行します。  
  
渡される値、**ドライバー**キーワードは、次のいずれかを指定できます。  
  
-   ドライバーをインストールしたときに使用した名前。

-   ドライバー ライブラリへのパス。ドライバーのインストールに使用されたテンプレート .ini ファイルで指定されています。  

DSN を作成する (必要に応じて) を作成し、ファイルを編集して **~/.odbc.ini** (`.odbc.ini` 、ホーム ディレクトリ) の現在のユーザーにのみアクセスできるユーザー DSN または`/etc/odbc.ini`システム dsn (管理のために必要な権限)。次のサンプル ファイルは、DSN に必要なエントリを示しています。  

```  
[MSSQLTest]  
Driver = ODBC Driver 13 for SQL Server  
Server = [protocol:]server[,port]  
#   
# Note:  
# Port is not a valid keyword in the odbc.ini file  
# for the Microsoft ODBC driver on Linux or macOS
#  
```  

サーバーに接続するために、必要に応じてプロトコルとポートを指定することができます。 たとえば、 **Server = tcp:**_servername_**, 12345**します。 Linux と macOS のドライバーでサポートされている唯一のプロトコルは`tcp`します。

静的ポートの名前付きインスタンスに接続するには、<b>Server=</b>*servername*,**port_number** を使用します。 動的ポートへの接続はサポートされていません。  

または、DSN 情報をテンプレート ファイルに追加し、次のコマンドを実行して `~/.odbc.ini` に追加することもできます。
 - **odbcinst -i -s -f** _template_file_  
 
使用して、ドライバーが動作していることを確認できる`isql`このコマンドを使用するか、接続をテストします。
 - **bcp master.INFORMATION_SCHEMA.TABLES out OutFile.dat -S <server> -U <name> -P <password>**  

## <a name="using-secure-sockets-layer-ssl"></a>Secure Sockets Layer (SSL) を使用する  
Secure Sockets Layer (SSL) を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]への接続を暗号化できます。 SSL は、ネットワーク上の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のユーザー名とパスワードを保護します。 また、サーバーの ID を検証して、man-in-the-middle (MITM) 攻撃に対して保護することもできます。  

暗号化を有効にすると、セキュリティは向上しますが、パフォーマンスは低下します。

詳細については、次を参照してください。 [SQL Server への接続の暗号化](https://go.microsoft.com/fwlink/?LinkId=220900)と[を使用して検証を伴わない暗号化](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation)します。

**Encrypt** と **TrustServerCertificate**の設定に関係なく、サーバー ログインの資格情報 (ユーザー名とパスワード) は常に暗号化されます。 次の表は、 **Encrypt** 設定と **TrustServerCertificate** 設定の効果の一覧です。  

||**TrustServerCertificate = いいえ**|**TrustServerCertificate = [はい]**|  
|-|-------------------------------------|------------------------------------|  
|**Encrypt=no**|サーバー証明書は確認されません。<br /><br />クライアントとサーバー間で送信されるデータは暗号化されません。|サーバー証明書は確認されません。<br /><br />クライアントとサーバー間で送信されるデータは暗号化されません。|  
|**Encrypt=yes**|サーバー証明書は確認されます。<br /><br />クライアントとサーバー間で送信されるデータは暗号化されます。<br /><br />[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSL 証明書のサブジェクトの共通名 (CN) またはサブジェクトの別名 (SAN) の名前 (または IP アドレス) は、接続文字列に指定されているサーバー名 (または IP アドレス) と一致する必要があります。|サーバー証明書は確認されません。<br /><br />クライアントとサーバー間で送信されるデータは暗号化されます。|  

既定では、暗号化された接続はサーバーの証明書を必ず検証します。 ただし、自己署名証明書を持つサーバーに接続する場合も追加、`TrustServerCertificate`信頼された証明書機関の一覧に対して証明書の確認を省略するオプション。  

```  
Driver={ODBC Driver 13 for SQL Server};Server=ServerNameHere;Encrypt=YES;TrustServerCertificate=YES  
```  
  
SSL は、OpenSSL ライブラリを使用します。 次の表は、OpenSSL の最低限のサポートされるバージョンと、各プラットフォームの既定の証明書信頼ストアを示します。

|プラットフォーム|最低限の OpenSSL のバージョン|既定の証明書信頼ストアの場所|  
|------------|---------------------------|--------------------------------------------|
|Debian 9|1.1.0|/etc/ssl/certs|
|Debian 8.71 |1.0.1|/etc/ssl/certs|
|macOS 10.13|1.0.2|/usr/local/etc/openssl/certs|
|macOS 10.12|1.0.2|/usr/local/etc/openssl/certs|
|OS X 10.11|1.0.2|/usr/local/etc/openssl/certs|
|Red Hat Enterprise Linux 7|1.0.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|
|SuSE Linux Enterprise 12 |1.0.1|/etc/ssl/certs|
|SuSE Linux Enterprise 11 |0.9.8|/etc/ssl/certs|
|Ubuntu 17.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.10 |1.0.2|/etc/ssl/certs|
|Ubuntu 16.04 |1.0.2|/etc/ssl/certs|
  
暗号化を使用して、接続文字列で指定することも、`Encrypt`オプションを使用する場合**SQLDriverConnect**に接続します。

## <a name="see-also"></a>参照  
[Linux および macOS に Microsoft ODBC Driver for SQL Server をインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)  
[プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)
