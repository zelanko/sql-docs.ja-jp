---
title: "sp_addmergearticle (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_addmergearticle
- sp_addmergearticle_TSQL
helpviewer_keywords: sp_addmergearticle
ms.assetid: 0df654ea-24e2-4c61-a75a-ecaa7a140a6c
caps.latest.revision: "69"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: cd9d9ead2695338116dd3da6a60285756cb433c6
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spaddmergearticle-transact-sql"></a>sp_addmergearticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のマージ パブリケーションにアーティクルを追加します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
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
 [  **@publication=** ] **'***パブリケーション***'**  
 目的のアーティクルを含むパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article=** ] **'***記事***'**  
 アーティクルの名前を指定します。 名前はパブリケーション内で一意であることが必要です。 *記事*は**sysname**、既定値はありません。 *記事*を実行しているローカル コンピューター上に存在する必要があります[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子の規則に従っている必要があります。  
  
 [  **@source_object=** ] **'***source_object***'**  
 パブリッシュされるデータベース オブジェクトを指定します。 *source_object*は**sysname**、既定値はありません。 マージ レプリケーションを使用してパブリッシュできるオブジェクトの種類の詳細については、次を参照してください。[公開データおよびデータベース オブジェクト](../../relational-databases/replication/publish/publish-data-and-database-objects.md)です。  
  
 [  **@type=** ] **'***型***'**  
 アーティクルの種類を指定します。 *型*は**sysname**、既定値は**テーブル**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**テーブル**(既定値)|スキーマとデータを持つテーブルです。 レプリケーションはテーブルを監視して、レプリケートするデータを特定します。|  
|**func スキーマのみ**|スキーマのみを使用する関数。|  
|**インデックス付きビュー** **スキーマのみ**|スキーマのみを使用するインデックス付きビュー。|  
|**proc スキーマのみ**|スキーマのみを使用するストアド プロシージャ。|  
|**シノニム スキーマのみ**|スキーマのみを使用するシノニム。|  
|**ビュー スキーマのみ**|スキーマのみを使用するビュー。|  
  
 [  **@description=** ] **'***説明***'**  
 アーティクルの説明を指定します。 *説明*は**nvarchar (255)**、既定値は NULL です。  
  
 [  **@column_tracking=** ] **'***column_tracking***'**  
 列レベルの追跡の設定を指定します。 *column_tracking*は**nvarchar (10)**、既定値は FALSE。 **true**列追跡をオンにします。 **false**列追跡をオフにし、行レベルで競合検出のままです。 テーブルが他のマージ レプリケーションで既にパブリッシュされている場合は、このテーブルに基づく既存のアーティクルが使用しているものと同じ列追跡値を使用する必要があります。 このパラメーターは、テーブル アーティクルのみに固有のものです。  
  
> [!NOTE]  
>  行レベルの追跡を使用して競合を検出する場合 (既定値)、ベース テーブルには最大 1,024 列含めることができますが、最大 246 列がパブリッシュされるようにアーティクルから列をフィルター選択する必要があります。 列の追跡を使用する場合、ベース テーブルには最大 246 列を含めることができます。  
  
 [  **@status=** ] **'***ステータス***'**  
 アーティクルの状態を指定します。 *ステータス*は**nvarchar (10)**、既定値は**unsynced**です。 場合**active**テーブルをパブリッシュする初期処理スクリプトを実行します。 場合**unsynced**、次回、スナップショット エージェントの実行時にテーブルをパブリッシュする初期処理スクリプトが実行されます。  
  
 [  **@pre_creation_cmd=** ] **'***pre_creation_cmd***'**  
 スナップショットの適用時、サブスクライバーにテーブルが存在した場合にシステムが実行する処理を指定します。 *pre_creation_cmd*は**nvarchar (10)**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**[なし]**|サブスクライバーに既にテーブルがある場合、操作は何も行われません。|  
|**削除**|サブセット フィルター内の WHERE 句に基づいて削除します。|  
|**drop** (既定値)|テーブルを再作成する前に削除します。 サポートするために必要な[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssEW](../../includes/ssew-md.md)]サブスクライバーです。|  
|**truncate**|レプリケーション先テーブルを切り捨てます。|  
  
 [  **@creation_script=** ] **'***creation_script***'**  
 オプションのアーティクル スキーマ スクリプトのパスと名前を指定します。このスクリプトは、サブスクリプション データベースでアーティクルを作成する場合に使用されます。 *creation_script*は**nvarchar (255)**、既定値は NULL です。  
  
> [!NOTE]  
>  作成スクリプトは [!INCLUDE[ssEW](../../includes/ssew-md.md)] サブスクライバー上では実行されません。  
  
 [  **@schema_option=** ] *schema_option*  
 特定のアーティクルに対するスキーマ生成オプションのビットマップを指定します。 *schema_option*は**binary (8)**、可能であり、 [|(ビットごとの OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md)これらの値の 1 つ以上の製品です。  
  
|値|Description|  
|-----------|-----------------|  
|**0x00**|スナップショット エージェントによるスクリプト作成を無効にしで定義されている指定されたスキーマ事前作成スクリプトを使用して*creation_script*です。|  
|**0x01**|オブジェクト作成 (CREATE TABLE、CREATE PROCEDURE など) を生成します。 これは、ストアド プロシージャ アーティクルの既定値です。|  
|**0x10**|対応するクラスター化インデックスを生成します。 このオプションが設定されていない場合でも、パブリッシュされたテーブルに主キーと UNIQUE 制約が既に定義されている場合は、これらの主キーや制約に関連するインデックスが生成されます。|  
|**0x20**|サブスクライバーでユーザー定義データ型 (UDT) を基本データ型に変換します。 UDT 列に CHECK 制約または DEFAULT 制約があるときに、UDT 列が主キーの一部になっている場合、または計算列で UDT 列が参照されている場合、このオプションは使用できません。|  
|**0x40**|対応する非クラスター化インデックスを生成します。 このオプションが設定されていない場合でも、パブリッシュされたテーブルに主キーと UNIQUE 制約が既に定義されている場合は、これらの主キーや制約に関連するインデックスが生成されます。|  
|**0x80**|PRIMARY KEY 制約をレプリケートします。 制約に関連するすべてのインデックスもレプリケートされる場合でもオプション**0x10**と**0x40**有効ではありません。|  
|**0x100**|定義されている場合、テーブル アーティクル上のユーザー トリガーをレプリケートします。|  
|**0x200**|FOREIGN KEY 制約をレプリケートします。 参照するテーブルがパブリケーションの一部でない場合は、パブリッシュされたテーブルのすべての FOREIGN KEY 制約がレプリケートされるわけではありません。|  
|**0x400**|CHECK 制約をレプリケートします。|  
|**0x800**|既定値をレプリケートします。|  
|**0x1000**|列レベルの照合順序をレプリケートします。|  
|**0x2000**|パブリッシュされたアーティクルのソース オブジェクトに関連付けられた拡張プロパティをレプリケートします。|  
|**0x4000**|UNIQUE 制約をレプリケートします。 制約に関連するすべてのインデックスもレプリケートされる場合でもオプション**0x10**と**0x40**有効ではありません。|  
|**0x8000**|このオプションは、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降のバージョンを実行しているパブリッシャーでは有効ではありません。|  
|**0x10000**|CHECK 制約を NOT FOR REPLICATION としてレプリケートして、この制約が同期中に適用されないようにします。|  
|**0x20000**|FOREIGN KEY 制約を NOT FOR REPLICATION としてレプリケートして、この制約が同期中に適用されないようにします。|  
|**0x40000**|パーティション テーブルまたはインデックスに関連付けられているファイル グループをレプリケートします。|  
|**これに対して、0x80000**|パーティション テーブルのパーティション構成をレプリケートします。|  
|**0x100000**|パーティション インデックスのパーティション構成をレプリケートします。|  
|**0x200000**|テーブルの統計をレプリケートします。|  
|**0x400000**|既定のバインドをレプリケートします。|  
|**0x800000**|ルールのバインドをレプリケートします。|  
|**0x1000000**|フルテキスト インデックスをレプリケートします。|  
|**0x2000000**|バインドされた XML スキーマ コレクション**xml**列はレプリケートされません。|  
|**0x4000000**|インデックスをレプリケート**xml**列です。|  
|**0x8000000**|サブスクライバーにまだ存在していないすべてのスキーマを作成します。|  
|**0x10000000**|変換します**xml**列**ntext**サブスクライバーにします。|  
|**0x20000000**|変換の大きなオブジェクトのデータ型 (**nvarchar (max)**、 **varchar (max)**、および**varbinary (max)**) で導入された[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]でサポートされているデータ型[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].|  
|**0x40000000**|権限をレプリケートします。|  
|**0x80000000**|パブリケーションの一部ではない任意のオブジェクトに対する依存関係の削除を試行します。|  
|**0x100000000**|このオプションを使用して指定されている場合に、FILESTREAM 属性をレプリケート**varbinary (max)**列です。 テーブルをレプリケートしている場合は、このオプションを指定しない[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]サブスクライバーです。 FILESTREAM 列を持つテーブルをレプリケート[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]サブスクライバーがサポートされていません、このスキーマ オプションを設定する方法に関係なく、します。 関連するオプションを参照してください**0x800000000**です。|  
|**0x200000000**|日付と時刻のデータ型に変換 (**日付**、**時間**、 **datetimeoffset**、および**datetime2**) で導入された[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]データ以前のバージョンでサポートされている種類[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。|  
|**0x400000000**|データとインデックスの圧縮オプションをレプリケートします。 詳細については、「 [Data Compression](../../relational-databases/data-compression/data-compression.md)」を参照してください。|  
|**0x800000000**|このオプションを設定すると、サブスクライバーの独自のファイル グループに FILESTREAM データを格納できます。 このオプションが設定されていない場合、FILESTREAM データは既定のファイル グループに格納されます。 レプリケーションではファイル グループは作成されないので、このオプションを設定する場合は、サブスクライバーでスナップショットを適用する前にファイル グループを作成しておく必要があります。 スナップショットを適用する前に、オブジェクトを作成する方法の詳細については、次を参照してください。[前にスクリプトを実行し、後のスナップショットが適用される](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)です。<br /><br /> 関連するオプションを参照してください**0x100000000**です。|  
|**0x1000000000**|共通言語ランタイム (CLR) ユーザー定義型 (Udt) に変換**varbinary (max)**を実行しているサブスクライバーに UDT 型の列をレプリケートできるように[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]です。|  
|**0x2000000000**|変換、 **hierarchyid**のデータ型**varbinary (max)**ように型の列**hierarchyid**実行しているサブスクライバーにレプリケートできる[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]です。 使用する方法の詳細についての**hierarchyid**レプリケートされたテーブル内の列を参照してください[hierarchyid &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/hierarchyid-data-type-method-reference.md).|  
|**0x4000000000**|テーブルのフィルター選択されたインデックスをレプリケートします。 フィルター選択されたインデックスの詳細については、次を参照してください。 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)です。|  
|**0x8000000000**|変換、 **geography**と**geometry**データ型を**varbinary (max)** を実行しているサブスクライバーにこれらの型の列をレプリケートできるように[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
|**0x10000000000**|型の列にインデックスをレプリケート**geography**と**geometry**です。|  
  
 この値が NULL の場合は、アーティクルの有効なスキーマ オプションが自動生成されます。 **スキーマ オプションの既定の**「解説」セクション内のテーブル アーティクルの種類に基づいて選択される値を示しています。 また、すべて*schema_option*レプリケーションのすべての種類およびアーティクルの種類の有効な値です。 **有効なスキーマ オプション**表は、「解説」で特定種類のアーティクルに対して指定できるオプションが表示されます。  
  
> [!NOTE]  
>  *Schema_option*パラメーターでは、初期スナップショットのレプリケーション オプションだけに影響します。 最初のスキーマをスナップショット エージェントによって生成され、サブスクライバーで適用すると、サブスクライバーにパブリケーションのスキーマ変更のレプリケーションがスキーマ変更レプリケーション ルールに基づいてで発生して、 *replicate_ddl*指定されたパラメーター設定[sp_addmergepublication](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)です。 詳細については、「[パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)」を参照してください。  
  
 [  **@subset_filterclause=** ] **'***subset_filterclause***'**  
 テーブル アーティクルの行フィルター選択を指定する、WHERE という語が含まれていない WHERE 句を指定します。 *subset_filterclause*の**nvarchar (1000)**の既定値は空の文字列。  
  
> [!IMPORTANT]  
>  パラメーター化された行フィルター句では列名に関数を適用しないことをお勧めします。これは、 `LEFT([MyColumn]) = SUSER_SNAME()`のように指定すると、パフォーマンスに問題が生じるためです。 使用する場合[HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)フィルター句と HOST_NAME 値よりも優先的に適用する場合を使用してデータ型を変換する必要があります[変換](../../t-sql/functions/cast-and-convert-transact-sql.md)です。 この場合のベスト プラクティスに関する詳細については、セクションの「HOST_NAME() 値のオーバーライド」を参照してください[Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)です。  
  
 [  **@article_resolver=** ] **'***article_resolver***'**  
 テーブル アーティクルで競合の回避に使用する COM ベースの競合回避モジュール、またはテーブル アーティクルでカスタム ビジネス ロジックを実行するために起動される .NET Framework アセンブリを指定します。 *article_resolver*は**varchar (255)**、既定値は NULL です。 このパラメーターで利用できる値の一覧については、「[!INCLUDE[msCoName](../../includes/msconame-md.md)] カスタム競合回避モジュール」を参照してください。 指定した値が [!INCLUDE[msCoName](../../includes/msconame-md.md)] 競合回避モジュールの値でない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、システムに付属の競合回避モジュールの代わりに指定した競合回避モジュールが使用されます。 使用して**sp_enumcustomresolvers**を利用可能なカスタム競合回避モジュールの一覧を列挙します。 詳細については、次を参照してください。[マージ同期中にビジネス ロジックを実行](../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)と[Advanced Merge Replication Conflict Detection と解像度](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)です。  
  
 [  **@resolver_info=** ] **'***resolver_info***'**  
 カスタム競合回避モジュールが必要とする追加の情報の指定に使用します。 一部の[!INCLUDE[msCoName](../../includes/msconame-md.md)]競合回避モジュールが、競合回避モジュールへの入力として提供される列を必要とします。 *resolver_info*は**nvarchar (255)**、既定値は NULL です。 詳細については、「 [Microsoft COM ベースの競合回避モジュール](../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-resolvers.md)」を参照してください。  
  
 [  **@source_owner=** ] **'***source_owner***'**  
 所有者の名前を指定します、 *source_object*です。 *source_owner*は**sysname**、既定値は NULL です。 NULL を指定した場合は、現在のユーザーが所有者であるものと見なされます。  
  
 [  **@destination_owner=** ] **'***destination_owner***'**  
 所有者が "dbo" ではない場合、サブスクリプション データベースのオブジェクトの所有者を指定します。 *destination_owner*は**sysname**、既定値は NULL です。 NULL を指定した場合は、'dbo' が所有者であるものと見なされます。  
  
 [  **@vertical_partition=** ] **'***column_filter***'**  
 テーブル アーティクル上の列フィルター選択を有効または無効にします。 *vertical_partition*は**nvarchar (5)**既定値は FALSE。  
  
 **false**垂直方向のフィルタ リングがないことを示します、すべての列をパブリッシュします。  
  
 **true**宣言された主キー以外のすべての列と ROWGUID 列を消去します。 列を使用して追加された**sp_mergearticlecolumn**です。  
  
 [  **@auto_identity_range=** ] **'***automatic_identity_range***'**  
 パブリケーションの作成時に、パブリケーション上でこのテーブル アーティクルの ID 範囲の自動処理を有効または無効にします。 *auto_identity_range*は**nvarchar (5)**、既定値は FALSE。 **true**により、自動 id 範囲処理、 **false**それを無効にします。  
  
> [!NOTE]  
>  *auto_identity_range*は廃止されておりは旧バージョンとの互換性を保つのために提供します。 使用する必要があります*identityrangemanagementoption* id 範囲管理オプションを指定するためです。 詳細については、「[Replicate Identity Columns](../../relational-databases/replication/publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。  
  
 [  **@pub_identity_range=** ] *identity_range*  
 自動 ID 範囲の管理を使用しているときに、サーバー サブスクリプションでサブスクライバーに割り当てられる ID 範囲のサイズを制御します。 この ID 範囲は、再パブリッシュ元のサブスクライバーが自らのサブスクライバーに割り当てるために予約されています。 *identity_range*は**bigint**、既定値は NULL です。 場合は、このパラメーターを指定する必要があります*identityrangemanagementoption*は**自動**場合*auto_identity_range*は**true**です。  
  
 [  **@identity_range=** ] *identity_range*  
 自動 ID 範囲の管理を使用するときに、パブリッシャーとサブスクライバーの両方に割り当てられる ID 範囲のサイズを制御します。 *identity_range*は**bigint**、既定値は NULL です。 場合は、このパラメーターを指定する必要があります*identityrangemanagementoption*は**自動**場合*auto_identity_range*は**true**です。  
  
> [!NOTE]  
>  *identity_range*再パブリッシュ サブスクライバーの以前のバージョンを使用して id 範囲サイズを制御[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 [  **@threshold=** ]*しきい値*  
 マージ エージェントがどの時点で新しい ID 範囲を割り当てるかを制御するパーセンテージ値です。 値の比率が指定されている場合*しきい値*はマージ エージェントは、新しい id 範囲を作成を使用します。 *しきい値*は**int**、既定値は NULL です。 場合は、このパラメーターを指定する必要があります*identityrangemanagementoption*は**自動**場合*auto_identity_range*は**true**です。  
  
 [  **@verify_resolver_signature=** ] *verify_resolver_signature*  
 マージ レプリケーションで競合回避モジュールを使用する前に、デジタル署名を検証するかどうかを指定します。 *verify_resolver_signature*は**int**、既定値は 1 です。  
  
 **0**署名は確認されませんを指定します。  
  
 **1**署名が元が信頼できるかどうかを確認することを指定します。  
  
 [  **@destination_object=** ] **'***destination_object***'**  
 サブスクリプション データベース内のオブジェクトの名前を指定します。 *destination_object*は**sysname**での新機能の既定値を持つ **@source_object**です。 このパラメーターは、アーティクルが、ストアド プロシージャ、ビュー、UDF など、スキーマ専用アーティクルである場合にのみ指定できます。 指定したアーティクルが、テーブル アーティクルの値がかどうか *@source_object* 内の値をオーバーライド*destination_object*です。  
  
 [  **@allow_interactive_resolver=** ] **'***allow_interactive_resolver***'**  
 アーティクルに対するインタラクティブ競合回避モジュールの使用を有効または無効にします。 *allow_interactive_resolver*は**nvarchar (5)**、既定値は FALSE。 **true**はアーティクルに対するインタラクティブ競合回避モジュールを使用できます**false**それを無効にします。  
  
> [!NOTE]  
>  インタラクティブ競合回避モジュールでサポートされていない[!INCLUDE[ssEW](../../includes/ssew-md.md)]サブスクライバーです。  
  
 [  **@fast_multicol_updateproc=** ] **'***@fast_multicol_updateproc***'**  
 このパラメーターは、スクリプトの下位互換性を確保するために用意されているものであり、使用は推奨されません。  
  
 [  **@check_permissions=** ] *check_permissions*  
 マージ エージェントがパブリッシャーに変更を適用するときに確認されるテーブルレベル権限のビットマップです。 マージ処理が使用するパブリッシャーのログインまたはユーザー アカウントが正しいテーブル権限を持っていない場合、無効な変更は競合としてログに記録されます。 *check_permissions*は**int**、可能であり、 [|(ビットごとの OR)](../../t-sql/language-elements/bitwise-or-transact-sql.md)値は次の 1 つ以上の製品です。  
  
|値|Description|  
|-----------|-----------------|  
|**0x00** (既定値)|権限は確認されません。|  
|**0x10**|サブスクライバーで行われる挿入操作をアップロードする前に、パブリッシャーでの権限を確認します。|  
|**0x20**|サブスクライバーで行われる更新操作をアップロードする前に、パブリッシャーでの権限を確認します。|  
|**0x40**|サブスクライバーで行われる削除操作をアップロードする前に、パブリッシャーでの権限を確認します。|  
  
 [  **@force_invalidate_snapshot=** ]*更によって*  
 このストアド プロシージャが実行する操作によって既存のスナップショットが無効になることを許可します。 *更によって*は、**ビット**、既定値は 0 です。  
  
 **0**がアーティクルを追加するがでないスナップショットが無効であることを指定します。 ストアド プロシージャで、変更に新しいスナップショットが必要であることが検出されると、エラーが発生し、変更は加えられません。  
  
 **1**するアーティクルを追加するスナップショットが無効であることがあり、新しいスナップショットを必要とする既存のサブスクリプションがある場合、既存のスナップショット不使用とマークすると、新しいスナップショットを生成を指定します。 *更によって*に設定されている**1**が既存のスナップショットを持つパブリケーションにアーティクルを追加するときにします。  
  
 [  **@published_in_tran_pub=** ] **'***published_in_tran_pub***'**  
 マージ パブリケーション内のアーティクルが、トランザクション パブリケーションでもパブリッシュされるかどうかを示します。 *published_in_tran_pub*は**nvarchar (5)**、既定値は FALSE。 **true**アーティクルがトランザクション パブリケーションでもパブリッシュことを指定します。  
  
 [  **@force_reinit_subscription=** ]*更によって*  
 このストアド プロシージャが実行する操作によって、既存のサブスクリプションの再初期化が必要になることを許可します。 *更によって*は、**ビット**、既定値は 0 です。  
  
 **0**アーティクルを追加することも、サブスクリプションを再初期化するのには発生しませんを指定します。 変更に既存のサブスクリプションの再初期化が必要であることをストアド プロシージャが検出すると、エラーが発生し、変更は加えられません。  
  
 **1**と、既存のサブスクリプションが初期化されることをマージ アーティクルに変更することを意味し、サブスクリプションを再初期化が発生するを許可します。 *更によって*に設定されている**1**とき*subset_filterclause*パラメーター化された行フィルターを指定します。  
  
 [  **@logical_record_level_conflict_detection=** ] **'***logical_record_level_conflict_detection***'**  
 論理レコードのメンバーであるアーティクルの競合検出レベルを指定します。 *logical_record_level_conflict_detection*は**nvarchar (5)**、既定値は FALSE。  
  
 **true**論理レコードのどこでも変更が加えられた場合に競合が検出されることを指定します。  
  
 **false**既定の競合検出を使用することを指定して指定されたとおり*column_tracking*です。 詳細については、「[Group Changes to Related Rows with Logical Records](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)」 (論理レコードによる関連行への変更のグループ化) を参照してください。  
  
> [!NOTE]  
>  論理レコードでサポートされていないため[!INCLUDE[ssEW](../../includes/ssew-md.md)]のサブスクライバー, の値を指定する必要があります**false**の*logical_record_level_conflict_detection*これらのサブスクライバーをサポートするためにします。  
  
 [  **@logical_record_level_conflict_resolution=** ] **'***logical_record_level_conflict_resolution***'**  
 論理レコードのメンバーであるアーティクルの競合解決レベルを指定します。 *logical_record_level_conflict_resolution*は**nvarchar (5)**、既定値は FALSE。  
  
 **true**優先されなかった論理レコード全体が優先されなかった論理レコードを上書きすることを指定します。  
  
 **false**優先されなかった行が論理レコードに制約を受けないことを指定します。 場合*logical_record_level_conflict_detection*は**true**、し*logical_record_level_conflict_resolution*にも設定する必要があります**true**. 詳細については、「[Group Changes to Related Rows with Logical Records](../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)」 (論理レコードによる関連行への変更のグループ化) を参照してください。  
  
> [!NOTE]  
>  論理レコードでサポートされていないため[!INCLUDE[ssEW](../../includes/ssew-md.md)]のサブスクライバー, の値を指定する必要があります**false**の*logical_record_level_conflict_resolution*これらのサブスクライバーをサポートするためにします。  
  
 [  **@partition_options=** ] *partition_options*  
 アーティクル内のデータをパーティション分割する方法を定義します。パーティション分割することにより、すべての行が 1 つのパーティションまたは 1 つのサブスクリプションに属している場合に、パフォーマンスを最適化できます。 *partition_options*は**tinyint**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**0** (既定値)|アーティクルのフィルター選択は、静的であるか、または各パーティション用にデータの一意なサブセットを作成しません。つまり、"重複する" パーティションになります。|  
|**1**|パーティションは重複しています。サブスクライバーで実行されたデータ操作言語 (DML) の更新では、行が属するパーティションを変更できません。|  
|**2**|アーティクルのフィルター選択により、重複しないパーティションが作成されますが、複数のサブスクライバーは同じパーティションを受け取ることができます。|  
|**3**|アーティクルのフィルター選択により、各サブスクリプションに対して、一意で重複しないパーティションが作成されます。|  
  
> [!NOTE]  
>  アーティクルのソース テーブルが、別のパブリケーションの値で既にパブリッシュされている場合*partition_options*の両方のアーティクルで同じである必要があります。  
  
 [  **@processing_order=** ] *processing_order*  
 マージ パブリケーション内のアーティクルの処理順序を示します。 *processing_order*は**int**、既定値は 0 です。 **0**アーティクルが順序付けられた、し、その他の値は、このアーティクルの処理順序の序数値を表すことを指定します。 アーティクルは、最も小さい値から最も大きい値の順序で処理されます。 処理順序が内のアーティクルのニックネームの順序によって決まりますが 2 つのアーティクルの値が同じ場合は、 [sysmergearticles](../../relational-databases/system-tables/sysmergearticles-transact-sql.md)システム テーブル。 詳細については、「[Specify the Processing Order of Merge Articles](../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)」 (マージ アーティクルの処理順序の指定) を参照してください。  
  
 [  **@subscriber_upload_options=** ] *subscriber_upload_options*  
 サブスクライバーにおける、クライアント サブスクリプションを使用した更新に対する制限を定義します。 詳細については、「[ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)」を参照してください。 *subscriber_upload_options*は**tinyint**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**0** (既定値)|制限はありません。 サブスクライバー側で行われた変更は、パブリッシャーにアップロードされます。|  
|**1**|サブスクライバー側での変更は可能ですが、パブリッシャーに変更はアップロードされません。|  
|**2**|サブスクライバー側での変更は許可されていません。|  
  
 変更する*subscriber_upload_options*を呼び出すことで再初期化するサブスクリプションが必要です[sp_reinitmergepullsubscription (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-reinitmergepullsubscription-transact-sql.md).  
  
> [!NOTE]  
>  値、別のパブリケーションでアーティクルのソース テーブルが既にパブリッシュされている場合*subscriber_upload_options*の両方のアーティクルで同じである必要があります。  
  
 [  **@identityrangemanagementoption=** ] *identityrangemanagementoption*  
 アーティクルに対する ID 範囲の管理がどのように処理されるかを指定します。 *identityrangemanagementoption*は**nvarchar (10)**値は次のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**[なし]**|ID 範囲の管理を無効にします。|  
|**手動**|NOT FOR REPLICATION を使用して手動による ID 範囲処理を有効にしている ID 列にマークを付けます。|  
|**自動**|ID 範囲の自動管理を指定します。|  
|NULL(default)|既定値は**なし**ときの値*auto_identity_range*は**true**です。|  
  
 旧バージョンとの互換性のためときの値*identityrangemanagementoption* NULL の場合の値は、 *auto_identity_range*がチェックします。 ただし、場合の値*identityrangemanagementoption* NULL の場合、次の値ではありません*auto_identity_range*は無視されます。 詳細については、「[Replicate Identity Columns](../../relational-databases/replication/publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。  
  
 [  **@delete_tracking=** ] **'***delete_tracking***'**  
 削除がレプリケートされるかどうかを示します。 *delete_tracking*は**nvarchar (5)**、既定値は TRUE です。 **false**削除がレプリケートされないことを示すと**true**マージ レプリケーションの通常の動作で、削除がレプリケートされることを示します。 ときに*delete_tracking*に設定されている**false**パブリッシャー、サブスクライバーで削除された行を手動で削除する必要があります、およびサブスクライバー、パブリッシャー側で削除された行を手動で削除する必要があります。  
  
> [!IMPORTANT]  
>  設定*delete_tracking*に**false**の非収束の結果します。 アーティクルのソース テーブルが、別のパブリケーションの値で既にパブリッシュされている場合*delete_tracking*の両方のアーティクルで同じである必要があります。  
  
> [!NOTE]  
>  *delete_tracking*を使用してオプションを設定することはできません、**新規パブリケーション ウィザード**または**パブリケーションのプロパティ** ダイアログ ボックス。  
  
 [  **@compensate_for_errors=** ] **'***compensate_for_errors***'**  
 同期中にエラーが検出されたときに補正アクションが行われるかどうかを示します。 *compensate_for_errors すれば*s **nvarchar (5)**、既定値は FALSE。 設定すると**true**変更をサブスクライバーで適用できないまたは、変更を元に戻す補正アクションを常に同期中にパブリッシャーが生じるただし、いずれか正しく構成されていないエラーが生成するサブスクライバー。元に戻すには他のサブスクライバーとパブリッシャーで加えられた変更が発生します。 **false**この補正アクション、ただし、エラーは引き続きログ記録補正、およびそれ以降のマージが成功するまで、変更を適用しようとするにつれてを無効にします。  
  
> [!IMPORTANT]  
>  影響を受ける行のデータは収束されないように見えますが、エラーを解決すると、変更は直ちに適用可能となり、データは収束されます。 アーティクルのソース テーブルが、別のパブリケーションの値で既にパブリッシュされている場合*compensate_for_errors*の両方のアーティクルで同じである必要があります。  
  
 [  **@stream_blob_columns=** ] **'***stream_blob_columns***'**  
 バイナリ ラージ オブジェクトの列をレプリケートするときに、データ ストリームの最適化を使用します。 *stream_blob_columns*は**nvarchar (5)**、既定値は FALSE。 **true**最適化が試行されることを意味します。 *stream_blob_columns*は FILESTREAM が有効な場合に true に設定します。 これにより、FILESTREAM データのレプリケーションを最適な形で実行し、メモリ使用率を低減することができます。 Blob ストリームを使用しないように FILESTREAM のテーブル アーティクルには、次のように使用します。 **sp_changemergearticle**を設定する*stream_blob_columns*を false に設定します。  
  
> [!IMPORTANT]  
>  このメモリ最適化を有効にすると、同期を行うときにマージ エージェントのパフォーマンスが低下する場合があります。 このオプションは、数メガバイトに及ぶデータが含まれる列をレプリケートする場合にのみ使用してください。  
  
> [!NOTE]  
>  論理レコードなど、特定のマージ レプリケーション機能を使用してもバイナリ ラージ オブジェクトをレプリケートするときに使用されているストリームの最適化が妨げられる可能性*stream_blob_columns* 'éý' **true**.  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addmergearticle**はマージ レプリケーションで使用します。  
  
 オブジェクトを発行するときに、その定義がサブスクライバーにコピーされます。 他の 1 つ以上のオブジェクトに依存しているデータベース オブジェクトをパブリッシュする場合は、参照されるオブジェクトをすべてパブリッシュする必要があります。 たとえば、テーブルに依存しているビューをパブリッシュする場合は、そのテーブルもパブリッシュする必要があります。  
  
 値を指定する場合**3**の*partition_options*を単一のサブスクリプションのみパーティションごとに該当するアーティクル内のデータがあります。 第 2 のサブスクリプションを作成し、その新しいサブスクリプションのフィルター選択条件が既存のサブスクリプションと同じパーティションとして判別される場合、既存のサブスクリプションは削除されます。  
  
 3 の値を指定するときに*partition_options*メタデータがクリーンアップたびに、マージ エージェントを実行し、パーティションのスナップショットに有効期限が短くします。 このオプションを使用するときは、サブスクライバーが要求したパーティション スナップショットを有効にすることを検討してください。 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。  
  
 静的行フィルターを追加する場合、アーティクルを使用して、 *subset_filterclause*を既存のパブリケーションがパラメーター化されたフィルターの記事は、サブスクリプションを再初期化が必要です。  
  
 指定するときに*processing_order*、ことをお勧めアーティクルの順序の値の間にすきまを残したりをしやすく、将来新しい値を設定します。 たとえば、Article1、Article2、Article3 の 3 つのアーティクルがあれば、設定*processing_order* 10、20、および 30 ではなく、1、2、および 3 にします。 詳細については、「[Specify the Processing Order of Merge Articles](../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)」 (マージ アーティクルの処理順序の指定) を参照してください。  
  
## <a name="default-schema-option-table"></a>既定のスキーマ オプションの一覧  
 次の表の NULL 値が指定されている場合、ストアド プロシージャによって設定されている既定値*schema_option*アーティクルの種類によって異なります。  
  
|アーティクルの種類|スキーマ オプションの値|  
|------------------|-------------------------|  
|**func スキーマのみ**|**0x01**|  
|**インデックス付きビュー スキーマのみ**|**0x01**|  
|**proc スキーマのみ**|**0x01**|  
|**テーブル**|**0x0C034FD1**  -  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]ネイティブ モードのスナップショット以降のバージョン互換性のあるパブリケーションです。<br /><br /> **0x08034FF1**  -  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]キャラクター モードのスナップショット以降のバージョン互換性のあるパブリケーションです。|  
|**ビュー スキーマのみ**|**0x01**|  
  
> [!NOTE]  
>  パブリケーションは、以前のバージョンをサポートしている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、既定のスキーマ オプション**テーブル**は**0x30034FF1**です。  
  
## <a name="valid-schema-option-table"></a>有効なスキーマ オプションの一覧  
 次の表に、有効な値*schema_option*アーティクルの種類によって異なります。  
  
|アーティクルの種類|スキーマ オプション値|  
|------------------|--------------------------|  
|**func スキーマのみ**|**0x01**と**0x2000**|  
|**インデックス付きビュー スキーマのみ**|**0x01**、 **0x040**、 **0x0100**、 **0x2000**、 **0x40000**、 **0x1000000**、および**0x200000**|  
|**proc スキーマのみ**|**0x01**と**0x2000**|  
|**テーブル**|すべてのオプション|  
|**ビュー スキーマのみ**|**0x01**、 **0x040**、 **0x0100**、 **0x2000**、 **0x40000**、 **0x1000000**、および**0x200000**|  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddMergeArticle](../../relational-databases/replication/codesnippet/tsql/sp-addmergearticle-trans_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 **sysadmin** 固定サーバー ロールまたは **db_owner** 固定データベース ロールのメンバーシップが必要です。  
  
## <a name="see-also"></a>参照  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [データとデータベース オブジェクトのパブリッシュ](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Id 列をレプリケートします。](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [sp_changemergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_dropmergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [sp_helpmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
