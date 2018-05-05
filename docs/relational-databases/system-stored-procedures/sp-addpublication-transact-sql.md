---
title: sp_addpublication (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_addpublication_TSQL
- sp_addpublication
helpviewer_keywords:
- sp_addpublication
ms.assetid: c7167ed1-2b7e-4824-b82b-65f4667c4407
caps.latest.revision: 69
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 59fcdcebd8c8397de2669491d4ea18cb38cfc853
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spaddpublication-transact-sql"></a>sp_addpublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  スナップショット パブリケーションまたはトランザクション パブリケーションを作成します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addpublication [ @publication = ] 'publication'  
    [ , [ @taskid = ] tasked ]  
    [ , [ @restricted = ] 'restricted' ]  
    [ , [ @sync_method = ] 'sync_method' ]  
    [ , [ @repl_freq = ] 'repl_freq' ]  
    [ , [ @description = ] 'description' ]  
    [ , [ @status = ] 'status' ]  
    [ , [ @independent_agent = ] 'independent_agent' ]  
    [ , [ @immediate_sync = ] 'immediate_sync' ]  
    [ , [ @enabled_for_internet = ] 'enabled_for_internet' ]  
    [ , [ @allow_push = ] 'allow_push'  
    [ , [ @allow_pull = ] 'allow_pull' ]  
    [ , [ @allow_anonymous = ] 'allow_anonymous' ]  
    [ , [ @allow_sync_tran = ] 'allow_sync_tran' ]  
    [ , [ @autogen_sync_procs = ] 'autogen_sync_procs' ]  
    [ , [ @retention = ] retention ]  
    [ , [ @allow_queued_tran= ] 'allow_queued_updating' ]  
    [ , [ @snapshot_in_defaultfolder= ] 'snapshot_in_default_folder' ]  
    [ , [ @alt_snapshot_folder= ] 'alternate_snapshot_folder' ]  
    [ , [ @pre_snapshot_script= ] 'pre_snapshot_script' ]  
    [ , [ @post_snapshot_script= ] 'post_snapshot_script' ]  
    [ , [ @compress_snapshot= ] 'compress_snapshot' ]  
    [ , [ @ftp_address = ] 'ftp_address' ]  
    [ , [ @ftp_port= ] ftp_port ]  
    [ , [ @ftp_subdirectory = ] 'ftp_subdirectory' ]  
    [ , [ @ftp_login = ] 'ftp_login' ]  
    [ , [ @ftp_password = ] 'ftp_password' ]  
    [ , [ @allow_dts = ] 'allow_dts' ]  
    [ , [ @allow_subscription_copy = ] 'allow_subscription_copy' ]  
    [ , [ @conflict_policy = ] 'conflict_policy' ]  
    [ , [ @centralized_conflicts = ] 'centralized_conflicts' ]   
    [ , [ @conflict_retention = ] conflict_retention ]  
    [ , [ @queue_type = ] 'queue_type' ]  
    [ , [ @add_to_active_directory = ] 'add_to_active_directory' ]  
    [ , [ @logreader_job_name = ] 'logreader_agent_name' ]  
    [ , [ @qreader_job_name = ] 'queue_reader_agent_name' ]  
    [ , [ @publisher = ] 'publisher' ]   
    [ , [ @allow_initialize_from_backup = ] 'allow_initialize_from_backup' ]  
    [ , [ @replicate_ddl = ] replicate_ddl ]  
    [ , [ @enabled_for_p2p = ] 'enabled_for_p2p' ]  
    [ , [ @publish_local_changes_only = ] 'publish_local_changes_only' ]  
    [ , [ @enabled_for_het_sub = ] 'enabled_for_het_sub' ]  
    [ , [ @p2p_conflictdetection = ] 'p2p_conflictdetection' ]  
    [ , [ @p2p_originator_id = ] p2p_originator_id  
    [ , [ @p2p_continue_onconflict = ] 'p2p_continue_onconflict'  
    [ , [ @allow_partition_switch = ] 'allow_partition_switch'  
    [ , [ @replicate_partition_switch = ]'replicate_partition_switch'  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 作成するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。 この名前は、データベース内で一意であることが必要です。  
  
 [  **@taskid=**] *taskid*  
 旧バージョンとの互換性のためです。 サポートされています。使用して[sp_addpublication_snapshot &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)です。  
  
 [  **@restricted=**] **'***制限***'**  
 旧バージョンとの互換性のためです。 サポートされています。使用して*default_access*です。  
  
 [  **@sync_method=**] *' sync_method * * * '**  
 同期モードを指定します。 *sync_method*は**nvarchar (13)** 値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**native**|すべてのテーブルのネイティブ モード BCP 出力を作成する。 *Oracle パブリッシャーに対してサポートされていません。*です。|  
|**character**|すべてのテーブルのキャラクタモード BCP 出力を作成する。 *Oracle パブリッシャーの場合、* **文字***はスナップショット レプリケーションでのみ有効*です。|  
|**同時実行**|すべてのテーブルのネイティブ モード BCP 出力を作成するが、スナップショット中はテーブルをロックしない。 トランザクション パブリケーションでのみサポートされます。 *Oracle パブリッシャーに対してサポートされていません。*です。|  
|**concurrent_c**|すべてのテーブルのキャラクタモードの BCP 出力を作成するが、スナップショット中はテーブルをロックしない。 トランザクション パブリケーションでのみサポートされます。|  
|**データベース スナップショット**|データベース スナップショットから、すべてのテーブルのネイティブ モードの一括コピー プログラム出力を作成します。 データベース スナップショットは、すべてのエディションで利用可能な[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。|  
|**データベース スナップショットの文字**|データベース スナップショットから、すべてのテーブルのキャラクター モードの一括コピー プログラム出力を作成します。 データベース スナップショットは、すべてのエディションで利用可能な[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の各エディションでサポートされる機能の一覧については、「 [SQL Server 2016 の各エディションがサポートする機能](~/sql-server/editions-and-supported-features-for-sql-server-2016.md)」を参照してください。|  
|NULL (既定値)|既定値は**ネイティブ**の[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーの場合、既定値は**文字**ときの値*repl_freq*は**スナップショット**にされ、 **concurrent_c**その他の場合。|  
  
 [  **@repl_freq=**] **'***repl_freq***'**  
 レプリケーションの頻度などの型は、 *repl_freq*は**nvarchar (10)** 値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**継続的な**(既定値)|すべてのログベースのトランザクションの出力をパブリッシュする。 非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーの場合、このことが必要*sync_method*に設定されている**concurrent_c**です。|  
|**スナップショット**|スケジュールされた同期イベントのみをパブリッシュする。 非[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーの場合、このことが必要*sync_method*に設定されている**文字**です。|  
  
 [  **@description=**] **'***説明***'**  
 パブリケーションに関する説明を指定します (省略可能)。 *説明*は**nvarchar (255)**、既定値は NULL です。  
  
 [  **@status=**] **'***ステータス***'**  
 パブリケーション データを使用できるかどうかを指定します。 *ステータス*は**nvarchar (8)** 値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**アクティブ**|サブスクライバーでパブリケーション データを直ちに使用できる。|  
|**非アクティブな**(既定値)|パブリケーションが最初に作成されたときは、サブスクライバーでパブリケーション データを使用できない (サブスクライブすることはできますが、サブスクリプションは処理されません)。|  
  
 *Oracle パブリッシャーに対してサポートされていません。*です。  
  
 [  **@independent_agent=**] **'***independent_agent***'**  
 このパブリケーションに対して、スタンドアロン ディストリビューション エージェントが存在するかどうかを指定します。 *independent_agent*は**nvarchar (5)**、既定値は FALSE。 場合**true**、このパブリケーション用のスタンドアロン ディストリビューション エージェントが存在します。 場合**false**パブリケーションでは共有ディストリビューション エージェントを使用、およびパブリッシャー データベース/サブスクライバー データベースの各ペアが 1 つの共有エージェントです。  
  
 [  **@immediate_sync=**] **'***immediate_synchronization***'**  
 スナップショット エージェントが実行されるたびに、パブリケーションに対して同期ファイルが作成されるかどうかを指定します。 *immediate_synchronization*は**nvarchar (5)**、既定値は FALSE。 場合**true**、同期ファイルが作成またはスナップショット エージェントを実行するたびに再作成します。 サブスクリプションが作成される前にスナップショット エージェントが完了していれば、サブスクライバーでは直ちに同期ファイルを取得できます。 新しいサブスクリプションは、最近実行されたスナップショット エージェントによって生成された最新の同期ファイルを取得します。 *independent_agent*する必要があります**true**の*immediate_synchronization*する**true**です。 場合**false**、新しいサブスクリプションがある場合にのみ、同期ファイルが作成されます。 呼び出す必要があります[sp_addsubscription](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md)サブスクリプションごとに、既存のパブリケーションを段階的に新しいアーティクルを追加するとします。 サブスクリプションの後、スナップショット エージェントが起動して完了するまでは、サブスクライバーでは同期ファイルを取得できません。  
  
 [  **@enabled_for_internet=**] **'***enabled_for_internet***'**  
 パブリケーションをインターネット対応にするかどうかを指定し、サブスクライバーへのスナップショット ファイルの転送にファイル転送プロトコル (FTP) を使用できるかどうかを決定します。 *enabled_for_internet*は**nvarchar (5)**、既定値は FALSE。 場合**true**パブリケーションの同期ファイルは、C:\Program files \microsoft SQL Server\MSSQL\MSSQL.x\Repldata\Ftp ディレクトリに格納されます。 ユーザーは Ftp ディレクトリを作成する必要があります。  
  
 [  **@allow_push=**] **'***allow_push***'**  
 特定のパブリケーションに対して、プッシュ サブスクリプションを作成できるかどうかを指定します。 *allow_push*は**nvarchar (5)** TRUE の場合、既定値は、パブリケーションに対してプッシュ サブスクリプションを許可します。  
  
 [  **@allow_pull=**] **'***allow_pull***'**  
 特定のパブリケーションに対して、プル サブスクリプションを作成できるかどうかを指定します。 *allow_pull*は**nvarchar (5)**、既定値は FALSE。 場合**false**、パブリケーションに対してプル サブスクリプションが許可されていません。  
  
 [  **@allow_anonymous=**] **'***allow_anonymous***'**  
 特定のパブリケーションに対して、匿名サブスクリプションを作成できるかどうかを指定します。 *allow_anonymous*は**nvarchar (5)**、既定値は FALSE。 場合**true**、 *immediate_synchronization*にも設定する必要があります**true**です。 場合**false**、パブリケーションに対して匿名サブスクリプションは許可されていません。  
  
 [  **@allow_sync_tran=**] **'***allow_sync_tran***'**  
 パブリケーションでサブスクリプションの即時更新を許可するかどうかを指定します。 *allow_sync_tran*は**nvarchar (5)**、既定値は FALSE。 **true**は*Oracle パブリッシャーに対してサポートされていません*です。  
  
 [  **@autogen_sync_procs=**] **'***autogen_sync_procs***'**  
 更新サブスクリプションの同期ストアド プロシージャがパブリッシャーで生成されるかどうかを指定します。 *autogen_sync_procs*は**nvarchar (5)** 値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**true**|更新サブスクリプションが有効の場合、自動的に生成される。|  
|**false**|更新サブスクリプションが無効の場合、または Oracle パブリッシャーの場合、自動的に生成される。|  
|NULL (既定値)|既定値は**true**更新サブスクリプションが有効になっているときに、 **false**とサブスクリプションの更新が有効になっていません。|  
  
> [!NOTE]  
>  ユーザーがの値を指定した*autogen_sync_procs*の指定した値によってオーバーライドされます*allow_queued_tran*と*allow_sync_tran*です。  
  
 [  **@retention=**]*保有期間*  
 サブスクリプション処理の保有期間を時間数で指定します。 *保有期間*は**int**の既定値は 336 時間です。 サブスクリプションは、保有期間内に非アクティブになると、期限切れとなって削除されます。 この値には、パブリッシャーによって使用されるディストリビューション データベースの最大保有期間を上回る値を指定することもできます。 場合**0**、よく知られているパブリケーションに対するサブスクリプションが決して期限切れし、期限切れサブスクリプション クリーンアップ エージェントによって削除されます。  
  
 [  **@allow_queued_tran=** ] **'***allow_queued_updating***'**  
 変更をパブリッシャーに適用できるようになるまで、サブスクライバーでの変更のキュー登録を有効または無効にします。 *allow_queued_updating*は**nvarchar (5)** 既定値は FALSE。 場合**false**、サブスクライバーの変更はキュー登録されません。 **true**は*Oracle パブリッシャーに対してサポートされていません*です。  
  
 [  **@snapshot_in_defaultfolder=** ] **'***snapshot_in_default_folder***'**  
 スナップショット ファイルを既定のフォルダーに格納するかどうかを指定します。 *snapshot_in_default_folder*は**nvarchar (5)** 既定値は TRUE です。 場合**true**、スナップショット ファイルは既定のフォルダーにあります。 場合**false**、スナップショット ファイルで指定された代替位置に格納されている*alternate_snapshot_folder*です。 代替位置は、他のサーバー、ネットワーク ドライブ、CD-ROM やリムーバブル ディスクなどのリムーバブル メディアに設定できます。 スナップショット ファイルを FTP サイトに保存し、後でサブスクライバーで取得することもできます。 このパラメーターが true にしてもに、場所があることができますに注意してください、 **@alt_snapshot_folder**パラメーター。 これらのパラメーターを組み合わせて指定した場合、スナップショット ファイルは、既定のフォルダーと代替位置の両方に格納されます。  
  
 [  **@alt_snapshot_folder=** ] **'***alternate_snapshot_folder***'**  
 スナップショットの代替フォルダーの場所を指定します。 *alternate_snapshot_folder*は**nvarchar (255)** 既定値は NULL です。  
  
 [  **@pre_snapshot_script=** ] **'***pre_snapshot_script***'**  
 ポインターを指定します、 **.sql**ファイルの場所。 *pre_snapshot_script*は**nvarchar (255)、**既定値は NULL です。 ディストリビューション エージェントでは、サブスクライバーでスナップショットが適用されるとき、レプリケートされたオブジェクト スクリプトよりも前に、プリスナップショット スクリプトが実行されます。 このスクリプトは、サブスクリプション データベースへの接続時にディストリビューション エージェントによって使用されるセキュリティ コンテキストで実行されます。  
  
 [  **@post_snapshot_script=** ] **'***post_snapshot_script***'**  
 ポインターを指定します、 **.sql**ファイルの場所。 *post_snapshot_script*は**nvarchar (255)**、既定値は NULL です。 最初の同期時、ディストリビューション エージェントでは、他のすべてのレプリケートされたオブジェクト スクリプトとデータが適用された後、ポスト スナップショット スクリプトが実行されます。 このスクリプトは、サブスクリプション データベースへの接続時にディストリビューション エージェントによって使用されるセキュリティ コンテキストで実行されます。  
  
 [  **@compress_snapshot=** ] **'***compress_snapshot***'**  
 指定に書き込まれたスナップショット、 **@alt_snapshot_folder**の場所を圧縮するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB 形式です。 *compress_snapshot*は**nvarchar (5)**、既定値は FALSE。 **false**指定したスナップショットは圧縮されません。**true**スナップショットが圧縮されることを指定します。 2 GB を超えるスナップショット ファイルは圧縮できません。 圧縮されたスナップショット ファイルは、ディストリビューション エージェントが実行される場所に展開されます。プル サブスクリプションでは通常、ファイルがサブスクライバーで展開されるよう、圧縮されたスナップショットが使用されます。 既定のフォルダー内のスナップショットは圧縮できません。  
  
 [  **@ftp_address =** ] **'***ftp_address***'**  
 ディストリビューター用の FTP サービスのネットワーク アドレスです。 *ftp_address*は**sysname**、既定値は NULL です。 ここでは、サブスクライバーのディストリビューション エージェントまたはマージ エージェントがパブリケーション スナップショット ファイルを取得する場所を指定します。 各パブリケーションを別に持つことができますので、このプロパティはパブリケーションごとに格納される、 *ftp_address*です。 パブリケーションでは、FTP を使用したスナップショットの配布がサポートされている必要があります。  
  
 [  **@ftp_port=** ] *ftp_port*  
 ディストリビューター用の FTP サービスのポート番号です。 *ftp_port*は**int**、既定値は 21 です。 サブスクライバーのディストリビューション エージェントまたはマージ エージェントがパブリケーション スナップショット ファイルを取得する場所を示します。 このプロパティはパブリケーションごとに格納されるに個々 のパブリケーションが持つことができます独自*ftp_port*です。  
  
 [  **@ftp_subdirectory =** ] **'***ftp_subdirectory***'**  
 パブリケーションで FTP を利用したスナップショット配布がサポートされている場合に、サブスクライバーのディストリビューション エージェントまたはマージ エージェントがパブリケーション スナップショット ファイルを取得する場所。 *ftp_subdirectory*は**nvarchar (255)**、既定値は NULL です。 このプロパティはパブリケーションごとに格納されるに個々 のパブリケーションが持つことができます独自*ftp_subdirctory*または NULL 値を持つ、サブディレクトリがないように選択します。  
  
 [  **@ftp_login =** ] **'***ftp_login***'**  
 FTP サービスに接続するときに使用するユーザー名です。 *ftp_login*は**sysname**匿名の既定値です。  
  
 [  **@ftp_password =** ] **'***ftp_password***'**  
 FTP サービスに接続するときに使用するユーザー パスワードです。 *ftp_password*は**sysname**、既定値は NULL です。  
  
 [  **@allow_dts =** ] **'***allow_dts を含む***'**  
 パブリケーションでデータを変換できるかどうかを指定します。 サブスクリプションを作成するときに DTS パッケージを指定できます。 *allow_transformable_subscriptions*は**nvarchar (5)** 既定値は FALSE には、これはいない DTS 変換が許可されます。 ときに*allow_dts を含む*が true の場合、 *sync_method*設定する必要がいずれかに**文字**または**concurrent_c**です。  
  
 **true**は*Oracle パブリッシャーに対してサポートされていません*です。  
  
 [  **@allow_subscription_copy =** ] **'***allow_subscription_copy***'**  
 このパブリケーションにサブスクライブするサブスクリプション データベースをコピーする機能を有効または無効にします。 *allow_subscription_copy*は**nvarchar (5)**、既定値は FALSE。  
  
 [  **@conflict_policy =** ] **'***conflict_policy***'**  
 キュー更新サブスクライバー オプションを使用するときの競合の解決方法。 *conflict_policy*は**nvarchar (100)** 既定値は NULL の場合、値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**pub wins**|パブリッシャーを優先。|  
|**sub reinit**|サブスクライバーを再初期化。|  
|**sub wins**|サブスクライバーを優先。|  
|NULL (既定値)|NULL の場合、およびパブリケーションがスナップショット パブリケーションの場合、既定のポリシーは次のようになります。 **sub reinit**です。 NULL で、パブリケーションがスナップショット パブリケーションでない場合、既定値は次のようになります。 **pub wins**です。|  
  
 *Oracle パブリッシャーに対してサポートされていません。*です。  
  
 [  **@centralized_conflicts =** ] **'***centralized_conflicts***'**  
 パブリッシャーに競合レコードを格納するかどうかを指定します。 *centralized_conflicts*は**nvarchar (5)**、既定値は TRUE です。 場合**true**、競合レコードはパブリッシャーに保存します。 場合**false**、競合レコードは、パブリッシャーの両方と、競合の原因となったサブスクライバーで格納します。 *Oracle パブリッシャーに対してサポートされていません。*です。  
  
 [  **@conflict_retention =** ] *conflict_retention*  
 競合の保有期間の日数を指定します。 これは、ピア ツー ピア トランザクション レプリケーションおよびキュー更新サブスクリプションの競合メタデータが格納される期間です。 *conflict_retention*は**int**、既定値は 14 です。 *Oracle パブリッシャーに対してサポートされていません。*です。  
  
 [  **@queue_type =** ] **'***queue_type***'**  
 使用されるキューの種類。 *queue_type*は**nvarchar (10)**、既定値は NULL、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**sql**|使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクションを格納します。|  
|NULL (既定値)|既定値は**sql**、使用するように指定する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクションを格納します。|  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (MSMQ) の使用は現在サポートされていません。 値を指定する**msmq** 、警告が発生し、レプリケーションが自動的に値を設定**sql**です。  
  
 *Oracle パブリッシャーに対してサポートされていません。*です。  
  
 [  **@add_to_active_directory =** ] **' * * * 追加**_**to_active_directory * * * '**  
 このパラメーターは、旧バージョンのスクリプトとの互換性を保つために用意されており、非推奨とされます。 パブリケーション情報を不要になった追加することができます、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory です。  
  
 [  **@logreader_job_name =** ] **'***logreader_agent_name***'**  
 既存のエージェント ジョブの名前を指定します。 *logreader_agent_name*は**sysname**既定値は NULL です。 このパラメーターは、ログ リーダー エージェントで、新しく作成されるジョブではなく既存のジョブが使用される場合にのみ指定します。  
  
 [  **@qreader_job_name =** ] **'***queue_reader_agent_name***'**  
 既存のエージェント ジョブの名前を指定します。 *queue_reader_agent_name*は**sysname**既定値は NULL です。 このパラメーターは、キュー リーダー エージェントで、新しく作成されるジョブではなく既存のジョブが使用される場合にのみ指定します。  
  
 [  **@publisher =** ] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*にパブリケーションを追加するときに使用しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
 [  **@allow_initialize_from_backup =** ] **'***allow_initialize_from_backup***'**  
 サブスクライバーでは、最初のスナップショットではなくバックアップから、このパブリケーションへのサブスクリプションを初期化できるかどうかを示します。 *allow_initialize_from_backup*は**nvarchar (5)**、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**true**|バックアップからの初期化を有効にする。|  
|**false**|バックアップからの初期化を無効にする。|  
|NULL (既定値)|既定値は**true** 、ピア ツー ピア レプリケーション トポロジでパブリケーションのおよび**false**他のすべてのパブリケーション。|  
  
 詳細については、「 [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。  
  
> [!WARNING]  
>  サブスクライバー データの欠落を回避するために、 **sp_addpublication** で `@allow_initialize_from_backup = N'true'`を使用する場合は、常に `@immediate_sync = N'true'`を使用します。  
  
 [  **@replicate_ddl =** ] *replicate_ddl*  
 スキーマ レプリケーションがパブリケーションに対してサポートされているかどうかを示します。 *replicate_ddl*は**int**、既定値は**1**の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーと**0**の以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 **1** 、パブリッシャー側で実行されるデータ定義言語 (DDL) ステートメントがレプリケートされることを示すと**0** DDL ステートメントがレプリケートされないことを示します。 *スキーマ レプリケーションが Oracle パブリッシャーに対してサポートされていません。* 詳細については、「[パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)」を参照してください。  
  
 *@replicate_ddl* DDL ステートメントは、列を追加するときは、パラメーターを有効にします。 *@replicate_ddl* DDL ステートメントが変更または次の理由により、列を削除すると、パラメーターは無視されます。  
  
-   列を削除すると場合、は、ディストリビューション エージェントは失敗が発生すると、削除された列を含むから新しい DML ステートメントを防ぐために sysarticlecolumns を更新する必要があります。 *@replicate_ddl*レプリケーションは、スキーマの変更を常にレプリケートする必要がありますので、パラメーターは無視されます。  
  
-   列が変更される場合は、ソースのデータ型または NULL 値の許容属性が変更され、サブスクライバーにあるテーブルと互換性のない値が DML ステートメントに含まれる可能性があります。 そうした DML ステートメントは、ディストリビューション エージェントが失敗する原因となる場合があります。 *@replicate_ddl*レプリケーションは、スキーマの変更を常にレプリケートする必要がありますので、パラメーターは無視されます。  
  
-   ときの DDL ステートメントは、新しい列を追加、sysarticlecolumns では、新しい列が含まれません。 DML ステートメントによって、新しい列のデータがレプリケートされることはありません。 DDL をレプリケートするかしないかのどちらかが許容されるため、パラメーターは有効になります。  
  
 [  **@enabled_for_p2p =** ] **'***enabled_for_p2p***'**  
 ピア ツー ピア レプリケーション トポロジでパブリケーションを使用できるようにします。 *enabled_for_p2p*は**nvarchar (5)**、既定値は FALSE。 **true**パブリケーションがピア ツー ピア レプリケーションをサポートしていることを示します。 設定するときに*enabled_for_p2p*に**true**、次の制限が適用されます。  
  
-   *allow_anonymous*する必要があります**false**です。  
  
-   *allow_dts を含む*する必要があります**false**です。  
  
-   *allow_initialize_from_backup*する必要があります**true**です。  
  
-   *allow_queued_tran*する必要があります**false**です。  
  
-   *allow_sync_tran*する必要があります**false**です。  
  
-   *conflict_policy*する必要があります**false**です。  
  
-   *independent_agent*する必要があります**true**です。  
  
-   *repl_freq*する必要があります**連続**です。  
  
-   *replicate_ddl*する必要があります**1**です。  
  
 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。  
  
 [  **@publish_local_changes_only =** ] **'***publish_local_changes_only***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@enabled_for_het_sub=** ] **'***enabled_for_het_sub***'**  
 パブリケーションをサポートしていないように[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。 *enabled_for_het_sub*は**nvarchar (5)** で既定値は FALSE。 値**true**パブリケーションをサポートしているではないことを意味[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーです。 ときに*enabled_for_het_sub*は**true**、次の制限が適用されます。  
  
-   *allow_initialize_from_backup*する必要があります**false**です。  
  
-   *allow_push*する必要があります**true**です。  
  
-   *allow_queued_tran*する必要があります**false**です。  
  
-   *allow_subscription_copy*する必要があります**false**です。  
  
-   *allow_sync_tran*する必要があります**false**です。  
  
-   *autogen_sync_procs*する必要があります**false**です。  
  
-   *conflict_policy* NULL にする必要があります。  
  
-   *enabled_for_internet*する必要があります**false**です。  
  
-   *enabled_for_p2p*する必要があります**false**です。  
  
-   *ftp_address* NULL にする必要があります。  
  
-   *ftp_subdirectory* NULL にする必要があります。  
  
-   *ftp_password* NULL にする必要があります。  
  
-   *pre_snapshot_script* NULL にする必要があります。  
  
-   *post_snapshot_script* NULL にする必要があります。  
  
-   *replicate_ddl* 0 にする必要があります。  
  
-   *qreader_job_name* NULL にする必要があります。  
  
-   *queue_type* NULL にする必要があります。  
  
-   *sync_method*することはできません**ネイティブ**または**同時**です。  
  
 詳細については、「 [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)」を参照してください。  
  
 [  **@p2p_conflictdetection=** ] **'***p2p_conflictdetection***'**  
 パブリケーションでピア ツー ピア レプリケーションが有効である場合に、ディストリビューション エージェントが競合を検出できるようにします。 *p2p_conflictdetection*は**nvarchar (5)** で既定値は TRUE です。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」を参照してください。  
  
 [  **@p2p_originator_id=** ] *p2p_originator_id*  
 ピア ツー ピア トポロジ内のノードの ID を指定します。 *p2p_originator_id*は**int**、既定値は NULL です。 場合、この ID は競合検出に対して使用*p2p_conflictdetection*が TRUE に設定します。 トポロジで使用されていない、正の値、0 以外の ID を指定します。 既に使用されている Id の一覧は、実行[sp_help_peerconflictdetection](../../relational-databases/system-stored-procedures/sp-help-peerconflictdetection-transact-sql.md)です。  
  
 [  **@p2p_continue_onconflict=** ] **'***@p2p_continue_onconflict***'**  
 競合の検出後にディストリビューション エージェントで変更の処理を続行するかどうかを示します。 *@p2p_continue_onconflict*は**nvarchar (5)** で既定値は FALSE。  
  
> [!CAUTION]  
>  既定値の FALSE を使用することをお勧めします。 このオプションを TRUE に設定すると、ディストリビューション エージェントは、発信元 ID が最も大きいノードから競合する行を適用してトポロジ内のデータを収束しようとします。 この方法では収束が保証されません。 競合が検出された後に、トポロジに一貫性があることを確認する必要があります。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」の「競合の処理」を参照してください。  
  
 [  **@allow_partition_switch=** ] **'***allow_partition_switch***'**  
 パブリッシュされたデータベースに対して ALTER TABLE ... SWITCH ステートメントを実行できるかどうかを指定します。 *allow_partition_switch*は**nvarchar (5)** で既定値は FALSE。 詳細については、「[パーティション テーブルとパーティション インデックスのレプリケート](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md)」を参照してください。  
  
 [  **@replicate_partition_switch=** ] **'***replicate_partition_switch***'**  
 パブリッシュされたデータベースに対して実行される ALTER TABLE ... SWITCH ステートメントをサブスクライバーにレプリケーションする必要があるかどうかを指定します。 *replicate_partition_switch*は**nvarchar (5)** で既定値は FALSE。 このオプションは有効な場合にのみ、 *allow_partition_switch*が TRUE に設定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addpublication**はスナップショット レプリケーションおよびトランザクション レプリケーションで使用します。  
  
 同じデータベース オブジェクトを使用するパブリケーションのみをパブリッシュする複数のパブリケーションが存在しない場合、 *replicate_ddl*の値**1**は ALTER TABLE、ALTER VIEW、ALTER PROCEDURE、ALTER FUNCTION をレプリケートし、ALTER TRIGGER DDL ステートメント。 ただし、ALTER TABLE DROP COLUMN DDL ステートメントは、削除された列をパブリッシュするすべてのパブリケーションでレプリケートされます。  
  
 DDL レプリケーションが有効になっている (*replicate_ddl* = **1**)、パブリケーションに対してレプリケーションなしの DDL を行うために変更をパブリケーション、 [sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)最初設定に実行する必要があります*replicate_ddl*に**0**します。 レプリケーションなしの DDL ステートメントが実行された後[sp_changepublication](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md) DDL レプリケーションを再びオンにもう一度実行することができます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddTranPub](../../relational-databases/replication/codesnippet/tsql/sp-addpublication-transa_1.sql)]  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addpublication**です。 Windows 認証ログインを行うには、Windows ユーザー アカウントを表すユーザー アカウントがデータベースに必要です。 Windows グループを表すユーザー アカウントでは不十分です。  
  
## <a name="see-also"></a>参照  
 [sp_addlogreader_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addlogreader-agent-transact-sql.md)   
 [sp_addpublication_snapshot &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_droppublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [sp_replicationdboption &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
