---
title: MSmerge_dynamic_snapshots (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology:
- replication
ms.topic: language-reference
f1_keywords:
- MSmerge_dynamic_snapshots_TSQL
- MSmerge_dynamic_snapshots
dev_langs:
- TSQL
helpviewer_keywords:
- MSmerge_dynamic_snapshots system table
ms.assetid: a5592b3c-731b-4fc9-ae4b-2602ed78248e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: fa40b26fec6e9d0a0924de068474966ecacc993a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47663026"
---
# <a name="msmergedynamicsnapshots-transact-sql"></a>MSmerge_dynamic_snapshots (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSmerge_dynamic_snapshots**テーブルは、パラメーター化された行フィルターを使用したマージ パブリケーションに対して定義されている各パーティションのフィルター選択されたデータ スナップショットの場所を追跡します。 このテーブルに格納されます、**パブリケーション**データベース。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**partition_id**|**int**|マージ パーティションの ID。|  
|**dynamic_snapshot_location**|**nvarchar (255)**|パーティションに関連する、フィルター選択されたデータのスナップショットの場所。|  
|**last_updated**|**datetime**|フィルター選択されたデータのスナップショットが更新された日付。|  
  
## <a name="see-also"></a>参照  
 [レプリケーション テーブル &#40;Transact-SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)  
  
  
