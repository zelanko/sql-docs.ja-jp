---
title: SQL Server Linux (RHEL) でのフェールオーバー クラスター インスタンスを構成します。
description: ''
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 08/28/2017
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 31c8c92e-12fe-4728-9b95-4bc028250d85
ms.openlocfilehash: 407e1e11bcaf2c1b7ffe0426c6a3c7493e71bc74
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833163"
---
# <a name="configure-failover-cluster-instance---sql-server-on-linux-rhel"></a>SQL Server Linux (RHEL) でのフェールオーバー クラスター インスタンスを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

SQL Server の 2 つのノードの共有ディスク フェールオーバー クラスターのインスタンスは、高可用性のためのサーバー レベルの冗長性を提供します。 このチュートリアルでは、Linux 上の SQL Server の 2 ノード フェールオーバー クラスター インスタンスを作成する方法について説明します。 完了が特定の手順は次のとおりです。

> [!div class="checklist"]
> * 設定および Linux を構成します。
> * インストールして SQL Server の構成
> * ホスト ファイルを構成します。
> * 共有記憶域を構成し、データベース ファイルの移動
> * 各クラスター ノードでPacemakerインストールして構成する
> * フェールオーバー クラスター インスタンスを構成します。

この記事では、SQL Server の 2 つのノードの共有ディスク フェールオーバー クラスター インスタンス (FCI) を作成する方法について説明します。 この記事には Red Hat Enterprise Linux (RHEL) の手順とスクリプトの例が含まれています。 Ubuntu ディストリビューションは、スクリプトの例は、通常されます RHEL のような Ubuntu でも機能します。 

概念については、次を参照してください。 [SQL Server フェールオーバー クラスター インスタンス (FCI) で Linux](sql-server-linux-shared-disk-cluster-concepts.md)します。

## <a name="prerequisites"></a>前提条件

次のエンド ツー エンド シナリオを完了するには、2 つのマシンが 2 つのノード クラスターと記憶域を別のサーバーを展開する必要があります。 以下の手順には、これらのサーバーを構成する方法を説明します。

## <a name="set-up-and-configure-linux"></a>設定および Linux を構成します。

最初の手順では、クラスター ノードで、オペレーティング システムを構成します。 クラスター内の各ノードでは、linux ディストリビューションを構成します。 両方のノードで、同じディストリビューションとバージョンを使用します。 いずれかまたは次のディストリビューションの他のいずれかを使用します。
    
* RHEL HA アドオンの有効なサブスクリプション

## <a name="install-and-configure-sql-server"></a>インストールして SQL Server の構成

1. インストールし、両方のノードで、SQL Server を設定します。  詳細については、次を参照してください。 [Linux 上の SQL Server のインストール](sql-server-linux-setup.md)します。
1. 構成のために、1つのノードをプライマリとして指定し、もう片方をセカンダリとして指定します。 このガイドでは、これ以降これらの用語を使用します。  
1. セカンダリ ノードでSQL Server を停止し無効にします。
    次の例では、SQL Server を停止して無効にします。 
    ```bash
    sudo systemctl stop mssql-server
    sudo systemctl disable mssql-server
    ```

    > [!NOTE] 
    > サーバーのマスター _ キーの SQL Server インスタンスの生成し、に配置に時間を設定するには、`var/opt/mssql/secrets/machine-key`します。 Linux では、SQL Server は、常に mssql と呼ばれるローカル アカウントとして実行されます。 ローカル アカウントであるために、その id は、ノード間で共有されません。 したがって、各ローカル mssql アカウント がサーバー マスター  キーの暗号化を解除するためにアクセスできるようにするために、各セカンダリ ノードにプライマリ ノードから暗号化キーをコピーする必要があります。 

1.  プライマリ ノードで、Pacemaker 用 SQL server ログインを作成および実行する権限をログイン`sp_server_diagnostics`します。 Pacemaker は、このアカウントを使用して、ノードは、SQL Server を実行していることを確認します。 

    ```bash
    sudo systemctl start mssql-server
    ```
   
   SQL Server の`master`データベースに sa アカウントを使用して接続し、次のスクリプトを実行します。

   ```sql
   USE [master]
   GO
   CREATE LOGIN [<loginName>] with PASSWORD= N'<loginPassword>'
   ALTER SERVER ROLE [sysadmin] ADD MEMBER [<loginName>]
   ```

   このスクリプトの代わりに、より細かなレベルでアクセス許可を設定することもできます。 Pacemaker のログインが必要です`VIEW SERVER STATE`sp_server_diagnostics の正常性状態をクエリする`setupadmin`と`ALTER ANY LINKED SERVER`sp_dropserver sp_addserver を実行して、リソース名を持つ FCI インスタンスの名前を更新します。 

1. プライマリ ノードで、SQL Server を停止し無効にします。 

## <a name="configure-the-hosts-file"></a>ホスト ファイルを構成します。

各クラスター ノードでは、hosts ファイルを構成します。 Hosts ファイルには、すべてのクラスター ノードの名前と IP アドレスを含める必要があります。

1. 各ノードの IP アドレスを確認します。 次のスクリプトでは、現在のノードの IP アドレスを示します。 

    ```bash
    sudo ip addr show
    ```

1. 各ノードで、コンピューター名を設定します。 各ノードに 15 文字以下の一意の名前を指定します。 そのコンピューター名を`/etc/hosts`に追加することにより設定します。 次のスクリプトを使うと、`vi` で `/etc/hosts` を編集できます。 

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

## <a name="configure-storage--move-database-files"></a>記憶域を構成するし、データベース ファイルの移動  

両方のノードにアクセスできる記憶域を提供する必要があります。 ISCSI、NFS、または SMB を使用することができます。 記憶域の構成や、記憶域クラスターのノードに提供する新しい記憶域にデータベース ファイルを移動します。 次の記事では、記憶域の種類ごとの手順について説明します。

- [フェールオーバー クラスター インスタンスの iSCSI - SQL Server on Linux を構成します。](sql-server-linux-shared-disk-cluster-configure-iscsi.md)
- [NFS - SQL Server on Linux を構成するには、フェールオーバー クラスター インスタンス。](sql-server-linux-shared-disk-cluster-configure-nfs.md)
- [フェールオーバー クラスター インスタンス - SMB - SQL Server on Linux の構成します。](sql-server-linux-shared-disk-cluster-configure-smb.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>各クラスター ノードでPacemakerインストールして構成する

1. 両方のクラスター ノードで、Pacemaker がログインするための SQL Server のユーザー名とパスワードを格納するファイルを作成します。 

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

   > 組み込みの高可用性構成がない別のファイアウォールを使用している場合、次のポートが、クラスター内の他のノードと通信できる Pacemaker 用に開かれる必要があります。
   >
   > * TCP: ポート、2224 3121、21064
   > * UDP:ポート 5405

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

FCI は、リソース グループに作成されます。 これは、機能は、リソース グループの制約の必要性を軽減するため、もう少し簡単です。 ただし、開始する必要がありますの順序でリソース グループにリソースを追加します。 開始する必要があります、順序は次のとおりです。 

1. ストレージ リソース
2. ネットワーク リソース
3. アプリケーションのリソース

この例では、NewLinFCIGrp グループで FCI を作成します。 リソース グループの名前は、Pacemaker で作成したリソースから一意である必要があります。

1.  ディスク リソースを作成します。 応答が返されますしない問題がない場合。 ディスク リソースを作成する方法は、ストレージの種類によって異なります。 各ストレージの種類の例を次に示します。 クラスター化された記憶域の記憶域の種類に適用する例を使用します。

    **iSCSI**

    ```bash
    sudo pcs resource create <iSCSIDiskResourceName> Filesystem device="/dev/<VolumeGroupName>/<LogicalVolumeName>" directory="<FolderToMountiSCSIDisk>" fstype="<FileSystemType>" --group RGName
    ```

    \<iSCSIDIskResourceName > iSCSI ディスクに関連付けられているリソースの名前を指定します

    \<VolumeGroupName > ボリューム グループの名前を指定します  

    \<LogicalVolumeName > が作成された論理ボリュームの名前を指定します  

    \<FolderToMountiSCSIDIsk > は、ディスクをマウントするフォルダーです (システム データベースと既定の場所は、なります/var/opt/mssql/data)

    \<FileSystemType > によって処理された書式設定方法と、どのような配布をサポートしています EXT4 または XFS があります。 

    **NFS**

    ```bash
    sudo pcs resource create <NFSDiskResourceName> Filesystem device="<IPAddressOfNFSServer>:<FolderOnNFSServer>" directory="<FolderToMountNFSShare>" fstype=nfs4 options=" nfsvers=4.2,timeo=14,intr" --group RGName
    mount -t nfs4 IPAddressOfNFSServer:FolderOnNFSServer /var/opt/mssql/data -o 
    ```

    \<NFSDIskResourceName > NFS 共有に関連付けられたリソースの名前を指定します

    \<IPAddressOfNFSServer > を使用している NFS サーバーの IP アドレスです

    \<FolderOnNFSServer >、NFS 共有の名前を指定します

    \<FolderToMountNFSShare > は、ディスクをマウントするフォルダーです (システム データベースと既定の場所は、なります/var/opt/mssql/data)

    例を次に示します。

    ```bash
    mount -t nfs4 200.201.202.63:/var/nfs/fci1 /var/opt/mssql/data -o nfsvers=4.2,timeo=14,intr
    ```

    **SMB**

    ```bash
    sudo pcs resource create SMBDiskResourceName Filesystem device="//<ServerName>/<ShareName>" directory="<FolderName>" fstype=cifs options="vers=3.0,username=<UserName>,password=<Password>,domain=<ADDomain>,uid=<mssqlUID>,gid=<mssqlGID>,file_mode=0777,dir_mode=0777" --group <RGName>
    ```

    \<ServerName > は SMB 共有を使用したサーバーの名前です

    \<共有名 > は、共有の名前です

    \<フォルダー名 > は、最後の手順で作成したフォルダーの名前です
    
    \<ユーザー名 > の共有にアクセスするユーザーの名前を指定します

    \<パスワード > は、ユーザーのパスワード

    \<ADDomain > (該当する場合、Windows Server ベースの SMB 共有を使用する場合)、AD DS ドメインは、

    \<mssqlUID > mssql ユーザーの UID は、

    \<mssqlGID > mssql ユーザーの GID は、

    \<RGName > リソース グループの名前を指定します
 
2.  FCI によって使用される IP アドレスを作成します。 応答が返されますしない問題がない場合。

    ```bash
    sudo pcs resource create <IPResourceName> ocf:heartbeat:IPaddr2 ip=<IPAddress> nic=<NetworkCard> cidr_netmask=<NetMask> --group <RGName>
    ```

    \<IPResourceName > IP アドレスに関連付けられたリソースの名前を指定します

    \<Ip アドレス > は、FCI の IP アドレス

    \<NetworkCard > (つまり eth0) サブネットに関連付けられているネットワーク カードには

    \<ネットマスク > サブネット (つまり 24) のネットマスクは、

    \<RGName > リソース グループの名前を指定します
 
3.  FCI のリソースを作成します。 応答が返されますしない問題がない場合。

    ```bash
    sudo pcs resource create FCIResourceName ocf:mssql:fci op defaults timeout=60s --group RGName
    ```

    \<FCIResourceName > だけでなく、リソースの名前が、FCI に関連付けられているフレンドリ名。 これは、どのようなユーザーとアプリケーションが接続に使用します。 

    \<RGName > リソース グループの名前を指定します。
 
4.  コマンドを実行`sudo pcs resource`します。 FCI は、オンラインにする必要があります。
 
5.  SSMS または FCI の DNS/リソース名を使用して sqlcmd で FCI に接続します。

6.  ステートメントを発行`SELECT @@SERVERNAME`します。 FCI の名前が返されます。

7.  ステートメントを発行`SELECT SERVERPROPERTY('ComputerNamePhysicalNetBIOS')`します。 FCI がで実行されているノードの名前が返されます。

8.  その他のノードに FCI を手動で失敗します。 」の手順を参照してください。 [Operate フェールオーバー クラスター インスタンス - SQL Server on Linux](sql-server-linux-shared-disk-cluster-operate.md)します。

9.  最後に、FCI を元のノードが失敗して、コロケーションの制約を削除します。

<!---

|Distribution |Topic 
|----- |-----
|**Red Hat Enterprise Linux with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)<br/>[Operate](sql-server-linux-shared-disk-cluster-red-hat-7-operate.md)
|**SUSE Linux Enterprise Server with HA add-on** |[Configure](sql-server-linux-shared-disk-cluster-sles-configure.md)

-->
## <a name="summary"></a>まとめ

このチュートリアルでは、次のタスクを完了します。

> [!div class="checklist"]
> * 設定および Linux を構成します。
> * インストールして SQL Server の構成
> * ホスト ファイルを構成します。
> * 共有記憶域を構成し、データベース ファイルの移動
> * 各クラスター ノードでPacemakerインストールして構成する
> * フェールオーバー クラスター インスタンスを構成します。

## <a name="next-steps"></a>次の手順

- [Linux 上の SQL Server のフェールオーバー クラスター インスタンスを動作します。](sql-server-linux-shared-disk-cluster-operate.md)

<!--Image references-->
