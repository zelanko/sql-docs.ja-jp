---
title: 構成する SQL Server Always On 可用性グループの Linux での高可用性 |Microsoft Docs
description: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 02/14/2018
ms.topic: article
ms.prod: sql
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: linux
ms.assetid: ''
ms.openlocfilehash: f392ccee932e27d35201426553bce26468d325e6
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/12/2018
ms.locfileid: "38981434"
---
# <a name="configure-sql-server-always-on-availability-group-for-high-availability-on-linux"></a>構成する SQL Server Always On 可用性グループの Linux での高可用性

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux 上で、SQL Server 常に 可用性グループ (AG) の高可用性を作成する方法について説明します。 Ag の構成の 2 つの種類があります。 A*高可用性*構成では、クラスター マネージャーを使用して、ビジネス継続性を提供します。 この構成は、読み取りスケール レプリカを含めることもできます。 このドキュメントでは、高可用性のため、可用性グループを作成する方法について説明します。

作成することも、クラスターのない、AG のマネージャー*読み取りスケール*します。 読み取りスケール可用性グループでは、パフォーマンス スケール アウトのための読み取り専用レプリカを提供することだけです。高可用性は提供されません。 読み取りスケール用の AG を作成するを参照してください。 [on Linux で読み取りスケールの SQL Server 可用性グループを構成する](sql-server-linux-availability-group-configure-rs.md)します。

高可用性とデータ保護を保証する構成では、2 つまたは 3 つの同期コミット レプリカが必要です。 次の 3 つの同期レプリカを可用性グループを 1 つのサーバーが利用できない場合でも自動的に回復できます。 詳細については、次を参照してください。[可用性グループの構成の高可用性とデータの保護](sql-server-linux-availability-group-ha.md)します。 

すべてのサーバーが物理または仮想にする必要があり、仮想サーバーが同じ仮想化プラットフォームである必要があります。 この要件は、フェンス エージェントはプラットフォーム固有であるためにです。 参照してください[ゲスト クラスター用のポリシー](https://access.redhat.com/articles/29440#guest_policies)します。

## <a name="roadmap"></a>ロードマップ

高可用性のための Linux サーバーで、AG を作成する手順は、Windows Server フェールオーバー クラスター上の手順と異なります。 手順の概要を以下に説明します。  

1. [次の 3 つのクラスター サーバー上の SQL Server の構成](sql-server-linux-setup.md)します。

   >[!IMPORTANT]
   >AG 内のすべての 3 つのサーバーは、Linux の高可用性では、フェンス エージェントを使用して、サーバー上のリソースを分離するため、物理または仮想の同一プラットフォームに配置する必要があります。 フェンス エージェントは、プラットフォームごとに固有です。

2. AG を作成します。 この手順は現在この記事で説明します。 

3. Pacemaker のように、クラスター リソース マネージャーを構成します。 
   
   クラスター リソース マネージャーを構成する方法は、特定の Linux ディストリビューションによって異なります。 配布の具体的な手順は次のリンクを参照してください。 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   * [SUSE](sql-server-linux-availability-group-cluster-sles.md)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   >[!IMPORTANT]
   >運用環境では、高可用性の STONITH などのフェンス エージェントが必要です。 このドキュメントでは、フェンス エージェントを使用しないでください。 デモはテストおよび検証のみです。 
   
   >Linux クラスターでは、フェンスを使用して、既知の状態、クラスターを返します。 フェンスを構成する方法は、ディストリビューションと、環境によって異なります。 現時点では、フェンス操作では、一部のクラウド環境で使用できません。 詳細については、次を参照してください。 [RHEL 高可用性クラスターの仮想化プラットフォームのサポート ポリシー](https://access.redhat.com/articles/29440)します。
   
   >SLES を参照してください。 [SUSE Linux Enterprise 高可用性 Extension](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing)します。

5. クラスター内のリソースとして、可用性グループを追加します。  

   クラスター内のリソースとして、可用性グループを追加する方法は、Linux ディストリビューションによって異なります。 配布の具体的な手順は次のリンクを参照してください。 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)
   * [SLES](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)

[!INCLUDE [Create Prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>AG を作成する

確実に自動フェールオーバーの高可用性構成の場合、可用性グループには、少なくとも 3 つのレプリカが必要です。 高可用性をサポート、次の構成のいずれかのことができます。

- [次の 3 つの同期レプリカ](sql-server-linux-availability-group-ha.md#threeSynch)

- [2 つの同期レプリカと構成のレプリカ](sql-server-linux-availability-group-ha.md#twoSynch)

詳しくは、次を参照してください。[可用性グループの構成の高可用性とデータの保護](sql-server-linux-availability-group-ha.md)します。

>[!NOTE]
>可用性グループには、追加の同期または非同期レプリカを含めることができます。 

Linux 上の高可用性のため、可用性グループを作成します。 使用して、 [CREATE AVAILABILITY GROUP](https://docs.microsoft.com/sql/t-sql/statements/create-availability-group-transact-sql)で`CLUSTER_TYPE = EXTERNAL`します。 

* 可用性グループ -`CLUSTER_TYPE = EXTERNAL`外部のクラスター エンティティが、可用性グループを管理するを指定します。 Pacemaker は、外部のクラスター エンティティの例を示します。 可用性グループのクラスターの種類が、外部場合 

* プライマリとセカンダリ レプリカを設定`FAILOVER_MODE = EXTERNAL`します。 
   Pacemaker などの外部のクラスター マネージャーを使って、レプリカが対話することを指定します。 

次の TRANSACT-SQL スクリプトの作成という名前の高可用性の AG`ag1`します。 このスクリプトでは、`SEEDING_MODE = AUTOMATIC` で AG レプリカが構成されます。 この設定により、各セカンダリ サーバーにデータベースを自動的に作成する SQL Server です。 ご利用の環境に合わせて次のスクリプトを変更してください。 置換、 `<node1>`、 `<node2>`、または`<node3>`レプリカをホストする SQL Server インスタンスの名前を持つ値。 置換、`<5022>`データ ミラーリング エンドポイントを設定するポート。 可用性グループを作成するには、プライマリ レプリカをホストする SQL Server インスタンスで次の TRANSACT-SQL を実行します。

実行**1 つだけ**の次のスクリプト。 

- [次の 3 つの同期レプリカを可用性グループの作成](#threeSynch)です。
- [2 つの同期レプリカと構成のレプリカの可用性グループの作成](#configOnly)
- [2 つの同期レプリカを可用性グループの作成](#readScale)です。

<a name="threeSynch"></a>

- 次の 3 つの同期レプリカでの AG を作成します。

   ```SQL
   CREATE AVAILABILITY GROUP [ag1]
       WITH (DB_FAILOVER = ON, CLUSTER_TYPE = EXTERNAL)
       FOR REPLICA ON
           N'<node1>' 
            WITH (
               ENDPOINT_URL = N'tcp://<node1>:<5022>',
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'<node2>' 
            WITH ( 
               ENDPOINT_URL = N'tcp://<node2>:<5022>', 
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'<node3>'
           WITH( 
              ENDPOINT_URL = N'tcp://<node3>:<5022>', 
              AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
              FAILOVER_MODE = EXTERNAL,
              SEEDING_MODE = AUTOMATIC
              );
        
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```

   >[!IMPORTANT]
   >次の 3 つの同期レプリカを AG を作成する前のスクリプトを実行した後、次のスクリプトを実行できません。

- 2 つの同期レプリカ構成のレプリカと AG を作成します。

   >[!IMPORTANT]
   >このアーキテクチャでは、3 番目のレプリカをホストする SQL Server の任意のエディションでできます。 たとえば、3 番目のレプリカは、SQL Server Enterprise Edition でホストできます。 Enterprise Edition では、唯一の有効なエンドポイントの種類は`WITNESS`します。 

   ```SQL
   CREATE AVAILABILITY GROUP [ag1] 
      WITH (CLUSTER_TYPE = EXTERNAL) 
      FOR REPLICA ON 
       N'<node1>' WITH ( 
          ENDPOINT_URL = N'tcp://<node1>:<5022>', 
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = EXTERNAL, 
          SEEDING_MODE = AUTOMATIC 
          ), 
       N'<node2>' WITH (  
          ENDPOINT_URL = N'tcp://<node2>:<5022>',  
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = EXTERNAL, 
          SEEDING_MODE = AUTOMATIC 
          ), 
       N'<node3>' WITH ( 
          ENDPOINT_URL = N'tcp://<node3>:<5022>', 
          AVAILABILITY_MODE = CONFIGURATION_ONLY  
          );
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```
<a name="readScale"></a>

- 2 つの同期レプリカでの AG を作成します。

   同期の可用性モードの 2 つのレプリカを含めます。 たとえば、次のスクリプトと呼ばれる、AG を作成します。`ag1`します。 `node1` `node2`自動シード処理と自動フェールオーバーで同期モードでのレプリカをホストします。

   >[!IMPORTANT]
   >のみと 2 つの同期レプリカを可用性グループを作成する次のスクリプトを実行します。 上記のいずれかのスクリプトを実行した場合、次のスクリプトは実行されません。 

   ```SQL
   CREATE AVAILABILITY GROUP [ag1]
      WITH (CLUSTER_TYPE = EXTERNAL)
      FOR REPLICA ON
      N'node1' WITH (
         ENDPOINT_URL = N'tcp://node1:5022',
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
         FAILOVER_MODE = EXTERNAL,
         SEEDING_MODE = AUTOMATIC
      ),
      N'node2' WITH ( 
         ENDPOINT_URL = N'tcp://node2:5022', 
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
         FAILOVER_MODE = EXTERNAL,
         SEEDING_MODE = AUTOMATIC
      );
        
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```


AG を構成することもできます。 `CLUSTER_TYPE=EXTERNAL` SQL Server Management Studio または PowerShell を使用します。 

### <a name="join-secondary-replicas-to-the-ag"></a>セカンダリ レプリカ、可用性グループへの参加します。

次の TRANSACT-SQL スクリプトでは、SQL Server インスタンスを結合という名前を AG に`ag1`します。 ご利用の環境に合わせてスクリプトを変更してください。 セカンダリ レプリカをホストする各 SQL Server インスタンスでは、可用性グループに参加する次の Transact SQL を実行します。

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

>[!IMPORTANT]
>可用性グループを作成した後は、Pacemaker などの高可用性のクラスター テクノロジと統合を構成する必要があります。 以降では、Ag を使用して読み取りスケール構成[!INCLUDE[SQL Server version](..\includes\sssqlv14-md.md)]クラスターのセットアップは必要ありません。

このドキュメントで手順を実行する場合、クラスター化されていない可用性グループがあります。 次の手順では、クラスターを追加します。 この構成が有効の読み取りスケール/負荷分散シナリオでは、高可用性の不完全な。 高可用性のためには、クラスター リソースとして、可用性グループを追加する必要があります。 参照してください[次のステップ](#next-steps)手順についてはします。 

## <a name="notes"></a>注

>[!IMPORTANT]
>クラスターを構成するクラスター リソースとして、可用性グループを追加したら、TRANSACT-SQL を使用して AG リソースをフェールオーバーすることはできません。 Linux 上の SQL Server クラスター リソースは関連付けられていませんに厳しく、オペレーティング システムは Windows Server フェールオーバー クラスター (WSFC) にします。 SQL Server サービスでは、クラスターの存在を認識しません。 すべてのオーケストレーションは、クラスターの管理ツールを使用して行われます。 RHEL または Ubuntu を使用して`pcs`します。 SLES で使用して`crm`します。 

>[!IMPORTANT]
>既知の問題が、可用性グループがクラスター リソースの場合は、非同期レプリカにデータ損失の強制フェールオーバーが機能しないという現在のリリースであります。 これは、今後のリリースで修正されます。 同期レプリカを手動または自動フェールオーバーは成功します。 


## <a name="next-steps"></a>次のステップ

[SQL Server 可用性グループのクラスター リソースの Red Hat Enterprise Linux クラスターを構成します。](sql-server-linux-availability-group-cluster-rhel.md)

[SQL Server 可用性グループのクラスター リソースの SUSE Linux Enterprise Server クラスターを構成します。](sql-server-linux-availability-group-cluster-sles.md)

[SQL Server 可用性グループのクラスター リソースの Ubuntu クラスターの構成します。](sql-server-linux-availability-group-cluster-ubuntu.md)
