---
title: sp_addmergepullsubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepullsubscription_TSQL
- sp_addmergepullsubscription
helpviewer_keywords:
- sp_addmergepullsubscription
ms.assetid: d63909a0-8ea7-4734-9ce8-8204d936a3e4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4e6e3a2ddd7c046051b0d7f89097c7c0a075ca6f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47659016"
---
# <a name="spaddmergepullsubscription-transact-sql"></a>sp_addmergepullsubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  プル サブスクリプションをマージ パブリケーションに追加します。 このストアド プロシージャは、サブスクライバー側でサブスクリプション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_addmergepullsubscription [ @publication= ] 'publication'   
    [ , [ @publisher= ] 'publisher' ]   
    [ , [ @publisher_db = ] 'publisher_db' ]   
    [ , [ @subscriber_type= ] 'subscriber_type' ]   
    [ , [ @subscription_priority= ] subscription_priority ]   
    [ , [ @sync_type= ] 'sync_type' ]   
    [ , [ @description= ] 'description' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@publication=**] **'***publication***'**  
 パブリケーションの名前です。 *パブリケーション*は**sysname**、既定値はありません。  
  
 [ **@publisher=**] **'***publisher***'**  
 パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値は、ローカル サーバー名。 パブリッシャーは有効なサーバーであることが必要です。  
  
 [  **@publisher_db =**] **'***publisher_db***'**  
 パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値は NULL です。  
  
 [  **@subscriber_type=**] **'***subscriber_type***'**  
 サブスクライバーの種類を指定します。 *subscriber_type*は**nvarchar (15)**、でき、**グローバル**、**ローカル**または**匿名**します。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]と以降のバージョンでは、ローカル サブスクリプションはクライアント サブスクリプションとして参照し、グローバル サブスクリプションはサーバー サブスクリプションとして参照します。  
  
 [  **@subscription_priority=**] *subscription_priority*  
 サブスクリプションの優先度。 *subscription_priority*は**実際**、既定値は NULL です。 ローカル サブスクリプションと匿名サブスクリプションを優先度は**0.0**します。 優先度は、競合の検出時、既定の競合回避モジュールによって実行される操作を選択する場合に使用されます。 グローバル サブスクライバーの場合、サブスクリプション優先度をパブリッシャーの優先度である 100 未満にする必要があります。  
  
 [  **@sync_type=**] **'***sync_type***'**  
 サブスクリプションの同期の種類を指定します。 *sync_type*は**nvarchar (15)**、既定値は**自動**します。 **自動**または**none**します。 場合**自動**スキーマと初期データのパブリッシュされたテーブルの最初に転送されます、サブスクライバー。 場合**none**サブスクライバーが既にスキーマと初期データのパブリッシュされたテーブルのことが前提とします。 システム テーブルとデータは常に転送されます。  
  
> [!NOTE]  
>  値を指定しないで**none**します。  
  
 [  **@description=**] **'***説明***'**  
 対象となるプル サブスクリプションの短い説明を指定します。 *説明*は**nvarchar (255)**、既定値は NULL です。 レプリケーション モニターでこの値が表示されます、**フレンドリ名**列は、監視されるパブリケーションのサブスクリプションの並べ替えに使用できます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_addmergepullsubscription**マージ レプリケーションに使用します。  
  
 使用して場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、サブスクリプションを同期するエージェント、 [sp_addmergepullsubscription_agent](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)エージェントと、パブリケーションと同期するジョブを作成するサブスクライバーでストアド プロシージャを実行する必要があります。  
  
## <a name="example"></a>例  
 [!code-sql[HowTo#sp_addmergepullsubscriptionagent](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_1.sql)]  
  
 [!code-sql[HowTo#sp_addmergepullsub_websync_anon](../../relational-databases/replication/codesnippet/tsql/sp-addmergepullsubscript_0_2.sql)]  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールまたは**db_owner**固定データベース ロールが実行できる**sp_addmergepullsubscription**します。  
  
## <a name="see-also"></a>参照  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Subscribe to Publications](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)   
 [sp_changemergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
