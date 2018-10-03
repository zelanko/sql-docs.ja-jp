---
title: sp_add_agent_profile (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- sp_add_agent_profile
- sp_add_agent_profile_TSQL
helpviewer_keywords:
- sp_add_agent_profile
ms.assetid: 5c246a33-2c21-4a77-9c2a-a2c9f0c5dda1
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: b5c6b2c03ff9956a58bf7da8426c87b692d5f879
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47670440"
---
# <a name="spaddagentprofile-transact-sql"></a>sp_add_agent_profile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケーション エージェントの新しいプロファイルを作成します。 このストアド プロシージャは、ディストリビューター側で任意のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_agent_profile [ [ @profile_id= ] profile_id OUTPUT ]  
        , [ @profile_name= ] 'profile_name'   
        , [ @agent_type= ] 'agent_type' ]   
    [ , [ @profile_type= ] profile_type ]  
    [ , [ @description= ] 'description' ]  
    [ , [ @default= ] default ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@profile_id=** ] *profile_id*  
 新たに挿入されたプロファイルに関連付けられている ID を指定します。 *profile_id*は**int**は省略可能な出力パラメーター。 指定した場合、値が新しいプロファイル ID として設定されます。  
  
 [ **@profile_name=** ] **'***profile_name***'**  
 プロファイルの名前を指定します。 *profile_name*は**sysname**、既定値はありません。  
  
 [ **@agent_type=** ] **'***agent_type***'**  
 レプリケーション エージェントの種類です。 *agent_type*は**int**, で、既定値はありませんはこれらの値のいずれかを指定します。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|スナップショット エージェント|  
|**2**|ログ リーダー エージェント (Log Reader Agent)|  
|**3**|ディストリビューション エージェント|  
|**4**|[マージ エージェント]|  
|**9**|キュー リーダー エージェント (Queue Reader Agent)|  
  
 [  **@profile_type=** ] *@profile_type*  
 プロファイルの種類です。*@profile_type*は**int**、既定値は**1**します。  
  
 **0**システム プロファイルを示します。 **1**カスタム プロファイルを示します。 このストアド プロシージャを使用してカスタム プロファイルだけを作成することができます。したがって、唯一の有効な値は**1**します。 のみ[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム プロファイルを作成します。  
  
 [  **@description=** ] **'***説明***'**  
 プロファイルの説明を指定します。 *説明*は**nvarchar (3000)**、既定値はありません。  
  
 [  **@default=** ]*既定*  
 既定のプロファイルかどうかを示します*agent_type * *。* *既定*は**ビット**、既定値は**0**します。 **1**追加されるプロファイルがで指定されたエージェントの新しい既定のプロファイルになることを示します*agent_type*します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_add_agent_profile**はスナップショット レプリケーション、トランザクション レプリケーション、およびマージ レプリケーションで使用します。  
  
 カスタム エージェント プロファイルは、既定のエージェント パラメーター値を使用して追加されます。 使用[sp_change_agent_parameter &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md)をこれらの既定値を変更または[sp_add_agent_parameter &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)追加パラメーターを追加します。  
  
 ときに**sp_add_agent_profile**が実行すると、行を追加、新しいカスタム プロファイルでの[MSagent_profiles &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msagent-profiles-transact-sql.md)テーブルとの関連付けられている既定のパラメータープロファイルに追加されて、 [MSagent_parameters &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msagent-parameters-transact-sql.md)テーブル。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_add_agent_profile**します。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェント プロファイルの操作](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [レプリケーション エージェント プロファイル](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [sp_add_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_change_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-parameter-transact-sql.md)   
 [sp_change_agent_profile &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [sp_drop_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_drop_agent_profile &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)   
 [sp_help_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [sp_help_agent_profile &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)  
  
  
