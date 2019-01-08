---
title: sp_dropmergesubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_dropmergesubscription_TSQL
- sp_dropmergesubscription
helpviewer_keywords:
- sp_dropmergesubscription
ms.assetid: 34244ae6-bd98-4a6a-bbd3-85f50edfcdc0
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: acb16727506952146ace1383c8d36808d7c22a73
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52791504"
---
# <a name="spdropmergesubscription-transact-sql"></a>sp_dropmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ パブリケーションのサブスクリプションおよびこれと関連するマージ エージェントを削除します。 このストアド プロシージャは、パブリッシャー側でパブリケーション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_dropmergesubscription [ [ @publication= ] 'publication' ]   
    [ , [ @subscriber= ] 'subscriber'    
    [ , [ @subscriber_db= ] 'subscriber_db' ]   
    [ , [ @subscription_type= ] 'subscription_type' ]   
    [ , [ @ignore_distributor = ] ignore_distributor ]   
    [ , [ @reserved = ] reserved ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publication=** ] **'***パブリケーション***'**  
 パブリケーション名を指定します。 *パブリケーション*は**sysname**、既定値は NULL です。 パブリケーションが存在し、識別子の規則に従っている必要があります。  
  
 [  **@subscriber=**] **'***サブスクライバー***'**  
 サブスクライバーの名前です。 *サブスクライバー*は**sysname**、既定値は NULL です。  
  
 [  **@subscriber_db=** ] **'***@subscriber_db***'**  
 サブスクリプション データベースの名前です。 *subscription_database*は**sysname**、既定値は NULL です。  
  
 [  **@subscription_type=** ] **'***subscription_type***'**  
 サブスクリプションの種類を指定します。 *subscription_type*は**nvarchar (15)**、これらの値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**すべての**|プッシュ サブスクリプション、プル サブスクリプション、および匿名サブスクリプションです。|  
|**匿名**|匿名サブスクリプションです。|  
|**プッシュ**|プッシュ サブスクリプションです。|  
|**プル**|プル サブスクリプションです。|  
|**どちらも**(既定値)|プッシュ サブスクリプションおよびプル サブスクリプションです。|  
  
 [  **@ignore_distributor =** ] *ignore_distributor*  
 ディストリビューターに接続せずに、このストアド プロシージャを実行するかどうかを指定します。 *ignore_distributor*は**ビット**、既定値は**0**します。 このパラメーターは、ディストリビューターでクリーンアップ タスクを実行せずにサブスクリプションを削除するために使用できます。 また、ディストリビューターを再インストールする必要がある場合も便利です。  
  
 [  **@reserved=** ]*予約済み*  
 将来の使用に備えて予約されています。 *予約済み*は**ビット**、既定値は**0**します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_dropmergesubscription**はマージ レプリケーションで使用します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_dropmergesubscription](../../relational-databases/replication/codesnippet/tsql/sp-dropmergesubscription_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_dropmergesubscription**します。  
  
## <a name="see-also"></a>参照  
 [プッシュ サブスクリプションを削除します。](../../relational-databases/replication/delete-a-push-subscription.md)   
 [プル サブスクリプションを削除します。](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addmergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_helpmergesubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergesubscription-transact-sql.md)  
  
  
