---
title: MStracer_history (TRANSACT-SQL) |Microsoft Docs
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
manager: craigg
ms.openlocfilehash: b1ba25e4f55debbe73a66de23986743a83d1feb5
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2018
ms.locfileid: "52765264"
---
# <a name="mstracerhistory-transact-sql"></a>MStracer_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MStracer_history**テーブルには、サブスクライバーで受信したすべてのトレーサー トークンの記録が保持されます。 このテーブルはディストリビューション データベースに格納され、レプリケーションによりパフォーマンス監視のために使用されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**parent_tracer_id**|**int**|トレーサー トークンを一意に識別します。|  
|**agent_id**|**int**|トレーサー トークン レコードを処理したエージェントを識別します。|  
|**subscriber_commit**|**datetime**|トレーサー トークン レコードがサブスクライバーでコミットされた日付と時刻です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
