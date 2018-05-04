---
title: Linux 上の読み取りのスケールの SQL Server 可用性グループの構成 |Microsoft ドキュメント
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 02/14/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.openlocfilehash: 2b566f27e227d21728030a160dd8fedbe29f92e9
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configure-a-sql-server-availability-group-for-read-scale-on-linux"></a>Linux 上の読み取りのスケールの SQL Server 可用性グループの構成します。

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

Linux では、SQL Server 常に 可用性グループ (AG) な読み取りワークロード用を構成できます。 2 つの種類の Ag のアーキテクチャがあります。 高可用性のためのアーキテクチャでは、クラスター マネージャーを使用して、ビジネス継続性を提供します。 このアーキテクチャは、読み取りスケール レプリカも含めることができます。 高可用性アーキテクチャを作成するを参照してください。[を構成する SQL Server Always On 可用性グループ Linux での高可用性の](sql-server-linux-availability-group-configure-ha.md)します。 その他のアーキテクチャでは、読み取りスケール ワークロードのみをサポートします。 この記事では、読み取りスケール ワークロードについてクラスター マネージャーがない可用性グループを作成する方法について説明します。 このアーキテクチャでは、読み取り-小数点以下桁数のみを提供します。 高可用性を実現をしていません。

>[!NOTE]
>可用性グループに`CLUSTER_TYPE = NONE`別のオペレーティング システム プラットフォームでホストされるレプリカを含めることができます。 高可用性をサポートできません。 

[!INCLUDE [Create prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>可用性グループを作成します。

可用性グループを作成します。 Set `CLUSTER_TYPE = NONE`. さらに、各レプリカを設定`FAILOVER_MODE = NONE`です。 分析を実行するか、ワークロードをレポートできますを直接クライアント アプリケーションは、セカンダリ データベースに接続します。 また、読み取り専用ルーティング リストを作成することもできます。 転送用のプライマリ レプリカへの接続は、ラウンド ロビン方式で、ルーティング リストから各セカンダリ レプリカに接続要求を読み取る。

次の TRANSACT-SQL スクリプトを作成、AG という`ag1`です。 スクリプトは、構成、可用性グループ レプリカと`SEEDING_MODE = AUTOMATIC`です。 この設定は、各セカンダリ サーバーでは、可用性グループに追加した後、データベースを自動的に作成する SQL Server をによりします。 環境内の次のスクリプトを更新します。 置換、`<node1>`と`<node2>`レプリカをホストする SQL Server インスタンスの名前を持つ値です。 置換、`<5022>`エンドポイント用に設定するポートを持つ値です。 SQL Server のプライマリ レプリカでは、次の TRANSACT-SQL スクリプトを実行します。

```SQL
CREATE AVAILABILITY GROUP [ag1]
    WITH (CLUSTER_TYPE = NONE)
    FOR REPLICA ON
        N'<node1>' WITH (
            ENDPOINT_URL = N'tcp://<node1>:<5022>',
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
                    SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            ),
        N'<node2>' WITH ( 
            ENDPOINT_URL = N'tcp://<node2>:<5022>', 
            AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,
            FAILOVER_MODE = MANUAL,
            SEEDING_MODE = AUTOMATIC,
            SECONDARY_ROLE (ALLOW_CONNECTIONS = ALL)
            );
        
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

### <a name="join-secondary-sql-servers-to-the-ag"></a>セカンダリ SQL サーバーを可用性グループに参加させる

次の TRANSACT-SQL スクリプトは、AG という名前に、サーバーを結合`ag1`です。 環境内で使用するスクリプトを更新します。 各セカンダリ SQL Server レプリカで、可用性グループに参加する次の TRANSACT-SQL スクリプトを実行します。

```SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = NONE);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create post](../includes/ss-linux-cluster-availability-group-create-post.md)]

この可用性グループでは、高可用性構成はありません。 高可用性を実現する場合は、ある手順に従って[、Always On 可用性グループを構成する SQL Server on Linux の](sql-server-linux-availability-group-configure-ha.md)します。 具体的で、可用性グループを作成`CLUSTER_TYPE=WSFC`(Windows) にまたは`CLUSTER_TYPE=EXTERNAL`(Linux) にします。 いずれかの Windows Server フェールオーバー クラスタ リング Windows または Linux のペースを使用して、クラスター マネージャーを統合し。

## <a name="connect-to-read-only-secondary-replicas"></a>読み取り専用のセカンダリ レプリカに接続します。

これには読み取り専用のセカンダリ レプリカに接続する 2 つの方法があります。 アプリケーションでは、セカンダリ レプリカをホストする SQL Server インスタンスに直接接続でき、データベースのクエリを実行することができます。 これらもルーティングを使用して読み取り専用、リスナーを作成する必要があります。

* [読み取り可能なセカンダリ レプリカ](../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)
* [読み取り専用ルーティング](../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md#ConnectToSecondary)

## <a name="fail-over-the-primary-replica-on-a-read-scale-availability-group"></a>読み取りのスケールの可用性グループのプライマリ レプリカのフェールオーバーします。

[!INCLUDE[Force failover](../includes/ss-force-failover-read-scale-out.md)]

## <a name="next-steps"></a>次の手順

* [分散型可用性グループを構成します。](..\database-engine\availability-groups\windows\distributed-availability-groups-always-on-availability-groups.md)
* [可用性グループの詳細を表示します](..\database-engine\availability-groups\windows\overview-of-always-on-availability-groups-sql-server.md)
* [強制手動フェールオーバーを実行します。](../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)

