## <a name="prerequisites"></a>前提条件

可用性グループを作成する前にする必要があります。

- 可用性レプリカをホストするすべてのサーバーが通信できるようにするために、環境を設定します。
- SQL Server をインストールする

>[!NOTE]
>Linux では、クラスターによって管理されるクラスター リソースとして追加する前に、可用性グループを作成する必要があります。 このドキュメントでは、可用性グループを作成する例を示します。 配布は、クラスターを作成し、可用性グループをクラスター リソースとして追加する具体的な指示は、の下のリンクを参照してください。[次のステップ](#next-steps)です。

1. **各ホストのコンピューター名を更新します。**

   各 SQL Server 名がある必要があります。
   
   - 15 文字以下
   - ネットワーク内で一意で
   
   コンピューター名を設定するには、編集`/etc/hostname`です。 次のスクリプトを編集できます。`/etc/hostname`で`vi`です。

   ```bash
   sudo vi /etc/hostname
   ```

1. **Hosts ファイルを構成します。**

>[!NOTE]
>ホスト名が、ip アドレス、DNS サーバーに登録されている場合、次の手順を実行する必要はありません。 可用性グループの構成の一部として設定されているすべてのノードが他の (対応する IP アドレスを持つ応答が、ホスト名に対して ping を実行) と通信できることを検証します。 また、その/etc/hosts ファイルに、ノードのホスト名と IP アドレス 127.0.0.1 localhost をマップするレコードが含まれていないことを確認してください。


   すべてのサーバー上の hosts ファイルには、IP アドレスと、可用性グループに参加するすべてのサーバーの名前が含まれています。 

   次のコマンドは、現在のサーバーの IP アドレスを返します。

   ```bash
   sudo ip addr show
   ```

   更新`/etc/hosts`です。 次のスクリプトを編集できます。`/etc/hosts`で`vi`です。

   ```bash
   sudo vi /etc/hosts
   ```

   次の例は`/etc/hosts`で**node1**の項目を追加**node1**と**node2**です。 このドキュメントで**node1** SQL Server のプライマリ レプリカを指します。 **node2**セカンダリ SQL サーバーを指します。 です。


   ```
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.128 node1
   10.128.16.77 node2
   ```

### <a name="install-sql-server"></a>SQL Server をインストールする

SQL Server をインストールします。 次のリンクは、さまざまな配布用の SQL Server インストールの手順をポイントします。 

- [Red Hat Enterprise Linux](..\linux\sql-server-linux-setup-red-hat.md)

- [SUSE Linux Enterprise Server](..\linux\sql-server-linux-setup-suse-linux-enterprise-server.md)

- [Ubuntu](..\linux\sql-server-linux-setup-ubuntu.md)

## <a name="enable-always-on-availability-groups-and-restart-sqlserver"></a>Always On 可用性グループを有効にして、sql server の再起動

SQL Server サービスをホストする各ノードで Always On 可用性グループを有効にしてから再起動`mssql-server`です。  次のスクリプトを実行します。

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-alwaysonhealth-event-session"></a>AlwaysOn_health イベント セッションを有効にします。 

Optionaly 有効にする Always On 可用性グループ固有のイベントを拡張可用性グループをトラブルシューティングする際に、根本原因の診断に役立てるために実行できます。

```Transact-SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

この XE セッションに関する詳細については、次を参照してください。[常に 拡張イベント](http://msdn.microsoft.com/library/dn135324.aspx)です。

## <a name="create-db-mirroring-endpoint-user"></a>データベース ミラーリング エンドポイントのユーザーを作成します。

次の TRANSACT-SQL スクリプトは、という名前のログインを作成`dbm_login`、という名前のユーザーと`dbm_user`です。 強力なパスワードでスクリプトを更新します。 すべての SQL Server データベース ミラーリングのエンドポイントのユーザーを作成するには、次のコマンドを実行します。

```Transact-SQL
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

## <a name="create-a-certificate"></a>証明書の作成します。

Linux 上の SQL Server サービスは、ミラーリングのエンドポイント間の通信を認証するのに証明書を使用します。 

次の TRANSACT-SQL スクリプトは、マスター_キーと証明書を作成します。 証明書をバックアップし、秘密キーを持つファイルをセキュリティで保護します。 強力なパスワードでスクリプトを更新します。 プライマリ SQL Server に接続し、証明書を作成する次の TRANSACT-SQL を実行します。

```Transact-SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate WITH SUBJECT = 'dbm';
BACKUP CERTIFICATE dbm_certificate
   TO FILE = '/var/opt/mssql/data/dbm_certificate.cer'
   WITH PRIVATE KEY (
           FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
           ENCRYPTION BY PASSWORD = '**<Private_Key_Password>**'
       );
```

この時点で証明書は、プライマリ SQL Server レプリカ`/var/opt/mssql/data/dbm_certificate.cer`と秘密キーで`var/opt/mssql/data/dbm_certificate.pvk`です。 可用性レプリカをホストするすべてのサーバー上の同じ場所にこれら 2 つのファイルをコピーします。 Mssql user を使用してまたは mssql ユーザーは、これらのファイルにアクセスする権限を付与します。 

たとえば移行元サーバーで、次のコマンド ファイルをコピー対象のコンピューター。 置換、  **<node2>** レプリカをホストする SQL Server インスタンスの名前を持つ値です。 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

対象サーバー上で mssql ユーザー証明書にアクセスする権限を付与します。

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>セカンダリ サーバー上の証明書を作成します。

次の TRANSACT-SQL スクリプトは、SQL Server のプライマリ レプリカに対して作成したバックアップからのマスター _ キーと証明書を作成します。 コマンドでは、証明書にアクセスするユーザーも許可します。 強力なパスワードでスクリプトを更新します。 復号化パスワードは、前の手順で、.pvk ファイルを作成するために使用する同じパスワードです。 証明書を作成するすべてのセカンダリ サーバーで、次のスクリプトを実行します。

```Transact-SQL
CREATE MASTER KEY ENCRYPTION BY PASSWORD = '**<Master_Key_Password>**';
CREATE CERTIFICATE dbm_certificate   
    AUTHORIZATION dbm_user
    FROM FILE = '/var/opt/mssql/data/dbm_certificate.cer'
    WITH PRIVATE KEY (
    FILE = '/var/opt/mssql/data/dbm_certificate.pvk',
    DECRYPTION BY PASSWORD = '**<Private_Key_Password>**'
            );
```

## <a name="create-the-database-mirroring-endpoints-on-all-replicas"></a>データベース ミラーリングのすべてのレプリカのエンドポイントを作成します。

データベース ミラーリング エンドポイントでは、伝送制御プロトコル (TCP) を使用して、データベース ミラーリング セッションに参加するサーバー インスタンス間、または可用性レプリカをホストするサーバー インスタンス間でメッセージを送受信します。 データベース ミラーリング エンドポイントでは、一意な TCP ポート番号でリッスンします。 

次の TRANSACT-SQL という名前の待機エンドポイントを作成する`Hadr_endpoint`可用性グループにします。 エンドポイントを開始し、作成したユーザーへの接続権限を提供します。 スクリプトを実行する前に、までの値を置き換える`**< ... >**`です。


>[!NOTE]
>このリリースでは、リスナーの IP 用に別の IP アドレスは使わないでください。 この問題の修正に取り組んでいますが、ここでのみ使用できる値は「0.0.0.0」。

すべての SQL Server インスタンスで、環境の次の TRANSACT-SQL を更新します。 

```Transact-SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = ALL,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login];
```

>[!IMPORTANT]
>ファイアウォールで TCP ポートは、リスナー ポート用に開かれる必要があります。

詳細については、次を参照してください。[データベース ミラーリング エンドポイント (SQL Server)](http://msdn.microsoft.com/library/ms179511.aspx)です。
