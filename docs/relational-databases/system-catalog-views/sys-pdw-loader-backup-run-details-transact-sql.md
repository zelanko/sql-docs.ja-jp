---
title: pdw_loader_backup_run_details (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: dead5962987f7fb132f21bb4e3517f7cc9249601
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68127647"
---
# <a name="syspdw_loader_backup_run_details-transact-sql"></a>pdw_loader_backup_run_details (Transact-sql)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  では、詳細情報が含まれています。詳細については、「」を参照して[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ください。詳細[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]については、「」を参照してください。詳細については、「」を参照してください。詳細については、「」の[&#41;&#40;pdw_loader_backup_runs](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)を参照してください。 情報は、システムの再起動の間で永続化します。  
  
|列名|データ型|説明|範囲|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|特定のバックアップまたは復元の実行の一意の識別子。<br /><br /> このビューのキーは run_id と pdw_node_id によって形成されます。||  
|pdw_node_id|**int**|このレコードが詳細を保持するアプライアンスノードの一意識別子。<br /><br /> このビューのキーは run_id と pdw_node_id によって形成されます。|『 [Transact-sql&#41;&#40;dm_pdw_nodes](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)の node_id を参照してください。|  
|status|**nvarchar (16)**|実行の現在の状態。|' 取り消された '、' COMPLETED '、' FAILED '、' QUEUED '、' RUNNING '|  
|start_time|**datetime**|この特定のノードで操作が開始された時刻。||  
|end_time|**datetime**|この特定のノードで操作が終了した時刻 (存在する場合)。||  
|total_elapsed_time|**int**|この特定のノードで操作が実行されていた合計時間。|Total_elapsed_time が整数の最大値 (ミリ秒単位で24.8 日) を超えた場合、オーバーフローによる具体化エラーが発生します。<br /><br /> ミリ秒単位の最大値は24.8 日に相当します。|  
|progress|**int**|比率で表された操作の進行状況。|0 から 100|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse and Parallel Data Warehouse Catalog Views (SQL Data Warehouse および Parallel Data Warehouse のカタログ ビュー)](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
