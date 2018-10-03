---
title: MStracer_tokens (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MStracer_tokens_TSQL
- MStracer_tokens
dev_langs:
- TSQL
helpviewer_keywords:
- MStracer_tokens system table
ms.assetid: b273aa48-8188-4213-8e2c-311543c3236f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 55140e134876870179c0a13208e85ee55414ca8f
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47628940"
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
  
  
