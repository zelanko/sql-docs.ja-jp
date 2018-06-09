---
title: 可用性グループのフェールオーバーの SQL Server on Linux の管理 |Microsoft ドキュメント
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/01/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: ddbe5f25cf3153b3354425fd426798e7061bdf36
ms.sourcegitcommit: 99e355b71ff2554782f6bc8e0da86e6d9e3e0bef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2018
ms.locfileid: "34799812"
---
# <a name="always-on-availability-group-failover-on-linux"></a>Linux 上の always On 可用性グループのフェールオーバー

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

可用性グループ (AG) のコンテキスト内でプライマリ ロールとセカンダリ ロールの可用性レプリカのフェールオーバーと呼ばれるプロセスで交換通常です。 フェールオーバーには、自動フェールオーバー (データ損失なし)、計画的な手動フェールオーバー (データ損失なし)、および " *強制フェールオーバー*" と通常呼ばれる強制手動フェールオーバー (データ損失の可能性あり) の 3 つの形式があります。 自動フェールオーバーと計画的な手動フェールオーバーでは、すべてのデータが保持されます。 AG は、可用性レプリカのレベルでフェールオーバーします。 つまり、AG はそのセカンダリ レプリカ (現在のフェールオーバー ターゲット) のいずれかにフェールオーバーします。 

フェールオーバーに関する背景情報については、次を参照してください。[フェールオーバーとフェールオーバー モード](../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)です。

## <a name="failover"></a>手動フェールオーバー

外部のクラスター マネージャーによって管理される、AG フェールオーバー クラスター管理ツールを使用します。 たとえば、ソリューションでは、Linux クラスターを管理するペースが使用されている場合を使用して`pcs`RHEL または Ubuntu に対して手動フェールオーバーを実行します。 Sles 使用`crm`です。 

> [!IMPORTANT]
> 通常の操作はフェールオーバーされません SSMS や PowerShell などの TRANSACT-SQL または SQL Server の管理ツール。 ときに`CLUSTER_TYPE = EXTERNAL`にのみ使用できる値`FAILOVER_MODE`は`EXTERNAL`します。 これらの設定では、すべてのアクションを手動または自動フェールオーバーは、外部のクラスター マネージャーで実行されます。 データ損失の可能性があるフェールオーバーを強制する手順については、次を参照してください。[を強制的にフェールオーバー](#forceFailover)です。

### <a name="a-namemanualfailovermanual-failover-steps"></a><a name="manualFailover">手動フェールオーバーの手順

フェールオーバーすると、プライマリ レプリカになるセカンダリ レプリカを同期する必要があります。 セカンダリ レプリカが非同期の場合は[可用性モードを変更](../database-engine/availability-groups/windows/change-the-availability-mode-of-an-availability-replica-sql-server.md)です。

2 つの手順を手動でフェールオーバーします。

   最初に、[ AG リソースを移動して手動でフェールオーバーする](#manualMove)新しいノードにリソースを所有しているクラスター ノードからです。

   クラスターでは、可用性グループ リソースがフェールオーバーし、場所の制約を追加します。 この制約は、新しいノードで実行するリソースを構成します。 今後で正常にフェールオーバーするためにこの制約を削除します。

   2 番目、[場所の制約を削除する](#removeLocConstraint)です。

#### <a name="a-namemanualmovestep-1-manually-fail-over-by-moving-availability-group-resource"></a><a name="manualMove">手順 1 です。 可用性グループ リソースを移動して手動でフェールオーバーします。

という名前の可用性グループ リソースを手動でフェールオーバーする*ag_cluster*という名前のクラスター ノードに*nodeName2*、配布用の適切なコマンドを実行します。

- **RHEL/Ubuntu 例**

   ```bash
   sudo pcs resource move ag_cluster-master nodeName2 --master
   ```

- **SLES 例**

   ```bash
   crm resource migrate ag_cluster nodeName2
   ```

>[!IMPORTANT]
>リソースを手動でフェールオーバーした後が自動的に追加する場所の制約を削除する必要があります。

#### <a name="a-nameremovelocconstraint-step-2-remove-the-location-constraint"></a><a name="removeLocConstraint"> 手順 2 です。 場所の制約の削除

手動フェールオーバー中、`pcs`コマンド`move`または`crm`コマンド`migrate`のリソースを新しいターゲット ノードに配置する場所の制約を追加します。 新しい制約を表示するには、リソースを手動で移動した後に次のコマンドを実行します。

- **RHEL/Ubuntu 例**

   ```bash
   sudo pcs constraint list --full
   ```

- **SLES 例**

   ```bash
   crm config show
   ```

手動フェールオーバーのために作成される制約の例です。 
 `Enabled on: Node1 (score:INFINITY) (role: Master) (id:cli-prefer-ag_cluster-master)`

- **RHEL/Ubuntu 例**

   次のコマンドで、`cli-prefer-ag_cluster-master` は削除が必要な制約の ID です。 `sudo pcs constraint list --full` によってこの ID が返されます。 
   
   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```
   
- **SLES 例**

   次のコマンドで`cli-prefer-ms-ag_cluster`制約の id を指定します。 `crm config show` によってこの ID が返されます。 
   
   ```bash
   crm configure
   delete cli-prefer-ms-ag_cluster 
   commit
   ```

>[!NOTE]
>自動フェールオーバーでは場所の制約が追加されないため、削除は不要です。 

詳細:
- [Red Hat - クラスター リソースの管理](http://access.redhat.com/documentation/Red_Hat_Enterprise_Linux/6/html/Configuring_the_Red_Hat_High_Availability_Add-On_with_Pacemaker/ch-manageresource-HAAR.html)
- [ペースのリソースを手動で移動](http://clusterlabs.org/doc/en-US/Pacemaker/1.1-pcs/html/Clusters_from_Scratch/_move_resources_manually.html)
 [SLES 管理ガイド - リソース](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#sec.ha.troubleshooting.resource) 
 
## <a name="forceFailover"></a> 強制フェールオーバー 

強制フェールオーバーは、厳密に災害復旧です。 ここでは、することはできませんフェールオーバー クラスター管理ツールを使用して、プライマリ データ センターがダウンしているため。 非同期のセカンダリ レプリカに対して強制フェールオーバーを実行した場合、データ損失の可能性があります。 サービスをすぐに、可用性グループに復元あり、データの損失を許容できる場合は、フェールオーバーを強制のみです。

場合は使用できない場合はクラスター管理ツール - たとえば、クラスターと対話するため、クラスターが、プライマリ データ センターで障害イベントにより応答しない場合、外部クラスター マネージャーをバイパスするフェールオーバーを強制する必要があります。 通常の操作は、データ損失のリスクがあるために、この手順はお勧めできません。 フェールオーバー アクションを実行するクラスター管理ツールが失敗したときに使用します。 機能的には、この手順がに似ていますが[強制手動フェールオーバーを実行する](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)Windows で、AG にします。
 
強制フェールオーバーに対して、このプロセスは、SQL Server on Linux に固有です。

1. かどうかを可用性グループ リソースをクラスターによって管理されませんを確認します。 

      - 対象のクラスター ノードでリソースをアンマネージ モードに設定します。 このコマンドは、停止リソースの監視および管理するリソースのエージェントを通知します。 以下に例を示します。 
      
      ```bash
      sudo pcs resource unmanage <resourceName>
      ```

      - アンマネージ モードに、リソースのモードを設定しようとすると、失敗した場合、リソースを削除します。 以下に例を示します。

      ```bash
      sudo pcs resource delete <resourceName>
      ```

      >[!NOTE]
      >リソースを削除するときにも削除すべての関連する制約です。 

1. セカンダリ レプリカをホストする SQL Server のインスタンスで、セッションのコンテキスト変数を設定`external_cluster`です。

   ```Transact-SQL
   EXEC sp_set_session_context @key = N'external_cluster', @value = N'yes';
   ```

1. Transact SQL を使用した可用性グループをフェールオーバーします。 次の例では、置換`<MyAg>`可用性グループの名前に置き換えます。 対象のセカンダリ レプリカをホストする SQL Server のインスタンスに接続し、次のコマンドを実行します。

   ```Transact-SQL
   ALTER AVAILABILITY GROUP <MyAg> FORCE_FAILOVER_ALLOW_DATA_LOSS;
   ```

1.  強制フェールオーバー後に、クラスター リソースの監視と管理を再起動するか、可用性グループ リソースを再作成する前に正常な状態に、可用性グループを表示します。 確認、[強制フェールオーバー後の必須タスク](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md#FollowUp)です。

1.  クラスター リソースの監視と管理を再起動するか。

   クラスター リソースの監視と管理を再開するには、次のコマンドを実行します。

   ```bash
   sudo pcs resource manage <resourceName>
   sudo pcs resource cleanup <resourceName>
   ```

   クラスター リソースを削除した場合は、それを再作成します。 クラスター リソースを再作成する手順についてで[可用性グループ リソースを作成する](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)です。

>[!Important]
>データの損失になる可能性があるために、障害復旧の訓練を上記の手順を使用しないでください。 代わりに、同期するレプリカを非同期と指示を変更[通常の手動フェールオーバー](#manualFailover)です。

## <a name="database-level-monitoring-and-failover-trigger"></a>データベース レベルの監視とフェールオーバーのトリガー

`CLUSTER_TYPE=EXTERNAL`、フェイル オーバー トリガー セマンティクスは次のさまざまな WSFC と比較します。 Wsfc では、SQL Server のインスタンスに、可用性グループがある場合は、out の遷移`ONLINE`データベースにより、エラーを報告する可用性グループの正常性の状態します。 応答では、クラスター マネージャーは、フェールオーバー アクションをトリガーします。 Linux では、SQL Server のインスタンスは、クラスターと通信できません。 データベースの正常性の完了を監視*外で*です。 かどうかのユーザーを選択してデータベース レベルのフェールオーバーの監視とフェールオーバー (オプションを設定して`DB_FAILOVER=ON`、可用性グループを作成するとき)、クラスターは、データベースの状態が確認`ONLINE`監視のアクションを実行するたびにします。 クラスター内の状態を照会する`sys.databases`です。 いずれかの状態とは異なる`ONLINE`、自動的に (自動フェールオーバーの条件が満たされた場合)、フェールオーバーがトリガーされます。 フェイル オーバーの実際の時間は、sys.databases で更新されているデータベースの状態と同様に、監視操作の頻度に依存します。

自動フェールオーバーには、少なくとも 1 つの同期レプリカが必要です。

## <a name="next-steps"></a>次のステップ

[SQL Server 可用性グループのクラスター リソースの Red Hat Enterprise Linux クラスターを構成します。](sql-server-linux-availability-group-cluster-rhel.md)

[SQL Server 可用性グループのクラスター リソースの SUSE Linux Enterprise Server クラスターを構成します。](sql-server-linux-availability-group-cluster-sles.md)

[Ubuntu クラスターは、SQL Server 可用性グループのクラスター リソースを構成します。](sql-server-linux-availability-group-cluster-ubuntu.md)
