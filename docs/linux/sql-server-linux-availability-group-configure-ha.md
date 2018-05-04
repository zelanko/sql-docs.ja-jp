---
title: 構成する SQL Server Always On 可用性グループ Linux での高可用性の |Microsoft ドキュメント
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
ms.openlocfilehash: 36b287251d91075b210737d869d52521f8f42b1e
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="configure-sql-server-always-on-availability-group-for-high-availability-on-linux"></a>構成する SQL Server Always On 可用性グループ Linux 上の高可用性

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

この記事では、Linux で、SQL Server 常に 可用性グループ (AG) 高可用性を作成する方法について説明します。 Ag の 2 つの構成の種類があります。 A*高可用性*構成では、クラスター マネージャーを使用して、ビジネス継続性を提供します。 この構成では、読み取りスケール レプリカを含めることもできます。 このドキュメントでは、高可用性のため、可用性グループを作成する方法について説明します。

作成することも、クラスターせず、AG のマネージャー*読み取りスケール*です。 のみ、読み取りのスケールの可用性グループは、パフォーマンスのスケール アウトの読み取り専用レプリカを提供します。高可用性は提供されません。 読み取りのスケールの可用性グループを作成するを参照してください。 [Linux 上の読み取りのスケールの SQL Server 可用性グループを構成する](sql-server-linux-availability-group-configure-rs.md)です。

高可用性とデータ保護を保証する構成では、2 または 3 つの同期コミット レプリカが必要です。 次の 3 つの同期レプリカで、可用性グループを 1 つのサーバーが利用できない場合でも自動的に回復できます。 詳細については、次を参照してください。[可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)です。 

物理または仮想、すべてのサーバーがある必要があり、仮想サーバーが同じ仮想化プラットフォーム上にある必要があります。 この要件は、フェンス操作エージェントがプラットフォーム固有であるためにです。 参照してください[ゲスト クラスターでポリシー](https://access.redhat.com/articles/29440#guest_policies)です。

## <a name="roadmap"></a>ロードマップ

高可用性の Linux サーバーで、可用性グループを作成する手順は、Windows Server フェールオーバー クラスター上の手順と異なります。 手順の概要を以下に説明します。  

1. [次の 3 つのクラスター サーバーで SQL Server を構成する](sql-server-linux-setup.md)です。

   >[!IMPORTANT]
   >AG の 3 つすべてのサーバーは、Linux の高可用性では、フェンス操作エージェントを使用して、サーバー上のリソースを特定するための物理または仮想の同じプラットフォーム上にある必要があります。 フェンス操作エージェントは、プラットフォームごとに固有です。

2. 可用性グループを作成します。 この手順は、現在この記事の内容について説明します。 

3. Pacemaker のように、クラスター リソース マネージャーを構成します。 
   
   クラスター リソース マネージャーを構成する方法は、特定の Linux ディストリビューションに依存します。 配布の具体的な手順については、次のリンクを参照してください。 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   * [SUSE](sql-server-linux-availability-group-cluster-sles.md)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   >[!IMPORTANT]
   >実稼働環境では、高可用性を実現 STONITH などのフェンス操作エージェントが必要です。 このドキュメントではデモンストレーションでは、フェンス操作エージェントは使用しないでください。 デモは、テストおよび検証のみです。 
   
   >Linux クラスターでは、フェンス操作を使用して、既知の状態をクラスターを返します。 フェンス操作を構成する方法は、分布と、環境によって異なります。 現時点では、フェンス操作では、一部のクラウド環境で使用できません。 詳細については、次を参照してください。 [RHEL 高可用性クラスターの仮想化プラットフォームのサポート ポリシー](https://access.redhat.com/articles/29440)です。
   
   >SLES を参照してください。 [SUSE Linux Enterprise 高可用性拡張子](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing)です。

5. クラスター内のリソースとして、可用性グループを追加します。  

   クラスター内のリソースとして、可用性グループを追加する方法は、Linux ディストリビューションに依存します。 配布の具体的な手順については、次のリンクを参照してください。 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)
   * [SLES](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)

[!INCLUDE [Create Prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-ag"></a>可用性グループを作成します。

により、自動フェールオーバーを高可用性構成には、可用性グループには、少なくとも 3 つのレプリカが必要です。 高可用性をサポートは次の構成のいずれかのことができます。

- [次の 3 つの同期レプリカ](sql-server-linux-availability-group-ha.md#threeSynch)

- [2 つの同期のレプリカと構成のレプリカ](sql-server-linux-availability-group-ha.md#twoSynch)

詳細については、次を参照してください。[可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)です。

>[!NOTE]
>可用性グループには、同期または非同期の追加のレプリカを含めることができます。 

Linux 上の高可用性のため、可用性グループを作成します。 使用して、[可用性グループの作成](https://docs.microsoft.com/en-us/sql/t-sql/statements/create-availability-group-transact-sql)で`CLUSTER_TYPE = EXTERNAL`です。 

* 可用性グループ -`CLUSTER_TYPE = EXTERNAL`外部クラスター エンティティが、可用性グループを管理することを指定します。 ペースでは、外部のクラスターのエンティティの例を示します。 可用性グループのクラスターの種類が、外部場合 

* プライマリ レプリカとセカンダリ レプリカを設定`FAILOVER_MODE = EXTERNAL`です。 
   レプリカが対話ペースのように、外部のクラスター マネージャーを指定します。 

次の TRANSACT-SQL スクリプトの作成という名前の可用性を高めるため、AG`ag1`です。 スクリプトは、構成、可用性グループ レプリカと`SEEDING_MODE = AUTOMATIC`です。 この設定は、各セカンダリ サーバーで、データベースを自動的に作成する SQL Server をによりします。 環境内の次のスクリプトを更新します。 置換、 `<node1>`、 `<node2>`、または`<node3>`レプリカをホストする SQL Server インスタンスの名前を持つ値です。 置換、`<5022>`データのミラーリング エンドポイントのポートを設定します。 可用性グループを作成するには、プライマリ レプリカをホストする SQL Server インスタンスで次の TRANSACT-SQL を実行します。

実行**1 つだけ**以下のスクリプト。 

- [次の 3 つの同期レプリカが可用性グループの作成](#threeSynch)です。
- [2 つの同期レプリカと構成のレプリカの可用性グループの作成](#configOnly)
- [2 つの同期レプリカが可用性グループを作成する](#readScale)です。

<a name="threeSynch"></a>

- 3 つの同期レプリカが可用性グループを作成します。

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
   >次の 3 つの同期レプリカで、可用性グループを作成する前のスクリプトを実行した後、次のスクリプトを実行しません。

- 2 つのレプリカを同期および構成のレプリカの可用性グループを作成します。

   >[!IMPORTANT]
   >このアーキテクチャにより、3 番目のレプリカをホストする SQL Server の任意のエディションです。 たとえば、SQL Server Enterprise Edition で 3 番目のレプリカをホストすることができます。 Enterprise Edition でのみ有効なエンドポイント タイプは`WITNESS`します。 

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

- 2 つの同期レプリカが可用性グループを作成します。

   同期の可用性モードの 2 つのレプリカが含まれます。 たとえば、次のスクリプトを作成と呼ばれる、AG`ag1`です。 `node1` および`node2`自動シード処理を自動フェールオーバーを伴うの同期モードでのレプリカをホストします。

   >[!IMPORTANT]
   >のみと 2 つの同期レプリカ、可用性グループを作成する次のスクリプトを実行します。 上記のスクリプトを実行した場合、次のスクリプトは実行されません。 

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


可用性グループを構成することもできます。 `CLUSTER_TYPE=EXTERNAL` SQL Server Management Studio または PowerShell を使用します。 

### <a name="join-secondary-replicas-to-the-ag"></a>セカンダリ レプリカ、可用性グループへの参加します。

次の TRANSACT-SQL スクリプトは、AG という名前に、SQL Server インスタンスを結合`ag1`です。 環境内で使用するスクリプトを更新します。 セカンダリ レプリカをホストする各 SQL Server インスタンスでは、可用性グループに参加する次の TRANSACT-SQL を実行します。

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

>[!IMPORTANT]
>可用性グループを作成した後は、高可用性のペースのようなクラスター テクノロジと統合を構成する必要があります。 以降で、Ag を使用して読み取りのスケール構成[!INCLUDE[SQL Server version](..\includes\sssqlv14-md.md)]クラスターのセットアップは必要ありません。

このドキュメントで手順を実行する場合は、クラスター化されていない可用性グループがあります。 次の手順では、クラスターを追加します。 この構成が読み取り-スケールまたは負荷分散シナリオで有効では高可用性のために完了しません。 高可用性のためには、クラスター リソースとして、可用性グループを追加する必要があります。 参照してください[次のステップ](#next-steps)手順についてはします。 

## <a name="notes"></a>注

>[!IMPORTANT]
>クラスターを構成し、クラスター リソースとして、可用性グループを追加した後は TRANSACT-SQL を使用して可用性グループ リソースをフェールオーバーすることはできません。 Linux 上の SQL Server クラスター リソースと関連していない緊密にオペレーティング システムで、Windows Server フェールオーバー クラスター (WSFC) とします。 SQL Server サービスでは、クラスターの存在を認識しません。 すべてのオーケストレーションは、クラスター管理ツールを使って行われます。 RHEL または Ubuntu を使用して`pcs`です。 SLES で使用して`crm`です。 

>[!IMPORTANT]
>既知の問題が、可用性グループがクラスター リソースの場合は、データ損失の非同期レプリカに強制フェールオーバーが機能しないという現在のリリースであります。 これは、今後のリリースで修正されます。 同期レプリカへの手動または自動フェールオーバーは成功します。 


## <a name="next-steps"></a>次の手順

[SQL Server 可用性グループのクラスター リソースの Red Hat Enterprise Linux クラスターを構成します。](sql-server-linux-availability-group-cluster-rhel.md)

[SQL Server 可用性グループのクラスター リソースの SUSE Linux Enterprise Server クラスターを構成します。](sql-server-linux-availability-group-cluster-sles.md)

[Ubuntu クラスターは、SQL Server 可用性グループのクラスター リソースを構成します。](sql-server-linux-availability-group-cluster-ubuntu.md)
