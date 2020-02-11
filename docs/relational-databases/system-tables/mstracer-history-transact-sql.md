---
title: MStracer_history (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MStracer_history
- MStracer_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_history system table
ms.assetid: 97237a0c-d574-4b17-8a94-1a8730b31d98
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e1683427057ac458e09bddde51dc70d8d402d38
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68016448"
---
# <a name="mstracer_history-transact-sql"></a>MStracer_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MStracer_history**テーブルには、サブスクライバーで受信したすべてのトレーサートークンの記録が保持されます。 このテーブルは、ディストリビューションデータベースに格納され、パフォーマンス監視のためにレプリケーションによって使用されます。  
  
|列名|データ型|[説明]|  
|-----------------|---------------|-----------------|  
|**parent_tracer_id**|**int**|トレーサー トークンを一意に識別します。|  
|**agent_id**|**int**|トレーサートークンレコードを処理したエージェントを識別します。|  
|**subscriber_commit**|**DATETIME**|トレーサー トークン レコードがサブスクライバーでコミットされた日付と時刻です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーションビュー &#40;Transact-sql&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
