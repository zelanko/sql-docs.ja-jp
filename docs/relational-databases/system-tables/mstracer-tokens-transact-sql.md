---
title: MStracer_tokens (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
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
- MStracer_tokens_TSQL
- MStracer_tokens
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_tokens system table
ms.assetid: b273aa48-8188-4213-8e2c-311543c3236f
caps.latest.revision: 28
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 25a5d05c3c4ad81da0856d4e073f7aeb462109e7
ms.sourcegitcommit: a431ca21eac82117492d7b84c398ddb3fced53cc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2018
ms.locfileid: "39103260"
---
# <a name="mstracertokens-transact-sql"></a>MStracer_tokens (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MStracer_tokens**テーブルには、パブリケーションに挿入されたトレーサー トークン レコードの記録が保持されます。 このテーブルはディストリビューション データベースに格納され、レプリケーションによりパフォーマンス監視のために使用されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|トレーサー トークン レコードの識別子。|  
|**publication_id**|**int**|トレーサー トークン レコードが挿入されるパブリケーションの識別子。|  
|**publisher_commit**|**datetime**|トレーサー トークン レコードがパブリッシャー側でコミットされた日付と時刻。|  
|**distributor_commit**|**datetime**|トレーサー トークン レコードがディストリビューター側でコミットされた日付と時刻。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
