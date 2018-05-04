---
title: sysmergepublications (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
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
- sysmergepublications
- sysmergepublications_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergepublications system table
ms.assetid: 7f82c6c3-22d1-47c0-a92b-4d64b98cc455
caps.latest.revision: 42
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 0761b6513217999915155bc37e02cdfb20bb479d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysmergepublications-transact-sql"></a>sysmergepublications (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データベースに定義されているマージ パブリケーションごとに 1 行のデータを保持します。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|既定のサーバーの名前です。|  
|**publisher_db**|**sysname**|既定のパブリッシャー データベースの名前です。|  
|**name**|**sysname**|パブリケーションの名前を指定します。|  
|**説明**|**nvarchar (255)**|パブリケーションの簡単な説明です。|  
|**保有期間**|**int**|パブリケーション全体設定 で、単位がの値によって示される位置の保有期間、 **retention_period_unit**列です。|  
|**publication_type**|**tinyint**|パブリケーションがフィルター選択されているかどうかを示します。<br /><br /> **0** = フィルター選択されたしません。<br /><br /> **1** = フィルター選択します。|  
|**pubid**|**uniqueidentifier**|このパブリケーションの一意な識別番号です。 パブリケーションが追加されたときに生成されます。|  
|**designmasterid**|**uniqueidentifier**|将来の使用のために予約されています。|  
|**parentid**|**uniqueidentifier**|現在のピアまたはサブセット パブリケーションの作成元である親パブリケーションです。階層パブリッシング トポロジで使用されます。|  
|**sync_mode**|**tinyint**|このパブリケーションの同期モードです。<br /><br /> **0**ネイティブを = です。<br /><br /> **1**文字を = です。|  
|**allow_push**|**int**|パブリケーションがプッシュ サブスクリプションを許可するかどうかを示します。<br /><br /> **0** = プッシュ サブスクリプションを許可しません。<br /><br /> **1** = プッシュ サブスクリプションを許可します。|  
|**allow_pull**|**int**|パブリケーションがプル サブスクリプションを許可するかどうかを示します。<br /><br /> **0** = プル サブスクリプションを許可しません。<br /><br /> **1** = プル サブスクリプションを許可します。|  
|**allow_anonymous**|**int**|パブリケーションが匿名サブスクリプションを許可するかどうかを示します。<br /><br /> **0** = 匿名サブスクリプションを許可しません。<br /><br /> **1** = 匿名サブスクリプションを許可します。|  
|**centralized_conflicts**|**int**|競合レコードがパブリッシャーで保存されるかどうかを示します。<br /><br /> **0** = 競合レコードはパブリッシャー側では保存されません。<br /><br /> **1** = 競合レコードはパブリッシャーに保存します。|  
|**ステータス**|**tinyint**|将来の使用のために予約されています。|  
|**snapshot_ready**|**tinyint**|パブリケーションのスナップショットの状態を示します。<br /><br /> **0** = スナップショットが使用できる状態ではありません。<br /><br /> **1** = スナップショットが使用できる状態です。<br /><br /> **2**新しいスナップショットを = このパブリケーションを作成する必要の。|  
|**enabled_for_internet**|**bit**|パブリケーションの同期ファイルが、FTP やその他のサービスを介して、インターネットに公開されるかどうかを示します。<br /><br /> **0** = 同期ファイルは、インターネットからアクセスできます。<br /><br /> **1** = 同期ファイルは、インターネットからアクセスすることはできません。|  
|**dynamic_filters**|**bit**|パラメーター化された行フィルターでパブリケーションがフィルター選択されているかどうかを示します。<br /><br /> **0** = パブリケーションは行ではなくフィルター選択します。<br /><br /> **1** = パブリケーションは行をフィルター処理します。|  
|**snapshot_in_defaultfolder**|**bit**|スナップショット ファイルが既定のフォルダーに格納されるかどうかを指定します。<br /><br /> **0**ファイルが既定のフォルダーにスナップショットを = です。<br /><br /> **1**で指定された場所にファイルが格納されているスナップショットを = **alt_snapshot_folder**です。|  
|**alt_snapshot_folder**|**nvarchar (255)**|スナップショットの代替フォルダーの場所です。|  
|**pre_snapshot_script**|**nvarchar (255)**|ポインター、します。**sql**サブスクライバーでスナップショットを適用するときに、マージ エージェントを実行する前に、レプリケーション オブジェクトのいずれかのファイルがスクリプトです。|  
|**post_snapshot_script**|**nvarchar (255)**|ポインター、します。**sql**ファイル、マージ エージェントが実行される結局、その他のレプリケーション オブジェクト スクリプトと、データは、初期同期中に適用されていること。|  
|**compress_snapshot**|**bit**|指定するかどうかに書き込まれるスナップショット、 **alt_snapshot_folder**場所を圧縮、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB 形式です。 **0**ファイルが圧縮されていないことを指定します。|  
|**ftp_address**|**sysname**|ディストリビューター用ファイル転送プロトコル (FTP) サービスのネットワーク アドレス。 FTP が有効である場合に、マージ エージェントがパブリケーション スナップショット ファイルを取得する場所を示します。|  
|**ftp_port**|**int**|ディストリビューター用 FTP サービスのポート番号。|  
|**ftp_subdirectory**|**nvarchar (255)**|マージ エージェントがスナップショット ファイルを取得する場所のサブディレクトリです。|  
|**ftp_login**|**sysname**|FTP サービスへの接続に使用されるユーザー名。|  
|**ftp_password**|**nvarchar (524)**|FTP サービスへの接続に使用されるユーザー パスワード。|  
|**conflict_retention**|**int**|競合を保有する保有期間の日数。 保有期間が経過すると、競合するテーブルから競合する行が削除されます。|  
|**keep_before_values**|**int**|このパブリケーションで同期の最適化が行われているかどうかを指定します。<br /><br /> **0** = 同期は最適化されず、すべてのサブスクライバーに送信されるパーティションはパーティションにデータが変更されたときに検証されます。<br /><br /> **1** = 同期は最適化され、変更されたパーティションの行を持つサブスクライバーだけが影響を受けます。|  
|**allow_subscription_copy**|**bit**|サブスクリプション データベースをコピーする機能が有効になっているかどうかを指定します。 **0**コピーが許可されないことを意味します。|  
|**allow_synctoalternate**|**bit**|代替同期パートナーがこのパブリッシャーと同期できるかどうかを示します。 **0**同期パートナーを使用できないことを意味します。|  
|**validate_subscriber_info**|**nvarchar(500)**|サブスクライバー情報を取得し、サブスクライバー上でのパラメーター化された行フィルター条件を検証するときに使用される機能の一覧。|  
|**ad_guidname**|**sysname**|パブリケーションがパブリッシュされるかどうかを指定します、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Active Directory です。 有効な GUID は、Active Directory でパブリケーションがパブリッシュされ、GUID が対応する Active Directory パブリケーション オブジェクトのことを指定します。 **objectGUID**です。 NULL の場合、パブリケーションは Active Directory にパブリッシュされません。|  
|**backward_comp_level**|**int**|データベースの互換性レベルです。 次の値のいずれかです。<br /><br /> **90** = [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)].<br /><br /> **100** = [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].|  
|**達した**|**int**|許可される同時実行マージ プロセスの最大数。 値**0**のこのプロパティは、特定の時点で実行されている同時実行マージ プロセスの数に制限がないことを意味します。 このプロパティは、1 つのマージ アプリケーションに対して一度に実行できる同時実行マージ処理数の制限値を設定します。 同時にスケジュールに組み込まれているスナップショット処理の数が、指定された実行可能な数より大きい場合、余分なジョブは待ち行列に挿入され、現在実行されているマージ処理が終わるまで待機状態に置かれます。|  
|**max_concurrent_dynamic_snapshots**|**int**|マージ パブリケーションに対して実行できるフィルター選択されたデータの同時実行スナップショット セッションの最大数です。 場合**0**、どの時点においても、パブリケーションに対して同時に実行できるフィルター選択されたデータの同時実行スナップショット セッションの最大数に制限はありません。 このプロパティは、1 つのマージ アプリケーションに対して一度に実行できる同時実行スナップショット処理数の制限値を設定します。 同時にスケジュールに組み込まれているスナップショット処理の数が、指定された実行可能な数より大きい場合、余分なジョブは待ち行列に挿入され、現在実行されているマージ処理が終わるまで待機状態に置かれます。|  
|**use_partition_groups**|**smallint**|パブリケーションで事前計算済みパーティションを使用するかどうかを指定します。|  
|**dynamic_filters_function_list**|**nvarchar(500)**|パブリケーションのパラメーター化された行フィルターで使用する関数の一覧です。各関数はセミコロンで区切られます。|  
|**partition_id_eval_proc**|**sysname**|割り当てられたパーティション ID を識別するために、サブスクライバーのマージ エージェントが実行するプロシージャの名前を指定します。|  
|**publication_number**|**smallint**|2 バイト マッピングを提供する id 列を指定**pubid**です。 **pubid**パブリケーションのグローバルに一意の識別子に対し、パブリケーション番号が、あるいは、同じデータベースでのみ一意です。|  
|**replicate_ddl**|**int**|パブリケーションに対してスキーマ レプリケーションがサポートされているかどうかを示します。<br /><br /> **0** = DDL ステートメントはレプリケートされません。<br /><br /> **1** = DDL ステートメントがパブリッシャーで実行がレプリケートされます。<br /><br /> 詳細については、「[パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)」を参照してください。|  
|**allow_subscriber_initiated_snapshot**|**bit**|サブスクライバーがパラメーター化フィルターを使用して、パブリケーションのスナップショットを生成する処理を開始できることを示します。 **1**サブスクライバーがスナップショット プロセスを開始できることを示します。|  
|**dynamic_snapshot_queue_timeout**|**int**|パラメーター化フィルターを使用するときに、サブスクライバーがスナップショット生成処理の開始までキューで待機する分数を指定します。|  
|**dynamic_snapshot_ready_timeout**|**int**|パラメーター化フィルターを使用するときに、サブスクライバーがスナップショット生成処理の完了まで待機する分数を指定します。|  
|**ディストリビューター**|**sysname**|パブリケーションのディストリビューターの名前。|  
|**snapshot_jobid**|**binary(16)**|サブスクライバーによるスナップショット生成処理の開始が可能な場合のスナップショットを生成するエージェント ジョブを示します。|  
|**allow_web_synchronization**|**bit**|Web 同期に対してパブリケーションが有効になっているかどうかを指定します。 ここで**1**パブリケーションに対して Web 同期が有効になっていることを意味します。|  
|**web_synchronization_url**|**nvarchar(500)**|Web 同期で使用するインターネット URL の既定値を指定します。|  
|**allow_partition_realignment**|**bit**|パブリッシャーでの行の変更がパーティションの変更を伴う場合、削除をサブスクライバーに送信するかどうかを示します。<br /><br /> **0** = データ、古いからパーティションは、このサブスクライバーにパブリッシャー上のこのデータに加えられた変更はレプリケートされませんが、サブスクライバーで行われた変更は、パブリッシャーにレプリケートされます、サブスクライバーに残ります。<br /><br /> **1** = サブスクライバーのパーティションの長い一部ではないデータを削除して、パーティション変更の結果を反映するためにサブスクライバーを削除します。<br /><br /> 詳細については、次を参照してください。 [sp_addmergepublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)です。<br /><br /> メモ: この値が、サブスクライバーで残っているデータ**0**が読み取り専用であるかのように扱う必要があります。 ただし、これは厳密に強制されていません、レプリケーション システムによってです。|  
|**retention_period_unit**|**tinyint**|定義するときに使用される単位を定義*保有*、これらの値のいずれかを指定することができます。<br /><br /> **0**日を = です。<br /><br /> **1**週を = です。<br /><br /> **2**月を = です。<br /><br /> **3**年を = です。|  
|**decentralized_conflicts**|**int**|競合の原因となったサブスクライバーで競合レコードを保存するかどうかを示します。<br /><br /> **0** = 競合レコードはサブスクライバー側では保存されません。<br /><br /> **1** = 競合レコードはサブスクライバーで格納します。|  
|**generation_leveling_threshold**|**int**|生成結果に含まれる変更の数を指定します。 生成とは、パブリッシャーまたはサブスクライバーに配信される変更のコレクションです。|  
|**automatic_reinitialization_policy**|**bit**|自動再初期化を実行する前に、サブスクライバーから変更をアップロードするかどうかを示します。<br /><br /> **1** = 自動再初期化が行われる前に、サブスクライバーから変更をアップロードします。<br /><br /> **0** = 自動再初期化する前に変更はアップロードされません。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addmergepublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql.md)   
 [sp_changemergepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql.md)   
 [sp_helpmergepublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql.md)  
  
  
