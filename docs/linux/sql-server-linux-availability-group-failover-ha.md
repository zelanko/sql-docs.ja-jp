---
title: "可用性グループの SQL Server on Linux の動作 |Microsoft ドキュメント"
description: 
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 07/20/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: sql-linux
ms.suite: sql
ms.custom: 
ms.technology: database-engine
ms.assetid: 
ms.workload: Inactive
ms.openlocfilehash: cf0a61c924a10066a41bcf4127e444b60f0f50bc
ms.sourcegitcommit: b4fd145c27bc60a94e9ee6cf749ce75420562e6b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/01/2018
---
# <a name="operate-always-on-availability-groups-on-linux"></a>Linux 上の可用性グループに対して常に実行します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

## <a name="failover"></a>可用性グループをフェールオーバーする方法

外部のクラスター マネージャーによって管理されている可用性グループにフェールオーバーするには、クラスター管理ツールを使用します。 たとえば、ソリューションでは、Linux クラスターを管理するペースが使用されている場合を使用して`pcs`RHEL または Ubuntu に対して手動フェールオーバーを実行します。 Sles 使用`crm`です。 

> [!IMPORTANT]
> 通常の操作はフェールオーバーされません SSMS や PowerShell などの TRANSACT-SQL または SQL Server の管理ツール。 ときに`CLUSTER_TYPE = EXTERNAL`にのみ使用できる値`FAILOVER_MODE`は`EXTERNAL`します。 これらの設定では、すべてのアクションを手動または自動フェールオーバーは、外部のクラスター マネージャーで実行されます。 

### <a name="manual-failover-examples"></a>手動フェールオーバーの例

外部のクラスター管理ツールを使用して可用性グループを手動でフェールオーバーします。 通常の操作では、TRANSACT-SQL でのフェールオーバーを開始できません。 外部のクラスター管理ツールが応答しない場合は、フェールオーバーする可用性グループを強制できます。 手動フェールオーバーを強制する手順については、次を参照してください。[手動移動クラスター ツールが応答性の高い](#forceManual)です。

2 つの手順で手動フェールオーバーを完了します。 

1. 新しいノードにリソースを所有しているクラスター ノードから、可用性グループ リソースを移動します。

   クラスター マネージャーでは、可用性グループ リソースを移動し、場所の制約を追加します。 この制約は、新しいノードで実行するリソースを構成します。 いずれかの手動または自動フェールオーバー、将来を移動するために、この制約を削除する必要があります。

2. 場所の制約を削除します。

#### <a name="1-manually-fail-over"></a>1.手動でフェールオーバーします。

という名前の可用性グループ リソースを手動でフェールオーバーする*ag_cluster*という名前のクラスター ノードに*nodeName2*、お使いのディストリビューションに適切なコマンドを実行します。

- **RHEL/Ubuntu 例**

   ```bash
   sudo pcs resource move ag_cluster-master nodeName2 --master
   ```

- **SLES 例**

   ```bash
   crm resource migrate ag_cluster nodeName2
   ```



>[!IMPORTANT]
>リソースを手動でフェールオーバーした後は、移動中に自動的に追加される場所の制約を削除する必要があります。

#### <a name="2-remove-the-location-constraint"></a>2.場所の制約の削除

手動の移動中に、`pcs`コマンド`move`または`crm`コマンド`migrate`のリソースを新しいターゲット ノードに配置する場所の制約を追加します。 新しい制約を表示するには、リソースを手動で移動した後に次のコマンドを実行します。

- **RHEL/Ubuntu 例**

   ```bash
   sudo pcs constraint --full
   ```

- **SLES 例**

   ```bash
   crm config show
   ```

今後の移動 (自動フェールオーバーを含む) が正常に行われるためには、場所の制約を削除しておく必要があります。 

次のコマンドを実行して、制約を削除します。 

- **RHEL/Ubuntu 例**

   この例では`ag_cluster-master`移動されたリソースの名前を指定します。 

   ```bash
   sudo pcs resource clear ag_cluster-master 
   ```

- **SLES 例**

   この例では`ag_cluster`移動されたリソースの名前を指定します。 

   ```bash
   crm resource clear ag_cluster
   ```

または、次のコマンドを実行して場所の制約を削除することもできます。  

- **RHEL/Ubuntu 例**

   次のコマンドで、`cli-prefer-ag_cluster-master` は削除が必要な制約の ID です。 `sudo pcs constraint --full` によってこの ID が返されます。 

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
 

### <a name="forceManual"></a>クラスター ツールの応答がありません手動移動します。 

極端な場合、ユーザーがクラスターと対話するためのクラスター管理ツールを使用できない場合 (つまり、クラスターが応答していない、クラスター管理ツールがある障害のある動作)、ユーザーが手動でフェールオーバーする必要があります外部クラスター マネージャーをバイパスします。 これはお勧めできませんの定期的操作は、クラスター管理ツールを使用してフェールオーバー操作を実行するクラスターが失敗している場合内で使用する必要があります。

クラスター管理ツールを使用して可用性グループをフェールオーバーすることはできない場合、は、SQL Server ツールからフェールオーバーをこれらの手順に従います。

1. かどうかを可用性グループ リソースをクラスターによって管理されませんを確認します。 

      - リソースをアンマネージ モードに設定しようとしてください。 これは、リソースの監視を停止するリソース エージェントと管理に通知します。 例: 
      
      ```bash
      sudo pcs resource unmanage <**resourceName**>
      ```

      - アンマネージ モードに、リソースのモードを設定しようとすると、失敗した場合、リソースを削除します。 例:

      ```bash
      sudo pcs resource delete <**resourceName**>
      ```

      >[!NOTE]
      >リソースを削除するときにも削除すべての関連する制約です。 

1. セッション コンテキストの変数を手動で設定`external_cluster`です。

   ```Transact-SQL
   EXEC sp_set_session_context @key = N'external_cluster', @value = N'yes';
   ```

1. Transact SQL を使用した可用性グループのフェールオーバーは失敗します。 置換次の例で`<**MyAg**>`可用性グループの名前に置き換えます。 対象のセカンダリ レプリカをホストする SQL Server のインスタンスに接続し、次のコマンドを実行します。

   ```Transact-SQL
   ALTER AVAILABILITY GROUP <**MyAg**> FAILOVER;
   ```

1. クラスター リソースの監視と管理を再起動します。 次のコマンドを実行します。

   ```bash
   sudo pcs resource manage <**resourceName**>
   sudo pcs resource cleanup <**resourceName**>
   ```

## <a name="database-level-monitoring-and-failover-trigger"></a>データベース レベルの監視とフェールオーバーのトリガー

`CLUSTER_TYPE=EXTERNAL`、フェイル オーバー トリガー セマンティクスは次のさまざまな WSFC と比較します。 Wsfc では、SQL Server のインスタンスに可用性グループがある場合は、out の遷移`ONLINE`データベースにより、エラーを報告する可用性グループのヘルスの状態します。 フェールオーバー アクションをトリガーする、クラスター マネージャーを通知これすます。 Linux では、SQL Server のインスタンスは、クラスターと通信できません。 データベース ヘルスの監視は、「外部で」行われます。 かどうかのユーザーを選択してデータベース レベルのフェールオーバーの監視とフェールオーバー (オプションを設定して`DB_FAILOVER=ON`、可用性グループを作成するとき)、クラスターは、データベースの状態が確認`ONLINE`と監視のアクションを実行するたびにします。 クラスター内の状態を照会する`sys.databases`です。 いずれかの状態とは異なる`ONLINE`、自動的に (自動フェールオーバーの条件が満たされた場合)、フェールオーバーがトリガーされます。 フェイル オーバーの実際の時間は、sys.databases で更新されているデータベースの状態と同様に、監視操作の頻度に依存します。

## <a name="upgrade-availability-group"></a>可用性グループをアップグレードします。

可用性グループをアップグレードする前に、ベスト プラクティスを確認で[可用性グループのレプリカ インスタンスをアップグレードする](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md)です。

次のセクションでは、可用性グループを含む Linux 上の SQL Server インスタンスでローリング アップグレードを実行する方法を説明します。 

### <a name="upgrade-steps-on-linux"></a>Linux 上のアップグレード手順

可用性グループのレプリカが Linux での SQL Server のインスタンス上にある場合は、可用性グループのクラスターの種類は`EXTERNAL`または`NONE`です。 さらには、Windows Server フェールオーバー クラスター (WSFC) クラスター マネージャーで管理されている可用性グループ`EXTERNAL`です。 Corosync とペースでは、外部のクラスター マネージャーの例を示します。 クラスター マネージャーがありませんがある可用性グループがクラスターの種類`NONE`アップグレード手順は、こちらは、クラスターの種類の可用性グループの特定`EXTERNAL`または`NONE`です。

1. 開始する前に、各データベースをバックアップします。
2. セカンダリ レプリカをホストする SQL Server のインスタンスをアップグレードします。

    a. 非同期のセカンダリ レプリカを最初にアップグレードします。

    b. 同期セカンダリ レプリカをアップグレードします。

   >[!NOTE]
   >のみの場合、可用性グループ非同期レプリカ - をデータの損失を回避するのには 1 つのレプリカを同期に変更しが同期されるまでを待ちます。 このレプリカをアップグレードします。
   
   b.1. アップグレードの対象となるセカンダリ レプリカをホストしているノード上のリソースを停止します。
   
   アップグレード コマンドを実行する前に、クラスターを監視し、は、不必要に失敗するように、リソースを停止します。 次の例では、停止するためのリソースに原因となるノードの場所の制約を追加します。 更新`ag_cluster-master`リソース名を持つと`nodeName1`アップグレードの対象となるレプリカをホストしているノードにします。

   ```bash
   pcs constraint location ag_cluster-master avoids nodeName1
   ```
   b.2. セカンダリ レプリカで SQL Server をアップグレードします。

   次の例のアップグレード`mssql-server`と`mssql-server-ha`パッケージです。

   ```bash
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
   b.3. 場所の制約の削除

   アップグレード コマンドを実行する前に、クラスターを監視し、は、不必要に失敗するように、リソースを停止します。 次の例では、停止するためのリソースに原因となるノードの場所の制約を追加します。 更新`ag_cluster-master`リソース名を持つと`nodeName1`アップグレードの対象となるレプリカをホストしているノードにします。

   ```bash
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```
   ベスト プラクティスとして、リソースが開始されたことを確認します (を使用して`pcs status`コマンド)、セカンダリ レプリカが接続されているし、アップグレード後に状態が同期されているとします。

1. すべてのセカンダリ レプリカをアップグレードした後に手動でフェールオーバー同期セカンダリ レプリカのいずれか。

   可用性グループを`EXTERNAL`タイプのクラスターをクラスター管理ツールを使用して、失敗を over; の可用性グループを`NONE`クラスターの種類は、TRANSACT-SQL を使用してフェールオーバーする必要があります。 
   次の例は、クラスター管理ツールを使用して可用性グループのフェールオーバーが失敗します。 置き換える`<targetReplicaName>`プライマリとなる同期セカンダリ レプリカの名前に置き換えます。

   ```bash
   sudo pcs resource move ag_cluster-master <targetReplicaName> --master  
   ``` 
   
   >[!IMPORTANT]
   >次の手順は、クラスター マネージャーがない可用性グループにのみ適用されます。  
   可用性グループのクラスターの種類が場合`NONE`を手動でフェールオーバーします。 次の手順を実行します。

      a. 次のコマンドは、プライマリ レプリカをセカンダリに設定します。 置き換える`AG1`可用性グループの名前に置き換えます。 プライマリ レプリカをホストする SQL Server のインスタンスで TRANSACT-SQL コマンドを実行します。

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY);
      ```

      b. 次のコマンドは、同期セカンダリ レプリカをプライマリに設定します。 同期セカンダリ レプリカをホストする SQL Server のインスタンスのターゲット インスタンスで、次の TRANSACT-SQL コマンドを実行します。

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] FAILOVER;
      ```

1. フェールオーバー後は、b.1 b.3 上記の手順で説明されている同じ手順を繰り返して、古いプライマリ レプリカで SQL Server をアップグレードします。

   次の例のアップグレード`mssql-server`と`mssql-server-ha`パッケージです。

   ```bash
   # add constraint for the resource to stop on the upgraded node
   # replace 'nodename2' with the name of the cluster node targeted for upgrade
   pcs constraint location ag_cluster-master avoids nodeName2
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
   
   ```bash
   # upgrade mssql-server and mssql-server-ha packages
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```

   ```bash
   # remove the constraint; make sure the resource is started and replica is connected and synchronized
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```

1. 外部のクラスターで、可用性グループ マネージャー - クラスターの入力場所は外部、クリーンアップ、手動フェールオーバーが発生した場所の制約条件です。 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```

1. 新たにアップグレードされたセカンダリ レプリカの元のプライマリ レプリカのデータ移動を再開します。 これは、機能は、SQL Server の上位バージョンのインスタンスが可用性グループに下位バージョンのインスタンスにログ ブロックを転送するときに必要です。 新しいセカンダリ レプリカ (元のプライマリ レプリカ) で、次のコマンドを実行します。

   ```transact-sql
   ALTER DATABASE database_name SET HADR RESUME;
   ```

すべてのサーバーをアップグレードすると、フェールバック - できますスイッチ_バック - 元のプライマリに必要な場合です。 

## <a name="drop-an-availability-group"></a>可用性グループを削除します。

可用性グループを削除するには実行[DROP AVAILABILITY GROUP](../t-sql/statements/drop-availability-group-transact-sql.md)です。 クラスターの種類が場合`EXTERNAL`または`NONE`レプリカをホストする SQL Server のすべてのインスタンスでのコマンドを実行します。 たとえば、という名前の可用性グループを削除する`group_name`次のコマンドを実行します。

   ```transact-sql
   DROP AVAILABILITY GROUP group_name
   ```
 

## <a name="next-steps"></a>次の手順

[SQL Server 可用性グループのクラスター リソースの Red Hat Enterprise Linux クラスターを構成します。](sql-server-linux-availability-group-cluster-rhel.md)

[SQL Server 可用性グループのクラスター リソースの SUSE Linux Enterprise Server クラスターを構成します。](sql-server-linux-availability-group-cluster-sles.md)

[Ubuntu クラスターは、SQL Server 可用性グループのクラスター リソースを構成します。](sql-server-linux-availability-group-cluster-ubuntu.md)
