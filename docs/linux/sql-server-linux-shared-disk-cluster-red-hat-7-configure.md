---
title: "SQL Server 用の Red Hat Enterprise Linux 共有クラスターの構成 |Microsoft ドキュメント"
description: "SQL Server の Red Hat Enterprise Linux 共有ディスク クラスターを構成することによって高可用性を実装します。"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: dcc0a8d3-9d25-4208-8507-a5e65d2a9a15
ms.workload: On Demand
ms.openlocfilehash: ffc0ea6cae32b5801b069748b2c124ef1bd87343
ms.sourcegitcommit: 6e016a4ffd28b09456008f40ff88aef3d911c7ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2017
---
# <a name="configure-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>SQL Server の Red Hat Enterprise Linux 共有ディスク クラスターを構成します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このガイドでは、Red Hat Enterprise Linux 上の SQL Server の 2 つのノードの共有ディスク クラスターを作成する手順を紹介します。 クラスタ リングの層は [Pacemaker](http://clusterlabs.org/)の上に構築されたRed Hat Enterprise Linux (RHEL) [HA アドオン](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf)に基づいています。 SQL Server のインスタンスは 1 つのノードもしくは別のもう一つのノードのどちらかでアクティブです。

> [!NOTE] 
> Red Hat HA アドオンおよびドキュメントへのアクセスには、サブスクリプションが必要です。 

次の図では、記憶域は 2 つのサーバーに提供されています。クラスタリングのコンポーネント - Corosync と Pacemaker - は、通信およびリソース管理を調整します。いずれかのサーバーが、記憶域リソースおよび SQL Server へのアクティブな接続を持ちます。Pacemaker が障害を検出すると、クラスタリングのコンポーネントは、他のノードへのリソースの移動を管理します。  

![Red Hat Enterprise Linux 7 ディスク SQL クラスターの共有](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 

クラスターの構成、リソース エージェント オプション、および管理の詳細については、[RHEL リファレンス ドキュメント](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html)を参照してください。


> [!NOTE] 
> この時点では、ペースで SQL Server の統合は Windows での WSFC でとして結合します。 SQL 内ではありません、クラスターの存在についてのナレッジ、すべてのオーケストレーションが外であり、サービスは、スタンドアロン インスタンスとしてペースによって制御されます。 など、クラスター dmv sys.dm_os_cluster_nodes と sys.dm_os_cluster_properties ないレコードがされます。
文字列のサーバー名を指す接続文字列を使用して、ip アドレスを使用しない、これらには、選択したサーバーの名前 (後述) の仮想 IP リソースを作成するために使用する ip アドレスが DNS サーバーに登録する必要があります。

次のセクションでは、フェールオーバー クラスター ソリューションをセットアップする手順について説明します。 

## <a name="prerequisites"></a>Prerequisites

次のエンド ツー エンド シナリオを完了するには、2 つのノードのクラスターを配置する2 台のコンピューターと NFS サーバーを構成する別のサーバーが必要です。 以下の手順で、これらのサーバーを構成する方法を説明します。

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>各クラスター ノードで、オペレーティング システムのセットアップと構成

最初の手順では、クラスター ノードで、オペレーティング システムを構成します。 このチュートリアルで、有効なサブスクリプションでの HA アドオン RHEL を使用します。 

## <a name="install-and-configure-sql-server-on-each-cluster-node"></a>インストールし、各クラスター ノードに SQL Server の構成

1. 両方のノード上に SQL Server をインストールし、セットアップします。  詳細な手順については [Linux 上の SQL Server のインストール](sql-server-linux-setup.md) を参照してください。

1. 構成のために、1つのノードをプライマリとして指定し、もう片方をセカンダリとして指定します。 このガイドでは、これ以降これらの用語を使用します。  

1. セカンダリ ノードでSQL Server を停止し無効にします。

   次の例では、SQL Server を停止して無効にします。 

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl disable mssql-server
   ```
> [!NOTE] 
> セットアップ時に、SQL Server インスタンスのためにサーバー マスター キーが生成され、`/var/opt/mssql/secrets/machine-key` に配置されます。 Linux では、SQL Server は、常に mssql と呼ばれるローカル アカウントとして実行されます。 ローカル アカウントであるため、その id はノード間で共有されません。 したがって、各ローカル mssql アカウント がサーバー マスター  キーの暗号化を解除するためにアクセスできるようにするために、各セカンダリ ノードにプライマリ ノードから暗号化キーをコピーする必要があります。 

1. プライマリ ノードで、ペースの SQL server ログインの作成および実行する権限をログイン`sp_server_diagnostics`です。 ペースのどのノードは、SQL Server を実行していることを確認するのにアカウントが使用されます。

   ```bash
   sudo systemctl start mssql-server
   ```

   SQL Server の`master`データベースに sa アカウントを使用して接続し、次のスクリプトを実行します。

   ```bashsql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'

   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```
   このスクリプトの代わりに、より細かなレベルでアクセス許可を設定することもできます。 Pacemaker ログインは、sp_server_diagnostics で正常性状態を照会するための`VIEW SERVER STATE`および、sp_dropserver と sp_addserver を実行して FCI インスタンス名をリソース名で更新するための`setupadmin`と`ALTER ANY LINKED SERVER`が必要です。

1. プライマリ ノードで、SQL Server を停止し無効にします。 

1. 各クラスター ノードのホスト ファイルを構成します。 ホスト ファイルには、すべてのクラスター ノードの名前と IP アドレスを含める必要があります。 

    各ノードの IP アドレスを確認してください。 次のスクリプトは、現在のノードの IP アドレスを示します。 

   ```bash
   sudo ip addr show
   ```

   各ノードで、コンピューター名を設定します。 各ノードに 15 文字以下の一意の名前を指定します。そのコンピューター名を `/etc/hosts`に追加することにより設定します。 次のスクリプトを使うと、`vi` で `/etc/hosts` を編集できます。

   ```bash
   sudo vi /etc/hosts
   ```
   次の`/etc/hosts`の例は`sqlfcivm1`と`sqlfcivm2`という名前の 2 つのノードの追加します。

   ```bash
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.128 sqlfcivm1
   10.128.16.77 sqlfcivm2
   ```

次のセクションでは、共有記憶域を構成し、そのストレージにデータベース ファイルを移動します。 

## <a name="configure-shared-storage-and-move-database-files"></a>共有記憶域を構成して、データベース ファイルを移動する

共有記憶域を提供するためのさまざまなソリューションがあります。 このチュートリアルでは、NFS を使った共有記憶域の構成について説明します。 ベストプラクティスに従い、Kerberos を使用して NFS を保護することを推奨します (例については https://www.certdepot.net/rhel7-use-kerberos-control-access-nfs-network-shares/ を参照してください)。 

>[!Warning]
>NFS を保護していない場合、ネットワークにアクセスして SQL ノードの IP アドレスを偽装できるすべてのユーザーがデータ ファイルにアクセスできます。通常どおり、実稼働環境で使用する前にお使いのシステムの脅威モデルを確認してください。別の記憶域オプションとして、SMB ファイル共有を使用できます。

### <a name="configure-shared-storage-with-nfs"></a>Nfs の共有記憶域を構成します。

> [!IMPORTANT] 
> バージョンを持つ NFS サーバー上のデータベース ファイルをホストしている < 4 がこのリリースでサポートされていません。 これは、NFS を使用して、共有ディスクに対してフェールオーバー クラスタ リングのデータベースと非クラスター化インスタンスに含まれています。 今後のリリースで他の NFS サーバーのバージョンの有効化に取り組んでいます。 

NFS サーバー上で、次の操作を行います。

1. `nfs-utils` のインストール

   ```bash
   sudo yum -y install nfs-utils
   ```

1. `rpcbind`を有効にして開始します

   ```bash
   sudo systemctl enable rpcbind && sudo systemctl start rpcbind
   ```

1. `nfs-server`を有効にして開始します
 
   ```bash
   sudo systemctl enable nfs-server && sudo systemctl start nfs-server
   ```
 
1.  編集`/etc/exports`を共有するディレクトリをエクスポートします。 必要な共有フォルダーごとに 1 行を必要があります。 例 : 

   ```bash
   /mnt/nfs  10.8.8.0/24(rw,sync,no_subtree_check,no_root_squash)
   ```

1. 共有をエクスポートします。

   ```bash
   sudo exportfs -rav
   ```

パスがエクスポート/共有されていることを確認するため、NFS サーバーから実行してください。

   ```bash
   sudo showmount -e
   ```

1. SELinux で例外を追加します。

   ```bash
   sudo setsebool -P nfs_export_all_rw 1
   ```
   
1. サーバーのファイアウォールを開きます。

   ```bash 
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

### <a name="configure-all-cluster-nodes-to-connect-to-the-nfs-shared-storage"></a>NFS 共有の記憶域に接続するすべてのクラスター ノードを構成します。

すべてのクラスター ノードで次の手順を実行します。

1.  `nfs-utils`をインストールします。

   ```bash
   sudo yum -y install nfs-utils
   ```

1. クライアントと NFS サーバー上のファイアウォールを開きます。

   ```bash
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

1. クライアント コンピューターで、NFS 共有を表示できることを確認します。

   ```bash
   sudo showmount -e <IP OF NFS SERVER>
   ```

1. すべてのクラスター ノードでこれらの手順を繰り返します。

NFS の使用に関する詳細については、次のリソースを参照してください。

* [NFS サーバーと firewalld |Stack Exchange](http://unix.stackexchange.com/questions/243756/nfs-servers-and-firewalld)
* [NFS ボリュームのマウント |Linux のネットワーク管理者ガイド](http://www.tldp.org/LDP/nag2/x-087-2-nfs.mountd.html)
* [NFS サーバーの構成](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/Reference_Guide/s1-nfs-server-export.html)

### <a name="mount-database-files-directory-to-point-to-the-shared-storage"></a>共有記憶域 をポイントにデータベース ファイル ディレクトリをマウントします。

1.  **プライマリ ノード上でのみ**、一時的な場所にデータベース ファイルを保存します。次のスクリプトでは、新しい一時ディレクトリを作成し、データベース ファイルを新しいディレクトリにコピーして、古いデータベース ファイルを削除します。SQL Server はローカル ユーザー mssql として実行されるため、マウントされた共有へのデータ転送後に、ローカル ユーザーが共有への読み取り/書き込みアクセスを持っているかどうかを確認する必要があります。 

   ``` 
   $ su mssql
   $ mkdir /var/opt/mssql/tmp
   $ cp /var/opt/mssql/data/* /var/opt/mssql/tmp
   $ rm /var/opt/mssql/data/*
   $ exit
   ``` 

1. すべてのクラスター ノードで編集`/etc/fstab`mount コマンドを追加するファイル。  

   ```bash
   <IP OF NFS SERVER>:<shared_storage_path> <database_files_directory_path> nfs timeo=14,intr 
   ```
   
   次のスクリプトは、編集の例を示します。  

   ``` 
   10.8.8.0:/mnt/nfs /var/opt/mssql/data nfs timeo=14,intr 
   ``` 
> [!NOTE] 
>ファイル システム (FS) のリソースを使用して、下の推奨どおり場合、/etc/fstab にコマンドのマウントを保持する必要はありません。 FS クラスター化されたリソースを開始するときに、フォルダーをマウント ペースくれます。 フェンス操作のヘルプ、FS が 2 回マウントしないことを確認されます。  

1. 実行`mount -a`マウントされているパスを更新するシステムのコマンド。  

1.  `/var/opt/mssql/tmp`に保存したデータベースとログ ファイルを新しくマウントされた共有`/var/opt/mssql/data`にコピーします。 **プライマリ ノードで**実行するだけですみます。 'mssql' ローカル ユーザーへの読み取り/書き込み権限を付与していることを確認します。

   ``` 
   $ chown mssql /var/opt/mssql/data
   $ chgrp mssql /var/opt/mssql/data
   $ su mssql
   $ cp /var/opt/mssql/tmp/* /var/opt/mssql/data/
   $ rm /var/opt/mssql/tmp/*
   $ exit
   ``` 
 
1. 新しいファイル パスで SQL Server が正常に開始するかを検証します。 これは、各ノードで行います。 この時点で 1 つのノードでは、一度に SQL Server を実行する必要があります。 これら両方ために実行できません同時に両方同時に (に両方のノードに SQL Server を誤って開始しないように、ファイル システムのクラスター リソースを使用して、共有が別々 のノードによって 2 回マウントされていないかどうかを確認) データ ファイルにアクセスする再試行されます。 次のコマンドは、SQL Server の起動、状態を確認し、SQL Server を停止します。
 
   ```bash
   sudo systemctl start mssql-server
   sudo systemctl status mssql-server
   sudo systemctl stop mssql-server
   ```
 
この時点で、共有記憶域上のデータベース ファイルを使用して実行する SQL Server の両方のインスタンスが構成されます。 次の手順では、ペースの SQL Server を構成します。 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>インストールし、ペースを各クラスター ノードの構成 


2. 両方のクラスター ノードで、Pacemaker がログインするための SQL Server のユーザー名とパスワードを格納するファイルを作成します。 次のコマンドは、このファイルを作成および設定します。

   ```bash
   sudo touch /var/opt/mssql/secrets/passwd
   sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
   sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/secrets/passwd 
   sudo chmod 600 /var/opt/mssql/secrets/passwd    
   ```

3. 両方のクラスター ノードで、Pacemaker ファイアウォールのポートを開きます。 `firewalld` を使用してこれらのポートを開くには、次のコマンドを実行します。

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > 組み込みの高可用性構成が備わっていない別のファイアウォールを使用する場合は、Pacemaker 用に次のポートを開き、クラスター内の他のノードと通信できるようにする必要があります
   >
   > * TCP: ポート 2224、3121、21064
   > * UDP: ポート 5405

1. 各ノードに Pacemaker パッケージをインストールします。

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```

   

2. Pacemaker と Corosync のパッケージをインストールしたときに作成された既定のユーザー用のパスワードを設定します。 両方のノードで同じパスワードを使用します。 

   ```bash
   sudo passwd hacluster
   ```

   

3. `pcsd` サービスと Pacemaker を有効にし、起動します。 これにより、再起動後にノードはクラスターに再度参加できます。 両方のノードで、次のコマンドを実行します。

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. SQL Server の FCI リソース エージェントをインストールします。 両方のノードで、次のコマンドを実行します。 

   ```bash
   sudo yum install mssql-server-ha
   ```

## <a name="create-the-cluster"></a>クラスターを作成する

1. ノードのいずれかで、クラスターを作成します。

   ```bash
   sudo pcs cluster auth <nodeName1 nodeName2 …> -u hacluster
   sudo pcs cluster setup --name <clusterName> <nodeName1 nodeName2 …>
   sudo pcs cluster start --all
   ```

   > RHEL HA アドオンは、VMWare と KVM エージェントをフェンスがします。 フェンス操作は、他のすべてのハイパーバイザーで無効にする必要があります。 実稼働環境では、フェンス操作エージェントを無効にしないでください。 時間帯、時点では、HyperV またはクラウド環境のフェンス操作エージェントがありません。 これらの構成を実行している場合は、フェンス操作を無効にする必要があります。 \**これは、説明は、実稼働システムでは推奨されません。** 

   次のコマンドで、フェンス操作エージェントを無効にします。

   ```bash
   sudo pcs property set stonith-enabled=false
   sudo pcs property set start-failure-is-fatal=false
   ```

2. SQL Server、ファイル システムと仮想 IP リソースのためにクラスター リソースを構成し、クラスターに構成をプッシュします。 次の情報が必要となります。

   - **SQL Server リソース名**: SQL Server のクラスター化リソースの名前。 
   - **タイムアウト値**: タイムアウトの値は、クラスターが待機する時間中に、リソースがオンラインにします。 SQL Server では、これは、時間を表示するために SQL Server、`master`データベースがオンラインです。 
   - **IP リソース名を浮動**: 仮想 IP アドレス リソースの名前。
   - **IP アドレス**: SQL Server のクラスター化されたインスタンスに接続するクライアントが使用する IP アドレス。 
   - **ファイル システム リソース名**: ファイル システム リソースの名前。
   - **デバイス**:、NFS 共有のパス
   - **デバイス**: 共有にマウントしているローカル パス
   - **fstype**: ファイル共有の種類 (つまり nfs)

   以下のスクリプトの値をあなたの環境向けに更新します。 クラスター化されたサービスを構成および開始するために 1 つのノード上で実行します。  

   ```bash
   sudo pcs cluster cib cfg 
   sudo pcs -f cfg resource create <sqlServerResourceName> ocf:mssql:fci op defaults timeout=<timeout_in_seconds>
   sudo pcs -f cfg resource create <floatingIPResourceName> ocf:heartbeat:IPaddr2 ip=<ip Address>
   sudo pcs -f cfg resource create <fileShareResourceName> Filesystem device=<networkPath> directory=<localPath>         fstype=<fileShareType>
   sudo pcs -f cfg constraint colocation add <virtualIPResourceName> <sqlResourceName>
   sudo pcs -f cfg constraint colocation add <fileShareResourceName> <sqlResourceName> 
   sudo pcs cluster cib-push cfg
   ```

   たとえば、次のスクリプトにより、`mssqlha`という名前のSQL Server のクラスター化リソース、および`10.0.0.99`という IP アドレスを持つフローティング IP リソースを作成します。 さらに、ファイル システム リソースを作成し、SQL リソースと同じノードにすべてのリソースが配置されるように制約を追加します。 

   ```bash
   sudo pcs cluster cib cfg
   sudo pcs -f cfg resource create mssqlha ocf:mssql:fci op defaults timeout=60s
   sudo pcs -f cfg resource create virtualip ocf:heartbeat:IPaddr2 ip=10.0.0.99
   sudo pcs -f cfg resource create fs Filesystem device="10.8.8.0:/mnt/nfs" directory="/var/opt/mssql/data" fstype="nfs"
   sudo pcs -f cfg constraint colocation add virtualip mssqlha
   sudo pcs -f cfg constraint colocation add fs mssqlha
   sudo pcs cluster cib-push cfg
   ```

   構成がプッシュされた後、SQL Server は、1 つのノードで開始されます。 

3. SQL Server が開始されたことを確認します。 

   ```bash
   sudo pcs status 
   ```

   次の例は、PacemakerがSQL Server のクラスター化されたインスタンスの開始に成功したときの結果を示しています。

   ```
   fs     (ocf::heartbeat:Filesystem):    Started sqlfcivm1
   virtualip     (ocf::heartbeat:IPaddr2):      Started sqlfcivm1
   mssqlha  (ocf::mssql:fci): Started sqlfcivm1
   
   PCSD Status:
    slqfcivm1: Online
    sqlfcivm2: Online
   
   Daemon Status:
    corosync: active/disabled
    pacemaker: active/enabled
    pcsd: active/enabled
   ```

## <a name="additional-resources"></a>その他のリソース

* [クラスターの最初から](http://clusterlabs.org/doc/Cluster_from_Scratch.pdf)ペースからガイド

## <a name="next-steps"></a>次の手順

[Red Hat Enterprise Linux 共有ディスク クラスターで SQL Server の運用します。](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
