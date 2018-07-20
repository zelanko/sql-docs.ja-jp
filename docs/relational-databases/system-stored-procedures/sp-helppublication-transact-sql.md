---
title: sp_helppublication (TRANSACT-SQL) |Microsoft Docs
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
- sp_helppublication_TSQL
- sp_helppublication
helpviewer_keywords:
- sp_helppublication
ms.assetid: e801c3f0-dcbd-4b4a-b254-949a05f63518
caps.latest.revision: 49
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: bbe9414a2cb1f2a9972143240ce4b474e1fa355e
ms.sourcegitcommit: 67d5f2a654b36da7fcc7c39d38b8bcf45791acc3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/14/2018
ms.locfileid: "39038089"
---
# <a name="sphelppublication-transact-sql"></a>sp_helppublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションに関する情報を返します。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリケーションでは、パブリッシャー、パブリケーション データベースに対してこのストアド プロシージャを実行します。 Oracle パブリケーションの場合、このストアド プロシージャは、任意のデータベース上のディストリビューター側で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helppublication [ [ @publication = ] 'publication' ]  
    [ , [ @found=] found OUTPUT]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication =** ] **'***publication***'**  
 表示するパブリケーションの名前を指定します。 *パブリケーション*が sysname で、既定値は**%**、すべてのパブリケーションに関する情報が返されます。  
  
 [  **@found =** ] **'***見つかった***'** 出力  
 行を返すことを示すフラグです。 *見つかった*は**int**は出力パラメーターで、既定値は**23456**します。 **1**パブリケーションが見つかったことを示します。 **0**パブリケーションが見つからないことを示します。  
  
 [ **@publisher** =] **'***パブリッシャー***'**  
 以外を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*が sysname で、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*からパブリケーション情報を要求するときに指定しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|pubid|**int**|パブリケーションの ID。|  
|NAME|**sysname**|パブリケーションの名前。|  
|restricted|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|status|**tinyint**|パブリケーションの現在の状態。<br /><br /> **0** = 非アクティブです。<br /><br /> **1** = アクティブ。|  
|タスク (task)||旧バージョンとの互換性のために用意されています。|  
|replication frequency|**tinyint**|レプリケーション周期の種類。<br /><br /> **0** = トランザクション<br /><br /> **1** = スナップショット|  
|synchronization method|**tinyint**|同期化モード。<br /><br /> **0** = ネイティブな一括コピー プログラム (**bcp**ユーティリティ)<br /><br /> **1** = キャラクター一括コピー<br /><br /> **3** = 同時実行ネイティブな一括コピー (**bcp**ユーティリティ) が使用されるテーブルは、スナップショット時にロックされませんが、<br /><br /> **4** = Concurrent_c 文字一括コピーが使用されますが、テーブルは、スナップショット時にロックされません|  
|description|**nvarchar (255)**|パブリケーションの説明 (省略可能)。|  
|immediate_sync|**bit**|スナップショット エージェントを実行するたびに、同期ファイルを作成または再作成するかどうかを示します。|  
|enabled_for_internet|**bit**|ファイル転送プロトコル (FTP) やその他のサービスによって、パブリケーション用の同期ファイルをインターネット上で公開するかどうかを示します。|  
|allow_push|**bit**|パブリケーションに対してプッシュ サブスクリプションを許可するかどうかを示します。|  
|allow_pull|**bit**|パブリケーションに対してプル サブスクリプションを許可するかどうかを示します。|  
|allow_anonymous|**bit**|パブリケーションに対して非同期サブスクリプションを許可するかどうかを示します。|  
|independent_agent|**bit**|パブリケーション用のスタンドアロン ディストリビューション エージェントがあるかどうかを示します。|  
|immediate_sync_ready|**bit**|スナップショット エージェントが、新しいサブスクリプションでそのまま使用できるスナップショットを作成するかどうかを示します。 新しいサブスクリプションまたは再初期化されたサブスクリプションに対して常にスナップショットが提供されるようパブリケーションが設定されている場合のみ、このパラメーターを定義します。|  
|allow_sync_tran|**bit**|かどうか、パブリケーションのパブリケーションで即時更新サブスクリプションが許可されています。|  
|autogen_sync_procs|**bit**|サブスクリプションの即時更新をサポートするストアド プロシージャを自動的に生成するかどうかを示します。|  
|snapshot_jobid|**binary(16)**|スケジュールされているタスクの ID。|  
|retention|**int**|指定されたパブリケーションに関する変更を保存する期間 (時間単位)。|  
|has subscription|**bit**|パブリケーションにアクティブなサブスクリプションがあるかどうかを示します。 **1**パブリケーションはアクティブなサブスクリプション、および**0**パブリケーションにサブスクリプションがないことを意味します。|  
|allow_queued_tran|**bit**|変更をパブリッシャーで適用できるようになるまで、サブスクライバーで変更をキューイングする機能を無効にするかどうかを示します。 場合**0**、サブスクライバーの変更はキュー登録されません。|  
|snapshot_in_defaultfolder|**bit**|既定のフォルダーに、スナップショット ファイルが格納されているかどうかを指定します。 場合**0**、スナップショット ファイルがで指定された代替位置に格納されている*alternate_snapshot_folder*します。 場合**1**、スナップショット ファイルは既定のフォルダーにあります。|  
|alt_snapshot_folder|**nvarchar (255)**|スナップショットの代替フォルダーの場所を指定します。|  
|pre_snapshot_script|**nvarchar (255)**|ポインターを指定します、 **.sql**ファイルの場所。 ディストリビューション エージェントでは、サブスクライバーでスナップショットが適用されるとき、レプリケートされたオブジェクト スクリプトよりも前に、プリスナップショット スクリプトが実行されます。|  
|post_snapshot_script|**nvarchar (255)**|ポインターを指定します、 **.sql**ファイルの場所。 最初の同期時、ディストリビューション エージェントでは、他のすべてのレプリケートされたオブジェクト スクリプトとデータが適用された後、ポスト スナップショット スクリプトが実行されます。|  
|compress_snapshot|**bit**|指定に書き込まれたスナップショット、 *alt_snapshot_folder*の場所を圧縮するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB 形式です。 **0**スナップショットを圧縮しないことを指定します。|  
|ftp_address|**sysname**|ディストリビューター用 FTP サービスのネットワーク アドレス。 ここでは、サブスクライバーのディストリビューション エージェントまたはマージ エージェントがパブリケーション スナップショット ファイルを取得する場所を指定します。|  
|ftp_port|**int**|ディストリビューター用 FTP サービスのポート番号。|  
|ftp_subdirectory|**nvarchar (255)**|パブリケーションで FTP を利用したスナップショット配布がサポートされている場合に、サブスクライバーのディストリビューション エージェントまたはマージ エージェントがパブリケーション スナップショット ファイルを取得する場所。|  
|ftp_login|**sysname**|FTP サービスへの接続に使用されるユーザー名。|  
|allow_dts|**bit**|パブリケーションでデータを変換できるかどうかを指定します。 **0** DTS 変換が許可されないことを指定します。|  
|allow_subscription_copy|**bit**|パブリケーションにサブスクライブするサブスクリプション データベースをコピーする機能が有効かどうかを示します。 **0**コピーが許可されないことを意味します。|  
|centralized_conflicts|**bit**|競合レコードがパブリッシャーに格納されるかどうかを示します。<br /><br /> **0** = 競合レコードはパブリッシャー側の両方と、競合の原因となったサブスクライバーで格納されます。<br /><br /> **1** = 競合レコードはパブリッシャーに格納されます。|  
|conflict_retention|**int**|競合の保有期間の日数を指定します。|  
|conflict_policy|**int**|キュー更新サブスクライバー オプションを使用するときの競合の解決方法。 これらの値のいずれかを指定できます。<br /><br /> **1** = パブリッシャー優先します。<br /><br /> **2** = サブスクライバー優先します。<br /><br /> **3** = サブスクリプションを再初期化します。|  
|queue_type||使用されるキューの種類。 これらの値のいずれかを指定できます。<br /><br /> **msmq** = 使用[!INCLUDE[msCoName](../../includes/msconame-md.md)]メッセージ キューがトランザクションを格納します。<br /><br /> **sql** = 使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクションを格納します。<br /><br /> 注: メッセージ キューのサポートは廃止されました。|  
|backward_comp_level||データベースの互換性レベル。次のいずれかの値をとります。<br /><br /> **90** = [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]<br /><br /> **100** = [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]|  
|publish_to_AD|**bit**|パブリケーションが [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory™ にパブリッシュされるかどうかを示します。 値**1**ことは、発行は、値と**0**公開しないことを示します。|  
|allow_initialize_from_backup|**bit**|サブスクライバーでは、最初のスナップショットではなくバックアップから、このパブリケーションへのサブスクリプションを初期化できるかどうかを示します。 **1** 、バックアップからサブスクリプションを初期化できることを意味し、 **0**できないことを意味します。 詳細については、次を参照してください。 [、せず、スナップショット トランザクション サブスクリプションの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)スナップショットを使用しないトランザクション サブスクライバーです。|  
|replicate_ddl|**int**|スキーマ レプリケーションがパブリケーションに対してサポートされているかどうかを示します。 **1** 、パブリッシャーで実行されるデータ定義言語 (DDL) ステートメントがレプリケートされることを示しますと**0** DDL ステートメントがレプリケートされないことを示します。 詳細については、「[パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)」を参照してください。|  
|enabled_for_p2p|**int**|ピア ツー ピア レプリケーション トポロジでパブリケーションを使用できるかどうかを示します。 **1**パブリケーションがピア ツー ピア レプリケーションをサポートしていることを示します。 詳細については、「 [Peer-to-Peer Transactional Replication](../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)」を参照してください。|  
|publish_local_changes_only|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|enabled_for_het_sub|**int**|パブリケーションで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のサブスクライバーがサポートされるかどうかを示します。 値**1**手段を以外[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーがサポートされます。 値**0**手段だけである[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]サブスクライバーがサポートされます。 詳細については、「 [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)」を参照してください。|  
|enabled_for_p2p_conflictdetection|**int**|ピア ツー ピア レプリケーションが有効になっているパブリケーションでの競合をディストリビューション エージェントが検出するかどうかを指定します。 値**1**競合が検出されることを意味します。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」を参照してください。|  
|originator_id|**int**|ピア ツー ピア トポロジ内のノードの ID を指定します。 場合、この ID は競合検出に対して使用**enabled_for_p2p_conflictdetection**に設定されている**1**します。 既に使用されている ID を確認するには、 [Mspeer_originatorid_history](../../relational-databases/system-tables/mspeer-originatorid-history-transact-sql.md) システム テーブルに対してクエリを実行します。|  
|p2p_continue_onconflict|**int**|競合の検出時にディストリビューション エージェントで変更の処理を継続するかどうかを指定します。 値**1**エージェントを継続の変更を処理することを意味します。<br /><br /> **\*\* 注意\* \*** の既定値を使用することをお勧めします。 **0**します。 このオプションを設定すると**1**、ディストリビューション エージェントが、最高の発信元 ID を持つノードから競合する行を適用してトポロジ内のデータを収束しようとしています。 この方法では収束が保証されません。 競合が検出された後に、トポロジに一貫性があることを確認する必要があります。 詳細については、「 [Conflict Detection in Peer-to-Peer Replication](../../relational-databases/replication/transactional/peer-to-peer-conflict-detection-in-peer-to-peer-replication.md)」の「競合の処理」を参照してください。|  
|allow_partition_switch|**int**|パブリッシュされたデータベースに対して ALTER TABLE ... SWITCH ステートメントを実行できるかどうかを指定します。 詳細については、「[パーティション テーブルとパーティション インデックスのレプリケート](../../relational-databases/replication/publish/replicate-partitioned-tables-and-indexes.md)」を参照してください。|  
|replicate_partition_switch|**int**|パブリッシュされたデータベースに対して実行される ALTER TABLE ... SWITCH ステートメントをサブスクライバーにレプリケーションする必要があるかどうかを指定します。 このオプションは有効な場合にのみ*allow_partition_switch*に設定されている**1**します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 sp_helppublication は、スナップショットおよびトランザクション レプリケーションで使用します。  
  
 sp_helppublication では、このプロシージャを実行するユーザーが所有しているすべてのパブリケーションに関する情報が返されます。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_helppublication](../../relational-databases/replication/codesnippet/tsql/sp-helppublication-trans_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 sp_helppublication を実行できるのは、パブリッシャーの sysadmin 固定サーバー ロールのメンバー、パブリケーション データベースの db_owner 固定データベース ロールのメンバー、またはパブリケーション アクセス リスト (PAL) のユーザーだけです。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 以外のパブリッシャーの場合、sp_helppublication を実行できるのは、ディストリビューターの sysadmin 固定サーバー ロールのメンバー、ディストリビューション データベースの db_owner 固定データベース ロールのメンバー、または PAL のユーザーだけです。  
  
## <a name="see-also"></a>参照  
 [パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [sp_addpublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_droppublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
