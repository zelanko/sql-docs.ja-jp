---
title: sp_droppublication (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/17/2017
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
- sp_droppublication_TSQL
- sp_droppublication
helpviewer_keywords:
- sp_droppublication
ms.assetid: b52b37e6-4fec-40cf-abba-7dce4ff395fd
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 94cd07570e41a10520b05c16df45068e186fe179
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spdroppublication-transact-sql"></a>sp_droppublication (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  パブリケーションおよびこれと関連するスナップショット エージェントを削除します。 パブリケーションを削除する前に、すべてのサブスクリプションを削除しておく必要があります。 パブリケーション内のアーティクルは自動的に削除されます。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_droppublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=** ] **'***パブリケーション***'**  
 削除するパブリケーションの名前を指定します。 *パブリケーション*は**sysname**、既定値はありません。 場合**すべて**が指定されているすべてのパブリケーションがサブスクリプションのあるものを除き、パブリケーション データベースから削除されます。  
  
 [  **@ignore_distributor =** ] *ignore_distributor*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_droppublication**はスナップショット レプリケーションおよびトランザクション レプリケーションで使用します。  
  
 **sp_droppublication**再帰的には、パブリケーションに関連付けられているすべてのアーティクルを削除し、し、パブリケーションそのものを削除します。 1 つでもサブスクリプションがあると、パブリケーションを削除することはできません。 サブスクリプションを削除する方法については、次を参照してください。 [Delete a Push Subscription](../../relational-databases/replication/delete-a-push-subscription.md)と[Delete a Pull Subscription](../../relational-databases/replication/delete-a-pull-subscription.md)です。  
  
 実行する**sp_droppublication**パブリケーションを削除するオブジェクトは削除されませんパブリッシュされたパブリケーション データベースまたはサブスクリプション データベースから対応するオブジェクトからです。 ドロップを使用して\<オブジェクト > 必要な場合に、これらのオブジェクトを手動で削除します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_droppublication**です。  
  
## <a name="examples"></a>使用例  
 [!code-sql[HowTo#sp_droppublication](../../relational-databases/replication/codesnippet/tsql/sp-droppublication-trans_1.sql)]  
  
## <a name="see-also"></a>参照  
 [パブリケーションを削除します](../../relational-databases/replication/publish/delete-a-publication.md)   
 [sp_addpublication &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
