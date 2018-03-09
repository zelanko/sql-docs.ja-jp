---
title: "MSreplication_subscriptions (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
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
f1_keywords:
- MSreplication_subscriptions
- MSreplication_subscriptions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSreplication_subscriptions system table
ms.assetid: fd0c5843-4e9b-4448-8bfb-0a4067d1d8d1
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 3840528a0a566f250eae99c2764f64766c4e0891
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="msreplicationsubscriptions-transact-sql"></a>MSreplication_subscriptions (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSreplication_subscriptions**テーブルに 1 行ディストリビューション エージェントが、ローカル サブスクライバー データベースのサービスごとのレプリケーション情報にはが含まれています。 次の表は、サブスクリプション データベースに格納されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**パブリッシャー**|**sysname**|パブリッシャーの名前。|  
|**publisher_db**|**sysname**|パブリッシャー データベースの名前。|  
|**パブリケーション**|**sysname**|パブリケーションの名前を指定します。|  
|**independent_agent**|**bit**|このパブリケーションに対して、スタンドアロンのディストリビューション エージェントがあるかどうかを示します。|  
|**subscription_type**|**int**|サブスクリプションの種類です。<br /><br /> 0 = プッシュ<br /><br /> 1 = プル<br /><br /> 2 = 匿名です。|  
|**distribution_agent**|**sysname**|ディストリビューション エージェントの名前。|  
|**[時刻]**|**smalldatetime**|ディストリビューション エージェントによる前回の更新時刻。|  
|**説明**|**nvarchar (255)**|サブスクリプションの説明。|  
|**transaction_timestamp**|**varbinary (16)**|内部使用のみ。|  
|**update_mode**|**tinyint**|更新の種類。|  
|**agent_id**|**binary (16)**|エージェントの ID。|  
|**subscription_guid**|**binary (16)**|パブリケーションにおけるサブスクリプションのバージョンを表すグローバル識別子。|  
|**subid**|**binary (16)**|匿名サブスクリプションのグローバル識別子です。|  
|**immediate_sync**|**bit**|スナップショット エージェントが実行されるたびに同期ファイルが作成されるか、または作り直されるかを示します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-views/replication-views-transact-sql.md)   
 [sp_helpsubscription &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helpsubscription-transact-sql.md)  
  
  
