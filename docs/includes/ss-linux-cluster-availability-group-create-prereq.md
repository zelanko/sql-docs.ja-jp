---
ms.openlocfilehash: 75f5280a90efd1eea1882da99ce125a94cde17a8
ms.sourcegitcommit: 50b60ea99551b688caf0aa2d897029b95e5c01f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51716214"
---
## <a name="prerequisites"></a>前提条件

可用性グループを作成する前に、以下のことを行う必要があります。

- 可用性レプリカをホストするすべてのサーバーが通信できるように環境を設定します。
- SQL Server をインストールします。

>[!NOTE]
>Linux では、クラスターによって管理されるクラスター リソースとして追加する前に、可用性グループを作成する必要があります。 このドキュメントでは、可用性グループを作成する例を示します。 クラスターを作成し、クラスター リソースとして、可用性グループを追加する特定の配布手順については、「次の手順」の下のリンクを参照してください。

1. 各ホストのコンピューター名を更新します。

   各 SQL Server 名には次の条件があります。
   
   - 15 文字以下。
   - ネットワーク内で一意です。
   
   コンピューター名を設定するには、`/etc/hostname` を編集します。 次のスクリプトを編集できます`/etc/hostname`で`vi`:。

   ```bash
   sudo vi /etc/hostname
   ```

2. Hosts ファイルを構成します。

    >[!NOTE]
    >ホスト名が ip アドレス、DNS サーバーに登録されている場合は、次の手順を実行する必要はありません。 可用性グループの構成の一部にするためのもので、ノードすべてが、互いと通信できることを検証します。 (ホスト名への ping は、対応する IP アドレスに応答する必要があります)。また、/etc/hosts ファイルに、ノードのホスト名を localhost IP アドレス 127.0.0.1 をマップするレコードが含まれていないことを確認します。
    >

   すべてのサーバー上の hosts ファイルには、可用性グループに参加するすべてのサーバーの IP アドレスと名前が含まれています。 

   次のコマンドは、現在のサーバーの IP アドレスを返します。

   ```bash
   sudo ip addr show
   ```

   `/etc/hosts` を更新します。 次のスクリプトを編集できます`/etc/hosts`で`vi`:。

   ```bash
   sudo vi /etc/hosts
   ```

   次の例は、**node1** の `/etc/hosts` を示しています。**node1**、**node2**、**node3** に対して追加があります。 このドキュメントで**node1**はプライマリ レプリカをホストするサーバーを表します。 **Node2**と**node3**セカンダリ レプリカをホストするサーバーを参照してください。

    ```
    127.0.0.1   localhost localhost4 localhost4.localdomain4
    ::1       localhost localhost6 localhost6.localdomain6
    10.128.18.12 node1
    10.128.16.77 node2
    10.128.15.33 node3
    ```

### <a name="install-sql-server"></a>SQL Server をインストールする

SQL Server をインストールします。 次のリンクは、さまざまなディストリビューションの SQL Server のインストール手順をポイントします。 

- [Red Hat Enterprise Linux](../linux/quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)
- [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)

## <a name="enable-alwayson-availability-groups-and-restart-mssql-server"></a>AlwaysOn 可用性グループを有効にして mssql-server を再起動する

SQL Server インスタンスをホストする各ノードで AlwaysOn 可用性グループを有効にします。 再起動`mssql-server`します。 次のスクリプトを実行します。

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-an-alwaysonhealth-event-session"></a>AlwaysOn_health イベント セッションを有効にする 

必要に応じて、可用性グループをトラブルシューティングする際に、根本原因を診断を支援する AlwaysOn 可用性グループの拡張イベントを有効にできます。 SQL Server の各インスタンスで次のコマンドを実行します。 

```SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

この XE セッションの詳細については、[AlwaysOn の拡張イベント](https://msdn.microsoft.com/library/dn135324.aspx)を参照してください。

## <a name="create-a-certificate"></a>証明書を作成する

Linux 上の SQL Server サービスは、ミラーリングのエンドポイント間の通信を認証するのに証明書を使用します。 

次の Transact-SQL スクリプトでは、マスター キーと証明書を作成します。 その後、証明書をバックアップし、秘密キーでファイルをセキュリティ保護します。 強力なパスワードでスクリプトを更新してください。 プライマリ SQL Server インスタンスに接続します。 証明書を作成するには、次の TRANSACT-SQL スクリプトを実行します。

```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
BACKUP CERTIFICATE dbm_certificate
   TO FILE = '/var/opt/mssql/data/dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '**<Private_Key_Password>**'
       );
```

この時点で、プライマリ SQL Server レプリカの `/var/opt/mssql/data/dbm_certificate.cer` には証明書が、`var/opt/mssql/data/dbm_certificate.pvk` には秘密キーが作成されています。 これら 2 つのファイルを、可用性レプリカをホストするすべてのサーバー上の同じ場所にコピーします。 Mssql ユーザーを使用して、またはファイルにアクセスを mssql ユーザーに権限を付与します。 

たとえば、ソース サーバーで、次のコマンド、ファイル コピー、ターゲット コンピューターにします。 置換、`**<node2>**`レプリカをホストする SQL Server インスタンスの名前を持つ値。 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

各対象サーバー上を mssql ユーザー証明書へのアクセスにアクセス許可を付与します。

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>セカンダリ サーバーで証明書を作成する

次の Transact-SQL スクリプトでは、プライマリ SQL Server レプリカで作成したバックアップからマスター キーと証明書を作成します。 強力なパスワードでスクリプトを更新してください。 暗号化解除パスワードは、前の手順で .pvk ファイルの作成に使ったものと同じパスワードです。 証明書を作成するには、すべてのセカンダリ サーバー上で、次のスクリプトを実行します。

```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate
    FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
    WITH PRIVATE KEY (
    FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
    DECRYPTION BY PASSWORD = '**<Private_Key_Password>**'
            );
```

## <a name="create-the-database-mirroring-endpoints-on-all-replicas"></a>すべてのレプリカにデータベース ミラーリング エンドポイントを作成する

データベース ミラーリング エンドポイントでは、伝送制御プロトコル (TCP) を使用して、データベース ミラーリング セッションに参加するサーバー インスタンス間、または可用性レプリカをホストするサーバー インスタンス間でメッセージを送受信します。 データベース ミラーリング エンドポイントでは、一意な TCP ポート番号でリッスンします。 

次の Transact-SQL スクリプトでは、可用性グループに対して `Hadr_endpoint` という名前のリスニング エンドポイントを作成します。 エンドポイントを開始し、作成した証明書への接続権限が与えられます。 スクリプトを実行する前に、`**< ... >**` の間の値を置き換えます。 必要に応じて、IP アドレス `LISTENER_IP = (0.0.0.0)` を含めることができます。 リスナー IP アドレスは、IPv4 アドレスである必要があります。 `0.0.0.0` を使用することもできます。 

すべての SQL Server インスタンスで、ご利用の環境に合わせて次の Transact-SQL スクリプトを更新します。 

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATABASE_MIRRORING (
        ROLE = ALL,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
```

>[!NOTE]
>構成専用レプリカの唯一の有効な値をホストする 1 つのノードで、SQL Server Express Edition を使用するかどうかは`ROLE`は`WITNESS`します。 SQL Server Express Edition では、次のスクリプトを実行します。

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATABASE_MIRRORING (
        ROLE = WITNESS,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
```

ファイアウォールの TCP ポートをリスナー ポート用に開く必要があります。



>[!IMPORTANT]
>データベース ミラーリング エンドポイントのサポートされている唯一の認証方法は、SQL Server 2017 リリースでは、`CERTIFICATE`します。 `WINDOWS`オプションは、将来のリリースで有効になります。

詳細については、「[データベース ミラーリング エンドポイント (SQL Server)](https://msdn.microsoft.com/library/ms179511.aspx)」を参照してください。


