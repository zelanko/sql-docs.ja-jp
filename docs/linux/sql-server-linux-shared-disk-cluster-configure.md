---
title: "SQL Server Linux (RHEL) でのフェールオーバー クラスター インスタンスの構成 |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/28/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.workload: Inactive
ms.openlocfilehash: ccb754ce5b37e3364ebe68b7b2065ce7b68d050f
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="configure-failover-cluster-instance---sql-server-on-linux-rhel"></a>SQL Server Linux (RHEL) でのフェールオーバー クラスター インスタンスを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server の 2 つのノードの共有ディスク フェールオーバー クラスターのインスタンスは、高可用性のためのサーバー レベルの冗長性を提供します。 このチュートリアルでは、Linux に SQL Server の 2 ノード フェールオーバー クラスター インスタンスを作成する方法を学習します。 完了する具体的な手順は次のとおりです。

> [!div class="checklist"]
> * 設定し、Linux を構成します。
> * SQL サーバー インストールし、構成
> * Hosts ファイルを構成します。
> * 共有記憶域を構成して、データベース ファイルの移動
> * インストールし、ペースを各クラスター ノードの構成
> * フェールオーバー クラスター インスタンスを構成します。

この記事では、SQL Server の 2 つのノードの共有ディスク フェールオーバー クラスター インスタンス (FCI) を作成する方法について説明します。 アーティクルには Red Hat Enterprise Linux (RHEL) の手順とスクリプトの例が含まれています。 Ubuntu 中の配布 RHEL のようなスクリプトの例は、通常されます Ubuntu でも機能します。 

概念については、次を参照してください。 [SQL Server フェールオーバー クラスター インスタンス (FCI) on Linux](sql-server-linux-shared-disk-cluster-concepts.md)です。

## <a name="prerequisites"></a>前提条件

次のエンド ツー エンド シナリオを完了するには、2 台のコンピューターを 2 つのノードのクラスターと記憶域を別のサーバーを展開する必要があります。 以下の手順には、これらのサーバーを構成する方法を説明します。

## <a name="set-up-and-configure-linux"></a>設定し、Linux を構成します。

最初の手順では、クラスター ノードで、オペレーティング システムを構成します。 クラスター内の各ノードでは、linux ディストリビューションを構成します。 両方のノードで同じディストリビューションとバージョンを使用します。 1 つまたは他の次のディストリビューションを使用します。
    
* HA のアドオンの有効なサブスクリプションで RHEL

## <a name="install-and-configure-sql-server"></a>SQL サーバー インストールし、構成

1. インストールし、両方のノードに SQL Server をセットアップします。  詳細な手順についてを参照してください。 [Linux 上の SQL Server のインストール](sql-server-linux-setup.md)です。
1. プライマリ サーバーと、他の構成のために、セカンダリとして 1 つのノードを指定します。 これらの用語を使用して、次のこのガイドです。  
1. セカンダリ ノードで停止し、SQL Server を無効にします。
    次の例では、停止して、SQL Server を無効にします。 
    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE] 
    > サーバーのマスター _ キーの SQL Server インスタンスの生成し、に配置時のセットアップで`var/opt/mssql/secrets/machine-key`です。 Linux では、SQL Server は、常に mssql と呼ばれるローカル アカウントとして実行されます。 ローカル アカウントであるために、その id は、ノード間で共有されません。 したがって、各ローカル mssql アカウント アクセスできるように、サーバーのマスター _ キーの暗号化を解除するは、各セカンダリ ノードにプライマリ ノードから、暗号化キーをコピーする必要があります。 

1.  プライマリ ノードで、ペースの SQL server ログインの作成および実行する権限をログイン`sp_server_diagnostics`です。 ペースのどのノードは、SQL Server を実行していることを確認するのにアカウントが使用されます。 

    ```bash
    sudo systemctl start mssql-server
    ```
   
   SQL Server に接続`master`sa アカウントを使用してデータベースにあり、次を実行します。

   ```sql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```

   または、より細かなレベルでアクセス許可を設定することもできます。 ペース ログインが必要です`VIEW SERVER STATE`sp_server_diagnostics でヘルス状態を照会`setupadmin`と`ALTER ANY LINKED SERVER`sp_dropserver と sp_addserver を実行して、リソース名を持つ FCI インスタンス名を更新します。 

1. プライマリ ノードで、停止し、SQL Server を無効にします。 

## <a name="configure-the-hosts-file"></a>Hosts ファイルを構成します。

各クラスター ノード上の hosts ファイルを構成します。 Hosts ファイルには、すべてのクラスター ノードの名前と IP アドレスを含める必要があります。

1. 各ノードの IP アドレスを確認してください。 次のスクリプトは、現在のノードの IP アドレスを示します。 

    ```bash
    sudo ip addr show
    ```

1. 各ノードで、コンピューター名を設定します。 各ノード一意の名前は 15 文字以下です。 追加することによって、コンピューター名を設定`/etc/hosts`です。 次のスクリプトを使うと、`vi` で `/etc/hosts` を編集できます。 

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

## <a name="configure-storage--move-database-files"></a>記憶域を構成するし、データベース ファイルの移動  

両方のノードにアクセスできる記憶域を提供する必要があります。 ISCSI、NFS、または SMB を使用することができます。 ストレージを構成し、クラスター ノードに記憶域を提供し、データベース ファイルを新しい記憶域に移動します。 次の記事では、記憶域の種類ごとの手順について説明します。

- [フェールオーバー クラスター インスタンス - iSCSI: Linux 上の SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [フェールオーバー クラスター インスタンス: NFS - Linux に SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [フェールオーバー クラスター インスタンス: SMB - Linux に SQL Server を構成します。](sql-server-linux-shared-disk-cluster-configure-smb.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>インストールし、ペースを各クラスター ノードの構成

1. 両方のクラスター ノードで、Pacemaker にログインするための SQL Server のユーザー名とパスワードを格納するファイルを作成します。 

    次のコマンドは、このファイルを作成および設定します。

    ```bash
    sudo touch /var/opt/mssql/secrets/passwd
    sudo echo '<loginName>' >> /var/opt/mssql/secrets/passwd
    sudo echo '<loginPassword>' >> /var/opt/mssql/secrets/passwd
    sudo chown root:root /var/opt/mssql/secrets/passwd 
    sudo chmod 600 /var/opt/mssql/secrets/passwd    
    ```

1. 両方のクラスター ノードで、Pacemaker ファイアウォールのポートを開きます。 `firewalld` を使用してこれらのポートを開くには、次のコマンドを実行します。

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
1. Pacemaker と Corosync のパッケージをインストールしたときに作成された既定のユーザー用のパスワードを設定します。 両方のノードで同じパスワードを使用します。 

   ```bash
   sudo passwd hacluster
   ```
1. `pcsd` サービスと Pacemaker を有効にし、起動します。 これにより、再起動後にノードはクラスターに再度参加できます。 両方のノードで、次のコマンドを実行します。

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

1. SQL Server の FCI リソース エージェントをインストールします。 両方のノードで、次のコマンドを実行します。 

   ```bash
   sudo yum install mssql-server-ha
   ```

## <a name="configure-the-failover-cluster-instance"></a>フェールオーバー クラスター インスタンスを構成します。

FCI は、リソース グループに作成されます。 これは、機能は、リソース グループの制約の必要性を軽減するため、もう少し簡単です。 ただし、開始する必要がありますの順序でリソース グループにリソースを追加します。 開始する必要があります順序を示します。 

1. 記憶域リソース
2. ネットワーク リソース
3. アプリケーション リソース

この例では、NewLinFCIGrp グループで、FCI を作成します。 リソース グループの名前は、ペースで作成されたすべてのリソースから一意である必要があります。

1.  ディスク リソースを作成します。 表示されますありません応答に問題がない場合に戻します。 ディスク リソースを作成する方法は、記憶域の種類によって異なります。 各記憶域の種類の例を次に示します。 クラスター化された記憶域用の記憶域の種類に適用する例を使用します。

    **iSCSI**

    ```bash
    sudo pcs resource create <iSCSIDiskResourceName> Filesystem device="/dev/<VolumeGroupName>/<LogicalVolumeName>" directory="<FolderToMountiSCSIDisk>" fstype="<FileSystemType>" --group RGName
    ```

    \<iSCSIDIskResourceName > iSCSI ディスクに関連付けられているリソースの名前を指定します

    \<VolumeGroupName > ボリューム グループの名前を指定します  

    \<LogicalVolumeName > が作成された論理ボリュームの名前を指定します  

    \<FolderToMountiSCSIDIsk > は、ディスクをマウントするフォルダーです (システム データベースと既定の場所は、なります/var/opt/mssql/data)

    \<FileSystemType > は EXT4、またはある XFS によって処理された書式設定方法およびどのような分布をサポートしています。 

    **NFS**

    ```bash
    sudo pcs resource create <NFSDiskResourceName> Filesystem device="<IPAddressOfNFSServer>:<FolderOnNFSServer>" directory="<FolderToMountNFSShare>" fstype=nfs4 options=" nfsvers=4.2,timeo=14,intr" --group RGName
    mount -t nfs4 IPAddressOfNFSServer:FolderOnNFSServer /var/opt/mssql/data -o 
    ```

    \<NFSDIskResourceName > NFS 共有に関連付けられているリソースの名前を指定します

    \<IPAddressOfNFSServer > を使用している NFS サーバーの IP アドレスは、

    \<FolderOnNFSServer > NFS 共有の名前を指定します。

    \<FolderToMountNFSShare > は、ディスクをマウントするフォルダーです (システム データベースと既定の場所は、なります/var/opt/mssql/data)

     次に例を示します。

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    **SMB**

    ```bash
    sudo pcs resource create SMBDiskResourceName Filesystem device="//<ServerName>/<ShareName>" directory="<FolderName>" fstype=cifs options="vers=3.0,username=<UserName>,password=<Password>,domain=<ADDomain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777" --group <RGName>
    ```

    \<サーバー名 > は SMB 共有を使用してサーバーの名前を指定します。

    \<共有名 > 共有の名前を指定します

    \<FolderName > の最後の手順で作成したフォルダーの名前を指定します。
    
    \<ユーザー名 > の共有にアクセスするユーザーの名前を指定します

    \<パスワード > は、ユーザーのパスワード

    \<ADDomain > は、AD DS ドメイン、(該当する場合、Windows Server ベースの SMB 共有を使用する場合)

    \<mssqlUID > は、mssql ユーザーの UID

    \<mssqlGID > mssql ユーザーのグループ ID は、

    \<RGName > リソース グループの名前を指定します
 
2.  FCI によって使用される IP アドレスを作成します。 表示されますありません応答に問題がない場合に戻します。

    ```bash
    sudo pcs resource create <IPResourceName> ocf:heartbeat:IPaddr2 ip=<IPAddress> nic=<NetworkCard> cidr_netmask=<NetMask> --group <RGName>
    ```

    \<IPResourceName > IP アドレスに関連付けられているリソースの名前を指定します

    \<Ip アドレス >、FCI の IP アドレスは、

    \<NetworkCard > サブネット (つまり eth0) に関連付けられているネットワーク カード

    \<ネットマスク > サブネット (つまり 24 個) のネットマスクは、

    \<RGName > リソース グループの名前を指定します
 
3.  FCI リソースを作成します。 表示されますありません応答に問題がない場合に戻します。

    ```bash
    sudo pcs resource create FCIResourceName ocf:mssql:fci op defaults timeout=60s --group RGName
    ```

    \<FCIResourceName > は、リソースの名前だけでなく、FCI に関連付けられているフレンドリ名。 これは、どのようなユーザーおよびアプリケーションが接続に使用します。 

    \<RGName >、リソース グループの名前を指定します。
 
4.  コマンドを実行`sudo pcs resource`です。 FCI をオンラインにする必要があります。
 
5.  SSMS または sqlcmd、FCI の DNS/リソース名を使用して FCI に接続します。

6.  ステートメントを発行`SELECT @@SERVERNAME`です。 FCI の名前を返します。

7.  ステートメントを発行`SELECT SERVERPROPERTY('ComputerNamePhysicalNetBIOS')`です。 FCI で実行されているノードの名前を返します。

8.  その他のノードに FCI を手動でフェールオーバーします。 下にある手順を参照して[Operate フェールオーバー クラスター インスタンス: SQL Server on Linux](sql-server-linux-shared-disk-cluster-operate.md)です。

9.  最後に、元のノードに戻したり、FCI を失敗し、コロケーション制約を削除します。

<!---
|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)
-->
## <a name="summary"></a>概要

このチュートリアルでは、次のタスクを完了しました。

> [!div class="checklist"]
> * 設定し、Linux を構成します。
> * SQL サーバー インストールし、構成
> * Hosts ファイルを構成します。
> * 共有記憶域を構成して、データベース ファイルの移動
> * インストールし、ペースを各クラスター ノードの構成
> * フェールオーバー クラスター インスタンスを構成します。

## <a name="next-steps"></a>次の手順

- [フェールオーバー クラスター インスタンス: Linux 上の SQL Server の動作します。](sql-server-linux-shared-disk-cluster-operate.md)

<!--Image references-->
