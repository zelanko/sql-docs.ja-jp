---
title: "SQL Server 用の Red Hat Enterprise Linux 共有クラスターの構成 |Microsoft ドキュメント"
description: "SQL Server の Red Hat Enterprise Linux 共有ディスク クラスターを構成することによって高可用性を実装します。"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: dcc0a8d3-9d25-4208-8507-a5e65d2a9a15
ms.translationtype: MT
ms.sourcegitcommit: 834bba08c90262fd72881ab2890abaaf7b8f7678
ms.openlocfilehash: 1708138f5eeb082f022f78dfb685f333f3f0a17b
ms.contentlocale: ja-jp
ms.lasthandoff: 10/02/2017

---
# <a name="configure-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>SQL Server の Red Hat Enterprise Linux 共有ディスク クラスターを構成します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このガイドでは、Red Hat Enterprise Linux 上の SQL Server の 2 つのノードの共有ディスク クラスターを作成する手順を紹介します。 クラスタ リングの層は Red Hat Enterprise Linux (RHEL) に基づいて[HA アドオン](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf)の上に構築[ペース](http://clusterlabs.org/)です。 SQL Server のインスタンスは 1 つのノードまたは他の上でアクティブです。

> [!NOTE] 
> Red Hat HA アドオンおよびドキュメントへのアクセスには、サブスクリプションが必要です。 

として、次の図は、記憶域は、2 つのサーバーに表示されます。 -Corosync とペース - クラスタ リングのコンポーネントは、通信およびリソース管理を調整します。 サーバーのいずれかが、記憶域リソース、および SQL Server へのアクティブな接続です。 ペースが障害を検出したときに、クラスタ リングのコンポーネントは、他のノードに、リソースの移動を管理します。  

![Red Hat Enterprise Linux 7 ディスク SQL クラスターの共有](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 

クラスターの構成、リソース エージェント オプション、および管理の詳細については、次を参照してください。 [RHEL リファレンス ドキュメント](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html)です。


> [!NOTE] 
> この時点では、ペースで SQL Server の統合は Windows での WSFC でとして結合します。 SQL 内ではありません、クラスターの存在についてのナレッジ、すべてのオーケストレーションが外であり、サービスは、スタンドアロン インスタンスとしてペースによって制御されます。 など、クラスター dmv sys.dm_os_cluster_nodes と sys.dm_os_cluster_properties ないレコードがされます。
文字列のサーバー名を指す接続文字列を使用して、ip アドレスを使用しない、これらには、選択したサーバーの名前 (後述) の仮想 IP リソースを作成するために使用する ip アドレスが DNS サーバーに登録する必要があります。

次のセクションでは、フェールオーバー クラスター ソリューションをセットアップする手順について説明します。 

## <a name="prerequisites"></a>前提条件

次のエンド ツー エンド シナリオを完了するには、2 台のコンピューターを 2 つのノードのクラスターと NFS サーバーを構成する別のサーバーを展開する必要があります。 以下の手順には、これらのサーバーを構成する方法を説明します。

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>セットアップし、各クラスター ノードで、オペレーティング システムを構成します。

最初の手順では、クラスター ノードで、オペレーティング システムを構成します。 このチュートリアルで、有効なサブスクリプションでの HA アドオン RHEL を使用します。 

## <a name="install-and-configure-sql-server-on-each-cluster-node"></a>インストールし、各クラスター ノードに SQL Server の構成

1. インストールし、両方のノード上に SQL Server をセットアップします。  詳細な手順についてを参照してください。 [Linux 上の SQL Server のインストール](sql-server-linux-setup.md)です。

1. プライマリ サーバーと、他の構成のために、セカンダリとして 1 つのノードを指定します。 これらの用語を使用して、次のこのガイドです。  

1. セカンダリ ノードで停止し、SQL Server を無効にします。

   次の例では、停止して、SQL Server を無効にします。 

   ```bash
   sudo systemctl stop mssql-server
   sudo systemctl disable mssql-server
   ```
> [!NOTE] 
> セットアップ時に、サーバーのマスター _ キーは、SQL Server インスタンスの生成され、var/オプトイン/mssql/シークレット/マシン キーに置かれます。 Linux では、SQL Server は、常に mssql と呼ばれるローカル アカウントとして実行されます。 ローカル アカウントであるために、その id は、ノード間で共有されません。 したがって、各ローカル mssql アカウント アクセスできるように、サーバーのマスター _ キーの暗号化を解除するは、各セカンダリ ノードにプライマリ ノードから、暗号化キーをコピーする必要があります。 

1. プライマリ ノードで、ペースの SQL server ログインの作成および実行する権限をログイン`sp_server_diagnostics`です。 ペースのどのノードは、SQL Server を実行していることを確認するのにアカウントが使用されます。 

   ```bash
   sudo systemctl start mssql-server
   ```

   SQL Server に接続`master`sa アカウントを使用してデータベースにあり、次を実行します。

   ```bashsql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'

   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```
   または、より細かなレベルでアクセス許可を設定することもできます。 ペース ログインが必要です`VIEW SERVER STATE`sp_server_diagnostics でヘルス状態を照会`setupadmin`と`ALTER ANY LINKED SERVER`sp_dropserver と sp_addserver を実行して、リソース名を持つ FCI インスタンス名を更新します。 

1. プライマリ ノードで、停止し、SQL Server を無効にします。 

1. 各クラスター ノードのホスト ファイルを構成します。 ホスト ファイルには、すべてのクラスター ノードの名前と IP アドレスを含める必要があります。 

    各ノードの IP アドレスを確認してください。 次のスクリプトは、現在のノードの IP アドレスを示します。 

   ```bash
   sudo ip addr show
   ```

   各ノードで、コンピューター名を設定します。 各ノード一意の名前は 15 文字以下です。 追加することによって、コンピューター名を設定`/etc/hosts`です。 次のスクリプトを使うと、`vi` で `/etc/hosts` を編集できます。 

   ```bash
   sudo vi /etc/hosts
   ```
   次の例は`/etc/hosts`という 2 つのノードの追加と`sqlfcivm1`と`sqlfcivm2`です。

   ```bash
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1       localhost localhost6 localhost6.localdomain6
   10.128.18.128 sqlfcivm1
   10.128.16.77 sqlfcivm2
   ```

次のセクションでは、共有記憶域を構成し、そのストレージにデータベース ファイルを移動します。 

## <a name="configure-shared-storage-and-move-database-files"></a>共有記憶域を構成して、データベース ファイルの移動 

さまざまな共有記憶域を提供するためのソリューションがあります。 このチュートリアルでは、NFS で共有記憶域の構成について説明します。 ベスト プラクティスに従うし、Kerberos を使用して NFS を保護することをお勧め (次に例を見つけることができます: https://www.certdepot.net/rhel7-use-kerberos-control-access-nfs-network-shares/)。 そうしないと場合、ネットワークへのアクセスおよび SQL ノードの IP アドレスを偽装できるすべてのユーザーができるデータ ファイルにアクセスします。 いつものように、脅威モデルの実稼働環境で使用する前に、システムを確認します。 別の記憶域オプションでは、SMB ファイル共有を使用します。

### <a name="configure-shared-storage-with-nfs"></a>Nfs の共有記憶域を構成します。

> [!IMPORTANT] 
> バージョンを持つ NFS サーバー上のデータベース ファイルをホストしている < 4 がこのリリースでサポートされていません。 これは、NFS を使用して、共有ディスクに対してフェールオーバー クラスタ リングのデータベースと非クラスター化インスタンスに含まれています。 今後のリリースで他の NFS サーバーのバージョンの有効化に取り組んでいます。 

NFS サーバー上には、次の操作を行います。

1. `nfs-utils` のインストール

   ```bash
   sudo yum -y install nfs-utils
   ```

1. 有効化と開始`rpcbind`

   ```bash
   sudo systemctl enable rpcbind && systemctl start rpcbind
   ```

1. 有効化と開始`nfs-server`
 
   ```bash
   systemctl enable nfs-server && systemctl start nfs-server
   ```
 
1.  編集`/etc/exports`を共有するディレクトリをエクスポートします。 必要な共有フォルダーごとに 1 行を必要があります。 例: 

   ```bash
   /mnt/nfs  10.8.8.0/24(rw,sync,no_subtree_check,no_root_squash)
   ```

1. 共有をエクスポートします。

   ```bash
   sudo exportfs -rav
   ```

1. パスが、エクスポート/共有 NFS サーバーから実行を確認してください。

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

1.  NFS サーバーから次のようにインストールします。`nfs-utils`

   ```bash
   sudo yum -y install nfs-utils
   ```

1. クライアントと NFS サーバー上のファイアウォールを open

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

詳細については、NFS を使用して、次のリソースを参照してください。

* [NFS サーバーと firewalld |スタックの交換](http://unix.stackexchange.com/questions/243756/nfs-servers-and-firewalld)
* [NFS ボリュームのマウント |Linux のネットワーク管理者ガイド](http://www.tldp.org/LDP/nag2/x-087-2-nfs.mountd.html)
* [NFS サーバーの構成](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/Reference_Guide/s1-nfs-server-export.html)

### <a name="mount-database-files-directory-to-point-to-the-shared-storage"></a>共有記憶域 をポイントにデータベース ファイル ディレクトリをマウントします。

1.  **プライマリ ノードのみで**、一時的な場所にデータベース ファイルを保存します。次のスクリプトでは、新しい一時ディレクトリを作成するには、データベース ファイルを新しいディレクトリにコピーおよび古いデータベース ファイルを削除します。 ローカル ユーザー mssql として SQL Server を実行すると、マウントされた共有へのデータ転送、後にローカル ユーザーが共有への読み取り/書き込みアクセスを持っているかどうかを確認する必要があります。 

   ``` 
   $ su mssql
   $ mkdir /var/opt/mssql/tmp
   $ cp /var/opt/mssql/data/* /var/opt/mssql/tmp
   $ rm /var/opt/mssql/data/*
   $ exit
   ``` 

1.  すべてのクラスター ノードで編集`/etc/fstab`mount コマンドを追加するファイル。  

   ```bash
   <IP OF NFS SERVER>:<shared_storage_path> <database_files_directory_path> nfs timeo=14,intr 
   ```
   
   次のスクリプトは、編集の例を示します。  

   ``` 
   10.8.8.0:/mnt/nfs /var/opt/mssql/data nfs timeo=14,intr 
   ``` 
> [!NOTE] 
>ファイル システム (FS) のリソースを使用して、下の推奨どおり場合、/etc/fstab にコマンドのマウントを保持する必要はありません。 FS クラスター化されたリソースを開始するときに、フォルダーをマウント ペースくれます。 フェンス操作のヘルプ、FS が 2 回マウントしないことを確認されます。 

1.  実行`mount -a`マウントされているパスを更新するシステムのコマンド。  

1.  保存したデータベースとログ ファイルをコピー`/var/opt/mssql/tmp`新しくマウントされた共有に`/var/opt/mssql/data`です。 実行するだけで済みますが**プライマリ ノードで**です。 'Mssql' のローカル ユーザーへの読み取り/書き込み権限を付与することを確認します。

   ``` 
   $ chown mssql /var/opt/mssql/data
   $ chgrp mssql /var/opt/mssql/data
   $ su mssql
   $ cp /var/opt/mssql/tmp/* /var/opt/mssql/data/
   $ rm /var/opt/mssql/tmp/*
   $ exit
   ``` 
 
1.  新しいファイル パスで SQL Server が正常に開始するかを検証します。 これは、各ノードで行います。 この時点で 1 つのノードでは、一度に SQL Server を実行する必要があります。 これら両方ために実行できません同時に両方同時に (に両方のノードに SQL Server を誤って開始しないように、ファイル システムのクラスター リソースを使用して、共有が別々 のノードによって 2 回マウントされていないかどうかを確認) データ ファイルにアクセスする再試行されます。 次のコマンドは、SQL Server の起動、状態を確認し、SQL Server を停止します。
 
   ```bash
   sudo systemctl start mssql-server
   sudo systemctl status mssql-server
   sudo systemctl stop mssql-server
   ```
 
この時点で、共有記憶域上のデータベース ファイルを使用して実行する SQL Server の両方のインスタンスが構成されます。 次の手順では、ペースの SQL Server を構成します。 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>インストールし、ペースを各クラスター ノードの構成


2. 両方のクラスター ノードで、Pacemaker にログインするための SQL Server のユーザー名とパスワードを格納するファイルを作成します。 次のコマンドは、このファイルを作成および設定します。

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

## <a name="create-the-cluster"></a>クラスターを作成します。 

1. ノードのいずれかで、クラスターを作成します。

   ```bash
   sudo pcs cluster auth <nodeName1 nodeName2 …> -u hacluster
   sudo pcs cluster setup --name <clusterName> <nodeName1 nodeName2 …>
   sudo pcs cluster start --all
   ```

   > RHEL HA アドオンは、VMWare と KVM エージェントをフェンスがします。 フェンス操作は、他のすべてのハイパーバイザーで無効にする必要があります。 実稼働環境では、フェンス操作エージェントを無効にしないでください。 時間帯、時点では、HyperV またはクラウド環境のフェンス操作エージェントがありません。 これらの構成を実行している場合は、フェンス操作を無効にする必要があります。 \**これは、説明は、実稼働システムでは推奨されません。**

   次のコマンドでは、フェンス操作エージェントが無効にします。

   ```bash
   sudo pcs property set stonith-enabled=false
   sudo pcs property set start-failure-is-fatal=false
   ```

2. SQL Server、ファイル システムと仮想 IP リソースをクラスター リソースを構成し、クラスターに構成をプッシュします。 次の情報を必要となります。

   - **SQL Server リソース名**: SQL Server のクラスター化リソースの名前。 
   - **タイムアウト値**: タイムアウトの値は、クラスターが待機する時間中に、リソースがオンラインにします。 SQL Server では、これは、時間を表示するために SQL Server、`master`データベースがオンラインです。  
   - **IP リソース名を浮動**: 仮想 IP アドレス リソースの名前。
   - **IP アドレス**: SQL Server のクラスター化されたインスタンスに接続するクライアントが使用する IP アドレス。 
   - **ファイル システム リソース名**: ファイル システム リソースの名前。
   - **デバイス**:、NFS 共有のパス
   - **デバイス**: にマウントされている共有へのローカル パス
   - **すれば**: ファイル共有の種類 (つまり nfs)

   以下のスクリプトを環境から値を更新します。 構成およびクラスター化されたサービスを開始する 1 つのノード上で実行します。  

   ```bash
   sudo pcs cluster cib cfg 
   sudo pcs -f cfg resource create <sqlServerResourceName> ocf:mssql:fci op defaults timeout=<timeout_in_seconds>
   sudo pcs -f cfg resource create <floatingIPResourceName> ocf:heartbeat:IPaddr2 ip=<ip Address>
   sudo pcs -f cfg resource create <fileShareResourceName> Filesystem device=<networkPath> directory=<localPath>         fstype=<fileShareType>
   sudo pcs -f cfg constraint colocation add <virtualIPResourceName> <sqlResourceName>
   sudo pcs -f cfg constraint colocation add <fileShareResourceName> <sqlResourceName> 
   sudo pcs cluster cib-push cfg
   ```

   たとえば、次のスクリプトがという名前の SQL Server のクラスター化リソースを作成`mssqlha`、および IP アドレスを持つフローティング IP リソース`10.0.0.99`です。 また、ファイル システム リソースを作成し、SQL リソースと同じノードにすべてのリソースが併置されているために、制約を追加します。 

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

   次の例に示しますペースがある正常に進んだ場合の結果には、SQL Server のクラスター化されたインスタンスが開始しました。 

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

