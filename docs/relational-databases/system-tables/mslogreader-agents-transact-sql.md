---
title: "MSlogreader_agents (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSlogreader_agents_TSQL
- MSlogreader_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_agents system table
ms.assetid: 8baa3c5a-cb40-42d0-b966-00e6d55368e8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a8cb5ac9e4393bbab70eac9128df2e186781bcec
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mslogreaderagents-transact-sql"></a>MSlogreader_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSlogreader_agents**テーブルには、ローカル ディストリビューターで実行されているログ リーダー エージェントごとに 1 つの行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|ログ リーダー エージェントの ID です。|  
|**name**|**nvarchar (100)**|ログ リーダー エージェントの名前です。|  
|**publisher_id などがあります。**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前。|  
|**パブリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**local_job**|**bit**|ローカル ディストリビューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブがあるかどうかを示します。|  
|**job_id**|**binary (16)**|ジョブの識別番号。|  
|**profile_id**|**int**|構成の ID、 [MSagent_profiles](../../relational-databases/system-tables/msagent-profiles-transact-sql.md)テーブル。|  
|**publisher_security_mode**|**smallint**|パブリッシャーに接続するときにエージェントで使用されるセキュリティ モード。次のいずれかの値をとります。<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証です。|  
|**publisher_login**|**sysname**|パブリッシャーに接続するときに使用されるログイン。|  
|**publisher_password**|**nvarchar (524)**|パブリッシャーに接続するときに使用されるパスワードの暗号化された値。|  
|**job_step_uid**|**uniqueidentifier**|エージェントが起動される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップの一意な ID|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
