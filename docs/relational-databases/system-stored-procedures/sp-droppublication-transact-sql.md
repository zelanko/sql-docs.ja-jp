---
title: sp_droppublication (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 3ef56f46696a2cb145804105d4d5f22fded6fe1f
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82830014"
---
# <a name="sp_droppublication-transact-sql"></a>sp_droppublication (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  パブリケーションおよびこれと関連するスナップショット エージェントを削除します。 パブリケーションを削除する前に、すべてのサブスクリプションを削除する必要があります。 パブリケーション内のアーティクルは自動的に削除されます。 このストアドプロシージャは、パブリッシャー側でパブリケーションデータベースに対して実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_droppublication [ @publication= ] 'publication'   
    [ , [ @ignore_distributor = ] ignore_distributor ]  
```  
  
## <a name="arguments"></a>引数  
`[ @publication = ] 'publication'`削除するパブリケーションの名前を指定します。 *publication*は**sysname**,、既定値はありません。 **All**を指定した場合は、サブスクリプションを持つパブリケーションを除き、すべてのパブリケーションがパブリケーションデータベースから削除されます。  
  
`[ @ignore_distributor = ] ignore_distributor` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_droppublication**は、スナップショットレプリケーションおよびトランザクションレプリケーションで使用します。  
  
 **sp_droppublication**は、パブリケーションに関連付けられているすべてのアーティクルを再帰的に削除してから、パブリケーション自体を削除します。 パブリケーションに1つ以上のサブスクリプションがある場合は、パブリケーションを削除できません。 サブスクリプションを削除する方法の詳細については、「 [delete a Push subscription](../../relational-databases/replication/delete-a-push-subscription.md) 」および「 [Delete a Pull subscription](../../relational-databases/replication/delete-a-pull-subscription.md)」を参照してください。  
  
 パブリケーションを削除するために**sp_droppublication**を実行しても、パブリッシュされたオブジェクトはパブリケーションデータベースから削除されず、対応するオブジェクトはサブスクリプションデータベースから削除されません。 必要に応じて \< 、DROP object> を使用してこれらのオブジェクトを手動で削除します。  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_droppublication**を実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="examples"></a>例  
 [!code-sql[HowTo#sp_droppublication](../../relational-databases/replication/codesnippet/tsql/sp-droppublication-trans_1.sql)]  
  
## <a name="see-also"></a>参照  
 [パブリケーションを削除する](../../relational-databases/replication/publish/delete-a-publication.md)   
 [sp_addpublication &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-transact-sql.md)   
 [sp_changepublication &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)   
 [sp_helppublication &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-helppublication-transact-sql.md)   
 [レプリケーション ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  
