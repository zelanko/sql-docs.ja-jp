---
title: "ALTER AVAILABILITY GROUP (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_AVAILABILITY_GROUP_TSQL
- ALTER_AVAILABILITY_TSQL
- ALTER AVAILABILITY GROUP
- ALTER AVAILABILITY
dev_langs:
- TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- ALTER AVAILABILITY GROUP statement
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: f039d0de-ade7-4aaf-8b7b-d207deb3371a
caps.latest.revision: 152
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ef1d68317c2e288a13d7b07d559b5de45e29cd28
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-availability-group-transact-sql"></a>ALTER AVAILABILITY GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  既存 Always On 可用性グループを変更に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 ALTER AVAILABILITY GROUP のほとんどの引数は、現在のプライマリ レプリカでのみサポートされます。 ただし、JOIN、FAILOVER、FORCE_FAILOVER_ALLOW_DATA_LOSS の各引数は、セカンダリ レプリカでのみサポートされます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER AVAILABILITY GROUP group_name   
  {  
     SET ( <set_option_spec> )   
   | ADD DATABASE database_name   
   | REMOVE DATABASE database_name  
   | ADD REPLICA ON <add_replica_spec>   
   | MODIFY REPLICA ON <modify_replica_spec>  
   | REMOVE REPLICA ON <server_instance>  
   | JOIN  
   | JOIN AVAILABILITY GROUP ON <add_availability_group_spec> [ ,...2 ]  
   | MODIFY AVAILABILITY GROUP ON <modify_availability_group_spec> [ ,...2 ]  
   | GRANT CREATE ANY DATABASE  
   | DENY CREATE ANY DATABASE  
   | FAILOVER  
   | FORCE_FAILOVER_ALLOW_DATA_LOSS   | ADD LISTENER ‘dns_name’ ( <add_listener_option> )  
   | MODIFY LISTENER ‘dns_name’ ( <modify_listener_option> )  
   | RESTART LISTENER ‘dns_name’  
   | REMOVE LISTENER ‘dns_name’  
   | OFFLINE  
  }  
[ ; ]  
  
<set_option_spec> ::=   
    AUTOMATED_BACKUP_PREFERENCE = { PRIMARY | SECONDARY_ONLY| SECONDARY | NONE }  
  | FAILURE_CONDITION_LEVEL  = { 1 | 2 | 3 | 4 | 5 }   
  | HEALTH_CHECK_TIMEOUT = milliseconds  
  | DB_FAILOVER  = { ON | OFF }   
  | REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = { integer }
  
<server_instance> ::=   
 { 'system_name[\instance_name]' | 'FCI_network_name[\instance_name]' }  
  
<add_replica_spec>::=  
  <server_instance> WITH  
    (  
       ENDPOINT_URL = 'TCP://system-address:port',  
       AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT },  
       FAILOVER_MODE = { AUTOMATIC | MANUAL }   
       [ , <add_replica_option> [ ,...n ] ]  
    )   
  
  <add_replica_option>::=  
       SEEDING_MODE = { AUTOMATIC | MANUAL }   
     | BACKUP_PRIORITY = n  
     | SECONDARY_ROLE ( {   
          ALLOW_CONNECTIONS = { NO | READ_ONLY | ALL }   
        | READ_ONLY_ROUTING_URL = 'TCP://system-address:port'   
          } )  
     | PRIMARY_ROLE ( {   
          ALLOW_CONNECTIONS = { READ_WRITE | ALL }   
        | READ_ONLY_ROUTING_LIST = { ( ‘<server_instance>’ [ ,...n ] ) | NONE }   
          } )  
     | SESSION_TIMEOUT = seconds  
  
<modify_replica_spec>::=  
  <server_instance> WITH  
    (    
       ENDPOINT_URL = 'TCP://system-address:port'   
     | AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }   
     | FAILOVER_MODE = { AUTOMATIC | MANUAL }   
     | SEEDING_MODE = { AUTOMATIC | MANUAL }   
     | BACKUP_PRIORITY = n  
     | SECONDARY_ROLE ( {   
          ALLOW_CONNECTIONS = { NO | READ_ONLY | ALL }   
        | READ_ONLY_ROUTING_URL = 'TCP://system-address:port'   
          } )  
     | PRIMARY_ROLE ( {   
          ALLOW_CONNECTIONS = { READ_WRITE | ALL }   
        | READ_ONLY_ROUTING_LIST = { ( ‘<server_instance>’ [ ,...n ] ) | NONE }   
          } )  
     | SESSION_TIMEOUT = seconds  
    )   
  
<add_availability_group_spec>::=  
 <ag_name> WITH  
    (  
       LISTENER_URL = 'TCP://system-address:port',  
       AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT },  
       FAILOVER_MODE = MANUAL,  
       SEEDING_MODE = { AUTOMATIC | MANUAL }  
    )  
  
<modify_availability_group_spec>::=  
 <ag_name> WITH  
    (  
       LISTENER = 'TCP://system-address:port'  
       | AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }  
       | SEEDING_MODE = { AUTOMATIC | MANUAL }  
    )  
  
<add_listener_option> ::=  
   {  
      WITH DHCP [ ON ( <network_subnet_option> ) ]  
    | WITH IP ( { ( <ip_address_option> ) } [ , ...n ] ) [ , PORT = listener_port ]  
   }  
  
  <network_subnet_option> ::=  
     ‘four_part_ipv4_address’, ‘four_part_ipv4_mask’    
  
  <ip_address_option> ::=  
     {   
        ‘four_part_ipv4_address’, ‘four_part_ipv4_mask’  
      | ‘ipv6_address’  
     }  
  
<modify_listener_option>::=  
    {  
       ADD IP ( <ip_address_option> )   
     | PORT = listener_port  
    }  
  
```  
  
## <a name="arguments"></a>引数  
 *group_name*  
 新しい可用性グループの名前を指定します。 *group_name*は有効な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子、およびその必要がありますで一意である WSFC クラスター内のすべての可用性グループです。  
  
 AUTOMATED_BACKUP_PREFERENCE  **=**  {プライマリ |SECONDARY_ONLY |セカンダリ |[なし]}  
 バックアップを実行する場所を選択するときにバックアップ ジョブがプライマリ レプリカを評価する方法についての優先設定を指定します。 自動バックアップの優先設定を考慮して、特定のバックアップ ジョブのスクリプトを作成できます。 優先順位がによって適用されませんを理解することが重要[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ので、アドホック バックアップに影響を与えません。  
  
 プライマリ レプリカでのみサポートされます。  
  
 値は次のとおりです。  
  
 PRIMARY  
 バックアップを常にプライマリ レプリカで実行することを指定します。 このオプションは、差分バックアップの作成など、バックアップがセカンダリ レプリカで実行されたときにはサポートされないバックアップ機能が必要な場合に役に立ちます。  
  
> [!IMPORTANT]  
>  ログ配布を使用して可用性グループのセカンダリ データベースを準備する場合は、すべてのセカンダリ データベースの準備が完了し、それらを可用性グループに参加させるまで、自動バックアップ設定を **[プライマリ]** に設定します。  
  
 SECONDARY_ONLY  
 バックアップをプライマリ レプリカでは実行しないことを指定します。 オンラインのレプリカがプライマリ レプリカだけの場合、バックアップは実行されません。  
  
 SECONDARY  
 オンラインのレプリカがプライマリ レプリカのみである場合を除き、セカンダリ レプリカでバックアップを実行することを指定します。 オンラインのレプリカがプライマリ レプリカのみである場合は、プライマリ レプリカでバックアップを実行する必要があります。 これは既定の動作です。  
  
 なし  
 バックアップを実行するレプリカを選択するときにバックアップ ジョブが可用性レプリカのロールを無視するように指定します。 バックアップ ジョブは、動作状態および接続状態と組み合わせて、各可用性レプリカのバックアップ優先順位などの他の要素を評価する場合があります。  
  
> [!IMPORTANT]  
>  AUTOMATED_BACKUP_PREFERENCE 設定の適用はありません。 この優先設定の解釈は、特定の可用性グループのデータベースに対するバックアップ ジョブのスクリプトでのロジックに依存します (ある場合)。 自動バックアップ設定はアドホック バックアップには影響しません。 詳細については、次を参照してください[可用性レプリカ &#40; バックアップの構成。SQL Server &#41;](../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md).  
  
> [!NOTE]  
>  既存の可用性グループの自動バックアップ設定を表示するには、選択、 **automated_backup_preference**または**automated_backup_preference_desc**の列、 [sys.availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)カタログ ビューです。 さらに、 [sys.fn_hadr_backup_is_preferred_replica & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql.md)優先されるバックアップ レプリカを決定するために使用できます。  この関数は常に少なくとも 1 つのレプリカの 1 を返す場合でも、`AUTOMATED_BACKUP_PREFERENCE = NONE`です。  
  
 FAILURE_CONDITION_LEVEL  **=**  {1 | 2 |**3** | 4 | 5}  
 この可用性グループの自動フェールオーバーをトリガーするエラー状態を指定します。 FAILURE_CONDITION_LEVEL はグループ レベルで設定されていますが、同期コミット可用性モードが構成されている可用性レプリカにのみ (AVAILIBILITY_MODE  **=**  SYNCHRONOUS_COMMIT)。 さらに、エラー状態が自動フェールオーバーをトリガー プライマリとセカンダリの両方のレプリカが自動フェールオーバー モードで構成されている場合にのみ (FAILOVER_MODE  **=** 自動) セカンダリ レプリカが、現在プライマリ レプリカと同期されています。  
  
 プライマリ レプリカでのみサポートされます。  
  
 エラー状態レベルの範囲は 1 ～ 5 で、レベル 1 が最も制限が緩く、レベル 5 が最も制限の厳しい指定です。 特定の条件レベルには、すべての制限の緩いレベルが含まれます。 したがって、最も厳しい状態レベル 5 にはそれより制限が緩い状態レベル (1 ～ 4) が含まれ、レベル 4 にはレベル 1 ～ 3 が含まれます。以下同様です。 次の表では、各レベルに対応するエラー状態について説明します。  
  
|レベル|エラー状態|  
|-----------|-----------------------|  
|1|次のいずれかが発生した場合に自動フェールオーバーを開始する必要があることを指定します。<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サービスがダウンした。<br /><br /> WSFC クラスターに接続するための可用性グループのリースが、サーバー インスタンスから ACK を受信しないために期限切れになった。 詳細については、「 [動作方法: SQL Server Always On のリース タイムアウト](http://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-Always%20On-lease-timeout.aspx)」を参照してください。|  
|2|次のいずれかが発生した場合に自動フェールオーバーを開始する必要があることを指定します。<br /><br /> インスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クラスターに接続しません。 可用性グループのユーザー指定の HEALTH_CHECK_TIMEOUT しきい値を超えました。<br /><br /> 可用性レプリカがエラー状態である。|  
|3|重要なので、自動フェールオーバーを開始することを指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]孤立したスピンロック、深刻な書き込みアクセス違反、ダンプが多すぎるなどの内部エラーが発生します。<br /><br /> これは既定の動作です。|  
|4|度が中程度、自動フェールオーバーを開始することを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で永続的なメモリ不足の状態などの内部エラーが発生、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内部リソース プールです。|  
|5|以下のような任意の修飾エラー状態に対して自動フェールオーバーを開始する必要があることを指定します。<br /><br /> SQL エンジンのワーカー スレッドが枯渇している。<br /><br /> 解決不可能なデッドロックが検出された。|  
  
> [!NOTE]  
>  インスタンスが応答しないこと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントに要求が可用性グループに関連します。  
  
 FAILURE_CONDITION_LEVEL および HEALTH_CHECK_TIMEOUT の値を定義して、*柔軟なフェールオーバー ポリシー*特定のグループです。 この柔軟なフェールオーバー ポリシーを使用すると、自動フェールオーバーを実行する条件をきめ細かく制御できます。 詳細については、次を参照してください[自動フェールオーバー、可用性グループ &#40; のための柔軟なフェールオーバー ポリシー。SQL Server &#41;](../../database-engine/availability-groups/windows/flexible-automatic-failover-policy-availability-group.md).  
  
 HEALTH_CHECK_TIMEOUT  **=**  *(ミリ秒)*  
 待機時間 (ミリ秒単位) を指定します、 [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md)システム ストアド プロシージャによってサーバーの状態の情報を返す前に、WSFC クラスターでは、サーバー インスタンスが速度低下またはハングがある前提としています。 HEALTH_CHECK_TIMEOUT はグループ レベルで設定されていますが、自動フェールオーバーを伴う同期コミット可用性モードが構成されている可用性レプリカにのみ (AVAILIBILITY_MODE  **=** 同期_COMMIT)。  さらに、正常性チェックのタイムアウトが自動フェールオーバーをトリガー プライマリとセカンダリの両方のレプリカが自動フェールオーバー モードで構成されている場合にのみ (FAILOVER_MODE  **=** 自動) とセカンダリレプリカがプライマリ レプリカと現在同期されています。  
  
 HEALTH_CHECK_TIMEOUT の既定値は 30000 ミリ秒 (30 秒) です。 最小値は 15000 ミリ秒 (15 秒)、最大値は 4294967295 ミリ秒です。  
  
 プライマリ レプリカでのみサポートされます。  
  
> [!IMPORTANT]  
>  **sp_server_diagnostics** では、データベース レベルでの正常性チェックは実行されません。  
  
 DB_FAILOVER  **=**  {ON |オフ}  
 プライマリ レプリカでのデータベースがオフラインのときに実行する応答を指定します。 ON に設定すると、可用性グループ内のデータベースのオンライン以外のすべての状態は、自動フェールオーバーをトリガーします。 このオプションが OFF に設定されている場合は、インスタンスのヘルスだけが自動フェールオーバーをトリガーに使用されます。  
 
 この設定に関する詳細については、次を参照してください[データベース レベルの正常性の検出のオプション。](../../database-engine/availability-groups/windows/sql-server-always-on-database-health-detection-failover-option.md) 

 
 REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT   
 SQL Server 2017 CTP 2.2 で導入されました。 プライマリ トランザクションをコミットする前にコミットするために必要なの同期セカンダリ レプリカの最小数を設定するために使用します。 SQL Server のトランザクションがトランザクション ログがセカンダリ レプリカの最小数で更新されるまでに待機することを保証します。 既定では 0 で、SQL Server 2016 と同じ動作を示します。 最小値は 0 です。 最大値は、レプリカから 1 を引いた数です。 このオプションは、同期コミット モードのレプリカに関連しています。 レプリカは、同期コミット モードでは、ときに、プライマリ レプリカでの書き込みは同期セカンダリ レプリカ上の書き込みはレプリカ データベースのトランザクション ログにコミットされるまでを待ちます。 同期セカンダリ レプリカをホストする SQL Server が応答しなくなった場合、プライマリ レプリカをホストする SQL Server は同期されていないと続行そのセカンダリ レプリカをマークします。 応答しない状態のデータベースがオンラインに戻ったときに「同期されていません」状態になるし、プライマリとなる同期再度までにそのレプリカが異常とマークされてです。 この設定により、レプリカの最小数は、各トランザクションをコミット済みになるまで、プライマリ レプリカは続行されません。 レプリカの最小数が使用できない場合は、プライマリ上のコミットは失敗します。 この設定は、クラスターの種類の可用性グループに適用されます。`WSFC`と`EXTERNAL`です。 クラスターの種類の`EXTERNAL`をクラスター リソースに追加されると、可用性グループの設定を変更します。 参照してください[可用性グループの構成の高可用性とデータ保護](../../linux/sql-server-linux-availability-group-ha.md)です。
  
 データベースの追加*database_name*  
 可用性グループに追加する 1 つ以上のユーザー データベースのリストを指定します。 これらのデータベースは、現在のプライマリ レプリカをホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス上にある必要があります。 1 つの可用性グループに対して複数のデータベースを指定できますが、各データベースが所属できる可用性グループは 1 つだけです。 可用性グループでサポートされるデータベースの種類については、次を参照してください[前提条件、制限事項、および Always On 可用性グループ &#40; ための推奨事項。SQL Server &#41;](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md). ローカル データベースが可用性グループに属しているを参照してください、 **replica_id**内の列、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)カタログ ビューです。  
  
 プライマリ レプリカでのみサポートされます。  
  
> [!NOTE]  
>  可用性グループを作成した後、セカンダリ レプリカをホストする各サーバー インスタンスに接続して、各セカンダリ データベースを準備し、可用性グループに参加させる必要があります。 詳細については、「 [AlwaysOn セカンダリ データベース上のデータ移動の開始 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/start-data-movement-on-an-always-on-secondary-database-sql-server.md)」を参照してください。  
  
 データベースの削除*database_name*  
 指定したプライマリ データベースと、対応するセカンダリ データベースを可用性グループから削除します。 プライマリ レプリカでのみサポートされます。  
  
 について推奨するフォロー アップの可用性グループから可用性データベースを削除した後は、次を参照してください[プライマリ データベースの可用性グループ &#40; から削除。SQL Server &#41;](../../database-engine/availability-groups/windows/remove-a-primary-database-from-an-availability-group-sql-server.md).  
  
 ADD REPLICA ON  
 可用性グループのセカンダリ レプリカをホストする 1 ～ 8 個の SQL Server インスタンスを指定します。  各レプリカを指定する際には、サーバー インスタンスのアドレスに続けて WITH (...) 句を入力します。  
  
 プライマリ レプリカでのみサポートされます。  
  
 すべての新しいセカンダリ レプリカを可用性グループに参加させる必要があります。 詳細については、後述する JOIN オプションの説明を参照してください。  
  
 \<server_instance >  
 インスタンスのアドレス指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリカのホストであります。 アドレスの形式は、インスタンスが既定のインスタンスか名前付きインスタンスか、およびスタンドアロン インスタンスかフェールオーバー クラスター インスタンス (FCI) かによって異なります。 構文は次のとおりです。  
  
 { '*system_name*[\\*instance_name*]' | '*FCI_network_name*[\\*instance_name*]' }  
  
 このアドレスの構成要素は次のとおりです。  
  
 *system_name*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のターゲット インスタンスが存在するコンピューター システムの NetBIOS 名です。 このコンピューターは WSFC ノードである必要があります。  
  
 *FCI_network_name*  
 使用されるネットワーク名にアクセスする、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フェイル オーバー クラスター。 サーバー インスタンスが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー パートナーとして参加している場合に使用します。 選択を実行する[@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) FCI では、サーバー インスタンスはその全体を返します '*FCI_network_name*[\\*instance_name*]' 文字列 (これは、。完全なレプリカ名)。  
  
 *instance_name*  
 インスタンスの名前を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によってホストされている*system_name*または*FCI_network_name*常に有効になっているとします。 既定のサーバー インスタンスの場合、 *instance_name* は省略可能です。 インスタンス名では大文字と小文字が区別されません。 この値の名前では、スタンドアロン サーバー インスタンスでは SELECT を実行することによって返される値と同じ[@@SERVERNAME](../../t-sql/functions/servername-transact-sql.md)です。  
  
 \  
 指定する場合にのみを使用する区切り記号は、 *instance_name*から区別するために、 *system_name*または*FCI_network_name*です。  
  
 WSFC ノードとサーバー インスタンスの前提条件については、次を参照してください[前提条件、制限事項、および Always On 可用性グループ &#40; ための推奨事項。SQL Server &#41;](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
 ENDPOINT_URL ='TCP://*システム アドレス*:*ポート*'  
 URL パスを指定します、[データベース ミラーリング エンドポイント](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)のインスタンスで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を追加または変更する可用性レプリカをホストします。  
  
 ENDPOINT_URL は、ADD REPLICA ON 句では必須で、MODIFY REPLICA ON 句では省略可能です。  詳細については、「 [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)の構成に関する一般的な問題のトラブルシューティングに役立つ情報を提供します。  
  
 **'**TCP**://***システム アドレス***:***ポート***'**  
 エンドポイントの URL または読み取り専用のルーティングの URL を指定するための URL を指定します。 URL のパラメーターは次のとおりです。  
  
 *system-address*  
 システム名、完全修飾ドメイン名では、対象のコンピューター システムを明確に識別する、IP アドレスなどの文字列です。  
  
 *port*  
 サーバー インスタンスのミラーリング エンドポイントと関連付けられているポート番号 (ENDPOINT_URL オプションの場合)、またはサーバー インスタンスの [!INCLUDE[ssDE](../../includes/ssde-md.md)]によって使用されるポート番号 (READ_ONLY_ROUTING_URL オプションの場合) です。  
  
 AVAILABILITY_MODE  **=**  {SYNCHRONOUS_COMMIT |ASYNCHRONOUS_COMMIT}  
 プライマリ レプリカが特定のプライマリ データベースでトランザクションをコミットする前に、セカンダリ レプリカによるディスクへのログ レコードの固定 (書き込み) の確認応答を待機する必要があるかどうかを指定します。 同じプライマリ レプリカに対する異なるデータベースでのトランザクションは個別にコミットできます。  
  
 SYNCHRONOUS_COMMIT  
 このセカンダリ レプリカでトランザクションが書き込まれるまで、プライマリ レプリカがトランザクションのコミットを待機することを指定します (同期コミット モード)。 SYNCHRONOUS_COMMIT は、プライマリ レプリカを含む最大 3 つのレプリカに対して指定できます。  
  
 ASYNCHRONOUS_COMMIT  
 このセカンダリ レプリカでログが書き込まれるのを待たずに、プライマリ レプリカがトランザクションをコミットすることを指定します (同期コミット可用性モード)。 ASYNCHRONOUS_COMMIT は、プライマリ レプリカを含む最大 5 つの可用性レプリカに対して指定できます。  
  
 AVAILABILITY_MODE は、ADD REPLICA ON 句では必須で、MODIFY REPLICA ON 句では省略可能です。 詳細については、「 [可用性モード &#40;AlwaysOn 可用性グループ&#41;](../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md)、または PowerShell を使用して、AlwaysOn 可用性グループ上で計画的な手動フェールオーバーまたは強制手動フェールオーバー (強制フェールオーバー) を実行する方法について説明します。  
  
 FAILOVER_MODE  **=**  {自動 |手動}  
 定義している可用性レプリカのフェールオーバー モードを指定します。  
  
 AUTOMATIC  
 自動フェールオーバーを有効にします。 AUTOMATIC は、AVAILABILITY_MODE = SYNCHRONOUS_COMMIT も指定した場合にのみサポートされます。 AUTOMATIC は、プライマリ レプリカを含む 2 つの可用性レプリカに対して指定できます。  
  
> [!NOTE]  
>  SQL Server フェールオーバー クラスター インスタンス (FCI) は可用性グループによる自動フェールオーバーをサポートしないため、FCI によってホストされる可用性レプリカは手動フェールオーバー用にのみ構成できます。  
  
 MANUAL  
 手動フェールオーバーまたは強制手動フェールオーバーを有効に (*強制フェールオーバー*)、データベース管理者です。  
  
 FAILOVER_MODE は、ADD REPLICA ON 句では必須で、MODIFY REPLICA ON 句では省略可能です。 手動フェールオーバーにはデータ損失のない手動フェールオーバーと強制フェールオーバー (データ損失の可能性あり) の 2 種類があり、異なる条件の下でサポートされます。  詳細については、「 [フェールオーバーとフェールオーバー モード &#40;AlwaysOn 可用性グループ&#41;](../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)、または PowerShell を使用して、AlwaysOn 可用性グループ上で計画的な手動フェールオーバーまたは強制手動フェールオーバー (強制フェールオーバー) を実行する方法について説明します。  
  
 SEEDING_MODE  **=**  {自動 |手動}  
 どのセカンダリ レプリカが最初にシード処理されるように指定します。  
  
 AUTOMATIC  
 直接シード処理を有効にします。 このメソッドは、ネットワーク経由でセカンダリ レプリカをシードします。 このメソッドは、バックアップし、レプリカのプライマリ データベースのコピーを復元することにも必要ありません。  
  
> [!NOTE]  
>  直接シード処理を行う必要がありますに許可するデータベースの作成各セカンダリ レプリカで呼び出すことによって**ALTER AVAILABILITY GROUP**で、 **GRANT CREATE ANY DATABASE**オプション。  
  
 MANUAL  
 手動によるシード (既定値) を指定します。 このメソッドでは、プライマリ レプリカで、データベースのバックアップを作成し、セカンダリ レプリカでバックアップを手動で復元する必要があります。  
  
 BACKUP_PRIORITY**=***n*  
 同じ可用性グループ内の他のレプリカと比較して、このレプリカでバックアップを実行する優先順位を指定します。 値は 0 ～ 100 の範囲の整数です。 これらの値には次の意味があります。  
  
-   1 ～ 100 は、その可用性レプリカがバックアップの実行に対して選択される可能性があることを示します。 1 は最も低い優先順位を示し、100 は最も高い優先順位を示します。 たとえば、BACKUP_PRIORITY = 1 の場合、現在使用可能な可用性レプリカにそれより高い優先順位のものがない場合にのみ、その可用性レプリカがバックアップの実行に対して選択されます。  
  
-   0 は、その可用性レプリカがバックアップの実行に対して選択されないことを示します。 これは、たとえば、バックアップをフェールオーバーすることがないリモート可用性レプリカのような場合に便利です。  
  
 詳細については、「[アクティブなセカンダリ: セカンダリ レプリカでのバックアップ &#40;AlwaysOn 可用性グループ&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)」を参照してください。  
  
 SECONDARY_ROLE **(** . **)**  
 この可用性レプリカが現在セカンダリ ロールを所有している場合に (つまり、セカンダリ レプリカである場合は常に) 有効であるロール固有の設定を指定します。 かっこの中では、いずれか一方または両方のセカンダリ ロール オプションを指定します。 両方を指定する場合は、コンマ区切りのリストを使用します。  
  
 セカンダリ ロール オプションは次のとおりです。  
  
 ALLOW_CONNECTIONS  **=**  {なし |READ_ONLY |すべて}  
 セカンダリ ロールを実行している (つまりセカンダリ レプリカとして機能している) 特定の可用性レプリカのデータベースがクライアントから接続を受け入れることができるかどうかを指定します。以下のいずれかになります。  
  
 いいえ  
 このレプリカのセカンダリ データベースに対するユーザー接続は禁止されます。 読み取りアクセスで利用することはできません。 これは既定の動作です。  
  
 READ_ONLY  
 Application Intent プロパティに設定されているセカンダリ レプリカのデータベースに対する接続のみが許可**ReadOnly**です。 このプロパティの詳細については、「 [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。  
  
 ALL  
 読み取り専用アクセスに限り、セカンダリ レプリカのデータベースに対するすべての接続が許可されます。  
  
 詳細については、「[アクティブなセカンダリ: 読み取り可能なセカンダリ レプリカ &#40;Always On 可用性グループ&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)」を参照してください。  
  
 READ_ONLY_ROUTING_URL **='**TCP**://***システム アドレス***:***ポート***'**  
 読み取りを目的とした接続要求をこの可用性レプリカにルーティングするために使用する URL を指定します。 これは、SQL Server データベース エンジンがリッスンしている URL です。 通常、SQL Server データベース エンジンの既定のインスタンスは、TCP ポート 1433 でリッスンします。  
  
 名前付きインスタンスの場合は、クエリを実行してポート番号を取得できます、**ポート**と**type_desc**の列、 [sys.dm_tcp_listener_states](../../relational-databases/system-dynamic-management-views/sys-dm-tcp-listener-states-transact-sql.md)動的管理ビュー。 サーバー インスタンスは TRANSACT-SQL リスナーを使用 (**type_desc ="TSQL"**)。  
  
 可用性レプリカの読み取り専用ルーティング URL の計算の詳細については、次を参照してください。 [Alwayson の read_only_routing_url の計算](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-Always%20On.aspx)です。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前付きインスタンスの場合は、特定のポートを使用するように Transact-SQL リスナーを構成する必要があります。 詳細については、「[特定の TCP ポートで受信待ちするようにサーバーを構成する方法 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md)」を参照してください。  
  
 PRIMARY_ROLE **(** . **)**  
 この可用性レプリカが現在プライマリ ロールを所有している場合に (つまり、プライマリ レプリカである場合は常に) 有効であるロール固有の設定を指定します。 かっこの中では、いずれか一方または両方のプライマリ ロール オプションを指定します。 両方を指定する場合は、コンマ区切りのリストを使用します。  
  
 プライマリ ロール オプションは次のとおりです。  
  
 ALLOW_CONNECTIONS  **=**  {READ_WRITE |すべて}  
 プライマリ ロールを実行している (つまりプライマリ レプリカとして機能している) 特定の可用性レプリカのデータベースが受け入れることのできるクライアントからの接続の種類を指定します。以下のいずれかになります。  
  
 READ_WRITE  
 Application Intent 接続プロパティが **ReadOnly** に設定されている接続は許可されません。  Application Intent プロパティが **ReadWrite** に設定されている場合、または Application Intent 接続プロパティが設定されていない場合は、接続が許可されます。 "アプリケーションの目的" 接続プロパティの詳細については、「 [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。  
  
 ALL  
 プライマリ レプリカのデータベースに対するすべての接続が許可されます。 これは既定の動作です。  
  
 READ_ONLY_ROUTING_LIST  **=**  { **('**\<server_instance >**'** [ **、**.*n* ] **)** |[なし]}  
 セカンダリ ロールの下で実行するときに次の要件を満たす、この可用性グループの可用性レプリカをホストするサーバー インスタンスのコンマ区切りリストを指定します。  
  
-   すべての接続または読み取り専用の接続を許可するように構成されていること (前に示した SECONDARY_ROLE オプションの ALLOW_CONNECTIONS 引数を参照)。  
  
-   読み取り専用ルーティングの URL が定義されていること (前に示した SECONDARY_ROLE オプションの READ_ONLY_ROUTING_URL 引数を参照)。  
  
 READ_ONLY_ROUTING_LIST の値は次のとおりです。  
  
 \<server_instance >  
 セカンダリ ロールで実行するときに読み取り可能なセカンダリ レプリカである可用性レプリカをホストする [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのアドレスを指定します。  
  
 読み取り可能なセカンダリ レプリカをホストする可能性があるすべてのサーバー インスタンスを指定するには、コンマ区切りのリストを使用します。 読み取り専用のルーティングは、リストで指定されているサーバー インスタンスの順序に従います。 一覧の最後に、このサーバー インスタンスを配置することで、レプリカの読み取り専用ルーティング リスト、レプリカのホスト サーバーのインスタンスを含める場合は通常、お勧め、1 つは、使用可能な場合に、読み取りを目的とした接続がセカンダリ レプリカに移動できるようにします。  
  
 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]、読み取り可能なセカンダリ レプリカの間で読み取りを目的とした要求の負荷を分散することができます。 これは、読み取り専用ルーティング リスト内のかっこの入れ子になったセットで、レプリカを配置することで指定します。 詳細と例については、次を参照してください。[読み取り専用レプリカ間の負荷分散の構成](../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md#loadbalancing)です。  
  
 なし  
 この可用性レプリカがプライマリ レプリカの場合は、読み取り専用のルーティングをサポートしないことを指定します。 これは既定の動作です。 MODIFY REPLICA ON と併せて使用すると、この値は既存のリスト (ある場合) を無効にします。  
  
 SESSION_TIMEOUT  **=**  *(秒)*  
 セッション タイムアウト期間を秒単位で指定します。 このオプションを指定しない場合、この時間は既定で 10 秒に設定されます。 最小値は 5 秒です。  
  
> [!IMPORTANT]  
>  タイムアウト期間を 10 秒以上にしておくことをお勧めします。  
  
 セッション タイムアウト期間の詳細については、次を参照してください[概要の Always On 可用性グループ &#40;。SQL Server &#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
 MODIFY REPLICA ON  
 可用性グループの任意のレプリカを変更します。 変更対象のレプリカの一覧には、サーバー インスタンスのアドレスと、各レプリカに対する WITH (…) 句が含まれます。  
  
 プライマリ レプリカでのみサポートされます。  
  
 REMOVE REPLICA ON  
 指定したセカンダリ レプリカを可用性グループから削除します。 現在のプライマリ レプリカを可用性グループから削除することはできません。 削除されたレプリカは、データの受信を停止します。 セカンダリ データベースが可用性グループから削除され、RESTORING 状態に移行します。  
  
 プライマリ レプリカでのみサポートされます。  
  
> [!NOTE]  
>  使用不可中または障害発生中のレプリカを削除した場合、オンラインに戻ったレプリカは、可用性グループに属していないことを検出します。  
  
 JOIN  
 ローカル サーバー インスタンスは指定した可用性グループ内のセカンダリ レプリカをホストするようになります。  
  
 可用性グループにまだ参加していないセカンダリ レプリカでのみサポートされます。  
  
 詳細については、「 [可用性グループへのセカンダリ レプリカの参加 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/join-a-secondary-replica-to-an-availability-group-sql-server.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。  
  
 FAILOVER  
 接続されているセカンダリ レプリカへの可用性グループのデータ損失のない手動フェールオーバーを開始します。 レプリカのフェールオーバー ターゲット フェールオーバー コマンドを使用すると、入力と呼ばれる、します。  フェールオーバー ターゲットは、プライマリ ロールを引き継ぎ、各データベースのコピーを復旧し、新しいプライマリ データベースとしてオンラインにします。 元のプライマリ レプリカは同時にセカンダリ ロールに移行し、そのデータベースがセカンダリ データベースになって、直ちに中断されます。 これらのロールは、連続する障害によって繰り返し切り替えられる可能性があります。  
  
 現在プライマリ レプリカと同期されている同期コミット モードのセカンダリ レプリカでのみサポートされます。 セカンダリ レプリカを同期する場合、プライマリ レプリカも同期コミット可用性モードで実行している必要があります。  
  
> [!NOTE]  
>  フェールオーバー コマンドは、フェールオーバー ターゲットがコマンドを受け入れた直後に戻ります。 ただし、データベースの復旧は、可用性グループがフェールオーバーを完了した後に非同期で行われます。  
  
 制限事項については、前提条件と計画された手動フェールオーバーを実行するための推奨事項を参照してください[計画的な手動フェールオーバーの実行、可用性グループ & #40 です。SQL Server &#41;](../../database-engine/availability-groups/windows/perform-a-planned-manual-failover-of-an-availability-group-sql-server.md).  
  
 FORCE_FAILOVER_ALLOW_DATA_LOSS  
 > [!CAUTION]  
>  データの損失を伴う可能性があるフェールオーバーの強制は、厳密にはディザスター リカバリー手段です。 したがって、プライマリ レプリカが動作しなくなった状況で、データの損失を許容でき、可用性グループに直ちにサービスを復元する必要がある場合のみ、強制フェールオーバーを実行することを強くお勧めします。  
  
 ロールが SECONDARY 状態または RESOLVING 状態であるレプリカでのみサポートされます。 フェールオーバー コマンドを入力する--レプリカと呼ばれる、*フェールオーバー ターゲット*です。  
  
 フェールオーバー ターゲットへの可用性グループのフェールオーバーを強制します (データ損失の可能性あり)。 フェールオーバー ターゲットは、プライマリ ロールを引き継ぎ、各データベースのコピーを復旧し、新しいプライマリ データベースとしてオンラインにします。 残りのセカンダリ レプリカのすべてのセカンダリ データベースは手動で再開するまで中断されます。 元のプライマリ レプリカが使用可能になった場合はセカンダリ ロールに切り替わり、そのデータベースは中断されたセカンダリ データベースになります。  
  
> [!NOTE]  
>  フェールオーバー コマンドは、フェールオーバー ターゲットがコマンドを受け入れた直後に戻ります。 ただし、データベースの復旧は、可用性グループがフェールオーバーを完了した後に非同期で行われます。  
  
 制限事項については、前提条件と、可用性グループで、元のプライマリ データベースにフェールオーバーと強制フェールオーバーの影響を強制するための推奨事項を参照してください[可用性の強制手動フェールオーバーを実行します。グループ & #40 です。SQL Server &#41;](../../database-engine/availability-groups/windows/perform-a-forced-manual-failover-of-an-availability-group-sql-server.md).  
  
 ADD LISTENER **'***dns_name***' (** \<add_listener_option > **)**  
 この可用性グループの新しい可用性グループ リスナーを定義します。 プライマリ レプリカでのみサポートされます。  
  
> [!IMPORTANT]  
>  初めてリスナーを作成する前に強くお勧めお読みになる[作成または構成する可用性グループ リスナーと #40 です。SQL Server &#41;](../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md).  
>   
>  可用性グループのリスナーを作成した後は、次のことを行うことを強くお勧めします。  
>   
>  -   リスナーの IP アドレスが排他的に使用されるように確保することを、ネットワーク管理者に依頼します。  
> -   この可用性グループへのクライアント接続を要求するときの接続文字列で使用できるよう、リスナーの DNS ホスト名をアプリケーション開発者に通知します。  
  
 *dns_name*  
 可用性グループ リスナーの DNS ホスト名を指定します。 リスナーの DNS 名が、ドメインおよび NetBIOS 内で一意であることが必要です。  
  
 *dns_name*文字列値です。 この名前には、英数字、ダッシュ (-)、およびハイフン (_) のみを任意の順序で含めることができます。 DNS ホスト名では大文字と小文字は区別されません。 最大長は 63 文字です。  
  
 意味のある文字列を指定することをお勧めします。 たとえば、可用性グループの名前が `AG1`の場合は、 `ag1-listener`のような意味のある DNS ホスト名にします。  
  
> [!IMPORTANT]  
>  NetBIOS では、dns_name の最初の 15 文字のみが認識されます。 同じ Active Directory で制御されている 2 つの WSFC クラスターがあり、両方のクラスターで可用性グループ リスナーを作成しようとする場合、15 文字より長い名前を使用して、15 文字のプレフィックスが同一であると、仮想ネットワーク名リソースをオンラインにできなかったことを示すエラーが表示されます。 DNS 名のプレフィックスに対する名前付け規則の詳細については、「 [ドメイン名を割り当てる](http://technet.microsoft.com/library/cc731265\(WS.10\).aspx)」を参照してください。  
  
 上の可用性グループの追加  
 結合、*分散型可用性グループ*です。 分散型可用性グループを作成するときに、クラスターが作成される場所で、可用性グループ、プライマリ可用性グループです。 分散型可用性グループに参加させる可用性グループは、セカンダリ可用性グループです。  
  
 \<ag_name >  
 いずれかを構成する可用性グループの名前を指定、分散型可用性グループの半分です。  
  
 リスナー **='**TCP**://***システム アドレス***:***ポート***'**  
 可用性グループに関連付けられているリスナーの URL パスを指定します。  
  
 リスナー句が必要です。  
  
 **'**TCP**://***システム アドレス***:***ポート***'**  
 可用性グループに関連付けられているリスナーの URL を指定します。 URL のパラメーターは次のとおりです。  
  
 *system-address*  
 システム名、完全修飾ドメイン名、IP アドレス、リスナーを明確に識別するなどの文字列です。  
  
 *port*  
 可用性グループのデータベース ミラーリング エンドポイントに関連付けられているポート番号です。 リスナーのポートではないことに注意してください。  
  
 AVAILABILITY_MODE  **=**  {SYNCHRONOUS_COMMIT |ASYNCHRONOUS_COMMIT}  
 プライマリ レプリカがセカンダリ可用性グループ プライマリ レプリカは、特定のプライマリ データベースでトランザクションをコミットできる前にディスクにログ レコードの固定 (書き込み) を確認するを待っているかどうかを指定します。  
  
 SYNCHRONOUS_COMMIT  
 プライマリ レプリカがセカンダリ可用性グループに書き込まれるまでトランザクションのコミットを待機するを指定します。 SYNCHRONOUS_COMMIT は、プライマリ可用性グループを含む、最大 2 つの可用性グループを指定できます。  
  
 ASYNCHRONOUS_COMMIT  
 プライマリ レプリカがこのセカンダリ可用性グループによるログ書き込みを待機することがなくトランザクションをコミットすることを指定します。 ASYNCHRONOUS_COMMIT は、プライマリ可用性グループを含む、最大 2 つの可用性グループを指定できます。  
  
 AVAILABILITY_MODE 句は必須です。  
  
 FAILOVER_MODE  **=**  {手動}  
 分散型可用性グループのフェールオーバー モードを指定します。  
  
 MANUAL  
 計画された手動フェールオーバーを有効または強制手動フェールオーバー (と通常呼ばれる*強制フェールオーバー*)、データベース管理者です。  
  
 セカンダリ可用性グループへの自動フェールオーバーはサポートされていません。  
  
 SEEDING_MODE **=**  {自動 |手動}  
 セカンダリ可用性グループに最初にシードは方法を指定します。  
  
 AUTOMATIC  
 自動シード処理を使用できます。 このメソッドは、ネットワーク経由でセカンダリ可用性グループがシードされます。 このメソッドは、バックアップし、セカンダリ可用性グループのレプリカのプライマリ データベースのコピーを復元することにも必要ありません。  
  
 MANUAL  
 手動によるシード処理を指定します。 このメソッドでは、プライマリ レプリカで、データベースのバックアップを作成し、セカンダリ可用性グループのレプリカでバックアップを手動で復元する必要があります。  
  
 可用性グループを変更します。  
 分散型可用性グループの可用性グループの設定のいずれかを変更します。 変更する可用性グループの一覧には、可用性グループの名前と、WITH が含まれています。 各可用性グループの (...) 句。  
  
> [!IMPORTANT]  
>  このコマンドは、プライマリ可用性グループとセカンダリ可用性グループのインスタンスの両方で繰り返す必要があります。  
  
 GRANT あらゆるデータベースを作成します。  
 直接シード処理をサポートする、プライマリ レプリカは、代わりのデータベースを作成する可用性グループで許可される (SEEDING_MODE = AUTOMATIC)。 このパラメーターは、そのセカンダリ可用性グループに参加した後は、直接シード処理をサポートするすべてのセカンダリ レプリカで実行する必要があります。  CREATE ANY DATABASE 権限が必要です。  
  
 拒否する任意のデータベースを作成します。  
 プライマリ レプリカの代わりのデータベースを作成する可用性グループの機能を削除します。  
  
 \<add_listener_option >  
 ADD LISTENER には、次のいずれかのオプションを指定できます。  
  
 DHCP と [ON { **('***four_part_ipv4_address***'、'***four_part_ipv4_mask***')** }]  
 可用性グループ リスナーが動的ホスト構成プロトコル (DHCP) を使用することを指定します。  必要に応じて、ON 句を使用して、このリスナーを作成するネットワークを識別します。 DHCP は、可用性グループの可用性レプリカをホストする各サーバー インスタンスに使用される単一のサブネットに限定されます。  
  
> [!IMPORTANT]  
>  運用環境での DHCP の使用はお勧めしません。 ダウンタイムが発生して DHCP IP のリース期限が切れると、リスナーの DNS 名に関連付けられている新しい DHCP のネットワーク IP アドレスの登録に余分な時間がかかり、クライアント接続に影響が及びます。 ただし、開発環境とテスト環境を設定して可用性グループの基本機能を確認する場合や、アプリケーションとの統合の場合には DHCP が適しています。  
  
 例:  
  
 `WITH DHCP ON ('10.120.19.0','255.255.254.0')`  
  
 IP による**(** { **('***four_part_ipv4_address***'、'***four_part_ipv4_mask* **')** | **('***ipv6_address***')** } [ **、** . *n*  ] **)** [ **、**ポート **=**  *listener_port*]  
 可用性グループ リスナーが、DHCP を使用する代わりに、1 つ以上の静的 IP アドレスを使用することを指定します。 複数のサブネットにわたる可用性グループを作成するには、各サブネットのリスナー構成に静的 IP アドレスが 1 つ必要です。 サブネットの静的 IP アドレスには、IPv4 アドレスまたは IPv6 アドレスを使用できます。 ネットワーク管理者に連絡し、新しい可用性グループの可用性レプリカをホストする各サブネットの静的 IP アドレスを入手してください。  
  
 例:  
  
 `WITH IP ( ('10.120.19.155','255.255.254.0') )`  
  
 *four_part_ipv4_address*  
 可用性グループ リスナーに対する IPv4 の 4 つの部分から成るアドレスを指定します。 たとえば、 `10.120.19.155`のようにします。  
  
 *four_part_ipv4_mask*  
 可用性グループ リスナーに対する IPv4 の 4 つの部分から成るマスクを指定します。 たとえば、 `255.255.254.0`のようにします。  
  
 *ipv6_address*  
 可用性グループ リスナーに対する IPv6 アドレスを指定します。 たとえば、 `2001::4898:23:1002:20f:1fff:feff:b3a3`のようにします。  
  
 ポート **=**  *listener_port*  
 ポート番号を指定します:*listener_port*— WITH IP 句で指定されている可用性グループ リスナーで使用します。 PORT は省略できます。  
  
 既定のポート番号 1433 がサポートされます。 ただし、セキュリティ上の問題がある場合は、別のポート番号を使用することをお勧めします。  
  
 例: `WITH IP ( ('2001::4898:23:1002:20f:1fff:feff:b3a3') ) , PORT = 7777`  
  
 MODIFY LISTENER **'***dns_name***' (** \<modify_listener_option > **)**  
 この可用性グループに対する既存の可用性グループ リスナーを変更します。 プライマリ レプリカでのみサポートされます。  
  
 \<modify_listener_option >  
 MODIFY LISTENER には、次のいずれかのオプションを指定できます。  
  
 追加の IP { **('***four_part_ipv4_address***'、'***four_part_ipv4_mask***')**  |  **('**dns_name*ipv6_address***')** }  
 指定された IP アドレスで指定された可用性グループ リスナーを追加*dns_name*です。  
  
 ポート **=**  *listener_port*  
 このセクションで既に説明したこの引数に関する説明を参照してください。  
  
 リスナーの再起動**'***dns_name***'**  
 指定した DNS 名に関連付けられたリスナーを再起動します。 プライマリ レプリカでのみサポートされます。  
  
 リスナーの削除**'***dns_name***'**  
 指定した DNS 名に関連付けられたリスナーを削除します。 プライマリ レプリカでのみサポートされます。  
  
 OFFLINE  
 オンラインの可用性グループをオフラインにする 同期コミット データベースのデータ損失はありません。  
  
 可用性グループがオフラインになると、クライアントはそのデータベースを使用できなくなりますが、可用性グループをオンラインに戻すことはできません。 したがって、OFFLINE オプションは、可用性グループのリソースを新しい WSFC クラスターに移行するときに、クラスター間での [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]の移行中に限って使用してください。  
  
 詳細については、次を参照してください。[かかる、可用性グループ オフライン (&) #40 です。SQL Server &#41;](../../database-engine/availability-groups/windows/take-an-availability-group-offline-sql-server.md).  
  
## <a name="prerequisites-and-restrictions"></a>前提条件と制限  
 については前提条件と制限の可用性レプリカ上、およびそのホスト サーバー インスタンスとコンピューターで、次を参照してください[前提条件、制限事項、および Always On 可用性グループ &#40; ための推奨事項。SQL Server &#41;](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
 可用性グループの TRANSACT-SQL ステートメントの制限については、次を参照してください[の Always On 可用性グループ &#40; TRANSACT-SQL ステートメントの概要。SQL Server &#41;](../../database-engine/availability-groups/windows/transact-sql-statements-for-always-on-availability-groups.md).  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 可用性グループの ALTER AVAILABILITY GROUP 権限、CONTROL AVAILABILITY GROUP 権限、ALTER ANY AVAILABILITY GROUP 権限、または CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
###  <a name="Join_Secondary_Replica"></a> A. セカンダリ レプリカを可用性グループに参加させる  
 次の例では、結合、セカンダリ レプリカに接続されている、`AccountsAG`可用性グループです。  
  
```  
ALTER AVAILABILITY GROUP AccountsAG JOIN;  
GO  
```  
  
###  <a name="Force_Failover"></a> B. 可用性グループを強制的にフェールオーバーする  
 次の例では、`AccountsAG` 可用性グループを、接続されているセカンダリ レプリカに強制的にフェールオーバーします。  
  
```  
ALTER AVAILABILITY GROUP AccountsAG FORCE_FAILOVER_ALLOW_DATA_LOSS;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/create-availability-group-transact-sql.md)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)   
 [DROP AVAILABILITY GROUP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-availability-group-transact-sql.md)   
 [sys.availability_replicas & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-availability-replicas-transact-sql.md)   
 [sys.availability_groups & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)   
 [Always On 可用性グループの構成 &#40; のトラブルシューティングします。SQL Server &#41;](../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)   
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)  
  
  

