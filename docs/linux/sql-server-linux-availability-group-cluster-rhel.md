---
title: "SQL Server 可用性グループに RHEL クラスターの構成 |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.date: 06/14/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: b7102919-878b-4c08-a8c3-8500b7b42397
ms.workload: Inactive
ms.openlocfilehash: 11eea4891b1214e48f70ca56462322305fa97c06
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="configure-rhel-cluster-for-sql-server-availability-group"></a>SQL Server 可用性グループ向けに RHEL クラスターを構成します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

このドキュメントでは、Red Hat Enterprise Linux 上の SQL Server の 3 つのノードの可用性グループのクラスターを作成する方法について説明します。 可用性を高めるためにはLinux 上の可用性グループでは 3 つのノードが必要です - [可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)を参照してください。 クラスタ リングの層は、[Pacemaker](http://clusterlabs.org/)の上に構築された Red Hat Enterprise Linux (RHEL) [HA アドオン](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf)に基づいています。 

> [!NOTE] 
> Red Hat の完全なドキュメントへのアクセスには、有効なサブスクリプションが必要です。 

クラスターの構成、リソース エージェント オプション、および管理の詳細については、 [RHEL リファレンス ドキュメント](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html)を参照してください。

> [!NOTE] 
> SQL Server は Linux 上では Pacemaker と、Windows Server フェールオーバー クラスタ リングほどには緊密には統合されていません。 SQL Server インスタンスは、クラスターを認識していません。 Pacemaker は、クラスター リソースのオーケストレーションを提供します。 また、 Windows Server フェールオーバー クラスタ リングに固有の仮想ネットワーク名に該当するものはPacemakerにはありません。 クラスター情報を照会する可用性グループ動的管理ビュー (DMV) は、Pacemaker クラスターでは空の行を返します。 フェールオーバー後に透過的に再接続するためのリスナーを作成するには、 DNS で仮想 IP リソースを作成するために使用する ip アドレスを使い、リスナー名を手動で登録します。 

次のセクションでは、ペース クラスターを設定し、クラスター内の高可用性のリソースとして可用性グループを追加する手順について説明します。

## <a name="roadmap"></a>ロードマップ

高可用性の Linux サーバーに可用性グループを作成する手順は、Windows Server フェールオーバー クラスターの手順と異なります。 手順の概要を以下に説明します。 

1. [クラスター ノードの SQL Server を構成する](sql-server-linux-setup.md)。

2. [可用性グループを作成する](sql-server-linux-availability-group-configure-ha.md)。 

3.  Pacemaker のように、クラスター リソース マネージャーを構成します。 これらの手順は、このドキュメントに記載されています。
   
   クラスター リソース マネージャーを構成する方法は、特定の Linux ディストリビューションに依存します。 

   >[!IMPORTANT]
   >実稼働環境では、高可用性を実現 STONITH などのフェンス操作エージェントが必要です。 このドキュメントでのデモンストレーションでは、フェンス操作エージェントは使用していません。 このデモはテストおよび検証目的のみです。 
   
   >Linux クラスターでは、フェンス操作を使用して、クラスターを既知の状態にします。 フェンス操作を構成する方法は、ディストリビューションと環境によって異なります。 現時点では、フェンス操作では、一部のクラウド環境で使用できません。 詳細については、[RHEL 高可用性クラスターの仮想化プラットフォームのサポート ポリシー](https://access.redhat.com/articles/29440)を参照してください。 

5. [可用性グループをクラスター内のリソースとして追加](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)。  

## <a name="configure-high-availability-for-rhel"></a>RHEL の高可用性を構成します。

RHEL の高可用性を構成するには、 High Availability サブスクリプションを有効にしてペースを構成します。

### <a name="enable-the-high-availability-subscription-for-rhel"></a>RHEL の High Availability サブスクリプションをを有効にします。

クラスター内の各ノードは、RHEL と High Availability Add on の適切なサブスクリプションが必要です。 [Red Hat Enterprise Linux での高可用性クラスター パッケージをインストールする方法](http://access.redhat.com/solutions/45930)の要件を確認してください。 サブスクリプションとリポジトリを構成する手順に従います。

1. システムを登録します。

   ```bash
   sudo subscription-manager register
   ```

   ユーザー名とパスワードを提供します。   

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

サブスクリプションを構成した後は、 Pacemaker を構成する次の手順を実行します。

### <a name="configure-pacemaker"></a> Pacemaker を構成します。

サブスクリプションを登録した後は、 Pacemaker を構成する次の手順を実行します。
   
[!INCLUDE [RHEL-Configure-Pacemaker](../includes/ss-linux-cluster-pacemaker-configure-rhel.md)]

 Pacemaker を設定した後は、`pcs`を使用することでクラスターと対話できます。 すべてのコマンドはクラスターの一つのノードで実行します。

## <a name="configure-fencing-stonith"></a>フェンス操作 (STONITH) を構成します。

 Pacemaker クラスターのベンダーは、STONITH を有効にして、サポートされているクラスターのセットアップ用に構成されたフェンス操作デバイスを必要としています。 STONITHは「shoot the other node in the head」の略です。 クラスター リソース マネージャーがノードまたはノード上のリソースの状態を判断できないときに、フェンス操作によりクラスターを既知の状態を戻します。

リソース レベルのフェンス操作により、構成されたリソースに障害が発生した場合でも、データの破損がないことを保証できます。 例えば、リソース レベルのフェンス操作を使用して、通信リンクがダウンしたときに、ノード上のディスクを古くなったとマークすることができます。

ノード レベルのフェンス操作により、ノードがすべてのリソースを実行できないことを保証できます。 これは、ノードをリセットすることによって行います。 Pacemaker はさまざまなフェンス操作デバイスをサポートします。 例えば、無停電電源装置、もしくはサーバーの管理インターフェイスのカード といったものです。

STONITH、およびフェンス操作については、次の記事を参照してください。

* [Pacemaker クラスター 入門](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html)
* [フェンス操作と STONITH](http://clusterlabs.org/doc/crm_fencing.html)
* [Pacemaker を使用した Red Hat High Availability Add-On の設定: フェンス機能](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/high_availability_add-on_reference/ch-fencing-haar)

ノード レベル でのフェンス操作は環境に大きく依存するため、このチュートリアルでは無効にします (後で構成することができます)。 次のスクリプトで、ノード レベルのフェンス操作を無効にします。

```bash
sudo pcs property set stonith-enabled=false
```
  
>[!IMPORTANT]
>STONITH を無効にするのはテスト目的のみです。 実稼働環境で Pacemaker を使用する場合は、環境に応じて STONITH 実装を計画して有効にしておいてください。 RHEL では、クラウド環境 (Azure を含む) や Hyper-V 向けにフェンス操作エージェントを提供していません。 このため、クラスターのベンダーでは、これらの環境で運用のためにクラスターを実行するサポートは提供していません。 将来のリリースで利用できるように取り組んでいます。

## <a name="set-cluster-property-start-failure-is-fatal-to-false"></a>クラスターのプロパティ start-failure-is-fatal を false に設定します。

`start-failure-is-fatal`は、ノードでリソースの起動が失敗したときにそのノードに対してさらに起動を試みることを許さないかどうかを示します。 `false`に設定すると、クラスターはリソースの現在の失敗数と移行のしきい値に基づいて、もう一度同じノードで起動するかどうかを決定します。 フェールオーバーが発生した後は、いったんSQL インスタンスが使用可能になったときに、 Pacemaker が以前のプライマリで可用性グループのリソースの起動を再度試行します。 Pacemaker はレプリカをセカンダリに降格し、可用性グループに自動的に再度参加させます。 

プロパティの値を`false`に更新するには、次のコマンドを実行します。

```bash
sudo pcs property set start-failure-is-fatal=false
```

>[!WARNING]
>自動フェールオーバーの後、`start-failure-is-fatal = true`の場合、リソース マネージャーはリソースの開始を試みます。 最初の試行で失敗した場合、`pcs resource cleanup <resourceName>`を手動で実行することで、リソースの失敗数をクリーンアップし、構成をリセットできます。

ペース クラスターのプロパティについては、[Pacemaker クラスター プロパティ](http://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-clusteropts-HAAR.html)を参照してください。

## <a name="create-a-sql-server-login-for-pacemaker"></a> Pacemaker の SQL Server ログインを作成します。

[!INCLUDE [SQL-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="create-availability-group-resource"></a>可用性グループ リソースを作成します。

可用性グループ リソースを作成するには、`pcs resource create`コマンドを使用し、リソース プロパティを設定します。 次のコマンドで、`ag1`という名前を持つ可用性グループにマスター/スレーブ型のリソース`ocf:mssql:ag`を作成します。

```bash
sudo pcs resource create ag_cluster ocf:mssql:ag ag_name=ag1 master notify=true
```

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

<a name="createIP"></a>

## <a name="create-virtual-ip-resource"></a>仮想 IP リソースを作成します。

仮想 IP アドレス リソースを作成するには、1 つのノードで次のコマンドを実行します。 ネットワークから使用可能な静的 IP アドレスを使用します。 `**<10.128.16.240>**`を有効な IP アドレスで置換します。

```bash
sudo pcs resource create virtualip ocf:heartbeat:IPaddr2 ip=**<10.128.16.240>**
```

仮想サーバー名に相当するものが Pacemaker にはありません。 IP アドレスの代わりに文字列のサーバー名を指す接続文字列を使用するには、目的の仮想サーバーの名前と仮想 IP リソースのアドレスを DNS に登録します。 災害復旧構成のプライマリおよび災害復旧サイトの両方で DNS サーバーに目的の仮想サーバー名と IP アドレスを登録します。

## <a name="add-colocation-constraint"></a>コロケーションの制約を追加します。

Pacemaker クラスターでは、リソースを実行する場所を選択するほとんどすべての意思決定は、スコアを比較することによって行われます。 スコアはリソースごとに計算されます。 クラスター リソース マネージャーでは、特定のリソースのスコアが最も高いノードが選択されます。 ありノードがあるリソースの負のスコアを持っている場合、そのリソースはそのノードで実行できません。

Pacemaker クラスターでは、制約でクラスターの意思決定を操作できます。 制約はスコアをもっています。 制約が`INFINITY`よりも低いスコアの場合、Pacemaker は推奨されていると認識します。 `INFINITY`というスコアは必須です。

プライマリ レプリカと仮想 ip リソースを同じホストで実行させることを保証させるためには、INFINITYというスコアでコロケーション制約を定義します。 コロケーション制約を追加するには、1 つのノードで次のコマンドを実行します。

```bash
sudo pcs constraint colocation add virtualip ag_cluster-master INFINITY with-rsc-role=Master
```

## <a name="add-ordering-constraint"></a>順序付けの制約を追加します。

コロケーションの制約には、暗黙的な順序付け制約があります。 可用性グループ リソースを移動する前に、仮想 IP リソースを移動します。 既定では一連のイベントは次のとおりです。

1. ユーザーが`pcs resource move`で可用性グループのプライマリ node1 から node2 に移動させます。
1. 仮想 IP リソースは、ノード 1 で停止します。
1. 仮想 IP リソースは、ノード 2 で開始します。
  
   >[!NOTE]
   >この時点では、ノード 2がまだフェールオーバー前のセカンダリのままであるのにも関わらず、IP アドレスは一時的にノード 2 を指しています。
   
1. ノード 1 の可用性グループ プライマリは、セカンダリに降格されます。
1. ノード 2 の可用性グループ セカンダリは、プライマリに昇格します。 

IP アドレスが一時的にフェイル オーバー前のセカンダリのノードを指すことを防ぐために、順序付けの制約を追加します。 

順序付けの制約を追加するには、1 つのノードで次のコマンドを実行します。

```bash
sudo pcs constraint order promote ag_cluster-master then start virtualip
```

>[!IMPORTANT]
>クラスターを構成し可用性グループをクラスター Transact-SQL を使用して可用性グループのリソースをフェールオーバーすることはできません。 Linux 上の SQL Server クラスター リソースは、Windows Server フェールオーバー クラスター (WSFC) のように、オペレーティング システムと緊密に関連していません。 SQL Server サービスはクラスターの存在を認識しません。 すべてのオーケストレーションは、クラスター管理ツールを使って行われます。 RHEL または Ubuntu では`pcs`を使用し、SLES では`crm`ツールを使用します。 

`pcs`を使って、可用性グループを手動でフェールオーバーしてください。 Transact-SQL を使用したフェールオーバーを開始してはいけません。 手順については、[フェールオーバー](sql-server-linux-availability-group-failover-ha.md#failover)を参照してください。

## <a name="next-steps"></a>次の手順

[HA 可用性グループを操作します。](sql-server-linux-availability-group-failover-ha.md)
