---
title: MSmerge_identity_range (Transact-sql) |Microsoft Docs
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 672715bb7bfa83767975c399f75595af04f23d57
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825844"
---
# <a name="msmerge_identity_range-transact-sql"></a>MSmerge_identity_range (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_identity_range**テーブルは、レプリケーションがこれらの範囲の割り当てを自動的に管理するパブリケーションに対するサブスクリプションの id 列に割り当てられた数値範囲を追跡するために使用されます。 このテーブルは、パブリケーションデータベースとサブスクリプションデータベースに格納されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**subid**|**uniqueidentifier**|指定されたサブスクリプションの一意の識別番号。|  
|**artid**|**uniqueidentifier**|指定されたアーティクルの一意の識別番号。|  
|**range_begin**|**数値 (38)**|現在の範囲の先頭にある id 値。|  
|**range_end**|**数値 (38)**|現在の範囲の末尾にある id 値。|  
|**next_range_begin**|**数値 (38)**|割り当てられる次の範囲の先頭にある id 値。|  
|**next_range_end**|**数値 (38)**|割り当てられる次の範囲の末尾にある id 値。|  
|**is_pub_range**|**bit**|Id 範囲がパブリケーションに割り当てられている場合は**1**を指定します。|  
|**max_used**|**数値 (38)**|割り当てることができる最大 id 値。|  
  
## <a name="see-also"></a>参照  
 [レプリケーションテーブル &#40;Transact-sql&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
