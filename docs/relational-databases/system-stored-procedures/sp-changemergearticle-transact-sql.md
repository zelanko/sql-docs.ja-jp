---
title: sp_changemergearticle (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 11/09/2015
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_changemergearticle_TSQL
- sp_changemergearticle
helpviewer_keywords:
- sp_changemergearticle
ms.assetid: 0dc3da5c-4af6-45be-b5f0-074da182def2
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3b9a298cb35b21559e6f89c42c61ca606674b504
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47752270"
---
# <a name="spchangemergearticle-transact-sql"></a>sp_changemergearticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ アーティクルのプロパティを変更します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_changemergearticle [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @property = ] 'property' ]  
    [ , [ @value = ] 'value' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 アーティクルが存在するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article=**] **'***記事***'**  
 変更するアーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません。  
  
 [  **@property=**] **'***プロパティ***'**  
 指定したアーティクルとパブリケーションの変更対象となるプロパティを指定します。 *プロパティ*は**nvarchar (30)**、指定できると、値の 1 つの表にします。  
  
 [  **@value=**] **'***値***'**  
 指定したプロパティの新しい値です。 *値*は**nvarchar (1000)**、指定できると、値の 1 つの表にします。  
  
 次の表に、アーティクルのプロパティと、それぞれの値を示します。  
  
|プロパティ|値|説明|  
|--------------|------------|-----------------|  
|**allow_interactive_resolver**|**true**|アーティクルに対してインタラクティブ競合回避モジュールの使用を有効にします。|  
||**false**|アーティクルに対してインタラクティブ競合回避モジュールの使用を無効にします。|  
|**article_resolver**||アーティクルのカスタム競合回避モジュールです。 テーブル アーティクルにのみ適用されます。|  
|**check_permissions** (ビットマップ)|**0x00**|テーブルレベルの権限は確認されません。|  
||**0x10**|サブスクライバーで実行された INSERT ステートメントをパブリッシャーで適用する前に、テーブルレベルの権限がパブリッシャーで確認されます。|  
||**0x20**|サブスクライバーで実行された UPDATE ステートメントをパブリッシャーで適用する前に、テーブルレベルの権限がパブリッシャーで確認されます。|  
||**0x40**|サブスクライバーで実行された DELETE ステートメントをパブリッシャーで適用する前に、テーブルレベルの権限がパブリッシャーで確認されます。|  
|**column_tracking**|**true**|列レベルの追跡を有効にします。 テーブル アーティクルにのみ適用されます。<br /><br /> 注: 複数の 246 列を含むテーブルをパブリッシュときは、列レベルの追跡を使用できません。|  
||**false**|列レベルの追跡を無効にし、競合検出を行レベルのままにします。 テーブル アーティクルにのみ適用されます。|  
|**compensate_for_errors**|**true**|同期中にエラーが発生したときに、補正操作が実行されます。 詳細については、次を参照してください。 [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。|  
||**false**|補正操作は実行されません。これは既定の動作です。 詳細については、次を参照してください。 [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)します。<br /><br /> **\*\* 重要な\* \*** エラーに対処するとすぐに収束に、影響を受けた行のデータが表示されますが変更を適用して、データが収束します。 アーティクルのソース テーブルが別のパブリケーションの値で既にパブリッシュされている場合*compensate_for_errors*の両方のアーティクルで同じである必要があります。|  
|**creation_script**||サブスクリプション データベースにアーティクルを作成する場合に使用される、オプションのアーティクル スキーマ スクリプトのパスと名前です。|  
|**delete_tracking**|**true**|DELETE ステートメントがレプリケートされます。これは既定の動作です。|  
||**false**|DELETE ステートメントはレプリケートされません。<br /><br /> **\*\* 重要な\* \*** 設定**delete_tracking**に**false**収束、および削除された行の結果を手動で削除する必要があります。|  
|**description**||アーティクルを説明するエントリです。|  
|**destination_owner**||ない場合、サブスクリプション データベース内のオブジェクトの所有者の名前**dbo**します。|  
|**identity_range**||**bigint**場合、アーティクルは、新しい id 値を割り当てるときに使用する範囲のサイズを指定する**identityrangemanagementoption**設定**自動**または**auto_identity_範囲**設定**true**します。 テーブル アーティクルのみに適用されます。 詳細については、の「マージ レプリケーション」セクションを参照してください。 [Id 列のレプリケート](../../relational-databases/replication/publish/replicate-identity-columns.md)します。|  
|**identityrangemanagementoption**|**手動**|自動での ID 範囲の管理を無効にします。 NOT FOR REPLICATION を使用して ID 列にマークを付け、手動による ID 範囲処理を有効にします。 詳細については、「[Replicate Identity Columns](../../relational-databases/replication/publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。|  
||**[なし]**|すべての ID 範囲の管理を無効にします。|  
|**logical_record_level_conflict_detection**|**true**|論理レコードの任意の場所で変更が行われた場合に、競合を検出します。 必要があります**logical_record_level_conflict_resolution**に設定する**true**します。|  
||**false**|既定の競合検出を使用して指定した**column_tracking**します。|  
|**logical_record_level_conflict_resolution**|**true**|優先される論理レコード全体で、優先されなかった論理レコードを上書きします。|  
||**false**|優先される行は、論理レコードに制約されません。|  
|**partition_options**|**0**|アーティクルのフィルター選択は、静的であるか、または各パーティションのデータの一意のサブセットを作成しません。つまり "重複する" パーティションになります。|  
||**1**|パーティションは重複しています。サブスクライバーで実行された DML 更新では、行が属するパーティションを変更できません。|  
||**2**|アーティクルのフィルター選択により、重複しないパーティションが作成されますが、複数のサブスクライバーは同じパーティションを受け取ることができます。|  
||**3**|アーティクルのフィルター選択により、各サブスクリプションに対して、一意で重複しないパーティションが作成されます。<br /><br /> 注: の値を指定する場合**3**の**partition_options**を単一のサブスクリプションのみパーティションごとにそのアーティクル内のデータがあります。 第 2 のサブスクリプションを作成し、その新しいサブスクリプションのフィルター選択条件が既存のサブスクリプションと同じパーティションとして判別される場合、既存のサブスクリプションは削除されます。|  
|**pre_creation_command**|**[なし]**|サブスクライバーに既にテーブルがある場合、操作は何も行われません。|  
||**delete**|サブセット フィルター内の WHERE 句に基づいて削除します。|  
||**drop**|テーブルを再作成する前に削除します。|  
||**truncate**|レプリケーション先テーブルを切り捨てます。|  
|**processing_order**||**int**マージ パブリケーションでアーティクルの処理順序を示します。|  
|**identity_range**||**bigint**場合、アーティクルは、サーバー サブスクリプションを使用してサブスクライバーに割り当てる範囲のサイズを指定する**identityrangemanagementoption**設定**自動**または**ツールidentity_range**設定**true**します。 この ID 範囲は、再パブリッシュ元のサブスクライバーが自らのサブスクライバーに割り当てるために予約されています。 テーブル アーティクルのみに適用されます。 詳細については、の「マージ レプリケーション」セクションを参照してください。 [Id 列のレプリケート](../../relational-databases/replication/publish/replicate-identity-columns.md)します。|  
|**published_in_tran_pub**|**true**|アーティクルはトランザクション パブリケーションでもパブリッシュされます。|  
||**false**|アーティクルはトランザクション パブリケーションではパブリッシュされません。|  
|**resolver_info**||カスタム競合回避モジュールが必要とする追加の情報の指定に使用します。 いくつかの[!INCLUDE[msCoName](../../includes/msconame-md.md)]競合回避モジュールが、競合回避モジュールへの入力として提供されている列が必要です。 **resolver_info**は**nvarchar (255)**、既定値は NULL です。 詳細については、「 [Microsoft COM ベースの競合回避モジュール](../../relational-databases/replication/merge/advanced-merge-replication-conflict-com-based-resolvers.md)」を参照してください。|  
|**schema_option** (ビットマップ)||詳細については、このトピックの後半の「解説」を参照してください。|  
||**0x00**|スナップショット エージェントによるスクリプト作成を無効にし、提供するスクリプトを使用して**creation_script**します。|  
||**0x01**|オブジェクト作成スクリプト (CREATE TABLE、CREATE PROCEDURE など) を生成します。|  
||**0x10**|対応するクラスター化インデックスを生成します。|  
||**0x20**|サブスクライバーでユーザー定義データ型を基本データ型に変換します。 ユーザー定義型 (UDT) 列に CHECK 制約または DEFAULT 制約があるときに、UDT 列が主キーの一部になっている場合、または計算列で UDT 列が参照されている場合、このオプションは使用できません。|  
||**0x40**|対応する非クラスター化インデックスを生成します。|  
||**0x80**|宣言された参照整合性を主キーに含めます。|  
||**0x100**|定義されている場合、テーブル アーティクル上のユーザー トリガーをレプリケートします。|  
||**0x200**|FOREIGN KEY 制約をレプリケートします。 参照するテーブルがパブリケーションの一部でない場合は、パブリッシュされたテーブルのすべての FOREIGN KEY 制約がレプリケートされるわけではありません。|  
||**0x400**|CHECK 制約をレプリケートします。|  
||**0x800**|既定値をレプリケートします。|  
||**0x1000**|列レベルの照合順序をレプリケートします。|  
||**0x2000**|パブリッシュされたアーティクルのソース オブジェクトに関連付けられた拡張プロパティをレプリケートします。|  
||**0x4000**|テーブル アーティクル上で定義されていれば、一意キーをレプリケートします。|  
||**0x8000**|制約のスクリプトを作成しているときに ALTER TABLE ステートメントを生成します。|  
||**0x10000**|CHECK 制約を NOT FOR REPLICATION としてレプリケートして、この制約が同期中に適用されないようにします。|  
||**0x20000**|FOREIGN KEY 制約を NOT FOR REPLICATION としてレプリケートして、この制約が同期中に適用されないようにします。|  
||**0x40000**|パーティション テーブルまたはインデックスに関連付けられているファイル グループをレプリケートします。|  
||**これに対して、0x80000**|パーティション テーブルのパーティション構成をレプリケートします。|  
||**0x100000**|パーティション インデックスのパーティション構成をレプリケートします。|  
||**0x200000**|テーブルの統計をレプリケートします。|  
||**0x400000**|既定のバインドをレプリケートします。|  
||**0x800000**|ルールのバインドをレプリケートします|  
||**0x1000000**|フルテキスト インデックスをレプリケートします。|  
||**0x2000000**|バインドされた XML スキーマ コレクション**xml**列はレプリケートされません。|  
||**0x4000000**|インデックスをレプリケート**xml**列。|  
||**0x8000000**|サブスクライバーにまだ存在しないスキーマを作成します。|  
||**0x10000000**|変換します**xml**列**ntext**サブスクライバーにします。|  
||**0x20000000**|変換の大きなオブジェクトのデータ型 (**nvarchar (max)**、 **varchar (max)**、および**varbinary (max)**) で導入された[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]はサポートされているデータ型に[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]します。|  
||**0x40000000**|アクセス許可をレプリケートします。|  
||**0x80000000**|パブリケーションの一部ではない任意のオブジェクトに対する依存関係を削除しようとしてください。|  
||**0x100000000**|このオプションを使用して、指定されている場合は、FILESTREAM 属性をレプリケートする**varbinary (max)** 列。 テーブルをレプリケートする場合は、このオプションを指定しない[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]サブスクライバー。 FILESTREAM 列を持つテーブルをレプリケート[!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]サブスクライバーがサポートされていません、このスキーマ オプションを設定する方法に関係なく、します。 関連するオプションを参照してください。 **0x800000000**します。|  
||**0x200000000**|日付と時刻のデータ型に変換 (**日付**、**時間**、 **datetimeoffset**、および**datetime2**) で導かれ[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]以前のバージョンでサポートされているデータ型に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。|  
||**0x400000000**|データとインデックスの圧縮オプションをレプリケートします。 詳細については、「 [Data Compression](../../relational-databases/data-compression/data-compression.md)」を参照してください。|  
||**0x800000000**|このオプションを設定すると、サブスクライバーの独自のファイル グループに FILESTREAM データを格納できます。 このオプションが設定されていない場合、FILESTREAM データは既定のファイル グループに格納されます。 レプリケーションではファイル グループは作成されないので、このオプションを設定する場合は、サブスクライバーでスナップショットを適用する前にファイル グループを作成しておく必要があります。 スナップショットを適用する前に、オブジェクトを作成する方法の詳細については、次を参照してください。[前にスクリプトを実行し、後のスナップショットが適用される](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)します。<br /><br /> 関連するオプションを参照してください。 **0x100000000**します。|  
||**0x1000000000**|共通言語ランタイム (CLR) ユーザー定義型 (Udt) に変換します**varbinary (max)** を実行しているサブスクライバーに UDT 型の列をレプリケートできるように[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]します。|  
||**0x2000000000**|変換、 **hierarchyid**のデータ型**varbinary (max)** ように型の列**hierarchyid**実行しているサブスクライバーにレプリケートできる[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]。 使用する方法の詳細についての**hierarchyid**レプリケートされたテーブル内の列を参照してください[hierarchyid &#40;TRANSACT-SQL&#41;](../../t-sql/data-types/hierarchyid-data-type-method-reference.md)します。|  
||**0x4000000000**|テーブルのフィルター選択されたインデックスをレプリケートします。 フィルター選択されたインデックスの詳細については、次を参照してください。 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)します。|  
||**0x8000000000**|変換、 **geography**と**geometry**データ型を**varbinary (max)** を実行しているサブスクライバーにこれらの型の列をレプリケートできるように[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].|  
||**0x10000000000**|型の列にインデックスをレプリケート**geography**と**geometry**します。|  
||NULL|システムによってアーティクルの有効なスキーマ オプションが自動生成されます。|  
|**status**|**アクティブ**|テーブルをパブリッシュするための初期処理スクリプトが実行されます。|  
||**unsynced**|スナップショット エージェントが次回実行されるときに、テーブルをパブリッシュする初期処理スクリプトが実行されます。|  
|**stream_blob_columns**|**true**|バイナリ ラージ オブジェクトの列をレプリケートするときに、データ ストリームの最適化が使用されます。 ただし、論理レコードなど、特定のマージ レプリケーション機能によって、ストリームの最適化の使用が妨げられる可能性があります。 *stream_blob_columns* FILESTREAM が有効な場合は true に設定されます。 これにより、FILESTREAM データのレプリケーションを最適な形で実行し、メモリ使用率を低減することができます。 Blob ストリームを使用しないように FILESTREAM のテーブル アーティクルを強制的には、次のように設定します。 *stream_blob_columns*を false にします。<br /><br /> **\*\* 重要な\* \*** 同期中に、マージ エージェントのパフォーマンスが低下する可能性がありますこのメモリ最適化を有効にします。 このオプションは、数メガバイトに及ぶデータが含まれる列をレプリケートする場合にのみ使用してください。|  
||**false**|バイナリ ラージ オブジェクトの列をレプリケートするときに、最適化が使用されません。|  
|**subscriber_upload_options**|**0**|クライアント サブスクリプションを使用したサブスクライバーでの更新は、制限を受けません。変更はパブリッシャーにアップロードされます。 このプロパティを変更するには、既存のサブスクライバーの再初期化が必要になる場合があります。|  
||**1**|クライアント サブスクリプションを使用したサブスクライバーでの変更は許可されますが、変更はパブリッシャーにアップロードされません。|  
||**2**|クライアント サブスクリプションを使用したサブスクライバーでの変更は許可されません。|  
|**subset_filterclause**||行方向のフィルター選択を指定する WHERE 句です。 テーブル アーティクルにのみ適用されます。<br /><br /> **\*\* 重要な\* \*** パフォーマンス上の理由をお勧めする関数を適用しないパラメーター化された行フィルター句内の列名など`LEFT([MyColumn]) = SUSER_SNAME()`します。 使用する場合[HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)フィルター句と HOST_NAME 値を使用してデータ型を変換する必要があります[変換](../../t-sql/functions/cast-and-convert-transact-sql.md)します。 この場合のベスト プラクティスの詳細については、の「HOST_NAME() 値のオーバーライド」セクションを参照してください[Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)します。|  
|**threshold**||実行しているサブスクライバーに使用されるパーセンテージ値[!INCLUDE[ssEW](../../includes/ssew-md.md)]または以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 **しきい値**マージ エージェントが新しい id 範囲を割り当てるときを制御します。 threshold で指定されているパーセンテージ値が使用される場合、マージ エージェントは新しい ID 範囲を作成します。 ときに使用される**identityrangemanagementoption**に設定されている**自動**または**auto_identity_range**に設定されている**true**します。 テーブル アーティクルのみに適用されます。 詳細については、の「マージ レプリケーション」セクションを参照してください。 [Id 列のレプリケート](../../relational-databases/replication/publish/replicate-identity-columns.md)します。|  
|**verify_resolver_signature**|**1**|カスタム競合回避モジュールのデジタル署名について、信頼されるソースからの署名であるかを判断するための検証を行います。|  
||**0**|カスタム競合回避モジュールのデジタル署名について、信頼されるソースからの署名であるかを判断するための検証を行いません。|  
|NULL (既定値)||サポートされている値の一覧を返します*プロパティ*します。|  
  
 [  **@force_invalidate_snapshot =** ]*更によって*  
 このストアド プロシージャが実行する操作によって既存のスナップショットが無効になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**スナップショットが無効であることをマージ アーティクルへの変更が発生しないことを指定します。 ストアド プロシージャで、変更に新しいスナップショットが必要であることが検出されると、エラーが発生し、変更は加えられません。  
  
 **1**手段に、マージ アーティクルへの変更には、スナップショットを無効になる可能性がありますを新しいスナップショットを必要とする既存のサブスクリプションがある場合は、不使用とマークするのには、既存のスナップショットを新しいスナップショットを生成のアクセス許可を付与します。  
  
 変更によって新しいスナップショットの生成が必要になるプロパティについては、「解説」を参照してください。  
  
 [  **@force_reinit_subscription =** ]*更によって*  
 このストアド プロシージャが実行する操作によって、既存のサブスクリプションの再初期化が必要になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**マージ アーティクルへの変更では、サブスクリプションを再初期化するのには発生しないことを指定します。 変更に既存のサブスクリプションの再初期化が必要であることをストアド プロシージャが検出すると、エラーが発生し、変更は加えられません。  
  
 **1**マージ アーティクルへの変更が発生する既存のサブスクリプションを再初期化するサブスクリプションの再初期化を許可します。  
  
 変更によって既存のサブスクリプションの再初期化が必要になるプロパティについては、「解説」を参照してください。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_changemergearticle**はマージ レプリケーションで使用します。  
  
 **Sp_changemergearticle**を使用して最初に指定されたアーティクルのプロパティを変更するために使用[sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)を参照してください[sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)これらのプロパティの詳細についてはします。  
  
 次のプロパティを変更するには、新しいスナップショットを生成することが必要ですし、値を指定する必要があります**1**の*更によって*パラメーター。  
  
-   **check_permissions**  
  
-   **column_tracking**  
  
-   **destination_owner**  
  
-   **pre_creation_command**  
  
-   **schema_options**  
  
-   **subset_filterclause**  
  
 次のプロパティを変更する場合は、既存する必要があります、サブスクリプションを再初期化の値を指定する必要があります**1**の*更によって*パラメーター。  
  
-   **check_permissions**  
  
-   **column_tracking**  
  
-   **destination_owner**  
  
-   **pre_creation_command**  
  
-   **identityrangemanagementoption**  
  
-   **subscriber_upload_options**  
  
-   **subset_filterclause**  
  
-   **creation_script**  
  
-   **schema_option**  
  
-   **logical_record_level_conflict_detection**  
  
-   **logical_record_level_conflict_resolution**  
  
 3 の値を指定するときに**partition_options**メタデータのクリーンアップ、マージ エージェントを実行し、パーティション スナップショット有効期限が短くされるたびにします。 このオプションを使用するときは、サブスクライバーが要求したパーティション スナップショットを有効にすることを検討してください。 詳しくは、「 [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)」をご覧ください。  
  
 設定するときに、 **column_tracking**プロパティ、テーブルが他のマージ パブリケーションで既にパブリッシュされている場合、列を追跡する必要がありますこのテーブルに基づく既存のアーティクルで使用されている値と同じです。 このパラメーターは、テーブル アーティクルのみに固有のものです。  
  
 複数のパブリケーションでは、同じ基になるテーブルに基づくアーティクルをパブリッシュ、変更、 **delete_tracking**プロパティまたは**compensate_for_errors**プロパティを 1 つのアーティクルと同じ変更を同じテーブルに基づくその他のアーティクルをに対してください。  
  
 マージ処理が使用するパブリッシャーのログインまたはユーザー アカウントが正しいテーブル権限を持っていない場合、無効な変更は競合としてログに記録されます。  
  
 値を変更するときに**schema_option**システムでは、ビットごとの更新は実行されません。 つまり、設定すると、 **schema_option**を使用して**sp_changemergearticle**既存ビット設定がオフにすることがあります。 実行する必要があります、既存の設定を保持する[& (ビット演算子 AND)](../../t-sql/language-elements/bitwise-and-transact-sql.md)値は、設定して、現在の値の間で*schema_option*を実行することによって、によって判断できます[sp_helpmergearticle](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)します。  
  
> [!CAUTION]  
>  して多く (おそらく何百も) を実行して、パブリケーション内のアーティクルの**sp_changemergearticle**記事の 1 つは、完了までに長い時間をかかる場合があります。  
  
## <a name="valid-schema-option-table"></a>有効なスキーマ オプションの一覧  
 次の表に、許可されている説明*schema_option*アーティクルの種類によっての値。  
  
|アーティクルの種類|スキーマ オプションの値|  
|------------------|--------------------------|  
|**func スキーマのみ**|**0x01**と**0x2000**|  
|**インデックス付きビュー スキーマのみ**|**0x01**、 **0x040**、 **0x0100**、 **0x2000**、 **0x40000**、 **0x1000000**、および**0x200000**|  
|**proc スキーマのみ**|**0x01**と**0x2000**|  
|**テーブル**|すべてのオプション|  
|**ビュー スキーマのみ**|**0x01**、 **0x040**、 **0x0100**、 **0x2000**、 **0x40000**、 **0x1000000**、および**0x200000**|  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_changemergearticle](../../relational-databases/replication/codesnippet/tsql/sp-changemergearticle-tr_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_changemergearticle**します。  
  
## <a name="see-also"></a>参照  
 [表示およびアーティクルのプロパティの変更](../../relational-databases/replication/publish/view-and-modify-article-properties.md)   
 [パブリケーションとアーティクルのプロパティの変更](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [sp_addmergearticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_dropmergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [sp_helpmergearticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
