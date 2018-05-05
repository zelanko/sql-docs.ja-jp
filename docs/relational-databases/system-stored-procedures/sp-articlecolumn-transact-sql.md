---
title: sp_articlecolumn (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- sp_articlecolumn
- sp_articlecolumn_TSQL
helpviewer_keywords:
- sp_articlecolumn
ms.assetid: 8abaa8c1-d99e-4788-970f-c4752246c577
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ceee1dbfeca61646843232214854d33a27ce6960
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="sparticlecolumn-transact-sql"></a>sp_articlecolumn (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシュされたテーブルで列方向にデータをフィルター選択するために、アーティクルに含まれている列を指定します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_articlecolumn [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @column = ] 'column' ]  
    [ , [ @operation = ] 'operation' ]  
    [ , [ @refresh_synctran_procs = ] refresh_synctran_procs ]  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @change_active = ] change_actve ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @internal = ] 'internal' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 このアーティクルを含むパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article=**] **'***記事***'**  
 アーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません。  
  
 [  **@column=**] **'***列***'**  
 追加または削除する列の名前を指定します。 *列*は**sysname**、既定値は NULL です。 NULL の場合はすべての列がパブリッシュされます。  
  
 [  **@operation=**] **'***操作***'**  
 アーティクルの列を追加するか削除するかを指定します。 *操作*は**nvarchar (5)**、既定値は add です。 **追加**レプリケーションする列をマークします。 **drop**列のマークを解除します。  
  
 [  **@refresh_synctran_procs=**] *refresh_synctran_procs*  
 レプリケートされた列数と一致するように、即時更新サブスクリプションをサポートするストアド プロシージャを再生成するかどうかを指定します。 *refresh_synctran_procs*は**ビット**、既定値は**1**です。 場合**1**、ストアド プロシージャを再生成します。  
  
 [  **@ignore_distributor =**] *ignore_distributor*  
 ディストリビューターに接続しなくてもこのストアド プロシージャが実行されるかどうかを示します。 *ignore_distributor*は**ビット**、既定値は**0**します。 場合**0**パブリッシング用のデータベースを有効にする必要があります、およびアーティクルによってレプリケートされた新しい列を反映するようにアーティクル キャッシュを更新する必要があります。 場合**1**アーティクルの列はパブリッシュされていないデータベースに存在する; 復元状況でのみ使用する必要があるアーティクルに対して削除を許可します。  
  
 [  **@change_active =** ] *@change_active*  
 サブスクリプションを持つパブリケーションの列の変更を許可します。 *@change_active*は、 **int** 、既定値は**0**します。 場合**0**列は変更されません。 場合**1**列を追加またはサブスクリプションを持つアクティブなアーティクルから削除されることができます。  
  
 [  **@force_invalidate_snapshot =** ]*更によって*  
 このストアド プロシージャが実行する操作によって既存のスナップショットが無効になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**スナップショットが無効であることをアーティクルへの変更が発生しないことを指定します。 ストアド プロシージャで、変更に新しいスナップショットが必要であることが検出されると、エラーが発生し、変更は加えられません。  
  
 **1**アーティクルへの変更がスナップショットが無効であることがあり、新しいスナップショットが必要となる既存のサブスクリプションがある場合は、アクセス許可を与える不使用とマークするのには、既存のスナップショットと、新しいスナップショットを生成するように指定します。  
  
 [ **@force_reinit_subscription =** ]*更によって*  
 このストアド プロシージャが実行する操作によって、既存のサブスクリプションの再初期化が必要になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**アーティクルへの変更によってが再初期化するサブスクリプションを指定します。 場合は、ストアド プロシージャを再初期化するサブスクリプションを変更が必要で検出されると、エラーが発生し、変更は行われません。 **1**アーティクルへの変更が既存のサブスクリプションが初期化されることを指定します、サブスクリプションの再初期化を許可します。  
  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*では使用できません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
 [  **@internal=** ] **'***内部***'**  
 内部使用のみです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_articlecolumn**はスナップショット レプリケーションおよびトランザクション レプリケーションで使用します。  
  
 使用してサブスクライブされていないアーティクルのみをフィルター処理すること**sp_articlecolumn**です。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articlecolumn-transac_1.sql)]  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_articlecolumn**です。  
  
## <a name="see-also"></a>参照  
 [アーティクルを定義します。](../../relational-databases/replication/publish/define-an-article.md)   
 [列フィルター定義および変更](../../relational-databases/replication/publish/define-and-modify-a-column-filter.md)   
 [パブリッシュされたデータのフィルター処理](../../relational-databases/replication/publish/filter-published-data.md)   
 [sp_addarticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articleview &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
