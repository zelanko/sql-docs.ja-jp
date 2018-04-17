---
title: MSmerge_dynamic_snapshots (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/04/2017
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
- MSmerge_dynamic_snapshots_TSQL
- MSmerge_dynamic_snapshots
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_dynamic_snapshots system table
ms.assetid: a5592b3c-731b-4fc9-ae4b-2602ed78248e
caps.latest.revision: 28
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: bea5dcda7bed95ca3c778075fdbeff8b918d5ce9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="msmergedynamicsnapshots-transact-sql"></a>MSmerge_dynamic_snapshots (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_dynamic_snapshots**テーブルは、パラメーター化された行フィルターを使用して、マージ パブリケーションに対して定義されている各パーティションに対してフィルター選択されたデータ スナップショットの場所を追跡します。 次の表は、**パブリケーション**データベース。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|マージ パーティションの ID。|  
|**dynamic_snapshot_location**|**nvarchar (255)**|パーティションに関連する、フィルター選択されたデータのスナップショットの場所。|  
|**last_updated**|**datetime**|フィルター選択されたデータのスナップショットが更新された日付。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
