---
title: "MSsnapshot_agents (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MSsnapshot_agents
- MSsnapshot_agents_TSQL
dev_langs: TSQL
helpviewer_keywords: MSsnapshot_agents system table
ms.assetid: aeae0a2e-4c21-4c45-be65-1e426fa52bdd
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 057db5ff4dbb7e9a9cfcfd5f36ae391f51160544
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mssnapshotagents-transact-sql"></a>MSsnapshot_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsnapshot_agents**テーブルは、ローカル ディストリビューターに関連付けられたスナップショット エージェントごとの 1 行を格納します。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|スナップショット エージェントの ID。|  
|**name**|**nvarchar (100)**|スナップショット エージェントの名前。|  
|**publisher_id などがあります。**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前。|  
|**パブリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**publication_type**|**int**|パブリケーションの種類。<br /><br /> **0** = トランザクションです。<br /><br /> **1**スナップショットを = です。<br /><br /> **2**マージを = です。|  
|**local_job**|**bit**|ローカル ディストリビューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブがあるかどうかを示します。|  
|**job_id**|**binary (16)**|ジョブの識別番号。|  
|**profile_id**|**int**|構成の ID、 [MSagent_profiles (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/msagent-profiles-transact-sql.md)テーブル。|  
|**dynamic_filter_login**|**sysname**|評価するために使用される値、 [SUSER_SNAME (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/suser-sname-transact-sql.md)パーティションを定義するパラメーター化されたフィルター内の関数。 この列はパーティション スナップショットに使用されます。|  
|**dynamic_filter_hostname**|**sysname**|評価するために使用される値、 [HOST_NAME &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/host-name-transact-sql.md)パーティションを定義するパラメーター化されたフィルター内の関数。 この列はパーティション スナップショットに使用されます。|  
|**publisher_security_mode**|**smallint**|パブリッシャーに接続するときにエージェントで使用されるセキュリティ モード。次のいずれかの値をとります。<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証です。|  
|**publisher_login**|**sysname**|パブリッシャーに接続するときに使用されるログイン。|  
|**publisher_password**|**nvarchar (524)**|パブリッシャーに接続するときに使用されるパスワードの暗号化された値。|  
|**job_step_uid**|**uniqueidentifier**|エージェントが起動される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップの一意な ID|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
