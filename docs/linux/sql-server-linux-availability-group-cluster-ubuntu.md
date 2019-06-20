---
title: SQL Server 可用性グループ用の Ubuntu クラスターを構成します。
titleSuffix: SQL Server
description: Ubuntu の可用性グループのクラスターを作成する方法について説明します
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: dd0d6fb9-df0a-41b9-9f22-9b558b2b2233
ms.openlocfilehash: 322ace7103fcba46894b56862c5066391cbe9f0e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66713428"
---
# <a name="configure-ubuntu-cluster-and-availability-group-resource"></a>Ubuntu のクラスターと可用性グループ リソースを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このドキュメントでは、Ubuntu 上で 3 ノード クラスターを作成し、クラスター内のリソースとして以前に作成した可用性グループを追加する方法について説明します。 可用性を高めるためにはLinux 上の可用性グループでは 3 つのノードが必要です - [可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)を参照してください。

> [!NOTE] 
> この時点では、Linux 上の Pacemaker との SQL Server の統合は、Windows の WSFC でとして結合ではありません。 SQL 内ではありません、クラスターの存在に関する知識、すべてのオーケストレーションは、外部、およびサービスは、スタンドアロン インスタンスとして Pacemaker によって制御されます。 また、仮想ネットワーク名は、WSFC を特定、Pacemaker で同じの相当するものはありません。 Always On 動的管理ビューに対してクエリ実行クラスター情報には、空の行が返されます。 フェールオーバー後は、透過的に再接続するために使用するリスナーを作成できますが、(次のセクションで説明) と仮想 IP リソースを作成するために使用する ip アドレス、DNS サーバーで、リスナー名を手動で登録する必要があります。

次のセクションでは、フェールオーバー クラスター ソリューションを設定する手順について説明します。 

## <a name="roadmap"></a>ロードマップ

高可用性の Linux サーバーに可用性グループを作成する手順は、Windows Server フェールオーバー クラスターの手順と異なります。 手順の概要を以下に説明します。 

1. [SQL Server のクラスター ノードで構成](sql-server-linux-setup.md)します。

2. [可用性グループの作成](sql-server-linux-availability-group-configure-ha.md)です。 

3. Pacemaker のように、クラスター リソース マネージャーを構成します。 これらの手順は、このドキュメントに記載されています。
   
   クラスター リソース マネージャーを構成する方法は、特定の Linux ディストリビューションによって異なります。 

   >[!IMPORTANT]
   >運用環境では、高可用性の STONITH などのフェンス エージェントが必要です。 このドキュメントでは、フェンス エージェントを使用しないでください。 デモはテストおよび検証のみです。 
   
   >Linux クラスターでは、フェンスを使用して、既知の状態、クラスターを返します。 フェンスを構成する方法は、ディストリビューションと、環境によって異なります。 この時点で、フェンス操作の対象は一部のクラウド環境で使用できません。 参照してください[RHEL 高可用性クラスターの仮想化プラットフォームのサポート ポリシー](https://access.redhat.com/articles/29440)詳細についてはします。

5.  [可用性グループ、クラスター内のリソースとして追加](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)します。 

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>各クラスター ノードでPacemakerインストールして構成する

1. すべてのノードでファイアウォール ポートを開きます。 Pacemaker の高可用性サービス、SQL Server インスタンス、および可用性グループのエンドポイントのポートを開きます。 SQL Server を実行しているサーバーの既定の TCP ポートは 1433 ですです。  

   ```bash
   sudo ufw allow 2224/tcp
   sudo ufw allow 3121/tcp
   sudo ufw allow 21064/tcp
   sudo ufw allow 5405/udp
        
   sudo ufw allow 1433/tcp # Replace with TDS endpoint
   sudo ufw allow 5022/tcp # Replace with DATA_MIRRORING endpoint
        
   sudo ufw reload
   ```
   
   また、ファイアウォールをのみ無効にできます。
        
   ```bash
   sudo ufw disable
   ```

1. Pacemaker パッケージをインストールします。 すべてのノードで、次のコマンドを実行します。

   ```bash
   sudo apt-get install pacemaker pcs fence-agents resource-agents
   ```

2. Pacemaker と Corosync のパッケージをインストールしたときに作成された既定のユーザー用のパスワードを設定します。 すべてのノードで同じパスワードを使います。 

   ```bash
   sudo passwd hacluster
   ```

## <a name="enable-and-start-pcsd-service-and-pacemaker"></a>有効にして pcsd サービスと Pacemaker を開始

次のコマンドは、有効にし、pcsd サービスと pacemaker を開始します。 すべてのノードで実行します。 これは、再起動後に、クラスターに再度参加するノードです。 

```bash
sudo systemctl enable pcsd
sudo systemctl start pcsd
sudo systemctl enable pacemaker
```
>[!NOTE]
>Enable pacemaker コマンドがエラーで完了ことがあります 'pacemaker の既定の開始に中止ランレベルありません ' これは、無害でクラスター構成を続行できます。 

## <a name="create-the-cluster"></a>クラスターを作成します。

1. すべてのノードから、既存のクラスター構成を削除します。 

   実行中の 'sudo apt-get install pc' は、pacemaker、corosync、および pc を同時にインストールし、3 つすべてのサービスの実行を開始します。  Corosync を起動するには、テンプレートが生成されます。 '/etc/cluster/corosync.conf' ファイル。  次の手順をこのファイルを成功に存在してはいけません - 回避 pacemaker を停止するには、/corosync および削除 '/etc/cluster/corosync.conf' とし、次の手順が正常に完了します。 同じことには 'pcs cluster destroy' と、1 つとして使用することができますに最初のクラスターのセットアップ手順です。
   
   次のコマンドは、既存のクラスター構成ファイルを削除し、すべてのクラスター サービスを停止します。 これにより、クラスターが完全に破棄します。 実稼働前環境での最初の手順として実行します。 注 pacemaker サービスと、再度有効にする必要があること"pcs cluster destroy' 無効になっています。 すべてのノードで次のコマンドを実行します。
   
   >[!WARNING]
   >コマンドは、既存のクラスター リソースを破棄します。

   ```bash
   sudo pcs cluster destroy 
   sudo systemctl enable pacemaker
   ```

1. クラスターを作成します。 

   >[!WARNING]
   >クラスタ リングのベンダーの調査、開始する既知の問題により、クラスター ('pc クラスター start') は、次のエラーで失敗します。 これは、ログ ファイルは、クラスターのセットアップ コマンドが実行時に作成、間違っている/etc/corosync/corosync.conf で構成されているためにです。 この問題を回避するには、ログ ファイルを変更:/var/log/corosync/corosync.log します。 また、/var/log/cluster/corosync.log ファイルを作成できます。
 
   ```Error
   Job for corosync.service failed because the control process exited with error code. 
   See "systemctl status corosync.service" and "journalctl -xe" for details.
   ```
  
次のコマンドは、3 ノード クラスターを作成します。 スクリプトを実行する前に、`< ... >` の間の値を置き換えます。 プライマリ ノードで、次のコマンドを実行します。 

   ```bash
   sudo pcs cluster auth <node1> <node2> <node3> -u hacluster -p <password for hacluster>
   sudo pcs cluster setup --name <clusterName> <node1> <node2...> <node3>
   sudo pcs cluster start --all
   sudo pcs cluster enable --all
   ```
   
   >[!NOTE]
   >前に同じノードでクラスターを構成した場合は、"pcs cluster setup" を実行するときに "--force" オプションを使用する必要があります。 これは、"pcs cluster destroy" を実行するのと同じあり、"sudo systemctl enable pacemaker" を使用して、Pacemaker のサービスを再度有効にする必要がある点に注意してください。


## <a name="configure-fencing-stonith"></a>フェンス (STONITH) を構成します。

Pacemaker クラスターのベンダーは、STONITH を有効にして、サポートされているクラスターのセットアップ用に構成されたフェンス操作デバイスを必要としています。 ノードまたはノード上のリソースの状態を判断できないのは、クラスター リソース マネージャー、既知の状態、クラスターを再度表示するフェンス操作が使用されます。 リソース レベルのフェンス操作はにより主に、リソースを構成することによって、障害発生時のデータの破損がないこと。 リソース レベルのフェンスを使用することができます、ように期限切れの場合、ノード上のディスクをマークする DRBD (レプリケートされたブロック デバイスの分散) との通信リンクがダウンしました。 ノード レベルのフェンス操作により、ノードがどのリソースも実行しないことが保証されます。 ノードをリセットすることでこれし、その Pacemaker 実装には、STONITH (これは「その他のノードを先頭に撮影」略) が呼び出されます。 例:、無停電電源装置または管理インターフェイスのサーバーのカード、pacemaker がさまざまな優れたフェンス デバイスをサポートします。 詳細については、次を参照してください[Pacemaker クラスターを最初から](https://clusterlabs.org/pacemaker/doc/en-US/Pacemaker/1.1/html/Clusters_from_Scratch/)と[フェンスと Stonith。](https://clusterlabs.org/doc/crm_fencing.html) 

フェンス構成ノードのレベルが、環境と大きく依存しているため無効に (後で、構成可能) このチュートリアルでは。 プライマリ ノードで、次のスクリプトを実行します。 

```bash
sudo pcs property set stonith-enabled=false
```

>[!IMPORTANT]
>STONITH を無効にするのはテスト目的のみです。 実稼働環境で Pacemaker を使用する場合は、環境に応じて STONITH 実装を計画して有効にしておいてください。 この時点でないこと (Azure を含む) のクラウド環境や HYPER-V フェンス エージェントに注意してください。 このため、クラスターのベンダーでは、これらの環境で運用のためにクラスターを実行するサポートは提供していません。 

## <a name="set-cluster-property-cluster-recheck-interval"></a>クラスター プロパティ クラスター-再確認-間隔を設定します。

`cluster-recheck-interval` リソース パラメーター、制約、またはその他のクラスターのオプションの変更のポーリング間隔、クラスターの確認を示します。 クラスターがしてバインドされている間隔で、レプリカを再起動しようとした場合は、レプリカがダウンしても、`failure-timeout`値と`cluster-recheck-interval`値。 たとえば場合、 `failure-timeout` 60 秒に設定されていると`cluster-recheck-interval`設定されている 120 秒間隔は 60 秒より大きく 120 秒未満で、再起動が試行します。 60 をクラスター再確認-間隔を 60 秒よりも大きい値には、エラー タイムアウトを設定することをお勧めします。 クラスター-再確認-間隔を小さい値に設定することは推奨されません。

プロパティの値を`2 minutes`に更新するには、次のコマンドを実行します。

```bash
sudo pcs property set cluster-recheck-interval=2min
```

> [!IMPORTANT] 
> Pacemaker クラスターによって管理されている可用性グループ リソースは、既にある場合は、最新使用可能な Pacemaker パッケージ 1.1.18-11.el7 を使用するすべてのディストリビューションが開始-障害が-致命的でクラスターの場合に、設定の動作の変更を導入ことに注意してください、値は false です。 この変更では、フェールオーバーのワークフローに影響します。 プライマリ レプリカ障害が発生した場合、使用可能なセカンダリ レプリカのいずれかへのフェールオーバー クラスターが必要です。 代わりに、ユーザーでは、クラスターが失敗したプライマリ レプリカを開始しようとする保持がわかります。 そのプライマリことはありませんがオンライン (永続的な停止) のために場合、クラスター フェールオーバーしない別の利用可能なセカンダリ レプリカにします。 この変更により、開始-障害が-致命的で設定する前に推奨される構成が無効になってと設定の既定値に戻す必要があります`true`します。 AG リソースがさらに含める更新する必要があります、`failover-timeout`プロパティ。 
>
>プロパティの値を`true`に更新するには、次のコマンドを実行します。
>
>```bash
>sudo pcs property set start-failure-is-fatal=true
>```
>
>既存の AG リソース プロパティを更新`failure-timeout`に`60s`実行 (置換`ag1`可用性グループ リソースの名前に置き換えます)。
>
>```bash
>pcs resource update ag1 meta failure-timeout=60s
>```

## <a name="install-sql-server-resource-agent-for-integration-with-pacemaker"></a>Pacemaker との統合のための SQL Server リソース エージェントをインストールします。

すべてのノードで次のコマンドを実行します。 

```bash
sudo apt-get install mssql-server-ha
```

## <a name="create-a-sql-server-login-for-pacemaker"></a>Pacemaker 用 SQL Server ログインを作成します。

[!INCLUDE [SLES-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="create-availability-group-resource"></a>可用性グループ リソースを作成します。

可用性グループ リソースを作成するには、`pcs resource create`コマンドを使用し、リソース プロパティを設定します。 次のコマンドを作成、`ocf:mssql:ag`型のリソースの名前を持つ可用性グループのマスター/スレーブ`ag1`します。 

```bash
sudo pcs resource create ag_cluster ocf:mssql:ag ag_name=ag1 meta failure-timeout=30s --master meta notify=true

```

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

## <a name="create-virtual-ip-resource"></a>仮想 IP リソースを作成します。

仮想 IP アドレス リソースを作成するには、1 つのノードで次のコマンドを実行します。 ネットワークから使用可能な静的 IP アドレスを使用します。 スクリプトを実行する前に、までの値を置き換える`< ... >`有効な IP アドレスを使用します。

```bash
sudo pcs resource create virtualip ocf:heartbeat:IPaddr2 ip=<10.128.16.240>
```

Pacemaker と同じ仮想サーバー名がありません。 文字列のサーバー名を指す接続文字列を使用し、IP アドレスを使用しない、目的の仮想サーバーの名前とリソースの IP アドレスを DNS に登録します。 DR 構成では、プライマリと DR サイトの両方で DNS サーバーで、目的の仮想サーバー名と IP アドレスを登録します。

## <a name="add-colocation-constraint"></a>コロケーションの制約を追加します。

リソースを実行する必要がありますを選択するように、Pacemaker クラスターのほぼすべての意思決定は、スコアを比較することによって行われます。 リソースごとのスコアの計算し、クラスター リソース マネージャーが特定のリソースに対してスコアが最も高いノードを選択します。 (ノードにリソースの負のスコアがある場合は、リソースで実行できませんノード。)意思決定、クラスターを構成するのにには、制約を使用します。 制約では、スコアがあります。 制約は無限大より低いスコアにされている場合は、推奨事項のみ。 無限大のスコアは、必須でを意味します。 プライマリ レプリカと、仮想 ip リソースが同じホスト上にあることを確認、スコアの無限大のコロケーションの制約を定義します。 コロケーション制約を追加するには、1 つのノードで次のコマンドを実行します。 

```bash
sudo pcs constraint colocation add virtualip ag_cluster-master INFINITY with-rsc-role=Master
```

## <a name="add-ordering-constraint"></a>順序付けの制約を追加します。

コロケーションの制約には、暗黙的な順序付け制約があります。 可用性グループ リソースを移動する前に、仮想 IP リソースを移動します。 既定では一連のイベントは次のとおりです。

1. ユーザーの問題に関する`pcs resource move`可用性グループにプライマリ node1 から node2 にします。
1. 仮想 IP リソースは、node1 で停止します。
1. 仮想 IP リソースは、node2 で開始します。

   >[!NOTE]
   >この時点では、IP アドレスの一時的に node2 にポイント node2 がフェールオーバーの前ではまだセカンダリ。 
   
1. Node1 でプライマリ可用性グループは、セカンダリに降格されます。
1. Node2 でセカンダリ可用性グループがプライマリに昇格します。 

IP アドレスが一時的にフェイル オーバー前のセカンダリのノードを指すことを防ぐために、順序付けの制約を追加します。 

順序付けの制約を追加するには、1 つのノードで次のコマンドを実行します。

```bash
sudo pcs constraint order promote ag_cluster-master then start virtualip
```

>[!IMPORTANT]
>クラスターを構成するクラスター リソースとして、可用性グループを追加したら、TRANSACT-SQL を使用して可用性グループのリソースをフェールオーバーすることはできません。 Linux 上の SQL Server クラスター リソースは関連付けられていませんに厳しく、オペレーティング システムは Windows Server フェールオーバー クラスター (WSFC) にします。 SQL Server サービスでは、クラスターの存在を認識しません。 すべてのオーケストレーションは、クラスターの管理ツールを使用して行われます。 RHEL または Ubuntu を使用して`pcs`します。 

<!---[!INCLUDE [Pacemaker Concepts](..\includes\ss-linux-cluster-pacemaker-concepts.md)]--->

## <a name="next-steps"></a>次のステップ

[HA の可用性グループを操作します。](sql-server-linux-availability-group-failover-ha.md)

