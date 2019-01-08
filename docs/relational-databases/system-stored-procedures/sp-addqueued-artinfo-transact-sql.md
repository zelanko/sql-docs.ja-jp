---
title: sp_addqueued_artinfo (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addqueued_artinfo
- sp_addqueued_artinfo_TSQL
helpviewer_keywords:
- sp_addqueued_artinfo
ms.assetid: decdb6eb-3dcd-4053-a21d-fd367c3fbafb
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c326a8e3a5fa2bd95f536d434ff9782952ba70d3
ms.sourcegitcommit: 37310da0565c2792aae43b3855bd3948fd13e044
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/18/2018
ms.locfileid: "53590897"
---
# <a name="spaddqueuedartinfo-transact-sql"></a>sp_addqueued_artinfo (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  
  
> [!IMPORTANT]  
>  [Sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)の代わりにプロシージャを使用する必要があります**sp_addqueued_artinfo**します。 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)を含むスクリプトを生成、 **sp_addqueued_artinfo**と**sp_addsynctrigger**呼び出し。  
  
 作成、 [MSsubscription_articles](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)アーティクルのサブスクリプション情報 (キュー更新、およびフェールオーバーとしてキュー更新を使用する即時更新) を追跡するために使用されるサブスクライバーのテーブルにします。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
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
 [  **@artid=** ] **'**_artid_**'**  
 アーティクル ID の名前を指定します。 *artid*は**int**、既定値はありません  
  
 [  **@article=**] **'**_記事_**'**  
 スクリプト作成の対象となるアーティクルの名前を指定します。 *記事*は**sysname**、既定値はありません  
  
 [  **@publisher=**] **'**_パブリッシャー_**'**  
 パブリッシャー サーバーの名前を指定します。 *パブリッシャー*は**sysname**、既定値はありません。  
  
 [  **@publisher_db=**] **'**_publisher_db_**'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。  
  
 [  **@publication=**] **'**_パブリケーション_**'**  
 スクリプト作成の対象となるパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [  **@dest_table=** ] _' dest_table_**'**  
 対象テーブルの名前を指定します。 *dest_table*は**sysname**、既定値はありません。  
  
 [ **@owner =** ] **'**_所有者_**'**  
 サブスクリプションの所有者を指定します。 *所有者*は**sysname**、既定値はありません。  
  
 [  **@cft_table=** ] **'**_cft_table_**'**  
 このアーティクルに対するキュー更新の競合テーブルの名前を指定します。 *cft_table*は**sysname**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addqueued_artinfo**サブスクリプションの初期化の一部として、ディストリビューション エージェントによって使用されます。 このストアド プロシージャは、ユーザーが頻繁に実行するものではありません。ただし、サブスクリプションを手動で設定する場合に利用できるストアド プロシージャです。  
  
 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)の代わりに**sp_addqueued_artinfo**します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addqueued_artinfo**します。  
  
## <a name="see-also"></a>参照  
 [Updatable Subscriptions for Transactional Replication](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [MSsubscription_articles &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
