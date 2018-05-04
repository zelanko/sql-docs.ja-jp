---
title: 作成し、Linux 上の SQL Server の可用性グループの構成 |Microsoft ドキュメント
description: このチュートリアルでは、作成して、Linux 上の SQL Server の可用性グループを構成する方法を示します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 12/11/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.openlocfilehash: 7e02a70e9f8542f11dbd08d8aca8afe9c7b29a46
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-and-configure-an-availability-group-for-sql-server-on-linux"></a>作成し、Linux 上の SQL Server の可用性グループを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このチュートリアルでは、作成し、可用性グループ (AG) を構成する方法を説明の[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Linux にします。 異なり[!INCLUDE[sssql15-md](../includes/sssql15-md.md)]以前 Windows では、有効にして Ag 有無にかかわらず、最初に基になるペース クラスターを作成します。 クラスターとの統合が必要な場合は行われません、後で。

このチュートリアルには、次のタスクが含まれています。
 
> [!div class="checklist"]
> * 可用性グループを有効にします。
> * 可用性グループのエンドポイントと証明書を作成します。
> * 使用して[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)](SSMS) または transact SQL 可用性グループを作成します。
> * 作成、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]ログインとペースのアクセス許可。
> * ペース クラスター (外部型のみ) で可用性グループのリソースを作成します。

## <a name="prerequisite"></a>前提条件
- 」の説明に従って、ペースの高可用性クラスターを展開[クラスターを展開するペース Linux に SQL Server の](sql-server-linux-deploy-pacemaker-cluster.md)します。


## <a name="enable-the-availability-groups-feature"></a>可用性グループ機能を有効にします。

異なり、Windows で使うことはできません PowerShell または[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Configuration Manager の可用性を有効にするグループ (AG) の機能です。 Linux で使用する必要があります`mssql-conf`機能を有効にします。 可用性グループ機能を有効にする 2 つの方法があります: を使用して、`mssql-conf`ユーティリティ、または編集、`mssql.conf`ファイルを手動でします。

> [!IMPORTANT]
> AG 機能を有効にする構成のみのレプリカの場合でも[!INCLUDE[ssexpress-md](../includes/ssexpress-md.md)]します。

### <a name="use-the-mssql-conf-utility"></a>Mssql conf ユーティリティを使用して

プロンプトで、次の手順を実行します。

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
```

### <a name="edit-the-mssqlconf-file"></a>Mssql.conf ファイルを編集します。

変更することも、`mssql.conf`の下にあるファイル、`/var/opt/mssql`フォルダーは、次の行を追加します。

```
[hadr]

hadr.hadrenabled = 1
```

### <a name="restart-includessnoversion-mdincludesssnoversion-mdmd"></a>再起動 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
Windows では、再起動する必要があります、可用性グループを有効にした後[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]です。 次のように行えます。

```bash
sudo systemctl restart mssql-server
```

## <a name="create-the-availability-group-endpoints-and-certificates"></a>可用性グループのエンドポイントと証明書を作成します。

可用性グループは、通信用の TCP エンドポイントを使用します。 Linux の下で、AG のエンドポイントは認証に証明書が使用されている場合のみサポートされます。 つまり、同じ可用性グループに参加しているレプリカとなるその他のすべてのインスタンスで 1 つのインスタンスからの証明書を復元する必要があります。 証明書の処理は、構成専用レプリカにも必要です。 

エンドポイントを作成して、証明書の復元は、TRANSACT-SQL 経由でのみ実行できます。 使用できる非[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-も証明書を生成します。 管理し、有効期限が切れる証明書を置換するためのプロセスも必要になります。

> [!IMPORTANT]
> 使用する場合、[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]それでも、可用性グループを作成するウィザードを作成し、Linux で TRANSACT-SQL を使用して、証明書を復元する必要があります。

(追加のセキュリティ) などのさまざまなコマンドに使用できるオプションの完全な構文を参照してください。

-   [BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)
-   [証明書を作成します。](../t-sql/statements/create-certificate-transact-sql.md)
-   [CREATE ENDPOINT](../t-sql/statements/create-endpoint-transact-sql.md)

> [!NOTE]
> エンドポイントの種類を使用して可用性グループを作成するが*FOR DATABASE_MIRRORING*、基になる点がここで非推奨機能と共有された 1 回ためです。

この例では、3 つのノード構成用の証明書を作成します。 インスタンス名は LinAGN1、LinAGN2、および LinAGN3 です。

1.  次のコードを実行して、マスター _ キー、証明書、およびエンドポイントを作成する LinAGN1 上だけでなく、証明書をバックアップします。 この例では、一般的な TCP ポート 5022 は、エンドポイントの使用されます。
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN1_Cert
    WITH SUBJECT = 'LinAGN1 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN1_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN1_Cert,
        ROLE = ALL);
    
    GO
    ```
    
2.  LinAGN2 で同じ操作を行います。
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN2_Cert
    WITH SUBJECT = 'LinAGN2 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN2_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN2_Cert,
        ROLE = ALL);
    
    GO
    ```
    
3.  最後に、LinAGN3 で同じシーケンスを実行します。
    
    ```SQL
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = '<StrongPassword>';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    WITH SUBJECT = 'LinAGN3 AG Certificate';
    
    GO
    
    BACKUP CERTIFICATE LinAGN3_Cert
    TO FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
    CREATE ENDPOINT AGEP
    STATE = STARTED
    AS TCP (
        LISTENER_PORT = 5022,
        LISTENER_IP = ALL)
    FOR DATABASE_MIRRORING (
        AUTHENTICATION = CERTIFICATE LinAGN3_Cert,
        ROLE = ALL);
    
    GO
    ```
    
4.  使用して`scp`または他のユーティリティ、証明書のバックアップを可用性グループの一部となる各ノードにコピーします。
    
    この例では。
    
    - LinAGN2 LinAGN3 へ LinAGN1_Cert.cer をコピーします。
    - LinAGN1 と LinAGN3 LinAGN2_Cert.cer にコピーします。
    - LinAGN1 と LinAGN2 LinAGN3_Cert.cer にコピーします。
    
5.  コピーした証明書ファイルに関連付けられているグループの所有権を変更する`mssql`です。
    
    ```bash
    sudo chown mssql:mssql <CertFileName>
    ```
    
6.  インスタンス レベルのログインと LinAGN2 と LinAGN1 で LinAGN3 に関連付けられているユーザーを作成します。
    
    ```SQL
    CREATE LOGIN LinAGN2_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN2_User FOR LOGIN LinAGN2_Login;
    
    GO
    
    CREATE LOGIN LinAGN3_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN3_User FOR LOGIN LinAGN3_Login;
    
    GO
    ```
    
7.  LinAGN2_Cert と LinAGN3_Cert LinAGN1 に復元します。 その他のレプリカの証明書が AG 通信およびセキュリティの重要な側面です。
    
    ```SQL
    CREATE CERTIFICATE LinAGN2_Cert
    AUTHORIZATION LinAGN2_User
    FROM FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    AUTHORIZATION LinAGN3_User
    FROM FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
8.  Grant the logins associated with LinAG2 and LinAGN3 permission to connect to the endpoint on LinAGN1.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN2_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN3_Login;
    
    GO
    ```
    
9.  インスタンス レベルのログインと LinAGN1 と LinAGN2 で LinAGN3 に関連付けられているユーザーを作成します。
    
    ```SQL
    CREATE LOGIN LinAGN1_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN1_User FOR LOGIN LinAGN1_Login;
    
    GO
    
    CREATE LOGIN LinAGN3_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN3_User FOR LOGIN LinAGN3_Login;
    
    GO
    ```
    
10.  LinAGN1_Cert と LinAGN3_Cert LinAGN2 に復元します。 
    
    ```SQL
    CREATE CERTIFICATE LinAGN1_Cert
    AUTHORIZATION LinAGN1_User
    FROM FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN3_Cert
    AUTHORIZATION LinAGN3_User
    FROM FILE = '/var/opt/mssql/data/LinAGN3_Cert.cer';
    
    GO
    
11.  Grant the logins associated with LinAG1 and LinAGN3 permission to connect to the endpoint on LinAGN2.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN1_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN3_Login;
    
    GO
    ```
    
12.  インスタンス レベルのログインと LinAGN1 と LinAGN3 で LinAGN2 に関連付けられているユーザーを作成します。
    
    ```SQL
    CREATE LOGIN LinAGN1_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN1_User FOR LOGIN LinAGN1_Login;
    
    GO
    
    CREATE LOGIN LinAGN2_Login WITH PASSWORD = '<StrongPassword>';
    CREATE USER LinAGN2_User FOR LOGIN LinAGN2_Login;
    
    GO
    ```
    
13.  LinAGN1_Cert と LinAGN2_Cert LinAGN3 に復元します。 
    
    ```SQL
    CREATE CERTIFICATE LinAGN1_Cert
    AUTHORIZATION LinAGN1_User
    FROM FILE = '/var/opt/mssql/data/LinAGN1_Cert.cer';
    
    GO
    
    CREATE CERTIFICATE LinAGN2_Cert
    AUTHORIZATION LinAGN2_User
    FROM FILE = '/var/opt/mssql/data/LinAGN2_Cert.cer';
    
    GO
    
14.  Grant the logins associated with LinAG1 and LinAGN2 permission to connect to the endpoint on LinAGN3.
    
    ```SQL
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN1_Login;
    
    GO
    
    GRANT CONNECT ON ENDPOINT::AGEP TO LinAGN2_Login;
    
    GO
    ```

## <a name="create-the-availability-group"></a>可用性グループを作成します。

このセクションを使用する方法を説明[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)](SSMS) またはの可用性グループを作成するには、TRANSACT-SQL[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]です。

### <a name="use-includessmanstudiofull-mdincludesssmanstudiofull-mdmd"></a>[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] を使用してください。

このセクションでは、SSMS を使用して、新しい可用性グループ ウィザードを使用して外部のクラスターの種類を可用性グループを作成する方法を示します。

1.  SSMS では、展開**Always On 高可用性**を右クリックして**可用性グループ**を選択して**新しい可用性グループ ウィザード**です。

2.  [概要] ダイアログ ボックスで、をクリックして**次**です。

3.  可用性グループ オプションの指定 ダイアログ ボックスで、可用性グループの名前を入力し、ドロップダウン リストで なし の外部のクラスターの種類を選択します。 ペースが配置されるときに、外部を使用する必要があります。 [なし] が、読み取りのスケール アウトなどの特殊なシナリオです。データベース レベルの正常性の検出のオプションを選択することはオプションです。 このオプションの詳細については、次を参照してください。[可用性グループ データベース レベルの正常性の検出フェールオーバー オプション](../database-engine/availability-groups/windows/sql-server-always-on-database-health-detection-failover-option.md)です。 **[次へ]** をクリックします。

    ![](./media/sql-server-linux-create-availability-group/image3.png)

4.  データベースの選択 ダイアログ ボックスで、可用性グループに参加するデータベースを選択します。 各データベースは、可用性グループに追加する前に、完全バックアップに必要です。 **[次へ]** をクリックします。

5.  レプリカの指定 ダイアログ ボックスでをクリックして**のレプリカ追加**です。

6.  サーバー ダイアログへの接続での Linux インスタンスの名前を入力してください。 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] 、セカンダリ レプリカとの接続に資格情報になります。 **[接続]** をクリックします。

7.  構成専用のレプリカまたは別のセカンダリ レプリカを格納するインスタンスの前の 2 つの手順を繰り返します。

8.  レプリカの指定 ダイアログで 3 つすべてのインスタンスが表示されます。 確認して、セカンダリの場合は true となるセカンダリ レプリカに対して、外部のクラスターの種類を使用する場合、プライマリ レプリカの可用性モードが一致してフェールオーバー モードが外部に設定します。 構成専用のレプリカのな可用性モードの構成のみを選択します。

    次の例では、2 つのレプリカ、外部のクラスターの種類の構成のみのレプリカと可用性グループを示します。

    ![](./media/sql-server-linux-create-availability-group/image4.png)

    次の例では、2 つのレプリカを可用性グループ、None、および構成専用のレプリカのクラスターの種類を示します。

    ![](./media/sql-server-linux-create-availability-group/image5.png)

9.  バックアップの設定を変更する場合は、バックアップの設定 タブをクリックします。Ag とバックアップの設定の詳細については、次を参照してください。[可用性レプリカでバックアップの構成](../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)です。

10. 読み取り可能セカンダリを使用するか、クラスターを備えた、可用性グループを作成する入力する場合読み取りスケールで [なし]、[リスナー] タブを選択してリスナーを作成できます。リスナーは、後で追加することもできます。 リスナーを作成するオプションを選択**可用性グループ リスナーを作成する**名、TCP/IP ポートと静的または自動的に割り当てられた DHCP IP アドレスを使用するかどうかを入力します。 静的および設定なしのクラスターの種類と、AG の IP 必要があることに留意プライマリの IP アドレスにします。

    ![](./media/sql-server-linux-create-availability-group/image6.png)

11. リスナーを作成する場合は読み取り可能なシナリオの 17.3 またはそれ以降の SSMS がウィザードで読み取り専用ルーティングの作成を許可します。 SSMS または TRANSACT-SQL を使用して後で、追加することもできます。 追加する読み取り専用ルーティングをようになりました。

    a.  読み取り専用ルーティング タブを選択します。

    b.  読み取り専用レプリカの Url を入力します。 エンドポイントではない、インスタンスのポートを使用する点を除いて、これらの Url は、エンドポイントに似ています。

    c.  各 URL を選択し、下から読み取り可能なレプリカを選択します。 複数選択して、押しながら shift キーまたはをクリックしてドラッグします。

12. **[次へ]** をクリックします。

13. セカンダリ レプリカの初期化方法を選択します。 既定値が使用するには[自動シード処理](../database-engine/availability-groups/windows/automatically-initialize-always-on-availability-group.md)、可用性グループに参加しているすべてのサーバー上の同じパスにする必要があります。 ウィザードはバックアップ、コピー、および (2 番目のオプション); を復元することもできます。手動でバックアップ、コピー、および、レプリカ上のデータベースを復元する場合に参加させて (オプション 3) です。データベースを後で追加または (最後のオプション)。 同様に証明書を手動でバックアップを作成すると、コピーすることは、バックアップ ファイルのアクセス許可を他のレプリカに設定する必要があります。 **[次へ]** をクリックします。

14. [検証] ダイアログ ボックスで、成功として戻すすべて作成されていない場合を調査します。 いくつかの警告は許容といない致命的などのリスナーを作成しない場合です。 **[次へ]** をクリックします。

15. [概要] ダイアログ ボックスで、をクリックして**完了**です。 可用性グループを作成するプロセスを開始します。

16. 可用性グループの作成が完了したらをクリックして**閉じる**結果にします。 レプリカの動的管理ビューおよび SSMS での Always On 高可用性フォルダーの下で、可用性グループを閲覧できます。

### <a name="use-transact-sql"></a>TRANSACT-SQL を使用します。

ここでは、TRANSACT-SQL を使用して、可用性グループを作成する例を示します。 可用性グループを作成した後は、リスナーと読み取り専用ルーティングを構成できます。 AG 自体を変更できますが`ALTER AVAILABILITY GROUP`でクラスターの種類の変更を行うことはできませんが、[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]です。 外部のクラスターのタイプ、可用性グループを作成するのでない、削除するして、なしのクラスターの種類で再作成します。 詳細については、その他のオプションは、次のリンクで見つかります。

-   [CREATE AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md)
-   [ALTER AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/alter-availability-group-transact-sql.md)
-   [読み取り専用ルーティングの可用性グループ (SQL Server) の構成します。](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)
-   [作成または構成する可用性グループ リスナー (SQL Server)](../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)

#### <a name="example-one--two-replicas-with-a-configuration-only-replica-external-cluster-type"></a>例 1: 2 レプリカ構成専用のレプリカ (外部クラスター型)

この例では、構成専用レプリカを使用する 2 つのレプリカの可用性グループを作成する方法を示します。

1.  データベースの完全読み取り/書き込みコピーを含む、プライマリ レプリカとなるノードで実行します。 この例では、自動シード処理を使用します。

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = EXTERNAL)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1' WITH (
       ENDPOINT_URL = N' TCP://LinAGN1.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT),
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       SEEDING_MODE = AUTOMATIC),
    N'LinAGN3' WITH (
       ENDPOINT_URL = N'TCP://LinAGN3.FullyQualified.Name:5022',
       AVAILABILITY_MODE = CONFIGURATION_ONLY);
       
    GO
    ```
    
2.  その他のレプリカに接続してクエリ ウィンドウで、可用性グループへのレプリカの参加し、セカンダリ レプリカにプライマリからシード処理プロセスを開始するには、次を実行します。
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  構成の唯一のレプリカに接続してクエリ ウィンドウで、可用性グループに参加します。
    
   ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
   ```

#### <a name="example-two--three-replicas-with-read-only-routing-external-cluster-type"></a>例 2 ~ 3 (外部のクラスターの種類) を読み取り専用ルーティング レプリカ

この例では 3 つすべてレプリカおよび読み取り専用ルーティングを最初に作成する可用性グループの一部として構成することができます。

1.  データベースの完全読み取り/書き込みコピーを含む、プライマリ レプリカとなるノードで実行します。 この例では、自動シード処理を使用します。

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = EXTERNAL)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1'
    WITH (
       ENDPOINT_URL = N'TCP://LinAGN1.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN2.FullyQualified.Name', 'LinAGN3.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN1.FullyQualified.Name:1433')),
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN3.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN2.FullyQualified.Name:1433')),
    N'LinAGN3' WITH (
       ENDPOINT_URL = N'TCP://LinAGN3.FullyQualified.Name:5022',
       FAILOVER_MODE = EXTERNAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN3.FullyQualified.Name:1433'))
    LISTENER '<ListenerName>' (WITH IP = ('<IPAddress>', '<SubnetMask>'), Port = 1433);
    
    GO
    ```
    
    この構成について注意するいくつかの点:
    
    - *AGName*可用性グループの名前を指定します。
    - *DBName*可用性グループに使用されるデータベースの名前を指定します。 一連のコンマで区切ってことができます。
    - *ListenerName*任意の基になるサーバー/ノードとは異なる名前を指定します。 と共に DNS に登録されます*IPAddress*です。
    - *IPAddress*に関連付けられている IP アドレスは、 *ListenerName*です。 一意でも、同じサーバー/ノードのいずれかではありません。 アプリケーションとエンドユーザーに使用される*ListenerName*または*IPAddress*可用性グループに接続します。
    - *SubnetMask*のサブネット マスクは、 *IPAddress*。 例: 255.255.255.0 です。

2.  その他のレプリカに接続してクエリ ウィンドウで、可用性グループへのレプリカの参加し、セカンダリ レプリカにプライマリからシード処理プロセスを開始するには、次を実行します。
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  3 番目のレプリカに対して手順 2. を繰り返します。

#### <a name="example-three--two-replicas-with-read-only-routing-none-cluster-type"></a>例 3-2 レプリカの読み取り専用ルーティング (None のクラスターの種類)

この例では、None のクラスターの種類を使用する、2 つのレプリカ構成の作成を示します。 ここでフェールオーバーする予定はありません、読み取りスケール シナリオに使用されます。 これには、ラウンド ロビン機能を使用して実際には、プライマリ レプリカだけでなく、読み取り専用ルーティングでは、リスナーが作成されます。

1.  データベースの完全読み取り/書き込みコピーを含む、プライマリ レプリカとなるノードで実行します。 この例では、自動シード処理を使用します。

    ```SQL
    CREATE AVAILABILITY GROUP [<AGName>]
    WITH (CLUSTER_TYPE = NONE)
    FOR DATABASE <DBName>
    REPLICA ON N'LinAGN1'
    WITH (
       ENDPOINT_URL = N'TCP://LinAGN1.FullyQualified.Name: <PortOfEndpoint>',
       FAILOVER_MODE = MANUAL,
       AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name'.'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL = N'TCP://LinAGN1.FullyQualified.Name:<PortOfInstance>'));
    N'LinAGN2' WITH (
       ENDPOINT_URL = N'TCP://LinAGN2.FullyQualified.Name:<PortOfEndpoint>',
       FAILOVER_MODE = MANUAL,
       SEEDING_MODE = AUTOMATIC,
       AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
       PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE, READ_ONLY_ROUTING_LIST = (('LinAGN1.FullyQualified.Name', 'LinAGN2.FullyQualified.Name'))),
       SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL, READ_ONLY_ROUTING_URL =N'TCP://LinAGN2.FullyQualified.Name:<PortOfInstance>'));
    LISTENER '<ListenerName>' (WITH IP = ('<PrimaryReplicaIPAddress>', '<SubnetMask>'), Port = <PortOfListener>);
    
    GO
    ```
    
    場所
    - *AGName*可用性グループの名前を指定します。
    - *DBName*可用性グループに使用されるデータベースの名前を指定します。 一連のコンマで区切ってことができます。
    - *PortOfEndpoint*作成されたエンドポイントによって使用されるポート番号です。
    - *PortOfInstance*のインスタンスによって使用されるポート番号は、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]です。
    - *ListenerName*名前を指定すると、任意のレプリカを基になるとは異なりますが、実際には使用されません。
    - *PrimaryReplicaIPAddress*は、プライマリ レプリカの IP アドレスです。
    - *SubnetMask*のサブネット マスクは、 *IPAddress*です。 たとえば、255.255.255.0 です。
    
2.  セカンダリ レプリカを可用性グループに参加させるし、自動シード処理を開始します。
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = NONE);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```

## <a name="create-the-includessnoversion-mdincludesssnoversion-mdmd-login-and-permissions-for-pacemaker"></a>作成、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]ログインとペースのアクセス許可

ペースの高可用性クラスターの基になる[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Linux 上へのアクセスが必要、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]自体の可用性グループに対するアクセス許可と同様に、インスタンス。 次の手順の作成、ログインおよび関連付けられているアクセス許可のペースにログインする方法について説明するファイルと共に[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]です。

1.  最初のレプリカに接続してクエリ ウィンドウで、次の手順を実行します。

    ```SQL
    CREATE LOGIN PMLogin WITH PASSWORD '<StrongPassword>';
    
    GO
    
    GRANT VIEW SERVER STATE TO PMLogin;
    
    GO
    
    GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::<AGThatWasCreated> TO PMLogin;
    
    GO
    ```
    
2.  ノード 1 では、コマンドを入力してください。 
    ```bash
    sudo emacs /var/opt/mssql/secrets/passwd
    ```
    
    Emacs のエディターが開きます。
    
3.  エディターには、次の 2 行を入力してください。

    ```
    PMLogin
    <StrongPassword>
    ```
    
4.  CTRL キーを押しながら押し X、し、C ファイルを保存して終了します。

5.  Execute 
    ```bash
    sudo chmod 400 /var/opt/mssql/secrets/passwd
    ```
    
    ファイルをロックします。

6.  レプリカとして使用する他のサーバーで手順 1. ~ 5. を繰り返します。

## <a name="create-the-availability-group-resources-in-the-pacemaker-cluster-external-only"></a>ペース クラスター (外部のみ) で、可用性グループのリソースを作成します。

可用性グループが作成[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]外部のクラスターの種類を指定すると、ペースで対応するリソースを作成する必要があります。 可用性グループに関連付けられている 2 つのリソース: AG 自身と IP アドレス。 IP アドレス リソースの構成は省略可能な場合にリスナーの機能を使用していないをお勧めします。

作成される可用性グループ リソースは、リソースの複製と呼ばれる特殊なです。 可用性グループ リソース本質的にコピー、各ノードに持ち、マスターと呼ばれる 1 つの制御するリソースが存在します。 マスターは、プライマリ レプリカをホストしているサーバーに関連付けられています。 セカンダリ レプリカ (定期的または構成専用) と、スレーブと見なされ、型に昇格できますフェールオーバーでは master です。

1.  次の構文で、可用性グループ リソースを作成します。

    **Red Hat Enterprise Linux (RHEL) および Ubuntu**
    
    ```bash
    sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> --master meta notify=true
    ```

    >[!NOTE]
    >RHEL 7.4 で master データベースの使用で警告が発生する可能性があります。 これを回避するには、次のように使用します。 `sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> master notify=true`
   
    **SUSE Linux Enterprise Server (SLES)**
    
    ```bash
    primitive <NameForAGResource> \
    ocf:mssql:ag \
    params ag_name="<AGName>" \
    op start timeout=60s \
    op stop timeout=60s \
    op promote timeout=60s \
    op demote timeout=10s \
    op monitor timeout=60s interval=10s \
    op monitor timeout=60s interval=11s role="Master" \
    op monitor timeout=60s interval=12s role="Slave" \
    op notify timeout=60s
    ms ms-ag_cluster <NameForAGResource> \
    meta master-max="1" master-node-max="1" clone-max="3" \
    clone-node-max="1" notify="true" \
    commit
    ```
    
    場所*NameForAGResource* 、可用性グループのクラスター リソースに指定された一意の名前と*AGName*が作成された可用性グループの名前を指定します。
 
2.  リスナーの機能に関連付けられる、AG の IP アドレス リソースを作成します。

    **RHEL および Ubuntu**
    
    ```bash
    sudo pcs resource create <NameForIPResource> ocf:heartbeat:IPaddr2 ip=<IPAddress> cidr_netmask=<Netmask>
    ```

    **SLES**
    
    ```bash
    crm configure \
    primitive <NameForIPResource> \
       ocf:heartbeat:IPaddr2 \
       params ip=<IPAddress> \
          cidr_netmask=<Netmask>
    ```
    
    場所*NameForIPResource* IP リソースの一意の名前と*IPAddress*リソースに割り当てられている静的 IP アドレスです。 Sles、ネットマスクを指定する必要があります。 たとえば、255.255.255.0、値はの 24*ネットマスク。*
    
3.  IP アドレスと、可用性グループ リソースが同じノードで実行されていることを確認してください、コロケーションの制約を構成する必要があります。

    **RHEL および Ubuntu**
    
    ```bash
    sudo pcs constraint colocation add <NameForIPResource> <NameForAGResource>-master INFINITY with-rsc-role=Master
    ```

    **SLES**
    
    ```bash
    crm configure <NameForConstraint> inf: \
    <NameForIPResource> <NameForAGResource>:Master 
    commit
    ```
    
    場所*NameForIPResource* IP リソースの名前を指定します*NameForAGResource* sles については、可用性グループ リソースの名前は、 *NameForConstraint*の名前を指定します制約です。

4.  オーダリングの制約を可用性グループ リソースがあることを確認して、IP アドレスの前に実行を作成します。 コロケーションの制約には、順序付けの制約がからわかるように、中に、実施します。

    **RHEL および Ubuntu**
    
    ```bash
    sudo pcs constraint order promote <NameForAGResource>-master then start <NameForIPResource>
    ```
    
    **SLES**
    
    ```bash
    crm configure \
    order <NameForConstraint> inf: <NameForAGResource>:promote <NameForIPResource>:start
    commit
    ```
    
    場所*NameForIPResource* IP リソースの名前を指定します*NameForAGResource* sles については、可用性グループ リソースの名前は、 *NameForConstraint*の名前を指定します制約です。

## <a name="next-steps"></a>次の手順

このチュートリアルで作成し、可用性グループを構成する方法を学習した[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Linux にします。 方法を学習します。
> [!div class="checklist"]
> * 可用性グループを有効にします。
> * 作成する可用性グループのエンドポイントと証明書。
> * 使用して[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)](SSMS) または、可用性グループを作成するには、TRANSACT-SQL です。
> * 作成、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]ログインとペースのアクセス許可。
> * ペース クラスターで可用性グループ リソースを作成します。

、、のフェールオーバーやアップグレードを含む、ほとんどの AG 管理タスクを参照してください。

> [!div class="nextstepaction"]
> [SQL Server on Linux の HA 可用性グループを操作します。](sql-server-linux-availability-group-failover-ha.md)

