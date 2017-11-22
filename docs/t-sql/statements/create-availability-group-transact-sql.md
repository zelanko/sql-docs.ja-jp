---
title: "可用性グループ (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/16/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- AVAILABILITY GROUP
- CREATE_AVAILABILITY_TSQL
- CREATE_AVAILABILITY_GROUP_TSQL
- CREATE AVAILABILITY GROUP
- CREATE AVAILABILITY
- AVAILABILITY_GROUP_TSQL
dev_langs: TSQL
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- CREATE AVAILABILITY GROUP statement
- Availability Groups [SQL Server], creating
- Availability Groups [SQL Server], Transact-SQL statements
ms.assetid: a3d55df7-b4e4-43f3-a14b-056cba36ab98
caps.latest.revision: "196"
author: MikeRayMSFT
ms.author: mikeray
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 35ccffcfbdce2c10b20c8459e59a1c2d41962088
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="create-availability-group-transact-sql"></a>CREATE AVAILABILITY GROUP (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスが [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]機能に対して有効である場合、新しい可用性グループを作成します。  
  
> [!IMPORTANT]  
>  インスタンスでの execute CREATE AVAILABILITY GROUP[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]新しい可用性グループの初期プライマリ レプリカとして使用するものです。 このサーバー インスタンスは、Windows Server フェールオーバー クラスタ リング (WSFC) ノード上に存在する必要があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```SQL  
  
CREATE AVAILABILITY GROUP group_name  
   WITH (<with_option_spec> [ ,...n ] )  
   FOR [ DATABASE database_name [ ,...n ] ]  
   REPLICA ON <add_replica_spec> [ ,...n ]  
   AVAILABILITY GROUP ON <add_availability_group_spec> [ ,...2 ]  
   [ LISTENER ‘dns_name’ ( <listener_option> ) ]  
[ ; ]  
  
<with_option_spec>::=   
    AUTOMATED_BACKUP_PREFERENCE = { PRIMARY | SECONDARY_ONLY| SECONDARY | NONE }  
  | FAILURE_CONDITION_LEVEL  = { 1 | 2 | 3 | 4 | 5 }   
  | HEALTH_CHECK_TIMEOUT = milliseconds  
  | DB_FAILOVER  = { ON | OFF }   
  | DTC_SUPPORT  = { PER_DB | NONE }  
  | BASIC  
  | DISTRIBUTED
  | REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT = { integer }
  | CLUSTER_TYPE = { WSFC | EXTERNAL | NONE } 
  
<add_replica_spec>::=  
  <server_instance> WITH  
    (  
       ENDPOINT_URL = 'TCP://system-address:port',  
       AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT | CONFIGURATION_ONLY },  
       FAILOVER_MODE = { AUTOMATIC | MANUAL | EXTERNAL }  
       [ , <add_replica_option> [ ,...n ] ]  
    )   
  
  <add_replica_option>::=  
       SEEDING_MODE = { AUTOMATIC | MANUAL }  
     | BACKUP_PRIORITY = n  
     | SECONDARY_ROLE ( {   
            [ ALLOW_CONNECTIONS = { NO | READ_ONLY | ALL } ]   
        [,] [ READ_ONLY_ROUTING_URL = 'TCP://system-address:port' ]  
     } )  
     | PRIMARY_ROLE ( {   
            [ ALLOW_CONNECTIONS = { READ_WRITE | ALL } ]   
        [,] [ READ_ONLY_ROUTING_LIST = { ( ‘<server_instance>’ [ ,...n ] ) | NONE } ]  
     } )  
     | SESSION_TIMEOUT = integer  
  
<add_availability_group_spec>::=  
 <ag_name> WITH  
    (  
       LISTENER_URL = 'TCP://system-address:port',  
       AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT },  
       FAILOVER_MODE = MANUAL,  
       SEEDING_MODE = { AUTOMATIC | MANUAL }  
    )  
  
<listener_option> ::=  
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
  
```  
  
## <a name="arguments"></a>引数  
 *group_name*  
 新しい可用性グループの名前を指定します。 *group_name*は有効な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][識別子](../../relational-databases/databases/database-identifiers.md)、および、WSFC クラスター内のすべての可用性グループ間で一意である必要があります。 可用性グループ名の最大文字数は 128 文字です。  
  
 AUTOMATED_BACKUP_PREFERENCE  **=**  {プライマリ |SECONDARY_ONLY |セカンダリ |[なし]}  
 バックアップを実行する場所を選択するときにバックアップ ジョブがプライマリ レプリカを評価する方法についての優先設定を指定します。 自動バックアップの優先設定を考慮して、特定のバックアップ ジョブのスクリプトを作成できます。 優先順位がによって適用されませんを理解することが重要[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ので、アドホック バックアップに影響を与えません。  
  
 サポートされる値は次のとおりです。  
  
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
>  既存の可用性グループの自動バックアップ設定を表示するには、選択、 **automated_backup_preference**または**automated_backup_preference_desc**の列、 [sys.availability_groups](../../relational-databases/system-catalog-views/sys-availability-groups-transact-sql.md)カタログ ビューです。 さらに、 [sys.fn_hadr_backup_is_preferred_replica &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql.md)優先されるバックアップ レプリカを決定するために使用できます。  この関数は、少なくとも 1 つで、レプリカの 1 を返す場合でも、`AUTOMATED_BACKUP_PREFERENCE = NONE`です。  
  
 FAILURE_CONDITION_LEVEL  **=**  {1 | 2 |**3** | 4 | 5}  
 この可用性グループの自動フェールオーバーを実行するエラー条件を指定します。 FAILURE_CONDITION_LEVEL はグループ レベルで設定されていますが、同期コミット可用性モードが構成されている可用性レプリカにのみ (AVAILIBILITY_MODE  **=**  SYNCHRONOUS_COMMIT)。 さらに、エラー状態が自動フェールオーバーをトリガー プライマリとセカンダリの両方のレプリカが自動フェールオーバー モードで構成されている場合にのみ (FAILOVER_MODE  **=** 自動) セカンダリ レプリカが、現在プライマリ レプリカと同期されています。  
  
 エラー状態レベルの範囲は 1 ～ 5 で、レベル 1 が最も制限が緩く、レベル 5 が最も制限の厳しい指定です。 任意の状態レベルは、それより制限が緩いすべてのレベルを含みます。 したがって、最も厳しい状態レベル 5 にはそれより制限が緩い状態レベル (1 ～ 4) が含まれ、レベル 4 にはレベル 1 ～ 3 が含まれます。以下同様です。 次の表では、各レベルに対応するエラー状態について説明します。  
  
|レベル|エラー状態|  
|-----------|-----------------------|  
|1|次のいずれかが発生した場合に自動フェールオーバーを開始する必要があることを指定します。<br /><br /> -[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サービスが停止します。<br /><br /> のサーバー インスタンスから ACK を受信しないため WSFC クラスターに接続するための可用性グループのリースが有効期限です。 詳細については、「 [動作方法: SQL Server Always On のリース タイムアウト](http://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-AlwaysOn-lease-timeout.aspx)」を参照してください。|  
|2|次のいずれかが発生した場合に自動フェールオーバーを開始する必要があることを指定します。<br /><br /> -インスタンスの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クラスターに接続しません。 可用性グループのユーザー指定の HEALTH_CHECK_TIMEOUT しきい値を超えました。<br /><br /> 可用性レプリカがエラー状態です。|  
|3|重要なので、自動フェールオーバーを開始することを指定します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]孤立したスピンロック、深刻な書き込みアクセス違反、ダンプが多すぎるなどの内部エラーが発生します。<br /><br /> これは既定の動作です。|  
|4|度が中程度、自動フェールオーバーを開始することを示す[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で永続的なメモリ不足の状態などの内部エラーが発生、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]内部リソース プールです。|  
|5|以下のような任意の修飾エラー状態に対して自動フェールオーバーを開始する必要があることを指定します。<br /><br /> -SQL エンジンのワーカー スレッドの枯渇しています。<br /><br /> 解決不可能なデッドロックの検出。|  
  
> [!NOTE]  
>  インスタンスが応答しないこと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントに要求が可用性グループに関連します。  
  
 FAILURE_CONDITION_LEVEL および HEALTH_CHECK_TIMEOUT の値を定義して、*柔軟なフェールオーバー ポリシー*特定のグループです。 この柔軟なフェールオーバー ポリシーを使用すると、自動フェールオーバーを実行する条件をきめ細かく制御できます。 詳細については、次を参照してください[自動フェールオーバー、可用性グループ &#40; のための柔軟なフェールオーバー ポリシー。SQL Server &#41;](../../database-engine/availability-groups/windows/flexible-automatic-failover-policy-availability-group.md).  
  
 HEALTH_CHECK_TIMEOUT  **=**  *(ミリ秒)*  
 待機時間 (ミリ秒単位) を指定します、 [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md)システム ストアド プロシージャによってサーバーの状態の情報を返す前に、WSFC クラスターでは、サーバー インスタンスが速度低下またはハングがある前提としています。 HEALTH_CHECK_TIMEOUT はグループ レベルで設定されていますが、自動フェールオーバーを伴う同期コミット可用性モードが構成されている可用性レプリカにのみ (AVAILIBILITY_MODE  **=** 同期_COMMIT)。  さらに、正常性チェックのタイムアウトが自動フェールオーバーをトリガー プライマリとセカンダリの両方のレプリカが自動フェールオーバー モードで構成されている場合にのみ (FAILOVER_MODE  **=** 自動) とセカンダリレプリカがプライマリ レプリカと現在同期されています。  
  
 HEALTH_CHECK_TIMEOUT の既定値は 30000 ミリ秒 (30 秒) です。 最小値は 15000 ミリ秒 (15 秒)、最大値は 4294967295 ミリ秒です。  
  
> [!IMPORTANT]  
>  **sp_server_diagnostics** では、データベース レベルでの正常性チェックは実行されません。  
  
 DB_FAILOVER  **=**  {ON |オフ}  
 プライマリ レプリカでのデータベースがオフラインのときに実行する応答を指定します。 ON に設定すると、可用性グループ内のデータベースのオンライン以外のすべての状態は、自動フェールオーバーをトリガーします。 このオプションが OFF に設定されている場合は、インスタンスのヘルスだけが自動フェールオーバーをトリガーに使用されます。  
  
  この設定に関する詳細については、次を参照してください[データベース レベルの正常性の検出のオプション。](../../database-engine/availability-groups/windows/sql-server-always-on-database-health-detection-failover-option.md) 
  
 DTC_SUPPORT  **=**  {PER_DB |[なし]}  
 データベースにまたがるトランザクションは分散トランザクション コーディネーター (DTC) ではサポートするかどうかを指定します。 データベースにまたがるトランザクションは、以降でのみサポートされます[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。 PER_DB では、これらのトランザクションのサポートを可用性グループを作成します。 詳細については、「[Always On 可用性グループとデータベース ミラーリングでの複数データベースにまたがるトランザクションと分散トランザクション &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/transactions-always-on-availability-and-database-mirroring.md)」を参照してください。  
  
 BASIC  
 基本的な可用性グループを作成するために使用します。 基本的な可用性グループは 1 つのデータベースと 2 つのレプリカに制限されます。 プライマリ レプリカとセカンダリ レプリカが 1 つです。 このオプションは、非推奨のデータベース ミラーリング SQL Server Standard Edition の機能に代わるものです。 詳細については、次を参照してください。[基本的な可用性グループ &#40;です。Always On 可用性グループ &#41;](../../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md). 基本的な可用性グループには、以降ではサポートされて[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。  

 DISTRIBUTED  
 分散型可用性グループを作成するために使用します。 このオプションは個別の Windows Server フェールオーバー クラスター内の 2 つの可用性グループを接続する可用性グループのパラメーターと共に使用します。  詳細については、「[Distributed Availability Groups &#40;Always On Availability Groups&#41; (分散型可用性グループ (Always On 可用性グループ))](../../database-engine/availability-groups/windows/distributed-availability-groups-always-on-availability-groups.md)」を参照してください。 分散型可用性グループには、以降ではサポートされて[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]です。 

 REQUIRED_SYNCHRONIZED_SECONDARIES_TO_COMMIT   
 SQL Server 2017 年 1 で導入されました。 プライマリ トランザクションをコミットする前にコミットするために必要なの同期セカンダリ レプリカの最小数を設定するために使用します。 SQL Server トランザクションがセカンダリ レプリカの最小数のトランザクション ログが更新されるまで待機することを保証します。 既定では 0 で、SQL Server 2016 と同じ動作を示します。 最小値は 0 です。 最大値は、レプリカから 1 を引いた数です。 このオプションは、同期コミット モードのレプリカに関連しています。 レプリカは、同期コミット モードでは、ときに、プライマリ レプリカでの書き込みは同期セカンダリ レプリカ上の書き込みはレプリカ データベースのトランザクション ログにコミットされるまでを待ちます。 同期セカンダリ レプリカをホストする SQL Server が応答しなくなった場合、プライマリ レプリカをホストする SQL Server は、同期されていないと続行としてそのセカンダリ レプリカをマークします。 応答しない状態のデータベースがオンラインに戻ったときに「同期されていません"状態にあるプライマリとなる同期再度まで、レプリカが異常とマークされてです。 この設定は、プライマリ レプリカはレプリカの最小数は、各トランザクションをコミット済みになるまで待機することを保証します。 レプリカの最小数が使用できない場合は、プライマリでコミットが失敗します。 クラスターの種類の`EXTERNAL`をクラスター リソースに追加されると、可用性グループの設定を変更します。 参照してください[可用性グループの構成の高可用性とデータ保護](../../linux/sql-server-linux-availability-group-ha.md)です。

 CLUSTER_TYPE  
 SQL Server 2017 年 1 で導入されました。 場合は、可用性グループで、Windows Server フェールオーバー クラスター (WSFC) を識別するために使用します。  Windows Server フェールオーバー クラスターでフェールオーバー クラスター インスタンス上の可用性グループがある場合は、WSFC に設定されます。 クラスターは、Linux ペースのように、Windows Server フェールオーバー クラスターではないクラスター マネージャーで管理されている場合は、外部に設定します。 可用性グループの WSFC をクラスターの調整を使用していない場合は、NONE に設定します。 たとえば、ときに、可用性グループを含む Linux サーバー クラスター マネージャーがありません。 

 データベース*database_name*  
 ローカル [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス (つまり可用性グループを作成するサーバー インスタンス) 上の 1 つ以上のユーザー データベースのリストを指定します。 1 つの可用性グループに対して複数のデータベースを指定できますが、各データベースが所属できる可用性グループは 1 つだけです。 可用性グループでサポートされるデータベースの種類については、次を参照してください[前提条件、制限事項、および Always On 可用性グループ &#40; ための推奨事項。SQL Server &#41;](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md). ローカル データベースが可用性グループに属しているを参照してください、 **replica_id**内の列、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)カタログ ビューです。  
  
 DATABASE 句は省略可能です。 を省略した場合、新しい可用性グループが空です。  
  
 可用性グループを作成した後にセカンダリ レプリカをホストする各サーバー インスタンスに接続し各セカンダリ データベースを準備し、可用性グループに参加します。 詳細については、「 [AlwaysOn セカンダリ データベース上のデータ移動の開始 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/start-data-movement-on-an-always-on-secondary-database-sql-server.md)」を参照してください。  
  
> [!NOTE]  
>  後で、現在のプライマリ レプリカをホストするサーバー インスタンス上の適格なデータベースを可用性グループに追加できます。 また、データベースを可用性グループから削除することもできます。 詳細については、「 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。  
  
 REPLICA ON  
 新しい可用性グループの可用性レプリカをホストする 1 ～ 5 個の SQL Server インスタンスを指定します。  各レプリカを指定する際には、サーバー インスタンスのアドレスに続けて WITH (...) 句を入力します。 では、少なくとも初期プライマリ レプリカになりますが、ローカル サーバー インスタンスを指定する必要があります。 必要に応じて、セカンダリ レプリカを 4 つまで指定することもできます。  
  
 すべてのセカンダリ レプリカを可用性グループに参加させる必要があります。 詳細については、「 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。  
  
> [!NOTE]  
>  使用していつでもセカンダリ レプリカを追加ができます、可用性グループを作成するときより小さい 4 つのセカンダリ レプリカを指定する場合、 [ALTER AVAILABILITY GROUP](../../t-sql/statements/alter-availability-group-transact-sql.md) [!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 このステートメントを使用することもできます。 これが既存の可用性グループから任意のセカンダリ レプリカを削除します。  
  
 \<server_instance > のインスタンスのアドレス指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリカのホストであります。 アドレスの形式は、インスタンスが既定のインスタンスか名前付きインスタンスか、およびスタンドアロン インスタンスかフェールオーバー クラスター インスタンス (FCI) かによって、次のように異なります。  
  
 { '*system_name*[\\*instance_name*]' | '*FCI_network_name*[\\*instance_name*]' }  
  
 このアドレスの構成要素は次のとおりです。  
  
 *system_name*  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のターゲット インスタンスが存在するコンピューター システムの NetBIOS 名です。 このコンピューターは WSFC ノードである必要があります。  
  
 *FCI_network_name*  
 使用されるネットワーク名にアクセスする、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]フェイル オーバー クラスター。 サーバー インスタンスが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー パートナーとして参加している場合に使用します。 選択を実行する[@@SERVERNAME ](../../t-sql/functions/servername-transact-sql.md) FCI では、サーバー インスタンスはその全体を返します '*FCI_network_name*[\\*instance_name*]' 文字列 (これは、。完全なレプリカ名)。  
  
 *instance_name*  
 インスタンスの名前を指定します、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]によってホストされている*system_name*または*FCI_network_name*とが HADR サービスが有効にします。 既定のサーバー インスタンスの場合、 *instance_name* は省略可能です。 インスタンス名では大文字と小文字が区別されません。 この値の名前では、スタンドアロン サーバー インスタンスでは SELECT を実行することによって返される値と同じ[@@SERVERNAME](../../t-sql/functions/servername-transact-sql.md)です。  
  
 \  
 指定する場合にのみを使用する区切り記号は、 *instance_name*から区別するために、 *system_name*または*FCI_network_name*です。  
  
 WSFC ノードとサーバー インスタンスの前提条件については、次を参照してください[前提条件、制限事項、および Always On 可用性グループ &#40; ための推奨事項。SQL Server &#41;](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
 ENDPOINT_URL **='**TCP**://***システム アドレス***:***ポート***'**  
 URL パスを指定します、[データベース ミラーリング エンドポイント](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)のインスタンスで[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]現在の REPLICA ON 句で定義している可用性レプリカをホストします。  
  
 ENDPOINT_URL 句は必須です。 詳細については、「 [可用性レプリカを追加または変更する場合のエンドポイント URL の指定 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/specify-endpoint-url-adding-or-modifying-availability-replica.md)の構成に関する一般的な問題のトラブルシューティングに役立つ情報を提供します。  
  
 **'**TCP**://***システム アドレス***:***ポート***'**  
 エンドポイントの URL または読み取り専用のルーティングの URL を指定するための URL を指定します。 URL のパラメーターは次のとおりです。  
  
 *system-address*  
 システム名、完全修飾ドメイン名では、対象のコンピューター システムを明確に識別する、IP アドレスなどの文字列です。  
  
 *port*  
 ポート番号 (ENDPOINT_URL オプションの場合) のパートナー サーバー インスタンスのミラーリング エンドポイントに関連付けられているかによって使用されるポート番号、[!INCLUDE[ssDE](../../includes/ssde-md.md)]のサーバー インスタンスの (READ_ONLY_ROUTING_URL オプションの場合)。  
  
 AVAILABILITY_MODE  **=**  {{SYNCHRONOUS_COMMIT |ASYNCHRONOUS_COMMIT |CONFIGURATION_ONLY}  
 SYNCHRONOUS_COMMIT または ASYNCHRONOUS_COMMIT は、プライマリ レプリカがセカンダリ レプリカをプライマリ レプリカは、特定のプライマリでトランザクションをコミットできる前にディスクにログ レコードの固定 (書き込み) を確認するを待っているかどうかを指定しますデータベースです。 同じプライマリ レプリカに対する異なるデータベースでのトランザクションは個別にコミットできます。 SQL Server 2017 CU 1 には、CONFIGURATION_ONLY が導入されています。 CONFIGURATION_ONLY レプリカは CLUSTER_TYPE を含む可用性グループにのみ適用されます = 外部または CLUSTER_TYPE = NONE です。 
  
 SYNCHRONOUS_COMMIT  
 プライマリ レプリカがトランザクションをコミットがこのセカンダリ レプリカ (同期コミット モード) に書き込まれるまで待機するを指定します。 SYNCHRONOUS_COMMIT は、プライマリ レプリカを含む最大 3 つのレプリカに対して指定できます。  
  
 ASYNCHRONOUS_COMMIT  
 このセカンダリ レプリカでログが書き込まれるのを待たずに、プライマリ レプリカがトランザクションをコミットすることを指定します (同期コミット可用性モード)。 ASYNCHRONOUS_COMMIT は、プライマリ レプリカを含む最大 5 つの可用性レプリカに対して指定できます。  

 CONFIGURATION_ONLY では、プライマリ レプリカは、このレプリカ上の master データベースを可用性グループ構成メタデータを同期的にコミットを指定します。 レプリカでは、ユーザー データは含まれません。 このオプションでは:

- Express Edition をなど、SQL Server の任意のエディションでホストできます。
- データの型である CONFIGURATION_ONLY レプリカのミラーリング エンドポイントを要求`WITNESS`です。
- 変更できません。
- 正しくない場合に`CLUSTER_TYPE = WSFC`です。 

   詳細については、次を参照してください。[構成のみのレプリカ](../../linux/sql-server-linux-availability-group-ha.md)です。
  
 AVAILABILITY_MODE 句は必須です。 詳細については、「 [可用性モード &#40;AlwaysOn 可用性グループ&#41;](../../database-engine/availability-groups/windows/availability-modes-always-on-availability-groups.md)、または PowerShell を使用して、AlwaysOn 可用性グループ上で計画的な手動フェールオーバーまたは強制手動フェールオーバー (強制フェールオーバー) を実行する方法について説明します。  
  
 FAILOVER_MODE  **=**  {自動 |手動}  
 定義している可用性レプリカのフェールオーバー モードを指定します。  
  
 AUTOMATIC  
 自動フェールオーバーを有効にします。 このオプションは、AVAILABILITY_MODE = SYNCHRONOUS_COMMIT も指定した場合にのみサポートされます。 AUTOMATIC は、プライマリ レプリカを含む 2 つの可用性レプリカに対して指定できます。  
  
> [!NOTE]  
>  SQL Server フェールオーバー クラスター インスタンス (FCI) は可用性グループによる自動フェールオーバーをサポートしないため、FCI によってホストされる可用性レプリカは手動フェールオーバー用にのみ構成できます。  
  
 MANUAL  
 計画された手動フェールオーバーを有効または強制手動フェールオーバー (と通常呼ばれる*強制フェールオーバー*)、データベース管理者です。  
  
 FAILOVER_MODE 句は必須です。 2 種類の手動フェールオーバー、つまりデータ損失のない手動フェールオーバーと強制フェールオーバー (データ損失の可能性あり) は、異なる条件の下でサポートされます。 詳細については、「 [フェールオーバーとフェールオーバー モード &#40;AlwaysOn 可用性グループ&#41;](../../database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups.md)、または PowerShell を使用して、AlwaysOn 可用性グループ上で計画的な手動フェールオーバーまたは強制手動フェールオーバー (強制フェールオーバー) を実行する方法について説明します。  
  
 SEEDING_MODE  **=**  {自動 |手動}  
 セカンダリ レプリカが最初にシード処理方法を指定します。  
  
 AUTOMATIC  
 直接シード処理を有効にします。 このメソッドでは、ネットワーク経由でセカンダリ レプリカがシード処理されます。 このメソッドは、バックアップし、レプリカのプライマリ データベースのコピーを復元することにも必要ありません。  
  
> [!NOTE]  
>  直接シード処理を行う必要がありますに許可するデータベースの作成各セカンダリ レプリカで呼び出すことによって**ALTER AVAILABILITY GROUP**で、 **GRANT CREATE ANY DATABASE**オプション。  
  
 MANUAL  
 手動によるシード (既定値) を指定します。 このメソッドでは、プライマリ レプリカで、データベースのバックアップを作成し、セカンダリ レプリカでバックアップを手動で復元する必要があります。  
  
 BACKUP_PRIORITY  **=** *n*  
 同じ可用性グループ内の他のレプリカと比較して、このレプリカでバックアップを実行する優先順位を指定します。 値は 0 ～ 100 の範囲の整数です。 これらの値には次の意味があります。  
  
-   1 ～ 100 は、その可用性レプリカがバックアップの実行に対して選択される可能性があることを示します。 1 は最も低い優先順位を示し、100 は最も高い優先順位を示します。 たとえば、BACKUP_PRIORITY = 1 の場合、現在使用可能な可用性レプリカにそれより高い優先順位のものがない場合にのみ、その可用性レプリカがバックアップの実行に対して選択されます。  
  
-   0 は、この可用性レプリカがバックアップの実行時であることを示します。 これは、たとえば、バックアップをフェールオーバーすることがないリモート可用性レプリカのような場合に便利です。  
  
 詳細については、「[アクティブなセカンダリ: セカンダリ レプリカでのバックアップ &#40;AlwaysOn 可用性グループ&#41;](../../database-engine/availability-groups/windows/active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)」を参照してください。  
  
 SECONDARY_ROLE **(** . **)**  
 この可用性レプリカが現在セカンダリ ロールを所有している場合に効果を実行する役割に固有の設定を指定します (つまり、常にセカンダリ レプリカである)。 かっこの中では、いずれか一方または両方のセカンダリ ロール オプションを指定します。 両方を指定する場合は、コンマ区切りのリストを使用します。  
  
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
  
 詳細については、レプリカの読み取り専用ルーティング URL の計算について、次を参照してください。 [Alwayson の read_only_routing_url の計算](http://blogs.msdn.com/b/mattn/archive/2012/04/25/calculating-read-only-routing-url-for-AlwaysOn.aspx)です。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前付きインスタンスの場合は、特定のポートを使用するように Transact-SQL リスナーを構成する必要があります。 詳細については、「[特定の TCP ポートで受信待ちするようにサーバーを構成する方法 &#40;SQL Server 構成マネージャー&#41;](../../database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port.md)」を参照してください。  
  
 PRIMARY_ROLE **(** . **)**  
 この可用性レプリカが現在プライマリ ロールを所有している場合に効果を実行する役割に固有の設定を指定します (つまり、常にプライマリ レプリカである)。 かっこの中では、いずれか一方または両方のプライマリ ロール オプションを指定します。 両方を指定する場合は、コンマ区切りのリストを使用します。  
  
 プライマリ ロール オプションは次のとおりです。  
  
 ALLOW_CONNECTIONS  **=**  {READ_WRITE |すべて}  
 プライマリ ロールを実行している (つまりプライマリ レプリカとして機能している) 特定の可用性レプリカのデータベースが受け入れることのできるクライアントからの接続の種類を指定します。以下のいずれかになります。  
  
 READ_WRITE  
 Application Intent 接続プロパティが **ReadOnly** に設定されている接続は許可されません。  Application Intent プロパティが **ReadWrite** に設定されている場合、または Application Intent 接続プロパティが設定されていない場合は、接続が許可されます。 "アプリケーションの目的" 接続プロパティの詳細については、「 [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)」を参照してください。  
  
 ALL  
 プライマリ レプリカのデータベースに対するすべての接続が許可されます。 これは既定の動作です。  
  
 READ_ONLY_ROUTING_LIST  **=**  { **('**\<server_instance >**'** [ **、**.*n* ] **)** |[なし]} セカンダリ ロールで実行されている場合は、次の要件を満たしているこの可用性グループの可用性レプリカをホストするサーバー インスタンスのコンマ区切りの一覧を指定します。  
  
-   すべての接続または読み取り専用の接続を許可するように構成されていること (前に示した SECONDARY_ROLE オプションの ALLOW_CONNECTIONS 引数を参照)。  
  
-   読み取り専用ルーティングの URL が定義されていること (前に示した SECONDARY_ROLE オプションの READ_ONLY_ROUTING_URL 引数を参照)。  
  
 READ_ONLY_ROUTING_LIST の値は次のとおりです。  
  
 \<server_instance > のインスタンスのアドレス指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリカのセカンダリ ロールで実行されている場合に読み取り可能なセカンダリ レプリカをホストであります。  
  
 コンマ区切りのリストを使用すると、読み取り可能なセカンダリ レプリカをホストするすべてのサーバー インスタンスを指定できます。 読み取り専用ルーティング リスト内でサーバー インスタンスの指定順序に従います。 一覧の最後に、このサーバー インスタンスを配置することで、レプリカの読み取り専用ルーティング リスト、レプリカのホスト サーバーのインスタンスを含める場合は通常、お勧め、1 つは、使用可能な場合に、読み取りを目的とした接続がセカンダリ レプリカに移動できるようにします。  
  
 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]、読み取り可能なセカンダリ レプリカの間で読み取りを目的とした要求の負荷を分散することができます。 これは、読み取り専用ルーティング リスト内のかっこの入れ子になったセットで、レプリカを配置することで指定します。 詳細と例については、次を参照してください。[読み取り専用レプリカ間の負荷分散の構成](../../database-engine/availability-groups/windows/configure-read-only-routing-for-an-availability-group-sql-server.md#loadbalancing)です。  
  
 なし  
 この可用性レプリカがプライマリ レプリカの場合は、読み取り専用ルーティングはサポートされていないことを指定します。 これは既定の動作です。  
  
 SESSION_TIMEOUT  **=**  *整数*  
 セッション タイムアウト期間を秒単位で指定します。 このオプションを指定しない場合、この時間は既定で 10 秒に設定されます。 最小値は 5 秒です。  
  
> [!IMPORTANT]  
>  タイムアウト期間を 10 秒以上にしておくことをお勧めします。  
  
 セッション タイムアウト期間の詳細については、次を参照してください[概要の Always On 可用性グループ &#40;。SQL Server &#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md).  
  
 上の可用性グループ  
 構成する 2 つの可用性グループを指定します、*分散型可用性グループ*です。 可用性グループが、一部の独自の Windows Server フェールオーバー クラスター (WSFC)。 分散型可用性グループを作成するときに現在の SQL Server インスタンス上の可用性グループは、プライマリ可用性グループになります。 2 つ目の可用性グループでは、セカンダリ可用性グループになります。  
  
 分散型可用性グループにセカンダリ可用性グループに参加する必要があります。 詳細については、「 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)、または PowerShell を使用して、既存の AlwaysOn 可用性グループにセカンダリ レプリカを追加する方法について説明します。  
  
 \<ag_name > いずれかを構成する可用性グループの名前を指定、分散型可用性グループの半分です。  
  
 リスナー **='**TCP**://***システム アドレス***:***ポート***'**  
 可用性グループに関連付けられているリスナーの URL パスを指定します。  
  
 リスナー句が必要です。  
  
 **'**TCP**://***システム アドレス***:***ポート***'**  
 可用性グループに関連付けられているリスナーの URL を指定します。 URL のパラメーターは次のとおりです。  
  
 *system-address*  
 システム名、完全修飾ドメイン名、IP アドレス、リスナーを明確に識別するなどの文字列です。  
  
 *port*  
 可用性グループのデータベース ミラーリング エンドポイントに関連付けられているポート番号です。 リスナーのポートではないことに注意してください。  
  
 AVAILABILITY_MODE  **=**  {SYNCHRONOUS_COMMIT |ASYNCHRONOUS_COMMIT |CONFIGURATION_ONLY}  
 プライマリ レプリカがセカンダリ可用性グループ プライマリ レプリカは、特定のプライマリ データベースでトランザクションをコミットできる前にディスクにログ レコードの固定 (書き込み) を確認するを待っているかどうかを指定します。  
  
 SYNCHRONOUS_COMMIT  
 プライマリ レプリカは、セカンダリ可用性グループに書き込まれるまでトランザクションのコミットを待機を指定します。 SYNCHRONOUS_COMMIT は、プライマリ可用性グループを含む、最大 2 つの可用性グループを指定できます。  
  
 ASYNCHRONOUS_COMMIT  
 プライマリ レプリカがこのセカンダリ可用性グループによるログ書き込みを待機することがなくトランザクションをコミットすることを指定します。 ASYNCHRONOUS_COMMIT は、プライマリ可用性グループを含む、最大 2 つの可用性グループを指定できます。  
  
 AVAILABILITY_MODE 句は必須です。  
  
 FAILOVER_MODE  **=**  {手動}  
 分散型可用性グループのフェールオーバー モードを指定します。  
  
 MANUAL  
 計画された手動フェールオーバーを有効または強制手動フェールオーバー (と通常呼ばれる*強制フェールオーバー*)、データベース管理者です。  
  
 FAILOVER_MODE 句が必要であり、唯一のオプションは MANUAL です。 セカンダリ可用性グループへの自動フェールオーバーはサポートされていません。  
  
 SEEDING_MODE  **=**  {自動 |手動}  
 セカンダリ可用性グループが最初にシード処理方法を指定します。  
  
 AUTOMATIC  
 直接シード処理を有効にします。 このメソッドでは、ネットワーク経由でセカンダリ可用性グループがシード処理されます。 このメソッドは、バックアップし、セカンダリ可用性グループのレプリカのプライマリ データベースのコピーを復元することにも必要ありません。  
  
 MANUAL  
 手動によるシード (既定値) を指定します。 このメソッドでは、プライマリ レプリカで、データベースのバックアップを作成し、セカンダリ可用性グループのレプリカでバックアップを手動で復元する必要があります。  
  
 リスナー **'***dns_name***' (** \<listener_option > **)**この新しい可用性グループ リスナーを定義します可用性グループです。 LISTENER は省略可能な引数です。  
  
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
>  NetBIOS では、dns_name の最初の 15 文字のみが認識されます。 エラーが、仮想ネットワークのことをレポートと同じ Active Directory で制御されている 2 つの WSFC クラスターがあり、15 文字以内と同一の 15 文字のプレフィックス名を使用して両方のクラスターで可用性グループ リスナーを作成しようとする場合名前のリソースをオンラインにできませんでした。 DNS 名のプレフィックスに対する名前付け規則の詳細については、「 [ドメイン名を割り当てる](http://technet.microsoft.com/library/cc731265\(WS.10\).aspx)」を参照してください。  
  
 \<listener_option > LISTENER には、次のいずれかの\<listener_option > オプション。 
  
 DHCP と [ON { **('***four_part_ipv4_address***'、'***four_part_ipv4_mask***')** }]  
 可用性グループ リスナーが動的ホスト構成プロトコル (DHCP) を使用するように指定します。  必要に応じて、ON 句を使用して、このリスナーが作成されたネットワークを識別します。 DHCP は、1 つのサブネットすべてのサーバー インスタンスに使用される、可用性グループのレプリカをホストするに限定されます。  
  
> [!IMPORTANT]  
>  運用環境での DHCP の使用はお勧めしません。 ダウンタイムが発生して DHCP IP のリース期限が切れると、リスナーの DNS 名に関連付けられている新しい DHCP のネットワーク IP アドレスの登録に余分な時間がかかり、クライアント接続に影響が及びます。 ただし、開発環境とテスト環境を設定して可用性グループの基本機能を確認する場合や、アプリケーションとの統合の場合には DHCP が適しています。  
  
 例:  
  
 `WITH DHCP ON ('10.120.19.0','255.255.254.0')`  
  
 IP による**(** { **('***four_part_ipv4_address***'、'***four_part_ipv4_mask* **')** | **('***ipv6_address***')** } [ **、** . *n*  ] **)** [ **、**ポート **=**  *listener_port*]  
 、DHCP を使用する代わりに、可用性グループ リスナーは 1 つまたは複数の静的 IP アドレスを指定します。 複数のサブネットにわたる可用性グループを作成するには、各サブネットのリスナー構成に静的 IP アドレスが 1 つ必要です。 サブネットの静的 IP アドレスには、IPv4 アドレスまたは IPv6 アドレスを使用できます。 新しい可用性グループのレプリカをホストする各サブネットの静的 IP アドレスを取得する、ネットワーク管理者に問い合わせてください。  
  
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
  
## <a name="prerequisites-and-restrictions"></a>前提条件と制限  
 可用性グループを作成するための前提条件については、次を参照してください[前提条件、制限事項、および Always On 可用性グループ &#40; ための推奨事項。SQL Server &#41;](../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md).  
  
 可用性グループの TRANSACT-SQL ステートメントの制限については、次を参照してください[の Always On 可用性グループ &#40; TRANSACT-SQL ステートメントの概要。SQL Server &#41;](../../database-engine/availability-groups/windows/transact-sql-statements-for-always-on-availability-groups.md).  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 **sysadmin** 固定サーバー ロールのメンバーシップと、CREATE AVAILABILITY GROUP サーバー権限、ALTER ANY AVAILABILITY GROUP 権限、CONTROL SERVER 権限のいずれかが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-configuring-backup-on-secondary-replicas-flexible-failover-policy-and-connection-access"></a>A. セカンダリ レプリカ上のバックアップ、柔軟なフェールオーバー ポリシー、および接続アクセスを構成する  
 次の例は、という名前の可用性グループを作成`MyAg`2 つのユーザー データベース、`ThisDatabase`と`ThatDatabase`です。 次の表は、可用性グループ全体を対象に設定されるオプションの指定値をまとめたものです。  
  
|グループ オプション|設定|Description|  
|------------------|-------------|-----------------|  
|AUTOMATED_BACKUP_PREFERENCE|SECONDARY|バックアップをセカンダリ レプリカで実行することを指定します (プライマリ レプリカ以外にオンラインのレプリカがない場合は除く)。これが既定の動作です。 AUTOMATED_BACKUP_PREFERENCE 設定が作用するためには、その設定を考慮して動作するバックアップ ジョブ スクリプトを可用性データベースに作成する必要があります。|  
|FAILURE_CONDITION_LEVEL|3|孤立したスピンロック、深刻な書き込みアクセス違反、ダンプが多すぎるなど、SQL Server 内部の深刻なエラーが発生した場合に自動フェールオーバーを開始する必要があることを指定します。|  
|HEALTH_CHECK_TIMEOUT|600000|この正常性チェックのタイムアウト値を 60 (秒単位) を指定、WSFC クラスターが 60000 ミリ秒を待機する、 [sp_server_diagnostics](../../relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql.md)システム ストアド プロシージャであるサーバー インスタンスに関するサーバーのヘルス情報を返すクラスターは、ホスト サーバー インスタンスが速度低下またはハングがある前提としています。 前に、自動同期コミット レプリカをホストします。 (既定値は 30000 ミリ秒) です。|  
  
 次の 3 つの可用性レプリカはという名前のコンピューター上の既定のサーバー インスタンスによってホストされる`COMPUTER01`、 `COMPUTER02`、および`COMPUTER03`です。 次の表は、レプリカ オプションの指定値をレプリカごとにまとめたものです。  
  
|レプリカ オプション|設定`COMPUTER01`|設定`COMPUTER02`|設定`COMPUTER03`|Description|  
|--------------------|-----------------------------|-----------------------------|-----------------------------|-----------------|  
|ENDPOINT_URL|TCP://*COMPUTER 01: 5022*|TCP://*COMPUTER 02: 5022*|TCP://*COMPUTER 03: 5022*|この例では、いずれのシステムも同じドメインに存在するため、エンドポイントの URL には、コンピューター システムの名前をシステム アドレスとして使用できます。|  
|AVAILABILITY_MODE|SYNCHRONOUS_COMMIT|SYNCHRONOUS_COMMIT|ASYNCHRONOUS_COMMIT|2 つのレプリカが同期コミット モードを使用できます。 同期されているレプリカは、データ損失のないフェールオーバーをサポートします。 3 番目のレプリカには、非同期コミットの可用性モードが使用されます。|  
|FAILOVER_MODE|AUTOMATIC|AUTOMATIC|MANUAL|同期コミット レプリカは、自動フェールオーバーおよび計画的な手動フェールオーバーをサポートします。 同期コミット可用性モードのレプリカは、強制手動フェールオーバーのみサポートします。|  
|BACKUP_PRIORITY|30|30|90|非同期コミット レプリカには、同期コミット レプリカよりも高い優先度 (90) が割り当てられます。 バックアップは、非同期コミット レプリカをホストするサーバー インスタンスで発生する傾向があります。|  
|SECONDARY_ROLE|( ALLOW_CONNECTIONS = NO,<br /><br /> READ_ONLY_ROUTING_URL = 'TCP://COMPUTER01:1433' )|( ALLOW_CONNECTIONS = NO,<br /><br /> READ_ONLY_ROUTING_URL = 'TCP://COMPUTER02:1433' )|( ALLOW_CONNECTIONS = READ_ONLY, <br />READ_ONLY_ROUTING_URL = 'TCP://COMPUTER03:1433' )|非同期コミット レプリカだけが、読み取り可能なセカンダリ レプリカとして機能します。<br /><br /> コンピューターの名前と、データベース エンジンの既定のポート番号 (1433) を指定します。<br /><br /> この引数は省略可能です。|  
|PRIMARY_ROLE|( ALLOW_CONNECTIONS = READ_WRITE, <br />READ_ONLY_ROUTING_LIST = (COMPUTER03) )|( ALLOW_CONNECTIONS = READ_WRITE, <br />READ_ONLY_ROUTING_LIST = (COMPUTER03) )|( ALLOW_CONNECTIONS = READ_WRITE, <br />READ_ONLY_ROUTING_LIST = NONE )|プライマリ ロールでは、すべてのレプリカは読み取りを目的とした接続試行を拒否します。<br /><br /> ローカル レプリカがセカンダリ ロールで実行されている場合、読み取りを目的とした接続要求は COMPUTER03 にルーティングされます。 そのレプリカがプライマリ ロールで実行していると、読み取り専用のルーティングは無効になります。<br /><br /> この引数は省略可能です。|  
|SESSION_TIMEOUT|10|10|10|この例では、既定のセッション タイムアウト値 (10) を指定します。 この引数は省略可能です。|  
  
 最後に、新しい可用性グループの可用性グループ リスナーを作成するためのオプションの LISTENER 句を指定します。 このリスナーには、一意の DNS 名 `MyAgListenerIvP6`を指定します。 2 つのレプリカが異なるサブネット上に存在するため、リスナーは静的 IP アドレスを使用する必要があります。 WITH IP 句が、静的 IP アドレスを指定する 2 つの可用性レプリカのそれぞれについて、`2001:4898:f0:f00f::cf3c`と`2001:4898:e0:f213::4ce2`、IPv6 形式を使用します。 また、この例では、オプションの PORT 引数を使用して、 `60173` をリスナー ポートとして指定しています。  
  
```SQL
CREATE AVAILABILITY GROUP MyAg   
   WITH (  
      AUTOMATED_BACKUP_PREFERENCE = SECONDARY,  
      FAILURE_CONDITION_LEVEL  =  3,   
      HEALTH_CHECK_TIMEOUT = 600000  
       )  
  
   FOR   
      DATABASE  ThisDatabase, ThatDatabase   
   REPLICA ON   
      'COMPUTER01' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER01:5022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC,  
         BACKUP_PRIORITY = 30,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = NO,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER01:1433' ),
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = (COMPUTER03) ),  
         SESSION_TIMEOUT = 10  
         ),   
  
      'COMPUTER02' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER02:5022',  
         AVAILABILITY_MODE = SYNCHRONOUS_COMMIT,  
         FAILOVER_MODE = AUTOMATIC,  
         BACKUP_PRIORITY = 30,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = NO,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER02:1433' ),  
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = (COMPUTER03) ),  
         SESSION_TIMEOUT = 10  
         ),   
  
      'COMPUTER03' WITH   
         (  
         ENDPOINT_URL = 'TCP://COMPUTER03:5022',  
         AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
         FAILOVER_MODE =  MANUAL,  
         BACKUP_PRIORITY = 90,  
         SECONDARY_ROLE (ALLOW_CONNECTIONS = READ_ONLY,   
            READ_ONLY_ROUTING_URL = 'TCP://COMPUTER03:1433' ),  
         PRIMARY_ROLE (ALLOW_CONNECTIONS = READ_WRITE,   
            READ_ONLY_ROUTING_LIST = NONE ),  
         SESSION_TIMEOUT = 10  
         );
GO  
ALTER AVAILABIIITY GROUP [MyAg]
  ADD LISTENER ‘MyAgListenerIvP6’ ( WITH IP ( ('2001:db88:f0:f00f::cf3c'),('2001:4898:e0:f213::4ce2') ) , PORT = 60173 );   
GO  
```  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [可用性グループの作成 &#40;Transact-SQL&#41;](../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;](../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [[新しい可用性グループ] ダイアログ ボックスの使用 &#40;SQL Server Management Studio&#41;](../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;](../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>参照  
 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](../../t-sql/statements/alter-availability-group-transact-sql.md)   
 [ALTER DATABASE SET HADR &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-hadr.md)   
 [DROP AVAILABILITY GROUP &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-availability-group-transact-sql.md)   
 [Always On 可用性グループの構成 &#40; のトラブルシューティングします。SQL Server &#41;](../../database-engine/availability-groups/windows/troubleshoot-always-on-availability-groups-configuration-sql-server.md)   
 [AlwaysOn 可用性グループの概要 &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [可用性グループ リスナー、クライアント接続、およびアプリケーションのフェールオーバー &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)  
  
  

