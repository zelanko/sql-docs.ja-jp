---
title: MSmerge_identity_range (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSmerge_identity_range_TSQL
- MSmerge_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_identity_range system table
ms.assetid: 493a2028-88a0-4e83-ad89-ae5661d9f477
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 27906e593020d45a9fb5e79be6ac53bc0e7fafcc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62904794"
---
# <a name="msmergeidentityrange-transact-sql"></a>MSmerge_identity_range (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_identity_range**テーブルがパブリケーションに対するサブスクリプションの id 列に割り当てられている数値の範囲を追跡するために使用されるレプリケーションが自動的に管理するこれらの範囲の割り当て。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|指定されたサブスクリプションの一意な識別番号。|  
|**artid**|**uniqueidentifier**|指定したアーティクルの一意な ID 番号です。|  
|**range_begin**|**numeric(38)**|現在の範囲の開始時の id 値です。|  
|**range_end**|**numeric(38)**|現在の範囲の最後に id 値です。|  
|**next_range_begin**|**numeric(38)**|[次へ] の範囲で割り当てられるの開始時の id 値です。|  
|**next_range_end**|**numeric(38)**|[次へ] の範囲で割り当てられるの最後の id 値です。|  
|**is_pub_range**|**bit**|値**1** id 範囲がパブリケーションに割り当てられている場合。|  
|**max_used**|**numeric(38)**|割り当てることができる最大 id 値です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
