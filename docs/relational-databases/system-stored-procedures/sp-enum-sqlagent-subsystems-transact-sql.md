---
title: sp_enum_sqlagent_subsystems (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_enum_sqlagent_subsystems
- sp_enum_sqlagent_subsystems_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_enum_sqlagent_subsystems
ms.assetid: 019a3c9d-bac3-495b-a70a-2c19f1d2e20e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 963cbcea93091eb48b8c73214ee3bc509f118e67
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68124673"
---
# <a name="sp_enum_sqlagent_subsystems-transact-sql"></a>sp_enum_sqlagent_subsystems (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  エージェントサブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システムの一覧を表示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_enum_sqlagent_subsystems  
```  
  
## <a name="arguments"></a>引数  
 なし  
  
## <a name="return-code-values"></a>リターン コードの値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**サブ**|**nvarchar (40)**|サブシステムの名前。|  
|**記述**|**nvarchar(512)**|サブシステムの説明。|  
|**subsystem_dll**|**nvarchar (510)**|サブシステムを格納している DLL モジュール|  
|**agent_exe**|**nvarchar (510)**|サブシステムによって使用される実行可能モジュール。|  
|**start_entry_point**|**nvarchar (30)**|ジョブステップの実行中に SQL Server エージェント呼び出しを行う手順。|  
|**event_entry_point**|**nvarchar (30)**|ジョブステップの実行中に SQL Server エージェント呼び出しを行う手順。|  
|**stop_entry_point**|**nvarchar (30)**|ジョブステップの実行中に SQL Server エージェント呼び出しを行う手順。|  
|**max_worker_threads**|**int**|このサブシステムに[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]対してエージェントが開始するスレッドの最大数。|  
|**subsystem_id**|**int**|サブシステムの識別子|  
  
## <a name="remarks"></a>解説  
 この手順では、インスタンスで使用可能なサブシステムの一覧を示します。  
  
## <a name="permissions"></a>アクセス許可  
 既定では、 **sysadmin**固定サーバーロールのメンバーは、このストアドプロシージャを実行できます。 それ以外のユーザーには、 **msdb** データベースの **SQLAgentOperatorRole** 固定サーバー ロールを与える必要があります。  
  
 **Sqlagentoperatorrole**の詳細については、「 [SQL Server エージェント固定データベースロール](../../ssms/agent/sql-server-agent-fixed-database-roles.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [SQL Server エージェントセキュリティを実装する](../../ssms/agent/implement-sql-server-agent-security.md)   
 [sp_add_jobstep &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql.md)  
  
  
