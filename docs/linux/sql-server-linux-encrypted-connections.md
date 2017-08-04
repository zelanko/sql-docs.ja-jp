---
title: "Linux 上の SQL Server への接続の暗号化 |Microsoft ドキュメント"
description: "このトピックでは、Linux 上の SQL Server への接続の暗号化について説明します。"
author: tmullaney
ms.date: 06/14/2017
ms.author: thmullan;rickbyh
manager: jhubbard
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 
helpviewer_keywords:
- Linux, encrypted connections
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: dfbfeee8292f3af4020185248d3d6a3fad3c71ea
ms.contentlocale: ja-jp
ms.lasthandoff: 08/02/2017

---
# <a name="encrypting-connections-to-sql-server-on-linux"></a>Linux 上の SQL Server への接続を暗号化

[!INCLUDE[tsql-appliesto-sslinx-only_md](../../docs/includes/tsql-appliesto-sslinx-only_md.md)]

[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]Linux のトランスポート層セキュリティ (TLS) 暗号化に使用できます、クライアント アプリケーションとのインスタンス間のネットワーク経由で送信されるデータ[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]Windows と Linux の両方で同じ TLS プロトコルをサポートします。 TLS 1.2、1.1 および 1.0 です。 ただし、TLS を構成する手順は、オペレーティング システムに固有[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]が実行されています。  
 
## <a name="typical-scenario"></a>標準のシナリオ 
TLS は、クライアント アプリケーションからの接続の暗号化に使用される[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]です。 正しく構成されていれば、TLS は、プライバシーとデータの整合性、クライアントとサーバー間の通信の両方を提供します。  
次の手順では、一般的なシナリオについて説明します。  

1. データベース管理者は、秘密キーと証明書署名要求 (CSR) を生成します。 CSR の共通名は、クライアントは、SQL Server 接続文字列で指定するサーバー名に一致する必要があります。 この共通名は、通常の完全修飾ドメイン名、[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]ホストします。 複数のサーバーを同じ証明書を使用するのには、共通名にワイルドカードを使用できます (たとえば、`"*.contoso.com"`の代わりに`"node1.contoso.com"`)。   
2. CSR は、署名のための証明書機関 (CA) に送信されます。 接続するすべてのクライアント コンピューターで CA を信頼する必要があります[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]です。 CA は、データベース管理者に、署名証明書を返します。   
3. データベース管理者が構成[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]TLS 接続の秘密キーと署名入りの証明書を使用します。   
4. クライアントは指定`"Encrypt=True"`と`"TrustServerCertificate=False"`接続文字列にします。 (特定のパラメーター名がありますどのドライバーが使用されているによって異なります) です。 クライアントの現在の試行は SQL Server への接続を暗号化し、仲介の攻撃を防ぐために SQL Server の証明書の有効性を確認します。  
 
## <a name="configuring-tls-on-linux"></a>Linux での TLS の構成  

使用して`mssql-conf`のインスタンスの TLS を構成する[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]Linux で実行されています。 次のオプションがサポートされています。  

|オプション |Description |
|--- |--- |
|`network.forceencryption` |1 の場合、し[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]強制的にすべての接続を暗号化します。 既定では、このオプションは 0 です。 |  
|`network.tlscert` |証明書への絶対パスがファイルを[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]は TLS を使用します。 例:`/etc/ssl/certs/mssql.pem`証明書ファイルは mssql アカウントでアクセスする必要があります。 使用してファイルのアクセスを制限することをお勧めします。`chown mssql:mssql <file>; chmod 400 <file>`です。 |  
|`network.tlskey` |秘密キーへの絶対パスがファイルを[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]は TLS を使用します。 例:`/etc/ssl/private/mssql.key`証明書ファイルは mssql アカウントでアクセスする必要があります。 使用してファイルのアクセスを制限することをお勧めします。`chown mssql:mssql <file>; chmod 400 <file>`です。 | 
|`network.tlsprotocols` |SQL Server でどの TLS のプロトコルが許可されているコンマ区切り一覧。 [!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]常にしようとすると、最も強力な許可されているプロトコルをネゴシエートします。 クライアントが、許可されているすべてのプロトコルをサポートしていない場合[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]接続の試行を拒否します。  互換性のため、すべてのサポートされているプロトコルが既定 (1.2、1.1、1.0) で許可されます。  TLS 1.2 をサポートして、クライアント場合は、TLS 1.2 のみを許可することをお勧めします。 |  
|`network.tlsciphers` |指定する暗号がによって許可[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]TLS 用です。 この文字列はに従って書式設定する必要があります[OpenSSL の暗号一覧形式](https://www.openssl.org/docs/man1.0.2/apps/ciphers.html)です。 一般に、このオプションを変更する必要はありません。 <br /> 既定では、次の暗号は使用できます。 <br /> `ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-ECDSA-AES256-SHA:ECDHE-ECDSA-AES128-SHA:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA` |   
| | |
 
## <a name="example"></a>例 
この例では、自己署名証明書を使用します。 通常の実稼働のシナリオですべてのクライアントによって信頼されている CA によって証明書を署名とします。  
 
### <a name="step-1-generate-private-key-and-certificate"></a>手順 1: プライベート キーと証明書を生成します。 
Linux コンピューターでターミナル コマンドを開く場所[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]が実行されています。 次のコマンドを実行します。  

- 自己署名証明書を生成します。 /CN、SQL Server ホストの完全修飾ドメイン名に一致することを確認します。 たとえば、ワイルドカードを使用する場合があります必要に応じて`'/CN=*.contoso.com'`です。    
   ```  
   openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
   ```  

- アクセスを制限します。`mssql`  
   ```  
   sudo chown mssql:mssql mssql.pem mssql.key 
   sudo chmod 400 mssql.pem mssql.key 
   ```  
 
- (省略可能) システム SSL ディレクトリに移動します。  
   ```  
   sudo mv mssql.pem /etc/ssl/certs/ 
   sudo mv mssql.key /etc/ssl/private/ 
   ```  
 
### <a name="step-2-configure--includessnoversiondocsincludesssnoversion-mdmd"></a>手順 2: 構成[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]  
使用して`mssql-conf`を構成する[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]証明書を使用して、TLS のキーします。 セキュリティ強化のためもで使用できるプロトコルのみに TLS 1.2 を設定し、暗号化された接続を使用するすべてのクライアントを強制できます。  

```  
sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssql.pem 
sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssql.key 
sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
sudo /opt/mssql/bin/mssql-conf set network.forceencryption 1 
```
 
### <a name="step-3-restart-includessnoversiondocsincludesssnoversion-mdmd"></a>手順 3: 再起動[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)] 
[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]これらの変更を有効にするを再起動する必要があります。  
`sudo systemctl restart mssql-server`  
 
### <a name="step-4-copy-self-signed-certificate-to-client-machines"></a>手順 4: クライアント コンピューターへの自己署名証明書をコピーします。 
この例は、によって自己署名証明書を使用しているため、[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]ホスト、(秘密キーではない) 証明書をコピーしてに接続するすべてのクライアント コンピューター上の信頼されたルート証明書としてインストールされている必要があります[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]です。 証明書がすべてのクライアントによって既に信頼されている CA によって署名されている場合、この手順は必要ではありません。 
 
### <a name="step-5-connect-from-clients-using-tls"></a>手順 5: TLS を使用してクライアントから接続します。 
接続[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]暗号化を有効に使用するクライアントからおよび`TrustServerCertificate`'éý'`False`接続文字列にします。 さまざまなツールとドライバーを使用してこれらのパラメーターを指定する方法のいくつかの例を示します。 

sqlcmd  
`sqlcmd -N -C -S mssql.contoso.com -U sa -P '<YourPassword>'`  

[!INCLUDE[ssmanstudiofull-md](../../docs/includes/ssmanstudiofull-md.md)]   
  ![SSMS の接続 ダイアログ ボックス](media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png "SSMS の接続 ダイアログ ボックス")  
  
ADO.NET  
`"Encrypt=true; TrustServerCertificate=true;"`  

ODBC   
`"Encrypt=yes; TrustServerCertificate=no;"`  

JDBC  
`"encrypt=true; trustServerCertificate=false;" `

 
## <a name="common-connection-errors"></a>一般的な接続エラー  

|エラー メッセージ |Fix |
|--- |--- |
|証明書チェーンが信頼されていない証明機関によって発行されました。  |このエラーは、クライアントが、TLS ハンドシェイク中に SQL サーバーによって提示される証明書の署名を確認できないときに発生します。 クライアントが信頼するかを確認してください、[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]証明書を直接、または SQL Server 証明書に署名する CA です。 |
|対象のプリンシパル名が正しくありません。  |SQL Server の証明書の共通名 フィールドが、クライアントの接続文字列で指定されたサーバー名と一致していることを確認してください。 |  
|既存の接続はリモート ホストによって強制的に切断されました。 |このエラーは、クライアントは、SQL Server で必要な TLS プロトコル バージョンをサポートしない場合に発生することができます。 たとえば場合、[!INCLUDE[ssNoVersion](../../docs/includes/ssnoversion-md.md)]を TLS 1.2 を必要とするクライアントも、TLS 1.2 プロトコルをサポートしているかどうかを確認するように構成します。 |
| | |   


