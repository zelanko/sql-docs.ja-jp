---
title: sp_addqueued_artinfo (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 33769260b25ef3f6127f6f12ac54af07c5951ad1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82820673"
---
# <a name="sp_addqueued_artinfo-transact-sql"></a>sp_addqueued_artinfo (Transact-sql)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  
  
> [!IMPORTANT]  
>  **Sp_addqueued_artinfo**の代わりに[sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)プロシージャを使用する必要があります。 [sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)は、 **sp_addqueued_artinfo**と**sp_addsynctrigger**の呼び出しを含むスクリプトを生成します。  
  
 アーティクルのサブスクリプション情報 (キュー更新、およびフェールオーバーとしてキュー更新を使用する即時更新) を追跡するために使用される、サブスクライバーで[MSsubscription_articles](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)テーブルを作成します。 このストアドプロシージャは、サブスクライバー側のサブスクリプションデータベースで実行されます。  
  
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
`[ @artid = ] 'artid'`アーティクル ID の名前を指定します。 *artid*は**int**,、既定値はありません。  
  
`[ @article = ] 'article'`スクリプトを記述するアーティクルの名前を指定します。 *アーティクル*は**sysname**で、既定値はありません  
  
`[ @publisher = ] 'publisher'`パブリッシャーサーバーの名前を指定します。 *publisher*は**sysname**で、既定値はありません。  
  
`[ @publisher_db = ] 'publisher_db'`パブリッシャーデータベースの名前を指定します。 *publisher_db*は**sysname**であり、既定値はありません。  
  
`[ @publication = ] 'publication'`スクリプトを記述するパブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。  
  
`[ @dest_table = ] _'dest_table'`コピー先テーブルの名前を指定します。 *dest_table*は**sysname**であり、既定値はありません。  
  
 [** @owner =** ] **'**_owner_**'**  
 サブスクリプションの所有者を示します。 *owner*は**sysname**,、既定値はありません。  
  
`[ @cft_table = ] 'cft_table'`このアーティクルのキュー更新の競合テーブルの名前。 *cft_table*は**sysname**であり、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_addqueued_artinfo**は、サブスクリプションの初期化の一部としてディストリビューションエージェントによって使用されます。 このストアド プロシージャは、ユーザーが頻繁に実行するものではありません。ただし、サブスクリプションを手動で設定する場合に利用できるストアド プロシージャです。  
  
 **sp_addqueued_artinfo**ではなく[sp_script_synctran_commands](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)します。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_addqueued_artinfo**を実行できるのは、固定サーバーロール**sysadmin**または固定データベースロール**db_owner**のメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [トランザクションレプリケーションの更新可能なサブスクリプション](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md)   
 [sp_script_synctran_commands &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-script-synctran-commands-transact-sql.md)   
 [MSsubscription_articles &#40;Transact-sql&#41;](../../relational-databases/system-tables/mssubscription-articles-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
