---
title: MSsnapshot_agents (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsnapshot_agents
- MSsnapshot_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshot_agents system table
ms.assetid: aeae0a2e-4c21-4c45-be65-1e426fa52bdd
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2d57700abecccf3dae55289b49d4fd6c1af3e537
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68079965"
---
# <a name="mssnapshot_agents-transact-sql"></a>MSsnapshot_agents (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsnapshot_agents**テーブルには、ローカルディストリビューターに関連付けられているスナップショットエージェントごとに1つの行が含まれています。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**番号**|**int**|スナップショットエージェントの ID。|  
|**name**|**nvarchar (100)**|スナップショット エージェントの名前。|  
|**publisher_id**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャーデータベースの名前。|  
|**レプリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**publication_type**|**int**|パブリケーションの種類です。<br /><br /> **0** = トランザクション。<br /><br /> **1** = スナップショット。<br /><br /> **2** = Merge。|  
|**local_job**|**bit**|ローカル ディストリビューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブがあるかどうかを示します。|  
|**job_id**|**バイナリ (16)**|ジョブの識別番号を指定します。|  
|**profile_id**|**int**|[MSagent_profiles &#40;transact-sql&#41;](../../relational-databases/system-tables/msagent-profiles-transact-sql.md)テーブルの構成 ID。|  
|**dynamic_filter_login**|**sysname**|パーティションを定義するパラメーター化されたフィルターで[SUSER_SNAME &#40;transact-sql&#41;](../../t-sql/functions/suser-sname-transact-sql.md)関数を評価するために使用される値。 この列は、パーティションスナップショットに使用されます。|  
|**dynamic_filter_hostname**|**sysname**|パーティションを定義するパラメーター化されたフィルターで[HOST_NAME &#40;transact-sql&#41;](../../t-sql/functions/host-name-transact-sql.md)関数を評価するために使用される値。 この列は、パーティションスナップショットに使用されます。|  
|**publisher_security_mode**|**smallint**|パブリッシャーに接続するときにエージェントによって使用されるセキュリティモード。次のいずれかになります。<br /><br /> **** =  0[!INCLUDE[msCoName](../../includes/msconame-md.md)]認証[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> **** =  1[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証。|  
|**publisher_login**|**sysname**|パブリッシャーに接続するときに使用されるログインです。|  
|**publisher_password**|**nvarchar (524)**|パブリッシャーに接続するときに使用されるパスワードの暗号化された値。|  
|**job_step_uid**|**UNIQUEIDENTIFIER**|エージェントが起動される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップの一意な ID|  
|**job_login**|**sysname**||  
|**job_password**|**nvarchar (524)**||  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
