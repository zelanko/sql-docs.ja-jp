---
title: sp_help_agent_parameter (TRANSACT-SQL) |Microsoft ドキュメント
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
- sp_help_agent_parameter
- sp_help_agent_parameter_TSQL
helpviewer_keywords:
- sp_help_agent_parameter
ms.assetid: 8fb4a9c3-19af-4a34-8004-572729ba3d15
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f158146f98334b82cbfe3c92a061ee927c57c551
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpagentparameter-transact-sql"></a>sp_help_agent_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  プロファイルのすべてのパラメーターを返します、 [MSagent_parameters &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msagent-parameters-transact-sql.md)システム テーブル。 このストアド プロシージャは、エージェントが動作しているディストリビューター側で任意のデータベースについて実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_agent_parameter [ [ @profile_id = ] profile_id ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@profile_id=**] *profile_id*  
 プロファイルの id、 [MSagent_parameters &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-tables/msagent-parameters-transact-sql.md)テーブル。 *profile_id*は**int**、既定値は**-1**、すべてのパラメーターが返されます。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|エージェント プロファイルの ID です。|  
|**parameter_name**|**sysname**|パラメーターの名前です。|  
|**value**|**nvarchar (255)**|パラメーターの値です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
 **sp_help_agent_parameter**はあらゆる種類のレプリケーションで使用します。  
  
## <a name="permissions"></a>権限  
 メンバーにのみ、 **sysadmin**固定サーバー ロールまたは**replmonitor**固定データベース ロールが実行できる**sp_help_agent_parameter**です。  
  
## <a name="see-also"></a>参照  
 [レプリケーション エージェント プロファイルの操作](../../relational-databases/replication/agents/work-with-replication-agent-profiles.md)   
 [sp_add_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_drop_agent_parameter &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
