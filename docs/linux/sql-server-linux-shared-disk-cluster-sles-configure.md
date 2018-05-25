---
title: SQL Server の SLES 共有ディスク クラスターの構成 |Microsoft ドキュメント
description: SQL Server の SUSE Linux Enterprise Server (SLES) 共有ディスク クラスターを構成することによって高可用性を実装します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: e5ad1bdd-c054-4999-a5aa-00e74770b481
ms.openlocfilehash: 5c394dbfc613803a8f7eb0cf906b4b7733777919
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
---
# <a name="configure-sles-shared-disk-cluster-for-sql-server"></a>SQL Server の SLES 共有ディスク クラスターを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このガイドでは、SQL Server SUSE Linux Enterprise Server (SLES) 上の 2 ノードの共有ディスク クラスターを作成する方法を提供します。 クラスタ リングのレイヤーが SUSE に基づいて[高可用性の拡張機能 (HAE)](https://www.suse.com/products/highavailability)の上に構築[ペース](http://clusterlabs.org/)です。 

クラスターの構成、リソース エージェント オプション、管理、ベスト プラクティス、および推奨事項の詳細については、次を参照してください。 [SUSE Linux Enterprise 高可用性拡張子 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html)です。

## <a name="prerequisites"></a>前提条件

次のエンド ツー エンドのシナリオを完了するには、2 つのマシンを 2 つのノードのクラスターと NFS 共有を構成する別のサーバーを展開する必要があります。 以下の手順には、これらのサーバーを構成する方法を説明します。

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>各クラスター ノードで、オペレーティング システムのセットアップと構成をする

最初の手順では、クラスター ノードで、オペレーティング システムを構成します。 このチュートリアルで、有効なサブスクリプションでの HA アドオン SLES を使用します。

## <a name="install-and-configure-sql-server-on-each-cluster-node"></a>各クラスター ノードで、SQL Server のインストールと構成をする

1. 両方のノード上に SQL Server をインストールし、セットアップします。 詳細については、次を参照してください。 [Linux 上の SQL Server のインストール](sql-server-linux-setup.md)です。
2. 構成のために、1つのノードをプライマリとして指定し、もう片方をセカンダリとして指定します。 このガイドでは、これ以降これらの用語を使用します。 
3. セカンダリ ノードでSQL Server を停止し無効にします。 次の例では、SQL Server を停止して無効にします。

    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE]
    > セットアップ時に、SQL Server インスタンスのためにサーバー マスター キーが生成され、`/var/opt/mssql/secrets/machine-key` に配置されます。 Linux では、SQL Server は、常に mssql と呼ばれるローカル アカウントとして実行されます。 ローカル アカウントであるため、その id はノード間で共有されません。 したがって、各ローカル mssql アカウント がサーバー マスター  キーの暗号化を解除するためにアクセスできるようにするために、各セカンダリ ノードにプライマリ ノードから暗号化キーをコピーする必要があります。
4. プライマリ ノードで、ペースの SQL server ログインの作成および実行する権限をログイン`sp_server_diagnostics`です。 ペースでは、このアカウントを使用して、どのノードが SQL Server を実行していることを確認します。

    ```bash
    sudo systemctl start mssql-server
    ```
    'Sa' アカウントを使用して SQL Server マスター データベースに接続し、次を実行します。

    ```tsql
    USE [master]
    GO
    CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
    GRANT VIEW SERVER STATE TO <loginName>
    ```
5. プライマリ ノードで、SQL Server を停止し無効にします。
6. 指示に従い[SUSE ドキュメント](https://www.suse.com/documentation/sles11/book_sle_admin/data/sec_basicnet_yast.html)を構成し、各クラスター ノードの hosts ファイルを更新します。 'Hosts' ファイルには、すべてのクラスター ノードの名前と IP アドレスを含める必要があります。

    実行する現在のノードの IP アドレスを確認してください。

    ```bash
    sudo ip addr show
    ```

    各ノードで、コンピューター名を設定します。 各ノードに 15 文字以下の一意の名前を指定します。 追加することによって、コンピューター名を設定`/etc/hostname`を使用して[yast](https://www.suse.com/documentation/sles11/book_sle_admin/data/sec_basicnet_yast.html)または[手動で](https://www.suse.com/documentation/sled11/book_sle_admin/data/sec_basicnet_manconf.html)です。

    次の`/etc/hosts`の例は`SLES1`と`SLES2`という名前の 2 つのノードの追加します。

    ```
    127.0.0.1   localhost
    10.128.18.128 SLES1
    10.128.16.77 SLES2
    ```

    > [!NOTE]
    > すべてのクラスター ノードでは、SSH を使用して相互にアクセスできる必要があります。 hb_report or crm_report (トラブルシューティング用) などのツールや Hawk の History Explorer では、ノード間でパスワードなしの SSH アクセスが必要です。それ以外の場合は、現在のノード以外のデータは収集できません。 非標準の SSH ポートを使用する場合に、-x オプションを使用して ([マニュアルを参照](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_requirements_other.html))。 たとえば、SSH ポートが 3479 の場合で、crm_report を呼び出します。
    >
    >```bash
    >crm_report -X "-p 3479" [...]
    >```
    >詳細については、[管理ガイド] を参照してください。(https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.misc)

次のセクションでは、共有記憶域を構成し、そのストレージにデータベース ファイルを移動します。  

## <a name="configure-shared-storage-and-move-database-files"></a>共有記憶域を構成して、データベース ファイルを移動する

共有記憶域を提供するためのさまざまなソリューションがあります。 このチュートリアルでは、NFS を使った共有記憶域の構成について説明します。 ベスト プラクティスに従うし、Kerberos を使用して NFS を保護することをお勧めします。 

- [ファイル システムと NFS 共有](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#cha.nfs)

このガイダンスに従っていない場合は、データ ファイルにアクセスすること、ネットワークにアクセスおよび SQL ノードの IP アドレスを偽装できるすべてのユーザーができます。 通常どおり、実稼働環境で使用する前にお使いのシステムの脅威モデルを確認してください。 

別の記憶域オプションでは、SMB ファイル共有を使用します。

- [SUSE ドキュメントの samba セクション](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#cha.samba)

### <a name="configure-an-nfs-server"></a>NFS サーバーを構成します。

NFS サーバーを構成するのには、SUSE ドキュメントでは、次の手順を参照してください: [NFS サーバーを構成する](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#sec.nfs.configuring-nfs-server)です。

### <a name="configure-all-cluster-nodes-to-connect-to-the-nfs-shared-storage"></a>NFS 共有の記憶域に接続するすべてのクラスター ノードを構成します。

共有記憶域の場所を指す SQL Server データベース ファイルのパスにマウントするように NFS クライアントを構成する前にデータベース ファイルにコピーして後で、共有できるように一時的な場所に保存するになっていることを確認します。

1. **プライマリ ノードのみで**、一時的な場所にデータベース ファイルを保存します。 次のスクリプトでは、新しい一時ディレクトリを作成するには、データベース ファイルを新しいディレクトリにコピーおよび古いデータベース ファイルを削除します。 SQL Server はローカル ユーザー mssql として実行されるため、マウントされた共有へのデータ転送後に、ローカル ユーザーが共有への読み取り/書き込みアクセスを持っているかどうかを確認する必要があります。 

    ```bash
    su mssql
    mkdir /var/opt/mssql/tmp
    cp /var/opt/mssql/data/* /var/opt/mssql/tmp
    rm /var/opt/mssql/data/*
    exit
    ```

    すべてのクラスター ノードに NFS クライアントを構成します。

    - [クライアントを構成します。](https://www.suse.com/documentation/sles-12/singlehtml/book_sle_admin/book_sle_admin.html#sec.nfs.configuring-nfs-clients)

    > [!NOTE]
    > SUSE のベスト プラクティスと使用できる NFS 高の記憶域に関する推奨事項に従うことをお勧めします。[高使用できる NFS および記憶域を DRBD ペース](https://www.suse.com/documentation/sle-ha-12/book_sleha_techguides/data/art_ha_quick_nfs.html)です。

2. 新しいファイル パスで SQL Server が正常に開始するかを検証します。 これは、各ノードで行います。 この時点で 一度に1 つのノードのみで SQL Server を実行する必要があります。 各ノードが同時にデータベースファイルにアクセスしようとするため(両方のノードで SQL Server が誤って開始しないように、ファイル システムのクラスター リソースを使用して、ファイル共有が別々 のノードによって 2 回マウントされていないようにします) 各ノードで同時に実行することはできません。 次のコマンドは、SQL Server を起動し、状態を確認し、SQL Server を停止します。 

    ```bash
    sudo systemctl start mssql-server
    sudo systemctl status mssql-server
    sudo systemctl stop mssql-server
    ```

この時点で、共有記憶域上のデータベース ファイルを使用して実行する SQL Server の両方のインスタンスが構成されます。 次の手順では、ペースの SQL Server を構成します。 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>各クラスター ノードでPacemakerインストールして構成する

1. **両方のクラスター ノードで、Pacemaker にログインするための SQL Server のユーザー名とパスワードを格納するファイルを作成します**。 次のコマンドは、このファイルを作成および設定します。

    ```bash
    sudo touch /var/opt/mssql/secrets/passwd
    sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
    sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
    sudo chown root:root /var/opt/mssql/secrets/passwd 
    sudo chmod 600 /var/opt/mssql/secrets/passwd
    ```
2. **すべてのクラスター ノードは、SSH を使用して相互にアクセスできる必要があります**。 hb_report or crm_report (トラブルシューティング用) などのツールや Hawk の History Explorer では、ノード間でパスワードなしの SSH アクセスが必要です。それ以外の場合は、現在のノード以外のデータは収集できません。 非標準の SSH ポートを使用する場合は、-X オプションを使用します (man ページを参照)。 たとえば、SSH ポートが 3479 の場合は、次のコマンドを実行して hb_report を呼び出します。

    ```bash
    crm_report -X "-p 3479" [...]
    ```

    詳細については、[SUSE ドキュメントのシステム要件と推奨事項](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_requirements_other.html)をご覧ください。

3. **High Availability Extension をインストールします**。 High Availability Extension をインストールするには、次の SUSE のトピックの手順を実行します。
    
    [インストールとセットアップのクイック スタート](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html)

4. **SQL Server の FCI リソース エージェントをインストールします**。 両方のノードで、次のコマンドを実行します。

    ```bash
    sudo zypper addrepo -fc https://packages.microsoft.com/config/sles/12/mssql-server-2017.repo
    sudo zypper --gpg-auto-import-keys refresh
    sudo zypper install mssql-server-ha
    ```

5. **最初のノードが自動的にセットアップされます**。 次の手順では、最初のノードである SLES1 を構成することにより、動作中の 1 ノード クラスターをセットアップします。 SUSE のトピック「[Setting Up the First Node](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node) (最初のノードのセットアップ)」の指示に従ってください。

    完了したら、`crm status` を使用してクラスターの状態を確認します。
    ```bash
    crm status
    ```

    ノード SLES1 が構成済みであることが表示されます。

6. **既存のクラスターにノードを追加します**。 次に、ノード SLES2 をクラスターに参加させます。 SUSE のトピック「[Adding the Second Node](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.2nd-node) (2 番目のノードの追加)」の指示に従います。
    
    完了したら、**crm status** を使用してクラスターの状態を確認します。 2 番目のノードが正常に追加されると、次のような出力が表示されます。
        
    ```
    2 nodes configured
    1 resource configured
    Online: [ SLES1 SLES2 ]
    Full list of resources:
    admin_addr     (ocf::heartbeat:IPaddr2):       Started SLES1
    ```

    > [!NOTE]
    > **admin_addr** は、最初の 1 ノード クラスターのセットアップ時に構成された仮想 IP クラスターのリソースです。

7.  **削除手順**。 クラスターからノードを削除する必要がある場合は、ブートストラップ スクリプト **ha-cluster-remove** を使用します。 詳細については、「[Overview of the Bootstrap Scripts](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.bootstrap) (ブートストラップ スクリプトの概要)」をご覧ください。  

## <a name="configure-the-cluster-resources-for-sql-server"></a>SQL Server のクラスター リソースを構成します。

次の手順では、SQL Server のクラスター リソースを構成する方法について説明します。 カスタマイズする必要のある 2 つの設定があります。

- **SQL Server リソース名**: SQL Server のクラスター化リソースの名前。 
- **タイムアウト値**: タイムアウトの値は、クラスターが、リソースがオンラインにしている間に待機する時間。 SQL Server では、これは、時間を表示するために SQL Server、`master`データベースがオンラインです。 

次のスクリプトを環境から値を更新します。 クラスター化されたサービスを構成および開始するために 1 つのノード上で実行します。

```bash
sudo crm configure
primitive <sqlServerResourceName> ocf:mssql:fci op start timeout=<timeout_in_seconds>
colocation <constraintName> inf: <virtualIPResourceName> <sqlServerResourceName>
show
commit
exit
```

たとえば、次のスクリプトは、mssqlha をという名前の SQL Server のクラスター化リソースを作成します。 

```bash
sudo crm configure
primitive mssqlha ocf:mssql:fci op start timeout=60s
colocation admin_addr_mssqlha inf: admin_addr mssqlha
show
commit
exit
```

構成がコミットされた後、SQL Server は仮想 IP リソースと同じノードで開始されます。 

詳細については、次を参照してください。[の構成とクラスター リソースを管理する」(コマンド ライン)](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.manual_config)です。 

### <a name="verify-that-sql-server-is-started"></a>SQL Server が開始されたことを確認します。 

SQL Server が開始されたことを確認するには、実行、 **crm ステータス**コマンド。

```bash
crm status
```

次の例は、ペースはクラスター化リソースとして正常に開始されたときに、結果を示します。 
```
2 nodes configured
2 resources configured

Online: [ SLES1 SLES2 ]

Full list of resources:

 admin_addr     (ocf::heartbeat:IPaddr2):       Started SLES1
 mssqlha        (ocf::mssql:fci):       Started SLES1
```

## <a name="managing-cluster-resources"></a>クラスター リソースの管理

クラスター リソースを管理するには、SUSE、次のトピックを参照してください:[クラスター リソースの管理](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.config.crm )

### <a name="manual-failover"></a>手動フェールオーバー (manual failover)

自動的にフェールオーバー (または移行)、ハードウェアまたはソフトウェアに障害が発生した場合、クラスターの他のノードには、リソースが構成されている、ペース GUI またはコマンドラインを使用して、クラスター内の別のノードにも手動でリソースを移動できます。 

このタスクの移行コマンドを使用します。 たとえば、移行するクラスター ノード名 SLES2 SQL リソースを実行します。 

```bash
crm resource
migrate mssqlha SLES2
```

## <a name="additional-resources"></a>その他のリソース

[SUSE Linux Enterprise の高可用性拡張機能の管理ガイド](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html) 
