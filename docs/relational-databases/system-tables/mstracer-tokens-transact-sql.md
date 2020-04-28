---
title: MStracer_tokens (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
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
ms.openlocfilehash: dc2e7e5b2cf767972ab6531b5f06c2043a3f07fc
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68016464"
---
# <a name="mstracer_tokens-transact-sql"></a>MStracer_tokens (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MStracer_tokens**テーブルは、パブリケーションに挿入されたトレーサートークンレコードの記録を保持します。 このテーブルは、ディストリビューションデータベースに格納され、パフォーマンス監視のためにレプリケーションによって使用されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|トレーサートークンレコードを識別します。|  
|**publication_id**|**int**|トレーサー トークン レコードが挿入されるパブリケーションの識別子。|  
|**publisher_commit**|**datetime**|トレーサートークンレコードがパブリッシャーでコミットされた日付と時刻。|  
|**distributor_commit**|**datetime**|トレーサー トークン レコードがディストリビューター側でコミットされた日付と時刻。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
