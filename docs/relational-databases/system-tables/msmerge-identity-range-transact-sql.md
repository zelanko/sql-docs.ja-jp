---
title: MSmerge_identity_range (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
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
ms.openlocfilehash: 623914f556064f690c0883e41316c76e84c3c7e3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47854770"
---
# <a name="msmergeidentityrange-transact-sql"></a>MSmerge_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_identity_range**テーブルがパブリケーションに対するサブスクリプションの id 列に割り当てられている数値の範囲を追跡するために使用されるレプリケーションが自動的に管理するこれらの範囲の割り当て。 このテーブルは、パブリケーション データベースとサブスクリプション データベースに保存されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|指定したサブスクリプションの一意の ID 番号です。|  
|**artid**|**uniqueidentifier**|指定したアーティクルの一意な ID 番号です。|  
|**range_begin**|**numeric(38)**|現在の範囲の開始 ID 値です。|  
|**range_end**|**numeric(38)**|現在の範囲の終了 ID 値です。|  
|**next_range_begin**|**numeric(38)**|割り当てられる次の範囲の開始 ID 値です。|  
|**next_range_end**|**numeric(38)**|割り当てられる次の範囲の終了 ID 値です。|  
|**is_pub_range**|**bit**|値**1** id 範囲がパブリケーションに割り当てられている場合。|  
|**max_used**|**numeric(38)**|割り当てることができる ID の最大値です。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
