---
title: sp_droppublication (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_droppublication_TSQL
- sp_droppublication
helpviewer_keywords:
- sp_droppublication
ms.assetid: b52b37e6-4fec-40cf-abba-7dce4ff395fd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0b8cda79919c318b6bee5817731e4ca83aea17aa
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58529754"
---
# <a name="spdroppublication-transact-sql"></a>sp_droppublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションおよびこれと関連するスナップショット エージェントを削除します。 パブリケーションを削除する前に、すべてのサブスクリプションを削除する必要があります。 パブリケーションのアーティクルが自動的に削除されます。 このストアド プロシージャは、パブリッシャー、パブリケーション データベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_droppublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'` 削除するパブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。 場合**すべて**を指定すると、すべてのパブリケーションがサブスクリプションのあるものを除き、パブリケーション データベースから削除されます。  
  
`[ @ignore_distributor = ] ignore_distributor` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_droppublication**スナップショット レプリケーションおよびトランザクション レプリケーションで使用されます。  
  
 **sp_droppublication**再帰的には、パブリケーションに関連付けられているすべてのアーティクルを削除し、後、パブリケーション自体が削除されます。 1 つまたは複数のサブスクリプションがある場合、パブリケーションを削除できません。 サブスクリプションを削除する方法については、[Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md)と[Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md)を参照してください。  
  
 実行**sp_droppublication**パブリケーションを削除するオブジェクトは削除されませんパブリッシュされたパブリケーション データベースまたはサブスクリプション データベースから対応するオブジェクト。 ドロップを使用して\<オブジェクト > に必要な場合は、これらのオブジェクトを手動で削除します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_droppublication**します。  
  
## <a name="examples"></a>使用例  
 [!code-sql[HowTo#sp_droppublication](../../relational-databases/replication/codesnippet/tsql/sp-droppublication-trans_1.sql)]  
  
## <a name="see-also"></a>参照  
 [パブリケーションを削除します](../../relational-databases/replication/publish/delete-a-publication.md)   
 [sp_addpublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
