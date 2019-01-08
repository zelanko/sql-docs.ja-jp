---
title: MSmerge_agents (TRANSACT-SQL) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 1053b358a5854febe1147ceb5ec0a374468c5b69
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52785704"
---
# <a name="msmergeagents-transact-sql"></a>MSmerge_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_agents**テーブルは、サブスクライバーで実行されるマージ エージェントはごとに 1 行を格納します。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**id**|**int**|マージ エージェントの ID です。|  
|**name**|**nvarchar(100)**|マージ エージェントの名前です。|  
|**publisher_id**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前。|  
|**パブリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**subscriber_id**|**smallint**|サブスクライバーの ID。|  
|**@subscriber_db**|**sysname**|サブスクリプション データベースの名前。|  
|**local_job**|**bit**|ローカル ディストリビューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブがあるかどうかを示します。|  
|**job_id**|**binary(16)**|ジョブの識別番号。|  
|**profile_id**|**int**|ある構成 ID、 **MSagent_profiles**テーブル。|  
|**anonymous_subid**|**uniqueidentifier**|匿名エージェントの ID です。|  
|**subscriber_name**|**sysname**|サブスクライバーの名前。|  
|**creation_date**|**datetime**|ディストリビューション エージェントまたはマージ エージェントが作成された日時です。|  
|**offload_enabled**|**bit**|エージェントをリモートから起動できることを指定します。<br /><br /> **0**エージェントをリモートでアクティブにできませんを指定します。<br /><br /> **1**リモート、および offload_server プロパティで指定されたリモート コンピューター上にエージェントをアクティブ化を指定します。|  
|**offload_server**|**sysname**|エージェントをリモートから起動するときに使用するサーバーのネットワーク名を指定します。|  
|**sid**|**varbinary(85)**|最初の実行時の、ディストリビューション エージェントまたはマージ エージェントのセキュリティ識別番号 (SID) です。|  
|**subscriber_security_mode**|**smallint**|サブスクライバーに接続するときにエージェントが使用するセキュリティ モードです。次のいずれかの値をとります。<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証。|  
|**subscriber_login**|**sysname**|サブスクライバーに接続するときに使用するログイン名です。|  
|**@subscriber_password**|**nvarchar (524)**|サブスクライバーに接続するときに使用するパスワードの暗号化された値です。|  
|**publisher_security_mode**|**smallint**|パブリッシャーに接続するときにエージェントで使用されるセキュリティ モード。次のいずれかの値をとります。<br /><br /> **0**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証します。<br /><br /> **1**  =  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 認証。|  
|**publisher_login**|**sysname**|パブリッシャーに接続するときに使用されるログイン。|  
|**publisher_password**|**nvarchar (524)**|パブリッシャーに接続するときに使用されるパスワードの暗号化された値。|  
|**job_step_uid**|**uniqueidentifier**|エージェントが起動される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップの一意な ID|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
