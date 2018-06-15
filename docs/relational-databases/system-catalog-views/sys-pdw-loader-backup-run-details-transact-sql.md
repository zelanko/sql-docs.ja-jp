---
title: sys.pdw_loader_backup_run_details (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.service: sql-data-warehouse
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 04fc004f-ee15-4d7a-be08-78357aa99b55
caps.latest.revision: 9
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 82523cd453a2c4352121655c98a57e0ee4cb173b
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33180424"
---
# <a name="syspdwloaderbackuprundetails-transact-sql"></a>sys.pdw_loader_backup_run_details (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  さらに詳細についてには、以外の情報が含まれています[sys.pdw_loader_backup_runs &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)、進行中と完了したバックアップおよび復元操作で[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]および継続的なについてバックアップ、復元、およびロード操作が完了し、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。 情報は、システムの再起動の間で永続化します。  
  
|列名|データ型|Description|範囲|  
|-----------------|---------------|-----------------|-----------|  
|run_id|**int**|特定のバックアップまたは復元の実行の一意の識別子。<br /><br /> run_id と pdw_node_id は、このビューのキーを形成します。||  
|pdw_node_id|**int**|このレコードの詳細を保持するアプライアンス ノードの一意の識別子。<br /><br /> run_id と pdw_node_id は、このビューのキーを形成します。|Node_id を参照してください[sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)です。|  
|ステータス|**nvarchar(16)**|実行の現在の状態。|'キャンセル'、' 完了 '、'失敗'、'QUEUED'、'実行中|  
|start_time|**datetime**|この特定のノードで操作が開始された時刻。||  
|end_time|**datetime**|時間は、操作の終了時刻、この特定のノードに存在する場合です。||  
|total_elapsed_time|**int**|この特定のノードで、操作が実行されている時間の合計。|Total_elapsed_time では、整数値 (ミリ秒単位で 24.8 日) の最大値を超えるをオーバーフローしました期日の実体化エラーが発生します。<br /><br /> 最大値をミリ秒単位は 24.8 日に相当します。|  
|進行状況|**int**|パーセンテージで表される操作の進行状況。|0 ～ 100|  
  
## <a name="see-also"></a>参照  
 [SQL Data Warehouse と並列データ ウェアハウスのカタログ ビュー](../../relational-databases/system-catalog-views/sql-data-warehouse-and-parallel-data-warehouse-catalog-views.md)  
  
  
