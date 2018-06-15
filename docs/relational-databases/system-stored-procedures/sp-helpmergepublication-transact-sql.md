---
title: sp_helpmergepublication (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- sp_helpmergepublication
- sp_helpmergepublication_TSQL
helpviewer_keywords:
- sp_helpmergepublication
ms.assetid: dfe1e1e1-9a65-406a-aced-6385a078e135
caps.latest.revision: 55
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: c419566cd0e43f27644433c6a6bbe5b597742b5f
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33003610"
---
# <a name="sphelpmergepublication-transact-sql"></a>sp_helpmergepublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ パブリケーションに関する情報を返します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergepublication [ [ @publication = ] 'publication' ]  
    [ , [ @found = ] 'found' OUTPUT ]  
    [ , [ @publication_id = ] 'publication_id' OUTPUT ]  
    [ , [ @reserved = ] 'reserved' ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @publisher_db = ] 'publisher_db' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @publication **=** ] **'***パブリケーション***'**  
 パブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値は**%**、現在のデータベース内のすべてのマージ パブリケーションに関する情報が返されます。  
  
 [ @found **=** ] **'***見つかった***'** 出力  
 行を返すことを示すフラグ。 *見つかった*は**int**と出力パラメーター、既定値は NULL です。 **1**パブリケーションが見つかったことを示します。 **0**パブリケーションが見つからないことを示します。  
  
 [ @publication_id **=**] **'***publication_id***'** 出力  
 パブリケーション識別番号です。 *publication_id*は**uniqueidentifier**と出力パラメーター、既定値は NULL です。  
  
 [ @reserved **=**] **'***予約***'**  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)] *予約済み*は**nvarchar (20)**、既定値は NULL です。  
  
 [ @publisher **=** ] **'***パブリッシャー***'**  
 パブリッシャーの名前。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
 [@publisher_db **=** ] **'***publisher_db***'**  
 パブリケーション データベースの名前です。 *publisher_db*は**sysname**、既定値は NULL です。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|id|**int**|結果セット一覧内のパブリケーションの順序。|  
|name|**sysname**|パブリケーションの名前です。|  
|description|**nvarchar (255)**|パブリケーションの説明です。|  
|ステータス|**tinyint**|パブリケーション データが使用できるようになる時期を示します。|  
|retention|**int**|パブリケーション内のアーティクルの変更に関するメタデータを保存する期間。 この期間の単位は、日、週、月、または年にすることができます。 単位の詳細については、retention_period_unit 列を参照してください。|  
|sync_mode|**tinyint**|パブリケーションの同期モード。<br /><br /> **0** = ネイティブな一括コピー プログラム (**bcp**ユーティリティ)<br /><br /> **1** = キャラクター一括コピー|  
|allow_push|**int**|特定のパブリケーションに対してプッシュ サブスクリプションを作成できるかどうかを示します。 **0**プッシュ サブスクリプションが許可されていないことを意味します。|  
|allow_pull|**int**|特定のパブリケーションに対してプル サブスクリプションを作成できるかどうかを示します。 **0**プル サブスクリプションが許可されていないことを意味します。|  
|allow_anonymous|**int**|特定のパブリケーションに対して匿名サブスクリプションを作成できるかどうかを示します。 **0**匿名サブスクリプションが許可されていないことを意味します。|  
|centralized_conflicts|**int**|競合レコードは指定されたパブリッシャーに保存されているかどうかを決定します。<br /><br /> **0** = 競合レコードは、パブリッシャーの両方と、競合の原因となったサブスクライバーで格納します。<br /><br /> **1** = すべての競合レコードはパブリッシャーに保存します。|  
|priority|**float(8)**|ループバック サブスクリプションの優先度。|  
|snapshot_ready|**tinyint**|このパブリケーションのスナップショットが使用できる状態にあるかどうかを示します。<br /><br /> **0** = スナップショットが使用できる状態です。<br /><br /> **1** = スナップショットが使用できる状態ではありません。|  
|publication_type|**int**|パブリケーションの種類です。<br /><br /> **0**スナップショットを = です。<br /><br /> **1** = トランザクションです。<br /><br /> **2**マージを = です。|  
|pubid|**uniqueidentifier**|このパブリケーションの一意の識別子。|  
|snapshot_jobid|**binary(16)**|スナップショット エージェントのジョブ ID。 スナップショット ジョブのエントリを取得する、 [sysjobs](../../relational-databases/system-tables/dbo-sysjobs-transact-sql.md)システム テーブルでは、この 16 進数の値を変換する必要があります**uniqueidentifier**です。|  
|enabled_for_internet|**int**|パブリケーションがインターネットで使用できるかどうかを示します。 場合**1**、パブリケーションの同期ファイルが入れられます、`C:\Program Files\Microsoft SQL Server\MSSQL\Repldata\Ftp`ディレクトリ。 ユーザーは、ファイル転送プロトコル (FTP) ディレクトリを作成する必要があります。 場合**0**パブリケーションはインターネット アクセスに対応できません。|  
|dynamic_filter|**int**|パラメーター化された行フィルターが使用されるかどうかを示します。 **0**パラメーター化された行フィルターを使用しないことを意味します。|  
|has_subscription|**bit**|パブリケーションにサブスクリプションがあるかどうかを示します。 **0**現在このパブリケーションに対するサブスクリプションがないことを意味します。|  
|snapshot_in_default_folder|**bit**|スナップショット ファイルが既定のフォルダーに格納されるかどうかを示します。<br /><br /> 場合**1**、スナップショット ファイルは既定のフォルダーにあります。<br /><br /> 場合**0**で指定された別の場所にスナップショット ファイルが格納されている**alt_snapshot_folder**です。 代替位置としては、他のサーバー、ネットワーク ドライブ、または CD-ROM やリムーバブル ディスクなどのリムーバブル メディアを指定できます。 またスナップショット ファイルを FTP サイトに保存し、後でサブスクライバーで取得することもできます。<br /><br /> 注: このパラメーターは true。 しての場所をまだ用意、 **alt_snapshot_folder**パラメーター。 このように指定した場合は、既定の位置と代替位置の両方に、スナップショット ファイルが格納されます。|  
|alt_snapshot_folder|**nvarchar (255)**|スナップショットの代替フォルダーの場所を指定します。|  
|pre_snapshot_script|**nvarchar (255)**|ポインターを指定します、 **.sql**サブスクライバーでスナップショットを適用するときに、マージ エージェントを実行する前に、レプリケートされたオブジェクトのいずれかのファイルがスクリプトです。|  
|post_snapshot_script|**nvarchar (255)**|ポインターを指定します、 **.sql**マージ エージェントが実行される結局のところ、他のファイルにレプリケートされたオブジェクト スクリプトとデータは、初期同期中に適用されています。|  
|compress_snapshot|**bit**|指定に書き込まれたスナップショット、 **alt_snapshot_folder**場所を圧縮、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB 形式です。|  
|ftp_address|**sysname**|ディストリビューター用の FTP サービスのネットワーク アドレスです。 マージ エージェントが受け取るパブリケーション スナップショット ファイルの場所を指定します。|  
|ftp_port|**int**|ディストリビューター用の FTP サービスのポート番号です。 **ftp_port**が、既定値は**21**です。 マージ エージェントが検索するパブリケーション スナップショット ファイルの場所を示します。|  
|ftp_subdirectory|**nvarchar (255)**|スナップショットが FTP を使用して配布される場合に、マージ エージェントがスナップショット ファイルを取得する場所。|  
|ftp_login|**sysname**|FTP サービスに接続するときに使用するユーザー名です。|  
|conflict_retention|**int**|競合を保有する保有期間の日数。 指定の日数が経過すると、競合テーブルから競合行が削除されます。|  
|keep_partition_changes|**int**|このパブリケーションの同期の最適化が発生しているかどうかを指定します。 **keep_partition_changes**が、既定値は**0**します。 値**0**にすると同期は最適化されず、すべてのサブスクライバーに送信されるパーティションはパーティションにデータが変更されたときに検証されます。<br /><br /> **1**同期は最適化され、変更されたパーティションの行を持つサブスクライバーだけが影響を受けることを意味します。<br /><br /> 注: 既定では、マージ パブリケーションを使用して事前計算済みパーティションは、このオプションよりも高い安全性の最適化を提供します。 詳細については、次を参照してください。 [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md)と[事前計算済みパーティションを持つパラメーター化されたフィルター パフォーマンスの最適化](../../relational-databases/replication/merge/parameterized-filters-optimize-for-precomputed-partitions.md)です。|  
|allow_subscription_copy|**int**|パブリケーションにサブスクライブするサブスクリプション データベースをコピーする機能が有効かどうかを示します。 値**0**コピーが許可されないことを意味します。|  
|allow_synctoalternate|**int**|代替同期パートナーがこのパブリッシャーと同期できるかどうかを示します。 値**0**同期パートナーを使用できないことを意味します。|  
|validate_subscriber_info|**nvarchar(500)**|サブスクライバー情報を取得し、サブスクライバー上でのパラメーター化された行フィルター条件を検証するときに使用される機能の一覧。 各マージで、情報に一貫性を持たせながらパーティション分割する場合に使用できます。|  
|backward_comp_level|**int**|データベースの互換性レベル。次のいずれかの値をとります。<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> **90**  =  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP1<br /><br /> **90**  =  [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] SP2<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
|publish_to_activedirectory|**bit**|パブリケーション情報を Active Directory にパブリッシュするかどうかを示します。 値**0** Active Directory からパブリケーション情報はないことを意味します。<br /><br /> このパラメーターは、旧バージョンのスクリプトとの互換性を保つために用意されており、非推奨とされます。 現在、Active Directory にはパブリケーション情報を追加できません。|  
|max_concurrent_merge|**int**|同時実行マージ プロセスの数。 場合**0**、特定の時点で実行されている同時実行マージ プロセスの数に制限はありません。|  
|max_concurrent_dynamic_snapshots|**int**|マージ パブリケーションに対して同時に実行できる、フィルター選択されたデータのスナップショット セッションの最大数。 場合**0**、どの時点においても、パブリケーションに対して同時に実行できるフィルター選択されたデータの同時実行スナップショット セッションの最大数に制限はありません。|  
|use_partition_groups|**int**|事前計算済みパーティションが使用されるかどうかを示します。 値**1**事前計算済みパーティションの方法が使用されます。|  
|num_of_articles|**int**|パブリケーション内のアーティクルの数。|  
|replicate_ddl|**int**|パブリッシュされたテーブルに対するスキーマ変更がレプリケートされるかどうかを示します。 値**1**スキーマ変更がレプリケートされることを意味します。|  
|publication_number|**smallint**|パブリケーションに割り当てられる番号。|  
|allow_subscriber_initiated_snapshot|**bit**|サブスクライバーが、フィルター選択されたデータのスナップショット生成プロセスを開始できるかどうかを示します。 値**1**サブスクライバーがスナップショット プロセスを開始できることを意味します。|  
|allow_web_synchronization|**bit**|パブリケーションで Web 同期が有効かどうかを示します。 値**1** Web 同期が有効になっていることを意味します。|  
|web_synchronization_url|**nvarchar(500)**|Web 同期に使用されるインターネット URL。|  
|allow_partition_realignment|**bit**|パブリッシャー上の行の変更によってパーティションが変更される場合、削除がサブスクライバーに送信されるかどうかを示します。 値**1**削除がサブスクライバーに送信されることを意味します。  詳細については、次を参照してください。 [sp_addmergepublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)です。|  
|retention_period_unit|**tinyint**|保有期間を定義するときに使用される単位を指定します。 次の値のいずれかになります。<br /><br /> **0** = 日<br /><br /> **1** = 週<br /><br /> **2** = 月<br /><br /> **3** = 年|  
|has_downloadonly_articles|**bit**|パブリケーションに属するアーティクルが、ダウンロードのみのアーティクルであるかどうかを示します。 値**1**ダウンロード専用アーティクルがあることを示します。|  
|decentralized_conflicts|**int**|競合レコードが、競合の原因となったサブスクライバーで格納されるかどうかを示します。 値**0**競合レコードがサブスクライバーで格納されないことを示します。 値 1 は、競合レコードがサブスクライバーで格納されることを表します。|  
|generation_leveling_threshold|**int**|1 回の生成に含まれる変更の数です。 生成とは、パブリッシャーまたはサブスクライバーに配信される変更の集まりです。|  
|automatic_reinitialization_policy|**bit**|自動再初期化を実行する前に、サブスクライバーから変更をアップロードするかどうかを示します。 値**1**自動再初期化が行われる前に、変更がサブスクライバーからアップロードされたことを示します。 値 0 は、自動再初期化の前に変更がアップロードされないことを表します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 sp_helpmergepublication は、マージ レプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 パブリケーションのパブリケーション アクセス リストのメンバーは、そのパブリケーションに対して sp_helpmergepublication を実行できます。 パブリケーション データベースの db_owner 固定データベース ロールのメンバーは、sp_helpmergepublication を実行してすべてのパブリケーションに関する情報を取得できます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_helpmergepublication](../../relational-databases/replication/codesnippet/tsql/sp-helpmergepublication-_1.sql)]  
  
## <a name="see-also"></a>参照  
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [sp_addmergepublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_changemergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_dropmergepublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
