---
title: "分散型可用性グループ (Always On 可用性グループ) | Microsoft Docs"
ms.custom: ""
ms.date: "08/30/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7c7acc5-a350-4a17-95e1-e689c78a0900
caps.latest.revision: 28
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 28
---
# 分散型可用性グループ (Always On 可用性グループ)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  分散型可用性グループを使用すると、異なる Windows Server Failover Clusters (WSFC) 上にある 2 つの可用性グループを関連付けることができます。 分散型可用性グループの主な用途の 1 つは、プライマリ サイトが DR サイトから地理的に離れている場合の災害復旧です。 データを DR サイトに引き続きレプリケートし、DR サイトのネットワークの問題や課題をプライマリ サイトに持ち込まないようにすることができます。  
  
 次の図は、分散型可用性グループのアーキテクチャを示しています。  
  
 ![AlwaysOn Distributed Availability Groups](../../../database-engine/availability-groups/windows/media/alwayson-distributed-availability-groups.png "AlwaysOn Distributed Availability Groups")  
  
 この図には、2 つの Windows Server Failover Clusters (WSFC 1 と WSFC 2) があります。 各クラスターには、データベースの構成に合わせた独自の可用性グループがあります。 分散型可用性グループは、"可用性グループの可用性グループ" と考えることができます。 この例では、AG 1 はプライマリ可用性グループになります。 挿入と更新はすべてプライマリ レプリカの AG 1 に対して行われてから、セカンダリ レプリカにレプリケートされます。 ただし、変更も、ネットワーク全体の WSFC 2 のセカンダリ可用性グループに 1 回レプリケートされます。 AG 2 可用性グループは、その変更をセカンダリ レプリカにレプリケートします。  
  
> [!IMPORTANT]  
>  2 つの可用性グループ間に分散型可用性グループのリレーションシップが確立すると、セカンダリ可用性グループが自動的に読み取り専用になります。 更新と挿入は、プライマリ可用性グループのプライマリ レプリカ (この例では、AG 1 のプライマリ レプリカ) に対してのみ行われます。  
  
 分散型可用性グループと、単一の Windows Server フェールオーバー クラスターの可用性グループは、次の点が異なります。  
  
-   各 WSFC は、独自のクォーラム モードとノード投票構成を保守しています。 つまり、セカンダリ WSFC の正常性はプライマリ WSFC に影響しません。  
  
-   データはネットワーク経由でセカンダリ WSFC に 1 回送信され、そのクラスター内でレプリケートされます。 単一の WSFC の場合、データは個別に各レプリカに送信されます。 地理的に分散しているセカンダリ サイトの場合、分散型可用性グループはより効率的です。  
  
-   プライマリ クラスターとセカンダリ クラスターには、異なるバージョンのオペレーティング システムを使用できます。 単一の WSFC では、すべてのサーバーが同じバージョンの OS 上にある必要があります。 そのため、分散型可用性グループを使用して、オペレーティング システムの更新/アップグレードを実行することができます。  
  
-   プライマリとセカンダリの可用性グループは、同じ構成のデータベースを持っている必要があります。  
  
-   セカンダリ可用性グループへの自動フェールオーバーはサポートされていません。  
  
## 分散型可用性グループを作成する  
 分散型可用性グループを作成するには、各 WSFC に可用性グループとリスナーを作成する必要があります。 次に、これらを分散型可用性グループに結合します。 次の手順は、Transact-SQL の基本的な例です。 この例では、可用性グループとリスナーを作成するすべての手順を取り上げていません。主な要件を強調することに重点を置いています。  
  
### 最初のクラスターにプライマリ可用性グループを作成する  
 最初の WSFC に可用性グループを作成します。   この例では、データベース `ag1` の `db1`という可用性グループです。  
  
```tsql  
CREATE AVAILABILITY GROUP [ag1]   
FOR DATABASE db1   
REPLICA ON N'server1' WITH (ENDPOINT_URL = N'TCP://server1.contoso.com:5022',  
    FAILOVER_MODE = AUTOMATIC,  
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server2' WITH (ENDPOINT_URL = N'TCP://server2.contoso.com:5022',   
    FAILOVER_MODE = AUTOMATIC,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
  
```  
  
 この例では、直接シード処理を使用しています。レプリカと分散型可用性グループの両方について、**SEEDING_MODE** は **AUTOMATIC** に設定されます。 つまり、確立後に、セカンダリ レプリカとセカンダリ可用性グループは自動的に設定されます。プライマリ データベースの手動バックアップと復元を実行する必要はありません。  
  
### セカンダリ レプリカをプライマリ可用性グループに追加する  
 **ALTER AVAILABILITY GROUP** に **JOIN** オプションを指定して、すべてのセカンダリ レプリカを可用性グループに追加する必要があります。 この例では直接シード処理を使用しているため、  **ALTER AVAILABILITY GROUP** に **GRANT CREATE ANY DATABASE** オプションを指定して呼び出す必要があります。 その結果、可用性グループでデータベースを作成し、プライマリ レプリカから自動的にシード処理を開始できるようになります。  
  
 この例では、セカンダリ レプリカ `server2`で次のコマンドが実行され、 `ag1` 可用性グループに追加されます。 この可用性グループは、セカンダリ上にデータベースを作成できるようになります。  
  
```tsql  
ALTER AVAILABILITY GROUP [ag1] JOIN   
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE  
GO  
```  
  
### プライマリ可用性グループのリスナーを作成する  
 次に、プライマリ可用性グループのリスナーを最初の WSFC に追加します。 この例では、 `ag1-listener`というリスナーです。 リスナーの詳細な作成手順については、「[可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)」を参照してください。  
  
```  
ALTER AVAILABILITY GROUP [ag1]    
    ADD LISTENER 'ag1-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
### 2 つ目のクラスターにセカンダリ可用性グループを作成する  
 2 つ目の WSFC に 2 つ目の可用性グループ `ag2`を作成します。 この場合、データベースはプライマリ可用性グループから自動的にシード処理されるため、データベースを指定しません。  
  
```tsql  
CREATE AVAILABILITY GROUP [ag2]   
FOR   
REPLICA ON N'server3' WITH (ENDPOINT_URL = N'TCP://server3.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC),   
N'server4' WITH (ENDPOINT_URL = N'TCP://server4.contoso.com:5022',   
    FAILOVER_MODE = MANUAL,   
    AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,   
    BACKUP_PRIORITY = 50,   
    SECONDARY_ROLE(ALLOW_CONNECTIONS = NO),   
    SEEDING_MODE = AUTOMATIC);   
GO  
```  
  
> [!NOTE]  
>  セカンダリ可用性グループは、同じデータベース ミラーリング エンドポイント (この例ではポート 5022) を使用する必要があります。 そうしないと、ローカルのフェールオーバー後にレプリケーションは停止します。  
  
### セカンダリ レプリカをセカンダリ可用性グループに追加する  
 この例では、セカンダリ レプリカ `server4`で次のコマンドが実行され、 `ag2` 可用性グループに追加されます。 この可用性グループは、直接シード処理をサポートするデータベースをセカンダリ上に作成できるようになります。  
  
```tsql  
ALTER AVAILABILITY GROUP [ag2] JOIN   
ALTER AVAILABILITY GROUP [ag2] GRANT CREATE ANY DATABASE  
GO  
```  
  
### セカンダリ可用性グループのリスナーを作成する  
 次に、セカンダリ可用性グループのリスナーを 2 つ目の WSFC に追加します。 この例では、 `ag2-listener`というリスナーです。 リスナーの詳細な作成手順については、「[可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)」を参照してください。  
  
```  
ALTER AVAILABILITY GROUP [ag2]    
    ADD LISTENER 'ag2-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
### 最初のクラスターに分散型可用性グループを作成する  
 最初の WSFC に分散型可用性グループ (この例では `distributedag`) を作成します。 **CREATE AVAILABILITY GROUP** コマンドに **DISTRIBUTED** オプションを指定して実行します。 **AVAILABILITY GROUP ON** パラメーターに、メンバー可用性グループの `ag1` と `ag2` を指定します。  
  
```tsql  
CREATE AVAILABILITY GROUP [distributedag]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO   
```  
  
> [!NOTE]  
>  **LISTENER_URL** で、各可用性グループのリスナーと、可用性グループのデータベース ミラーリング エンドポイントを指定します。 この例では、ポート `5022` です (リスナーの作成に使用したポート `60173` ではありません)。  
  
### 2 つ目のクラスターの分散型可用性グループに参加する  
 次に、2 つ目の WSFC の分散型可用性グループに参加します。  
  
```tsql  
ALTER AVAILABILITY GROUP [distributedag]   
   JOIN   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO  
```  

  
## セカンダリ可用性グループにフェールオーバーする  
 現在のところ、手動フェールオーバーのみがサポートされています。 次の Transact-SQL ステートメントは、`distributedag` という分散型可用性グループに対してフェールオーバーを強制します。  


1. セカンダリ可用性グループで、可用性モードを同期コミットに設定します。 
    
      ```tsql  
      ALTER AVAILABILITY GROUP [distributedag] 
      MODIFY 
      AVAILABILITY GROUP ON
      'ag1' WITH  
         ( 
          LISTENER_URL = 'tcp://ag1-listener:5022',  
          AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = MANUAL, 
          SEEDING_MODE = MANUAL 
          ), 
      'ag2' WITH  
        ( 
        LISTENER_URL = 'tcp://ag2-listener:5022', 
        AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
        FAILOVER_MODE = MANUAL, 
        SEEDING_MODE = MANUAL 
        );  
       
      ```  
  
1. 分散型可用性グループの状態が `SYNCHRONIZED` に変化するまで待機します。 プライマリ可用性グループのプライマリ レプリカをホストする SQL Server で、次のクエリを実行します。 
    
      ```tsql  
      SELECT ag.name
             , drs.database_id
             , drs.group_id
             , drs.replica_id
             , drs.synchronization_state_desc
             , drs.end_of_log_lsn 
        FROM sys.dm_hadr_database_replica_states drs,
        sys.availability_groups ag
          WHERE drs.group_id = ag.group_id;      
      ```  

    可用性グループ **synchronization_state_desc** が `SYNCHRONIZED` になってから先に進みます。 **synchronization_state_desc** が `SYNCHRONIZED` にならない場合は、その状態に変化するまで 5 秒間隔でコマンドを実行します。 **synchronization_state_desc** = `SYNCHRONIZED` の条件が満たされるまで、先に進まないでください。 

1. プライマリ可用性グループのプライマリ レプリカをホストする SQL Server で、分散型可用性グループのロールを `SECONDARY` に設定します。 

      ```tsql
      ALTER AVAILABILITY GROUP distributedag SET (ROLE = SECONDARY); 
      ```  

    注: この時点で、分散型可用性グループは使用できません。

1. フェールオーバーの準備をテストします。 次のクエリを実行します。

      ```tsql
      SELECT ag.name, 
             drs.database_id, 
             drs.group_id, 
             drs.replica_id, 
             drs.synchronization_state_desc, 
             drs.end_of_log_lsn 
      FROM sys.dm_hadr_database_replica_states drs, sys.availability_groups ag
      WHERE drs.group_id = ag.group_id; 
      ```  
    可用性グループは、**synchronization_state_desc** が `SYNCHRONIZED` であり、かつ、両方の可用性グループで **end_of_log_lsn** が同じである場合に、フェールオーバーできる状態となります。 

1. プライマリ可用性グループからセカンダリ可用性グループにフェールオーバーします。 セカンダリ可用性グループのプライマリ レプリカをホストする SQL Server で、次のコマンドを実行します。 

      ```tsql
      ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
      ```  
      注: この手順の後で、分散型可用性グループが使用できるようになります。
      
上記の手順が完了すると、データ損失なしで、分散型可用性グループのフェールオーバーが行われます。 Microsoft では、可用性グループ間の地理的な距離が遅延を引き起こす距離にある場合、可用性モードを ASYNCHRONOUS_COMMIT に戻すことをお勧めしています。 
  
## 分散型可用性グループを削除する  
 次の Transact-SQL ステートメントは、`distributedag` という分散型可用性グループを削除します。  
  
```tsql  
DROP AVAILABILITY GROUP [distributedag]  
```  

## フェールオーバー クラスター インスタンスを含む可用性グループの作成

フェールオーバー クラスター インスタンス (FCI) で可用性グループを使用して、分散可用性グループを作成することができます。 この場合、可用性グループ リスナーは必要ありません。 FCI インスタンスのプライマリ レプリカに対して仮想ネットワーク名 (VNN) を使用します。 次の例は、SQLFCIDAG と呼ばれる分散型可用性グループを示しています。 1 つの可用性グループは SQLFCIAG です。 SQLFCIAG には、2 つの FCI レプリカがあります。 プライマリ FCI レプリカの VNN は SQLFCIAG-1 であり、セカンダリ FCI レプリカの VNN は SQLFCIAG 2 です。 分散型可用性グループには、災害復旧のための SQLAG DR も含まれています。

![分散型の AlwaysOn 可用性グループ](../../../database-engine/availability-groups/windows/media/always-on-availability-group-distributed.png)

 
 
 次の DDL では、この分散可用性グループが作成されます。 

```tsql  
CREATE AVAILABILITY GROUP [SQLFCIDAG]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
  'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-1:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      ),   
  'SQLAG-DR' WITH    
       (   
         LISTENER_URL = 'tcp://SQLAG-DR:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      );   
```  

リスナーの URL は、プライマリ FCI インスタンスの VNN です。

## 分散型可用性グループで FCI を手動でフェールオーバーする

FCI 可用性グループを手動でフェールオーバーするには、分散型可用性グループを更新してリスナー URL の変更を反映します。 たとえば、SQLFCIAG のプライマリ AG とセカンダリ AG の両方で次の DDL を実行します。

```tsql  
ALTER AVAILABILITY GROUP [SQLFCIDAG]  
   MODIFY AVAILABILITY GROUP ON  
 'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-2:5022'
    )
```  
  
## 参照  
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  