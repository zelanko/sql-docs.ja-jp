---
title: MSmerge_agents (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_agents
- MSmerge_agents_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_agents system table
ms.assetid: 639d2ebb-2c37-4fe0-b14b-1637bc5fc221
author: stevestein
ms.author: sstein
ms.openlocfilehash: 980ecd00a07e1119a64552a3f4c903434fd09029
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68106441"
---
# <a name="msmerge_agents-transact-sql"></a>MSmerge_agents (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_agents**テーブルには、サブスクライバーで実行されているマージエージェントごとに1つの行が含まれています。 このテーブルは、ディストリビューションデータベースに格納されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**番号**|**int**|マージエージェントの ID。|  
|**name**|**nvarchar (100)**|マージエージェントの名前。|  
|**publisher_id**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャーデータベースの名前。|  
|**レプリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**subscriber_id**|**smallint**|サブスクライバーの ID です。|  
|**subscriber_db**|**sysname**|サブスクリプションデータベースの名前。|  
|**local_job**|**bit**|ローカル ディストリビューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブがあるかどうかを示します。|  
|**job_id**|**バイナリ (16)**|ジョブの識別番号を指定します。|  
|**profile_id**|**int**|**MSagent_profiles**テーブルの構成 ID。|  
|**anonymous_subid**|**UNIQUEIDENTIFIER**|匿名エージェントの ID。|  
|**subscriber_name**|**sysname**|サブスクライバーの名前です。|  
|**creation_date**|**DATETIME**|分布またはマージエージェントが作成された日付と時刻。|  
|**offload_enabled**|**bit**|エージェントをリモートでアクティブ化できることを指定します。<br /><br /> **0**を指定すると、エージェントをリモートでアクティブにすることはできません。<br /><br /> **1**は、エージェントをリモートでアクティブにし、offload_server プロパティで指定されたリモートコンピューターでアクティブにすることを指定します。|  
|**offload_server**|**sysname**|リモートエージェントのアクティブ化に使用するサーバーのネットワーク名を指定します。|  
|**sid**|**varbinary (85)**|最初の実行時の、ディストリビューション エージェントまたはマージ エージェントのセキュリティ識別番号 (SID) です。|  
|**subscriber_security_mode**|**smallint**|サブスクライバーへの接続時にエージェントによって使用されるセキュリティモード。次のいずれかになります。<br /><br /> **** =  0[!INCLUDE[msCoName](../../includes/msconame-md.md)]認証[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。<br /><br /> **** =  1[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証。|  
|**subscriber_login**|**sysname**|サブスクライバーへの接続時に使用されるログインです。|  
|**subscriber_password**|**nvarchar (524)**|サブスクライバーへの接続時に使用されるパスワードの暗号化された値です。|  
|**publisher_security_mode**|**smallint**|パブリッシャーに接続するときにエージェントによって使用されるセキュリティモード。次のいずれかになります。<br /><br /> **** =  0[!INCLUDE[msCoName](../../includes/msconame-md.md)]認証[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。<br /><br /> **** =  1[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証。|  
|**publisher_login**|**sysname**|パブリッシャーに接続するときに使用されるログインです。|  
|**publisher_password**|**nvarchar (524)**|パブリッシャーに接続するときに使用されるパスワードの暗号化された値。|  
|**job_step_uid**|**UNIQUEIDENTIFIER**|エージェントが起動される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップの一意な ID|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
