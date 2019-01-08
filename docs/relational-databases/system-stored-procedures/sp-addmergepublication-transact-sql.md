---
title: sp_addmergepublication (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepublication
- sp_addmergepublication_TSQL
helpviewer_keywords:
- sp_addmergepublication
ms.assetid: 28a629a1-7374-4614-9b04-279d290a942a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 75390bbbc490046af6db4e47a7ca10cefac2546c
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53591876"
---
# <a name="spaddmergepublication-transact-sql"></a>sp_addmergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  新しいマージ パブリケーションを作成します。 このストアド プロシージャは、パブリッシャー側でパブリッシュ対象のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addmergepublication [ @publication = ] 'publication'   
    [ , [ @description = ] 'description'   
    [ , [ @retention = ] retention ]   
    [ , [ @sync_mode = ] 'sync_mode' ]   
    [ , [ @allow_push = ] 'allow_push' ]   
    [ , [ @allow_pull = ] 'allow_pull' ]   
    [ , [ @allow_anonymous = ] 'allow_anonymous' ]   
    [ , [ @enabled_for_internet = ] 'enabled_for_internet' ]   
    [ , [ @centralized_conflicts = ] 'centralized_conflicts' ]   
    [ , [ @dynamic_filters = ] 'dynamic_filters' ]   
    [ , [ @snapshot_in_defaultfolder = ] 'snapshot_in_default_folder' ]   
    [ , [ @alt_snapshot_folder = ] 'alternate_snapshot_folder' ]   
    [ , [ @pre_snapshot_script = ] 'pre_snapshot_script' ]   
    [ , [ @post_snapshot_script = ] 'post_snapshot_script' ]   
    [ , [ @compress_snapshot = ] 'compress_snapshot' ]   
    [ , [ @ftp_address = ] 'ftp_address' ]   
    [ , [ @ftp_port = ] ftp_port ]   
    [ , [ @ftp_subdirectory = ] 'ftp_subdirectory' ]   
    [ , [ @ftp_login = ] 'ftp_login' ]   
    [ , [ @ftp_password = ] 'ftp_password' ]   
    [ , [ @conflict_retention = ] conflict_retention ]   
    [ , [ @keep_partition_changes = ] 'keep_partition_changes' ]   
    [ , [ @allow_subscription_copy = ] 'allow_subscription_copy' ]   
    [ , [ @allow_synctoalternate = ] 'allow_synctoalternate' ]   
    [ , [ @validate_subscriber_info = ] 'validate_subscriber_info' ]   
    [ , [ @add_to_active_directory = ] 'add_to_active_directory' ]   
    [ , [ @max_concurrent_merge = ] maximum_concurrent_merge ]   
    [ , [ @max_concurrent_dynamic_snapshots = ] max_concurrent_dynamic_snapshots ]  
    [ , [ @use_partition_groups = ] 'use_partition_groups' ]  
    [ , [ @publication_compatibility_level = ] 'backward_comp_level' ]  
    [ , [ @replicate_ddl = ] replicate_ddl ]  
    [ , [ @allow_subscriber_initiated_snapshot = ] 'allow_subscriber_initiated_snapshot' ]   
    [ , [ @allow_web_synchronization = ] 'allow_web_synchronization' ]   
    [ , [ @web_synchronization_url = ] 'web_synchronization_url' ]  
    [ , [ @allow_partition_realignment = ] 'allow_partition_realignment' ]  
    [ , [ @retention_period_unit = ] 'retention_period_unit' ]  
    [ , [ @generation_leveling_threshold = ] generation_leveling_threshold ]  
    [ , [ @automatic_reinitialization_policy = ] automatic_reinitialization_policy ]  
    [ , [ @conflict_logging = ] 'conflict_logging' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication =** ] **'**_パブリケーション_**'**  
 作成するマージ パブリケーションの名前です。 *パブリケーション*は**sysname**ない必要があり、既定では、キーワードは指定できませんすべてです。 パブリケーションの名前は、データベース内で一意である必要があります。  
  
 [  **@description =** ] **'**_説明_**'**  
 パブリケーションの説明を指定します。 *説明*は**nvarchar (255)**、既定値は NULL です。  
  
 [  **@retention =** ]*保有期間*  
 保有期間を保有期間の変更を保存する期間の単位は、指定された*パブリケーション*します。 *保有期間*は**int**単位は 14 の既定値。 保有期間の単位がによって定義されている*retention_period_unit*します。 保有期間内にサブスクリプションが同期されず、受信した保留中の変更がディストリビューター側でクリーンアップ操作によって削除された場合、サブスクリプションは有効期限切れとなり、再初期化する必要があります。 最大許容保有期間では、現在の日付と 9999 年 12 月 31 日までの日数の数です。  
  
> [!NOTE]  
>  マージ パブリケーションの保有期間は、サブスクライバーの異なるタイム ゾーンに対応する 24 時間の猶予期間です。 たとえば、保有期間を 1 日に設定した場合、実際の保有期間は 48 時間となります。  
  
 [  **@sync_mode =** ] **'**_sync_mode_**'**  
 サブスクライバーのパブリケーションに対する初期同期モードです。 *sync_mode*は**nvarchar (10)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**ネイティブ**(既定値)|すべてのテーブルのネイティブ モード BCP 出力を作成する。|  
|**character**|すべてのテーブルのキャラクタモード BCP 出力を作成する。 サポートに必要な[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssEW](../../includes/ssew-md.md)]と非-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバー。|  
  
 [  **@allow_push =** ] **'**_allow_push_**'**  
 特定のパブリケーションに対して、プッシュ サブスクリプションを作成できるかどうかを指定します。 *allow_push*は**nvarchar (5)**、既定値は TRUE、パブリケーションに対してプッシュ サブスクリプションを許可します。  
  
 [  **@allow_pull =** ] **'**_allow_pull_**'**  
 特定のパブリケーションに対して、プル サブスクリプションを作成できるかどうかを指定します。 *allow_pull*は**nvarchar (5)**、既定値は TRUE、パブリケーションに対してプル サブスクリプションを許可します。 サポートする場合は true を指定する必要があります[!INCLUDE[ssEW](../../includes/ssew-md.md)]サブスクライバー。  
  
 [  **@allow_anonymous =** ] **'**_allow_anonymous_**'**  
 特定のパブリケーションに対して、匿名サブスクリプションを作成できるかどうかを指定します。 *allow_anonymous*は**nvarchar (5)**、既定値は TRUE、パブリケーションに対して匿名サブスクリプションを許可します。 サポートするために[!INCLUDE[ssEW](../../includes/ssew-md.md)]指定する必要がありますサブスクライバー、 **true**します。  
  
 [  **@enabled_for_internet =** ] **'**_enabled_for_internet_**'**  
 パブリケーションをインターネット対応にするかどうかを指定し、サブスクライバーへのスナップショット ファイルの転送にファイル転送プロトコル (FTP) を使用できるかどうかを決定します。 *enabled_for_internet*は**nvarchar (5)**、既定値は FALSE。 場合**true**パブリケーションの同期ファイルは C:\Program files \microsoft SQL Server\MSSQL\MSSQL.x\Repldata\Ftp ディレクトリに格納します。 ユーザーは Ftp ディレクトリを作成する必要があります。 場合**false**インターネットにアクセスできるは、パブリケーションが有効になっていません。  
  
 [  **@centralized_conflicts =**] **'**_centralized_conflicts_**'**  
 このパラメーターは、旧バージョンのスクリプトとの互換性を保つために用意されており、非推奨とされます。 使用*conflict_logging*競合レコードの保存先の場所を指定します。  
  
 [  **@dynamic_filters =**] **'**_dynamic_filters_**'**  
 マージ パブリケーションでパラメーター化された行フィルターを使用できるようにします。 *dynamic_filters*は**nvarchar (5)**、既定値は FALSE。  
  
> [!NOTE]  
>  このパラメーターは使用せず、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がパラメーター化された行フィルターが使用されているかどうかを自動的に判定できるようにしてください。 値を指定する場合**true**の*dynamic_filters*アーティクルのパラメーター化された行フィルターを定義する必要があります。 詳しくは、「 [マージ アーティクルのパラメーター化された行フィルターの定義および変更](../../relational-databases/replication/publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)」をご覧ください。  
  
 [  **@snapshot_in_defaultfolder =** ] **'**_snapshot_in_default_folder_**'**  
 スナップショット ファイルが既定のフォルダーに格納されるかどうかを示します。 *snapshot_in_default_folder*は**nvarchar (5)**、既定値は TRUE。 場合**true**、スナップショット ファイルは既定のフォルダーにあります。 場合**false**、スナップショット ファイルは、によって指定された代替位置に格納されます*alternate_snapshot_folder*します。 代替位置としては、他のサーバー、ネットワーク ドライブ、または CD-ROM やリムーバブル ディスクなどのリムーバブル メディアを指定できます。 また、スナップショット ファイルは、後でサブスクライバーにより取得するために、ファイル転送プロトコル (FTP) サイトに保存してもかまいません。 このパラメーターが真であることができで指定された場所がまだあることに注意してください*alt_snapshot_folder*します。 これらのパラメーターを組み合わせて指定した場合、スナップショット ファイルは、既定のフォルダーと代替位置の両方に格納されます。  
  
 [  **@alt_snapshot_folder =** ] **'**_alternate_snapshot_folder_**'**  
 スナップショットの代替フォルダーの場所を指定します。 *alternate_snapshot_folder*は**nvarchar (255)**、既定値は NULL です。  
  
 [  **@pre_snapshot_script =** ] **'**_pre_snapshot_script_**'**  
 ポインターを指定します、 **.sql**ファイルの場所。 *pre_snapshot_script*は**nvarchar (255)**、既定値は NULL です。 マージ エージェントは、サブスクライバーでスナップショットを適用するときに、レプリケートされたオブジェクト スクリプトより前に、プリスナップショット スクリプトを実行します。 このスクリプトは、マージ エージェントがサブスクリプション データベースに接続するときにセキュリティ コンテキスト内で実行されます。 プリスナップ ショット スクリプトは実行されません[!INCLUDE[ssEW](../../includes/ssew-md.md)]サブスクライバー。  
  
 [  **@post_snapshot_script =** ] **'**_post_snapshot_script_**'**  
 ポインターを指定します、 **.sql**ファイルの場所。 *post_snapshot_script*は**nvarchar (255)**、既定値は NULL です。 最初の同期のときに、マージ エージェントは、他のすべてのレプリケートされたオブジェクト スクリプトとデータが適用された後に、ポストスナップショット スクリプトを実行します。 このスクリプトは、マージ エージェントがサブスクリプション データベースに接続するときにセキュリティ コンテキスト内で実行されます。 ポスト スナップ ショット スクリプトは実行されません[!INCLUDE[ssEW](../../includes/ssew-md.md)]サブスクライバー。  
  
 [  **@compress_snapshot =** ] **'**_compress_snapshot_**'**  
 書き込まれるスナップショットを指定します、 **@alt_snapshot_folder**の場所を圧縮するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB 形式です。 *compress_snapshot*は**nvarchar (5)**、既定値は FALSE。 **false**こと、スナップショットは圧縮されません。 を指定します。**true**スナップショットは圧縮することを指定します。 2 GB より大きいスナップショット ファイルは圧縮できません。 圧縮されたスナップショット ファイルは、マージ エージェントが実行されている場所で解凍されます。一般にプル サブスクリプションでは、サブスクライバーでファイルが解凍されるように、圧縮されたスナップショットが使用されます。 既定のフォルダー内のスナップショットは圧縮できません。 サポートするために[!INCLUDE[ssEW](../../includes/ssew-md.md)]指定する必要がありますサブスクライバー、 **false**します。  
  
 [  **@ftp_address =** ] **'**_ftp_address_**'**  
 ディストリビューター用の FTP サービスのネットワーク アドレスです。 *ftp_address*は**sysname**、既定値は NULL です。 取得するサブスクライバーのマージ エージェント パブリケーション スナップショット ファイルの場所を指定します。 各パブリケーションを別に持つことができますので、このプロパティはパブリケーションごとに格納されている、 *ftp_address*します。 パブリケーションでは、FTP を使用したスナップショットの配布がサポートされている必要があります。  
  
 [  **@ftp_port=** ] *ftp_port*  
 ディストリビューター用の FTP サービスのポート番号です。 *ftp_port*は**int**、既定値は 21 です。 サブスクライバーのマージ エージェントが検索するパブリケーション スナップショット ファイルの場所を指定します。 このプロパティはパブリケーションごとに格納されている、ために各パブリケーションが持つことができます独自*ftp_port*します。  
  
 [  **@ftp_subdirectory =** ] **'**_ftp_subdirectory_**'**  
 パブリケーションが FTP を利用したスナップショットの配布をサポートしている場合に、サブスクライバーのマージ エージェントがスナップショット ファイルを取得できる場所を指定します。 *ftp_subdirectory*は**nvarchar (255)**、既定値は NULL です。 このプロパティはパブリケーションごとに格納されている、ために各パブリケーションが持つことができます独自*ftp_subdirctory*に NULL 値を持つ、サブディレクトリがないこともできます。  
  
 パラメーター化されたフィルターを使用してパブリケーションのスナップショットを事前に生成する場合、各サブスクライバーのパーティションのデータ スナップショットはそれぞれのフォルダーに入っている必要があります。 FTP を使用する事前生成済みのスナップショットのディレクトリ構造は、次の構造に従っている必要があります。  
  
 *alternate_snapshot_folder*\ftp\\*publisher_publicationDB_publication*\\*partitionID*します。  
  
> [!NOTE]  
>  上記の斜体の値は、パブリケーションおよびサブスクライバー パーティションの詳細によって異なります。  
  
 [  **@ftp_login =** ] **'**_ftp_login_**'**  
 FTP サービスに接続するときに使用するユーザー名です。 *ftp_login*は**sysname**、既定値は 'anonymous' です。  
  
 [  **@ftp_password =** ] **'**_ftp_password_**'**  
 FTP サービスに接続するときに使用するユーザー パスワードです。 *ftp_password*は**sysname**、既定値は NULL です。  
  
> [!IMPORTANT]  
>  空白のパスワードは使用しないでください。 強力なパスワードを使用してください。  
  
 [  **@conflict_retention =** ] *conflict_retention*  
 競合を保有する保有期間の日数。 *conflict_retention*は**int**、既定値は、競合する前に 14 日間の競合テーブルから行が削除されます。  
  
 [  **@keep_partition_changes =** ] **'**_keep_partition_changes_**'**  
 事前計算済みパーティションを使用できない場合に、パーティションの変更の最適化を有効にするかどうかを指定します。 *keep_partition_changes*は**nvarchar (5)**、既定値は TRUE。 **false**変更をパーティション分割することを意味に最適化されていない、およびパーティションのデータが変更されたときに事前計算済みパーティションを使用しない場合のすべてのサブスクライバーに送信されるパーティションが検証されます。 **true**変更をパーティション分割の方法は最適化され、変更されたパーティションの行を持つサブスクライバーだけが影響を受けます。 事前計算済みパーティションを使用する場合は、設定*use_partition_groups*に**true**設定と*keep_partition_changes*に**false**します。 詳細については、「[事前計算済みパーティションによるパラメーター化されたフィルターのパフォーマンス最適化](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)」を参照してください。  
  
> [!NOTE]  
>  値を指定する場合**true**の*keep_partition_changes*の値を指定**1** 、スナップショット エージェント パラメーターの **-MaxNetworkOptimization**. このパラメーターの詳細については、次を参照してください。 [Replication Snapshot Agent](../../relational-databases/replication/agents/replication-snapshot-agent.md)します。 エージェントのパラメーターを指定する方法については、次を参照してください。[レプリケーション エージェントの管理](../../relational-databases/replication/agents/replication-agent-administration.md)します。  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]サブスクライバー、 *keep_partition_changes*削除を正しく反映する場合は true に設定する必要があります。 false に設定すると、サブスクライバーに予想よりも多くの行が含まれる場合があります。  
  
 [  **@allow_subscription_copy=** ] **'**_allow_subscription_copy_**'**  
 このパブリケーションにサブスクライブするサブスクリプション データベースをコピーする機能を有効または無効にします。 *allow_subscription_copy*は**nvarchar (5)**、既定値は FALSE。 コピーされるサブスクリプション データベースのサイズは 2 ギガバイト (GB) 未満でなければなりません。  
  
 [  **@allow_synctoalternate =** ] **'**_allow_synctoalternate_**'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@validate_subscriber_info =** ] **'**_validate_subscriber_info_**'**  
 パラメーター化された行フィルターを使用する場合、パブリッシュされたデータのサブスクライバー パーティションを定義するのに使用する関数を一覧表示します。 *validate_subscriber_info*は**nvarchar (500)**、既定値は NULL です。 この情報は、マージ エージェントがサブスクライバーのパーティションを検証するときに使用されます。 たとえば場合、 [SUSER_SNAME](../../t-sql/functions/suser-sname-transact-sql.md)されるパラメーターは、パラメーター化された行フィルターでなければなりません`@validate_subscriber_info=N'SUSER_SNAME()'`。  
  
> [!NOTE]  
>  このパラメーターは指定しないで、代わりに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がフィルター選択条件を自動的に決定できるようにしてください。  
  
 [  **@add_to_active_directory =** ] **'**_add_to_active_directory_**'**  
 このパラメーターは、旧バージョンのスクリプトとの互換性を保つために用意されており、非推奨とされます。 現在、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory にはパブリケーション情報を追加できません。  
  
 [  **@max_concurrent_merge =** ] *maximum_concurrent_merge*  
 同時に実行できるマージ処理の最大数です。 *maximum_concurrent_merge*は**int**既定値は 0。 値**0**のこのプロパティは、特定の時点で実行されている同時マージ処理の数に制限がないことを意味します。 このプロパティでは、マージ パブリケーションに対して同時に実行できる同時マージ処理の数を制限します。 同時にスケジュールに組み込まれているマージ処理の数が、指定された実行可能な数より大きい場合、余分なジョブは待ち行列に挿入され、現在実行されているマージ処理が終わるまで待機状態に置かれます。  
  
 [  **@max_concurrent_dynamic_snapshots =**] *max_concurrent_dynamic_snapshots*  
 サブスクライバー パーティションのフィルター選択されたデータ スナップショットを生成するために、同時に実行できるスナップショット エージェントの最大セッション数です。 *maximum_concurrent_dynamic_snapshots*は**int**既定値は 0。 場合**0**、スナップショット セッションの数に制限はありません。 同時にスケジュールに組み込まれているスナップショット処理の数が、指定された実行可能な数より大きい場合、余分なジョブは待ち行列に挿入され、現在実行されているスナップショット処理が終わるまで待機状態に置かれます。  
  
 [  **@use_partition_groups =** ] **'**_use_partition_groups_**'**  
 事前計算済みパーティションを使用して、同期処理を最適化することを指定します。 *use_partition_groups*は**nvarchar (5)**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**true**|パブリケーションは事前計算済みパーティションを使用します。|  
|**false**|パブリケーションは事前計算済みパーティションを使用しません。|  
|NULL(default)|システムがパーティション分割ストラテジを決定します。|  
  
 既定では事前計算済みパーティションを使用します。 事前計算済みパーティションを使用しないように*use_partition_groups*に設定する必要があります**false**します。 NULL に指定すると、システムが事前計算済みパーティションを使用するかどうかを決定します。 パーティションを使用することはできませんし、この値は実質的に事前計算済み場合**false**任意のエラーは生成されません。 このような場合、 *keep_partition_changes*に設定することができます**true**をある程度最適化を提供します。 詳細については、次を参照してください。 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)と[事前計算済みパーティションによるパラメーター化されたフィルター パフォーマンスの最適化](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)します。  
  
 [  **@publication_compatibility_level =** ] *backward_comp_level*  
 パブリケーションの下位互換性を示します。 *backward_comp_level*は**nvarchar (6)**、これらの値のいずれかを指定できます。  
  
|値|バージョン|  
|-----------|-------------|  
|**90 RTM**|[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|  
|**100 RTM**|[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
  
 [  **@replicate_ddl =** ] *replicate_ddl*  
 スキーマ レプリケーションがパブリケーションに対してサポートされているかどうかを示します。 *replicate_ddl*は**int**、既定値は 1 です。 **1** 、パブリッシャーで実行されるデータ定義言語 (DDL) ステートメントがレプリケートされることを示しますと**0** DDL ステートメントがレプリケートされないことを示します。 詳細については、「[パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)」を参照してください。  
  
 *@replicate_ddl* DDL ステートメントは、列を追加するときは、パラメーターを有効にします。 *@replicate_ddl* DDL ステートメントが変更または次の理由により、列を削除するときに、パラメーターは無視されます。  
  
-   列が削除されるとき、ディストリビューション エージェントは失敗の原因となる、削除された列を含むから新しい DML ステートメントを防ぐために sysarticlecolumns を更新する必要があります。 *@replicate_ddl*レプリケーションは、スキーマの変更を常にレプリケートする必要がありますので、パラメーターは無視されます。  
  
-   列が変更される場合は、ソースのデータ型または NULL 値の許容属性が変更され、サブスクライバーにあるテーブルと互換性のない値が DML ステートメントに含まれる可能性があります。 そうした DML ステートメントは、ディストリビューション エージェントが失敗する原因となる場合があります。 *@replicate_ddl*レプリケーションは、スキーマの変更を常にレプリケートする必要がありますので、パラメーターは無視されます。  
  
-   DDL ステートメントは、新しい列を追加するときに sysarticlecolumns では、新しい列が含まれません。 DML ステートメントによって、新しい列のデータがレプリケートされることはありません。 DDL をレプリケートするかしないかのどちらかが許容されるため、パラメーターは有効になります。  
  
 [  **@allow_subscriber_initiated_snapshot =** ] **'**_@allow_subscriber_initiated_snapshot_**'**  
 このパブリケーションのサブスクライバーが、データ パーティションのフィルター選択されたスナップショットを生成するスナップショット処理を開始できるかどうかを指定します。 *@allow_subscriber_initiated_snapshot*は**nvarchar (5)**、既定値は FALSE。 **true**サブスクライバーがスナップショット プロセスを開始できることを示します。  
  
 [  **@allow_web_synchronization =** ] **'**_allow_web_synchronization_**'**  
 Web 同期に対してパブリケーションを有効にするかどうかを指定します。 *allow_web_synchronization*は**nvarchar (5)**、既定値は FALSE。 **true** HTTPS 経由でこのパブリケーションに対するサブスクリプションを同期できることを指定します。 詳細については、「 [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md)」を参照してください。 サポートするために[!INCLUDE[ssEW](../../includes/ssew-md.md)]指定する必要がありますサブスクライバー、 **true**します。  
  
 [  **@web_synchronization_url=** ] **'**_web_synchronization_url_**'**  
 Web 同期で使用するインターネット URL の既定値を指定します。 *web_synchronization_url は*s **nvarchar (500)**、既定値は NULL です。 いずれかが明示的に設定されていない場合がある場合は、既定のインターネット URL を定義します[sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)を実行します。  
  
 [  **@allow_partition_realignment =** ] **'**_allow_partition_realignment_**'**  
 パブリッシャーで、行の変更によりパーティションに変更があった場合、削除をサブスクライバーに送信するかどうかを決定します。 *allow_partition_realignment*は**nvarchar (5)**、既定値は TRUE。 **true**削除をサブスクライバーのパーティションの一部では不要になったデータを削除して、パーティション変更の結果を反映するように、サブスクライバーに送信します。 **false**このサブスクライバーには、パブリッシャーでこのデータに加えられた変更はレプリケートされませんが、サブスクライバーで加えられた変更は、パブリッシャーにレプリケートされます、サブスクライバーで古いパーティションから、データをそのまま保持します。 設定*allow_partition_realignment*に**false**データを履歴目的でアクセスできるようにする必要がある場合、古いパーティションからのサブスクリプションにデータを保持するために使用します。  
  
> [!NOTE]  
>  設定の結果としてサブスクライバーに残るデータ*allow_partition_realignment*に**false**読み取り専用であるかのように扱う必要あるはただし、これは強制されません、レプリケーション システムによって。  
  
 [  **@retention_period_unit =** ] **'**_retention_period_unit_**'**  
 期間を設定保有期間の単位を指定します*保有*します。 *retention_period_unit*は**nvarchar (10)** 値は次のいずれかを指定できます。  
  
|値|バージョン|  
|-----------|-------------|  
|**1 日**(既定値)|保有期間は、日単位で指定されます。|  
|**week**|保有期間は、週単位で指定されます。|  
|**month**|保有期間は、月単位で指定されます。|  
|**year**|保有期間は、年単位で指定されます。|  
  
 [  **@generation_leveling_threshold=** ] *generation_leveling_threshold*  
 1 回の生成に含まれる変更の数です。 生成とは、パブリッシャーまたはサブスクライバーに配信される変更のコレクションです。 *generation_leveling_threshold*は**int**既定値は 1000 です。  
  
 [  **@automatic_reinitialization_policy =** ] *automatic_reinitialization_policy*  
 値が、パブリケーションへの変更によって必要な自動再初期化する前にサブスクライバーから変更をアップロードするかどうかを指定します。 **1**が指定されました **@force_reinit_subscription**します。 *automatic_reinitialization_policy*は bit で、既定値は 0 です。 **1**自動再初期化が発生する前に、変更がサブスクライバーからアップロードされたことを意味します。  
  
> [!IMPORTANT]  
>  パラメーター化フィルターを追加、削除、変更する場合は、再初期化の際、サブスクライバーで保留中の変更をパブリッシャーにアップロードできません。 保留中の変更をアップロードしたい場合は、フィルターを変更する前にすべてのサブスクリプションを同期してください。  
  
 [  **@conflict_logging =** ] **'**_conflict_logging_**'**  
 競合レコードの保存先を指定します。 *conflict_logging*は**nvarchar (15)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**パブリッシャー**|競合レコードはパブリッシャーに保存されます。|  
|**サブスクライバー**|競合レコードは、競合の原因となったサブスクライバーに保存されます。 [!INCLUDE[ssEW](../../includes/ssew-md.md)] サブスクライバーではサポートされません。|  
|**両方**|競合レコードは、パブリッシャーとサブスクライバーの両方に保存されます。|  
|NULL (既定値)|レプリケーションが自動的に設定*conflict_logging*に**両方**ときに、値*backward_comp_level*は**90 rtm**と**パブリッシャー**それ以外の場合。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addmergepublication**はマージ レプリケーションで使用します。  
  
 使用して Active Directory パブリケーション オブジェクトの一覧、 **@add_to_active_directory**パラメーター、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]オブジェクトは、Active Directory で既に作成する必要があります。  
  
 同じデータベース オブジェクトを使用するパブリケーションのみをパブリッシュする複数のパブリケーションが存在しない場合、 *replicate_ddl* @property **1** ALTER TABLE、ALTER VIEW、ALTER PROCEDURE、ALTER FUNCTION、レプリケートとALTER TRIGGER DDL ステートメント。 ただし、ALTER TABLE DROP COLUMN DDL ステートメントは、削除された列をパブリッシュするすべてのパブリケーションでレプリケートされます。  
  
 [!INCLUDE[ssEW](../../includes/ssew-md.md)]サブスクライバーの場合、値の*alternate_snapshot_folder*場合のみ使用の値*snapshot_in_default_folder*は**false**します。  
  
 DDL レプリケーションが有効になっている (_replicate_ddl_**= 1**)、パブリケーションに対してレプリケーションなしの DDL 変更を行う、パブリケーション[sp_changemergepublication &#40;Transact SQL&#41; ](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)設定に最初に実行する必要があります*replicate_ddl*に**0**します。 レプリケーションなしの DDL ステートメントが実行された後**sp_changemergepublication** DDL レプリケーションをオンにもう一度実行することができます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddMergePub](../../relational-databases/replication/codesnippet/tsql/sp-addmergepublication-t_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addmergepublication**します。  
  
## <a name="see-also"></a>参照  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [sp_changemergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_dropmergepublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
