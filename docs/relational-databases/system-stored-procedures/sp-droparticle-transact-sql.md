---
title: "sp_droparticle (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_droparticle_TSQL
- sp_droparticle
helpviewer_keywords:
- sp_droparticle
ms.assetid: 09fec594-53f4-48a5-8edb-c50731c7adb2
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5c2d3ec47a41e2783bc5bab5a5eaaf1a4cedd3de
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spdroparticle-transact-sql"></a>sp_droparticle (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  スナップショット パブリケーションまたはトランザクション パブリケーションからアーティクルを削除します。 1 つでもサブスクリプションがあると、そのアーティクルは削除できません。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_droparticle [ @publication= ] 'publication'  
        , [ @article= ] 'article'  
    [ , [ @ignore_distributor = ] ignore_distributor ]  
    [ , [ @force_invalidate_snapshot= ] force_invalidate_snapshot ]  
    [ , [ @publisher = ] 'publisher' ]  
    [ , [ @from_drop_publication = ] from_drop_publication ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=**] **'***パブリケーション***'**  
 削除するアーティクルを含むパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@article=**] **'***記事***'**  
 削除するアーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません。  
  
 [  **@ignore_distributor =**] *ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
 [  **@force_invalidate_snapshot =** ]*更によって*  
 このストアド プロシージャが実行する操作によって既存のスナップショットが無効になることを許可します。 *更によって*は、**ビット**、既定値は**0**します。  
  
 **0**スナップショットが無効であることをアーティクルへの変更が発生しないことを指定します。 ストアド プロシージャで、変更に新しいスナップショットが必要であることが検出されると、エラーが発生し、変更は加えられません。  
  
 **1**アーティクルへの変更がスナップショットが無効であることがあり、新しいスナップショットが必要となる既存のサブスクリプションがある場合は、アクセス許可を与える不使用とマークするのには、既存のスナップショットと、新しいスナップショットを生成するように指定します。  
  
 [  **@publisher** =] **'***パブリッシャー***'**  
 指定以外[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。 *パブリッシャー*は**sysname**、既定値は NULL です。  
  
> [!NOTE]  
>  *パブリッシャー*でアーティクルのプロパティを変更するときに使用しないで、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パブリッシャーです。  
  
 [  **@from_drop_publication** =] *from_drop_publication*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_droparticle**は、スナップショットおよびトランザクション レプリケーションで使用します。  
  
 水平方向にフィルター選択されたアーティクルで**sp_droparticle**チェック、**型**内のアーティクルの列、 [sysarticles (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/sysarticles-transact-sql.md)テーブル、ビューやフィルターを削除するもあるかどうかを決定します。 自動作成されたビューまたはフィルターは、アーティクルと共に削除されます。 手動で作成した場合は、削除されません。  
  
 実行する**sp_droparticle**パブリケーションからアーティクルを削除する削除されませんオブジェクトから、パブリケーション データベースまたはサブスクリプション データベースから対応するオブジェクト。 これらのオブジェクトは、必要に応じて `DROP <object>` を使用して手動で削除します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_droparticle](../../relational-databases/replication/codesnippet/tsql/sp-droparticle-transact-_1.sql)]  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_droparticle**です。  
  
## <a name="see-also"></a>参照  
 [アーティクルを削除します。](../../relational-databases/replication/publish/delete-an-article.md)   
 [既存のパブリケーションでのアーティクルの追加と削除](../../relational-databases/replication/publish/add-articles-to-and-drop-articles-from-existing-publications.md)   
 [sp_addarticle &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addarticle-transact-sql.md)   
 [sp_changearticle (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changearticle-transact-sql.md)   
 [sp_helparticle &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helparticle-transact-sql.md)   
 [sp_helparticlecolumns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
