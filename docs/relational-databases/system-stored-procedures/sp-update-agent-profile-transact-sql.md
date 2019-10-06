---
title: sp_update_agent_profile (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_update_agent_profile_TSQL
- sp_update_agent_profile
helpviewer_keywords:
- sp_update_agent_profile
ms.assetid: cc81f227-0df3-4151-bb4d-4f45ea997b71
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e90136d319ed0f04766bfec503126999bb73dd0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68061219"
---
# <a name="spupdateagentprofile-transact-sql"></a>sp_update_agent_profile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  レプリケーション エージェントにより使用されるプロファイルを更新します。 このストアド プロシージャは、ディストリビューター側でディストリビューション データベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_update_agent_profile [@agent_type=] agent_type, [ @agent_id= ] agent_id, [ @profile_id= ] profile_id  
```  
  
## <a name="arguments"></a>引数  
 [ **\@agent_type=** ] **'***agent_type***'**  
 エージェントの種類を指定します。 *agent_type*は**int**, で、既定値はありませんはこれらの値のいずれかを指定します。  
  
|値|説明|  
|-----------|-----------------|  
|**1**|スナップショット エージェント。|  
|**2**|ログ リーダー エージェント|  
|**3**|ディストリビューション エージェント。|  
|**4**|マージ エージェントです。|  
|**9**|キュー リーダー エージェント|  
  
 [ **\@agent_id=** ] *agent_id*  
 エージェントの ID を指定します。 *agent_id*は**int**、既定値はありません。  
  
 [ **\@profile_id=** ] *profile_id*  
 エージェントで使用する必要のあるプロファイルの ID を指定します。 *profile_id*は**int**、既定値はありません。 をエージェントごとに定義されているプロファイルの一覧を表示するには使用[sp_help_agent_profile &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)します。 システム プロファイルの詳細については、次を参照してください。[レプリケーション エージェント プロファイル](../../relational-databases/replication/agents/replication-agent-profiles.md)します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_update_agent_profile**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_update_agent_profile**します。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェント プロファイル](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [sp_add_agent_profile &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md)   
 [sp_change_agent_profile &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-change-agent-profile-transact-sql.md)   
 [sp_drop_agent_profile &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-profile-transact-sql.md)   
 [sp_help_agent_profile &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-profile-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
