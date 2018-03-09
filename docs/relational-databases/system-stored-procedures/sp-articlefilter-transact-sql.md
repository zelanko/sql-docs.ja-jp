---
title: "sp_articlefilter (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_articlefilter_TSQL
- sp_articlefilter
helpviewer_keywords:
- sp_articlefilter
ms.assetid: 4c3fee32-a43f-4757-a029-30aef4696afb
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: de8979cdc3cb382aa290148e560d8eb72db94b1b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sparticlefilter-transact-sql"></a>sp_articlefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリッシュされたデータをテーブル アーティクルに基づいてフィルター選択します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_articlefilter [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @filter_name = ] 'filter_name' ]  
    [ , [ @filter_clause = ] 'filter_clause' ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=**] **'***パブリケーション***'**  
 目的のアーティクルを含むパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article=**] **'***記事***'**  
 アーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません。  
  
 [  **@filter_name=**] **'***filter_name***'**  
 作成されるフィルター ストアド プロシージャの名前を指定します、 *filter_name*です。 *filter_name*は**nvarchar (386)**、既定値は NULL です。 アーティクル フィルターには一意の名前を指定する必要があります。  
  
 [  **@filter_clause=**] **'***filter_clause***'**  
 行フィルターを定義する制限句 (WHERE) を指定します。 制限句を入力する場合は、WHERE キーワードを省略します。 *filter_clause*は**ntext**、既定値は NULL です。  
  
 [  **@force_invalidate_snapshot =** ]*更によって*  
 このストアド プロシージャが実行する操作によって既存のスナップショットが無効になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**スナップショットが無効であることをアーティクルへの変更が発生しないことを指定します。 ストアド プロシージャで、変更に新しいスナップショットが必要であることが検出されると、エラーが発生し、変更は加えられません。  
  
 **1**アーティクルへの変更がスナップショットが無効であることがあり、新しいスナップショットが必要となる既存のサブスクリプションがある場合は、アクセス許可を与える不使用とマークするのには、既存のスナップショットと、新しいスナップショットを生成するように指定します。  
  
 [  **@force_reinit_subscription =** ]*更によって*  
 このストアド プロシージャが実行する操作によって、既存のサブスクリプションの再初期化が必要になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**アーティクルへの変更ではサブスクリプションの再初期化の必要性は発生しないことを指定します。 場合は、ストアド プロシージャを再初期化するサブスクリプションを変更が必要で検出されると、エラーが発生し、変更は行われません。  
  
 **1**アーティクルへの変更の場合、既存のサブスクリプションが初期化されることを指定し、サブスクリプションを再初期化が発生するを許可します。  
  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*では使用できません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_articlefilter**はスナップショット レプリケーションおよびトランザクション レプリケーションで使用します。  
  
 実行する**sp_articlefilter**の既存のサブスクリプションを持つアーティクルでは、する必要があります、サブスクリプションを再初期化します。  
  
 **sp_articlefilter**フィルターを作成し、フィルター ストアド プロシージャの ID を挿入、**フィルター**の列、 [sysarticles (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/sysarticles-transact-sql.md)テーブル、および制限句のテキストを挿入、 **filter_clause**列です。  
  
 水平方向のフィルターを使用してアーティクルを作成するには、実行[sp_addarticle (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)なし*フィルター*パラメーター。 実行**sp_articlefilter**、含むすべてのパラメーターを提供する*filter_clause*、し、実行[sp_articleview (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)を同じを含むすべてのパラメーターを提供する*filter_clause*です。 場合、フィルターが既に存在する場合、**型**で**sysarticles**は**1** (ログベース アーティクル) は、以前のフィルターが削除され、新しいフィルターを作成します。  
  
 場合*filter_name*と*filter_clause*が指定されていない、以前のフィルターが削除され、フィルター ID に設定されている**0**します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articlefilter-transac_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_articlefilter**です。  
  
## <a name="see-also"></a>参照  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [静的行フィルターの定義と変更](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articleview &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
