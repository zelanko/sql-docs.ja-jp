---
title: MStracer_tokens (TRANSACT-SQL) |Microsoft ドキュメント
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
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 1822cdc0dd42a2e7797dec4aeb3a5b9627b4eac8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33004539"
---
# <a name="mstracertokens-transact-sql"></a>MStracer_tokens (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MStracer_tokens**テーブルがパブリケーションに挿入されたトレーサー トークン レコードの記録を保持します。 このテーブルはディストリビューション データベースに格納され、レプリケーションによりパフォーマンス監視のために使用されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**tracer_id**|**int**|トレーサー トークン レコードの識別子。|  
|**publication_id**|**int**|トレーサー トークン レコードが挿入されるパブリケーションの識別子。|  
|**publisher_commit**|**datetime**|トレーサー トークン レコードがパブリッシャー側でコミットされた日付と時刻。|  
|**distributor_commit**|**datetime**|トレーサー トークン レコードがディストリビューター側でコミットされた日付と時刻。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
