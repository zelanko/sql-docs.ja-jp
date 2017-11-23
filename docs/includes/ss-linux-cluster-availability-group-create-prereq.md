## <a name="prerequisites"></a>前提条件

可用性グループを作成する前に、以下のことを行う必要があります。

- 可用性レプリカをホストするすべてのサーバーが通信できるように環境を設定します
- SQL Server をインストールする

>[!NOTE]
>Linux で、クラスターによって管理されるクラスター リソースとして追加する可用性グループを作成する必要があります。 このドキュメントでは、可用性グループを作成する例を示します。 クラスターを作成し、可用性グループをクラスター リソースとして追加するディストリビューション固有の具体的な説明については、「[次のステップ](#next-steps)」の後のリンクをご覧ください。

1. **各ホストのコンピューター名を更新する**

   各 SQL Server 名には次の条件があります。
   
   - 15 文字以下
   - ネットワーク内で一意
   
   コンピューター名を設定するには、`/etc/hostname` を編集します。 次のスクリプトを使うと、`vi` で `/etc/hostname` を編集できます。

   ```bash
   sudo vi /etc/hostname
   ```

1. **hosts ファイルを構成する**

>[!NOTE]
>ホスト名が IP アドレスで DNS サーバーに登録されている場合、次の手順を実行する必要はありません。 可用性グループ構成の一部になるすべてのノードが相互に通信できることを確認します (ホスト名に対して ping を実行すると、対応する IP アドレスで応答される必要があります)。 また、/etc/hosts ファイルに、localhost IP アドレス 127.0.0.1 をノードのホスト名とマップするレコードが含まれないことを確認します。


   すべてのサーバー上の hosts ファイルには、可用性グループに参加するすべてのサーバーの IP アドレスと名前が含まれています。 

   次のコマンドは、現在のサーバーの IP アドレスを返します。

   ```bash
   sudo ip addr show
   ```

   `/etc/hosts` を更新します。 次のスクリプトを使うと、`vi` で `/etc/hosts` を編集できます。

   ```bash
   sudo vi /etc/hosts
   ```

   次の例は、**node1** の `/etc/hosts` を示しています。**node1**、**node2**、**node3** に対して追加があります。 このドキュメントでは、**node1** はプライマリ レプリカをホストするサーバーを指します。 **node2** と **node3** は、セカンダリ レプリカをホストするサーバーを指します。


   ```
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.12 node1
   10.128.16.77 node2
   10.128.15.33 node3
   ```

### <a name="install-sql-server"></a>SQL Server をインストールする

SQL Server をインストールします。 次のリンクは、さまざまなディストリビューションの SQL Server インストールの手順に移動します。 

- [Red Hat Enterprise Linux](../linux/quickstart-install-connect-red-hat.md)

- [SUSE Linux Enterprise Server](../linux/quickstart-install-connect-suse.md)

- [Ubuntu](../linux/quickstart-install-connect-ubuntu.md)

## <a name="enable-always-on-availability-groups-and-restart-sqlserver"></a>Always On 可用性グループを有効にして sqlserver を再起動する

SQL Server インスタンスをホストする各ノードで Always On 可用性グループを有効にしてから、`mssql-server` を再起動します。  次のスクリプトを実行します。

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled  1
sudo systemctl restart mssql-server
```

##  <a name="enable-alwaysonhealth-event-session"></a>AlwaysOn_health イベント セッションを有効にする 

オプションで、Always On 可用性グループの拡張イベントを有効にすると、可用性グループのトラブルシューティング時に根本原因を診断するために役立ちます。 SQL Server の各インスタンスで次のコマンドを実行します。 

```SQL
ALTER EVENT SESSION  AlwaysOn_health ON SERVER WITH (STARTUP_STATE=ON);
GO
```

この XE セッションの詳細については、「[AlwaysOn の拡張イベント](http://msdn.microsoft.com/library/dn135324.aspx)」をご覧ください。

## <a name="create-db-mirroring-endpoint-user"></a>db ミラーリング エンドポイント ユーザーを作成する

次の Transact-SQL スクリプトでは、`dbm_login` という名前のログインと `dbm_user` という名前のユーザーを作成します。 強力なパスワードでスクリプトを更新します。 データベース ミラーリング エンドポイントのユーザーを作成するために、すべての SQL Server インスタンスで次のコマンドを実行します。

```SQL
CREATE LOGIN dbm_login WITH PASSWORD = '**<1Sample_Strong_Password!@#>**';
CREATE USER dbm_user FOR LOGIN dbm_login;
```

## <a name="create-a-certificate"></a>証明書を作成する

Linux 上の SQL Server サービスは、ミラーリングのエンドポイント間の通信を認証するのに証明書を使用します。 

次の Transact-SQL スクリプトは、マスター キーと証明書を作成します。 その後、証明書をバックアップし、秘密キーでファイルをセキュリティ保護します。 強力なパスワードでスクリプトを更新してください。 プライマリ SQL Server インスタンスに接続し、証明書を作成する次の Transact-SQL を実行します。

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

この時点で、プライマリ SQL Server レプリカの `/var/opt/mssql/data/dbm_certificate.cer` には証明書が、`var/opt/mssql/data/dbm_certificate.pvk` には秘密キーが作成されています。 これら 2 つのファイルを、可用性レプリカをホストするすべてのサーバー上の同じ場所にコピーします。 mssql ユーザーを使うか、またはこれらのファイルへのアクセス許可を mssql ユーザーに付与します。 

たとえば、ソース サーバーでは、次のコマンドでファイルをターゲット コンピューターにコピーします。 **<node2>** の値を、レプリカをホストする SQL Server インスタンスの名前に置き換えます。 

```bash
cd /var/opt/mssql/data
scp dbm_certificate.* root@**<node2>**:/var/opt/mssql/data/
```

各対象サーバー上で証明書へのアクセス許可を mssql ユーザーに付与します。

```bash
cd /var/opt/mssql/data
chown mssql:mssql dbm_certificate.*
```

## <a name="create-the-certificate-on-secondary-servers"></a>セカンダリ サーバーで証明書を作成する

次の Transact-SQL スクリプトは、SQL Server のプライマリ レプリカで作成したバックアップからマスター キーと証明書を作成します。 また、ユーザーに証明書へのアクセスを承認します。 強力なパスワードでスクリプトを更新してください。 暗号化解除パスワードは、前の手順で .pvk ファイルの作成に使ったものと同じパスワードです。 すべてのセカンダリ サーバーで次のスクリプトを実行し、証明書を作成します。

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

データベース ミラーリング エンドポイントでは、伝送制御プロトコル (TCP) を使用して、データベース ミラーリング セッションに参加するサーバー インスタンス間、または可用性レプリカをホストするサーバー インスタンス間でメッセージを送受信します。 データベース ミラーリング エンドポイントでは、一意な TCP ポート番号でリッスンします。 TCP リスナーには、リスナーの IP アドレスが必要です。 リスナーの IP アドレスは、IPv4 アドレスである必要があります。 使用することも`0.0.0.0`します。 

次の Transact-SQL は、可用性グループに対して `Hadr_endpoint` という名前のリスニング エンドポイントを作成します。 エンドポイントを開始し、作成したユーザーに接続許可を付与します。 スクリプトを実行する前に、`**< ... >**` の間の値を置き換えます。

すべての SQL Server インスタンスで、環境の次の TRANSACT-SQL を更新します。 

```SQL
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

>[!NOTE]
>ロールの唯一の有効な値は、1 つのノードの構成のみのレプリカをホストする SQL Server Express Edition を使用している場合、`WITNESS`です。 SQL Server Express Edition では、次のスクリプトを実行します。
>```SQL
CREATE ENDPOINT [Hadr_endpoint]
    AS TCP (LISTENER_IP = (0.0.0.0), LISTENER_PORT = **<5022>**)
    FOR DATA_MIRRORING (
        ROLE = WITNESS,
        AUTHENTICATION = CERTIFICATE dbm_certificate,
        ENCRYPTION = REQUIRED ALGORITHM AES
        );
ALTER ENDPOINT [Hadr_endpoint] STATE = STARTED;
GRANT CONNECT ON ENDPOINT::[Hadr_endpoint] TO [dbm_login];
```

The TCP port on the firewall needs to be open for the listener port.



>[!IMPORTANT]
>For SQL Server 2017 release, the only authentication method supported for database mirroring endpoint is `CERTIFICATE`. `WINDOWS` option will be enabled in a future release.

For complete information, see [The Database Mirroring Endpoint (SQL Server)](http://msdn.microsoft.com/library/ms179511.aspx).
