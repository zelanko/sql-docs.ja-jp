---
title: IHpublications (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- IHpublications_TSQL
- IHpublications
dev_langs:
- TSQL
helpviewer_keywords:
- IHpublications system table
ms.assetid: b519a101-fa53-44be-bd55-6ea79245b5d1
caps.latest.revision: 32
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 5c1f28e6a594a97882bb122f310d77f857414fc7
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ihpublications-transact-sql"></a>IHpublications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **IHpublications**システム テーブルには、SQL Server 以外のパブリケーションが、現在のディストリビューターを使用するごとに 1 つの行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**pubid**|**int**|パブリケーションの一意な ID を示す ID 列。|  
|**name**|**sysname**|パブリケーションに関連付けられた一意な名前。|  
|**repl_freq**|**tinyint**|レプリケーションの頻度。<br /><br /> **0** = トランザクション ベースします。<br /><br /> **1** = テーブルの定期更新します。|  
|**ステータス**|**tinyint**|パブリケーションの状態。次のいずれかになります。<br /><br /> **0** = 非アクティブです。<br /><br /> **1**アクティブを = です。|  
|**sync_method**|**tinyint**|同期方法。<br /><br /> **1** = キャラクター一括コピーします。<br /><br /> **4** = Concurrent_c 文字一括コピーが使用されますが、スナップショット時に、テーブルはロックされていないことを意味します。|  
|**snapshot_jobid**|**[バイナリ]**|スケジュールされたタスク id。|  
|**enabled_for_internet**|**bit**|パブリケーションの同期ファイルが FTP やその他のサービス経由でインターネットに公開されるかどうかを示します、 **1**インターネットからアクセスできることを意味します。|  
|**immediate_sync_ready**|**bit**|同期ファイルを使用できるかどうかをここで示す**1**が利用できることを意味します。 *SQL 以外のパブリッシャーにサポートされていません。*|  
|**allow_queued_tran**|**bit**|変更をパブリッシャーで適用できるようになるまで、サブスクライバーで変更をキューに保持するかどうかを示します。 場合**1**、サブスクライバーの変更はキューに格納します。 *SQL 以外のパブリッシャーにサポートされていません。*|  
|**allow_sync_tran**|**bit**|パブリケーションでサブスクリプションの即時更新を許可するかどうかを示します。 **1**即時更新サブスクリプションが許可されることを意味します。 *SQL 以外のパブリッシャーにサポートされていません。*|  
|**autogen_sync_procs**|**bit**|即時更新サブスクリプションの同期ストアド プロシージャがパブリッシャーで生成されるかどうかを示します。 **1**パブリッシャー側で生成されることを意味します。 *SQL 以外のパブリッシャーにサポートされていません。*|  
|**snapshot_in_defaultfolder**|**bit**|スナップショット ファイルは既定のフォルダーに格納されているかどうかを指定します。 場合**0**、スナップショット ファイルで指定された代替位置に格納されている*alternate_snapshot_folder*です。 場合**1**、スナップショット ファイルは既定のフォルダーにあります。|  
|**alt_snapshot_folder**|**nvarchar(510)**|スナップショットの代替フォルダーの場所を指定します。|  
|**pre_snapshot_script**|**nvarchar(510)**|ポインターを指定します、 **.sql**ファイルの場所。 ディストリビューション エージェントは、サブスクライバー側でスナップショットを適用するとき、レプリケートされたオブジェクト スクリプトより前に、プリスナップショット スクリプトを実行します。|  
|**post_snapshot_script**|**nvarchar(510)**|ポインターを指定します、 **.sql**ファイルの場所。 ディストリビューション エージェントは、最初の同期中、他のすべてのレプリケートされたオブジェクト スクリプトとデータが適用された後に、ポストスナップショット スクリプトを実行します。|  
|**compress_snapshot**|**bit**|指定に書き込まれたスナップショット、 *alt_snapshot_folder*の場所を圧縮するには、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB 形式です。 **0**を指定したスナップショットは圧縮されません。|  
|**ftp_address**|**sysname**|ディストリビューター用 FTP サービスのネットワーク アドレス。 ディストリビューション エージェントが受け取るパブリケーション スナップショット ファイルの場所を示します。|  
|**ftp_port**|**int**|ディストリビューター用 FTP サービスのポート番号。 パブリケーションのスナップショット ファイルが、ディストリビューション エージェントを取得する配置されているを指定します|  
|**ftp_subdirectory**|**nvarchar(510)**|スナップショット ファイルは、パブリケーションが FTP を使用してスナップショットの配布をサポートしている場合に、ディストリビューション エージェントの使用可能な場所を指定します。|  
|**ftp_login**|**nvarchar (256)**|FTP サービスへの接続に使用されるユーザー名。|  
|**ftp_password**|**nvarchar(1048)**|FTP サービスへの接続に使用されるユーザー パスワード。|  
|**allow_dts**|**bit**|パブリケーションでデータを変換できるかどうかを指定します。 **1** DTS 変換が許可されていることを指定します。 *SQL 以外のパブリッシャーにサポートされていません。*|  
|**allow_anonymous**|**bit**|パブリケーションに対して匿名サブスクリプションを許可するかどうかを示す、 **1**が許可されていることを意味します。|  
|**centralized_conflicts**|**bit**|競合レコードがパブリッシャーに格納されるかどうかを示します。<br /><br /> **0** = 競合レコードは、パブリッシャーの両方と、競合の原因となったサブスクライバーで格納します。<br /><br /> **1** = 競合レコードはパブリッシャーに保存します。<br /><br /> *SQL 以外のパブリッシャーにサポートされていません。*|  
|**conflict_retention**|**int**|競合の保有期間の日数を指定します。 *SQL 以外のパブリッシャーにサポートされていません。*|  
|**conflict_policy**|**int**|キュー更新サブスクライバー オプションを使用するときの競合の解決方法。 これらの値のいずれかを指定できます。<br /><br /> **1** = パブリッシャー優先します。<br /><br /> **2** = サブスクライバー優先します。<br /><br /> **3** = サブスクリプションを再初期化します。<br /><br /> *SQL 以外のパブリッシャーにサポートされていません。*|  
|**queue_type**|**int**|使用されるキューの種類。 これらの値のいずれかを指定できます。<br /><br /> **1** = を使用して msmq[!INCLUDE[msCoName](../../includes/msconame-md.md)]メッセージ キューがトランザクションを格納します。<br /><br /> **2** = を使用して sql[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トランザクションを格納します。<br /><br /> 以外でこの列は使用されません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。<br /><br /> 注: を使用して[!INCLUDE[msCoName](../../includes/msconame-md.md)]メッセージ キューは廃止されており、現在サポートされていません。<br /><br /> *この列にはの SQL 以外のパブリッシャーがサポートされていません。*|  
|**ad_guidname**|**sysname**|パブリケーションがパブリッシュされるかどうかを指定します、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory です。 有効なグローバル一意識別子 (GUID) は、パブリケーションがパブリッシュされることを指定します、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory、および GUID は、対応する Active Directory パブリケーション オブジェクト**objectGUID**です。 NULL の場合、パブリケーションで非公開[!INCLUDE[msCoName](../../includes/msconame-md.md)]Active Directory です。 *SQL 以外のパブリッシャーにサポートされていません。*|  
|**backward_comp_level**|**int**|データベースの互換性レベル。次のいずれかの値になります。<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].<br /><br /> *SQL 以外のパブリッシャーにサポートされていません。*|  
|**説明**|**nvarchar (255)**|パブリケーションの説明エントリ。|  
|**independent_agent**|**bit**|このパブリケーションに対して、スタンドアロンのディストリビューション エージェントがあるかどうかを示します。<br /><br /> **0** = パブリケーションでは共有ディストリビューション エージェントを使用して、パブリッシャー データベース/サブスクライバー データベースの各ペアが 1 つの共有エージェントです。<br /><br /> **1** = このパブリケーション用のスタンドアロン ディストリビューション エージェントが存在します。|  
|**immediate_sync**|**bit**|同期ファイルが作成またはスナップショット エージェントを実行するたびに再作成するかどうかを示す、 **1**が作成されるたびにエージェントが実行されることを意味します。|  
|**allow_push**|**bit**|パブリケーションに対してプッシュ サブスクリプションを許可するかどうかを示す、 **1**が許可されていることを意味します。|  
|**allow_pull**|**bit**|パブリケーションに対してプル サブスクリプションを許可するかどうかを示す、 **1**が許可されていることを意味します。|  
|**保有期間**|**int**|指定されたパブリケーションに関する変更を保存する時間。|  
|**allow_subscription_copy**|**bit**|パブリケーションにサブスクライブするサブスクリプション データベースをコピーする機能が有効かどうかを示します。 **1**コピーが許可されていることを意味します。|  
|**allow_initialize_from_backup**|**bit**|サブスクライバーでは、最初のスナップショットではなくバックアップから、このパブリケーションへのサブスクリプションを初期化できるかどうかを示します。 **1**をバックアップからサブスクリプションを初期化できることを意味し、 **0**できないことを意味します。 詳細については、「 [Initialize a Transactional Subscription Without a Snapshot](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)を使用して、サブスクリプションを手動で初期化する方法について説明します。 *SQL 以外のパブリッシャーにサポートされていません。*|  
|**min_autonosync_lsn**|**binary(1)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**replicate_ddl**|**int**|スキーマ レプリケーションがパブリケーションに対してサポートされているかどうかを示します。 **1** 、パブリッシャー側で実行される DDL ステートメントがレプリケートされることを示すと**0** DDL ステートメントがレプリケートされないことを示します。 詳細については、「[パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)」を参照してください。 *SQL 以外のパブリッシャーにサポートされていません。*|  
|**options**|**int**|ビットごとのオプションの値が、追加の発行オプションを指定するビットマップ。<br /><br /> **0x1** - ピア ツー ピア レプリケーションに対して有効です。<br /><br /> **0x2** -ローカル変更のみをパブリッシュします。<br /><br /> **0x4** - SQL Server 以外のサブスクライバーに対して有効です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addpublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [syspublications&#40;システム ビュー&#41; &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/syspublications-system-view-transact-sql.md)   
 [syspublications &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/syspublications-transact-sql.md)  
  
  
