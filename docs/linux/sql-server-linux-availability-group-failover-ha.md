---
title: 可用性グループのフェールオーバー - SQL Server on Linux の管理 |Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/01/2018
ms.topic: conceptual
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: 1fe1a785314b30e0f6027c845da5ac2b34692966
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47796720"
---
# <a name="always-on-availability-group-failover-on-linux"></a>Linux 上の always On 可用性グループのフェールオーバー

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

、可用性グループ (AG) のコンテキスト内でプライマリ ロールとセカンダリ ロールの可用性レプリカは通常、フェールオーバーと呼ばれるプロセスで交換されることです。 フェールオーバーには、自動フェールオーバー (データ損失なし)、計画的な手動フェールオーバー (データ損失なし)、および " *強制フェールオーバー*" と通常呼ばれる強制手動フェールオーバー (データ損失の可能性あり) の 3 つの形式があります。 自動フェールオーバーと計画的な手動フェールオーバーでは、すべてのデータを保持します。 AG は、可用性レプリカのレベルでフェールオーバーします。 つまり、AG はそのセカンダリ レプリカ (現在のフェールオーバー ターゲット) のいずれかにフェールオーバーします。 

フェールオーバーの背景については、次を参照してください。[フェールオーバーとフェールオーバー モード](../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)します。

## <a name="failover"></a>手動フェールオーバー

クラスターの管理ツールを使用して、外部のクラスター マネージャーによって管理されている AG をフェールオーバーする場合します。 たとえば、ソリューションでは、Linux クラスターを管理する Pacemaker を使用している場合を使用して`pcs`RHEL または Ubuntu での手動フェールオーバーを実行します。 SLES を使用して`crm`します。 

> [!IMPORTANT]
> 通常の操作では、失敗しない経由で SSMS または PowerShell のような TRANSACT-SQL または SQL Server の管理ツールを使用します。 ときに`CLUSTER_TYPE = EXTERNAL`にのみ使用できる値`FAILOVER_MODE`は`EXTERNAL`します。 これらの設定では、すべての手動または自動フェールオーバー アクションは、外部のクラスター マネージャーで実行されます。 データ損失のフェールオーバーを強制する手順については、次を参照してください。[を強制的にフェールオーバー](#forceFailover)します。

### <a name="a-namemanualfailovermanual-failover-steps"></a><a name="manualFailover">手動のフェールオーバー手順

フェールオーバーすると、プライマリ レプリカになるセカンダリ レプリカが同期される必要があります。 セカンダリ レプリカは非同期で場合[可用性モードを変更](../database-engine/availability-groups/windows/change-the-availability-mode-of-an-availability-replica-sql-server.md)します。

手動で 2 つの手順でフェールオーバーします。

   まず、[ AG リソースを移動して手動フェールオーバーを](#manualMove)新しいノードにリソースを所有するクラスター ノードから。

   クラスターでは、可用性グループ リソースをフェールオーバーし、場所の制約を追加します。 この制約は、新しいノードで実行するリソースを構成します。 将来的で正常にフェールオーバーするには、この制約を削除します。

   2 番目、[場所の制約を削除](#removeLocConstraint)します。

#### <a name="a-namemanualmovestep-1-manually-fail-over-by-moving-availability-group-resource"></a><a name="manualMove">手順 1 です。 可用性グループ リソースを移動して手動で失敗します。

という名前の可用性グループ リソースを手動でフェールオーバーする*ag_cluster*という名前のクラスター ノードに*nodeName2*、お使いのディストリビューションの適切なコマンドを実行します。

- **RHEL または Ubuntu の例**

   ```bash
   sudo pcs resource move ag_cluster-master nodeName2 --master
   ```

- **SLES の例**

   ```bash
   crm resource migrate ag_cluster nodeName2
   ```

>[!IMPORTANT]
>リソースを手動でフェールオーバーを後は、自動的に追加される場所の制約を削除する必要があります。

#### <a name="a-nameremovelocconstraint-step-2-remove-the-location-constraint"></a><a name="removeLocConstraint"> 手順 2 です。 場所の制約の削除

手動のフェールオーバー中に、`pcs`コマンド`move`または`crm`コマンド`migrate`新しいターゲット ノードに配置するリソースの場所の制約を追加します。 新しい制約を表示するには、リソースを手動で移動した後に次のコマンドを実行します。

- **RHEL または Ubuntu の例**

   ```bash
   sudo pcs constraint list --full
   ```

- **SLES の例**

   ```bash
   crm config show
   ```

手動フェールオーバーのために作成される制約の例です。 
 `Enabled on: Node1 (score:INFINITY) (role: Master) (id:cli-prefer-ag_cluster-master)`

- **RHEL または Ubuntu の例**

   次のコマンドで、`cli-prefer-ag_cluster-master` は削除が必要な制約の ID です。 `sudo pcs constraint list --full` によってこの ID が返されます。 
   
   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```
   
- **SLES の例**

   次のコマンドで`cli-prefer-ms-ag_cluster`制約の ID です。 `crm config show` によってこの ID が返されます。 
   
   ```bash
   crm configure
   delete cli-prefer-ms-ag_cluster 
   commit
   ```

>[!NOTE]
>自動フェールオーバーでは場所の制約が追加されないため、削除は不要です。 

詳細:
- [Red Hat - クラスター リソースの管理](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/ch-manageresource-HAAR.html)
- [Pacemaker - 手動でのリソースの移動](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-pcs/html/Clusters_from_Scratch/_move_resources_manually.html)
 [SLES 管理ガイド - リソース](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.resource) 
 
## <a name="forceFailover"></a> 強制フェールオーバー 

厳密に強制フェールオーバーはディザスター リカバリー、です。 この場合は、ことはできませんフェールオーバーを実行するクラスター管理ツールを使用して、プライマリ データ センターがダウンしているためです。 非同期のセカンダリ レプリカに対して強制フェールオーバーを実行した場合、データ損失の可能性があります。 サービスをすぐに、可用性グループに復元し、データの損失を許容する場合は、フェールオーバーを強制のみです。

場合は、クラスターが、プライマリ データ センターで障害が原因で応答していない場合など、クラスターと対話するため、クラスター管理ツールを使用することはできません、外部のクラスター マネージャーをバイパスするフェールオーバーを強制する必要があります。 この手順は、データ損失のリスクがありますので、通常の操作は推奨されません。 フェールオーバー アクションを実行するクラスターの管理ツールが失敗したときに使用します。 機能的には、この手順は、のような[強制手動フェールオーバーを実行する](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)Windows での AG にします。
 
強制フェールオーバーを実行するためにこのプロセスは、SQL Server on Linux に固有です。

1. 以上、可用性グループ リソースをクラスターによって管理されませんを確認します。 

      - ターゲット クラスターのノードで、リソースを非管理対象モードに設定します。 このコマンドは、停止リソースの監視および管理するリソース エージェントを通知します。 以下に例を示します。 
      
      ```bash
      sudo pcs resource unmanage <resourceName>
      ```

      - リソース モードを非管理対象モードに設定しようとすると、失敗した場合、リソースを削除します。 以下に例を示します。

      ```bash
      sudo pcs resource delete <resourceName>
      ```

      >[!NOTE]
      >リソースを削除する場合は、すべての関連付けられている制約のことをも削除されます。 

1. セカンダリ レプリカをホストする SQL Server のインスタンスで、セッションのコンテキスト変数を設定`external_cluster`します。

   ```Transact-SQL
   EXEC sp_set_session_context @key = N'external_cluster', @value = N'yes';
   ```

1. Transact SQL を使用した AG をフェールオーバーします。 次の例では、置き換える`<MyAg>`AG の名前に置き換えます。 対象のセカンダリ レプリカをホストする SQL Server のインスタンスに接続し、次のコマンドを実行します。

   ```Transact-SQL
   ALTER AVAILABILITY GROUP <MyAg> FORCE_FAILOVER_ALLOW_DATA_LOSS;
   ```

1.  強制フェールオーバー後、正常な状態にクラスター リソースの監視と管理を再起動するか、可用性グループ リソースを再作成する前に、AG をもたらします。 レビュー、[強制フェールオーバー後の必須タスク](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md#FollowUp)します。

1.  クラスター リソースの監視と管理を再起動するか。

   クラスター リソースの監視と管理を再起動するには、次のコマンドを実行します。

   ```bash
   sudo pcs resource manage <resourceName>
   sudo pcs resource cleanup <resourceName>
   ```

   クラスター リソースを削除した場合は、それを再作成します。 クラスター リソースを再作成する」の手順に従います[可用性グループ リソースを作成する](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)します。

>[!Important]
>データの損失になる可能性があるために、ディザスター リカバリーの訓練を前の手順を使用しないでください。 非同期レプリカを同期的でとための手順を変更する代わりに[通常の手動フェールオーバー](#manualFailover)します。

## <a name="database-level-monitoring-and-failover-trigger"></a>データベース レベルの監視とフェールオーバーのトリガー

`CLUSTER_TYPE=EXTERNAL`フェールオーバーのトリガーのセマンティクスが異なる WSFC と比較します。 WSFC 内の SQL Server のインスタンスに可用性グループがある場合は、移行`ONLINE`データベースにより、エラーを報告する可用性グループの正常性の状態します。 応答では、クラスター マネージャーは、フェールオーバー アクションをトリガーします。 Linux では、SQL Server インスタンスは、クラスターと通信できません。 監視データベースの正常性が行われます*外部*します。 データベース レベルのフェールオーバーの監視とフェールオーバーでユーザーをオプトインかどうか (オプションを設定して`DB_FAILOVER=ON`AG を作成するときに)、クラスターは、データベースの状態が確認`ONLINE`監視アクションを実行するたびにします。 クラスターの状態をクエリする`sys.databases`します。 いずれかの状態とは異なる`ONLINE`、自動的に (自動フェールオーバーの条件が満たされた場合) にフェールオーバーがトリガーされます。 フェイル オーバーの実際の時間は、sys.databases で更新されているデータベースの状態と同様に、監視操作の頻度に依存します。

自動フェールオーバーでは、少なくとも 1 つの同期レプリカが必要です。

## <a name="next-steps"></a>次の手順

[SQL Server 可用性グループのクラスター リソースの Red Hat Enterprise Linux クラスターを構成します。](sql-server-linux-availability-group-cluster-rhel.md)

[SQL Server 可用性グループのクラスター リソースの SUSE Linux Enterprise Server クラスターを構成します。](sql-server-linux-availability-group-cluster-sles.md)

[SQL Server 可用性グループのクラスター リソースの Ubuntu クラスターの構成します。](sql-server-linux-availability-group-cluster-ubuntu.md)
