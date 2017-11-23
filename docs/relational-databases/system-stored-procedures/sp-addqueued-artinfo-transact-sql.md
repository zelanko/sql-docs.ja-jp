---
title: "sp_addqueued_artinfo (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- sp_addqueued_artinfo
- sp_addqueued_artinfo_TSQL
helpviewer_keywords: sp_addqueued_artinfo
ms.assetid: decdb6eb-3dcd-4053-a21d-fd367c3fbafb
caps.latest.revision: "20"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d9d843930ab1626ac4caadc169567163043e8b1b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spaddqueuedartinfo-transact-sql"></a>sp_addqueued_artinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  
  
> [!IMPORTANT]  
>  [Sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)の代わりにプロシージャを使用する必要があります**sp_addqueued_artinfo**です。 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)を含むスクリプトを生成、 **sp_addqueued_artinfo**と**sp_addsynctrigger**呼び出しです。  
  
 作成、 [MSsubscription_articles](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)アーティクルのサブスクリプション情報 (キュー更新、およびフェールオーバーとしてキュー更新で即時更新) を追跡するために使用されるサブスクライバーのテーブルにします。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addqueued_artinfo [ @artid= ] 'artid'  
        , [ @article= ] 'article'  
        , [ @publisher = ] 'publisher'  
        , [ @publisher_db = ] 'publisher_db'  
        , [ @publication = ] 'publication'  
        , [ @dest_table= ] 'dest_table'  
        , [ @owner = ] 'owner'  
        , [ @cft_table= ] 'cft_table'  
```  
  
## <a name="arguments"></a>引数  
 [  **@artid=** ] **'***artid***'**  
 アーティクル ID の名前を指定します。 *artid*は**int**、既定値はありません  
  
 [  **@article=**] **'***記事***'**  
 スクリプト作成の対象となるアーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません  
  
 [  **@publisher=**] **'***パブリッシャー***'**  
 パブリッシャー サーバーの名前を指定します。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [  **@publisher_db=**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。  
  
 [  **@publication=**] **'***パブリケーション***'**  
 スクリプト作成の対象となるパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@dest_table=** ] *' dest_table***'**  
 対象テーブルの名前を指定します。 *dest_table*は**sysname**、既定値はありません。  
  
 [ **@owner =** ] **'***所有者***'**  
 サブスクリプションの所有者を指定します。 *所有者*は**sysname**、既定値はありません。  
  
 [  **@cft_table=** ] **'***cft_table***'**  
 このアーティクルに対するキュー更新の競合テーブルの名前を指定します。 *cft_table*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addqueued_artinfo**は、ディストリビューション エージェントによってサブスクリプションの初期化の一部として使用します。 このストアド プロシージャは、ユーザーが頻繁に実行するものではありません。ただし、サブスクリプションを手動で設定する場合に利用できるストアド プロシージャです。  
  
 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)の代わりに**sp_addqueued_artinfo**です。  
  
## <a name="permissions"></a>Permissions  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addqueued_artinfo**です。  
  
## <a name="see-also"></a>参照  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [MSsubscription_articles &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
