---
title: "SQL Server 可用性グループに RHEL クラスターの構成 |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
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
ms.openlocfilehash: 860d3571aa1edf7c467125de1cc2920a968eb704
ms.sourcegitcommit: acab4bcab1385d645fafe2925130f102e114f122
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2018
---
# <a name="configure-rhel-cluster-for-sql-server-availability-group"></a>SQL Server 可用性グループに RHEL クラスターを構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

このドキュメントでは、Red Hat Enterprise Linux 上の SQL Server の 3 つのノードの可用性グループのクラスターを作成する方法について説明します。 Linux 上の可用性グループ、可用性を高めるためには 3 つのノードが必要です - 参照[可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)です。 クラスタ リングの層は Red Hat Enterprise Linux (RHEL) に基づいて[HA アドオン](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/pdf/High_Availability_Add-On_Overview/Red_Hat_Enterprise_Linux-6-High_Availability_Add-On_Overview-en-US.pdf)の上に構築[ペース](http://clusterlabs.org/)です。 

> [!NOTE] 
> Red Hat の完全なドキュメントへのアクセスには、有効なサブスクリプションが必要です。 

クラスターの構成、リソース エージェント オプション、および管理の詳細については、次を参照してください。 [RHEL リファレンス ドキュメント](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/index.html)です。

> [!NOTE] 
> SQL Server がいない緊密に統合された Linux 上のペースで Windows Server フェールオーバー クラスタ リングではします。 SQL Server インスタンスでは、クラスターの認識しません。 ペースでは、クラスター リソースのオーケストレーションを提供します。 また、仮想ネットワーク名が Windows Server フェールオーバー クラスタ リングに固有 - ペースで該当するショートカットはありません。 クラスター情報を照会する可用性グループ動的管理ビュー (Dmv) は、クラスターのペースで空の行を返します。 フェールオーバー後に透過的に再接続するためのリスナーを作成するには、仮想 IP リソースを作成するために使用する ip アドレスの DNS で、リスナー名を手動で登録します。 

次のセクションでは、ペース クラスターを設定し、クラスター内の高可用性のリソースとして可用性グループを追加する手順について説明します。

## <a name="roadmap"></a>ロードマップ

高可用性の Linux サーバーに可用性グループを作成する手順は、Windows Server フェールオーバー クラスター上の手順と異なります。 次に、手順の概要を説明します。 

1. [クラスター ノードの SQL Server を構成する](sql-server-linux-setup.md)です。

2. [可用性グループの作成](sql-server-linux-availability-group-configure-ha.md)です。 

3. ペースのように、クラスター リソース マネージャーを構成します。 これらの手順は、このドキュメントではします。
   
   クラスター リソース マネージャーを構成する方法は、特定の Linux ディストリビューションに依存します。 

   >[!IMPORTANT]
   >実稼働環境では、高可用性を実現 STONITH などのフェンス操作エージェントが必要です。 このドキュメントではデモンストレーションでは、フェンス操作エージェントは使用しないでください。 デモは、テストおよび検証のみです。 
   
   >Linux クラスターでは、フェンス操作を使用して、既知の状態をクラスターを返します。 フェンス操作を構成する方法は、分布と、環境によって異なります。 現時点では、フェンス操作では、一部のクラウド環境で使用できません。 詳細については、次を参照してください。 [RHEL 高可用性クラスターの仮想化プラットフォームのサポート ポリシー](https://access.redhat.com/articles/29440)です。

5. [可用性グループ、クラスター内のリソースとして追加](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)です。  

## <a name="configure-high-availability-for-rhel"></a>RHEL の高可用性を構成します。

RHEL の高可用性を構成するには、高可用性のサブスクリプションを有効にしてペースを構成します。

### <a name="enable-the-high-availability-subscription-for-rhel"></a>RHEL のサブスクリプションを高可用性を有効にします。

クラスター内の各ノードは、RHEL と高可用性の追加の適切なサブスクリプションが必要です。 要件を確認して[Red Hat Enterprise Linux での高可用性クラスター パッケージをインストールする方法](http://access.redhat.com/solutions/45930)です。 サブスクリプションとリポジトリを構成する手順に従います。

1. システムを登録します。

   ```bash
   sudo subscription-manager register
   ```

   ユーザー名とパスワードを提供します。   

1. 登録の使用可能なプールの一覧を表示します。

   ```bash
   sudo subscription-manager list --available
   ```

   、使用可能なプールの一覧から、プール サブスクリプションの ID を高可用性に注意してください。

1. 次のスクリプトを更新します。 置き換える`<pool id>`プールの id、前の手順から高可用性を実現します。 サブスクリプションをアタッチするスクリプトを実行します。

   ```bash
   sudo subscription-manager attach --pool=<pool id>
   ```

1. リポジトリを有効にします。

   ```bash
   sudo subscription-manager repos --enable=rhel-ha-for-rhel-7-server-rpms
   ```

詳細については、次を参照してください。[ペース –、オープン ソースでは、高可用性クラスター](http://www.opensourcerers.org/pacemaker-the-open-source-high-availability-cluster/)です。 

サブスクリプションを構成した後は、ペースを構成する次の手順を実行します。

### <a name="configure-pacemaker"></a>ペースを構成します。

サブスクリプションを登録した後は、ペースを構成する次の手順を実行します。
   
[!INCLUDE [RHEL-Configure-Pacemaker](../includes/ss-linux-cluster-pacemaker-configure-rhel.md)]

ペースを設定すると後の使用`pcs`クラスターとの対話にします。 クラスターから 1 つのノードですべてのコマンドを実行します。 

## <a name="configure-fencing-stonith"></a>フェンス操作 (STONITH) を構成します。

ペース クラスターのベンダーは、STONITH を有効にして、サポートされているクラスターのセットアップ用に構成されたフェンス操作デバイスが必要です。 「他のノードは、head で撮影します」の略 STONITH ノードまたはノード上のリソースの状態を判断できないのは、クラスター リソース マネージャー、フェンス操作は再度、クラスターを既知の状態を表示します。

リソース レベルのフェンス操作により、リソースを構成することにより、障害が発生した場合、データの破損がないこと。 リソース レベルのフェンス操作を使用して、ディスクをマークするなどのように古くなった場合に、ノード上の通信リンクがダウンします。 

ノード レベルのフェンス操作により、ノードがすべてのリソースを実行できません。 これは、ノードをリセットすることによって行います。 ペースでは、さまざまなデバイスのフェンスをサポートします。 例には、無停電電源装置、または管理インターフェイスのカード サーバーにはが含まれます。

STONITH、およびフェンス操作については、次の記事を参照してください。

* [最初からペース クラスター](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-plugin/html/Clusters_from_Scratch/ch05.html)
* [フェンス操作と STONITH](http://clusterlabs.org/doc/crm_fencing.html)
* [Red Hat の高可用性のアドオンをペース: フェンス](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/ch-fencing-HAAR.html)

フェンス構成ノードのレベルは、環境内に大きく依存、ために、(、構成後で) このチュートリアルでは無効にします。 次のスクリプトには、ノード レベルのフェンス操作が無効にします。

```bash
sudo pcs property set stonith-enabled=false
```
  
>[!IMPORTANT]
>テストのためだけには STONITH を無効にします。 実稼働環境でペースを使用する場合は、環境に応じて STONITH 実装を計画して有効にしておいてください。 RHEL では、クラウド環境でも (Azure を含む) や HYPER-V フェンス操作エージェントが提供されません。 ので、クラスターのベンダーでは、これらの環境で運用クラスターを実行するためのサポートは提供しません。 この時間差が将来のリリースで利用できるためのソリューションに取り組んでいます。

## <a name="set-cluster-property-start-failure-is-fatal-to-false"></a>開始-障害が-致命的でクラスターのプロパティが false に設定します。

`start-failure-is-fatal`ノードにリソースを起動しますの失敗によってそのノードに対して試行された開始でがさらにかどうかを示します。 設定すると`false`クラスターは、リソースの現在の失敗数と移行のしきい値に基づいて、もう一度同じノードで起動するかどうかを決定します。 フェールオーバーが発生した後は、SQL インスタンスが使用可能に以前のプライマリ上のリソースがグループ ペースの再試行回数が、可用性を開始します。 ペースがセカンダリ レプリカを降格し、可用性グループを自動的に再度参加します。 

プロパティの値を更新する`false`を実行します。

```bash
sudo pcs property set start-failure-is-fatal=false
```

>[!WARNING]
>自動フェールオーバーの後と`start-failure-is-fatal = true`リソース マネージャーは、リソースを開始を試みます。 最初の試行で失敗した場合を手動で実行`pcs resource cleanup <resourceName>`リソース障害の数をクリーンアップし、構成をリセットします。

ペース クラスターのプロパティについては、次を参照してください。[ペース クラスター プロパティ](http://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/High_Availability_Add-On_Reference/ch-clusteropts-HAAR.html)です。

## <a name="create-a-sql-server-login-for-pacemaker"></a>ペースの SQL Server ログインを作成します。

[!INCLUDE [SQL-Create-SQL-Login](../includes/ss-linux-cluster-pacemaker-create-login.md)]

## <a name="create-availability-group-resource"></a>可用性グループ リソースを作成します。

可用性グループ リソースを作成するには使用`pcs resource create`コマンドおよびリソース プロパティを設定します。 次のコマンドは、作成、`ocf:mssql:ag`型のリソースの名前を持つ可用性グループのマスター/スレーブ`ag1`です。

```bash
sudo pcs resource create ag_cluster ocf:mssql:ag ag_name=ag1 master notify=true
```

[!INCLUDE [required-synchronized-secondaries-default](../includes/ss-linux-cluster-required-synchronized-secondaries-default.md)]

<a name="createIP"></a>

## <a name="create-virtual-ip-resource"></a>仮想 IP リソースを作成します。

仮想 IP アドレス リソースを作成するには、1 つのノードで次のコマンドを実行します。 ネットワークから使用可能な静的 IP アドレスを使用します。 間で IP アドレスの代わりに`<10.128.16.240>`有効な IP アドレスを使用します。

```bash
sudo pcs resource create virtualip ocf:heartbeat:IPaddr2 ip=<10.128.16.240>
```

同じペースで仮想サーバー名がありません。 IP アドレスの代わりに文字列のサーバー名を指す接続文字列を使用するには、目的の仮想サーバーの名前とリソースの仮想 IP アドレスを DNS に登録します。 災害復旧構成のプライマリおよび災害復旧サイトの両方で DNS サーバーで、目的の仮想サーバー名と IP アドレスを登録します。

## <a name="add-colocation-constraint"></a>コロケーションの制約を追加します。

ペース クラスターでは、リソースを実行する場所を選択するようのほとんどすべての意思決定は、スコアを比較することによって行われます。 スコアは、リソースごとに計算されます。 クラスター リソース マネージャーでは、特定のリソースのスコアが最も高いノードが選択されます。 ノードにリソースの負のスコアがある場合は、リソースは、そのノードで実行できません。

ペース クラスター上の制約で、クラスターの意思決定を操作できます。 制約では、スコアがあります。 制約は、スコアよりも低い場合`INFINITY`ペースの既定では、推奨されます。 スコアの`INFINITY`は必須です。

プライマリ レプリカと仮想 ip リソースが、同じホストで実行させるには、スコアの無限大のコロケーション制約を定義します。 コロケーション制約を追加するには、1 つのノードで次のコマンドを実行します。

```bash
sudo pcs constraint colocation add virtualip ag_cluster-master INFINITY with-rsc-role=Master
```

## <a name="add-ordering-constraint"></a>順序付けの制約を追加します。

コロケーションの制約には、暗黙的な順序付け制約があります。 可用性グループ リソースを移動する前に、仮想 IP リソースを移動します。 既定で、一連のイベントは次のとおりです。

1. ユーザーの問題`pcs resource move`可用性グループにプライマリ node1 から node2 にします。
1. 仮想 IP リソースは、ノード 1 を停止します。
1. 仮想 IP リソースは、ノード 2 で開始します。
  
   >[!NOTE]
   >この時点では、IP アドレスの一時的に 2 のノードへのポインターより前のフェールオーバーがノード 2 セカンダリ。 
   
1. 可用性グループのプライマリ ノード 1 では、セカンダリに降格されます。
1. 可用性グループ ノード 2 のセカンダリがプライマリに昇格します。 

IP アドレスが一時的にフェイル オーバー前のセカンダリを持つノードを指すようにするのには、順序付けの制約を追加します。 

順序付けの制約を追加するには、1 つのノードで次のコマンドを実行します。

```bash
sudo pcs constraint order promote ag_cluster-master then start virtualip
```

>[!IMPORTANT]
>クラスターを構成し、可用性グループをクラスター リソースとして追加した後は TRANSACT-SQL を使用して、可用性グループのリソースをフェールオーバーすることはできません。 Linux 上の SQL Server クラスター リソースと関連していない緊密にオペレーティング システムで、Windows Server フェールオーバー クラスター (WSFC) とします。 SQL Server サービスでは、クラスターの存在を認識しません。 すべてのオーケストレーションは、クラスター管理ツールを使って行われます。 RHEL または Ubuntu を使用して`pcs`と SLES 使用`crm`ツールです。 

可用性グループを手動でフェールオーバー`pcs`です。 Transact SQL を使用したフェールオーバーを開始してはいけません。 手順については、次を参照してください。[フェールオーバー](sql-server-linux-availability-group-failover-ha.md#failover)です。

## <a name="next-steps"></a>次の手順

[HA 可用性グループを操作します。](sql-server-linux-availability-group-failover-ha.md)
