---
title: sp_getagentparameterlist (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- sp_getagentparameterlist
- sp_getagentparameterlist_TSQL
helpviewer_keywords:
- sp_getagentparameterlist
ms.assetid: 50d3d3c1-b9a1-417c-bad4-674089c9c60d
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: ff1a352f8580e85e3607a0259080841c1997e524
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spgetagentparameterlist-transact-sql"></a>sp_getagentparameterlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたエージェント タイプのエージェント プロファイルに設定可能なすべてのレプリケーション エージェント パラメーターの一覧を返します。 このストアド プロシージャは、エージェントが動作しているディストリビューター側で任意のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_getagentparameterlist [ @agent_type = ] 'agent_type'  
```  
  
## <a name="arguments"></a>引数  
 [  **@agent_type =** ] **'***agent_type***'**  
 パラメーターを追加するレプリケーション エージェントを指定します。 *agent_type*は**int**、これらの値のいずれかを指定できます。  
  
|値|エージェント|  
|-----------|-----------|  
|**1**|スナップショット|  
|**2**|ログ リーダー|  
|**3**|Distribution|  
|**4**|Merge|  
|**9**|キュー リーダー|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_getagentparameter**です。  
  
## <a name="see-also"></a>参照  
 [sp_add_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_add_agent_profile &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md)   
 [sp_drop_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [レプリケーション エージェント プロファイル](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
