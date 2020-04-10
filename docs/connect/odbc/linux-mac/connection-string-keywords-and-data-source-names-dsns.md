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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d323481aaf3e12da9786a3b02f21f47c3c98f7cf
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924540"
---
# <a name="connecting-to-sql-server"></a>SQL Server への接続
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

このトピックでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースへの接続を作成する方法について説明します。  
  
## <a name="connection-properties"></a>接続のプロパティ  

Linux および Mac でサポートされている接続文字列のすべてのキーワードと属性については、「[DSN と接続文字列のキーワードと属性](../../../connect/odbc/dsn-connection-string-attribute.md)」をご覧ください

> [!IMPORTANT]  
> データベース ミラーリングを使用する (フェールオーバー パートナーがある) データベースに接続する場合は、接続文字列にデータベース名を指定しないでください。 代わりに、**use** <_データベース名_> コマンドを送信してデータベースに接続してから、クエリを実行します。  
  
**Driver** キーワードには、次のいずれかの値を渡すことができます。  
  
-   ドライバーをインストールしたときに使用した名前。

-   ドライバー ライブラリへのパス。ドライバーのインストールに使用されたテンプレート .ini ファイルで指定されています。  

DSN を作成するには、現在のユーザーだけがアクセスできるユーザー DSN の場合はファイル **~/.odbc.ini** (ユーザーのホーム ディレクトリの `.odbc.ini`) を、システム DSN の場合は `/etc/odbc.ini` を (管理者特権が必要)、(必要に応じて) 作成し、編集します。次のサンプル ファイルでは、DSN に必要な最小限のエントリを示します。  

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

サーバーに接続するために、必要に応じてプロトコルとポートを指定することができます。 たとえば、**Server=tcp:** _servername_ **,12345** などです。 Linux および macOS ドライバーでサポートされているプロトコルは `tcp` のみであることに注意してください。

静的ポートの名前付きインスタンスに接続するには、<b>Server=</b>*servername*,**port_number** を使用します。 バージョン 17.4 より前では、動的ポートへの接続はサポートされていません。

または、DSN 情報をテンプレート ファイルに追加し、次のコマンドを実行して `~/.odbc.ini` に追加することもできます。
 - **odbcinst -i -s -f** <_テンプレート ファイル_>  
 
`isql` を使用して接続をテストすることで、ドライバーが機能していることを確認できます。または、次のコマンドを使用できます。
 - **bcp master.INFORMATION_SCHEMA.TABLES out OutFile.dat -S <server> -U <name> -P <password>**  

## <a name="using-secure-sockets-layer-ssl"></a>Secure Sockets Layer (SSL) を使用する  
Secure Sockets Layer (SSL) を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] への接続を暗号化できます。 SSL は、ネットワーク上で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のユーザー名とパスワードを保護します。 また、サーバーの ID を検証して、man-in-the-middle (MITM) 攻撃に対して保護することもできます。  

暗号化を有効にすると、セキュリティは向上しますが、パフォーマンスは低下します。

詳しくは、「[SQL Server への接続の暗号化](https://go.microsoft.com/fwlink/?LinkId=220900)」および「[検証を伴わない暗号化の使用](https://docs.microsoft.com/sql/relational-databases/native-client/features/using-encryption-without-validation)」をご覧ください。

**Encrypt** と **TrustServerCertificate**の設定に関係なく、サーバー ログインの資格情報 (ユーザー名とパスワード) は常に暗号化されます。 次の表は、 **Encrypt** 設定と **TrustServerCertificate** 設定の効果の一覧です。  

||**TrustServerCertificate=no**|**TrustServerCertificate=yes**|  
|-|-------------------------------------|------------------------------------|  
|**Encrypt=no**|サーバー証明書は確認されません。<br /><br />クライアントとサーバー間で送信されるデータは暗号化されません。|サーバー証明書は確認されません。<br /><br />クライアントとサーバー間で送信されるデータは暗号化されません。|  
|**Encrypt=yes**|サーバー証明書は確認されます。<br /><br />クライアントとサーバー間で送信されるデータは暗号化されます。<br /><br />[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSL 証明書のサブジェクトの共通名 (CN) またはサブジェクトの別名 (SAN) の名前 (または IP アドレス) は、接続文字列に指定されているサーバー名 (または IP アドレス) と正確に一致する必要があります。|サーバー証明書は確認されません。<br /><br />クライアントとサーバー間で送信されるデータは暗号化されます。|  

既定では、暗号化された接続はサーバーの証明書を必ず検証します。 ただし、自己署名証明書があるサーバーに接続する場合は、`TrustServerCertificate` オプションも追加して、信頼された証明機関の一覧に対する証明書の確認をバイパスします。  

```  
Driver={ODBC Driver 13 for SQL Server};Server=ServerNameHere;Encrypt=YES;TrustServerCertificate=YES  
```  
  
SSL は、OpenSSL ライブラリを使用します。 次の表は、OpenSSL の最低限のサポートされるバージョンと、各プラットフォームの既定の証明書信頼ストアを示します。

|プラットフォーム|最低限の OpenSSL のバージョン|既定の証明書信頼ストアの場所|  
|------------|---------------------------|--------------------------------------------|
|Debian 10|1.1.1|/etc/ssl/certs|
|Debian 9|1.1.0|/etc/ssl/certs|
|Debian 8.71|1.0.1|/etc/ssl/certs|
|OS X 10.11、macOS 10.12、10.13、10.14|1.0.2|/usr/local/etc/openssl/certs|
|Red Hat Enterprise Linux 8|1.1.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 7|1.0.1|/etc/pki/tls/cert.pem|
|Red Hat Enterprise Linux 6|1.0.0-10|/etc/pki/tls/cert.pem|
|SUSE Linux Enterprise 15|1.1.0|/etc/ssl/certs|
|SUSE Linux Enterprise 11、12|1.0.1|/etc/ssl/certs|
|Ubuntu 18.10、19.04|1.1.1|/etc/ssl/certs|
|Ubuntu 18.04|1.1.0|/etc/ssl/certs|
|Ubuntu 16.04、16.10、17.10|1.0.2|/etc/ssl/certs|
|Ubuntu 14.04|1.0.1|/etc/ssl/certs|

また、**SQLDriverConnect** を使用して接続するときに、`Encrypt` オプションを使用して接続文字列で暗号化を指定することもできます。

## <a name="adjusting-the-tcp-keep-alive-settings"></a>TCP キープアライブの設定を調整する

ODBC ドライバー 17.4 以降では、ドライバーでキープアライブ パケットを送信し、応答が受信されないときに再送信する頻度を、構成できます。
構成するには、`odbcinst.ini` のドライバーのセクション、または `odbc.ini` の DSN のセクションに、次の設定を追加します。 DSN を使用して接続するとき、ドライバーでは、DSN のセクションがある場合はその設定が使用されします。それ以外の場合、または接続文字列のみを使用して接続する場合は、`odbcinst.ini` のドライバーのセクションの設定が使用されます。 どちらの場所にも設定が存在しない場合、ドライバーでは既定値が使用されます。

- `KeepAlive=<integer>` では、TCP がキープアライブ パケットを送信することによって、アイドル状態の接続が壊れていないかどうかを確認する頻度を制御します。 既定値は **30** 秒です。

- `KeepAliveInterval=<integer>` では、応答を受信するまでキープアライブを再送信する間隔を設定します。  既定値は **1** 秒です。

## <a name="see-also"></a>参照

- [Linux に SQL Server 用 Microsoft ODBC Driver をインストールする](../../../connect/odbc/linux-mac/installing-the-microsoft-odbc-driver-for-sql-server.md)
- [macOS に Microsoft ODBC Driver for SQL Server をインストールする](../../../connect/odbc/linux-mac/install-microsoft-odbc-driver-sql-server-macos.md)
- [プログラミング ガイドライン](../../../connect/odbc/linux-mac/programming-guidelines.md)
