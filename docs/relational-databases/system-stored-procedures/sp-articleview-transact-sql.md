---
title: sp_articleview (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_articleview
- sp_articleview_TSQL
helpviewer_keywords:
- sp_articleview
ms.assetid: a3d63fd6-f360-4a2f-8a82-a0dc15f650b3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b06d348358a141771816230179ca7deae4e4353a
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2019
ms.locfileid: "54132863"
---
# <a name="sparticleview-transact-sql"></a>sp_articleview (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  テーブルが列または行でフィルター選択されている場合に、パブリッシュされたアーティクルを定義するビューを作成します。 このビューは、出力先のテーブル用にフィルター選択されたスキーマやデータのソースとして使用されます。 このストアド プロシージャでは、サブスクライブされていないアーティクルだけを変更できます。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_articleview [ @publication = ] 'publication'  
        , [ @article = ] 'article'  
    [ , [ @view_name = ] 'view_name']  
    [ , [ @filter_clause = ] 'filter_clause']  
    [ , [ @change_active = ] change_active ]  
    [ , [ @force_invalidate_snapshot = ] force_invalidate_snapshot ]  
    [ , [ @force_reinit_subscription = ] force_reinit_subscription ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @refreshsynctranprocs = ] refreshsynctranprocs ]  
    [ , [ @internal = ] internal ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=**] **'**_パブリケーション_**'**  
 目的のアーティクルを含むパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article=**] **'**_記事_**'**  
 アーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません。  
  
 [  **@view_name=**] **'**_view_name_**'**  
 パブリッシュされたアーティクルを定義するビューの名前を指定します。 *view_name*は**nvarchar (386)**、既定値は NULL です。  
  
 [  **@filter_clause=**] **'**_filter_clause_**'**  
 行フィルターを定義する制限句 (WHERE) を指定します。 制限句を入力する場合は、WHERE キーワードを省略します。 *filter_clause*は**ntext**、既定値は NULL です。  
  
 [  **@change_active =** ] *@change_active*  
 サブスクリプションを持つパブリケーションの列の変更を許可します。 *@change_active*は、 **int**、既定値は**0**します。 場合**0**列は変更されません。 場合**1**ビューを作成または再サブスクリプションを持つアクティブなアーティクルに対して作成することができます。  
  
 [ **@force_invalidate_snapshot =** ]*更によって*  
 このストアド プロシージャが実行する操作によって既存のスナップショットが無効になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**スナップショットが無効であることをアーティクルへの変更が発生しないことを指定します。 ストアド プロシージャで、変更に新しいスナップショットが必要であることが検出されると、エラーが発生し、変更は加えられません。  
  
 **1**アーティクルへの変更はスナップショットが無効であることがあり、新しいスナップショットを必要とする既存のサブスクリプションがある場合は、アクセス許可を付与 obsolete としてマーク済みである既存のスナップショットを新しいスナップショットを生成を指定します。  
  
 [  **@force_reinit_subscription =]** _更によって_  
 このストアド プロシージャが実行する操作によって、既存のサブスクリプションの再初期化が必要になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**アーティクルへの変更では、サブスクリプションを再初期化するのには発生しないことを指定します。 ストアド プロシージャが、変更がサブスクリプションの再初期化する必要になることを検出した場合は、エラーが発生し、変更は行われません。  
  
 **1**アーティクルの変更の場合、既存のサブスクリプションが初期化されることを指定します。 サブスクリプションの再初期化を許可します。  
  
 [ **@publisher**=] **'**_パブリッシャー_**'**  
 以外を指定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*から発行するときに使用されません、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
 [ **@refreshsynctranprocs** =] *refreshsynctranprocs*  
 レプリケーションの同期に使用するストアド プロシージャを自動的に再作成するかどうかを指定します。 *refreshsynctranprocs*は**ビット**、既定値は 1 です。  
  
 **1**ストアド プロシージャが再作成することを意味します。  
  
 **0**ストアド プロシージャが再作成しないことを意味します。  
  
 [ **@internal**=]*内部*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_articleview**パブリッシュされたアーティクルを定義しでは、このビューの ID を挿入するビューを作成、 **sync_objid**の列、 [sysarticles &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md)テーブル、および制限句のテキストを挿入、 **filter_clause**列。 すべての列がレプリケートされる場合は、ない**filter_clause**、 **sync_objid**で、 [sysarticles &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md)テーブルの ID には設定されて、ベース テーブルと、使用して**sp_articleview**は必要ありません。  
  
 垂直方向にフィルター選択されたテーブルをパブリッシュする (つまり、列をフィルター) 最初に実行**sp_addarticle**なしで*sync_object*実行パラメーター [sp_articlecolumn &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md) (垂直方向のフィルターを定義する) をレプリケートし実行するには、各列に対して 1 回**sp_articleview**パブリッシュされたアーティクルを定義するビューを作成します。  
  
 水平方向にフィルター選択されたテーブルをパブリッシュする (つまり、フィルター処理する行)、実行[sp_addarticle &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)なしで*フィルター*パラメーター。 実行[sp_articlefilter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)を含むすべてのパラメーターを指定*filter_clause*します。 実行して**sp_articleview**を同じを含むすべてのパラメーターを提供する*filter_clause*します。  
  
 垂直方向および水平方向にフィルター選択されたテーブルを公開するには、実行[sp_addarticle &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)なしで*sync_object*または*フィルター*パラメーター。 実行[sp_articlecolumn &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlecolumn-transact-sql.md)をレプリケートする列ごとに 1 回とし実行[sp_articlefilter &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)と**sp _articleview**します。  
  
 場合、アーティクルがパブリッシュされたアーティクルを定義するビューを既には**sp_articleview**既存のビューを削除し、新しいものを自動的に作成されます。 ビューが手動で作成された場合 (**型**で[sysarticles &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/sysarticles-transact-sql.md)は**5**)、既存のビューは削除されません。  
  
 カスタム フィルター ストアド プロシージャと、パブリッシュされたアーティクルを手動で定義するビューを作成する場合は実行しないでください**sp_articleview**します。 代わりに、提供するよう、*フィルター*と*sync_object*パラメーター [sp_addarticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)、適切なと共に*型*値。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_AddTranArticle](../../relational-databases/replication/codesnippet/tsql/sp-articleview-transact-_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_articleview**します。  
  
## <a name="see-also"></a>参照  
 [Define an Article](../../relational-databases/replication/publish/define-an-article.md)   
 [静的行フィルターの定義と変更](../../relational-databases/replication/publish/define-and-modify-a-static-row-filter.md)   
 [sp_addarticle &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_articlefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-articlefilter-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_droparticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droparticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
