---
title: MSmerge_identity_range_allocations (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
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
- MSmerge_identity_range_allocations
- MSmerge_identity_range_allocations_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range_allocations system table
ms.assetid: 6362e35e-0ab3-4638-855b-1ce013f5fd6d
caps.latest.revision: 13
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 9a7d2e628f8bd70b5e71b294b64674214dd2a0f0
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "33005479"
---
# <a name="msmergeidentityrangeallocations-transact-sql"></a>MSmerge_identity_range_allocations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_identity_range_allocations** id 範囲の割り当て、パブリッシャーとサブスクライバーの両方にパブリッシュされたアーティクルの履歴を追跡するためにテーブルを使用します。 このテーブルは、ディストリビューション データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**publisher_id**|**smallint**|パブリッシャーの ID。|  
|**publisher_db**|**nvarchar(128)**|パブリケーション データベースの名前です。|  
|**パブリケーション**|**nvarchar(128)**|パブリケーションの名前を指定します。|  
|**article**|**nvarchar(128)**|アーティクルの名前です。|  
|**サブスクライバー**|**nvarchar(128)**|サブスクライバーの名前。|  
|**@subscriber_db**|**nvarchar(128)**|サブスクリプション データベースの名前。|  
|**is_pub_range**|**bit**|ID 範囲がパブリッシャーに割り当てられているかどうかの一覧です。|  
|**ranges_allocated**|**tinyint**|割り当てられている ID 範囲の数です。|  
|**range_begin**|**numeric(38)**|範囲の開始値です。|  
|**range_end**|**numeric(38)**|範囲の最後の値です。|  
|**next_range_begin**|**numeric(38)**|次の範囲で割り当てられる開始値です。|  
|**next_range_end**|**numeric(38)**|次の範囲で割り当てられる最後の値です。|  
|**max_used**|**numeric(38)**|使用されている最大 ID 値です。|  
|**time_of_allocation**|**datetime**|割り当てが行われた時刻です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
