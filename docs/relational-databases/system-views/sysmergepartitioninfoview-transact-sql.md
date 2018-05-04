---
title: sysmergepartitioninfoview (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-views
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sysmergepartitioninfoview
- sysmergepartitioninfoview_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysmergepartitioninfoview view
ms.assetid: 714e2935-1bc7-4901-aea2-64b1bbda03d6
caps.latest.revision: 16
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fe47e35ed87d486e72e34b59aa2045486686d869
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sysmergepartitioninfoview-transact-sql"></a>sysmergepartitioninfoview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sysmergepartitioninfoview**ビューは、テーブル アーティクルのパーティション分割情報を公開します。 このビューは、パブリッシャー側のパブリケーション データベース、およびサブスクライバー側のサブスクリプション データベースに格納されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|アーティクルの名前です。|  
|**type**|**tinyint**|アーティクルの種類。次のいずれかになります。<br /><br /> **0x0a**テーブルを = です。<br /><br /> **0x20** = プロシージャ スキーマのみです。<br /><br /> **0x40** = ビュー スキーマのみ、またはインデックス付きビュー スキーマのみです。<br /><br /> **0x80** = 関数スキーマのみです。|  
|**objid**|**int**|パブリッシュされたオブジェクトの識別子です。|  
|**sync_objid**|**int**|同期データセットを表すビューのオブジェクト ID。|  
|**view_type**|**tinyint**|ビューの種類。<br /><br /> **0**ビューではなくを = です。 すべてのベース オブジェクトを使用します。<br /><br /> **1** = パーマネント ビュー。<br /><br /> **2** = 一時ビュー。|  
|**artid**|**uniqueidentifier**|指定したアーティクルの一意な ID 番号です。|  
|**説明**|**nvarchar (255)**|アーティクルの簡単な説明。|  
|**pre_creation_command**|**tinyint**|サブスクリプション データベースにアーティクルが作成されるときに実行される既定の操作。<br /><br /> **0** = なし - サブスクライバーでテーブルが既に存在する場合のアクションは行われません。<br /><br /> **1** = drop - テーブルを再作成する前に削除します。<br /><br /> **2** = 削除 - サブセット フィルターの WHERE 句に基づいて削除します。<br /><br /> **3** = 切り捨て - 2 が行ではなくページを削除と同じです。 ただし、WHERE 句は使用しません。|  
|**pubid**|**uniqueidentifier**|現在のアーティクルが属するパブリケーションの ID。|  
|**nickname**|**int**|アーティクル識別用のニックネーム マップ。|  
|**column_tracking**|**int**|アーティクルの列の追跡が実装されているかどうかを示します。|  
|**ステータス**|**tinyint**|アーティクルの状態。次のいずれかになります。<br /><br /> **1** = Unsynced - テーブルをパブリッシュする初期処理スクリプトは、次回、スナップショット エージェントの実行を実行します。<br /><br /> **2** = active - テーブルをパブリッシュする初期処理スクリプトが実行されています。|  
|**conflict_table**|**sysname**|現在のアーティクルに関する競合レコードが含まれているローカル テーブルの名前。 このテーブルは情報用のみとして提供されており、その内容は、カスタム競合回避ルーチンを使用して変更や削除ができます。または、管理者が直接変更したり、削除することもできます。|  
|**creation_script**|**nvarchar (255)**|アーティクルの作成スクリプト。|  
|**conflict_script**|**nvarchar (255)**|アーティクルの競合スクリプト。|  
|**article_resolver**|**nvarchar (255)**|このアーティクルの競合回避モジュールです。|  
|**ins_conflict_proc**|**sysname**|競合テーブルへの競合情報の書き込みに使用するプロシージャです。|  
|**insert_proc**|**sysname**|同期時に行の挿入に使用するプロシージャです。|  
|**update_proc**|**sysname**|同期時に行の更新に使用するプロシージャです。|  
|**select_proc**|**sysname**|マージ エージェントがロックやアーティクルの列と行の検索に使用する、自動生成ストアド プロシージャの名前です。|  
|**metadata_select_proc**|**sysname**|マージ レプリケーション システム テーブル内のメタデータへのアクセスに使用する、自動生成ストアド プロシージャの名前です。|  
|**delete_proc**|**sysname**|同期時に行の削除に使用するプロシージャです。|  
|**schema_option**|**binary(8)**|指定されたアーティクルに対するスキーマ生成オプションのビットマップです。 詳細については、サポート*schema_option*値を参照してください[sp_addmergearticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)です。|  
|**destination_object**|**sysname**|サブスクライバーで作成されるテーブルの名前。|  
|**destination_owner**|**sysname**|目的のオブジェクトの所有者名。|  
|**resolver_clsid**|**nvarchar (50)**|カスタム競合回避モジュールの ID。 ビジネス ロジック ハンドラーの場合、この値は NULL です。|  
|**subset_filterclause**|**nvarchar(1000)**|アーティクルのフィルター句。|  
|**missing_col_count**|**int**|アーティクルにない、パブリッシュされた列の数です。|  
|**missing_cols**|**varbinary (128)**|アーティクルにない列を示すビットマップです。|  
|**excluded_cols**|**varbinary (128)**|アーティクルから除外された列のビットマップです。|  
|**excluded_col_count**|**int**|アーティクルから除外された列の数です。|  
|**columns**|**varbinary (128)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**deleted_cols**|**varbinary (128)**|アーティクルから削除された列を示すビットマップです。|  
|**resolver_info**|**nvarchar (255)**|カスタム競合回避モジュールによって必要な追加情報の記憶域。|  
|**view_sel_proc**|**nvarchar(290)**|マージ エージェントが、動的にフィルター選択されたパブリケーションでアーティクルを最初に作成するとき、およびフィルター選択された任意のパブリケーションで変更された行を列挙するときに使用するストアド プロシージャの名前です。|  
|**gen_cur**|**bigint**|アーティクルのベース テーブルに対するローカルの変更の generates 値です。|  
|**vertical_partition**|**int**|列のフィルター選択がテーブル アーティクルで有効かどうかを示します。 **0**垂直方向のフィルタ リングがないことを示します、すべての列をパブリッシュします。|  
|**identity_support**|**int**|ID 範囲の自動処理が有効かどうかを示します。 **1** id 範囲処理が有効になっていることを意味し、 **0**範囲サポートの識別情報がないことを意味します。|  
|**before_image_objid**|**int**|追跡テーブルのオブジェクト ID。 追跡テーブルには、パブリケーションに対するパーティションの変更の最適化が有効な場合、特定のキー列の値が含まれます。|  
|**before_view_objid**|**int**|ビュー テーブルのオブジェクト ID。 ビューが存在するテーブルでは、行の削除または更新前に、その行が特定のサブスクライバーに属していたかどうかが追跡されます。 パブリケーションに対するパーティションの変更の最適化が有効な場合にのみ適用されます。|  
|**verify_resolver_signature**|**int**|マージ レプリケーションで競合回避モジュールを使用する前に、デジタル署名を確認するかどうかを示します。<br /><br /> **0** = 署名がないことを確認します。<br /><br /> **1** = 署名が信頼できる発行元であるかどうかを表示することを確認します。|  
|**allow_interactive_resolver**|**bit**|アーティクルに対する対話型の競合回避モジュールの使用が有効かどうかを示します。 **1**アーティクルにインタラクティブ競合回避モジュールを使用できることを意味します。|  
|**fast_multicol_updateproc**|**bit**|1 つの UPDATE ステートメントで同じ行の複数の列に対して変更を適用するように、マージ エージェントが有効になっているかどうかを示します。<br /><br /> **0**列ごとに個別の更新の変更の問題を = です。<br /><br /> **1** 1 つのステートメントで複数の列を更新する UPDATE ステートメントの発行を = です。|  
|**check_permissions**|**int**|テーブル レベルの権限のビットマップは、マージ エージェントがパブリッシャーに変更を適用するときにことを確認します。 *check_permissions*これらの値のいずれかを持つことができます。<br /><br /> **0x00** = 権限はチェックされません。<br /><br /> **0x10** = チェックをサブスクライバーで挿入が行われる前に、パブリッシャー側でのアクセス許可をアップロードすることができます。<br /><br /> **0x20**サブスクライバーで行われた更新プログラムをアップロードする前に、パブリッシャー側で権限をチェックを = です。<br /><br /> **0x40**したサブスクライバー側で Delete をアップロードする前に、パブリッシャー側で権限をチェックを = です。|  
|**maxversion_at_cleanup**|**int**|マージ エージェントの次回実行時にクリーンアップされる generation の最大値です。|  
|**processing_order**|**int**|マージ パブリケーション内のアーティクルの処理順序を示します値が**0**ことを示し、アーティクルが順序付けられた、非アーティクルが最高の最低値から順に処理します。 2 つのアーティクルの値が同じ場合、それらは同時に処理されます。 詳細については、「[マージ アーティクルの処理順序の指定](../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)」を参照してください。|  
|**upload_options**|**tinyint**|変更がサブスクライバーで許可されるか、サブスクライバーからアップロードされるかを示します。次の値のいずれかになります。<br /><br /> **0** = サブスクライバー側で行われる更新に制限はありません。 すべての変更がパブリッシャーにアップロードされます。<br /><br /> **1** = 変更は許可されます、サブスクライバーでパブリッシャーにアップロードされません。<br /><br /> **2** = 変更はサブスクライバーで許可されません。|  
|**published_in_tran_pub**|**bit**|マージ パブリケーション内のアーティクルが、トランザクション パブリケーションでもパブリッシュされるかどうかを示します。<br /><br /> **0** = アーティクルはトランザクション アーティクルでパブリッシュされません。<br /><br /> **1** = アーティクルはトランザクション アーティクルでもパブリッシュされます。|  
|**lightweight**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**procname_postfix**|**nchar(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**well_partitioned_lightweight**|**bit**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**before_upd_view_objid**|**int**|更新前のテーブルのビューの ID です。|  
|**delete_tracking**|**bit**|削除がレプリケートされるかどうかを示します。<br /><br /> **0** = 削除はレプリケートされません。<br /><br /> **1** = マージ レプリケーションの既定の動作は、削除がレプリケートされます。<br /><br /> ときに、値の*delete_tracking*は**0**パブリッシャー、サブスクライバーで削除された行を手動で削除する必要があります、およびサブスクライバー、パブリッシャー側で削除された行を手動で削除する必要があります。<br /><br /> 注: 値の**0**の非収束の結果します。|  
|**compensate_for_errors**|**bit**|同期中にエラーが検出されたときに補正アクションが行われるかどうかを示します。<br /><br /> **0** = 補正アクションは無効です。<br /><br /> **1** = マージ レプリケーションの既定の動作は、これらの変更を元に戻すアクションを補正するサブスクライバーまたはパブリッシャーが常に潜在顧客で適用できない変更します。<br /><br /> 注: 値の**0**の非収束の結果します。|  
|**pub_range**|**bigint**|パブリッシャーの ID 範囲の大きさ。|  
|**range**|**bigint**|調整の際にサブスクライバーに割り当てられる、連続する ID 値の大きさ。|  
|**threshold**|**int**|ID 範囲のしきい値のパーセンテージ。|  
|**stream_blob_columns**|**bit**|バイナリ ラージ オブジェクトの列にストリームの最適化を使用するかどうかを示します。 **1**最適化が試行されたことを意味します。|  
|**preserve_rowguidcol**|**bit**|レプリケーションが既存の rowguid 列を使用するかどうかを示します。 値**1**既存の ROWGUIDCOL 列を使用することを意味します。 **0**レプリケーションによって ROWGUIDCOL 列を追加することを意味します。|  
|**partition_view_id**|**int**|サブスクライバー パーティションを定義するビューを指定します。|  
|**repl_view_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**partition_deleted_view_rule**|**sysname**|マージ レプリケーション トリガー内で、列の古い値に基づいて削除または更新された各行のパーティション ID を取得するために使用されるステートメントです。|  
|**partition_inserted_view_rule**|**sysname**|マージ レプリケーション トリガー内で、列の新しい値に基づいて挿入または更新された各行のパーティション ID を取得するために使用されるステートメントです。|  
|**membership_eval_proc_name**|**sysname**|内の行の現在のパーティション Id を評価するプロシージャの名前[MSmerge_contents &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/msmerge-contents-transact-sql.md)です。|  
|**column_list**|**sysname**|アーティクル内でパブリッシュされた列のコンマ区切りの一覧です。|  
|**column_list_blob**|**sysname**|バイナリ ラージ オブジェクトの列を含む、アーティクル内でパブリッシュされた列のコンマ区切りの一覧です。|  
|**expand_proc**|**sysname**|新たに挿入された親行のすべての子行、パーティションを変更された親行、および削除された親行のパーティション ID を再評価するプロシージャの名前です。|  
|**logical_record_parent_nickname**|**int**|論理レコード内の、指定されたアーティクルのトップレベルにある親のニックネームです。|  
|**logical_record_view**|**int**|それぞれの子の rowguid に対応する、トップレベルにある親アーティクルの rowguid を出力するビューです。|  
|**logical_record_deleted_view_rule**|**sysname**|ような**logical_record_view**子テーブル内の行、"deleted"には、update および delete トリガーが表示される点を除いて、します。|  
|**logical_record_level_conflict_detection**|**bit**|競合を、論理レコード レベルと、行または列レベルのどちらで検出するかを示します。<br /><br /> **0** = 行または列レベルの競合検出を使用します。<br /><br /> **1** = 論理レコードの競合検出を使用する、パブリッシャーで行の変更と、個別の変更は、同じ論理行を行、サブスクライバーのレコードは、競合として処理します。<br /><br /> この値が 1 の場合には、論理レコード レベルでの競合解決だけを使用できます。|  
|**logical_record_level_conflict_resolution**|**bit**|競合を時、行または列レベル、または論理レコード レベルで解決できるかどうかを示します。<br /><br /> **0** = 行または列レベルの解決を使用します。<br /><br /> **1** = の場合に、論理レコード全体が優先されるデータ競合の側を優先されなかった論理レコード全体が上書きされます。<br /><br /> 値 1 は、論理レコード レベルでの検出でも、行または列レベルの検出でも使用することができます。|  
|**partition_options**|**tinyint**|アーティクル内のデータをパーティション分割する方法を定義します。パーティション分割することにより、すべての行が 1 つのパーティションまたは 1 つのサブスクリプションに属している場合に、パフォーマンスを最適化できます。 *Partition_options*値は次のいずれかになります。<br /><br /> **0** 「重複する」パーティションは、各パーティションのデータの一意のサブセットを作成しませんまたは静的のいずれか、アーティクルのフィルターを = です。<br /><br /> **1** = パーティションが重複している場合、およびサブスクライバーで実行された DML 更新は、行が属するパーティションを変更できません。<br /><br /> **2** = フィルター選択は、アーティクルには、重複しないパーティションが得られますが、複数のサブスクライバーが同じパーティションを受け取ることができます。<br /><br /> **3** = フィルター選択は、アーティクルには、各サブスクリプションに対して一意では、重複しないパーティションが得られます。|  
|**name**|**sysname**|パーティションの名前。|  
  
## <a name="see-also"></a>参照  
 [パラメーター化されたフィルターによるマージ パブリケーションのパーティションを管理します。](../../relational-databases/replication/publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)   
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;TRANSACT-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_addmergepartition &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepartition-transact-sql.md)   
 [sp_helpmergepartition &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepartition-transact-sql.md)  
  
  
