---
title: MSagent_profiles (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
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
- MSagent_profiles
- MSagent_profiles_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSagent_profiles system table
ms.assetid: 4ab1b2ae-b6d9-42b7-9b31-98547dbb7f99
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2ed91d28975305af16fd70c21e986a75f774fb57
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="msagentprofiles-transact-sql"></a>MSagent_profiles (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSagent_profiles**テーブルに定義されているレプリケーション エージェントのプロファイルごとに 1 つの行が含まれています。 次の表は、 **msdb**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**profile_id**|**int**|プロファイル ID です。|  
|**profile_name**|**sysname**|エージェントの種類に固有のプロファイル名です。|  
|**agent_type**|**int**|エージェントの種類。<br /><br /> **1**スナップショット エージェントを =<br /><br /> **2**ログ リーダー エージェントを =<br /><br /> **3** = ディストリビューション エージェント<br /><br /> **4** = マージ エージェント<br /><br /> **9**キュー リーダー エージェントを =|  
|**type**|**int**|プロファイルの種類です。<br /><br /> **0**システムを =**1** = カスタム|  
|**説明**|**nvarchar(3000)**|プロファイルの説明です。|  
|**def_profile**|**bit**|このプロファイルがこのエージェント タイプの既定値かどうかを示します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
