## <a name="prerequisites"></a>前提条件

可用性グループを作成する前に、以下のことを行う必要があります。

- 可用性レプリカをホストするすべてのサーバーが通信できるように、環境を設定します。
- SQL Server をインストールします。

>[!NOTE]
>Linux では、クラスターによって管理されるクラスター リソースとして追加する前に、可用性グループを作成する必要があります。 このドキュメントでは、可用性グループを作成する例を示します。 クラスターを作成し、可用性グループをクラスター リソースとして追加する特定の配布手順については、「次の手順」の下のリンクを参照してください。

1. 各ホストのコンピューター名を更新します。

   各 SQL Server 名には次の条件があります。
   
   - 15 文字以下です。
   - ネットワーク内で一意です。
   
   コンピューター名を設定するには、`/etc/hostname` を編集します。 次のスクリプトを編集できます`/etc/hostname`で`vi`:。

   ```bash
   sudo vi /etc/hostname
   ```

2. Hosts ファイルを構成します。

    >[!NOTE]
    >ホスト名が、ip アドレス、DNS サーバーに登録されている場合は、次の手順を行う必要はありません。 可用性グループの構成の一部にするためのもので、ノードのすべてが相互に通信できることを検証します。 (ホスト名への ping は、対応する IP アドレスに応答する必要があります)。またの/etc/hosts ファイルに、localhost の IP アドレス 127.0.0.1 でノードのホスト名をマップするレコードが含まれていないことを確認します。
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

   次の例は、**node1** の `/etc/hosts` を示しています。**node1**、**node2**、**node3** に対して追加があります。 このドキュメントで**node1**はプライマリ レプリカをホストするサーバーを表します。 および**node2**と**node3**セカンダリ レプリカをホストするサーバーを参照してください。

    ```
    127.0.0.1   localhost localhost4 localhost4.localdomain4
    ::1       localhost localhost6 localhost6.localdomain6
    10.128.18.12 node1
    10.128.16.77 node2
    10.128.15.33 node3
    ```

### <a name="install-sql-server"></a>SQL Server をインストールする

SQL Server をインストールします。 次のリンクは、さまざまな配布用の SQL Server インストールの手順をポイントします。 

- [Red Hat Enterprise Linux](../linux/quickstart-install-connect-red-hat.md)
- [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)
- [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)

## <a name="enable-alwayson-availability-groups-and-restart-mssql-server"></a>AlwaysOn 可用性グループを有効にし、mssql サーバーを再起動

SQL Server インスタンスをホストする各ノードで AlwaysOn 可用性グループを有効にします。 再起動`mssql-server`です。 次のスクリプトを実行します。

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-an-alwaysonhealth-event-session"></a>AlwaysOn_health イベント セッションを有効にします。 

必要に応じて、可用性グループをトラブルシューティングする際に、根本原因の診断に役立てるために AlwaysOn 可用性グループの拡張イベントを有効にすることができます。 SQL Server の各インスタンスで、次のコマンドを実行します。 

```SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

この XE セッションに関する詳細については、次を参照してください。[拡張イベント AlwaysOn](http://msdn.microsoft.com/library/dn135324.aspx)です。

## <a name="create-a-database-mirroring-endpoint-user"></a>データベース ミラーリング エンドポイントのユーザーを作成します。

次の TRANSACT-SQL スクリプトは、という名前のログインを作成`dbm_login`という名前のユーザーと`dbm_user`です。 強力なパスワードでスクリプトを更新します。 データベース ミラーリングのエンドポイントのユーザーを作成するには、すべての SQL Server インスタンスで、次のコマンドを実行します。

```SQL
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

## <a name="create-a-certificate"></a>証明書を作成する

Linux 上の SQL Server サービスは、ミラーリングのエンドポイント間の通信を認証するのに証明書を使用します。 

次の TRANSACT-SQL スクリプトは、マスター_キーと証明書を作成します。 証明書をバックアップにし、秘密キーを持つファイルをセキュリティで保護します。 強力なパスワードでスクリプトを更新してください。 プライマリ SQL Server インスタンスに接続します。 証明書を作成するには、次の TRANSACT-SQL スクリプトを実行します。

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

この時点にある証明書が、プライマリ SQL Server レプリカ`/var/opt/mssql/data/dbm_certificate.cer`と秘密キーで`var/opt/mssql/data/dbm_certificate.pvk`です。 これら 2 つのファイルを、可用性レプリカをホストするすべてのサーバー上の同じ場所にコピーします。 Mssql user を使用してまたは mssql ユーザーは、これらのファイルにアクセスする権限を付与します。 

たとえば、移行元サーバーで、次のコマンド ファイルをコピー、ターゲット マシンにします。 置換、`**<node2>**`レプリカをホストする SQL Server インスタンスの名前を持つ値です。 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

各対象サーバー上には、mssql ユーザー証明書にアクセスする権限を付与します。

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>セカンダリ サーバーで証明書を作成する

次の TRANSACT-SQL スクリプトは、SQL Server のプライマリ レプリカに対して作成したバックアップから、マスター _ キーと証明書を作成します。 また、ユーザーに証明書へのアクセスを承認します。 強力なパスワードでスクリプトを更新してください。 暗号化解除パスワードは、前の手順で .pvk ファイルの作成に使ったものと同じパスワードです。 証明書を作成するには、するには、すべてのセカンダリ サーバー上で、次のスクリプトを実行します。

```SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate   
    AUTHORIZATION dbm_user
    FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
    WITH PRIVATE KEY (
    FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
    DECRYPTION BY PASSWORD = '**<Private_Key_Password>**'
            );
```

## <a name="create-the-database-mirroring-endpoints-on-all-replicas"></a>すべてのレプリカにデータベース ミラーリング エンドポイントを作成する

データベース ミラーリング エンドポイントは、データベース ミラーリング セッションに参加させる、または可用性レプリカをホストするサーバー インスタンス間でメッセージの送受信に伝送制御プロトコル (TCP) を使用します。 データベース ミラーリング エンドポイントでは、一意な TCP ポート番号でリッスンします。 

次の TRANSACT-SQL スクリプトの作成という名前のリッスンしているエンドポイント`Hadr_endpoint`可用性グループのです。 エンドポイントを開始し、接続のアクセス許可を作成したユーザーに与えられます。 スクリプトを実行する前に、`**< ... >**` の間の値を置き換えます。 IP アドレスを含めることができます必要に応じて`LISTENER_IP = (0.0.0.0)`です。 リスナーの IP アドレスは、IPv4 アドレスである必要があります。 使用することも`0.0.0.0`します。 

すべての SQL Server インスタンスで、環境には、次の TRANSACT-SQL スクリプトを更新します。 

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = ALL,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login];
```

>[!NOTE]
>レプリカをホストする構成のみでの唯一の有効な値を 1 つのノードに SQL Server Express Edition を使用するかどうか`ROLE`は`WITNESS`します。 SQL Server Express Edition では、次のスクリプトを実行します。

```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = WITNESS,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login];
```

ファイアウォールで TCP ポートは、リスナー ポートを開く必要があります。



>[!IMPORTANT]
>データベース ミラーリング エンドポイントにサポートされている唯一の認証メソッドは、SQL Server 2017 リリースでは、`CERTIFICATE`です。 `WINDOWS`オプションは将来のリリースで有効にします。

詳細については、次を参照してください。[データベース ミラーリング エンドポイント (SQL Server)](http://msdn.microsoft.com/library/ms179511.aspx)です。


