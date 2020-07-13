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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 0822c2de02de9ef0a420f0066d058fad200b4a88
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85881467"
---
# <a name="mstracer_tokens-transact-sql"></a>MStracer_tokens (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  **MStracer_tokens**テーブルは、パブリケーションに挿入されたトレーサートークンレコードの記録を保持します。 このテーブルは、ディストリビューションデータベースに格納され、パフォーマンス監視のためにレプリケーションによって使用されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|トレーサートークンレコードを識別します。|  
|**publication_id**|**int**|トレーサー トークン レコードが挿入されるパブリケーションの識別子。|  
|**publisher_commit**|**datetime**|トレーサートークンレコードがパブリッシャーでコミットされた日付と時刻。|  
|**distributor_commit**|**datetime**|トレーサー トークン レコードがディストリビューター側でコミットされた日付と時刻。|  
  
## <a name="see-also"></a>関連項目  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
