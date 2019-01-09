---
title: sp_articlefilter (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_articlefilter_TSQL
- sp_articlefilter
helpviewer_keywords:
- sp_articlefilter
ms.assetid: 4c3fee32-a43f-4757-a029-30aef4696afb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f0869cfb6914766e2ab43e138831e2992aa6977b
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53209201"
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
 [  **@publication=**] **'**_パブリケーション_**'**  
 目的のアーティクルを含むパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article=**] **'**_記事_**'**  
 アーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません。  
  
 [  **@filter_name=**] **'**_filter_name_**'**  
 作成されるフィルター ストアド プロシージャの名前を指定します、 *filter_name*します。 *filter_name*は**nvarchar (386)**、既定値は NULL です。 アーティクル フィルターには一意の名前を指定する必要があります。  
  
 [  **@filter_clause=**] **'**_filter_clause_**'**  
 行フィルターを定義する制限句 (WHERE) を指定します。 制限句を入力する場合は、WHERE キーワードを省略します。 *filter_clause*は**ntext**、既定値は NULL です。  
  
 [ **@force_invalidate_snapshot =** ]*更によって*  
 このストアド プロシージャが実行する操作によって既存のスナップショットが無効になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**スナップショットが無効であることをアーティクルへの変更が発生しないことを指定します。 ストアド プロシージャで、変更に新しいスナップショットが必要であることが検出されると、エラーが発生し、変更は加えられません。  
  
 **1**アーティクルへの変更はスナップショットが無効であることがあり、新しいスナップショットを必要とする既存のサブスクリプションがある場合は、アクセス許可を付与 obsolete としてマーク済みである既存のスナップショットを新しいスナップショットを生成を指定します。  
  
 [  **@force_reinit_subscription =** ]*更によって*  
 このストアド プロシージャが実行する操作によって、既存のサブスクリプションの再初期化が必要になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**アーティクルへの変更がサブスクリプションの再初期化の必要性を発生しないことを指定します。 ストアド プロシージャが、変更がサブスクリプションの再初期化する必要になることを検出した場合は、エラーが発生し、変更は行われません。  
  
 **1**アーティクルの変更の場合、既存のサブスクリプションが初期化されることを指定します。 サブスクリプションの再初期化を許可します。  
  
 [  **@publisher=** ] **'**_パブリッシャー_**'**  
 以外を指定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*では使用できません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_articlefilter**スナップショット レプリケーションおよびトランザクション レプリケーションで使用されます。  
  
 実行**sp_articlefilter**の既存のサブスクリプションを持つアーティクルである必要があります、サブスクリプションを再初期化します。  
  
 **sp_articlefilter**フィルターを作成し、フィルター ストアド プロシージャの ID を挿入、**フィルター**の列、 [sysarticles &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md)テーブルし、制限句のテキストを挿入、 **filter_clause**列。  
  
 行方向のフィルターを使用してアーティクルを作成するには実行[sp_addarticle &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)なしで*フィルター*パラメーター。 実行**sp_articlefilter**を含むすべてのパラメーターを指定*filter_clause*、し、実行[sp_articleview &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)、同じを含むすべてのパラメーターを提供する*filter_clause*します。 フィルターが既に存在する場合と場合、**型**で**sysarticles**は**1** (ログベース アーティクル) は、前のフィルターが削除され、新しいフィルターが作成されます。  
  
 場合*filter_name*と*filter_clause*が指定されていない、以前のフィルターが削除され、フィルター ID に設定されて**0**します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articlefilter-transac_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_articlefilter**します。  
  
## <a name="see-also"></a>参照  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [静的行フィルターの定義と変更](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articleview &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articleview-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
