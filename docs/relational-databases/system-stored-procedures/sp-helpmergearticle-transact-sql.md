---
title: "sp_helpmergearticle (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_helpmergearticle
- sp_helpmergearticle_TSQL
helpviewer_keywords: sp_helpmergearticle
ms.assetid: 0fb9986a-3c33-46ef-87bb-297396ea5a6a
caps.latest.revision: "40"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 970c07111ba123be3262f9effb5c87a26bb14960
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpmergearticle-transact-sql"></a>sp_helpmergearticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  アーティクルに関する情報を返します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されるか、再パブリッシュしているサブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpmergearticle [ [ @publication = ] 'publication' ]  
    [ , [ @article= ] 'article' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=**] **'***パブリケーション***'**  
 情報を取得するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値は **%** 、現在のデータベース内のすべてのパブリケーションに含まれているすべてのマージ アーティクルに関する情報が返されます。  
  
 [  **@article=**] **'***記事***'**  
 情報を返すアーティクルの名前を指定します。 *記事*は**sysname**、既定値は **%** 、指定したパブリケーションのすべてのマージ アーティクルに関する情報が返されます。  
  
## <a name="result-set"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|アーティクルの識別子。|  
|**name**|**sysname**|アーティクルの名前。|  
|**source_owner**|**sysname**|ソース オブジェクトの所有者の名前。|  
|**source_object**|**sysname**|追加するアーティクルのソース オブジェクトの名前。|  
|**sync_object_owner**|**sysname**|パブリッシュされたアーティクルを定義するビューの所有者の名前。|  
|**sync_object**|**sysname**|パーティションの初期データを設定するときに使用するカスタム オブジェクトの名前。|  
|**説明**|**nvarchar (255)**|アーティクルの説明。|  
|**ステータス**|**tinyint**|アーティクルの状態。次のいずれかの値になります。<br /><br /> **1** = 非アクティブ<br /><br /> **2** = アクティブ<br /><br /> **5**保留中のデータ定義言語 (DDL) 操作を =<br /><br /> **6** = 新たに生成されたスナップショットを使った DDL 操作<br /><br /> 注: 値はアーティクルが再初期化されるときの**5**と**6**に変更されます**2**です。|  
|**creation_script**|**nvarchar (255)**|サブスクリプション データベースにアーティクルを作成する場合に使用される、オプションのアーティクル スキーマ スクリプトのパスと名前です。|  
|**conflict_table**|**nvarchar(270)**|追加または更新の競合を記録するテーブルの名前です。|  
|**article_resolver**|**nvarchar (255)**|アーティクルのカスタム競合回避モジュールです。|  
|**subset_filterclause**|**nvarchar (1000)**|行方向のフィルター選択を指定する WHERE 句です。|  
|**pre_creation_command**|**tinyint**|事前作成メソッド。次のいずれかの値になります。<br /><br /> **0** = なし<br /><br /> **1**ドロップを =<br /><br /> **2** = delete<br /><br /> **3** = truncate|  
|**schema_option**|**binary (8)**|アーティクルのスキーマ生成オプションのビットマップ。 このビットマップ オプションについては、次を参照してください。 [sp_addmergearticle](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)または[sp_changemergearticle](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)です。|  
|**型**|**smallint**|アーティクルの種類。次のいずれかの値になります。<br /><br /> **10** = テーブル<br /><br /> **32**ストアド プロシージャを =<br /><br /> **64** = ビューまたはインデックス付きビュー<br /><br /> **128** = ユーザー定義関数<br /><br /> **160** = シノニム スキーマのみ|  
|**column_tracking**|**int**|列レベルの追跡の設定ここで**1**列レベルの追跡が、上にあることを意味し、 **0**列レベルの追跡がオフであることを意味します。|  
|**resolver_info**|**nvarchar (255)**|アーティクルの競合回避モジュールの名前。|  
|**vertical_partition**|**bit**|アーティクルが垂直方向にパーティション分割されている場合ここで**1**アーティクルは垂直方向にパーティション分割によって、ことを意味し、 **0**なっていないことを意味します。|  
|**destination_owner**|**sysname**|対象オブジェクトの所有者。 ストアド プロシージャ、ビュー、およびユーザー定義関数 (UDF) スキーマ アーティクルをマージするときのみ適用されます。|  
|**identity_support**|**int**|自動 id 範囲処理が有効である場合ここで**1**が有効になっていると**0**は無効になります。|  
|**identity_range**|**bigint**|新しい ID 値を割り当てるときに使用する範囲サイズ。 詳細については、マージ レプリケーション」セクションを参照してください。 [Id 列のレプリケート](../../relational-databases/replication/publish/replicate-identity-columns.md)です。|  
|**identity_range**|**bigint**|新しい ID 値を割り当てるときに使用する範囲サイズ。 詳細については、マージ レプリケーション」セクションを参照してください。 [Id 列のレプリケート](../../relational-databases/replication/publish/replicate-identity-columns.md)です。|  
|**しきい値**|**int**|実行しているサブスクライバーで使用されるパーセンテージ値[!INCLUDE[ssEW](../../includes/ssew-md.md)]または以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。 **しきい値**マージ エージェントが新しい id 範囲を割り当てる場合を制御します。 threshold で指定されているパーセンテージ値が使用される場合、マージ エージェントは新しい ID 範囲を作成します。 詳細については、マージ レプリケーション」セクションを参照してください。 [Id 列のレプリケート](../../relational-databases/replication/publish/replicate-identity-columns.md)です。|  
|**verify_resolver_signature**|**int**|マージ レプリケーションで競合回避モジュールを使用する前に、デジタル署名を検証する場合ここで**0**署名が確認されないことを意味し、 **1**元が信頼できるかどうかに署名を検証することを意味します。|  
|**destination_object**|**sysname**|対象オブジェクトの名前です。 ストアド プロシージャ、ビュー、および UDF スキーマ アーティクルをマージするときのみ適用されます。|  
|**allow_interactive_resolver**|**int**|アーティクルに対するインタラクティブ競合回避モジュールを使用する場合ここで**1**この競合回避モジュールを使用することを意味し、 **0**使用されないことを意味します。|  
|**@fast_multicol_updateproc**|**int**|有効または無効に 1 つの UPDATE ステートメントで同じ行に複数の列に変更を適用するマージ エージェントここで**1** 1 つのステートメントで複数の列が更新されることを意味し、 **0** UPDATE ステートメントを分離する手段が更新される各列の問題です。|  
|**check_permissions**|**int**|確認されるテーブルレベル権限のビットマップを表す整数値。 使用可能な値の一覧は、次を参照してください。 [sp_addmergearticle (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md).|  
|**processing_order**|**int**|パブリケーションのアーティクルに対してデータ変更が適用される順序。|  
|**upload_options**|**tinyint**|クライアント サブスクリプションを使用したサブスクライバー側での更新に対する制限を定義します。次のいずれかの値になります。<br /><br /> **0** = クライアント サブスクリプションを使用したサブスクライバー側で更新に制限はありません。 すべての変更がパブリッシャーにアップロードされます。<br /><br /> **1** = クライアント サブスクリプションを使用したサブスクライバー側で変更が許可されますが、パブリッシャーにアップロードされません。<br /><br /> **2** = クライアント サブスクリプションを使用したサブスクライバーでの変更は許可されません。<br /><br /> 詳細については、「[ダウンロード専用アーティクルを使用したマージ レプリケーションのパフォーマンス最適化](../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)」を参照してください。|  
|**identityrangemanagementoption**|**int**|自動 id 範囲処理が有効である場合ここで**1**が有効になっていると**0**は無効になります。|  
|**delete_tracking**|**bit**|削除はレプリケートされます。 場合、ここで**1**削除がレプリケートされることを意味し、 **0**されないことを意味します。|  
|**compensate_for_errors**|**bit**|同期中にエラーが発生したときに補正アクションが実行を示しますここで**1**補正アクションを取られることを示しますと**0**補正アクションの実行は取得されないことを意味します。|  
|**partition_options**|**tinyint**|アーティクル内のデータをパーティション分割する方法を定義します。パーティション分割することにより、すべての行が 1 つのパーティションまたは 1 つのサブスクリプションに属している場合に、パフォーマンスを最適化できます。 *partition_options*値は次のいずれかになります。<br /><br /> **0** =「重複する」パーティションは、これは、;、アーティクルのフィルターを静的か、各パーティションのデータの一意なサブセットを生成しません。<br /><br /> **1** = パーティションが重複しています。 データ操作言語 (DML) の更新がサブスクライバーで行が属しているパーティションを変更することはできません。<br /><br /> **2** = フィルター選択は、アーティクルには、重複しないパーティションが得られますが、複数のサブスクライバーが同じパーティションを受け取ることができます。<br /><br /> **3** = フィルター選択は、アーティクルには、各サブスクリプションに対して一意では、重複しないパーティションが得られます。|  
|**artid**|**uniqueidentifier**|アーティクルを一意に識別する識別子。|  
|**pubid**|**uniqueidentifier**|アーティクルがパブリッシュされるパブリケーションを一意に識別する識別子。|  
|**stream_blob_columns**|**bit**|バイナリ ラージ オブジェクトの列をレプリケートするときにデータ ストリームの最適化を使用するかどうかを示します。 **1**最適化を使用していることを意味し、 **0**最適化が使用されていないことを意味します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_helpmergearticle**はマージ レプリケーションで使用します。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **db_owner**パブリケーション データベースの固定データベース ロール、 **replmonitor** を実行できるは、ディストリビューションデータベースまたはパブリケーションのパブリケーションアクセスリストでのロール**sp_helpmergearticle**です。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_helpmergearticle](../../relational-databases/replication/codesnippet/tsql/sp-helpmergearticle-tran_1.sql)]  
  
## <a name="see-also"></a>参照  
 [表示およびアーティクルのプロパティの変更](../../relational-databases/replication/publish/view-and-modify-article-properties.md)   
 [sp_addmergearticle &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)   
 [sp_changemergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md)   
 [sp_dropmergearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergearticle-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
