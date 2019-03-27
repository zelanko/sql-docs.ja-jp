---
title: sp_addmergearticle (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergearticle
- sp_addmergearticle_TSQL
helpviewer_keywords:
- sp_addmergearticle
ms.assetid: 0df654ea-24e2-4c61-a75a-ecaa7a140a6c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8852aaf6b8d6baa7a5451f0ccc31229d6f521a33
ms.sourcegitcommit: 2db83830514d23691b914466a314dfeb49094b3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58494374"
---
# <a name="spaddmergearticle-transact-sql"></a>sp_addmergearticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のマージ パブリケーションにアーティクルを追加します。 このストアド プロシージャは、パブリッシャー、パブリケーション データベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addmergearticle [ @publication = ] 'publication'   
        , [ @article = ] 'article'   
        , [ @source_object = ] 'source_object'   
    [ , [ @type = ] 'type' ]   
    [ , [ @description = ] 'description' ]   
    [ , [ @column_tracking = ] 'column_tracking' ]   
    [ , [ @status = ] 'status' ]   
    [ , [ @pre_creation_cmd = ] 'pre_creation_cmd' ]   
    [ , [ @creation_script = ] 'creation_script' ]   
    [ , [ @schema_option = ] schema_option ]   
    [ , [ @subset_filterclause = ] 'subset_filterclause' ]   
    [ , [ @article_resolver = ] 'article_resolver' ]   
    [ , [ @resolver_info = ] 'resolver_info' ]   
    [ , [ @source_owner = ] 'source_owner' ]   
    [ , [ @destination_owner = ] 'destination_owner' ]   
    [ , [ @vertical_partition = ] 'vertical_partition' ]   
    [ , [ @auto_identity_range = ] 'auto_identity_range' ]   
    [ , [ @pub_identity_range = ] pub_identity_range ]   
    [ , [ @identity_range = ] identity_range ]   
    [ , [ @threshold = ] threshold ]   
    [ , [ @verify_resolver_signature = ] verify_resolver_signature ]   
    [ , [ @destination_object = ] 'destination_object' ]   
    [ , [ @allow_interactive_resolver = ] 'allow_interactive_resolver' ]   
    [ , [ @fast_multicol_updateproc = ] 'fast_multicol_updateproc' ]   
    [ , [ @check_permissions = ] check_permissions ]   
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @published_in_tran_pub = ] 'published_in_tran_pub' ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @logical_record_level_conflict_detection = ] 'logical_record_level_conflict_detection' ]  
    [ , [ @logical_record_level_conflict_resolution = ] 'logical_record_level_conflict_resolution' ]  
    [ , [ @partition_options = ] partition_options ]  
    [ , [ @processing_order = ] processing_order ]  
    [ , [ @subscriber_upload_options = ] subscriber_upload_options ]  
    [ , [ @identityrangemanagementoption = ] 'identityrangemanagementoption' ]  
    [ , [ @delete_tracking = ] delete_tracking ]  
    [ , [ @compensate_for_errors = ] 'compensate_for_errors' ]   
    [ , [ @stream_blob_columns = ] 'stream_blob_columns' ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` アーティクルを含むパブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @article = ] 'article'` アーティクルの名前です。 名前はパブリケーション内で一意であることが必要です。 *記事*は**sysname**、既定値はありません。 *記事*を実行しているローカル コンピューター上に存在する必要があります[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子の規則に従っている必要があります。  
  
`[ @source_object = ] 'source_object'` パブリッシュするデータベース オブジェクトです。 *source_object*は**sysname**、既定値はありません。 マージ レプリケーションを使用してパブリッシュできるオブジェクトの種類の詳細については、次を参照してください。[発行データおよびデータベース オブジェクト](../../relational-databases/replication/publish/publish-data-and-database-objects.md)します。  
  
`[ @type = ] 'type'` アーティクルの種類です。 *型*は**sysname**、既定値は**テーブル**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**テーブル**(既定値)|スキーマとデータを含むテーブル。 レプリケーションはテーブルを監視して、レプリケートするデータを特定します。|  
|**func スキーマのみ**|スキーマのみで機能します。|  
|**インデックス付きビュー** **スキーマのみ**|スキーマのみを使用するインデックス付きビュー。|  
|**proc スキーマのみ**|スキーマのみを使用するストアド プロシージャ。|  
|**シノニム スキーマのみ**|スキーマのみを使用するシノニム。|  
|**ビュー スキーマのみ**|スキーマのみを使用するビュー。|  
  
`[ @description = ] 'description'` 記事で説明します。 *説明*は**nvarchar (255)**、既定値は NULL です。  
  
`[ @column_tracking = ] 'column_tracking'` 列レベルの追跡の設定です。 *column_tracking*は**nvarchar (10)**、既定値は FALSE。 **true**列追跡をオンにします。 **false**列追跡をオフにし、行レベルで競合検出のままです。 テーブルが他のマージ レプリケーションで既にパブリッシュされている場合は、このテーブルに基づく既存のアーティクルが使用しているものと同じ列追跡値を使用する必要があります。 このパラメーターは、テーブル アーティクルのみに固有のものです。  
  
> [!NOTE]  
>  行レベルの追跡を使用して競合を検出する場合 (既定値)、ベース テーブルには最大 1,024 列含めることができますが、最大 246 列がパブリッシュされるようにアーティクルから列をフィルター選択する必要があります。 列の追跡を使用する場合、ベース テーブルには最大 246 列を含めることができます。  
  
`[ @status = ] 'status'` この記事の状態です。 *ステータス*は**nvarchar (10)**、既定値は**unsynced**します。 場合**active**テーブルをパブリッシュする初期処理スクリプトを実行します。 場合**unsynced**、次回、スナップショット エージェントの実行時にテーブルをパブリッシュする初期処理スクリプトが実行されます。  
  
`[ @pre_creation_cmd = ] 'pre_creation_cmd'` スナップショットを適用するときに、サブスクライバーでテーブルが存在する場合の対処方法を指定します。 *pre_creation_cmd*は**nvarchar (10)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**[なし]**|サブスクライバーでテーブルが既に存在する場合、アクションは行われません。|  
|**delete**|サブセット フィルターの WHERE 句に基づいて削除を発行します。|  
|**drop** (既定値)|テーブルを再作成する前に削除します。 サポートに必要な[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssEW](../../includes/ssew-md.md)]サブスクライバー。|  
|**truncate**|変換先テーブルを切り捨てます。|  
  
`[ @creation_script = ] 'creation_script'` パスとサブスクリプション データベースでアーティクルを作成するために使用、オプションのアーティクル スキーマ スクリプトの名前です。 *creation_script*は**nvarchar (255)**、既定値は NULL です。  
  
> [!NOTE]  
>  作成スクリプトは [!INCLUDE[ssEW](../../includes/ssew-md.md)] サブスクライバー上では実行されません。  
  
`[ @schema_option = ] schema_option` 指定されたアーティクルに対するスキーマ生成オプションのビットマップです。 *schema_option*は**binary (8)**、でき、 [|(ビットごとの OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md)これらの値の 1 つ以上の製品です。  
  
|値|説明|  
|-----------|-----------------|  
|**0x00**|スナップショット エージェントによるスクリプト作成を無効にしで定義されている指定されたスキーマ事前作成スクリプトを使用して*creation_script*します。|  
|**0x01**|オブジェクトの作成 (CREATE TABLE、CREATE PROCEDURE など) を生成します。 これは、ストアド プロシージャ アーティクルの既定値です。|  
|**0x10**|対応するクラスター化インデックスを生成します。 このオプションが設定されていない場合でも、パブリッシュされたテーブルに主キーと UNIQUE 制約が既に定義されている場合は、これらの主キーや制約に関連するインデックスが生成されます。|  
|**0x20**|サブスクライバーのデータ型の基に変換しますユーザー定義データ型 (UDT)。 UDT 列が主キーの一部である場合、または計算列は、UDT 列を参照している場合、UDT 列のチェックまたは既定の制約がある場合に、このオプションを使用することはできません。|  
|**0x40**|対応する非クラスター化インデックスを生成します。 このオプションが設定されていない場合でも、パブリッシュされたテーブルに主キーと UNIQUE 制約が既に定義されている場合は、これらの主キーや制約に関連するインデックスが生成されます。|  
|**0x80**|PRIMARY KEY 制約をレプリケートします。 制約に関連するすべてのインデックスもレプリケートされる場合でもオプション**0x10**と**0x40**有効ではありません。|  
|**0x100**|定義されている場合、テーブル アーティクル上のユーザー トリガーをレプリケートします。|  
|**0x200**|FOREIGN KEY 制約をレプリケートします。 参照先のテーブルがパブリケーションの一部は、パブリッシュされたテーブルですべての FOREIGN KEY 制約はレプリケートされません。|  
|**0x400**|CHECK 制約をレプリケートします。|  
|**0x800**|既定値をレプリケートします。|  
|**0x1000**|列レベルの照合順序をレプリケートします。|  
|**0x2000**|パブリッシュされたアーティクルのソース オブジェクトに関連付けられた拡張プロパティをレプリケートします。|  
|**0x4000**|UNIQUE 制約をレプリケートします。 制約に関連するすべてのインデックスもレプリケートされる場合でもオプション**0x10**と**0x40**有効ではありません。|  
|**0x8000**|このオプションは、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンを実行しているパブリッシャーでは有効ではありません。|  
|**0x10000**|制約が同期中に適用されないように、CHECK 制約を NOT FOR REPLICATION としてレプリケートします。|  
|**0x20000**|制約が同期中に適用されないように、FOREIGN KEY 制約を NOT FOR REPLICATION としてレプリケートします。|  
|**0x40000**|パーティション テーブルまたはインデックスに関連付けられているファイル グループをレプリケートします。|  
|**0x80000**|パーティション テーブルのパーティション構成をレプリケートします。|  
|**0x100000**|パーティション インデックスのパーティション構成をレプリケートします。|  
|**0x200000**|テーブルな統計をレプリケートします。|  
|**0x400000**|既定のバインドをレプリケートします。|  
|**0x800000**|ルールのバインドをレプリケートします。|  
|**0x1000000**|フルテキスト インデックスをレプリケートします。|  
|**0x2000000**|バインドされた XML スキーマ コレクション**xml**列はレプリケートされません。|  
|**0x4000000**|インデックスをレプリケート**xml**列。|  
|**0x8000000**|サブスクライバーにまだ存在しないすべてのスキーマを作成します。|  
|**0x10000000**|変換します**xml**列**ntext**サブスクライバーにします。|  
|**0x20000000**|変換の大きなオブジェクトのデータ型 (**nvarchar (max)**、 **varchar (max)**、および**varbinary (max)**) で導入された[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]でサポートされているデータ型[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].|  
|**0x40000000**|アクセス許可をレプリケートします。|  
|**0x80000000**|パブリケーションの一部ではない任意のオブジェクトに対する依存関係の削除を試行します。|  
|**0x100000000**|このオプションを使用して、指定されている場合は、FILESTREAM 属性をレプリケートする**varbinary (max)** 列。 テーブルをレプリケートする場合は、このオプションを指定しない[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]サブスクライバー。 FILESTREAM 列を持つテーブルをレプリケート[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]サブスクライバーがサポートされていません、このスキーマ オプションを設定する方法に関係なく、します。 関連するオプションを参照してください。 **0x800000000**します。|  
|**0x200000000**|日付と時刻のデータ型に変換 (**日付**、**時間**、 **datetimeoffset**、および**datetime2**) で導入された[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]データ以前のバージョンでサポートされている種類[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
|**0x400000000**|データとインデックスの圧縮オプションをレプリケートします。 詳細については、「 [Data Compression](../../relational-databases/data-compression/data-compression.md)」を参照してください。|  
|**0x800000000**|このオプションを設定すると、サブスクライバーの独自のファイル グループに FILESTREAM データを格納できます。 このオプションが設定されていない場合は、FILESTREAM データが既定のファイル グループに格納されます。 レプリケーションが; ファイル グループを作成できません。したがって、このオプションを設定する場合、サブスクライバーでスナップショットを適用する前に、ファイル グループを作成する必要があります。 スナップショットを適用する前に、オブジェクトを作成する方法の詳細については、次を参照してください。[前にスクリプトを実行し、後のスナップショットが適用される](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied)します。<br /><br /> 関連するオプションを参照してください。 **0x100000000**します。|  
|**0x1000000000**|共通言語ランタイム (CLR) ユーザー定義型 (Udt) に変換します**varbinary (max)** を実行しているサブスクライバーに UDT 型の列をレプリケートできるように[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]します。|  
|**0x2000000000**|変換、 **hierarchyid**のデータ型**varbinary (max)** ように型の列**hierarchyid**実行しているサブスクライバーにレプリケートできる[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]。 使用する方法の詳細についての**hierarchyid**レプリケートされたテーブル内の列を参照してください[hierarchyid &#40;TRANSACT-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)します。|  
|**0x4000000000**|テーブルにフィルター選択されたインデックスをレプリケートします。 フィルター選択されたインデックスの詳細については、次を参照してください。 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)します。|  
|**0x8000000000**|変換、 **geography**と**geometry**データ型を**varbinary (max)** を実行しているサブスクライバーにこれらの型の列をレプリケートできるように[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|**0x10000000000**|型の列にインデックスをレプリケート**geography**と**geometry**します。|  
  
 この値が NULL の場合、システムの自動生成されたアーティクルに対する有効なスキーマ オプション。 **スキーマ オプションの既定の**「解説」セクションの表には、アーティクルの種類に基づいて選択されている値が表示されます。 また、すべて*schema_option*値は、レプリケーションのすべての種類およびアーティクルの種類に有効です。 **有効なスキーマ オプション**表の「解説」で指定された特定アーティクル種類を指定できるオプションを示します。  
  
> [!NOTE]  
>  *Schema_option*パラメーターでは、初期スナップショットのレプリケーション オプションだけに影響します。 最初のスキーマをスナップショット エージェントによって生成され、サブスクライバーで適用すると、サブスクライバーにパブリケーションのスキーマ変更のレプリケーションがスキーマ変更レプリケーション ルールに基づいてで発生して、 *replicate_ddl*指定されたパラメーター設定[sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)します。 詳細については、「[パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)」を参照してください。  
  
`[ @subset_filterclause = ] 'subset_filterclause'` 語を除く、テーブル アーティクルの水平方向のフィルター処理を指定する WHERE 句が含まれています。 *subset_filterclause*の**nvarchar (1000)**、既定値は空の文字列。  
  
> [!IMPORTANT]  
>  パラメーター化された行フィルター句では列名に関数を適用しないことをお勧めします。これは、 `LEFT([MyColumn]) = SUSER_SNAME()`のように指定すると、パフォーマンスに問題が生じるためです。 使用する場合[HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)フィルター句と HOST_NAME 値を使用してデータ型を変換する必要があります[変換](../../t-sql/functions/cast-and-convert-transact-sql.md)します。 この場合のベスト プラクティスの詳細については、の「HOST_NAME() 値のオーバーライド」セクションを参照してください[Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)します。  
  
`[ @article_resolver = ] 'article_resolver'` COM ベース競合回避モジュール テーブル アーティクルで競合を解決するために使用またはテーブル アーティクルでカスタム ビジネス ロジックを実行する起動される .NET Framework アセンブリです。 *article_resolver*は**varchar (255)**、既定値は NULL です。 このパラメーターで利用できる値の一覧については、「[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタム競合回避モジュール」を参照してください。 指定した値が [!INCLUDE[msCoName](../../includes/msconame-md.md)] 競合回避モジュールの値でない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、システムに付属の競合回避モジュールの代わりに指定した競合回避モジュールが使用されます。 使用**sp_enumcustomresolvers**使用可能なカスタム競合回避モジュールの一覧を列挙します。 詳細については、次を参照してください。[マージ同期中にビジネス ロジックを実行](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)と[Merge Replication Conflict Detection の詳細と解決](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)します。  
  
`[ @resolver_info = ] 'resolver_info'` カスタム競合回避モジュールが必要な追加情報の指定に使用されます。 いくつかの[!INCLUDE[msCoName](../../includes/msconame-md.md)]競合回避モジュールが、競合回避モジュールへの入力として提供されている列が必要です。 *resolver_info*は**nvarchar (255)**、既定値は NULL です。 詳細については、「 [Microsoft COM ベースの競合回避モジュール](../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-resolvers.md)」を参照してください。  
  
`[ @source_owner = ] 'source_owner'` 所有者の名前を指定します、 *source_object*します。 *source_owner*は**sysname**、既定値は NULL です。 NULL の場合、現在のユーザーが所有者であると見なされます。  
  
`[ @destination_owner = ] 'destination_owner'` サブスクリプション データベースの場合はなく 'dbo' でオブジェクトの所有者です。 *destination_owner*は**sysname**、既定値は NULL です。 NULL の場合、'dbo' が所有者であると見なされます。  
  
`[ @vertical_partition = ] 'column_filter'` 有効にし、テーブル アーティクルに列フィルターを無効にします。 *vertical_partition*は**nvarchar (5)** 既定値は FALSE。  
  
 **false**垂直方向のフィルター処理がないことを示します、すべての列をパブリッシュします。  
  
 **true**宣言された主キー以外のすべての列と ROWGUID 列を消去します。 使用して列が追加**sp_mergearticlecolumn**します。  
  
`[ @auto_identity_range = ] 'automatic_identity_range'` 有効にし、自動 id 範囲の作成時、パブリケーションのパブリケーションでは、このテーブル アーティクルの処理を無効にします。 *auto_identity_range*は**nvarchar (5)**、既定値は FALSE。 **true**により、自動 id 範囲処理、 **false**無効にします。  
  
> [!NOTE]  
>  *auto_identity_range*は非推奨し、旧バージョンとの互換性を保つのために提供されます。 使用する必要があります*identityrangemanagementoption* id 範囲管理オプションを指定するためです。 詳細については、「[Replicate Identity Columns](../../relational-databases/replication/publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。  
  
`[ @pub_identity_range = ] pub_identity_range` コントロール自動 id 範囲管理を使用する場合に、サーバー サブスクリプションを使用してサブスクライバーに id 範囲のサイズが割り当てられます。 この ID 範囲は、再パブリッシュ元のサブスクライバーが自らのサブスクライバーに割り当てるために予約されています。 *identity_range*は**bigint**、既定値は NULL です。 場合、このパラメーターを指定する必要があります*identityrangemanagementoption*は**自動**場合*auto_identity_range*は**true**します。  
  
`[ @identity_range = ] identity_range` コントロール id 範囲のサイズ割り当てられる、パブリッシャーとサブスクライバーの両方自動 id 範囲管理を使用するとします。 *identity_range*は**bigint**、既定値は NULL です。 場合、このパラメーターを指定する必要があります*identityrangemanagementoption*は**自動**場合*auto_identity_range*は**true**します。  
  
> [!NOTE]  
>  *identity_range*再パブリッシュ サブスクライバーの以前のバージョンを使用して id 範囲のサイズを制御[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
`[ @threshold = ] threshold` マージ エージェントが新しい id 範囲を割り当てるときを制御するパーセンテージの値。 値の比率が指定されている場合*しきい値*はマージ エージェントは、新しい id 範囲を作成を使用します。 *しきい値*は**int**、既定値は NULL です。 場合、このパラメーターを指定する必要があります*identityrangemanagementoption*は**自動**場合*auto_identity_range*は**true**します。  
  
`[ @verify_resolver_signature = ] verify_resolver_signature` マージ レプリケーションで競合回避モジュールを使用する前にデジタル署名を検証するかどうかを指定します。 *verify_resolver_signature*は**int**、既定値は 1 です。  
  
 **0**署名は検証されませんを指定します。  
  
 **1**署名を信頼できる発行元かどうかを確認することを指定します。  
  
`[ @destination_object = ] 'destination_object'` サブスクリプション データベース内のオブジェクトの名前です。 *destination_object*は**sysname**、既定値は含まれている **@source_object**します。 このパラメーターは、アーティクルがストアド プロシージャ、ビュー、Udf など、スキーマ専用アーティクルがかどうかにのみ指定します。 指定したアーティクルが、テーブル アーティクルの値がかどうか*@source_object*で値をオーバーライド*destination_object*します。  
  
`[ @allow_interactive_resolver = ] 'allow_interactive_resolver'` 有効またはアーティクルに対するインタラクティブ競合回避モジュールの使用を無効にします。 *allow_interactive_resolver*は**nvarchar (5)**、既定値は FALSE。 **true**はアーティクルに対するインタラクティブ競合回避モジュールの使用を可能に**false**無効にします。  
  
> [!NOTE]  
>  インタラクティブ競合回避モジュールでサポートされていない[!INCLUDE[ssEW](../../includes/ssew-md.md)]サブスクライバー。  
  
`[ @fast_multicol_updateproc = ] 'fast_multicol_updateproc'` このパラメーターは非推奨とされましたが、スクリプトの旧バージョンと互換性が維持されます。  
  
`[ @check_permissions = ] check_permissions` マージ エージェントがパブリッシャーに変更を適用するときに検証されるテーブル レベル権限のビットマップ。 マージ処理が使用するパブリッシャーのログインまたはユーザー アカウントが正しいテーブル権限を持っていない場合、無効な変更は競合としてログに記録されます。 *check_permissions*は**int**、でき、 [|(ビットごとの OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md)次の値の 1 つ以上の製品です。  
  
|値|説明|  
|-----------|-----------------|  
|**0x00** (既定値)|権限は確認されません。|  
|**0x10**|サブスクライバー側で行われる挿入操作をアップロードする前に、パブリッシャー側で権限を確認します。|  
|**0x20**|サブスクライバー側で行われる更新操作をアップロードする前に、パブリッシャー側で権限を確認します。|  
|**0x40**|サブスクライバー側で行われる削除操作をアップロードする前に、パブリッシャー側で権限を確認します。|  
  
`[ @force_invalidate_snapshot = ] force_invalidate_snapshot` このストアド プロシージャが実行する操作が既存のスナップショットが無効になることを確認します。 *更によって*は、**ビット**、既定値は 0。  
  
 **0**アーティクルの追加も無効になるスナップショットは発生しませんを指定します。 ストアド プロシージャは、変更は、新しいスナップショットを必要になることを検出する場合は、エラーが発生し、変更は行われません。  
  
 **1**ことアーティクルを追加する可能性がありますが、無効になるスナップショットと、新しいスナップショットを必要とする既存のサブスクリプションがある場合は、アクセス許可を付与 obsolete としてマーク済みである既存のスナップショットを新しいスナップショットを生成を指定します。 *更によって*に設定されている**1**既存のスナップショットを持つパブリケーションにアーティクルを追加するときにします。  
  
`[ @published_in_tran_pub = ] 'published_in_tran_pub'` マージ パブリケーションでアーティクルがトランザクション パブリケーションででもパブリッシュすることを示します。 *published_in_tran_pub*は**nvarchar (5)**、既定値は FALSE。 **true**アーティクルがトランザクション パブリケーションでもパブリッシュことを指定します。  
  
`[ @force_reinit_subscription = ] force_reinit_subscription` このストアド プロシージャが実行されるアクションでは、既存のサブスクリプションの再初期化される場合がありますかを確認します。 *更によって*は、**ビット**、既定値は 0。  
  
 **0**アーティクルを追加することも、サブスクリプションを再初期化するのには発生しませんを指定します。 ストアド プロシージャは、変更が既存のサブスクリプションを再初期化する必要になることを検出する場合は、エラーが発生し、変更は行われません。  
  
 **1**マージ アーティクルへの変更によって既存のサブスクリプションを再初期化するサブスクリプションの再初期化を許可します。 *更によって*に設定されている**1**とき*subset_filterclause*パラメーター化された行フィルターを指定します。  
  
`[ @logical_record_level_conflict_detection = ] 'logical_record_level_conflict_detection'` 論理レコードのメンバーであるアーティクルの競合検出レベルを指定します。 *logical_record_level_conflict_detection*は**nvarchar (5)**、既定値は FALSE。  
  
 **true**任意の場所、論理レコードに変更があった場合に競合が検出されることを指定します。  
  
 **false**既定の競合検出を使用することを指定で指定された*column_tracking*します。 詳細については、「[Group Changes to Related Rows with Logical Records](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)」 (論理レコードによる関連行への変更のグループ化) を参照してください。  
  
> [!NOTE]  
>  論理レコードがサポートされていないため、[!INCLUDE[ssEW](../../includes/ssew-md.md)]の値を指定する必要がありますサブスクライバー、 **false**の*logical_record_level_conflict_detection*これらのサブスクライバーをサポートするためにします。  
  
`[ @logical_record_level_conflict_resolution = ] 'logical_record_level_conflict_resolution'` 論理レコードのメンバーであるアーティクルの競合解決レベルを指定します。 *logical_record_level_conflict_resolution*は**nvarchar (5)**、既定値は FALSE。  
  
 **true**優先されなかった論理レコード全体が、優先されなかった論理レコードを上書きすることを指定します。  
  
 **false**優先されなかった行が論理レコードに制約されないことを指定します。 場合*logical_record_level_conflict_detection*は**true**、し*logical_record_level_conflict_resolution*に設定する必要がありますも**true**. 詳細については、「[Group Changes to Related Rows with Logical Records](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)」 (論理レコードによる関連行への変更のグループ化) を参照してください。  
  
> [!NOTE]  
>  論理レコードがサポートされていないため、[!INCLUDE[ssEW](../../includes/ssew-md.md)]の値を指定する必要がありますサブスクライバー、 **false**の*logical_record_level_conflict_resolution*これらのサブスクライバーをサポートするためにします。  
  
`[ @partition_options = ] partition_options` アーティクル内のデータがパーティション分割されて 1 つのパーティションまたは 1 つのサブスクリプションのすべての行が属している場合に、パフォーマンスの最適化を有効にする方法を定義します。 *partition_options*は**tinyint**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0** (既定値)|アーティクルのフィルター処理または静的のいずれか、つまり「重複する」パーティションを各パーティションのデータの一意のサブセットを生成していません。|  
|**1**|パーティションが重複していると、データ操作言語 (DML) の更新がサブスクライバーで行が属しているパーティションを変更することはできません。|  
|**2**|重複しないパーティションでは、アーティクルのフィルター処理が生成されますが、複数のサブスクライバーが同じパーティションを受け取ることができます。|  
|**3**|アーティクルのフィルター処理には、サブスクリプションごとに固有の重複しないパーティションが生成されます。|  
  
> [!NOTE]  
>  アーティクルのソース テーブルが別のパブリケーションの値で既にパブリッシュされている場合*partition_options*の両方のアーティクルで同じである必要があります。  
  
`[ @processing_order = ] processing_order` マージ パブリケーションでアーティクルの処理順序を示します。 *processing_order*は**int**、既定値は 0。 **0**アーティクルが順序付けられたがないと、その他の値は、このアーティクルの処理順序の序数値を表すことを指定します。 アーティクルは、最も小さい値から最も大きい値の順序で処理されます。 処理順序が内のアーティクル ニックネームの順序によって決まりますが 2 つのアーティクルの値が同じ場合は、 [sysmergearticles](../../relational-databases/system-tables/sysmergearticles-transact-sql.md)システム テーブル。 詳細については、「[Specify Merge Replication properties](../../relational-databases/replication/merge/specify-merge-replication-properties.md)」 (マージ レプリケーションのプロパティの指定) を参照してください。  
  
`[ @subscriber_upload_options = ] subscriber_upload_options` クライアント サブスクリプションを使用したサブスクライバーで行われる更新の制限を定義します。 詳細については、「[ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)」を参照してください。 *subscriber_upload_options*は**tinyint**値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0** (既定値)|制限はありません。 サブスクライバー側で行われた変更は、パブリッシャーにアップロードされます。|  
|**1**|変更がサブスクライバーで、許可されているが、パブリッシャーにはアップロードされません。|  
|**2**|サブスクライバーでは、変更することはできません。|  
  
 変更する*subscriber_upload_options*を呼び出して再初期化するサブスクリプションが必要です[sp_reinitmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql.md)します。  
  
> [!NOTE]  
>  値、別のパブリケーションでアーティクルのソース テーブルが既にパブリッシュされている場合*subscriber_upload_options*の両方のアーティクルで同じである必要があります。  
  
`[ @identityrangemanagementoption = ] identityrangemanagementoption` アーティクルに対する id 範囲管理を処理する方法を指定します。 *identityrangemanagementoption*は**nvarchar (10)** 値は次のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**[なし]**|Id 範囲管理を無効にします。|  
|**手動**|手動による id 範囲処理を有効にする NOT FOR REPLICATION を使用して id 列をマークします。|  
|**自動**|Id 範囲の自動管理を指定します。|  
|NULL(default)|既定値は**none**ときの値*auto_identity_range*でない**true**します。|  
  
 旧バージョンとの互換性のためときの値*identityrangemanagementoption* null の場合の値は、 *auto_identity_range*がチェックされます。 ただし、場合の値*identityrangemanagementoption* null の場合、次の値でない*auto_identity_range*は無視されます。 詳細については、「[Replicate Identity Columns](../../relational-databases/replication/publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。  
  
`[ @delete_tracking = ] 'delete_tracking'` 削除がレプリケートされるかどうかを示します。 *delete_tracking*は**nvarchar (5)**、既定値は TRUE。 **false**削除はレプリケートされないことを示しますと**true**マージ レプリケーションの通常の動作で、削除がレプリケートされることを示します。 ときに*delete_tracking*に設定されている**false**、パブリッシャー、サブスクライバーで削除された行を手動で削除する必要があり、パブリッシャー側で削除された行はサブスクライバー側で手動で削除する必要があります。  
  
> [!IMPORTANT]  
>  設定*delete_tracking*に**false**未集約になります。 アーティクルのソース テーブルが別のパブリケーションの値で既にパブリッシュされている場合*delete_tracking*の両方のアーティクルで同じである必要があります。  
  
> [!NOTE]  
>  *delete_tracking*を使用してオプションを設定することはできません、**パブリケーションの新規作成ウィザード**または**パブリケーションのプロパティ** ダイアログ ボックス。  
  
`[ @compensate_for_errors = ] 'compensate_for_errors'` 同期中にエラーが発生したときに、補正アクションが行われるかどうかを示します。 *compensate_for_errors は*s **nvarchar (5)**、既定値は FALSE。 設定すると**true**変更をサブスクライバーで適用できないまたは、変更を元に戻す補正アクションを常に同期中にパブリッシャーがありますただし、いずれかが正しく構成されていない、エラーが生成するサブスクライバー。元に戻すには他のサブスクライバーとパブリッシャーで加えられた変更が発生します。 **false**補正、およびそれ以降のマージで成功するまで、変更を適用するにはこの補正アクション、ただし、エラーも記録を無効にします。  
  
> [!IMPORTANT]  
>  影響を受ける行のデータは収束されないように見えますが、エラーを解決すると、変更は直ちに適用可能となり、データは収束されます。 アーティクルのソース テーブルが別のパブリケーションの値で既にパブリッシュされている場合*compensate_for_errors*の両方のアーティクルで同じである必要があります。  
  
`[ @stream_blob_columns = ] 'stream_blob_columns'` バイナリ ラージ オブジェクト列をレプリケートするときに、データ ストリームの最適化を使用することを指定します。 *stream_blob_columns*は**nvarchar (5)**、既定値は FALSE。 **true**最適化が試行されることを意味します。 *stream_blob_columns* FILESTREAM が有効な場合は true に設定されます。 これにより、最適に実行し、メモリ使用率を低減する FILESTREAM データのレプリケーションができます。 Blob ストリームを使用しないように FILESTREAM のテーブル アーティクルを強制的には、次のように使用します。 **sp_changemergearticle**を設定する*stream_blob_columns*を false にします。  
  
> [!IMPORTANT]  
>  このメモリ最適化を有効にすると、同期中に、マージ エージェントのパフォーマンスが低下する可能性があります。 このオプションは、メガバイト単位のデータを含む列をレプリケートする場合にのみ使用する必要があります。  
  
> [!NOTE]  
>  論理レコードなど、特定のマージ レプリケーション機能を使用してもバイナリ ラージ オブジェクトをレプリケートするときに使用されている、ストリームの最適化を妨げられる*stream_blob_columns*設定**true**.  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addmergearticle**はマージ レプリケーションで使用します。  
  
 オブジェクトを発行するときに、その定義がサブスクライバーにコピーされます。 その他の 1 つまたは複数のオブジェクトに依存するデータベース オブジェクトをパブリッシュする場合は、すべての参照先オブジェクトを発行する必要があります。 たとえば、テーブルに依存しているビューをパブリッシュする場合は、そのテーブルもパブリッシュする必要があります。  
  
 値を指定する場合**3**の*partition_options*を単一のサブスクリプションのみパーティションごとにそのアーティクル内のデータがあります。 第 2 のサブスクリプションを作成し、その新しいサブスクリプションのフィルター選択条件が既存のサブスクリプションと同じパーティションとして判別される場合、既存のサブスクリプションは削除されます。  
  
 3 の値を指定するときに*partition_options*メタデータがクリーンアップたびに、マージ エージェントを実行し、パーティション スナップショット有効期限が短くします。 このオプションを使用する場合は、要求されたパーティション スナップショットをサブスクライバーの有効化を検討してください。 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)」をご覧ください。  
  
 使用して、静的行フィルターでアーティクルを追加する*subset_filterclause*を既存のパブリケーションがパラメーター化されたフィルターの記事では、サブスクリプションを再初期化する必要があります。  
  
 指定するときに*processing_order*をお勧めします記事順序の値の間にすきまを残したりを簡単に、将来新しい値を設定します。 たとえば、Article1、Article2、Article3 の 3 つのアーティクルがあれば、設定*processing_order* 10、20、30 ではなく 1、2、および 3 にします。 詳細については、「[Specify Merge Replication properties](../../relational-databases/replication/merge/specify-merge-replication-properties.md)」 (マージ レプリケーションのプロパティの指定) を参照してください。  
  
## <a name="default-schema-option-table"></a>既定のスキーマ オプションの一覧  
 次の表は、NULL 値が指定されている場合、ストアド プロシージャによって設定されている既定値を示します*schema_option*アーティクルの種類によって決まります。  
  
|アーティクルの種類|スキーマ オプションの値|  
|------------------|-------------------------|  
|**func スキーマのみ**|**0x01**|  
|**インデックス付きビュー スキーマのみ**|**0x01**|  
|**proc スキーマのみ**|**0x01**|  
|**table**|**0x0C034FD1**  -  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]と、ネイティブ モードのスナップショット以降のバージョン互換性のあるパブリケーションです。<br /><br /> **0x08034FF1**  -  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]とキャラクター モードのスナップショット以降のバージョン互換性のあるパブリケーションです。|  
|**ビュー スキーマのみ**|**0x01**|  
  
> [!NOTE]  
>  パブリケーションは、以前のバージョンをサポートしている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、既定のスキーマ オプション**テーブル**は**0x30034FF1**します。  
  
## <a name="valid-schema-option-table"></a>有効なスキーマ オプションの一覧  
 次の表に、許可されている値*schema_option*アーティクルの種類によって異なります。  
  
|アーティクルの種類|スキーマ オプションの値|  
|------------------|--------------------------|  
|**func スキーマのみ**|**0x01**と**0x2000**|  
|**インデックス付きビュー スキーマのみ**|**0x01**、 **0x040**、 **0x0100**、 **0x2000**、 **0x40000**、 **0x1000000**、および**0x200000**|  
|**proc スキーマのみ**|**0x01**と**0x2000**|  
|**table**|すべてのオプション。|  
|**ビュー スキーマのみ**|**0x01**、 **0x040**、 **0x0100**、 **0x2000**、 **0x40000**、 **0x1000000**、および**0x200000**|  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-addmergearticle-trans_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 **sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Id 列をレプリケートします。](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [sp_changemergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_dropmergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [sp_helpmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
