---
title: Linux 上の SQL Server への接続の暗号化 |Microsoft ドキュメント
description: この記事では、Linux 上の SQL Server への接続の暗号化について説明します。
author: tmullaney
ms.date: 01/30/2018
ms.author: meetb
manager: craigg
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
helpviewer_keywords:
- Linux, encrypted connections
ms.workload: Inactive
ms.openlocfilehash: b60ded8bde38413ccc2818efd2ca3852d88f235c
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="encrypting-connections-to-sql-server-on-linux"></a>Linux 上の SQL Server への接続を暗号化

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Linux のトランスポート層セキュリティ (TLS) 暗号化に使用できます、クライアント アプリケーションとのインスタンス間のネットワーク経由で送信されるデータ[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Windows と Linux の両方で同じ TLS プロトコルをサポートします。 TLS 1.2、1.1 および 1.0 です。 ただし、TLS を構成する手順は、オペレーティング システムに固有[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]が実行されています。  

## <a name="requirements-for-certificates"></a>証明書の要件 
始める前に、証明書は、これらの要件を満たすかどうかを確認する必要があります。
- 現在のシステム時刻は、証明書のプロパティをプロパティと有効期間の前に、証明書の発効後にする必要があります。
- 証明書がサーバー認証に使用されていること。 つまり、証明書の [拡張キー使用法] プロパティで [ サーバー認証 ] \(1.3.6.1.5.5.7.3.1) が指定されている必要があります。
- AT_KEYEXCHANGE の KeySpec オプションを使用して、証明書を作成する必要があります。 通常、証明書のキー使用法プロパティ (KEY_USAGE) には、キーの暗号化 (CERT_KEY_ENCIPHERMENT_KEY_USAGE) も含まれます。
- 証明書の Subject プロパティは、共通名 (CN) が同じであるホスト名またはサーバー コンピューターの完全修飾ドメイン名 (FQDN) として示す必要があります。 注: ワイルド カードの証明書がサポートされています。 

## <a name="overview"></a>概要
TLS は、クライアント アプリケーションからの接続の暗号化に使用される[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]です。 正しく構成されていれば、TLS は、プライバシーとデータの整合性、クライアントとサーバー間の通信の両方を提供します。  TLS 接続できますが開始したクライアントまたはサーバーが開始しました。 


## <a name="client-initiated-encryption"></a>クライアントが暗号化を開始 
- **証明書を生成**(/CN は、SQL Server ホストの完全修飾ドメイン名を一致する必要があります)

> [!NOTE]
> この例では、自己署名証明書を使用して、この必要があります指定しないで実稼働のシナリオです。 CA の証明書を使用する必要があります。 

        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **SQL Server を構成します。**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssqlfqdn.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssqlfqdn.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 0 

- **(Windows、Linux、または macOS)、クライアント コンピューターの証明書を登録します。**

    -   CA の署名証明書を使用している場合、ユーザー証明書の代わりに証明機関 (CA) 証明書をクライアント コンピューターにコピーする必要があります。 
    -   自己署名証明書を使用している場合だけ .pem ファイルを配布するそれぞれの次のフォルダーにコピーし、コマンドを実行できるようにします 
        - **Ubuntu**: コピーの証明書と```/usr/share/ca-certificates/```.crt に名前の変更拡張では、dpkg reconfigure ca 証明書を使用して、システム CA 証明書として有効にすることをします。 
        - **RHEL**: コピーの証明書と```/etc/pki/ca-trust/source/anchors/```使用```update-ca-trust```システム CA 証明書として有効にします。
        - **SUSE**: コピーの証明書と```/usr/share/pki/trust/anchors/```使用```update-ca-certificates```システム CA 証明書として有効にします。
        - **Windows**: ルート証明機関証明書]-> [信頼された証明書を現在のユーザーとして .pem ファイル]-> [インポート
        - **macOS**: 
           - 証明書をコピーします。 ```/usr/local/etc/openssl/certs```
           - ハッシュ値を取得するには、次のコマンドを実行します。 ```/usr/local/Cellar/openssql/1.0.2l/openssql x509 -hash -in mssql.pem -noout```
           - 値に、証明書の名前を変更します。 たとえば、 ```mv mssql.pem dc2dd900.0```のようにします。 Dc2dd900.0 を確認してください。 ```/usr/local/etc/openssl/certs```
    
-   **接続文字列の例** 

    - **[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]**   
  ![SSMS の接続 ダイアログ ボックス](media/sql-server-linux-encrypted-connections/ssms-encrypt-connection.png "SSMS の接続 ダイアログ ボックス")  
  
    - **SQLCMD** 

            sqlcmd  -S <sqlhostname> -N -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=True; TrustServerCertificate=False;" 
    - **ODBC** 

            "Encrypt=Yes; TrustServerCertificate=no;" 
    - **JDBC** 
    
            "encrypt=true; trustServerCertificate=false;" 

## <a name="server-initiated-encryption"></a>サーバーの暗号化を開始します。 

- **証明書を生成**(/CN は、SQL Server ホストの完全修飾ドメイン名を一致する必要があります)
        
        openssl req -x509 -nodes -newkey rsa:2048 -subj '/CN=mssql.contoso.com' -keyout mssql.key -out mssql.pem -days 365 
        sudo chown mssql:mssql mssql.pem mssql.key 
        sudo chmod 600 mssql.pem mssql.key   
        sudo mv mssql.pem /etc/ssl/certs/ 
        sudo mv mssql.key /etc/ssl/private/ 

- **SQL Server を構成します。**

        systemctl stop mssql-server 
        cat /var/opt/mssql/mssql.conf 
        sudo /opt/mssql/bin/mssql-conf set network.tlscert /etc/ssl/certs/mssqlfqdn.pem 
        sudo /opt/mssql/bin/mssql-conf set network.tlskey /etc/ssl/private/mssqlfqdn.key 
        sudo /opt/mssql/bin/mssql-conf set network.tlsprotocols 1.2 
        sudo /opt/mssql/bin/mssql-conf set network.forceencryption 1 
        
-   **接続文字列の例** 

    - **SQLCMD**

            sqlcmd  -S <sqlhostname> -U sa -P '<YourPassword>' 
    - **ADO.NET** 

            "Encrypt=False; TrustServerCertificate=False;" 
    - **ODBC** 

            "Encrypt=no; TrustServerCertificate=no;"  
    - **JDBC** 
    
            "encrypt=false; trustServerCertificate=false;" 
            
> [!NOTE]
> 設定**TrustServerCertificate**クライアント証明書の信頼性を検証するように CA に接続できない場合は True に

## <a name="common-connection-errors"></a>一般的な接続エラー  

|エラー メッセージ |Fix |
|--- |--- |
|証明書チェーンが信頼されていない証明機関によって発行されました。  |このエラーは、クライアントが、TLS ハンドシェイク中に SQL サーバーによって提示される証明書の署名を確認できないときに発生します。 クライアントが信頼するかを確認してください、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]証明書を直接、または SQL Server 証明書に署名する CA です。 |
|対象のプリンシパル名が正しくありません。  |SQL Server の証明書の共通名 フィールドが、クライアントの接続文字列で指定されたサーバー名と一致していることを確認してください。 |  
|既存の接続はリモート ホストによって強制的に切断されました。 |このエラーは、クライアントは、SQL Server で必要な TLS プロトコル バージョンをサポートしない場合に発生することができます。 たとえば場合、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]を TLS 1.2 を必要とするクライアントも、TLS 1.2 プロトコルをサポートしているかどうかを確認するように構成します。 |
| | |   
