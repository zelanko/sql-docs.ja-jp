---
title: "Linux 上の SQL Server の可用性グループの構成 |Microsoft ドキュメント"
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
ms.assetid: 
ms.workload: On Demand
ms.openlocfilehash: e75ae9a6f3c48f0ece0c95be9f3836c8205a1b8c
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="configure-always-on-availability-group-for-sql-server-on-linux"></a>Linux 上の SQL Server の Always On 可用性グループを構成します。

[!INCLUDE[tsql-appliesto-sslinux-only](../includes/tsql-appliesto-sslinux-only.md)]

この記事では、Linux 上の高可用性の可用性グループに SQL サーバーを常に作成する方法について説明します。 可用性グループの 2 つの構成の種類があります。 A*高可用性*構成では、クラスター マネージャーを使用して、ビジネス継続性を提供します。 この構成では、読み取りスケール レプリカを含めることもできます。 このドキュメントでは、可用性グループの高可用性構成を作成する方法について説明します。

作成することも、*読み取りスケール*クラスター マネージャーがない可用性グループです。 のみ、この構成は、パフォーマンスのスケール アウトの読み取り専用レプリカを提供します。高可用性は提供されません。 読み取りのスケールの可用性グループを作成するを参照してください。 [Linux に SQL Server の読み取りスケール可用性グループを構成する](sql-server-linux-availability-group-configure-rs.md)です。

高可用性とデータ保護を保証する構成では、2 または 3 つの同期コミット レプリカが必要です。 次の 3 つの同期レプリカ、可用性グループが自動的に回復場合でも、1 つのサーバーは使用できません。 詳細については、次を参照してください。[可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)です。 

物理または仮想、すべてのサーバーがある必要があり、仮想サーバーが同じ仮想化プラットフォーム上にある必要があります。 この要件は、フェンス操作エージェントがプラットフォーム固有であるためにです。 参照してください[ゲスト クラスターでポリシー](https://access.redhat.com/articles/29440#guest_policies)です。

## <a name="roadmap"></a>ロードマップ

高可用性の Linux サーバーに可用性グループを作成する手順は、Windows Server フェールオーバー クラスター上の手順と異なります。 次に、高レベルの手順を説明します。 

1. [次の 3 つのクラスター サーバーで SQL Server を構成する](sql-server-linux-setup.md)です。

   >[!IMPORTANT]
   >可用性グループ内のすべての 3 つのサーバーは、Linux の高可用性では、フェンス操作エージェントを使用して、サーバー上のリソースを特定するための物理または仮想の同じプラットフォーム上にある必要があります。 フェンス操作エージェントは、プラットフォームごとに固有です。

2. 可用性グループを作成します。 この手順は、現在この記事の内容について説明します。 

3. ペースのように、クラスター リソース マネージャーを構成します。
   
   クラスター リソース マネージャーを構成する方法は、特定の Linux ディストリビューションに依存します。 配布の具体的な手順については、次のリンクを参照してください。 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md)
   * [SUSE](sql-server-linux-availability-group-cluster-sles.md)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md)

   >[!IMPORTANT]
   >実稼働環境では、高可用性を実現 STONITH などのフェンス操作エージェントが必要です。 このドキュメントではデモンストレーションでは、フェンス操作エージェントは使用しないでください。 デモは、テストおよび検証のみです。 
   
   >Linux クラスターでは、フェンス操作を使用して、既知の状態をクラスターを返します。 フェンス操作を構成する方法は、分布と、環境によって異なります。 現時点では、フェンス操作では、一部のクラウド環境で使用できません。 詳細については、次を参照してください。 [RHEL 高可用性クラスターの仮想化プラットフォームのサポート ポリシー](https://access.redhat.com/articles/29440)です。
   
   >SLES を参照してください。 [SUSE Linux Enterprise 高可用性拡張子](https://www.suse.com/documentation/sle-ha-12/singlehtml/book_sleha/book_sleha.html#cha.ha.fencing)です。

5. クラスター内のリソースとして、可用性グループを追加します。  

   可用性グループ、クラスター内のリソースとして追加するための方法は、Linux ディストリビューションに依存します。 配布の具体的な手順については、次のリンクを参照してください。 

   * [RHEL](sql-server-linux-availability-group-cluster-rhel.md#create-availability-group-resource)
   * [SLES](sql-server-linux-availability-group-cluster-sles.md#configure-the-cluster-resources-for-sql-server)
   * [Ubuntu](sql-server-linux-availability-group-cluster-ubuntu.md#create-availability-group-resource)

[!INCLUDE [Create Prerequisites](../includes/ss-linux-cluster-availability-group-create-prereq.md)]

## <a name="create-the-availability-group"></a>可用性グループを作成します。

SQL Server on Linux の 2 つのサポートされている可用性グループの構成があります。

- [次の 3 つの同期レプリカ](sql-server-linux-availability-group-ha.md#threeSynch)

- [2 つの同期レプリカ](sql-server-linux-availability-group-ha.md#twoSynch)

詳細については、次を参照してください。[可用性グループの構成の高可用性とデータ保護](sql-server-linux-availability-group-ha.md)です。

Linux 上の高可用性の可用性グループを作成します。 使用して、[可用性グループの作成](https://docs.microsoft.com/en-us/sql/t-sql/statements/create-availability-group-transact-sql)で`CLUSTER_TYPE = EXTERNAL`です。 

* 可用性グループ -`CLUSTER_TYPE = EXTERNAL`外部クラスター エンティティが、可用性グループを管理することを指定します。 ペースでは、外部のクラスターのエンティティの例を示します。 可用性グループのクラスターの種類が外部の場合 

* プライマリ レプリカとセカンダリ レプリカを設定`FAILOVER_MODE = EXTERNAL`です。 
   レプリカが対話ペースのように、外部のクラスター マネージャーを指定します。 

次の TRANSACT-SQL スクリプトという名前の高可用性の可用性グループを作成する`ag1`です。 スクリプトは、構成、可用性グループ レプリカと`SEEDING_MODE = AUTOMATIC`です。 この設定は、各セカンダリ サーバーで、データベースを自動的に作成する SQL Server をによりします。 環境内の次のスクリプトを更新します。 置換、 `**<node1>**`、 `**<node2>**`、または`**<node3>**`レプリカをホストする SQL Server インスタンスの名前を持つ値です。 置換、`**<5022>**`データのミラーリング エンドポイントのポートを設定します。 可用性グループを作成するには、プライマリ レプリカをホストする SQL Server インスタンスで次の TRANSACT-SQL を実行します。

実行**1 つだけ**以下のスクリプト。 

- [次の 3 つの同期レプリカが可用性グループの作成](#threeSynch)です。
- [2 つの同期レプリカと構成のレプリカの可用性グループを作成します。](#configOnly)
- [2 つの同期レプリカが可用性グループの作成](#readScale)です。

<a name="threeSynch"></a>

- 次の 3 つの同期レプリカが可用性グループを作成します。

   ```SQL
   CREATE AVAILABILITY GROUP [ag1]
       WITH (DB_FAILOVER = ON, CLUSTER_TYPE = EXTERNAL)
       FOR REPLICA ON
           N'**<node1>**' 
            WITH (
               ENDPOINT_URL = N'tcp://**<node1>:**<5022>**',
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'**<node2>**' 
            WITH ( 
               ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**', 
               AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
               FAILOVER_MODE = EXTERNAL,
               SEEDING_MODE = AUTOMATIC
               ),
           N'**<node3>**'
           WITH( 
              ENDPOINT_URL = N'tcp://**<node3>**:**<5022>**', 
              AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,
              FAILOVER_MODE = EXTERNAL,
              SEEDING_MODE = AUTOMATIC
              );
        
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```

   >[!IMPORTANT]
   >次の 3 つの同期レプリカが可用性グループを作成する前のスクリプトを実行した後、次のスクリプトを実行しません。

- 2 つの同期レプリカと構成のレプリカの可用性グループを作成します。

   >[!IMPORTANT]
   >このアーキテクチャにより、3 番目のレプリカをホストする SQL Server の任意のエディションです。 たとえば、SQL Server Enterprise Edition で 3 番目のレプリカをホストすることができます。 Enterprise Edition でのみ有効なエンドポイント タイプは`WITNESS`します。 

   ```SQL
   CREATE AVAILABILITY GROUP [ag1] 
      WITH (CLUSTER_TYPE = EXTERNAL) 
      FOR REPLICA ON 
       N'**<node1>**' WITH ( 
          ENDPOINT_URL = N'tcp://**<node1>**:**<5022>**', 
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = EXTERNAL, 
          SEEDING_MODE = AUTOMATIC 
          ), 
       N'**<node2>**' WITH (  
          ENDPOINT_URL = N'tcp://**<node2>**:**<5022>**',  
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = EXTERNAL, 
          SEEDING_MODE = AUTOMATIC 
          ), 
       N'**<node3>**' WITH ( 
          ENDPOINT_URL = N'tcp://**<node3>**:**<5022>**', 
          AVAILABILITY_MODE = CONFIGURATION_ONLY  
          );
   ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
   ```
<a name="readScale"></a>

- 2 つの同期レプリカが可用性グループを作成します。

   同期の可用性モードの 2 つのレプリカが含まれます。 次のスクリプトがという可用性グループを作成するなど、`ag1`です。 `node1`および`node2`自動シード処理を自動フェールオーバーを伴うの同期モードでのレプリカをホストします。

   >[!IMPORTANT]
   >のみと 2 つの同期レプリカの可用性グループを作成する次のスクリプトを実行します。 上記のスクリプトを実行した場合、次のスクリプトは実行されません。 

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


持つ可用性グループを構成することもできます。 `CLUSTER_TYPE=EXTERNAL` SQL Server Management Studio または PowerShell を使用します。 

### <a name="join-secondary-replicas-to-the-availability-group"></a>可用性グループにセカンダリ レプリカを参加します。

次の TRANSACT-SQL スクリプトは、という名前の可用性グループに SQL Server インスタンスを結合`ag1`です。 環境内で使用するスクリプトを更新します。 セカンダリ レプリカをホストする各 SQL Server インスタンスでは、可用性グループに参加する次の TRANSACT-SQL を実行します。

```Transact-SQL
ALTER AVAILABILITY GROUP [ag1] JOIN WITH (CLUSTER_TYPE = EXTERNAL);
         
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE;
```

[!INCLUDE [Create Post](../includes/ss-linux-cluster-availability-group-create-post.md)]

>[!IMPORTANT]
>可用性グループを作成した後は、高可用性のペースのようなクラスター テクノロジを統合を構成する必要があります。 以降で、可用性グループを使用して読み取りのスケール構成[!INCLUDE[SQL Server version](..\includes\sssqlv14-md.md)]クラスターのセットアップは必要ありません。

このドキュメントで手順を実行する場合は、クラスター化されていない可用性グループがあります。 次の手順では、クラスターを追加します。 この構成が読み取り-スケールまたは負荷分散シナリオで有効では高可用性のために完了しません。 高可用性を実現するには、可用性グループをクラスター リソースとして追加する必要があります。 参照してください[次のステップ](#next-steps)手順についてはします。 

## <a name="notes"></a>注

>[!IMPORTANT]
>クラスターを構成し、可用性グループをクラスター リソースとして追加した後は TRANSACT-SQL を使用して、可用性グループのリソースをフェールオーバーすることはできません。 Linux 上の SQL Server クラスター リソースと関連していない緊密にオペレーティング システムで、Windows Server フェールオーバー クラスター (WSFC) とします。 SQL Server サービスでは、クラスターの存在を認識しません。 すべてのオーケストレーションは、クラスター管理ツールを使って行われます。 RHEL または Ubuntu を使用して`pcs`です。 SLES で使用して`crm`です。 

>[!IMPORTANT]
>既知の問題が、可用性グループがクラスター リソースの場合は、データ損失の非同期レプリカに強制フェールオーバーが機能しないという現在のリリースであります。 これは、今後のリリースで修正されます。 同期レプリカへの手動または自動フェールオーバーは成功します。 


## <a name="next-steps"></a>次の手順

[SQL Server 可用性グループのクラスター リソースの Red Hat Enterprise Linux クラスターを構成します。](sql-server-linux-availability-group-cluster-rhel.md)

[SQL Server 可用性グループのクラスター リソースの SUSE Linux Enterprise Server クラスターを構成します。](sql-server-linux-availability-group-cluster-sles.md)

[Ubuntu クラスターは、SQL Server 可用性グループのクラスター リソースを構成します。](sql-server-linux-availability-group-cluster-ubuntu.md)
