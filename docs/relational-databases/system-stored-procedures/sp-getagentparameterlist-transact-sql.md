---
title: sp_getagentparameterlist (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_getagentparameterlist
- sp_getagentparameterlist_TSQL
helpviewer_keywords:
- sp_getagentparameterlist
ms.assetid: 50d3d3c1-b9a1-417c-bad4-674089c9c60d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2d80aedbe2503c4ab11fd894d44e8e37f2167daf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124010"
---
# <a name="sp_getagentparameterlist-transact-sql"></a>sp_getagentparameterlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定されたエージェント タイプのエージェント プロファイルに設定可能なすべてのレプリケーション エージェント パラメーターの一覧を返します。 このストアドプロシージャは、任意のデータベース上でエージェントが実行されているディストリビューターで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_getagentparameterlist [ @agent_type = ] 'agent_type'  
```  
  
## <a name="arguments"></a>引数  
`[ @agent_type = ] 'agent_type'`パラメーターを追加するレプリケーションエージェントを指定します。 *agent_type*は**int**で、次のいずれかの値を指定できます。  
  
|Value|エージェント|  
|-----------|-----------|  
|**1**|スナップショット|  
|**2**|ログリーダー|  
|**番**|Distribution|  
|**4**|Merge|  
|**9**|キュー リーダー|  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="remarks"></a>解説  
  
## <a name="permissions"></a>アクセス許可  
 **Sp_getagentparameter**を実行できるのは、 **sysadmin**固定サーバーロールのメンバーだけです。  
  
## <a name="see-also"></a>参照  
 [sp_add_agent_parameter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_add_agent_profile &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-profile-transact-sql.md)   
 [sp_drop_agent_parameter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-drop-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [レプリケーションエージェントプロファイル](../../relational-databases/replication/agents/replication-agent-profiles.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
