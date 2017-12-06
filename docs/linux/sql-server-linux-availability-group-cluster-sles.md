---
title: "SQL Server 可用性グループに SLES クラスターの構成 |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 05/17/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 85180155-6726-4f42-ba57-200bf1e15f4d
ms.workload: Inactive
ms.openlocfilehash: 7bb98b8da1af1b97b9c06b58e5b8264a653547d3
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="configure-sles-cluster-for-sql-server-availability-group"></a>SQL Server 可用性グループに SLES クラスターを構成します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このガイドでは、SQL Server SUSE Linux Enterprise Server (SLES) 12 SP2 での 3 つのノードのクラスターを作成する手順を提供します。 Linux 上の可用性グループ、可用性を高めるためには 3 つのノードが必要です - 参照[可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)です。 クラスタ リングのレイヤーが SUSE に基づいて[高可用性の拡張機能 (HAE)](https://www.suse.com/products/highavailability)の上に構築[ペース](http://clusterlabs.org/)です。 

クラスターの構成、リソース エージェント オプション、管理、ベスト プラクティス、および推奨事項の詳細については、次を参照してください。 [SUSE Linux Enterprise 高可用性拡張子 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html)です。

>[!NOTE]
>この時点では、Linux 上のペースで SQL Server の統合は Windows での WSFC でとして結合します。 Linux 上の SQL Server サービスはクラスター対応ではありません。 ペースでは、すべての可用性グループ リソースを含め、クラスター リソースのオーケストレーションを制御します。 Linux は、常に 可用性グループ動的管理ビュー (Dmv) sys.dm_hadr_cluster のようにクラスター情報を提供する保証はありません。 また、仮想ネットワーク名は、WSFC を特定、相当するのと同じペースではありません。 フェールオーバー後は、透過的な再接続に使用するリスナーを作成できますが、仮想 IP リソース (下記参照) を作成するために使用する ip アドレス、DNS サーバーで、リスナー名を手動で登録する必要があります。


## <a name="roadmap"></a>ロードマップ

高可用性の Linux サーバーに可用性グループを作成する手順は、Windows Server フェールオーバー クラスター上の手順と異なります。 次に、高レベルの手順を説明します。 

1. [クラスター ノードの SQL Server を構成する](sql-server-linux-setup.md)です。

2. [可用性グループの作成](sql-server-linux-availability-group-failover-ha.md)です。 

3. ペースのように、クラスター リソース マネージャーを構成します。 これらの手順は、このドキュメントではします。
   
   クラスター リソース マネージャーを構成する方法は、特定の Linux ディストリビューションに依存します。 

   >[!IMPORTANT]
   >実稼働環境では、高可用性を実現 STONITH などのフェンス操作エージェントが必要です。 このドキュメントではデモンストレーションでは、フェンス操作エージェントは使用しないでください。 デモは、テストおよび検証のみです。 
   
   >ペース クラスターでは、フェンス操作を使用して、既知の状態をクラスターを返します。 フェンス操作を構成する方法は、分布と、環境によって異なります。 この時点でのフェンス操作は一部のクラウド環境で使用できません。 参照してください[SUSE Linux Enterprise の高可用性拡張子](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing)です。

5. [可用性グループ、クラスター内のリソースとして追加](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server)です。 

## <a name="prerequisites"></a>前提条件

次のエンド ツー エンド シナリオを完了するには、3 つのマシンを 3 つのノードのクラスターを展開する必要があります。 次の手順では、これらのサーバーを構成する方法を説明します。

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>セットアップし、各クラスター ノードで、オペレーティング システムを構成します。 

最初の手順では、クラスター ノードで、オペレーティング システムを構成します。 このチュートリアルで、有効なサブスクリプションでの HA アドオン SLES 12 SP2 を使用します。

### <a name="install-and-configure-sql-server-service-on-each-cluster-node"></a>インストールし、各クラスター ノードに SQL Server サービスを構成します。

1. インストールし、すべてのノード上の SQL Server サービスをセットアップします。 詳細な手順についてを参照してください。 [Linux 上の SQL Server のインストール](sql-server-linux-setup.md)です。

1. プライマリ ノードとその他のノードのセカンダリとしてとして 1 つのノードを指定します。 このガイドではこれらの用語を使用します。

1. クラスターの一部として設定されているノードが相互に通信できることを確認してください。

   次の例は`/etc/hosts`SLES1、SLES2 SLES3 という 3 つのノードの項目を追加します。

   ```
   127.0.0.1   localhost
   10.128.16.33 SLES1
   10.128.16.77 SLES2
   10.128.16.22 SLES3
   ```

   すべてのクラスター ノードでは、SSH を使用して相互にアクセスできる必要があります。 ツールと同様に`hb_report`または`crm_report`(トラブルシューティング) 用、およびホークの履歴 には、ノード間の passwordless の SSH アクセスが必要なため、現在のノードからデータをのみ収集、それ以外の場合。 非標準の SSH ポートを使用する場合に、-x オプションを使用して (を参照してください`man` ページ)。 たとえば、SSH ポートが 3479 の場合は、起動、`crm_report`で。

   ```bash
   sudo crm_report -X "-p 3479" [...]
   ```

   詳細については、次を参照してください。、 [SLES 管理ガイド - その他 セクション](http://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.misc)です。


## <a name="create-a-sql-server-login-for-pacemaker"></a>ペースの SQL Server ログインを作成します。

[!INCLUDE [SLES-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="configure-an-always-on-availability-group"></a>Always On 可用性グループを構成します。

Linux では、サーバーは、可用性グループの構成し、クラスター リソースを構成します。 可用性グループを構成するのを参照してください[構成 Always On 可用性グループの SQL Server on Linux。](sql-server-linux-availability-group-configure-ha.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>インストールし、ペースを各クラスター ノードの構成

1. 高可用性の拡張機能をインストールします。

   リファレンスについては、次を参照してください[SUSE Linux Enterprise Server のインストールと高可用性の拡張機能。](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.installation)

1. 両方のノードでは、SQL Server リソース エージェント パッケージをインストールします。

   ```bash
   sudo zypper install mssql-server-ha
   ```

## <a name="set-up-the-first-node"></a>最初のノードを設定します。

   参照してください[SLES インストール手順](http://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node)

1. としてログイン`root`物理マシンまたはバーチャル マシンのクラスター ノードとして使用する場合にします。
2. 実行することによってブートス トラップのスクリプトを起動します。
   ```bash
   sudo ha-cluster-init
   ```

   ブート時に開始する NTP が構成されていない場合、メッセージが表示されます。 

   続行する場合は、スクリプトは自動的に SSH アクセスおよび Csync2 同期ツールのキーを生成し、両方に必要なサービスを開始します。 

3. クラスター通信層 (Corosync) を構成します。 

   a. バインドするネットワーク アドレスを入力します。 既定では、スクリプトは eth0 のネットワーク アドレスを提案します。 代わりに、別のネットワーク アドレス、たとえば bond0 のアドレスを入力します。 

   b. マルチキャスト アドレスを入力します。 スクリプトは、既定値として使用できるランダムなアドレスを提案します。 

   c. マルチキャストのポートを入力します。 スクリプトは、既定値として 5405 を提案します。 

   d. 構成する`SBD ()`SBD を使用するブロック デバイスのパーティションに永続的なパスを入力します。 パスは、クラスター内のすべてのノード間で一貫性のあるである必要があります。 
   最後に、スクリプトは、1 ノード クラスターをオンラインを Hawk2 の Web 管理インターフェイスを有効にするペース サービスを開始します。 Hawk2 に使用する URL は、画面に表示されます。 

4. セットアップ プロセスの詳細を確認`/var/log/sleha-bootstrap.log`です。 実行中の 1 ノード クラスターがあるようになりました。 Crm の状態とクラスターの状態を確認します。

   ```bash
   sudo crm status
   ```

   クラスター構成を確認することも`crm configure show xml`または`crm configure show`です。

5. ブートス トラップ手順では、パスワード、linux で hacluster をという名前の Linux ユーザーを作成します。 できるだけ早くセキュリティで保護された 1 つを既定のパスワードに置き換えます。 

   ```bash
   sudo passwd hacluster
   ```

## <a name="add-nodes-to-the-existing-cluster"></a>既存のクラスターにノードを追加します。

1 つまたは複数のノードで実行されているクラスターがある場合は、高可用性クラスター-結合ブートス トラップ スクリプトを使用してより多くのクラスター ノードを追加します。 スクリプトはだけが必要既存のクラスター ノードへのアクセスし、自動的に現在のコンピューター上の基本的なセットアップを完了します。 下記の手順に従ってください。

既存のクラスター ノードを構成している場合、`YaST`クラスター モジュールを実行する前に、次の前提条件が満たされたかどうかを確認`ha-cluster-join`:
- 既存のノードの root ユーザーでは、passwordless ログイン用の SSH キーがあります。 
- `Csync2`既存のノードで構成されます。 詳細については、YaST で Csync2 の構成を参照してください。 

1. 物理マシンまたはバーチャル マシンがクラスターに参加する先のルートとしてログインします。 
2. 実行することによってブートス トラップのスクリプトを起動します。 

   ```bash
   sudo ha-cluster-join
   ```

   ブート時に開始する NTP が構成されていない場合、メッセージが表示されます。 

3. 続行する場合は、既存のノードの IP アドレスを求められます。 IP アドレスを入力します。 

4. 両方のコンピューター間の passwordless SSH アクセスをまだ構成していない場合も求められます既存のノードのルート パスワードにします。 

   指定したノードにログインした後、スクリプトは Corosync 構成のコピー、SSH の構成と`Csync2`と、現在オンラインとコンピューターに新しいクラスター ノードが表示されます。 ホークに必要なサービスとは別に、開始されます。 共有記憶域を構成してある場合`OCFS2`、それも自動的にディレクトリが作成されます、マウント ポイントの`OCFS2`ファイル システム。 

5. すべてのマシンをクラスターに追加するには、上記の手順を繰り返します。 

6. プロセスの詳細については、確認`/var/log/ha-cluster-bootstrap.log`です。 

1. クラスターの状態を確認して`sudo crm status`です。 2 番目のノードが正常に追加されると、次のような出力が表示されます。

   ```bash
   sudo crm status
   
   3 nodes configured
   1 resource configured
   Online: [ SLES1 SLES2 SLES3]
   Full list of resources:   
   admin_addr     (ocf::heartbeat:IPaddr2):       Started node1
   ```

   >[!NOTE]
   >`admin_addr`1 ノード クラスターの初期セットアップ中に構成されている仮想 IP クラスター リソースです。

すべてのノードを追加するとかどうか、は、ポリシーを調整なし-クォーラム - グローバル クラスターのオプションにする必要があります。 を確認します。 これは、2 ノード クラスターにとって特に重要です。 詳細については、4.1.2 オプションなし-クォーラムのポリシーを参照してください。 

## <a name="set-cluster-property-start-failure-is-fatal-to-false"></a>開始-障害が-致命的でクラスターのプロパティが false に設定します。

`Start-failure-is-fatal`ノードにリソースを起動しますの失敗によってそのノードに対して試行された開始でがさらにかどうかを示します。 設定すると`false`クラスターが、リソースの現在の失敗数と移行のしきい値に基づいて、もう一度同じノードで起動するかどうかを決定します。 そのため、フェールオーバーが発生した後にペース再試行、可用性グループ リソースで開始以前のプライマリ SQL インスタンスが使用可能にします。 ペースが対処するセカンダリ レプリカを降格して、可用性グループを自動的に再参加がします。 また場合、`start-failure-is-fatal`に設定されている`false`クラスターは移行しきい値で構成されている移行しきい値が適宜更新の既定値のことを確認する必要があるので、構成された failcount 制限にフォールバックします。

False 実行するようにプロパティの値を更新します。
```bash
sudo crm configure property start-failure-is-fatal=false
sudo crm configure rsc_defaults migration-threshold=5000
```
プロパティ値を持つ場合、既定の`true`リソースが失敗した、ユーザーの介入を開始する最初の試行後、リソースの失敗した回数をクリーンアップするには、自動フェールオーバーが必要なとを使用して構成をリセットする場合は、:`sudo crm resource cleanup <resourceName>`コマンド。

ペース クラスターのプロパティの詳細についてを参照してください[クラスター リソースの構成](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_config_crm_resources.html)です。

# <a name="configure-fencing-stonith"></a>フェンス操作 (STONITH) を構成します。
ペース クラスターのベンダーは、STONITH を有効にして、サポートされているクラスターのセットアップ用に構成されたフェンス操作デバイスが必要です。 ノードまたはノード上のリソースの状態を判断できないのは、クラスター リソース マネージャー、既知の状態をクラスターに戻すにフェンス操作が使用されます。
主ににより、リソース レベルのフェンス操作はリソースを構成することにより、障害が発生した場合、データの破損がないことです。 リソース レベルのフェンス操作を使用するインスタンスのように古くなった場合に、ノード上のディスクをマークする DRBD (レプリケート ブロック デバイスの分散) との通信リンクがダウンしました。
ノード レベルのフェンス操作により、ノードがすべてのリソースを実行できません。 ノードをリセットすることによってこれし、ペース実装は STONITH (これは、「head で、他のノードを撮影」の略) と呼ばれます。 例: 無停電電源装置または管理インターフェイスのサーバーのカードをペースがさまざまなデバイスのフェンス操作をサポートします。
詳細については、次を参照してください。[を最初からペース クラスター](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html)、[フェンス操作と Stonith](http://clusterlabs.org/doc/crm_fencing.html)と[SUSE HA ドキュメント: フェンス操作と STONITH](https://www.suse.com/documentation/sle_ha/book_sleha/data/cha_ha_fencing.html)です。

クラスターの初期化時に、構成が検出されない場合 STONITH は無効です。 次のコマンドを実行して後で有効にすることができます。

```bash
sudo crm configure property stonith-enabled=true
```
  
>[!IMPORTANT]
>テストのためだけには STONITH を無効にします。 実稼働環境でペースを使用する場合は、環境に応じて STONITH 実装を計画して有効にしておいてください。 SUSE によって、クラウド環境でも (Azure を含む) や HYPER-V フェンス操作エージェントが提供されていないことに注意してください。 ので、クラスターのベンダーでは、これらの環境で運用クラスターを実行するためのサポートは提供しません。 この時間差が将来のリリースで利用できるためのソリューションに取り組んでいます。


## <a name="configure-the-cluster-resources-for-sql-server"></a>SQL Server のクラスター リソースを構成します。

参照してください[SLES 管理 Guid](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.manual_config)

### <a name="create-availability-group-resource"></a>可用性グループ リソースを作成します。

次のコマンドは、作成し、可用性グループ [ag1] の 3 つのレプリカの可用性グループ リソースを構成します。 モニターの操作とタイムアウト指定する必要は明示的に SLES で、という事実に基づいてタイムアウトが非常に依存しているワークロードや展開ごとに慎重に調整する必要があります。
クラスター内のノードの 1 つで、コマンドを実行します。

1. 実行`crm configure`crm プロンプトを開きます。

   ```bash
   sudo crm configure 
   ```

1. Crm プロンプトで、リソースのプロパティを構成するには、次のコマンドを実行します。

   ```bash
primitive ag_cluster \
   ocf:mssql:ag \
   params ag_name="ag1" \
   op start timeout=60s \
   op stop timeout=60s \
   op promote timeout=60s \
   op demote timeout=10s \
   op monitor timeout=60s interval=10s \
   op monitor timeout=60s interval=11s role="Master" \
   op monitor timeout=60s interval=12s role="Slave" \
   op notify timeout=60s
ms ms-ag_cluster ag_cluster \
   meta master-max="1" master-node-max="1" clone-max="3" \
  clone-node-max="1" notify="true" \
commit
   ```

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

### <a name="create-virtual-ip-resource"></a>仮想 IP リソースを作成します。

実行したときに、仮想 IP リソースを作成しなかったかどうか`ha-cluster-init`今すぐこのリソースを作成することができます。 次のコマンドでは、仮想 IP リソースを作成します。 置換`<**0.0.0.0**>`をネットワークから使用可能なアドレスを持つと`<**24**>`CIDR サブネット マスクのビット数でします。 1 つのノードで実行します。

```bash
crm configure \
primitive admin_addr \
   ocf:heartbeat:IPaddr2 \
   params ip=<**0.0.0.0**> \
      cidr_netmask=<**24**>
```

### <a name="add-colocation-constraint"></a>コロケーションの制約を追加します。
ペース クラスターでは、リソースを実行する場所を選択するようのほとんどすべての意思決定は、スコアを比較することによって行われます。 スコアの計算リソース、およびクラスター リソース マネージャーは、特定のリソースのスコアが最も高いノードを選択します。 (ノードにリソースの負のスコアがある場合は、リソースで実行できませんノード。)制約で、クラスターの意思決定を操作できることです。 制約では、スコアがあります。 制約に無限大より小さいスコアがある場合は、推奨設定のみを勧めします。 無限大のスコアは、必要であるを意味します。 可用性グループと仮想のプライマリ ip リソースが実行されること、同じホスト上の無限大のスコアのコロケーション制約を定義しますのでことを確認します。 

コロケーションの制約をマスターと同じノードで実行する仮想 IP を設定するには、1 つのノードで次のコマンドを実行します。

```bash
crm configure
colocation vip_on_master inf: \
    admin_addr ms-ag_cluster:Master
commit
```

### <a name="add-ordering-constraint"></a>順序付けの制約を追加します。
コロケーションの制約には、暗黙的な順序付け制約があります。 可用性グループ リソースを移動する前に、仮想 IP リソースを移動します。 既定で、一連のイベントは次のとおりです。 

1. ユーザーの問題のリソースは、可用性グループのマスターに node1 から node2 に移行します。
2. 仮想 IP リソースは、ノード 1 を停止します。
3. 仮想 IP リソースは、ノード 2 で開始します。 この時点では、IP アドレスの一時的に 2 のノードへのポインターより前のフェールオーバーがノード 2 セカンダリ。 
4. ノード 1 で、可用性グループのマスターは、スレーブに降格されます。
5. 昇格するには、可用性グループのスレーブ ノード 2 でマスターにします。 

IP アドレスが一時的にフェイル オーバー前のセカンダリを持つノードを指すようにするのには、順序付けの制約を追加します。 順序付けの制約を追加するには、1 つのノードで次のコマンドを実行します。 

```bash
crm crm configure \
   order ag_first inf: ms-ag_cluster:promote admin_addr:start
```


>[!IMPORTANT]
>クラスターを構成し、可用性グループをクラスター リソースとして追加した後は TRANSACT-SQL を使用して、可用性グループのリソースをフェールオーバーすることはできません。 Linux 上の SQL Server クラスター リソースと関連していない緊密にオペレーティング システムで、Windows Server フェールオーバー クラスター (WSFC) とします。 SQL Server サービスでは、クラスターの存在を認識しません。 すべてのオーケストレーションは、クラスター管理ツールを使って行われます。 SLES で使用して`crm`です。 

可用性グループを手動でフェールオーバー`crm`です。 Transact SQL を使用したフェールオーバーを開始してはいけません。 手順については、次を参照してください。[フェールオーバー](sql-server-linux-availability-group-failover-ha.md#failover)です。


追加の詳細を参照してください。
- [クラスター リソースを管理する](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.config.crm)です。   
- [HA の概念](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.concepts)
- [ペースのクイック リファレンス](https://github.com/ClusterLabs/pacemaker/blob/master/doc/pcs-crmsh-quick-ref.md) 

<!---[!INCLUDE [Pacemaker Concepts](..\includes\ss-linux-cluster-pacemaker-concepts.md)]--->

## <a name="next-steps"></a>次の手順

[HA 可用性グループを操作します。](sql-server-linux-availability-group-failover-ha.md)
