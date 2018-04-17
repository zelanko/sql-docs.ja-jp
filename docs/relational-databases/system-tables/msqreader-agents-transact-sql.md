---
title: MSqreader_agents (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-tables
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- MSqreader_agents_TSQL
- MSqreader_agents
dev_langs:
- TSQL
helpviewer_keywords:
- MSqreader_agents system table
ms.assetid: dfa1f45e-c531-4385-a097-0a9edd1d7eab
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5eb1b2dc7fee99982131c0abeae250b403c50786
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="msqreaderagents-transact-sql"></a>MSqreader_agents (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSqreader_agents**テーブルには、キュー リーダー エージェントがローカル ディストリビューターで実行されるごとに 1 つの行が含まれています。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|キュー リーダー エージェントの ID|  
|**name**|**nvarchar(100)**|キュー リーダー エージェントの名前|  
|**job_id**|**binary(16)**|一意のジョブの ID 番号から**sysjobs**テーブル。|  
|**profile_id**|**int**|プロファイルの ID、 **MSagent_profiles**テーブル。|  
|**job_step_uid**|**uniqueidentifier**|エージェントが起動される [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブ ステップの一意な ID|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
