---
title: SQL Server 可用性グループの SLES クラスターを構成します。
titleSuffix: SQL Server
description: SQL Server SUSE Linux Enterprise Server (SLES) 上の可用性グループのクラスターを作成する方法について説明します
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 04/30/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux, seodec18
ms.technology: linux
ms.assetid: 85180155-6726-4f42-ba57-200bf1e15f4d
ms.openlocfilehash: 72ca07a14495261d61601c4acd503790697ce6a4
ms.sourcegitcommit: 706f3a89fdb98e84569973f35a3032f324a92771
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "58658096"
---
# <a name="configure-sles-cluster-for-sql-server-availability-group"></a>SQL Server 可用性グループの SLES クラスターを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このガイドでは、SQL Server SUSE Linux Enterprise Server (SLES) 12 SP2 での 3 ノード クラスターを作成する手順を提供します。 可用性を高めるためにはLinux 上の可用性グループでは 3 つのノードが必要です - [可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)を参照してください。 クラスタ リングの階層は SUSE に基づいて[高可用性の拡張機能 (HAE)](https://www.suse.com/products/highavailability)上に構築された[Pacemaker](https://clusterlabs.org/)します。 

クラスターの構成、リソース エージェントのオプション、管理、ベスト プラクティス、および推奨事項の詳細については、次を参照してください。 [SUSE Linux Enterprise 高可用性拡張子 12 SP2](https://www.suse.com/documentation/sle-ha-12/index.html)します。

>[!NOTE]
>この時点では、Linux 上の Pacemaker との SQL Server の統合は、Windows の WSFC でとして結合ではありません。 Linux 上の SQL Server サービスがクラスターに対応してないです。 Pacemaker は、可用性グループ リソースを含む、クラスター リソースのオーケストレーションのすべてを制御します。 Linux では、常に 可用性グループ動的管理ビュー (Dmv) sys.dm_hadr_cluster などのクラスター情報を提供するに依存する必要がありますしないしています。 また、仮想ネットワーク名は、WSFC を特定、Pacemaker で同じの相当するものはありません。 フェールオーバー後は、透過的に再接続するために使用するリスナーを作成できますが、(次のセクションで説明) と仮想 IP リソースを作成するために使用する ip アドレス、DNS サーバーで、リスナー名を手動で登録する必要があります。


## <a name="roadmap"></a>ロードマップ

高可用性の可用性グループを作成する手順は、Linux サーバーと Windows Server フェールオーバー クラスターで異なります。 手順の概要を以下に説明します。  

1. [SQL Server のクラスター ノードで構成](sql-server-linux-setup.md)します。

2. [可用性グループの作成](sql-server-linux-availability-group-failover-ha.md)です。 

3. Pacemaker のように、クラスター リソース マネージャーを構成します。  これらの手順は、このドキュメントに記載されています。
   
   クラスター リソース マネージャーを構成する方法は、特定の Linux ディストリビューションによって異なります。 

   >[!IMPORTANT]
   >運用環境では、高可用性の STONITH などのフェンス エージェントが必要です。 この記事の例では、フェンス エージェントを使用しません。 テストと検証にのみこれらです。 
   
   >Pacemaker クラスターでは、フェンスを使用して、既知の状態、クラスターを返します。 フェンスを構成する方法は、ディストリビューションと、環境によって異なります。 この時点で、フェンス操作の対象は一部のクラウド環境で使用できません。 参照してください[SUSE Linux Enterprise High Availability Extension](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing)します。

5. [可用性グループ、クラスター内のリソースとして追加](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server)します。 

## <a name="prerequisites"></a>前提条件

次のエンド ツー エンド シナリオを完了するには、3 つのノード クラスターをデプロイする 3 つのマシンが必要です。 次の手順では、これらのサーバーを構成する方法を説明します。

## <a name="setup-and-configure-the-operating-system-on-each-cluster-node"></a>各クラスター ノードで、オペレーティング システムのセットアップと構成をする 

最初の手順では、クラスター ノードで、オペレーティング システムを構成します。 このチュートリアルで、有効なサブスクリプションを使用した HA アドオンの SLES 12 SP2 を使用します。

### <a name="install-and-configure-sql-server-service-on-each-cluster-node"></a>インストールし、各クラスター ノード上の SQL Server サービスの構成

1. すべてのノードで SQL Server のサービスのインストールとセットアップ 詳細については、次を参照してください。 [Linux 上の SQL Server のインストール](sql-server-linux-setup.md)します。

1. セカンダリとプライマリおよびその他のノードとして 1 つのノードを指定します。 このガイドではこれらの用語を使用します。

1. クラスターの一部となるノードが相互に通信できることを確認します。

   次の例は`/etc/hosts`SLES1、SLES2、SLES3 という 3 つのノードの項目を追加します。

   ```
   127.0.0.1   localhost
   10.128.16.33 SLES1
   10.128.16.77 SLES2
   10.128.16.22 SLES3
   ```

   すべてのクラスター ノードでは、SSH を使用して相互にアクセスできる必要があります。 などのツール`hb_report`または`crm_report`(トラブルシューティング) を現在のノードからデータをのみ収集、それ以外の場合、Hawk の History Explorer は、ノード間でパスワードなしの SSH アクセスを必要とします。 非標準の SSH ポートを使用する場合は、-x オプションを使用して (を参照してください`man`ページ)。 たとえば、SSH ポートが 3479 の場合は、起動、`crm_report`で。

   ```bash
   sudo crm_report -X "-p 3479" [...]
   ```

   詳細については、次を参照してください。、 [SLES 管理ガイド - その他のセクション](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.misc)します。


## <a name="create-a-sql-server-login-for-pacemaker"></a>Pacemaker 用 SQL Server ログインを作成します。

[!INCLUDE [SLES-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="configure-an-always-on-availability-group"></a>Always On 可用性グループを構成します。

Linux サーバーで、可用性グループを構成し、クラスター リソースを構成します。 可用性グループを構成するには、次を参照してください[構成 Always On 可用性グループの SQL Server on Linux。](sql-server-linux-availability-group-configure-ha.md)

## <a name="install-and-configure-pacemaker-on-each-cluster-node"></a>各クラスター ノードでPacemakerインストールして構成する

1. 高可用性の拡張機能をインストールします。

   リファレンスについては、次を参照してください[SUSE Linux Enterprise Server のインストールと高可用性の拡張機能。](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.installation)

1. 両方のノードでは、SQL Server リソース エージェント パッケージをインストールします。

   ```bash
   sudo zypper install mssql-server-ha
   ```

## <a name="set-up-the-first-node"></a>最初のノードを設定します。

   参照してください[SLES インストール手順](https://www.suse.com/documentation/sle-ha-12/singlehtml/install-quick/install-quick.html#sec.ha.inst.quick.setup.1st-node)

1. としてログイン`root`に物理マシンまたは仮想マシンのクラスター ノードとして使用します。
2. ブートス トラップ スクリプトを実行することによって開始します。
   ```bash
   sudo ha-cluster-init
   ```

   起動時に開始する NTP が構成されていない場合は、メッセージが表示されます。 

   このまま続行する場合は、スクリプトは自動的に SSH アクセスおよび Csync2 同期ツールのキーを生成し、両方に必要なサービスを開始します。 

3. クラスター通信層 (Corosync) を構成するには。 

   A. バインドするネットワーク アドレスを入力します。 既定では、スクリプトは、eth0 のネットワーク アドレスを提案します。 または、別のネットワーク アドレス、たとえば bond0 のアドレスを入力します。 

   B. マルチキャスト アドレスを入力します。 スクリプトでは、既定値として使用できるランダムなアドレスを提案します。 

   c. マルチキャストのポートを入力します。 スクリプトは、既定値として 5405 を提案します。 

   d. 構成する`SBD ()`SBD を使用する、ブロック デバイスのパーティションに永続的なパスを入力します。 パスは、クラスター内のすべてのノード間で一貫性のあるである必要があります。 
   最後に、スクリプトを 1 ノード クラスターをオンラインと Hawk2 Web 管理インターフェイスを有効にする Pacemaker サービスが開始されます。 Hawk2 に使用する URL は、画面に表示されます。 

4. セットアップ プロセスの詳細を確認`/var/log/sleha-bootstrap.log`します。 実行中の 1 ノード クラスターがあるようになりました。 Crm 状態でクラスターの状態を確認します。

   ```bash
   sudo crm status
   ```

   クラスター構成を表示することも`crm configure show xml`または`crm configure show`します。

5. ブートス トラップの手順では、パスワードの linux hacluster をという名前の Linux ユーザーを作成します。 できるだけ早くセキュリティで保護された 1 つを既定のパスワードに置き換えます。 

   ```bash
   sudo passwd hacluster
   ```

## <a name="add-nodes-to-the-existing-cluster"></a>既存のクラスターにノードを追加します。

1 つまたは複数のノードで実行されているクラスターがある場合は、ha クラスター-結合ブートス トラップ スクリプトを使用して複数のクラスター ノードを追加します。 だけが必要、スクリプトは、既存のクラスター ノードへのアクセスし、自動的に現在のコンピューターで基本的なセットアップを完了します。 次の手順に従います。

既存のクラスター ノードで構成した場合、`YaST`クラスター モジュールを実行する前に、次の前提条件が満たされたかどうかを確認`ha-cluster-join`:
- 既存のノードの root ユーザーでは、パスワードなしのログイン用の SSH キーがあります。 
- `Csync2` 既存のノードで構成されます。 詳細については、YaST で Csync2 の構成を参照してください。 

1. 物理マシンまたはクラスターに参加する仮想マシンに、root としてログインします。 
2. ブートス トラップ スクリプトを実行することによって開始します。 

   ```bash
   sudo ha-cluster-join
   ```

   起動時に開始する NTP が構成されていない場合は、メッセージが表示されます。 

3. このまま続行する場合は、既存のノードの IP アドレスの促されます。 IP アドレスを入力します。 

4. 両方のマシン間でパスワードなしの SSH アクセスをまだ構成していない場合も求め、既存のノードのルート パスワード。 

   指定したノードにログインした後、スクリプト Corosync 構成をコピー、SSH を構成および`Csync2`、により、現在マシンをオンラインに新しいクラスター ノードとして。 別に、Hawk に必要なサービスを開始します。 共有記憶域を構成している場合`OCFS2`、マウント ポイント ディレクトリも自動的に作成、`OCFS2`ファイル システム。 

5. クラスターに追加するすべてのマシンに対して、前の手順を繰り返します。 

6. プロセスの詳細については、確認`/var/log/ha-cluster-bootstrap.log`します。 

1. クラスターの状態を確認してください。`sudo crm status`します。 2 番目のノードが正常に追加されると、次のような出力が表示されます。

   ```bash
   sudo crm status
   
   3 nodes configured
   1 resource configured
   Online: [ SLES1 SLES2 SLES3]
   Full list of resources:   
   admin_addr     (ocf::heartbeat:IPaddr2):       Started node1
   ```

   >[!NOTE]
   >`admin_addr` 1 ノード クラスターの初期セットアップ中に構成されている仮想 IP クラスター リソースです。

すべてのノードを追加するとかどうか、は、ポリシーを調整なし-クォーラムのグローバル クラスター オプションにする必要があります。 確認してください。 これは、2 ノード クラスターの場合は特に重要です。 詳細については、4.1.2 オプション ポリシー クォーラムなしを参照してください。 

## <a name="set-cluster-property-cluster-recheck-interval"></a>クラスター プロパティ クラスター-再確認-間隔を設定します。

`cluster-recheck-interval` リソース パラメーター、制約、またはその他のクラスターのオプションの変更のポーリング間隔、クラスターの確認を示します。 クラスターがしてバインドされている間隔で、レプリカを再起動しようとした場合は、レプリカがダウンしても、`failure-timeout`値と`cluster-recheck-interval`値。 たとえば場合、 `failure-timeout` 60 秒に設定されていると`cluster-recheck-interval`設定されている 120 秒間隔は 60 秒より大きく 120 秒未満で、再起動が試行します。 60 をクラスター再確認-間隔を 60 秒よりも大きい値には、エラー タイムアウトを設定することをお勧めします。 クラスター-再確認-間隔を小さい値に設定することは推奨されません。

プロパティの値を`2 minutes`に更新するには、次のコマンドを実行します。

```bash
crm configure property cluster-recheck-interval=2min
```

> [!IMPORTANT] 
> Pacemaker クラスターによって管理されている可用性グループ リソースは、既にある場合は、最新使用可能な Pacemaker パッケージ 1.1.18-11.el7 を使用するすべてのディストリビューションが開始-障害が-致命的でクラスターの場合に、設定の動作の変更を導入ことに注意してください、値は false です。 この変更では、フェールオーバーのワークフローに影響します。 プライマリ レプリカ障害が発生した場合、使用可能なセカンダリ レプリカのいずれかへのフェールオーバー クラスターが必要です。 代わりに、ユーザーでは、クラスターが失敗したプライマリ レプリカを開始しようとする保持がわかります。 そのプライマリことはありませんがオンライン (永続的な停止) のために場合、クラスター フェールオーバーしない別の利用可能なセカンダリ レプリカにします。 この変更により、開始-障害が-致命的で設定する前に推奨される構成が無効になってと設定の既定値に戻す必要があります`true`します。 AG リソースがさらに含める更新する必要があります、`failover-timeout`プロパティ。 
>
>プロパティの値を`true`に更新するには、次のコマンドを実行します。
>
>```bash
>crm configure property start-failure-is-fatal=true
>```
>
>既存の AG リソース プロパティを更新`failure-timeout`に`60s`実行 (置換`ag1`可用性グループ リソースの名前に置き換えます)。 
>
>```bash
>crm configure edit ag1
># In the text editor, add `meta failure-timeout=60s` after any `param`s and before any `op`s
>```

Pacemaker クラスターのプロパティの詳細については、次を参照してください。[クラスター リソースの構成](https://www.suse.com/documentation/sle_ha/book_sleha/data/sec_ha_config_crm_resources.html)します。

## <a name="configure-fencing-stonith"></a>フェンス (STONITH) を構成します。
Pacemaker クラスターのベンダーは、STONITH を有効にして、サポートされているクラスターのセットアップ用に構成されたフェンス操作デバイスを必要としています。 ノードまたはノード上のリソースの状態を判断できないのは、クラスター リソース マネージャー、既知の状態、クラスターを再度表示するフェンス操作が使用されます。

リソース レベルのフェンス操作はにより主に、リソースを構成することによって、障害発生時にデータの破損がないこと。 リソース レベルのフェンスを使用することができます、ように期限切れの場合、ノード上のディスクをマークする DRBD (レプリケートされたブロック デバイスの分散) との通信リンクがダウンしました。

ノード レベルのフェンス操作により、ノードがどのリソースも実行しないことが保証されます。 ノードをリセットすることでこれし、その Pacemaker 実装には、STONITH (これは「その他のノードを先頭に撮影」略) が呼び出されます。 Pacemaker は、さまざまな、無停電電源装置または管理インターフェイス カードのサーバーなどのデバイスをフェンスをサポートします。

詳細については、次を参照してください。 [Pacemaker クラスターを最初から](https://clusterlabs.org/pacemaker/doc/en-US/Pacemaker/1.1/html/Clusters_from_Scratch/)、[フェンスと Stonith](https://clusterlabs.org/doc/crm_fencing.html)と[SUSE HA のドキュメント。フェンスと STONITH](https://www.suse.com/documentation/sle_ha/book_sleha/data/cha_ha_fencing.html)します。

クラスターの初期化時に構成が検出されない場合は、STONITH が無効です。 次のコマンドを実行中で後で有効にできます。

```bash
sudo crm configure property stonith-enabled=true
```
  
>[!IMPORTANT]
>STONITH を無効にするのはテスト目的のみです。 実稼働環境で Pacemaker を使用する場合は、環境に応じて STONITH 実装を計画して有効にしておいてください。 SUSE では、(Azure を含む) のクラウド環境や HYPER-V フェンス エージェントは提供されません。 このため、クラスターのベンダーでは、これらの環境で運用のためにクラスターを実行するサポートは提供していません。 将来のリリースで利用できるように取り組んでいます。


## <a name="configure-the-cluster-resources-for-sql-server"></a>SQL Server のクラスター リソースを設定します。

参照してください[SLES 管理 Guid](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.manual_config)

## <a name="enable-pacemaker"></a>Pacemaker を有効にします。

自動的に開始するように、Pacemaker を有効にします。

クラスター内のすべてのノードで、次のコマンドを実行します。

```bash
systemctl enable pacemaker
```

### <a name="create-availability-group-resource"></a>可用性グループ リソースを作成します。

次のコマンドは、作成し、可用性グループ [ag1] の 3 つのレプリカの可用性グループ リソースを構成します。 操作を監視し、タイムアウト、という事実に基づいてタイムアウトが高いワークロードに依存して、展開ごとに慎重に調整する必要があります SLES で明示的に指定する必要があります。
クラスター内のノードのいずれかのコマンドを実行します。

1. 実行`crm configure`crm プロンプトを開きます。

   ```bash
   sudo crm configure 
   ```

1. Crm プロンプトで、リソースのプロパティを構成するのには、次のコマンドを実行します。

   ```bash
   primitive ag_cluster \
      ocf:mssql:ag \
      params ag_name="ag1" \
      meta failure-timeout=60s \
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

実行したときに、仮想 IP リソースを作成しなかったかどうか`ha-cluster-init`今すぐこのリソースを作成できます。 次のコマンドは、仮想 IP リソースを作成します。 置換`<**0.0.0.0**>`ネットワークから使用可能なアドレスでと`<**24**>`CIDR サブネット マスクのビット数。 1 つのノードで実行します。

```bash
crm configure \
primitive admin_addr \
   ocf:heartbeat:IPaddr2 \
   params ip=<**0.0.0.0**> \
      cidr_netmask=<**24**>
```

### <a name="add-colocation-constraint"></a>コロケーションの制約を追加します。
リソースを実行する必要がありますを選択するように、Pacemaker クラスターのほぼすべての意思決定は、スコアを比較することによって行われます。 リソースごとのスコアの計算し、クラスター リソース マネージャーが特定のリソースに対してスコアが最も高いノードを選択します。 (ノードにリソースの負のスコアがある場合は、リソースで実行できませんノード。)制約で、クラスターの意思決定を操作できることです。 制約では、スコアがあります。 制約は無限大より低いスコアにされている場合は、推奨事項のみ。 無限大のスコアは、これを意味します。 プライマリの可用性グループと仮想 ip リソースが実行される、同じホスト上の無限大のスコアを使用して、コロケーション制約を定義しますのでことを確認します。 

マスターと同じノード上で実行する仮想 IP のコロケーションの制約を設定するには、1 つのノードで次のコマンドを実行します。

```bash
crm configure
colocation vip_on_master inf: \
    admin_addr ms-ag_cluster:Master
commit
```

### <a name="add-ordering-constraint"></a>順序付けの制約を追加します。
コロケーションの制約には、暗黙的な順序付け制約があります。 可用性グループ リソースを移動する前に、仮想 IP リソースを移動します。 既定では一連のイベントは次のとおりです。  

1. ユーザーの問題のリソースは、node1 から node2 に可用性グループのマスターに移行します。
2. 仮想 IP リソースは、ノード 1 で停止します。
3. 仮想 IP リソースは、ノード 2 で開始します。 >この時点では、ノード 2がまだフェールオーバー前のセカンダリのままであるのにも関わらず、IP アドレスは一時的にノード 2 を指しています。 
4. 可用性グループのマスター ノード 1 には、スレーブに降格されます。
5. 可用性グループのスレーブ ノード 2 での昇格をマスターします。 

IP アドレスが一時的にフェイル オーバー前のセカンダリのノードを指すことを防ぐために、順序付けの制約を追加します。 順序付けの制約を追加するには、1 つのノードで次のコマンドを実行します。 

```bash
crm crm configure \
   order ag_first inf: ms-ag_cluster:promote admin_addr:start
```


>[!IMPORTANT]
>クラスターを構成するクラスター リソースとして、可用性グループを追加したら、TRANSACT-SQL を使用して可用性グループのリソースをフェールオーバーすることはできません。 Linux 上の SQL Server クラスター リソースは関連付けられていませんに厳しく、オペレーティング システムは Windows Server フェールオーバー クラスター (WSFC) にします。 SQL Server サービスでは、クラスターの存在を認識しません。 すべてのオーケストレーションは、クラスターの管理ツールを使用して行われます。 SLES で使用して`crm`します。 

`crm`を使って、可用性グループを手動でフェールオーバーしてください。 Transact SQL を使用したフェールオーバーの開始はありません。 詳細については、次を参照してください。[フェールオーバー](sql-server-linux-availability-group-failover-ha.md#failover)します。


詳細については、以下をご覧ください。
- [クラスター リソースの管理](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.config.crm)します。   
- [HA の概念](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.concepts)
- [Pacemaker のクイック リファレンス](https://github.com/ClusterLabs/pacemaker/blob/master/doc/pcs-crmsh-quick-ref.md) 

<!---[!INCLUDE [Pacemaker Concepts](..\includes\ss-linux-cluster-pacemaker-concepts.md)]--->

## <a name="next-steps"></a>次のステップ

[HA の可用性グループを操作します。](sql-server-linux-availability-group-failover-ha.md)
