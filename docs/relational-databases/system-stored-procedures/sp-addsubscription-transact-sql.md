---
title: sp_addsubscription (TRANSACT-SQL) |Microsoft ドキュメント
ms.date: 10/28/2015
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_addsubscription
- sp_addsubscription_TSQL
helpviewer_keywords:
- sp_addsubscription
ms.assetid: 61ddf287-1fa0-4c1a-8657-ced50cebf0e0
caps.latest.revision: 53
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 42e9a7a49aab996a26ed0514854e7f2c1db9ce0b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spaddsubscription-transact-sql"></a>sp_addsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションにサブスクリプションを追加し、サブスクライバーの状態を設定します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addsubscription [ @publication = ] 'publication'  
    [ , [ @article = ] 'article']  
    [ , [ @subscriber = ] 'subscriber' ]  
    [ , [ @destination_db = ] 'destination_db' ]  
        [ , [ @sync_type = ] 'sync_type' ]  
    [ , [ @status = ] 'status'  
        [ , [ @subscription_type = ] 'subscription_type' ]  
    [ , [ @update_mode = ] 'update_mode' ]  
    [ , [ @loopback_detection = ] 'loopback_detection' ]  
    [ , [ @frequency_type = ] frequency_type ]  
    [ , [ @frequency_interval = ] frequency_interval ]  
    [ , [ @frequency_relative_interval = ] frequency_relative_interval ]  
    [ , [ @frequency_recurrence_factor = ] frequency_recurrence_factor ]  
    [ , [ @frequency_subday = ] frequency_subday ]  
    [ , [ @frequency_subday_interval = ] frequency_subday_interval ]  
    [ , [ @active_start_time_of_day = ] active_start_time_of_day ]  
    [ , [ @active_end_time_of_day = ] active_end_time_of_day ]  
    [ , [ @active_start_date = ] active_start_date ]  
    [ , [ @active_end_date = ] active_end_date ]  
    [ , [ @optional_command_line = ] 'optional_command_line' ]  
    [ , [ @reserved = ] 'reserved' ]  
    [ , [ @enabled_for_syncmgr= ] 'enabled_for_syncmgr' ]  
    [ , [ @offloadagent= ] remote_agent_activation]  
    [ , [ @offloadserver= ] 'remote_agent_server_name' ]  
    [ , [ @dts_package_name= ] 'dts_package_name' ]  
    [ , [ @dts_package_password= ] 'dts_package_password' ]  
    [ , [ @dts_package_location= ] 'dts_package_location' ]  
    [ , [ @distribution_job_name= ] 'distribution_job_name' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @backupdevicetype = ] 'backupdevicetype' ]  
    [ , [ @backupdevicename = ] 'backupdevicename' ]  
    [ , [ @mediapassword = ] 'mediapassword' ]  
    [ , [ @password = ] 'password' ]  
    [ , [ @fileidhint = ] fileidhint ]  
    [ , [ @unload = ] unload ]  
    [ , [ @subscriptionlsn = ] subscriptionlsn ]  
    [ , [ @subscriptionstreams = ] subscriptionstreams ]  
    [ , [ @subscriber_type = ] subscriber_type ]  
    [ , [ @memory_optimized = ] memory_optimized ]  
```  
  
## <a name="arguments"></a>引数  
 [ @publication=] '*publication*'  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [ @article=] '*記事*'  
 パブリケーションがサブスクライブされるアーティクルを指定します。 *記事*は**sysname**、既定値は all です。 all に設定した場合は、そのパブリケーションのすべてのアーティクルに対してサブスクリプションが加えられます。 Oracle パブリッシャーの場合、サポートされている値は all と NULL だけです。  
  
 [ @subscriber=] '*サブスクライバー*'  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値は NULL です。  
  
 [ @destination_db=] '*destination_db*'  
 レプリケートされたデータの格納先となるデータベースの名前を指定します。 *destination_db*は**sysname**、既定値は NULL です。 Null の場合、 *destination_db*がパブリケーション データベースの名前に設定します。 Oracle パブリッシャーに対して*destination_db*指定する必要があります。 SQL Server 以外のサブスクライバー、値を指定 (default destination) の*destination_db*です。  
  
 [ @sync_type=] '*sync_type*'  
 サブスクリプションの同期の種類を指定します。 *sync_type*は**nvarchar (255)** 値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|なし|パブリッシュされたテーブルのスキーマと初期データは既にサブスクライバーにあります。<br /><br /> 注: このオプションは廃止されました。 代わりに replication support only を使用してください。|  
|automatic (既定値)|パブリッシュされたテーブルのスキーマと初期データが、最初にサブスクライバーに転送されます。|  
|replication support only|更新サブスクリプションをサポートするアーティクルのカスタム ストアド プロシージャとトリガーがサブスクライバー側で必要に応じて自動的に生成されます。 パブリッシュされたテーブルのスキーマと初期データがサブスクライバーにあることが前提となります。 ピアツーピア トランザクション レプリケーション トポロジを構成する場合は、トポロジのすべてのノードのデータが一致していることを確認してください。 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。<br /><br /> *SQL Server 以外のパブリケーションに対するサブスクリプションの場合はサポートされていません。*|  
|initialize with backup|パブリッシュされたテーブルのスキーマと初期データは、パブリケーション データベースのバックアップから取得されます。 パブリケーション データベースのバックアップにサブスクライバーがアクセスできることが前提となります。 バックアップのバックアップとメディアの種類の場所がで指定された*backupdevicename*と*backupdevicetype*です。 このオプションを使用する場合は、構成時にピアツーピア トランザクション レプリケーション トポロジを停止する必要はありません。<br /><br /> *SQL Server 以外のパブリケーションに対するサブスクリプションの場合はサポートされていません。*|  
|initialize from lsn|ピア ツー ピア トランザクション レプリケーション トポロジにノードを追加するときに使用します。 @subscriptionlsn と共に使用すると、関連するトランザクションのすべてが、新しいノードに確実にレプリケートされます。 パブリッシュされたテーブルのスキーマと初期データがサブスクライバーにあることが前提となります。 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。|  
  
> [!NOTE]  
>  システム テーブルとデータは常に転送されます。  
  
 [ @status=] '*ステータス*'  
 サブスクリプションの状態を指定します。 *ステータス*は**sysname**既定値は NULL です。 このパラメーターを明示的に設定しない場合は、レプリケーションで自動的に次のいずれかの値が設定されます。  
  
|値|Description|  
|-----------|-----------------|  
|active|サブスクリプションは初期化され、変更の準備ができています。 場合、このオプションが設定の値*sync_type*は none、initialize with backup、またはレプリケーションのサポートのみです。|  
|subscribed|サブスクリプションを初期化する必要があります。 場合、このオプションが設定の値*sync_type*は自動です。|  
  
 [ @subscription_type=] '*subscription_type*'  
 サブスクリプションの種類を指定します。 *subscription_type*は**nvarchar (4)**、既定値は push です。 push または pull に設定できます。 プッシュ サブスクリプションのディストリビューション エージェントは、ディストリビューター側に存在し、プル サブスクリプションのディストリビューション エージェントはサブスクライバーに存在します。 *subscription_type*パブリッシャーに認識されている名前付きプル サブスクリプションを作成するプルをすることができます。 詳細については、「[パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)」を参照してください。  
  
> [!NOTE]  
>  匿名サブスクリプションの場合、このストアド プロシージャを使用する必要はありません。  
  
 [ @update_mode=] '*update_mode*'  
 更新プログラムの種類です。*update_mode*は**nvarchar (30)**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|read only (既定値)|サブスクリプションは読み取り専用です。 サブスクライバーで加えられた変更はパブリッシャーに送信されません。|  
|sync tran|即時更新サブスクリプションのサポートを有効にします。 Oracle パブリッシャーに対してはサポートされていません。|  
|queued tran|サブスクリプションのキュー更新を有効にします。 サブスクライバーでデータを変更し、キューに格納し、それをパブリッシャーに配信することができます。 Oracle パブリッシャーに対してはサポートされていません。|  
|failover|キュー更新をフェールオーバーとするサブスクリプションの即時更新を有効にします。 サブスクライバーでデータを変更し、それを直ちにパブリッシャーに配信することができます。 パブリッシャーとサブスクライバーが接続されていない場合は、更新モードを変更することにより、サブスクライバーで加えられたデータの変更を、サブスクライバーとパブリッシャーが接続されるまで、キューに格納することができます。 Oracle パブリッシャーに対してはサポートされていません。|  
|queued failover|即時更新モードへの変更が可能なキュー更新サブスクリプションとしてサブスクリプションを有効にします。 サブスクライバーでデータを変更し、サブスクライバーとパブリッシャーの間の接続が確立されるまで、その変更をキューに格納することができます。 継続的な接続が確立されると、更新モードを即時更新に変更できます。 Oracle パブリッシャーに対してはサポートされていません。|  
  
 値 synctran および queued tran は使用できないことにサブスクライブされるパブリケーションで DTS を許可する場合に注意してください。  
  
 [ @loopback_detection=] '*loopback_detection*'  
 ディストリビューション エージェントがサブスクライバーで発生したトランザクションをサブスクライバーに戻すかどうかを指定します。 *loopback_detection*は**nvarchar (5)**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|true|ディストリビューション エージェントは、サブスクライバーで発生したトランザクションをサブスクライバーに戻しません。 双方向トランザクション レプリケーションで使用されます。 詳細については、「 [双方向トランザクション レプリケーション](../../relational-databases/replication/transactional/bidirectional-transactional-replication.md)」を参照してください。|  
|オプション|ディストリビューション エージェントは、サブスクライバーで発生したトランザクションをサブスクライバーに戻します。|  
|NULL (既定値)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバーの場合は true、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーの場合は false に自動設定されます。|  
  
 [ @frequency_type=] *frequency_type*  
 ディストリビューション タスクをスケジュールに組み込む頻度を指定します。 *frequency_type* int であり、これらの値のいずれかになります。  
  
|値|Description|  
|-----------|-----------------|  
|1|指定日時|  
|2|[要求時]|  
|4|毎日。|  
|8|毎週。|  
|16|毎月。|  
|32|月単位|  
|64 (既定値)|自動的に起動|  
|128|定期的|  
  
 [ @frequency_interval=] *frequency_interval*  
 設定した頻度に適用する値は、 *frequency_type*です。 *frequency_interval*は**int**、既定値は NULL です。  
  
 [ @frequency_relative_interval=] *frequency_relative_interval*  
 ディストリビューション エージェントを実行する日付です。 このパラメーターが使用されるときに*frequency_type* 32 (月単位) に設定されています。 *frequency_relative_interval*は**int**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|1|First|  
|2|第 2 週|  
|4|第 3 週|  
|8|第 4 週|  
|16|Last|  
|NULL (既定値)||  
  
 [ @frequency_recurrence_factor=] *frequency_recurrence_factor*  
 によって使用される定期実行係数*frequency_type*です。 *frequency_recurrence_factor*は**int**、既定値は NULL です。  
  
 [ @frequency_subday=] *frequency_subday*  
 定義した期間にスケジュールを組み直す頻度を分単位で指定します。 *frequency_subday*は**int**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|1|1 回。|  
|2|第 2 週|  
|4|Minute|  
|8|Hour|  
|NULL||  
  
 [ @frequency_subday_interval=] *frequency_subday_interval*  
 間隔は、 *frequency_subday*です。 *frequency_subday_interval*は**int**、既定値は NULL です。  
  
 [ @active_start_time_of_day=] *active_start_time_of_day*  
 ディストリビューション エージェントを最初にスケジュール設定する時刻を HHMMSS 形式で指定します。 *active_start_time_of_day*は**int**、既定値は NULL です。  
  
 [ @active_end_time_of_day=] *active_end_time_of_day*  
 ディストリビューション エージェントのスケジュール設定を停止する時刻を HHMMSS 形式で指定します。 *active_end_time_of_day*は**int**、既定値は NULL です。  
  
 [ @active_start_date=] *active_start_date*  
 ディストリビューション エージェントを最初にスケジュール設定する日付を YYYYMMDD 形式で指定します。 *active_start_date*は**int**、既定値は NULL です。  
  
 [ @active_end_date=] *active_end_date*  
 ディストリビューション エージェントのスケジュール設定を停止する日付を YYYYMMDD 形式で指定します。 *active_end_date*は**int**、既定値は NULL です。  
  
 [ @optional_command_line=] '*optional_command_line*'  
 省略可能な実行用のコマンド プロンプトを指定します。 *optional_command_line*は**nvarchar (4000)**、既定値は NULL です。  
  
 [ @reserved=] '*予約*'  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @enabled_for_syncmgr=] '*enabled_for_syncmgr*'  
 使用、サブスクリプションを同期させるかどうかが[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows 同期マネージャーです。 *enabled_for_syncmgr*は**nvarchar (5)**、既定値は FALSE。 false の場合、サブスクリプションは Windows 同期マネージャーに登録されません。 true の場合、サブスクリプションは Windows 同期マネージャーに登録され、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を起動せずに同期させることができます。 Oracle パブリッシャーに対してはサポートされていません。  
  
 [ @offloadagent= ] '*remote_agent_activation*'  
 エージェントをリモートから起動できることを指定します。 *remote_agent_activation*は**ビット**既定値は 0 です。  
  
> [!NOTE]  
>  このパラメーターは廃止されており、スクリプトの旧バージョンとの互換性のためのみ保持します。  
  
 [ @offloadserver= ] '*remote_agent_server_name*'  
 リモート起動に使用されるサーバーのネットワーク名を指定します。 *remote_agent_server_name*は**sysname**、既定値は NULL です。  
  
 [ @dts_package_name= ] '*dts_package_name*'  
 データ変換サービス (DTS) パッケージの名前。 *dts_package_name*は、 **sysname**既定値は NULL です。 たとえば、DTSPub_Package というパッケージを指定するには、パラメーターを `@dts_package_name = N'DTSPub_Package'` にする必要があります。 プッシュ サブスクリプションでは、このパラメーターを使用できます。 プル サブスクリプションに DTS パッケージ情報を追加するには、sp_addpullsubscription_agent を使用します。  
  
 [ @dts_package_password= ] '*dts_package_password*'  
 パッケージのパスワード (ある場合) を指定します。 *dts_package_password*は**sysname**既定値は NULL です。  
  
> [!NOTE]  
>  場合は、パスワードを指定する必要があります*dts_package_name*を指定します。  
  
 [ @dts_package_location= ] '*dts_package_location*'  
 パッケージの場所を指定します。 *dts_package_location*は、 **nvarchar (12)**、既定値は DISTRIBUTOR です。 パッケージの場所としては、distributor または subscriber を指定できます。  
  
 [ @distribution_job_name= ] '*distribution_job_name*'  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [ @publisher=] '*パブリッシャー*'  
 指定以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*を指定しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
 [ @backupdevicetype=] '*backupdevicetype*'  
 バックアップからサブスクライバーを初期化する際に使用するバックアップ デバイスの種類を指定します。 *backupdevicetype*は**nvarchar (20)**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|logical (既定値)|バックアップ デバイスは論理デバイスです。|  
|disk|バックアップ デバイスはディスク ドライブです。|  
|tape|バックアップ デバイスはテープ ドライブです。|  
  
 *backupdevicetype*場合のみ使用*sync_method*が initialize_with_backup に設定します。  
  
 [ @backupdevicename=] '*backupdevicename*'  
 バックアップからサブスクライバーを初期化する際に使用するデバイスの名前を指定します。 *backupdevicename*は**nvarchar (1000)**、既定値は NULL です。  
  
 [ @mediapassword=] '*mediapassword*'  
 メディア セットのパスワードを指定します (メディアをフォーマットしたときにパスワードを設定した場合)。 *mediapassword*は**sysname**既定値は NULL です。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 [ @password= ] '*password*'  
 バックアップのパスワードを指定します (バックアップを作成したときにパスワードを設定した場合)。 *パスワード*は**sysname**既定値は NULL です。  
  
 [ @fileidhint= ] *fileidhint*  
 復元するバックアップ セットの序数値を識別します。 *fileidhint*は**int**既定値は NULL です。  
  
 [ @unload= ] *unload*  
 バックアップからの初期化が完了した後テープ バックアップ デバイスをアンロードするかどうかを指定します。 *アンロード*は**ビット**で既定値は 1 です。 1 は、テープがアンロードされることを指定します。 *アンロード*場合のみ使用*backupdevicetype*テープします。  
  
 [ @subscriptionlsn= ] *subscriptionlsn*  
 サブスクリプションでピア ツー ピア トランザクション レプリケーション トポロジのノードへの変更の配信を開始するログ シーケンス番号 (LSN) を指定します。 使用される、 @sync_type initialize from lsn を新しいノードに関連するすべてのトランザクションがレプリケートされるかどうかを確認の値。 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。  
  
 [ @subscriptionstreams= ] *subscriptionstreams*  
 単一のスレッドを使用しているときに、トランザクションに関連したさまざまな特性を維持しながら、サブスクライバーに対してバッチ変更を適用することのできる、ディストリビューション エージェントあたりの接続数です。 *subscriptionstreams*は**tinyint**既定値は NULL です。 サポートされている値の範囲は 1 ～ 64 です。 このパラメーターは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバー、Oracle パブリッシャー、およびピアツーピア サブスクリプションではサポートされていません。 サブスクリプション ストリームが使用されるたびに、msreplication_subscriptions テーブルに行が追加され (ストリームごとに 1 行)、agent_id が NULL に設定されます。  
  
> [!NOTE]  
>  Subscriptionstreams は、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を渡すように構成されたアーティクルでは使用できません。 subscriptionstreams を使用するには、代わりにストアド プロシージャの呼び出しを渡すようにアーティクルを構成します。  
  
 [ @subscriber_type=] *subscriber_type*  
 サブスクライバーの種類を指定します。 *subscriber_type*は**tinyint**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|0 (既定値)|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サブスクライバー|  
|1|ODBC データ ソース サーバー|  
|2|[!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet データベース|  
|3|OLE DB プロバイダー|  
  
 [ @memory_optimized=] *memory_optimized*  
 サブスクリプションがメモリ最適化テーブルをサポートしていることを示します。 *memory_optimized*は**ビット**場所 1 が true (サブスクリプションでは、メモリ最適化テーブルをサポートします)、します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 sp_addsubscription は、スナップショット レプリケーションおよびトランザクション レプリケーションで使用します。  
  
 sp_addsubscription が固定サーバー ロール sysadmin のメンバーによってプッシュ サブスクリプションを作成するために実行されると、ディストリビューション エージェントのジョブが暗黙的に作成され、SQL Server エージェント サービス アカウントで実行されます。 実行することをお勧め[sp_addpushsubscription_agent](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)に対して異なるエージェントに固有の Windows アカウントの資格情報を指定して@job_loginと@job_passwordです。 詳細については、「 [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md)」を参照してください。  
  
 sp_addsubscription は、ODBC サブスクライバーおよび OLE DB サブスクライバーが次のパブリケーションにアクセスするのを禁止します。  
  
-   ネイティブで作成された*sync_method*への呼び出しで[sp_addpublication](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)です。  
  
-   アーティクルを持つパブリケーションに追加された、 [sp_addarticle](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)ストアド プロシージャで、 *pre_creation_cmd*パラメーターに値 3 (切り捨て)。  
  
-   設定しようとしています。 *update_mode* tran を同期します。  
  
-   パラメーター化されたステートメントを使用するように構成されたアーティクルを含むパブリケーション。  
  
 さらに、パブリケーションがある場合、 *allow_queued_tran*オプションを設定する (これは、パブリッシャーが適用されるまで、サブスクライバーの変更のキューをにより) true の場合、アーティクルに timestamp 列がスクリプト化として**タイムスタンプ**、その列に対する変更がサブスクライバーに送信されます。 サブスクライバーは、タイムスタンプ列値を生成し、更新します。 ODBC または OLE DB サブスクライバーの場合は、sp_addsubscription は失敗を持つパブリケーションにサブスクライブしようとしましたが場合*allow_queued_tran* true とタイムスタンプ列を持つアーティクルに設定します。  
  
 サブスクリプションに DTS パッケージが使用していない場合に設定されているパブリケーションにサブスクライブできません*allow_transformable_subscriptions*です。 パブリケーションのテーブルを DTS サブスクリプションと非 DTS サブスクリプションの両方にレプリケートする必要がある場合は、サブスクリプションの種類ごとに別々の 2 つのパブリケーションを作成する必要があります。  
  
 **sync_type** オプション *replication support only*、 *initialize with backup*、または *initialize from lsn*を選択した場合、 **sp_addsubscription**の実行後にログ リーダー エージェントを実行して、スクリプトの設定がディストリビューション データベースに書き込まれるようにする必要があります。 ログ リーダー エージェントが、 **sysadmin** 固定サーバー ロールのメンバーであるアカウントで実行されている必要があります。 **sync_type** オプションが *Automatic*に設定されている場合、特別なログ リーダー エージェントの操作は必要ありません。  
  
## <a name="permissions"></a>権限  
 sp_addsubscription を実行できるのは、固定サーバー ロール sysadmin または固定データベース ロール db_owner のメンバーだけです。 プル サブスクリプションの場合、パブリケーションのアクセス リストにログインのあるユーザーは sp_addsubscription を実行できます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_addtranpushsubscription_agent](../../relational-databases/replication/codesnippet/tsql/sp-addsubscription-trans_1.sql)]  
  
## <a name="see-also"></a>参照  
 [ssSDSFull](../../relational-databases/replication/create-a-push-subscription.md)   
 [SQL Server 以外のサブスクライバーのサブスクリプションの作成](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addpushsubscription_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpushsubscription-agent-transact-sql.md)   
 [sp_changesubstatus &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubstatus-transact-sql.md)   
 [sp_dropsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)   
 [sp_helpsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
