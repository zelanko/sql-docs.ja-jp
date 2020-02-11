---
title: MSlogreader_agents (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSlogreader_agents_TSQL
- MSlogreader_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSlogreader_agents system table
ms.assetid: 8baa3c5a-cb40-42d0-b966-00e6d55368e8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 802d2075a0146febc4521fb17b65f236533596bf
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67907300"
---
# <a name="mslogreader_agents-transact-sql"></a>MSlogreader_agents (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSlogreader_agents**テーブルには、ローカルディストリビューターで実行されているログリーダーエージェントごとに1つの行が含まれています。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**番号**|**int**|ログリーダーエージェントの ID。|  
|**name**|**nvarchar (100)**|ログ リーダー エージェントの名前です。|  
|**publisher_id**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャーデータベースの名前。|  
|**レプリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**local_job**|**bit**|ローカル ディストリビューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブがあるかどうかを示します。|  
|**job_id**|**バイナリ (16)**|ジョブの識別番号を指定します。|  
|**profile_id**|**int**|[MSagent_profiles](../../relational-databases/system-tables/msagent-profiles-transact-sql.md)テーブルの構成 ID。|  
|**publisher_security_mode**|**smallint**|パブリッシャーに接続するときにエージェントによって使用されるセキュリティモード。次のいずれかになります。<br /><br /> **** =  0[!INCLUDE[msCoName](../../includes/msconame-md.md)]認証[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。<br /><br /> **** =  1[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証。|  
|**publisher_login**|**sysname**|パブリッシャーに接続するときに使用されるログインです。|  
|**publisher_password**|**nvarchar (524)**|パブリッシャーに接続するときに使用されるパスワードの暗号化された値。|  
|**job_step_uid**|**UNIQUEIDENTIFIER**|エージェントが起動される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップの一意な ID|  
|**job_login**|**sysname**||  
|**job_password**|**nvarchar (524)**||  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
