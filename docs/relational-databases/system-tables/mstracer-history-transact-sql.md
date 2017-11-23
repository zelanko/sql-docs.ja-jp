---
title: "MStracer_history (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-tables
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- MStracer_history
- MStracer_history_TSQL
dev_langs: TSQL
helpviewer_keywords: MStracer_history system table
ms.assetid: 97237a0c-d574-4b17-8a94-1a8730b31d98
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 59673833f8862368296e6803805a3f2c99ef1b8a
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mstracerhistory-transact-sql"></a>MStracer_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MStracer_history**テーブルがサブスクライバーで受信されたすべてのトレーサー トークン レコードを保持します。 このテーブルはディストリビューション データベースに格納され、レプリケーションによりパフォーマンス監視のために使用されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**parent_tracer_id**|**int**|トレーサー トークンを一意に識別します。|  
|**agent_id**|**int**|トレーサー トークン レコードを処理したエージェントを識別します。|  
|**subscriber_commit**|**datetime**|トレーサー トークン レコードがサブスクライバーでコミットされた日付と時刻です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
