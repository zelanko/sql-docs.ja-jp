---
title: "sys.traces (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- traces
- sys.traces_TSQL
- sys.traces
- traces_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.traces catalog view
ms.assetid: 4a03be22-b7da-4e2a-97ff-94bed890a620
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a846bac5a610bac22c9b00712df5ea04c2779df1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="systraces-transact-sql"></a>sys.traces (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **Sys.traces**カタログ ビューには、システムで現在実行中のトレースが含まれています。 このビューでは、代わりに、 **fn_trace_getinfo**関数。  
  
 サポートされているトレース イベントの一覧については、次を参照してください。 [SQL Server Event Class Reference](../../relational-databases/event-classes/sql-server-event-class-reference.md)です。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 拡張イベント カタログ ビューを代わりに使用します。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|トレース ID。|  
|**ステータス**|**int**|トレースの状態。<br /><br /> 0 = 停止<br /><br /> 1 = 実行中|  
|**path**|**nvarchar(260)**|トレース ファイルのパス。 トレースが行セット トレースの場合、この値は NULL になります。|  
|**max_size**|**bigint**|トレース ファイル サイズの上限 (MB 単位)。 トレースが行セット トレースの場合、この値は NULL になります。|  
|**stop_time**|**datetime**|実行中のトレースを停止する日時。|  
|**max_files**|**int**|ロールオーバー ファイルの最大数。 最大数が設定されていない場合、この値は NULL になります。|  
|**is_rowset**|**bit**|1 = 行セット トレース。|  
|**is_rollover**|**bit**|1 = ロールオーバー オプションが有効。|  
|**is_shutdown**|**bit**|1 = シャットダウン オプションが有効。|  
|**is_default**|**bit**|1 = 既定のトレース。|  
|**buffer_count**|**int**|トレースによって使用されるメモリ内バッファーの数。|  
|**buffer_size**|**int**|各バッファーのサイズ (KB 単位)。|  
|**file_position**|**bigint**|最後のトレース ファイルの位置。 トレースが行セット トレースの場合、この値は NULL になります。|  
|**reader_spid**|**int**|行セット トレース リーダーのセッション ID。 トレースがファイル トレースの場合、この値は NULL になります。|  
|**start_time**|**datetime**|トレースの開始日時。|  
|**last_event_time**|**datetime**|最後のイベントが発生した日時。|  
|**event_count**|**bigint**|発生したイベントの総数。|  
|**dropped_event_count**|**int**|削除されたイベントの総数。|  
  
## <a name="permissions"></a>権限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [オブジェクト カタログ ビュー &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [sys.trace_categories &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-categories-transact-sql.md)   
 [sys.trace_columns &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-columns-transact-sql.md)   
 [sys.trace_events &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-events-transact-sql.md)   
 [sys.trace_event_bindings &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-event-bindings-transact-sql.md)   
 [sys.trace_subclass_values &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-trace-subclass-values-transact-sql.md)  
  
  
