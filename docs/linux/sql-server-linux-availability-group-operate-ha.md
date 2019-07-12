---
title: SQL Server on Linux の可用性グループを操作します。
description: ''
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
manager: jroth
ms.date: 03/01/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: c1dfdeead4f8eb82dc95882d719ef42f16017bdc
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834241"
---
# <a name="operate-always-on-availability-groups-on-linux"></a>Linux 上の可用性グループに対して常に

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

## <a name="upgrade-availability-group"></a>可用性グループをアップグレードします。

可用性グループをアップグレードする前に、パターンとプラクティスを確認してください。[可用性グループ レプリカ インスタンスのアップグレード](../database-engine/availability-groups/windows/upgrading-always-on-availability-group-replica-instances.md)します。

次のセクションでは、可用性グループで Linux 上の SQL Server インスタンスでのローリング アップグレードを実行する方法を説明します。 

### <a name="upgrade-steps-on-linux"></a>Linux 上のアップグレード手順

可用性グループ レプリカが Linux での SQL Server のインスタンス上にある場合は、可用性グループのクラスターの種類は`EXTERNAL`または`NONE`します。 さらに、Windows Server フェールオーバー クラスター (WSFC) は、クラスター マネージャーで管理されている可用性グループ`EXTERNAL`します。 Corosync と pacemaker は、外部のクラスター マネージャーの例を示します。 クラスター マネージャーがない可用性グループがクラスターの種類`NONE`アップグレード手順は、こちらは、クラスターの種類の可用性グループの特定`EXTERNAL`または`NONE`します。

インスタンスをアップグレードする順序は、各自のロールがセカンダリと同期または非同期レプリカをホストするかどうかのかどうかに依存します。 最初に非同期のセカンダリ レプリカをホストする SQL Server のインスタンスをアップグレードします。 同期セカンダリ レプリカをホストするインスタンスをアップグレードします。 

   >[!NOTE]
   >場合は、可用性グループのみがある非同期レプリカは、データの損失を回避するためには 1 つのレプリカを同期に変更し、同期されるまで待ちます。 このレプリカをアップグレードします。
   
開始する前に、各データベースをバックアップします。

1. アップグレードの対象となるセカンダリ レプリカをホストしているノードのリソースを停止します。
   
   アップグレード コマンドを実行する前に、クラスターの監視し、不必要に失敗することはありませんので、リソースを停止します。 次の例では、停止するリソース上の原因となるノードの場所の制約を追加します。 Update`ag_cluster-master`リソース名を持つと`nodeName1`ノードがアップグレードの対象となるレプリカをホストします。

   ```bash
   pcs constraint location ag_cluster-master avoids nodeName1
   ```

1. セカンダリ レプリカでは、SQL Server をアップグレードします。

   次の例のアップグレード`mssql-server`と`mssql-server-ha`パッケージ。

   ```bash
   sudo yum update mssql-server
   sudo yum update mssql-server-ha
   ```
1. 場所の制約を削除します。

   アップグレード コマンドを実行する前に、クラスターの監視し、不必要に失敗することはありませんので、リソースを停止します。 次の例では、停止するリソース上の原因となるノードの場所の制約を追加します。 Update`ag_cluster-master`リソース名を持つと`nodeName1`ノードがアップグレードの対象となるレプリカをホストします。

   ```bash
   pcs constraint remove location-ag_cluster-master-rhel1--INFINITY
   ```
   ベスト プラクティスとして、リソースが開始されたことを確認します (を使用して`pcs status`コマンド) と、セカンダリ レプリカが接続されているし、アップグレード後に状態を同期します。

1. すべてのセカンダリ レプリカをアップグレードした後に手動でフェールオーバー同期セカンダリ レプリカの 1 つ。

   可用性グループを`EXTERNAL`クラスターの種類をクラスターの管理ツールを使用して、失敗を over; で可用性グループを`NONE`クラスターの種類は、TRANSACT-SQL を使用してフェールオーバーする必要があります。 
   次の例では、クラスターの管理ツールを使用して可用性グループのフェールオーバーが失敗しました。 置換`<targetReplicaName>`プライマリとなる同期セカンダリ レプリカの名前に置き換えます。

   ```bash
   sudo pcs resource move ag_cluster-master <targetReplicaName> --master  
   ``` 
   
   >[!IMPORTANT]
   >次の手順は、クラスター マネージャーがない可用性グループにのみ適用されます。

   可用性グループのクラスターの種類が場合`NONE`、手動でフェールオーバーします。 次の手順を実行します。

      a. 次のコマンドは、プライマリ レプリカをセカンダリに設定します。 置換`AG1`可用性グループの名前に置き換えます。 プライマリ レプリカをホストする SQL Server のインスタンスでは、TRANSACT-SQL コマンドを実行します。

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] SET (ROLE = SECONDARY);
      ```

      b. 次のコマンドは、同期セカンダリ レプリカをプライマリに設定します。 同期セカンダリ レプリカをホストする SQL Server のインスタンスのターゲット インスタンスで、次の TRANSACT-SQL コマンドを実行します。

      ```transact-sql
      ALTER AVAILABILITY GROUP [ag1] FAILOVER;
      ```

1. フェールオーバー後は、前の手順を繰り返すことにより、古いプライマリ レプリカで SQL Server をアップグレードします。

   次の例のアップグレード`mssql-server`と`mssql-server-ha`パッケージ。

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

1. クラスター タイプが EXTERNAL、-、外部のクラスター マネージャーで、可用性グループの手動フェールオーバーが発生した場所の制約をクリーンアップします。 

   ```bash
   sudo pcs constraint remove cli-prefer-ag_cluster-master  
   ```

1. 新しくアップグレードされたセカンダリ レプリカの元のプライマリ レプリカのデータ移動を再開します。 SQL Server の上位バージョンのインスタンスが可用性グループに低いバージョンのインスタンスにログ ブロックを転送するときに、この手順が必要です。 新しいセカンダリ レプリカ (元のプライマリ レプリカ) で、次のコマンドを実行します。

   ```transact-sql
   ALTER DATABASE database_name SET HADR RESUME;
   ```

すべてのサーバーをアップグレードした後にフェールバックできます。 必要な場合は、- 元のプライマリにフェールオーバーします。 

## <a name="drop-an-availability-group"></a>可用性グループを削除します。

可用性グループを削除する実行[DROP AVAILABILITY GROUP](../t-sql/statements/drop-availability-group-transact-sql.md)します。 クラスターの種類が場合`EXTERNAL`または`NONE`レプリカをホストする SQL Server の各インスタンス上のコマンドを実行します。 たとえば、という名前の可用性グループを削除する`group_name`次のコマンドを実行します。

   ```transact-sql
   DROP AVAILABILITY GROUP group_name
   ```
 

## <a name="next-steps"></a>次の手順

[SQL Server 可用性グループのクラスター リソースの Red Hat Enterprise Linux クラスターを構成します。](sql-server-linux-availability-group-cluster-rhel.md)

[SQL Server 可用性グループのクラスター リソースの SUSE Linux Enterprise Server クラスターを構成します。](sql-server-linux-availability-group-cluster-sles.md)

[SQL Server 可用性グループのクラスター リソースの Ubuntu クラスターの構成します。](sql-server-linux-availability-group-cluster-ubuntu.md)
