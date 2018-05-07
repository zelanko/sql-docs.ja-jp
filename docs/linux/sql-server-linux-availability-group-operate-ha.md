---
title: 可用性グループの SQL Server on Linux の動作 |Microsoft ドキュメント
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/01/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.openlocfilehash: fd23b5c0de42fa0d91b893000c409083a2637fbb
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="operate-always-on-availability-groups-on-linux"></a>Linux 上の可用性グループに対して常に実行します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

## <a name="upgrade-availability-group"></a>可用性グループをアップグレードします。

可用性グループをアップグレードする前に確認して、パターンとプラクティスで[可用性グループのレプリカ インスタンスをアップグレードする](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md)です。

次のセクションでは、可用性グループを含む Linux 上の SQL Server インスタンスでローリング アップグレードを実行する方法を説明します。 

### <a name="upgrade-steps-on-linux"></a>Linux 上のアップグレード手順

可用性グループのレプリカが Linux での SQL Server のインスタンス上にある場合は、可用性グループのクラスターの種類は`EXTERNAL`または`NONE`です。 さらには、Windows Server フェールオーバー クラスター (WSFC) クラスター マネージャーで管理されている可用性グループ`EXTERNAL`です。 Corosync とペースでは、外部のクラスター マネージャーの例を示します。 クラスター マネージャーがありませんがある可用性グループがクラスターの種類`NONE`アップグレード手順は、こちらは、クラスターの種類の可用性グループの特定`EXTERNAL`または`NONE`です。

インスタンスをアップグレードする順序は、その役割は、セカンダリ、同期または非同期のレプリカをホストするかどうかかどうかに依存します。 最初に非同期のセカンダリ レプリカをホストする SQL Server のインスタンスをアップグレードします。 同期セカンダリ レプリカをホストするインスタンスをアップグレードします。 

   >[!NOTE]
   >のみの場合、可用性グループ非同期をデータの損失を回避するのには、レプリカは 1 つのレプリカを同期に変更しが同期されるまで待ちます。 このレプリカをアップグレードします。
   
開始する前に、各データベースをバックアップします。

1. アップグレードの対象となるセカンダリ レプリカをホストしているノード上のリソースを停止します。
   
   アップグレード コマンドを実行する前に、クラスターを監視し、は、不必要に失敗するように、リソースを停止します。 次の例では、停止するためのリソースに原因となるノードの場所の制約を追加します。 更新`ag_cluster-master`リソース名を持つと`nodeName1`アップグレードの対象となるレプリカをホストしているノードにします。

   ```bash
   pcs constraint location ag_cluster-master avoids nodeName1
   ```

1. セカンダリ レプリカでは、SQL Server をアップグレードします。

   次の例のアップグレード`mssql-server`と`mssql-server-ha`パッケージです。

   ```bash
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
1. 場所の制約を削除します。

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

1. フェールオーバー後は、前の手順を繰り返して、古いプライマリ レプリカで SQL Server をアップグレードします。

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

1. クラスターの種類が外部、-、外部のクラスター マネージャーで、可用性グループの手動フェールオーバーが発生した場所の制約をクリーンアップします。 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```

1. 新たにアップグレードされたセカンダリ レプリカの元のプライマリ レプリカのデータ移動を再開します。 SQL Server の上位バージョンのインスタンスが可用性グループに下位バージョンのインスタンスにログ ブロックを転送するときに、この手順が必要です。 新しいセカンダリ レプリカ (元のプライマリ レプリカ) で、次のコマンドを実行します。

   ```transact-sql
   ALTER DATABASE database_name SET HADR RESUME;
   ```

すべてのサーバーをアップグレードするには、後にすることができますフェールバックします。 必要な場合は、- 元のプライマリに失敗します。 

## <a name="drop-an-availability-group"></a>可用性グループを削除します。

可用性グループを削除するには実行[DROP AVAILABILITY GROUP](../t-sql/statements/drop-availability-group-transact-sql.md)です。 クラスターの種類が場合`EXTERNAL`または`NONE`レプリカをホストする SQL Server のすべてのインスタンスでのコマンドを実行します。 たとえば、という名前の可用性グループを削除する`group_name`次のコマンドを実行します。

   ```transact-sql
   DROP AVAILABILITY GROUP group_name
   ```
 

## <a name="next-steps"></a>次の手順

[SQL Server 可用性グループのクラスター リソースの Red Hat Enterprise Linux クラスターを構成します。](sql-server-linux-availability-group-cluster-rhel.md)

[SQL Server 可用性グループのクラスター リソースの SUSE Linux Enterprise Server クラスターを構成します。](sql-server-linux-availability-group-cluster-sles.md)

[Ubuntu クラスターは、SQL Server 可用性グループのクラスター リソースを構成します。](sql-server-linux-availability-group-cluster-ubuntu.md)
