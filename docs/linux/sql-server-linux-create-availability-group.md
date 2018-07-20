---
title: 作成し、SQL Server on Linux の可用性グループの構成 |Microsoft Docs
description: このチュートリアルでは、作成して、SQL Server on Linux の可用性グループを構成する方法を示します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 06/28/2018
ms.topic: conceptual
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.openlocfilehash: 21ca1eea093121107b2e04cff40b6f749a6c6bda
ms.sourcegitcommit: c8f7e9f05043ac10af8a742153e81ab81aa6a3c3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39083494"
---
# <a name="create-and-configure-an-availability-group-for-sql-server-on-linux"></a>作成し、SQL Server on Linux の可用性グループの構成

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このチュートリアルを作成し、可用性グループ (AG) を構成する方法をについて説明[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Linux 上。 異なり[!INCLUDE[sssql15-md](../includes/sssql15-md.md)]し前で、Windows を実行する Ag 有無にかかわらず、最初に、基になる Pacemaker クラスターを作成します。 クラスターとの統合が必要な場合は行われません、後で。

このチュートリアルには、次のタスクが含まれています。
 
> [!div class="checklist"]
> * 可用性グループを有効にします。
> * 可用性グループのエンドポイントと証明書を作成します。
> * 使用[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)](SSMS) または可用性グループを作成するには、TRANSACT-SQL です。
> * 作成、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]ログインと Pacemaker 用のアクセスを許可します。
> * Pacemaker クラスター (外部型のみ) で可用性グループ リソースを作成します。

## <a name="prerequisite"></a>前提条件
- 」の説明に従って、Pacemaker の高可用性クラスターをデプロイ[SQL Server on Linux の Pacemaker クラスターをデプロイ](sql-server-linux-deploy-pacemaker-cluster.md)します。


## <a name="enable-the-availability-groups-feature"></a>可用性グループの機能を有効にします。

異なり、Windows にすることはできませんを使用して、PowerShell または[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Configuration Manager の可用性を有効にするグループ (AG) の機能です。 Linux で使用する必要があります`mssql-conf`機能を有効にします。 可用性グループ機能を有効にする 2 つの方法があります: を使用して、`mssql-conf`ユーティリティ、または編集、`mssql.conf`ファイルを手動でします。

> [!IMPORTANT]
> AG 機能は構成専用レプリカの場合であっても有効にする必要があります[!INCLUDE[ssexpress-md](../includes/ssexpress-md.md)]します。

### <a name="use-the-mssql-conf-utility"></a>Mssql conf ユーティリティを使用して

プロンプトで、次の手順を実行します。

```bash
sudo /opt/mssql/bin/mssql-conf set hadr.hadrenabled 1
```

### <a name="edit-the-mssqlconf-file"></a>Mssql.conf ファイルを編集します。

変更することも、`mssql.conf`下にあるファイル、`/var/opt/mssql`フォルダーは、次の行を追加します。

```
[hadr]

hadr.hadrenabled = 1
```

### <a name="restart-includessnoversion-mdincludesssnoversion-mdmd"></a>再起動 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]
再起動する必要があります、Windows と、可用性グループを有効にした後[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]します。 次のようにできます。

```bash
sudo systemctl restart mssql-server
```

## <a name="create-the-availability-group-endpoints-and-certificates"></a>可用性グループのエンドポイントと証明書を作成します。

可用性グループは、通信に TCP エンドポイントを使用します。 Linux では、AG のエンドポイントは認証に証明書を使用する場合のみサポートされます。 つまり、同じ AG に参加しているレプリカとなるその他のすべてのインスタンスで 1 つのインスタンスからの証明書を復元する必要があります。 証明書の処理は、構成専用レプリカにも必要です。 

エンドポイントを作成して、証明書を復元するには TRANSACT-SQL を介してのみ実行できます。 以外を使用することができます[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]-も証明書を生成します。 また、プロセスの管理し、有効期限が切れる証明書を置換する必要もあります。

> [!IMPORTANT]
> 使用する場合、[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)]が可用性グループを作成するウィザードを作成し、Linux で TRANSACT-SQL を使用して、証明書を復元する必要があります。

(追加のセキュリティ) などのさまざまなコマンドで使用できるオプションの完全な構文を参照してください。

-   [BACKUP CERTIFICATE](../t-sql/statements/backup-certificate-transact-sql.md)
-   [証明書を作成します。](../t-sql/statements/create-certificate-transact-sql.md)
-   [CREATE ENDPOINT](../t-sql/statements/create-endpoint-transact-sql.md)

> [!NOTE]
> エンドポイントの種類を使用して可用性グループを作成しても*FOR DATABASE_MIRRORING*基になる点がありますが現在非推奨機能と共有された 1 回ためです。

この例では、3 つのノード構成用の証明書を作成します。 LinAGN1、LinAGN2、LinAGN3、インスタンス名。

1.  LinAGN1 マスター_キー、証明書、およびエンドポイントを作成すると、証明書のバックアップは、次を実行します。 この例で 5022 の一般的な TCP ポートがエンドポイントの使用します。
    
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
    
4.  使用して`scp`または他のユーティリティ、可用性グループの一部となる各ノードに証明書のバックアップをコピーします。
    
    この例では。
    
    - LinAGN2 と LinAGN3 LinAGN1_Cert.cer にコピーします。
    - LinAGN1 と LinAGN3 LinAGN2_Cert.cer にコピーします。
    - LinAGN1 と LinAGN2 LinAGN3_Cert.cer にコピーします。
    
5.  所有権とにコピーした証明書ファイルに関連付けられているグループを変更`mssql`します。
    
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
    
7.  LinAGN2_Cert と LinAGN3_Cert LinAGN1 に復元します。 証明書の他のレプリカの AG の通信およびセキュリティの重要な側面です。
    
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

使用する方法について説明[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)](SSMS) の可用性グループを作成するには、TRANSACT-SQL または[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]します。

### <a name="use-includessmanstudiofull-mdincludesssmanstudiofull-mdmd"></a>[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)] を使用してください。

このセクションでは、新しい可用性グループ ウィザードを使用して SSMS を使用して外部のクラスターの種類で、AG を作成する方法を示します。

1.  SSMS で、展開**Always On 高可用性**を右クリックして**可用性グループ**、選択と**新しい可用性グループ ウィザード**します。

2.  [概要] ダイアログで次のようにクリックします。**次**します。

3.  可用性グループ オプションの指定] ダイアログ ボックスで、可用性グループの名前を入力し、[EXTERNAL または NONE、ドロップダウン リストでのクラスターの種類を選択します。 Pacemaker が配置されるときに、外部を使用する必要があります。 [なし] は、読み取りスケール アウトなどの特殊なシナリオ用です。データベース レベルの正常性検出オプションを選択するは省略可能です。 このオプションの詳細については、次を参照してください。[可用性グループのデータベース レベルの正常性検出フェールオーバー オプション](../database-engine/availability-groups/windows/sql-server-always-on-database-health-detection-failover-option.md)します。 **[次へ]** をクリックします。

    ![](./media/sql-server-linux-create-availability-group/image3.png)

4.  データベースの選択 ダイアログ ボックスで、可用性グループに参加するデータベースを選択します。 各データベースは、AG に追加する前に、完全バックアップにすることが必要です。 **[次へ]** をクリックします。

5.  レプリカの指定 ダイアログ ボックスで次のようにクリックします。**のレプリカ追加**します。

6.  サーバーのダイアログへの接続での Linux インスタンスの名前を入力します。 [!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)] 、セカンダリ レプリカとの接続に資格情報になります。 **[接続]** をクリックします。

7.  構成のみのレプリカまたは別のセカンダリ レプリカを含むインスタンスの前の 2 つの手順を繰り返します。

8.  レプリカの指定 ダイアログで次の 3 つすべてのインスタンスが表示されます。 には true。 セカンダリとなるセカンダリ レプリカを、外部のクラスターの種類を使用して場合、プライマリ レプリカの可用性モードが一致して、フェールオーバー モードは External に設定されていることを確認します。 構成のみのレプリカ、可用性モードの構成のみを選択します。

    次の例では、2 つのレプリカ、クラスターの種類の外部の構成のみのレプリカと AG を示します。

    ![](./media/sql-server-linux-create-availability-group/image4.png)

    次の例では、2 つのレプリカと AG、None、および構成のみのレプリカのクラスターの種類を示します。

    ![](./media/sql-server-linux-create-availability-group/image5.png)

9.  バックアップの設定を変更する場合は、バックアップの設定 タブをクリックします。Ag でのバックアップの設定の詳細については、次を参照してください。[可用性レプリカでバックアップの構成](../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)します。

10. 読み取りスケールなしの型読み取り可能なセカンダリを使用して、またはクラスターでの AG を作成する場合は、[リスナー] タブを選択してリスナーを作成できます。リスナーは、後でも追加できます。 リスナーを作成するオプションを選択**可用性グループ リスナーの作成**名前、TCP/IP ポート、および静的または自動的に割り当てられた DHCP IP アドレスを使用するかどうかを入力します。 静的および設定が None のクラスターの種類で、AG の ip アドレスがあることに注意してください。 プライマリの IP アドレスにします。

    ![](./media/sql-server-linux-create-availability-group/image6.png)

11. リスナーを作成する場合は読み取り可能なシナリオの SSMS 17.3 以降は、ウィザードで読み取り専用ルーティングの作成を許可します。 SSMS または TRANSACT-SQL を使用して後で、追加することもできます。 読み取り専用ルーティングを今すぐに追加するには

    A.  読み取り専用ルーティング タブを選択します。

    B.  読み取り専用レプリカの Url を入力します。 エンドポイントではない、インスタンスのポートを使用する点を除いて、これらの Url は、エンドポイントに似ています。

    c.  各 URL を選択し、下から読み取り可能なレプリカを選択します。 複数選択は、shift キーまたはクリック アンド ドラッグを押しします。

12. **[次へ]** をクリックします。

13. セカンダリ レプリカを初期化する方法を選択します。 既定値が使用するには[自動シード処理](../database-engine/availability-groups/windows/automatically-initialize-always-on-availability-group.md)AG に参加しているすべてのサーバー上の同じパス必要があります。 ウィザードはバックアップ、コピー、および (2 番目のオプション); を復元することもできます。手動でバックアップ、コピー、およびレプリカ上のデータベースを復元する場合に参加させて (オプション 3)。または、データベースを後で追加 (最後のオプション)。 証明書を手動でバックアップを作成してにコピーする場合と同様、バックアップ ファイルのアクセス許可は、その他のレプリカに設定する必要があります。 **[次へ]** をクリックします。

14. [検証] ダイアログで成功として戻すすべて提供されない場合が調査します。 いくつかの警告とは、許容され、致命的でないなどのリスナーを作成しない場合です。 **[次へ]** をクリックします。

15. [概要] ダイアログで次のようにクリックします。**完了**します。 可用性グループを作成するプロセスを開始します。

16. AG の作成が完了したら、クリックして**閉じる**結果にします。 SSMS の Always On 高可用性フォルダーの下や動的管理ビューでのレプリカで可用性グループがわかります。

### <a name="use-transact-sql"></a>TRANSACT-SQL を使用します。

このセクションでは、TRANSACT-SQL を使用して AG を作成する例を示します。 可用性グループを作成した後、リスナーと読み取り専用ルーティングを構成できます。 AG 自体を変更できますが`ALTER AVAILABILITY GROUP`、クラスターの種類の変更実行することはできませんが、[!INCLUDE[sssql17-md](../includes/sssql17-md.md)]します。 AG を作成する外部のクラスターの種類でない場合は、削除し、None のクラスターの種類で再作成する必要があります。 詳細については、その他のオプションは、次のリンクで見つかります。

-   [CREATE AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/create-availability-group-transact-sql.md)
-   [ALTER AVAILABILITY GROUP (Transact-SQL)](../t-sql/statements/alter-availability-group-transact-sql.md)
-   [読み取り専用ルーティングの可用性グループ (SQL Server) の構成します。](../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md)
-   [作成または可用性グループ リスナー (SQL Server) の構成](../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)

#### <a name="example-one--two-replicas-with-a-configuration-only-replica-external-cluster-type"></a>例 1-2 レプリカ構成のみのレプリカ (外部のクラスターの種類)

この例では、構成専用レプリカを使用する 2 つのレプリカの可用性グループを作成する方法を示します。

1.  データベースの完全読み取り/書き込みコピーを格納しているプライマリ レプリカとなるノードで実行します。 この例では、自動シード処理を使用します。

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
    
2.  その他のレプリカに接続してクエリ ウィンドウで、レプリカを AG に参加させるし、セカンダリ レプリカにプライマリからシード処理プロセスを開始するには、次を実行します。
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  構成のみのレプリカに接続されているクエリ ウィンドウで、可用性グループに参加します。
    
   ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
   ```

#### <a name="example-two--three-replicas-with-read-only-routing-external-cluster-type"></a>例 2 ~ 3 レプリカの読み取り専用ルーティング (外部のクラスターの種類)

この例では 3 つの完全なレプリカとどのように読み取り専用ルーティングは、最初に作成する可用性グループの一部として構成できます。

1.  データベースの完全読み取り/書き込みコピーを格納しているプライマリ レプリカとなるノードで実行します。 この例では、自動シード処理を使用します。

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
    - *DBName*可用性グループで使用されるデータベースの名前を指定します。 一連の名をコンマで区切られたことができます。
    - *ListenerName*任意のサーバー/ノードを基になるとは異なる名前を指定します。 と共に DNS に登録されます*IPAddress*します。
    - *IPAddress*に関連付けられている IP アドレスは、 *ListenerName*します。 一意であることも、任意のサーバー/ノードとは異なります。 アプリケーションとエンドユーザーはいずれかで使用されます*ListenerName*または*IPAddress* AG に接続します。
    - *SubnetMask*のサブネット マスクは、 *IPAddress*。 例: 255.255.255.0 です。

2.  その他のレプリカに接続してクエリ ウィンドウで、レプリカを AG に参加させるし、セカンダリ レプリカにプライマリからシード処理プロセスを開始するには、次を実行します。
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```
    
3.  3 番目のレプリカに対して、手順 2. を繰り返します。

#### <a name="example-three--two-replicas-with-read-only-routing-none-cluster-type"></a>例 3-2 レプリカの読み取り専用ルーティング (None クラスターの種類)

この例では、None のクラスターの種類を使用して、2 つのレプリカ構成の作成を示します。 フェールオーバーする必要はありません、読み取りスケールのシナリオに使用されます。 これは実際には、プライマリ レプリカだけでなく、読み取り専用ルーティング、ラウンド ロビンの機能を使用してリスナーを作成します。

1.  データベースの完全読み取り/書き込みコピーを格納しているプライマリ レプリカとなるノードで実行します。 この例では、自動シード処理を使用します。

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
    - *DBName*可用性グループで使用されるデータベースの名前を指定します。 一連の名をコンマで区切られたことができます。
    - *PortOfEndpoint*は作成されたエンドポイントによって使用されるポート番号です。
    - *PortOfInstance*のインスタンスによって使用されるポート番号は、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]します。
    - *ListenerName*名前を指定する任意のレプリカを基になるとは異なりますが、実際には使用されません。
    - *PrimaryReplicaIPAddress*はプライマリ レプリカの IP アドレスです。
    - *SubnetMask*のサブネット マスクは、 *IPAddress*します。 たとえば、255.255.255.0 です。
    
2.  セカンダリ レプリカを可用性グループに参加し、自動シード処理を開始します。
    
    ```SQL
    ALTER AVAILABILITY GROUP [<AGName>] JOIN WITH (CLUSTER_TYPE = NONE);
    
    GO
    
    ALTER AVAILABILITY GROUP [<AGName>] GRANT CREATE ANY DATABASE;
    
    GO
    ```

## <a name="create-the-includessnoversion-mdincludesssnoversion-mdmd-login-and-permissions-for-pacemaker"></a>作成、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]ログインと Pacemaker 用のアクセス許可

Pacemaker の高可用性クラスター基[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]on Linux へのアクセスが必要、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]自体の可用性グループに対するアクセス許可と同様に、インスタンス。 次の手順の作成、ログインおよび関連付けられたアクセス許可で、Pacemaker にログインする方法を指示するファイルと共に[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]します。

1.  最初のレプリカに接続されているクエリ ウィンドウで、次の手順を実行します。

    ```SQL
    CREATE LOGIN PMLogin WITH PASSWORD '<StrongPassword>';
    
    GO
    
    GRANT VIEW SERVER STATE TO PMLogin;
    
    GO
    
    GRANT ALTER, CONTROL, VIEW DEFINITION ON AVAILABILITY GROUP::<AGThatWasCreated> TO PMLogin;
    
    GO
    ```
    
2.  ノード 1 で、コマンドを入力します。 
    ```bash
    sudo emacs /var/opt/mssql/secrets/passwd
    ```
    
    これにより、Emacs エディターが開きます。
    
3.  エディターには、次の 2 つの行を入力します。

    ```
    PMLogin
    <StrongPassword>
    ```
    
4.  CTRL キーを押しながらし、し、C を終了し、ファイルを保存、X キーを押します。

5.  Execute 
    ```bash
    sudo chmod 400 /var/opt/mssql/secrets/passwd
    ```
    
    ファイルをロックします。

6.  レプリカとして使用する他のサーバーで手順 1. ~ 5. を繰り返します。

## <a name="create-the-availability-group-resources-in-the-pacemaker-cluster-external-only"></a>Pacemaker クラスター (外部のみ) で、可用性グループ リソースを作成します。

可用性グループが作成されます[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]外部のクラスターの種類を指定した場合、pacemaker、対応するリソースを作成する必要があります。 AG に関連付けられている 2 つのリソースがある: AG 自身と IP アドレス。 お勧めしますが、リスナーの機能を使用していない場合、IP アドレス リソースの構成は省略可能です。

作成される可用性グループ リソースでは、特殊な複製と呼ばれるリソースです。 AG リソースがコピーを各ノードで、基本的には、マスターと呼ばれる 1 つの制御するリソース。 マスターは、プライマリ レプリカをホストするサーバーと関連付けられます。 (正規表現または構成のみ) のセカンダリ レプリカがスレーブと見なされに昇格できる、フェールオーバーでは、マスターです。

1.  次の構文で、可用性グループ リソースを作成します。

    **Red Hat Enterprise Linux (RHEL) および Ubuntu**
    
    ```bash
    sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> meta failure-timeout=30s --master meta notify=true
    ```

    >[!NOTE]
    >RHEL 7.4 でという警告がマスターの使用が発生する可能性があります。 これを回避するには、次のように使用します。 `sudo pcs resource create <NameForAGResource> ocf:mssql:ag ag_name=<AGName> meta failover-timeout=30s master notify=true`
   
    **SUSE Linux Enterprise Server (SLES)**
    
    ```bash
    primitive <NameForAGResource> \
    ocf:mssql:ag \
    params ag_name="<AGName>" \
    meta failure-timeout=60s \
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
    
    場所*NameForAGResource*可用性グループには、このクラスター リソースに指定された一意の名前と*AGName*作成された可用性グループの名前を指定します。
 
2.  可用性グループ リスナーの機能に関連付けられる IP アドレス リソースを作成します。

    **RHEL と Ubuntu**
    
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
    
    場所*NameForIPResource* 、IP リソースの一意の名前と*IPAddress*リソースに割り当てられた静的 IP アドレスです。 Sles、ネットマスクを提供する必要があります。 たとえば、255.255.255.0、値の 24 の*ネットマスク。*
    
3.  IP アドレスおよび AG リソースが同じノードで実行されていることを確認するには、コロケーションの制約を構成する必要があります。

    **RHEL と Ubuntu**
    
    ```bash
    sudo pcs constraint colocation add <NameForIPResource> <NameForAGResource>-master INFINITY with-rsc-role=Master
    ```

    **SLES**
    
    ```bash
    crm configure <NameForConstraint> inf: \
    <NameForIPResource> <NameForAGResource>:Master 
    commit
    ```
    
    場所*NameForIPResource* IP リソースに名前を指定します*NameForAGResource* sles、AG リソースの名前は、 *NameForConstraint*の名前を指定します、制約です。

4.  可用性グループ リソースが稼働していることを確認する制約を順序付けと IP アドレスの前に実行を作成します。 コロケーションの制約では、順序付けの制約からわかるように、中に、これを強制します。

    **RHEL と Ubuntu**
    
    ```bash
    sudo pcs constraint order promote <NameForAGResource>-master then start <NameForIPResource>
    ```
    
    **SLES**
    
    ```bash
    crm configure \
    order <NameForConstraint> inf: <NameForAGResource>:promote <NameForIPResource>:start
    commit
    ```
    
    場所*NameForIPResource* IP リソースに名前を指定します*NameForAGResource* sles、AG リソースの名前は、 *NameForConstraint*の名前を指定します、制約です。

## <a name="next-steps"></a>次のステップ

このチュートリアルで作成し、可用性グループを構成する方法について説明しました[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]Linux 上。 学習したします。
> [!div class="checklist"]
> * 可用性グループを有効にします。
> * 作成する可用性グループのエンドポイントと証明書。
> * 使用[!INCLUDE[ssmanstudiofull-md](../includes/ssmanstudiofull-md.md)](SSMS) または AG を作成するには、TRANSACT-SQL です。
> * 作成、[!INCLUDE[ssnoversion-md](../includes/ssnoversion-md.md)]ログインと Pacemaker 用のアクセスを許可します。
> * Pacemaker クラスターで可用性グループ リソースを作成します。

、アップグレード、フェールオーバーなど、ほとんどの AG の管理タスクを参照してください。

> [!div class="nextstepaction"]
> [SQL Server on Linux の HA 可用性グループを操作します。](sql-server-linux-availability-group-failover-ha.md)

