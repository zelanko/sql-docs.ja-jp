---
title: "Ubuntu クラスターは、SQL Server 可用性グループを構成する |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 01/30/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: dd0d6fb9-df0a-41b9-9f22-9b558b2b2233
ms.workload: Inactive
ms.openlocfilehash: d6a49bc2f3fb815cecda0e8a24a63993b5423103
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="configure-ubuntu-cluster-and-availability-group-resource"></a>Ubuntu クラスターと可用性グループ リソースを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このドキュメントでは、Ubuntu で 3 つのノードのクラスターを作成し、以前に作成した可用性グループをクラスター内のリソースとして追加する方法について説明します。 Linux 上の可用性グループ、可用性を高めるためには 3 つのノードが必要です - 参照[可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)です。

> [!NOTE] 
> この時点では、Linux 上のペースで SQL Server の統合は Windows での WSFC でとして結合します。 SQL 内ではありません、クラスターの存在についてのナレッジ、すべてのオーケストレーションの外部には、およびサービスが、スタンドアロン インスタンスとしてペースで制御されます。 また、仮想ネットワーク名は、WSFC を特定、相当するのと同じペースではありません。 Always On の動的管理ビューのクラスター情報を照会するには、空の行が返されます。 フェールオーバー後は、透過的な再接続に使用するリスナーを作成できますが、仮想 IP リソース (下記参照) を作成するために使用する ip アドレス、DNS サーバーで、リスナー名を手動で登録する必要があります。

次のセクションでは、フェールオーバー クラスター ソリューションをセットアップする手順について説明します。 

## <a name="roadmap"></a>ロードマップ

高可用性の Linux サーバーに可用性グループを作成する手順は、Windows Server フェールオーバー クラスター上の手順と異なります。 次に、手順の概要を説明します。 

1. [クラスター ノードの SQL Server を構成する](sql-server-linux-setup.md)です。

2. [可用性グループの作成](sql-server-linux-availability-group-configure-ha.md)です。 

3. ペースのように、クラスター リソース マネージャーを構成します。 これらの手順は、このドキュメントではします。
   
   クラスター リソース マネージャーを構成する方法は、特定の Linux ディストリビューションに依存します。 

   >[!IMPORTANT]
   >実稼働環境では、高可用性を実現 STONITH などのフェンス操作エージェントが必要です。 このドキュメントではデモンストレーションでは、フェンス操作エージェントは使用しないでください。 デモは、テストおよび検証のみです。 
   
   >Linux クラスターでは、フェンス操作を使用して、既知の状態をクラスターを返します。 フェンス操作を構成する方法は、分布と、環境によって異なります。 この時点でのフェンス操作は一部のクラウド環境で使用できません。 参照してください[RHEL 高可用性クラスターの仮想化プラットフォームのサポート ポリシー](https://access.redhat.com/articles/29440)詳細についてはします。

5.  [可用性グループ、クラスター内のリソースとして追加](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)です。 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>インストールし、ペースを各クラスター ノードの構成

1. すべてのノードでファイアウォール ポートを開きます。 ペースの高可用性サービス、SQL Server インスタンス、および可用性グループのエンドポイントのポートを開きます。 SQL Server を実行しているサーバーの既定の TCP ポートは 1433 です。  

   ```bash
   sudo ufw allow 2224/tcp
   sudo ufw allow 3121/tcp
   sudo ufw allow 21064/tcp
   sudo ufw allow 5405/udp
        
   sudo ufw allow 1433/tcp # Replace with TDS endpoint
   sudo ufw allow 5022/tcp # Replace with DATA_MIRRORING endpoint
        
   sudo ufw reload
   ```
   
   代わりに、ファイアウォールをのみ無効にすることができます。
        
   ```bash
   sudo ufw disable
   ```

1. ペース パッケージをインストールします。 すべてのノードでは、次のコマンドを実行します。

   ```bash
   sudo apt-get install pacemaker pcs fence-agents resource-agents
   ```

2. Pacemaker と Corosync のパッケージをインストールしたときに作成された既定のユーザー用のパスワードを設定します。 すべてのノードで同じパスワードを使います。 

   ```bash
   sudo passwd hacluster
   ```

## <a name="enable-and-start-pcsd-service-and-pacemaker"></a>有効にして pcsd サービスとペースを開始

次のコマンドは、有効にし、pcsd サービスとペースを開始します。 すべてのノードで実行します。 これは、再起動後に、クラスターに再度参加するノードです。 

```bash
sudo systemctl enable pcsd
sudo systemctl start pcsd
sudo systemctl enable pacemaker
```
>[!NOTE]
>有効にするペース コマンドがエラーで完了可能性があります 'ペース既定の開始を含まないランレベルを中止しています ' 影響を与えませんが、クラスター構成を続行できます。 

## <a name="create-the-cluster"></a>クラスターを作成します。

1. すべてのノードから、既存のクラスター構成を削除します。 

   Running 'sudo apt-get install pcs' installs pacemaker, corosync, and pcs at the same time and starts running all 3 of the services.  テンプレートが生成される開始 corosync '/etc/cluster/corosync.conf' ファイル。  次の手順をこのファイルを正常に存在してはいけません – 回避ペースを停止するには、/corosync および削除 '/etc/cluster/corosync.conf' とし、次の手順が正常に完了します。 'pc クラスターを破棄' 同じ操作を実行し、1 つとして使用することができますに初期クラスター セットアップの手順です。
   
   次のコマンドは、既存のクラスターの構成ファイルを削除し、すべてのクラスター サービスを停止します。 クラスターが完全に破棄します。 実稼働前環境の最初の手順として実行します。 注 'pc クラスターを破棄こと' は無効、ペースのサービスに再度有効にする必要があります。 すべてのノードで次のコマンドを実行します。
   
   >[!WARNING]
   >コマンドでは、すべて既存のクラスター リソースを破棄します。

   ```bash
   sudo pcs cluster destroy 
   sudo systemctl enable pacemaker
   ```

1. クラスターを作成します。 

   >[!WARNING]
   >クラスター ('pc クラスター start') は、クラスタ リングの仕入先があり、調査して、開始する既知の問題により、以下のエラーで失敗します。 ログ ファイルは、クラスター セットアップ コマンドが実行時に作成されて、間違った/etc/corosync/corosync.conf で構成されているためにです。 この問題を回避するには、ログ ファイルを変更:/var/log/corosync/corosync.log です。 また、/var/log/cluster/corosync.log ファイルを作成します。
 
   ```Error
   Job for corosync.service failed because the control process exited with error code. 
   See "systemctl status corosync.service" and "journalctl -xe" for details.
   ```
  
次のコマンドでは、3 つのノードのクラスターを作成します。 スクリプトを実行する前に、`< ... >` の間の値を置き換えます。 プライマリ ノードで次のコマンドを実行します。 

   ```bash
   sudo pcs cluster auth <node1> <node2> <node3> -u hacluster -p <password for hacluster>
   sudo pcs cluster setup --name <clusterName> <node1> <node2…> <node3>
   sudo pcs cluster start --all
   ```
   
   >[!NOTE]
   >前に同じノードでクラスターを構成した場合は、"pcs cluster setup" を実行するときに "--force" オプションを使用する必要があります。 これは、"pcs cluster destroy" を実行するのと同じあり、"sudo systemctl enable pacemaker" を使用して、Pacemaker のサービスを再度有効にする必要がある点に注意してください。


## <a name="configure-fencing-stonith"></a>フェンス操作 (STONITH) を構成します。

ペース クラスターのベンダーは、STONITH を有効にして、サポートされているクラスターのセットアップ用に構成されたフェンス操作デバイスが必要です。 ノードまたはノード上のリソースの状態を判断できないのは、クラスター リソース マネージャー、既知の状態をクラスターに戻すにフェンス操作が使用されます。 主ににより、リソース レベルのフェンス操作はリソースを構成することにより、障害が発生した場合、データの破損がないことです。 リソース レベルのフェンス操作を使用するインスタンスのように古くなった場合に、ノード上のディスクをマークする DRBD (レプリケート ブロック デバイスの分散) との通信リンクがダウンしました。 ノード レベルのフェンス操作により、ノードがすべてのリソースを実行できません。 ノードをリセットすることによってこれし、ペース実装は STONITH (これは、「head で、他のノードを撮影」の略) と呼ばれます。 例: 無停電電源装置または管理インターフェイスのサーバーのカードをペースがさまざまなデバイスのフェンス操作をサポートします。 詳細については、次を参照してください[を最初からペース クラスター](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html)と[フェンス操作と Stonith。](http://clusterlabs.org/doc/crm_fencing.html) 

フェンス構成ノードのレベルは、環境内に大きく依存するため無効に、このチュートリアルでは (後で、構成できます)。 プライマリ ノードで、次のスクリプトを実行します。 

```bash
sudo pcs property set stonith-enabled=false
```

>[!IMPORTANT]
>テストのためだけには STONITH を無効にします。 実稼働環境でペースを使用する場合は、環境に応じて STONITH 実装を計画して有効にしておいてください。 この時点でがないことにクラウド環境でも (Azure を含む) や HYPER-V フェンス操作エージェントに注意してください。 ので、クラスターのベンダーでは、これらの環境で運用クラスターを実行するためのサポートは提供しません。 

## <a name="set-cluster-property-start-failure-is-fatal-to-false"></a>開始-障害が-致命的でクラスターのプロパティが false に設定します。

`start-failure-is-fatal`ノードにリソースを起動しますの失敗によってそのノードに対して試行された開始でがさらにかどうかを示します。 設定すると`false`クラスターは、リソースの現在の失敗数と移行のしきい値に基づいて、もう一度同じノードで起動するかどうかを決定します。 そのため、フェールオーバーが発生した後、SQL インスタンスが使用可能なペースの再試行回数が、可用性を開始には以前のプライマリ上のリソースがグループ化します。 ペースがセカンダリ レプリカを降格し、可用性グループを自動的に再度参加します。 

プロパティの値を更新する`false`次のスクリプトを実行します。

```bash
sudo pcs property set start-failure-is-fatal=false
```


>[!WARNING]
>自動フェールオーバーの後と`start-failure-is-fatal = true`リソース マネージャーは、リソースを開始しようとしています。 手動で実行しなければならない場合、最初の試行に失敗した場合は`pcs resource cleanup <resourceName>`リソース障害の数をクリーンアップし、構成をリセットします。

## <a name="install-sql-server-resource-agent-for-integration-with-pacemaker"></a>ペースで統合するための SQL Server リソースのエージェントをインストールします。

すべてのノードで次のコマンドを実行します。 

```bash
sudo apt-get install mssql-server-ha
```

## <a name="create-a-sql-server-login-for-pacemaker"></a>ペースの SQL Server ログインを作成します。

[!INCLUDE [SLES-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="create-availability-group-resource"></a>可用性グループ リソースを作成します。

可用性グループ リソースを作成するには使用`pcs resource create`コマンドおよびリソース プロパティを設定します。 次のコマンドを作成、`ocf:mssql:ag`型のリソースの名前を持つ可用性グループのマスター/スレーブ`ag1`です。 

```bash
sudo pcs resource create ag_cluster ocf:mssql:ag ag_name=ag1 --master meta notify=true

```

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

## <a name="create-virtual-ip-resource"></a>仮想 IP リソースを作成します。

仮想 IP アドレス リソースを作成するには、1 つのノードで次のコマンドを実行します。 ネットワークから使用可能な静的 IP アドレスを使用します。 スクリプトを実行する前に、までの値を置き換える`< ... >`有効な IP アドレスを使用します。

```bash
sudo pcs resource create virtualip ocf:heartbeat:IPaddr2 ip=<10.128.16.240>
```

同じペースで仮想サーバー名がありません。 文字列のサーバー名を指す接続文字列を使用し、IP アドレスを使用しない、目的の仮想サーバー名と IP リソースのアドレスを DNS に登録します。 災害復旧構成のプライマリおよび災害復旧サイトの両方で DNS サーバーで、目的の仮想サーバー名と IP アドレスを登録します。

## <a name="add-colocation-constraint"></a>コロケーションの制約を追加します。

ペース クラスターでは、リソースを実行する場所を選択するようのほとんどすべての意思決定は、スコアを比較することによって行われます。 スコアの計算リソース、およびクラスター リソース マネージャーは、特定のリソースのスコアが最も高いノードを選択します。 (ノードにリソースの負のスコアがある場合は、リソースで実行できませんノード。)クラスターの意思決定を構成するのにには、制約を使用します。 制約では、スコアがあります。 制約に無限大より小さいスコアがある場合は、推奨設定のみを勧めします。 必須では無限大のスコアを意味します。 プライマリ レプリカと仮想 ip リソースが、同じホスト上にあることを確認、スコアの無限大のコロケーション制約を定義します。 コロケーション制約を追加するには、1 つのノードで次のコマンドを実行します。 

```bash
sudo pcs constraint colocation add virtualip ag_cluster-master INFINITY with-rsc-role=Master
```

## <a name="add-ordering-constraint"></a>順序付けの制約を追加します。

コロケーションの制約には、暗黙的な順序付け制約があります。 可用性グループ リソースを移動する前に、仮想 IP リソースを移動します。 既定で、一連のイベントは次のとおりです。

1. ユーザーの問題`pcs resource move`可用性グループにプライマリ node1 から node2 にします。
1. 仮想 IP リソースは、node1 を停止します。
1. 仮想 IP リソースは node2 で開始します。

   >[!NOTE]
   >この時点では、IP アドレスの一時的を node2 にポイント node2 が前のフェールオーバーではまだセカンダリ。 
   
1. Node1 でプライマリ可用性グループは、セカンダリに降格されます。
1. Node2 でセカンダリ可用性グループがプライマリに昇格します。 

IP アドレスが一時的にフェイル オーバー前のセカンダリを持つノードを指すようにするのには、順序付けの制約を追加します。 

順序付けの制約を追加するには、1 つのノードで次のコマンドを実行します。

```bash
sudo pcs constraint order promote ag_cluster-master then start virtualip
```

>[!IMPORTANT]
>クラスターを構成し、可用性グループをクラスター リソースとして追加した後は TRANSACT-SQL を使用して、可用性グループのリソースをフェールオーバーすることはできません。 Linux 上の SQL Server クラスター リソースと関連していない緊密にオペレーティング システムで、Windows Server フェールオーバー クラスター (WSFC) とします。 SQL Server サービスでは、クラスターの存在を認識しません。 すべてのオーケストレーションは、クラスター管理ツールを使って行われます。 RHEL または Ubuntu を使用して`pcs`です。 

<!---[!INCLUDE [Pacemaker Concepts](..\includes\ss-linux-cluster-pacemaker-concepts.md)]--->

## <a name="next-steps"></a>次の手順

[HA 可用性グループを操作します。](sql-server-linux-availability-group-failover-ha.md)

