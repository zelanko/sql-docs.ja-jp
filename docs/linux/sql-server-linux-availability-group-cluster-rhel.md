---
title: SQL Server 可用性グループの RHEL のクラスターの構成 |Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 06/14/2017
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: b7102919-878b-4c08-a8c3-8500b7b42397
ms.openlocfilehash: 784f98acb1e8223e14d3f1e1a74e73cfdc3561bc
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "38057210"
---
# <a name="configure-rhel-cluster-for-sql-server-availability-group"></a>SQL Server 可用性グループの RHEL のクラスターを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このドキュメントでは、Red Hat Enterprise Linux 上の SQL Server の 3 つのノードの可用性グループのクラスターを作成する方法について説明します。 可用性を高めるためにはLinux 上の可用性グループでは 3 つのノードが必要です - [可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)を参照してください。 クラスタ リングの層は、[Pacemaker](http://clusterlabs.org/)の上に構築された Red Hat Enterprise Linux (RHEL) [HA アドオン](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf)に基づいています。  

> [!NOTE] 
> Red Hat の完全なドキュメントにアクセスするには、有効なサブスクリプションが必要です。 

クラスターの構成、リソース エージェント オプション、および管理の詳細については、  [RHEL リファレンス ドキュメント](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html)を参照してください。

> [!NOTE] 
> SQL Server は Linux 上では Pacemaker と、Windows Server フェールオーバー クラスタ リングほどには緊密には統合されていません。 SQL Server インスタンスは、クラスターを認識していません。 Pacemaker は、クラスター リソースのオーケストレーションを提供します。 また、 Windows Server フェールオーバー クラスタ リングに固有の仮想ネットワーク名に該当するものはPacemakerにはありません。 クラスター情報を照会する可用性グループ動的管理ビュー (DMV) は、Pacemaker クラスターでは空の行を返します。 フェールオーバー後に透過的に再接続するためのリスナーを作成するには、 DNS で仮想 IP リソースを作成するために使用する ip アドレスを使い、リスナー名を手動で登録します。  

次のセクションでは、Pacemaker クラスターを設定して、可用性グループの高可用性クラスター内のリソースとして追加する手順について説明します。

## <a name="roadmap"></a>ロードマップ

高可用性の Linux サーバーに可用性グループを作成する手順は、Windows Server フェールオーバー クラスターの手順と異なります。 手順の概要を以下に説明します。  

1. [SQL Server のクラスター ノードで構成](sql-server-linux-setup.md)します。

2. [可用性グループの作成](sql-server-linux-availability-group-configure-ha.md)です。 

3. Pacemaker のように、クラスター リソース マネージャーを構成します。  これらの手順は、このドキュメントに記載されています。
   
   クラスター リソース マネージャーを構成する方法は、特定の Linux ディストリビューションによって異なります。 

   >[!IMPORTANT]
   >運用環境では、高可用性の STONITH などのフェンス エージェントが必要です。 このドキュメントでは、フェンス エージェントを使用しないでください。 デモはテストおよび検証のみです。 
   
   >Linux クラスターでは、フェンスを使用して、既知の状態、クラスターを返します。 フェンスを構成する方法は、ディストリビューションと、環境によって異なります。 現時点では、フェンス操作では、一部のクラウド環境で使用できません。 詳細については、次を参照してください。 [RHEL 高可用性クラスターの仮想化プラットフォームのサポート ポリシー](https://access.redhat.com/articles/29440)します。

5. [可用性グループ、クラスター内のリソースとして追加](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)します。  

## <a name="configure-high-availability-for-rhel"></a>RHEL の高可用性を構成します。

RHEL の高可用性を構成するには、高可用性のサブスクリプションを有効にし、Pacemaker を構成します。

### <a name="enable-the-high-availability-subscription-for-rhel"></a>RHEL の高可用性のサブスクリプションを有効にします。

クラスター内の各ノードは、RHEL と High Availability Add on の適切なサブスクリプションが必要です。 [Red Hat Enterprise Linux での高可用性クラスター パッケージをインストールする方法](http://access.redhat.com/solutions/45930)の要件を確認してください。  サブスクリプションとリポジトリを構成する手順に従います。

1. システムを登録します。

   ```bash
   sudo subscription-manager register
   ```

   ユーザー名とパスワードを入力します。   

1. 登録に使用可能なプールの一覧を表示します。

   ```bash
   sudo subscription-manager list --available
   ```

   使用可能なプールの一覧から、High Availability サブスクリプションのプール ID を記録します。

1. 次のスクリプトを書き換えます。 `<pool id>`を、前の手順で記録したHigh Availability のプール ID で置換します。 サブスクリプションをアタッチするスクリプトを実行します。

   ```bash
   sudo subscription-manager attach --pool=<pool id>
   ```

1. リポジトリを有効にします。

   ```bash
   sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
   ```

詳細については、[Pacemaker – オープン ソースな高可用性クラスター](http://www.opensourcerers.org/pacemaker-the-open-source-high-availability-cluster/)を参照してください。  

サブスクリプションを構成した後は、 Pacemaker を構成するため次の手順を実行します。

### <a name="configure-pacemaker"></a>Pacemaker を構成します。

サブスクリプションを登録した後は、 Pacemaker を構成するため次の手順を実行します。
   
[!INCLUDE [RHEL-Configure-Pacemaker](../includes/ss-linux-cluster-pacemaker-configure-rhel.md)]

Pacemaker を設定した後は、`pcs`を使用することでクラスターと対話できます。 すべてのコマンドはクラスターの 1 つのノードで実行します。 

## <a name="configure-fencing-stonith"></a>フェンス (STONITH) を構成します。

Pacemaker クラスターのベンダーは、STONITH を有効にして、サポートされているクラスターのセットアップ用に構成されたフェンス操作デバイスを必要としています。 STONITHは「shoot the other node in the head」の略です。 クラスター リソース マネージャーがノードまたはノード上のリソースの状態を判断できないときに、フェンス操作によりクラスターを既知の状態を戻します。

リソース レベルのフェンス操作により、リソースの構成で障害が発生した場合でも、データの破損がないことが保証されます。 たとえば、リソース レベルのフェンス操作を使用して、通信リンクがダウンしたときに、ノード上のディスクを古くなったとマークすることができます。 

ノード レベルのフェンス操作により、ノードがどのリソースも実行しないことが保証されます。 これは、ノードをリセットすることによって行います。  Pacemaker はさまざまなフェンス操作デバイスをサポートします。 たとえば、無停電電源装置やサーバーの管理インターフェイスのカードなどがあります。

STONITH、およびフェンス操作については、次の記事を参照してください。

* [Pacemaker クラスターを最初から作成](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html)
* [フェンスと STONITH](http://clusterlabs.org/doc/crm_fencing.html)
* [Pacemaker を使用した Red Hat High Availability Add-On の設定: フェンス機能](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/ch-fencing-HAAR.html)

ノード レベル でのフェンス操作は環境に大きく依存するため、このチュートリアルでは無効にします (後で構成することができます)。 次のスクリプトで、ノード レベルのフェンス操作を無効にします。

```bash
sudo pcs property set stonith-enabled=false
```
  
>[!IMPORTANT]
>STONITH を無効にするのはテスト目的のみです。 実稼働環境で Pacemaker を使用する場合は、環境に応じて STONITH 実装を計画して有効にしておいてください。 RHEL では、クラウド環境 (Azure を含む) や Hyper-V 向けにフェンス操作エージェントを提供していません。 このため、クラスターのベンダーでは、これらの環境で運用のためにクラスターを実行するサポートは提供していません。 将来のリリースで利用できるように取り組んでいます。

## <a name="set-cluster-property-cluster-recheck-interval"></a>クラスター プロパティ クラスター-再確認-間隔を設定します。

`cluster-recheck-interval` リソース パラメーター、制約、またはその他のクラスターのオプションの変更のポーリング間隔、クラスターの確認を示します。 クラスターがしてバインドされている間隔で、レプリカを再起動しようとした場合は、レプリカがダウンしても、`failure-timeout`値と`cluster-recheck-interval`値。 たとえば場合、 `failure-timeout` 60 秒に設定されていると`cluster-recheck-interval`設定されている 120 秒間隔は 60 秒より大きく 120 秒未満で、再起動が試行します。 60 をクラスター再確認-間隔を 60 秒よりも大きい値には、エラー タイムアウトを設定することをお勧めします。 クラスター-再確認-間隔を小さい値に設定することは推奨されません。

プロパティの値を`2 minutes`に更新するには、次のコマンドを実行します。

```bash
sudo pcs property set cluster-recheck-interval=2min
```

> [!IMPORTANT] 
> (RHEL 7.3、7.4 を含む)、最新使用可能な Pacemaker パッケージ 1.1.18-11.el7 を使用するすべてのディストリビューションは、その値が false の場合、開始-障害が-致命的でクラスターの設定の動作の変更を紹介します。 この変更では、フェールオーバーのワークフローに影響します。 プライマリ レプリカ障害が発生した場合、使用可能なセカンダリ レプリカのいずれかへのフェールオーバー クラスターが必要です。 代わりに、ユーザーでは、クラスターが失敗したプライマリ レプリカを開始しようとする保持がわかります。 そのプライマリことはありませんがオンライン (永続的な停止) のために場合、クラスター フェールオーバーしない別の利用可能なセカンダリ レプリカにします。 この変更により、開始-障害が-致命的で設定する前に推奨される構成が無効になってと設定の既定値に戻す必要があります`true`します。 AG リソースがさらに含める更新する必要があります、`failover-timeout`プロパティ。 

プロパティの値を`true`に更新するには、次のコマンドを実行します。

```bash
sudo pcs property set start-failure-is-fatal=true
```

更新する、`ag1`リソース プロパティ`failure-timeout`に`60s`を実行します。

```bash
pcs resource update ag1 meta failure-timeout=60s
```


Pacemaker クラスターのプロパティについては、次を参照してください。 [Pacemaker クラスター プロパティ](http://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-clusteropts-HAAR.html)します。

## <a name="create-a-sql-server-login-for-pacemaker"></a>Pacemaker 用 SQL Server ログインを作成します。

[!INCLUDE [SQL-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="create-availability-group-resource"></a>可用性グループ リソースを作成します。

可用性グループ リソースを作成するには、`pcs resource create`コマンドを使用し、リソース プロパティを設定します。 次のコマンドで、`ag1`という名前を持つ可用性グループにマスター/スレーブ型のリソース`ocf:mssql:ag`を作成します。

```bash
sudo pcs resource create ag_cluster ocf:mssql:ag ag_name=ag1 meta failure-timeout=30s master notify=true
``` 

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

<a name="createIP"></a>

## <a name="create-virtual-ip-resource"></a>仮想 IP リソースを作成します。

仮想 IP アドレス リソースを作成するには、1 つのノードで次のコマンドを実行します。 ネットワークから使用可能な静的 IP アドレスを使用します。 `<10.128.16.240>`を有効な IP アドレスで置換します。 

```bash
sudo pcs resource create virtualip ocf:heartbeat:IPaddr2 ip=<10.128.16.240>
```

Pacemaker と同じ仮想サーバー名がありません。 IP アドレスではなく文字列のサーバー名を指す接続文字列を使用するには、目的の仮想サーバーの名前とリソースの仮想 IP アドレスを DNS に登録します。 DR 構成では、プライマリと DR サイトの両方で DNS サーバーで、目的の仮想サーバー名と IP アドレスを登録します。

## <a name="add-colocation-constraint"></a>コロケーションの制約を追加します。

リソースを実行する必要がありますを選択するように、Pacemaker クラスターのほぼすべての意思決定は、スコアを比較することによって行われます。 スコアは、リソースごとに計算されます。 クラスター リソース マネージャーは、特定のリソースに対してスコアが最も高いノードを選択します。 ノードにリソースの負のスコアがある場合は、リソースは、そのノードで実行できません。

Pacemaker クラスター上の制約で、クラスターの意思決定を操作できます。 制約では、スコアがあります。 制約にスコアよりも低い場合`INFINITY`Pacemaker が推奨事項とみなします。 スコアの`INFINITY`は必須です。

プライマリ レプリカと仮想 ip リソースが同じホストで実行させるには、スコアの無限大のコロケーションの制約を定義します。 コロケーション制約を追加するには、1 つのノードで次のコマンドを実行します。

```bash
sudo pcs constraint colocation add virtualip ag_cluster-master INFINITY with-rsc-role=Master
```

## <a name="add-ordering-constraint"></a>順序付けの制約を追加します。

コロケーションの制約には、暗黙的な順序付け制約があります。 可用性グループ リソースを移動する前に、仮想 IP リソースを移動します。 既定では一連のイベントは次のとおりです。 

1. ユーザーの問題に関する`pcs resource move`可用性グループにプライマリ node1 から node2 にします。
1. 仮想 IP リソースは、ノード 1 で停止します。
1. 仮想 IP リソースは、ノード 2 で開始します。
  
   >[!NOTE]
   >>この時点では、ノード 2がまだフェールオーバー前のセカンダリのままであるのにも関わらず、IP アドレスは一時的にノード 2 を指しています。 
   
1. ノード 1 の可用性グループ プライマリは、セカンダリに降格されます。
1. ノード 2 の可用性グループ セカンダリは、プライマリに昇格されます。 

IP アドレスが一時的にフェイル オーバー前のセカンダリのノードを指すことを防ぐために、順序付けの制約を追加します。 

順序付けの制約を追加するには、1 つのノードで次のコマンドを実行します。

```bash
sudo pcs constraint order promote ag_cluster-master then start virtualip
```

>[!IMPORTANT]
>クラスターを構成するクラスター リソースとして、可用性グループを追加したら、TRANSACT-SQL を使用して可用性グループのリソースをフェールオーバーすることはできません。 Linux 上の SQL Server クラスター リソースは関連付けられていませんに厳しく、オペレーティング システムは Windows Server フェールオーバー クラスター (WSFC) にします。 SQL Server サービスでは、クラスターの存在を認識しません。 すべてのオーケストレーションは、クラスターの管理ツールを使用して行われます。 RHEL または Ubuntu を使用して`pcs`と SLES 使用`crm`ツール。 

`pcs`を使って、可用性グループを手動でフェールオーバーしてください。 Transact-SQL を使用したフェールオーバーを開始してはいけません。 手順については、[フェールオーバー](sql-server-linux-availability-group-failover-ha.md#failover)を参照してください。 

## <a name="next-steps"></a>次のステップ

[HA の可用性グループを操作します。](sql-server-linux-availability-group-failover-ha.md)
