---
title: "SQL Server の Red Hat Enterprise Linux 共有クラスターを運用 |Microsoft ドキュメント"
description: "SQL Server の Red Hat Enterprise Linux 共有ディスク クラスターを構成することによって高可用性を実装します。"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 075ab7d8-8b68-43f3-9303-bbdf00b54db1
ms.workload: Inactive
ms.openlocfilehash: d3abecd450bbb734304c8c04909c38ae216595ad
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="operate-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>SQL Server の Red Hat Enterprise Linux 共有ディスク クラスターを運用します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このドキュメントでは、Red Hat Enterprise Linux、共有ディスク フェールオーバー クラスターで SQL Server を次のタスクを実行する方法について説明します。

- 手動でフェールオーバー クラスター
- フェールオーバー クラスターの SQL Server サービスを監視します。
- クラスター ノードを追加します。
- クラスター ノードを削除します。
- 頻度を監視する SQL Server リソースを変更します。

## <a name="architecture-description"></a>アーキテクチャの説明

クラスタ リングの層は Red Hat Enterprise Linux (RHEL) に基づいて[HA アドオン](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf)の上に構築[ペース](http://clusterlabs.org/)です。 Corosync とペースのクラスター ネットワーク通信およびリソース管理を調整します。 SQL Server のインスタンスは 1 つのノードまたは他の上でアクティブです。

次の図は、Linux クラスターで SQL Server コンポーネントを示しています。 

![Red Hat Enterprise Linux 7 ディスク SQL クラスターの共有](./media/sql-server-linux-shared-disk-cluster-red-hat-7-configure/LinuxCluster.png) 

クラスターの構成、リソース エージェント オプション、および管理の詳細については、次を参照してください。 [RHEL リファレンス ドキュメント](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html)です。

## <a name = "failManual"></a>フェールオーバー クラスターを手動で

`resource move`コマンドは、ターゲット ノードで起動するリソースを強制する制約を作成します。  実行した後、`move`リソースを実行したコマンド`clear`のため、リソースをもう一度移動したり、リソースを自動的にフェールオーバーすることは、制約が削除されます。 

```bash
sudo pcs resource move <sqlResourceName> <targetNodeName>  
sudo pcs resource clear <sqlResourceName> 
```

次の例では移動、 **mssqlha**という名前のノードにリソース**sqlfcivm2**、し、そのリソースが後での別のノードに移動できるように、制約を削除します。  

```bash
sudo pcs resource move mssqlha sqlfcivm2 
sudo pcs resource clear mssqlha 
```

## <a name="monitor-a-failover-cluster-sql-server-service"></a>フェールオーバー クラスターの SQL Server サービスを監視します。

現在のクラスターの状態を表示します。

```bash
sudo pcs status  
```

クラスターとリソースのライブ状態の表示:

```bash
sudo crm_mon 
```

リソースのエージェント ログを表示します。`/var/log/cluster/corosync.log`

## <a name="add-a-node-to-a-cluster"></a>クラスターにノードを追加します。

1. 各ノードの IP アドレスを確認してください。 次のスクリプトは、現在のノードの IP アドレスを示します。 

   ```bash
   ip addr show
   ```

3. 新しいノードに必要な一意の名前は 15 文字以下です。 コンピューター名は、既定では、Red Hat Linux`localhost.localdomain`です。 この既定の名前が一意でないが長すぎます。 新しいノードにコンピューター名を設定します。 追加することによって、コンピューター名を設定`/etc/hosts`です。 次のスクリプトを使うと、`vi` で `/etc/hosts` を編集できます。 

   ```bash
   sudo vi /etc/hosts
   ```

   次の例は`/etc/hosts`という 3 つのノードの追加と`sqlfcivm1`、 `sqlfcivm2`、および`sqlfcivm3`です。

   ```
   127.0.0.1   localhost localhost4 localhost4.localdomain4
   ::1         localhost localhost6 localhost6.localdomain6
   10.128.18.128 fcivm1
   10.128.16.77 fcivm2
   10.128.14.26 fcivm3
    ```
    
   ファイルは、すべてのノードで同じにする必要があります。 

1. 新しいノードに SQL Server サービスを停止します。

1. 共有の場所にデータベース ファイル ディレクトリをマウントする手順に従います。

   NFS サーバーから次のようにインストールします。`nfs-utils`

   ```bash
   sudo yum -y install nfs-utils 
   ``` 

   クライアントと NFS サーバー上のファイアウォールを open 

   ```bash
   sudo firewall-cmd --permanent --add-service=nfs
   sudo firewall-cmd --permanent --add-service=mountd
   sudo firewall-cmd --permanent --add-service=rpc-bind
   sudo firewall-cmd --reload
   ```

   Mount コマンドを含むように/etc/fstab ファイルを編集します。 

   ```bash
   <IP OF NFS SERVER>:<shared_storage_path> <database_files_directory_path> nfs timeo=14,intr
   ```

   実行`mount -a`変更を有効にするためにします。
   
1. 新しいノードで、SQL Server のユーザー名とペース ログインのパスワードを格納するファイルを作成します。 次のコマンドは、このファイルを作成および設定します。

   ```bash
   sudo touch /var/opt/mssql/passwd
   sudo echo "<loginName>" >> /var/opt/mssql/secrets/passwd
   sudo echo "<loginPassword>" >> /var/opt/mssql/secrets/passwd
   sudo chown root:root /var/opt/mssql/passwd
   sudo chmod 600 /var/opt/mssql/passwd
   ```

3. 新しいノードで、ペースのファイアウォール ポートを開きます。 `firewalld` を使用してこれらのポートを開くには、次のコマンドを実行します。

   ```bash
   sudo firewall-cmd --permanent --add-service=high-availability
   sudo firewall-cmd --reload
   ```

   > [!NOTE]
   > 組み込みの高可用性構成が備わっていない別のファイアウォールを使用する場合は、Pacemaker 用に次のポートを開き、クラスター内の他のノードと通信できるようにする必要があります
   >
   > * TCP: ポート 2224、3121、21064
   > * UDP: ポート 5405

1. 新しいノードにペース パッケージをインストールします。

   ```bash
   sudo yum install pacemaker pcs fence-agents-all resource-agents
   ```
 
2. Pacemaker と Corosync のパッケージをインストールしたときに作成された既定のユーザー用のパスワードを設定します。 既存のノードと同じパスワードを使用します。 

   ```bash
   sudo passwd hacluster
   ```
 
3. `pcsd` サービスと Pacemaker を有効にし、起動します。 これにより、新しいノードを再起動した後、クラスターを再参加が許可されます。 新しいノードには、次のコマンドを実行します。

   ```bash
   sudo systemctl enable pcsd
   sudo systemctl start pcsd
   sudo systemctl enable pacemaker
   ```

4. SQL Server の FCI リソース エージェントをインストールします。 新しいノードには、次のコマンドを実行します。 

   ```bash
   sudo yum install mssql-server-ha
   ```

1. 既存ノードでクラスターから、新しいノードを認証し、クラスターに追加します。

    ```bash
    sudo pcs    cluster auth <nodeName3> -u hacluster 
    sudo pcs    cluster node add <nodeName3> 
    ```

    次の例は、という名前のノードを追加**vm3**クラスターにします。

    ```bash
    sudo pcs    cluster auth  
    sudo pcs    cluster start 
    ```

## <a name="remove-nodes-from-a-cluster"></a>クラスターからノードを削除します。

次のコマンドを実行するクラスターからノードを削除します。

```bash
sudo pcs    cluster node remove <nodeName>  
```

## <a name="change-the-frequency-of-sqlservr-resource-monitoring-interval"></a>Sqlservr リソース監視の間隔の頻度を変更します。

```bash
sudo pcs    resource op monitor interval=<interval>s <sqlResourceName> 
```

次の例では、監視間隔を mssql リソースが 2 秒に設定します。

```bash
sudo pcs    resource op monitor interval=2s mssqlha 
```
## <a name="troubleshoot-red-hat-enterprise-linux-shared-disk-cluster-for-sql-server"></a>SQL Server の Red Hat Enterprise Linux 共有ディスク クラスターをトラブルシューティングします。

クラスターのトラブルシューティングに動作を理解する 3 つのデーモン一緒にクラスター リソースの管理に役立ちます。 

| デーモン | Description 
| ----- | -----
| Corosync | クォーラムのメンバーシップとクラスター ノード間のメッセージングを提供します。
| ペース | Corosync 上に存在し、ステート マシンのリソースを提供します。 
| PCSD | ペースとを通じて Corosync の両方を管理、`pcs`ツール

使用するために実行する必要あります PCSD`pcs`ツールです。 

### <a name="current-cluster-status"></a>クラスターの現在の状態 

`sudo pcs status`各ノードのクラスター、クォーラム、ノード、リソース、およびデーモンの状態に関する基本的な情報を返します。 

正常なペース クォーラム出力の例は次のようになります。

```
Cluster name: MyAppSQL 
Last updated: Wed Oct 31 12:00:00 2016  Last change: Wed Oct 31 11:00:00 2016 by root via crm_resource on sqlvmnode1 
Stack: corosync 
Current DC: sqlvmnode1  (version 1.1.13-10.el7_2.4-44eb2dd) - partition with quorum 
3 nodes and 1 resource configured 

Online: [ sqlvmnode1 sqlvmnode2 sqlvmnode3] 

Full list of resources: 

mssqlha (ocf::sql:fci): Started sqlvmnode1 

PCSD Status: 
sqlvmnode1: Online 
sqlvmnode2: Online 
sqlvmnode3: Online 

Daemon Status: 
corosync: active/disabled 
pacemaker: active/enabled 
```

例では、`partition with quorum`ノード マジョリティ クォーラムがオンラインであることを意味します。 クラスターはノード マジョリティ クォーラムを失った場合`pcs status`戻ります`partition WITHOUT quorum`され、すべてのリソースが中止されます。 

`online: [sqlvmnode1 sqlvmnode2 sqlvmnode3]`クラスターに現在参加しているすべてのノードの名前を返します。 すべてのノードが参加していない場合`pcs status`返します`OFFLINE: [<nodename>]`です。

`PCSD Status`各ノードのクラスターの状態を示しています。

### <a name="reasons-why-a-node-may-be-offline"></a>上の理由から、ノードをオフラインになる理由

ノードがオフラインのときは、次の項目を確認します。

- **ファイアウォール**

    次のポートは、通信できるようにするペースのすべてのノードで開かれている必要があります。
    
    - **TCP: 2224, 3121, 21064

- **ペースまたはを実行している Corosync services**

- **ノードの通信**

- **ノード名のマッピング**

## <a name="additional-resources"></a>その他のリソース

* [クラスターの最初から](http://clusterlabs.org/doc/Cluster_from_Scratch.pdf)ペースからガイド

## <a name="next-steps"></a>次の手順

[SQL Server の Red Hat Enterprise Linux 共有ディスク クラスターを構成します。](sql-server-linux-shared-disk-cluster-red-hat-7-configure.md)

