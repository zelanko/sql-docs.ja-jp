---
title: MSsub_identity_range (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
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
- MSsub_identity_range_TSQL
- MSsub_identity_range
dev_langs:
- TSQL
helpviewer_keywords:
- MSsub_identity_range system table
ms.assetid: 26e20d28-14ed-44fc-af3b-4de386de4bb8
caps.latest.revision: 26
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bc5a151a86defb3b76bad8b6a525e3add3a6a159
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="mssubidentityrange-transact-sql"></a>MSsub_identity_range (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsub_identity_range**テーブルは、サブスクリプションの id 範囲管理サポートを提供します。 このテーブルは、subscription データベースに保存されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**objid**|**int**|レプリケーションで管理される ID 列を持つテーブルの ID です。|  
|**range**|**bigint**|サブスクライバーで調整の際に割り当てられる連続する ID 値の範囲の大きさを制御します。|  
|**last_seed**|**bigint**|現在の範囲の下限です。|  
|**threshold**|**int**|ディストリビューション エージェントがどの時点で新しい ID 範囲を割り当てるかを制御するパーセンテージの値です。 値の比率が指定されている場合*しきい値*はディストリビューション エージェントは、新しい id 範囲を作成を使用します。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40; です。TRANSACT-SQL と &#41; です。](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [レプリケーション ビュー &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
