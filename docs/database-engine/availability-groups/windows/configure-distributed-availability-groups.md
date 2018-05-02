---
title: 分散型可用性グループを構成する (Always On 可用性グループ) |Microsoft Docs
ms.custom: ''
ms.date: 08/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: availability-groups
ms.reviewer: ''
ms.suite: sql
ms.technology: dbe-high-availability
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f7c7acc5-a350-4a17-95e1-e689c78a0900
caps.latest.revision: 28
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d39e9c1decf1f41c47b7dfc9e161996bfa9b9951
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="configure-distributed-availability-group"></a>分散型可用性グループを構成する  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

分散型可用性グループを作成するには、各 Windows Server フェールオーバー クラスター (WSFC) に可用性グループとリスナーを作成する必要があります。 次に、これらの可用性グループを分散型可用性グループに結合します。 次の手順は、Transact-SQL の基本的な例です。 この例では、可用性グループとリスナーを作成するすべての手順を取り上げていません。主な要件を強調することに重点を置いています。 

分散型可用性グループの技術の概要については、「[Distributed availability groups](distributed-availability-groups.md)」 (分散可用性グループ) を参照してください。   

## <a name="prerequisites"></a>Prerequisites

### <a name="set-the-endpoint-listeners-to-listen-to-all-ip-addresses"></a>エンドポイント リスナーがすべての IP アドレスをリッスンするよう設定する

分散型可用性グループで、エンドポイントが別の可用性グループとも通信できることを確認します。 エンドポイント上で 1 つの可用性グループが特定のネットワークに設定されている場合、分散型可用性グループは正しく機能しません。 分散型可用性グループ内のレプリカをホストする各サーバーで、リスナーを `LISTENER_IP = ALL` に構成します。 

#### <a name="create-a-listener-to-listen-to-all-ip-addresses"></a>リスナーがすべての IP アドレスをリッスンするようにする

たとえば、次のスクリプトで、TCP ポート 5022 上ですべての IP アドレスをリッスンするリスナー エンドポイントを作成します。  

```sql
CREATE ENDPOINT [aodns-hadr] 
    STATE=STARTED
    AS TCP (LISTENER_PORT = 5022, LISTENER_IP = ALL)
FOR DATA_MIRRORING (
   ROLE = ALL, 
   AUTHENTICATION = WINDOWS NEGOTIATE,
   ENCRYPTION = REQUIRED ALGORITHM AES
)
GO
```

#### <a name="alter-a-listener-to-listen-to-all-ip-addresses"></a>すべての IP アドレスをリッスンするようリスナーを変更する

たとえば、次のスクリプトで、すべての IP アドレスをリッスンするようリスナー エンドポイントを変更します。  

```sql
ALTER ENDPOINT [aodns-hadr] 
    AS TCP (LISTENER_IP = ALL)
GO
```

## <a name="create-first-availability-group"></a>最初の可用性グループを作成する

### <a name="create-the-primary-availability-group-on-the-first-cluster"></a>最初のクラスターにプライマリ可用性グループを作成する  
最初の WSFC に可用性グループを作成します。   この例では、データベース `ag1` の `db1`という可用性グループです。      
  
```sql  
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
  
>[!NOTE]
>上記の例では、直接シード処理を使用しています。レプリカと分散型可用性グループの両方について、**SEEDING_MODE** は **AUTOMATIC** に設定されます。 この構成では、確立後に、セカンダリ レプリカとセカンダリ可用性グループは自動的に設定されます。プライマリ データベースの手動バックアップと復元を実行する必要はありません。  
  
### <a name="join-the-secondary-replicas-to-the-primary-availability-group"></a>セカンダリ レプリカをプライマリ可用性グループに追加する  
**ALTER AVAILABILITY GROUP** に **JOIN** オプションを指定して、すべてのセカンダリ レプリカを可用性グループに追加する必要があります。 この例では直接シード処理を使用しているため、  **ALTER AVAILABILITY GROUP** に **GRANT CREATE ANY DATABASE** オプションを指定して呼び出す必要があります。 この設定では、可用性グループでデータベースを作成し、プライマリ レプリカから自動的にシード処理を開始できるようになります。  
  
この例では、セカンダリ レプリカ `server2`で次のコマンドが実行され、 `ag1` 可用性グループに追加されます。 この可用性グループは、セカンダリ上にデータベースを作成できるようになります。  
  
```sql  
ALTER AVAILABILITY GROUP [ag1] JOIN   
ALTER AVAILABILITY GROUP [ag1] GRANT CREATE ANY DATABASE  
GO  
```  

>[!NOTE]
>可用性グループがセカンダリ レプリカにデータベースを作成すると、`ALTER AVAILABILITY GROUP` ステートメントを実行したアカウントとしてデータベース所有者が設定され、任意のデータベースを作成するアクセス許可が付与されます。 詳細については、「[セカンダリ レプリカの CREATE DATABASE アクセス許可を可用性グループに付与する](automatic-seeding-secondary-replicas.md#grantCreate)」を参照してください。
  
### <a name="create-a-listener-for-the-primary-availability-group"></a>プライマリ可用性グループのリスナーを作成する  

次に、プライマリ可用性グループのリスナーを最初の WSFC に追加します。 この例では、 `ag1-listener`というリスナーです。 リスナーの詳細な作成手順については、「[可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)」を参照してください。  
  
```sql
ALTER AVAILABILITY GROUP [ag1]    
    ADD LISTENER 'ag1-listener' ( 
        WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , 
        PORT = 60173);    
GO  
```  
  

## <a name="create-second-availability-group"></a>2 つ目の可用性グループを作成する  
 2 つ目の WSFC に 2 つ目の可用性グループ `ag2`を作成します。 この場合、データベースはプライマリ可用性グループから自動的にシード処理されるため、データベースを指定しません。  
  
```sql  
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
> セカンダリ可用性グループは、同じデータベース ミラーリング エンドポイント (この例ではポート 5022) を使用する必要があります。 そうしないと、ローカルのフェールオーバー後にレプリケーションは停止します。  
  
### <a name="join-the-secondary-replicas-to-the-secondary-availability-group"></a>セカンダリ レプリカをセカンダリ可用性グループに追加する  
 この例では、セカンダリ レプリカ `server4`で次のコマンドが実行され、 `ag2` 可用性グループに追加されます。 この可用性グループは、直接シード処理をサポートするデータベースをセカンダリ上に作成できるようになります。  
  
```sql  
ALTER AVAILABILITY GROUP [ag2] JOIN   
ALTER AVAILABILITY GROUP [ag2] GRANT CREATE ANY DATABASE  
GO  
```  
  
### <a name="create-a-listener-for--the-secondary-availability-group"></a>セカンダリ可用性グループのリスナーを作成する  
 次に、セカンダリ可用性グループのリスナーを 2 つ目の WSFC に追加します。 この例では、 `ag2-listener`というリスナーです。 リスナーの詳細な作成手順については、「[可用性グループ リスナーの作成または構成 &#40;SQL Server&#41;](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)」を参照してください。  
  
```  
ALTER AVAILABILITY GROUP [ag2]    
    ADD LISTENER 'ag2-listener' ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173);    
GO  
```  
  
## <a name="create-distributed-availability-group-on-first-cluster"></a>最初のクラスターに分散型可用性グループを作成する  
 最初の WSFC に分散型可用性グループ (この例では `distributedag` ) を作成します。 **CREATE AVAILABILITY GROUP** コマンドに **DISTRIBUTED** オプションを指定して実行します。 **AVAILABILITY GROUP ON** パラメーターに、メンバー可用性グループの `ag1` と `ag2` を指定します。  
  
```sql  
CREATE AVAILABILITY GROUP [distributedag]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO   
```  
  
> [!NOTE]  
>  **LISTENER_URL** で、各可用性グループのリスナーと、可用性グループのデータベース ミラーリング エンドポイントを指定します。 この例では、ポート `5022` です (リスナーの作成に使用したポート `60173` ではありません)。 Azure でインスタンスにロード バランサーを使用している場合、[分散型可用性グループのポートの負荷分散の規則を追加します](http://docs.microsoft.com/azure/virtual-machines/windows/sql/virtual-machines-windows-portal-sql-alwayson-int-listener#add-load-balancing-rule-for-distributed-availability-group)。 SQL Server インスタンスのポートだけでなく、リスナー ポートの規則を追加します。 
  
## <a name="join-distributed-availability-group-on-second-cluster"></a>2 つ目のクラスターの分散型可用性グループに参加する  
 次に、2 つ目の WSFC の分散型可用性グループに参加します。  
  
```sql  
ALTER AVAILABILITY GROUP [distributedag]   
   JOIN   
   AVAILABILITY GROUP ON  
      'ag1' WITH    
      (   
         LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      ),   
      'ag2' WITH    
      (   
         LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC   
      );    
GO  
```  

## <a name="failover"></a> 2 つ目の可用性グループのセカンダリ上のデータベースを結合する
2 つ目の可用性グループのセカンダリ上のデータベースが復元状態になったら、それを可用性グループに手動で結合する必要があります。

```sql  
ALTER DATABASE [db1] SET HADR AVAILABILITY GROUP = [ag2];   
```  
  
## <a name="failover"></a> セカンダリ可用性グループにフェールオーバーする  
現在のところ、手動フェールオーバーのみがサポートされています。 次の Transact-SQL ステートメントは、`distributedag` という分散型可用性グループでフェールオーバーします。  


1. 両方の可用性グループに対して、可用性モードを同期コミットに設定します。 
    
      ```sql  
      ALTER AVAILABILITY GROUP [distributedag] 
      MODIFY 
      AVAILABILITY GROUP ON
      'ag1' WITH 
         ( 
          LISTENER_URL = 'tcp://ag1-listener.contoso.com:5022',  
          AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
          FAILOVER_MODE = MANUAL, 
          SEEDING_MODE = MANUAL 
          ), 
      'ag2' WITH  
        ( 
        LISTENER_URL = 'tcp://ag2-listener.contoso.com:5022', 
        AVAILABILITY_MODE = SYNCHRONOUS_COMMIT, 
        FAILOVER_MODE = MANUAL, 
        SEEDING_MODE = MANUAL 
        );  
       
      ```  
   >[!NOTE]
   >標準の可用性グループと同様に、分散型可用性グループの 2 つの可用性グループのレプリカ部分の同期状態は、両方のレプリカの可用性モードによって異なります。 たとえば、同期コミットを発生させるには、現在のプライマリ可用性グループとセカンダリ可用性グループの両方が、synchronous_commit 可用性モードで構成されている必要があります。  


1. 分散型可用性グループの状態が `SYNCHRONIZED`に変化するまで待機します。 プライマリ可用性グループのプライマリ レプリカをホストする SQL Server で、次のクエリを実行します。 
    
      ```sql  
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

    可用性グループ **synchronization_state_desc** が `SYNCHRONIZED`になってから先に進みます。 **synchronization_state_desc** が `SYNCHRONIZED`にならない場合は、その状態に変化するまで 5 秒間隔でコマンドを実行します。 **synchronization_state_desc** = `SYNCHRONIZED`の条件が満たされるまで、先に進まないでください。 

1. プライマリ可用性グループのプライマリ レプリカをホストする SQL Server で、分散型可用性グループのロールを `SECONDARY` に設定します。 

    ```sql
    ALTER AVAILABILITY GROUP distributedag SET (ROLE = SECONDARY); 
    ```  

    この時点で、分散型可用性グループは使用できません。

1. フェールオーバーの準備をテストします。 次のクエリを実行します。

    ```sql
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

    ```sql
    ALTER AVAILABILITY GROUP distributedag FORCE_FAILOVER_ALLOW_DATA_LOSS; 
    ```  

    この手順の後で、分散型可用性グループが使用できるようになります。
      
上記の手順が完了すると、データ損失なしで、分散型可用性グループのフェールオーバーが行われます。 可用性グループ間の地理的な距離が遅延を引き起こす距離にある場合、可用性モードを ASYNCHRONOUS_COMMIT に変更してください。 
  
## <a name="remove-a-distributed-availability-group"></a>分散型可用性グループを削除する  
 次の Transact-SQL ステートメントは、 `distributedag`という分散型可用性グループを削除します。  
  
```sql  
DROP AVAILABILITY GROUP [distributedag]  
```  

## <a name="create-distributed-availability-group-on-failover-cluster-instances"></a>フェールオーバー クラスター インスタンスに分散可用性グループを作成する

フェールオーバー クラスター インスタンス (FCI) で可用性グループを使用して、分散可用性グループを作成することができます。 この場合、可用性グループ リスナーは必要ありません。 FCI インスタンスのプライマリ レプリカに対して仮想ネットワーク名 (VNN) を使用します。 次の例は、SQLFCIDAG と呼ばれる分散型可用性グループを示しています。 1 つの可用性グループは SQLFCIAG です。 SQLFCIAG には、2 つの FCI レプリカがあります。 プライマリ FCI レプリカの VNN は SQLFCIAG-1 であり、セカンダリ FCI レプリカの VNN は SQLFCIAG 2 です。 分散型可用性グループには、ディザスター リカバリーのための SQLAG DR も含まれています。

![分散型の AlwaysOn 可用性グループ](../../../database-engine/availability-groups/windows/media/always-on-availability-group-distributed.png)

 
 
 次の DDL では、この分散可用性グループが作成されます。 

```sql  
CREATE AVAILABILITY GROUP [SQLFCIDAG]  
   WITH (DISTRIBUTED)   
   AVAILABILITY GROUP ON  
  'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-1.contoso.com:5022',    
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      ),   
  'SQLAG-DR' WITH    
       (   
         LISTENER_URL = 'tcp://SQLAG-DR.contoso.com:5022',   
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,   
         FAILOVER_MODE = MANUAL,   
         SEEDING_MODE = AUTOMATIC
      );   
```  

リスナーの URL は、プライマリ FCI インスタンスの VNN です。

## <a name="manually-fail-over-fci-in-distributed-availability-group"></a>分散型可用性グループで FCI を手動でフェールオーバーする

FCI 可用性グループを手動でフェールオーバーするには、分散型可用性グループを更新してリスナー URL の変更を反映します。 たとえば、SQLFCIAG のプライマリ AG とセカンダリ AG の両方で次の DDL を実行します。

```sql  
ALTER AVAILABILITY GROUP [SQLFCIDAG]  
   MODIFY AVAILABILITY GROUP ON  
 'SQLFCIAG' WITH    
    (   
        LISTENER_URL = 'tcp://SQLFCIAG-2.contoso.com:5022'
    )
```  
  
## <a name="next-steps"></a>次の手順

 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../../t-sql/statements/alter-availability-group-transact-sql.md)  
  
  
