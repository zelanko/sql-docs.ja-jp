---
title: sp_addmergepullsubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_addmergepullsubscription_TSQL
- sp_addmergepullsubscription
helpviewer_keywords:
- sp_addmergepullsubscription
ms.assetid: d63909a0-8ea7-4734-9ce8-8204d936a3e4
author: stevestein
ms.author: sstein
ms.openlocfilehash: ef860a30ba5994e25a9d532445af0ec2c39f9e1c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68042731"
---
# <a name="spaddmergepullsubscription-transact-sql"></a>sp_addmergepullsubscription (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  マージ パブリケーションに対するプル サブスクリプションを追加します。 このストアド プロシージャは、サブスクライバーのサブスクリプション データベースで実行されます。  
  
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
`[ @publication = ] 'publication'` パブリケーションの名前です。 *パブリケーション* は **sysname** 、既定値はありません。  
  
`[ @publisher = ] 'publisher'` パブリッシャーの名前です。 *パブリッシャー*は**sysname**、既定値は、ローカル サーバー名。 パブリッシャーは、有効なサーバーである必要があります。  
  
`[ @publisher_db = ] 'publisher_db'` パブリッシャー データベースの名前です。 *publisher_db*は**sysname**、既定値は NULL です。  
  
`[ @subscriber_type = ] 'subscriber_type'` サブスクライバーの種類です。 *subscriber_type*は**nvarchar (15)** 、でき、**グローバル**、**ローカル**または**匿名**します。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]と以降のバージョンでは、ローカル サブスクリプションはクライアント サブスクリプションとして参照し、グローバル サブスクリプションはサーバー サブスクリプションとして参照します。  
  
`[ @subscription_priority = ] subscription_priority` サブスクリプションの優先順位です。 *subscription_priority*は**実際**、既定値は NULL です。 ローカル サブスクリプションと匿名サブスクリプションを優先度は**0.0**します。 優先順位は、競合が検出された場合、優勝者を選択する既定の競合回避モジュールによって使用されます。 グローバル サブスクライバーは、サブスクリプションの優先度必要があります 100 よりも小さい、これは、パブリッシャーの優先順位です。  
  
`[ @sync_type = ] 'sync_type'` サブスクリプションの同期型です。 *sync_type*は**nvarchar (15)** 、既定値は**自動**します。 **自動**または**none**します。 場合**自動**スキーマと初期データのパブリッシュされたテーブルの最初に転送されます、サブスクライバー。 場合**none**サブスクライバーが既にスキーマと初期データのパブリッシュされたテーブルのことが前提とします。 システム テーブルとデータは常に転送されます。  
  
> [!NOTE]  
>  値を指定しないで**none**します。  
  
`[ @description = ] 'description'` このプル サブスクリプションの簡単な説明です。 *説明*は**nvarchar (255)** 、既定値は NULL です。 レプリケーション モニターでこの値が表示されます、**フレンドリ名**列は、監視されるパブリケーションのサブスクリプションの並べ替えに使用できます。  
  
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
  
## <a name="see-also"></a>関連項目  
 [プル サブスクリプションの作成](../../relational-databases/replication/create-a-pull-subscription.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)   
 [sp_addmergepullsubscription_agent &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md)   
 [sp_changemergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergepullsubscription-transact-sql.md)   
 [sp_dropmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepullsubscription-transact-sql.md)   
 [sp_helpmergepullsubscription &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)   
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql.md)  
  
  
