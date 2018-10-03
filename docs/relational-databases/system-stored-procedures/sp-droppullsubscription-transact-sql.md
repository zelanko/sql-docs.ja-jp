---
title: sp_droppullsubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_droppullsubscription
- sp_droppullsubscription_TSQL
helpviewer_keywords:
- sp_droppullsubscription
ms.assetid: 7352d94a-f8f2-42ea-aaf1-d08c3b5a0e76
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 35b050798f9be9255b9ee35fdc0a8d378f03ecf5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47733782"
---
# <a name="spdroppullsubscription-transact-sql"></a>sp_droppullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  サブスクライバーの現在のデータベースでサブスクリプションを削除します。 このストアド プロシージャは、サブスクライバー側でプル サブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_droppullsubscription [ @publisher= ] 'publisher'  
        , [ @publisher_db= ] 'publisher_db'  
        , [ @publication= ] 'publication'  
    [ , [ @reserved= ] reserved ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@publisher=** ] **'***パブリッシャー***'**  
 リモート サーバー名を指定します。 *パブリッシャー*は**sysname**、既定値はありません。 場合**すべて**、サブスクリプションがすべてのパブリッシャーで削除されます。  
  
 [  **@publisher_db=** ] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値はありません。 **すべて**はすべてのパブリッシャー データベースを意味します。  
  
 [  **@publication=** ] **'***パブリケーション***'**  
 パブリケーション名を指定します。 *パブリケーション*は**sysname**、既定値はありません。 場合**すべて**、すべてのパブリケーションに対するサブスクリプションが削除されます。  
  
 [  **@reserved=** ]*予約済み*  
 [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_droppullsubscription**スナップショット レプリケーションおよびトランザクション レプリケーションで使用されます。  
  
 **sp_droppullsubscription** 、対応する行を削除、 [MSreplication_subscriptions &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md)テーブルと、サブスクライバーで対応するディストリビューター エージェントです。 行が残っていない場合[MSreplication_subscriptions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-tables/msreplication-subscriptions-transact-sql.md)、テーブルを削除します。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_droptranpullsubscription](../../relational-databases/replication/codesnippet/tsql/sp-droppullsubscription-_1.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたはプル サブスクリプションを作成したユーザーが実行できる**sp_droppullsubscription**します。 **Db_owner**固定データベース ロールを実行することがのみ**sp_droppullsubscription**プル サブスクリプションを作成したユーザーがこのロールに属している場合。  
  
## <a name="see-also"></a>参照  
 [プル サブスクリプションを削除します。](../../relational-databases/replication/delete-a-pull-subscription.md)   
 [sp_addpullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-transact-sql.md)   
 [sp_change_subscription_properties &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-subscription-properties-transact-sql.md)   
 [sp_helppullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helppullsubscription-transact-sql.md)   
 [sp_dropsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscription-transact-sql.md)  
  
  
